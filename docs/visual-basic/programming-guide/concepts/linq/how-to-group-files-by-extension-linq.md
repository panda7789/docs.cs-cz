---
title: 'Postupy: Skupiny souborů podle přípony (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 904dc6d7-7162-4655-a7f4-5785d669bc5a
ms.openlocfilehash: f36be784641d45aaae447097ae2bebb5fd650034
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593471"
---
# <a name="how-to-group-files-by-extension-linq-visual-basic"></a>Postupy: Skupiny souborů podle přípony (LINQ) (Visual Basic)
Tento příklad ukazuje, jak lze provádět pokročilé seskupování a řazení v seznamech soubory nebo složky LINQ. Také ukazuje, jak pomocí stránky výstup v okně konzoly <xref:System.Linq.Enumerable.Skip%2A> a <xref:System.Linq.Enumerable.Take%2A> metody.  
  
## <a name="example"></a>Příklad  
 Následující dotaz ukazuje, jak seskupit obsah určený adresářový strom podle přípony názvu souboru.  
  
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
  
 Výstup z tohoto programu může být dlouhý, v závislosti na podrobnosti o místního systému souborů a co `startFolder` nastavena. Chcete-li povolit zobrazení všech výsledků, tento příklad ukazuje, jak stránkovat výsledky. Stejné postupy můžete použít pro Windows a webových aplikací. Všimněte si, že protože kód stránky položky ve skupině, vnořený `For Each` smyčky je povinný. Je také některé další logiku pro výpočet aktuální pozici v seznamu a umožňuje uživateli zastavit stránkování a ukončit program. V tomto konkrétním případě dotazu stránkování spustit pro výsledky uložené v mezipaměti z původního dotazu. V jiných kontextech, jako je například technologie LINQ to SQL tyto ukládání do mezipaměti se nevyžaduje.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
Vytvoření projektu aplikace konzoly VB.NET, pomocí `Imports` příkaz pro obor názvů System.Linq.
  
## <a name="see-also"></a>Viz také:

- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [LINQ a souborové adresáře (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
