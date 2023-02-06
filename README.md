# Recuperando pen-drive no linux

## Descobrindo a unidade do sistema para o pendrive

```sh
lsblk | grep "^sd*"
```

## Removendo blocos defeituosos

> IMPORTANTE: substituir o "/sda" com a unidade do sistema para o pendrive

```sh
sudo fsck /dev/sda
```

> IMPORTANTE: substituir o "/sda" com a unidade do sistema para o pendrive

## Zerando o pen-drive

> IMPORTANTE: substituir o "/sda" com a unidade do sistema para o pendrive

```sh
sudo dd if=/dev/zero of=/dev/sda
```

Monitorando o processo 

```sh
sudo watch -n 1 "pgrep -l ^dd$ | cut -d ' ' -f 1 | xargs kill -USR1"
```

## Criando nova tabela de partição DOS

> IMPORTANTE: substituir o "/sda" com a unidade do sistema para o pendrive

```sh
sudo fdisk /dev/sda
```

## Definindo sistema de arquivos

> IMPORTANTE: substituir o "/sda" com a unidade do sistema para o pendrive

```sh
sudo mkfs.msdos -I -f 2 /dev/sda
```

