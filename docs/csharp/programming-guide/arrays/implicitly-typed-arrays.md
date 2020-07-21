---
title: Implicitně typované pole – Průvodce programováním v C#
description: Typ implicitně typovaného pole v jazyce C# je odvozen z prvků v inicializátoru pole. Ve výrazech dotazů použijte implicitně typované pole.
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicitly-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 1f14f68207dfb79c92eaa01ac2a8ffaa08facc03
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474706"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a><span data-ttu-id="8bf79-104">Implicitně typovaná pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="8bf79-104">Implicitly Typed Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="8bf79-105">Můžete vytvořit implicitně typované pole, ve kterém je typ instance pole odvozen z prvků zadaných v inicializátoru pole.</span><span class="sxs-lookup"><span data-stu-id="8bf79-105">You can create an implicitly-typed array in which the type of the array instance is inferred from the elements specified in the array initializer.</span></span> <span data-ttu-id="8bf79-106">Pravidla pro všechny implicitně typované proměnné platí také pro implicitně typované pole.</span><span class="sxs-lookup"><span data-stu-id="8bf79-106">The rules for any implicitly-typed variable also apply to implicitly-typed arrays.</span></span> <span data-ttu-id="8bf79-107">Další informace naleznete v tématu [implicitně typované lokální proměnné](../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="8bf79-107">For more information, see [Implicitly Typed Local Variables](../classes-and-structs/implicitly-typed-local-variables.md).</span></span>

<span data-ttu-id="8bf79-108">Implicitně typované pole se obvykle používají ve výrazech dotazů společně s anonymními typy a Inicializátory objektů a kolekcí.</span><span class="sxs-lookup"><span data-stu-id="8bf79-108">Implicitly-typed arrays are usually used in query expressions together with anonymous types and object and collection initializers.</span></span>

<span data-ttu-id="8bf79-109">Následující příklady ukazují, jak vytvořit implicitně typované pole:</span><span class="sxs-lookup"><span data-stu-id="8bf79-109">The following examples show how to create an implicitly-typed array:</span></span>

[!code-csharp[csProgGuideLINQ#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#37)]

<span data-ttu-id="8bf79-110">V předchozím příkladu si všimněte, že s implicitně typovými poli nejsou na levé straně příkazu Initialization použity žádné hranaté závorky.</span><span class="sxs-lookup"><span data-stu-id="8bf79-110">In the previous example, notice that with implicitly-typed arrays, no square brackets are used on the left side of the initialization statement.</span></span> <span data-ttu-id="8bf79-111">Všimněte si také, že vícenásobná pole jsou inicializována pomocí `new []` stejně jako pole s jednou dimenzí.</span><span class="sxs-lookup"><span data-stu-id="8bf79-111">Note also that jagged arrays are initialized by using `new []` just like single-dimension arrays.</span></span>

## <a name="implicitly-typed-arrays-in-object-initializers"></a><span data-ttu-id="8bf79-112">Implicitně typované pole v inicializátorech objektů</span><span class="sxs-lookup"><span data-stu-id="8bf79-112">Implicitly-typed Arrays in Object Initializers</span></span>

<span data-ttu-id="8bf79-113">Při vytváření anonymního typu, který obsahuje pole, musí být pole implicitně zadáno v inicializátoru objektu typu.</span><span class="sxs-lookup"><span data-stu-id="8bf79-113">When you create an anonymous type that contains an array, the array must be implicitly typed in the type's object initializer.</span></span> <span data-ttu-id="8bf79-114">V následujícím příkladu `contacts` je implicitně typované pole anonymních typů, z nichž každý obsahuje pole s názvem `PhoneNumbers` .</span><span class="sxs-lookup"><span data-stu-id="8bf79-114">In the following example, `contacts` is an implicitly-typed array of anonymous types, each of which contains an array named `PhoneNumbers`.</span></span> <span data-ttu-id="8bf79-115">Všimněte si, že `var` klíčové slovo se v inicializátorech objektů nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="8bf79-115">Note that the `var` keyword is not used inside the object initializers.</span></span>

[!code-csharp[csProgGuideLINQ#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#38)]

## <a name="see-also"></a><span data-ttu-id="8bf79-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="8bf79-116">See also</span></span>

- [<span data-ttu-id="8bf79-117">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="8bf79-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8bf79-118">Implicitně typované lokální proměnné</span><span class="sxs-lookup"><span data-stu-id="8bf79-118">Implicitly Typed Local Variables</span></span>](../classes-and-structs/implicitly-typed-local-variables.md)
- [<span data-ttu-id="8bf79-119">Pole</span><span class="sxs-lookup"><span data-stu-id="8bf79-119">Arrays</span></span>](./index.md)
- [<span data-ttu-id="8bf79-120">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="8bf79-120">Anonymous Types</span></span>](../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="8bf79-121">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="8bf79-121">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="8bf79-122">var</span><span class="sxs-lookup"><span data-stu-id="8bf79-122">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="8bf79-123">LINQ v jazyku C#</span><span class="sxs-lookup"><span data-stu-id="8bf79-123">LINQ in C#</span></span>](../../linq/index.md)
