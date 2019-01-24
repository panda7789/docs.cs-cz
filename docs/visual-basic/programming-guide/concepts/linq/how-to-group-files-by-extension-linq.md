---
title: 'Postupy: Skupiny souborů podle přípony (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 904dc6d7-7162-4655-a7f4-5785d669bc5a
ms.openlocfilehash: c52debf2e40c6ed6da2d7f3c7dbdb16e1f7396f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728223"
---
# <a name="how-to-group-files-by-extension-linq-visual-basic"></a><span data-ttu-id="752bc-102">Postupy: Skupiny souborů podle přípony (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="752bc-102">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="752bc-103">Tento příklad ukazuje, jak lze provádět pokročilé seskupování a řazení v seznamech soubory nebo složky LINQ.</span><span class="sxs-lookup"><span data-stu-id="752bc-103">This example shows how LINQ can be used to perform advanced grouping and sorting operations on lists of files or folders.</span></span> <span data-ttu-id="752bc-104">Také ukazuje, jak pomocí stránky výstup v okně konzoly <xref:System.Linq.Enumerable.Skip%2A> a <xref:System.Linq.Enumerable.Take%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="752bc-104">It also shows how to page output in the console window by using the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="752bc-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="752bc-105">Example</span></span>  
 <span data-ttu-id="752bc-106">Následující dotaz ukazuje, jak seskupit obsah určený adresářový strom podle přípony názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="752bc-106">The following query shows how to group the contents of a specified directory tree by the file name extension.</span></span>  
  
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
  
    ' Pages console diplay for large query results. No more than one group per page.  
    ' This sub specifically works with group queries of FileInfo objects  
    ' but can be modified for any type.  
    Sub PageOutput(ByVal groupQuery, ByVal charsToSkip)  
  
        ' "3" = 1 line for extension key + 1 for "Press any key" + 1 for input cursor.  
        Dim numLines As Integer = Console.WindowHeight - 3  
        ' Flag to indicate whether there are more results to diplay  
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
  
 <span data-ttu-id="752bc-107">Výstup z tohoto programu může být dlouhý, v závislosti na podrobnosti o místního systému souborů a co `startFolder` nastavena.</span><span class="sxs-lookup"><span data-stu-id="752bc-107">The output from this program can be long, depending on the details of the local file system and what the `startFolder` is set to.</span></span> <span data-ttu-id="752bc-108">Chcete-li povolit zobrazení všech výsledků, tento příklad ukazuje, jak stránkovat výsledky.</span><span class="sxs-lookup"><span data-stu-id="752bc-108">To enable viewing of all results, this example shows how to page through results.</span></span> <span data-ttu-id="752bc-109">Stejné postupy můžete použít pro Windows a webových aplikací.</span><span class="sxs-lookup"><span data-stu-id="752bc-109">The same techniques can be applied to Windows and Web applications.</span></span> <span data-ttu-id="752bc-110">Všimněte si, že protože kód stránky položky ve skupině, vnořený `For Each` smyčky je povinný.</span><span class="sxs-lookup"><span data-stu-id="752bc-110">Notice that because the code pages the items in a group, a nested `For Each` loop is required.</span></span> <span data-ttu-id="752bc-111">Je také některé další logiku pro výpočet aktuální pozici v seznamu a umožňuje uživateli zastavit stránkování a ukončit program.</span><span class="sxs-lookup"><span data-stu-id="752bc-111">There is also some additional logic to compute the current position in the list, and to enable the user to stop paging and exit the program.</span></span> <span data-ttu-id="752bc-112">V tomto konkrétním případě dotazu stránkování spustit pro výsledky uložené v mezipaměti z původního dotazu.</span><span class="sxs-lookup"><span data-stu-id="752bc-112">In this particular case, the paging query is run against the cached results from the original query.</span></span> <span data-ttu-id="752bc-113">V jiných kontextech, jako je například technologie LINQ to SQL tyto ukládání do mezipaměti se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="752bc-113">In other contexts, such as LINQ to SQL, such caching is not required.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="752bc-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="752bc-114">Compiling the Code</span></span>  
 <span data-ttu-id="752bc-115">Vytvořit projekt, který cílí na rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na knihovnu System.Core.dll a `Imports` příkaz pro obor názvů System.Linq.</span><span class="sxs-lookup"><span data-stu-id="752bc-115">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a   `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="752bc-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="752bc-116">See also</span></span>
- [<span data-ttu-id="752bc-117">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="752bc-117">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="752bc-118">LINQ a souborové adresáře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="752bc-118">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
