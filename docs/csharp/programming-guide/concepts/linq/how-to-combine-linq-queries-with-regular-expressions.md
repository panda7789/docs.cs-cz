---
title: Jak kombinovat dotazy LINQ s regulárními výrazy (C#)
ms.date: 07/20/2015
ms.assetid: 6b003b65-20a4-4ca2-929e-2ee3f215aecc
ms.openlocfilehash: 104e63adb9c07a75077b92654afd791b6c82d8de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169426"
---
# <a name="how-to-combine-linq-queries-with-regular-expressions-c"></a>Jak kombinovat dotazy LINQ s regulárními výrazy (C#)
Tento příklad ukazuje, <xref:System.Text.RegularExpressions.Regex> jak použít třídu k vytvoření regulárního výrazu pro složitější párování v textových řetězcích. Dotaz LINQ usnadňuje filtrování přesně souborů, které chcete prohledávat pomocí regulárního výrazu, a tvarovat výsledky.  
  
## <a name="example"></a>Příklad  
  
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
  
 Všimněte si, že <xref:System.Text.RegularExpressions.MatchCollection> můžete také dotaz `RegEx` na objekt, který je vrácen hledáním. V tomto příkladu je ve výsledcích vytvořena pouze hodnota každé shody. Je však také možné použít LINQ provádět všechny druhy filtrování, řazení a seskupení v této kolekci. Protože <xref:System.Text.RegularExpressions.MatchCollection> je neobecná <xref:System.Collections.IEnumerable> kolekce, musíte explicitně uvést typ proměnné rozsahu v dotazu.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vytvořte projekt aplikace konzoly Jazyka C# se `using` direktivami pro obory názvů System.Linq a System.IO.  
  
## <a name="see-also"></a>Viz také

- [LINQ a řetězce (C#)](./linq-and-strings.md)
- [Linq a souborové adresáře (C#)](./linq-and-file-directories.md)
