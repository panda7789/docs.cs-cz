---
title: Hodnota kontextové klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: ee80888a57e999fa44e891dd6e0d64caa698009c
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612059"
---
# <a name="value-c-reference"></a>value (Referenční dokumentace jazyka C#)

Kontextové klíčové slovo `value` se používá v přístupový objekt set v deklaracích běžnou vlastností. Je to podobné do vstupního parametru pro metodu. Slovo `value` odkazuje na hodnotu, která kód klienta se pokouší přiřadit vlastnosti. V následujícím příkladu `MyDerivedClass` má vlastnost s názvem `Name` , která používá `value` parametr přiřadit nový řetězec pro pole zálohování `name`. Z hlediska kódu klienta je zapsán operace jako jednoduchého přiřazení.

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

Další informace o použití `value`, naleznete v tématu [vlastnosti](../../programming-guide/classes-and-structs/properties.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)