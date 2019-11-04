---
title: Implicitně typované pole – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicitly-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: ac47ec6e69b7910f474378eebd91d58c171a802e
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419553"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a><span data-ttu-id="69709-102">Implicitně typovaná pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="69709-102">Implicitly Typed Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="69709-103">Můžete vytvořit implicitně typované pole, ve kterém je typ instance pole odvozen z prvků zadaných v inicializátoru pole.</span><span class="sxs-lookup"><span data-stu-id="69709-103">You can create an implicitly-typed array in which the type of the array instance is inferred from the elements specified in the array initializer.</span></span> <span data-ttu-id="69709-104">Pravidla pro všechny implicitně typované proměnné platí také pro implicitně typované pole.</span><span class="sxs-lookup"><span data-stu-id="69709-104">The rules for any implicitly-typed variable also apply to implicitly-typed arrays.</span></span> <span data-ttu-id="69709-105">Další informace naleznete v tématu [implicitně typované lokální proměnné](../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="69709-105">For more information, see [Implicitly Typed Local Variables](../classes-and-structs/implicitly-typed-local-variables.md).</span></span>

<span data-ttu-id="69709-106">Implicitně typované pole se obvykle používají ve výrazech dotazů společně s anonymními typy a Inicializátory objektů a kolekcí.</span><span class="sxs-lookup"><span data-stu-id="69709-106">Implicitly-typed arrays are usually used in query expressions together with anonymous types and object and collection initializers.</span></span>

<span data-ttu-id="69709-107">Následující příklady ukazují, jak vytvořit implicitně typované pole:</span><span class="sxs-lookup"><span data-stu-id="69709-107">The following examples show how to create an implicitly-typed array:</span></span>

[!code-csharp[csProgGuideLINQ#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#37)]

<span data-ttu-id="69709-108">V předchozím příkladu si všimněte, že s implicitně typovými poli nejsou na levé straně příkazu Initialization použity žádné hranaté závorky.</span><span class="sxs-lookup"><span data-stu-id="69709-108">In the previous example, notice that with implicitly-typed arrays, no square brackets are used on the left side of the initialization statement.</span></span> <span data-ttu-id="69709-109">Všimněte si také, že vícenásobná pole jsou inicializována pomocí `new []` stejně jako pole s jednou dimenzí.</span><span class="sxs-lookup"><span data-stu-id="69709-109">Note also that jagged arrays are initialized by using `new []` just like single-dimension arrays.</span></span>

## <a name="implicitly-typed-arrays-in-object-initializers"></a><span data-ttu-id="69709-110">Implicitně typované pole v inicializátorech objektů</span><span class="sxs-lookup"><span data-stu-id="69709-110">Implicitly-typed Arrays in Object Initializers</span></span>

<span data-ttu-id="69709-111">Při vytváření anonymního typu, který obsahuje pole, musí být pole implicitně zadáno v inicializátoru objektu typu.</span><span class="sxs-lookup"><span data-stu-id="69709-111">When you create an anonymous type that contains an array, the array must be implicitly typed in the type's object initializer.</span></span> <span data-ttu-id="69709-112">V následujícím příkladu je `contacts` implicitně typované pole anonymních typů, z nichž každý obsahuje pole s názvem `PhoneNumbers`.</span><span class="sxs-lookup"><span data-stu-id="69709-112">In the following example, `contacts` is an implicitly-typed array of anonymous types, each of which contains an array named `PhoneNumbers`.</span></span> <span data-ttu-id="69709-113">Všimněte si, že klíčové slovo `var` se v inicializátorech objektů nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="69709-113">Note that the `var` keyword is not used inside the object initializers.</span></span>

[!code-csharp[csProgGuideLINQ#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#38)]

## <a name="see-also"></a><span data-ttu-id="69709-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69709-114">See also</span></span>

- [<span data-ttu-id="69709-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="69709-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="69709-116">Implicitně typované lokální proměnné</span><span class="sxs-lookup"><span data-stu-id="69709-116">Implicitly Typed Local Variables</span></span>](../classes-and-structs/implicitly-typed-local-variables.md)
- [<span data-ttu-id="69709-117">Pole</span><span class="sxs-lookup"><span data-stu-id="69709-117">Arrays</span></span>](./index.md)
- [<span data-ttu-id="69709-118">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="69709-118">Anonymous Types</span></span>](../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="69709-119">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="69709-119">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="69709-120">var</span><span class="sxs-lookup"><span data-stu-id="69709-120">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="69709-121">LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="69709-121">LINQ in C#</span></span>](../../linq/index.md)
