---
description: výraz nameof – Referenční dokumentace jazyka C#
title: výraz nameof – Referenční dokumentace jazyka C#
ms.date: 04/23/2020
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 04109cde2a1f9146bf9bb44f301272808797ded0
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118309"
---
# <a name="nameof-expression-c-reference"></a>nameof – výraz (Referenční dokumentace jazyka C#)

`nameof`Výraz vytvoří název proměnné, typu nebo členu jako řetězcové konstanty:

[!code-csharp-interactive[nameof expression](snippets/shared/NameOfOperator.cs#Examples)]

Jak ukazuje předchozí příklad, v případě typu a oboru názvů není vytvořen název obvykle [plně kvalifikovaný](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).

V případě [doslovnéch identifikátorů](../tokens/verbatim.md)není `@` znak součástí názvu, jak ukazuje následující příklad:

[!code-csharp-interactive[nameof verbatim](snippets/shared/NameOfOperator.cs#Verbatim)]

`nameof`Výraz je vyhodnocen v době kompilace a nemá žádný vliv na dobu běhu.

Výraz lze použít `nameof` k zajištění udržovatelnosti kódu kontroly argumentu:

[!code-csharp[nameof and argument check](snippets/shared/NameOfOperator.cs#ExceptionMessage)]

`nameof`Výraz je k dispozici v C# 6 a novějším.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Expressions nameof](~/_csharplang/spec/expressions.md#nameof-expressions) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory a výrazy v C#](index.md)
