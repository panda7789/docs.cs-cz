---
title: Implicitně zadaný pole – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicitly-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 943760af30422cd333fdff65cdf678108c9d9564
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705714"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a><span data-ttu-id="9c25e-102">Implicitně typovaná pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="9c25e-102">Implicitly Typed Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="9c25e-103">Můžete vytvořit implicitně zadané pole, ve kterém je typ instance pole odvozen z prvků určených v inicializátoru pole.</span><span class="sxs-lookup"><span data-stu-id="9c25e-103">You can create an implicitly-typed array in which the type of the array instance is inferred from the elements specified in the array initializer.</span></span> <span data-ttu-id="9c25e-104">Pravidla pro všechny implicitně zadané proměnné platí také pro implicitně zadaných polí.</span><span class="sxs-lookup"><span data-stu-id="9c25e-104">The rules for any implicitly-typed variable also apply to implicitly-typed arrays.</span></span> <span data-ttu-id="9c25e-105">Další informace naleznete [v tématu Implicitně zadané místní proměnné](../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="9c25e-105">For more information, see [Implicitly Typed Local Variables](../classes-and-structs/implicitly-typed-local-variables.md).</span></span>

<span data-ttu-id="9c25e-106">Implicitně zadávaná pole se obvykle používají ve výrazech dotazu spolu s anonymními typy a inicializátory objektů a kolekcí.</span><span class="sxs-lookup"><span data-stu-id="9c25e-106">Implicitly-typed arrays are usually used in query expressions together with anonymous types and object and collection initializers.</span></span>

<span data-ttu-id="9c25e-107">Následující příklady ukazují, jak vytvořit implicitně zadané pole:</span><span class="sxs-lookup"><span data-stu-id="9c25e-107">The following examples show how to create an implicitly-typed array:</span></span>

[!code-csharp[csProgGuideLINQ#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#37)]

<span data-ttu-id="9c25e-108">V předchozím příkladu všimněte si, že s implicitně zadanými poli se na levé straně inicializačního příkazu nepoužívají žádné hranaté závorky.</span><span class="sxs-lookup"><span data-stu-id="9c25e-108">In the previous example, notice that with implicitly-typed arrays, no square brackets are used on the left side of the initialization statement.</span></span> <span data-ttu-id="9c25e-109">Všimněte si také, že zubaté pole jsou inicializovány pomocí `new []` stejně jako jednorozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="9c25e-109">Note also that jagged arrays are initialized by using `new []` just like single-dimension arrays.</span></span>

## <a name="implicitly-typed-arrays-in-object-initializers"></a><span data-ttu-id="9c25e-110">Implicitně zadaný pole v inicializátorech objektů</span><span class="sxs-lookup"><span data-stu-id="9c25e-110">Implicitly-typed Arrays in Object Initializers</span></span>

<span data-ttu-id="9c25e-111">Při vytváření anonymnítyp, který obsahuje pole, musí být pole implicitně zadáno do inicializátoru objektu.</span><span class="sxs-lookup"><span data-stu-id="9c25e-111">When you create an anonymous type that contains an array, the array must be implicitly typed in the type's object initializer.</span></span> <span data-ttu-id="9c25e-112">V následujícím příkladu `contacts` je implicitně zadané pole anonymních typů, z `PhoneNumbers`nichž každý obsahuje pole s názvem .</span><span class="sxs-lookup"><span data-stu-id="9c25e-112">In the following example, `contacts` is an implicitly-typed array of anonymous types, each of which contains an array named `PhoneNumbers`.</span></span> <span data-ttu-id="9c25e-113">Všimněte `var` si, že klíčové slovo se nepoužívá uvnitř inicializátory objektu.</span><span class="sxs-lookup"><span data-stu-id="9c25e-113">Note that the `var` keyword is not used inside the object initializers.</span></span>

[!code-csharp[csProgGuideLINQ#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#38)]

## <a name="see-also"></a><span data-ttu-id="9c25e-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="9c25e-114">See also</span></span>

- [<span data-ttu-id="9c25e-115">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9c25e-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9c25e-116">Implicitně typované lokální proměnné</span><span class="sxs-lookup"><span data-stu-id="9c25e-116">Implicitly Typed Local Variables</span></span>](../classes-and-structs/implicitly-typed-local-variables.md)
- [<span data-ttu-id="9c25e-117">Pole</span><span class="sxs-lookup"><span data-stu-id="9c25e-117">Arrays</span></span>](./index.md)
- [<span data-ttu-id="9c25e-118">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="9c25e-118">Anonymous Types</span></span>](../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="9c25e-119">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="9c25e-119">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="9c25e-120">Var</span><span class="sxs-lookup"><span data-stu-id="9c25e-120">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="9c25e-121">LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9c25e-121">LINQ in C#</span></span>](../../linq/index.md)
