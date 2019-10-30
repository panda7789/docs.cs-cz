---
title: operátor nameof – C# odkaz
ms.custom: seodec18
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof operator [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: fa858db918cdaf04c757f2741265e359acb74f7b
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036341"
---
# <a name="nameof-operator-c-reference"></a>nameof – operátorC# (Referenční dokumentace)

Operátor `nameof` Získá název proměnné, typu nebo členu jako řetězcové konstanty:

[!code-csharp-interactive[nameof operator](~/samples/csharp/language-reference/operators/NameOfOperator.cs#Examples)]

Jak ukazuje předchozí příklad, v případě typu a oboru názvů není vytvořen název obvykle [plně kvalifikovaný](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).

Operátor `nameof` je vyhodnocen v době kompilace a nemá žádný vliv na dobu běhu.

Operátor `nameof` lze použít k zajištění udržovatelnosti kódu pro kontrolu argumentu:

[!code-csharp[nameof and argument check](~/samples/csharp/language-reference/operators/NameOfOperator.cs#ExceptionMessage)]

Operátor `nameof` je k dispozici C# v 6 nebo novějším.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v části [výrazy nameof](~/_csharplang/spec/expressions.md#nameof-expressions) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
