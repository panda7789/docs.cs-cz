---
title: klíčové slovo pro operátor (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords:
- operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
ms.openlocfilehash: c3bfada235993670bf158fe9803a09707b2b3251
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929869"
---
# <a name="operator-c-reference"></a>operator (Referenční dokumentace jazyka C#)

Použití `operator` – klíčové slovo přetížení předdefinovaný operátor nebo k poskytování uživatelsky definovaný převod v deklaraci třídy nebo struktury.

## <a name="example"></a>Příklad

Níže je velmi zjednodušený třídu desetinná čísla. Přetěžuje `+` a `*` operátory provádět desetinné sčítání a násobení a také poskytuje operátor převodu které převádí `Fraction` typ, který `double` typu.

[!code-csharp[csrefKeywordsConversion#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#6)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [implicit](implicit.md)
- [explicit](explicit.md)
- [Postupy: Implementace uživatelem definovaných převodů mezi strukturami](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
