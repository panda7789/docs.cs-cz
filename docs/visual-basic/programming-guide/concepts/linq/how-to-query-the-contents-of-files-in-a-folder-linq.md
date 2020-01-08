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
# <a name="how-to-query-the-contents-of-files-in-a-folder-linq-visual-basic"></a>Postup dotazování na obsah souborů ve složce (LINQ) (Visual Basic)

Tento příklad ukazuje, jak se dotázat na všechny soubory v zadaném stromovém stromu, otevřít každý soubor a zkontrolovat jeho obsah. Tento typ techniky lze použít k vytvoření indexů nebo zpětných indexů obsahu stromu adresáře. V tomto příkladu je provedeno jednoduché vyhledávání řetězců. Složitější typy porovnávání vzorů však mohou být provedeny s regulárním výrazem. Další informace naleznete v tématu [How to: kombinovat dotazy LINQ s regulárními výrazy (Visual Basic)](how-to-combine-linq-queries-with-regular-expressions.md).  
  
## <a name="example"></a>Příklad  
  
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

## <a name="compile-the-code"></a>Kompilace kódu

Vytvořte projekt konzolové aplikace Visual Basic, zkopírujte a vložte ukázku kódu a upravte hodnotu spouštěcího objektu ve vlastnostech projektu.

## <a name="see-also"></a>Viz také:

- [LINQ to Objects (Visual Basic)](linq-to-objects.md)
- [LINQ a souborové adresáře (Visual Basic)](linq-and-file-directories.md)
