---
title: Filtrování dat (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: 74399244990f8ff2deaa1d10576ea94a57c16bee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75346995"
---
# <a name="filtering-data-c"></a><span data-ttu-id="f629d-102">Filtrování dat (C#)</span><span class="sxs-lookup"><span data-stu-id="f629d-102">Filtering Data (C#)</span></span>
<span data-ttu-id="f629d-103">Filtrování odkazuje na operaci omezení sady výsledků obsahovat pouze ty prvky, které splňují zadanou podmínku.</span><span class="sxs-lookup"><span data-stu-id="f629d-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="f629d-104">To je také známé jako výběr.</span><span class="sxs-lookup"><span data-stu-id="f629d-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="f629d-105">Následující obrázek znázorňuje výsledky filtrování posloupnosti znaků.</span><span class="sxs-lookup"><span data-stu-id="f629d-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="f629d-106">Predikát pro operaci filtrování určuje, že znak musí být "A".</span><span class="sxs-lookup"><span data-stu-id="f629d-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![Diagram, který znázorňuje operaci filtrování LINQ](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="f629d-108">Standardní metody operátoru dotazu, které provádějí výběr, jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="f629d-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f629d-109">Metody</span><span class="sxs-lookup"><span data-stu-id="f629d-109">Methods</span></span>  
  
|<span data-ttu-id="f629d-110">Název metody</span><span class="sxs-lookup"><span data-stu-id="f629d-110">Method Name</span></span>|<span data-ttu-id="f629d-111">Popis</span><span class="sxs-lookup"><span data-stu-id="f629d-111">Description</span></span>|<span data-ttu-id="f629d-112">Syntaxe výrazu dotazu jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f629d-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="f629d-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="f629d-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="f629d-114">Oftype</span><span class="sxs-lookup"><span data-stu-id="f629d-114">OfType</span></span>|<span data-ttu-id="f629d-115">Vybere hodnoty v závislosti na jejich schopnosti přetypovat na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="f629d-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="f629d-116">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="f629d-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f629d-117">Kde</span><span class="sxs-lookup"><span data-stu-id="f629d-117">Where</span></span>|<span data-ttu-id="f629d-118">Vybere hodnoty, které jsou založeny na funkci predikátu.</span><span class="sxs-lookup"><span data-stu-id="f629d-118">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="f629d-119">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="f629d-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="f629d-120">Následující příklad používá `where` klauzuli k filtrování z pole ty řetězce, které mají určitou délku.</span><span class="sxs-lookup"><span data-stu-id="f629d-120">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f629d-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="f629d-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="f629d-122">Standardní operátory dotazů – přehled (C#)</span><span class="sxs-lookup"><span data-stu-id="f629d-122">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="f629d-123">where – klauzule</span><span class="sxs-lookup"><span data-stu-id="f629d-123">where clause</span></span>](../../../language-reference/keywords/where-clause.md)
- [<span data-ttu-id="f629d-124">Dynamické určování filtrů predikátů při běhu</span><span class="sxs-lookup"><span data-stu-id="f629d-124">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="f629d-125">Jak dotazovat metadata sestavení s reflexe (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="f629d-125">How to query an assembly's metadata with Reflection (LINQ) (C#)</span></span>](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="f629d-126">Jak dotazovat na soubory se zadaným atributem nebo názvem (C#)</span><span class="sxs-lookup"><span data-stu-id="f629d-126">How to query for files with a specified attribute or name (C#)</span></span>](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="f629d-127">Jak řadit nebo filtrovat textová data podle libovolného slova nebo pole (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="f629d-127">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
