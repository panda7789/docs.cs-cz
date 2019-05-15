---
title: 'Postupy: Seskupování souborů podle přípony (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 21a98320-a5a1-4981-82d8-6a637e7d9018
ms.openlocfilehash: 0b8cb30396a93f5f878c091c4aad3cab9db3f2d4
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65584295"
---
# <a name="how-to-group-files-by-extension-linq-c"></a><span data-ttu-id="aec80-102">Postupy: Seskupování souborů podle přípony (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="aec80-102">How to: Group Files by Extension (LINQ) (C#)</span></span>
<span data-ttu-id="aec80-103">Tento příklad ukazuje, jak lze provádět pokročilé seskupování a řazení v seznamech soubory nebo složky LINQ.</span><span class="sxs-lookup"><span data-stu-id="aec80-103">This example shows how LINQ can be used to perform advanced grouping and sorting operations on lists of files or folders.</span></span> <span data-ttu-id="aec80-104">Také ukazuje, jak pomocí stránky výstup v okně konzoly <xref:System.Linq.Enumerable.Skip%2A> a <xref:System.Linq.Enumerable.Take%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="aec80-104">It also shows how to page output in the console window by using the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aec80-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="aec80-105">Example</span></span>  
 <span data-ttu-id="aec80-106">Následující dotaz ukazuje, jak seskupit obsah určený adresářový strom podle přípony názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="aec80-106">The following query shows how to group the contents of a specified directory tree by the file name extension.</span></span>  
  
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
  
 <span data-ttu-id="aec80-107">Výstup z tohoto programu může být dlouhý, v závislosti na podrobnosti o místního systému souborů a co `startFolder` nastavena.</span><span class="sxs-lookup"><span data-stu-id="aec80-107">The output from this program can be long, depending on the details of the local file system and what the `startFolder` is set to.</span></span> <span data-ttu-id="aec80-108">Chcete-li povolit zobrazení všech výsledků, tento příklad ukazuje, jak stránkovat výsledky.</span><span class="sxs-lookup"><span data-stu-id="aec80-108">To enable viewing of all results, this example shows how to page through results.</span></span> <span data-ttu-id="aec80-109">Stejné postupy můžete použít pro Windows a webových aplikací.</span><span class="sxs-lookup"><span data-stu-id="aec80-109">The same techniques can be applied to Windows and Web applications.</span></span> <span data-ttu-id="aec80-110">Všimněte si, že protože kód stránky položky ve skupině, vnořený `foreach` smyčky je povinný.</span><span class="sxs-lookup"><span data-stu-id="aec80-110">Notice that because the code pages the items in a group, a nested `foreach` loop is required.</span></span> <span data-ttu-id="aec80-111">Je také některé další logiku pro výpočet aktuální pozici v seznamu a umožňuje uživateli zastavit stránkování a ukončit program.</span><span class="sxs-lookup"><span data-stu-id="aec80-111">There is also some additional logic to compute the current position in the list, and to enable the user to stop paging and exit the program.</span></span> <span data-ttu-id="aec80-112">V tomto konkrétním případě dotazu stránkování spustit pro výsledky uložené v mezipaměti z původního dotazu.</span><span class="sxs-lookup"><span data-stu-id="aec80-112">In this particular case, the paging query is run against the cached results from the original query.</span></span> <span data-ttu-id="aec80-113">V jiných kontextech, jako je například technologie LINQ to SQL tyto ukládání do mezipaměti se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="aec80-113">In other contexts, such as LINQ to SQL, such caching is not required.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="aec80-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="aec80-114">Compiling the Code</span></span>  
 <span data-ttu-id="aec80-115">Vytvoření C# konzole projekt aplikace s `using` direktivy pro obory názvů System.Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="aec80-115">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aec80-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aec80-116">See also</span></span>

- [<span data-ttu-id="aec80-117">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="aec80-117">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="aec80-118">LINQ a souborové adresáře (C#)</span><span class="sxs-lookup"><span data-stu-id="aec80-118">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
