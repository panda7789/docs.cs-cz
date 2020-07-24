---
title: Dotazování na největší soubor nebo soubory ve stromu adresářů (LINQ) (C#)
description: Tento příklad v jazyce C# ukazuje pět dotazů LINQ týkajících se velikosti souboru v bajtech. Můžete je upravit tak, aby se dotazoval na nějaké jiné vlastnosti objektu FileInfo.
ms.date: 07/20/2015
ms.assetid: 20c8a917-0552-4514-b489-0b8b6a4c3b4c
ms.openlocfilehash: c06c6017d6fd1efd6412729c5df63a2b819908a6
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104382"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a>Dotazování na největší soubor nebo soubory ve stromu adresářů (LINQ) (C#)
Tento příklad ukazuje pět dotazů týkajících se velikosti souboru v bajtech:  
  
- Jak načíst velikost v bajtech pro největší soubor  
  
- Jak načíst velikost nejmenšího souboru v bajtech.  
  
- Jak načíst <xref:System.IO.FileInfo> největší nebo nejmenší soubor z jedné nebo více složek v zadané kořenové složce.  
  
- Jak načíst sekvenci, jako je 10 největších souborů.  
  
- Postup při řazení souborů do skupin na základě velikosti jejich souboru v bajtech. soubory, které jsou menší než zadaná velikost, se ignorují.  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje pět samostatných dotazů, které ukazují, jak zadávat dotazy a seskupovat soubory v závislosti na velikosti souboru v bajtech. Tyto příklady lze snadno upravit tak, aby dotaz byly základem pro některé další vlastnosti <xref:System.IO.FileInfo> objektu.  
  
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
  
 Chcete-li vrátit jeden nebo více úplných <xref:System.IO.FileInfo> objektů, dotaz nejprve musí projít každou z nich ve zdroji dat a pak je seřadit podle hodnoty vlastnosti length. Pak může vrátit jednu z nich nebo sekvenci s největší délkou. Slouží <xref:System.Linq.Enumerable.First%2A> k vrácení prvního prvku v seznamu. Slouží <xref:System.Linq.Enumerable.Take%2A> k vrácení prvního n počtu prvků. Určete sestupné řazení, aby bylo možné umístit nejmenší prvky na začátek seznamu.  
  
 Dotaz volá na samostatnou metodu pro získání velikosti souboru v bajtech, aby využívala možnou výjimku, která bude vyvolána v případě, že byl soubor v časovém intervalu odstraněn v jiném vlákně, protože byl <xref:System.IO.FileInfo> objekt vytvořen při volání `GetFiles` . I přes <xref:System.IO.FileInfo> objekt již byl vytvořen, výjimka může být způsobena tím, že se <xref:System.IO.FileInfo> objekt pokusí aktualizovat svou <xref:System.IO.FileInfo.Length%2A> vlastnost pomocí nejaktuálnější velikosti v bajtech při prvním otevření vlastnosti. Vložením této operace do bloku try-catch mimo dotaz se řídí pravidlo vyloučení operací v dotazech, které můžou způsobit vedlejší účinky. Obecně je potřeba věnovat velkou péči při využívání výjimek, aby se zajistilo, že aplikace zůstane v neznámém stavu.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
Vytvořte projekt konzolové aplikace v jazyce C# se `using` direktivami pro obory názvů System. Linq a System.IO.

## <a name="see-also"></a>Viz také

- [LINQ to Objects (C#)](./linq-to-objects.md)
- [LINQ a souborové adresáře (C#)](./linq-and-file-directories.md)
