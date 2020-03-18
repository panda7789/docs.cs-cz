---
title: nameof operátor - c# odkaz
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof operator [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: ffbc801acf61bf72db1c88912dc2142a478fa280
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846269"
---
# <a name="nameof-operator-c-reference"></a>nameof operátor (odkaz C# )

Operátor `nameof` získá název proměnné, typu nebo člena jako řetězcovou konstantu:

[!code-csharp-interactive[nameof operator](snippets/NameOfOperator.cs#Examples)]

Jak ukazuje předchozí příklad, v případě typu a oboru názvů není produkovaný název obvykle [plně kvalifikovaný](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).

Operátor `nameof` je vyhodnocován v době kompilace a nemá žádný vliv v době běhu.

Pomocí operátoru `nameof` můžete vytvořit kód pro kontrolu argumentů, který bude moci být udržovatelný:

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

Operátor `nameof` je k dispozici v C# 6 a novější.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
