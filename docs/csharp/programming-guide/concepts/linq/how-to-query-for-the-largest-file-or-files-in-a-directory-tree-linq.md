---
title: 'Postupy: dotazování na největší soubor či soubory v adresářovém stromu (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 20c8a917-0552-4514-b489-0b8b6a4c3b4c
ms.openlocfilehash: 004726c4df1af5a12a411d26c4dc36e1836597ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325354"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a><span data-ttu-id="a5b88-102">Postupy: dotazování na největší soubor či soubory v adresářovém stromu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a5b88-102">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (C#)</span></span>
<span data-ttu-id="a5b88-103">Tento příklad ukazuje pět dotazů souvisejících s velikost souboru v bajtech:</span><span class="sxs-lookup"><span data-stu-id="a5b88-103">This example shows five queries related to file size in bytes:</span></span>  
  
-   <span data-ttu-id="a5b88-104">Jak načíst velikost v bajtech na největší soubor.</span><span class="sxs-lookup"><span data-stu-id="a5b88-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
-   <span data-ttu-id="a5b88-105">Jak načíst velikost v bajtech nejmenší soubor.</span><span class="sxs-lookup"><span data-stu-id="a5b88-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
-   <span data-ttu-id="a5b88-106">Jak načíst <xref:System.IO.FileInfo> objekt nejvyšší nebo nejnižší soubor z jednoho nebo více složek v zadané kořenové složce.</span><span class="sxs-lookup"><span data-stu-id="a5b88-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
-   <span data-ttu-id="a5b88-107">Jak načíst pořadí například 10 největší soubory.</span><span class="sxs-lookup"><span data-stu-id="a5b88-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
-   <span data-ttu-id="a5b88-108">Jak pořadí souborů do skupiny založené na jejich velikost souboru v bajtech, soubory, které jsou menší než zadaná velikost je ignorována.</span><span class="sxs-lookup"><span data-stu-id="a5b88-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5b88-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="a5b88-109">Example</span></span>  
 <span data-ttu-id="a5b88-110">Následující příklad obsahuje pět samostatné dotazy, které ukazují, jak dotazovat a skupiny souborů, v závislosti na jejich velikost souboru v bajtech.</span><span class="sxs-lookup"><span data-stu-id="a5b88-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="a5b88-111">Můžete snadno upravit tyto příklady provést dotaz na některé jiné vlastnosti <xref:System.IO.FileInfo> objektu.</span><span class="sxs-lookup"><span data-stu-id="a5b88-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
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
  
 <span data-ttu-id="a5b88-112">Vrátit jeden nebo více dokončení <xref:System.IO.FileInfo> objekty, dotaz musí nejprve zkontrolujte každé z nich v datech zdroje a seřadit je podle hodnoty vlastnosti jejich délka.</span><span class="sxs-lookup"><span data-stu-id="a5b88-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="a5b88-113">Potom může vrátit jeden jeden nebo pořadí s největší délky.</span><span class="sxs-lookup"><span data-stu-id="a5b88-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="a5b88-114">Použití <xref:System.Linq.Enumerable.First%2A> vrátit první prvek v seznamu.</span><span class="sxs-lookup"><span data-stu-id="a5b88-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="a5b88-115">Použití <xref:System.Linq.Enumerable.Take%2A> vrátit první n počet elementů.</span><span class="sxs-lookup"><span data-stu-id="a5b88-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="a5b88-116">Zadejte sestupně uvést nejmenší elementy na začátku seznamu.</span><span class="sxs-lookup"><span data-stu-id="a5b88-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="a5b88-117">Dotaz volá samostatné metodě získat velikost souboru v bajtech, aby bylo možné využívat možné výjimku, která bude vyvolána v případě, kdy byl odstraněn soubor na jiné vlákno v období od <xref:System.IO.FileInfo> objekt byl vytvořen ve volání `GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="a5b88-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="a5b88-118">I přes <xref:System.IO.FileInfo> objekt již byl vytvořen, výjimka může dojít, protože <xref:System.IO.FileInfo> objekt se pokusí obnovit jeho <xref:System.IO.FileInfo.Length%2A> vlastnost pomocí aktuálního velikost v bajtech poprvé vlastnost přistupuje.</span><span class="sxs-lookup"><span data-stu-id="a5b88-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="a5b88-119">Vložením tuto operaci v bloku try-catch – mimo dotaz jsme podle pravidla vyloučení operace v dotazech, které můžou způsobit vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="a5b88-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="a5b88-120">Obecně platí skvělé musí dát pozor při využívání výjimky, abyste měli jistotu, že aplikace není ponecháno v neznámém stavu.</span><span class="sxs-lookup"><span data-stu-id="a5b88-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a5b88-121">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a5b88-121">Compiling the Code</span></span>  
 <span data-ttu-id="a5b88-122">Vytvoření projektu, jehož cílem rozhraní .NET Framework verze 3.5 nebo vyšší, s odkazem na System.Core.dll a `using` direktivy pro obory názvů System.Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="a5b88-122">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5b88-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="a5b88-123">See Also</span></span>  
 [<span data-ttu-id="a5b88-124">LINQ na objekty (C#)</span><span class="sxs-lookup"><span data-stu-id="a5b88-124">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="a5b88-125">LINQ a souborové adresáře (C#)</span><span class="sxs-lookup"><span data-stu-id="a5b88-125">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
