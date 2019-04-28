---
title: -= – operátor - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
ms.openlocfilehash: 3b6890be4460a599a5d2f5f5f6ee1627be933f0b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61688680"
---
# <a name="--operator-c-reference"></a>-= – operátor (C# odkaz)

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

s tím rozdílem, že `x` se jenom vyhodnotí jednou. Význam [-– operátor](subtraction-operator.md) závisí na typech `x` a `y` (odčítání pro číselné operandy, delegovat odebrání pro delegáta operandy a tak dále).

`-=` Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [-– operátor](subtraction-operator.md) (naleznete v tématu [operátor](../keywords/operator.md)).

-= – Operátor také umožňuje v jazyce C# zrušit odběr události. Další informace najdete v tématu [jak: Přihlaste se k odběru a zrušit její odběr události](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="example"></a>Příklad

[!code-csharp[csRefOperators#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#6)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
