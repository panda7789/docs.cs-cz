---
title: 'Postupy: Dotaz na největší soubor či soubory v adresářovém stromu (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
ms.openlocfilehash: cc41fb29a765e8824526dcd78c9ecab377f06d22
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724054"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a>Postupy: Dotaz na největší soubor či soubory v adresářovém stromu (LINQ) (Visual Basic)
Tento příklad ukazuje pět dotazů souvisejících s velikostí souboru v bajtech:  
  
-   Jak načíst velikost v bajtech největší soubor.  
  
-   Jak načíst velikost v bajtech nejmenší souboru.  
  
-   Jak načíst <xref:System.IO.FileInfo> největší nebo nejmenší soubor objektu z jedné nebo více složek v rámci zadané kořenové složky.  
  
-   Jak získávají pořadí, jako je například 10 největších souborů.  
  
-   Způsob řazení souborů do skupiny založené na jejich velikost souboru v bajtech, soubory, které jsou menší než zadaná velikost se ignoruje.  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje pět samostatné dotazy, které ukazují, jak zadávat dotazy na soubory a skupin, v závislosti na jejich velikost souboru v bajtech. Můžete snadno upravit tyto příklady na základní dotaz na některé jiné vlastnosti <xref:System.IO.FileInfo> objektu.  
  
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
  
 K vrácení jednoho nebo více dokončení <xref:System.IO.FileInfo> objekty, dotaz musí nejprve zkontrolujte každé z nich data zdroje a pak je můžete seřadit podle hodnoty jejich vlastnost Length. Potom může vrátit jeden nebo pořadí s největší délky. Použití <xref:System.Linq.Enumerable.First%2A> se vraťte první prvek v seznamu. Použití <xref:System.Linq.Enumerable.Take%2A> vrátit prvních n počet prvků. Zadejte sestupně umístit nejmenší prvky na začátek seznamu.  
  
 Dotaz, volá do samostatné metodě získat velikost souboru v bajtech, aby bylo možné využívat možné výjimku, která bude vyvolána v případě, kdy byl odstraněn soubor v jiném vlákně v období od <xref:System.IO.FileInfo> objekt byl vytvořen při volání funkce `GetFiles`. I přes <xref:System.IO.FileInfo> objekt již byl vytvořen, výjimce může dojít, protože <xref:System.IO.FileInfo> objekt se pokusí obnovit jeho <xref:System.IO.FileInfo.Length%2A> vlastnost pomocí aktuální velikost v bajtech při prvním přístupu k vlastnosti. Vložením této operace v bloku try-catch mimo dotazu, budeme postupovat podle pravidla vyloučení operací v dotazech, které může způsobit vedlejší účinky. Obecně platí musí být věnovat pozornost při využívání výjimky, abyste měli jistotu, že aplikace není ponechán v neznámém stavu.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vytvořit projekt, který cílí na rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na knihovnu System.Core.dll a `Imports` příkaz pro obor názvů System.Linq.  
  
## <a name="see-also"></a>Viz také:
- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [LINQ a souborové adresáře (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
