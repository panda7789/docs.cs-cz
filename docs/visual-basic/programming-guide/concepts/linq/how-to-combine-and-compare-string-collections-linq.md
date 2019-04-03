---
title: 'Postupy: Kombinace a porovnávání kolekcí řetězců (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 243cfafc-9eaa-4354-a9df-d329f1d39913
ms.openlocfilehash: efd8ebdcc12c2941753b6811028d73655167c2f9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828963"
---
# <a name="how-to-combine-and-compare-string-collections-linq-visual-basic"></a><span data-ttu-id="1f263-102">Postupy: Kombinace a porovnávání kolekcí řetězců (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f263-102">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="1f263-103">Tento příklad ukazuje, jak sloučit soubory, které obsahují řádků textu a pak výsledky seřaďte.</span><span class="sxs-lookup"><span data-stu-id="1f263-103">This example shows how to merge files that contain lines of text and then sort the results.</span></span> <span data-ttu-id="1f263-104">Konkrétně ukazuje, jak provádět jednoduché zřetězení, sjednocení a průnik dvou sad řádků textu.</span><span class="sxs-lookup"><span data-stu-id="1f263-104">Specifically, it shows how to perform a simple concatenation, a union, and an intersection on the two sets of text lines.</span></span>  
  
### <a name="to-set-up-the-project-and-the-text-files"></a><span data-ttu-id="1f263-105">Nastavení projektu a textové soubory</span><span class="sxs-lookup"><span data-stu-id="1f263-105">To set up the project and the text files</span></span>  
  
1.  <span data-ttu-id="1f263-106">Zkopírujte do textového souboru s názvem names1.txt tyto názvy a uložte ho do složky projektu:</span><span class="sxs-lookup"><span data-stu-id="1f263-106">Copy these names into a text file that is named names1.txt and save it in your project folder:</span></span>  
  
    ```  
    Bankov, Peter  
    Holm, Michael  
    Garcia, Hugo  
    Potra, Cristina  
    Noriega, Fabricio  
    Aw, Kam Foo  
    Beebe, Ann  
    Toyoshima, Tim  
    Guy, Wey Yuan  
    Garcia, Debra  
    ```  
  
2.  <span data-ttu-id="1f263-107">Zkopírujte do textového souboru s názvem names2.txt tyto názvy a uložte ho do složky projektu.</span><span class="sxs-lookup"><span data-stu-id="1f263-107">Copy these names into a text file that is named names2.txt and save it in your project folder.</span></span> <span data-ttu-id="1f263-108">Mějte na paměti, že dva soubory mají společnou některé názvy.</span><span class="sxs-lookup"><span data-stu-id="1f263-108">Note that the two files have some names in common.</span></span>  
  
    ```  
    Liu, Jinghao  
    Bankov, Peter  
    Holm, Michael  
    Garcia, Hugo  
    Beebe, Ann  
    Gilchrist, Beth  
    Myrcha, Jacek  
    Giakoumakis, Leo  
    McLin, Nkenge  
    El Yassir, Mehdi  
    ```  
  
## <a name="example"></a><span data-ttu-id="1f263-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="1f263-109">Example</span></span>  
  
```vb  
Class ConcatenateStrings  
    Shared Sub Main()  
  
        ' Create the IEnumerable data sources.  
        Dim fileA As String() = System.IO.File.ReadAllLines("../../../names1.txt")  
        Dim fileB As String() = System.IO.File.ReadAllLines("../../../names2.txt")  
  
        ' Simple concatenation and sort.  
        Dim concatQuery = fileA.Concat(fileB).OrderBy(Function(name) name)  
  
        ' Pass the query variable to another function for execution  
        OutputQueryResults(concatQuery, "Simple concatenation and sort. Duplicates are preserved:")  
  
        ' New query. Concatenate files and remove duplicates  
        Dim uniqueNamesQuery = fileA.Union(fileB).OrderBy(Function(name) name)  
        OutputQueryResults(uniqueNamesQuery, "Union removes duplicate names:")  
  
        ' New query. Find the names that occur in both files.  
        Dim commonNamesQuery = fileA.Intersect(fileB)  
        OutputQueryResults(commonNamesQuery, "Merge based on intersect: ")  
  
        ' New query in three steps for better readability   
        ' First filter each list separately  
  
        Dim nameToSearch As String = "Garcia"  
        Dim mergeQueryA As IEnumerable(Of String) = From name In fileA   
                          Let n = name.Split(New Char() {","})   
                          Where n(0) = nameToSearch   
                          Select name  
  
        Dim mergeQueryB = From name In fileB   
                          Let n = name.Split(New Char() {","})   
                          Where n(0) = nameToSearch   
                          Select name  
  
        ' Create a new query to concatenate and sort results. Duplicates are removed in Union.  
        ' Note that none of the queries actually executed until the call to OutputQueryResults.  
        Dim mergeSortQuery = mergeQueryA.Union(mergeQueryB).OrderBy(Function(str) str)  
  
        ' Now execute mergeSortQuery  
        OutputQueryResults(mergeSortQuery, "Concat based on partial name match """ & nameToSearch & """ from each list:")  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
  
    Shared Sub OutputQueryResults(ByVal query As IEnumerable(Of String), ByVal message As String)  
  
        Console.WriteLine(System.Environment.NewLine & message)  
        For Each item As String In query  
            Console.WriteLine(item)  
        Next  
        Console.WriteLine(query.Count & " total names in list")  
  
    End Sub  
End Class  
' Output:  
  
' Simple concatenation and sort. Duplicates are preserved:  
' Aw, Kam Foo  
' Bankov, Peter  
' Bankov, Peter  
' Beebe, Ann  
' Beebe, Ann  
' El Yassir, Mehdi  
' Garcia, Debra  
' Garcia, Hugo  
' Garcia, Hugo  
' Giakoumakis, Leo  
' Gilchrist, Beth  
' Guy, Wey Yuan  
' Holm, Michael  
' Holm, Michael  
' Liu, Jinghao  
' McLin, Nkenge  
' Myrcha, Jacek  
' Noriega, Fabricio  
' Potra, Cristina  
' Toyoshima, Tim  
' 20 total names in list  
  
' Union removes duplicate names:  
' Aw, Kam Foo  
' Bankov, Peter  
' Beebe, Ann  
' El Yassir, Mehdi  
' Garcia, Debra  
' Garcia, Hugo  
' Giakoumakis, Leo  
' Gilchrist, Beth  
' Guy, Wey Yuan  
' Holm, Michael  
' Liu, Jinghao  
' McLin, Nkenge  
' Myrcha, Jacek  
' Noriega, Fabricio  
' Potra, Cristina  
' Toyoshima, Tim  
' 16 total names in list  
  
' Merge based on intersect:  
' Bankov, Peter  
' Holm, Michael  
' Garcia, Hugo  
' Beebe, Ann  
' 4 total names in list  
  
' Concat based on partial name match "Garcia" from each list:  
' Garcia, Debra  
' Garcia, Hugo  
' 2 total names in list  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1f263-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1f263-110">Compiling the Code</span></span>  
 <span data-ttu-id="1f263-111">Vytvořit projekt, který cílí na rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na knihovnu System.Core.dll a `Imports` příkaz pro obor názvů System.Linq.</span><span class="sxs-lookup"><span data-stu-id="1f263-111">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f263-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1f263-112">See also</span></span>

- [<span data-ttu-id="1f263-113">LINQ a řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f263-113">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [<span data-ttu-id="1f263-114">LINQ a souborové adresáře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f263-114">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
