---
layout: post
title: "Uma primeira vez para o open source"
description: 
headline: 
modified: 2015-04-21
category: coding
tags: [ruby rails open-source coding]
comments: true
mathjax: 
---

Contribuir para algum projeto open source é uma das coisas que eu sempre deixei pra
fazer amanhã/semana que vem/nunca. Eu sempre admirei muito a iniciativa de quem se 
empenha pra manter os projetos que eu e muitas outras pessoas utilizamos no dia
a dia, mas por um misto de insegurança com o a qualidade do próprio código e um
pouco de preguiça também, as contribuições sempre ficaram em segundo plano.

Outro ponto importante, onde eu acho que todo mundo que um dia resolveu
contribuir com algum projeto já chegou é não saber exatamente como começar.
Muitos projetos incluem guidelines para pessoas que querem contribuir e 5
minutos de google-fu vão te trazer toneladas de videos sobre pessoas que já
contribuíram pra varios projetos extremamente conceituados contando um pouco
sobre como começaram, mas é difícil encontrar referências sobre o processo em
si. Alguém documentando todas as falhas e sucessos do caminho enquanto avança.

O objetivo principal desse blog é esse.

Faz uma semana que eu comecei a enviar contribuições. As duas primeiras foram
para duas roles de [Ansible](http://www.ansible.com/home), que pra quem não
conhece, é um sistema de provisionamento de servidores (uma maneira automatizada
de instalar toda a tralha que faz suas apps rodarem). As duas ainda estão
sentadas lá esperando review. Um começo morno.

Durante a semana, enquanto eu estava organizando as coisas para o blog, eu 
comecei a procurar um sistema de comentários open source como alternativa ao
Disqus e cheguei até a pensar em criar um próprio até encontrar o
[Juvia](https://github.com/phusion/juvia).

O projeto estava sem mantenedor, e parado há bastante tempo. Olhando um pouco do
código, deu pra perceber que o projeto era organizado e os testes faziam
sentido, então baixei a base e pra minha surpresa todos os testes passavam. Ele
ainda estava usando Rails 3.2, então eu tinha encontrado minha missão.

*Let's give this motherfucker some love*

O objetivo final era deixar o projeto rodando com rails 4.2 e ruby 2.2 com todos
os testes ainda passando.

A primeira coisa que eu fiz foi já mudar logo tudo pra última versão e ir consertando os
testes.

Bad move, bro.

Tudo quebrou e uma meia hora depois eu percebi que o caminho não era aquele,
então voltei para o Ruby 1.9.3, subi somente a versão do Rails para 4.0 e usei o
[Guia de Upgrades do Rails](http://edgeguides.rubyonrails.org/upgrading_ruby_on_rails.html)
pra ajustar as coisas *the right way* e uma vez que tudo passou, passei para o
Rails 4.1 e assim em diante.

Entre as coisas interessantes aprendidas no processo:

- Usar `object.method(:method_name).source_location` te poupa MUITO tempo
  debugando, principalmente quando o código não é seu (esse na verdade eu já
  conhecia, mas usei várias vezes durante a conversão).
- [Capybara Screenshot](https://github.com/mattheworiordan/capybara-screenshot)
  faz o mesmo para quando você está debugando testes de integração com
  javascript habilitado.
- Usar [Transpec](http://yujinakayama.me/transpec/) para converter testes feitos
  com sintaxe antiga do [Rspec](http://rspec.info/) funciona tão bem quanto
  sanduiche de Paçoquita Cremosa com Nutella (se você não gosta sanduíche de
  Paçoquita Cremosa com Nutella, desculpe, mas você não tem muitos motivos pra
  viver).

Tudo feito, enviei o pull request e esperava que ele ficasse sentado no limbo
como os outros, mas para a minha surpresa, na manhã seguinte, ele recebeu o
merge e um agradecimento do dono do repositório. O sentimento de missão cumprida
é sensacional.

Ele ainda foi atencioso em alertar que eu havia colocado a secret key do Devise 
no versionamento de código e corrigiu após fazer o merge.

E [aqui está o danado](https://github.com/phusion/juvia/pull/67).

Se você encontrar algum problema, dê um grito e abra uma issue.
