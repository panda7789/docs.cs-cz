---
title: 'Postupy: dotazu na duplicitní soubory v adresářovém stromu (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 1ff5562b-0d30-46d1-b426-a04e8f78c840
ms.openlocfilehash: 09ce574c68cbf11c0ee50df663692fd207038758
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43734233"
---
# <a name="how-to-query-for-duplicate-files-in-a-directory-tree-linq-c"></a><span data-ttu-id="8b33e-102">Postupy: dotazu na duplicitní soubory v adresářovém stromu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="8b33e-102">How to: Query for Duplicate Files in a Directory Tree (LINQ) (C#)</span></span>
<span data-ttu-id="8b33e-103">Někdy může nacházet v více složek soubory, které mají stejný název.</span><span class="sxs-lookup"><span data-stu-id="8b33e-103">Sometimes files that have the same name may be located in more than one folder.</span></span> <span data-ttu-id="8b33e-104">Například v instalační složce aplikace Visual Studio, mají několik složek souboru readme.htm.</span><span class="sxs-lookup"><span data-stu-id="8b33e-104">For example, under the Visual Studio installation folder, several folders have a readme.htm file.</span></span> <span data-ttu-id="8b33e-105">Tento příklad ukazuje, jak se dotázat na tyto duplicitní názvy zadané kořenové složce.</span><span class="sxs-lookup"><span data-stu-id="8b33e-105">This example shows how to query for such duplicate file names under a specified root folder.</span></span> <span data-ttu-id="8b33e-106">Druhý příklad ukazuje, jak provádět dotazy pro soubory, jejichž velikost a také odpovídat času vytvoření.</span><span class="sxs-lookup"><span data-stu-id="8b33e-106">The second example shows how to query for files whose size and creation times also match.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b33e-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="8b33e-107">Example</span></span>  
  
```csharp  
class QueryDuplicateFileNames  
{  
    static void Main(string[] args)  
    {  
        // Uncomment QueryDuplicates2 to run that query.  
        QueryDuplicates();  
        // QueryDuplicates2();  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit.");  
        Console.ReadKey();  
    }  
  
    static void QueryDuplicates()  
    {  
        // Change the root drive or folder if necessary  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        // used in WriteLine to keep the lines shorter  
        int charsToSkip = startFolder.Length;  
  
        // var can be used for convenience with groups.  
        var queryDupNames =  
            from file in fileList  
            group file.FullName.Substring(charsToSkip) by file.Name into fileGroup  
            where fileGroup.Count() > 1  
            select fileGroup;  
  
        // Pass the query to a method that will  
        // output one page at a time.  
        PageOutput<string, string>(queryDupNames);  
    }  
  
    // A Group key that can be passed to a separate method.  
    // Override Equals and GetHashCode to define equality for the key.  
    // Override ToString to provide a friendly name for Key.ToString()  
    class PortableKey  
    {  
        public string Name { get; set; }  
        public DateTime CreationTime { get; set; }  
        public long Length { get; set; }  
  
        public override bool Equals(object obj)  
        {  
            PortableKey other = (PortableKey)obj;  
            return other.CreationTime == this.CreationTime &&  
                   other.Length == this.Length &&  
                   other.Name == this.Name;  
        }  
  
        public override int GetHashCode()  
        {  
            string str = String.Format("{0}{1}{2}", this.CreationTime, this.Length, this.Name);  
            return str.GetHashCode();  
        }  
        public override string ToString()  
        {  
            return String.Format("{0} {1} {2}", this.Name, this.Length, this.CreationTime);  
        }  
    }  
    static void QueryDuplicates2()  
    {  
        // Change the root drive or folder if necessary.  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\Common7";  
  
        // Make the lines shorter for the console display  
        int charsToSkip = startFolder.Length;  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        // Note the use of a compound key. Files that match  
        // all three properties belong to the same group.  
        // A named type is used to enable the query to be  
        // passed to another method. Anonymous types can also be used  
        // for composite keys but cannot be passed across method boundaries  
        //   
        var queryDupFiles =  
            from file in fileList  
            group file.FullName.Substring(charsToSkip) by  
                new PortableKey { Name = file.Name, CreationTime = file.CreationTime, Length = file.Length } into fileGroup  
            where fileGroup.Count() > 1  
            select fileGroup;  
  
        var list = queryDupFiles.ToList();  
  
        int i = queryDupFiles.Count();  
  
        PageOutput<PortableKey, string>(queryDupFiles);  
    }  
  
    // A generic method to page the output of the QueryDuplications methods  
    // Here the type of the group must be specified explicitly. "var" cannot  
    // be used in method signatures. This method does not display more than one  
    // group per page.  
    private static void PageOutput<K, V>(IEnumerable<System.Linq.IGrouping<K, V>> groupByExtList)  
    {  
        // Flag to break out of paging loop.  
        bool goAgain = true;  
  
        // "3" = 1 line for extension + 1 for "Press any key" + 1 for input cursor.  
        int numLines = Console.WindowHeight - 3;  
  
        // Iterate through the outer collection of groups.  
        foreach (var filegroup in groupByExtList)  
        {  
            // Start a new extension at the top of a page.  
            int currentLine = 0;  
  
            // Output only as many lines of the current group as will fit in the window.  
            do  
            {  
                Console.Clear();  
                Console.WriteLine("Filename = {0}", filegroup.Key.ToString() == String.Empty ? "[none]" : filegroup.Key.ToString());  
  
                // Get 'numLines' number of items starting at number 'currentLine'.  
                var resultPage = filegroup.Skip(currentLine).Take(numLines);  
  
                //Execute the resultPage query  
                foreach (var fileName in resultPage)  
                {  
                    Console.WriteLine("\t{0}", fileName);  
                }  
  
                // Increment the line counter.  
                currentLine += numLines;  
  
                // Give the user a chance to escape.  
                Console.WriteLine("Press any key to continue or the 'End' key to break...");  
                ConsoleKey key = Console.ReadKey().Key;  
                if (key == ConsoleKey.End)  
                {  
                    goAgain = false;  
                    break;  
                }  
            } while (currentLine < filegroup.Count());  
  
            if (goAgain == false)  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="8b33e-108">První dotaz pomocí jednoduchého klíče k určení shody to vyhledá soubory, které mají stejný název, ale jehož obsah se může lišit.</span><span class="sxs-lookup"><span data-stu-id="8b33e-108">The first query uses a simple key to determine a match; this finds files that have the same name but whose contents might be different.</span></span> <span data-ttu-id="8b33e-109">Druhý dotaz používá složený klíč tak, aby odpovídala tři vlastnosti <xref:System.IO.FileInfo> objektu.</span><span class="sxs-lookup"><span data-stu-id="8b33e-109">The second query uses a compound key to match against three properties of the <xref:System.IO.FileInfo> object.</span></span> <span data-ttu-id="8b33e-110">Tento dotaz je mnohem pravděpodobnější k vyhledání souborů, které mají stejný název a obsah podobné nebo identické.</span><span class="sxs-lookup"><span data-stu-id="8b33e-110">This query is much more likely to find files that have the same name and similar or identical content.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8b33e-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="8b33e-111">Compiling the Code</span></span>  
 <span data-ttu-id="8b33e-112">Vytvořit projekt, který cílí na rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na knihovnu System.Core.dll a `using` direktivy pro obory názvů System.Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="8b33e-112">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b33e-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b33e-113">See Also</span></span>

- [<span data-ttu-id="8b33e-114">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="8b33e-114">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
- [<span data-ttu-id="8b33e-115">LINQ a souborové adresáře (C#)</span><span class="sxs-lookup"><span data-stu-id="8b33e-115">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
