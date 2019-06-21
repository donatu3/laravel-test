## 使い方

docker-compose up -d

## 環境
・windows10
・Vagrant 1.9.8
・VirtualBox 5.1.30 r118389 (Qt5.6.2)

vagrantとvirtualboxは結構古いから新しいのでも大丈夫だと思う。
docker環境があるならvagrantとかは不要そう。

## できるまでにやったこと

・vagrantの設定（
以下参考、既に入ってたので必要な部分だけ）
https://qiita.com/yasushi00/items/0926b65ab0abd8f20e21


```
vagrant box add bento/centos-7.3  --provider virtualbox
cd /path/to/workdir
vagrant init bento/centos-7.3
```

Vagrantfileをipの記載されている部分のコメントアウト外して、ip変更
```
  # config.vm.network "private_network", ip: "192.168.33.10"
     ↓
  config.vm.network "private_network", ip: "192.168.100.10"
```

起動（初回は数分くらいかかる）

```
vagrant up
```

マウント云々でエラーでたので対処

```
vagrant ssh
sudo yum -y update kernel
exit
vagrant reload
```

マウントできた(ググれば色々でてくるので同じ現象なったら頑張る)


vagrantにdockerとか入れる
```
vagrant ssh
sudo yum update
sudo yum -y install docker
sudo service docker start
sudo systemctl enable docker
sudo curl -L "https://github.com/docker/compose/releases/download/1.22.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

あとはこの辺見ながら

https://re-engines.com/2019/03/14/laravel%E3%81%AE%E9%96%8B%E7%99%BA%E7%92%B0%E5%A2%83%E3%82%92docker-compose%E3%81%A7%E4%B8%80%E3%81%8B%E3%82%89%E6%A7%8B%E7%AF%89%E3%81%97%E3%81%A6%E3%81%BF%E3%82%8B/