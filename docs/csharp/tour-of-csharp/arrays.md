---
title: C# Arrays – prohlídka jazyka C#
description: Pole jsou nejzákladnějším typem kolekce v jazyce C#
ms.date: 02/27/2020
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: 3e045c0933a21beab6958c7851546ba6e0b55ef9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159192"
---
# <a name="arrays"></a><span data-ttu-id="fc25b-103">Pole</span><span class="sxs-lookup"><span data-stu-id="fc25b-103">Arrays</span></span>

<span data-ttu-id="fc25b-104">***Pole*** je datová struktura, která obsahuje řadu proměnných, které jsou přístupné prostřednictvím vypočítaných indexů.</span><span class="sxs-lookup"><span data-stu-id="fc25b-104">An ***array*** is a data structure that contains a number of variables that are accessed through computed indices.</span></span> <span data-ttu-id="fc25b-105">Proměnné obsažené v poli, nazývané také ***prvky*** pole, jsou všechny stejného typu a tento typ se nazývá ***typ prvku*** pole.</span><span class="sxs-lookup"><span data-stu-id="fc25b-105">The variables contained in an array, also called the ***elements*** of the array, are all of the same type, and this type is called the ***element type*** of the array.</span></span>

<span data-ttu-id="fc25b-106">Typy polí jsou typy odkazů a deklarace proměnné pole jednoduše vyčlení prostor pro odkaz na instanci pole.</span><span class="sxs-lookup"><span data-stu-id="fc25b-106">Array types are reference types, and the declaration of an array variable simply sets aside space for a reference to an array instance.</span></span> <span data-ttu-id="fc25b-107">Skutečné instance pole jsou vytvářeny dynamicky za běhu pomocí nového operátoru.</span><span class="sxs-lookup"><span data-stu-id="fc25b-107">Actual array instances are created dynamically at runtime using the new operator.</span></span> <span data-ttu-id="fc25b-108">Nová operace určuje ***délku*** nové instance pole, která je pak pevná po dobu životnosti instance.</span><span class="sxs-lookup"><span data-stu-id="fc25b-108">The new operation specifies the ***length*** of the new array instance, which is then fixed for the lifetime of the instance.</span></span> <span data-ttu-id="fc25b-109">Indexy prvků rozsahu pole od `0` . `Length - 1`</span><span class="sxs-lookup"><span data-stu-id="fc25b-109">The indices of the elements of an array range from `0` to `Length - 1`.</span></span> <span data-ttu-id="fc25b-110">Operátor `new` automaticky inicializuje prvky pole na výchozí hodnotu, která je například `null` nulová pro všechny číselné typy a pro všechny typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="fc25b-110">The `new` operator automatically initializes the elements of an array to their default value, which, for example, is zero for all numeric types and `null` for all reference types.</span></span>

<span data-ttu-id="fc25b-111">Následující příklad vytvoří pole `int` prvků, inicializuje pole a vytiskne obsah pole.</span><span class="sxs-lookup"><span data-stu-id="fc25b-111">The following example creates an array of `int` elements, initializes the array, and prints out the contents of the array.</span></span>

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

<span data-ttu-id="fc25b-112">Tento příklad vytvoří a pracuje na ***jednorozměrné pole***.</span><span class="sxs-lookup"><span data-stu-id="fc25b-112">This example creates and operates on a ***single-dimensional array***.</span></span> <span data-ttu-id="fc25b-113">C# také podporuje ***vícerozměrná pole***.</span><span class="sxs-lookup"><span data-stu-id="fc25b-113">C# also supports ***multi-dimensional arrays***.</span></span> <span data-ttu-id="fc25b-114">Počet dimenzí typu pole, označovaný také jako ***pořadí*** typu pole, je jeden plus počet čárek zapsaných mezi hranatými závorkami typu pole.</span><span class="sxs-lookup"><span data-stu-id="fc25b-114">The number of dimensions of an array type, also known as the ***rank*** of the array type, is one plus the number of commas written between the square brackets of the array type.</span></span> <span data-ttu-id="fc25b-115">Následující příklad přiděluje jednorozměrné, dvojrozměrné a trojrozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="fc25b-115">The following example allocates a single-dimensional, a two-dimensional, and a three-dimensional array, respectively.</span></span>

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

<span data-ttu-id="fc25b-116">Pole `a1` obsahuje 10 prvků, `a2` pole obsahuje 50 (10 × `a3` 5) prvků a pole obsahuje 100 (10 × 5 × 2) prvků.</span><span class="sxs-lookup"><span data-stu-id="fc25b-116">The `a1` array contains 10 elements, the `a2` array contains 50 (10 × 5) elements, and the `a3` array contains 100 (10 × 5 × 2) elements.</span></span>
<span data-ttu-id="fc25b-117">Typ prvku pole může být libovolný typ, včetně typu pole.</span><span class="sxs-lookup"><span data-stu-id="fc25b-117">The element type of an array can be any type, including an array type.</span></span> <span data-ttu-id="fc25b-118">Pole s prvky typu pole se někdy nazývá ***zubaté pole,*** protože délky polí elementu nemusí být všechny stejné.</span><span class="sxs-lookup"><span data-stu-id="fc25b-118">An array with elements of an array type is sometimes called a ***jagged array*** because the lengths of the element arrays don't all have to be the same.</span></span> <span data-ttu-id="fc25b-119">Následující příklad přiděluje pole `int`polí :</span><span class="sxs-lookup"><span data-stu-id="fc25b-119">The following example allocates an array of arrays of `int`:</span></span>

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

<span data-ttu-id="fc25b-120">První řádek vytvoří pole se třemi `int[]` prvky, každý typu `null`a každý s počáteční hodnotou .</span><span class="sxs-lookup"><span data-stu-id="fc25b-120">The first line creates an array with three elements, each of type `int[]` and each with an initial value of `null`.</span></span> <span data-ttu-id="fc25b-121">Následující řádky pak inicializovat tři prvky s odkazy na jednotlivé instance pole různých délek.</span><span class="sxs-lookup"><span data-stu-id="fc25b-121">The subsequent lines then initialize the three elements with references to individual array instances of varying lengths.</span></span>

<span data-ttu-id="fc25b-122">Nový operátor umožňuje zadat počáteční hodnoty prvků pole pomocí ***inicializátoru pole***, což je `{` seznam `}`výrazů napsaných mezi oddělovači a .</span><span class="sxs-lookup"><span data-stu-id="fc25b-122">The new operator permits the initial values of the array elements to be specified using an ***array initializer***, which is a list of expressions written between the delimiters `{` and `}`.</span></span> <span data-ttu-id="fc25b-123">Následující příklad přiděluje `int[]` a inicializuje se třemi prvky.</span><span class="sxs-lookup"><span data-stu-id="fc25b-123">The following example allocates and initializes an `int[]` with three elements.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

<span data-ttu-id="fc25b-124">Délka pole je odvozena z počtu výrazů mezi { a }.</span><span class="sxs-lookup"><span data-stu-id="fc25b-124">The length of the array is inferred from the number of expressions between { and }.</span></span> <span data-ttu-id="fc25b-125">Místní proměnné a pole deklarace lze zkrátit dále tak, aby typ pole není třeba přeformulovat.</span><span class="sxs-lookup"><span data-stu-id="fc25b-125">Local variable and field declarations can be shortened further such that the array type does not have to be restated.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

<span data-ttu-id="fc25b-126">Oba předchozí příklady jsou ekvivalentní následující kód:</span><span class="sxs-lookup"><span data-stu-id="fc25b-126">Both of the previous examples are equivalent to the following code:</span></span>

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
><span data-ttu-id="fc25b-127">[Předchozí](classes-and-objects.md)
>[další](interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="fc25b-127">[Previous](classes-and-objects.md)
[Next](interfaces.md)</span></span>
