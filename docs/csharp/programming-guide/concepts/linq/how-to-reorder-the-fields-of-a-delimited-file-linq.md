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
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-c"></a><span data-ttu-id="3b2c6-102">Změna pořadí polí souboru s oddělovači (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="3b2c6-102">How to reorder the fields of a delimited file (LINQ) (C#)</span></span>
<span data-ttu-id="3b2c6-103">Textový soubor s oddělovači (CSV) je textový soubor, který se často používá k ukládání dat tabulky nebo jiných tabulkových dat, která jsou reprezentovaná řádky a sloupci.</span><span class="sxs-lookup"><span data-stu-id="3b2c6-103">A comma-separated value (CSV) file is a text file that is often used to store spreadsheet data or other tabular data that is represented by rows and columns.</span></span> <span data-ttu-id="3b2c6-104">Pomocí metody <xref:System.String.Split%2A> k oddělení polí je velmi snadné dotazování a manipulace se soubory CSV pomocí LINQ.</span><span class="sxs-lookup"><span data-stu-id="3b2c6-104">By using the <xref:System.String.Split%2A> method to separate the fields, it is very easy to query and manipulate CSV files by using LINQ.</span></span> <span data-ttu-id="3b2c6-105">Ve skutečnosti lze stejnou techniku použít k přeřazení částí libovolného strukturovaného řádku textu; Nejedná se pouze o soubory CSV.</span><span class="sxs-lookup"><span data-stu-id="3b2c6-105">In fact, the same technique can be used to reorder the parts of any structured line of text; it is not limited to CSV files.</span></span>  
  
 <span data-ttu-id="3b2c6-106">V následujícím příkladu Předpokládejme, že tři sloupce zastupují studenty "" příjmení "," křestní jméno "a" ID ".</span><span class="sxs-lookup"><span data-stu-id="3b2c6-106">In the following example, assume that the three columns represent students' "last name," "first name", and "ID."</span></span> <span data-ttu-id="3b2c6-107">Pole jsou v abecedním pořadí podle příjmení studentů.</span><span class="sxs-lookup"><span data-stu-id="3b2c6-107">The fields are in alphabetical order based on the students' last names.</span></span> <span data-ttu-id="3b2c6-108">Dotaz vytvoří nové pořadí, ve kterém se nejprve zobrazí sloupec ID následovaný druhým sloupcem, který kombinuje křestní jméno a příjmení studenta.</span><span class="sxs-lookup"><span data-stu-id="3b2c6-108">The query produces a new sequence in which the ID column appears first, followed by a second column that combines the student's first name and last name.</span></span> <span data-ttu-id="3b2c6-109">Řádky se přesměrují podle pole ID.</span><span class="sxs-lookup"><span data-stu-id="3b2c6-109">The lines are reordered according to the ID field.</span></span> <span data-ttu-id="3b2c6-110">Výsledky se uloží do nového souboru a původní data se nezmění.</span><span class="sxs-lookup"><span data-stu-id="3b2c6-110">The results are saved into a new file and the original data is not modified.</span></span>  
  
### <a name="to-create-the-data-file"></a><span data-ttu-id="3b2c6-111">Vytvoření datového souboru</span><span class="sxs-lookup"><span data-stu-id="3b2c6-111">To create the data file</span></span>  
  
1. <span data-ttu-id="3b2c6-112">Zkopírujte následující řádky do souboru prostého textu s názvem Spreadsheet1. csv.</span><span class="sxs-lookup"><span data-stu-id="3b2c6-112">Copy the following lines into a plain text file that is named spreadsheet1.csv.</span></span> <span data-ttu-id="3b2c6-113">Uložte soubor do složky projektu.</span><span class="sxs-lookup"><span data-stu-id="3b2c6-113">Save the file in your project folder.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="3b2c6-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="3b2c6-114">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="3b2c6-115">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="3b2c6-115">Compiling the Code</span></span>  
<span data-ttu-id="3b2c6-116">Vytvořte projekt C# konzolové aplikace s direktivami `using` pro obory názvů System. Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="3b2c6-116">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3b2c6-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3b2c6-117">See also</span></span>

- [<span data-ttu-id="3b2c6-118">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="3b2c6-118">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="3b2c6-119">LINQ a souborové adresáře (C#)</span><span class="sxs-lookup"><span data-stu-id="3b2c6-119">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
- [<span data-ttu-id="3b2c6-120">Generování XML ze souborů CSV (C#)</span><span class="sxs-lookup"><span data-stu-id="3b2c6-120">How to generate XML from CSV files (C#)</span></span>](./how-to-generate-xml-from-csv-files.md)
