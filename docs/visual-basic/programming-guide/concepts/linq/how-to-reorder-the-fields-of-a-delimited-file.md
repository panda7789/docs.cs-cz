---
title: 'Postupy: Změna pořadí polí souboru s oddělovači (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: c451c7db-663b-4daf-b8ba-a2093095d672
ms.openlocfilehash: 4bef55c35311672ab3f28c2ce04a64e1cd21c170
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642028"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-visual-basic"></a><span data-ttu-id="c2c45-102">Postupy: Změna pořadí polí souboru s oddělovači (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2c45-102">How to: Reorder the Fields of a Delimited File (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="c2c45-103">Soubor s oddělovači (CSV) je textový soubor, který se často používá k ukládání dat tabulky nebo jiných tabulková data, která je reprezentována řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="c2c45-103">A comma-separated value (CSV) file is a text file that is often used to store spreadsheet data or other tabular data that is represented by rows and columns.</span></span> <span data-ttu-id="c2c45-104">Pomocí <xref:System.String.Split%2A> metoda k oddělení polí, je velmi snadné pro dotazování a pracovat se soubory CSV pomocí LINQ.</span><span class="sxs-lookup"><span data-stu-id="c2c45-104">By using the <xref:System.String.Split%2A> method to separate the fields, it is very easy to query and manipulate CSV files by using LINQ.</span></span> <span data-ttu-id="c2c45-105">Ve skutečnosti stejný postup lze použít ke změně pořadí části všech strukturovaných řádků textu; není omezeno na souborů CSV.</span><span class="sxs-lookup"><span data-stu-id="c2c45-105">In fact, the same technique can be used to reorder the parts of any structured line of text; it is not limited to CSV files.</span></span>  
  
 <span data-ttu-id="c2c45-106">V následujícím příkladu se předpokládá, že tři sloupce představují studenty. "příjmení," "jméno" a "ID".</span><span class="sxs-lookup"><span data-stu-id="c2c45-106">In the following example, assume that the three columns represent students' "last name," "first name", and "ID."</span></span> <span data-ttu-id="c2c45-107">Pole jsou v abecedním pořadí podle na studentů příjmení.</span><span class="sxs-lookup"><span data-stu-id="c2c45-107">The fields are in alphabetical order based on the students' last names.</span></span> <span data-ttu-id="c2c45-108">Dotaz vytvoří nové pořadí, ve kterém sloupec ID první se objeví, za nímž následuje druhý sloupec, který kombinuje Studentova křestní jméno a příjmení.</span><span class="sxs-lookup"><span data-stu-id="c2c45-108">The query produces a new sequence in which the ID column appears first, followed by a second column that combines the student's first name and last name.</span></span> <span data-ttu-id="c2c45-109">Řádky přeuspořádají podle pole ID.</span><span class="sxs-lookup"><span data-stu-id="c2c45-109">The lines are reordered according to the ID field.</span></span> <span data-ttu-id="c2c45-110">Výsledky se uloží do nového souboru a původní data se nemění.</span><span class="sxs-lookup"><span data-stu-id="c2c45-110">The results are saved into a new file and the original data is not modified.</span></span>  
  
### <a name="to-create-the-data-file"></a><span data-ttu-id="c2c45-111">K vytvoření datového souboru</span><span class="sxs-lookup"><span data-stu-id="c2c45-111">To create the data file</span></span>  
  
1.  <span data-ttu-id="c2c45-112">Zkopírujte následující řádky do souboru prostý text, který je pojmenován spreadsheet1.csv.</span><span class="sxs-lookup"><span data-stu-id="c2c45-112">Copy the following lines into a plain text file that is named spreadsheet1.csv.</span></span> <span data-ttu-id="c2c45-113">Uložte soubor ve složce projektu.</span><span class="sxs-lookup"><span data-stu-id="c2c45-113">Save the file in your project folder.</span></span>  
  
    ```  
    Adams,Terry,120  
    Fakhouri,Fadi,116  
    Feng,Hanying,117  
    Garcia,Cesar,114  
    Garcia,Debra,115  
    Garcia,Hugo,118  
    Mortensen,Sven,113  
    O'Donnell,Claire,112  
    Omelchenko,Svetlana,111  
    Tucker,Lance,119  
    Tucker,Michael,122  
    Zabokritski,Eugene,121  
    ```  
  
## <a name="example"></a><span data-ttu-id="c2c45-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="c2c45-114">Example</span></span>  
  
```vb  
Class CSVFiles  
  
    Shared Sub Main()  
  
        ' Create the IEnumerable data source.  
        Dim lines As String() = System.IO.File.ReadAllLines("../../../spreadsheet1.csv")  
  
        ' Execute the query. Put field 2 first, then  
        ' reverse and combine fields 0 and 1 from the old field  
        Dim lineQuery = From line In lines   
                        Let x = line.Split(New Char() {","})   
                        Order By x(2)   
                        Select x(2) & ", " & (x(1) & " " & x(0))  
  
        ' Execute the query and write out the new file. Note that WriteAllLines  
        ' takes a string array, so ToArray is called on the query.  
        System.IO.File.WriteAllLines("../../../spreadsheet2.csv", lineQuery.ToArray())  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Spreadsheet2.csv written to disk. Press any key to exit")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output to spreadsheet2.csv:  
' 111, Svetlana Omelchenko  
' 112, Claire O'Donnell  
' 113, Sven Mortensen  
' 114, Cesar Garcia  
' 115, Debra Garcia  
' 116, Fadi Fakhouri  
' 117, Hanying Feng  
' 118, Hugo Garcia  
' 119, Lance Tucker  
' 120, Terry Adams  
' 121, Eugene Zabokritski  
' 122, Michael Tucker  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c2c45-115">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="c2c45-115">Compiling the Code</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2c45-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2c45-116">See Also</span></span>  
 [<span data-ttu-id="c2c45-117">LINQ a řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2c45-117">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 [<span data-ttu-id="c2c45-118">LINQ a souborové adresáře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2c45-118">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
 [<span data-ttu-id="c2c45-119">Postupy: Generování XML ze souborů CSV</span><span class="sxs-lookup"><span data-stu-id="c2c45-119">How to: Generate XML from CSV Files</span></span>](http://msdn.microsoft.com/library/dd7bab8c-96fa-4343-94d0-9739dd6a74fd)
