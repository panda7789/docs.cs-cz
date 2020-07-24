---
title: Jak kombinovat dotazy LINQ s regulárními výrazy (C#)
description: Tento příklad vytvoří regulární výraz pro porovnání v textových řetězcích pomocí třídy Regex v jazyce C#.
ms.date: 07/20/2015
ms.assetid: 6b003b65-20a4-4ca2-929e-2ee3f215aecc
ms.openlocfilehash: af63d096e3c2f19ed557180d82d606989a016120
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105345"
---
# <a name="how-to-combine-linq-queries-with-regular-expressions-c"></a><span data-ttu-id="7a429-103">Jak kombinovat dotazy LINQ s regulárními výrazy (C#)</span><span class="sxs-lookup"><span data-stu-id="7a429-103">How to combine LINQ queries with regular expressions (C#)</span></span>
<span data-ttu-id="7a429-104">Tento příklad ukazuje, jak použít <xref:System.Text.RegularExpressions.Regex> třídu k vytvoření regulárního výrazu pro komplexnější porovnání v textových řetězcích.</span><span class="sxs-lookup"><span data-stu-id="7a429-104">This example shows how to use the <xref:System.Text.RegularExpressions.Regex> class to create a regular expression for more complex matching in text strings.</span></span> <span data-ttu-id="7a429-105">Dotaz LINQ usnadňuje filtrování přesně těch souborů, které chcete prohledávat pomocí regulárního výrazu, a k tvarování výsledků.</span><span class="sxs-lookup"><span data-stu-id="7a429-105">The LINQ query makes it easy to filter on exactly the files that you want to search with the regular expression, and to shape the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a429-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="7a429-106">Example</span></span>  
  
```csharp  
class QueryWithRegEx  
{  
    public static void Main()  
    {  
        // Modify this path as necessary so that it accesses your version of Visual Studio.  
        string startFolder = @"C:\Program Files (x86)\Microsoft Visual Studio 14.0\";  
        // One of the following paths may be more appropriate on your computer.  
        //string startFolder = @"C:\Program Files (x86)\Microsoft Visual Studio\2017\";  
  
        // Take a snapshot of the file system.  
        IEnumerable<System.IO.FileInfo> fileList = GetFiles(startFolder);  
  
        // Create the regular expression to find all things "Visual".  
        System.Text.RegularExpressions.Regex searchTerm =  
            new System.Text.RegularExpressions.Regex(@"Visual (Basic|C#|C\+\+|Studio)");  
  
        // Search the contents of each .htm file.  
        // Remove the where clause to find even more matchedValues!  
        // This query produces a list of files where a match  
        // was found, and a list of the matchedValues in that file.  
        // Note: Explicit typing of "Match" in select clause.  
        // This is required because MatchCollection is not a
        // generic IEnumerable collection.  
        var queryMatchingFiles =  
            from file in fileList  
            where file.Extension == ".htm"  
            let fileText = System.IO.File.ReadAllText(file.FullName)  
            let matches = searchTerm.Matches(fileText)  
            where matches.Count > 0  
            select new  
            {  
                name = file.FullName,  
                matchedValues = from System.Text.RegularExpressions.Match match in matches  
                                select match.Value  
            };  
  
        // Execute the query.  
        Console.WriteLine("The term \"{0}\" was found in:", searchTerm.ToString());  
  
        foreach (var v in queryMatchingFiles)  
        {  
            // Trim the path a bit, then write
            // the file name in which a match was found.  
            string s = v.name.Substring(startFolder.Length - 1);  
            Console.WriteLine(s);  
  
            // For this file, write out all the matching strings  
            foreach (var v2 in v.matchedValues)  
            {  
                Console.WriteLine("  " + v2);  
            }  
        }  
  
        // Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // This method assumes that the application has discovery
    // permissions for all folders under the specified path.  
    static IEnumerable<System.IO.FileInfo> GetFiles(string path)  
    {  
        if (!System.IO.Directory.Exists(path))  
            throw new System.IO.DirectoryNotFoundException();  
  
        string[] fileNames = null;  
        List<System.IO.FileInfo> files = new List<System.IO.FileInfo>();  
  
        fileNames = System.IO.Directory.GetFiles(path, "*.*", System.IO.SearchOption.AllDirectories);  
        foreach (string name in fileNames)  
        {  
            files.Add(new System.IO.FileInfo(name));  
        }  
        return files;  
    }  
}  
```  
  
 <span data-ttu-id="7a429-107">Všimněte si, že můžete také zadat dotaz na <xref:System.Text.RegularExpressions.MatchCollection> objekt, který je vrácený `RegEx` hledáním.</span><span class="sxs-lookup"><span data-stu-id="7a429-107">Note that you can also query the <xref:System.Text.RegularExpressions.MatchCollection> object that is returned by a `RegEx` search.</span></span> <span data-ttu-id="7a429-108">V tomto příkladu se ve výsledcích vytvoří pouze hodnota každé shody.</span><span class="sxs-lookup"><span data-stu-id="7a429-108">In this example only the value of each match is produced in the results.</span></span> <span data-ttu-id="7a429-109">Je ale také možné použít LINQ k provádění všech druhů filtrování, řazení a seskupování v této kolekci.</span><span class="sxs-lookup"><span data-stu-id="7a429-109">However, it is also possible to use LINQ to perform all kinds of filtering, sorting, and grouping on that collection.</span></span> <span data-ttu-id="7a429-110">Vzhledem k tomu <xref:System.Text.RegularExpressions.MatchCollection> , že je neobecná <xref:System.Collections.IEnumerable> kolekce, je nutné explicitně uvést typ proměnné rozsahu v dotazu.</span><span class="sxs-lookup"><span data-stu-id="7a429-110">Because <xref:System.Text.RegularExpressions.MatchCollection> is a non-generic <xref:System.Collections.IEnumerable> collection, you have to explicitly state the type of the range variable in the query.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7a429-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7a429-111">Compiling the Code</span></span>  
 <span data-ttu-id="7a429-112">Vytvořte projekt konzolové aplikace v jazyce C# se `using` směrnicemi pro obory názvů System. Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="7a429-112">Create a C# console application project with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a429-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a429-113">See also</span></span>

- [<span data-ttu-id="7a429-114">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="7a429-114">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="7a429-115">LINQ a souborové adresáře (C#)</span><span class="sxs-lookup"><span data-stu-id="7a429-115">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
