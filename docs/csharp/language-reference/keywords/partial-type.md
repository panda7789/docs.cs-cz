---
description: částečný typ – reference jazyka C#
title: částečný typ – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 8ae98805eea7231e3a15cb74e636313e796796a2
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89117984"
---
# <a name="partial-type-c-reference"></a>částečný typ (Referenční dokumentace jazyka C#)

Definice částečného typu umožňují, aby definice třídy, struktury nebo rozhraní byly rozděleny do více souborů.

V *FILE1.cs*:

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

V *File2.cs* deklaraci:

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a>Poznámky

Rozdělení třídy, struktury nebo typu rozhraní do několika souborů může být užitečné při práci s velkými projekty nebo s automaticky generovaným kódem, jako je například, který poskytuje [Návrhář formulářů](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md). Částečný typ může obsahovat [částečnou metodu](partial-method.md). Další informace naleznete v tématu [částečné třídy a metody](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Modifikátory](index.md)
- [Úvod do obecných typů](../../programming-guide/generics/index.md)
