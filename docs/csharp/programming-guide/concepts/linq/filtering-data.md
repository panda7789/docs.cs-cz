---
title: Filtrování dat (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: 61d80674fd858063e77749342a33d714e3a57c6e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826064"
---
# <a name="filtering-data-c"></a><span data-ttu-id="f99d9-102">Filtrování dat (C#)</span><span class="sxs-lookup"><span data-stu-id="f99d9-102">Filtering Data (C#)</span></span>
<span data-ttu-id="f99d9-103">Filtrování odkazuje na operaci omezení sady výsledků do obsahovat pouze prvky, které splňují zadanou podmínku.</span><span class="sxs-lookup"><span data-stu-id="f99d9-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="f99d9-104">Je také označován jako výběr.</span><span class="sxs-lookup"><span data-stu-id="f99d9-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="f99d9-105">Následující obrázek ukazuje výsledky filtrování posloupnost znaků.</span><span class="sxs-lookup"><span data-stu-id="f99d9-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="f99d9-106">Predikát pro filtrování operace určuje, že znak musí být "A".</span><span class="sxs-lookup"><span data-stu-id="f99d9-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![Diagram, který ukazuje filtrování operace LINQ](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="f99d9-108">V následující části jsou uvedeny standardní metody operátoru dotazu, které provádějí výběru.</span><span class="sxs-lookup"><span data-stu-id="f99d9-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f99d9-109">Metody</span><span class="sxs-lookup"><span data-stu-id="f99d9-109">Methods</span></span>  
  
|<span data-ttu-id="f99d9-110">Název metody</span><span class="sxs-lookup"><span data-stu-id="f99d9-110">Method Name</span></span>|<span data-ttu-id="f99d9-111">Popis</span><span class="sxs-lookup"><span data-stu-id="f99d9-111">Description</span></span>|<span data-ttu-id="f99d9-112">Syntaxe výrazu dotazu jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f99d9-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="f99d9-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="f99d9-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="f99d9-114">OfType</span><span class="sxs-lookup"><span data-stu-id="f99d9-114">OfType</span></span>|<span data-ttu-id="f99d9-115">Vybere hodnoty v závislosti na jejich schopnost převést na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="f99d9-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="f99d9-116">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="f99d9-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f99d9-117">Where</span><span class="sxs-lookup"><span data-stu-id="f99d9-117">Where</span></span>|<span data-ttu-id="f99d9-118">Vybere hodnoty, které jsou založeny na funkce predikátu.</span><span class="sxs-lookup"><span data-stu-id="f99d9-118">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="f99d9-119">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="f99d9-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="f99d9-120">V následujícím příkladu `where` klauzule můžete filtrovat z pole těchto řetězců, které mají určité délky.</span><span class="sxs-lookup"><span data-stu-id="f99d9-120">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f99d9-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f99d9-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="f99d9-122">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="f99d9-122">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="f99d9-123">where – klauzule</span><span class="sxs-lookup"><span data-stu-id="f99d9-123">where clause</span></span>](../../../../csharp/language-reference/keywords/where-clause.md)
- [<span data-ttu-id="f99d9-124">Postupy: Dynamické určování filtrů predikátů při běhu</span><span class="sxs-lookup"><span data-stu-id="f99d9-124">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="f99d9-125">Postupy: Dotazu na Metadata sestavení s reflexí (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="f99d9-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="f99d9-126">Postupy: Dotaz pro soubory s konkrétním atributem či názvem (C#)</span><span class="sxs-lookup"><span data-stu-id="f99d9-126">How to: Query for Files with a Specified Attribute or Name (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="f99d9-127">Postupy: Řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="f99d9-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
