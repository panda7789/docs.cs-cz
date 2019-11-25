---
title: 'Postupy: Seskupování souborů podle přípony (LINQ)'
ms.date: 07/20/2015
ms.assetid: 904dc6d7-7162-4655-a7f4-5785d669bc5a
ms.openlocfilehash: 9e0b5bc29cbfc454cc8031bcd62ed723b8995095
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344551"
---
# <a name="how-to-group-files-by-extension-linq-visual-basic"></a><span data-ttu-id="b013a-102">How to: Group Files by Extension (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b013a-102">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="b013a-103">This example shows how LINQ can be used to perform advanced grouping and sorting operations on lists of files or folders.</span><span class="sxs-lookup"><span data-stu-id="b013a-103">This example shows how LINQ can be used to perform advanced grouping and sorting operations on lists of files or folders.</span></span> <span data-ttu-id="b013a-104">It also shows how to page output in the console window by using the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods.</span><span class="sxs-lookup"><span data-stu-id="b013a-104">It also shows how to page output in the console window by using the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b013a-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="b013a-105">Example</span></span>  
 <span data-ttu-id="b013a-106">The following query shows how to group the contents of a specified directory tree by the file name extension.</span><span class="sxs-lookup"><span data-stu-id="b013a-106">The following query shows how to group the contents of a specified directory tree by the file name extension.</span></span>  
  
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
  
 <span data-ttu-id="b013a-107">The output from this program can be long, depending on the details of the local file system and what the `startFolder` is set to.</span><span class="sxs-lookup"><span data-stu-id="b013a-107">The output from this program can be long, depending on the details of the local file system and what the `startFolder` is set to.</span></span> <span data-ttu-id="b013a-108">To enable viewing of all results, this example shows how to page through results.</span><span class="sxs-lookup"><span data-stu-id="b013a-108">To enable viewing of all results, this example shows how to page through results.</span></span> <span data-ttu-id="b013a-109">The same techniques can be applied to Windows and Web applications.</span><span class="sxs-lookup"><span data-stu-id="b013a-109">The same techniques can be applied to Windows and Web applications.</span></span> <span data-ttu-id="b013a-110">Notice that because the code pages the items in a group, a nested `For Each` loop is required.</span><span class="sxs-lookup"><span data-stu-id="b013a-110">Notice that because the code pages the items in a group, a nested `For Each` loop is required.</span></span> <span data-ttu-id="b013a-111">There is also some additional logic to compute the current position in the list, and to enable the user to stop paging and exit the program.</span><span class="sxs-lookup"><span data-stu-id="b013a-111">There is also some additional logic to compute the current position in the list, and to enable the user to stop paging and exit the program.</span></span> <span data-ttu-id="b013a-112">In this particular case, the paging query is run against the cached results from the original query.</span><span class="sxs-lookup"><span data-stu-id="b013a-112">In this particular case, the paging query is run against the cached results from the original query.</span></span> <span data-ttu-id="b013a-113">In other contexts, such as LINQ to SQL, such caching is not required.</span><span class="sxs-lookup"><span data-stu-id="b013a-113">In other contexts, such as LINQ to SQL, such caching is not required.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b013a-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b013a-114">Compiling the Code</span></span>  
<span data-ttu-id="b013a-115">Create a VB.NET console application project, with an `Imports` statement for the System.Linq namespace.</span><span class="sxs-lookup"><span data-stu-id="b013a-115">Create a VB.NET console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b013a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b013a-116">See also</span></span>

- [<span data-ttu-id="b013a-117">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b013a-117">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="b013a-118">LINQ and File Directories (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b013a-118">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
