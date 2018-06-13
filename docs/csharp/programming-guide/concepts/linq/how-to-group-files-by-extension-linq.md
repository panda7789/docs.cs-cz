---
title: 'Postupy: seskupování souborů podle přípony (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 21a98320-a5a1-4981-82d8-6a637e7d9018
ms.openlocfilehash: 4b2200799a7623bf9d47540f922798f5161be1bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33319290"
---
# <a name="how-to-group-files-by-extension-linq-c"></a>Postupy: seskupování souborů podle přípony (LINQ) (C#)
Tento příklad ukazuje, jak lze pomocí LINQ provádět pokročilé seskupení a řazení v seznamech soubory nebo složky. Také ukazuje, jak na stránku výstup v okně konzoly pomocí <xref:System.Linq.Enumerable.Skip%2A> a <xref:System.Linq.Enumerable.Take%2A> metody.  
  
## <a name="example"></a>Příklad  
 Následující dotaz ukazuje, jak seskupit obsah zadaného adresářovém stromu příponu názvu souboru.  
  
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
  
 Výstup z tento program může být dlouhý, v závislosti na podrobnosti o místní systém souborů a co `startFolder` je nastaven na. Povolit zobrazování všechny výsledky, tento příklad ukazuje, jak na stránku prostřednictvím výsledky. Stejné postupy lze použít k systému Windows a webové aplikace. Všimněte si, že vzhledem k tomu, že kód stránky položky ve skupině vnořený `foreach` smyčka je požadovaná. Je také některé další logiku výpočetní aktuální pozici v seznamu a zajistit, aby uživatel stránkování zastavení a ukončení programu. V tomto konkrétním případě stránkování spuštění dotazu s výsledky uložené v mezipaměti z původní dotaz. V jiných kontextech, jako je například technologie LINQ to SQL takové ukládání do mezipaměti se nevyžaduje.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vytvoření projektu, jehož cílem rozhraní .NET Framework verze 3.5 nebo vyšší, s odkazem na System.Core.dll a `using` direktivy pro obory názvů System.Linq a System.IO.  
  
## <a name="see-also"></a>Viz také  
 [LINQ na objekty (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
 [LINQ a souborové adresáře (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
