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
# <a name="how-to-combine-linq-queries-with-regular-expressions-c"></a>Jak kombinovat dotazy LINQ s regulárními výrazy (C#)
Tento příklad ukazuje, jak použít <xref:System.Text.RegularExpressions.Regex> třídu k vytvoření regulárního výrazu pro komplexnější porovnání v textových řetězcích. Dotaz LINQ usnadňuje filtrování přesně těch souborů, které chcete prohledávat pomocí regulárního výrazu, a k tvarování výsledků.  
  
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
  
 Všimněte si, že můžete také zadat dotaz na <xref:System.Text.RegularExpressions.MatchCollection> objekt, který je vrácený `RegEx` hledáním. V tomto příkladu se ve výsledcích vytvoří pouze hodnota každé shody. Je ale také možné použít LINQ k provádění všech druhů filtrování, řazení a seskupování v této kolekci. Vzhledem k tomu <xref:System.Text.RegularExpressions.MatchCollection> , že je neobecná <xref:System.Collections.IEnumerable> kolekce, je nutné explicitně uvést typ proměnné rozsahu v dotazu.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vytvořte projekt konzolové aplikace v jazyce C# se `using` směrnicemi pro obory názvů System. Linq a System.IO.  
  
## <a name="see-also"></a>Viz také

- [LINQ a řetězce (C#)](./linq-and-strings.md)
- [LINQ a souborové adresáře (C#)](./linq-and-file-directories.md)
