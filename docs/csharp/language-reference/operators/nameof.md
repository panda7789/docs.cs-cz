---
title: operátor nameof - C# odkaz
ms.custom: seodec18
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 945a8a8ff6d96cb505fa10e85c21a93347661a23
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238690"
---
# <a name="nameof-operator-c-reference"></a>operátor nameof (C# odkaz)

`nameof` Operátor získá název proměnné, typ nebo člena jako řetězcová konstanta:

[!code-csharp-interactive[nameof operator](~/samples/csharp/language-reference/operators/NameOfOperator.cs#Examples)]

Jak ukazuje předchozí příklad, v případě typu a obor názvů, název vyprodukované není obvykle [úplný](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).

`nameof` Operátor je vyhodnocen v době kompilace a nemá žádný vliv za běhu.

Můžete použít `nameof` operátor provádět jednodušší údržbu argument Kontrola kódu:

[!code-csharp[nameof and argument check](~/samples/csharp/language-reference/operators/NameOfOperator.cs#ExceptionMessage)]

`nameof` Operátor je k dispozici v C# 6 nebo novější.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [výrazy Nameof](~/_csharplang/spec/expressions.md#nameof-expressions) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#referenční dokumentace](../index.md)
- [Operátory jazyka C#](index.md)
