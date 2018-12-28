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
# <a name="value-c-reference"></a><span data-ttu-id="412e9-102">value (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="412e9-102">value (C# Reference)</span></span>

<span data-ttu-id="412e9-103">Kontextové klíčové slovo `value` se používá v přístupový objekt set v deklaracích běžnou vlastností.</span><span class="sxs-lookup"><span data-stu-id="412e9-103">The contextual keyword `value` is used in the set accessor in ordinary property declarations.</span></span> <span data-ttu-id="412e9-104">Je to podobné do vstupního parametru pro metodu.</span><span class="sxs-lookup"><span data-stu-id="412e9-104">It is similar to an input parameter on a method.</span></span> <span data-ttu-id="412e9-105">Slovo `value` odkazuje na hodnotu, která kód klienta se pokouší přiřadit vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="412e9-105">The word `value` references the value that client code is attempting to assign to the property.</span></span> <span data-ttu-id="412e9-106">V následujícím příkladu `MyDerivedClass` má vlastnost s názvem `Name` , která používá `value` parametr přiřadit nový řetězec pro pole zálohování `name`.</span><span class="sxs-lookup"><span data-stu-id="412e9-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="412e9-107">Z hlediska kódu klienta je zapsán operace jako jednoduchého přiřazení.</span><span class="sxs-lookup"><span data-stu-id="412e9-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="412e9-108">Další informace o použití `value`, naleznete v tématu [vlastnosti](../../programming-guide/classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="412e9-108">For more information about the use of `value`, see [Properties](../../programming-guide/classes-and-structs/properties.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="412e9-109">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="412e9-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="412e9-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="412e9-110">See also</span></span>

- [<span data-ttu-id="412e9-111">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="412e9-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="412e9-112">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="412e9-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="412e9-113">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="412e9-113">C# Keywords</span></span>](index.md)