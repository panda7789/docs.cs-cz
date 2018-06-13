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
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-visual-basic"></a>Postupy: Změna pořadí polí souboru s oddělovači (LINQ) (Visual Basic)
Soubor s oddělovači (CSV) je textový soubor, který se často používá k ukládání dat tabulky nebo jiných tabulková data, která je reprezentována řádků a sloupců. Pomocí <xref:System.String.Split%2A> metoda k oddělení polí, je velmi snadné pro dotazování a pracovat se soubory CSV pomocí LINQ. Ve skutečnosti stejný postup lze použít ke změně pořadí části všech strukturovaných řádků textu; není omezeno na souborů CSV.  
  
 V následujícím příkladu se předpokládá, že tři sloupce představují studenty. "příjmení," "jméno" a "ID". Pole jsou v abecedním pořadí podle na studentů příjmení. Dotaz vytvoří nové pořadí, ve kterém sloupec ID první se objeví, za nímž následuje druhý sloupec, který kombinuje Studentova křestní jméno a příjmení. Řádky přeuspořádají podle pole ID. Výsledky se uloží do nového souboru a původní data se nemění.  
  
### <a name="to-create-the-data-file"></a>K vytvoření datového souboru  
  
1.  Zkopírujte následující řádky do souboru prostý text, který je pojmenován spreadsheet1.csv. Uložte soubor ve složce projektu.  
  
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
  
## <a name="example"></a>Příklad  
  
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
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
## <a name="see-also"></a>Viz také  
 [LINQ a řetězce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 [LINQ a souborové adresáře (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
 [Postupy: Generování XML ze souborů CSV](http://msdn.microsoft.com/library/dd7bab8c-96fa-4343-94d0-9739dd6a74fd)
