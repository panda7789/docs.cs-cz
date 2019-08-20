---
title: Pole jako objekty – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: fd4496e0f84953204ad8c3f40db699e911c3f477
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597358"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="644ad-102">Pole jako objekty (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="644ad-102">Arrays as Objects (C# Programming Guide)</span></span>

<span data-ttu-id="644ad-103">V C#jsou pole vlastně objekty a nikoli pouze adresovatelné oblasti souvislé paměti jako v jazyce C a C++.</span><span class="sxs-lookup"><span data-stu-id="644ad-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="644ad-104"><xref:System.Array>je abstraktní základní typ pro všechny typy polí.</span><span class="sxs-lookup"><span data-stu-id="644ad-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="644ad-105">Můžete použít vlastnosti a další členy třídy, které <xref:System.Array> mají.</span><span class="sxs-lookup"><span data-stu-id="644ad-105">You can use the properties, and other class members, that <xref:System.Array> has.</span></span> <span data-ttu-id="644ad-106">Příkladem je použití <xref:System.Array.Length%2A> vlastnosti k získání délky pole.</span><span class="sxs-lookup"><span data-stu-id="644ad-106">An example of this would be using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="644ad-107">Následující kód přiřadí délku `numbers` pole, `5`tj. proměnné s názvem `lengthOfNumbers`:</span><span class="sxs-lookup"><span data-stu-id="644ad-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>  
  
 [!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]  
  
 <span data-ttu-id="644ad-108"><xref:System.Array> Třída poskytuje mnoho dalších užitečných metod a vlastností pro řazení, vyhledávání a kopírování polí.</span><span class="sxs-lookup"><span data-stu-id="644ad-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>  
  
## <a name="example"></a><span data-ttu-id="644ad-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="644ad-109">Example</span></span>

 <span data-ttu-id="644ad-110">Tento příklad používá <xref:System.Array.Rank%2A> vlastnost k zobrazení počtu rozměrů pole.</span><span class="sxs-lookup"><span data-stu-id="644ad-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]  
  
## <a name="see-also"></a><span data-ttu-id="644ad-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="644ad-111">See also</span></span>

- [<span data-ttu-id="644ad-112">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="644ad-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="644ad-113">Pole</span><span class="sxs-lookup"><span data-stu-id="644ad-113">Arrays</span></span>](./index.md)
- [<span data-ttu-id="644ad-114">Jednorozměrná pole</span><span class="sxs-lookup"><span data-stu-id="644ad-114">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="644ad-115">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="644ad-115">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="644ad-116">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="644ad-116">Jagged Arrays</span></span>](./jagged-arrays.md)
