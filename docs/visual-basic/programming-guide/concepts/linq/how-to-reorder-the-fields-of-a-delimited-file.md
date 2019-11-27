---
title: 'Postupy: Změna pořadí polí v souboru s oddělovači (LINQ)'
ms.date: 07/20/2015
ms.assetid: c451c7db-663b-4daf-b8ba-a2093095d672
ms.openlocfilehash: 736f0218f14f0077683456599d3d7ef3ecec7517
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347606"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-visual-basic"></a>Postupy: Změna pořadí polí souboru s oddělovači (LINQ) (Visual Basic)

Textový soubor s oddělovači (CSV) je textový soubor, který se často používá k ukládání dat tabulky nebo jiných tabulkových dat, která jsou reprezentovaná řádky a sloupci. Pomocí metody <xref:System.String.Split%2A> k oddělení polí je velmi snadné dotazování a manipulace se soubory CSV pomocí LINQ. Ve skutečnosti lze stejnou techniku použít k přeřazení částí libovolného strukturovaného řádku textu; Nejedná se pouze o soubory CSV.

V následujícím příkladu Předpokládejme, že tři sloupce zastupují studenty "" příjmení "," křestní jméno "a" ID ". Pole jsou v abecedním pořadí podle příjmení studentů. Dotaz vytvoří nové pořadí, ve kterém se nejprve zobrazí sloupec ID následovaný druhým sloupcem, který kombinuje křestní jméno a příjmení studenta. Řádky se přesměrují podle pole ID. Výsledky se uloží do nového souboru a původní data se nezmění.

### <a name="to-create-the-data-file"></a>Vytvoření datového souboru

1. Zkopírujte následující řádky do souboru prostého textu s názvem Spreadsheet1. csv. Uložte soubor do složky projektu.

    ```csv
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

## <a name="see-also"></a>Viz také:

- [LINQ a řetězce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [LINQ a souborové adresáře (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
- [Postupy: Generování XML ze souborů CSV](../../../../visual-basic/programming-guide/concepts/linq/how-to-generate-xml-from-csv-files.md)
