---
title: 'Postupy: dotaz na celkový počet bajtů v sadě složek (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
ms.openlocfilehash: 6a6babaf019cdac2298aee6eff55581bf35b2e47
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643546"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a>Postupy: dotaz na celkový počet bajtů v sadě složek (LINQ) (Visual Basic)
Tento příklad ukazuje, jak načíst celkový počet bajtů použitých tak, že všechny soubory v zadané složce a jejích podsložkách.  
  
## <a name="example"></a>Příklad  
 <xref:System.Linq.Enumerable.Sum%2A> Metoda přidá hodnoty všech položek vybraných v `select` klauzule. Můžete snadno upravit tento dotaz pro načtení souboru největších nebo nejmenší ve stromové struktuře zadaný adresář voláním <xref:System.Linq.Enumerable.Min%2A> nebo <xref:System.Linq.Enumerable.Max%2A> metoda místo <xref:System.Linq.Enumerable.Sum%2A>.  
  
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
  
 Pokud máte pouze počet bajtů ve stromu zadaný adresář, musíte efektivněji bez vytvoření dotazu LINQ, což způsobuje režií při vytváření kolekce seznamu jako zdroj dat. Použitelnosti tohoto přístupu LINQ zvyšuje dotaz začne být složitější, nebo pokud máte ke spouštění více dotazů na stejném datovém zdroji.  
  
 Dotaz se volá samostatné metodě získat délku souboru. Aby bylo možné využívat možné výjimku, která bude vyvolána, pokud soubor byl odstraněn na jiné vlákno po dělá to <xref:System.IO.FileInfo> objekt byl vytvořen ve volání `GetFiles`. I když <xref:System.IO.FileInfo> objekt již byl vytvořen, výjimka může dojít, protože <xref:System.IO.FileInfo> objekt se pokusí obnovit jeho <xref:System.IO.FileInfo.Length%2A> vlastnost s nejaktuálnější délka poprvé vlastnost přistupuje. Try-catch – blok mimo dotaz vložíte tuto operaci, následuje kód pravidla vyloučení operace v dotazech, které můžou způsobit vedlejší účinky. Obecně platí musí být přijata pozor při využívat výjimky a ujistěte se, že aplikace není ponecháno v neznámém stavu.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vytvoření projektu, jehož cílem rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na System.Core.dll a `Imports` příkaz pro obor názvů System.Linq.  
  
## <a name="see-also"></a>Viz také  
 [LINQ na objekty (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
 [LINQ a souborové adresáře (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
