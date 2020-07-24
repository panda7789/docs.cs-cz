---
title: Dotazování na soubory se zadaným atributem nebo názvem (C#)
description: Naučte se používat LINQ v jazyce C# k nalezení souborů, které mají zadanou příponu názvu souboru ve stromu adresářů a jak vrátí nejnovější nebo nejstarší soubor.
ms.date: 07/20/2015
ms.assetid: 560e3879-b0b3-4549-ad02-0a53aff2f83c
ms.openlocfilehash: 9820b96e19d805b792e18ff242e64dfb6cf4a606
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104506"
---
# <a name="how-to-query-for-files-with-a-specified-attribute-or-name-c"></a><span data-ttu-id="4f811-103">Dotazování na soubory se zadaným atributem nebo názvem (C#)</span><span class="sxs-lookup"><span data-stu-id="4f811-103">How to query for files with a specified attribute or name (C#)</span></span>
<span data-ttu-id="4f811-104">Tento příklad ukazuje, jak najít všechny soubory, které mají zadanou příponu názvu souboru (například ". txt") v zadaném stromu adresářů.</span><span class="sxs-lookup"><span data-stu-id="4f811-104">This example shows how to find all files that have a specified file name extension (for example ".txt") in a specified directory tree.</span></span> <span data-ttu-id="4f811-105">Také ukazuje, jak vrátit nejnovější nebo nejstarší soubor ve stromu na základě času vytvoření.</span><span class="sxs-lookup"><span data-stu-id="4f811-105">It also shows how to return either the newest or oldest file in the tree based on the creation time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f811-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="4f811-106">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="4f811-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4f811-107">Compiling the Code</span></span>  
  <span data-ttu-id="4f811-108">Vytvořte projekt konzolové aplikace v jazyce C# se `using` direktivami pro obory názvů System. Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="4f811-108">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4f811-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="4f811-109">See also</span></span>

- [<span data-ttu-id="4f811-110">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="4f811-110">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="4f811-111">LINQ a souborové adresáře (C#)</span><span class="sxs-lookup"><span data-stu-id="4f811-111">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
