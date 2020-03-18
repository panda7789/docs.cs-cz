---
title: částečný typ - odkaz jazyka C#
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 551145b9cdf5fa24f3ae365665e8ff06cf5e9307
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715211"
---
# <a name="partial-type-c-reference"></a><span data-ttu-id="28e99-102">částečný typ (odkaz C#</span><span class="sxs-lookup"><span data-stu-id="28e99-102">partial type (C# Reference)</span></span>

<span data-ttu-id="28e99-103">Definice částečného typu umožňují rozdělit definici třídy, struktury nebo rozhraní do více souborů.</span><span class="sxs-lookup"><span data-stu-id="28e99-103">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>

<span data-ttu-id="28e99-104">V *File1.cs*:</span><span class="sxs-lookup"><span data-stu-id="28e99-104">In *File1.cs*:</span></span>

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

<span data-ttu-id="28e99-105">V *File2.cs* prohlášení:</span><span class="sxs-lookup"><span data-stu-id="28e99-105">In *File2.cs* the declaration:</span></span>

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a><span data-ttu-id="28e99-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="28e99-106">Remarks</span></span>

<span data-ttu-id="28e99-107">Rozdělení třídy, struktury nebo typu rozhraní na několik souborů může být užitečné při práci s velkými projekty nebo s automaticky generovaným kódem, například kódem poskytovaným [návrhářem formulářů systému Windows](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="28e99-107">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span></span> <span data-ttu-id="28e99-108">Částečný typ může obsahovat [částečnou metodu](partial-method.md).</span><span class="sxs-lookup"><span data-stu-id="28e99-108">A partial type may contain a [partial method](partial-method.md).</span></span> <span data-ttu-id="28e99-109">Další informace naleznete [v tématu Částečné třídy a metody](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="28e99-109">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="28e99-110">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="28e99-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="28e99-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="28e99-111">See also</span></span>

- [<span data-ttu-id="28e99-112">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="28e99-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="28e99-113">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="28e99-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="28e99-114">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="28e99-114">Modifiers</span></span>](index.md)
- [<span data-ttu-id="28e99-115">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="28e99-115">Introduction to Generics</span></span>](../../programming-guide/generics/index.md)
