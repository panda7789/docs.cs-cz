---
title: 'Postupy: dotaz pro celkový počet bajtů v sadě složek (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: a01bd1d4-133c-4ca2-aa4e-e93e81d6076c
ms.openlocfilehash: 7a11e30a41ce171d516d3ea00a0e8664efe33520
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43859027"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-c"></a><span data-ttu-id="83d45-102">Postupy: dotaz pro celkový počet bajtů v sadě složek (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="83d45-102">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (C#)</span></span>
<span data-ttu-id="83d45-103">Tento příklad ukazuje, jak získat celkový počet bajtů, které používají všechny soubory v zadané složce a jejích podsložkách.</span><span class="sxs-lookup"><span data-stu-id="83d45-103">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83d45-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="83d45-104">Example</span></span>  
 <span data-ttu-id="83d45-105"><xref:System.Linq.Enumerable.Sum%2A> Metoda přidá hodnoty všechny položky vybrané v `select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="83d45-105">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="83d45-106">Můžete snadno upravit tento dotaz pro načtení souboru největší nebo nejmenší ve stromové struktuře zadaný adresář voláním <xref:System.Linq.Enumerable.Min%2A> nebo <xref:System.Linq.Enumerable.Max%2A> metoda místo <xref:System.Linq.Enumerable.Sum%2A>.</span><span class="sxs-lookup"><span data-stu-id="83d45-106">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
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
  
 <span data-ttu-id="83d45-107">Pokud máte jenom spočítat počet bajtů v zadaném adresáři stromu, může to provedete efektivněji bez vytvoření LINQ dotaz, který režijní náklady na vytvoření kolekce seznamu jako zdroj dat s sebou nese náklady.</span><span class="sxs-lookup"><span data-stu-id="83d45-107">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="83d45-108">Užitečnost LINQ přístup zvyšuje, jak dotaz stává složitější, nebo když musíte spustit více dotazů na stejném zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="83d45-108">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="83d45-109">Dotaz zdůrazňuje samostatné metodě získat délku souboru.</span><span class="sxs-lookup"><span data-stu-id="83d45-109">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="83d45-110">Aby bylo možné využívat možnou výjimkou, která bude vyvolána, pokud soubor byl odstraněn v jiném vlákně po dělá to <xref:System.IO.FileInfo> objekt byl vytvořen při volání funkce `GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="83d45-110">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="83d45-111">I v případě, <xref:System.IO.FileInfo> objekt již byl vytvořen, výjimce může dojít, protože <xref:System.IO.FileInfo> objekt se pokusí obnovit jeho <xref:System.IO.FileInfo.Length%2A> vlastnost s nejaktuálnější délku při prvním přístupu k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="83d45-111">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="83d45-112">Vložením této operace v bloku try-catch mimo dotaz následuje kód pravidlo vyhnout operací v dotazech, které může způsobit vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="83d45-112">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="83d45-113">Obecně platí musí být věnovat pozornost při využívání výjimky, abyste měli jistotu, že aplikace není ponechán v neznámém stavu.</span><span class="sxs-lookup"><span data-stu-id="83d45-113">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="83d45-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="83d45-114">Compiling the Code</span></span>  
 <span data-ttu-id="83d45-115">Vytvořit projekt, který cílí na rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na knihovnu System.Core.dll a `using` direktivy pro obory názvů System.Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="83d45-115">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to   System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83d45-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="83d45-116">See Also</span></span>

- [<span data-ttu-id="83d45-117">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="83d45-117">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
- [<span data-ttu-id="83d45-118">LINQ a souborové adresáře (C#)</span><span class="sxs-lookup"><span data-stu-id="83d45-118">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
