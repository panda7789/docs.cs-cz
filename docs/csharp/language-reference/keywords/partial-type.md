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
ms.openlocfilehash: db3fc477ddf857146072088e49e76855f5390701
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422713"
---
# <a name="partial-type-c-reference"></a><span data-ttu-id="21886-102">částečný typ (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="21886-102">partial type (C# Reference)</span></span>

<span data-ttu-id="21886-103">Definice částečného typu umožňují definice třídy, struktury nebo rozhraní který se má rozdělit do více souborů.</span><span class="sxs-lookup"><span data-stu-id="21886-103">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>

<span data-ttu-id="21886-104">V *File1.cs*:</span><span class="sxs-lookup"><span data-stu-id="21886-104">In *File1.cs*:</span></span>

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

<span data-ttu-id="21886-105">V *File2.cs* deklarace:</span><span class="sxs-lookup"><span data-stu-id="21886-105">In *File2.cs* the declaration:</span></span>

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a><span data-ttu-id="21886-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="21886-106">Remarks</span></span>

<span data-ttu-id="21886-107">Rozdělení třídy, struktury nebo rozhraní typ přes několik souborů může být užitečný při práci na velkých projektech nebo pomocí automaticky generovaného kódu, jako je například poskytuje [Návrháře formulářů Windows](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="21886-107">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span></span> <span data-ttu-id="21886-108">Může obsahovat částečného typu [částečná metoda](partial-method.md).</span><span class="sxs-lookup"><span data-stu-id="21886-108">A partial type may contain a [partial method](partial-method.md).</span></span> <span data-ttu-id="21886-109">Další informace najdete v tématu [částečné třídy a metody](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="21886-109">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="21886-110">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="21886-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="21886-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="21886-111">See also</span></span>

- [<span data-ttu-id="21886-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="21886-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="21886-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="21886-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="21886-114">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="21886-114">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="21886-115">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="21886-115">Introduction to Generics</span></span>](../../programming-guide/generics/index.md)
