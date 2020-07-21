---
title: Předávání polí jako argumentů – Průvodce programováním v C#
description: Pole v jazyce C# lze předat jako argumenty parametrům metody. Vzhledem k tomu, že pole jsou odkazové typy, metoda může změnit hodnotu prvků.
ms.date: 07/05/2018
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: 68f174421e56e2cf082fe670f93c4f6627d7c17b
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474628"
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a><span data-ttu-id="21a9d-104">Předávání polí jako argumentů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="21a9d-104">Passing arrays as arguments (C# Programming Guide)</span></span>

<span data-ttu-id="21a9d-105">Pole mohou být předána jako argumenty parametrům metody.</span><span class="sxs-lookup"><span data-stu-id="21a9d-105">Arrays can be passed as arguments to method parameters.</span></span> <span data-ttu-id="21a9d-106">Vzhledem k tomu, že pole jsou odkazové typy, metoda může změnit hodnotu prvků.</span><span class="sxs-lookup"><span data-stu-id="21a9d-106">Because arrays are reference types, the method can change the value of the elements.</span></span>

## <a name="passing-single-dimensional-arrays-as-arguments"></a><span data-ttu-id="21a9d-107">Předávání jednorozměrného pole jako argumentů</span><span class="sxs-lookup"><span data-stu-id="21a9d-107">Passing single-dimensional arrays as arguments</span></span>

<span data-ttu-id="21a9d-108">Do metody můžete předat inicializované jednorozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="21a9d-108">You can pass an initialized single-dimensional array to a method.</span></span> <span data-ttu-id="21a9d-109">Například následující příkaz odešle pole do metody Print.</span><span class="sxs-lookup"><span data-stu-id="21a9d-109">For example, the following statement sends an array to a print method.</span></span>

[!code-csharp[csProgGuideArrays#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#34)]

<span data-ttu-id="21a9d-110">Následující kód ukazuje částečnou implementaci metody Print.</span><span class="sxs-lookup"><span data-stu-id="21a9d-110">The following code shows a partial implementation of the print method.</span></span>

[!code-csharp[csProgGuideArrays#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#33)]

<span data-ttu-id="21a9d-111">Můžete inicializovat a předat nové pole v jednom kroku, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="21a9d-111">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>

[!code-csharp[CsProgGuideArrays#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#35)]

### <a name="example"></a><span data-ttu-id="21a9d-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="21a9d-112">Example</span></span>

<span data-ttu-id="21a9d-113">V následujícím příkladu je pole řetězců inicializováno a předáno jako argument `DisplayArray` metodě pro řetězce.</span><span class="sxs-lookup"><span data-stu-id="21a9d-113">In the following example, an array of strings is initialized and passed as an argument to a `DisplayArray` method for strings.</span></span> <span data-ttu-id="21a9d-114">Metoda zobrazí prvky pole.</span><span class="sxs-lookup"><span data-stu-id="21a9d-114">The method displays the elements of the array.</span></span> <span data-ttu-id="21a9d-115">Dále `ChangeArray` Metoda obrátí prvky pole a poté `ChangeArrayElements` Metoda upraví první tři prvky pole.</span><span class="sxs-lookup"><span data-stu-id="21a9d-115">Next, the `ChangeArray` method reverses the array elements, and then the `ChangeArrayElements` method modifies the first three elements of the array.</span></span> <span data-ttu-id="21a9d-116">Po vrácení každé metody metoda `DisplayArray` ukazuje, že předání pole hodnotou nebrání změnám prvků pole.</span><span class="sxs-lookup"><span data-stu-id="21a9d-116">After each method returns, the `DisplayArray` method shows that passing an array by value doesn't prevent changes to the array elements.</span></span>

[!code-csharp[csProgGuideArrays#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/ArrayExample.cs)]

## <a name="passing-multidimensional-arrays-as-arguments"></a><span data-ttu-id="21a9d-117">Předávání multidimenzionálních polí jako argumentů</span><span class="sxs-lookup"><span data-stu-id="21a9d-117">Passing multidimensional arrays as arguments</span></span>

<span data-ttu-id="21a9d-118">Inicializované multidimenzionální pole do metody předáte stejným způsobem jako jednorozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="21a9d-118">You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.</span></span>

[!code-csharp[csProgGuideArrays#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#41)]

<span data-ttu-id="21a9d-119">Následující kód ukazuje částečnou deklaraci metody Print, která přijímá dvojrozměrné pole jako argument.</span><span class="sxs-lookup"><span data-stu-id="21a9d-119">The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.</span></span>

[!code-csharp[csProgGuideArrays#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#36)]

<span data-ttu-id="21a9d-120">Můžete inicializovat a předat nové pole v jednom kroku, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="21a9d-120">You can initialize and pass a new array in one step, as is shown in the following example:</span></span>

[!code-csharp[csProgGuideArrays#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#32)]

### <a name="example"></a><span data-ttu-id="21a9d-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="21a9d-121">Example</span></span>

<span data-ttu-id="21a9d-122">V následujícím příkladu je inicializováno dvojrozměrné pole celých čísel a předáno do `Print2DArray` metody.</span><span class="sxs-lookup"><span data-stu-id="21a9d-122">In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method.</span></span> <span data-ttu-id="21a9d-123">Metoda zobrazí prvky pole.</span><span class="sxs-lookup"><span data-stu-id="21a9d-123">The method displays the elements of the array.</span></span>

[!code-csharp[csProgGuideArrays#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#31)]

## <a name="see-also"></a><span data-ttu-id="21a9d-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="21a9d-124">See also</span></span>

- [<span data-ttu-id="21a9d-125">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="21a9d-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="21a9d-126">Pole</span><span class="sxs-lookup"><span data-stu-id="21a9d-126">Arrays</span></span>](index.md)
- [<span data-ttu-id="21a9d-127">Jednorozměrná pole</span><span class="sxs-lookup"><span data-stu-id="21a9d-127">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="21a9d-128">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="21a9d-128">Multidimensional Arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="21a9d-129">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="21a9d-129">Jagged Arrays</span></span>](jagged-arrays.md)
