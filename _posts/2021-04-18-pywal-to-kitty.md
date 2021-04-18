---
layout: post
title:  "Add Ctrl+L clear to neoterm in neovim"
author: lucas
categories: [ linux, tutorial, customization, script ]
tags: [ pywal, wal, kitty, terminal, linux]
image: assets/images/kitty.png
description: "Como exportar cores geradas pelo pywal para o Kitty"
featured: true
hidden: false
---

Recentemente, resolvi dar uma chance a outro terminal emulator: Sai do Alacritty e comecei a usar Kitty. Porém, eu já tinha um script para converter meu esquema de cores obtidos através do pywal para o Alacritty, então resolvi adaptar o script para usá-lo com o Kitty.

#### O Script

<script src="https://gist.github.com/limeiralucas/c882349a7f20b11c42ab6da288452dcc.js"></script>

### Como usar

Baixe o script, dê permissão de execução `chmod +x wal-to-kitty.sh` e execute-o indicando um arquivo de output (o arquivo precisa existir):
```
# Caso o arquivo não exista
touch path/to/file.conf

# Execute o script
./wal-to-kitty.sh path/to/file.conf
```

Após isso, basta incluir o arquivo na sua configuração do Kitty, inserindo essa linha em sua atual configuração:

```
include path/to/file.conf
```

Espero ter ajudado! :D



