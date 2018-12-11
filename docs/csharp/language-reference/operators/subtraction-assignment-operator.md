---
title: -= – Operátor - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
ms.openlocfilehash: dc3cedafc57e1c6ec9bc34ca4e2c2aa9c604848c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239576"
---
# <a name="--operator-c-reference"></a>-= – operátor (Referenční dokumentace jazyka C#)
Operátor přiřazení odčítání.  
  
## <a name="remarks"></a>Poznámky  
 Pomocí výrazu `-=` operátor přiřazení, jako například  
  
```csharp  
x -= y  
```  
  
 je ekvivalentem  
  
```csharp  
x = x - y  
```  
  
 s tím rozdílem, že `x` se jenom vyhodnotí jednou. Význam [-– operátor](../../../csharp/language-reference/operators/subtraction-operator.md) závisí na typech `x` a `y` (odčítání pro číselné operandy, delegovat odebrání pro delegáta operandy a tak dále).  
  
 `-=` Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [-– operátor](../../../csharp/language-reference/operators/subtraction-operator.md) (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)).  
  
 -= – Operátor také umožňuje v jazyce C# zrušit odběr události. Další informace najdete v tématu [jak: Přihlaste se k odběru a zrušit její odběr události](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
