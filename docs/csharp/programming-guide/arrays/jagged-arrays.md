---
title: Vícenásobná pole – Průvodce programováním v C#
description: Vícenásobné pole v jazyce C# je pole, jehož prvky jsou pole různých rozměrů a velikostí. Naučte se deklarovat, inicializovat a přistupovat k vícenásobným polím.
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 40da9fbda34aef4e69ebf2ae20485e883b79f871
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474680"
---
# <a name="jagged-arrays-c-programming-guide"></a><span data-ttu-id="8c595-104">Vícenásobná pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="8c595-104">Jagged Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="8c595-105">Vícenásobné pole je pole, jehož prvky jsou pole.</span><span class="sxs-lookup"><span data-stu-id="8c595-105">A jagged array is an array whose elements are arrays.</span></span> <span data-ttu-id="8c595-106">Prvky vícenásobného pole mohou mít různé rozměry a velikosti.</span><span class="sxs-lookup"><span data-stu-id="8c595-106">The elements of a jagged array can be of different dimensions and sizes.</span></span> <span data-ttu-id="8c595-107">Vícenásobné pole se někdy označuje jako "pole polí".</span><span class="sxs-lookup"><span data-stu-id="8c595-107">A jagged array is sometimes called an "array of arrays."</span></span> <span data-ttu-id="8c595-108">Následující příklady ukazují, jak deklarovat, inicializovat a přistupovat k vícenásobným polím.</span><span class="sxs-lookup"><span data-stu-id="8c595-108">The following examples show how to declare, initialize, and access jagged arrays.</span></span>  
  
 <span data-ttu-id="8c595-109">Níže je deklarace jednorozměrného pole, které má tři prvky, z nichž každý je jednorozměrné pole celých čísel:</span><span class="sxs-lookup"><span data-stu-id="8c595-109">The following is a declaration of a single-dimensional array that has three elements, each of which is a single-dimensional array of integers:</span></span>  
  
 [!code-csharp[csProgGuideArrays#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#19)]  
  
 <span data-ttu-id="8c595-110">Než budete moci použít `jaggedArray` , musí být inicializovány jeho prvky.</span><span class="sxs-lookup"><span data-stu-id="8c595-110">Before you can use `jaggedArray`, its elements must be initialized.</span></span> <span data-ttu-id="8c595-111">Prvky můžete inicializovat takto:</span><span class="sxs-lookup"><span data-stu-id="8c595-111">You can initialize the elements like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#20)]  
  
 <span data-ttu-id="8c595-112">Každý prvek je jednorozměrné pole celých čísel.</span><span class="sxs-lookup"><span data-stu-id="8c595-112">Each of the elements is a single-dimensional array of integers.</span></span> <span data-ttu-id="8c595-113">První prvek je pole o 5 celých čísel, druhým je pole o 4 celých číslech a třetí je pole o 2 celých číslech.</span><span class="sxs-lookup"><span data-stu-id="8c595-113">The first element is an array of 5 integers, the second is an array of 4 integers, and the third is an array of 2 integers.</span></span>  
  
 <span data-ttu-id="8c595-114">Je také možné použít inicializátory k vyplnění prvků pole hodnotami, v takovém případě nepotřebujete velikost pole.</span><span class="sxs-lookup"><span data-stu-id="8c595-114">It is also possible to use initializers to fill the array elements with values, in which case you do not need the array size.</span></span> <span data-ttu-id="8c595-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="8c595-115">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#21)]  
  
 <span data-ttu-id="8c595-116">Pole můžete také inicializovat při deklaraci takto:</span><span class="sxs-lookup"><span data-stu-id="8c595-116">You can also initialize the array upon declaration like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#22)]  
  
 <span data-ttu-id="8c595-117">Můžete použít následující zkrácený tvar.</span><span class="sxs-lookup"><span data-stu-id="8c595-117">You can use the following shorthand form.</span></span> <span data-ttu-id="8c595-118">Všimněte si, že nelze vynechat `new` operátor z inicializace prvků, protože neexistuje žádná výchozí inicializace pro prvky:</span><span class="sxs-lookup"><span data-stu-id="8c595-118">Notice that you cannot omit the `new` operator from the elements initialization because there is no default initialization for the elements:</span></span>  
  
 [!code-csharp[csProgGuideArrays#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#23)]  
  
 <span data-ttu-id="8c595-119">Vícenásobné pole je pole pole, a proto jeho prvky jsou odkazové typy a jsou inicializovány na `null` .</span><span class="sxs-lookup"><span data-stu-id="8c595-119">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
 <span data-ttu-id="8c595-120">Můžete přistupovat k jednotlivým prvkům pole, jako jsou tyto příklady:</span><span class="sxs-lookup"><span data-stu-id="8c595-120">You can access individual array elements like these examples:</span></span>  
  
 [!code-csharp[csProgGuideArrays#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#24)]  
  
 <span data-ttu-id="8c595-121">Je možné kombinovat zubatá a multidimenzionální pole.</span><span class="sxs-lookup"><span data-stu-id="8c595-121">It is possible to mix jagged and multidimensional arrays.</span></span> <span data-ttu-id="8c595-122">Následuje deklarace a inicializace jednorozměrného vícenásobného pole, které obsahuje 3 2 prvky pole s různou velikostí.</span><span class="sxs-lookup"><span data-stu-id="8c595-122">The following is a declaration and initialization of a single-dimensional jagged array that contains three two-dimensional array elements of different sizes.</span></span> <span data-ttu-id="8c595-123">Další informace o dvojrozměrnéch polích naleznete v tématu [multidimenzionální pole](./multidimensional-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="8c595-123">For more information about two-dimensional arrays, see [Multidimensional Arrays](./multidimensional-arrays.md).</span></span>  
  
 [!code-csharp[csProgGuideArrays#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#25)]  
  
 <span data-ttu-id="8c595-124">Můžete přistupovat k jednotlivým prvkům, jak je znázorněno v tomto příkladu, který zobrazuje hodnotu prvku `[1,0]` prvního pole (hodnota `5` ):</span><span class="sxs-lookup"><span data-stu-id="8c595-124">You can access individual elements as shown in this example, which displays the value of the element `[1,0]` of the first array (value `5`):</span></span>  
  
 [!code-csharp[csProgGuideArrays#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#26)]  
  
 <span data-ttu-id="8c595-125">Metoda `Length` vrátí počet polí obsažených ve vícenásobném poli.</span><span class="sxs-lookup"><span data-stu-id="8c595-125">The method `Length` returns the number of arrays contained in the jagged array.</span></span> <span data-ttu-id="8c595-126">Předpokládejme například, že jste deklarovali předchozí pole, tento řádek:</span><span class="sxs-lookup"><span data-stu-id="8c595-126">For example, assuming you have declared the previous array, this line:</span></span>  
  
 [!code-csharp[csProgGuideArrays#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#27)]  
  
 <span data-ttu-id="8c595-127">Vrátí hodnotu 3.</span><span class="sxs-lookup"><span data-stu-id="8c595-127">returns a value of 3.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c595-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c595-128">Example</span></span>

 <span data-ttu-id="8c595-129">Tento příklad vytvoří pole, jehož prvky jsou sami.</span><span class="sxs-lookup"><span data-stu-id="8c595-129">This example builds an array whose elements are themselves arrays.</span></span> <span data-ttu-id="8c595-130">Každé z prvků pole má jinou velikost.</span><span class="sxs-lookup"><span data-stu-id="8c595-130">Each one of the array elements has a different size.</span></span>  
  
 [!code-csharp[csProgGuideArrays#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#18)]  
  
## <a name="see-also"></a><span data-ttu-id="8c595-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="8c595-131">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="8c595-132">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="8c595-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8c595-133">Pole</span><span class="sxs-lookup"><span data-stu-id="8c595-133">Arrays</span></span>](./index.md)
- [<span data-ttu-id="8c595-134">Jednorozměrná pole</span><span class="sxs-lookup"><span data-stu-id="8c595-134">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="8c595-135">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="8c595-135">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
