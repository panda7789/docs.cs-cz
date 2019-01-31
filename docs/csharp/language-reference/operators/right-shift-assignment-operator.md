---
title: '>>= – operátor - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: 8cc341c14ee1b90fde2abb369c187e57b4ce5c00
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278977"
---
# <a name="-operator-c-reference"></a>>> = – operátor (C# odkaz)

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