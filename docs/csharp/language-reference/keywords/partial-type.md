---
title: částečný odkaz na C# typ
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 551145b9cdf5fa24f3ae365665e8ff06cf5e9307
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715211"
---
# <a name="partial-type-c-reference"></a>částečný typ (C# Referenční dokumentace)

Definice částečného typu umožňují, aby definice třídy, struktury nebo rozhraní byly rozděleny do více souborů.

V *FILE1.cs*:

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

V *File2.cs* deklaraci:

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a>Poznámky

Rozdělení třídy, struktury nebo typu rozhraní do několika souborů může být užitečné při práci s velkými projekty nebo s automaticky generovaným kódem, jako je například, který poskytuje [Návrhář formulářů](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md). Částečný typ může obsahovat [částečnou metodu](partial-method.md). Další informace naleznete v tématu [částečné třídy a metody](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Modifikátory](index.md)
- [Úvod do obecných typů](../../programming-guide/generics/index.md)
