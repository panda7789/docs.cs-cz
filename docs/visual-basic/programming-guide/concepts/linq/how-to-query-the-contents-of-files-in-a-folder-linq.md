---
title: 'Postupy: Dotaz na obsah souborů ve složce (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: edacbcd3-f3e4-4429-a8be-28a58dc0dd70
ms.openlocfilehash: 8af6653c3cffe846082606de81d4bbefedaa30e9
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592121"
---
# <a name="how-to-query-the-contents-of-files-in-a-folder-linq-visual-basic"></a><span data-ttu-id="8ccad-102">Postupy: Dotaz na obsah souborů ve složce (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ccad-102">How to: Query the Contents of Files in a Folder (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="8ccad-103">Tento příklad ukazuje, jak dotaz nad všechny soubory ve stromové struktuře zadaný adresář, otevřete každý soubor a zkontrolujte jeho obsah.</span><span class="sxs-lookup"><span data-stu-id="8ccad-103">This example shows how to query over all the files in a specified directory tree, open each file, and inspect its contents.</span></span> <span data-ttu-id="8ccad-104">Tento typ technika může použít k vytváření indexů nebo obrácení pořadí indexů obsah adresářovém stromu.</span><span class="sxs-lookup"><span data-stu-id="8ccad-104">This type of technique could be used to create indexes or reverse indexes of the contents of a directory tree.</span></span> <span data-ttu-id="8ccad-105">Hledání jednoduchého řetězce se provádí v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="8ccad-105">A simple string search is performed in this example.</span></span> <span data-ttu-id="8ccad-106">Porovnávání vzorů složitější typy však lze provést s regulárním výrazem.</span><span class="sxs-lookup"><span data-stu-id="8ccad-106">However, more complex types of pattern matching can be performed with a regular expression.</span></span> <span data-ttu-id="8ccad-107">Další informace najdete v tématu [jak: Kombinace dotazů LINQ s regulárními výrazy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="8ccad-107">For more information, see [How to: Combine LINQ Queries with Regular Expressions (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ccad-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="8ccad-108">Example</span></span>  
  
```vb  
Module Module1  
    'QueryContents  
    Public Sub Main()  
  
        ' Modify this path as necessary.  
        Dim startFolder = "c:\program files\Microsoft Visual Studio 9.0\VB\"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(startFolder)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        Dim searchTerm = "Visual Studio"  
  
        ' Search the contents of each file.  
        ' A regular expression created with the RegEx class  
        ' could be used instead of the Contains method.  
        Dim queryMatchingFiles = From file In fileList _  
                                 Where file.Extension = ".htm" _  
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
    Function GetFileText(ByVal name As String) As String  
  
        ' If the file has been deleted, the right thing  
        ' to do in this case is return an empty string.  
        Dim fileContents = String.Empty  
  
        ' If the file has been deleted since we took   
        ' the snapshot, ignore it and return the empty string.  
        If System.IO.File.Exists(name) Then  
            fileContents = System.IO.File.ReadAllText(name)  
        End If  
  
        Return fileContents  
  
    End Function  
End Module  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8ccad-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="8ccad-109">Compiling the Code</span></span>  
<span data-ttu-id="8ccad-110">Vytvoření projektu aplikace konzoly VB.NET, pomocí `Imports` příkaz pro obor názvů System.Linq.</span><span class="sxs-lookup"><span data-stu-id="8ccad-110">Create a VB.NET console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8ccad-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8ccad-111">See also</span></span>

- [<span data-ttu-id="8ccad-112">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ccad-112">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="8ccad-113">LINQ a souborové adresáře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ccad-113">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
