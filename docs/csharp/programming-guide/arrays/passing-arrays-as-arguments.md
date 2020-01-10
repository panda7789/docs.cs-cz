---
title: Předávání polí jako argumentů – C# Průvodce programováním
ms.date: 07/05/2018
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: 2e53008910a9062ada25680eb4b8e54a225fd226
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705688"
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a><span data-ttu-id="8236d-102">Předávání polí jako argumentů (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="8236d-102">Passing arrays as arguments (C# Programming Guide)</span></span>

<span data-ttu-id="8236d-103">Pole mohou být předána jako argumenty parametrům metody.</span><span class="sxs-lookup"><span data-stu-id="8236d-103">Arrays can be passed as arguments to method parameters.</span></span> <span data-ttu-id="8236d-104">Vzhledem k tomu, že pole jsou odkazové typy, metoda může změnit hodnotu prvků.</span><span class="sxs-lookup"><span data-stu-id="8236d-104">Because arrays are reference types, the method can change the value of the elements.</span></span>

## <a name="passing-single-dimensional-arrays-as-arguments"></a><span data-ttu-id="8236d-105">Předávání jednorozměrného pole jako argumentů</span><span class="sxs-lookup"><span data-stu-id="8236d-105">Passing single-dimensional arrays as arguments</span></span>

<span data-ttu-id="8236d-106">Do metody můžete předat inicializované jednorozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="8236d-106">You can pass an initialized single-dimensional array to a method.</span></span> <span data-ttu-id="8236d-107">Například následující příkaz odešle pole do metody Print.</span><span class="sxs-lookup"><span data-stu-id="8236d-107">For example, the following statement sends an array to a print method.</span></span>

[!code-csharp[csProgGuideArrays#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#34)]

<span data-ttu-id="8236d-108">Následující kód ukazuje částečnou implementaci metody Print.</span><span class="sxs-lookup"><span data-stu-id="8236d-108">The following code shows a partial implementation of the print method.</span></span>

[!code-csharp[csProgGuideArrays#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#33)]

<span data-ttu-id="8236d-109">Můžete inicializovat a předat nové pole v jednom kroku, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8236d-109">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>

[!code-csharp[CsProgGuideArrays#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#35)]

### <a name="example"></a><span data-ttu-id="8236d-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="8236d-110">Example</span></span>

<span data-ttu-id="8236d-111">V následujícím příkladu je pole řetězců inicializováno a předáno jako argument metodě `DisplayArray` pro řetězce.</span><span class="sxs-lookup"><span data-stu-id="8236d-111">In the following example, an array of strings is initialized and passed as an argument to a `DisplayArray` method for strings.</span></span> <span data-ttu-id="8236d-112">Metoda zobrazí prvky pole.</span><span class="sxs-lookup"><span data-stu-id="8236d-112">The method displays the elements of the array.</span></span> <span data-ttu-id="8236d-113">Dále metoda `ChangeArray` obrátí prvky pole a poté metoda `ChangeArrayElements` upraví první tři prvky pole.</span><span class="sxs-lookup"><span data-stu-id="8236d-113">Next, the `ChangeArray` method reverses the array elements, and then the `ChangeArrayElements` method modifies the first three elements of the array.</span></span> <span data-ttu-id="8236d-114">Po vrácení každé metody metoda `DisplayArray` ukazuje, že předání pole hodnotou nezabrání změnám prvků pole.</span><span class="sxs-lookup"><span data-stu-id="8236d-114">After each method returns, the `DisplayArray` method shows that passing an array by value doesn't prevent changes to the array elements.</span></span>

[!code-csharp[csProgGuideArrays#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/ArrayExample.cs)]

## <a name="passing-multidimensional-arrays-as-arguments"></a><span data-ttu-id="8236d-115">Předávání multidimenzionálních polí jako argumentů</span><span class="sxs-lookup"><span data-stu-id="8236d-115">Passing multidimensional arrays as arguments</span></span>

<span data-ttu-id="8236d-116">Inicializované multidimenzionální pole do metody předáte stejným způsobem jako jednorozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="8236d-116">You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.</span></span>

[!code-csharp[csProgGuideArrays#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#41)]

<span data-ttu-id="8236d-117">Následující kód ukazuje částečnou deklaraci metody Print, která přijímá dvojrozměrné pole jako argument.</span><span class="sxs-lookup"><span data-stu-id="8236d-117">The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.</span></span>

[!code-csharp[csProgGuideArrays#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#36)]

<span data-ttu-id="8236d-118">Můžete inicializovat a předat nové pole v jednom kroku, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="8236d-118">You can initialize and pass a new array in one step, as is shown in the following example:</span></span>

[!code-csharp[csProgGuideArrays#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#32)]

### <a name="example"></a><span data-ttu-id="8236d-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="8236d-119">Example</span></span>

<span data-ttu-id="8236d-120">V následujícím příkladu je inicializováno dvojrozměrné pole celých čísel a předáno do metody `Print2DArray`.</span><span class="sxs-lookup"><span data-stu-id="8236d-120">In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method.</span></span> <span data-ttu-id="8236d-121">Metoda zobrazí prvky pole.</span><span class="sxs-lookup"><span data-stu-id="8236d-121">The method displays the elements of the array.</span></span>

[!code-csharp[csProgGuideArrays#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#31)]

## <a name="see-also"></a><span data-ttu-id="8236d-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8236d-122">See also</span></span>

- [<span data-ttu-id="8236d-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8236d-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8236d-124">Pole</span><span class="sxs-lookup"><span data-stu-id="8236d-124">Arrays</span></span>](index.md)
- [<span data-ttu-id="8236d-125">Jednorozměrná pole</span><span class="sxs-lookup"><span data-stu-id="8236d-125">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="8236d-126">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="8236d-126">Multidimensional Arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="8236d-127">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="8236d-127">Jagged Arrays</span></span>](jagged-arrays.md)
