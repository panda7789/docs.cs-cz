---
title: výraz nameof – Referenční dokumentace jazyka C#
ms.date: 04/23/2020
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: d71acf0cf7d5cdcfa5310455af2120fa1f82d567
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135916"
---
# <a name="nameof-expression-c-reference"></a>nameof – výraz (Referenční dokumentace jazyka C#)

`nameof` Výraz vytvoří název proměnné, typu nebo členu jako řetězcové konstanty:

[!code-csharp-interactive[nameof expression](snippets/NameOfOperator.cs#Examples)]

Jak ukazuje předchozí příklad, v případě typu a oboru názvů není vytvořen název obvykle [plně kvalifikovaný](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).

V případě [doslovnéch identifikátorů](../tokens/verbatim.md)není `@` znak součástí názvu, jak ukazuje následující příklad:

[!code-csharp-interactive[nameof verbatim](snippets/NameOfOperator.cs#Verbatim)]

`nameof` Výraz je vyhodnocen v době kompilace a nemá žádný vliv na dobu běhu.

`nameof` Výraz lze použít k zajištění udržovatelnosti kódu kontroly argumentu:

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

`nameof` Výraz je k dispozici v C# 6 a novějším.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Expressions nameof](~/_csharplang/spec/expressions.md#nameof-expressions) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
