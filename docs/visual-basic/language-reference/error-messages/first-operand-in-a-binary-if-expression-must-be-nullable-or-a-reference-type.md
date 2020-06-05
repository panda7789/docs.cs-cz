---
title: První operand v binárním výrazu 'If' musí být typu, který povoluje hodnotu Null, nebo typu odkazu.
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: ca16c6604ee071668a5c65d7e9052b233e2313c7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403015"
---
# <a name="first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a>První operand v binárním výrazu 'If' musí být typu, který povoluje hodnotu Null, nebo typu odkazu.
`If`Výraz může přijmout buď dva, nebo tři argumenty. Když odesíláte pouze dva argumenty, první argument musí být odkazový typ nebo typ hodnoty s možnou hodnotou null. Pokud je první argument vyhodnocen jako cokoli jiného než `Nothing` , je vrácena jeho hodnota. Pokud je první argument vyhodnocen jako `Nothing` , je vyhodnocen a vrácen druhý argument.  
  
 Například následující kód obsahuje dva `If` výrazy, jeden se třemi argumenty a jeden se dvěma argumenty. Výrazy vypočítávají a vracejí stejnou hodnotu.  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 Tato chyba způsobí tyto výrazy:  
  
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
  
- Pokud nemůžete změnit kód tak, aby první argument byl typ hodnoty s možnou hodnotou null nebo odkazový typ, zvažte převod na výraz se třemi argumenty `If` nebo na `If...Then...Else` příkaz.  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a>Viz také

- [If – operátor](../operators/if-operator.md)
- [If...Then...Else – příkaz](../statements/if-then-else-statement.md)
- [Typy hodnot s možnou hodnotou null](../../programming-guide/language-features/data-types/nullable-value-types.md)
