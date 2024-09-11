# Instalação no WSL2

Essa jornado com o NixOS começa no WSL já que atualmente estou confortável com windows mas ainda assim quero testar algo novo, e não consegui instalar como uma maquina virtual no vmware ou hyperv e não tive interesse em continuar depois de algumas horas.

A instalação foi seguindo os passos do repositório [NixOS-WSL](https://github.com/nix-community/NixOS-WSL) no Github.

Primeiro baixe o `nixos-wsl.tar.gz` do [último lançamento](https://github.com/nix-community/NixOS-WSL/releases) no repositório

Então habilite o WSL, caso não esteja habilitado
```powershell
   wsl --install --no-distribution
```

Importe o tarball para o WSL
Caso esteja no `powershell` execute
```powershell
   wsl --import NixOS --version 2 $env:USERPROFILE\NixOS\ $env:USERPROFILE\Downloads\nixos-wsl.tar.gz
```

Caso esteja no `CMD` execute
```bash
   wsl --import NixOS --version 2 %USERPROFILE%\NixOS\ %USERPROFILE%\Downloads\nixos-wsl.tar.gz
```

Isso criar uma nova distribuição WSL do `NixOS`, onde:
- `NixOS` é o nome da distribuição e você pode modificar se quiser
- `$env:USERPROFILE\NixOS\` ou `%USERPROFILE%\NixOS\`  é o diretório onde o NixOS será instalado e poderá ajusta-lo se desejar.
-  `$env:USERPROFILE\Downloads\nixos-wsl.tar.gz` ou `%USERPROFILE%\Downloads\nixos-wsl.tar.gz` é caminho do arquivo que você baixou, se for em uma pasta diferente ou foi movida deverá ajusta-lo.
Feito isso você pode executar o shell usando:
```powershell
wsl -d NixOS
```

Não esqueça de adequar o nome caso tenha o feito na importação

## Pós instalação

Depois da instalação inicial, você deve atualizar seus canais uma vez para poder usar `nixos-rebuild`:
```sh
sudo nix-channel --update
```

E você também pode tornar o NixOS sua distribuição principal com:
```powershell
wsl -s NixOS
```
