---
title: 'Postupy: dotaz pro soubory s konkrétním atributem či názvem (C#)'
ms.date: 07/20/2015
ms.assetid: 560e3879-b0b3-4549-ad02-0a53aff2f83c
ms.openlocfilehash: ee366f551eb73059196cb4dcd61c1ca42bf55fda
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324353"
---
# <a name="how-to-query-for-files-with-a-specified-attribute-or-name-c"></a><span data-ttu-id="17c1b-102">Postupy: dotaz pro soubory s konkrétním atributem či názvem (C#)</span><span class="sxs-lookup"><span data-stu-id="17c1b-102">How to: Query for Files with a Specified Attribute or Name (C#)</span></span>
<span data-ttu-id="17c1b-103">Tento příklad ukazuje, jak najít všechny soubory, které mají příponu názvu zadaný soubor (například ".txt") v zadané adresářovém stromu.</span><span class="sxs-lookup"><span data-stu-id="17c1b-103">This example shows how to find all files that have a specified file name extension (for example ".txt") in a specified directory tree.</span></span> <span data-ttu-id="17c1b-104">Také ukazuje, jak vrátit nejnovější nebo nejstarší soubor ve stromu podle času vytvoření.</span><span class="sxs-lookup"><span data-stu-id="17c1b-104">It also shows how to return either the newest or oldest file in the tree based on the creation time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17c1b-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="17c1b-105">Example</span></span>  
  
```csharp  
class FindFileByExtension  
{  
    // This query will produce the full path for all .txt files  
    // under the specified folder including subfolders.  
    // It orders the list according to the file name.  
    static void Main()  
    {  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        //Create the query  
        IEnumerable<System.IO.FileInfo> fileQuery =  
            from file in fileList  
            where file.Extension == ".txt"  
            orderby file.Name  
            select file;  
  
        //Execute the query. This might write out a lot of files!  
        foreach (System.IO.FileInfo fi in fileQuery)  
        {  
            Console.WriteLine(fi.FullName);  
        }  
  
        // Create and execute a new query by using the previous   
        // query as a starting point. fileQuery is not   
        // executed again until the call to Last()  
        var newestFile =  
            (from file in fileQuery  
             orderby file.CreationTime  
             select new { file.FullName, file.CreationTime })  
            .Last();  
  
        Console.WriteLine("\r\nThe newest .txt file is {0}. Creation time: {1}",  
            newestFile.FullName, newestFile.CreationTime);  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="17c1b-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="17c1b-106">Compiling the Code</span></span>  
 <span data-ttu-id="17c1b-107">Vytvoření projektu, jehož cílem rozhraní .NET Framework verze 3.5 nebo vyšší, s odkazem na System.Core.dll a `using` direktivy pro obory názvů System.Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="17c1b-107">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to   System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17c1b-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="17c1b-108">See Also</span></span>  
 [<span data-ttu-id="17c1b-109">LINQ na objekty (C#)</span><span class="sxs-lookup"><span data-stu-id="17c1b-109">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="17c1b-110">LINQ a souborové adresáře (C#)</span><span class="sxs-lookup"><span data-stu-id="17c1b-110">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
