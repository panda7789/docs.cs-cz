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
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-c"></a><span data-ttu-id="e5e55-102">Postupy: Změna pořadí polí v souboru s oddělovači (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e5e55-102">How to: Reorder the Fields of a Delimited File (LINQ) (C#)</span></span>
<span data-ttu-id="e5e55-103">Soubor hodnot oddělených čárkami (CSV) je textový soubor, který se často používá k ukládání dat tabulky nebo jiné tabulková data, která je reprezentována řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="e5e55-103">A comma-separated value (CSV) file is a text file that is often used to store spreadsheet data or other tabular data that is represented by rows and columns.</span></span> <span data-ttu-id="e5e55-104">S použitím <xref:System.String.Split%2A> metoda oddělují pole, je velmi snadné dotazování a zpracování souborů CSV pomocí jazyka LINQ.</span><span class="sxs-lookup"><span data-stu-id="e5e55-104">By using the <xref:System.String.Split%2A> method to separate the fields, it is very easy to query and manipulate CSV files by using LINQ.</span></span> <span data-ttu-id="e5e55-105">Ve skutečnosti stejným způsobem umožňuje změnit uspořádání částí jakéhokoli strukturovaných řádku textu. není omezený na souborů CSV.</span><span class="sxs-lookup"><span data-stu-id="e5e55-105">In fact, the same technique can be used to reorder the parts of any structured line of text; it is not limited to CSV files.</span></span>  
  
 <span data-ttu-id="e5e55-106">V následujícím příkladu se předpokládá, že tři sloupce představují studentů "příjmení," "jméno" a "ID".</span><span class="sxs-lookup"><span data-stu-id="e5e55-106">In the following example, assume that the three columns represent students' "last name," "first name", and "ID."</span></span> <span data-ttu-id="e5e55-107">Pole jsou v abecedním pořadí podle příjmení na studentů.</span><span class="sxs-lookup"><span data-stu-id="e5e55-107">The fields are in alphabetical order based on the students' last names.</span></span> <span data-ttu-id="e5e55-108">Dotaz vyprodukuje nové pořadí, ve kterém sloupci ID se zobrazí první, za nímž následuje druhý sloupec, který kombinuje student získal křestní jméno a příjmení.</span><span class="sxs-lookup"><span data-stu-id="e5e55-108">The query produces a new sequence in which the ID column appears first, followed by a second column that combines the student's first name and last name.</span></span> <span data-ttu-id="e5e55-109">Řádky přeuspořádají podle pole ID.</span><span class="sxs-lookup"><span data-stu-id="e5e55-109">The lines are reordered according to the ID field.</span></span> <span data-ttu-id="e5e55-110">Výsledky jsou uloženy do nového souboru a se nezmění původní data.</span><span class="sxs-lookup"><span data-stu-id="e5e55-110">The results are saved into a new file and the original data is not modified.</span></span>  
  
### <a name="to-create-the-data-file"></a><span data-ttu-id="e5e55-111">Vytvoření datového souboru</span><span class="sxs-lookup"><span data-stu-id="e5e55-111">To create the data file</span></span>  
  
1.  <span data-ttu-id="e5e55-112">Zkopírujte následující řádky do souboru ve formátu prostého textu, který je pojmenován spreadsheet1.csv.</span><span class="sxs-lookup"><span data-stu-id="e5e55-112">Copy the following lines into a plain text file that is named spreadsheet1.csv.</span></span> <span data-ttu-id="e5e55-113">Uložte soubor do složky projektu.</span><span class="sxs-lookup"><span data-stu-id="e5e55-113">Save the file in your project folder.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="e5e55-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="e5e55-114">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="e5e55-115">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e5e55-115">Compiling the Code</span></span>  
 <span data-ttu-id="e5e55-116">Vytvořit projekt, který cílí na rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na knihovnu System.Core.dll a `using` direktivy pro obory názvů System.Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="e5e55-116">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5e55-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5e55-117">See Also</span></span>

- [<span data-ttu-id="e5e55-118">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="e5e55-118">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
- [<span data-ttu-id="e5e55-119">LINQ a souborové adresáře (C#)</span><span class="sxs-lookup"><span data-stu-id="e5e55-119">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)  
- [<span data-ttu-id="e5e55-120">Postupy: Generování XML ze souborů CSV (C#)</span><span class="sxs-lookup"><span data-stu-id="e5e55-120">How to: Generate XML from CSV Files (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-generate-xml-from-csv-files.md)
