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
ms.openlocfilehash: 697521276e2d5a8d0a4aaae38789a21b7aa87fcb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940757"
---
# <a name="ifthenelse-directives"></a>#If...Then...#Else – direktivy
Podmíněně zkompiluje vybrané bloky kódu Visual Basic.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 Požadováno pro `#If` příkazy `#ElseIf` a, volitelně jinde. Libovolný výraz, který obsahuje výhradně jednu nebo více podmíněné konstanty kompilátoru, literály a operátory, které jsou vyhodnoceny `False`jako `True` nebo.  
  
 `statements`  
 Vyžadováno pro `#If` blok příkazu, volitelně jinde. Visual Basic řádky programu nebo direktivy kompilátoru, které jsou kompilovány, pokud je přidružený `True`výraz vyhodnocen jako.  
  
 `#End If`  
 Ukončí blok příkazu `#If` .  
  
## <a name="remarks"></a>Poznámky  
 Na povrchu se chování `#If...Then...#Else` direktiv zobrazí stejně jako `If...Then...Else` u příkazů. Nicméně direktivy vyhodnotí, co je zkompilováno kompilátorem, `If...Then...Else` zatímco příkazy vyhodnotí podmínky v době běhu. `#If...Then...#Else`  
  
 Podmíněná kompilace se obvykle používá ke kompilaci stejného programu pro různé platformy. Slouží také k tomu, aby se zabránilo zobrazování kódu ladění ve spustitelném souboru. Kód vyloučený během podmíněné kompilace je zcela vynechán z finálního spustitelného souboru, takže nemá žádný vliv na velikost nebo výkon.  
  
 Bez ohledu na výsledek všech vyhodnocení jsou všechny výrazy vyhodnocovány pomocí `Option Compare Binary`. Příkaz nemá vliv na výrazy v `#If` příkazech `#ElseIf`a. `Option Compare`  
  
> [!NOTE]
> Neexistuje `#If`žádný jednořádkový tvar direktiv, `#Else`, `#ElseIf`a `#End If` . Žádný jiný kód se nemůže zobrazit na stejném řádku jako kterákoli ze direktiv. 

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
 V tomto příkladu je `#If...Then...#Else` použita konstrukce k určení, zda mají být zkompilovány určité příkazy.  
  
 [!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Direktiva #Const](../../../visual-basic/language-reference/directives/const-directive.md)
- [Příkaz If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
