---
title: Jak najít množinu rozdílů mezi dvěma seznamy (LINQ) (C#)
description: Naučte se používat LINQ v jazyce C# k porovnání dvou seznamů řetězců a výstupu těchto řádků, které jsou v jednom seznamu, ale nejsou v druhém.
ms.date: 07/20/2015
ms.assetid: 8e8945f0-4aba-439d-8d5d-c8d1eeef4e71
ms.openlocfilehash: 24509488d91f9861ee9bf84277238bea7031e5f6
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105086"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-c"></a><span data-ttu-id="4b78e-103">Jak najít množinu rozdílů mezi dvěma seznamy (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="4b78e-103">How to find the set difference between two lists (LINQ) (C#)</span></span>
<span data-ttu-id="4b78e-104">Tento příklad ukazuje, jak použít LINQ k porovnání dvou seznamů řetězců a výstupu těchto řádků, které jsou v names1.txt, ale ne v names2.txt.</span><span class="sxs-lookup"><span data-stu-id="4b78e-104">This example shows how to use LINQ to compare two lists of strings and output those lines that are in names1.txt but not in names2.txt.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="4b78e-105">Vytvoření datových souborů</span><span class="sxs-lookup"><span data-stu-id="4b78e-105">To create the data files</span></span>  
  
1. <span data-ttu-id="4b78e-106">Zkopírujte names1.txt a names2.txt do složky řešení, jak je znázorněno v tématu [jak kombinovat a porovnat kolekce řetězců (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md).</span><span class="sxs-lookup"><span data-stu-id="4b78e-106">Copy names1.txt and names2.txt to your solution folder as shown in [How to combine and compare string collections (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b78e-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b78e-107">Example</span></span>  
  
```csharp  
class CompareLists  
{
    static void Main()  
    {  
        // Create the IEnumerable data sources.  
        string[] names1 = System.IO.File.ReadAllLines(@"../../../names1.txt");  
        string[] names2 = System.IO.File.ReadAllLines(@"../../../names2.txt");  
  
        // Create the query. Note that method syntax must be used here.  
        IEnumerable<string> differenceQuery =  
          names1.Except(names2);  
  
        // Execute the query.  
        Console.WriteLine("The following lines are in names1.txt but not names2.txt");  
        foreach (string s in differenceQuery)  
            Console.WriteLine(s);  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
     The following lines are in names1.txt but not names2.txt  
    Potra, Cristina  
    Noriega, Fabricio  
    Aw, Kam Foo  
    Toyoshima, Tim  
    Guy, Wey Yuan  
    Garcia, Debra  
     */  
```  
  
 <span data-ttu-id="4b78e-108">Některé typy operací dotazů v jazyce C#, například, <xref:System.Linq.Enumerable.Except%2A> , <xref:System.Linq.Enumerable.Distinct%2A> <xref:System.Linq.Enumerable.Union%2A> a <xref:System.Linq.Enumerable.Concat%2A> , lze vyjádřit pouze v syntaxi založené na metodě.</span><span class="sxs-lookup"><span data-stu-id="4b78e-108">Some types of query operations in C#, such as <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Concat%2A>, can only be expressed in method-based syntax.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4b78e-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4b78e-109">Compiling the Code</span></span>  
 <span data-ttu-id="4b78e-110">Vytvořte projekt konzolové aplikace v jazyce C# se `using` direktivami pro obory názvů System. Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="4b78e-110">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b78e-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b78e-111">See also</span></span>

- [<span data-ttu-id="4b78e-112">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="4b78e-112">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
