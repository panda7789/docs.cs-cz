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
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a><span data-ttu-id="13bd3-102">Jak dotazovat na největší soubor nebo soubory ve stromu adresářů (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="13bd3-102">How to query for the largest file or files in a directory tree (LINQ) (C#)</span></span>
<span data-ttu-id="13bd3-103">Tento příklad ukazuje pět dotazů souvisejících s velikostí souboru v bajtech:</span><span class="sxs-lookup"><span data-stu-id="13bd3-103">This example shows five queries related to file size in bytes:</span></span>  
  
- <span data-ttu-id="13bd3-104">Jak načíst velikost v bajtů největšího souboru.</span><span class="sxs-lookup"><span data-stu-id="13bd3-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
- <span data-ttu-id="13bd3-105">Jak načíst velikost v bajtů nejmenšího souboru.</span><span class="sxs-lookup"><span data-stu-id="13bd3-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
- <span data-ttu-id="13bd3-106">Jak načíst <xref:System.IO.FileInfo> největší nebo nejmenší soubor objektu z jedné nebo více složek v zadané kořenové složce.</span><span class="sxs-lookup"><span data-stu-id="13bd3-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
- <span data-ttu-id="13bd3-107">Jak načíst sekvenci, jako je například 10 největších souborů.</span><span class="sxs-lookup"><span data-stu-id="13bd3-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
- <span data-ttu-id="13bd3-108">Jak seřadit soubory do skupin na základě jejich velikosti souboru v bajtů, ignoruje soubory, které jsou menší než zadaná velikost.</span><span class="sxs-lookup"><span data-stu-id="13bd3-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13bd3-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="13bd3-109">Example</span></span>  
 <span data-ttu-id="13bd3-110">Následující příklad obsahuje pět samostatných dotazů, které ukazují, jak dotazovat a seskupit soubory, v závislosti na jejich velikosti souboru v bajtů.</span><span class="sxs-lookup"><span data-stu-id="13bd3-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="13bd3-111">Tyto příklady můžete snadno upravit a založit dotaz <xref:System.IO.FileInfo> na jiné vlastnosti objektu.</span><span class="sxs-lookup"><span data-stu-id="13bd3-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
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
  
 <span data-ttu-id="13bd3-112">Chcete-li vrátit <xref:System.IO.FileInfo> jeden nebo více úplných objektů, dotaz nejprve musí prozkoumat každý z nich ve zdroji dat a pak je seřadit podle hodnoty jejich Length vlastnost.</span><span class="sxs-lookup"><span data-stu-id="13bd3-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="13bd3-113">Pak může vrátit jeden nebo sekvence s největší délky.</span><span class="sxs-lookup"><span data-stu-id="13bd3-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="13bd3-114">Slouží <xref:System.Linq.Enumerable.First%2A> k vrácení prvníprvek v seznamu.</span><span class="sxs-lookup"><span data-stu-id="13bd3-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="13bd3-115">Slouží <xref:System.Linq.Enumerable.Take%2A> k vrácení první n počet prvků.</span><span class="sxs-lookup"><span data-stu-id="13bd3-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="13bd3-116">Určete sestupné pořadí řazení, chcete-li umístit nejmenší prvky na začátek seznamu.</span><span class="sxs-lookup"><span data-stu-id="13bd3-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="13bd3-117">Dotaz volá samostatnou metodu k získání velikosti souboru v bajtů s cílem spotřebovat možnou výjimku, která bude vyvolána v případě, kdy byl soubor odstraněn v jiném vlákně v časovém období od vytvoření objektu <xref:System.IO.FileInfo> ve volání `GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="13bd3-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="13bd3-118">I prostřednictvím objektu <xref:System.IO.FileInfo> již byla vytvořena, <xref:System.IO.FileInfo> může dojít k <xref:System.IO.FileInfo.Length%2A> výjimce, protože objekt se pokusí aktualizovat svou vlastnost pomocí nejaktuálnější velikost v bajtů při prvním přístupu k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="13bd3-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="13bd3-119">Umístěním této operace v try-catch bloku mimo dotaz, budeme dodržovat pravidlo vyhnout se operacím v dotazech, které mohou způsobit vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="13bd3-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="13bd3-120">Obecně je třeba věnovat velkou pozornost při využívání výjimek, abyste se ujistili, že aplikace není ponechána v neznámém stavu.</span><span class="sxs-lookup"><span data-stu-id="13bd3-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="13bd3-121">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="13bd3-121">Compiling the Code</span></span>  
<span data-ttu-id="13bd3-122">Vytvořte projekt aplikace konzoly `using` Jazyka C# se direktivami pro obory názvů System.Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="13bd3-122">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>

## <a name="see-also"></a><span data-ttu-id="13bd3-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="13bd3-123">See also</span></span>

- [<span data-ttu-id="13bd3-124">LINQ na objekty (C#)</span><span class="sxs-lookup"><span data-stu-id="13bd3-124">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="13bd3-125">Linq a souborové adresáře (C#)</span><span class="sxs-lookup"><span data-stu-id="13bd3-125">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
