---
title: '* = – Operátor - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 2038f3b55d46f3503496275b3d25b17663b8c1db
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333431"
---
# <a name="-operator-c-reference"></a>\*= – Operátor (referenční dokumentace jazyka C#)

Operátor přiřazení binárního násobení.

## <a name="remarks"></a>Poznámky

Pomocí výrazu `*=` operátor přiřazení, jako například

```csharp
x *= y
```

je ekvivalentem

```csharp
x = x * y
```

s tím rozdílem, že `x` se jenom vyhodnotí jednou. [ \* Operátor](multiplication-operator.md) předdefinovaných číselných typů k provedení násobení.

`*=` Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [ \* operátor](multiplication-operator.md) (naleznete v tématu [operátor](../keywords/operator.md)).

## <a name="example"></a>Příklad

[!code-csharp[csRefOperators#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#13)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
