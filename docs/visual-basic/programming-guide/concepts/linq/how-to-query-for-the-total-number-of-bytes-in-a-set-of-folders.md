---
title: 'Postupy: Vytvoření dotazu na celkový počet bajtů v sadě složek (LINQ)'
ms.date: 07/20/2015
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
ms.openlocfilehash: 25e2c2894d9feccf42ee92bdddd17d8558779e6c
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266973"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a>Postup: Dotaz na celkový počet bajtů v sadě složek (LINQ) (Visual Basic)
Tento příklad ukazuje, jak načíst celkový počet bajtů používaných všemi soubory v zadané složce a všech podsložkách.  
  
## <a name="example"></a>Příklad  
 Metoda <xref:System.Linq.Enumerable.Sum%2A> přidá hodnoty všech položek vybraných `select` v klauzuli. Tento dotaz můžete snadno upravit a načíst největší nebo nejmenší <xref:System.Linq.Enumerable.Min%2A> soubor <xref:System.Linq.Enumerable.Max%2A> v <xref:System.Linq.Enumerable.Sum%2A>zadaném adresářovém stromu voláním metody nebo namísto .  
  
```vb  
Module QueryTotalBytes  
    Sub Main()  
  
        ' Change the drive\path if necessary.  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0\VB"  
  
        'Take a snapshot of the folder contents.  
        ' This method assumes that the application has discovery permissions  
        ' for all folders under the specified path.  
        Dim fileList = My.Computer.FileSystem.GetFiles _  
                  (root, FileIO.SearchOption.SearchAllSubDirectories, "*.*")  
  
        Dim fileQuery = From file In fileList _  
                        Select GetFileLength(file)  
  
        ' Force execution and cache the results to avoid multiple trips to the file system.  
        Dim fileLengths = fileQuery.ToArray()  
  
        ' Find the largest file  
        Dim maxSize = Aggregate aFile In fileLengths Into Max()  
  
        ' Find the total number of bytes  
        Dim totalBytes = Aggregate aFile In fileLengths Into Sum()  
  
        Console.WriteLine("The largest file is " & maxSize & " bytes")  
        Console.WriteLine("There are " & totalBytes & " total bytes in " & _  
                          fileList.Count & " files under " & root)  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    Function GetFileLength(ByVal filename As String) As Long  
        Dim retval As Long  
        Try  
            Dim fi As New System.IO.FileInfo(filename)  
            retval = fi.Length  
        Catch ex As System.IO.FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 Pokud máte pouze počítat počet bajtů v zadaném adresářovém stromu, můžete to provést efektivněji bez vytvoření dotazu LINQ, který vznikne režie vytváření kolekce seznamu jako zdroj dat. Užitečnost přístupu LINQ se zvyšuje s dotazem se stává složitější, nebo pokud máte spustit více dotazů proti stejnému zdroji dat.  
  
 Dotaz volá samostatnou metodu k získání délky souboru. Je to proto, aby bylo možné využívat možnou výjimku, která <xref:System.IO.FileInfo> bude vyvolána, pokud `GetFiles`byl soubor odstraněn v jiném vlákně po vytvoření objektu ve volání . I v <xref:System.IO.FileInfo> případě, že objekt již byl <xref:System.IO.FileInfo> vytvořen, může dojít <xref:System.IO.FileInfo.Length%2A> k výjimce, protože objekt se pokusí aktualizovat svou vlastnost s nejaktuálnější délkou při prvním přístupu k vlastnosti. Umístěním této operace v bloku try-catch mimo dotaz, kód se řídí pravidlem vyhnout se operacím v dotazech, které mohou způsobit vedlejší účinky. Obecně je třeba věnovat velkou pozornost při použití výjimky a ujistěte se, že aplikace není ponechána v neznámém stavu.  
  
## <a name="compile-the-code"></a>Kompilace kódu  
Vytvořte projekt aplikace konzoly `Imports` jazyka s příkazem pro obor názvů System.Linq.
  
## <a name="see-also"></a>Viz také

- [LINQ na objekty (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [Linq a adresáře souborů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
