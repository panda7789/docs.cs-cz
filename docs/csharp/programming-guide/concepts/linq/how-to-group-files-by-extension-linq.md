---
title: Postup seskupení souborů podle přípony (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 21a98320-a5a1-4981-82d8-6a637e7d9018
ms.openlocfilehash: d12b40c7dba7bd3e10f30ddfd394b25c36794428
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345903"
---
# <a name="how-to-group-files-by-extension-linq-c"></a>Postup seskupení souborů podle přípony (LINQ) (C#)
Tento příklad ukazuje, jak lze LINQ použít k provádění pokročilých operací seskupení a řazení v seznamech souborů nebo složek. Ukazuje také výstup stránky v okně konzoly pomocí metod <xref:System.Linq.Enumerable.Skip%2A> a <xref:System.Linq.Enumerable.Take%2A>.  
  
## <a name="example"></a>Příklad  
 Následující dotaz ukazuje, jak seskupit obsah zadaného stromu adresářů podle přípony názvu souboru.  
  
```csharp  
class GroupByExtension  
{  
    // This query will sort all the files under the specified folder  
    //  and subfolder into groups keyed by the file extension.  
    private static void Main()  
    {  
        // Take a snapshot of the file system.  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\Common7";  
  
        // Used in WriteLine to trim output lines.  
        int trimLength = startFolder.Length;  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        // Create the query.  
        var queryGroupByExt =  
            from file in fileList  
            group file by file.Extension.ToLower() into fileGroup  
            orderby fileGroup.Key  
            select fileGroup;  
  
        // Display one group at a time. If the number of   
        // entries is greater than the number of lines  
        // in the console window, then page the output.  
        PageOutput(trimLength, queryGroupByExt);  
    }  
  
    // This method specifically handles group queries of FileInfo objects with string keys.  
    // It can be modified to work for any long listings of data. Note that explicit typing  
    // must be used in method signatures. The groupbyExtList parameter is a query that produces  
    // groups of FileInfo objects with string keys.  
    private static void PageOutput(int rootLength,  
                                    IEnumerable<System.Linq.IGrouping<string, System.IO.FileInfo>> groupByExtList)  
    {  
        // Flag to break out of paging loop.  
        bool goAgain = true;  
  
        // "3" = 1 line for extension + 1 for "Press any key" + 1 for input cursor.  
        int numLines = Console.WindowHeight - 3;  
  
        // Iterate through the outer collection of groups.  
        foreach (var filegroup in groupByExtList)  
        {  
            // Start a new extension at the top of a page.  
            int currentLine = 0;  
  
            // Output only as many lines of the current group as will fit in the window.  
            do  
            {  
                Console.Clear();  
                Console.WriteLine(filegroup.Key == String.Empty ? "[none]" : filegroup.Key);  
  
                // Get 'numLines' number of items starting at number 'currentLine'.  
                var resultPage = filegroup.Skip(currentLine).Take(numLines);  
  
                //Execute the resultPage query  
                foreach (var f in resultPage)  
                {  
                    Console.WriteLine("\t{0}", f.FullName.Substring(rootLength));  
                }  
  
                // Increment the line counter.  
                currentLine += numLines;  
  
                // Give the user a chance to escape.  
                Console.WriteLine("Press any key to continue or the 'End' key to break...");  
                ConsoleKey key = Console.ReadKey().Key;  
                if (key == ConsoleKey.End)  
                {  
                    goAgain = false;  
                    break;  
                }  
            } while (currentLine < filegroup.Count());  
  
            if (goAgain == false)  
                break;  
        }  
    }  
}  
```  
  
 Výstup z tohoto programu může být dlouhý v závislosti na podrobnostech místního systému souborů a nastavení, na které je `startFolder`. Pokud chcete povolit zobrazení všech výsledků, tento příklad ukazuje, jak stránky procházet výsledky. Stejné postupy můžete použít pro Windows a webové aplikace. Všimněte si, že vzhledem k tomu, že kód stránky má položky ve skupině, je nutná vnořená `foreach` smyčka. K dispozici je také některá další logika, která umožňuje vypočítat aktuální pozici v seznamu a umožnit uživateli zastavit stránkování a ukončit program. V tomto konkrétním případě se stránkovací dotaz spustí proti výsledkům uloženým v mezipaměti z původního dotazu. V jiných kontextech, jako je například LINQ to SQL, taková mezipaměť není nutná.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vytvořte projekt C# konzolové aplikace s direktivami `using` pro obory názvů System. Linq a System.IO.  
  
## <a name="see-also"></a>Viz také:

- [LINQ to Objects (C#)](./linq-to-objects.md)
- [LINQ a souborové adresáře (C#)](./linq-and-file-directories.md)
