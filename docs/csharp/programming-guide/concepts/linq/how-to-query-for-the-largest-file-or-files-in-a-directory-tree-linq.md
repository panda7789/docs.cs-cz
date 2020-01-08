---
title: Dotazování na největší soubor nebo soubory ve stromu adresářů (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 20c8a917-0552-4514-b489-0b8b6a4c3b4c
ms.openlocfilehash: dee501dc8d0cabd718307b45c99ca049ae4250aa
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344556"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a>Dotazování na největší soubor nebo soubory ve stromu adresářů (LINQ) (C#)
Tento příklad ukazuje pět dotazů týkajících se velikosti souboru v bajtech:  
  
- Jak načíst velikost v bajtech pro největší soubor  
  
- Jak načíst velikost nejmenšího souboru v bajtech.  
  
- Jak načíst největší nebo nejmenší soubor objektu <xref:System.IO.FileInfo> z jedné nebo více složek v zadané kořenové složce.  
  
- Jak načíst sekvenci, jako je 10 největších souborů.  
  
- Postup při řazení souborů do skupin na základě velikosti jejich souboru v bajtech. soubory, které jsou menší než zadaná velikost, se ignorují.  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje pět samostatných dotazů, které ukazují, jak zadávat dotazy a seskupovat soubory v závislosti na velikosti souboru v bajtech. Tyto příklady lze snadno upravit tak, aby dotaz byly založeny na nějaké jiné vlastnosti objektu <xref:System.IO.FileInfo>.  
  
```csharp  
class QueryBySize  
{  
    static void Main(string[] args)  
    {  
        QueryFilesBySize();  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    private static void QueryFilesBySize()  
    {  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        //Return the size of the largest file  
        long maxSize =  
            (from file in fileList  
             let len = GetFileLength(file)  
             select len)  
             .Max();  
  
        Console.WriteLine("The length of the largest file under {0} is {1}",  
            startFolder, maxSize);  
  
        // Return the FileInfo object for the largest file  
        // by sorting and selecting from beginning of list  
        System.IO.FileInfo longestFile =  
            (from file in fileList  
             let len = GetFileLength(file)  
             where len > 0  
             orderby len descending  
             select file)  
            .First();  
  
        Console.WriteLine("The largest file under {0} is {1} with a length of {2} bytes",  
                            startFolder, longestFile.FullName, longestFile.Length);  
  
        //Return the FileInfo of the smallest file  
        System.IO.FileInfo smallestFile =  
            (from file in fileList  
             let len = GetFileLength(file)  
             where len > 0  
             orderby len ascending  
             select file).First();  
  
        Console.WriteLine("The smallest file under {0} is {1} with a length of {2} bytes",  
                            startFolder, smallestFile.FullName, smallestFile.Length);  
  
        //Return the FileInfos for the 10 largest files  
        // queryTenLargest is an IEnumerable<System.IO.FileInfo>  
        var queryTenLargest =  
            (from file in fileList  
             let len = GetFileLength(file)  
             orderby len descending  
             select file).Take(10);  
  
        Console.WriteLine("The 10 largest files under {0} are:", startFolder);  
  
        foreach (var v in queryTenLargest)  
        {  
            Console.WriteLine("{0}: {1} bytes", v.FullName, v.Length);  
        }  
  
        // Group the files according to their size, leaving out  
        // files that are less than 200000 bytes.   
        var querySizeGroups =  
            from file in fileList  
            let len = GetFileLength(file)  
            where len > 0  
            group file by (len / 100000) into fileGroup  
            where fileGroup.Key >= 2  
            orderby fileGroup.Key descending  
            select fileGroup;  
  
        foreach (var filegroup in querySizeGroups)  
        {  
            Console.WriteLine(filegroup.Key.ToString() + "00000");  
            foreach (var item in filegroup)  
            {  
                Console.WriteLine("\t{0}: {1}", item.Name, item.Length);  
            }  
        }  
    }  
  
    // This method is used to swallow the possible exception  
    // that can be raised when accessing the FileInfo.Length property.  
    // In this particular case, it is safe to swallow the exception.  
    static long GetFileLength(System.IO.FileInfo fi)  
    {  
        long retval;  
        try  
        {  
            retval = fi.Length;  
        }  
        catch (System.IO.FileNotFoundException)  
        {  
            // If a file is no longer present,  
            // just add zero bytes to the total.  
            retval = 0;  
        }  
        return retval;  
    }  
  
}  
```  
  
 Chcete-li vrátit jeden nebo více úplných objektů <xref:System.IO.FileInfo>, musí dotaz nejprve projít každý zdroj dat a pak je seřadit podle hodnoty vlastnosti length. Pak může vrátit jednu z nich nebo sekvenci s největší délkou. Použijte <xref:System.Linq.Enumerable.First%2A> k vrácení prvního prvku v seznamu. Použijte <xref:System.Linq.Enumerable.Take%2A> k vrácení prvního n počtu prvků. Určete sestupné řazení, aby bylo možné umístit nejmenší prvky na začátek seznamu.  
  
 Dotaz, volá do samostatné metodě získat velikost souboru v bajtech, aby bylo možné využívat možné výjimku, která bude vyvolána v případě, kdy byl odstraněn soubor v jiném vlákně v období od <xref:System.IO.FileInfo> objekt byl vytvořen při volání funkce `GetFiles`. I přes objekt <xref:System.IO.FileInfo> již byl vytvořen, výjimka může být způsobena tím, že se objekt <xref:System.IO.FileInfo> pokusí aktualizovat jeho vlastnost <xref:System.IO.FileInfo.Length%2A> pomocí nejaktuálnější velikosti v bajtech, při které je vlastnost poprvé k dispozici. Vložením této operace do bloku try-catch mimo dotaz se řídí pravidlo vyloučení operací v dotazech, které můžou způsobit vedlejší účinky. Obecně je potřeba věnovat velkou péči při využívání výjimek, aby se zajistilo, že aplikace zůstane v neznámém stavu.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
Vytvořte projekt C# konzolové aplikace s direktivami `using` pro obory názvů System. Linq a System.IO.
 
## <a name="see-also"></a>Viz také:

- [LINQ to Objects (C#)](./linq-to-objects.md)
- [LINQ a souborové adresáře (C#)](./linq-and-file-directories.md)
