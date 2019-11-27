---
title: 'Postupy: Vytvoření dotazu na soubory s konkrétním atributem či názvem'
ms.date: 07/20/2015
ms.assetid: b26026a3-3f43-448f-a582-259997af6be0
ms.openlocfilehash: 68b8f02e3c7f53092ef91f2b8b96736a644a7fd1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347690"
---
# <a name="how-to-query-for-files-with-a-specified-attribute-or-name-visual-basic"></a><span data-ttu-id="19fd0-102">Postupy: dotazování na soubory se zadaným atributem nebo názvem (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19fd0-102">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>
<span data-ttu-id="19fd0-103">Tento příklad ukazuje, jak najít všechny soubory, které mají zadanou příponu názvu souboru (například ". txt") v zadaném stromu adresářů.</span><span class="sxs-lookup"><span data-stu-id="19fd0-103">This example shows how to find all files that have a specified file name extension (for example ".txt") in a specified directory tree.</span></span> <span data-ttu-id="19fd0-104">Také ukazuje, jak vrátit nejnovější nebo nejstarší soubor ve stromu na základě času vytvoření.</span><span class="sxs-lookup"><span data-stu-id="19fd0-104">It also shows how to return either the newest or oldest file in the tree based on the creation time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19fd0-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="19fd0-105">Example</span></span>  
  
```vb  
Module FindFileByExtension  
    Sub Main()  
  
        ' Change the drive\path if necessary  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(root)  
  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' This query will produce the full path for all .txt files  
        ' under the specified folder including subfolders.  
        ' It orders the list according to the file name.  
        Dim fileQuery = From file In fileList _  
                        Where file.Extension = ".txt" _  
                        Order By file.Name _  
                        Select file  
  
        For Each file In fileQuery  
            Console.WriteLine(file.FullName)  
        Next  
  
        ' Create and execute a new query by using  
        ' the previous query as a starting point.  
        ' fileQuery is not executed again until the  
        ' call to Last  
        Dim fileQuery2 = From file In fileQuery _  
                         Order By file.CreationTime _  
                         Select file.Name, file.CreationTime  
  
        ' Execute the query  
        Dim newestFile = fileQuery2.Last  
  
        Console.WriteLine("\r\nThe newest .txt file is {0}. Creation time: {1}", _  
                newestFile.Name, newestFile.CreationTime)  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
End Module  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="19fd0-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="19fd0-106">Compiling the Code</span></span>  
<span data-ttu-id="19fd0-107">Vytvořte projekt konzolové aplikace VB.NET s příkazem `Imports` pro obor názvů System. Linq.</span><span class="sxs-lookup"><span data-stu-id="19fd0-107">Create a VB.NET console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="19fd0-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19fd0-108">See also</span></span>

- [<span data-ttu-id="19fd0-109">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19fd0-109">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="19fd0-110">LINQ a souborové adresáře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19fd0-110">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
