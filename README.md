Packer CSD
==========

## Descripción

Script para generar una máquina Virtual Box con algunas herramientas para un ambiente de IC.

## Requerimientos

- Ruby 2.+

## Cómo generar la máquina Virtual?

### Paso 1: Descargar módulos externos para el provisionamiento
	$ gem install librarian-puppet
    $ librarian-puppet install --path provisioning/modules-vendor

### Paso 2: Generar la máquina virtual

Puedes generar la máquina virtual de 2 maneras diferentes: Vagrant o Packer

#### Generar la máquina con vagrant (instalar previamente Vagrant)
	$ vagrant up

#### Generar la máquina con Packer (instalar previamente Packer)
	$ gem build ubuntu.json

## Qué contiene?
- JDK
- Jenkins (Puerto 8008)
- Apache
- Subversion (Puerto 80)
- RVM, Ruby

## Development

Instalar puppet:

	https://docs.puppetlabs.com/guides/install_puppet/pre_install.html

Verificar la sintaxis de puppet

	$ puppet parser validate provisioning/manifests/init.pp

Mostrar que va a hacer puppet pero sin cambiar nada

	$ puppet apply –-noop --modulepath=modules:modules-vendor manifests/init.pp

Reprosionar con vagrant luego del primer "vagrant up"

	$ vagrant reload --provision

Verificar el template de packer

	$ packer validate ubuntu-server.json