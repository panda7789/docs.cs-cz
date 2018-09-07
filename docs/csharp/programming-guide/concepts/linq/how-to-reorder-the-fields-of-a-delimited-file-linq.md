---
title: 'Postupy: Změna pořadí polí v souboru s oddělovači (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 4e62d82c-61b7-4f18-b9a1-86723746d7d2
ms.openlocfilehash: 24d1bf9825e00d0764846a0ae83ae73cd0ea03e1
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44080563"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-c"></a>Postupy: Změna pořadí polí v souboru s oddělovači (LINQ) (C#)
Soubor hodnot oddělených čárkami (CSV) je textový soubor, který se často používá k ukládání dat tabulky nebo jiné tabulková data, která je reprezentována řádků a sloupců. S použitím <xref:System.String.Split%2A> metoda oddělují pole, je velmi snadné dotazování a zpracování souborů CSV pomocí jazyka LINQ. Ve skutečnosti stejným způsobem umožňuje změnit uspořádání částí jakéhokoli strukturovaných řádku textu. není omezený na souborů CSV.  
  
 V následujícím příkladu se předpokládá, že tři sloupce představují studentů "příjmení," "jméno" a "ID". Pole jsou v abecedním pořadí podle příjmení na studentů. Dotaz vyprodukuje nové pořadí, ve kterém sloupci ID se zobrazí první, za nímž následuje druhý sloupec, který kombinuje student získal křestní jméno a příjmení. Řádky přeuspořádají podle pole ID. Výsledky jsou uloženy do nového souboru a se nezmění původní data.  
  
### <a name="to-create-the-data-file"></a>Vytvoření datového souboru  
  
1.  Zkopírujte následující řádky do souboru ve formátu prostého textu, který je pojmenován spreadsheet1.csv. Uložte soubor do složky projektu.  
  
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
 Vytvořit projekt, který cílí na rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na knihovnu System.Core.dll a `using` direktivy pro obory názvů System.Linq a System.IO.  
  
## <a name="see-also"></a>Viz také

- [LINQ a řetězce (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
- [LINQ a souborové adresáře (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)  
- [Postupy: Generování XML ze souborů CSV (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-generate-xml-from-csv-files.md)
