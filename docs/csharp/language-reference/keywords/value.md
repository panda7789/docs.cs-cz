---
title: kontextové klíčové slovo Value C# – referenční informace
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: 84d0c51ddafb59144f4ba8c6e73412642fa8fa28
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712894"
---
# <a name="value-c-reference"></a>value (Referenční dokumentace jazyka C#)

Kontextové klíčové slovo `value` se používá v přistupujícím objektu `set` v deklaracích [Property](../../programming-guide/classes-and-structs/properties.md) a [indexeru](../../programming-guide/indexers/index.md) . Je podobný vstupnímu parametru metody. Slovo `value` odkazuje na hodnotu, kterou klientský kód pokouší přiřadit vlastnosti nebo indexeru. V následujícím příkladu `MyDerivedClass` obsahuje vlastnost s názvem `Name`, která používá parametr `value` k přiřazení nového řetězce k poli pro zálohování `name`. Z hlediska kódu klienta je operace zapsána jako jednoduché přiřazení.

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

Další informace najdete v článcích věnovaném [vlastnostem](../../programming-guide/classes-and-structs/properties.md) a [Indexeres](../../programming-guide/indexers/index.md) .

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
