# Tratamento de Planilha para o Relatório de Transparência 📊

Este código trata um arquivo de extrato mensal do banco Cora utilizando Pandas, baseando-se em planilhas já tratadas de meses anteriores para identificar classificações de pagamentos.
Esta planilha será utilizada no Power BI para criar o relatório de transparência.

## Como usar o código

Para utilizar este código, siga os passos abaixo:

### 1. Importação de Planilhas

Antes de começar o tratamento da planilha atual, você deve importar as planilhas necessárias. Para fazer isso, siga os seguintes passos:

1. Certifique-se de que as planilhas estão armazenadas em uma pasta no seu Google Drive 📂.
2. Execute o código para montar o Google Drive (utiliza a biblioteca `google.colab`).

```python
from google.colab import drive
drive.mount('/content/drive')
drive.mount("/content/drive", force_remount=True)
```

3. Importe as planilhas que você deseja tratar, como no exemplo abaixo:

```python
projetointerno = pd.read_csv("drive/MyDrive/planilhas para tratamento/projetointerno.csv")
AntigaJanAgo = pd.read_csv('drive/MyDrive/planilhas para tratamento/jan-ago.csv')
Antiga0922 = pd.read_csv('drive/MyDrive/planilhas para tratamento/09.csv')
# Importe outras planilhas conforme necessário
```

### 2. Importação da Planilha Atual

Depois de importar as planilhas anteriores, você precisa importar a planilha atual que deseja tratar. Utilize o código a seguir para fazer isso:

```python
from google.colab import files
uploaded = files.upload()
planilha_atual = pd.read_csv(io.BytesIO(uploaded['cora_agosto.csv']))
```

Substitua `'cora_agosto.csv'` pelo nome do arquivo CSV que você deseja importar.

### 3. Tratamento Básico da Planilha Atual

Nesta etapa, o código realiza o pré-processamento da planilha atual. Isso inclui a adição de colunas, renomeação de categorias e categorização de transações com base em critérios específicos. O código já está configurado para realizar essas ações.

### 4. Tratamento da Planilha do [ProjetoInterno]

Este trecho de código é responsável por tratar a planilha do [ProjetoInterno]. Ele renomeia colunas e adiciona a categoria '[ProjetoInterno]' a transações específicas, conforme as configurações predefinidas.

### 5. Tratamento das Planilhas Antigas & Acréscimo de Categorias na Planilha Atual

Nesta seção, o código aplica a função `tratamento_planilhas_antigas()` a todas as planilhas antigas que você importou anteriormente. Essa função realiza o tratamento específico necessário para essas planilhas e adiciona categorias às transações da planilha atual com base nas correspondências encontradas nas planilhas antigas.

### 6. Transforma o CSV em Arquivo Excel

Por fim, o código exporta a planilha tratada em formato Excel. Certifique-se de modificar o nome do arquivo de saída conforme o mês ou período do relatório que você está gerando. Por exemplo:

```python
arquivo = 'agosto_tratado.xlsx'
planilha_atual.to_excel(arquivo)
```

Substitua `'agosto_tratado.xlsx'` pelo nome desejado para o arquivo de saída.

## Requisitos

Para executar este código, você precisará das seguintes bibliotecas Python:

- pandas
- io
- google.colab

Certifique-se de que todas as dependências estejam instaladas antes de executar o código. Utilize-o no [Google Colab de IDFin](https://colab.research.google.com/drive/11DQfx65-2Jdl9edW-mPUX8adCSCWtDAQ?usp=sharing).

## Alterações Pendentes e Atualizações Frequentes 🔄

Este código pode estar sujeito a alterações pendentes e atualizações frequentes. Certifique-se de verificar as issues do repositório para obter informações atualizadas.

- **Semestral**: Verificar a planilha do [ProjetoInterno] para garantir que as colunas ainda estão compatíveis.
- **Mensal**: Adicionar novas planilhas e, se possível, substituir por planilhas mais compactas (anuais, semestrais).

Mantenha-se atualizado com as melhorias e ajustes neste código para garantir um processamento eficiente das planilhas de transações financeiras.
