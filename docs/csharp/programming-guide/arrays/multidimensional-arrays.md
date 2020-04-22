---
title: Vícerozměrná pole – programovací průvodce C#
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: ee5fae36ff844fadad7e1b6a766020319b67a83c
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021757"
---
# <a name="multidimensional-arrays-c-programming-guide"></a><span data-ttu-id="5aad2-102">Vícerozměrná pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="5aad2-102">Multidimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="5aad2-103">Pole mohou mít více než jednu dimenzi.</span><span class="sxs-lookup"><span data-stu-id="5aad2-103">Arrays can have more than one dimension.</span></span> <span data-ttu-id="5aad2-104">Například následující deklarace vytvoří dvojrozměrné pole čtyř řádků a dvou sloupců.</span><span class="sxs-lookup"><span data-stu-id="5aad2-104">For example, the following declaration creates a two-dimensional array of four rows and two columns.</span></span>  
  
 [!code-csharp[csProgGuideArrays#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#11)]  
  
 <span data-ttu-id="5aad2-105">Následující deklarace vytvoří pole tří dimenzí, 4, 2 a 3.</span><span class="sxs-lookup"><span data-stu-id="5aad2-105">The following declaration creates an array of three dimensions, 4, 2, and 3.</span></span>  
  
 [!code-csharp[csProgGuideArrays#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#12)]  
  
## <a name="array-initialization"></a><span data-ttu-id="5aad2-106">Inicializace pole</span><span class="sxs-lookup"><span data-stu-id="5aad2-106">Array Initialization</span></span>

 <span data-ttu-id="5aad2-107">Pole můžete inicializovat při deklaraci, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="5aad2-107">You can initialize the array upon declaration, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#13)]  
  
 <span data-ttu-id="5aad2-108">Můžete také inicializovat pole bez zadání pořadí.</span><span class="sxs-lookup"><span data-stu-id="5aad2-108">You can also initialize the array without specifying the rank.</span></span>  
  
 [!code-csharp[csProgGuideArrays#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#14)]  
  
 <span data-ttu-id="5aad2-109">Pokud se rozhodnete deklarovat proměnnou pole `new` bez inicializace, musíte použít operátor k přiřazení pole proměnné.</span><span class="sxs-lookup"><span data-stu-id="5aad2-109">If you choose to declare an array variable without initialization, you must use the `new` operator to assign an array to the variable.</span></span> <span data-ttu-id="5aad2-110">Použití `new` je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="5aad2-110">The use of `new` is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#15)]  
  
 <span data-ttu-id="5aad2-111">Následující příklad přiřadí hodnotu určitému prvku pole.</span><span class="sxs-lookup"><span data-stu-id="5aad2-111">The following example assigns a value to a particular array element.</span></span>  
  
 [!code-csharp[csProgGuideArrays#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#16)]  
  
 <span data-ttu-id="5aad2-112">Podobně následující příklad získá hodnotu určitého prvku pole a `elementValue`přiřadí jej proměnné .</span><span class="sxs-lookup"><span data-stu-id="5aad2-112">Similarly, the following example gets the value of a particular array element and assigns it to variable `elementValue`.</span></span>  
  
 [!code-csharp[csProgGuideArrays#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#42)]  
  
 <span data-ttu-id="5aad2-113">Následující příklad kódu inicializuje prvky pole na výchozí hodnoty (s výjimkou zubatých polí).</span><span class="sxs-lookup"><span data-stu-id="5aad2-113">The following code example initializes the array elements to default values (except for jagged arrays).</span></span>  
  
 [!code-csharp[csProgGuideArrays#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#17)]  
  
## <a name="see-also"></a><span data-ttu-id="5aad2-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="5aad2-114">See also</span></span>

- [<span data-ttu-id="5aad2-115">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5aad2-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5aad2-116">Pole</span><span class="sxs-lookup"><span data-stu-id="5aad2-116">Arrays</span></span>](./index.md)
- [<span data-ttu-id="5aad2-117">Jednorozměrná pole</span><span class="sxs-lookup"><span data-stu-id="5aad2-117">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="5aad2-118">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="5aad2-118">Jagged Arrays</span></span>](./jagged-arrays.md)
