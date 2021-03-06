O básico que permitirá você fazer uns scripts simples sem depender do programador pé-no-saco.
Tenham em mente que ainda assim é bastante conteúdo condensado e, por isso, cada comentário tem
informação importante!

# Setup
Esse guia focará num ambiente [Unity](https://unity.com/) (tenha ao menos uma versão instalada).
Por conta disso, nós iremos programar em [C#](https://en.wikipedia.org/wiki/C_Sharp_%28programming_language%29) e,
pra isso, recomendo o editor de código [VS Code](https://code.visualstudio.com/).

## VS Code
É recomendado instalar a extensão de C#. Após abrir o vscode:
- `ctrl+shift+x`
- procure por 'C#'
- instale clicando no botão verde 'install'
- (você pode fechar a sidebar com `ctrl+b`)

## Unity
Configure o vscode como editor de código padrão da unity:
- `Edit` > `Preferences...` > `External Tools`
- mude `External Script Editor` para `Visual Studio Code`

Caso não exista essa opção, instale o pacote de suporte do vscode:
- `Window` > `Package Manager`
- no dropdown superior esquerdo, selecione `All Packages`
- na busca digite `code`
- instale o pacote 'Visual Studio Code Editor'

# Primeiro Script
Na Unity, procure ou crie uma pasta 'Scripts' e lá crie um script C# com o nome `MeuScript.cs`.

[create-script](images/create-script.png)

Mude o conteúdo do script para:
```csharp
using UnityEngine;

public class MeuScript : MonoBehaviour
{
	private void Start()
	{
		Debug.Log("VIVE NO ABACAXI");
		Debug.Log("E MORA NO MAR");
	}
}
```
Repare que o nome do arquivo é o mesmo nome da classe: 'MeuScript'.
Isso é importante pra Unity reconhecer o script como um componente.

Ao adicionar o componente 'MeuScript' a um GameObject na cena e dar play no editor, você poderá
ver a mensagem `VIVE NO ABACAXI` seguida de `E MORA NO MAR` aparecer no console.

## 'Start'
Ignorando por hora as estruturas extras no script, podemos reparar em algumas coisas:
- todo o código dentro de `Start()` é executado quando damos play
- é importante que o nome seja exatamente `Start` para que a Unity saiba o que executar (1)
- `Debug.Log` serve para mostrar mensagens no console
- a execução do código é linear e segue de cima para baixo!!

```
1. Existem outros nomes importantes para a Unity. Podemos encontrá-los na documentação:
https://docs.unity3d.com/ScriptReference/MonoBehaviour.html
Um exemplo é 'Update' que executa um trecho de código *todo* frame.
```

# Variáveis
Faça a seguinte mudança no script anterior:
```csharp
using UnityEngine;

public class MeuScript : MonoBehaviour
{
	private void Start()
	{
		string mensagem1 = "VIVE NO ABACAXI";
		string mensagem2 = "E MORA NO MAR";
		Debug.Log(mensagem1);
		Debug.Log(mensagem2);
	}
}
```

Ao executar o código, vemos que as mensagens continuam a mesma apesar do código ter mudado.
`mensagem1` e `mensagem2` são variáveis que cujos valores são as mensagens de antes.

A estrutura padrão pra declarar variáveis é `<tipo> <nome> = <valor>`. No nosso caso, as
mensagens têm tipo `string` que significa "essas variáveis apenas podem conter valores do tipo texto". (2)

Após declarada, podemos usar a variável à vontade e será como se tivéssemos escrito diretamente o valor
que ela contém. Porém, variáveis existem para que possamos fazer operações com seus valores. Exemplo:
```csharp
// código omitido
private void Start()
{
	string mensagem1 = "VIVE NO ABACAXI";
	string mensagem2 = "E MORA NO MAR";
	string tudoJunto = mensagem1 + " " + mensagem2;
	Debug.Log(tudoJunto);
}
```
Agora criamos uma terceira variável (`tudoJunto`) que contém os valores concatenados de `mensagem1` e `mensagem2`.
Ai quando chamamos `Debug.Log` com `tudoJunto`, o que irá aparecer é o resultado da operação.

O potencial disso é que podemos criar códigos cujo comportamento se adapta com base nos valores de suas variáveis. (3)

## Unity Inspector
Se mudarmos mais um pouco o exemplo para:
```csharp
using UnityEngine;

public class MeuScript : MonoBehaviour
{
	// agora as variáveis estão fora do 'Start'
	public string mensagem1 = "VIVE NO ABACAXI";
	public string mensagem2 = "E MORA NO MAR";

	private void Start()
	{
		Debug.Log(mensagem1);
		Debug.Log(mensagem2);
	}
}
```
As variaveis agora aparecem no inspector da Unity. Isso nos permite mudar seus valores *antes* da execução do programa.
É como se tivéssemos escrito o programa com aqueles valores porém sem precisar tocar no código ou recompilar! Você pode
reparar que na hora de executar, ele ignora o valor inicial escrito no código e usa o que foi inserido no inspector.

## Exemplo Outros Tipos
```csharp
// código omitido
private void Start()
{
	// variáveis podem ser criadas a partir de expressões
	int meuNumero = 10 + 2;
	Debug.Log(meuNumero); // 12

	// pode misturar int e float
	// porem, nesse caso, o int é convertido pra float (cuidado!)
	// o 'f' em '0.5f' serve pra indicar que esse literal é um número float
	float metade = meuNumero * 0.5f;
	Debug.Log(metade); // 6.0

	// 'true' se meuNumero for maior que 10, 'false' caso contrário
	bool numeroEhGrande = meuNumero > 10;
	Debug.Log(numeroEhGrande); // true

	// um dos tipos que existem na Unity
	// representa um ponto no espaço 3d
	Vector3 position = new Vector3(0.0f, meuNumero, metade + 4.0f);
	Debug.Log(position); // Vector3(0.0, 12.0, 10.0)
}
```

```
2. Outros tipos:
	- int = numeros inteiros
	- float = numeros com casas decimais
	- bool = 'true' ou 'false', valores lógicos, "sim"/"não", "ligado"/"desligado"
	- e mais! Qualquer um pode definir tipos extras (a Unity define vários por sinal)

3. Isso é a base e todo o propósito de programação em geral e irá ficar mais claro adiante!
```

# Sintaxe
É o que define a estrutura visual de uma linguagem de programação. São regras que devemos seguir ao escrever códigos
para que eles sejam corretamente interpretados pelo computador. Cada linguagem de programação tem sua própria
sintaxe. Todas diferentes, porém semelhantes o suficiente para que possamos aplicar conceitos de uma linguagem para outra.

Exemplos de C#:
```csharp
// cria uma classe (mais detalhes adiante)
// ': MonoBehaviour' significa que esse script é também um componente da Unity
public class MeuScript : MonoBehaviour
{
	// tudo entre {} faz parte do conteúdo da classe

	// quando a variavel aparece no inspector,
	// não precisa ter valor inicial
	public string mensagem;

	public void MinhaFuncao() // cria uma função (mais detalhes adiante)
	{
		Debug.Log(mensagem); // linhas de execução (statements) terminam com ';'
	}

	public void OutraFuncao()
	{
		// tudo entre {} faz parte do conteúdo da função

		int meuNumero = 10; // cria uma variável. ela pode ser usada daqui em diante

		// testa uma condição e bifurca o fluxo de execução
		if(meuNumero > 0) 
		{
			// executa tudo entre {} caso a condição seja verdadeira (true)

			meuNumero = meuNumero - 1; // é possível alterar uma variável depois de criada
		}
		else
		{
			// executa tudo entre {} caso a condição seja false (false)

			MinhaFuncao(); // podemos executar uma outra função
		}

		while(meuNumero < 100) // *repete* tudo entre {} enquando a condição for verdadeira
		{
			// misturando string com int,
			// int é convertido em texto
			Debug.Log("contando até cem: " + meuNumero);
			meuNumero += 1; // shorthand para 'meuNumero = meuNumero + 1'
		}
	}
}
```

# Fluxo
Vamos aplicar tudo já visto até agora:
```csharp
public class MeuScript : MonoBehaviour
{
	// KeyCode representa uma tecla ou botão
	public KeyCode rightKey = KeyCode.RightArrow;
	public KeyCode leftKey = KeyCode.LeftArrow;
	// velocidade em metros/segundo
	public float velocity = 5.0f;

	// como queremos verificar a todo momento quando o jogador
	// pressionou um botão, nosso código fica no 'Update'
	private void Update()
	{
		// transforma velocidade em distância percorrida em um intervalo de tempo
		// 'Time.deltaTime' é quanto tempo se passou desde o último frame em segundos
		float delta = velocity * Time.deltaTime;

		if(Input.GetKeyDown(rightKey))
		{
			// na Unity, 'transform' é uma referência pro Transform onde
			// esse script está
			transform.position += new Vector3(delta, 0.0f, 0.0f);
		}

		if(Input.GetKeyDown(leftKey))
		{
			// na Unity, a esquerda fica na parte negativa do eixo X
			transform.position -= new Vector3(delta, 0.0f, 0.0f);
		}
	}
}
```
Ponha esse script em um GameObject que contenha um renderer para vê-lo se mover para os lados usando
as setas do teclado. No inspector, será possível também alterar não apenas as teclas que fazem mover o objeto,
como também a velocidade com que ele move.

# Se Aprofundando
Como que na prática aplicamos esse básico e resolvemos problemas com programaçào.

## Funções
Duas ideias estão por trás do conceito de funções são:
- organização: isolar clusters de linhas e dando um nome para eles
- reutilização: trechos que se repetem (mesmo que com pequenas variações)

### Parâmetros
Um código qualquer pode interagir com uma função por tanto passar valores para ela, como também
receber de volta valores gerados por ela.

Exemplo:
```csharp
private int Incrementa(int valor)
{
	valor += 1;

	// 'return' é como uma função passa um valor
	// gerado por ela pro código que a chamou
	return valor;
}

private void Start()
{
	var meuNumeroEspecial = Incrementa(10);
	Debug.Log(meuNumeroEspecial); // 11

	// não tem problema essa variável ter o mesmo nome
	// pois ela está em uma função diferente
	var valor = 4;
	var resultado = Incrementa(valor);
	Debug.Log(resultado); // 5

	// quando um valor é passado para uma função,
	// ele é copiado e então a função pode altera-los
	// à vontade sem se preocupar com o código que a chamou
	var maisUm = Incrementa(valor);
	Debug.Log(maisUm); // 5
	Debug.Log(valor); // 4
}
```

### Refatorando

Considere esse trecho que tem por objetivo testar duas condições para cada inimigo:
- se o player está suficientemente perto
- uma chance de sucesso

E que, caso ambas sejam positivas, inflinge dano no player com base no ataque de cada um e, por fim,
também mostra no console quanto de dano que tomou:
```csharp
// código omitido
private void Update()
{
	float distanciaAteInimigoChao = Vector3.Distance(player.transform.position, inimigoChao.transform.position);
	bool sucessoInimigoChao = Random.value > inimigoChao.sorte;
	// '&&' indica que só entramos no 'if' caso ambas as condições sejam verdadeiras
	if(distanciaAteInimigoChao < 1.0f && sucessoInimigoChao)
	{
		player.health -= inimigoChao.ataque;
		Debug.Log("levou " + inimigoChao.ataque + " de dano");
	}

	float distanciaAteInimigoVoador = Vector3.Distance(player.transform.position, inimigoVoador.transform.position)
	bool sucessoInimigoVoador = Random.value > inimigoVoador.sorte;
	if(distanciaAteInimigoVoador < 1.0f && sucessoInimigoVoador)
	{
		player.health -= inimigoVoador.ataque;
		Debug.Log("levou " + inimigoVoador.ataque + " de dano");
	}

	float distanciaAteInimigoAgua = Vector3.Distance(player.transform.position, inimigoAgua.transform.position);
	bool sucessoInimigoAgua = Random.value > inimigoAgua.sorte;
	if(distanciaAteInimigoAgua < 1.0f && sucessoInimigoAgua)
	{
		player.health -= inimigoAgua.ataque;
		Debug.Log("levou " + inimigoAgua.ataque + " de dano");
	}
}
```

Repare como a forma do código se repete para cada inimigo apenas alterando de qual inimigo estamos tratando.
Vamos refatorar para usar função para tanto lidar com a repetição como também organizar para darmos um nome
pro trecho de código com base no que ele faz:
```csharp
// código omitido

// repare que, como a única coisa que mudava no trecho que era repetido era o inimigo,
// será necessário passá-lo como parâmetro.
private void TomarDanoCasoMuitoPerto(Inimigo inimigo)
{
	float distanciaAteInimigo = Vector3.Distance(player.transform.position, inimigo.transform.position);
	bool sucessoInimigo = Random.value > inimigo.sorte;
	if(distanciaAteInimigo < 1.0f && sucessoInimigo)
	{
		player.health -= inimigo.ataque;
		Debug.Log("levou " + inimigo.ataque + " de dano");
	}
}

private void Update()
{
	TomarDanoCasoMuitoPerto(inimigoChao);
	TomarDanoCasoMuitoPerto(inimigoVoador);
	TomarDanoCasoMuitoPerto(inimigoAgua);
}
```
Com isso conseguimos juntar toda a lógica de levar dano em um lugar apenas.
Caso outros inimigos sejam criados, nós apenas realizamos mais uma chamada da função dentro de `Update`.
Caso seja necessário alterar a lógica do player levando dano, precisaremos apenas alterar as linhas dentro
de `TomarDanoCasoMuitoPerto` e apenas uma única vez.

Como e quando isolar trechos do programa em funções é algo que vem com o tempo. Porém, você pode
considerar extrair uma função a partir de linhas que se repetem (ou muito parecidas como foi visto) ou
quando você botaria um comentário descrevendo o que um conjunto de código faz.

## Classes
Voltando para a função `TomarDanoCasoMuitoPerto`, ela recebe um parâmetro chamado `inimigo` de tipo `Inimigo`.
Porém, como o computador sabe que a variável `inimigo` possui um valor ('field'), por exemplo, chamado `ataque`?

Isso vem da definição de `Inimigo`! Em algum outro lugar, alguém definiu `Inimigo` como algo, digamos, assim:
```csharp
using UnityEngine;

// 'Inimigo' também pode ser adicionado a um GameObject
public class Inimigo : MonoBehaviour
{
	public float ataque = 10;
	public float sorte = 0.8f;
}
```
Esse trecho indica ao computador que toda vez que aparecer uma variável do tipo `Inimigo`, ela irá
possuir os campos `ataque` e `sorte` disponíveis para uso. Você pode imaginar campos como sendo "sub-variáveis",
ou então "variáveis dentro de variáveis".

Exemplo do que é possível fazer definindo nossas classes:
```csharp
public class MeuScript : MonoBehaviour
{
	// nosso script tem referencias para componentes
	// do tipo 'Inimigo' em algum GameObject
	public Inimigo inimigoChao;
	public Inimigo inimigoVoador;
	public Inimigo inimigoAgua;

	private void Start()
	{
		// vamo fazer uns balanceamentos:
		inimigoChao.ataque = 100;
		inimigoVoador.ataque = 50;

		// repare que cada campo 'ataque' é independente
		// para cada variável do tipo 'Inimigo'
		Debug.Log(inimigoChao.ataque); // 100
		Debug.Log(inimigoVoador.ataque); // 50
	}
}
```

*Classes são para dados o que funções são para códigos.*

```
Em outras linguagens, o que foi descrito aqui como 'Classe', lá é chamado de 'Estruturas' (struct),
ou então a linguagem nem possui a formalidade de definir tipos e é tudo dinâmico (o que cada
variável pode carregar tem o potencial de mudar a qualquer momento).
```

