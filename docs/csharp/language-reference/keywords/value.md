---
title: kontextové klíčové slovo value – odkaz jazyka C#
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: 84d0c51ddafb59144f4ba8c6e73412642fa8fa28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712894"
---
# <a name="value-c-reference"></a>value (Referenční dokumentace jazyka C#)

Kontextové klíčové `value` slovo se `set` používá v přistupujícíobjekt v [deklarace vlastnosta](../../programming-guide/classes-and-structs/properties.md) a [indexeru.](../../programming-guide/indexers/index.md) Je podobný vstupní parametr metody. Slovo `value` odkazuje na hodnotu, kterou se klientský kód pokouší přiřadit vlastnosti nebo indexeru. V následujícím příkladu `MyDerivedClass` má `Name` vlastnost s `value` názvem, která používá parametr `name`přiřadit nový řetězec do záložního pole . Z hlediska klientského kódu je operace zapsána jako jednoduché přiřazení.

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

Další informace naleznete v [článcích Vlastnosti](../../programming-guide/classes-and-structs/properties.md) a [indexery.](../../programming-guide/indexers/index.md)

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
