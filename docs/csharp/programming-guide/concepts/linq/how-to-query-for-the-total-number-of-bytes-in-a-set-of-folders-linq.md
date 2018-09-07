---
title: 'Postupy: dotaz pro celkový počet bajtů v sadě složek (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: a01bd1d4-133c-4ca2-aa4e-e93e81d6076c
ms.openlocfilehash: 7a11e30a41ce171d516d3ea00a0e8664efe33520
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44071827"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-c"></a>Postupy: dotaz pro celkový počet bajtů v sadě složek (LINQ) (C#)
Tento příklad ukazuje, jak získat celkový počet bajtů, které používají všechny soubory v zadané složce a jejích podsložkách.  
  
## <a name="example"></a>Příklad  
 <xref:System.Linq.Enumerable.Sum%2A> Metoda přidá hodnoty všechny položky vybrané v `select` klauzuli. Můžete snadno upravit tento dotaz pro načtení souboru největší nebo nejmenší ve stromové struktuře zadaný adresář voláním <xref:System.Linq.Enumerable.Min%2A> nebo <xref:System.Linq.Enumerable.Max%2A> metoda místo <xref:System.Linq.Enumerable.Sum%2A>.  
  
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
  
 Pokud máte jenom spočítat počet bajtů v zadaném adresáři stromu, může to provedete efektivněji bez vytvoření LINQ dotaz, který režijní náklady na vytvoření kolekce seznamu jako zdroj dat s sebou nese náklady. Užitečnost LINQ přístup zvyšuje, jak dotaz stává složitější, nebo když musíte spustit více dotazů na stejném zdroji dat.  
  
 Dotaz zdůrazňuje samostatné metodě získat délku souboru. Aby bylo možné využívat možnou výjimkou, která bude vyvolána, pokud soubor byl odstraněn v jiném vlákně po dělá to <xref:System.IO.FileInfo> objekt byl vytvořen při volání funkce `GetFiles`. I v případě, <xref:System.IO.FileInfo> objekt již byl vytvořen, výjimce může dojít, protože <xref:System.IO.FileInfo> objekt se pokusí obnovit jeho <xref:System.IO.FileInfo.Length%2A> vlastnost s nejaktuálnější délku při prvním přístupu k vlastnosti. Vložením této operace v bloku try-catch mimo dotaz následuje kód pravidlo vyhnout operací v dotazech, které může způsobit vedlejší účinky. Obecně platí musí být věnovat pozornost při využívání výjimky, abyste měli jistotu, že aplikace není ponechán v neznámém stavu.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vytvořit projekt, který cílí na rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na knihovnu System.Core.dll a `using` direktivy pro obory názvů System.Linq a System.IO.  
  
## <a name="see-also"></a>Viz také

- [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
- [LINQ a souborové adresáře (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
