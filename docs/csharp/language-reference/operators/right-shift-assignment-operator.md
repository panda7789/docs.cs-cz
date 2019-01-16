---
title: '&gt;&gt;= – operátor - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: 02a9559a5c4086eeed09094c15c3620366ffad8c
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333682"
---
# <a name="gtgt-operator-c-reference"></a>&gt;&gt;= – operátor (C# odkaz)

Operátor přiřazení posunutí doprava.

## <a name="remarks"></a>Poznámky

Výraz ve tvaru

```csharp
x >>= y
```

je vyhodnocen jako

```csharp
x = x >> y
```

s tím rozdílem, že `x` se jenom vyhodnotí jednou. [>> Operátor](right-shift-operator.md) posune `x` přímo podle zadaného množství určené `y`.

>> = Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [>> operátor](right-shift-operator.md) (naleznete v tématu [operátor](../keywords/operator.md)).

## <a name="example"></a>Příklad

[!code-csharp[csRefOperators#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#11)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [C#operátory](index.md)