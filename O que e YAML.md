---
title: O que é YAML
tags: YAML, MarkUp
description: Breve apresentação sobre o conceito e estrutura da linguagem "YAML".
---

![](https://i.imgur.com/adZTNVb.png)


## O que é YAML?

O presente documento tem a intenção de explicar, de forma objetiva, o que é YAML, bem como se estrutura um arquivo .yml.

Para atingir esse fim, utilizarei de comentários à ordenação de um arquivo comum, para explicar cada parte.

### O Início

`---`  Todo arquivo, ou bloco no fluxo, inicia por três hifens. 
    # Todo comentário é precedido por '#'.

**Definição**: *YAML* é o acrônimo de *YAML Ain't Markup Language*¹. A linguagem tem o intuito de representar todos os dados, de forma adequada, utilizando-se para isto da combinação de listas, hashes (mapas) e dados escalares (valores simples).

A sua síntaxe é estruturada de maneira a permitir a fácil leitura e compreensão por pessoas e o fácil mapeamento pelos tipos de dados comumente encontrados na maior parte das linguagens de alto-nível.

Sua notação é baseada em **indentação** e um conjunto de caracteres **sigil** distintos dos que são usados pelo **XML**, fazendo com que as duas linguagens, YAML e XML, sejam facilmente compostas uma na outra.

#### Algumas Características²

* YAML utiliza a codificação de caracteres unicode (UTF-8 ou UTF-16);
* A estrutura do documento utiliza a identação com espaços em branco, não sendo permitido o uso de caracteres de tabulação para este fim;
* Os itens das listas são iniciados por hífen nos títulos e serão alocados cada um em uma linha, ou entre colchetes. Neste último caso, os itens serão separados por uma vígula seguida de espaço;
* As chaves são sucedidas por dois pontos, seguido por um espaço. Tal como em "Uma Chave Qualquer: valor" e serão alocadas uma por linha . Uma outra forma de alinhar as chaves, também chamadas de 'valores associativos', é inseri-las entre chaves, separando-as co vírgula e espaço.
* Um valor de um vetor associativo vem precedida por um sinal interrogação (? ), o que permite que se construam chaves complexas sem ambiguidade.
* Nas aspas duplas, os caracteres especiais podem ser representados com sequências de escape similares a da linguagem de programação C, que começam com uma barra invertida.
* Pode-se incluir múltiplos documentos dentro de um único fluxo, separando-os por três traços ( `---` ); os três pontos ( `...` ) indicam o fim de um documento dentro de um fluxo.
* Os comentários são encabeçados por cerquilha ( `#` ) e continuam até o final da linha.
* Os documentos YAML podem ser precedidos por diretivas compostas por um sinal de porcentagem ( % ) seguidos de um nome e parâmetros delimitados por um espaço.
* A diretiva %YAML é utilizada para identificar a versão do YAML em um documento.
* A diretiva %TAG é utilizada como atalho para prefixos de URIs.
* YAML requer que as vírgulas e pontos sejam utilizados como separadores nas listas seguidos por um espaço, de forma que os valores escalares que contenham sinais de pontuação possam se representar sem a necessidade de utilizar aspas.

**Exemplos de linguagens Markup**: *XML, HTML, XHTML*.

¹ *Markup Language é uma forma de anotação de texto que permite que as funções sintáticas sejam perceptíveis e distinguíveis. Na área de tecnlogia é usada para codificar o dado, determinando a forma como será interpretado pela máquina (sua função), bem como estabelecer (em alguns casos) como se dará a sua apresentação.*

² *Características retiradas da Wikipédia: https://pt.wikipedia.org/wiki/YAML *.

... # Todo arquivo, ou bloco no fluxo, finaliza com três pontos.

---

### Dados Escalares

O objeto raiz em um arquivo YAML, que se estende por toda a sua estrutura, tem a função de um mapa. Em outras linguagens, seria equivalente a um dicionário, hash, ou objeto.

**esta_é_uma_chave**: `um valor`                          # *Aqui inserimos o valor que define a chave*
**esta_é_outra_chave**: `um outro valor`                  # *Aqui inserimos o valor que específica a função descrita*.
**esta_chave_tem_um_valor_numerico**: `100`               # *Se um atributo numérico se faz necessário, ele é inserido tal como se mostra*.
**esta_chave_tem_a_escrita_cientifica**: `1e+12`          # *Se for necessário, podemos usar da escrita científica, sem correr risco de não interpretação do nosso código*.
**esta_chave_recebe_o_valor_boleano**: `true`             # *Podemos usar de valores da lógica boleana, se preciso*.
**esta_chave_recebe_o_valor_nulo**: `null`                # *Se uma nulidade precisar ser especificada, podemos fazê-lo sem falhas.*
**esta chave é escrita com espaço**: `valor`              # *A string pode ser escrita com espaço, sem a necessida de* `_` *para interligar suas partes*.

As strings não precisam se escritas entre aspas. Porém, podemos usá-las com aspas simples ou duplas, caso queiramos. Por exemplo:

**string_01**: `'Uma string, entre aspas simples.'`
**string_02**: `"Uma string, entre aspas duplas."`

Veja o exemplo abaixo, para melhor compreender. Nele temos um código de tradução de uma aplicação financeira:

```gherkin=
pt-BR:
  action_reasons:
    opening_balance: 'Saldo Inicial'
    account_payment_via_app: 'Pagamento de conta via aplicativo'
    transfer_between_XurumelasPay_accounts: 'Transferência entre contas XurumelasPay'
    lottery_withdrawal: 'Saque na lotérica'
    lottery_deposit: 'Depósito na lotérica'
    receipt_via_XurumelasCesta_partner: 'Recebimento via XurumelasCesta'
    cell_phone_recharge: 'Recarga de Celular'
    deposit: 'Depósito'
    reversal: 'Estorno de Pagamento'
    ted: 'TED para outros bancos'
    fee: 'Taxa de transação'
```

Não é muito usual, mas você pode escrever as chaves entre aspas, também.

**"Esta é uma chave, escrita entre aspas"**: `a string está sem.`

Podemos escrever as nossas chaves em estilo de blocos, que nada mais são que o agrupamento de linhas sequenciais.

Os blocos podem ser 'Literais' ou 'Compactos'. Para escrever uma chave de bloco literal, devemos utilizar o pipe ( `|` ); para bloco compacto, usamos o sinal de maior ( `>` ).

**bloco_literal**: |
```
    Todo texto inserido aqui, será o valor da chave, em estilo de bloco literal, que terá preservada
    a quebra de linhas, que
    fizermos.

    O bloco literal terá sua estrutura mantida até o ponto em que modificarmos a indentação do código.

        As linhas que receberem o novo padrão, formarão um novo bloco e terão a sua estrutura mantida
        e a indentação preservada. 
        Atente para o fato de que estas linhas terão quatro espaços em seu início, para estabelecer sua notação.
            Isto vale para novos níveis criados. :)
```

**estilo_compacto**: >
    Todo esse bloco de texto será o valor de '`estilo_compacto`', mas esta
    vez, todas as novas linhas serão substituídas com espaço simples.

    Linhas em branco, como acima, são convertidas em um carater de nova linha.

        Linhas 'mais-indentadas' mantém suas novas linhas também -
        este texto irá aparecer em duas linhas.

Espero que essas informações possam-lhes serem úteis e ajudarem nas atividades diárias.
...

fonte da imagem: https://i0.wp.com/blog.fossasia.org/wp-content/uploads/2017/07/yaml-2.png?fit=800%2C247&ssl=1