---
title: 'Postupy: Dotaz na celkový počet bajtů v sadě složek (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: a01bd1d4-133c-4ca2-aa4e-e93e81d6076c
ms.openlocfilehash: 2db979c10eae9ecc5d4e154ae58248ca95a7cdc3
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592733"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-c"></a>Postupy: Dotaz na celkový počet bajtů v sadě složek (LINQ) (C#)
Tento příklad ukazuje, jak načíst celkový počet bajtů použitých všemi soubory v zadané složce a všech jejích podsložkách.  
  
## <a name="example"></a>Příklad  
 Metoda přidá hodnoty všech položek vybraných `select` v klauzuli. <xref:System.Linq.Enumerable.Sum%2A> Tento dotaz můžete snadno upravit tak, aby získal největší nebo nejmenší soubor v zadaném stromu adresářů voláním <xref:System.Linq.Enumerable.Min%2A> metody nebo <xref:System.Linq.Enumerable.Max%2A> namísto <xref:System.Linq.Enumerable.Sum%2A>.  
  
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
  
 Pokud potřebujete pouze spočítat počet bajtů v zadaném stromové struktuře, můžete to udělat efektivněji bez vytvoření dotazu LINQ, což způsobí režii při vytváření kolekce seznamu jako zdroje dat. Užitečnost přístupu LINQ se zvyšuje, protože dotaz je složitější, nebo když je nutné spustit více dotazů proti stejnému zdroji dat.  
  
 Dotaz volá k samostatné metodě, aby získal délku souboru. Provede to za účelem využívání možné výjimky, která bude vyvolána, pokud byl soubor odstraněn v jiném vlákně poté, <xref:System.IO.FileInfo> co byl objekt vytvořen při `GetFiles`volání. I když <xref:System.IO.FileInfo> již byl objekt vytvořen, výjimka může nastat, <xref:System.IO.FileInfo> protože se objekt pokusí aktualizovat jeho <xref:System.IO.FileInfo.Length%2A> vlastnost s nejaktuálnější délkou při prvním otevření vlastnosti. Vložením této operace do bloku try-catch mimo dotaz kód sleduje pravidlo vyloučení operací v dotazech, které mohou způsobit vedlejší účinky. Obecně platí, že je potřeba věnovat velkou péči, když využijete výjimky, aby se zajistilo, že aplikace zůstane v neznámém stavu.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
Vytvořte projekt C# konzolové aplikace se `using` direktivami pro obory názvů System. Linq a System.IO.
  
## <a name="see-also"></a>Viz také:

- [LINQ to Objects (C#)](./linq-to-objects.md)
- [LINQ a souborové adresáře (C#)](./linq-and-file-directories.md)
