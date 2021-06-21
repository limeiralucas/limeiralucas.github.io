---
layout: post
title:  "Como usar chaves SSH diferentes para diferentes hosts git"
author: lucas
categories: [ tutorial, git, security]
tags: [ git, ssh, work, security, linux, unix]
image: assets/images/security-lock.webp
description: "Quer isolar cada chave SSH para repositórios pessoais e repositórios do trabalho? Eis a dica! ;D"
featured: true
hidden: false
---

Todos os nós *developers* com certeza temos a nossa conta em um serviço de repositórios git, como o github, gitlab, bitbucket, etc. E, provavelmente, temos uma chave SSH configurada nesses serviços para segurança e também facilidade (ninguém gosta de ter que ficar digitando senha a cada pull, não é? 😝). Mas não é seguro utilizarmos a mesma chave SSH para múltiplos serviços, por exemplo, a sua conta do github pessoal e da empresa compartilhando a mesma chave, pois, caso ocorra o vazamento dessa chave, não apenas os seus repositórios pessoais estarão comprometidos, assim como os do seu trabalho.

Como uma alternativa segura, podemos ter uma chave SSH por *host* ou até mesmo conta. E fazer isso é bem simples como vocês podem ver a seguir!

### Gerando uma chave SSH
Vamos considerar o seguinte cenário: você já tem uma chave SSH associada à sua conta do Github pessoal, mas agora deseja criar uma diferente para acesso aos repositórios da empresa. Então, primeiro vamos criar uma nova chave SSH:

![Gerando a chave ssh](/assets/images/ssh-code01.gif)

**Lembrete:** Importante utilizar uma *passphrase* forte para maior segurança!

### Configurando a relação host-chave
Agora que temos a nossa nova chave, vamos associá-la ao *host* do utilizado pelos repositórios do trabalho. Basta acessar a pasta `.ssh` no seu diretório *home* e nela abrir o arquivo `config`.

Nele, você fará uma nova configuração da seguinte maneira (utilizando os valores correspondentes as localizações e nomes de arquivos da sua máquina):

```config
Host github-work
    HostName github.com
    User git
    AddKeysToAgent yes
    UseKeychain yes
    IdentityFile ~/.ssh/github-work
```

Pronto! Agora está tudo configurado. Para usar a sua chave, ao clonar um repositório, ao invés de `git@github.com:youruser/repo.git`, você vai substituir pelo host que configurou no arquivo `config`, no caso do exemplo acima ficaria: `git@github-work:youruser/repo.git`. Dessa forma será utilizada a chave SSH correspondete a este *host*.

Espero ter ajudado e até a próxima! 😁
