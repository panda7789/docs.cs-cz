---
title: 'Postupy: Řazení pole v jazyce Visual Basic'
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 0b04bfbedf9d7266d1b2e190fa85b8a64cf6efbf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558433"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a><span data-ttu-id="81d15-102">Postupy: Řazení pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="81d15-102">How to: Sort An Array in Visual Basic</span></span>
<span data-ttu-id="81d15-103">V tomto příkladu deklaruje pole `String` objektů s názvem `zooAnimals`, naplní ho a pak ho seřadí podle abecedy.</span><span class="sxs-lookup"><span data-stu-id="81d15-103">This example declares an array of `String` objects named `zooAnimals`, populates it, and then sorts it alphabetically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81d15-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="81d15-104">Example</span></span>  
  
```  
Private Sub sortAnimals()  
    Dim zooAnimals(2) As String  
    zooAnimals(0) = "lion"  
    zooAnimals(1) = "turtle"  
    zooAnimals(2) = "ostrich"  
    Array.Sort(zooAnimals)  
End Sub  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="81d15-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="81d15-105">Compiling the Code</span></span>  
 <span data-ttu-id="81d15-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="81d15-106">This example requires:</span></span>  
  
-   <span data-ttu-id="81d15-107">Přístup k Mscorlib.dll a <xref:System> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="81d15-107">Access to Mscorlib.dll and the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="81d15-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="81d15-108">Robust Programming</span></span>  
 <span data-ttu-id="81d15-109">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="81d15-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="81d15-110">Pole je prázdné (<xref:System.ArgumentNullException> třídy)</span><span class="sxs-lookup"><span data-stu-id="81d15-110">Array is empty (<xref:System.ArgumentNullException> class)</span></span>  
  
-   <span data-ttu-id="81d15-111">Pole je vícerozměrné (<xref:System.RankException> třídy)</span><span class="sxs-lookup"><span data-stu-id="81d15-111">Array is multidimensional (<xref:System.RankException> class)</span></span>  
  
-   <span data-ttu-id="81d15-112">Jeden nebo více prvků pole neimplementují <xref:System.IComparable> rozhraní (<xref:System.InvalidOperationException> třídy)</span><span class="sxs-lookup"><span data-stu-id="81d15-112">One or more elements of the array do not implement the <xref:System.IComparable> interface (<xref:System.InvalidOperationException> class)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81d15-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="81d15-113">See also</span></span>
- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [<span data-ttu-id="81d15-114">Pole</span><span class="sxs-lookup"><span data-stu-id="81d15-114">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="81d15-115">Řešení potíží s poli</span><span class="sxs-lookup"><span data-stu-id="81d15-115">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [<span data-ttu-id="81d15-116">Kolekce</span><span class="sxs-lookup"><span data-stu-id="81d15-116">Collections</span></span>](../../concepts/collections.md)
- [<span data-ttu-id="81d15-117">Příkaz For Each...Next</span><span class="sxs-lookup"><span data-stu-id="81d15-117">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
