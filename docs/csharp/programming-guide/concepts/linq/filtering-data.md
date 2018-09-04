---
title: Filtrování dat (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: df2f9f1bab7767365be65dbb60fb4af324ae3dab
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503294"
---
# <a name="filtering-data-c"></a><span data-ttu-id="7f638-102">Filtrování dat (C#)</span><span class="sxs-lookup"><span data-stu-id="7f638-102">Filtering Data (C#)</span></span>
<span data-ttu-id="7f638-103">Filtrování odkazuje na operaci omezení sady výsledků do obsahovat pouze prvky, které splňují zadanou podmínku.</span><span class="sxs-lookup"><span data-stu-id="7f638-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="7f638-104">Je také označován jako výběr.</span><span class="sxs-lookup"><span data-stu-id="7f638-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="7f638-105">Následující obrázek ukazuje výsledky filtrování posloupnost znaků.</span><span class="sxs-lookup"><span data-stu-id="7f638-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="7f638-106">Predikát pro filtrování operace určuje, že znak musí být "A".</span><span class="sxs-lookup"><span data-stu-id="7f638-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 <span data-ttu-id="7f638-107">![Filtrování operace LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span><span class="sxs-lookup"><span data-stu-id="7f638-107">![LINQ Filtering Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span></span>  
  
 <span data-ttu-id="7f638-108">V následující části jsou uvedeny standardní metody operátoru dotazu, které provádějí výběru.</span><span class="sxs-lookup"><span data-stu-id="7f638-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7f638-109">Metody</span><span class="sxs-lookup"><span data-stu-id="7f638-109">Methods</span></span>  
  
|<span data-ttu-id="7f638-110">Název metody</span><span class="sxs-lookup"><span data-stu-id="7f638-110">Method Name</span></span>|<span data-ttu-id="7f638-111">Popis</span><span class="sxs-lookup"><span data-stu-id="7f638-111">Description</span></span>|<span data-ttu-id="7f638-112">Syntaxe výrazu dotazu jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7f638-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="7f638-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="7f638-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="7f638-114">OfType</span><span class="sxs-lookup"><span data-stu-id="7f638-114">OfType</span></span>|<span data-ttu-id="7f638-115">Vybere hodnoty v závislosti na jejich schopnost převést na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="7f638-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="7f638-116">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="7f638-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7f638-117">Where</span><span class="sxs-lookup"><span data-stu-id="7f638-117">Where</span></span>|<span data-ttu-id="7f638-118">Vybere hodnoty, které jsou založeny na funkce predikátu.</span><span class="sxs-lookup"><span data-stu-id="7f638-118">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="7f638-119">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="7f638-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="7f638-120">V následujícím příkladu `where` klauzule můžete filtrovat z pole těchto řetězců, které mají určité délky.</span><span class="sxs-lookup"><span data-stu-id="7f638-120">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7f638-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f638-121">See Also</span></span>

- <xref:System.Linq>  
- [<span data-ttu-id="7f638-122">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="7f638-122">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
- [<span data-ttu-id="7f638-123">where – klauzule</span><span class="sxs-lookup"><span data-stu-id="7f638-123">where clause</span></span>](../../../../csharp/language-reference/keywords/where-clause.md)  
- [<span data-ttu-id="7f638-124">Postupy: dynamické určování filtrů predikátů při běhu</span><span class="sxs-lookup"><span data-stu-id="7f638-124">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)  
- [<span data-ttu-id="7f638-125">Postupy: dotazu na Metadata sestavení s reflexí (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7f638-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
- [<span data-ttu-id="7f638-126">Postupy: dotaz na soubory s konkrétním atributem či názvem (C#)</span><span class="sxs-lookup"><span data-stu-id="7f638-126">How to: Query for Files with a Specified Attribute or Name (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
- [<span data-ttu-id="7f638-127">Postupy: řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7f638-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
