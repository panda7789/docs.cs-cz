---
title: "Postupy: rozdělení souboru na mnoho souborů pomocí skupin (LINQ) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e8b2a2b-0b1d-4933-8a2b-03e91dfaf77f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76fb89136e05ee803c1bb2c91674e6b216e4ed2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-split-a-file-into-many-files-by-using-groups-linq-visual-basic"></a>Postupy: rozdělení souboru na mnoho souborů pomocí skupin (LINQ) (Visual Basic)
Tento příklad ukazuje jeden ze způsobů sloučí obsah dva soubory a pak vytvořit sadu nové soubory, které uspořádání dat nový způsob.  
  
### <a name="to-create-the-data-files"></a>K vytvoření datových souborů  
  
1.  Zkopírujte tyto názvy do textového souboru s názvem names1.txt a uložit do složky projektu:  
  
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
  
2.  Zkopírujte tyto názvy do textového souboru s názvem names2.txt a uložte ho do složky projektu: Všimněte si, že dva soubory obsahují některé názvy společné.  
  
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
  
## <a name="example"></a>Příklad  
  
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
  
 Program zapíše samostatný soubor pro každou skupinu ve stejné složce jako datové soubory.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vytvoření projektu, jehož cílem rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na System.Core.dll a `Imports` příkaz pro obor názvů System.Linq.  
  
## <a name="see-also"></a>Viz také  
 [LINQ a řetězce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 [LINQ a souborové adresáře (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
