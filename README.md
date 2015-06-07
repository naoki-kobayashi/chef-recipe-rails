Chef Recipes of Rails
=====================

## Dependency

* VirtualBox: 4.3.20
* Vagrant: 1.7.2
* Cmder: 1.1.4.1
* Ubuntu: 14.04
* ChefDK: 0.6.0
* Ruby: 2.1.5
* Rails: 4.2.0

## Installation

### Git

[Vagrantfile](https://www.vagrantup.com)と[ChefDK](https://ownloads.chef.io/chef-dk/)をダウンロードします。
(OSが`32bit`の場合は`box_url`を`ubuntu-14.04-i386_chef`に変更して下さい。)

```
$ git clone https://github.com/naoki-kobayashi/chef-recipe-rails.git
$ cd ./chef-recipe-rails
```

berkshelfで`cookbook`をダウンロードします。

```
$ berks vendor 
```

### Vagrant

マシンを構築するとChefのRecipeで`Ruby`の開発環境が構築されます。

```
$ vagrant up
```

ChefのRecipeを再実行するには`provision`コマンドを利用すればいいはずですが、エラーが発生するので再起動します。

```
$ rm .vagrant/machines/default/virtualbox/synced_folders 
$ vagrant reload --provision
```

### Bundler

仮想マシンにログインします。

```
$ vagrant ssh
```

Railsをインストールして、アプリケーションを作りましょう。

```
vagrant@vagrant:~$ bundle config --global jobs 4
vagrant@vagrant:~$ gem install rails --no-rdoc --no-ri
vagrant@vagrant:~$ rails new rails-example
vagrant@vagrant:~$ cd rails-example
vagrant@vagrant:~$ rails server --binding 0.0.0.0
```

`http://192.168.33.30:3000/`にアクセスすると`Welcome`が表示されます。

## License

* MIT
