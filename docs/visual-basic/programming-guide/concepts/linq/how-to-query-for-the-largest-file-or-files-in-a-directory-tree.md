---
title: "Postupy: dotazování na největší soubor či soubory v adresářovém stromu (LINQ) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bcdb73006958188ef14949e37b04c2913c3fa0a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a><span data-ttu-id="e3272-102">Postupy: dotazování na největší soubor či soubory v adresářovém stromu (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3272-102">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="e3272-103">Tento příklad ukazuje pět dotazů souvisejících s velikost souboru v bajtech:</span><span class="sxs-lookup"><span data-stu-id="e3272-103">This example shows five queries related to file size in bytes:</span></span>  
  
-   <span data-ttu-id="e3272-104">Jak načíst velikost v bajtech na největší soubor.</span><span class="sxs-lookup"><span data-stu-id="e3272-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
-   <span data-ttu-id="e3272-105">Jak načíst velikost v bajtech nejmenší soubor.</span><span class="sxs-lookup"><span data-stu-id="e3272-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
-   <span data-ttu-id="e3272-106">Jak načíst <xref:System.IO.FileInfo> objekt nejvyšší nebo nejnižší soubor z jednoho nebo více složek v zadané kořenové složce.</span><span class="sxs-lookup"><span data-stu-id="e3272-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
-   <span data-ttu-id="e3272-107">Jak načíst pořadí například 10 největší soubory.</span><span class="sxs-lookup"><span data-stu-id="e3272-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
-   <span data-ttu-id="e3272-108">Jak pořadí souborů do skupiny založené na jejich velikost souboru v bajtech, soubory, které jsou menší než zadaná velikost je ignorována.</span><span class="sxs-lookup"><span data-stu-id="e3272-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3272-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="e3272-109">Example</span></span>  
 <span data-ttu-id="e3272-110">Následující příklad obsahuje pět samostatné dotazy, které ukazují, jak dotazovat a skupiny souborů, v závislosti na jejich velikost souboru v bajtech.</span><span class="sxs-lookup"><span data-stu-id="e3272-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="e3272-111">Můžete snadno upravit tyto příklady provést dotaz na některé jiné vlastnosti <xref:System.IO.FileInfo> objektu.</span><span class="sxs-lookup"><span data-stu-id="e3272-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
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
  
 <span data-ttu-id="e3272-112">Vrátit jeden nebo více dokončení <xref:System.IO.FileInfo> objekty, dotaz musí nejprve zkontrolujte každé z nich v datech zdroje a seřadit je podle hodnoty vlastnosti jejich délka.</span><span class="sxs-lookup"><span data-stu-id="e3272-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="e3272-113">Potom může vrátit jeden jeden nebo pořadí s největší délky.</span><span class="sxs-lookup"><span data-stu-id="e3272-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="e3272-114">Použití <xref:System.Linq.Enumerable.First%2A> vrátit první prvek v seznamu.</span><span class="sxs-lookup"><span data-stu-id="e3272-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="e3272-115">Použití <xref:System.Linq.Enumerable.Take%2A> vrátit první n počet elementů.</span><span class="sxs-lookup"><span data-stu-id="e3272-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="e3272-116">Zadejte sestupně uvést nejmenší elementy na začátku seznamu.</span><span class="sxs-lookup"><span data-stu-id="e3272-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="e3272-117">Dotaz volá samostatné metodě získat velikost souboru v bajtech, aby bylo možné využívat možné výjimku, která bude vyvolána v případě, kdy byl odstraněn soubor na jiné vlákno v období od <xref:System.IO.FileInfo> objekt byl vytvořen ve volání `GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="e3272-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="e3272-118">I přes <xref:System.IO.FileInfo> objekt již byl vytvořen, výjimka může dojít, protože <xref:System.IO.FileInfo> objekt se pokusí obnovit jeho <xref:System.IO.FileInfo.Length%2A> vlastnost pomocí aktuálního velikost v bajtech poprvé vlastnost přistupuje.</span><span class="sxs-lookup"><span data-stu-id="e3272-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="e3272-119">Vložením tuto operaci v bloku try-catch – mimo dotaz jsme podle pravidla vyloučení operace v dotazech, které můžou způsobit vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="e3272-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="e3272-120">Obecně platí skvělé musí dát pozor při využívání výjimky, abyste měli jistotu, že aplikace není ponecháno v neznámém stavu.</span><span class="sxs-lookup"><span data-stu-id="e3272-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e3272-121">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e3272-121">Compiling the Code</span></span>  
 <span data-ttu-id="e3272-122">Vytvoření projektu, jehož cílem rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na System.Core.dll a `Imports` příkaz pro obor názvů System.Linq.</span><span class="sxs-lookup"><span data-stu-id="e3272-122">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3272-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="e3272-123">See Also</span></span>  
 [<span data-ttu-id="e3272-124">LINQ na objekty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3272-124">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="e3272-125">LINQ a souborové adresáře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3272-125">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
