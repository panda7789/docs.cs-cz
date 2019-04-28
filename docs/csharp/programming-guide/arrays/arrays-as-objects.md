---
title: Pole jako objekty - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 8500cf508b77a0fa7e348ce0fe6b1f16fd2bab25
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683974"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="a59d7-102">Pole jako objekty (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="a59d7-102">Arrays as Objects (C# Programming Guide)</span></span>

<span data-ttu-id="a59d7-103">V jazyce C# pole jsou ve skutečnosti objekty a právě adresovatelný oblastech souvislé paměti jako v jazyce C a C++.</span><span class="sxs-lookup"><span data-stu-id="a59d7-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="a59d7-104"><xref:System.Array> je abstraktní základní typ pro všechny typy polí.</span><span class="sxs-lookup"><span data-stu-id="a59d7-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="a59d7-105">Můžete použít vlastnosti a ostatních členů třídy, která <xref:System.Array> má.</span><span class="sxs-lookup"><span data-stu-id="a59d7-105">You can use the properties, and other class members, that <xref:System.Array> has.</span></span> <span data-ttu-id="a59d7-106">Příklad tohoto by pomocí <xref:System.Array.Length%2A> vlastnost získat délku pole.</span><span class="sxs-lookup"><span data-stu-id="a59d7-106">An example of this would be using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="a59d7-107">Následující kód přiřadí délka `numbers` pole, které je `5`, proměnné s názvem `lengthOfNumbers`:</span><span class="sxs-lookup"><span data-stu-id="a59d7-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>  
  
 [!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]  
  
 <span data-ttu-id="a59d7-108"><xref:System.Array> Třída poskytuje mnoho dalších užitečných metod a vlastností pro řazení, hledání a kopírování polí.</span><span class="sxs-lookup"><span data-stu-id="a59d7-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a59d7-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="a59d7-109">Example</span></span>

 <span data-ttu-id="a59d7-110">V tomto příkladu <xref:System.Array.Rank%2A> vlastnost zobrazíte počet rozměrů pole.</span><span class="sxs-lookup"><span data-stu-id="a59d7-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]  
  
## <a name="see-also"></a><span data-ttu-id="a59d7-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a59d7-111">See also</span></span>

- [<span data-ttu-id="a59d7-112">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a59d7-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="a59d7-113">Pole</span><span class="sxs-lookup"><span data-stu-id="a59d7-113">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)
- [<span data-ttu-id="a59d7-114">Jednorozměrná pole</span><span class="sxs-lookup"><span data-stu-id="a59d7-114">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)
- [<span data-ttu-id="a59d7-115">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="a59d7-115">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
- [<span data-ttu-id="a59d7-116">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="a59d7-116">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
