---
title: 'Postupy: Dotaz pro celkový počet bajtů v sadě složek (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
ms.openlocfilehash: 9aa098ddca2e3ad300913b207c9db5a4976eded7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051400"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a>Postupy: Dotaz pro celkový počet bajtů v sadě složek (LINQ) (Visual Basic)
Tento příklad ukazuje, jak získat celkový počet bajtů, které používají všechny soubory v zadané složce a jejích podsložkách.  
  
## <a name="example"></a>Příklad  
 <xref:System.Linq.Enumerable.Sum%2A> Metoda přidá hodnoty všechny položky vybrané v `select` klauzuli. Můžete snadno upravit tento dotaz pro načtení souboru největší nebo nejmenší ve stromové struktuře zadaný adresář voláním <xref:System.Linq.Enumerable.Min%2A> nebo <xref:System.Linq.Enumerable.Max%2A> metoda místo <xref:System.Linq.Enumerable.Sum%2A>.  
  
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
  
 Pokud máte jenom spočítat počet bajtů v zadaném adresáři stromu, může to provedete efektivněji bez vytvoření LINQ dotaz, který režijní náklady na vytvoření kolekce seznamu jako zdroj dat s sebou nese náklady. Užitečnost LINQ přístup zvyšuje, jak dotaz stává složitější, nebo když musíte spustit více dotazů na stejném zdroji dat.  
  
 Dotaz zdůrazňuje samostatné metodě získat délku souboru. Aby bylo možné využívat možnou výjimkou, která bude vyvolána, pokud soubor byl odstraněn v jiném vlákně po dělá to <xref:System.IO.FileInfo> objekt byl vytvořen při volání funkce `GetFiles`. I v případě, <xref:System.IO.FileInfo> objekt již byl vytvořen, výjimce může dojít, protože <xref:System.IO.FileInfo> objekt se pokusí obnovit jeho <xref:System.IO.FileInfo.Length%2A> vlastnost s nejaktuálnější délku při prvním přístupu k vlastnosti. Vložením této operace v bloku try-catch mimo dotaz následuje kód pravidlo vyhnout operací v dotazech, které může způsobit vedlejší účinky. Obecně platí musí být věnovat pozornost při využívání výjimky, abyste měli jistotu, že aplikace není ponechán v neznámém stavu.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vytvořit projekt, který cílí na rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na knihovnu System.Core.dll a `Imports` příkaz pro obor názvů System.Linq.  
  
## <a name="see-also"></a>Viz také:

- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [LINQ a souborové adresáře (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
