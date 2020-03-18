---
title: Jak dotazovat na celkový počet bajtů v sadě složek (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: a01bd1d4-133c-4ca2-aa4e-e93e81d6076c
ms.openlocfilehash: c6bfe6bb6d76e7ce8ea8887eef85cd64f2a025df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344821"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-c"></a>Jak dotazovat na celkový počet bajtů v sadě složek (LINQ) (C#)
Tento příklad ukazuje, jak načíst celkový počet bajtů používaných všemi soubory v zadané složce a všech podsložkách.  
  
## <a name="example"></a>Příklad  
 Metoda <xref:System.Linq.Enumerable.Sum%2A> přidá hodnoty všech položek vybraných `select` v klauzuli. Tento dotaz můžete snadno upravit a načíst největší nebo nejmenší <xref:System.Linq.Enumerable.Min%2A> soubor <xref:System.Linq.Enumerable.Max%2A> v <xref:System.Linq.Enumerable.Sum%2A>zadaném adresářovém stromu voláním metody nebo namísto .  
  
```csharp  
class QuerySize  
{  
    public static void Main()  
    {  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\VC#";  
  
        // Take a snapshot of the file system.  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<string> fileList = System.IO.Directory.GetFiles(startFolder, "*.*", System.IO.SearchOption.AllDirectories);  
  
        var fileQuery = from file in fileList  
                        select GetFileLength(file);  
  
        // Cache the results to avoid multiple trips to the file system.  
        long[] fileLengths = fileQuery.ToArray();  
  
        // Return the size of the largest file  
        long largestFile = fileLengths.Max();  
  
        // Return the total number of bytes in all the files under the specified folder.  
        long totalBytes = fileLengths.Sum();  
  
        Console.WriteLine("There are {0} bytes in {1} files under {2}",  
            totalBytes, fileList.Count(), startFolder);  
        Console.WriteLine("The largest files is {0} bytes.", largestFile);  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit.");  
        Console.ReadKey();  
    }  
  
    // This method is used to swallow the possible exception  
    // that can be raised when accessing the System.IO.FileInfo.Length property.  
    static long GetFileLength(string filename)  
    {  
        long retval;  
        try  
        {  
            System.IO.FileInfo fi = new System.IO.FileInfo(filename);  
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
  
 Pokud máte pouze počítat počet bajtů v zadaném adresářovém stromu, můžete to provést efektivněji bez vytvoření dotazu LINQ, který vznikne režie vytváření kolekce seznamu jako zdroj dat. Užitečnost přístupu LINQ se zvyšuje s dotazem se stává složitější, nebo pokud máte spustit více dotazů proti stejnému zdroji dat.  
  
 Dotaz volá samostatnou metodu k získání délky souboru. Je to proto, aby bylo možné využívat možnou výjimku, která <xref:System.IO.FileInfo> bude vyvolána, pokud `GetFiles`byl soubor odstraněn v jiném vlákně po vytvoření objektu ve volání . I v <xref:System.IO.FileInfo> případě, že objekt již byl <xref:System.IO.FileInfo> vytvořen, může dojít <xref:System.IO.FileInfo.Length%2A> k výjimce, protože objekt se pokusí aktualizovat svou vlastnost s nejaktuálnější délkou při prvním přístupu k vlastnosti. Umístěním této operace v bloku try-catch mimo dotaz, kód se řídí pravidlem vyhnout se operacím v dotazech, které mohou způsobit vedlejší účinky. Obecně je třeba věnovat velkou pozornost při použití výjimky a ujistěte se, že aplikace není ponechána v neznámém stavu.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
Vytvořte projekt aplikace konzoly `using` Jazyka C# se direktivami pro obory názvů System.Linq a System.IO.
  
## <a name="see-also"></a>Viz také

- [LINQ na objekty (C#)](./linq-to-objects.md)
- [Linq a souborové adresáře (C#)](./linq-and-file-directories.md)
