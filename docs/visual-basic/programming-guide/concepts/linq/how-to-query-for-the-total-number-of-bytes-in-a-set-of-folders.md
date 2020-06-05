---
title: 'Postupy: Vytvoření dotazu na celkový počet bajtů v sadě složek (LINQ)'
ms.date: 07/20/2015
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
ms.openlocfilehash: c6490c8863b5762b0b487c6f3f3b2809e16d6519
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397931"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a><span data-ttu-id="8fbc9-102">Postupy: vytvoření dotazu na celkový počet bajtů v sadě složek (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8fbc9-102">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="8fbc9-103">Tento příklad ukazuje, jak načíst celkový počet bajtů použitých všemi soubory v zadané složce a všech jejích podsložkách.</span><span class="sxs-lookup"><span data-stu-id="8fbc9-103">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fbc9-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="8fbc9-104">Example</span></span>  
 <span data-ttu-id="8fbc9-105"><xref:System.Linq.Enumerable.Sum%2A>Metoda přidá hodnoty všech položek vybraných v `select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="8fbc9-105">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="8fbc9-106">Tento dotaz můžete snadno upravit tak, aby získal největší nebo nejmenší soubor v zadaném stromu adresářů voláním <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.Max%2A> metody nebo namísto <xref:System.Linq.Enumerable.Sum%2A> .</span><span class="sxs-lookup"><span data-stu-id="8fbc9-106">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
```vb  
Module QueryTotalBytes  
    Sub Main()  
  
        ' Change the drive\path if necessary.  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0\VB"  
  
        'Take a snapshot of the folder contents.  
        ' This method assumes that the application has discovery permissions  
        ' for all folders under the specified path.  
        Dim fileList = My.Computer.FileSystem.GetFiles _  
                  (root, FileIO.SearchOption.SearchAllSubDirectories, "*.*")  
  
        Dim fileQuery = From file In fileList _  
                        Select GetFileLength(file)  
  
        ' Force execution and cache the results to avoid multiple trips to the file system.  
        Dim fileLengths = fileQuery.ToArray()  
  
        ' Find the largest file  
        Dim maxSize = Aggregate aFile In fileLengths Into Max()  
  
        ' Find the total number of bytes  
        Dim totalBytes = Aggregate aFile In fileLengths Into Sum()  
  
        Console.WriteLine("The largest file is " & maxSize & " bytes")  
        Console.WriteLine("There are " & totalBytes & " total bytes in " & _  
                          fileList.Count & " files under " & root)  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    Function GetFileLength(ByVal filename As String) As Long  
        Dim retval As Long  
        Try  
            Dim fi As New System.IO.FileInfo(filename)  
            retval = fi.Length  
        Catch ex As System.IO.FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 <span data-ttu-id="8fbc9-107">Pokud potřebujete pouze spočítat počet bajtů v zadaném stromové struktuře, můžete to udělat efektivněji bez vytvoření dotazu LINQ, což způsobí režii při vytváření kolekce seznamu jako zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="8fbc9-107">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="8fbc9-108">Užitečnost přístupu LINQ se zvyšuje, protože dotaz je složitější, nebo když je nutné spustit více dotazů proti stejnému zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="8fbc9-108">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="8fbc9-109">Dotaz volá k samostatné metodě, aby získal délku souboru.</span><span class="sxs-lookup"><span data-stu-id="8fbc9-109">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="8fbc9-110">Provede to za účelem využívání možné výjimky, která bude vyvolána, pokud byl soubor odstraněn v jiném vlákně poté, co <xref:System.IO.FileInfo> byl objekt vytvořen při volání `GetFiles` .</span><span class="sxs-lookup"><span data-stu-id="8fbc9-110">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="8fbc9-111">I když <xref:System.IO.FileInfo> již byl objekt vytvořen, výjimka může nastat, protože se <xref:System.IO.FileInfo> objekt pokusí aktualizovat jeho <xref:System.IO.FileInfo.Length%2A> vlastnost s nejaktuálnější délkou při prvním otevření vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8fbc9-111">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="8fbc9-112">Vložením této operace do bloku try-catch mimo dotaz kód sleduje pravidlo vyloučení operací v dotazech, které mohou způsobit vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="8fbc9-112">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="8fbc9-113">Obecně platí, že je potřeba věnovat velkou péči, když využijete výjimky, aby se zajistilo, že aplikace zůstane v neznámém stavu.</span><span class="sxs-lookup"><span data-stu-id="8fbc9-113">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="8fbc9-114">Kompilovat kód</span><span class="sxs-lookup"><span data-stu-id="8fbc9-114">Compile the code</span></span>  
<span data-ttu-id="8fbc9-115">Vytvořte projekt konzolové aplikace Visual Basic s `Imports` příkazem pro obor názvů System. Linq.</span><span class="sxs-lookup"><span data-stu-id="8fbc9-115">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8fbc9-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="8fbc9-116">See also</span></span>

- [<span data-ttu-id="8fbc9-117">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8fbc9-117">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
- [<span data-ttu-id="8fbc9-118">LINQ a souborové adresáře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8fbc9-118">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
