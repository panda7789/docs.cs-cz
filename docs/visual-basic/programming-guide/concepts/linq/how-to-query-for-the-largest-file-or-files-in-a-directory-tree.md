---
title: 'Postupy: Vytvoření dotazu na největší soubor či soubory v adresářovém stromu (LINQ)'
ms.date: 07/20/2015
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
ms.openlocfilehash: 34f2cd97cafbe142c9462e8d0cf7c17f9f0d16f9
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346073"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a>Postupy: vytvoření dotazu na největší soubor nebo soubory ve stromu adresářů (LINQ) (Visual Basic)
Tento příklad ukazuje pět dotazů týkajících se velikosti souboru v bajtech:  
  
- Jak načíst velikost v bajtech pro největší soubor  
  
- Jak načíst velikost nejmenšího souboru v bajtech.  
  
- Jak načíst největší nebo nejmenší soubor objektu <xref:System.IO.FileInfo> z jedné nebo více složek v zadané kořenové složce.  
  
- Jak načíst sekvenci, jako je 10 největších souborů.  
  
- Postup při řazení souborů do skupin na základě velikosti jejich souboru v bajtech. soubory, které jsou menší než zadaná velikost, se ignorují.  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje pět samostatných dotazů, které ukazují, jak zadávat dotazy a seskupovat soubory v závislosti na velikosti souboru v bajtech. Tyto příklady lze snadno upravit tak, aby dotaz byly založeny na nějaké jiné vlastnosti objektu <xref:System.IO.FileInfo>.  
  
```vb  
Module QueryBySize  
    Sub Main()  
  
        ' Change the drive\path if necessary  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(root)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Return the size of the largest file  
        Dim maxSize = Aggregate aFile In fileList Into Max(GetFileLength(aFile))  
  
        'Dim maxSize = fileLengths.Max  
        Console.WriteLine("The length of the largest file under {0} is {1}", _  
                          root, maxSize)  
  
        ' Return the FileInfo object of the largest file  
        ' by sorting and selecting from the beginning of the list  
        Dim filesByLengDesc = From file In fileList _  
                              Let filelength = GetFileLength(file) _  
                              Where filelength > 0 _  
                              Order By filelength Descending _  
                              Select file  
  
        Dim longestFile = filesByLengDesc.First  
  
        Console.WriteLine("The largest file under {0} is {1} with a length of {2} bytes", _  
                          root, longestFile.FullName, longestFile.Length)  
  
        Dim smallestFile = filesByLengDesc.Last  
  
        Console.WriteLine("The smallest file under {0} is {1} with a length of {2} bytes", _  
                                root, smallestFile.FullName, smallestFile.Length)  
  
        ' Return the FileInfos for the 10 largest files  
        ' Based on a previous query, but nothing is executed  
        ' until the For Each statement below.  
        Dim tenLargest = From file In filesByLengDesc Take 10  
  
        Console.WriteLine("The 10 largest files under {0} are:", root)  
  
        For Each fi As System.IO.FileInfo In tenLargest  
            Console.WriteLine("{0}: {1} bytes", fi.FullName, fi.Length)  
        Next  
  
        ' Group files according to their size,  
        ' leaving out the ones under 200K  
        Dim sizeGroups = From file As System.IO.FileInfo In fileList _  
                         Where file.Length > 0 _  
                         Let groupLength = file.Length / 100000 _  
                         Group file By groupLength Into fileGroup = Group _  
                         Where groupLength >= 2 _  
                         Order By groupLength Descending  
  
        For Each group In sizeGroups  
            Console.WriteLine(group.groupLength + "00000")  
  
            For Each item As System.IO.FileInfo In group.fileGroup  
                Console.WriteLine("   {0}: {1}", item.Name, item.Length)  
            Next  
        Next  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    ' In this particular case, it is safe to ignore the exception.  
    Function GetFileLength(ByVal fi As System.IO.FileInfo) As Long  
        Dim retval As Long  
        Try  
            retval = fi.Length  
        Catch ex As FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.   
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 Chcete-li vrátit jeden nebo více úplných objektů <xref:System.IO.FileInfo>, musí dotaz nejprve projít každý zdroj dat a pak je seřadit podle hodnoty vlastnosti length. Pak může vrátit jednu z nich nebo sekvenci s největší délkou. Použijte <xref:System.Linq.Enumerable.First%2A> k vrácení prvního prvku v seznamu. Použijte <xref:System.Linq.Enumerable.Take%2A> k vrácení prvního n počtu prvků. Určete sestupné řazení, aby bylo možné umístit nejmenší prvky na začátek seznamu.  
  
 Dotaz, volá do samostatné metodě získat velikost souboru v bajtech, aby bylo možné využívat možné výjimku, která bude vyvolána v případě, kdy byl odstraněn soubor v jiném vlákně v období od <xref:System.IO.FileInfo> objekt byl vytvořen při volání funkce `GetFiles`. I přes objekt <xref:System.IO.FileInfo> již byl vytvořen, výjimka může být způsobena tím, že se objekt <xref:System.IO.FileInfo> pokusí aktualizovat jeho vlastnost <xref:System.IO.FileInfo.Length%2A> pomocí nejaktuálnější velikosti v bajtech, při které je vlastnost poprvé k dispozici. Vložením této operace do bloku try-catch mimo dotaz se řídí pravidlo vyloučení operací v dotazech, které můžou způsobit vedlejší účinky. Obecně je potřeba věnovat velkou péči při využívání výjimek, aby se zajistilo, že aplikace zůstane v neznámém stavu.  
  
## <a name="compile-the-code"></a>Kompilace kódu  
Vytvořte projekt konzolové aplikace Visual Basic s příkazem `Imports` pro obor názvů System. Linq.
  
## <a name="see-also"></a>Viz také:

- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [LINQ a souborové adresáře (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
