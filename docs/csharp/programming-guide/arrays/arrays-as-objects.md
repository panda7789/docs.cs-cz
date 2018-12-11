---
title: Pole jako objekty - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 0bbbf7ecc5eff650f7a2edc73546833afd2be094
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242331"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="a592f-102">Pole jako objekty (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="a592f-102">Arrays as Objects (C# Programming Guide)</span></span>

<span data-ttu-id="a592f-103">V jazyce C# pole jsou ve skutečnosti objekty a právě adresovatelný oblastech souvislé paměti jako v jazyce C a C++.</span><span class="sxs-lookup"><span data-stu-id="a592f-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="a592f-104"><xref:System.Array> je abstraktní základní typ pro všechny typy polí.</span><span class="sxs-lookup"><span data-stu-id="a592f-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="a592f-105">Můžete použít vlastnosti a ostatních členů třídy, která <xref:System.Array> má.</span><span class="sxs-lookup"><span data-stu-id="a592f-105">You can use the properties, and other class members, that <xref:System.Array> has.</span></span> <span data-ttu-id="a592f-106">Příklad tohoto by pomocí <xref:System.Array.Length%2A> vlastnost získat délku pole.</span><span class="sxs-lookup"><span data-stu-id="a592f-106">An example of this would be using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="a592f-107">Následující kód přiřadí délka `numbers` pole, které je `5`, proměnné s názvem `lengthOfNumbers`:</span><span class="sxs-lookup"><span data-stu-id="a592f-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>  
  
 [!code-csharp[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]  
  
 <span data-ttu-id="a592f-108"><xref:System.Array> Třída poskytuje mnoho dalších užitečných metod a vlastností pro řazení, hledání a kopírování polí.</span><span class="sxs-lookup"><span data-stu-id="a592f-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a592f-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="a592f-109">Example</span></span>

 <span data-ttu-id="a592f-110">V tomto příkladu <xref:System.Array.Rank%2A> vlastnost zobrazíte počet rozměrů pole.</span><span class="sxs-lookup"><span data-stu-id="a592f-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a592f-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="a592f-111">See Also</span></span>

- [<span data-ttu-id="a592f-112">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a592f-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="a592f-113">Pole</span><span class="sxs-lookup"><span data-stu-id="a592f-113">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
- [<span data-ttu-id="a592f-114">Jednorozměrná pole</span><span class="sxs-lookup"><span data-stu-id="a592f-114">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
- [<span data-ttu-id="a592f-115">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="a592f-115">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
- [<span data-ttu-id="a592f-116">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="a592f-116">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
