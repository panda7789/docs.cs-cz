---
title: 'Postupy: dotaz na celkový počet bajtů v sadě složek (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
ms.openlocfilehash: 6a6babaf019cdac2298aee6eff55581bf35b2e47
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643546"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a><span data-ttu-id="7720b-102">Postupy: dotaz na celkový počet bajtů v sadě složek (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7720b-102">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="7720b-103">Tento příklad ukazuje, jak načíst celkový počet bajtů použitých tak, že všechny soubory v zadané složce a jejích podsložkách.</span><span class="sxs-lookup"><span data-stu-id="7720b-103">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7720b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="7720b-104">Example</span></span>  
 <span data-ttu-id="7720b-105"><xref:System.Linq.Enumerable.Sum%2A> Metoda přidá hodnoty všech položek vybraných v `select` klauzule.</span><span class="sxs-lookup"><span data-stu-id="7720b-105">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="7720b-106">Můžete snadno upravit tento dotaz pro načtení souboru největších nebo nejmenší ve stromové struktuře zadaný adresář voláním <xref:System.Linq.Enumerable.Min%2A> nebo <xref:System.Linq.Enumerable.Max%2A> metoda místo <xref:System.Linq.Enumerable.Sum%2A>.</span><span class="sxs-lookup"><span data-stu-id="7720b-106">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
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
  
 <span data-ttu-id="7720b-107">Pokud máte pouze počet bajtů ve stromu zadaný adresář, musíte efektivněji bez vytvoření dotazu LINQ, což způsobuje režií při vytváření kolekce seznamu jako zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="7720b-107">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="7720b-108">Použitelnosti tohoto přístupu LINQ zvyšuje dotaz začne být složitější, nebo pokud máte ke spouštění více dotazů na stejném datovém zdroji.</span><span class="sxs-lookup"><span data-stu-id="7720b-108">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="7720b-109">Dotaz se volá samostatné metodě získat délku souboru.</span><span class="sxs-lookup"><span data-stu-id="7720b-109">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="7720b-110">Aby bylo možné využívat možné výjimku, která bude vyvolána, pokud soubor byl odstraněn na jiné vlákno po dělá to <xref:System.IO.FileInfo> objekt byl vytvořen ve volání `GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="7720b-110">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="7720b-111">I když <xref:System.IO.FileInfo> objekt již byl vytvořen, výjimka může dojít, protože <xref:System.IO.FileInfo> objekt se pokusí obnovit jeho <xref:System.IO.FileInfo.Length%2A> vlastnost s nejaktuálnější délka poprvé vlastnost přistupuje.</span><span class="sxs-lookup"><span data-stu-id="7720b-111">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="7720b-112">Try-catch – blok mimo dotaz vložíte tuto operaci, následuje kód pravidla vyloučení operace v dotazech, které můžou způsobit vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="7720b-112">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="7720b-113">Obecně platí musí být přijata pozor při využívat výjimky a ujistěte se, že aplikace není ponecháno v neznámém stavu.</span><span class="sxs-lookup"><span data-stu-id="7720b-113">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7720b-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7720b-114">Compiling the Code</span></span>  
 <span data-ttu-id="7720b-115">Vytvoření projektu, jehož cílem rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na System.Core.dll a `Imports` příkaz pro obor názvů System.Linq.</span><span class="sxs-lookup"><span data-stu-id="7720b-115">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a   `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7720b-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="7720b-116">See Also</span></span>  
 [<span data-ttu-id="7720b-117">LINQ na objekty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7720b-117">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="7720b-118">LINQ a souborové adresáře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7720b-118">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
