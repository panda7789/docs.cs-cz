---
title: Seskupování dat (C#)
ms.date: 07/20/2015
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
ms.openlocfilehash: 7ef3d3c9097d7a9478605565518ac8975feb9fe2
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635740"
---
# <a name="grouping-data-c"></a><span data-ttu-id="9ca25-102">Seskupování dat (C#)</span><span class="sxs-lookup"><span data-stu-id="9ca25-102">Grouping Data (C#)</span></span>
<span data-ttu-id="9ca25-103">Seskupení odkazuje na operaci vložení dat do skupin, aby elementy v každé skupině sdílely společný atribut.</span><span class="sxs-lookup"><span data-stu-id="9ca25-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="9ca25-104">Následující ilustrace znázorňuje výsledky seskupení sekvencí znaků.</span><span class="sxs-lookup"><span data-stu-id="9ca25-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="9ca25-105">Klíč pro každou skupinu je znak.</span><span class="sxs-lookup"><span data-stu-id="9ca25-105">The key for each group is the character.</span></span>  
  
 ![Diagram, který znázorňuje operaci seskupení LINQ.](./media/grouping-data/linq-group-operation.png)  
  
 <span data-ttu-id="9ca25-107">Standardní metody operátoru dotazu, které seskupují datové prvky, jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="9ca25-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9ca25-108">Metody</span><span class="sxs-lookup"><span data-stu-id="9ca25-108">Methods</span></span>  
  
|<span data-ttu-id="9ca25-109">Název metody</span><span class="sxs-lookup"><span data-stu-id="9ca25-109">Method Name</span></span>|<span data-ttu-id="9ca25-110">Popis</span><span class="sxs-lookup"><span data-stu-id="9ca25-110">Description</span></span>|<span data-ttu-id="9ca25-111">C#Syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="9ca25-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="9ca25-112">Další informace</span><span class="sxs-lookup"><span data-stu-id="9ca25-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="9ca25-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="9ca25-113">GroupBy</span></span>|<span data-ttu-id="9ca25-114">Seskupí prvky, které sdílejí společný atribut.</span><span class="sxs-lookup"><span data-stu-id="9ca25-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="9ca25-115">Jednotlivé skupiny jsou reprezentovány objektem <xref:System.Linq.IGrouping%602>.</span><span class="sxs-lookup"><span data-stu-id="9ca25-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`group … by`<br /><br /> <span data-ttu-id="9ca25-116">-nebo-</span><span class="sxs-lookup"><span data-stu-id="9ca25-116">-or-</span></span><br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9ca25-117">ToLookup</span><span class="sxs-lookup"><span data-stu-id="9ca25-117">ToLookup</span></span>|<span data-ttu-id="9ca25-118">Vloží prvky do <xref:System.Linq.Lookup%602> (slovník 1: n) na základě funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="9ca25-118">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="9ca25-119">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="9ca25-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="9ca25-120">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="9ca25-120">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="9ca25-121">Následující příklad kódu používá klauzuli `group by` k seskupení celých čísel v seznamu podle toho, zda jsou sudé nebo liché.</span><span class="sxs-lookup"><span data-stu-id="9ca25-121">The following code example uses the `group by` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9ca25-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ca25-122">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="9ca25-123">Přehled standardních operátorů dotazůC#()</span><span class="sxs-lookup"><span data-stu-id="9ca25-123">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="9ca25-124">group – klauzule</span><span class="sxs-lookup"><span data-stu-id="9ca25-124">group clause</span></span>](../../../language-reference/keywords/group-clause.md)
- [<span data-ttu-id="9ca25-125">Vytvoření vnořené skupiny</span><span class="sxs-lookup"><span data-stu-id="9ca25-125">Create a nested group</span></span>](../../../linq/create-a-nested-group.md)
- [<span data-ttu-id="9ca25-126">Postup seskupení souborů podle přípony (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="9ca25-126">How to group files by extension (LINQ) (C#)</span></span>](./how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="9ca25-127">Seskupení výsledků dotazu</span><span class="sxs-lookup"><span data-stu-id="9ca25-127">Group query results</span></span>](../../../linq/group-query-results.md)
- [<span data-ttu-id="9ca25-128">Provádění poddotazů na skupinách</span><span class="sxs-lookup"><span data-stu-id="9ca25-128">Perform a subquery on a grouping operation</span></span>](../../../linq/perform-a-subquery-on-a-grouping-operation.md)
- [<span data-ttu-id="9ca25-129">Rozdělení souboru na více souborů pomocí skupin (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="9ca25-129">How to split a file into many files by using groups (LINQ) (C#)</span></span>](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
