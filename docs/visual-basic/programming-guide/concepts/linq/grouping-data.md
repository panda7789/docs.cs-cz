---
title: Seskupování dat (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
ms.openlocfilehash: e2732c91dfff65ebb86ef45296ba369c3073a8f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644196"
---
# <a name="grouping-data-visual-basic"></a><span data-ttu-id="98d47-102">Seskupování dat (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98d47-102">Grouping Data (Visual Basic)</span></span>
<span data-ttu-id="98d47-103">Seskupení odkazuje na operaci ukládání dat do skupin tak, aby elementy v každé skupině sdílejí společný atribut.</span><span class="sxs-lookup"><span data-stu-id="98d47-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="98d47-104">Následující obrázek znázorňuje výsledky seskupování posloupnost znaků.</span><span class="sxs-lookup"><span data-stu-id="98d47-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="98d47-105">Klíč pro každou skupinu je znak.</span><span class="sxs-lookup"><span data-stu-id="98d47-105">The key for each group is the character.</span></span>  
  
 <span data-ttu-id="98d47-106">![Operace seskupení LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span><span class="sxs-lookup"><span data-stu-id="98d47-106">![LINQ Grouping Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span></span>  
  
 <span data-ttu-id="98d47-107">V následující části jsou uvedené metody operátor standardní dotazů, které seskupují datové prvky.</span><span class="sxs-lookup"><span data-stu-id="98d47-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="98d47-108">Metody</span><span class="sxs-lookup"><span data-stu-id="98d47-108">Methods</span></span>  
  
|<span data-ttu-id="98d47-109">Název metody</span><span class="sxs-lookup"><span data-stu-id="98d47-109">Method Name</span></span>|<span data-ttu-id="98d47-110">Popis</span><span class="sxs-lookup"><span data-stu-id="98d47-110">Description</span></span>|<span data-ttu-id="98d47-111">Syntaxe výrazu dotazu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="98d47-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="98d47-112">Další informace</span><span class="sxs-lookup"><span data-stu-id="98d47-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="98d47-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="98d47-113">GroupBy</span></span>|<span data-ttu-id="98d47-114">Prvky skupiny, které sdílejí společný atribut.</span><span class="sxs-lookup"><span data-stu-id="98d47-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="98d47-115">Každá skupina je reprezentována <xref:System.Linq.IGrouping%602> objektu.</span><span class="sxs-lookup"><span data-stu-id="98d47-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="98d47-116">ToLookup</span><span class="sxs-lookup"><span data-stu-id="98d47-116">ToLookup</span></span>|<span data-ttu-id="98d47-117">Vloží elementy do <xref:System.Linq.Lookup%602> (slovník 1 n) podle funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="98d47-117">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="98d47-118">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="98d47-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="98d47-119">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="98d47-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="98d47-120">Následující příklad kódu používá `Group By` klauzule na celá čísla skupinu v seznamu podle toho, zda jsou popisných.</span><span class="sxs-lookup"><span data-stu-id="98d47-120">The following code example uses the `Group By` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
```vb  
Dim numbers As New System.Collections.Generic.List(Of Integer)(  
     New Integer() {35, 44, 200, 84, 3987, 4, 199, 329, 446, 208})  
  
Dim query = From number In numbers   
            Group By Remainder = (number Mod 2) Into Group  
  
Dim sb As New System.Text.StringBuilder()  
For Each group In query  
    sb.AppendLine(If(group.Remainder = 0, vbCrLf & "Even numbers:", vbCrLf & "Odd numbers:"))  
    For Each num In group.Group  
        sb.AppendLine(num)  
    Next  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' Odd numbers:  
' 35  
' 3987  
' 199  
' 329  
  
' Even numbers:  
' 44  
' 200  
' 84  
' 4  
' 446  
' 208  
```  
  
## <a name="see-also"></a><span data-ttu-id="98d47-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="98d47-121">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="98d47-122">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98d47-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="98d47-123">Klauzule Group By</span><span class="sxs-lookup"><span data-stu-id="98d47-123">Group By Clause</span></span>](../../../../visual-basic/language-reference/queries/group-by-clause.md)  
 [<span data-ttu-id="98d47-124">Postupy: seskupování souborů podle přípony (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98d47-124">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 [<span data-ttu-id="98d47-125">Postupy: rozdělení souboru na mnoho souborů pomocí skupin (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98d47-125">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
