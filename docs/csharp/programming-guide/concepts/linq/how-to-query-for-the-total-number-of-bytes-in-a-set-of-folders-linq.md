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
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-c"></a><span data-ttu-id="f6762-102">Postupy: Dotaz na celkový počet bajtů v sadě složek (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="f6762-102">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (C#)</span></span>
<span data-ttu-id="f6762-103">Tento příklad ukazuje, jak načíst celkový počet bajtů použitých všemi soubory v zadané složce a všech jejích podsložkách.</span><span class="sxs-lookup"><span data-stu-id="f6762-103">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6762-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f6762-104">Example</span></span>  
 <span data-ttu-id="f6762-105">Metoda přidá hodnoty všech položek vybraných `select` v klauzuli. <xref:System.Linq.Enumerable.Sum%2A></span><span class="sxs-lookup"><span data-stu-id="f6762-105">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="f6762-106">Tento dotaz můžete snadno upravit tak, aby získal největší nebo nejmenší soubor v zadaném stromu adresářů voláním <xref:System.Linq.Enumerable.Min%2A> metody nebo <xref:System.Linq.Enumerable.Max%2A> namísto <xref:System.Linq.Enumerable.Sum%2A>.</span><span class="sxs-lookup"><span data-stu-id="f6762-106">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
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
  
 <span data-ttu-id="f6762-107">Pokud potřebujete pouze spočítat počet bajtů v zadaném stromové struktuře, můžete to udělat efektivněji bez vytvoření dotazu LINQ, což způsobí režii při vytváření kolekce seznamu jako zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="f6762-107">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="f6762-108">Užitečnost přístupu LINQ se zvyšuje, protože dotaz je složitější, nebo když je nutné spustit více dotazů proti stejnému zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="f6762-108">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="f6762-109">Dotaz volá k samostatné metodě, aby získal délku souboru.</span><span class="sxs-lookup"><span data-stu-id="f6762-109">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="f6762-110">Provede to za účelem využívání možné výjimky, která bude vyvolána, pokud byl soubor odstraněn v jiném vlákně poté, <xref:System.IO.FileInfo> co byl objekt vytvořen při `GetFiles`volání.</span><span class="sxs-lookup"><span data-stu-id="f6762-110">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="f6762-111">I když <xref:System.IO.FileInfo> již byl objekt vytvořen, výjimka může nastat, <xref:System.IO.FileInfo> protože se objekt pokusí aktualizovat jeho <xref:System.IO.FileInfo.Length%2A> vlastnost s nejaktuálnější délkou při prvním otevření vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f6762-111">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="f6762-112">Vložením této operace do bloku try-catch mimo dotaz kód sleduje pravidlo vyloučení operací v dotazech, které mohou způsobit vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="f6762-112">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="f6762-113">Obecně platí, že je potřeba věnovat velkou péči, když využijete výjimky, aby se zajistilo, že aplikace zůstane v neznámém stavu.</span><span class="sxs-lookup"><span data-stu-id="f6762-113">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f6762-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f6762-114">Compiling the Code</span></span>  
<span data-ttu-id="f6762-115">Vytvořte projekt C# konzolové aplikace se `using` direktivami pro obory názvů System. Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="f6762-115">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f6762-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f6762-116">See also</span></span>

- [<span data-ttu-id="f6762-117">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="f6762-117">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="f6762-118">LINQ a souborové adresáře (C#)</span><span class="sxs-lookup"><span data-stu-id="f6762-118">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
