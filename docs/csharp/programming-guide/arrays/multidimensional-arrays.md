---
title: Multidimenzionální pole – Průvodce programováním v C#
description: Pole v jazyce C# mohou mít více než jednu dimenzi. Tato příklad deklarace vytvoří dvourozměrné pole se čtyřmi řádky a dva sloupce.
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: a2f204c0866672b317569fbc620aa8af60829ffd
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475005"
---
# <a name="multidimensional-arrays-c-programming-guide"></a><span data-ttu-id="95149-104">Vícerozměrná pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="95149-104">Multidimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="95149-105">Pole mohou mít více než jednu dimenzi.</span><span class="sxs-lookup"><span data-stu-id="95149-105">Arrays can have more than one dimension.</span></span> <span data-ttu-id="95149-106">Například následující deklarace vytvoří dvojrozměrné pole se čtyřmi řádky a dva sloupce.</span><span class="sxs-lookup"><span data-stu-id="95149-106">For example, the following declaration creates a two-dimensional array of four rows and two columns.</span></span>  
  
 [!code-csharp[csProgGuideArrays#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#11)]  
  
 <span data-ttu-id="95149-107">Následující deklarace vytvoří pole tří dimenzí, 4, 2 a 3.</span><span class="sxs-lookup"><span data-stu-id="95149-107">The following declaration creates an array of three dimensions, 4, 2, and 3.</span></span>  
  
 [!code-csharp[csProgGuideArrays#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#12)]  
  
## <a name="array-initialization"></a><span data-ttu-id="95149-108">Inicializace pole</span><span class="sxs-lookup"><span data-stu-id="95149-108">Array Initialization</span></span>

 <span data-ttu-id="95149-109">Můžete inicializovat pole na základě deklarace, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="95149-109">You can initialize the array upon declaration, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#13)]  
  
 <span data-ttu-id="95149-110">Můžete také inicializovat pole bez zadání pořadí.</span><span class="sxs-lookup"><span data-stu-id="95149-110">You can also initialize the array without specifying the rank.</span></span>  
  
 [!code-csharp[csProgGuideArrays#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#14)]  
  
 <span data-ttu-id="95149-111">Pokud se rozhodnete deklarovat proměnnou pole bez inicializace, je nutné použít `new` operátor k přiřazení pole k proměnné.</span><span class="sxs-lookup"><span data-stu-id="95149-111">If you choose to declare an array variable without initialization, you must use the `new` operator to assign an array to the variable.</span></span> <span data-ttu-id="95149-112">Použití `new` je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="95149-112">The use of `new` is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#15)]  
  
 <span data-ttu-id="95149-113">Následující příklad přiřadí hodnotu k určitému prvku pole.</span><span class="sxs-lookup"><span data-stu-id="95149-113">The following example assigns a value to a particular array element.</span></span>  
  
 [!code-csharp[csProgGuideArrays#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#16)]  
  
 <span data-ttu-id="95149-114">Podobně následující příklad získá hodnotu konkrétního prvku pole a přiřadí ho k proměnné `elementValue` .</span><span class="sxs-lookup"><span data-stu-id="95149-114">Similarly, the following example gets the value of a particular array element and assigns it to variable `elementValue`.</span></span>  
  
 [!code-csharp[csProgGuideArrays#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#42)]  
  
 <span data-ttu-id="95149-115">Následující příklad kódu inicializuje prvky pole na výchozí hodnoty (s výjimkou vícenásobných polí).</span><span class="sxs-lookup"><span data-stu-id="95149-115">The following code example initializes the array elements to default values (except for jagged arrays).</span></span>  
  
 [!code-csharp[csProgGuideArrays#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#17)]  
  
## <a name="see-also"></a><span data-ttu-id="95149-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="95149-116">See also</span></span>

- [<span data-ttu-id="95149-117">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="95149-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="95149-118">Pole</span><span class="sxs-lookup"><span data-stu-id="95149-118">Arrays</span></span>](./index.md)
- [<span data-ttu-id="95149-119">Jednorozměrná pole</span><span class="sxs-lookup"><span data-stu-id="95149-119">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="95149-120">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="95149-120">Jagged Arrays</span></span>](./jagged-arrays.md)
