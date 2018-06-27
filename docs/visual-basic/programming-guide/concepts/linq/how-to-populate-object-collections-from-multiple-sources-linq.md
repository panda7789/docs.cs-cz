---
title: 'Postupy: vyplňování kolekcí objektů z více zdrojů (LINQ) (Visual Basic)'
ms.date: 06/22/2018
ms.assetid: 63062a22-e6a9-42c0-b357-c7c965f58f33
ms.openlocfilehash: 097a41614b4e7fb48c3ef3903faec8ed9ee3d5b6
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948446"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-visual-basic"></a><span data-ttu-id="b82b6-102">Postupy: vyplňování kolekcí objektů z více zdrojů (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b82b6-102">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="b82b6-103">Tento příklad ukazuje postup slučovat data z různých zdrojů do sekvence nových typů.</span><span class="sxs-lookup"><span data-stu-id="b82b6-103">This example shows how to merge data from different sources into a sequence of new types.</span></span>

> [!NOTE]
> <span data-ttu-id="b82b6-104">Nemáte pokusí připojit k data v paměti nebo dat v systému souborů s daty, která je stále v databázi.</span><span class="sxs-lookup"><span data-stu-id="b82b6-104">Don't try to join in-memory data or data in the file system with data that is still in a database.</span></span> <span data-ttu-id="b82b6-105">Takové spojení mezi doménami přispět nedefinované výsledky z důvodu různé způsoby, ve kterém může být definovaná operace spojení pro dotazy na databázi a jiné typy zdrojů.</span><span class="sxs-lookup"><span data-stu-id="b82b6-105">Such cross-domain joins can yield undefined results because of different ways in which join operations might be defined for database queries and other types of sources.</span></span> <span data-ttu-id="b82b6-106">Kromě toho existuje riziko, že takovou operaci může způsobit výjimku z důvodu nedostatku paměti Pokud dostatečně velká množství dat v databázi.</span><span class="sxs-lookup"><span data-stu-id="b82b6-106">Additionally, there is a risk that such an operation could cause an out-of-memory exception if the amount of data in the database is large enough.</span></span> <span data-ttu-id="b82b6-107">K připojení dat z databáze k datům v paměti, první volání `ToList` nebo `ToArray` v databázi dotazu a potom proveďte spojení na vrácená kolekce.</span><span class="sxs-lookup"><span data-stu-id="b82b6-107">To join data from a database to in-memory data, first call `ToList` or `ToArray` on the database query, and then perform the join on the returned collection.</span></span>

## <a name="to-create-the-data-file"></a><span data-ttu-id="b82b6-108">K vytvoření datového souboru</span><span class="sxs-lookup"><span data-stu-id="b82b6-108">To create the data file</span></span>

- <span data-ttu-id="b82b6-109">Zkopírujte soubory names.csv a scores.csv do složky projektu, jak je popsáno v [postupy: připojení k obsahu z odlišných typů souborů (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).</span><span class="sxs-lookup"><span data-stu-id="b82b6-109">Copy the names.csv and scores.csv files into your project folder, as described in [How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).</span></span>

## <a name="example"></a><span data-ttu-id="b82b6-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="b82b6-110">Example</span></span>

<span data-ttu-id="b82b6-111">Následující příklad ukazuje, jak používat typ s názvem `Student` k uložení sloučenými daty z dvě kolekce v paměti řetězců, které simulují data z tabulky ve formátu CSV.</span><span class="sxs-lookup"><span data-stu-id="b82b6-111">The following example shows how to use a named type `Student` to store merged data from two in-memory collections of strings that simulate spreadsheet data in .csv format.</span></span> <span data-ttu-id="b82b6-112">První kolekce řetězců reprezentuje student názvy a ID, a druhá kolekce reprezentuje ID student (ve sloupci první) a čtyři skóre zkoušku.</span><span class="sxs-lookup"><span data-stu-id="b82b6-112">The first collection of strings represents the student names and IDs, and the second collection represents the student ID (in the first column) and four exam scores.</span></span> <span data-ttu-id="b82b6-113">ID je použít jako cizí klíč.</span><span class="sxs-lookup"><span data-stu-id="b82b6-113">The ID is used as the foreign key.</span></span>

```vb
Imports System
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
                               .FirstName = splitName(0), .LastName = splitName(1), .ID = splitName(2),
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
' The average score of Omelchenko Svetlana is 82.5
' The average score of O'Donnell Claire is 72.25
' The average score of Mortensen Sven is 84.5
' The average score of Garcia Cesar is 88.25
' The average score of Garcia Debra is 67
' The average score of Fakhouri Fadi is 92.25
' The average score of Feng Hanying is 88
' The average score of Garcia Hugo is 85.75
' The average score of Tucker Lance is 81.75
' The average score of Adams Terry is 85.25
' The average score of Zabokritski Eugene is 83
' The average score of Tucker Michael is 92
```

<span data-ttu-id="b82b6-114">V [klauzule Select](../../../../visual-basic/language-reference/queries/select-clause.md) klauzuli inicializátoru objektu se používá k vytvoření instance každé nové `Student` objekt pomocí dat z těchto dvou zdrojů.</span><span class="sxs-lookup"><span data-stu-id="b82b6-114">In the [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md) clause, an object initializer is used to instantiate each new `Student` object by using the data from the two sources.</span></span>

<span data-ttu-id="b82b6-115">Pokud nemáte k ukládání výsledků dotazu, může být vhodnější než pojmenované typy anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="b82b6-115">If you don't have to store the results of a query, anonymous types can be more convenient than named types.</span></span> <span data-ttu-id="b82b6-116">Pokud předáte mimo metodu, ve kterém se spustí dotaz výsledky dotazu jsou požadovány pojmenované typy.</span><span class="sxs-lookup"><span data-stu-id="b82b6-116">Named types are required if you pass the query results outside the method in which the query is executed.</span></span> <span data-ttu-id="b82b6-117">Následující příklad provede úlohu stejný jako předchozí příklad, ale místo pojmenované typy používá anonymní typy:</span><span class="sxs-lookup"><span data-stu-id="b82b6-117">The following example performs the same task as the previous example, but uses anonymous types instead of named types:</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="b82b6-118">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b82b6-118">Compiling the code</span></span>

<span data-ttu-id="b82b6-119">Vytvoření a kompilace projektu, jehož cílem jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="b82b6-119">Create and compile a project that targets one of the following options:</span></span>

- <span data-ttu-id="b82b6-120">Rozhraní .NET framework verze 3.5 nebo vyšší s odkazem na System.Core.dll.</span><span class="sxs-lookup"><span data-stu-id="b82b6-120">.NET Framework version 3.5 or higher with a reference to System.Core.dll.</span></span>
- <span data-ttu-id="b82b6-121">.NET core verze 1.0 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="b82b6-121">.NET Core version 1.0 or higher.</span></span>

## <a name="see-also"></a><span data-ttu-id="b82b6-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b82b6-122">See also</span></span>

[<span data-ttu-id="b82b6-123">LINQ a řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b82b6-123">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
