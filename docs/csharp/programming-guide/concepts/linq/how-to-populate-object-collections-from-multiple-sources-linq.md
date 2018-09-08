---
title: 'Postupy: vyplňování kolekcí objektů z více zdrojů (LINQ) (C#)'
ms.date: 06/12/2018
ms.assetid: 8ad7d480-b46c-4ccc-8c57-76f2d04ccc6d
ms.openlocfilehash: 377b4a21c78be2b53d2bcd0e88d39d06609c462b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44216090"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-c"></a><span data-ttu-id="9180b-102">Postupy: vyplňování kolekcí objektů z více zdrojů (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="9180b-102">How to: Populate Object Collections from Multiple Sources (LINQ) (C#)</span></span>

<span data-ttu-id="9180b-103">Tento příklad ukazuje, jak sloučit data z různých zdrojů do sekvence nových typů.</span><span class="sxs-lookup"><span data-stu-id="9180b-103">This example shows how to merge data from different sources into a sequence of new types.</span></span>

> [!NOTE]
> <span data-ttu-id="9180b-104">Nedoporučujeme připojení dat v paměti nebo dat v systému souborů s daty, která je stále v databázi.</span><span class="sxs-lookup"><span data-stu-id="9180b-104">Don't try to join in-memory data or data in the file system with data that is still in a database.</span></span> <span data-ttu-id="9180b-105">Takové spojení mezi doménami může přinést nedefinované výsledky z důvodu různé způsoby, ve kterém mohou být definovány operace spojení pro databázové dotazy a jiné druhy zdrojů.</span><span class="sxs-lookup"><span data-stu-id="9180b-105">Such cross-domain joins can yield undefined results because of different ways in which join operations might be defined for database queries and other types of sources.</span></span> <span data-ttu-id="9180b-106">Kromě toho existuje riziko, že tato operace může způsobit výjimku paměti, pokud je příliš velká množství dat v databázi.</span><span class="sxs-lookup"><span data-stu-id="9180b-106">Additionally, there is a risk that such an operation could cause an out-of-memory exception if the amount of data in the database is large enough.</span></span> <span data-ttu-id="9180b-107">K připojení dat z databáze pro data v paměti, nejprve volat `ToList` nebo `ToArray` v databázi dotaz a pak provedením příkazu join na vrácené kolekci.</span><span class="sxs-lookup"><span data-stu-id="9180b-107">To join data from a database to in-memory data, first call `ToList` or `ToArray` on the database query, and then perform the join on the returned collection.</span></span>

## <a name="to-create-the-data-file"></a><span data-ttu-id="9180b-108">Vytvoření datového souboru</span><span class="sxs-lookup"><span data-stu-id="9180b-108">To create the data file</span></span>

<span data-ttu-id="9180b-109">Zkopírujte soubory names.csv a scores.csv do složky vašeho projektu, jak je popsáno v [postupy: spojení obsahu z Nepodobných souborů (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).</span><span class="sxs-lookup"><span data-stu-id="9180b-109">Copy the names.csv and scores.csv files into your project folder, as described in [How to: Join Content from Dissimilar Files (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).</span></span>

## <a name="example"></a><span data-ttu-id="9180b-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="9180b-110">Example</span></span>

<span data-ttu-id="9180b-111">Následující příklad ukazuje způsob použití pojmenovaného typu `Student` k uložení sloučených data ze dvou kolekcích v paměti řetězců, které simulují data z tabulky ve formátu .csv.</span><span class="sxs-lookup"><span data-stu-id="9180b-111">The following example shows how to use a named type `Student` to store merged data from two in-memory collections of strings that simulate spreadsheet data in .csv format.</span></span> <span data-ttu-id="9180b-112">První kolekce řetězců představuje jména studentů a ID, a druhá kolekce, kterou představuje ID studenta (v prvním sloupci) a čtyři skóre zkoušku.</span><span class="sxs-lookup"><span data-stu-id="9180b-112">The first collection of strings represents the student names and IDs, and the second collection represents the student ID (in the first column) and four exam scores.</span></span> <span data-ttu-id="9180b-113">ID je použít jako cizí klíč.</span><span class="sxs-lookup"><span data-stu-id="9180b-113">The ID is used as the foreign key.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

class Student
{
    public string FirstName { get; set; }
    public string LastName { get; set; }
    public int ID { get; set; }
    public List<int> ExamScores { get; set; }
}

class PopulateCollection
{
    static void Main()
    {
        // These data files are defined in How to: Join Content from
        // Dissimilar Files (LINQ).

        // Each line of names.csv consists of a last name, a first name, and an
        // ID number, separated by commas. For example, Omelchenko,Svetlana,111
        string[] names = System.IO.File.ReadAllLines(@"../../../names.csv");

        // Each line of scores.csv consists of an ID number and four test
        // scores, separated by commas. For example, 111, 97, 92, 81, 60
        string[] scores = System.IO.File.ReadAllLines(@"../../../scores.csv");

        // Merge the data sources using a named type.
        // var could be used instead of an explicit type. Note the dynamic
        // creation of a list of ints for the ExamScores member. The first item
        // is skipped in the split string because it is the student ID,
        // not an exam score.
        IEnumerable<Student> queryNamesScores =
            from nameLine in names
            let splitName = nameLine.Split(',')
            from scoreLine in scores
            let splitScoreLine = scoreLine.Split(',')
            where Convert.ToInt32(splitName[2]) == Convert.ToInt32(splitScoreLine[0])
            select new Student()
            {
                FirstName = splitName[0],
                LastName = splitName[1],
                ID = Convert.ToInt32(splitName[2]),
                ExamScores = (from scoreAsText in splitScoreLine.Skip(1)
                              select Convert.ToInt32(scoreAsText)).
                              ToList()
            };

        // Optional. Store the newly created student objects in memory
        // for faster access in future queries. This could be useful with
        // very large data files.
        List<Student> students = queryNamesScores.ToList();

        // Display each student's name and exam score average.
        foreach (var student in students)
        {
            Console.WriteLine("The average score of {0} {1} is {2}.",
                student.FirstName, student.LastName,
                student.ExamScores.Average());
        }

        //Keep console window open in debug mode
        Console.WriteLine("Press any key to exit.");
        Console.ReadKey();
    }
}
/* Output:
    The average score of Omelchenko Svetlana is 82.5.
    The average score of O'Donnell Claire is 72.25.
    The average score of Mortensen Sven is 84.5.
    The average score of Garcia Cesar is 88.25.
    The average score of Garcia Debra is 67.
    The average score of Fakhouri Fadi is 92.25.
    The average score of Feng Hanying is 88.
    The average score of Garcia Hugo is 85.75.
    The average score of Tucker Lance is 81.75.
    The average score of Adams Terry is 85.25.
    The average score of Zabokritski Eugene is 83.
    The average score of Tucker Michael is 92.
 */
```

<span data-ttu-id="9180b-114">V [vyberte](../../../../csharp/language-reference/keywords/select-clause.md) klauzule inicializátoru objektu se používá k vytvoření instance každé nové `Student` s použitím data ze dvou zdrojů.</span><span class="sxs-lookup"><span data-stu-id="9180b-114">In the [select](../../../../csharp/language-reference/keywords/select-clause.md) clause, an object initializer is used to instantiate each new `Student` object by using the data from the two sources.</span></span>

<span data-ttu-id="9180b-115">Pokud nemáte k dispozici pro ukládání výsledků dotazu, může být vhodnější než pojmenované typy anonymních typů.</span><span class="sxs-lookup"><span data-stu-id="9180b-115">If you don't have to store the results of a query, anonymous types can be more convenient than named types.</span></span> <span data-ttu-id="9180b-116">Pokud předáte výsledky dotazu mimo metodu spuštění dotazu, je nutné pojmenovaných typů.</span><span class="sxs-lookup"><span data-stu-id="9180b-116">Named types are required if you pass the query results outside the method in which the query is executed.</span></span> <span data-ttu-id="9180b-117">Následující příklad provede stejné úkoly, jako předchozí příklad, ale místo pojmenované typy používá anonymní typy:</span><span class="sxs-lookup"><span data-stu-id="9180b-117">The following example executes the same task as the previous example, but uses anonymous types instead of named types:</span></span>

```csharp
// Merge the data sources by using an anonymous type.
// Note the dynamic creation of a list of ints for the
// ExamScores member. We skip 1 because the first string
// in the array is the student ID, not an exam score.
var queryNamesScores2 =
    from nameLine in names
    let splitName = nameLine.Split(',')
    from scoreLine in scores
    let splitScoreLine = scoreLine.Split(',')
    where Convert.ToInt32(splitName[2]) == Convert.ToInt32(splitScoreLine[0])
    select new
    {
        First = splitName[0],
        Last = splitName[1],
        ExamScores = (from scoreAsText in splitScoreLine.Skip(1)
                      select Convert.ToInt32(scoreAsText))
                      .ToList()
    };

// Display each student's name and exam score average.
foreach (var student in queryNamesScores2)
{
    Console.WriteLine("The average score of {0} {1} is {2}.",
        student.First, student.Last, student.ExamScores.Average());
}
```

## <a name="compiling-the-code"></a><span data-ttu-id="9180b-118">Kompilování kódu</span><span class="sxs-lookup"><span data-stu-id="9180b-118">Compiling the code</span></span>

<span data-ttu-id="9180b-119">Vytvoření a kompilace projektu, který cílí na jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="9180b-119">Create and compile a project that targets one of the following options:</span></span>

- <span data-ttu-id="9180b-120">Rozhraní .NET framework verze 3.5 s odkazem na knihovnu System.Core.dll.</span><span class="sxs-lookup"><span data-stu-id="9180b-120">.NET Framework version 3.5 with a reference to System.Core.dll.</span></span>
- <span data-ttu-id="9180b-121">Rozhraní .NET framework verze 4.0 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="9180b-121">.NET Framework version 4.0 or higher.</span></span>
- <span data-ttu-id="9180b-122">Verze .NET core 1.0 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="9180b-122">.NET Core version 1.0 or higher.</span></span>

## <a name="see-also"></a><span data-ttu-id="9180b-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="9180b-123">See Also</span></span>

- [<span data-ttu-id="9180b-124">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="9180b-124">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
- [<span data-ttu-id="9180b-125">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="9180b-125">Object and Collection Initializers</span></span>](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
- [<span data-ttu-id="9180b-126">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="9180b-126">Anonymous Types</span></span>](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
