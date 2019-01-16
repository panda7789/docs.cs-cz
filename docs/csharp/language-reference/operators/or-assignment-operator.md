---
title: '| = – operátor - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
ms.openlocfilehash: f4f7806c8679af400a371decd0c367929b3fb81d
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333262"
---
# <a name="-operator-c-reference"></a>| = – operátor (C# odkaz)

Operátor přiřazení OR.

## <a name="remarks"></a>Poznámky

Pomocí výrazu `|=` operátor přiřazení, jako například

```csharp
x |= y
```

je ekvivalentem

```csharp
x = x | y
```

s tím rozdílem, že `x` se jenom vyhodnotí jednou. [ &#124; Operátor](or-operator.md) provádí bitové logické OR operace na celočíselných operandech a logický operátor OR na operandech typu bool.

`|=` Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [ &#124; operátor](or-operator.md) (naleznete v tématu [operátor](../keywords/operator.md)).

## <a name="example"></a>Příklad

[!code-csharp[csRefOperators#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#10)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [C#operátory](index.md)