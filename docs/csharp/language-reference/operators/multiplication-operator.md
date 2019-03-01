---
title: '* Operator - C# odkaz'
ms.custom: seodec18
ms.date: 02/26/2019
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: a5e120d26614f1e38cc2f2db02949552140b594e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977341"
---
# <a name="-operator-c-reference"></a>* – operátor (C# odkaz)

`*` Operátor je podporován ve dvou formách: Unární operátor dereference ukazatele nebo operátor binárního násobení.

## <a name="pointer-indirection-operator"></a>Operátor dereference ukazatele

Použít unární `*` operátoru získat proměnnou, na kterou ukazuje operand typu ukazatele. Další informace najdete v tématu [postupy: získávání hodnoty proměnné ukazatele](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-value-of-a-pointer-variable.md).

Operátor dereference ukazatele `*` vyžaduje [nebezpečné](../keywords/unsafe.md) kontextu.

## <a name="multiplication-operator"></a>Operátor násobení

Pro číselné typy `*` operátor vypočítá součin z operandů:

[!code-csharp-interactive[multiplication](~/samples/snippets/csharp/language-reference/operators/MultiplicationExamples.cs#Multiply)]

## <a name="operator-overloadability"></a>Overloadability – operátor

Uživatelem definované typy lze [přetížení](../keywords/operator.md) binární soubor `*` operátor. Když binární soubor `*` je operátor přetížen, [operátor přiřazení násobení](multiplication-assignment-operator.md) `*=` je také implicitně přetížená.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [dereferenci ukazatele](~/_csharplang/spec/unsafe-code.md#pointer-indirection) a [operátor násobení](~/_csharplang/spec/expressions.md#multiplication-operator) oddíly [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)