---
title: Postup porovnání obsahu dvou složek (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: c7c4870e-c500-4de3-afa4-2c8e07f510e6
ms.openlocfilehash: 9d46303068f2284415ea50c0514d76c5b2b55780
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346540"
---
# <a name="how-to-compare-the-contents-of-two-folders-linq-c"></a><span data-ttu-id="edebd-102">Postup porovnání obsahu dvou složek (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="edebd-102">How to compare the contents of two folders (LINQ) (C#)</span></span>
<span data-ttu-id="edebd-103">Tento příklad ukazuje tři způsoby, jak porovnat dva seznamy souborů:</span><span class="sxs-lookup"><span data-stu-id="edebd-103">This example demonstrates three ways to compare two file listings:</span></span>  
  
- <span data-ttu-id="edebd-104">Dotazování na logickou hodnotu, která určuje, zda jsou dva seznamy souborů identické.</span><span class="sxs-lookup"><span data-stu-id="edebd-104">By querying for a Boolean value that specifies whether the two file lists are identical.</span></span>  
  
- <span data-ttu-id="edebd-105">Dotazem pro průnik pro načtení souborů, které jsou v obou složkách.</span><span class="sxs-lookup"><span data-stu-id="edebd-105">By querying for the intersection to retrieve the files that are in both folders.</span></span>  
  
- <span data-ttu-id="edebd-106">Pomocí dotazu na nastavený rozdíl, který načte soubory, které jsou v jedné složce, ale ne na druhé.</span><span class="sxs-lookup"><span data-stu-id="edebd-106">By querying for the set difference to retrieve the files that are in one folder but not the other.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="edebd-107">Zde uvedené techniky lze přizpůsobit pro porovnání sekvencí objektů libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="edebd-107">The techniques shown here can be adapted to compare sequences of objects of any type.</span></span>  
  
 <span data-ttu-id="edebd-108">Třída `FileComparer` zobrazená zde ukazuje, jak použít vlastní třídu porovnávače společně se standardními operátory dotazu.</span><span class="sxs-lookup"><span data-stu-id="edebd-108">The `FileComparer` class shown here demonstrates how to use a custom comparer class together with the Standard Query Operators.</span></span> <span data-ttu-id="edebd-109">Třída není určena pro použití ve scénářích reálného světa.</span><span class="sxs-lookup"><span data-stu-id="edebd-109">The class is not intended for use in real-world scenarios.</span></span> <span data-ttu-id="edebd-110">Používá pouze název a délku v bajtech jednotlivých souborů, aby bylo možné určit, zda obsah každé složky je identický nebo nikoli.</span><span class="sxs-lookup"><span data-stu-id="edebd-110">It just uses the name and length in bytes of each file to determine whether the contents of each folder are identical or not.</span></span> <span data-ttu-id="edebd-111">Ve scénáři reálného světa byste tuto porovnávací metodu měli upravit, aby prováděla přísnější kontrolu rovnosti.</span><span class="sxs-lookup"><span data-stu-id="edebd-111">In a real-world scenario, you should modify this comparer to perform a more rigorous equality check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edebd-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="edebd-112">Example</span></span>  
  
```csharp  
namespace QueryCompareTwoDirs  
{  
    class CompareDirs  
    {  
  
        static void Main(string[] args)  
        {  
  
            // Create two identical or different temporary folders   
            // on a local drive and change these file paths.  
            string pathA = @"C:\TestDir";  
            string pathB = @"C:\TestDir2";  
  
            System.IO.DirectoryInfo dir1 = new System.IO.DirectoryInfo(pathA);  
            System.IO.DirectoryInfo dir2 = new System.IO.DirectoryInfo(pathB);  
  
            // Take a snapshot of the file system.  
            IEnumerable<System.IO.FileInfo> list1 = dir1.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
            IEnumerable<System.IO.FileInfo> list2 = dir2.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
            //A custom file comparer defined below  
            FileCompare myFileCompare = new FileCompare();  
  
            // This query determines whether the two folders contain  
            // identical file lists, based on the custom file comparer  
            // that is defined in the FileCompare class.  
            // The query executes immediately because it returns a bool.  
            bool areIdentical = list1.SequenceEqual(list2, myFileCompare);  
  
            if (areIdentical == true)  
            {  
                Console.WriteLine("the two folders are the same");  
            }  
            else  
            {  
                Console.WriteLine("The two folders are not the same");  
            }  
  
            // Find the common files. It produces a sequence and doesn't   
            // execute until the foreach statement.  
            var queryCommonFiles = list1.Intersect(list2, myFileCompare);  
  
            if (queryCommonFiles.Any())  
            {  
                Console.WriteLine("The following files are in both folders:");  
                foreach (var v in queryCommonFiles)  
                {  
                    Console.WriteLine(v.FullName); //shows which items end up in result list  
                }  
            }  
            else  
            {  
                Console.WriteLine("There are no common files in the two folders.");  
            }  
  
            // Find the set difference between the two folders.  
            // For this example we only check one way.  
            var queryList1Only = (from file in list1  
                                  select file).Except(list2, myFileCompare);  
  
            Console.WriteLine("The following files are in list1 but not list2:");  
            foreach (var v in queryList1Only)  
            {  
                Console.WriteLine(v.FullName);  
            }  
  
            // Keep the console window open in debug mode.  
            Console.WriteLine("Press any key to exit.");  
            Console.ReadKey();  
        }  
    }  
  
    // This implementation defines a very simple comparison  
    // between two FileInfo objects. It only compares the name  
    // of the files being compared and their length in bytes.  
    class FileCompare : System.Collections.Generic.IEqualityComparer<System.IO.FileInfo>  
    {  
        public FileCompare() { }  
  
        public bool Equals(System.IO.FileInfo f1, System.IO.FileInfo f2)  
        {  
            return (f1.Name == f2.Name &&  
                    f1.Length == f2.Length);  
        }  
  
        // Return a hash that reflects the comparison criteria. According to the   
        // rules for IEqualityComparer<T>, if Equals is true, then the hash codes must  
        // also be equal. Because equality as defined here is a simple value equality, not  
        // reference identity, it is possible that two or more objects will produce the same  
        // hash code.  
        public int GetHashCode(System.IO.FileInfo fi)  
        {  
            string s = $"{fi.Name}{fi.Length}";
            return s.GetHashCode();  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="edebd-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="edebd-113">Compiling the Code</span></span>  
 <span data-ttu-id="edebd-114">Vytvořte projekt C# konzolové aplikace s direktivami `using` pro obory názvů System. Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="edebd-114">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edebd-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="edebd-115">See also</span></span>

- [<span data-ttu-id="edebd-116">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="edebd-116">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="edebd-117">LINQ a souborové adresáře (C#)</span><span class="sxs-lookup"><span data-stu-id="edebd-117">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
