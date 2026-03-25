# Word to PDF (Service Now) - Extensão do Chrome

![image](https://github.com/fkengdb/WordToPDF-ServiceNow/blob/main/Screenshot_2%20(1).png?raw=true)

Esta é uma extensão para a conversão de documentos Word (`.docx`) para PDF diretamente da interface da plataforma ServiceNow. A extensão adiciona uma zona de _drag and drop_ (arrastar e soltar) na tela, convertendo os arquivos em segundo plano via API do iLovePDF e abrindo o PDF resultante instantaneamente em uma nova aba para visualização. (125 conversões por mês gratuitamente)

## 🛠️ Instalação (Modo Desenvolvedor)

Necessário carregá-la manualmente no seu navegador para uso. (Testado no Chrome & Edge)

[Download Extensão](https://github.com/fkengdb/WordToPDF-ServiceNow/releases/download/v1.0.1/WordToPdf_ServiceNow_v1.0.1.zip)

### Chrome
1. Faça o download e extrai a pasta onde desejar no seu computador.
2. Abra o Google Chrome e digite `chrome://extensions/` na barra de endereços (ou abra o menu > Extensões > Gerenciar extensões).
3. No canto superior direito da página de extensões, ative a chave **Modo do desenvolvedor**.
4. Em seguida, clique no botão **Carregar sem compactação** que surgirá no canto superior esquerdo.
5. Selecione a pasta no seu computador onde os arquivos da extensão (`manifest.json`, `background.js`, etc.) estão localizados e confirme.
6. A extensão e seu ícone devem aparecer na sua lista de extensões instaladas. Recomendado fixa-lá na barra superior (clicando no ícone de "quebra-cabeça" e no alfinete).

### Microsoft Edge
1. Faça o download e extrai a pasta onde desejar no seu computador.
2. Abra o Edge e digite `edge://extensions/` na barra de endereços.
3. No menu lateral, ative a chave **Modo de desenvolvedor**.
4. Clique no botão **Carregar sem compactação** (canto superior direito).
5. Selecione a pasta com os arquivos da extensão e confirme.

### Mozilla Firefox
1. Faça o download e extrai a pasta onde desejar no seu computador.
2. Abra o Firefox e digite `about:debugging#/runtime/this-firefox` na barra de endereços.
3. Na seção "Extensões Temporárias", clique no botão **Carregar extensão temporária...**.
4. Navegue até a pasta da extensão e selecione o arquivo `manifest.json`.
5. *Nota:* No Firefox, extensões temporárias podem ser descarregadas ao fechar o navegador, precisando repetir o processo ao abri-lo 

## ⚙️ Configuração Inicial (Chave da API)

Para realizar as conversões, a extensão consome a API oficial do iLovePDF. É preciso configurar uma chave de autenticação (Public Key) antes da primeira utilização:

1. Acesse o portal de desenvolvedores do iLovePDF: [https://www.iloveapi.com/user/projects](https://www.iloveapi.com/user/projects)
2. Acesse a sua conta (ou crie uma nova) e verifique seu projeto para obter a **Chave Pública** (Public Key).
3. No próprio Chrome, clique no ícone da extensão "Word to PDF (Service Now)" na barra do navegador superior.
4. Um pequeno popup vai se abrir. Cole a sua Chave Pública obtida no campo de texto **Public Key iLovePDF**.
5. Clique em **Salvar Chave**. Uma mensagem de confirmação (alert) atestará o sucesso.

## 💡 Como Usar

1. Acesse o sistema do ServiceNow na rota coberta pela extensão (extensão só é ativada para uso nesta url: https://dominio/now/nav/ui/classic/params/target/change_request.do%*).
2. Aguarde a página carregar: repare que um pequeno quadrado/botão roxo com texto **.docx** aparecerá flutuando no canto inferior direito do navegador.
3. Arraste e solte o documento word anexo a change (`.doc`, `.docx`) sobre este quadrado flutuante.
4. Acompanhe a barrinha verde de progresso e o indicativo textual da etapa logo acima dela:
   - *Autenticando...*
   - *Iniciando...*
   - *Upload...*
   - *Convertendo...*
   - *Baixando...*
5. Alcançando os 100%, o arquivo convertido será aberto quase instantaneamente em uma **nova aba** do seu navegador, utilizando o visualizador nativo de PDF.
6. A partir dessa nova aba de visualização, você pode ler o documento e, se desejar salvá-lo no seu computador com o nome original, basta clicar no botão roxo **"Baixar .pdf"** fixado no topo da tela.

---
**Nota:** A injeção da interface do "dropzone" da extensão está programada (via `manifest.json` e scripts de injeção) restritamente para as páginas dentro do *ServiceNow* atendendo às URLs do Change Request e atua apenas se a altura da tela for superior a 300px (para prevenir injeções em frames reduzidos do sistema).
