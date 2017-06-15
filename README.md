# logstash 在线实验环境

## 软件简介

Logstash是一种可用于收集，处理和转发事件和日志消息的工具。集合是通过可配置的输入插件，包括原始插座/分组通信，文件拖尾和几个消息总线客户端完成的。一旦输入插件收集数据，就可以通过修改和注释事件数据的任何数量的过滤器进行处理。最后，事件路由到输出插件，可以将事件转发到各种外部程序，包括Elasticsearch，本地文件和多个消息总线实现。

所属类别是企业应用

License:Elasticsearch

## 软件官网

https://wikitech.wikimedia.org/wiki/Logstash

## Dockerfile 使用方法

### 如何使用
使用命令行配置启动Logstash

如果您需要使用命令行中提供的配置运行logstash，则可以使用logstash映像，如下所示：
```
$ docker run -it --rm logstash -e 'input { stdin { } } output { stdout { } }'
```
启动Logstash配置文件

如果您需要使用配置文件（logstash.conf位于当前目录中）运行logstash，则可以使用logstash映像，如下所示：
```
$ docker run -it --rm -v "$PWD":/config-dir logstash -f /config-dir/logstash.conf
```
使用a Dockerfile

如果要使用预烘焙配置文件生成Logstash映像，建议使用a Dockerfile：
```
FROM logstash

COPY logstash.conf /some/config-dir/

CMD ["-f", "/some/config-dir/logstash.conf"]
```
然后，使用以下内容构建docker build -t my-logstash .和部署：
```
$ docker run -d my-logstash
```
## 资源链接

- https://wikitech.wikimedia.org/wiki/Logstash
