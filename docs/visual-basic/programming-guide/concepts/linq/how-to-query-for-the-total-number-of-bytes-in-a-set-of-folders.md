---
title: 'Postupy: Vytvoření dotazu na celkový počet bajtů v sadě složek (LINQ)'
ms.date: 07/20/2015
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
ms.openlocfilehash: c32985d7b1d87a45107159726d6ee24aea0b59b7
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346030"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a>Postupy: vytvoření dotazu na celkový počet bajtů v sadě složek (LINQ) (Visual Basic)
Tento příklad ukazuje, jak načíst celkový počet bajtů použitých všemi soubory v zadané složce a všech jejích podsložkách.  
  
## <a name="example"></a>Příklad  
 Metoda <xref:System.Linq.Enumerable.Sum%2A> přidá hodnoty všech položek vybraných v klauzuli `select`. Tento dotaz můžete snadno upravit tak, aby získal největší nebo nejmenší soubor v zadaném stromu adresářů voláním metody <xref:System.Linq.Enumerable.Min%2A> nebo <xref:System.Linq.Enumerable.Max%2A> namísto <xref:System.Linq.Enumerable.Sum%2A>.  
  
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
  
 Pokud potřebujete pouze spočítat počet bajtů v zadaném stromové struktuře, můžete to udělat efektivněji bez vytvoření dotazu LINQ, což způsobí režii při vytváření kolekce seznamu jako zdroje dat. Užitečnost přístupu LINQ se zvyšuje, protože dotaz je složitější, nebo když je nutné spustit více dotazů proti stejnému zdroji dat.  
  
 Dotaz volá k samostatné metodě, aby získal délku souboru. Provede to za účelem využívání možné výjimky, která bude vyvolána, pokud byl soubor odstraněn v jiném vlákně poté, co byl objekt <xref:System.IO.FileInfo> vytvořen při volání `GetFiles`. I když již byl objekt <xref:System.IO.FileInfo> vytvořen, může dojít k výjimce, protože objekt <xref:System.IO.FileInfo> se pokusí aktualizovat jeho vlastnost <xref:System.IO.FileInfo.Length%2A> s nejaktuálnější délkou při prvním otevření vlastnosti. Vložením této operace do bloku try-catch mimo dotaz kód sleduje pravidlo vyloučení operací v dotazech, které mohou způsobit vedlejší účinky. Obecně platí, že je potřeba věnovat velkou péči, když využijete výjimky, aby se zajistilo, že aplikace zůstane v neznámém stavu.  
  
## <a name="compile-the-code"></a>Kompilace kódu  
Vytvořte projekt konzolové aplikace Visual Basic s příkazem `Imports` pro obor názvů System. Linq.
  
## <a name="see-also"></a>Viz také:

- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [LINQ a souborové adresáře (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
