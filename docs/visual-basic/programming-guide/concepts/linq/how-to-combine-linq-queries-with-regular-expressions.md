---
title: Jak kombinovat dotazy LINQ s regulárními výrazy
ms.date: 07/20/2015
ms.assetid: 3da1bd10-b0d8-4d5b-a637-966891c13592
ms.openlocfilehash: 27fc46056ad78567339ca0c5818aef38d0fbb9a6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348421"
---
# <a name="how-to-combine-linq-queries-with-regular-expressions-visual-basic"></a>Jak kombinovat dotazy LINQ s regulárními výrazy (Visual Basic)

Tento příklad ukazuje, jak použít třídu <xref:System.Text.RegularExpressions.Regex> k vytvoření regulárního výrazu pro komplexnější porovnání v textových řetězcích. Dotaz LINQ usnadňuje filtrování přesně těch souborů, které chcete prohledávat pomocí regulárního výrazu, a k tvarování výsledků.

## <a name="example"></a>Příklad

```vb
Imports System.IO
Imports System.Text.RegularExpressions

Class LinqRegExVB

    Shared Sub Main()

        ' Root folder to query, along with all subfolders.
        ' Modify this path as necessary so that it accesses your Visual Studio folder.
        Dim startFolder As String = "C:\Program Files (x86)\Microsoft Visual Studio 14.0\"
        ' One of the following paths may be more appropriate on your computer.
        'Dim startFolder As String = "C:\Program Files (x86)\Microsoft Visual Studio\2017\"

        ' Take a snapshot of the file system.
        Dim fileList As IEnumerable(Of FileInfo) = GetFiles(startFolder)

        ' Create a regular expression to find all things "Visual".
        Dim searchTerm As New Regex("Visual (Basic|C#|C\+\+|Studio)")

        ' Search the contents of each .htm file.
        ' Remove the where clause to find even more matches!
        ' This query produces a list of files where a match
        ' was found, and a list of the matches in that file.
        ' Note: Explicit typing of "Match" in select clause.
        ' This is required because MatchCollection is not a
        ' generic IEnumerable collection.
        Dim queryMatchingFiles = From afile In fileList
                                Where afile.Extension = ".htm"
                                Let fileText = File.ReadAllText(afile.FullName)
                                Let matches = searchTerm.Matches(fileText)
                                Where (matches.Count > 0)
                                Select Name = afile.FullName,
                                       Matches = From match As Match In matches
                                                 Select match.Value

        ' Execute the query.
        Console.WriteLine("The term " & searchTerm.ToString() & " was found in:")

        For Each fileMatches In queryMatchingFiles
            ' Trim the path a bit, then write
            ' the file name in which a match was found.
            Dim s = fileMatches.Name.Substring(startFolder.Length - 1)
            Console.WriteLine(s)

            ' For this file, write out all the matching strings
            For Each match In fileMatches.Matches
                Console.WriteLine("  " + match)
            Next
        Next

        ' Keep the console window open in debug mode
        Console.WriteLine("Press any key to exit")
        Console.ReadKey()
    End Sub

    ' Function to retrieve a list of files. Note that this is a copy
    ' of the file information.
    Shared Function GetFiles(root As String) As IEnumerable(Of FileInfo)
        Return From file In My.Computer.FileSystem.GetFiles(
                   root, FileIO.SearchOption.SearchAllSubDirectories, "*.*")
               Select New FileInfo(file)
    End Function

End Class
```

Všimněte si, že můžete také zadat dotaz na objekt <xref:System.Text.RegularExpressions.MatchCollection>, který je vrácený `RegEx` vyhledávání. V tomto příkladu se ve výsledcích vytvoří pouze hodnota každé shody. Je ale také možné použít LINQ k provádění všech druhů filtrování, řazení a seskupování v této kolekci. Vzhledem k tomu, že <xref:System.Text.RegularExpressions.MatchCollection> je neobecná <xref:System.Collections.IEnumerable> kolekce, je nutné explicitně uvést typ proměnné rozsahu v dotazu.

## <a name="compiling-the-code"></a>Kompilování kódu

Vytvořte projekt konzolové aplikace VB.NET, zkopírujte a vložte ukázku kódu a upravte hodnotu spouštěcího objektu ve vlastnostech projektu.

## <a name="see-also"></a>Viz také:

- [LINQ a řetězce (Visual Basic)](linq-and-strings.md)
- [LINQ a souborové adresáře (Visual Basic)](linq-and-file-directories.md)
