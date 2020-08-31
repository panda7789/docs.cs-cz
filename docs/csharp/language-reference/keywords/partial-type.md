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
# <a name="partial-type-c-reference"></a><span data-ttu-id="903f9-103">částečný typ (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="903f9-103">partial type (C# Reference)</span></span>

<span data-ttu-id="903f9-104">Definice částečného typu umožňují, aby definice třídy, struktury nebo rozhraní byly rozděleny do více souborů.</span><span class="sxs-lookup"><span data-stu-id="903f9-104">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>

<span data-ttu-id="903f9-105">V *FILE1.cs*:</span><span class="sxs-lookup"><span data-stu-id="903f9-105">In *File1.cs*:</span></span>

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

<span data-ttu-id="903f9-106">V *File2.cs* deklaraci:</span><span class="sxs-lookup"><span data-stu-id="903f9-106">In *File2.cs* the declaration:</span></span>

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a><span data-ttu-id="903f9-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="903f9-107">Remarks</span></span>

<span data-ttu-id="903f9-108">Rozdělení třídy, struktury nebo typu rozhraní do několika souborů může být užitečné při práci s velkými projekty nebo s automaticky generovaným kódem, jako je například, který poskytuje [Návrhář formulářů](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="903f9-108">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span></span> <span data-ttu-id="903f9-109">Částečný typ může obsahovat [částečnou metodu](partial-method.md).</span><span class="sxs-lookup"><span data-stu-id="903f9-109">A partial type may contain a [partial method](partial-method.md).</span></span> <span data-ttu-id="903f9-110">Další informace naleznete v tématu [částečné třídy a metody](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="903f9-110">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="903f9-111">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="903f9-111">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="903f9-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="903f9-112">See also</span></span>

- [<span data-ttu-id="903f9-113">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="903f9-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="903f9-114">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="903f9-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="903f9-115">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="903f9-115">Modifiers</span></span>](index.md)
- [<span data-ttu-id="903f9-116">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="903f9-116">Introduction to Generics</span></span>](../../programming-guide/generics/index.md)
