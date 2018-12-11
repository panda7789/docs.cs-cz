---
title: = – Operátor - C# odkaz
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 2c999e76a9238e6401e89af0faa81967b13a3995
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244385"
---
# <a name="-operator-c-reference"></a>= – operátor (Referenční dokumentace jazyka C#)

Operátor přiřazení `=` hodnota jeho operandu pravé přiřadí proměnné, [vlastnost](../../programming-guide/classes-and-structs/properties.md), nebo [indexer](../../../csharp/programming-guide/indexers/index.md) element Dal jeho levý operand. Výsledkem výrazu přiřazení je hodnota přiřazená k levý operand. Typ operandu pravé musí být stejný jako typ levý operand nebo implicitně převeditelné na ni.

Operátor přiřazení je asociativní zprava, to znamená, výraz ve tvaru

```csharp
a = b = c
```

je vyhodnocen jako

```csharp
a = (b = c)
```

Následující příklad ukazuje použití operátoru přiřazení k přiřazení hodnot k místní proměnné, vlastnosti a elementu indexeru:

[!code-csharp-interactive[assignment operator](~/samples/snippets/csharp/language-reference/operators/AssignmentExamples.cs#Assignments)]

## <a name="ref-assignment-operator"></a>operátoru přiřazení odkazu

Počínaje C# 7.3, můžete pomocí operátoru přiřazení odkazu `= ref` přiřazení [lokální proměnná podle odkazu](../keywords/ref.md#ref-locals) nebo [lokální proměnná podle odkazu jen pro čtení](../keywords/ref.md#ref-readonly-locals) proměnné. Následující příklad ukazuje použití operátoru přiřazení odkazu:

[!code-csharp[ref assignment operator](~/samples/snippets/csharp/language-reference/operators/AssignmentExamples.cs#RefAssignment)]

V případě operátoru přiřazení odkazu typ levého operandu a pravý operand musí být stejné.

Další informace najdete v tématu [Poznámka návrh funkce](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.3/ref-local-reassignment.md).

## <a name="operator-overloadability"></a>Overloadability – operátor

Uživatelem definovaný typ nejde přetížit operátor přiřazení. Uživatelem definovaný typ však můžete definovat implicitní převod na jiného typu. Tímto způsobem hodnota uživatelem definovaného typu lze přiřadit k proměnné, vlastnosti nebo elementu indexeru jiného typu. Další informace najdete v tématu [implicitní](../keywords/implicit.md) článku – klíčové slovo.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [jednoduché přiřazení](~/_csharplang/spec/expressions.md#simple-assignment) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- [REF – klíčové slovo](../keywords/ref.md)
