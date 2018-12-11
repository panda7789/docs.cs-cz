---
title: ~ – Operátor - C# odkaz
ms.custom: seodec18
ms.date: 11/05/2018
f1_keywords:
- ~_CSharpKeyword
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
ms.openlocfilehash: 57e5baee423c0b5d9292d0ad4cbf909646eb3a38
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235716"
---
# <a name="-operator-c-reference"></a>~ – operátor (Referenční dokumentace jazyka C#)

Operátor bitového doplňku `~` je unární operátor, který vytvoří bitový doplněk svého operandu přehozením každý bit. Podporují všechny typy celých čísel `~` operátor.

> [!NOTE]
> `~` Symbol se také používá k deklaraci finalizační metody. Další informace najdete v tématu [finalizační metody](../../programming-guide/classes-and-structs/destructors.md).

Následující příklad ukazuje použití `~` operátor:

[!code-csharp-interactive[bitwise NOT](~/samples/snippets/csharp/language-reference/operators/BitwiseComplementExamples.cs#Example)]

> [!NOTE]
> V předchozím příkladu binární literály: [zavedený C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) a [rozšířené v C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).

## <a name="operator-overloadability"></a>Overloadability – operátor

Uživatelem definované typy lze [přetížení](../keywords/operator.md) `~` operátor.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [operátor bitového doplňku](~/_csharplang/spec/expressions.md#bitwise-complement-operator) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- [Finalizační metody](../../programming-guide/classes-and-structs/destructors.md)
- [& – operátor](and-operator.md)
- [| – operátor](or-operator.md)
- [^ – operátor](xor-operator.md)
