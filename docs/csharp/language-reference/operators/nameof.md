---
title: operátor nameof – C# odkaz
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof operator [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: c1d71d52a9222379adc36479715113b181da7133
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712686"
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
