---
title: Předávání polí jako argumentů – Průvodce programováním jazyka C#
ms.date: 07/05/2018
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: 2e53008910a9062ada25680eb4b8e54a225fd226
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705688"
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a><span data-ttu-id="b7a9d-102">Předávání polí jako argumentů (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b7a9d-102">Passing arrays as arguments (C# Programming Guide)</span></span>

<span data-ttu-id="b7a9d-103">Pole mohou být předána jako argumenty parametrům metody.</span><span class="sxs-lookup"><span data-stu-id="b7a9d-103">Arrays can be passed as arguments to method parameters.</span></span> <span data-ttu-id="b7a9d-104">Vzhledem k tomu, že pole jsou typy odkazů, metoda může změnit hodnotu prvků.</span><span class="sxs-lookup"><span data-stu-id="b7a9d-104">Because arrays are reference types, the method can change the value of the elements.</span></span>

## <a name="passing-single-dimensional-arrays-as-arguments"></a><span data-ttu-id="b7a9d-105">Předávání jednorozměrných polí jako argumentů</span><span class="sxs-lookup"><span data-stu-id="b7a9d-105">Passing single-dimensional arrays as arguments</span></span>

<span data-ttu-id="b7a9d-106">Metodě můžete předat inicializované jednorozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="b7a9d-106">You can pass an initialized single-dimensional array to a method.</span></span> <span data-ttu-id="b7a9d-107">Například následující příkaz odešle pole metodě tisku.</span><span class="sxs-lookup"><span data-stu-id="b7a9d-107">For example, the following statement sends an array to a print method.</span></span>

[!code-csharp[csProgGuideArrays#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#34)]

<span data-ttu-id="b7a9d-108">Následující kód ukazuje částečnou implementaci metody tisku.</span><span class="sxs-lookup"><span data-stu-id="b7a9d-108">The following code shows a partial implementation of the print method.</span></span>

[!code-csharp[csProgGuideArrays#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#33)]

<span data-ttu-id="b7a9d-109">Můžete inicializovat a předat nové pole v jednom kroku, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b7a9d-109">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>

[!code-csharp[CsProgGuideArrays#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#35)]

### <a name="example"></a><span data-ttu-id="b7a9d-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="b7a9d-110">Example</span></span>

<span data-ttu-id="b7a9d-111">V následujícím příkladu je inicializováno pole řetězců a `DisplayArray` předáno jako argument metodě pro řetězce.</span><span class="sxs-lookup"><span data-stu-id="b7a9d-111">In the following example, an array of strings is initialized and passed as an argument to a `DisplayArray` method for strings.</span></span> <span data-ttu-id="b7a9d-112">Metoda zobrazí prvky pole.</span><span class="sxs-lookup"><span data-stu-id="b7a9d-112">The method displays the elements of the array.</span></span> <span data-ttu-id="b7a9d-113">Dále `ChangeArray` metoda obrátí prvky pole a `ChangeArrayElements` potom metoda upraví první tři prvky pole.</span><span class="sxs-lookup"><span data-stu-id="b7a9d-113">Next, the `ChangeArray` method reverses the array elements, and then the `ChangeArrayElements` method modifies the first three elements of the array.</span></span> <span data-ttu-id="b7a9d-114">Po každé metoda `DisplayArray` vrátí, metoda ukazuje, že předávání pole podle hodnoty nezabrání změnám prvků pole.</span><span class="sxs-lookup"><span data-stu-id="b7a9d-114">After each method returns, the `DisplayArray` method shows that passing an array by value doesn't prevent changes to the array elements.</span></span>

[!code-csharp[csProgGuideArrays#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/ArrayExample.cs)]

## <a name="passing-multidimensional-arrays-as-arguments"></a><span data-ttu-id="b7a9d-115">Předávání vícerozměrných polí jako argumentů</span><span class="sxs-lookup"><span data-stu-id="b7a9d-115">Passing multidimensional arrays as arguments</span></span>

<span data-ttu-id="b7a9d-116">Inicializované vícerozměrné pole předáte metodě stejným způsobem, jakým předáte jednorozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="b7a9d-116">You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.</span></span>

[!code-csharp[csProgGuideArrays#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#41)]

<span data-ttu-id="b7a9d-117">Následující kód ukazuje částečnou deklaraci metody tisku, která přijímá dvourozměrné pole jako svůj argument.</span><span class="sxs-lookup"><span data-stu-id="b7a9d-117">The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.</span></span>

[!code-csharp[csProgGuideArrays#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#36)]

<span data-ttu-id="b7a9d-118">Můžete inicializovat a předat nové pole v jednom kroku, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="b7a9d-118">You can initialize and pass a new array in one step, as is shown in the following example:</span></span>

[!code-csharp[csProgGuideArrays#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#32)]

### <a name="example"></a><span data-ttu-id="b7a9d-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="b7a9d-119">Example</span></span>

<span data-ttu-id="b7a9d-120">V následujícím příkladu je inicializováno dvojrozměrné pole celáčísla a předáno metodě. `Print2DArray`</span><span class="sxs-lookup"><span data-stu-id="b7a9d-120">In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method.</span></span> <span data-ttu-id="b7a9d-121">Metoda zobrazí prvky pole.</span><span class="sxs-lookup"><span data-stu-id="b7a9d-121">The method displays the elements of the array.</span></span>

[!code-csharp[csProgGuideArrays#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#31)]

## <a name="see-also"></a><span data-ttu-id="b7a9d-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="b7a9d-122">See also</span></span>

- [<span data-ttu-id="b7a9d-123">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b7a9d-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b7a9d-124">Pole</span><span class="sxs-lookup"><span data-stu-id="b7a9d-124">Arrays</span></span>](index.md)
- [<span data-ttu-id="b7a9d-125">Jednorozměrná pole</span><span class="sxs-lookup"><span data-stu-id="b7a9d-125">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="b7a9d-126">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="b7a9d-126">Multidimensional Arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="b7a9d-127">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="b7a9d-127">Jagged Arrays</span></span>](jagged-arrays.md)
