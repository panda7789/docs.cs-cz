---
title: 'Postupy: Kombinování a porovnávání kolekcí řetězců (LINQ)C#()'
ms.date: 07/20/2015
ms.assetid: 25926e5b-fde2-4dc1-86a0-16ead7aa13d2
ms.openlocfilehash: 414d9764d8de0a1d7cd395a3192a097d48983856
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205362"
---
# <a name="how-to-combine-and-compare-string-collections-linq-c"></a><span data-ttu-id="d7c1b-102">Postupy: Kombinování a porovnávání kolekcí řetězců (LINQ)C#()</span><span class="sxs-lookup"><span data-stu-id="d7c1b-102">How to: Combine and Compare String Collections (LINQ) (C#)</span></span>
<span data-ttu-id="d7c1b-103">Tento příklad ukazuje, jak sloučit soubory, které obsahují řádky textu a následně seřadit výsledky.</span><span class="sxs-lookup"><span data-stu-id="d7c1b-103">This example shows how to merge files that contain lines of text and then sort the results.</span></span> <span data-ttu-id="d7c1b-104">Konkrétně ukazuje, jak provést jednoduché zřetězení, sjednocení a průnik dvou sad textových řádků.</span><span class="sxs-lookup"><span data-stu-id="d7c1b-104">Specifically, it shows how to perform a simple concatenation, a union, and an intersection on the two sets of text lines.</span></span>  
  
### <a name="to-set-up-the-project-and-the-text-files"></a><span data-ttu-id="d7c1b-105">Nastavení projektu a textových souborů</span><span class="sxs-lookup"><span data-stu-id="d7c1b-105">To set up the project and the text files</span></span>  
  
1. <span data-ttu-id="d7c1b-106">Zkopírujte tyto názvy do textového souboru s názvem names1. txt a uložte je do složky projektu:</span><span class="sxs-lookup"><span data-stu-id="d7c1b-106">Copy these names into a text file that is named names1.txt and save it in your project folder:</span></span>  
  
    ```text  
    Bankov, Peter  
    Holm, Michael  
    Garcia, Hugo  
    Potra, Cristina  
    Noriega, Fabricio  
    Aw, Kam Foo  
    Beebe, Ann  
    Toyoshima, Tim  
    Guy, Wey Yuan  
    Garcia, Debra  
    ```  
  
2. <span data-ttu-id="d7c1b-107">Zkopírujte tyto názvy do textového souboru s názvem names2. txt a uložte je do složky projektu.</span><span class="sxs-lookup"><span data-stu-id="d7c1b-107">Copy these names into a text file that is named names2.txt and save it in your project folder.</span></span> <span data-ttu-id="d7c1b-108">Všimněte si, že dva soubory mají některé běžné názvy.</span><span class="sxs-lookup"><span data-stu-id="d7c1b-108">Note that the two files have some names in common.</span></span>  
  
    ```text  
    Liu, Jinghao  
    Bankov, Peter  
    Holm, Michael  
    Garcia, Hugo  
    Beebe, Ann  
    Gilchrist, Beth  
    Myrcha, Jacek  
    Giakoumakis, Leo  
    McLin, Nkenge  
    El Yassir, Mehdi  
    ```  
  
## <a name="example"></a><span data-ttu-id="d7c1b-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="d7c1b-109">Example</span></span>  
  
```csharp  
class MergeStrings  
    {  
        static void Main(string[] args)  
        {  
            //Put text files in your solution folder  
            string[] fileA = System.IO.File.ReadAllLines(@"../../../names1.txt");  
            string[] fileB = System.IO.File.ReadAllLines(@"../../../names2.txt");  
  
            //Simple concatenation and sort. Duplicates are preserved.  
            IEnumerable<string> concatQuery =  
                fileA.Concat(fileB).OrderBy(s => s);  
  
            // Pass the query variable to another function for execution.  
            OutputQueryResults(concatQuery, "Simple concatenate and sort. Duplicates are preserved:");  
  
            // Concatenate and remove duplicate names based on  
            // default string comparer.  
            IEnumerable<string> uniqueNamesQuery =  
                fileA.Union(fileB).OrderBy(s => s);  
            OutputQueryResults(uniqueNamesQuery, "Union removes duplicate names:");  
  
            // Find the names that occur in both files (based on  
            // default string comparer).  
            IEnumerable<string> commonNamesQuery =  
                fileA.Intersect(fileB);  
            OutputQueryResults(commonNamesQuery, "Merge based on intersect:");  
  
            // Find the matching fields in each list. Merge the two   
            // results by using Concat, and then  
            // sort using the default string comparer.  
            string nameMatch = "Garcia";  
  
            IEnumerable<String> tempQuery1 =  
                from name in fileA  
                let n = name.Split(',')  
                where n[0] == nameMatch  
                select name;  
  
            IEnumerable<string> tempQuery2 =  
                from name2 in fileB  
                let n2 = name2.Split(',')  
                where n2[0] == nameMatch  
                select name2;  
  
            IEnumerable<string> nameMatchQuery =  
                tempQuery1.Concat(tempQuery2).OrderBy(s => s);  
            OutputQueryResults(nameMatchQuery, $"Concat based on partial name match \"{nameMatch}\":");
  
            // Keep the console window open in debug mode.  
            Console.WriteLine("Press any key to exit");  
            Console.ReadKey();  
        }  
  
        static void OutputQueryResults(IEnumerable<string> query, string message)  
        {  
            Console.WriteLine(System.Environment.NewLine + message);  
            foreach (string item in query)  
            {  
                Console.WriteLine(item);  
            }  
            Console.WriteLine("{0} total names in list", query.Count());  
        }  
    }  
    /* Output:  
        Simple concatenate and sort. Duplicates are preserved:  
        Aw, Kam Foo  
        Bankov, Peter  
        Bankov, Peter  
        Beebe, Ann  
        Beebe, Ann  
        El Yassir, Mehdi  
        Garcia, Debra  
        Garcia, Hugo  
        Garcia, Hugo  
        Giakoumakis, Leo  
        Gilchrist, Beth  
        Guy, Wey Yuan  
        Holm, Michael  
        Holm, Michael  
        Liu, Jinghao  
        McLin, Nkenge  
        Myrcha, Jacek  
        Noriega, Fabricio  
        Potra, Cristina  
        Toyoshima, Tim  
        20 total names in list  
  
        Union removes duplicate names:  
        Aw, Kam Foo  
        Bankov, Peter  
        Beebe, Ann  
        El Yassir, Mehdi  
        Garcia, Debra  
        Garcia, Hugo  
        Giakoumakis, Leo  
        Gilchrist, Beth  
        Guy, Wey Yuan  
        Holm, Michael  
        Liu, Jinghao  
        McLin, Nkenge  
        Myrcha, Jacek  
        Noriega, Fabricio  
        Potra, Cristina  
        Toyoshima, Tim  
        16 total names in list  
  
        Merge based on intersect:  
        Bankov, Peter  
        Holm, Michael  
        Garcia, Hugo  
        Beebe, Ann  
        4 total names in list  
  
        Concat based on partial name match "Garcia":  
        Garcia, Debra  
        Garcia, Hugo  
        Garcia, Hugo  
        3 total names in list  
*/  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d7c1b-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="d7c1b-110">Compiling the Code</span></span>  
 <span data-ttu-id="d7c1b-111">Vytvořte projekt C# konzolové aplikace se `using` direktivami pro obory názvů System. Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="d7c1b-111">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7c1b-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d7c1b-112">See also</span></span>

- [<span data-ttu-id="d7c1b-113">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="d7c1b-113">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="d7c1b-114">LINQ a souborové adresáře (C#)</span><span class="sxs-lookup"><span data-stu-id="d7c1b-114">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
