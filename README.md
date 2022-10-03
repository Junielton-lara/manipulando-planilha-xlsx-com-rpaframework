# manipulando-planilha-xlsx-com-rpaframework
manipulando planilha xlsx com rpaframework

# Sobre o projecto
O principal objectivo deste projeto e explicar sobre o preenchimento de dados de planilha xls/xlsx de forma simples

# Isenção de responsabilidade
A solução foi testada com o sistema operativo Windows 11.

# Como configurar a sua máquina Windows 11 para executar os testes:

## 1. Instalar o Python 3
- https://www.python.org/downloads
- verificar a opção para **add Python a PATH*** durante a instalação
- em terminal de linha de comando, verificar se a Python está correctamente instalada: "python --version" - a saída deve fornecer-lhe a versão instalada

## 2. Instalar bibliotecas de estruturas de Robot
- **instalar o Robot framework** executando `pip install robotframework` num terminal de linha de comando


# Lib usada nesse teste > rpaframework

##  pip install rpaframework

# Para executar o projeto no terminal execute o comando > robot -d /log .\teste.robot


## Cod base


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
 
