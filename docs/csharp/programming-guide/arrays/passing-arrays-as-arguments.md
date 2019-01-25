---
title: Předávání polí jako argumentů - C# Průvodce programováním pro službu
ms.custom: seodec18
ms.date: 07/05/2018
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: 1538988c1145a19055074b440f04cbaac4ef7aa7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741175"
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a><span data-ttu-id="bb2a2-102">Předávání polí jako argumentů (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="bb2a2-102">Passing arrays as arguments (C# Programming Guide)</span></span>

<span data-ttu-id="bb2a2-103">Pole může být předány jako argumenty na parametry metod.</span><span class="sxs-lookup"><span data-stu-id="bb2a2-103">Arrays can be passed as arguments to method parameters.</span></span> <span data-ttu-id="bb2a2-104">Protože pole jsou typy odkazů, metodu můžete změnit hodnotu prvků.</span><span class="sxs-lookup"><span data-stu-id="bb2a2-104">Because arrays are reference types, the method can change the value of the elements.</span></span>

## <a name="passing-single-dimensional-arrays-as-arguments"></a><span data-ttu-id="bb2a2-105">Jednorozměrná předávání polí jako argumentů</span><span class="sxs-lookup"><span data-stu-id="bb2a2-105">Passing single-dimensional arrays as arguments</span></span>

<span data-ttu-id="bb2a2-106">Metodu můžete předat inicializované jednorozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="bb2a2-106">You can pass an initialized single-dimensional array to a method.</span></span> <span data-ttu-id="bb2a2-107">Například následující příkaz odešle pole tisku metodě.</span><span class="sxs-lookup"><span data-stu-id="bb2a2-107">For example, the following statement sends an array to a print method.</span></span>

[!code-csharp[csProgGuideArrays#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#34)]

<span data-ttu-id="bb2a2-108">Následující kód ukazuje částečnou implementaci metody tisku.</span><span class="sxs-lookup"><span data-stu-id="bb2a2-108">The following code shows a partial implementation of the print method.</span></span>

[!code-csharp[csProgGuideArrays#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#33)]

<span data-ttu-id="bb2a2-109">Můžete inicializovat a předat nové pole v jednom kroku, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="bb2a2-109">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>

[!code-csharp[CsProgGuideArrays#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#35)]

### <a name="example"></a><span data-ttu-id="bb2a2-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="bb2a2-110">Example</span></span>

<span data-ttu-id="bb2a2-111">V následujícím příkladu je pole řetězců inicializován a předat jako argument `DisplayArray` metodu pro řetězce.</span><span class="sxs-lookup"><span data-stu-id="bb2a2-111">In the following example, an array of strings is initialized and passed as an argument to a `DisplayArray` method for strings.</span></span> <span data-ttu-id="bb2a2-112">Metoda zobrazí prvků pole.</span><span class="sxs-lookup"><span data-stu-id="bb2a2-112">The method displays the elements of the array.</span></span> <span data-ttu-id="bb2a2-113">Dále `ChangeArray` metoda obrátí prvků pole a pak `ChangeArrayElements` metoda upraví první tři prvky pole.</span><span class="sxs-lookup"><span data-stu-id="bb2a2-113">Next, the `ChangeArray` method reverses the array elements, and then the `ChangeArrayElements` method modifies the first three elements of the array.</span></span> <span data-ttu-id="bb2a2-114">Poté, co každá metoda vrací výsledek, `DisplayArray` metoda ukazuje, že předá podle hodnoty pole nezabrání změny k prvkům pole.</span><span class="sxs-lookup"><span data-stu-id="bb2a2-114">After each method returns, the `DisplayArray` method shows that passing an array by value doesn't prevent changes to the array elements.</span></span>

[!code-csharp[csProgGuideArrays#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/ArrayExample.cs)]

## <a name="passing-multidimensional-arrays-as-arguments"></a><span data-ttu-id="bb2a2-115">Předání vícerozměrných polí jako argumentů</span><span class="sxs-lookup"><span data-stu-id="bb2a2-115">Passing multidimensional arrays as arguments</span></span>

<span data-ttu-id="bb2a2-116">Inicializované vícerozměrná pole můžete předat metodě stejným způsobem, který předáte jednorozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="bb2a2-116">You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.</span></span>

[!code-csharp[csProgGuideArrays#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#41)]

<span data-ttu-id="bb2a2-117">Následující kód znázorňuje deklaraci částečné tisku metody, která přijímá jako svůj argument dvourozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="bb2a2-117">The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.</span></span>

[!code-csharp[csProgGuideArrays#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#36)]

<span data-ttu-id="bb2a2-118">Můžete inicializovat a předejte nové pole v jednom kroku, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="bb2a2-118">You can initialize and pass a new array in one step, as is shown in the following example:</span></span>

[!code-csharp[csProgGuideArrays#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#32)]

### <a name="example"></a><span data-ttu-id="bb2a2-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="bb2a2-119">Example</span></span>

<span data-ttu-id="bb2a2-120">V následujícím příkladu je inicializován a předat dvourozměrné pole celých čísel `Print2DArray` metody.</span><span class="sxs-lookup"><span data-stu-id="bb2a2-120">In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method.</span></span> <span data-ttu-id="bb2a2-121">Metoda zobrazí prvků pole.</span><span class="sxs-lookup"><span data-stu-id="bb2a2-121">The method displays the elements of the array.</span></span>

[!code-csharp[csProgGuideArrays#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#31)]

## <a name="see-also"></a><span data-ttu-id="bb2a2-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb2a2-122">See also</span></span>

- [<span data-ttu-id="bb2a2-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="bb2a2-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="bb2a2-124">Pole</span><span class="sxs-lookup"><span data-stu-id="bb2a2-124">Arrays</span></span>](index.md)
- [<span data-ttu-id="bb2a2-125">Jednorozměrná pole</span><span class="sxs-lookup"><span data-stu-id="bb2a2-125">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="bb2a2-126">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="bb2a2-126">Multidimensional Arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="bb2a2-127">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="bb2a2-127">Jagged Arrays</span></span>](jagged-arrays.md)
