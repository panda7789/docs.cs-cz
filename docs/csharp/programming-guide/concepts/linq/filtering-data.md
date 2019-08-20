---
title: Filtrování dat (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: 17d3a65b6042c9679a263eff0048f5360c4aa546
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594391"
---
# <a name="filtering-data-c"></a><span data-ttu-id="59f7a-102">Filtrování dat (C#)</span><span class="sxs-lookup"><span data-stu-id="59f7a-102">Filtering Data (C#)</span></span>
<span data-ttu-id="59f7a-103">Filtrování odkazuje na operaci omezení sady výsledků tak, aby obsahovala pouze prvky, které odpovídají zadané podmínce.</span><span class="sxs-lookup"><span data-stu-id="59f7a-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="59f7a-104">Označuje se také jako výběr.</span><span class="sxs-lookup"><span data-stu-id="59f7a-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="59f7a-105">Následující ilustrace znázorňuje výsledky filtrování posloupnosti znaků.</span><span class="sxs-lookup"><span data-stu-id="59f7a-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="59f7a-106">Predikát pro operaci filtrování určuje, že znak musí být "A".</span><span class="sxs-lookup"><span data-stu-id="59f7a-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![Diagram, který znázorňuje operaci filtrování LINQ](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="59f7a-108">Standardní metody operátoru dotazu, které provádějí výběr, jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="59f7a-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="59f7a-109">Metody</span><span class="sxs-lookup"><span data-stu-id="59f7a-109">Methods</span></span>  
  
|<span data-ttu-id="59f7a-110">Název metody</span><span class="sxs-lookup"><span data-stu-id="59f7a-110">Method Name</span></span>|<span data-ttu-id="59f7a-111">Popis</span><span class="sxs-lookup"><span data-stu-id="59f7a-111">Description</span></span>|<span data-ttu-id="59f7a-112">C#Syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="59f7a-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="59f7a-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="59f7a-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="59f7a-114">Only</span><span class="sxs-lookup"><span data-stu-id="59f7a-114">OfType</span></span>|<span data-ttu-id="59f7a-115">Vybere hodnoty v závislosti na jejich schopnosti je přetypovat na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="59f7a-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="59f7a-116">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="59f7a-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="59f7a-117">Where</span><span class="sxs-lookup"><span data-stu-id="59f7a-117">Where</span></span>|<span data-ttu-id="59f7a-118">Vybere hodnoty, které jsou založeny na funkci predikátu.</span><span class="sxs-lookup"><span data-stu-id="59f7a-118">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="59f7a-119">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="59f7a-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="59f7a-120">V následujícím příkladu je použita `where` klauzule pro filtrování z pole, které mají konkrétní délku.</span><span class="sxs-lookup"><span data-stu-id="59f7a-120">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="59f7a-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59f7a-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="59f7a-122">Přehled standardních operátorů dotazůC#()</span><span class="sxs-lookup"><span data-stu-id="59f7a-122">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="59f7a-123">where – klauzule</span><span class="sxs-lookup"><span data-stu-id="59f7a-123">where clause</span></span>](../../../language-reference/keywords/where-clause.md)
- [<span data-ttu-id="59f7a-124">Postupy: Dynamické určování filtrů predikátů za běhu</span><span class="sxs-lookup"><span data-stu-id="59f7a-124">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="59f7a-125">Postupy: Dotazování na metadata sestavení s reflexí (LINQC#) ()</span><span class="sxs-lookup"><span data-stu-id="59f7a-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (C#)</span></span>](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="59f7a-126">Postupy: Dotaz na soubory se zadaným atributem nebo názvem (C#)</span><span class="sxs-lookup"><span data-stu-id="59f7a-126">How to: Query for Files with a Specified Attribute or Name (C#)</span></span>](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="59f7a-127">Postupy: Řazení nebo filtrování textových dat podle libovolného slova nebo pole (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="59f7a-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
