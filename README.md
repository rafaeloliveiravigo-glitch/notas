# Notas de Consumo

App de navegador para fotografar notas, ler **data, descrição e valor total** automaticamente e gerar um **relatório em PDF** com a lista e as fotos em anexo.

- Funciona no celular e no computador, sem instalar nada.
- A leitura da nota é feita no próprio aparelho (gratuita). Na primeira vez ele baixa o "dicionário" de leitura, que demora uns segundos; depois fica guardado.
- Os dados ficam salvos no navegador do aparelho. Com o Google Drive configurado, dá para salvar a apuração no Drive e abrir em outro aparelho.

---

## Parte 1 — Colocar o app no ar (GitHub Pages) · ~10 min

1. Crie a conta em **github.com** (botão *Sign up*). Escolha bem o nome de usuário: ele vai aparecer no endereço do app (`https://SEU-USUARIO.github.io/notas/`).
2. Já logado, clique no **+** (canto superior direito) → **New repository**.
   - *Repository name*: `notas`
   - Marque **Public** (o GitHub Pages gratuito exige repositório público. Só o código fica público; suas notas **não** vão para o GitHub).
   - Clique em **Create repository**.
3. Na página do repositório, clique no link **uploading an existing file**.
4. Arraste para a página **todos os arquivos** da pasta do app: `index.html`, `manifest.webmanifest`, `icon-192.png`, `icon-512.png` e `README.md`. Clique em **Commit changes**.
5. Vá em **Settings** (aba do repositório) → **Pages** (menu da esquerda).
   - Em *Source*, escolha **Deploy from a branch**.
   - Em *Branch*, escolha **main** e a pasta **/(root)**. Clique em **Save**.
6. Aguarde 1 a 2 minutos e recarregue a página. Vai aparecer: *"Your site is live at https://SEU-USUARIO.github.io/notas/"*.
7. Abra esse endereço no celular.
   - **Android (Chrome):** menu ⋮ → *Adicionar à tela inicial* / *Instalar app*.
   - **iPhone (Safari):** botão compartilhar → *Adicionar à Tela de Início*.

Pronto: o app já funciona (sem o Drive). Para atualizar o app no futuro, é só subir o `index.html` novo pelo mesmo caminho (*Add file → Upload files*).

---

## Parte 2 — Ligar o Google Drive (opcional) · ~15 min

O app precisa de um "Client ID" do Google para pedir permissão de salvar no seu Drive. É gratuito. O app só enxerga os arquivos que ele mesmo criou (pasta **Notas de Consumo**), não o resto do seu Drive.

1. Acesse **console.cloud.google.com** com a sua conta Google.
2. No topo, clique no seletor de projetos → **Novo projeto** → nome `Notas de Consumo` → **Criar**. Confira se o projeto novo ficou selecionado no topo.
3. **Ativar a API do Drive:** menu ☰ → **APIs e serviços** → **Biblioteca** → pesquise **Google Drive API** → **Ativar**.
4. **Tela de consentimento:** menu ☰ → **Google Auth Platform** (ou *APIs e serviços → Tela de permissão OAuth*) → **Começar**.
   - Nome do app: `Notas de Consumo`; e-mail de suporte: o seu.
   - Público: **Externo**.
   - Dados de contato: o seu e-mail. Aceite os termos e **Criar**.
5. **Público / usuários de teste:** no menu da esquerda, **Público** → em *Usuários de teste*, clique **Add users** e coloque o seu Gmail (e de quem mais for usar). Salve.
6. **Criar o Client ID:** menu da esquerda **Clientes** → **Criar cliente**.
   - Tipo de aplicativo: **Aplicativo da Web**.
   - Nome: `Notas web`.
   - Em **Origens JavaScript autorizadas**, clique *Adicionar URI* e coloque: `https://SEU-USUARIO.github.io` (sem `/notas` e sem barra no final).
   - **Criar**. Copie o **ID do cliente** (termina em `.apps.googleusercontent.com`).
7. No app: menu **⋮** → **Configurações** → cole em **Google Client ID** → **Salvar**.
8. Toque em **Google Drive** → **Salvar esta apuração no Drive**. Na primeira vez o Google mostra um aviso "O Google não verificou este app": clique em **Continuar** (o app é seu). Autorize o acesso.

> Se aparecer erro `origin_mismatch`: o endereço do passo 6 está diferente do endereço do app. Confira `https://` e o nome de usuário. A alteração pode levar alguns minutos para valer.

---

## Como usar no dia a dia

1. **Fotografar nota** (ou **Galeria**, que aceita várias fotos de uma vez).
2. O app lê a nota e preenche os campos. Os **campos em amarelo** foram lidos automaticamente: confira e corrija se precisar. Se a foto ficou de lado, toque em **Girar**.
3. **Salvar.** A nota entra na lista e o total é atualizado. Toque em uma nota para editar ou excluir.
4. Toque no nome da apuração (topo) para renomear, ex.: `Despesas Setembro/2026 – Obra X`.
5. No fim do período: **Gerar relatório** → *Baixar PDF*, *Compartilhar* (WhatsApp, e-mail) ou *Salvar PDF no Google Drive*.
6. Depois de enviar o relatório: menu **⋮** → **Iniciar nova apuração**.

**Dicas para a leitura sair certa:** nota esticada sobre fundo escuro, boa luz, sem sombra, foto de frente e enquadrando a nota inteira. Cupom muito longo: tire a foto da parte de baixo (onde estão total e data) e confira a descrição.

**Cuidado:** os dados ficam no navegador. Se você limpar os dados do navegador ou trocar de celular, perde o que não foi salvo. Salve no Drive (ou em *⋮ → Salvar backup no aparelho*) de tempos em tempos.
