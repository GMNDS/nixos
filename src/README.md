# Introdução

Olá pessoas, estou fazendo isso para documentar minha jornado com o NixOS, não encontrei muito conteúdo sobre ele em português, então espero me ajudar no futuro caso eu esqueça algo e talvez por ventura ajudar alguém que precise e tenha o mesmo problema. E sinceramente estou meio perdido com tudo isso, também é uma forma de organizar minhas ideias.

Nesse começo não terá uma ordem bem definida e nem sei se vou até o fim, mas pretendo. Conforme for evoluindo as informações também vão mudando, talvez no final esse texto inicial nem exista mais.

Primeiro preciso começar pelo ecosistema do Nix.

## NixOS
É uma distribuição linux não baseada em nenhuma outra e sim em Nix. Ele é puramente funcional e sua ideia principal é ser um sistema rápido e fácil de configurar e apesar da íngreme curva de aprendizado é oque acontece de fato, ele usa a linguagem Nix para configurar o sistema de forma declarativa a partir de um arquivo chamado `configuration.nix` onde você pode fazer configurações profundas e reproduzíveis do sistema operacional que inclui o comportamento do boot loader, do sistema de arquivos, de módulos do kernel, da interface gráfica, além de vários serviços como git ou ssh.

Ele também oferece reversões do sistema, atualizações atômicas e suporte multi-usuário. Na prática você consegue criar um sistema fácilmente reproduzível, sabe aquela desculpa que na minha máquina não funciona? Acredito que o NixOS resolva isso.

## Nix Language
É uma linguagem funcional, criada para ser descritiva e conveniente que instrui Nix como contruir seus pacotes, ambientes e sistemas.

## Nick Package Manager e Nixpkgs
Enquanto o Nix Package Manager é o gerenciador de pacotes do Nix, Nixpkgs é o maior repositório de pacotes Nix com mais de 100.000 pacotes.



