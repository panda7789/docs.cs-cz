---
title: '#If...Then...#Else – direktivy'
ms.date: 04/11/2018
f1_keywords:
- vb.#EndIf
- '#End If'
- '#Then'
- '#ElseIf'
- vb.#ElseIf
- vb.#Else
- vb.#If
helpviewer_keywords:
- Visual Basic code, compiling
- '#If directive [Visual Basic]'
- conditional compilation [Visual Basic], directives
- '#End if directive [Visual Basic]'
- selective compiling
- else directive (#else)
- '#Else directive [Visual Basic]'
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
ms.openlocfilehash: 7054a6ada4583c5d89e020437eb622a59d3eb17a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410007"
---
# <a name="ifthenelse-directives"></a>#If...Then...#Else – direktivy

Podmíněně zkompiluje vybrané bloky kódu Visual Basic.

## <a name="syntax"></a>Syntaxe

```vb
#If expression Then
   statements
[ #ElseIf expression Then
   [ statements ]
...
#ElseIf expression Then
   [ statements ] ]
[ #Else
   [ statements ] ]
#End If
```

## <a name="parts"></a>Součásti

`expression`  
Požadováno pro `#If` `#ElseIf` příkazy a, volitelně jinde. Libovolný výraz, který obsahuje výhradně jednu nebo více podmíněné konstanty kompilátoru, literály a operátory, které jsou vyhodnoceny jako `True` nebo `False` .

`statements`  
Vyžadováno pro `#If` blok příkazu, volitelně jinde. Visual Basic řádky programu nebo direktivy kompilátoru, které jsou kompilovány, pokud je přidružený výraz vyhodnocen jako `True` .

`#End If`  
Ukončí `#If` blok příkazu.

## <a name="remarks"></a>Poznámky

Na povrchu `#If...Then...#Else` se chování direktiv zobrazí stejně jako u `If...Then...Else` příkazů. Nicméně `#If...Then...#Else` direktivy vyhodnotí, co je zkompilováno kompilátorem, zatímco `If...Then...Else` příkazy vyhodnotí podmínky v době běhu.

Podmíněná kompilace se obvykle používá ke kompilaci stejného programu pro různé platformy. Slouží také k tomu, aby se zabránilo zobrazování kódu ladění ve spustitelném souboru. Kód vyloučený během podmíněné kompilace je zcela vynechán z finálního spustitelného souboru, takže nemá žádný vliv na velikost nebo výkon.

Bez ohledu na výsledek všech vyhodnocení jsou všechny výrazy vyhodnocovány pomocí `Option Compare Binary` . `Option Compare`Příkaz nemá vliv na výrazy v `#If` `#ElseIf` příkazech a.

> [!NOTE]
> Neexistuje žádný jednořádkový tvar `#If` `#Else` direktiv,, `#ElseIf` a `#End If` . Žádný jiný kód se nemůže zobrazit na stejném řádku jako kterákoli ze direktiv.

Příkazy v bloku podmíněné kompilace musí být dokončeny pomocí logických příkazů. Například nemůžete podmíněně kompilovat pouze atributy funkce, ale můžete podmíněně deklarovat funkci spolu s jejími atributy:

```vb
#If DEBUG Then
<WebMethod()>
Public Function SomeFunction() As String
#Else
<WebMethod(CacheDuration:=86400)>
Public Function SomeFunction() As String
#End If
```

## <a name="example"></a>Příklad

V tomto příkladu je použita `#If...Then...#Else` konstrukce k určení, zda mají být zkompilovány určité příkazy.

[!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]

## <a name="see-also"></a>Viz také

- [#Const direktiva](const-directive.md)
- [If...Then...Else – příkaz](../statements/if-then-else-statement.md)
- [Podmíněná kompilace](../../programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
