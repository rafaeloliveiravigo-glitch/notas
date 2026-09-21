# Notas de Consumo

App de navegador para fotografar notas, ler **data, descrição e valor total** automaticamente e gerar um **relatório em PDF** com a lista e as fotos em anexo.

- Funciona no celular e no computador, sem instalar nada.
- A leitura da nota é feita no próprio aparelho (gratuita). Na primeira vez ele baixa o "dicionário" de leitura, que demora uns segundos; depois fica guardado.
- Com o Google Drive configurado, **tudo é sincronizado automaticamente** (notas, fotos, pedidos e extrato): o que você lança no celular aparece no computador e vice-versa.

---

## Parte 1 — Colocar o app no ar (GitHub Pages) · ~10 min

Seu endereço final será: **https://rafaeloliveiravigo-glitch.github.io/notas/**

1. Conta no GitHub criada ✔ (usuário `rafaeloliveiravigo-glitch`).
2. Repositório `notas` criado como **Público** ✔.
3. **Descompacte o zip** no computador: botão direito em `notas-app.zip` → **Extrair tudo**. Vão aparecer 5 arquivos: `index.html`, `manifest.webmanifest`, `icon-192.png`, `icon-512.png` e `README.md`.
4. Na página do repositório, no quadro azul **"Configuração rápida"**, clique no link **"enviando um arquivo existente"**.
   - Se o repositório já tiver arquivos, o caminho é: botão **Adicionar arquivo** → **Carregar arquivos**.
5. Selecione os **5 arquivos** (não a pasta) e arraste para a área **"Arraste arquivos aqui"** (ou clique em **"escolha seus arquivos"**).
6. Espere os 5 nomes aparecerem na lista, role até o fim e clique no botão verde **Confirmar alterações**.
7. No menu de cima do repositório, clique em **Configurações** (ícone de engrenagem, último item).
8. No menu da esquerda, seção **Código e automação**, clique em **Pages** (ou **Páginas**).
9. Em **Construir e implantar** (*Build and deployment*):
   - **Fonte** (*Source*): **Implantar a partir de uma ramificação** (*Deploy from a branch*).
   - **Ramificação** (*Branch*): escolha **main** e, ao lado, a pasta **/ (root)**. Clique em **Salvar**.
10. Aguarde 1 a 2 minutos e recarregue a página. Vai aparecer no topo: **"Seu site está ativo em https://rafaeloliveiravigo-glitch.github.io/notas/"** e um botão **Visitar site**.
11. Abra esse endereço no celular e coloque na tela inicial:
    - **Android (Chrome):** menu **⋮** → **Adicionar à tela inicial** (ou **Instalar app**).
    - **iPhone (Safari):** botão **Compartilhar** (quadrado com seta) → **Adicionar à Tela de Início**.

Pronto: o app já funciona (sem o Drive).

**Para atualizar o app no futuro:** no repositório, **Adicionar arquivo** → **Carregar arquivos** → arraste o `index.html` novo → **Confirmar alterações**. Em 1–2 minutos o site atualiza.

---

## Parte 2 — Ligar o Google Drive (opcional) · ~15 min

O app precisa de um **ID do cliente** do Google para pedir permissão de salvar no seu Drive. É gratuito. O app só enxerga os arquivos que ele mesmo cria (pasta **Notas de Consumo**), não o resto do seu Drive.

> Se o Google Cloud abrir em inglês: clique na sua foto (canto superior direito) → **Preferences / Preferências** → **Language / Idioma** → **Português (Brasil)**.

1. Acesse **console.cloud.google.com** com a conta Google onde quer salvar as notas. Aceite os termos se for o primeiro acesso.
2. **Criar projeto:** no topo, clique em **Selecionar um projeto** → **Novo projeto** → **Nome do projeto:** `Notas de Consumo` → **Criar**. Depois, no mesmo seletor do topo, confirme que o projeto **Notas de Consumo** está selecionado.
3. **Ativar a API do Drive:** menu **☰** (canto superior esquerdo) → **APIs e serviços** → **Biblioteca** → pesquise **Google Drive API** → clique nela → **Ativar**.
4. **Configurar a tela de consentimento:** menu **☰** → **APIs e serviços** → **Tela de permissão OAuth** (ou **Google Auth Platform**) → **Vamos começar** (*Get started*).
   - **Informações do app:** Nome do app `Notas de Consumo` · E-mail para suporte do usuário: o seu → **Próxima**.
   - **Público-alvo:** **Externo** → **Próxima**.
   - **Dados de contato:** o seu e-mail → **Próxima**.
   - **Concluir:** marque que concorda com a política → **Continuar** → **Criar**.
5. **Adicionar você como usuário de teste:** no menu da esquerda, **Público-alvo** → em **Usuários de teste**, clique **+ Adicionar usuários** → digite o seu Gmail (e de quem mais for usar) → **Salvar**.
6. **Criar o ID do cliente:** no menu da esquerda, **Clientes** → **+ Criar cliente**.
   - **Tipo de aplicativo:** **Aplicativo da Web**.
   - **Nome:** `Notas web`.
   - **Origens JavaScript autorizadas** → **+ Adicionar URI** → digite exatamente:
     `https://rafaeloliveiravigo-glitch.github.io`
     (sem `/notas` e sem barra no final).
   - Deixe **URIs de redirecionamento autorizados** em branco → **Criar**.
   - Vai abrir uma janela com o **ID do cliente** (termina em `.apps.googleusercontent.com`). Clique no ícone de copiar.
7. **No app:** menu **⋮** → **Configurações** → cole em **Google Client ID** → **Salvar**.
8. Feche um pedido com **Gerar relatório e salvar no Google Drive** (ou use **⋮ → Backup no Google Drive**). Na primeira vez:
   - Escolha sua conta Google.
   - Vai aparecer **"O Google não verificou este app"**: clique em **Continuar** (o app é seu).
   - Autorize o acesso → **Continuar**.
   - Confira no seu Drive: vai surgir a pasta **Notas de Consumo** com o PDF do pedido.

> **Erro `origin_mismatch` ou "Acesso bloqueado":** o endereço do item 6 está diferente do endereço do app. Confira o `https://` e o nome de usuário. Depois de corrigir, a mudança pode levar alguns minutos para valer.
>
> **Erro "access_denied" / "não concluiu o processo de verificação":** faltou colocar seu e-mail em **Usuários de teste** (item 5).

---

## Como usar no dia a dia

1. **Fotografar nota** (ou **Galeria**, que aceita várias fotos de uma vez).
2. O app lê a nota e preenche os campos. Os **campos em amarelo** foram lidos automaticamente: confira e corrija se precisar. Se a foto ficou de lado, toque em **Girar**.
3. **Salvar.** A nota entra na tabela (Data · Descrição · Valor), da mais antiga para a mais recente. Toque numa linha para ver a foto ou editar; a **lixeira** exclui.
4. As notas lançadas formam o **Pedido Nº xxxx em aberto** (topo). Se quiser, preencha a **Referência** (ex.: `Obra X / Setembro`).
5. No fim: **Fechar Pedido e gerar relatório** → **Gerar relatório e salvar no Google Drive**. O PDF vai direto para a pasta **Notas de Consumo** do Drive, o pedido vai para a aba **Pedidos** e um novo pedido (próximo número) é aberto.
6. Aba **Pedidos**: lista dos últimos pedidos fechados. Toque num pedido para abrir no Drive, baixar ou compartilhar o PDF.
7. **Relatório saiu errado?** Abra o último pedido → **Relatório errado? Excluir e refazer** (toque duas vezes para confirmar). O PDF é apagado do Drive e as notas voltam para a lista com o mesmo número de pedido. Corrija e gere de novo.
8. Para mudar o número do pedido em aberto, toque no **Nº** (ícone de lápis) no topo.
9. Aba **Extrato do Cartão**: fotografe (ou escolha da galeria) as páginas do extrato. Use **‹ ›** para mudar a ordem, **↻** para girar e a lixeira para excluir. Confira o **Pedido Nº** vinculado (vem preenchido com o pedido em aberto) e toque em **Gerar relatório do extrato**. O PDF **Extrato Cartão - Pedido Nº xxxx** vai direto para a pasta **Notas de Consumo** do Drive. Gerar de novo para o mesmo pedido substitui o arquivo; se sair errado, use **Relatório errado? Excluir do Drive**.

## Sincronização celular ⇄ computador (Google Drive)

- Configure o **mesmo Google Client ID** (⋮ → Configurações) em cada aparelho e entre com a **mesma conta Google**.
- A faixa no topo mostra a situação: **Sincronizado às hh:mm** (tudo certo), **Salvando no Drive…**, ou **Drive desconectado · toque para sincronizar**.
- Por segurança o Google libera o acesso por **1 hora**. Depois disso, ao abrir o app, **toque na faixa** para reconectar (é um toque; na maioria das vezes a janela do Google abre e fecha sozinha).
- Cada alteração é enviada ao Drive em poucos segundos. Ao voltar para o app (ou abrir em outro aparelho), ele baixa o que mudou.
- Se você alterou nos dois aparelhos sem sincronizar, o app pergunta qual versão manter.
- Os dados ficam na pasta **Notas de Consumo → _dados do app (não apagar)** do seu Drive. Não apague nem mexa nessa pasta.

**Dicas para a leitura sair certa:** nota esticada sobre fundo escuro, boa luz, sem sombra, foto de frente e enquadrando a nota inteira. Cupom muito longo: tire a foto da parte de baixo (onde estão total e data) e confira a descrição.

**Cuidado:** sem o Drive configurado, os dados ficam só no navegador do aparelho. Se limpar os dados do navegador ou trocar de celular, perde o que não foi sincronizado.
