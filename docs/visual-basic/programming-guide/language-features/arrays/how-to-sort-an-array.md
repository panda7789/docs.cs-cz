---
title: 'Postupy: Řazení pole v jazyce Visual Basic'
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 467d1bcce6bda2feb5a8e59c152cb292d753e79b
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700979"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a><span data-ttu-id="13746-102">Postupy: řazení pole v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="13746-102">How to: sort an array in Visual Basic</span></span>

<span data-ttu-id="13746-103">Tento článek ukazuje příklad řazení pole řetězců v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="13746-103">This article shows an example of how to sort an array of strings in Visual Basic.</span></span>

## <a name="example"></a><span data-ttu-id="13746-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="13746-104">Example</span></span>

<span data-ttu-id="13746-105">Tento příklad deklaruje pole objektů `String` s názvem `zooAnimals`, naplní ho a pak ho seřadí podle abecedy:</span><span class="sxs-lookup"><span data-stu-id="13746-105">This example declares an array of `String` objects named `zooAnimals`, populates it, and then sorts it alphabetically:</span></span>
  
```vb
Private Sub SortAnimals()
    Dim zooAnimals(2) As String
    zooAnimals(0) = "lion"
    zooAnimals(1) = "turtle"
    zooAnimals(2) = "ostrich"
    Array.Sort(zooAnimals)
End Sub
```

## <a name="robust-programming"></a><span data-ttu-id="13746-106">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="13746-106">Robust programming</span></span>

<span data-ttu-id="13746-107">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="13746-107">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="13746-108">Pole je prázdné (<xref:System.ArgumentNullException> Class).</span><span class="sxs-lookup"><span data-stu-id="13746-108">Array is empty (<xref:System.ArgumentNullException> class).</span></span>
- <span data-ttu-id="13746-109">Array je multidimenzionální (<xref:System.RankException> Class).</span><span class="sxs-lookup"><span data-stu-id="13746-109">Array is multidimensional (<xref:System.RankException> class).</span></span>
- <span data-ttu-id="13746-110">Jeden nebo více prvků pole neimplementuje rozhraní <xref:System.IComparable> (třída <xref:System.InvalidOperationException>).</span><span class="sxs-lookup"><span data-stu-id="13746-110">One or more elements of the array don't implement the <xref:System.IComparable> interface (<xref:System.InvalidOperationException> class).</span></span>

## <a name="see-also"></a><span data-ttu-id="13746-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="13746-111">See also</span></span>

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [<span data-ttu-id="13746-112">Pole</span><span class="sxs-lookup"><span data-stu-id="13746-112">Arrays</span></span>](index.md)
- [<span data-ttu-id="13746-113">Řešení potíží s poli</span><span class="sxs-lookup"><span data-stu-id="13746-113">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
- [<span data-ttu-id="13746-114">Kolekce</span><span class="sxs-lookup"><span data-stu-id="13746-114">Collections</span></span>](../../concepts/collections.md)
- [<span data-ttu-id="13746-115">Příkaz For Each...Next</span><span class="sxs-lookup"><span data-stu-id="13746-115">For Each...Next Statement</span></span>](../../../language-reference/statements/for-each-next-statement.md)
