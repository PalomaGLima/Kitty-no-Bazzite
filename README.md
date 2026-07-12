🚀 Customização do Terminal Kitty no Bazzite

Este guia prático ensina passo a passo como instalar o terminal Kitty, configurar o Fastfetch com imagens personalizadas, desativar o banner padrão do Bazzite e customizar as cores do prompt do seu Bash.

---

## 📦 1. Instalação e Configuração Inicial

### Passo 1.1: Instalar o Kitty
Como o Bazzite é um sistema baseado em imagens atômicas (Fedora Silverblue/Kinoite), use o `rpm-ostree` para instalar pacotes diretamente no sistema:
```bash
rpm-ostree install kitty
Reinicie o sistema caso o terminal recém-instalado não apareça no seu menu imediatamente.
Passo 1.2: Gerar pasta de configuração do Fastfetch
Para fazer a pasta oculta do Fastfetch aparecer no seu diretório de configurações para que você possa modificá-la:
Bash
fastfetch --gen-config
Isso criará automaticamente a pasta ~/.config/fastfetch/ com o arquivo padrão config.jsonc lá dentro.
Passo 1.3: Desativar a tela de boas-vindas do Bazzite
O Bazzite injeta uma tela azul padrão que mascara o Fastfetch. Para desativar esse comportamento e deixar o terminal limpo:
Bash
ujust toggle-user-motd
🎨 2. Automatização e Fixação do Fastfetch
Para garantir que o Fastfetch seja carregado perfeitamente com as suas imagens e layouts customizados sem sofrer interferência das variáveis do Bazzite, adicione o comando correto na inicialização do sistema.
    1. Abra o arquivo de configuração do Bash:
       Bash
       nano ~/.bashrc
    2. Vá até o final do arquivo e cole a seguinte linha:
       Bash
       clear && env -u FASTFETCH_CONFIG fastfetch -c ~/.config/fastfetch/config.jsonc
🌈 3. Customização de Cores do Prompt (PS1)
Você pode mudar a cor clássica verde do seu prompt (nome@maquina:~$) para a cor que desejar editando a variável PS1 no seu ~/.bashrc.
Passo 3.1: Configurar a Paleta de Cores
Ainda com o arquivo ~/.bashrc aberto, cole a sua combinação favorita logo abaixo da linha do Fastfetch que adicionamos no passo anterior.
    • Opção A: Nome em Azul Negrito e Pasta em Ciano
      Bash
      export PS1="\\e[1;34m\\u@\\h\\e[0m:\\e[1;36m\\w\\e[0m\\$ "
    • Opção B: Nome em Ciano Negrito e Pasta em Azul
      Bash
      export PS1="\\e[1;36m\\u@\\h\\e[0m:\\e[1;34m\\w\\e[0m\\$ "
Passo 3.2: Salvar e Aplicar
    1. No editor Nano, pressione Ctrl + O e dê Enter para salvar o arquivo.
    2. Pressione Ctrl + X para sair do editor.
    3. Para aplicar todas as mudanças na mesma janela do terminal sem precisar reiniciá-lo, execute:
       Bash
       source ~/.bashrc
🎨 4. Tabela de Referência de Cores (Códigos ANSI)
Substitua os números dentro do padrão \\e[1;XXm (onde XX é o código da cor) para criar a sua própria identidade visual:
🔹 Cores Padrão (Tons Normais)
Código	Cor correspondente
30	⚫ Preto
31	🔴 Vermelho
32	🟢 Verde
33	🟡 Amarelo
34	🔵 Azul
35	🟣 Roxo / Magenta
36	🌐 Ciano (Azul Claro)
37	⚪ Branco
🔹 Cores de Alta Intensidade (Tons Neon/Brilhantes)
Se quiser um visual com cores muito mais vivas, utilize a série de códigos 90:
Código	Cor correspondente
90	🔘 Cinza Escuro
91	🛑 Vermelho Claro
92	🟢 Verde Claro
93	🟡 Amarelo Claro
94	🔵 Azul Claro
95	🟣 Roxo / Magenta Claro
96	🌐 Ciano Claro
97	⚪ Branco Brilhante
Dica técnica: Sempre mantenha os marcadores \\e[0m no seu PS1 para garantir que a cor do comando digitado não herde acidentalmente a cor do seu nome de usuário!
