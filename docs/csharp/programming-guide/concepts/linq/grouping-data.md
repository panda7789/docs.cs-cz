---
title: Seskupení dat (C#)
description: Seskupení vloží data do skupin prvků, které sdílejí atribut. Přečtěte si o standardních metodách operátoru dotazu v LINQ v jazyce C#, které seskupují datové prvky.
ms.date: 07/20/2015
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
ms.openlocfilehash: 5e1bca1d360b0f44a081cf2770118a0551629b5b
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103684"
---
# <a name="grouping-data-c"></a><span data-ttu-id="6c1ed-104">Seskupení dat (C#)</span><span class="sxs-lookup"><span data-stu-id="6c1ed-104">Grouping Data (C#)</span></span>
<span data-ttu-id="6c1ed-105">Seskupení odkazuje na operaci vložení dat do skupin, aby elementy v každé skupině sdílely společný atribut.</span><span class="sxs-lookup"><span data-stu-id="6c1ed-105">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="6c1ed-106">Následující ilustrace znázorňuje výsledky seskupení sekvencí znaků.</span><span class="sxs-lookup"><span data-stu-id="6c1ed-106">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="6c1ed-107">Klíč pro každou skupinu je znak.</span><span class="sxs-lookup"><span data-stu-id="6c1ed-107">The key for each group is the character.</span></span>  
  
 ![Diagram, který znázorňuje operaci seskupení LINQ.](./media/grouping-data/linq-group-operation.png)  
  
 <span data-ttu-id="6c1ed-109">Standardní metody operátoru dotazu, které seskupují datové prvky, jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="6c1ed-109">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6c1ed-110">Metody</span><span class="sxs-lookup"><span data-stu-id="6c1ed-110">Methods</span></span>  
  
|<span data-ttu-id="6c1ed-111">Název metody</span><span class="sxs-lookup"><span data-stu-id="6c1ed-111">Method Name</span></span>|<span data-ttu-id="6c1ed-112">Popis</span><span class="sxs-lookup"><span data-stu-id="6c1ed-112">Description</span></span>|<span data-ttu-id="6c1ed-113">Syntaxe výrazu dotazu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6c1ed-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="6c1ed-114">Další informace</span><span class="sxs-lookup"><span data-stu-id="6c1ed-114">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="6c1ed-115">GroupBy</span><span class="sxs-lookup"><span data-stu-id="6c1ed-115">GroupBy</span></span>|<span data-ttu-id="6c1ed-116">Seskupí prvky, které sdílejí společný atribut.</span><span class="sxs-lookup"><span data-stu-id="6c1ed-116">Groups elements that share a common attribute.</span></span> <span data-ttu-id="6c1ed-117">Jednotlivé skupiny jsou reprezentovány <xref:System.Linq.IGrouping%602> objektem.</span><span class="sxs-lookup"><span data-stu-id="6c1ed-117">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`group … by`<br /><br /> <span data-ttu-id="6c1ed-118">-nebo-</span><span class="sxs-lookup"><span data-stu-id="6c1ed-118">-or-</span></span><br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6c1ed-119">ToLookup</span><span class="sxs-lookup"><span data-stu-id="6c1ed-119">ToLookup</span></span>|<span data-ttu-id="6c1ed-120">Vloží prvky do <xref:System.Linq.Lookup%602> slovníku (do slovníku 1: n) na základě funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="6c1ed-120">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="6c1ed-121">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="6c1ed-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="6c1ed-122">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="6c1ed-122">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="6c1ed-123">Následující příklad kódu používá `group by` klauzuli pro seskupení celých čísel v seznamu podle toho, zda jsou sudé nebo liché.</span><span class="sxs-lookup"><span data-stu-id="6c1ed-123">The following code example uses the `group by` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
```csharp  
List<int> numbers = new List<int>() { 35, 44, 200, 84, 3987, 4, 199, 329, 446, 208 };  
  
IEnumerable<IGrouping<int, int>> query = from number in numbers  
                                         group number by number % 2;  
  
foreach (var group in query)  
{  
    Console.WriteLine(group.Key == 0 ? "\nEven numbers:" : "\nOdd numbers:");  
    foreach (int i in group)  
        Console.WriteLine(i);  
}  
  
/* This code produces the following output:  
  
    Odd numbers:  
    35  
    3987  
    199  
    329  
  
    Even numbers:  
    44  
    200  
    84  
    4  
    446  
    208  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c1ed-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c1ed-124">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="6c1ed-125">Přehled standardních operátorů dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="6c1ed-125">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="6c1ed-126">group – klauzule</span><span class="sxs-lookup"><span data-stu-id="6c1ed-126">group clause</span></span>](../../../language-reference/keywords/group-clause.md)
- [<span data-ttu-id="6c1ed-127">Vytvoření vnořené skupiny</span><span class="sxs-lookup"><span data-stu-id="6c1ed-127">Create a nested group</span></span>](../../../linq/create-a-nested-group.md)
- [<span data-ttu-id="6c1ed-128">Postup seskupení souborů podle přípony (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="6c1ed-128">How to group files by extension (LINQ) (C#)</span></span>](./how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="6c1ed-129">Seskupení výsledků dotazu</span><span class="sxs-lookup"><span data-stu-id="6c1ed-129">Group query results</span></span>](../../../linq/group-query-results.md)
- [<span data-ttu-id="6c1ed-130">Provádění poddotazů na skupinách</span><span class="sxs-lookup"><span data-stu-id="6c1ed-130">Perform a subquery on a grouping operation</span></span>](../../../linq/perform-a-subquery-on-a-grouping-operation.md)
- [<span data-ttu-id="6c1ed-131">Rozdělení souboru na více souborů pomocí skupin (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="6c1ed-131">How to split a file into many files by using groups (LINQ) (C#)</span></span>](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
