Comandos do Git e GitHub!
==========================

### Branch
Exibe todas as branches e a branch atual sinalizado com "*":
```sh
$ git branch 
  * master
```

Lista as branches remotas origin/master, onde **origin** é a branch remota e **master** branch do remoto:
```sh
$ git branch -r
  origin/HEAD -> origin/master
  origin/master
```
Lista as branches remotas e locais:
```sh
$ git branch -a
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/master
```
Exibe para qual commit a branch está apontando:
```sh
$ git branch -v
* master 44f6c4a Adicionado arquivo readme.txt
```

Lista os commits para as quais as branches remotas estão apontando:
```sh
$ git branch -r -v
  origin/HEAD   -> origin/master
  origin/master 44f6c4a Adicionado arquivo readme.txt
```



---
### Status
O comdo exibe que o arquivo está sendo rastreado.
```sh
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```

### Diff
Exibe as diferenças entre o arquivo alterado não rastreado (não está na stage) e o que foi comitado anteriormente:
```sh
$ git diff
diff --git a/index.html b/index.html
index cc72e3d..b55bebd 100644
--- a/index.html
+++ b/index.html
@@ -8,7 +8,7 @@
 <script src="principal.js"></script>
 <title>Móveis Ecológicos</title>
 </head>
-<body>
+<body onload="trocaBanner();">
 <h1>Móveis Ecológicos S. A.</h1>
 <h2 id="mensagem"></h2>
 <ul>
```

> **Note:**
O git diff não poderá ser utilizado para arquivos novos, que ainda
não estão sendo rastreados pelo Git (ou seja, que ainda não tiveram o
primeiro git add executado).

É possível mostrar as diferenças entre os arquivos na área de stage e a
última versão que foi comitada utilizando a opção --staged:
```sh
$ git diff --staged
diff --git a/index.html b/index.html
index cc72e3d..b55bebd 100644
--- a/index.html
+++ b/index.html
@@ -8,7 +8,7 @@
 <script src="principal.js"></script>
 <title>Móveis Ecológicos</title>
 </head>
-<body>
+<body onload="trocaBanner();">
 <h1>Móveis Ecológicos S. A.</h1>
 <h2 id="mensagem"></h2>
 <ul>
```

### Desfazendo mudanças

O comando **git checkout** desfaz as alterações ainda não rastreadas,
ou seja, que ainda não estão na área de stage, voltando ao conteúdo anterior do arquivo.
```sh
$ git checkout -- index.html
```

Se quisermos apenas remover da área de stage a mudança efetuada no arquivo index.html, preservando o arquivo modificado, devemos executar:
```sh
$ git reset -- index.html
Unstaged changes after reset:
M       index.html
```

Retira todos os arquivos da área de stage e desfaz todas as alterações nesses arquivos. No fim das contas, o repositório fica exatamente no estado que estava no último commit.
```sh
$ git reset --hard
HEAD is now at 238f734 Movendo principal.js.
```

Desfazendo mudanças já comitadas
```sh
$ git revert --no-edit a0139c6
[master 2d85a0b] Revert "Adicionando texto peculiar."
 1 file changed, 1 deletion(-)
```

>**Note**: Em vez de passar o código do último commit como parâmetro para o git revert, poderíamos ter utilizado HEAD que, no nosso caso, aponta
para o último commit.

Desfazendo os commits com o comando **git reset --hard ID_commit**
```sh
$ git log --oneline
2d85a0b Revert "Adicionando texto peculiar."
a0139c6 Adicionando texto peculiar.
238f734 Movendo principal.js.
2e3cff7 Renomeando CSS.
66196bd Removendo página de produtos.
94de6c7 Página de produtos.
00ea320 Diminuindo intervalo de troca de banner.
e775991 Banner ao abrir pagina.
dbdd784 Inserindo arquivo principal.js
904bf32 Script de troca de banner.
02b79e7 Inserindo titulo e diminuindo tamanho da pagina.
4c17ba5 Commit inicial

maycon@maycon-PC MINGW64 ~/GitHub/moveis (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   index.html

no changes added to commit (use "git add" and/or "git commit -a")

maycon@maycon-PC MINGW64 ~/GitHub/moveis (master)
$ git commit -am "Comendo erro no index.html"
[master 86c9a98] Comendo erro no index.html
 1 file changed, 1 insertion(+), 1 deletion(-)

maycon@maycon-PC MINGW64 ~/GitHub/moveis (master)
$ git log --oneline
86c9a98 Comendo erro no index.html
2d85a0b Revert "Adicionando texto peculiar."
a0139c6 Adicionando texto peculiar.
238f734 Movendo principal.js.
2e3cff7 Renomeando CSS.
66196bd Removendo página de produtos.
94de6c7 Página de produtos.
00ea320 Diminuindo intervalo de troca de banner.
e775991 Banner ao abrir pagina.
dbdd784 Inserindo arquivo principal.js
904bf32 Script de troca de banner.
02b79e7 Inserindo titulo e diminuindo tamanho da pagina.
4c17ba5 Commit inicial

maycon@maycon-PC MINGW64 ~/GitHub/moveis (master)
$ git reset --hard 2d85a0b
HEAD is now at 2d85a0b Revert "Adicionando texto peculiar."

maycon@maycon-PC MINGW64 ~/GitHub/moveis (master)
$ git log --oneline
2d85a0b Revert "Adicionando texto peculiar."
a0139c6 Adicionando texto peculiar.
238f734 Movendo principal.js.
2e3cff7 Renomeando CSS.
66196bd Removendo página de produtos.
94de6c7 Página de produtos.
00ea320 Diminuindo intervalo de troca de banner.
e775991 Banner ao abrir pagina.
dbdd784 Inserindo arquivo principal.js
904bf32 Script de troca de banner.
02b79e7 Inserindo titulo e diminuindo tamanho da pagina.
4c17ba5 Commit inicial
```





sfasd

----


# Dillinger

Dillinger is a cloud-enabled, mobile-ready, offline-storage, AngularJS powered HTML5 Markdown editor.

  - Type some Markdown on the left
  - See HTML in the right
  - Magic

Markdown is a lightweight markup language based on the formatting conventions that people naturally use in email.  As [John Gruber] writes on the [Markdown site][df1]

> The overriding design goal for Markdown's
> formatting syntax is to make it as readable
> as possible. The idea is that a
> Markdown-formatted document should be
> publishable as-is, as plain text, without
> looking like it's been marked up with tags
> or formatting instructions.

This text you see here is *actually* written in Markdown! To get a feel for Markdown's syntax, type some text into the left window and watch the results in the right.

### Version
3.0.2

### Tech

Dillinger uses a number of open source projects to work properly:

* [AngularJS] - HTML enhanced for web apps!
* [Ace Editor] - awesome web-based text editor
* [Marked] - a super fast port of Markdown to JavaScript
* [Twitter Bootstrap] - great UI boilerplate for modern web apps
* [node.js] - evented I/O for the backend
* [Express] - fast node.js network app framework [@tjholowaychuk]
* [Gulp] - the streaming build system
* [keymaster.js] - awesome keyboard handler lib by [@thomasfuchs]
* [jQuery] - duh

And of course Dillinger itself is open source with a [public repository][dill]
 on GitHub.

### Installation

You need Gulp installed globally:

```shnode app
$ npm i -g gulp
```

```sh
$ git clone [git-repo-url] dillinger
$ cd dillinger
$ npm i -d
$ mkdir -p public/files/{md,html,pdf}
$ gulp build --prod
$ NODE_ENV=production node app
```

### Plugins

Dillinger is currently extended with the following plugins

* Dropbox
* Github
* Google Drive
* OneDrive

Readmes, how to use them in your own application can be found here:

* [plugins/dropbox/README.md] [PlDb]
* [plugins/github/README.md] [PlGh]
* [plugins/googledrive/README.md] [PlGd]
* [plugins/onedrive/README.md] [PlOd]

### Development

Want to contribute? Great!

Dillinger uses Gulp + Webpack for fast developing.
Make a change in your file and instantanously see your updates!

Open your favorite Terminal and run these commands.

First Tab:
```sh
$ node app
```

Second Tab:
```sh
$ gulp watch
```

(optional) Third:
```sh
$ karma start
```

### Todos

 - Write Tests
 - Rethink Github Save
 - Add Code Comments
 - Add Night Mode

License
----

MIT


**Free Software, Hell Yeah!**

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does it's job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)


   [dill]: <https://github.com/joemccann/dillinger>
   [git-repo-url]: <https://github.com/joemccann/dillinger.git>
   [john gruber]: <http://daringfireball.net>
   [@thomasfuchs]: <http://twitter.com/thomasfuchs>
   [df1]: <http://daringfireball.net/projects/markdown/>
   [marked]: <https://github.com/chjj/marked>
   [Ace Editor]: <http://ace.ajax.org>
   [node.js]: <http://nodejs.org>
   [Twitter Bootstrap]: <http://twitter.github.com/bootstrap/>
   [keymaster.js]: <https://github.com/madrobby/keymaster>
   [jQuery]: <http://jquery.com>
   [@tjholowaychuk]: <http://twitter.com/tjholowaychuk>
   [express]: <http://expressjs.com>
   [AngularJS]: <http://angularjs.org>
   [Gulp]: <http://gulpjs.com>
   
   [PlDb]: <https://github.com/joemccann/dillinger/tree/master/plugins/dropbox/README.md>
   [PlGh]:  <https://github.com/joemccann/dillinger/tree/master/plugins/github/README.md>
   [PlGd]: <https://github.com/joemccann/dillinger/tree/master/plugins/googledrive/README.md>
   [PlOd]: <https://github.com/joemccann/dillinger/tree/master/plugins/onedrive/README.md>


