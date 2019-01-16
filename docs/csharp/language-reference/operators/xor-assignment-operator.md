---
title: ^ = – operátor - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
ms.openlocfilehash: 12189d6469a9716d3b7ebcffef23423a75692d1a
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333548"
---
# <a name="-operator-c-reference"></a>^ = – operátor (C# odkaz)

Operátor přiřazení exkluzivní disjunkce OR.

## <a name="remarks"></a>Poznámky

Výraz ve tvaru

```csharp
x ^= y
```

je vyhodnocen jako

```csharp
x = x ^ y
```

s tím rozdílem, že `x` se jenom vyhodnotí jednou. [^ – Operátor](xor-operator.md) provádí bitový exkluzivní operátor OR operaci na celočíselných operandech a logické exkluzivní disjunkce OR na [bool](../keywords/bool.md) operandy.

^ = – Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [^ – operátor](xor-operator.md) (naleznete v tématu [operátor](../keywords/operator.md)).

## <a name="example"></a>Příklad

[!code-csharp[csRefOperators#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#23)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [C#operátory](index.md)