---
title: '#If... Then... #Else – direktivy'
ms.date: 04/11/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 884c7ed6f0a346f2d35f01006cea23e47907d13f
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="ifthenelse-directives"></a>#If...Then...#Else – direktivy
Podmíněná zkompiluje vybrané bloky kódu jazyka Visual Basic.  
  
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
 Vyžaduje se pro `#If` a `#ElseIf` příkazy, volitelné jinde. Jakýkoli výraz tvořené výhradně jeden nebo více podmíněného kompilátoru konstanty, literály a operátory, které se vyhodnocuje `True` nebo `False`.  
  
 `statements`  
 Vyžaduje se pro `#If` příkaz blok volitelné jinde. Řádky programu jazyka Visual Basic nebo direktivy kompilátoru, které jsou kompilovány, pokud je výsledkem přidružený výraz `True`.  
  
 `#End If`  
 Ukončí `#If` příkaz bloku.  
  
## <a name="remarks"></a>Poznámky  
 Na ploše, chování `#If...Then...#Else` direktivy zobrazuje stejně jako u `If...Then...Else` příkazy. Ale `#If...Then...#Else` direktivy vyhodnotit zkompilují kompilátoru, zatímco `If...Then...Else` příkazy vyhodnocení podmínky za běhu.  
  
 Podmíněná kompilace se obvykle používá ke kompilaci stejný program pro různé platformy. Také se používá při prevenci ladění kódu ze storu ve spustitelném souboru. Vyloučené během Podmíněná kompilace kódu je úplně vynechaný konečné spustitelný soubor, takže ho nemá žádný vliv na výkon nebo velikost.  
  
 Bez ohledu na výsledek žádné vyhodnocení všechny výrazy vyhodnocují se pomocí `Option Compare Binary`. `Option Compare` Příkaz nemá vliv na výrazy v `#If` a `#ElseIf` příkazy.  
  
> [!NOTE]
>  Žádné jeden řádek formu `#If`, `#Else`, `#ElseIf`, a `#End If` direktivy existuje. Žádný jiný kód, můžete zobrazit na stejném řádku jako kterákoli ze direktivy. 

Příkazy v bloku Podmíněná kompilace musí být úplný logické příkazy. Například nelze Podmíněná kompilace pouze atributy, funkce, ale můžou podmíněně deklarovat funkce společně s jeho atributy:

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
 Tento příklad používá `#If...Then...#Else` konstrukce k určení, zda se pro kompilaci určité příkazy.  
  
 [!code-vb[VbVbalrConditionalComp#1](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/if-then-else-directives_1.vb)]  
  
## <a name="see-also"></a>Viz také  
[Direktiva #Const](../../../visual-basic/language-reference/directives/const-directive.md)  
[Příkaz If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
[Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
<xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>   


