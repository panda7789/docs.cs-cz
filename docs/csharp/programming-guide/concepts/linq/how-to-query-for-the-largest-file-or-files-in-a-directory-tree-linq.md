---
title: Jak dotazovat na největší soubor nebo soubory ve stromu adresářů (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 20c8a917-0552-4514-b489-0b8b6a4c3b4c
ms.openlocfilehash: ed7d610bd292be4062db89f3c94af280e851141f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168762"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a>Jak dotazovat na největší soubor nebo soubory ve stromu adresářů (LINQ) (C#)
Tento příklad ukazuje pět dotazů souvisejících s velikostí souboru v bajtech:  
  
- Jak načíst velikost v bajtů největšího souboru.  
  
- Jak načíst velikost v bajtů nejmenšího souboru.  
  
- Jak načíst <xref:System.IO.FileInfo> největší nebo nejmenší soubor objektu z jedné nebo více složek v zadané kořenové složce.  
  
- Jak načíst sekvenci, jako je například 10 největších souborů.  
  
- Jak seřadit soubory do skupin na základě jejich velikosti souboru v bajtů, ignoruje soubory, které jsou menší než zadaná velikost.  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje pět samostatných dotazů, které ukazují, jak dotazovat a seskupit soubory, v závislosti na jejich velikosti souboru v bajtů. Tyto příklady můžete snadno upravit a založit dotaz <xref:System.IO.FileInfo> na jiné vlastnosti objektu.  
  
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
  
 Chcete-li vrátit <xref:System.IO.FileInfo> jeden nebo více úplných objektů, dotaz nejprve musí prozkoumat každý z nich ve zdroji dat a pak je seřadit podle hodnoty jejich Length vlastnost. Pak může vrátit jeden nebo sekvence s největší délky. Slouží <xref:System.Linq.Enumerable.First%2A> k vrácení prvníprvek v seznamu. Slouží <xref:System.Linq.Enumerable.Take%2A> k vrácení první n počet prvků. Určete sestupné pořadí řazení, chcete-li umístit nejmenší prvky na začátek seznamu.  
  
 Dotaz volá samostatnou metodu k získání velikosti souboru v bajtů s cílem spotřebovat možnou výjimku, která bude vyvolána v případě, kdy byl soubor odstraněn v jiném vlákně v časovém období od vytvoření objektu <xref:System.IO.FileInfo> ve volání `GetFiles`. I prostřednictvím objektu <xref:System.IO.FileInfo> již byla vytvořena, <xref:System.IO.FileInfo> může dojít k <xref:System.IO.FileInfo.Length%2A> výjimce, protože objekt se pokusí aktualizovat svou vlastnost pomocí nejaktuálnější velikost v bajtů při prvním přístupu k vlastnosti. Umístěním této operace v try-catch bloku mimo dotaz, budeme dodržovat pravidlo vyhnout se operacím v dotazech, které mohou způsobit vedlejší účinky. Obecně je třeba věnovat velkou pozornost při využívání výjimek, abyste se ujistili, že aplikace není ponechána v neznámém stavu.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
Vytvořte projekt aplikace konzoly `using` Jazyka C# se direktivami pro obory názvů System.Linq a System.IO.

## <a name="see-also"></a>Viz také

- [LINQ na objekty (C#)](./linq-to-objects.md)
- [Linq a souborové adresáře (C#)](./linq-and-file-directories.md)
