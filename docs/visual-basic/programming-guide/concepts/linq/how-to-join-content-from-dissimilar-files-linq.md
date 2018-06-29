---
title: 'Postupy: spojení obsahu z Nepodobných souborů (LINQ) (Visual Basic)'
ms.date: 06/27/2018
ms.assetid: e7530857-c467-41ea-9730-84e6b1065a4d
ms.openlocfilehash: d82e43449651ead5f39ec9c9442d3087b34d10ef
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2018
ms.locfileid: "37072043"
---
# <a name="how-to-join-content-from-dissimilar-files-linq-visual-basic"></a><span data-ttu-id="f57d8-102">Postupy: spojení obsahu z Nepodobných souborů (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f57d8-102">How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="f57d8-103">Tento příklad ukazuje, jak propojit data z dva soubory s položkami oddělenými čárkou, které sdílejí společné hodnotu, která se používá jako odpovídající klíč.</span><span class="sxs-lookup"><span data-stu-id="f57d8-103">This example shows how to join data from two comma-delimited files that share a common value that is used as a matching key.</span></span> <span data-ttu-id="f57d8-104">Tento postup může být užitečné, pokud budete muset kombinovat data ze dvou tabulek, nebo z tabulky a ze souboru, který má jiný formát do nového souboru.</span><span class="sxs-lookup"><span data-stu-id="f57d8-104">This technique can be useful if you have to combine data from two spreadsheets, or from a spreadsheet and from a file that has another format, into a new file.</span></span> <span data-ttu-id="f57d8-105">Příklad pro práci s jakýkoli druh strukturovaných textových můžete upravit.</span><span class="sxs-lookup"><span data-stu-id="f57d8-105">You can modify the example to work with any kind of structured text.</span></span>  
  
## <a name="to-create-the-data-files"></a><span data-ttu-id="f57d8-106">K vytvoření datových souborů</span><span class="sxs-lookup"><span data-stu-id="f57d8-106">To create the data files</span></span>
  
1.  <span data-ttu-id="f57d8-107">Zkopírujte následující řádky do souboru, který je pojmenován scores.csv a uložte ho do složky projektu.</span><span class="sxs-lookup"><span data-stu-id="f57d8-107">Copy the following lines into a file that is named scores.csv and save it to your project folder.</span></span> <span data-ttu-id="f57d8-108">Soubor představuje data z tabulky.</span><span class="sxs-lookup"><span data-stu-id="f57d8-108">The file represents spreadsheet data.</span></span> <span data-ttu-id="f57d8-109">Sloupec 1 je ID Studentova a sloupce 2 až 5 jsou výsledků testu.</span><span class="sxs-lookup"><span data-stu-id="f57d8-109">Column 1 is the student's ID, and columns 2 through 5 are test scores.</span></span>  
  
    ```  
    111, 97, 92, 81, 60  
    112, 75, 84, 91, 39  
    113, 88, 94, 65, 91  
    114, 97, 89, 85, 82  
    115, 35, 72, 91, 70  
    116, 99, 86, 90, 94  
    117, 93, 92, 80, 87  
    118, 92, 90, 83, 78  
    119, 68, 79, 88, 92  
    120, 99, 82, 81, 79  
    121, 96, 85, 91, 60  
    122, 94, 92, 91, 91  
    ```  
  
2.  <span data-ttu-id="f57d8-110">Zkopírujte následující řádky do souboru, který je pojmenován names.csv a uložte ho do složky projektu.</span><span class="sxs-lookup"><span data-stu-id="f57d8-110">Copy the following lines into a file that is named names.csv and save it to your project folder.</span></span> <span data-ttu-id="f57d8-111">Soubor představuje tabulky, který obsahuje příjmení, křestní jméno a student ID. Studentova</span><span class="sxs-lookup"><span data-stu-id="f57d8-111">The file represents a spreadsheet that contains the student's last name, first name, and student ID.</span></span>  
  
    ```  
    Omelchenko,Svetlana,111  
    O'Donnell,Claire,112  
    Mortensen,Sven,113  
    Garcia,Cesar,114  
    Garcia,Debra,115  
    Fakhouri,Fadi,116  
    Feng,Hanying,117  
    Garcia,Hugo,118  
    Tucker,Lance,119  
    Adams,Terry,120  
    Zabokritski,Eugene,121  
    Tucker,Michael,122  
    ```  
  
## <a name="example"></a><span data-ttu-id="f57d8-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="f57d8-112">Example</span></span>  

```vb
Imports System.Collections.Generic
Imports System.Linq

Class JoinStrings  
  
    Shared Sub Main()  
  
        ' Join content from spreadsheet files that contain  
        ' related information. names.csv contains the student name  
        ' plus an ID number. scores.csv contains the ID and a   
        ' set of four test scores. The following query joins  
        ' the scores to the student names by using ID as a  
        ' matching key.  
  
        Dim names As String() = System.IO.File.ReadAllLines("../../../names.csv")  
        Dim scores As String() = System.IO.File.ReadAllLines("../../../scores.csv")  
  
        ' Name:    Last[0],       First[1],  ID[2],     Grade Level[3]  
        '          Omelchenko,    Svetlana,  111,       2  
        ' Score:   StudentID[0],  Exam1[1]   Exam2[2],  Exam3[3],  Exam4[4]  
        '          111,           97,        92,        81,        60  
  
        ' This query joins two dissimilar spreadsheets based on common ID value.  
        ' Multiple from clauses are used instead of a join clause  
        ' in order to store results of id.Split.  
        Dim scoreQuery1 = From name In names   
                         Let n = name.Split(New Char() {","})   
                            From id In scores   
                            Let n2 = id.Split(New Char() {","})   
                            Where Convert.ToInt32(n(2)) = Convert.ToInt32(n2(0))
                            Select n(0) & "," & n(1) & "," & n2(0) & "," & n2(1) & "," &  
                              n2(2) & "," & n2(3)  
  
        ' Pass a query variable to a Sub and execute it there.  
        ' The query itself is unchanged.  
        OutputQueryResults(scoreQuery1, "Merge two spreadsheets:")  
  
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
' Merge two spreadsheets:
' Omelchenko, 97, 92, 81, 60
' O'Donnell, 75, 84, 91, 39
' Mortensen, 88, 94, 65, 91
' Garcia, 97, 89, 85, 82
' Garcia, 35, 72, 91, 70
' Fakhouri, 99, 86, 90, 94
' Feng, 93, 92, 80, 87
' Garcia, 92, 90, 83, 78
' Tucker, 68, 79, 88, 92
' Adams, 99, 82, 81, 79
' Zabokritski, 96, 85, 91, 60
' Tucker, 94, 92, 91, 91
' 12 total names in list 
```  

## <a name="compiling-the-code"></a><span data-ttu-id="f57d8-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f57d8-113">Compiling the code</span></span>

<span data-ttu-id="f57d8-114">Vytvoření a kompilace projektu, jehož cílem jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="f57d8-114">Create and compile a project that targets one of the following options:</span></span>

- <span data-ttu-id="f57d8-115">Rozhraní .NET framework verze 3.5 s odkazem na System.Core.dll.</span><span class="sxs-lookup"><span data-stu-id="f57d8-115">.NET Framework version 3.5 with a reference to System.Core.dll.</span></span>
- <span data-ttu-id="f57d8-116">Rozhraní .NET framework verze 4.0 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="f57d8-116">.NET Framework version 4.0 or higher.</span></span>
- <span data-ttu-id="f57d8-117">.NET core verze 1.0 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="f57d8-117">.NET Core version 1.0 or higher.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f57d8-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f57d8-118">See also</span></span>

 [<span data-ttu-id="f57d8-119">LINQ a řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f57d8-119">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 [<span data-ttu-id="f57d8-120">LINQ a souborové adresáře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f57d8-120">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
