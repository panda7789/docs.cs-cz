---
title: C#Pole – připravuje C# jazyka
description: Pole jsou v základním typem kolekce C# jazyka
ms.date: 08/10/2016
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: 8685e6ad08eb74534cdad499099b3d12da0a497a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706413"
---
# <a name="arrays"></a><span data-ttu-id="1f664-103">Pole</span><span class="sxs-lookup"><span data-stu-id="1f664-103">Arrays</span></span>

<span data-ttu-id="1f664-104">***Pole*** je datová struktura, která obsahuje několik proměnných, které jsou přístupné prostřednictvím vypočítané indexy.</span><span class="sxs-lookup"><span data-stu-id="1f664-104">An ***array*** is a data structure that contains a number of variables that are accessed through computed indices.</span></span> <span data-ttu-id="1f664-105">Proměnné, které jsou obsaženy v poli, tzv. ***prvky*** pole, jsou všechny stejného typu a tento typ se nazývá ***typ elementu*** pole.</span><span class="sxs-lookup"><span data-stu-id="1f664-105">The variables contained in an array, also called the ***elements*** of the array, are all of the same type, and this type is called the ***element type*** of the array.</span></span>

<span data-ttu-id="1f664-106">Typy pole jsou typy odkazů a deklarace proměnné pole jednoduše vyčleňuje místo odkazu na pole instance.</span><span class="sxs-lookup"><span data-stu-id="1f664-106">Array types are reference types, and the declaration of an array variable simply sets aside space for a reference to an array instance.</span></span> <span data-ttu-id="1f664-107">Dynamicky se vytvářejí instance skutečné pole za běhu pomocí operátoru new.</span><span class="sxs-lookup"><span data-stu-id="1f664-107">Actual array instances are created dynamically at runtime using the new operator.</span></span> <span data-ttu-id="1f664-108">Určuje novou operaci ***délka*** nové instance pole, které se potom jsme opravili po dobu životnosti instance.</span><span class="sxs-lookup"><span data-stu-id="1f664-108">The new operation specifies the ***length*** of the new array instance, which is then fixed for the lifetime of the instance.</span></span> <span data-ttu-id="1f664-109">Indexy prvků v rozsahu pole z `0` k `Length - 1`.</span><span class="sxs-lookup"><span data-stu-id="1f664-109">The indices of the elements of an array range from `0` to `Length - 1`.</span></span> <span data-ttu-id="1f664-110">`new` Operátor automaticky inicializuje prvků pole na výchozí hodnoty, které je třeba nulu pro všechny číselné typy a `null` pro všechny typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="1f664-110">The `new` operator automatically initializes the elements of an array to their default value, which, for example, is zero for all numeric types and `null` for all reference types.</span></span>

<span data-ttu-id="1f664-111">Následující příklad vytvoří pole `int` prvky, inicializuje pole a vytiskne obsah pole.</span><span class="sxs-lookup"><span data-stu-id="1f664-111">The following example creates an array of `int` elements, initializes the array, and prints out the contents of the array.</span></span>

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

<span data-ttu-id="1f664-112">Tento příklad vytvoří a pracuje ***jednorozměrné pole***.</span><span class="sxs-lookup"><span data-stu-id="1f664-112">This example creates and operates on a ***single-dimensional array***.</span></span> <span data-ttu-id="1f664-113">C# rovněž podporuje ***vícerozměrných polí***.</span><span class="sxs-lookup"><span data-stu-id="1f664-113">C# also supports ***multi-dimensional arrays***.</span></span> <span data-ttu-id="1f664-114">Zadejte počet rozměrů pole, označované také jako ***pořadí*** typ pole je jednu plus počet čárek mezi hranaté závorky pole zapsána.</span><span class="sxs-lookup"><span data-stu-id="1f664-114">The number of dimensions of an array type, also known as the ***rank*** of the array type, is one plus the number of commas written between the square brackets of the array type.</span></span> <span data-ttu-id="1f664-115">Následující příklad přiděluje jednorozměrná dvourozměrném a trojrozměrného pole.</span><span class="sxs-lookup"><span data-stu-id="1f664-115">The following example allocates a single-dimensional, a two-dimensional, and a three-dimensional array, respectively.</span></span>

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

<span data-ttu-id="1f664-116">`a1` Pole obsahuje 10 prvků `a2` pole obsahuje 50 (10 × 5) elementy a `a3` 100 (10 × 5 × 2) obsahuje pole prvků.</span><span class="sxs-lookup"><span data-stu-id="1f664-116">The `a1` array contains 10 elements, the `a2` array contains 50 (10 × 5) elements, and the `a3` array contains 100 (10 × 5 × 2) elements.</span></span>
<span data-ttu-id="1f664-117">Typ elementu pole může být libovolného typu, včetně typu pole.</span><span class="sxs-lookup"><span data-stu-id="1f664-117">The element type of an array can be any type, including an array type.</span></span> <span data-ttu-id="1f664-118">Někdy se označuje jako pole s prvky typu pole ***vícenásobného pole*** protože ne všechny délky pole elementu mají být stejné.</span><span class="sxs-lookup"><span data-stu-id="1f664-118">An array with elements of an array type is sometimes called a ***jagged array*** because the lengths of the element arrays do not all have to be the same.</span></span> <span data-ttu-id="1f664-119">V následujícím příkladu se přiděluje pole polí `int`:</span><span class="sxs-lookup"><span data-stu-id="1f664-119">The following example allocates an array of arrays of `int`:</span></span>

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

<span data-ttu-id="1f664-120">První řádek vytvoří pole se třemi prvky, každý typ `int[]` a každý s počáteční hodnotou `null`.</span><span class="sxs-lookup"><span data-stu-id="1f664-120">The first line creates an array with three elements, each of type `int[]` and each with an initial value of `null`.</span></span> <span data-ttu-id="1f664-121">Následující řádky následně inicializujete tři prvky s odkazy na jednotlivá pole instancí z různých délek.</span><span class="sxs-lookup"><span data-stu-id="1f664-121">The subsequent lines then initialize the three elements with references to individual array instances of varying lengths.</span></span>

<span data-ttu-id="1f664-122">Operátor new povoluje počáteční hodnoty prvků pole zadat pomocí ***inicializátor pole***, což je seznamem výrazů napsané mezi oddělovači `{` a `}`.</span><span class="sxs-lookup"><span data-stu-id="1f664-122">The new operator permits the initial values of the array elements to be specified using an ***array initializer***, which is a list of expressions written between the delimiters `{` and `}`.</span></span> <span data-ttu-id="1f664-123">V následujícím příkladu se přiděluje a inicializuje `int[]` s tři elementy.</span><span class="sxs-lookup"><span data-stu-id="1f664-123">The following example allocates and initializes an `int[]` with three elements.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

<span data-ttu-id="1f664-124">Všimněte si, že délka pole je odvozen z počet výrazů mezi {a}.</span><span class="sxs-lookup"><span data-stu-id="1f664-124">Note that the length of the array is inferred from the number of expressions between { and }.</span></span> <span data-ttu-id="1f664-125">Lokální proměnná a pole deklarace lze zkrátit další tak, aby typ pole nemusí být revidovat.</span><span class="sxs-lookup"><span data-stu-id="1f664-125">Local variable and field declarations can be shortened further such that the array type does not have to be restated.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

<span data-ttu-id="1f664-126">Obě předchozí příklady jsou ekvivalentní následujícímu zápisu:</span><span class="sxs-lookup"><span data-stu-id="1f664-126">Both of the previous examples are equivalent to the following:</span></span>

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
><span data-ttu-id="1f664-127">[Předchozí](structs.md)
>[další](interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="1f664-127">[Previous](structs.md)
[Next](interfaces.md)</span></span>