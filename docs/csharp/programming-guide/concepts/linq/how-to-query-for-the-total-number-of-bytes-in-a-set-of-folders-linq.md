---
title: 'Postupy: dotaz na celkový počet bajtů v sadě složek (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: a01bd1d4-133c-4ca2-aa4e-e93e81d6076c
ms.openlocfilehash: 6a02f5a645c545883c05fc52448d10e3d835d615
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322468"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-c"></a><span data-ttu-id="ee590-102">Postupy: dotaz na celkový počet bajtů v sadě složek (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ee590-102">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (C#)</span></span>
<span data-ttu-id="ee590-103">Tento příklad ukazuje, jak načíst celkový počet bajtů použitých tak, že všechny soubory v zadané složce a jejích podsložkách.</span><span class="sxs-lookup"><span data-stu-id="ee590-103">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee590-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ee590-104">Example</span></span>  
 <span data-ttu-id="ee590-105"><xref:System.Linq.Enumerable.Sum%2A> Metoda přidá hodnoty všech položek vybraných v `select` klauzule.</span><span class="sxs-lookup"><span data-stu-id="ee590-105">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="ee590-106">Můžete snadno upravit tento dotaz pro načtení souboru největších nebo nejmenší ve stromové struktuře zadaný adresář voláním <xref:System.Linq.Enumerable.Min%2A> nebo <xref:System.Linq.Enumerable.Max%2A> metoda místo <xref:System.Linq.Enumerable.Sum%2A>.</span><span class="sxs-lookup"><span data-stu-id="ee590-106">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
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
  
 <span data-ttu-id="ee590-107">Pokud máte pouze počet bajtů ve stromu zadaný adresář, musíte efektivněji bez vytvoření dotazu LINQ, což způsobuje režií při vytváření kolekce seznamu jako zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="ee590-107">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="ee590-108">Použitelnosti tohoto přístupu LINQ zvyšuje dotaz začne být složitější, nebo pokud máte ke spouštění více dotazů na stejném datovém zdroji.</span><span class="sxs-lookup"><span data-stu-id="ee590-108">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="ee590-109">Dotaz se volá samostatné metodě získat délku souboru.</span><span class="sxs-lookup"><span data-stu-id="ee590-109">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="ee590-110">Aby bylo možné využívat možné výjimku, která bude vyvolána, pokud soubor byl odstraněn na jiné vlákno po dělá to <xref:System.IO.FileInfo> objekt byl vytvořen ve volání `GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="ee590-110">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="ee590-111">I když <xref:System.IO.FileInfo> objekt již byl vytvořen, výjimka může dojít, protože <xref:System.IO.FileInfo> objekt se pokusí obnovit jeho <xref:System.IO.FileInfo.Length%2A> vlastnost s nejaktuálnější délka poprvé vlastnost přistupuje.</span><span class="sxs-lookup"><span data-stu-id="ee590-111">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="ee590-112">Try-catch – blok mimo dotaz vložíte tuto operaci, následuje kód pravidla vyloučení operace v dotazech, které můžou způsobit vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="ee590-112">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="ee590-113">Obecně platí musí být přijata pozor při využívat výjimky a ujistěte se, že aplikace není ponecháno v neznámém stavu.</span><span class="sxs-lookup"><span data-stu-id="ee590-113">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ee590-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ee590-114">Compiling the Code</span></span>  
 <span data-ttu-id="ee590-115">Vytvoření projektu, jehož cílem rozhraní .NET Framework verze 3.5 nebo vyšší, s odkazem na System.Core.dll a `using` direktivy pro obory názvů System.Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="ee590-115">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to   System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee590-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ee590-116">See Also</span></span>  
 [<span data-ttu-id="ee590-117">LINQ na objekty (C#)</span><span class="sxs-lookup"><span data-stu-id="ee590-117">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="ee590-118">LINQ a souborové adresáře (C#)</span><span class="sxs-lookup"><span data-stu-id="ee590-118">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
