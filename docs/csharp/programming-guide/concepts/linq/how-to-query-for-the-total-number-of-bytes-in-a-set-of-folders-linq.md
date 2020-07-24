---
title: Postup dotazování na celkový počet bajtů v sadě složek (LINQ) (C#)
description: Naučte se, jak pomocí LINQ v jazyce C# najít celkový počet bajtů použitých všemi soubory v zadané složce a jejích podsložkách.
ms.date: 07/20/2015
ms.assetid: a01bd1d4-133c-4ca2-aa4e-e93e81d6076c
ms.openlocfilehash: 964d92a55599d60388f7add937c7f7338f697817
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104287"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-c"></a>Postup dotazování na celkový počet bajtů v sadě složek (LINQ) (C#)
Tento příklad ukazuje, jak načíst celkový počet bajtů použitých všemi soubory v zadané složce a všech jejích podsložkách.  
  
## <a name="example"></a>Příklad  
 <xref:System.Linq.Enumerable.Sum%2A>Metoda přidá hodnoty všech položek vybraných v `select` klauzuli. Tento dotaz můžete snadno upravit tak, aby získal největší nebo nejmenší soubor v zadaném stromu adresářů voláním <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.Max%2A> metody nebo namísto <xref:System.Linq.Enumerable.Sum%2A> .  
  
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
  
 Dotaz volá k samostatné metodě, aby získal délku souboru. Provede to za účelem využívání možné výjimky, která bude vyvolána, pokud byl soubor odstraněn v jiném vlákně poté, co <xref:System.IO.FileInfo> byl objekt vytvořen při volání `GetFiles` . I když <xref:System.IO.FileInfo> již byl objekt vytvořen, výjimka může nastat, protože se <xref:System.IO.FileInfo> objekt pokusí aktualizovat jeho <xref:System.IO.FileInfo.Length%2A> vlastnost s nejaktuálnější délkou při prvním otevření vlastnosti. Vložením této operace do bloku try-catch mimo dotaz kód sleduje pravidlo vyloučení operací v dotazech, které mohou způsobit vedlejší účinky. Obecně platí, že je potřeba věnovat velkou péči, když využijete výjimky, aby se zajistilo, že aplikace zůstane v neznámém stavu.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
Vytvořte projekt konzolové aplikace v jazyce C# se `using` direktivami pro obory názvů System. Linq a System.IO.
  
## <a name="see-also"></a>Viz také

- [LINQ to Objects (C#)](./linq-to-objects.md)
- [LINQ a souborové adresáře (C#)](./linq-and-file-directories.md)
