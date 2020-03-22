---
title: 'Postupy: Vytvoření dotazu na celkový počet bajtů v sadě složek (LINQ)'
ms.date: 07/20/2015
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
ms.openlocfilehash: 25e2c2894d9feccf42ee92bdddd17d8558779e6c
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266973"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a><span data-ttu-id="fe5bb-102">Postup: Dotaz na celkový počet bajtů v sadě složek (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe5bb-102">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="fe5bb-103">Tento příklad ukazuje, jak načíst celkový počet bajtů používaných všemi soubory v zadané složce a všech podsložkách.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-103">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe5bb-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="fe5bb-104">Example</span></span>  
 <span data-ttu-id="fe5bb-105">Metoda <xref:System.Linq.Enumerable.Sum%2A> přidá hodnoty všech položek vybraných `select` v klauzuli.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-105">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="fe5bb-106">Tento dotaz můžete snadno upravit a načíst největší nebo nejmenší <xref:System.Linq.Enumerable.Min%2A> soubor <xref:System.Linq.Enumerable.Max%2A> v <xref:System.Linq.Enumerable.Sum%2A>zadaném adresářovém stromu voláním metody nebo namísto .</span><span class="sxs-lookup"><span data-stu-id="fe5bb-106">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
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
  
 <span data-ttu-id="fe5bb-107">Pokud máte pouze počítat počet bajtů v zadaném adresářovém stromu, můžete to provést efektivněji bez vytvoření dotazu LINQ, který vznikne režie vytváření kolekce seznamu jako zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-107">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="fe5bb-108">Užitečnost přístupu LINQ se zvyšuje s dotazem se stává složitější, nebo pokud máte spustit více dotazů proti stejnému zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-108">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="fe5bb-109">Dotaz volá samostatnou metodu k získání délky souboru.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-109">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="fe5bb-110">Je to proto, aby bylo možné využívat možnou výjimku, která <xref:System.IO.FileInfo> bude vyvolána, pokud `GetFiles`byl soubor odstraněn v jiném vlákně po vytvoření objektu ve volání .</span><span class="sxs-lookup"><span data-stu-id="fe5bb-110">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="fe5bb-111">I v <xref:System.IO.FileInfo> případě, že objekt již byl <xref:System.IO.FileInfo> vytvořen, může dojít <xref:System.IO.FileInfo.Length%2A> k výjimce, protože objekt se pokusí aktualizovat svou vlastnost s nejaktuálnější délkou při prvním přístupu k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-111">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="fe5bb-112">Umístěním této operace v bloku try-catch mimo dotaz, kód se řídí pravidlem vyhnout se operacím v dotazech, které mohou způsobit vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-112">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="fe5bb-113">Obecně je třeba věnovat velkou pozornost při použití výjimky a ujistěte se, že aplikace není ponechána v neznámém stavu.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-113">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="fe5bb-114">Kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="fe5bb-114">Compile the code</span></span>  
<span data-ttu-id="fe5bb-115">Vytvořte projekt aplikace konzoly `Imports` jazyka s příkazem pro obor názvů System.Linq.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-115">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fe5bb-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="fe5bb-116">See also</span></span>

- [<span data-ttu-id="fe5bb-117">LINQ na objekty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe5bb-117">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="fe5bb-118">Linq a adresáře souborů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe5bb-118">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
