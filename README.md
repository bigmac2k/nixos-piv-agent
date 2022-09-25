# PIV-Agent

Nix flake to install [piv-agent](https://github.com/smlx/piv-agent) on nixos.

It provides the piv-agent package and a module to enable the service.

## State

This is currently work in progress.

## Using the flake

`configuration.nix`
```
  inputs = {
    piv-agent.url = "git+ssh://git@sven.cc:222/scm/nix-piv-agent";
  };

  outputs = inputs @ {
    piv-agent,
    ...
  }:
  let
    system = "x86_64-linux";
  in {
    modules = [ piv-agent.nixosModules.${system}.piv-agent ];
    services = {
      pcscd.enable = true;
      piv-agent.enable = true;
    };
  }
```
