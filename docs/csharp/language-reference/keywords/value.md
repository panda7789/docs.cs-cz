---
description: kontextové klíčové slovo Value – reference jazyka C#
title: kontextové klíčové slovo Value – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: f72e9f097880d9de725a85a0973001baaefd9a9c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141735"
---
# <a name="value-c-reference"></a><span data-ttu-id="8e252-103">value (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8e252-103">value (C# Reference)</span></span>

<span data-ttu-id="8e252-104">Klíčové slovo kontextové `value` se používá v `set` přístupovém objektu v deklaracích [Property](../../programming-guide/classes-and-structs/properties.md) a [indexeru](../../programming-guide/indexers/index.md) .</span><span class="sxs-lookup"><span data-stu-id="8e252-104">The contextual keyword `value` is used in the `set` accessor in [property](../../programming-guide/classes-and-structs/properties.md) and [indexer](../../programming-guide/indexers/index.md) declarations.</span></span> <span data-ttu-id="8e252-105">Je podobný vstupnímu parametru metody.</span><span class="sxs-lookup"><span data-stu-id="8e252-105">It is similar to an input parameter of a method.</span></span> <span data-ttu-id="8e252-106">Slovo `value` odkazuje na hodnotu, kterou klientský kód pokouší přiřadit vlastnosti nebo indexeru.</span><span class="sxs-lookup"><span data-stu-id="8e252-106">The word `value` references the value that client code is attempting to assign to the property or indexer.</span></span> <span data-ttu-id="8e252-107">V následujícím příkladu `MyDerivedClass` má vlastnost s názvem `Name` , která používá `value` parametr k přiřazení nového řetězce k poli pro zálohování `name` .</span><span class="sxs-lookup"><span data-stu-id="8e252-107">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="8e252-108">Z hlediska kódu klienta je operace zapsána jako jednoduché přiřazení.</span><span class="sxs-lookup"><span data-stu-id="8e252-108">From the point of view of client code, the operation is written as a simple assignment.</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="8e252-109">Další informace najdete v článcích věnovaném [vlastnostem](../../programming-guide/classes-and-structs/properties.md) a [Indexeres](../../programming-guide/indexers/index.md) .</span><span class="sxs-lookup"><span data-stu-id="8e252-109">For more information, see the [Properties](../../programming-guide/classes-and-structs/properties.md) and [Indexeres](../../programming-guide/indexers/index.md) articles.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8e252-110">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8e252-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="8e252-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e252-111">See also</span></span>

- [<span data-ttu-id="8e252-112">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8e252-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8e252-113">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="8e252-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8e252-114">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8e252-114">C# Keywords</span></span>](index.md)
