---
title: 'Postupy: Dotazu na obsah textových souborů ve složce (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: f5b4dce7-1a34-4eb4-9bf1-60d5bdda264c
ms.openlocfilehash: 66e2a2d6ee2b8dd3be3e66f7277947b6d6f749a4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688154"
---
# <a name="how-to-query-the-contents-of-text-files-in-a-folder-linq-c"></a><span data-ttu-id="7df3d-102">Postupy: Dotazu na obsah textových souborů ve složce (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7df3d-102">How to: Query the Contents of Text Files in a Folder (LINQ) (C#)</span></span>
<span data-ttu-id="7df3d-103">Tento příklad ukazuje, jak dotaz nad všechny soubory ve stromové struktuře zadaný adresář, otevřete každý soubor a zkontrolujte jeho obsah.</span><span class="sxs-lookup"><span data-stu-id="7df3d-103">This example shows how to query over all the files in a specified directory tree, open each file, and inspect its contents.</span></span> <span data-ttu-id="7df3d-104">Tento typ technika může použít k vytváření indexů nebo obrácení pořadí indexů obsah adresářovém stromu.</span><span class="sxs-lookup"><span data-stu-id="7df3d-104">This type of technique could be used to create indexes or reverse indexes of the contents of a directory tree.</span></span> <span data-ttu-id="7df3d-105">Hledání jednoduchého řetězce se provádí v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="7df3d-105">A simple string search is performed in this example.</span></span> <span data-ttu-id="7df3d-106">Porovnávání vzorů složitější typy však lze provést s regulárním výrazem.</span><span class="sxs-lookup"><span data-stu-id="7df3d-106">However, more complex types of pattern matching can be performed with a regular expression.</span></span> <span data-ttu-id="7df3d-107">Další informace najdete v tématu [jak: Kombinace dotazů LINQ s regulárními výrazy (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="7df3d-107">For more information, see [How to: Combine LINQ Queries with Regular Expressions (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7df3d-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="7df3d-108">Example</span></span>  
  
```csharp  
class QueryContents  
{  
    public static void Main()  
    {  
        // Modify this path as necessary.  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        string searchTerm = @"Visual Studio";  
  
        // Search the contents of each file.  
        // A regular expression created with the RegEx class  
        // could be used instead of the Contains method.  
        // queryMatchingFiles is an IEnumerable<string>.  
        var queryMatchingFiles =  
            from file in fileList  
            where file.Extension == ".htm"  
            let fileText = GetFileText(file.FullName)  
            where fileText.Contains(searchTerm)  
            select file.FullName;  
  
        // Execute the query.  
        Console.WriteLine("The term \"{0}\" was found in:", searchTerm);  
        foreach (string filename in queryMatchingFiles)  
        {  
            Console.WriteLine(filename);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // Read the contents of the file.  
    static string GetFileText(string name)  
    {  
        string fileContents = String.Empty;  
  
        // If the file has been deleted since we took   
        // the snapshot, ignore it and return the empty string.  
        if (System.IO.File.Exists(name))  
        {  
            fileContents = System.IO.File.ReadAllText(name);  
        }  
        return fileContents;  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7df3d-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7df3d-109">Compiling the Code</span></span>  
 <span data-ttu-id="7df3d-110">Vytvořit projekt, který cílí na rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na knihovnu System.Core.dll a `using` direktivy pro obory názvů System.Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="7df3d-110">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7df3d-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7df3d-111">See also</span></span>

- [<span data-ttu-id="7df3d-112">LINQ a souborové adresáře (C#)</span><span class="sxs-lookup"><span data-stu-id="7df3d-112">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
- [<span data-ttu-id="7df3d-113">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="7df3d-113">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
