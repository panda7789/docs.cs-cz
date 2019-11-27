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
# <a name="how-to-combine-linq-queries-with-regular-expressions-visual-basic"></a><span data-ttu-id="452d3-102">Jak kombinovat dotazy LINQ s regulárními výrazy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="452d3-102">How to combine LINQ queries with regular expressions (Visual Basic)</span></span>

<span data-ttu-id="452d3-103">Tento příklad ukazuje, jak použít třídu <xref:System.Text.RegularExpressions.Regex> k vytvoření regulárního výrazu pro komplexnější porovnání v textových řetězcích.</span><span class="sxs-lookup"><span data-stu-id="452d3-103">This example shows how to use the <xref:System.Text.RegularExpressions.Regex> class to create a regular expression for more complex matching in text strings.</span></span> <span data-ttu-id="452d3-104">Dotaz LINQ usnadňuje filtrování přesně těch souborů, které chcete prohledávat pomocí regulárního výrazu, a k tvarování výsledků.</span><span class="sxs-lookup"><span data-stu-id="452d3-104">The LINQ query makes it easy to filter on exactly the files that you want to search with the regular expression, and to shape the results.</span></span>

## <a name="example"></a><span data-ttu-id="452d3-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="452d3-105">Example</span></span>

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

<span data-ttu-id="452d3-106">Všimněte si, že můžete také zadat dotaz na objekt <xref:System.Text.RegularExpressions.MatchCollection>, který je vrácený `RegEx` vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="452d3-106">Note that you can also query the <xref:System.Text.RegularExpressions.MatchCollection> object that is returned by a `RegEx` search.</span></span> <span data-ttu-id="452d3-107">V tomto příkladu se ve výsledcích vytvoří pouze hodnota každé shody.</span><span class="sxs-lookup"><span data-stu-id="452d3-107">In this example only the value of each match is produced in the results.</span></span> <span data-ttu-id="452d3-108">Je ale také možné použít LINQ k provádění všech druhů filtrování, řazení a seskupování v této kolekci.</span><span class="sxs-lookup"><span data-stu-id="452d3-108">However, it is also possible to use LINQ to perform all kinds of filtering, sorting, and grouping on that collection.</span></span> <span data-ttu-id="452d3-109">Vzhledem k tomu, že <xref:System.Text.RegularExpressions.MatchCollection> je neobecná <xref:System.Collections.IEnumerable> kolekce, je nutné explicitně uvést typ proměnné rozsahu v dotazu.</span><span class="sxs-lookup"><span data-stu-id="452d3-109">Because <xref:System.Text.RegularExpressions.MatchCollection> is a non-generic <xref:System.Collections.IEnumerable> collection, you have to explicitly state the type of the range variable in the query.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="452d3-110">Kompilování kódu</span><span class="sxs-lookup"><span data-stu-id="452d3-110">Compiling the code</span></span>

<span data-ttu-id="452d3-111">Vytvořte projekt konzolové aplikace VB.NET, zkopírujte a vložte ukázku kódu a upravte hodnotu spouštěcího objektu ve vlastnostech projektu.</span><span class="sxs-lookup"><span data-stu-id="452d3-111">Create a VB.NET console application project, copy and paste the code sample, and adjust the Startup object value in the project properties.</span></span>

## <a name="see-also"></a><span data-ttu-id="452d3-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="452d3-112">See also</span></span>

- [<span data-ttu-id="452d3-113">LINQ a řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="452d3-113">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
- [<span data-ttu-id="452d3-114">LINQ a souborové adresáře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="452d3-114">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
