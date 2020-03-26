---
title: nameof expression - C# odkaz
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 5a68161be7bb03122d2a63ccef4365c5853862b2
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507136"
---
# <a name="nameof-expression-c-reference"></a>nameof expression (odkaz C# )

Výraz `nameof` vytvoří název proměnné, typu nebo člena jako řetězcovou konstantu:

[!code-csharp-interactive[nameof expression](snippets/NameOfOperator.cs#Examples)]

Jak ukazuje předchozí příklad, v případě typu a oboru názvů není produkovaný název obvykle [plně kvalifikovaný](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).

Výraz `nameof` je vyhodnocován v době kompilace a nemá žádný vliv v době běhu.

Výraz můžete `nameof` použít k tomu, aby byl kód pro kontrolu argumentů více udržovatelný:

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

Výraz `nameof` je k dispozici v C# 6 a novější.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
