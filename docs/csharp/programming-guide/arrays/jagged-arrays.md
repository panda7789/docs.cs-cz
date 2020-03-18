---
title: Zubatá pole – programovací průvodce C#
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 56013f0143d5efcb31a476909cb6e92504ff0dbc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705701"
---
# <a name="jagged-arrays-c-programming-guide"></a><span data-ttu-id="6faa8-102">Vícenásobná pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="6faa8-102">Jagged Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="6faa8-103">Vícenásobné pole je pole, jehož prvky jsou pole.</span><span class="sxs-lookup"><span data-stu-id="6faa8-103">A jagged array is an array whose elements are arrays.</span></span> <span data-ttu-id="6faa8-104">Prvky zubaté pole může být různých rozměrů a velikostí.</span><span class="sxs-lookup"><span data-stu-id="6faa8-104">The elements of a jagged array can be of different dimensions and sizes.</span></span> <span data-ttu-id="6faa8-105">Zubaté pole se někdy nazývá "pole polí".</span><span class="sxs-lookup"><span data-stu-id="6faa8-105">A jagged array is sometimes called an "array of arrays."</span></span> <span data-ttu-id="6faa8-106">Následující příklady ukazují, jak deklarovat, inicializovat a přistupovat k zubatý pole.</span><span class="sxs-lookup"><span data-stu-id="6faa8-106">The following examples show how to declare, initialize, and access jagged arrays.</span></span>  
  
 <span data-ttu-id="6faa8-107">Následuje deklarace jednorozměrného pole, které má tři prvky, z nichž každý je jednorozměrné pole celá čísla:</span><span class="sxs-lookup"><span data-stu-id="6faa8-107">The following is a declaration of a single-dimensional array that has three elements, each of which is a single-dimensional array of integers:</span></span>  
  
 [!code-csharp[csProgGuideArrays#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#19)]  
  
 <span data-ttu-id="6faa8-108">Před použitím `jaggedArray`musí být jeho prvky inicializovány.</span><span class="sxs-lookup"><span data-stu-id="6faa8-108">Before you can use `jaggedArray`, its elements must be initialized.</span></span> <span data-ttu-id="6faa8-109">Prvky můžete inicializovat takto:</span><span class="sxs-lookup"><span data-stu-id="6faa8-109">You can initialize the elements like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#20)]  
  
 <span data-ttu-id="6faa8-110">Každý z prvků je jednorozměrné pole celá čísla.</span><span class="sxs-lookup"><span data-stu-id="6faa8-110">Each of the elements is a single-dimensional array of integers.</span></span> <span data-ttu-id="6faa8-111">První prvek je pole 5 celá čísla, druhý je pole 4 celá čísla a třetí je pole 2 celá čísla.</span><span class="sxs-lookup"><span data-stu-id="6faa8-111">The first element is an array of 5 integers, the second is an array of 4 integers, and the third is an array of 2 integers.</span></span>  
  
 <span data-ttu-id="6faa8-112">Je také možné použít inicializátory vyplnit prvky pole s hodnotami, v takovém případě nepotřebujete velikost pole.</span><span class="sxs-lookup"><span data-stu-id="6faa8-112">It is also possible to use initializers to fill the array elements with values, in which case you do not need the array size.</span></span> <span data-ttu-id="6faa8-113">Například:</span><span class="sxs-lookup"><span data-stu-id="6faa8-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#21)]  
  
 <span data-ttu-id="6faa8-114">Můžete také inicializovat pole při deklaraci, jako je tento:</span><span class="sxs-lookup"><span data-stu-id="6faa8-114">You can also initialize the array upon declaration like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#22)]  
  
 <span data-ttu-id="6faa8-115">Můžete použít následující zkrácený formulář.</span><span class="sxs-lookup"><span data-stu-id="6faa8-115">You can use the following shorthand form.</span></span> <span data-ttu-id="6faa8-116">Všimněte si, že `new` nelze vynechat operátor z inicializace prvků, protože neexistuje žádná výchozí inicializace pro prvky:</span><span class="sxs-lookup"><span data-stu-id="6faa8-116">Notice that you cannot omit the `new` operator from the elements initialization because there is no default initialization for the elements:</span></span>  
  
 [!code-csharp[csProgGuideArrays#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#23)]  
  
 <span data-ttu-id="6faa8-117">Zubaté pole je pole polí, a proto jeho prvky jsou `null`typy odkazů a jsou inicializovány na .</span><span class="sxs-lookup"><span data-stu-id="6faa8-117">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
 <span data-ttu-id="6faa8-118">Můžete přistupovat k jednotlivým prvkům pole, jako jsou tyto příklady:</span><span class="sxs-lookup"><span data-stu-id="6faa8-118">You can access individual array elements like these examples:</span></span>  
  
 [!code-csharp[csProgGuideArrays#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#24)]  
  
 <span data-ttu-id="6faa8-119">Je možné kombinovat zubaté a vícerozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="6faa8-119">It is possible to mix jagged and multidimensional arrays.</span></span> <span data-ttu-id="6faa8-120">Následuje deklarace a inicializace jednorozměrného zubatého pole, které obsahuje tři dvourozměrné prvky pole různých velikostí.</span><span class="sxs-lookup"><span data-stu-id="6faa8-120">The following is a declaration and initialization of a single-dimensional jagged array that contains three two-dimensional array elements of different sizes.</span></span> <span data-ttu-id="6faa8-121">Další informace o dvojrozměrných polích naleznete [v tématu Multidimenzionální pole](./multidimensional-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="6faa8-121">For more information about two-dimensional arrays, see [Multidimensional Arrays](./multidimensional-arrays.md).</span></span>  
  
 [!code-csharp[csProgGuideArrays#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#25)]  
  
 <span data-ttu-id="6faa8-122">Můžete přistupovat k jednotlivým prvkům, jak je znázorněno v tomto příkladu, který zobrazuje hodnotu prvku `[1,0]` prvního pole (hodnota `5`):</span><span class="sxs-lookup"><span data-stu-id="6faa8-122">You can access individual elements as shown in this example, which displays the value of the element `[1,0]` of the first array (value `5`):</span></span>  
  
 [!code-csharp[csProgGuideArrays#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#26)]  
  
 <span data-ttu-id="6faa8-123">Metoda `Length` vrátí počet polí obsažených v zubaté pole.</span><span class="sxs-lookup"><span data-stu-id="6faa8-123">The method `Length` returns the number of arrays contained in the jagged array.</span></span> <span data-ttu-id="6faa8-124">Například za předpokladu, že jste deklarovali předchozí pole, tento řádek:</span><span class="sxs-lookup"><span data-stu-id="6faa8-124">For example, assuming you have declared the previous array, this line:</span></span>  
  
 [!code-csharp[csProgGuideArrays#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#27)]  
  
 <span data-ttu-id="6faa8-125">vrátí hodnotu 3.</span><span class="sxs-lookup"><span data-stu-id="6faa8-125">returns a value of 3.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6faa8-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="6faa8-126">Example</span></span>

 <span data-ttu-id="6faa8-127">Tento příklad vytvoří pole, jehož prvky jsou samy o sobě pole.</span><span class="sxs-lookup"><span data-stu-id="6faa8-127">This example builds an array whose elements are themselves arrays.</span></span> <span data-ttu-id="6faa8-128">Každý jeden z prvků pole má jinou velikost.</span><span class="sxs-lookup"><span data-stu-id="6faa8-128">Each one of the array elements has a different size.</span></span>  
  
 [!code-csharp[csProgGuideArrays#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#18)]  
  
## <a name="see-also"></a><span data-ttu-id="6faa8-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="6faa8-129">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="6faa8-130">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6faa8-130">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6faa8-131">Pole</span><span class="sxs-lookup"><span data-stu-id="6faa8-131">Arrays</span></span>](./index.md)
- [<span data-ttu-id="6faa8-132">Jednorozměrná pole</span><span class="sxs-lookup"><span data-stu-id="6faa8-132">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="6faa8-133">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="6faa8-133">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
