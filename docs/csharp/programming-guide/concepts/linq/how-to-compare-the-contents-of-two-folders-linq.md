---
title: 'Postupy: Porovnání obsahu dvou složek (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: c7c4870e-c500-4de3-afa4-2c8e07f510e6
ms.openlocfilehash: c6a44070e251a1521e7ea94c47a3c0c9360df1b5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543039"
---
# <a name="how-to-compare-the-contents-of-two-folders-linq-c"></a><span data-ttu-id="ce983-102">Postupy: Porovnání obsahu dvou složek (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ce983-102">How to: Compare the Contents of Two Folders (LINQ) (C#)</span></span>
<span data-ttu-id="ce983-103">Tento příklad ukazuje tři způsoby, jak porovnat dvě výpisu souborů zobrazuje:</span><span class="sxs-lookup"><span data-stu-id="ce983-103">This example demonstrates three ways to compare two file listings:</span></span>  
  
-   <span data-ttu-id="ce983-104">Pomocí dotazu na logickou hodnotu, která určuje, zda dva seznamy souborů jsou identické.</span><span class="sxs-lookup"><span data-stu-id="ce983-104">By querying for a Boolean value that specifies whether the two file lists are identical.</span></span>  
  
-   <span data-ttu-id="ce983-105">Pomocí dotazu pro je určena průsečíkem načíst soubory, které jsou v obě složky.</span><span class="sxs-lookup"><span data-stu-id="ce983-105">By querying for the intersection to retrieve the files that are in both folders.</span></span>  
  
-   <span data-ttu-id="ce983-106">Pomocí dotazu pro množinových rozdílů načíst soubory, které jsou v jedné složce, ale nikoli u druhého.</span><span class="sxs-lookup"><span data-stu-id="ce983-106">By querying for the set difference to retrieve the files that are in one folder but not the other.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ce983-107">Techniky je znázorněno zde mohou být přizpůsobeny pro porovnání sekvence objektů libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="ce983-107">The techniques shown here can be adapted to compare sequences of objects of any type.</span></span>  
  
 <span data-ttu-id="ce983-108">`FileComparer` Třídy je vidět tady ukazuje, jak použít vlastní porovnávací metody třídy společně s standardní operátory dotazu.</span><span class="sxs-lookup"><span data-stu-id="ce983-108">The `FileComparer` class shown here demonstrates how to use a custom comparer class together with the Standard Query Operators.</span></span> <span data-ttu-id="ce983-109">Třída není určena pro použití ve scénářích reálného světa.</span><span class="sxs-lookup"><span data-stu-id="ce983-109">The class is not intended for use in real-world scenarios.</span></span> <span data-ttu-id="ce983-110">Právě používá název a délku v bajtech každého souboru k určení, zda jsou identické obsahu jednotlivých složek, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="ce983-110">It just uses the name and length in bytes of each file to determine whether the contents of each folder are identical or not.</span></span> <span data-ttu-id="ce983-111">Ve skutečném scénáři byste měli upravit toto porovnávání provádění přísnější kontroly rovnosti.</span><span class="sxs-lookup"><span data-stu-id="ce983-111">In a real-world scenario, you should modify this comparer to perform a more rigorous equality check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce983-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce983-112">Example</span></span>  
  
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
  
            if (queryCommonFiles.Count() > 0)  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="ce983-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ce983-113">Compiling the Code</span></span>  
 <span data-ttu-id="ce983-114">Vytvořit projekt, který cílí na rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na knihovnu System.Core.dll a `using` direktivy pro obory názvů System.Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="ce983-114">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce983-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ce983-115">See also</span></span>

- [<span data-ttu-id="ce983-116">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="ce983-116">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="ce983-117">LINQ a souborové adresáře (C#)</span><span class="sxs-lookup"><span data-stu-id="ce983-117">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
