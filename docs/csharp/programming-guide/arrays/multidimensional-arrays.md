---
title: Multidimenzionální pole – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: 63b8729a14e4c309e85a588c5cddc692fb6a6fad
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597405"
---
# <a name="multidimensional-arrays-c-programming-guide"></a><span data-ttu-id="2b150-102">Vícerozměrná pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="2b150-102">Multidimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="2b150-103">Pole mohou mít více než jednu dimenzi.</span><span class="sxs-lookup"><span data-stu-id="2b150-103">Arrays can have more than one dimension.</span></span> <span data-ttu-id="2b150-104">Například následující deklarace vytvoří dvojrozměrné pole se čtyřmi řádky a dva sloupce.</span><span class="sxs-lookup"><span data-stu-id="2b150-104">For example, the following declaration creates a two-dimensional array of four rows and two columns.</span></span>  
  
 [!code-csharp[csProgGuideArrays#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#11)]  
  
 <span data-ttu-id="2b150-105">Následující deklarace vytvoří pole tří dimenzí, 4, 2 a 3.</span><span class="sxs-lookup"><span data-stu-id="2b150-105">The following declaration creates an array of three dimensions, 4, 2, and 3.</span></span>  
  
 [!code-csharp[csProgGuideArrays#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#12)]  
  
## <a name="array-initialization"></a><span data-ttu-id="2b150-106">Inicializace pole</span><span class="sxs-lookup"><span data-stu-id="2b150-106">Array Initialization</span></span>

 <span data-ttu-id="2b150-107">Můžete inicializovat pole na základě deklarace, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2b150-107">You can initialize the array upon declaration, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#13)]  
  
 <span data-ttu-id="2b150-108">Můžete také inicializovat pole bez zadání pořadí.</span><span class="sxs-lookup"><span data-stu-id="2b150-108">You also can initialize the array without specifying the rank.</span></span>  
  
 [!code-csharp[csProgGuideArrays#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#14)]  
  
 <span data-ttu-id="2b150-109">Pokud se rozhodnete deklarovat proměnnou pole bez inicializace, je nutné použít `new` operátor k přiřazení pole k proměnné.</span><span class="sxs-lookup"><span data-stu-id="2b150-109">If you choose to declare an array variable without initialization, you must use the `new` operator to assign an array to the variable.</span></span> <span data-ttu-id="2b150-110">Použití `new` je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2b150-110">The use of `new` is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#15)]  
  
 <span data-ttu-id="2b150-111">Následující příklad přiřadí hodnotu k určitému prvku pole.</span><span class="sxs-lookup"><span data-stu-id="2b150-111">The following example assigns a value to a particular array element.</span></span>  
  
 [!code-csharp[csProgGuideArrays#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#16)]  
  
 <span data-ttu-id="2b150-112">Podobně následující příklad získá hodnotu konkrétního prvku pole a přiřadí ho k proměnné `elementValue`.</span><span class="sxs-lookup"><span data-stu-id="2b150-112">Similarly, the following example gets the value of a particular array element and assigns it to variable `elementValue`.</span></span>  
  
 [!code-csharp[csProgGuideArrays#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#42)]  
  
 <span data-ttu-id="2b150-113">Následující příklad kódu inicializuje prvky pole na výchozí hodnoty (s výjimkou vícenásobných polí).</span><span class="sxs-lookup"><span data-stu-id="2b150-113">The following code example initializes the array elements to default values (except for jagged arrays).</span></span>  
  
 [!code-csharp[csProgGuideArrays#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#17)]  
  
## <a name="see-also"></a><span data-ttu-id="2b150-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b150-114">See also</span></span>

- [<span data-ttu-id="2b150-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="2b150-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2b150-116">Pole</span><span class="sxs-lookup"><span data-stu-id="2b150-116">Arrays</span></span>](./index.md)
- [<span data-ttu-id="2b150-117">Jednorozměrná pole</span><span class="sxs-lookup"><span data-stu-id="2b150-117">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="2b150-118">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="2b150-118">Jagged Arrays</span></span>](./jagged-arrays.md)
