---
title: 'Postupy: Vyplňování kolekcí objektů z více zdrojů (LINQ)'
ms.date: 06/22/2018
ms.assetid: 63062a22-e6a9-42c0-b357-c7c965f58f33
ms.openlocfilehash: 74a2a0f71e575136f1758f72f9a8db72549a9489
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346982"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-visual-basic"></a><span data-ttu-id="d1fcf-102">Postupy: naplnění kolekcí objektů z více zdrojů (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d1fcf-102">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="d1fcf-103">Tento příklad ukazuje, jak sloučit data z různých zdrojů do sekvence nových typů.</span><span class="sxs-lookup"><span data-stu-id="d1fcf-103">This example shows how to merge data from different sources into a sequence of new types.</span></span>

> [!NOTE]
> <span data-ttu-id="d1fcf-104">Nepokoušejte se připojit data v paměti nebo data v systému souborů s daty, která jsou stále v databázi.</span><span class="sxs-lookup"><span data-stu-id="d1fcf-104">Don't try to join in-memory data or data in the file system with data that is still in a database.</span></span> <span data-ttu-id="d1fcf-105">Takové spojení mezi doménami může vracet nedefinované výsledky z důvodu různých způsobů, kterými je možné definovat operace join pro databázové dotazy a jiné typy zdrojů.</span><span class="sxs-lookup"><span data-stu-id="d1fcf-105">Such cross-domain joins can yield undefined results because of different ways in which join operations might be defined for database queries and other types of sources.</span></span> <span data-ttu-id="d1fcf-106">Kromě toho existuje riziko, že taková operace by mohla způsobit výjimku z důvodu nedostatku paměti, pokud je objem dat v databázi dostatečně velký.</span><span class="sxs-lookup"><span data-stu-id="d1fcf-106">Additionally, there is a risk that such an operation could cause an out-of-memory exception if the amount of data in the database is large enough.</span></span> <span data-ttu-id="d1fcf-107">Chcete-li spojit data z databáze s daty v paměti, nejdříve zavolejte `ToList` nebo `ToArray` na dotaz databáze a pak proveďte spojení se vrácenou kolekcí.</span><span class="sxs-lookup"><span data-stu-id="d1fcf-107">To join data from a database to in-memory data, first call `ToList` or `ToArray` on the database query, and then perform the join on the returned collection.</span></span>

## <a name="to-create-the-data-file"></a><span data-ttu-id="d1fcf-108">Vytvoření datového souboru</span><span class="sxs-lookup"><span data-stu-id="d1fcf-108">To create the data file</span></span>

- <span data-ttu-id="d1fcf-109">Zkopírujte soubory Names. csv a výsledků. CSV do složky projektu, jak je popsáno v tématu [Postupy: spojení obsahu z nepodobných souborů (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).</span><span class="sxs-lookup"><span data-stu-id="d1fcf-109">Copy the names.csv and scores.csv files into your project folder, as described in [How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).</span></span>

## <a name="example"></a><span data-ttu-id="d1fcf-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="d1fcf-110">Example</span></span>

<span data-ttu-id="d1fcf-111">Následující příklad ukazuje způsob použití pojmenovaného typu `Student` k uložení sloučených dat ze dvou kolekcí v paměti řetězců, které simulují data tabulky ve formátu CSV.</span><span class="sxs-lookup"><span data-stu-id="d1fcf-111">The following example shows how to use a named type `Student` to store merged data from two in-memory collections of strings that simulate spreadsheet data in .csv format.</span></span> <span data-ttu-id="d1fcf-112">První kolekce řetězců představuje jména a ID studentů a druhá kolekce představuje ID studenta (v prvním sloupci) a čtyři skóre zkoušek.</span><span class="sxs-lookup"><span data-stu-id="d1fcf-112">The first collection of strings represents the student names and IDs, and the second collection represents the student ID (in the first column) and four exam scores.</span></span> <span data-ttu-id="d1fcf-113">ID se používá jako cizí klíč.</span><span class="sxs-lookup"><span data-stu-id="d1fcf-113">The ID is used as the foreign key.</span></span>

```vb
Imports System.Collections.Generic
Imports System.Linq

Class Student
    Public FirstName As String
    Public LastName As String
    Public ID As Integer
    Public ExamScores As List(Of Integer)
End Class

Class PopulateCollection

    Shared Sub Main()

        ' Merge content from spreadsheets into a list of Student objects.

        ' These data files are defined in How to: Join Content from
        ' Dissimilar Files (LINQ).

        ' Each line of names.csv consists of a last name, a first name, and an
        ' ID number, separated by commas. For example, Omelchenko,Svetlana,111
        Dim names As String() = System.IO.File.ReadAllLines("../../../names.csv")

        ' Each line of scores.csv consists of an ID number and four test
        ' scores, separated by commas. For example, 111, 97, 92, 81, 60
        Dim scores As String() = System.IO.File.ReadAllLines("../../../scores.csv")

        ' The following query merges the content of two dissimilar spreadsheets
        ' based on common ID values.
        ' Multiple From clauses are used instead of a Join clause
        ' in order to store the results of scoreLine.Split.
        ' Note the dynamic creation of a list of integers for the
        ' ExamScores member. The first item is skipped in the split string
        ' because it is the student ID, not an exam score.
        Dim queryNamesScores = From nameLine In names
                          Let splitName = nameLine.Split(New Char() {","})
                          From scoreLine In scores
                          Let splitScoreLine = scoreLine.Split(New Char() {","})
                          Where Convert.ToInt32(splitName(2)) = Convert.ToInt32(splitScoreLine(0))
                          Select New Student() With {
                               .FirstName = splitName(1), .LastName = splitName(0), .ID = splitName(2),
                               .ExamScores = (From scoreAsText In splitScoreLine Skip 1
                                             Select Convert.ToInt32(scoreAsText)).ToList()}

        ' Optional. Store the query results for faster access in future
        ' queries. This could be useful with very large data files.
        Dim students As List(Of Student) = queryNamesScores.ToList()

        ' Display each student's name and exam score average.
        For Each s In students
            Console.WriteLine("The average score of " & s.FirstName & " " &
                              s.LastName & " is " & s.ExamScores.Average())
        Next

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub
End Class

' Output:
' The average score of Svetlana Omelchenko is 82.5
' The average score of Claire O'Donnell is 72.25
' The average score of Sven Mortensen is 84.5
' The average score of Cesar Garcia is 88.25
' The average score of Debra Garcia is 67
' The average score of Fadi Fakhouri is 92.25
' The average score of Hanying Feng is 88
' The average score of Hugo Garcia is 85.75
' The average score of Lance Tucker is 81.75
' The average score of Terry Adams is 85.25
' The average score of Eugene Zabokritski is 83
' The average score of Michael Tucker is 92
```

<span data-ttu-id="d1fcf-114">V klauzuli [Select klauzule](../../../../visual-basic/language-reference/queries/select-clause.md) se inicializátor objektu používá k vytvoření instance každého nového objektu `Student` pomocí dat z těchto dvou zdrojů.</span><span class="sxs-lookup"><span data-stu-id="d1fcf-114">In the [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md) clause, an object initializer is used to instantiate each new `Student` object by using the data from the two sources.</span></span>

<span data-ttu-id="d1fcf-115">Pokud nepotřebujete ukládat výsledky dotazu, anonymní typy můžou být vhodnější než pojmenované typy.</span><span class="sxs-lookup"><span data-stu-id="d1fcf-115">If you don't have to store the results of a query, anonymous types can be more convenient than named types.</span></span> <span data-ttu-id="d1fcf-116">Pojmenované typy jsou požadovány, Pokud předáte výsledky dotazu mimo metodu, ve které je dotaz proveden.</span><span class="sxs-lookup"><span data-stu-id="d1fcf-116">Named types are required if you pass the query results outside the method in which the query is executed.</span></span> <span data-ttu-id="d1fcf-117">Následující příklad provádí stejný úkol jako předchozí příklad, ale používá anonymní typy namísto pojmenovaných typů:</span><span class="sxs-lookup"><span data-stu-id="d1fcf-117">The following example performs the same task as the previous example, but uses anonymous types instead of named types:</span></span>

```vb
' Merge the data by using an anonymous type.
' Note the dynamic creation of a list of integers for the
' ExamScores member. We skip 1 because the first string
' in the array is the student ID, not an exam score.
Dim queryNamesScores2 =
    From nameLine In names
    Let splitName = nameLine.Split(New Char() {","})
    From scoreLine In scores
    Let splitScoreLine = scoreLine.Split(New Char() {","})
    Where Convert.ToInt32(splitName(2)) = Convert.ToInt32(splitScoreLine(0))
    Select New With
           {.Last = splitName(0),
            .First = splitName(1),
            .ExamScores = (From scoreAsText In splitScoreLine Skip 1
                           Select Convert.ToInt32(scoreAsText)).ToList()}

' Display each student's name and exam score average.
For Each s In queryNamesScores2
    Console.WriteLine("The average score of " & s.First & " " &
                      s.Last & " is " & s.ExamScores.Average())
Next
```

## <a name="see-also"></a><span data-ttu-id="d1fcf-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d1fcf-118">See also</span></span>

- [<span data-ttu-id="d1fcf-119">LINQ a řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d1fcf-119">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
