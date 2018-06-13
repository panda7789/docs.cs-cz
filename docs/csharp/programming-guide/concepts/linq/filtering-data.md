---
title: Filtrování dat (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: ad8c167cf1b084c5e05bec84cd5c2f3f05716d03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321490"
---
# <a name="filtering-data-c"></a><span data-ttu-id="9a74a-102">Filtrování dat (C#)</span><span class="sxs-lookup"><span data-stu-id="9a74a-102">Filtering Data (C#)</span></span>
<span data-ttu-id="9a74a-103">Filtrování odkazuje na operaci omezit tak, aby obsahovala pouze elementy, které splňují zadanou podmínku sadu výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="9a74a-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="9a74a-104">Je také označované jako výběr.</span><span class="sxs-lookup"><span data-stu-id="9a74a-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="9a74a-105">Následující obrázek znázorňuje výsledky filtrování posloupnost znaků.</span><span class="sxs-lookup"><span data-stu-id="9a74a-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="9a74a-106">Predikát pro filtrování operaci Určuje, že znak musí být "A".</span><span class="sxs-lookup"><span data-stu-id="9a74a-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 <span data-ttu-id="9a74a-107">![LINQ filtrování operaci](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span><span class="sxs-lookup"><span data-stu-id="9a74a-107">![LINQ Filtering Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span></span>  
  
 <span data-ttu-id="9a74a-108">Operátor metody standardní dotazu, které provedení výběru jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="9a74a-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9a74a-109">Metody</span><span class="sxs-lookup"><span data-stu-id="9a74a-109">Methods</span></span>  
  
|<span data-ttu-id="9a74a-110">Název metody</span><span class="sxs-lookup"><span data-stu-id="9a74a-110">Method Name</span></span>|<span data-ttu-id="9a74a-111">Popis</span><span class="sxs-lookup"><span data-stu-id="9a74a-111">Description</span></span>|<span data-ttu-id="9a74a-112">Syntaxe výrazu dotazu jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9a74a-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="9a74a-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="9a74a-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="9a74a-114">OfType</span><span class="sxs-lookup"><span data-stu-id="9a74a-114">OfType</span></span>|<span data-ttu-id="9a74a-115">Vybere hodnoty, v závislosti na jejich schopnost převést na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="9a74a-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="9a74a-116">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="9a74a-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9a74a-117">Where</span><span class="sxs-lookup"><span data-stu-id="9a74a-117">Where</span></span>|<span data-ttu-id="9a74a-118">Vybere hodnoty, které jsou založeny na funkce predikátu.</span><span class="sxs-lookup"><span data-stu-id="9a74a-118">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="9a74a-119">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="9a74a-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="9a74a-120">Následující příklad používá `where` klauzule vyfiltrujete z pole tyto řetězce, které mají určité délky.</span><span class="sxs-lookup"><span data-stu-id="9a74a-120">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9a74a-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="9a74a-121">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="9a74a-122">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="9a74a-122">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="9a74a-123">where – klauzule</span><span class="sxs-lookup"><span data-stu-id="9a74a-123">where clause</span></span>](../../../../csharp/language-reference/keywords/where-clause.md)  
 [<span data-ttu-id="9a74a-124">Postupy: dynamické určování filtrů predikátů při běhu</span><span class="sxs-lookup"><span data-stu-id="9a74a-124">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)  
 [<span data-ttu-id="9a74a-125">Postupy: vytvoření dotazu na Metadata sestavení s reflexí (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="9a74a-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 [<span data-ttu-id="9a74a-126">Postupy: dotaz pro soubory s konkrétním atributem či názvem (C#)</span><span class="sxs-lookup"><span data-stu-id="9a74a-126">How to: Query for Files with a Specified Attribute or Name (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 [<span data-ttu-id="9a74a-127">Postupy: řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="9a74a-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
