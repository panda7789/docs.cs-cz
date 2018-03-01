---
title: "Předávání polí jako argumentů (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f152173b747a171052ab99f261ed91ced9465fdc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a><span data-ttu-id="e9920-102">Předávání polí jako argumentů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="e9920-102">Passing Arrays as Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="e9920-103">Pole může být předán jako argumenty pro parametry metody.</span><span class="sxs-lookup"><span data-stu-id="e9920-103">Arrays can be passed as arguments to method parameters.</span></span> <span data-ttu-id="e9920-104">Vzhledem k tomu, že pole jsou odkazové typy, metodu můžete změnit hodnotu elementy.</span><span class="sxs-lookup"><span data-stu-id="e9920-104">Because arrays are reference types, the method can change the value of the elements.</span></span>  
  
## <a name="passing-single-dimensional-arrays-as-arguments"></a><span data-ttu-id="e9920-105">Jednorozměrná předávání polí jako argumentů</span><span class="sxs-lookup"><span data-stu-id="e9920-105">Passing Single-Dimensional Arrays As Arguments</span></span>  
 <span data-ttu-id="e9920-106">Metodu lze předat inicializovaného jednorozměrná pole.</span><span class="sxs-lookup"><span data-stu-id="e9920-106">You can pass an initialized single-dimensional array to a method.</span></span> <span data-ttu-id="e9920-107">Následující příkaz například odešle pole tiskové metodě.</span><span class="sxs-lookup"><span data-stu-id="e9920-107">For example, the following statement sends an array to a print method.</span></span>  
  
 [!code-csharp[csProgGuideArrays#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_1.cs)]  
  
 <span data-ttu-id="e9920-108">Následující kód ukazuje částečnou implementaci metodu tisku.</span><span class="sxs-lookup"><span data-stu-id="e9920-108">The following code shows a partial implementation of the print method.</span></span>  
  
 [!code-csharp[csProgGuideArrays#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_2.cs)]  
  
 <span data-ttu-id="e9920-109">Můžete inicializovat a předat nové pole v jednom kroku, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e9920-109">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>  
  
 [!code-csharp[CsProgGuideArrays#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="e9920-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="e9920-110">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="e9920-111">Popis</span><span class="sxs-lookup"><span data-stu-id="e9920-111">Description</span></span>  
 <span data-ttu-id="e9920-112">V následujícím příkladu je pole řetězců inicializovat a předat jako argument k `PrintArray` metoda pro řetězce.</span><span class="sxs-lookup"><span data-stu-id="e9920-112">In the following example, an array of strings is initialized and passed as an argument to a `PrintArray` method for strings.</span></span> <span data-ttu-id="e9920-113">Metoda zobrazí elementy pole.</span><span class="sxs-lookup"><span data-stu-id="e9920-113">The method displays the elements of the array.</span></span> <span data-ttu-id="e9920-114">Dále metody `ChangeArray` a `ChangeArrayElement` se nazývají prokázat, že odesílání argument pole hodnotou nebrání změny na elementy pole.</span><span class="sxs-lookup"><span data-stu-id="e9920-114">Next, methods `ChangeArray` and `ChangeArrayElement` are called to demonstrate that sending an array argument by value does not prevent changes to the array elements.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e9920-115">Kód</span><span class="sxs-lookup"><span data-stu-id="e9920-115">Code</span></span>  
 [!code-csharp[csProgGuideArrays#30](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_4.cs)]  
  
## <a name="passing-multidimensional-arrays-as-arguments"></a><span data-ttu-id="e9920-116">Vícerozměrná pole předání jako argumentů</span><span class="sxs-lookup"><span data-stu-id="e9920-116">Passing Multidimensional Arrays As Arguments</span></span>  
 <span data-ttu-id="e9920-117">Inicializovaného multidimenzionálního pole můžete předat metodě stejným způsobem, že předáváte jednorozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="e9920-117">You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_5.cs)]  
  
 <span data-ttu-id="e9920-118">Následující kód ukazuje částečné deklaraci tiskové metodu, která přijímá dvourozměrná pole jako její argument.</span><span class="sxs-lookup"><span data-stu-id="e9920-118">The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.</span></span>  
  
 [!code-csharp[csProgGuideArrays#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_6.cs)]  
  
 <span data-ttu-id="e9920-119">Můžete inicializovat a předat nové pole v jednom kroku, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e9920-119">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_7.cs)]  
  
## <a name="example"></a><span data-ttu-id="e9920-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="e9920-120">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="e9920-121">Popis</span><span class="sxs-lookup"><span data-stu-id="e9920-121">Description</span></span>  
 <span data-ttu-id="e9920-122">V následujícím příkladu je inicializován a předaný dvourozměrná pole celých čísel `Print2DArray` metoda.</span><span class="sxs-lookup"><span data-stu-id="e9920-122">In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method.</span></span> <span data-ttu-id="e9920-123">Metoda zobrazí elementy pole.</span><span class="sxs-lookup"><span data-stu-id="e9920-123">The method displays the elements of the array.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e9920-124">Kód</span><span class="sxs-lookup"><span data-stu-id="e9920-124">Code</span></span>  
 [!code-csharp[csProgGuideArrays#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_8.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e9920-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9920-125">See Also</span></span>  
 [<span data-ttu-id="e9920-126">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="e9920-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e9920-127">Pole</span><span class="sxs-lookup"><span data-stu-id="e9920-127">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="e9920-128">Jednorozměrná pole</span><span class="sxs-lookup"><span data-stu-id="e9920-128">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="e9920-129">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="e9920-129">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="e9920-130">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="e9920-130">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
