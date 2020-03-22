---
title: 'Postupy: Seskupování souborů podle přípony (LINQ)'
ms.date: 07/20/2015
ms.assetid: 904dc6d7-7162-4655-a7f4-5785d669bc5a
ms.openlocfilehash: 4d2c51fa62b3ec144bc5ad51b4a9f8305476645e
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78267025"
---
# <a name="how-to-group-files-by-extension-linq-visual-basic"></a><span data-ttu-id="8af64-102">Postup: Seskupení souborů podle rozšíření (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8af64-102">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="8af64-103">Tento příklad ukazuje, jak linq lze použít k provádění rozšířené seskupení a řazení operace v seznamech souborů nebo složek.</span><span class="sxs-lookup"><span data-stu-id="8af64-103">This example shows how LINQ can be used to perform advanced grouping and sorting operations on lists of files or folders.</span></span> <span data-ttu-id="8af64-104">Také ukazuje, jak stránkovat výstup v <xref:System.Linq.Enumerable.Skip%2A> okně <xref:System.Linq.Enumerable.Take%2A> konzoly pomocí a metody.</span><span class="sxs-lookup"><span data-stu-id="8af64-104">It also shows how to page output in the console window by using the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8af64-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="8af64-105">Example</span></span>  
 <span data-ttu-id="8af64-106">Následující dotaz ukazuje, jak seskupit obsah zadaného adresářového stromu podle přípony názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="8af64-106">The following query shows how to group the contents of a specified directory tree by the file name extension.</span></span>  
  
```vb  
Module GroupByExtension  
    Public Sub Main()  
  
        ' Root folder to query, along with all subfolders.  
        Dim startFolder As String = "C:\program files\Microsoft Visual Studio 9.0\VB\"  
  
        ' Used in WriteLine() to skip over startfolder in output lines.  
        Dim rootLength As Integer = startFolder.Length  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(startFolder)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Create the query.  
        Dim queryGroupByExt = From file In fileList _  
                          Group By file.Extension.ToLower() Into fileGroup = Group _  
                          Order By ToLower _  
                          Select fileGroup  
  
        ' Execute the query. By storing the result we can  
        ' page the display with good performance.  
        Dim groupByExtList = queryGroupByExt.ToList()  
  
        ' Display one group at a time. If the number of
        ' entries is greater than the number of lines  
        ' in the console window, then page the output.  
        Dim trimLength = startFolder.Length  
        PageOutput(groupByExtList, trimLength)  
  
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
                Console.WriteLine(fg(0).Extension)  
  
                ' Get the next page of results  
                ' No more than one filename per page  
                Dim resultPage = From file In fg _  
                                Skip currentLine Take numLines  
  
                ' Execute the query. Trim the display output.  
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
  
 <span data-ttu-id="8af64-107">Výstup z tohoto programu může být dlouhý, v závislosti na `startFolder` podrobnostech místního systému souborů a na tom, na co je nastaven.</span><span class="sxs-lookup"><span data-stu-id="8af64-107">The output from this program can be long, depending on the details of the local file system and what the `startFolder` is set to.</span></span> <span data-ttu-id="8af64-108">Chcete-li povolit zobrazení všech výsledků, tento příklad ukazuje, jak stránkovat výsledky.</span><span class="sxs-lookup"><span data-stu-id="8af64-108">To enable viewing of all results, this example shows how to page through results.</span></span> <span data-ttu-id="8af64-109">Stejné techniky lze použít pro systém Windows a webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="8af64-109">The same techniques can be applied to Windows and Web applications.</span></span> <span data-ttu-id="8af64-110">Všimněte si, že vzhledem k tomu, `For Each` že kód stránky položky ve skupině, vnořené smyčky je vyžadována.</span><span class="sxs-lookup"><span data-stu-id="8af64-110">Notice that because the code pages the items in a group, a nested `For Each` loop is required.</span></span> <span data-ttu-id="8af64-111">K dispozici je také některé další logiku vypočítat aktuální pozici v seznamu a umožnit uživateli zastavit stránkování a ukončovat program.</span><span class="sxs-lookup"><span data-stu-id="8af64-111">There is also some additional logic to compute the current position in the list, and to enable the user to stop paging and exit the program.</span></span> <span data-ttu-id="8af64-112">V tomto konkrétním případě je stránkovací dotaz spuštěn proti výsledky uložené v mezipaměti z původního dotazu.</span><span class="sxs-lookup"><span data-stu-id="8af64-112">In this particular case, the paging query is run against the cached results from the original query.</span></span> <span data-ttu-id="8af64-113">V jiných kontextech, jako je například LINQ na SQL, takové ukládání do mezipaměti není vyžadováno.</span><span class="sxs-lookup"><span data-stu-id="8af64-113">In other contexts, such as LINQ to SQL, such caching is not required.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="8af64-114">Kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="8af64-114">Compile the code</span></span>  
<span data-ttu-id="8af64-115">Vytvořte projekt aplikace konzoly `Imports` jazyka s příkazem pro obor názvů System.Linq.</span><span class="sxs-lookup"><span data-stu-id="8af64-115">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8af64-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="8af64-116">See also</span></span>

- [<span data-ttu-id="8af64-117">LINQ na objekty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8af64-117">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="8af64-118">Linq a adresáře souborů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8af64-118">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
