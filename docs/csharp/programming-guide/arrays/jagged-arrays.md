---
title: Vícenásobná pole - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 9fc05c8bdebf9c1c6b613db0b6a121e06765ac00
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651997"
---
# <a name="jagged-arrays-c-programming-guide"></a><span data-ttu-id="19bd2-102">Vícenásobná pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="19bd2-102">Jagged Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="19bd2-103">Vícenásobné pole je pole, jehož prvky jsou pole.</span><span class="sxs-lookup"><span data-stu-id="19bd2-103">A jagged array is an array whose elements are arrays.</span></span> <span data-ttu-id="19bd2-104">Prvky vícenásobného pole mohou být různé dimenze a velikostí.</span><span class="sxs-lookup"><span data-stu-id="19bd2-104">The elements of a jagged array can be of different dimensions and sizes.</span></span> <span data-ttu-id="19bd2-105">Vícenásobné pole se někdy označuje jako "pole polí."</span><span class="sxs-lookup"><span data-stu-id="19bd2-105">A jagged array is sometimes called an "array of arrays."</span></span> <span data-ttu-id="19bd2-106">Následující příklady ukazují, jak deklarovat, inicializovat a přístup Vícenásobná pole.</span><span class="sxs-lookup"><span data-stu-id="19bd2-106">The following examples show how to declare, initialize, and access jagged arrays.</span></span>  
  
 <span data-ttu-id="19bd2-107">Následuje deklaraci jednorozměrné pole s, která má tři prvky, z nichž každý je jednorozměrné pole celých čísel:</span><span class="sxs-lookup"><span data-stu-id="19bd2-107">The following is a declaration of a single-dimensional array that has three elements, each of which is a single-dimensional array of integers:</span></span>  
  
 [!code-csharp[csProgGuideArrays#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#19)]  
  
 <span data-ttu-id="19bd2-108">Než budete moct použít `jaggedArray`, jeho prvky musí být inicializován.</span><span class="sxs-lookup"><span data-stu-id="19bd2-108">Before you can use `jaggedArray`, its elements must be initialized.</span></span> <span data-ttu-id="19bd2-109">Můžete inicializovat prvky takto:</span><span class="sxs-lookup"><span data-stu-id="19bd2-109">You can initialize the elements like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#20)]  
  
 <span data-ttu-id="19bd2-110">Každý prvek je jednorozměrné pole celých čísel.</span><span class="sxs-lookup"><span data-stu-id="19bd2-110">Each of the elements is a single-dimensional array of integers.</span></span> <span data-ttu-id="19bd2-111">Prvním prvkem je pole 5 celých čísel, druhá je pole 4 celých čísel a třetí je pole 2 celých čísel.</span><span class="sxs-lookup"><span data-stu-id="19bd2-111">The first element is an array of 5 integers, the second is an array of 4 integers, and the third is an array of 2 integers.</span></span>  
  
 <span data-ttu-id="19bd2-112">Je také možné použít inicializátory k vyplnění hodnot prvků pole, v takovém případě nepotřebujete velikost pole.</span><span class="sxs-lookup"><span data-stu-id="19bd2-112">It is also possible to use initializers to fill the array elements with values, in which case you do not need the array size.</span></span> <span data-ttu-id="19bd2-113">Příklad:</span><span class="sxs-lookup"><span data-stu-id="19bd2-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#21)]  
  
 <span data-ttu-id="19bd2-114">Můžete také inicializovat pole při deklaraci takto:</span><span class="sxs-lookup"><span data-stu-id="19bd2-114">You can also initialize the array upon declaration like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#22)]  
  
 <span data-ttu-id="19bd2-115">Můžete použít následující Zkrácený tvar.</span><span class="sxs-lookup"><span data-stu-id="19bd2-115">You can use the following shorthand form.</span></span> <span data-ttu-id="19bd2-116">Všimněte si, že nemůžete vynechat `new` operátor od inicializace prvků vzhledem k tomu, že neexistuje žádná výchozí inicializace pro prvky:</span><span class="sxs-lookup"><span data-stu-id="19bd2-116">Notice that you cannot omit the `new` operator from the elements initialization because there is no default initialization for the elements:</span></span>  
  
 [!code-csharp[csProgGuideArrays#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#23)]  
  
 <span data-ttu-id="19bd2-117">Vícenásobné pole je pole polí, a proto jeho prvky jsou odkazové typy a jsou inicializovány na hodnotu `null`.</span><span class="sxs-lookup"><span data-stu-id="19bd2-117">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
 <span data-ttu-id="19bd2-118">Můžete přistupovat k prvkům jednotlivá pole jako v těchto příkladech:</span><span class="sxs-lookup"><span data-stu-id="19bd2-118">You can access individual array elements like these examples:</span></span>  
  
 [!code-csharp[csProgGuideArrays#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#24)]  
  
 <span data-ttu-id="19bd2-119">Je možné kombinovat vícenásobného a vícedimenzionální pole.</span><span class="sxs-lookup"><span data-stu-id="19bd2-119">It is possible to mix jagged and multidimensional arrays.</span></span> <span data-ttu-id="19bd2-120">Následuje deklaraci a inicializaci jednorozměrné vícenásobného pole, která obsahuje tři prvky dvourozměrné pole různých velikostí.</span><span class="sxs-lookup"><span data-stu-id="19bd2-120">The following is a declaration and initialization of a single-dimensional jagged array that contains three two-dimensional array elements of different sizes.</span></span> <span data-ttu-id="19bd2-121">Další informace o dvojrozměrné pole najdete v tématu [vícerozměrná pole](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="19bd2-121">For more information about two-dimensional arrays, see [Multidimensional Arrays](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).</span></span>  
  
 [!code-csharp[csProgGuideArrays#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#25)]  
  
 <span data-ttu-id="19bd2-122">Jak je znázorněno v tomto příkladu, který se zobrazí hodnota elementu, který můžete přístup ke jednotlivým prvkům `[1,0]` první pole (hodnotu `5`):</span><span class="sxs-lookup"><span data-stu-id="19bd2-122">You can access individual elements as shown in this example, which displays the value of the element `[1,0]` of the first array (value `5`):</span></span>  
  
 [!code-csharp[csProgGuideArrays#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#26)]  
  
 <span data-ttu-id="19bd2-123">Metoda `Length` vrátí počet polí obsažených v vícenásobného pole.</span><span class="sxs-lookup"><span data-stu-id="19bd2-123">The method `Length` returns the number of arrays contained in the jagged array.</span></span> <span data-ttu-id="19bd2-124">Například za předpokladu, že je deklarován předchozí pole, tento řádek:</span><span class="sxs-lookup"><span data-stu-id="19bd2-124">For example, assuming you have declared the previous array, this line:</span></span>  
  
 [!code-csharp[csProgGuideArrays#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#27)]  
  
 <span data-ttu-id="19bd2-125">Vrátí hodnotu 3.</span><span class="sxs-lookup"><span data-stu-id="19bd2-125">returns a value of 3.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19bd2-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="19bd2-126">Example</span></span>

 <span data-ttu-id="19bd2-127">Tento příklad vytvoří pole, jehož prvky jsou samotné pole.</span><span class="sxs-lookup"><span data-stu-id="19bd2-127">This example builds an array whose elements are themselves arrays.</span></span> <span data-ttu-id="19bd2-128">Prvky pole každé z nich má jinou velikost.</span><span class="sxs-lookup"><span data-stu-id="19bd2-128">Each one of the array elements has a different size.</span></span>  
  
 [!code-csharp[csProgGuideArrays#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#18)]  
  
## <a name="see-also"></a><span data-ttu-id="19bd2-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19bd2-129">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="19bd2-130">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="19bd2-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="19bd2-131">Pole</span><span class="sxs-lookup"><span data-stu-id="19bd2-131">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)
- [<span data-ttu-id="19bd2-132">Jednorozměrná pole</span><span class="sxs-lookup"><span data-stu-id="19bd2-132">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)
- [<span data-ttu-id="19bd2-133">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="19bd2-133">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
