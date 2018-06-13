---
title: Pole jako objekty (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 07e824d21ffc02ba7a3c33507d22d1dc7a1ac638
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33312605"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="f2e18-102">Pole jako objekty (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="f2e18-102">Arrays as Objects (C# Programming Guide)</span></span>
<span data-ttu-id="f2e18-103">V jazyce C# pole jsou ve skutečnosti objekty a právě adresovatelné oblasti souvislé paměti jako C a C++.</span><span class="sxs-lookup"><span data-stu-id="f2e18-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="f2e18-104"><xref:System.Array> je abstraktní základní typ všechny typy polí.</span><span class="sxs-lookup"><span data-stu-id="f2e18-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="f2e18-105">Můžete použít vlastnosti a členy třídy, která <xref:System.Array> má.</span><span class="sxs-lookup"><span data-stu-id="f2e18-105">You can use the properties, and other class members, that <xref:System.Array> has.</span></span> <span data-ttu-id="f2e18-106">Příkladem by používat <xref:System.Array.Length%2A> vlastnost k získání délka pole.</span><span class="sxs-lookup"><span data-stu-id="f2e18-106">An example of this would be using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="f2e18-107">Následující kód přiřadí délka `numbers` pole, která je `5`, proměnné s názvem `lengthOfNumbers`:</span><span class="sxs-lookup"><span data-stu-id="f2e18-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>  
  
 [!code-csharp[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]  
  
 <span data-ttu-id="f2e18-108"><xref:System.Array> Třída poskytuje mnoho užitečných metod a vlastností pro řazení, vyhledávání a kopírování pole.</span><span class="sxs-lookup"><span data-stu-id="f2e18-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2e18-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2e18-109">Example</span></span>  
 <span data-ttu-id="f2e18-110">Tento příklad používá <xref:System.Array.Rank%2A> vlastnost zobrazíte počet rozměrů pole.</span><span class="sxs-lookup"><span data-stu-id="f2e18-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f2e18-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2e18-111">See Also</span></span>  
 [<span data-ttu-id="f2e18-112">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f2e18-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f2e18-113">Pole</span><span class="sxs-lookup"><span data-stu-id="f2e18-113">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="f2e18-114">Jednorozměrná pole</span><span class="sxs-lookup"><span data-stu-id="f2e18-114">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="f2e18-115">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="f2e18-115">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="f2e18-116">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="f2e18-116">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
