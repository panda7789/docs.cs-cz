---
title: Pole jako objekty – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: d8b929eccf9be259874d03dd93f49a49798bb349
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715095"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="34756-102">Pole jako objekty (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="34756-102">Arrays as Objects (C# Programming Guide)</span></span>

<span data-ttu-id="34756-103">V jazyce C# pole jsou ve skutečnosti objekty a není pouze adresovatelné oblasti souvislé paměti jako v jazyce C a C++.</span><span class="sxs-lookup"><span data-stu-id="34756-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="34756-104"><xref:System.Array>je abstraktní základní typ všech typů polí.</span><span class="sxs-lookup"><span data-stu-id="34756-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="34756-105">Můžete použít vlastnosti a další <xref:System.Array> členy třídy, které má.</span><span class="sxs-lookup"><span data-stu-id="34756-105">You can use the properties and other class members that <xref:System.Array> has.</span></span> <span data-ttu-id="34756-106">Příkladem je použití vlastnosti <xref:System.Array.Length%2A> získat délku pole.</span><span class="sxs-lookup"><span data-stu-id="34756-106">An example of this is using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="34756-107">Následující kód přiřadí délku `numbers` pole, `5`což je , `lengthOfNumbers`proměnné s názvem :</span><span class="sxs-lookup"><span data-stu-id="34756-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<span data-ttu-id="34756-108">Třída <xref:System.Array> poskytuje mnoho dalších užitečných metod a vlastností pro řazení, vyhledávání a kopírování polí.</span><span class="sxs-lookup"><span data-stu-id="34756-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>

## <a name="example"></a><span data-ttu-id="34756-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="34756-109">Example</span></span>

<span data-ttu-id="34756-110">Tento příklad <xref:System.Array.Rank%2A> používá vlastnost k zobrazení počtu dimenzí pole.</span><span class="sxs-lookup"><span data-stu-id="34756-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a><span data-ttu-id="34756-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="34756-111">See also</span></span>

- [<span data-ttu-id="34756-112">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="34756-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="34756-113">Pole</span><span class="sxs-lookup"><span data-stu-id="34756-113">Arrays</span></span>](./index.md)
- [<span data-ttu-id="34756-114">Jednorozměrná pole</span><span class="sxs-lookup"><span data-stu-id="34756-114">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="34756-115">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="34756-115">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="34756-116">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="34756-116">Jagged Arrays</span></span>](./jagged-arrays.md)
