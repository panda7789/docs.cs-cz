---
title: -&gt; Operator - C# odkaz
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: bb1ccd026f403e68565c5c7681943d8017578d01
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53234887"
---
# <a name="-gt-operator-c-reference"></a>-&gt; – Operátor (referenční dokumentace jazyka C#)

Operátor přístupu členů ukazatel `->` kombinuje ukazatel nepřímý odkaz a členské přístup.

Pokud `x` je ukazatel typu `T*` a `y` je přístupný člen `T`, výraz ve tvaru

```csharp
x->y
```

je ekvivalentem

```csharp
(*x).y
```

`->` Operátor vyžaduje [nebezpečné](../keywords/unsafe.md) kontextu.

Další informace najdete v tématu [postupy: přístup ke členu pomocí ukazatele](../../programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md).

## <a name="operator-overloadability"></a>Overloadability – operátor

`->` Operátor nelze přetížit.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [přístupu k členovi](~/_csharplang/spec/unsafe-code.md#pointer-member-access) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)
