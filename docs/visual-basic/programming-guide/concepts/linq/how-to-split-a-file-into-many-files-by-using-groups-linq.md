---
title: 'Postupy: Rozdělení souboru na více souborů pomocí skupin (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5e8b2a2b-0b1d-4933-8a2b-03e91dfaf77f
ms.openlocfilehash: 3c3d0d4d8c45ba2d7016636f0272ace0fdc6ffa3
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592478"
---
# <a name="how-to-split-a-file-into-many-files-by-using-groups-linq-visual-basic"></a><span data-ttu-id="9f7e0-102">Postupy: Rozdělení souboru na více souborů pomocí skupin (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f7e0-102">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="9f7e0-103">Tento příklad ukazuje jeden způsob, jak sloučit obsah těchto dvou souborů a potom vytvořit nové soubory, které uspořádání dat novým způsobem.</span><span class="sxs-lookup"><span data-stu-id="9f7e0-103">This example shows one way to merge the contents of two files and then create a set of new files that organize the data in a new way.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="9f7e0-104">K vytvoření datových souborů</span><span class="sxs-lookup"><span data-stu-id="9f7e0-104">To create the data files</span></span>  
  
1. <span data-ttu-id="9f7e0-105">Zkopírujte do textového souboru s názvem names1.txt tyto názvy a uložte ho do složky projektu:</span><span class="sxs-lookup"><span data-stu-id="9f7e0-105">Copy these names into a text file that is named names1.txt and save it in your project folder:</span></span>  
  
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
  
2. <span data-ttu-id="9f7e0-106">Zkopírujte do textového souboru s názvem names2.txt tyto názvy a uložte ho do složky projektu: Mějte na paměti, že dva soubory mají společnou některé názvy.</span><span class="sxs-lookup"><span data-stu-id="9f7e0-106">Copy these names into a text file that is named names2.txt and save it in your project folder: Note that the two files have some names in common.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="9f7e0-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f7e0-107">Example</span></span>  
  
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
  
 <span data-ttu-id="9f7e0-108">Program zapíše do samostatného souboru pro každou skupinu ve stejné složce jako datové soubory.</span><span class="sxs-lookup"><span data-stu-id="9f7e0-108">The program writes a separate file for each group in the same folder as the data files.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9f7e0-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="9f7e0-109">Compiling the Code</span></span>  
<span data-ttu-id="9f7e0-110">Vytvoření projektu aplikace konzoly VB.NET, pomocí `Imports` příkaz pro obor názvů System.Linq.</span><span class="sxs-lookup"><span data-stu-id="9f7e0-110">Create a VB.NET console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9f7e0-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f7e0-111">See also</span></span>

- [<span data-ttu-id="9f7e0-112">LINQ a řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f7e0-112">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [<span data-ttu-id="9f7e0-113">LINQ a souborové adresáře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f7e0-113">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
