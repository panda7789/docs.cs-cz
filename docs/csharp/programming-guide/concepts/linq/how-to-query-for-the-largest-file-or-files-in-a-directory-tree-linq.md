---
title: 'Postupy: Dotazování na největší soubor či soubory v adresářovém stromu (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 20c8a917-0552-4514-b489-0b8b6a4c3b4c
ms.openlocfilehash: 20453c754c792d4f5c59fde481e1fec56dcd0e09
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61702279"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a><span data-ttu-id="e5029-102">Postupy: Dotazování na největší soubor či soubory v adresářovém stromu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e5029-102">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (C#)</span></span>
<span data-ttu-id="e5029-103">Tento příklad ukazuje pět dotazů souvisejících s velikostí souboru v bajtech:</span><span class="sxs-lookup"><span data-stu-id="e5029-103">This example shows five queries related to file size in bytes:</span></span>  
  
- <span data-ttu-id="e5029-104">Jak načíst velikost v bajtech největší soubor.</span><span class="sxs-lookup"><span data-stu-id="e5029-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
- <span data-ttu-id="e5029-105">Jak načíst velikost v bajtech nejmenší souboru.</span><span class="sxs-lookup"><span data-stu-id="e5029-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
- <span data-ttu-id="e5029-106">Jak načíst <xref:System.IO.FileInfo> největší nebo nejmenší soubor objektu z jedné nebo více složek v rámci zadané kořenové složky.</span><span class="sxs-lookup"><span data-stu-id="e5029-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
- <span data-ttu-id="e5029-107">Jak získávají pořadí, jako je například 10 největších souborů.</span><span class="sxs-lookup"><span data-stu-id="e5029-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
- <span data-ttu-id="e5029-108">Způsob řazení souborů do skupiny založené na jejich velikost souboru v bajtech, soubory, které jsou menší než zadaná velikost se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="e5029-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5029-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="e5029-109">Example</span></span>  
 <span data-ttu-id="e5029-110">Následující příklad obsahuje pět samostatné dotazy, které ukazují, jak zadávat dotazy na soubory a skupin, v závislosti na jejich velikost souboru v bajtech.</span><span class="sxs-lookup"><span data-stu-id="e5029-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="e5029-111">Můžete snadno upravit tyto příklady na základní dotaz na některé jiné vlastnosti <xref:System.IO.FileInfo> objektu.</span><span class="sxs-lookup"><span data-stu-id="e5029-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
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
  
 <span data-ttu-id="e5029-112">K vrácení jednoho nebo více dokončení <xref:System.IO.FileInfo> objekty, dotaz musí nejprve zkontrolujte každé z nich data zdroje a pak je můžete seřadit podle hodnoty jejich vlastnost Length.</span><span class="sxs-lookup"><span data-stu-id="e5029-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="e5029-113">Potom může vrátit jeden nebo pořadí s největší délky.</span><span class="sxs-lookup"><span data-stu-id="e5029-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="e5029-114">Použití <xref:System.Linq.Enumerable.First%2A> se vraťte první prvek v seznamu.</span><span class="sxs-lookup"><span data-stu-id="e5029-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="e5029-115">Použití <xref:System.Linq.Enumerable.Take%2A> vrátit prvních n počet prvků.</span><span class="sxs-lookup"><span data-stu-id="e5029-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="e5029-116">Zadejte sestupně umístit nejmenší prvky na začátek seznamu.</span><span class="sxs-lookup"><span data-stu-id="e5029-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="e5029-117">Dotaz, volá do samostatné metodě získat velikost souboru v bajtech, aby bylo možné využívat možné výjimku, která bude vyvolána v případě, kdy byl odstraněn soubor v jiném vlákně v období od <xref:System.IO.FileInfo> objekt byl vytvořen při volání funkce `GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="e5029-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="e5029-118">I přes <xref:System.IO.FileInfo> objekt již byl vytvořen, výjimce může dojít, protože <xref:System.IO.FileInfo> objekt se pokusí obnovit jeho <xref:System.IO.FileInfo.Length%2A> vlastnost pomocí aktuální velikost v bajtech při prvním přístupu k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e5029-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="e5029-119">Vložením této operace v bloku try-catch mimo dotazu, budeme postupovat podle pravidla vyloučení operací v dotazech, které může způsobit vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="e5029-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="e5029-120">Obecně platí musí být věnovat pozornost při využívání výjimky, abyste měli jistotu, že aplikace není ponechán v neznámém stavu.</span><span class="sxs-lookup"><span data-stu-id="e5029-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e5029-121">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e5029-121">Compiling the Code</span></span>  
 <span data-ttu-id="e5029-122">Vytvořit projekt, který cílí na rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na knihovnu System.Core.dll a `using` direktivy pro obory názvů System.Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="e5029-122">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5029-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5029-123">See also</span></span>

- [<span data-ttu-id="e5029-124">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="e5029-124">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="e5029-125">LINQ a souborové adresáře (C#)</span><span class="sxs-lookup"><span data-stu-id="e5029-125">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
