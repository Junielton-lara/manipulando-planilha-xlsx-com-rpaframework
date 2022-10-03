# manipulando-planilha-xlsx-com-rpaframework
manipulando planilha xlsx com rpaframework

#Instalação via > pip install rpaframework

#Para executar o projeto no terminal execute o comando > robot -d /log .\teste.robot


Validar preenchimento de dados no Arquivo1.xlsx  


          #Abrindo o Arquivo1.xlsx           
          Open Workbook    Arquivo1.xlsx      

        #FOR PARA GERAR DADOS ALEATORIOS PARA PREENCHIMENTO DO XLSX
        FOR    ${counter}    IN RANGE    1    10
                  ${CODIGO}  FakerLibrary.Random Int
                  ${NOME}    FakerLibrary.Name
                  ${SITUACAO}    FakerLibrary.Boolean
                  ${DATA}    FakerLibrary.Date

        # CRIANDO DICIONARIO DE PREENCHIMENTO DE ACORDO AS COLUNAS DO XLSX
        &{RESULT}  Create Dictionary
          ...  Código  ${CODIGO}
          ...  nome     ${NOME}
          ...  Situação  ${SITUACAO}
          ...  Data do cadastro  ${DATA}
        # PREENCHENDO O XLSX
          Append Rows To Worksheet  ${RESULT}  header=${TRUE}            
        END
        # SALVANDO O ARQUIVO
        Save Workbook
 
