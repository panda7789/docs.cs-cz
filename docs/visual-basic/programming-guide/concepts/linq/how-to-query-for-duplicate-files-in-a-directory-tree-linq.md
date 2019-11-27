---
title: 'Postupy: Vytvoření dotazu na duplicitní soubory v adresářovém stromu (LINQ)'
ms.date: 07/20/2015
ms.assetid: 387d7c97-95dd-4a50-9761-7e9cf8ae9e6a
ms.openlocfilehash: 9be0d1e7be70569e1fac0033414400a85071bfec
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347708"
---
# <a name="how-to-query-for-duplicate-files-in-a-directory-tree-linq-visual-basic"></a><span data-ttu-id="5618f-102">Postupy: dotaz na duplicitní soubory v adresářovém stromu (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5618f-102">How to: Query for Duplicate Files in a Directory Tree (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="5618f-103">Někdy se soubory, které mají stejný název, mohou nacházet ve více než jedné složce.</span><span class="sxs-lookup"><span data-stu-id="5618f-103">Sometimes files that have the same name may be located in more than one folder.</span></span> <span data-ttu-id="5618f-104">Například v instalační složce sady Visual Studio má několik složek soubor Readme. htm.</span><span class="sxs-lookup"><span data-stu-id="5618f-104">For example, under the Visual Studio installation folder, several folders have a readme.htm file.</span></span> <span data-ttu-id="5618f-105">Tento příklad ukazuje, jak zadat dotaz na tyto duplicitní názvy souborů v zadané kořenové složce.</span><span class="sxs-lookup"><span data-stu-id="5618f-105">This example shows how to query for such duplicate file names under a specified root folder.</span></span> <span data-ttu-id="5618f-106">Druhý příklad ukazuje, jak se dotázat na soubory, jejichž velikost a časy vytvoření se také shodují.</span><span class="sxs-lookup"><span data-stu-id="5618f-106">The second example shows how to query for files whose size and creation times also match.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5618f-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="5618f-107">Example</span></span>  
  
```vb  
Module QueryDuplicateFileNames  
  
    Public Sub Main()  
  
        Dim path As String = "C:\Program Files\Microsoft Visual Studio 9.0\Common7"  
        QueryDuplicates1(path)  
        ' Uncomment to run this query instead  
        ' QueryDuplicates2(path)  
  
    End Sub  
    Sub QueryDuplicates1(ByVal root As String)  
        Dim dir As New System.IO.DirectoryInfo(root)  
        Dim duplicates = From aFile In dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories) _  
                                 Order By aFile.Name _  
                                 Group aFile By aFile.Name Into newGroup = Group _  
                                 Where newGroup.Count() >= 2 _  
                                 Select newGroup  
  
        ' Page the display so that the results can be read.  
        Dim trimLength = root.Length  
        PageOutput(duplicates, trimLength)  
  
    End Sub  
    Sub QueryDuplicates2(ByVal root As String)  
  
        ' This time a composite key is used. This sub finds all files  
        ' that have been copied into multiple subfolders.  
        Dim dir As New System.IO.DirectoryInfo(root)  
  
        Dim duplicates = From aFile In Dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories) _  
                                 Order By aFile.Name _  
                                 Group aFile By aFile.Name, aFile.CreationTime, aFile.Length Into newGroup = Group _  
                                 Where newGroup.Count() >= 2 _  
                                 Select newGroup  
  
        ' Page the display so that the results can be read.  
        Dim trimLength = root.Length  
        PageOutput(duplicates, trimLength)  
  
    End Sub  
    ' Pages console display for large query results. No more than one group per page.  
    ' This sub specifically works with group queries of FileInfo objects  
    ' but can be modified for any type.  
    Sub PageOutput(ByVal groupQuery, ByVal charsToSkip)  
  
        ' "3" = 1 line for extension key + 1 for "Press any key" + 1 for input cursor.  
        Dim numLines As Integer = Console.WindowHeight - 3  
        ' Flag to indicate whether there are more results to display  
        Dim goAgain As Boolean = True  
  
        For Each fg As IEnumerable(Of System.IO.FileInfo) In groupQuery  
            ' Start a new extension at the top of a page.  
            Dim currentLine As Integer = 0  
  
            Do While (currentLine < fg.Count())  
                Console.Clear()  
  
                ' Get the next page of results  
                ' No more than one filename per page  
                Dim resultPage = From file In fg _  
                                Skip currentLine Take numLines  
  
                ' Execute the query. Trim the paths in the output.  
                For Each line In resultPage  
                    Console.WriteLine(vbTab & line.FullName.Substring(charsToSkip))  
                Next  
  
                ' Advance the current position  
                currentLine = numLines + currentLine  
  
                ' Give the user a chance to break out of the loop  
                Console.WriteLine("Press any key for next page or the 'End' key to exit.")  
                Dim key As ConsoleKey = Console.ReadKey().Key  
                If key = ConsoleKey.End Then  
                    goAgain = False  
                    Exit For  
                End If  
            Loop  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="5618f-108">První dotaz k určení shody používá jednoduchý klíč. Vyhledá soubory, které mají stejný název, ale jejichž obsah se může lišit.</span><span class="sxs-lookup"><span data-stu-id="5618f-108">The first query uses a simple key to determine a match; this finds files that have the same name but whose contents might be different.</span></span> <span data-ttu-id="5618f-109">Druhý dotaz používá složený klíč pro porovnání se třemi vlastnostmi objektu <xref:System.IO.FileInfo>.</span><span class="sxs-lookup"><span data-stu-id="5618f-109">The second query uses a compound key to match against three properties of the <xref:System.IO.FileInfo> object.</span></span> <span data-ttu-id="5618f-110">Tento dotaz je mnohem pravděpodobnější najít soubory se stejným názvem a podobným nebo shodným obsahem.</span><span class="sxs-lookup"><span data-stu-id="5618f-110">This query is much more likely to find files that have the same name and similar or identical content.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5618f-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="5618f-111">Compiling the Code</span></span>  
<span data-ttu-id="5618f-112">Vytvořte projekt konzolové aplikace VB.NET s příkazem `Imports` pro obor názvů System. Linq.</span><span class="sxs-lookup"><span data-stu-id="5618f-112">Create a VB.NET console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5618f-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5618f-113">See also</span></span>

- [<span data-ttu-id="5618f-114">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5618f-114">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="5618f-115">LINQ a souborové adresáře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5618f-115">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
