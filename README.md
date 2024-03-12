# Realizando comparações com `git diff` 

O comando `git diff` é uma ferramenta essencial no Git, sendo usado para visualizar as diferenças entre duas versões de um arquivo ou entre duas branches no repositório Git, arquivos ou inputs. Esse comando de comparação é uma ferramenta poderosa para entender as alterações feitas em um projeto e para verificar o estado do seu código antes de fazer um commit ou mesclagem de _branches_.
<br/>
O comando em questão, o `git diff`, possuí diversas funcionalidades, sendo elas:
- Comparação entre arquivos
- Comparação de binários
- Comparação entre _branches_, _commits_ e _merges_
- Visualização de alterações

Agora que foi mostrado sobre as principais funcionalidades, será demonstrado e exemplificado os tópicos.

## Funcionamento das áreas

Antes de tudo, vamos primeiramentes explicar os contextos de arquivos que existem dentro do Git, isto é, como ele trabalha as alterações internamente:

![git diff img](https://github.com/GuilhermeBley/dio-git-15edi-explanation/assets/69880922/e4f8f2ba-1a5f-42d3-87b3-66aee8949ba2)

Como pode ser visto na imagem, o Git possuí diversas fontes comparativas para executar a comparação do código. Comecando pelo _HEAD_, ele basicamente é um _commit_ anterior aos arquivos atuais. Já o _HEAD~{n}_ específica um comando antepenúltimo, podendo navegar entre os últimos _commits_.
Portanto, enquanto _HEAD_ se refere ao commit atual, _HEAD~_ se refere ao commit pai desse commit atual. Isso pode ser útil para acessar commits anteriores, especialmente ao navegar pela história do projeto ou ao realizar operações como git diff, git checkout, entre outras.
<br/>
Seguindo adiante na imagem, podemos indentificar outros dois importantes quadrantes, que é o `Index` e a `Working Tree`. o `Index` é basicamente uma área intermediária entre o _Working Directory_ e o próximo _commit_. Ele é onde você prepara as modificações que deseja incluir no próximo _commit_, sendo também conhecida como _Staging Area_. Agora sobre o _Working Tree_, ela é o diretório do atual do sistema de arquivos onde os arquivos do projeto estão contidos, sendo as modificações feitas nele não adicionadas ao _commit_, permanecendo somente na máquina local.

## Comparação entre arquivos

Primeiramente, vamos simular que vai ser criado o seguinte arquivo, sendo ele comitado para a _branch master_:

```
## arquivo.txt

meu arquivo texto
```

E agora, vamos fazer a seguinte alteração nele:

```
## arquivo.txt

meu arquivo texto alterado
```

Para comparar especificamente um arquivo com `git diff`, deve-se especificar o caminho do arquivo que vai ser compararado, lembrando que ao utilizar o comando `diff` sem conter nada em _stage_, ele vai coletar da `HEAD`. Como pode ser visto na seguinte sintaxe:

`git diff arquivo.txt`

demonstrando o seguinte _out put_:
```
index 6f78ec0..e190bdc 100644
--- a/arquivo.txt
+++ b/arquivo.txt
@@ -1 +1 @@
-meu arquivo texto
\ No newline at end of file
+meu arquivo texto alterado
```

O resultado apresentado contém diversas informações importantes, começando por `index 6f78ec0..e190bdc 100644`, esta linha fornece informações sobre os hashes SHA-1 dos commits que representam as versões antiga e atual do arquivo arquivo.txt. Sendo o `6f78ec0` o hash do commit anterior e o `e190bdc` é o hash do commit atual. A parte `--- a/arquivo.txt +++ b/arquivo.txt` indica o início e o fim da seção que mostra o estado anterior e o atual do arquivo `arquivo.txt`. Seguindo em frente, pode ser visto `@@ -1 +1 @@`, que é basicamente a linha que foram feitas as alterações. E por fim, logo abaixo podemos ver as alterações que foram feitas, `-meu arquivo texto \ No newline at end of file +meu arquivo texto alterado`, sendo as linhas com `-` o estado anterior, e as linhas com `+` o estado atual.

## Comparação de binários

Comparar binários com `git diff` pode ser útil para entender as diferenças entre as versões de arquivos binários, como imagens, arquivos executáveis, arquivos de vídeo, entre outros. A maneira de utilização do comando é exatamente a mesma, no entanto, neste caso ele não fornece uma visualização direta das alterações feitas, como faz os arquivos de texto. Em vez disso, ele exibirá uma mensagem indicando que os arquivos são diferentes, como pode ser visto no seguinte exemplo:

```
diff --git a/binario.xlsx b/binario.xlsx
index 9645442..bca8b53 100644
Binary files a/binario.xlsx and b/binario.xlsx differ
```

Nesse exemplo foi criado um arquivo `xlsx`, que não pode ser lido em formato de texto.

## Comparação entre _branches_, _commits_ e _merges_

Quando é executado o `git diff`, o Git realiza uma comparação do estado atual do diretório de trabalho com o último commit feito na branch em que você está. Ele mostra as diferenças linha por linha, destacando as adições (linhas verdes) e remoções (linhas vermelhas).  

## Conclusão

Apesar da maioria das IDEs atuais apresentarem ferramentas porderosas para o controle e visualização das modificações feitas, é de extrema importância entender e aplicar os conceitos oferecidos pela ferramenta `git diff`. Com o conhecimento dessa área é possível 

## Referências
- [Docs Git](https://git-scm.com/docs/git-diff)
- [Entendimento áreas](https://www.geeksforgeeks.org/git-diff/)
