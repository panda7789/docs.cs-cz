---
title: 'Postupy: rozdělení souboru na více souborů pomocí skupin (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5e8b2a2b-0b1d-4933-8a2b-03e91dfaf77f
ms.openlocfilehash: e12de7380ca34478506fde98aecae2501d2529ee
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835115"
---
# <a name="how-to-split-a-file-into-many-files-by-using-groups-linq-visual-basic"></a><span data-ttu-id="99cba-102">Postupy: rozdělení souboru na více souborů pomocí skupin (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99cba-102">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="99cba-103">Tento příklad ukazuje jeden ze způsobů, jak sloučit obsah dvou souborů a pak vytvořit sadu nových souborů, které data organizují novým způsobem.</span><span class="sxs-lookup"><span data-stu-id="99cba-103">This example shows one way to merge the contents of two files and then create a set of new files that organize the data in a new way.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="99cba-104">Vytvoření datových souborů</span><span class="sxs-lookup"><span data-stu-id="99cba-104">To create the data files</span></span>  
  
1. <span data-ttu-id="99cba-105">Zkopírujte tyto názvy do textového souboru s názvem names1. txt a uložte je do složky projektu:</span><span class="sxs-lookup"><span data-stu-id="99cba-105">Copy these names into a text file that is named names1.txt and save it in your project folder:</span></span>  
  
    ```text  
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
  
2. <span data-ttu-id="99cba-106">Zkopírujte tyto názvy do textového souboru s názvem names2. txt a uložte je do složky projektu: Všimněte si, že dva soubory mají některé běžné názvy.</span><span class="sxs-lookup"><span data-stu-id="99cba-106">Copy these names into a text file that is named names2.txt and save it in your project folder: Note that the two files have some names in common.</span></span>  
  
    ```text  
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
  
## <a name="example"></a><span data-ttu-id="99cba-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="99cba-107">Example</span></span>  
  
```vb  
Class SplitWithGroups  
  
    Shared Sub Main()  
  
        Dim fileA As String() = System.IO.File.ReadAllLines("../../../names1.txt")  
        Dim fileB As String() = System.IO.File.ReadAllLines("../../../names2.txt")  
  
        ' Concatenate and remove duplicate names based on  
        Dim mergeQuery As IEnumerable(Of String) = fileA.Union(fileB)  
  
        ' Group the names by the first letter in the last name  
        Dim groupQuery = From name In mergeQuery   
                     Let n = name.Split(New Char() {","})   
                     Order By n(0)   
                     Group By groupKey = n(0)(0)   
                     Into groupName = Group  
  
        ' Create a new file for each group that was created  
        ' Note that nested foreach loops are required to access  
        ' individual items with each group.  
        For Each gGroup In groupQuery  
            Dim fileName As String = "..'..'..'testFile_" & gGroup.groupKey & ".txt"  
            Dim sw As New System.IO.StreamWriter(fileName)  
            Console.WriteLine(gGroup.groupKey)  
            For Each item In gGroup.groupName  
                Console.WriteLine("   " & item.name)  
                sw.WriteLine(item.name)  
            Next  
            sw.Close()  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Files have been written. Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
End Class  
' Console Output:  
' A  
'    Aw, Kam Foo  
' B  
'    Bankov, Peter  
'    Beebe, Ann  
' E  
'    El Yassir, Mehdi  
' G  
'    Garcia, Hugo  
'    Garcia, Debra  
'    Giakoumakis, Leo  
'    Gilchrist, Beth  
'    Guy, Wey Yuan  
' H  
'    Holm, Michael  
' L  
'    Liu, Jinghao  
' M  
'    McLin, Nkenge  
'    Myrcha, Jacek  
' N  
'    Noriega, Fabricio  
' P  
'    Potra, Cristina  
' T  
'    Toyoshima, Tim  
```  
  
 <span data-ttu-id="99cba-108">Program zapisuje samostatný soubor pro každou skupinu ve stejné složce jako datové soubory.</span><span class="sxs-lookup"><span data-stu-id="99cba-108">The program writes a separate file for each group in the same folder as the data files.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="99cba-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="99cba-109">Compiling the Code</span></span>  
<span data-ttu-id="99cba-110">Vytvořte projekt konzolové aplikace VB.NET s příkazem `Imports` pro obor názvů System. Linq.</span><span class="sxs-lookup"><span data-stu-id="99cba-110">Create a VB.NET console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="99cba-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="99cba-111">See also</span></span>

- [<span data-ttu-id="99cba-112">LINQ a řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99cba-112">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [<span data-ttu-id="99cba-113">LINQ a souborové adresáře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99cba-113">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
