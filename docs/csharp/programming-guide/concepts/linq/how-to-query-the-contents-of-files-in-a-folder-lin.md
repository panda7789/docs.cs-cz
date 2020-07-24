---
title: Postup dotazování obsahu textových souborů ve složce (LINQ) (C#)
description: Naučte se používat LINQ v jazyce C# k dotazování všech souborů ve stromovém stromu, otevřít jednotlivé soubory a zkontrolovat její obsah.
ms.date: 07/20/2015
ms.assetid: f5b4dce7-1a34-4eb4-9bf1-60d5bdda264c
ms.openlocfilehash: 216edc2ee6fc43fd06a3c89b1b6b73f693f752f8
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104260"
---
# <a name="how-to-query-the-contents-of-text-files-in-a-folder-linq-c"></a>Postup dotazování obsahu textových souborů ve složce (LINQ) (C#)
Tento příklad ukazuje, jak se dotázat na všechny soubory v zadaném stromovém stromu, otevřít každý soubor a zkontrolovat jeho obsah. Tento typ techniky lze použít k vytvoření indexů nebo zpětných indexů obsahu stromu adresáře. V tomto příkladu je provedeno jednoduché vyhledávání řetězců. Složitější typy porovnávání vzorů však mohou být provedeny s regulárním výrazem. Další informace najdete v tématu [postup kombinování dotazů LINQ s regulárními výrazy (C#)](./how-to-combine-linq-queries-with-regular-expressions.md).  
  
## <a name="example"></a>Příklad  
  
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
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
Vytvořte projekt konzolové aplikace v jazyce C# se `using` direktivami pro obory názvů System. Linq a System.IO.
  
## <a name="see-also"></a>Viz také

- [LINQ a souborové adresáře (C#)](./linq-and-file-directories.md)
- [LINQ to Objects (C#)](./linq-to-objects.md)
