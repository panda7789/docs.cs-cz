---
title: 'Postupy: dotaz na celkový počet bajtů v sadě složek (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: a01bd1d4-133c-4ca2-aa4e-e93e81d6076c
ms.openlocfilehash: 6a02f5a645c545883c05fc52448d10e3d835d615
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-c"></a>Postupy: dotaz na celkový počet bajtů v sadě složek (LINQ) (C#)
Tento příklad ukazuje, jak načíst celkový počet bajtů použitých tak, že všechny soubory v zadané složce a jejích podsložkách.  
  
## <a name="example"></a>Příklad  
 <xref:System.Linq.Enumerable.Sum%2A> Metoda přidá hodnoty všech položek vybraných v `select` klauzule. Můžete snadno upravit tento dotaz pro načtení souboru největších nebo nejmenší ve stromové struktuře zadaný adresář voláním <xref:System.Linq.Enumerable.Min%2A> nebo <xref:System.Linq.Enumerable.Max%2A> metoda místo <xref:System.Linq.Enumerable.Sum%2A>.  
  
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
  
 Pokud máte pouze počet bajtů ve stromu zadaný adresář, musíte efektivněji bez vytvoření dotazu LINQ, což způsobuje režií při vytváření kolekce seznamu jako zdroj dat. Použitelnosti tohoto přístupu LINQ zvyšuje dotaz začne být složitější, nebo pokud máte ke spouštění více dotazů na stejném datovém zdroji.  
  
 Dotaz se volá samostatné metodě získat délku souboru. Aby bylo možné využívat možné výjimku, která bude vyvolána, pokud soubor byl odstraněn na jiné vlákno po dělá to <xref:System.IO.FileInfo> objekt byl vytvořen ve volání `GetFiles`. I když <xref:System.IO.FileInfo> objekt již byl vytvořen, výjimka může dojít, protože <xref:System.IO.FileInfo> objekt se pokusí obnovit jeho <xref:System.IO.FileInfo.Length%2A> vlastnost s nejaktuálnější délka poprvé vlastnost přistupuje. Try-catch – blok mimo dotaz vložíte tuto operaci, následuje kód pravidla vyloučení operace v dotazech, které můžou způsobit vedlejší účinky. Obecně platí musí být přijata pozor při využívat výjimky a ujistěte se, že aplikace není ponecháno v neznámém stavu.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vytvoření projektu, jehož cílem rozhraní .NET Framework verze 3.5 nebo vyšší, s odkazem na System.Core.dll a `using` direktivy pro obory názvů System.Linq a System.IO.  
  
## <a name="see-also"></a>Viz také  
 [LINQ na objekty (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
 [LINQ a souborové adresáře (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
