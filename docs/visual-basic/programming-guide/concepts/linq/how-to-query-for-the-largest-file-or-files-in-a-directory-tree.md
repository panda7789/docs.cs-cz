---
title: 'Postupy: Vytvoření dotazu na největší soubor či soubory v adresářovém stromu (LINQ)'
ms.date: 07/20/2015
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
ms.openlocfilehash: 4f7dcb46670612695b5a7219b12a7f2e83746af2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347670"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a><span data-ttu-id="7aa01-102">Postupy: vytvoření dotazu na největší soubor nebo soubory ve stromu adresářů (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7aa01-102">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="7aa01-103">Tento příklad ukazuje pět dotazů týkajících se velikosti souboru v bajtech:</span><span class="sxs-lookup"><span data-stu-id="7aa01-103">This example shows five queries related to file size in bytes:</span></span>  
  
- <span data-ttu-id="7aa01-104">Jak načíst velikost v bajtech pro největší soubor</span><span class="sxs-lookup"><span data-stu-id="7aa01-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
- <span data-ttu-id="7aa01-105">Jak načíst velikost nejmenšího souboru v bajtech.</span><span class="sxs-lookup"><span data-stu-id="7aa01-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
- <span data-ttu-id="7aa01-106">Jak načíst největší nebo nejmenší soubor objektu <xref:System.IO.FileInfo> z jedné nebo více složek v zadané kořenové složce.</span><span class="sxs-lookup"><span data-stu-id="7aa01-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
- <span data-ttu-id="7aa01-107">Jak načíst sekvenci, jako je 10 největších souborů.</span><span class="sxs-lookup"><span data-stu-id="7aa01-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
- <span data-ttu-id="7aa01-108">Postup při řazení souborů do skupin na základě velikosti jejich souboru v bajtech. soubory, které jsou menší než zadaná velikost, se ignorují.</span><span class="sxs-lookup"><span data-stu-id="7aa01-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7aa01-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="7aa01-109">Example</span></span>  
 <span data-ttu-id="7aa01-110">Následující příklad obsahuje pět samostatných dotazů, které ukazují, jak zadávat dotazy a seskupovat soubory v závislosti na velikosti souboru v bajtech.</span><span class="sxs-lookup"><span data-stu-id="7aa01-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="7aa01-111">Tyto příklady lze snadno upravit tak, aby dotaz byly založeny na nějaké jiné vlastnosti objektu <xref:System.IO.FileInfo>.</span><span class="sxs-lookup"><span data-stu-id="7aa01-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
```vb  
Module QueryBySize  
    Sub Main()  
  
        ' Change the drive\path if necessary  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(root)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Return the size of the largest file  
        Dim maxSize = Aggregate aFile In fileList Into Max(GetFileLength(aFile))  
  
        'Dim maxSize = fileLengths.Max  
        Console.WriteLine("The length of the largest file under {0} is {1}", _  
                          root, maxSize)  
  
        ' Return the FileInfo object of the largest file  
        ' by sorting and selecting from the beginning of the list  
        Dim filesByLengDesc = From file In fileList _  
                              Let filelength = GetFileLength(file) _  
                              Where filelength > 0 _  
                              Order By filelength Descending _  
                              Select file  
  
        Dim longestFile = filesByLengDesc.First  
  
        Console.WriteLine("The largest file under {0} is {1} with a length of {2} bytes", _  
                          root, longestFile.FullName, longestFile.Length)  
  
        Dim smallestFile = filesByLengDesc.Last  
  
        Console.WriteLine("The smallest file under {0} is {1} with a length of {2} bytes", _  
                                root, smallestFile.FullName, smallestFile.Length)  
  
        ' Return the FileInfos for the 10 largest files  
        ' Based on a previous query, but nothing is executed  
        ' until the For Each statement below.  
        Dim tenLargest = From file In filesByLengDesc Take 10  
  
        Console.WriteLine("The 10 largest files under {0} are:", root)  
  
        For Each fi As System.IO.FileInfo In tenLargest  
            Console.WriteLine("{0}: {1} bytes", fi.FullName, fi.Length)  
        Next  
  
        ' Group files according to their size,  
        ' leaving out the ones under 200K  
        Dim sizeGroups = From file As System.IO.FileInfo In fileList _  
                         Where file.Length > 0 _  
                         Let groupLength = file.Length / 100000 _  
                         Group file By groupLength Into fileGroup = Group _  
                         Where groupLength >= 2 _  
                         Order By groupLength Descending  
  
        For Each group In sizeGroups  
            Console.WriteLine(group.groupLength + "00000")  
  
            For Each item As System.IO.FileInfo In group.fileGroup  
                Console.WriteLine("   {0}: {1}", item.Name, item.Length)  
            Next  
        Next  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    ' In this particular case, it is safe to ignore the exception.  
    Function GetFileLength(ByVal fi As System.IO.FileInfo) As Long  
        Dim retval As Long  
        Try  
            retval = fi.Length  
        Catch ex As FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.   
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 <span data-ttu-id="7aa01-112">Chcete-li vrátit jeden nebo více úplných objektů <xref:System.IO.FileInfo>, musí dotaz nejprve projít každý zdroj dat a pak je seřadit podle hodnoty vlastnosti length.</span><span class="sxs-lookup"><span data-stu-id="7aa01-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="7aa01-113">Pak může vrátit jednu z nich nebo sekvenci s největší délkou.</span><span class="sxs-lookup"><span data-stu-id="7aa01-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="7aa01-114">Použijte <xref:System.Linq.Enumerable.First%2A> k vrácení prvního prvku v seznamu.</span><span class="sxs-lookup"><span data-stu-id="7aa01-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="7aa01-115">Použijte <xref:System.Linq.Enumerable.Take%2A> k vrácení prvního n počtu prvků.</span><span class="sxs-lookup"><span data-stu-id="7aa01-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="7aa01-116">Určete sestupné řazení, aby bylo možné umístit nejmenší prvky na začátek seznamu.</span><span class="sxs-lookup"><span data-stu-id="7aa01-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="7aa01-117">Dotaz volá samostatnou metodu, která získá velikost souboru v bajtech, aby využívala možnou výjimku, která se vyvolá v případě, že se soubor v časovém období odstranil v jiném vlákně, protože byl ve volání `GetFiles`vytvořený objekt <xref:System.IO.FileInfo>.</span><span class="sxs-lookup"><span data-stu-id="7aa01-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="7aa01-118">I přes objekt <xref:System.IO.FileInfo> již byl vytvořen, výjimka může být způsobena tím, že se objekt <xref:System.IO.FileInfo> pokusí aktualizovat jeho vlastnost <xref:System.IO.FileInfo.Length%2A> pomocí nejaktuálnější velikosti v bajtech, při které je vlastnost poprvé k dispozici.</span><span class="sxs-lookup"><span data-stu-id="7aa01-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="7aa01-119">Vložením této operace do bloku try-catch mimo dotaz se řídí pravidlo vyloučení operací v dotazech, které můžou způsobit vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="7aa01-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="7aa01-120">Obecně je potřeba věnovat velkou péči při využívání výjimek, aby se zajistilo, že aplikace zůstane v neznámém stavu.</span><span class="sxs-lookup"><span data-stu-id="7aa01-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7aa01-121">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7aa01-121">Compiling the Code</span></span>  
<span data-ttu-id="7aa01-122">Vytvořte projekt konzolové aplikace VB.NET s příkazem `Imports` pro obor názvů System. Linq.</span><span class="sxs-lookup"><span data-stu-id="7aa01-122">Create a VB.NET console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7aa01-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7aa01-123">See also</span></span>

- [<span data-ttu-id="7aa01-124">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7aa01-124">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="7aa01-125">LINQ a souborové adresáře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7aa01-125">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
