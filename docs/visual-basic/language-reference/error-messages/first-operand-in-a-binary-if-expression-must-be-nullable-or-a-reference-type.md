---
title: První operand v binárním &#39;Pokud&#39; musí být výraz s možnou hodnotou Null nebo typ odkazu
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: 85094ba6d6a44bf2e6cc4fba7946598c286a08a2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668268"
---
# <a name="first-operand-in-a-binary-39if39-expression-must-be-nullable-or-a-reference-type"></a>První operand v binárním &#39;Pokud&#39; musí být výraz s možnou hodnotou Null nebo typ odkazu
`If` Výraz může trvat dvě až tři argumenty. Když posíláte pouze dva argumenty, první argument musí být typu odkaz nebo typ připouštějící hodnotu Null. Pokud je první argument vyhodnocen jako cokoli jiného než `Nothing`, je tato hodnota vrácena. Pokud je vyhodnocen jako první argument `Nothing`, vyhodnotí a vrátí druhý argument.  
  
 Například následující kód obsahuje dva `If` výrazy, jeden s tři argumenty a druhý se dvěma argumenty. Výrazy vypočítat a vrátit se stejnou hodnotou.  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 Tato chyba je způsobena těchto výrazů:  
  
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
  
-   Pokud kód nelze změnit tak, aby první argument je typ připouštějící hodnotu null nebo typ odkazu, zvažte převedení na tři argumenty `If` výrazu, nebo `If...Then...Else` příkazu.  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a>Viz také:
- [Operátor If](../../../visual-basic/language-reference/operators/if-operator.md)
- [Příkaz If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Typy hodnot s povolenou hodnotou Null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
