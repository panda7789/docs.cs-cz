---
title: částečný typ - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: ed3e18c5981fa52dc2c6ef09bfb666cfa705fede
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239563"
---
# <a name="partial-type-c-reference"></a>částečný typ (referenční dokumentace jazyka C#)

Definice částečného typu umožňují definice třídy, struktury nebo rozhraní který se má rozdělit do více souborů.

V *File1.cs*:

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

V *File2.cs* deklarace:

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a>Poznámky

Rozdělení třídy, struktury nebo rozhraní typ přes několik souborů může být užitečný při práci na velkých projektech nebo pomocí automaticky generovaného kódu, jako je například poskytuje [Návrháře formulářů Windows](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md). Může obsahovat částečného typu [částečná metoda](partial-method.md). Další informace najdete v tématu [částečné třídy a metody](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Modifikátory](modifiers.md)
- [Úvod do obecných typů](../../programming-guide/generics/introduction-to-generics.md)