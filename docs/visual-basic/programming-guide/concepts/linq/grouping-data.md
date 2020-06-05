---
title: Seskupování dat
ms.date: 07/20/2015
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
ms.openlocfilehash: 8996eee748489c596bc5adc32f53b6b39dbfc6ac
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398380"
---
# <a name="grouping-data-visual-basic"></a><span data-ttu-id="c063a-102">Seskupování dat (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c063a-102">Grouping Data (Visual Basic)</span></span>
<span data-ttu-id="c063a-103">Seskupení odkazuje na operaci vložení dat do skupin, aby elementy v každé skupině sdílely společný atribut.</span><span class="sxs-lookup"><span data-stu-id="c063a-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="c063a-104">Následující ilustrace znázorňuje výsledky seskupení sekvencí znaků.</span><span class="sxs-lookup"><span data-stu-id="c063a-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="c063a-105">Klíč pro každou skupinu je znak.</span><span class="sxs-lookup"><span data-stu-id="c063a-105">The key for each group is the character.</span></span>  
  
 ![Diagram, který znázorňuje operaci seskupení LINQ.](./media/grouping-data/linq-group-operation.png)  
  
 <span data-ttu-id="c063a-107">Standardní metody operátoru dotazu, které seskupují datové prvky, jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="c063a-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c063a-108">Metody</span><span class="sxs-lookup"><span data-stu-id="c063a-108">Methods</span></span>  
  
|<span data-ttu-id="c063a-109">Název metody</span><span class="sxs-lookup"><span data-stu-id="c063a-109">Method Name</span></span>|<span data-ttu-id="c063a-110">Description</span><span class="sxs-lookup"><span data-stu-id="c063a-110">Description</span></span>|<span data-ttu-id="c063a-111">Visual Basic syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="c063a-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="c063a-112">Další informace</span><span class="sxs-lookup"><span data-stu-id="c063a-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="c063a-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="c063a-113">GroupBy</span></span>|<span data-ttu-id="c063a-114">Seskupí prvky, které sdílejí společný atribut.</span><span class="sxs-lookup"><span data-stu-id="c063a-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="c063a-115">Jednotlivé skupiny jsou reprezentovány <xref:System.Linq.IGrouping%602> objektem.</span><span class="sxs-lookup"><span data-stu-id="c063a-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c063a-116">ToLookup</span><span class="sxs-lookup"><span data-stu-id="c063a-116">ToLookup</span></span>|<span data-ttu-id="c063a-117">Vloží prvky do <xref:System.Linq.Lookup%602> slovníku (do slovníku 1: n) na základě funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="c063a-117">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="c063a-118">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="c063a-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="c063a-119">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="c063a-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="c063a-120">Následující příklad kódu používá `Group By` klauzuli pro seskupení celých čísel v seznamu podle toho, zda jsou sudé nebo liché.</span><span class="sxs-lookup"><span data-stu-id="c063a-120">The following code example uses the `Group By` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c063a-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="c063a-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="c063a-122">Přehled standardních operátorů dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c063a-122">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="c063a-123">Group By – klauzule</span><span class="sxs-lookup"><span data-stu-id="c063a-123">Group By Clause</span></span>](../../../language-reference/queries/group-by-clause.md)
- [<span data-ttu-id="c063a-124">Postupy: seskupování souborů podle přípony (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c063a-124">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>](how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="c063a-125">Postupy: rozdělení souboru na více souborů pomocí skupin (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c063a-125">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
