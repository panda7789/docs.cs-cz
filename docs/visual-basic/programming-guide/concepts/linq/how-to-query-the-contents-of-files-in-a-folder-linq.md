---
title: Jak vytvářet dotazy na obsah souborů ve složce (LINQ)
ms.date: 07/20/2015
ms.assetid: edacbcd3-f3e4-4429-a8be-28a58dc0dd70
ms.openlocfilehash: 3ad5fd6c893d590d46be67e6320ac5b915829f4b
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346038"
---
# <a name="how-to-query-the-contents-of-files-in-a-folder-linq-visual-basic"></a><span data-ttu-id="2d490-102">Postup dotazování na obsah souborů ve složce (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d490-102">How to query the contents of files in a folder (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="2d490-103">Tento příklad ukazuje, jak se dotázat na všechny soubory v zadaném stromovém stromu, otevřít každý soubor a zkontrolovat jeho obsah.</span><span class="sxs-lookup"><span data-stu-id="2d490-103">This example shows how to query over all the files in a specified directory tree, open each file, and inspect its contents.</span></span> <span data-ttu-id="2d490-104">Tento typ techniky lze použít k vytvoření indexů nebo zpětných indexů obsahu stromu adresáře.</span><span class="sxs-lookup"><span data-stu-id="2d490-104">This type of technique could be used to create indexes or reverse indexes of the contents of a directory tree.</span></span> <span data-ttu-id="2d490-105">V tomto příkladu je provedeno jednoduché vyhledávání řetězců.</span><span class="sxs-lookup"><span data-stu-id="2d490-105">A simple string search is performed in this example.</span></span> <span data-ttu-id="2d490-106">Složitější typy porovnávání vzorů však mohou být provedeny s regulárním výrazem.</span><span class="sxs-lookup"><span data-stu-id="2d490-106">However, more complex types of pattern matching can be performed with a regular expression.</span></span> <span data-ttu-id="2d490-107">Další informace naleznete v tématu [How to: kombinovat dotazy LINQ s regulárními výrazy (Visual Basic)](how-to-combine-linq-queries-with-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="2d490-107">For more information, see [How to: Combine LINQ Queries with Regular Expressions (Visual Basic)](how-to-combine-linq-queries-with-regular-expressions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d490-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="2d490-108">Example</span></span>  
  
```vb
Imports System.IO

Module Module1  
    'QueryContents  
    Public Sub Main()  
  
        ' Modify this path as necessary.  
        Dim startFolder = "C:\Program Files (x86)\Microsoft Visual Studio 14.0"  

        ' Take a snapshot of the folder contents.
        Dim dir As New DirectoryInfo(startFolder)
        Dim fileList = dir.GetFiles("*.*", SearchOption.AllDirectories)

        Dim searchTerm = "Welcome"

        ' Search the contents of each file.
        ' A regular expression created with the RegEx class
        ' could be used instead of the Contains method.
        Dim queryMatchingFiles = From file In fileList _
                                 Where file.Extension = ".html" _
                                 Let fileText = GetFileText(file.FullName) _
                                 Where fileText.Contains(searchTerm) _
                                 Select file.FullName

        Console.WriteLine("The term " & searchTerm & " was found in:")

        ' Execute the query.
        For Each filename In queryMatchingFiles
            Console.WriteLine(filename)
        Next

        ' Keep the console window open in debug mode.
        Console.WriteLine("Press any key to exit")
        Console.ReadKey()

    End Sub

    ' Read the contents of the file. This is done in a separate
    ' function in order to handle potential file system errors.
    Function GetFileText(name As String) As String

        ' If the file has been deleted, the right thing
        ' to do in this case is return an empty string.
        Dim fileContents = String.Empty

        ' If the file has been deleted since we took
        ' the snapshot, ignore it and return the empty string.
        If File.Exists(name) Then
            fileContents = File.ReadAllText(name)
        End If

        Return fileContents

    End Function
End Module
```

## <a name="compile-the-code"></a><span data-ttu-id="2d490-109">Kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="2d490-109">Compile the code</span></span>

<span data-ttu-id="2d490-110">Vytvořte projekt konzolové aplikace Visual Basic, zkopírujte a vložte ukázku kódu a upravte hodnotu spouštěcího objektu ve vlastnostech projektu.</span><span class="sxs-lookup"><span data-stu-id="2d490-110">Create a Visual Basic console application project, copy and paste the code sample, and adjust the Startup object value in the project properties.</span></span>

## <a name="see-also"></a><span data-ttu-id="2d490-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d490-111">See also</span></span>

- [<span data-ttu-id="2d490-112">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d490-112">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
- [<span data-ttu-id="2d490-113">LINQ a souborové adresáře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d490-113">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
