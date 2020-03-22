---
title: Seskupování dat
ms.date: 07/20/2015
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
ms.openlocfilehash: 9a4011b77f91ff241d23f7aeca95925a1e170483
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266817"
---
# <a name="grouping-data-visual-basic"></a><span data-ttu-id="b822e-102">Seskupení dat (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b822e-102">Grouping Data (Visual Basic)</span></span>
<span data-ttu-id="b822e-103">Seskupení odkazuje na operaci vkládání dat do skupin tak, aby prvky v každé skupině sdílejí společný atribut.</span><span class="sxs-lookup"><span data-stu-id="b822e-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="b822e-104">Následující obrázek znázorňuje výsledky seskupování posloupnosti znaků.</span><span class="sxs-lookup"><span data-stu-id="b822e-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="b822e-105">Klíčem pro každou skupinu je znak.</span><span class="sxs-lookup"><span data-stu-id="b822e-105">The key for each group is the character.</span></span>  
  
 ![Diagram, který znázorňuje operaci seskupení LINQ.](./media/grouping-data/linq-group-operation.png)  
  
 <span data-ttu-id="b822e-107">Standardní metody operátoru dotazu, které seskupují datové prvky, jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="b822e-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b822e-108">Metody</span><span class="sxs-lookup"><span data-stu-id="b822e-108">Methods</span></span>  
  
|<span data-ttu-id="b822e-109">Název metody</span><span class="sxs-lookup"><span data-stu-id="b822e-109">Method Name</span></span>|<span data-ttu-id="b822e-110">Popis</span><span class="sxs-lookup"><span data-stu-id="b822e-110">Description</span></span>|<span data-ttu-id="b822e-111">Syntaxe výrazu dotazu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b822e-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="b822e-112">Další informace</span><span class="sxs-lookup"><span data-stu-id="b822e-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="b822e-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="b822e-113">GroupBy</span></span>|<span data-ttu-id="b822e-114">Seskupí prvky, které sdílejí společný atribut.</span><span class="sxs-lookup"><span data-stu-id="b822e-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="b822e-115">Každá skupina je <xref:System.Linq.IGrouping%602> reprezentována objektem.</span><span class="sxs-lookup"><span data-stu-id="b822e-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b822e-116">Vyhledávání</span><span class="sxs-lookup"><span data-stu-id="b822e-116">ToLookup</span></span>|<span data-ttu-id="b822e-117">Vloží prvky <xref:System.Linq.Lookup%602> do (slovníku 1:N) na základě funkce voliče klíčů.</span><span class="sxs-lookup"><span data-stu-id="b822e-117">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="b822e-118">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="b822e-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="b822e-119">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="b822e-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="b822e-120">Následující příklad kódu `Group By` používá klauzuli k seskupení celá čísla v seznamu podle toho, zda jsou sudé nebo liché.</span><span class="sxs-lookup"><span data-stu-id="b822e-120">The following code example uses the `Group By` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b822e-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="b822e-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="b822e-122">Standardní operátory dotazů – přehled (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b822e-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="b822e-123">Klauzule Group By</span><span class="sxs-lookup"><span data-stu-id="b822e-123">Group By Clause</span></span>](../../../../visual-basic/language-reference/queries/group-by-clause.md)
- [<span data-ttu-id="b822e-124">Postup: Seskupení souborů podle rozšíření (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b822e-124">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="b822e-125">Postup: Rozdělení souboru do mnoha souborů pomocí skupin (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b822e-125">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
