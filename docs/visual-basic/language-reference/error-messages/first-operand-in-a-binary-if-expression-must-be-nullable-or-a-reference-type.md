---
title: První operand v binárním &#39;Pokud&#39; výraz musí být null nebo zadejte odkaz
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: 76078d315b2c32a2a29aa652a65b463622afec36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="first-operand-in-a-binary-39if39-expression-must-be-nullable-or-a-reference-type"></a>První operand v binárním &#39;Pokud&#39; výraz musí být null nebo zadejte odkaz
`If` Výrazu může trvat dvě nebo tři argumenty. Při odesílání pouze dva argumenty, první argument musí být odkazového typu nebo typ s možnou hodnotou Null. Pokud je první argument výsledkem k ničemu jiné než `Nothing`, je vrácena jeho hodnota. Pokud se vyhodnotí jako první argument `Nothing`, druhý argument je vyhodnocena a vrácena.  
  
 Například následující kód obsahuje dva `If` výrazy, jeden s tři argumenty a jednu s dva argumenty. Výrazy výpočtu a vrací stejnou hodnotu.  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 Tuto chybu způsobí těchto výrazů:  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 **ID chyby:** BC33107  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud kód nelze změnit tak, aby první argument na typ s možnou hodnotou Null nebo odkaz na typ, zvažte, převod argumentem tři `If` výrazu, nebo `If...Then...Else` příkaz.  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a>Viz také  
 [Operátor If](../../../visual-basic/language-reference/operators/if-operator.md)  
 [Příkaz If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Typy hodnot s povolenou hodnotou Null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
