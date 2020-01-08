---
title: Dotazování na největší soubor nebo soubory ve stromu adresářů (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 20c8a917-0552-4514-b489-0b8b6a4c3b4c
ms.openlocfilehash: dee501dc8d0cabd718307b45c99ca049ae4250aa
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344556"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a><span data-ttu-id="d3340-102">Dotazování na největší soubor nebo soubory ve stromu adresářů (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d3340-102">How to query for the largest file or files in a directory tree (LINQ) (C#)</span></span>
<span data-ttu-id="d3340-103">Tento příklad ukazuje pět dotazů týkajících se velikosti souboru v bajtech:</span><span class="sxs-lookup"><span data-stu-id="d3340-103">This example shows five queries related to file size in bytes:</span></span>  
  
- <span data-ttu-id="d3340-104">Jak načíst velikost v bajtech pro největší soubor</span><span class="sxs-lookup"><span data-stu-id="d3340-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
- <span data-ttu-id="d3340-105">Jak načíst velikost nejmenšího souboru v bajtech.</span><span class="sxs-lookup"><span data-stu-id="d3340-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
- <span data-ttu-id="d3340-106">Jak načíst největší nebo nejmenší soubor objektu <xref:System.IO.FileInfo> z jedné nebo více složek v zadané kořenové složce.</span><span class="sxs-lookup"><span data-stu-id="d3340-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
- <span data-ttu-id="d3340-107">Jak načíst sekvenci, jako je 10 největších souborů.</span><span class="sxs-lookup"><span data-stu-id="d3340-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
- <span data-ttu-id="d3340-108">Postup při řazení souborů do skupin na základě velikosti jejich souboru v bajtech. soubory, které jsou menší než zadaná velikost, se ignorují.</span><span class="sxs-lookup"><span data-stu-id="d3340-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3340-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="d3340-109">Example</span></span>  
 <span data-ttu-id="d3340-110">Následující příklad obsahuje pět samostatných dotazů, které ukazují, jak zadávat dotazy a seskupovat soubory v závislosti na velikosti souboru v bajtech.</span><span class="sxs-lookup"><span data-stu-id="d3340-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="d3340-111">Tyto příklady lze snadno upravit tak, aby dotaz byly založeny na nějaké jiné vlastnosti objektu <xref:System.IO.FileInfo>.</span><span class="sxs-lookup"><span data-stu-id="d3340-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
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
  
 <span data-ttu-id="d3340-112">Chcete-li vrátit jeden nebo více úplných objektů <xref:System.IO.FileInfo>, musí dotaz nejprve projít každý zdroj dat a pak je seřadit podle hodnoty vlastnosti length.</span><span class="sxs-lookup"><span data-stu-id="d3340-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="d3340-113">Pak může vrátit jednu z nich nebo sekvenci s největší délkou.</span><span class="sxs-lookup"><span data-stu-id="d3340-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="d3340-114">Použijte <xref:System.Linq.Enumerable.First%2A> k vrácení prvního prvku v seznamu.</span><span class="sxs-lookup"><span data-stu-id="d3340-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="d3340-115">Použijte <xref:System.Linq.Enumerable.Take%2A> k vrácení prvního n počtu prvků.</span><span class="sxs-lookup"><span data-stu-id="d3340-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="d3340-116">Určete sestupné řazení, aby bylo možné umístit nejmenší prvky na začátek seznamu.</span><span class="sxs-lookup"><span data-stu-id="d3340-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="d3340-117">Dotaz, volá do samostatné metodě získat velikost souboru v bajtech, aby bylo možné využívat možné výjimku, která bude vyvolána v případě, kdy byl odstraněn soubor v jiném vlákně v období od <xref:System.IO.FileInfo> objekt byl vytvořen při volání funkce `GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="d3340-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="d3340-118">I přes objekt <xref:System.IO.FileInfo> již byl vytvořen, výjimka může být způsobena tím, že se objekt <xref:System.IO.FileInfo> pokusí aktualizovat jeho vlastnost <xref:System.IO.FileInfo.Length%2A> pomocí nejaktuálnější velikosti v bajtech, při které je vlastnost poprvé k dispozici.</span><span class="sxs-lookup"><span data-stu-id="d3340-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="d3340-119">Vložením této operace do bloku try-catch mimo dotaz se řídí pravidlo vyloučení operací v dotazech, které můžou způsobit vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="d3340-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="d3340-120">Obecně je potřeba věnovat velkou péči při využívání výjimek, aby se zajistilo, že aplikace zůstane v neznámém stavu.</span><span class="sxs-lookup"><span data-stu-id="d3340-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d3340-121">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="d3340-121">Compiling the Code</span></span>  
<span data-ttu-id="d3340-122">Vytvořte projekt C# konzolové aplikace s direktivami `using` pro obory názvů System. Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="d3340-122">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
 
## <a name="see-also"></a><span data-ttu-id="d3340-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3340-123">See also</span></span>

- [<span data-ttu-id="d3340-124">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="d3340-124">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="d3340-125">LINQ a souborové adresáře (C#)</span><span class="sxs-lookup"><span data-stu-id="d3340-125">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
