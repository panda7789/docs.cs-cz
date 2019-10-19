---
title: '#Pokud... Then... #Else – direktivy (Visual Basic)'
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
ms.openlocfilehash: aaf5e7dd82cebf734da59e9feb89174705468a4b
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72580094"
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
Vyžaduje se pro příkazy `#If` a `#ElseIf`, které jsou volitelné jinde. Libovolný výraz, který se skládá výhradně z jedné nebo více podmíněných konstant kompilátoru, literálů a operátorů, které jsou vyhodnoceny jako `True` nebo `False`.

`statements`  
Vyžadováno pro blok příkazu `#If`, volitelně jinde. Visual Basic řádky programu nebo direktivy kompilátoru, které jsou kompilovány, pokud je přidružený výraz vyhodnocen jako `True`.

`#End If`  
Ukončí blok příkazu `#If`.

## <a name="remarks"></a>Poznámky

Na povrchu se chování direktiv `#If...Then...#Else` zobrazí stejně jako u příkazů `If...Then...Else`. Direktivy `#If...Then...#Else` však vyhodnotí, co je zkompilováno kompilátorem, zatímco příkazy `If...Then...Else` vyhodnocují podmínky v době běhu.

Podmíněná kompilace se obvykle používá ke kompilaci stejného programu pro různé platformy. Slouží také k tomu, aby se zabránilo zobrazování kódu ladění ve spustitelném souboru. Kód vyloučený během podmíněné kompilace je zcela vynechán z finálního spustitelného souboru, takže nemá žádný vliv na velikost nebo výkon.

Bez ohledu na výsledek žádného vyhodnocení jsou všechny výrazy vyhodnocovány pomocí `Option Compare Binary`. Příkaz `Option Compare` neovlivňuje výrazy v příkazech `#If` a `#ElseIf`.

> [!NOTE]
> Neexistuje žádný jednořádkový tvar `#If`, `#Else`, `#ElseIf` a direktivy `#End If`. Žádný jiný kód se nemůže zobrazit na stejném řádku jako kterákoli ze direktiv.

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

V tomto příkladu se používá konstrukce `#If...Then...#Else` k určení, zda se mají kompilovat určité příkazy.

[!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]

## <a name="see-also"></a>Viz také:

- [Direktiva #Const](../../../visual-basic/language-reference/directives/const-directive.md)
- [Příkaz If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
