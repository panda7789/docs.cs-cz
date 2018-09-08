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
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-c"></a>Postupy: vyplňování kolekcí objektů z více zdrojů (LINQ) (C#)

Tento příklad ukazuje, jak sloučit data z různých zdrojů do sekvence nových typů.

> [!NOTE]
> Nedoporučujeme připojení dat v paměti nebo dat v systému souborů s daty, která je stále v databázi. Takové spojení mezi doménami může přinést nedefinované výsledky z důvodu různé způsoby, ve kterém mohou být definovány operace spojení pro databázové dotazy a jiné druhy zdrojů. Kromě toho existuje riziko, že tato operace může způsobit výjimku paměti, pokud je příliš velká množství dat v databázi. K připojení dat z databáze pro data v paměti, nejprve volat `ToList` nebo `ToArray` v databázi dotaz a pak provedením příkazu join na vrácené kolekci.

## <a name="to-create-the-data-file"></a>Vytvoření datového souboru

Zkopírujte soubory names.csv a scores.csv do složky vašeho projektu, jak je popsáno v [postupy: spojení obsahu z Nepodobných souborů (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití pojmenovaného typu `Student` k uložení sloučených data ze dvou kolekcích v paměti řetězců, které simulují data z tabulky ve formátu .csv. První kolekce řetězců představuje jména studentů a ID, a druhá kolekce, kterou představuje ID studenta (v prvním sloupci) a čtyři skóre zkoušku. ID je použít jako cizí klíč.

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

V [vyberte](../../../../csharp/language-reference/keywords/select-clause.md) klauzule inicializátoru objektu se používá k vytvoření instance každé nové `Student` s použitím data ze dvou zdrojů.

Pokud nemáte k dispozici pro ukládání výsledků dotazu, může být vhodnější než pojmenované typy anonymních typů. Pokud předáte výsledky dotazu mimo metodu spuštění dotazu, je nutné pojmenovaných typů. Následující příklad provede stejné úkoly, jako předchozí příklad, ale místo pojmenované typy používá anonymní typy:

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

## <a name="compiling-the-code"></a>Kompilování kódu

Vytvoření a kompilace projektu, který cílí na jednu z následujících možností:

- Rozhraní .NET framework verze 3.5 s odkazem na knihovnu System.Core.dll.
- Rozhraní .NET framework verze 4.0 nebo vyšší.
- Verze .NET core 1.0 nebo vyšší.

## <a name="see-also"></a>Viz také

- [LINQ a řetězce (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
- [Inicializátory objektu a kolekce](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
- [Anonymní typy](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
