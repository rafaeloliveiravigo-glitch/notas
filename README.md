# Notas de Consumo

App de navegador para fotografar notas, ler **data, descrição e valor total** automaticamente e gerar um **relatório em PDF** com a lista e as fotos em anexo.

- Funciona no celular e no computador, sem instalar nada.
- A leitura da nota é feita no próprio aparelho (gratuita). Na primeira vez ele baixa o "dicionário" de leitura, que demora uns segundos; depois fica guardado.
- Os dados ficam salvos no navegador do aparelho. Com o Google Drive configurado, dá para salvar a apuração no Drive e abrir em outro aparelho.

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
8. Toque em **Google Drive** → **Salvar esta apuração no Drive**. Na primeira vez:
   - Escolha sua conta Google.
   - Vai aparecer **"O Google não verificou este app"**: clique em **Continuar** (o app é seu).
   - Autorize o acesso → **Continuar**.
   - Confira no seu Drive: vai surgir a pasta **Notas de Consumo** com o arquivo da apuração.

> **Erro `origin_mismatch` ou "Acesso bloqueado":** o endereço do item 6 está diferente do endereço do app. Confira o `https://` e o nome de usuário. Depois de corrigir, a mudança pode levar alguns minutos para valer.
>
> **Erro "access_denied" / "não concluiu o processo de verificação":** faltou colocar seu e-mail em **Usuários de teste** (item 5).

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
