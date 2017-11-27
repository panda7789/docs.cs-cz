---
title: "C# pole - přehled používání jazyka C#"
description: "Pole jsou nejzákladnější typ kolekce v jazyce C#"
keywords: "Rozhraní .NET, csharp, pole, kolekce"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: d7d5ae9f99ba1629a6f0aec57bebf74853cab27f
ms.sourcegitcommit: a19548e5167cbe7e9e58df4ffd8c3b23f17d5c7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2017
---
# <a name="arrays"></a><span data-ttu-id="b8de0-104">Pole</span><span class="sxs-lookup"><span data-stu-id="b8de0-104">Arrays</span></span>

<span data-ttu-id="b8de0-105">***Pole*** je datová struktura, která obsahuje počet proměnných, které jsou přístupné prostřednictvím počítaný indexy.</span><span class="sxs-lookup"><span data-stu-id="b8de0-105">An ***array*** is a data structure that contains a number of variables that are accessed through computed indices.</span></span> <span data-ttu-id="b8de0-106">Proměnné, které jsou obsaženy v poli, označované taky jako ***elementy*** pole, jsou všechny stejného typu a se nazývá tento typ ***typ elementu*** pole.</span><span class="sxs-lookup"><span data-stu-id="b8de0-106">The variables contained in an array, also called the ***elements*** of the array, are all of the same type, and this type is called the ***element type*** of the array.</span></span>

<span data-ttu-id="b8de0-107">Typy polí jsou odkazové typy a deklarace proměnné pole jednoduše vyčleňuje místa pro odkaz na pole instance.</span><span class="sxs-lookup"><span data-stu-id="b8de0-107">Array types are reference types, and the declaration of an array variable simply sets aside space for a reference to an array instance.</span></span> <span data-ttu-id="b8de0-108">Skutečné pole vytváření instancí dynamicky za běhu pomocí nové operátoru.</span><span class="sxs-lookup"><span data-stu-id="b8de0-108">Actual array instances are created dynamically at runtime using the new operator.</span></span> <span data-ttu-id="b8de0-109">Určuje operaci nového ***délka*** nové pole instance, kterou pak vyřešen po dobu jeho existence instance.</span><span class="sxs-lookup"><span data-stu-id="b8de0-109">The new operation specifies the ***length*** of the new array instance, which is then fixed for the lifetime of the instance.</span></span> <span data-ttu-id="b8de0-110">Indexy elementů rozsah pole z `0` k `Length - 1`.</span><span class="sxs-lookup"><span data-stu-id="b8de0-110">The indices of the elements of an array range from `0` to `Length - 1`.</span></span> <span data-ttu-id="b8de0-111">`new` Operátor automaticky inicializuje prvků pole na jejich výchozí hodnoty, které je třeba nulu pro všechny číselnými typy a `null` pro všechny typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="b8de0-111">The `new` operator automatically initializes the elements of an array to their default value, which, for example, is zero for all numeric types and `null` for all reference types.</span></span>

<span data-ttu-id="b8de0-112">Následující příklad vytvoří pole `int` elementy, inicializuje pole a vytiskne obsah pole.</span><span class="sxs-lookup"><span data-stu-id="b8de0-112">The following example creates an array of `int` elements, initializes the array, and prints out the contents of the array.</span></span>

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

<span data-ttu-id="b8de0-113">Tento příklad vytvoří a bude pracovat ***jednorozměrná pole***.</span><span class="sxs-lookup"><span data-stu-id="b8de0-113">This example creates and operates on a ***single-dimensional array***.</span></span> <span data-ttu-id="b8de0-114">C# také podporuje ***vícerozměrných polí***.</span><span class="sxs-lookup"><span data-stu-id="b8de0-114">C# also supports ***multi-dimensional arrays***.</span></span> <span data-ttu-id="b8de0-115">Zadejte počet rozměrů pole, také známé jako ***pořadí*** typ pole, je jedna plus počet čárkami zapsána mezi hranaté závorky typu pole.</span><span class="sxs-lookup"><span data-stu-id="b8de0-115">The number of dimensions of an array type, also known as the ***rank*** of the array type, is one plus the number of commas written between the square brackets of the array type.</span></span> <span data-ttu-id="b8de0-116">Následující příklad přiděluje jednorozměrná, dvourozměrná a trojrozměrné, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="b8de0-116">The following example allocates a single-dimensional, a two-dimensional, and a three-dimensional array, respectively.</span></span>

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

<span data-ttu-id="b8de0-117">`a1` Pole obsahuje prvky, 10, `a2` pole obsahuje 50 (10 × 5) elementů a `a3` 100 (10 × 5 × 2) obsahuje pole elementy.</span><span class="sxs-lookup"><span data-stu-id="b8de0-117">The `a1` array contains 10 elements, the `a2` array contains 50 (10 × 5) elements, and the `a3` array contains 100 (10 × 5 × 2) elements.</span></span>
<span data-ttu-id="b8de0-118">Typ elementu typu pole mohou být jakéhokoli typu, včetně typu pole.</span><span class="sxs-lookup"><span data-stu-id="b8de0-118">The element type of an array can be any type, including an array type.</span></span> <span data-ttu-id="b8de0-119">Pole s prvky typu pole se někdy nazývá ***Vícenásobná pole*** protože ne všechny délek element pole mají být stejné.</span><span class="sxs-lookup"><span data-stu-id="b8de0-119">An array with elements of an array type is sometimes called a ***jagged array*** because the lengths of the element arrays do not all have to be the same.</span></span> <span data-ttu-id="b8de0-120">Následující příklad přiděluje pole pole `int`:</span><span class="sxs-lookup"><span data-stu-id="b8de0-120">The following example allocates an array of arrays of `int`:</span></span>

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

<span data-ttu-id="b8de0-121">První řádek vytvoří pole u elementů na tři, každý typ `int[]` a každý s počáteční hodnotou `null`.</span><span class="sxs-lookup"><span data-stu-id="b8de0-121">The first line creates an array with three elements, each of type `int[]` and each with an initial value of `null`.</span></span> <span data-ttu-id="b8de0-122">Další řádek potom inicializujte tři prvky s odkazy na pole jednotlivých instancí různých délek.</span><span class="sxs-lookup"><span data-stu-id="b8de0-122">The subsequent lines then initialize the three elements with references to individual array instances of varying lengths.</span></span>

<span data-ttu-id="b8de0-123">Operátor new umožňuje počáteční hodnoty prvků pole, které mají být zadán pomocí ***inicializátor pole***, což je seznam výrazů zapsána mezi oddělovače `{` a `}`.</span><span class="sxs-lookup"><span data-stu-id="b8de0-123">The new operator permits the initial values of the array elements to be specified using an ***array initializer***, which is a list of expressions written between the delimiters `{` and `}`.</span></span> <span data-ttu-id="b8de0-124">V následujícím příkladu přiděluje a inicializuje `int[]` s tři prvky.</span><span class="sxs-lookup"><span data-stu-id="b8de0-124">The following example allocates and initializes an `int[]` with three elements.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

<span data-ttu-id="b8de0-125">Všimněte si, že je délka pole odvodit z počet výrazů mezi {a}.</span><span class="sxs-lookup"><span data-stu-id="b8de0-125">Note that the length of the array is inferred from the number of expressions between { and }.</span></span> <span data-ttu-id="b8de0-126">Místní proměnné a deklarace pole lze zkrátit další tak, aby typ pole není nutné nutno revidovat.</span><span class="sxs-lookup"><span data-stu-id="b8de0-126">Local variable and field declarations can be shortened further such that the array type does not have to be restated.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

<span data-ttu-id="b8de0-127">Obě v předchozích příkladech jsou ekvivalentní takto:</span><span class="sxs-lookup"><span data-stu-id="b8de0-127">Both of the previous examples are equivalent to the following:</span></span>

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
<span data-ttu-id="b8de0-128">[Předchozí](structs.md)
[další](interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="b8de0-128">[Previous](structs.md)
[Next](interfaces.md)</span></span>
