---
title: Seskupování dat (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
ms.openlocfilehash: 14b114906a0e04a4d11c323f80b070603a7286c0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576960"
---
# <a name="grouping-data-visual-basic"></a><span data-ttu-id="57480-102">Seskupování dat (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57480-102">Grouping Data (Visual Basic)</span></span>
<span data-ttu-id="57480-103">Seskupení odkazuje na operace ukládání dat do skupin, aby elementy v každé skupině sdílet společný atribut.</span><span class="sxs-lookup"><span data-stu-id="57480-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="57480-104">Následující obrázek ukazuje výsledky seskupení posloupnost znaků.</span><span class="sxs-lookup"><span data-stu-id="57480-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="57480-105">Klíč pro každou skupinu je znak.</span><span class="sxs-lookup"><span data-stu-id="57480-105">The key for each group is the character.</span></span>  
  
 <span data-ttu-id="57480-106">![LINQ Grouping Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span><span class="sxs-lookup"><span data-stu-id="57480-106">![LINQ Grouping Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span></span>  
  
 <span data-ttu-id="57480-107">Standardní metody operátoru dotazu, které seskupují datové prvky jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="57480-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="57480-108">Metody</span><span class="sxs-lookup"><span data-stu-id="57480-108">Methods</span></span>  
  
|<span data-ttu-id="57480-109">Název metody</span><span class="sxs-lookup"><span data-stu-id="57480-109">Method Name</span></span>|<span data-ttu-id="57480-110">Popis</span><span class="sxs-lookup"><span data-stu-id="57480-110">Description</span></span>|<span data-ttu-id="57480-111">Syntaxe výrazu dotazu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="57480-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="57480-112">Další informace</span><span class="sxs-lookup"><span data-stu-id="57480-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="57480-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="57480-113">GroupBy</span></span>|<span data-ttu-id="57480-114">Seskupí elementy, které sdílejí společný atribut.</span><span class="sxs-lookup"><span data-stu-id="57480-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="57480-115">Každá skupina představuje <xref:System.Linq.IGrouping%602> objektu.</span><span class="sxs-lookup"><span data-stu-id="57480-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="57480-116">ToLookup</span><span class="sxs-lookup"><span data-stu-id="57480-116">ToLookup</span></span>|<span data-ttu-id="57480-117">Vloží prvky do <xref:System.Linq.Lookup%602> (jeden na mnoho slovník) podle funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="57480-117">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="57480-118">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="57480-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="57480-119">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="57480-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="57480-120">Následující příklad kódu používá `Group By` klauzule, která skupina celých čísel v seznamu podle toho, zda jsou sudý, nebo lichý.</span><span class="sxs-lookup"><span data-stu-id="57480-120">The following code example uses the `Group By` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="57480-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57480-121">See also</span></span>
- <xref:System.Linq>
- [<span data-ttu-id="57480-122">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57480-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="57480-123">Klauzule Group By</span><span class="sxs-lookup"><span data-stu-id="57480-123">Group By Clause</span></span>](../../../../visual-basic/language-reference/queries/group-by-clause.md)
- [<span data-ttu-id="57480-124">Postupy: Skupiny souborů podle přípony (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57480-124">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="57480-125">Postupy: Rozdělení souboru na více souborů pomocí skupin (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57480-125">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
