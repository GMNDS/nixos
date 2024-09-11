# Instalação do Docker

Docker é uma ferramenta que utilizo com certa frequência já que gosto de testar vários aplicativos auto-hospedados que podem ser úteis e configurar o docker no NixOs é uma tarefa relativamente simples se for feito da maneira correta, podemos ver isso também na [documentação oficial](https://nixos.wiki/wiki/Docker) 

## Forma incorreta

O primeiro reflexo é instalar como se fosse outro pacote e fazer algo assim ou semelhante:

```nix
  environment.systemPackages = with pkgs; [
    ...
    docker
];
```

mas está errado, isso não vai funcionar como deveria e gerar vários erros ao tentar usar o docker.

## Forma correta

Para instalar o docker corretamente podemos seguir alguns passos simples:

- Habilitar docker com virtualização
- Adicionar seu usuário no grupo docker
- Se desejar habilitar Rootless habilitar
- Configuração adicional para sistema BTRFS

### Habilite o docker

Para isso basta adicionar a seguinte linha ao seu arquivo de configuração nix:

```nix
virtualisation.docker.enable = true;
```
Nesse ponto se você fizer `nixos-rebuild switch` você já conseguirá usar o docker, mas precisará usar sudo.

### Adicione seu usuário ao grupo docker

Você pode fazer isso adicionando:

```nix
users.users.<youruser>.extraGroups = [ "docker" ];
```
Caso você tenha mais configurações para seu usuário pode ficar algo asssim:
```nix
users.users.<youruser> = {
    ...
    extraGroups = ["docker"];
  };
```

Isso fará seu usuário conseguir usar comandos docker sem sudo, mas **ele ainda estará operando como root**

### Ativar Rootless
Caso o root não seja necessário para executar seus containers, você pode ativar o modo sem root adicionando a seguinte linha ao arquivo de configuração:

```nix
virtualisation.docker.rootless = {
  enable = true;
  setSocketVariable = true;
};
```

### Adicionar suporte para BTRFS
Se você estiver usando o sistema de arquivos `BTRFS` provavelmente será necessário definiir a opção storageDriver com a seguinte linha:

```nix
virtualisation.docker.storageDriver = "btrfs";
```

### Configuração final
A configuração final ficará mais ou menos assim:

```nix
...
# DOCKER CONFIGURATION
virtualisation.docker.enable = true;
users.users.GMNDS.extraGroups = [ "docker" ];
virtualisation.docker.rootless = {
  enable = true;
  setSocketVariable = true;
};
...
```

Agora só reconstruir o Nix com `sudo nixos-rebuild switch` e reiniciar o shell e/ou a máquina caso ainda não esteja consigo acessar o docker.

Além dessas configurações existem várias outras opções disponíveis que podem ser verificadas na [documentação oficial](https://nixos.wiki/wiki/Docker).
