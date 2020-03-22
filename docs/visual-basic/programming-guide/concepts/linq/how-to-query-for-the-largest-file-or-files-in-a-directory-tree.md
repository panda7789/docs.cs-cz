---
title: 'Postupy: Vytvoření dotazu na největší soubor či soubory v adresářovém stromu (LINQ)'
ms.date: 07/20/2015
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
ms.openlocfilehash: 723a42e79f1def171a08b28986049ffa04945fc4
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266986"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a>Postup: Dotaz na největší soubor nebo soubory ve stromu adresářů (LINQ) (Visual Basic)
Tento příklad ukazuje pět dotazů souvisejících s velikostí souboru v bajtech:  
  
- Jak načíst velikost v bajtů největšího souboru.  
  
- Jak načíst velikost v bajtů nejmenšího souboru.  
  
- Jak načíst <xref:System.IO.FileInfo> největší nebo nejmenší soubor objektu z jedné nebo více složek v zadané kořenové složce.  
  
- Jak načíst sekvenci, jako je například 10 největších souborů.  
  
- Jak seřadit soubory do skupin na základě jejich velikosti souboru v bajtů, ignoruje soubory, které jsou menší než zadaná velikost.  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje pět samostatných dotazů, které ukazují, jak dotazovat a seskupit soubory, v závislosti na jejich velikosti souboru v bajtů. Tyto příklady můžete snadno upravit a založit dotaz <xref:System.IO.FileInfo> na jiné vlastnosti objektu.  
  
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
  
 Chcete-li vrátit <xref:System.IO.FileInfo> jeden nebo více úplných objektů, dotaz nejprve musí prozkoumat každý z nich ve zdroji dat a pak je seřadit podle hodnoty jejich Length vlastnost. Pak může vrátit jeden nebo sekvence s největší délky. Slouží <xref:System.Linq.Enumerable.First%2A> k vrácení prvníprvek v seznamu. Slouží <xref:System.Linq.Enumerable.Take%2A> k vrácení první n počet prvků. Určete sestupné pořadí řazení, chcete-li umístit nejmenší prvky na začátek seznamu.  
  
 Dotaz volá samostatnou metodu k získání velikosti souboru v bajtů s cílem spotřebovat možnou výjimku, která bude vyvolána v případě, kdy byl soubor odstraněn v jiném vlákně v časovém období od vytvoření objektu <xref:System.IO.FileInfo> ve volání `GetFiles`. I prostřednictvím objektu <xref:System.IO.FileInfo> již byla vytvořena, <xref:System.IO.FileInfo> může dojít k <xref:System.IO.FileInfo.Length%2A> výjimce, protože objekt se pokusí aktualizovat svou vlastnost pomocí nejaktuálnější velikost v bajtů při prvním přístupu k vlastnosti. Umístěním této operace v try-catch bloku mimo dotaz, budeme dodržovat pravidlo vyhnout se operacím v dotazech, které mohou způsobit vedlejší účinky. Obecně je třeba věnovat velkou pozornost při využívání výjimek, abyste se ujistili, že aplikace není ponechána v neznámém stavu.  
  
## <a name="compile-the-code"></a>Kompilace kódu  
Vytvořte projekt aplikace konzoly `Imports` jazyka s příkazem pro obor názvů System.Linq.
  
## <a name="see-also"></a>Viz také

- [LINQ na objekty (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [Linq a adresáře souborů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
