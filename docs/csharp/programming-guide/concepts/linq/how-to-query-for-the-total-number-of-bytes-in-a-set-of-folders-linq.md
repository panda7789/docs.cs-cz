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
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-c"></a><span data-ttu-id="528ca-102">Jak dotazovat na celkový počet bajtů v sadě složek (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="528ca-102">How to query for the total number of bytes in a set of folders (LINQ) (C#)</span></span>
<span data-ttu-id="528ca-103">Tento příklad ukazuje, jak načíst celkový počet bajtů používaných všemi soubory v zadané složce a všech podsložkách.</span><span class="sxs-lookup"><span data-stu-id="528ca-103">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="528ca-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="528ca-104">Example</span></span>  
 <span data-ttu-id="528ca-105">Metoda <xref:System.Linq.Enumerable.Sum%2A> přidá hodnoty všech položek vybraných `select` v klauzuli.</span><span class="sxs-lookup"><span data-stu-id="528ca-105">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="528ca-106">Tento dotaz můžete snadno upravit a načíst největší nebo nejmenší <xref:System.Linq.Enumerable.Min%2A> soubor <xref:System.Linq.Enumerable.Max%2A> v <xref:System.Linq.Enumerable.Sum%2A>zadaném adresářovém stromu voláním metody nebo namísto .</span><span class="sxs-lookup"><span data-stu-id="528ca-106">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
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
  
 <span data-ttu-id="528ca-107">Pokud máte pouze počítat počet bajtů v zadaném adresářovém stromu, můžete to provést efektivněji bez vytvoření dotazu LINQ, který vznikne režie vytváření kolekce seznamu jako zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="528ca-107">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="528ca-108">Užitečnost přístupu LINQ se zvyšuje s dotazem se stává složitější, nebo pokud máte spustit více dotazů proti stejnému zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="528ca-108">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="528ca-109">Dotaz volá samostatnou metodu k získání délky souboru.</span><span class="sxs-lookup"><span data-stu-id="528ca-109">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="528ca-110">Je to proto, aby bylo možné využívat možnou výjimku, která <xref:System.IO.FileInfo> bude vyvolána, pokud `GetFiles`byl soubor odstraněn v jiném vlákně po vytvoření objektu ve volání .</span><span class="sxs-lookup"><span data-stu-id="528ca-110">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="528ca-111">I v <xref:System.IO.FileInfo> případě, že objekt již byl <xref:System.IO.FileInfo> vytvořen, může dojít <xref:System.IO.FileInfo.Length%2A> k výjimce, protože objekt se pokusí aktualizovat svou vlastnost s nejaktuálnější délkou při prvním přístupu k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="528ca-111">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="528ca-112">Umístěním této operace v bloku try-catch mimo dotaz, kód se řídí pravidlem vyhnout se operacím v dotazech, které mohou způsobit vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="528ca-112">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="528ca-113">Obecně je třeba věnovat velkou pozornost při použití výjimky a ujistěte se, že aplikace není ponechána v neznámém stavu.</span><span class="sxs-lookup"><span data-stu-id="528ca-113">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="528ca-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="528ca-114">Compiling the Code</span></span>  
<span data-ttu-id="528ca-115">Vytvořte projekt aplikace konzoly `using` Jazyka C# se direktivami pro obory názvů System.Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="528ca-115">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="528ca-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="528ca-116">See also</span></span>

- [<span data-ttu-id="528ca-117">LINQ na objekty (C#)</span><span class="sxs-lookup"><span data-stu-id="528ca-117">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="528ca-118">Linq a souborové adresáře (C#)</span><span class="sxs-lookup"><span data-stu-id="528ca-118">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
