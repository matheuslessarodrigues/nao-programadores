O básico que permitirá você fazer uns scripts simples sem depender do programador pé-no-saco.

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
1. Existem outros nomes importantes para a Unity. Podemos encontrá-los na documentação: https://docs.unity3d.com/ScriptReference/MonoBehaviour.html
```

# Variaveis
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

```
2. Outros tipos:
	- int = numeros inteiros
	- float = numeros com casas decimais
	- bool = 'true' ou 'false', valores lógicos, "sim"/"não", "ligado"/"desligado"
	- e mais! Qualquer um pode definir tipos extras (a Unity define vários por sinal)
```

----
variaveis => guardar valores pra mais tarde
- rapido devaneio sobre tipos?
fluxo
Update()
if input => Input.GetKeyDown()
variaveis publicas => inspector
docs Unity
