---
layout: post
title: "A day in the life of a programmer(How I fixed the pika.exceptions.ConnectionClosed error) "
date:   2017-02-07 23:10:00
---

I am a huge [rabbitmq](https://www.rabbitmq.com/) fanboy! it helps me be a better node wrangler. However today I decided to ditch node to complete a synchronous task. Although Freshdesk made me comfortable with ruby, for a change I chose to do it with python. Shivasurya had warned me against choosing python because of its notorious indentations(at least for newbies). I was up for the challenge and read up the Rabbitmq docs for python and it was pretty straight-forward. With an air of confidence and faith in Stackoverflow I ventured into the recommended pika package for connecting rabbitmq with python!


Rabbitmq makes me feel at home! Our interaction happens on a daily basis. However when I tried to run the following simple hello world snippet, the pika package threw the `pika.exceptions.ConnectionClosed error`, this is the code that was used and it was pretty straight forward. The  userid, Ip address and rabbitmq configurations were good to go, still the error persisted.


<script src="https://gist.github.com/anonymous/f1d068a77e7bab32a01b1c66a4d56c4e.js"></script>

Like every confused developed I sunk in hours on github issues , stack overflow and the Pika docs to fix a trivial issue! Finally A [stack overflow answer](http://stackoverflow.com/a/35716539) had the right solution for my problem!

If you too have landed here confused, don't worry, adding a **socket_timeout** to the pika connection parameters would save you loads of time and effort! Here is the code that fixed the `pika.exceptions.ConnectionClosed error`

```
import pika

credentials = pika.PlainCredentials('rabbitmq_uid', 'rabbitmq_passwd')
parameters = pika.ConnectionParameters('12.26.212.172',
                                   5672,
                                   '/',
                                   credentials,
                                   socket_timeout=2)
connection = pika.BlockingConnection(parameters)

channel = connection.channel()

channel.queue_declare(queue='hello')

channel.basic_publish(exchange='',
                  routing_key='hello',
                  body='Hello World!')
print(" [x] Sent 'Hello World!'")
connection.close()
```
