---
title: "Postupy: vyplňování kolekcí objektů z více zdrojů (LINQ) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 8ad7d480-b46c-4ccc-8c57-76f2d04ccc6d
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a3d3f0f9380e13addac38e32d4cc095d60e19bcf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-c"></a><span data-ttu-id="f74aa-102">Postupy: vyplňování kolekcí objektů z více zdrojů (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="f74aa-102">How to: Populate Object Collections from Multiple Sources (LINQ) (C#)</span></span>
<span data-ttu-id="f74aa-103">Tento příklad ukazuje postup slučovat data z různých zdrojů do sekvence nových typů.</span><span class="sxs-lookup"><span data-stu-id="f74aa-103">This example shows how to merge data from different sources into a sequence of new types.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f74aa-104">Nepokoušejte se připojit k data v paměti nebo dat v systému souborů s daty, která je stále v databázi.</span><span class="sxs-lookup"><span data-stu-id="f74aa-104">Do not try to join in-memory data or data in the file system with data that is still in a database.</span></span> <span data-ttu-id="f74aa-105">Takové spojení mezi doménami přispět nedefinované výsledky z důvodu různé způsoby, ve kterém může být definovaná operace spojení pro dotazy na databázi a jiné typy zdrojů.</span><span class="sxs-lookup"><span data-stu-id="f74aa-105">Such cross-domain joins can yield undefined results because of different ways in which join operations might be defined for database queries and other types of sources.</span></span> <span data-ttu-id="f74aa-106">Kromě toho existuje riziko, že takovou operaci může způsobit výjimku z důvodu nedostatku paměti Pokud dostatečně velká množství dat v databázi.</span><span class="sxs-lookup"><span data-stu-id="f74aa-106">Additionally, there is a risk that such an operation could cause an out-of-memory exception if the amount of data in the database is large enough.</span></span> <span data-ttu-id="f74aa-107">K připojení dat z databáze k datům v paměti, první volání `ToList` nebo `ToArray` v databázi dotazu a potom proveďte spojení na vrácená kolekce.</span><span class="sxs-lookup"><span data-stu-id="f74aa-107">To join data from a database to in-memory data, first call `ToList` or `ToArray` on the database query, and then perform the join on the returned collection.</span></span>  
  
### <a name="to-create-the-data-file"></a><span data-ttu-id="f74aa-108">K vytvoření datového souboru</span><span class="sxs-lookup"><span data-stu-id="f74aa-108">To create the data file</span></span>  
  
-   <span data-ttu-id="f74aa-109">Zkopírujte soubory names.csv a scores.csv do složky projektu, jak je popsáno v [postupy: připojení k obsahu z odlišných typů souborů (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).</span><span class="sxs-lookup"><span data-stu-id="f74aa-109">Copy the names.csv and scores.csv files into your project folder, as described in [How to: Join Content from Dissimilar Files (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f74aa-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="f74aa-110">Example</span></span>  
 <span data-ttu-id="f74aa-111">Následující příklad ukazuje, jak používat typ s názvem `Student` k uložení sloučenými daty z dvě kolekce v paměti řetězců, které simulují data z tabulky ve formátu CSV.</span><span class="sxs-lookup"><span data-stu-id="f74aa-111">The following example shows how to use a named type `Student` to store merged data from two in-memory collections of strings that simulate spreadsheet data in .csv format.</span></span> <span data-ttu-id="f74aa-112">První kolekce řetězců reprezentuje student názvy a ID, a druhá kolekce reprezentuje ID student (ve sloupci první) a čtyři skóre zkoušku.</span><span class="sxs-lookup"><span data-stu-id="f74aa-112">The first collection of strings represents the student names and IDs, and the second collection represents the student ID (in the first column) and four exam scores.</span></span> <span data-ttu-id="f74aa-113">ID je použít jako cizí klíč.</span><span class="sxs-lookup"><span data-stu-id="f74aa-113">The ID is used as the foreign key.</span></span>  
  
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
  
 <span data-ttu-id="f74aa-114">V [vyberte](../../../../csharp/language-reference/keywords/select-clause.md) klauzuli inicializátoru objektu se používá k vytvoření instance každé nové `Student` objekt pomocí dat z těchto dvou zdrojů.</span><span class="sxs-lookup"><span data-stu-id="f74aa-114">In the [select](../../../../csharp/language-reference/keywords/select-clause.md) clause, an object initializer is used to instantiate each new `Student` object by using the data from the two sources.</span></span>  
  
 <span data-ttu-id="f74aa-115">Pokud nemáte k ukládání výsledků dotazu, může být vhodnější než pojmenované typy anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="f74aa-115">If you do not have to store the results of a query, anonymous types can be more convenient than named types.</span></span> <span data-ttu-id="f74aa-116">Pokud předáte mimo metodu, ve kterém se spustí dotaz výsledky dotazu jsou požadovány pojmenované typy.</span><span class="sxs-lookup"><span data-stu-id="f74aa-116">Named types are required if you pass the query results outside the method in which the query is executed.</span></span> <span data-ttu-id="f74aa-117">Následující příklad provede úlohu stejný jako předchozí příklad, ale místo pojmenované typy používá anonymní typy:</span><span class="sxs-lookup"><span data-stu-id="f74aa-117">The following example performs the same task as the previous example, but uses anonymous types instead of named types:</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="f74aa-118">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f74aa-118">Compiling the Code</span></span>  
 <span data-ttu-id="f74aa-119">Vytvoření projektu, jehož cílem rozhraní .NET Framework verze 3.5 nebo vyšší, s odkazem na System.Core.dll a `using` direktivy pro obory názvů System.Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="f74aa-119">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f74aa-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="f74aa-120">See Also</span></span>  
 [<span data-ttu-id="f74aa-121">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="f74aa-121">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
 [<span data-ttu-id="f74aa-122">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="f74aa-122">Object and Collection Initializers</span></span>](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [<span data-ttu-id="f74aa-123">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="f74aa-123">Anonymous Types</span></span>](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
