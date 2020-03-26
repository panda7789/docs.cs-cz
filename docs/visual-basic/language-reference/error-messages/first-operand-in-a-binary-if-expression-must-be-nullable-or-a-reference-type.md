---
title: První operand v binárním výrazu 'If' musí být typu, který povoluje hodnotu Null, nebo typu odkazu.
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: 4b520949cb59b63ea39441632dc5e2c6d000d711
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249523"
---
# <a name="first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a>První operand v binárním výrazu 'If' musí být typu, který povoluje hodnotu Null, nebo typu odkazu.
Výraz `If` může trvat dva nebo tři argumenty. Při odeslání pouze dva argumenty, první argument musí být typ odkazu nebo typ hodnoty s hodnotou s hodnotou, kterou lze hodnotit. Pokud první argument vyhodnotí `Nothing`na něco jiného než , jeho hodnota je vrácena. Pokud první argument vyhodnotí `Nothing`na , druhý argument je vyhodnocena a vrácena.  
  
 Například následující kód obsahuje `If` dva výrazy, jeden se třemi argumenty a jeden se dvěma argumenty. Výrazy vypočítat a vrátit stejnou hodnotu.  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 Následující výrazy způsobit tuto chybu:  
  
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
  
- Pokud nemůžete změnit kód tak, aby první argument byl typ hodnoty s hodnotou s `If` hodnotou s `If...Then...Else` hodnotou s hodnotou nebo typ odkazu, zvažte převod na výraz se třemi argumenty nebo na příkaz.  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a>Viz také

- [Operátor If](../../../visual-basic/language-reference/operators/if-operator.md)
- [Příkaz If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Typy hodnot s povolenou hodnotou Null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
