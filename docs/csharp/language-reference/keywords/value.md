---
title: kontextové klíčové slovo value – odkaz jazyka C#
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: 84d0c51ddafb59144f4ba8c6e73412642fa8fa28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712894"
---
# <a name="value-c-reference"></a><span data-ttu-id="47fe2-102">value (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="47fe2-102">value (C# Reference)</span></span>

<span data-ttu-id="47fe2-103">Kontextové klíčové `value` slovo se `set` používá v přistupujícíobjekt v [deklarace vlastnosta](../../programming-guide/classes-and-structs/properties.md) a [indexeru.](../../programming-guide/indexers/index.md)</span><span class="sxs-lookup"><span data-stu-id="47fe2-103">The contextual keyword `value` is used in the `set` accessor in [property](../../programming-guide/classes-and-structs/properties.md) and [indexer](../../programming-guide/indexers/index.md) declarations.</span></span> <span data-ttu-id="47fe2-104">Je podobný vstupní parametr metody.</span><span class="sxs-lookup"><span data-stu-id="47fe2-104">It is similar to an input parameter of a method.</span></span> <span data-ttu-id="47fe2-105">Slovo `value` odkazuje na hodnotu, kterou se klientský kód pokouší přiřadit vlastnosti nebo indexeru.</span><span class="sxs-lookup"><span data-stu-id="47fe2-105">The word `value` references the value that client code is attempting to assign to the property or indexer.</span></span> <span data-ttu-id="47fe2-106">V následujícím příkladu `MyDerivedClass` má `Name` vlastnost s `value` názvem, která používá parametr `name`přiřadit nový řetězec do záložního pole .</span><span class="sxs-lookup"><span data-stu-id="47fe2-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="47fe2-107">Z hlediska klientského kódu je operace zapsána jako jednoduché přiřazení.</span><span class="sxs-lookup"><span data-stu-id="47fe2-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="47fe2-108">Další informace naleznete v [článcích Vlastnosti](../../programming-guide/classes-and-structs/properties.md) a [indexery.](../../programming-guide/indexers/index.md)</span><span class="sxs-lookup"><span data-stu-id="47fe2-108">For more information, see the [Properties](../../programming-guide/classes-and-structs/properties.md) and [Indexeres](../../programming-guide/indexers/index.md) articles.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="47fe2-109">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="47fe2-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="47fe2-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="47fe2-110">See also</span></span>

- [<span data-ttu-id="47fe2-111">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="47fe2-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="47fe2-112">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="47fe2-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="47fe2-113">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="47fe2-113">C# Keywords</span></span>](index.md)
