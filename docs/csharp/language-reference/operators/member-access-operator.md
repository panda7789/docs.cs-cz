---
title: . Operator - C# odkaz
ms.custom: seodec18
ms.date: 02/25/2019
f1_keywords:
- ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
ms.openlocfilehash: 2661676d53deb874c5e5a90b4443b301730e09df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61689200"
---
# <a name="-operator-c-reference"></a>. operator (Referenční dokumentace jazyka C#)

Tečka, `.`, se obvykle používá pro přístup ke členu.

Můžete použít `.` token pro přístup k oboru názvů nebo typ, jak ukazují následující příklady:

- Použití `.` pro přístup k vnořené oboru názvů v oboru názvů, jako následující příklad [ `using` směrnice](../keywords/using-directive.md) ukazuje:

  [!code-csharp[nested namespaces](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#NestedNamespace)]

- Použití `.` do formuláře *kvalifikovaný název* pro přístup k typu v rámci oboru názvů, jak ukazuje následující kód:

  [!code-csharp[qualified name](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#QualifiedName)]

  Použít [ `using` směrnice](../keywords/using-directive.md) provést volitelné použijte kvalifikované názvy.

- Použití `.` přístup [členy typu](../../programming-guide/classes-and-structs/index.md#members), statické a nestatické, pokud jako ukazuje následující kód:

  [!code-csharp-interactive[type members](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#TypeMemberAccess)]

Můžete také použít `.` k vyvolání [– metoda rozšíření](../../programming-guide/classes-and-structs/extension-methods.md).

## <a name="operator-overloadability"></a>Overloadability – operátor

Operátor `.` nemohou být přetíženy.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [přístup ke členu](~/_csharplang/spec/expressions.md#member-access) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- [?. a? operátory]](null-conditional-operators.md)