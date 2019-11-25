---
title: 'Postupy: Vyhledání rozdílového nastavení mezi dvěma seznamy (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 8e8945f0-4aba-439d-8d5d-c8d1eeef4e71
ms.openlocfilehash: 9e2a42a466a71d4e351df89398be197197a54042
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140986"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-c"></a><span data-ttu-id="40c1f-102">Postupy: Vyhledání rozdílového nastavení mezi dvěma seznamy (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="40c1f-102">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>
<span data-ttu-id="40c1f-103">Tento příklad ukazuje, jak použít LINQ k porovnání dvou seznamů řetězců a výstupu těchto řádků, které jsou v names1. txt, ale ne v names2. txt.</span><span class="sxs-lookup"><span data-stu-id="40c1f-103">This example shows how to use LINQ to compare two lists of strings and output those lines that are in names1.txt but not in names2.txt.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="40c1f-104">Vytvoření datových souborů</span><span class="sxs-lookup"><span data-stu-id="40c1f-104">To create the data files</span></span>  
  
1. <span data-ttu-id="40c1f-105">Zkopírujte names1. txt a names2. txt do složky řešení, jak je znázorněno v tématu [jak kombinovat a porovnat kolekce řetězců (LINQC#) ()](./how-to-combine-and-compare-string-collections-linq.md).</span><span class="sxs-lookup"><span data-stu-id="40c1f-105">Copy names1.txt and names2.txt to your solution folder as shown in [How to combine and compare string collections (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="40c1f-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="40c1f-106">Example</span></span>  
  
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
  
 <span data-ttu-id="40c1f-107">Některé typy operací dotazů v C#, například <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>a <xref:System.Linq.Enumerable.Concat%2A>, lze vyjádřit pouze v syntaxi založené na metodě.</span><span class="sxs-lookup"><span data-stu-id="40c1f-107">Some types of query operations in C#, such as <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Concat%2A>, can only be expressed in method-based syntax.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="40c1f-108">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="40c1f-108">Compiling the Code</span></span>  
 <span data-ttu-id="40c1f-109">Vytvořte projekt C# konzolové aplikace s direktivami `using` pro obory názvů System. Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="40c1f-109">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40c1f-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40c1f-110">See also</span></span>

- [<span data-ttu-id="40c1f-111">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="40c1f-111">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
