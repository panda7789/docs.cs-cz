---
title: 'Postupy: vyplňování kolekcí objektů z více zdrojů (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 8ad7d480-b46c-4ccc-8c57-76f2d04ccc6d
ms.openlocfilehash: 3ff51b0b5f04a44f83db2590bd7005097b1c0161
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323349"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-c"></a>Postupy: vyplňování kolekcí objektů z více zdrojů (LINQ) (C#)
Tento příklad ukazuje postup slučovat data z různých zdrojů do sekvence nových typů.  
  
> [!NOTE]
>  Nepokoušejte se připojit k data v paměti nebo dat v systému souborů s daty, která je stále v databázi. Takové spojení mezi doménami přispět nedefinované výsledky z důvodu různé způsoby, ve kterém může být definovaná operace spojení pro dotazy na databázi a jiné typy zdrojů. Kromě toho existuje riziko, že takovou operaci může způsobit výjimku z důvodu nedostatku paměti Pokud dostatečně velká množství dat v databázi. K připojení dat z databáze k datům v paměti, první volání `ToList` nebo `ToArray` v databázi dotazu a potom proveďte spojení na vrácená kolekce.  
  
### <a name="to-create-the-data-file"></a>K vytvoření datového souboru  
  
-   Zkopírujte soubory names.csv a scores.csv do složky projektu, jak je popsáno v [postupy: připojení k obsahu z odlišných typů souborů (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat typ s názvem `Student` k uložení sloučenými daty z dvě kolekce v paměti řetězců, které simulují data z tabulky ve formátu CSV. První kolekce řetězců reprezentuje student názvy a ID, a druhá kolekce reprezentuje ID student (ve sloupci první) a čtyři skóre zkoušku. ID je použít jako cizí klíč.  
  
```csharp  
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
        // creation of a list of ints for the ExamScores member. We skip   
        // the first item in the split string because it is the student ID,   
        // not an exam score.  
        IEnumerable<Student> queryNamesScores =  
            from nameLine in names  
            let splitName = nameLine.Split(',')  
            from scoreLine in scores  
            let splitScoreLine = scoreLine.Split(',')  
            where splitName[2] == splitScoreLine[0]  
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
  
 V [vyberte](../../../../csharp/language-reference/keywords/select-clause.md) klauzuli inicializátoru objektu se používá k vytvoření instance každé nové `Student` objekt pomocí dat z těchto dvou zdrojů.  
  
 Pokud nemáte k ukládání výsledků dotazu, může být vhodnější než pojmenované typy anonymní typy. Pokud předáte mimo metodu, ve kterém se spustí dotaz výsledky dotazu jsou požadovány pojmenované typy. Následující příklad provede úlohu stejný jako předchozí příklad, ale místo pojmenované typy používá anonymní typy:  
  
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
    where splitName[2] == splitScoreLine[0]  
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
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vytvoření projektu, jehož cílem rozhraní .NET Framework verze 3.5 nebo vyšší, s odkazem na System.Core.dll a `using` direktivy pro obory názvů System.Linq a System.IO.  
  
## <a name="see-also"></a>Viz také  
 [LINQ a řetězce (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
 [Inicializátory objektu a kolekce](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [Anonymní typy](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
