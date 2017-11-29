---
title: "Postupy: kombinace dotazů LINQ s regulárními výrazy (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3da1bd10-b0d8-4d5b-a637-966891c13592
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6cf6ee296f142ce50a9448d80ab961dafe86ab4f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-combine-linq-queries-with-regular-expressions-visual-basic"></a><span data-ttu-id="38dee-102">Postupy: kombinace dotazů LINQ s regulárními výrazy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38dee-102">How to: Combine LINQ Queries with Regular Expressions (Visual Basic)</span></span>
<span data-ttu-id="38dee-103">Tento příklad ukazuje způsob použití <xref:System.Text.RegularExpressions.Regex> třídy za účelem vytvoření regulární výraz pro složitější párování v textové řetězce.</span><span class="sxs-lookup"><span data-stu-id="38dee-103">This example shows how to use the <xref:System.Text.RegularExpressions.Regex> class to create a regular expression for more complex matching in text strings.</span></span> <span data-ttu-id="38dee-104">Dotaz LINQ usnadňuje filtru na přesně soubory, které chcete hledat s regulárnímu výrazu a utvářejí výsledky.</span><span class="sxs-lookup"><span data-stu-id="38dee-104">The LINQ query makes it easy to filter on exactly the files that you want to search with the regular expression, and to shape the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38dee-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="38dee-105">Example</span></span>  
  
```vb  
Class LinqRegExVB  
  
    Shared Sub Main()  
  
        ' Root folder to query, along with all subfolders.  
        ' Modify this path as necessary so that it accesses your Visual Studio folder.  
        Dim startFolder As String = "C:\Program Files (x86)\Microsoft Visual Studio 14.0\"
        ' One of the following paths may be more appropriate on your computer.  
        'Dim startFolder As String = "C:\Program Files (x86)\Microsoft Visual Studio\2017\"
  
        ' Take a snapshot of the file system.  
        Dim fileList As IEnumerable(Of System.IO.FileInfo) = GetFiles(startFolder)  
  
        ' Create a regular expression to find all things "Visual".  
        Dim searchTerm As System.Text.RegularExpressions.Regex =   
            New System.Text.RegularExpressions.Regex("Visual (Basic|C#|C\+\+|Studio)")  
  
        ' Search the contents of each .htm file.  
        ' Remove the where clause to find even more matches!  
        ' This query produces a list of files where a match  
        ' was found, and a list of the matches in that file.  
        ' Note: Explicit typing of "Match" in select clause.  
        ' This is required because MatchCollection is not a   
        ' generic IEnumerable collection.  
        Dim queryMatchingFiles = From afile In fileList  
                                Where afile.Extension = ".htm"  
                                Let fileText = System.IO.File.ReadAllText(afile.FullName)  
                                Let matches = searchTerm.Matches(fileText)  
                                Where (matches.Count > 0)  
                                Select Name = afile.FullName,  
                                       Matches = From match As System.Text.RegularExpressions.Match In matches  
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
    Shared Function GetFiles(ByVal root As String) As IEnumerable(Of System.IO.FileInfo)  
        Return From file In My.Computer.FileSystem.GetFiles(  
                   root, FileIO.SearchOption.SearchAllSubDirectories, "*.*")   
               Select New System.IO.FileInfo(file)  
    End Function  
  
End Class  
```  
  
 <span data-ttu-id="38dee-106">Všimněte si, že se můžete dotazovat i <xref:System.Text.RegularExpressions.MatchCollection> objekt, který je vrácen `RegEx` vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="38dee-106">Note that you can also query the <xref:System.Text.RegularExpressions.MatchCollection> object that is returned by a `RegEx` search.</span></span> <span data-ttu-id="38dee-107">V tomto příkladu se vytvoří pouze hodnotu každé shody ve výsledcích.</span><span class="sxs-lookup"><span data-stu-id="38dee-107">In this example only the value of each match is produced in the results.</span></span> <span data-ttu-id="38dee-108">Je však také možné používat LINQ k provádění nejrůznějších druhy filtrování, řazení a seskupování v dané kolekci.</span><span class="sxs-lookup"><span data-stu-id="38dee-108">However, it is also possible to use LINQ to perform all kinds of filtering, sorting, and grouping on that collection.</span></span> <span data-ttu-id="38dee-109">Protože <xref:System.Text.RegularExpressions.MatchCollection> je není obecný <xref:System.Collections.IEnumerable> kolekci, je nutné explicitně stavu druh proměnné rozsahu v dotazu.</span><span class="sxs-lookup"><span data-stu-id="38dee-109">Because <xref:System.Text.RegularExpressions.MatchCollection> is a non-generic <xref:System.Collections.IEnumerable> collection, you have to explicitly state the type of the range variable in the query.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="38dee-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="38dee-110">Compiling the Code</span></span>  
 <span data-ttu-id="38dee-111">Vytvoření projektu, jehož cílem rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na System.Core.dll a `Imports` příkaz pro obor názvů System.Linq.</span><span class="sxs-lookup"><span data-stu-id="38dee-111">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38dee-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="38dee-112">See Also</span></span>  
 [<span data-ttu-id="38dee-113">LINQ a řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38dee-113">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 [<span data-ttu-id="38dee-114">LINQ a souborové adresáře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38dee-114">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
