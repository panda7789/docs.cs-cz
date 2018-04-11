---
title: Pole jako objekty (Průvodce programováním v C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e29685af509009f42f38ba2dbf8524075e880ff9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="5f207-102">Pole jako objekty (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="5f207-102">Arrays as Objects (C# Programming Guide)</span></span>
<span data-ttu-id="5f207-103">V jazyce C# pole jsou ve skutečnosti objekty a právě adresovatelné oblasti souvislé paměti jako C a C++.</span><span class="sxs-lookup"><span data-stu-id="5f207-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="5f207-104"><xref:System.Array>je abstraktní základní typ všechny typy polí.</span><span class="sxs-lookup"><span data-stu-id="5f207-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="5f207-105">Můžete použít vlastnosti a členy třídy, která <xref:System.Array> má.</span><span class="sxs-lookup"><span data-stu-id="5f207-105">You can use the properties, and other class members, that <xref:System.Array> has.</span></span> <span data-ttu-id="5f207-106">Příkladem by používat <xref:System.Array.Length%2A> vlastnost k získání délka pole.</span><span class="sxs-lookup"><span data-stu-id="5f207-106">An example of this would be using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="5f207-107">Následující kód přiřadí délka `numbers` pole, která je `5`, proměnné s názvem `lengthOfNumbers`:</span><span class="sxs-lookup"><span data-stu-id="5f207-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>  
  
 [!code-csharp[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]  
  
 <span data-ttu-id="5f207-108"><xref:System.Array> Třída poskytuje mnoho užitečných metod a vlastností pro řazení, vyhledávání a kopírování pole.</span><span class="sxs-lookup"><span data-stu-id="5f207-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f207-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="5f207-109">Example</span></span>  
 <span data-ttu-id="5f207-110">Tento příklad používá <xref:System.Array.Rank%2A> vlastnost zobrazíte počet rozměrů pole.</span><span class="sxs-lookup"><span data-stu-id="5f207-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5f207-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f207-111">See Also</span></span>  
 [<span data-ttu-id="5f207-112">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="5f207-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5f207-113">Pole</span><span class="sxs-lookup"><span data-stu-id="5f207-113">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="5f207-114">Jednorozměrná pole</span><span class="sxs-lookup"><span data-stu-id="5f207-114">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="5f207-115">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="5f207-115">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="5f207-116">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="5f207-116">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
