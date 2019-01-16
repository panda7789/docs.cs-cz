---
title: '&lt;&lt;= – operátor - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: 4513c4b78dea3e8102c72a43249b4a44ffa2421d
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333249"
---
# <a name="ltlt-operator-c-reference"></a>&lt;&lt;= – operátor (C# odkaz)

Operátor přiřazení posunutí doleva.

## <a name="remarks"></a>Poznámky

Výraz ve tvaru

```csharp
x <<= y
```

je vyhodnocen jako

```csharp
x = x << y
```

s tím rozdílem, že `x` se jenom vyhodnotí jednou. [<< Operátor](left-shift-operator.md) posune `x` doleva o počet bitů určený `y`.

`<<=` Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [<< operátor](left-shift-operator.md) (naleznete v tématu [operátor](../keywords/operator.md)).

## <a name="example"></a>Příklad

[!code-csharp[csRefOperators#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#12)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
