---
title: Filtrování dat (C#)
description: Filtrování, označované také jako výběr, omezuje výsledky na základě podmínky. Přečtěte si o standardních metodách operátoru dotazu v LINQ v jazyce C#, které provádějí filtrování.
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: f9f6d691da73b566e5135f6692c87ba3a8978005
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103928"
---
# <a name="filtering-data-c"></a><span data-ttu-id="77e58-104">Filtrování dat (C#)</span><span class="sxs-lookup"><span data-stu-id="77e58-104">Filtering Data (C#)</span></span>
<span data-ttu-id="77e58-105">Filtrování odkazuje na operaci omezení sady výsledků tak, aby obsahovala pouze prvky, které odpovídají zadané podmínce.</span><span class="sxs-lookup"><span data-stu-id="77e58-105">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="77e58-106">Označuje se také jako výběr.</span><span class="sxs-lookup"><span data-stu-id="77e58-106">It is also known as selection.</span></span>  
  
 <span data-ttu-id="77e58-107">Následující ilustrace znázorňuje výsledky filtrování posloupnosti znaků.</span><span class="sxs-lookup"><span data-stu-id="77e58-107">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="77e58-108">Predikát pro operaci filtrování určuje, že znak musí být "A".</span><span class="sxs-lookup"><span data-stu-id="77e58-108">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![Diagram, který znázorňuje operaci filtrování LINQ](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="77e58-110">Standardní metody operátoru dotazu, které provádějí výběr, jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="77e58-110">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="77e58-111">Metody</span><span class="sxs-lookup"><span data-stu-id="77e58-111">Methods</span></span>  
  
|<span data-ttu-id="77e58-112">Název metody</span><span class="sxs-lookup"><span data-stu-id="77e58-112">Method Name</span></span>|<span data-ttu-id="77e58-113">Popis</span><span class="sxs-lookup"><span data-stu-id="77e58-113">Description</span></span>|<span data-ttu-id="77e58-114">Syntaxe výrazu dotazu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="77e58-114">C# Query Expression Syntax</span></span>|<span data-ttu-id="77e58-115">Další informace</span><span class="sxs-lookup"><span data-stu-id="77e58-115">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="77e58-116">Only</span><span class="sxs-lookup"><span data-stu-id="77e58-116">OfType</span></span>|<span data-ttu-id="77e58-117">Vybere hodnoty v závislosti na jejich schopnosti je přetypovat na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="77e58-117">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="77e58-118">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="77e58-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="77e58-119">Kde</span><span class="sxs-lookup"><span data-stu-id="77e58-119">Where</span></span>|<span data-ttu-id="77e58-120">Vybere hodnoty, které jsou založeny na funkci predikátu.</span><span class="sxs-lookup"><span data-stu-id="77e58-120">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="77e58-121">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="77e58-121">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="77e58-122">V následujícím příkladu je použita `where` klauzule pro filtrování z pole, které mají konkrétní délku.</span><span class="sxs-lookup"><span data-stu-id="77e58-122">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            where word.Length == 3  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="77e58-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="77e58-123">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="77e58-124">Přehled standardních operátorů dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="77e58-124">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="77e58-125">where – klauzule</span><span class="sxs-lookup"><span data-stu-id="77e58-125">where clause</span></span>](../../../language-reference/keywords/where-clause.md)
- [<span data-ttu-id="77e58-126">Dynamické určování filtrů predikátů při běhu</span><span class="sxs-lookup"><span data-stu-id="77e58-126">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="77e58-127">Postup dotazování na metadata sestavení s reflexí (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="77e58-127">How to query an assembly's metadata with Reflection (LINQ) (C#)</span></span>](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="77e58-128">Dotazování na soubory se zadaným atributem nebo názvem (C#)</span><span class="sxs-lookup"><span data-stu-id="77e58-128">How to query for files with a specified attribute or name (C#)</span></span>](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="77e58-129">Postup řazení nebo filtrování textových dat podle libovolného slova nebo pole (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="77e58-129">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
