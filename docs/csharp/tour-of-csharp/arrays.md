---
title: C#Pole – prohlídka C# jazyka
description: Pole jsou nejzákladnější typ kolekce v C# jazyce.
ms.date: 08/10/2016
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: 195df1f31c71ee7a202a3b57076775c4f717d399
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "77673313"
---
# <a name="arrays"></a><span data-ttu-id="2260a-103">Pole</span><span class="sxs-lookup"><span data-stu-id="2260a-103">Arrays</span></span>

<span data-ttu-id="2260a-104">***Pole*** je datová struktura, která obsahuje počet proměnných, které jsou dostupné prostřednictvím počítaných indexů.</span><span class="sxs-lookup"><span data-stu-id="2260a-104">An ***array*** is a data structure that contains a number of variables that are accessed through computed indices.</span></span> <span data-ttu-id="2260a-105">Proměnné obsažené v poli, označované také jako ***prvky*** pole, jsou všechny stejného typu a tento typ se nazývá ***typ elementu*** pole.</span><span class="sxs-lookup"><span data-stu-id="2260a-105">The variables contained in an array, also called the ***elements*** of the array, are all of the same type, and this type is called the ***element type*** of the array.</span></span>

<span data-ttu-id="2260a-106">Typy polí jsou odkazové typy a deklarace proměnné pole jednoduše nastaví volné místo pro odkaz na instanci pole.</span><span class="sxs-lookup"><span data-stu-id="2260a-106">Array types are reference types, and the declaration of an array variable simply sets aside space for a reference to an array instance.</span></span> <span data-ttu-id="2260a-107">Skutečné instance pole jsou vytvářeny dynamicky za běhu pomocí operátoru new.</span><span class="sxs-lookup"><span data-stu-id="2260a-107">Actual array instances are created dynamically at runtime using the new operator.</span></span> <span data-ttu-id="2260a-108">Nová operace určuje ***délku*** nové instance pole, která je poté opravena po dobu života instance.</span><span class="sxs-lookup"><span data-stu-id="2260a-108">The new operation specifies the ***length*** of the new array instance, which is then fixed for the lifetime of the instance.</span></span> <span data-ttu-id="2260a-109">Indexy prvků rozsahu pole od `0` do `Length - 1`.</span><span class="sxs-lookup"><span data-stu-id="2260a-109">The indices of the elements of an array range from `0` to `Length - 1`.</span></span> <span data-ttu-id="2260a-110">Operátor `new` automaticky inicializuje prvky pole na výchozí hodnotu, což je například nula pro všechny číselné typy a `null` pro všechny typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="2260a-110">The `new` operator automatically initializes the elements of an array to their default value, which, for example, is zero for all numeric types and `null` for all reference types.</span></span>

<span data-ttu-id="2260a-111">Následující příklad vytvoří pole `int` prvky, inicializuje pole a vytiskne obsah pole.</span><span class="sxs-lookup"><span data-stu-id="2260a-111">The following example creates an array of `int` elements, initializes the array, and prints out the contents of the array.</span></span>

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

<span data-ttu-id="2260a-112">Tento příklad vytvoří a pracuje na jednorozměrném ***poli***.</span><span class="sxs-lookup"><span data-stu-id="2260a-112">This example creates and operates on a ***single-dimensional array***.</span></span> <span data-ttu-id="2260a-113">C#podporuje rovněž ***multidimenzionální pole***.</span><span class="sxs-lookup"><span data-stu-id="2260a-113">C# also supports ***multi-dimensional arrays***.</span></span> <span data-ttu-id="2260a-114">Počet rozměrů typu pole, označovaný také jako ***rozměr*** typu pole, je jedna plus počet čárek napsaných mezi hranatými závorkami typu pole.</span><span class="sxs-lookup"><span data-stu-id="2260a-114">The number of dimensions of an array type, also known as the ***rank*** of the array type, is one plus the number of commas written between the square brackets of the array type.</span></span> <span data-ttu-id="2260a-115">Následující příklad přiděluje jednorozměrné, dvojrozměrné a trojrozměrné pole v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="2260a-115">The following example allocates a single-dimensional, a two-dimensional, and a three-dimensional array, respectively.</span></span>

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

<span data-ttu-id="2260a-116">Pole `a1` obsahuje 10 prvků, pole `a2` obsahuje 50 (10 × 5) prvků a pole `a3` obsahuje 100 (10 × 5 × 2) prvků.</span><span class="sxs-lookup"><span data-stu-id="2260a-116">The `a1` array contains 10 elements, the `a2` array contains 50 (10 × 5) elements, and the `a3` array contains 100 (10 × 5 × 2) elements.</span></span>
<span data-ttu-id="2260a-117">Typ elementu pole může být libovolný typ, včetně typu pole.</span><span class="sxs-lookup"><span data-stu-id="2260a-117">The element type of an array can be any type, including an array type.</span></span> <span data-ttu-id="2260a-118">Pole s prvky typu pole se někdy nazývá ***vícenásobné pole*** , protože délky polí elementů nemusí být stejné.</span><span class="sxs-lookup"><span data-stu-id="2260a-118">An array with elements of an array type is sometimes called a ***jagged array*** because the lengths of the element arrays do not all have to be the same.</span></span> <span data-ttu-id="2260a-119">Následující příklad přiděluje pole polí `int`:</span><span class="sxs-lookup"><span data-stu-id="2260a-119">The following example allocates an array of arrays of `int`:</span></span>

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

<span data-ttu-id="2260a-120">První řádek vytvoří pole se třemi prvky, každou typu `int[]` a každý s počáteční hodnotou `null`.</span><span class="sxs-lookup"><span data-stu-id="2260a-120">The first line creates an array with three elements, each of type `int[]` and each with an initial value of `null`.</span></span> <span data-ttu-id="2260a-121">Následující řádky poté inicializují tři prvky s odkazy na jednotlivé instance pole s různou délkou.</span><span class="sxs-lookup"><span data-stu-id="2260a-121">The subsequent lines then initialize the three elements with references to individual array instances of varying lengths.</span></span>

<span data-ttu-id="2260a-122">Operátor New umožňuje zadat počáteční hodnoty prvků pole pomocí ***inicializátoru pole***, což je seznam výrazů zapsaných mezi oddělovači `{` a `}`.</span><span class="sxs-lookup"><span data-stu-id="2260a-122">The new operator permits the initial values of the array elements to be specified using an ***array initializer***, which is a list of expressions written between the delimiters `{` and `}`.</span></span> <span data-ttu-id="2260a-123">Následující příklad přiděluje a inicializuje `int[]` se třemi prvky.</span><span class="sxs-lookup"><span data-stu-id="2260a-123">The following example allocates and initializes an `int[]` with three elements.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

<span data-ttu-id="2260a-124">Všimněte si, že délka pole je odvozená od počtu výrazů mezi {a}.</span><span class="sxs-lookup"><span data-stu-id="2260a-124">Note that the length of the array is inferred from the number of expressions between { and }.</span></span> <span data-ttu-id="2260a-125">Deklarace lokální proměnné a pole lze dále zkrátit tak, aby se typ pole nemuselo přestavit.</span><span class="sxs-lookup"><span data-stu-id="2260a-125">Local variable and field declarations can be shortened further such that the array type does not have to be restated.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

<span data-ttu-id="2260a-126">Oba předchozí příklady jsou ekvivalentní následujícímu:</span><span class="sxs-lookup"><span data-stu-id="2260a-126">Both of the previous examples are equivalent to the following:</span></span>

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
><span data-ttu-id="2260a-127">[Předchozí](classes-and-objects.md)
>[Další](interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="2260a-127">[Previous](classes-and-objects.md)
[Next](interfaces.md)</span></span>
