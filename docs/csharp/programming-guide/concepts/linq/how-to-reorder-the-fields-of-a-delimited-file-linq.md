---
title: Změna pořadí polí souboru s oddělovači (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 4e62d82c-61b7-4f18-b9a1-86723746d7d2
ms.openlocfilehash: 6bc502ff12a908edf43f9ff7f5f63f98c3ff29c4
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347656"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-c"></a>Změna pořadí polí souboru s oddělovači (LINQ) (C#)
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
  
```csharp  
class CSVFiles  
{  
    static void Main(string[] args)  
    {  
        // Create the IEnumerable data source  
        string[] lines = System.IO.File.ReadAllLines(@"../../../spreadsheet1.csv");  
  
        // Create the query. Put field 2 first, then  
        // reverse and combine fields 0 and 1 from the old field  
        IEnumerable<string> query =  
            from line in lines  
            let x = line.Split(',')  
            orderby x[2]  
            select x[2] + ", " + (x[1] + " " + x[0]);  
  
        // Execute the query and write out the new file. Note that WriteAllLines  
        // takes a string[], so ToArray is called on the query.  
        System.IO.File.WriteAllLines(@"../../../spreadsheet2.csv", query.ToArray());  
  
        Console.WriteLine("Spreadsheet2.csv written to disk. Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output to spreadsheet2.csv:  
111, Svetlana Omelchenko  
112, Claire O'Donnell  
113, Sven Mortensen  
114, Cesar Garcia  
115, Debra Garcia  
116, Fadi Fakhouri  
117, Hanying Feng  
118, Hugo Garcia  
119, Lance Tucker  
120, Terry Adams  
121, Eugene Zabokritski  
122, Michael Tucker  
 */  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
Vytvořte projekt C# konzolové aplikace s direktivami `using` pro obory názvů System. Linq a System.IO.
  
## <a name="see-also"></a>Viz také:

- [LINQ a řetězce (C#)](./linq-and-strings.md)
- [LINQ a souborové adresáře (C#)](./linq-and-file-directories.md)
- [Generování XML ze souborů CSV (C#)](./how-to-generate-xml-from-csv-files.md)
