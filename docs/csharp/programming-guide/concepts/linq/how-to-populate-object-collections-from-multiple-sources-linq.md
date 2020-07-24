---
title: Jak naplnit kolekce objektů z více zdrojů (LINQ) (C#)
description: Naučte se, jak sloučit data z různých zdrojů do sekvence nových typů pomocí LINQ v jazyce C#. Tyto příklady používají anonymní i pojmenované typy.
ms.date: 06/12/2018
ms.assetid: 8ad7d480-b46c-4ccc-8c57-76f2d04ccc6d
ms.openlocfilehash: 9dc9f98ae09e0fe3437b5d2ccab32b3dbcd93714
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104721"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-c"></a>Jak naplnit kolekce objektů z více zdrojů (LINQ) (C#)

Tento příklad ukazuje, jak sloučit data z různých zdrojů do sekvence nových typů.

> [!NOTE]
> Nepokoušejte se připojit data v paměti nebo data v systému souborů s daty, která jsou stále v databázi. Takové spojení mezi doménami může vracet nedefinované výsledky z důvodu různých způsobů, kterými je možné definovat operace join pro databázové dotazy a jiné typy zdrojů. Kromě toho existuje riziko, že taková operace by mohla způsobit výjimku z důvodu nedostatku paměti, pokud je objem dat v databázi dostatečně velký. Chcete-li spojit data z databáze s daty v paměti, nejprve zavolejte `ToList` nebo `ToArray` v databázovém dotazu a potom proveďte spojení se vrácenou kolekcí.

## <a name="to-create-the-data-file"></a>Vytvoření datového souboru

Zkopírujte soubory names.csv a scores.csv do složky projektu, jak je popsáno v tématu [Postup připojení obsahu z nepodobných souborů (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít pojmenovaný typ `Student` k ukládání sloučených dat ze dvou kolekcí v paměti řetězců, které simulují data tabulky ve formátu CSV. První kolekce řetězců představuje jména a ID studentů a druhá kolekce představuje ID studenta (v prvním sloupci) a čtyři skóre zkoušek. ID se používá jako cizí klíč.

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
        // These data files are defined in How to join content from
        // dissimilar files (LINQ).

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

V klauzuli [Select](../../../language-reference/keywords/select-clause.md) se inicializátor objektu používá k vytvoření instance každého nového `Student` objektu pomocí dat z těchto dvou zdrojů.

Pokud nepotřebujete ukládat výsledky dotazu, anonymní typy můžou být vhodnější než pojmenované typy. Pojmenované typy jsou požadovány, Pokud předáte výsledky dotazu mimo metodu, ve které je dotaz proveden. Následující příklad provádí stejný úkol jako předchozí příklad, ale používá anonymní typy namísto pojmenovaných typů:

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

## <a name="see-also"></a>Viz také

- [LINQ a řetězce (C#)](./linq-and-strings.md)
- [Inicializátory objektu a kolekce](../../classes-and-structs/object-and-collection-initializers.md)
- [Anonymní typy](../../classes-and-structs/anonymous-types.md)
