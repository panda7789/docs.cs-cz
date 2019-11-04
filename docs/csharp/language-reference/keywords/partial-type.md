---
title: částečný odkaz na C# typ
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 7af43a25f88ff0a53e5fa257b13bb1dc8a6d55eb
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422601"
---
# <a name="partial-type-c-reference"></a><span data-ttu-id="0446b-102">částečný typ (C# Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="0446b-102">partial type (C# Reference)</span></span>

<span data-ttu-id="0446b-103">Definice částečného typu umožňují, aby definice třídy, struktury nebo rozhraní byly rozděleny do více souborů.</span><span class="sxs-lookup"><span data-stu-id="0446b-103">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>

<span data-ttu-id="0446b-104">V *FILE1.cs*:</span><span class="sxs-lookup"><span data-stu-id="0446b-104">In *File1.cs*:</span></span>

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

<span data-ttu-id="0446b-105">V *File2.cs* deklaraci:</span><span class="sxs-lookup"><span data-stu-id="0446b-105">In *File2.cs* the declaration:</span></span>

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a><span data-ttu-id="0446b-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0446b-106">Remarks</span></span>

<span data-ttu-id="0446b-107">Rozdělení třídy, struktury nebo typu rozhraní do několika souborů může být užitečné při práci s velkými projekty nebo s automaticky generovaným kódem, jako je například, který poskytuje [Návrhář formulářů](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="0446b-107">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span></span> <span data-ttu-id="0446b-108">Částečný typ může obsahovat [částečnou metodu](partial-method.md).</span><span class="sxs-lookup"><span data-stu-id="0446b-108">A partial type may contain a [partial method](partial-method.md).</span></span> <span data-ttu-id="0446b-109">Další informace naleznete v tématu [částečné třídy a metody](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="0446b-109">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0446b-110">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0446b-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="0446b-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0446b-111">See also</span></span>

- [<span data-ttu-id="0446b-112">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="0446b-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0446b-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0446b-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0446b-114">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="0446b-114">Modifiers</span></span>](index.md)
- [<span data-ttu-id="0446b-115">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="0446b-115">Introduction to Generics</span></span>](../../programming-guide/generics/index.md)
