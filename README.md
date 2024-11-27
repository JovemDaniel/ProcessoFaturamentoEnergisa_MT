# Projeto Faturamento Energisa Mato Grosso do Sul

Este repositório contém os scripts e fluxos de trabalho necessários para o processo de faturamento da Energisa MS.

![image](https://github.com/user-attachments/assets/3136039c-3393-40de-a81e-395776c1b451)

## Visão Geral

O objetivo deste projeto é automatizar o processo de faturamento da Energisa, desde a verificação de emails até a transmissão e monitoramento das faturas. O projeto é dividido em várias etapas, cada uma representada por um arquivo de workflow distinto.

## Estrutura do Projeto

- **1 Main Sequence (Sequence)**: Coordena a execução de todos os sub-processos, inicializando variáveis e chamando workflows específicos.
- **1.1 CheckEmailEnergisaMS (Sequence)**: Verifica a caixa de entrada de emails para mensagens com medições de lote, salva os anexos PDF e extrai o nome do arquivo.
- **1.2 GetDataPDF (Sequence)**: Lê dados de arquivos PDF, extrai informações importantes e preenche um arquivo Excel com esses dados.
- **1.3 LoginTOTVS (Sequence)**: Realiza o login no sistema TOTVS usando credenciais armazenadas de forma segura.
- **1.4 ProcessDataInTOTVS (Sequence)**: Processa os dados dentro do sistema TOTVS, navegando pelas telas e interagindo com a aplicação conforme necessário.
- **1.5 InvoiceTransmissionAndMonitoring (Sequence)**: Realiza a transmissão e monitoramento das notas fiscais (NFs) dentro do sistema TOTVS.
- **1.6 DownloadingNFSemfaz (Sequence)**: Faz o download das notas fiscais do site da Semfaz.
- **1.7 KillAllProcesses (Sequence)**: Encerra todos os processos ao final da execução.

## Variáveis

### CheckEmailEnergisaMS
- `strOutputPathMedicoesMS`: Caminho para salvar os PDFs filtrados.

### GetDataPDF
- `strDataPDF`: Texto extraído do PDF.
- `strContractPDF`: Contrato extraído do PDF.
- `strDatePDF`: Data extraída do PDF.
- `strCodInvoicePDF`: Código da fatura extraído do PDF.
- `strConsolidationPDF`: Consolidação extraída do PDF.
- `strTotalCost`: Custo total extraído do PDF.
- `strCityPDF`: Cidade extraída do PDF.
- `strMunicipalityPDF`: Município extraído do PDF.
- `strClientCode`: Código do cliente.
- `strOrderType`: Tipo de pedido.
- `strOrderTOTVS`: Código da ordem TOTVS.
- `strCommentText`: Texto de comentário.
- `strState`: Estado extraído do PDF.

### LoginTOTVS
- `strUserTOTVS`: Nome de usuário para login no TOTVS.
- `strUserPasswordTOTVS`: Senha do usuário para login no TOTVS.

### ProcessDataInTOTVS
- `strCodeRPS`: Código RPS usado durante o processamento dos dados no TOTVS.
- `in_strOrderTOTVS`: Código da ordem TOTVS para busca e confirmação.
- `in_strPedidoVendaPath`: Caminho para o arquivo de Pedido de Venda.

### InvoiceTransmissionAndMonitoring
- `strNFCode`: Código da nota fiscal usado durante a transmissão e o monitoramento.

### DownloadingNFSemfaz
- `strSemfazURL`: URL do sistema tributário municipal.
- `strUserSemfaz`: Usuário para login no sistema Semfaz.
- `strPasswordUserSemfaz`: Senha do usuário para login no sistema Semfaz.
- `strPrintNFBar`: Barra de impressão da nota fiscal.
- `strSourceNFFilePath`: Caminho do arquivo fonte da nota fiscal.
- `strDestinationNFFilePath`: Caminho do arquivo de destino da nota fiscal.
- `ReadPDFTextResult`: Resultado da leitura do texto do PDF.
- `intTotalPagesNFFile`: Total de páginas do arquivo da nota fiscal.
- `strOutputNFFilePath`: Caminho do arquivo de saída da nota fiscal.

## Dependências

- **UiPath**: Este projeto foi desenvolvido usando o UiPath. Certifique-se de ter o UiPath instalado e configurado adequadamente.
  
Este projeto utiliza os seguintes pacotes UiPath:

- **UiPath.Excel.Activities**: 2.24.3 ou posterior
- **UiPath.Mail.Activities**: 1.23.11 ou posterior
- **UiPath.PDF.Activities**: 3.20.1 ou posterior
- **UiPath.System.Activities**: 24.11.0 ou posterior
- **UiPath.Testing.Activities**: 24.10.3 ou posterior
- **UiPath.UIAutomation.Activities**: 24.11.1 ou posterior

Certifique-se de que os pacotes estejam instalados e atualizados para evitar problemas de compatibilidade.

## Uso

1. Clone este repositório:
    ```bash
    git clone https://github.com/seu-usuario/seu-repositorio.git
    ```

2. Abra o projeto no UiPath Studio.

3. Configure as variáveis e caminhos necessários conforme mencionado nas **Configurações**.

4. Execute a sequência principal (`Main.xaml`) para iniciar o processo de faturamento.

## Desenvolvedor

**Daniel Nascimento**  
[LinkedIn](https://www.linkedin.com/in/danieloliveirain/)
