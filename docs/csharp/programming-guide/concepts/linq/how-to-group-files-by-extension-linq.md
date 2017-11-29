---
title: "Postupy: seskupování souborů podle přípony (LINQ) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 21a98320-a5a1-4981-82d8-6a637e7d9018
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 71bee94ad5aec6cc7aaef480f72f4220716a2cd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-files-by-extension-linq-c"></a><span data-ttu-id="c8845-102">Postupy: seskupování souborů podle přípony (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="c8845-102">How to: Group Files by Extension (LINQ) (C#)</span></span>
<span data-ttu-id="c8845-103">Tento příklad ukazuje, jak lze pomocí LINQ provádět pokročilé seskupení a řazení v seznamech soubory nebo složky.</span><span class="sxs-lookup"><span data-stu-id="c8845-103">This example shows how LINQ can be used to perform advanced grouping and sorting operations on lists of files or folders.</span></span> <span data-ttu-id="c8845-104">Také ukazuje, jak na stránku výstup v okně konzoly pomocí <xref:System.Linq.Enumerable.Skip%2A> a <xref:System.Linq.Enumerable.Take%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c8845-104">It also shows how to page output in the console window by using the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8845-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="c8845-105">Example</span></span>  
 <span data-ttu-id="c8845-106">Následující dotaz ukazuje, jak seskupit obsah zadaného adresářovém stromu příponu názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="c8845-106">The following query shows how to group the contents of a specified directory tree by the file name extension.</span></span>  
  
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
  
 <span data-ttu-id="c8845-107">Výstup z tento program může být dlouhý, v závislosti na podrobnosti o místní systém souborů a co `startFolder` je nastaven na.</span><span class="sxs-lookup"><span data-stu-id="c8845-107">The output from this program can be long, depending on the details of the local file system and what the `startFolder` is set to.</span></span> <span data-ttu-id="c8845-108">Povolit zobrazování všechny výsledky, tento příklad ukazuje, jak na stránku prostřednictvím výsledky.</span><span class="sxs-lookup"><span data-stu-id="c8845-108">To enable viewing of all results, this example shows how to page through results.</span></span> <span data-ttu-id="c8845-109">Stejné postupy lze použít k systému Windows a webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="c8845-109">The same techniques can be applied to Windows and Web applications.</span></span> <span data-ttu-id="c8845-110">Všimněte si, že vzhledem k tomu, že kód stránky položky ve skupině vnořený `foreach` smyčka je požadovaná.</span><span class="sxs-lookup"><span data-stu-id="c8845-110">Notice that because the code pages the items in a group, a nested `foreach` loop is required.</span></span> <span data-ttu-id="c8845-111">Je také některé další logiku výpočetní aktuální pozici v seznamu a zajistit, aby uživatel stránkování zastavení a ukončení programu.</span><span class="sxs-lookup"><span data-stu-id="c8845-111">There is also some additional logic to compute the current position in the list, and to enable the user to stop paging and exit the program.</span></span> <span data-ttu-id="c8845-112">V tomto konkrétním případě stránkování spuštění dotazu s výsledky uložené v mezipaměti z původní dotaz.</span><span class="sxs-lookup"><span data-stu-id="c8845-112">In this particular case, the paging query is run against the cached results from the original query.</span></span> <span data-ttu-id="c8845-113">V jiných kontextech, jako je například technologie LINQ to SQL takové ukládání do mezipaměti se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="c8845-113">In other contexts, such as LINQ to SQL, such caching is not required.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c8845-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="c8845-114">Compiling the Code</span></span>  
 <span data-ttu-id="c8845-115">Vytvoření projektu, jehož cílem rozhraní .NET Framework verze 3.5 nebo vyšší, s odkazem na System.Core.dll a `using` direktivy pro obory názvů System.Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="c8845-115">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to   System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8845-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="c8845-116">See Also</span></span>  
 [<span data-ttu-id="c8845-117">LINQ na objekty (C#)</span><span class="sxs-lookup"><span data-stu-id="c8845-117">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="c8845-118">LINQ a souborové adresáře (C#)</span><span class="sxs-lookup"><span data-stu-id="c8845-118">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
