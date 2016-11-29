# Ejercicios tema 2 CC

>Autor: Juan Pablo González Casado

>Fecha: 25/11/2016

## Ejercicio 1
#### Instalar chef-solo en la máquiina virtual que vayamos a usar:

1. Creamos una cuenta en AWS.

2. Iniciamos Ubuntu Server 14 e instalamos Ruby
  ```
  sudo apt-get install ruby1.9.1 ruby1.9.1-dev rubygems
  ```

3. Instalamos chef de la manera mas rápida:

  *curl -L https://www.opscode.com/chef/install.sh | sudo bash*

4. Creamos el directorio para la receta de emacs

  *mkdir -p chef/cookbooks/emacs/recipes*

5. Dentro de el creamos el archivo *default.rb* con el siguiente contenido:

  ```
  package 'emacs'
  directory '/home/ubuntu/Facultad'
  file "/home/ubuntu/Facultad/LEEME" do
  	owner "ubuntu"
  	group "ubuntu"
  	mode 00544
  	action :create
  	content "Directorio para documentos de la facultad"
  end
  ```
  *Este archivo contiene la receta para instalar emacs, crear un directorio y crear un archivo dentro del directorio.*

6. Dentro del directorio de chef creamos el archivo *node.json*, que contendrá una refrencia a la receta anterior.

  ```
  {
	"run_list": [ "recipe[emacs]" ]
  }
  ```
7. También creamos el archivo *solo.rb*:

  ```
  file_cache_path "/home/ubuntu/chef"
  cookbook_path "/home/ubuntu/chef/cookbooks"
  json_attribs "/home/ubuntu/chef/node.json"
  ```
8. Finalmente ejecutamos:

  ```
  sudo chef-solo -c solo.rb
  ```

## Ejercicio 2