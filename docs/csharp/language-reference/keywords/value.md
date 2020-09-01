---
description: kontextové klíčové slovo Value – reference jazyka C#
title: kontextové klíčové slovo Value – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: f72e9f097880d9de725a85a0973001baaefd9a9c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141735"
---
# <a name="value-c-reference"></a>value (Referenční dokumentace jazyka C#)

Klíčové slovo kontextové `value` se používá v `set` přístupovém objektu v deklaracích [Property](../../programming-guide/classes-and-structs/properties.md) a [indexeru](../../programming-guide/indexers/index.md) . Je podobný vstupnímu parametru metody. Slovo `value` odkazuje na hodnotu, kterou klientský kód pokouší přiřadit vlastnosti nebo indexeru. V následujícím příkladu `MyDerivedClass` má vlastnost s názvem `Name` , která používá `value` parametr k přiřazení nového řetězce k poli pro zálohování `name` . Z hlediska kódu klienta je operace zapsána jako jednoduché přiřazení.

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

Další informace najdete v článcích věnovaném [vlastnostem](../../programming-guide/classes-and-structs/properties.md) a [Indexeres](../../programming-guide/indexers/index.md) .

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
