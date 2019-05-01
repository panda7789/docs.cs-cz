---
title: 'Postupy: Vyplňování kolekcí objektů z více zdrojů (LINQ) (Visual Basic)'
ms.date: 06/22/2018
ms.assetid: 63062a22-e6a9-42c0-b357-c7c965f58f33
ms.openlocfilehash: 65c7e2c791ba8331416ee2eee292f1e8c4888712
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024323"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-visual-basic"></a><span data-ttu-id="38015-102">Postupy: Vyplňování kolekcí objektů z více zdrojů (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38015-102">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="38015-103">Tento příklad ukazuje, jak sloučit data z různých zdrojů do sekvence nových typů.</span><span class="sxs-lookup"><span data-stu-id="38015-103">This example shows how to merge data from different sources into a sequence of new types.</span></span>

> [!NOTE]
> <span data-ttu-id="38015-104">Nedoporučujeme připojení dat v paměti nebo dat v systému souborů s daty, která je stále v databázi.</span><span class="sxs-lookup"><span data-stu-id="38015-104">Don't try to join in-memory data or data in the file system with data that is still in a database.</span></span> <span data-ttu-id="38015-105">Takové spojení mezi doménami může přinést nedefinované výsledky z důvodu různé způsoby, ve kterém mohou být definovány operace spojení pro databázové dotazy a jiné druhy zdrojů.</span><span class="sxs-lookup"><span data-stu-id="38015-105">Such cross-domain joins can yield undefined results because of different ways in which join operations might be defined for database queries and other types of sources.</span></span> <span data-ttu-id="38015-106">Kromě toho existuje riziko, že tato operace může způsobit výjimku paměti, pokud je příliš velká množství dat v databázi.</span><span class="sxs-lookup"><span data-stu-id="38015-106">Additionally, there is a risk that such an operation could cause an out-of-memory exception if the amount of data in the database is large enough.</span></span> <span data-ttu-id="38015-107">K připojení dat z databáze pro data v paměti, nejprve volat `ToList` nebo `ToArray` v databázi dotaz a pak provedením příkazu join na vrácené kolekci.</span><span class="sxs-lookup"><span data-stu-id="38015-107">To join data from a database to in-memory data, first call `ToList` or `ToArray` on the database query, and then perform the join on the returned collection.</span></span>

## <a name="to-create-the-data-file"></a><span data-ttu-id="38015-108">Vytvoření datového souboru</span><span class="sxs-lookup"><span data-stu-id="38015-108">To create the data file</span></span>

- <span data-ttu-id="38015-109">Zkopírujte soubory names.csv a scores.csv do složky vašeho projektu, jak je popsáno v [jak: Připojte se k obsahu z Nepodobných souborů (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).</span><span class="sxs-lookup"><span data-stu-id="38015-109">Copy the names.csv and scores.csv files into your project folder, as described in [How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).</span></span>

## <a name="example"></a><span data-ttu-id="38015-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="38015-110">Example</span></span>

<span data-ttu-id="38015-111">Následující příklad ukazuje způsob použití pojmenovaného typu `Student` k uložení sloučených data ze dvou kolekcích v paměti řetězců, které simulují data z tabulky ve formátu .csv.</span><span class="sxs-lookup"><span data-stu-id="38015-111">The following example shows how to use a named type `Student` to store merged data from two in-memory collections of strings that simulate spreadsheet data in .csv format.</span></span> <span data-ttu-id="38015-112">První kolekce řetězců představuje jména studentů a ID, a druhá kolekce, kterou představuje ID studenta (v prvním sloupci) a čtyři skóre zkoušku.</span><span class="sxs-lookup"><span data-stu-id="38015-112">The first collection of strings represents the student names and IDs, and the second collection represents the student ID (in the first column) and four exam scores.</span></span> <span data-ttu-id="38015-113">ID je použít jako cizí klíč.</span><span class="sxs-lookup"><span data-stu-id="38015-113">The ID is used as the foreign key.</span></span>

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

<span data-ttu-id="38015-114">V [klauzule Select](../../../../visual-basic/language-reference/queries/select-clause.md) klauzule inicializátoru objektu se používá k vytvoření instance každé nové `Student` s použitím data ze dvou zdrojů.</span><span class="sxs-lookup"><span data-stu-id="38015-114">In the [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md) clause, an object initializer is used to instantiate each new `Student` object by using the data from the two sources.</span></span>

<span data-ttu-id="38015-115">Pokud nemáte k dispozici pro ukládání výsledků dotazu, může být vhodnější než pojmenované typy anonymních typů.</span><span class="sxs-lookup"><span data-stu-id="38015-115">If you don't have to store the results of a query, anonymous types can be more convenient than named types.</span></span> <span data-ttu-id="38015-116">Pokud předáte výsledky dotazu mimo metodu spuštění dotazu, je nutné pojmenovaných typů.</span><span class="sxs-lookup"><span data-stu-id="38015-116">Named types are required if you pass the query results outside the method in which the query is executed.</span></span> <span data-ttu-id="38015-117">Následující příklad provede stejné úkoly, jako předchozí příklad, ale místo pojmenované typy používá anonymní typy:</span><span class="sxs-lookup"><span data-stu-id="38015-117">The following example performs the same task as the previous example, but uses anonymous types instead of named types:</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="38015-118">Kompilování kódu</span><span class="sxs-lookup"><span data-stu-id="38015-118">Compiling the code</span></span>

<span data-ttu-id="38015-119">Vytvoření a kompilace projektu, který cílí na jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="38015-119">Create and compile a project that targets one of the following options:</span></span>

- <span data-ttu-id="38015-120">Rozhraní .NET framework verze 3.5 s odkazem na knihovnu System.Core.dll.</span><span class="sxs-lookup"><span data-stu-id="38015-120">.NET Framework version 3.5 with a reference to System.Core.dll.</span></span>
- <span data-ttu-id="38015-121">Rozhraní .NET framework verze 4.0 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="38015-121">.NET Framework version 4.0 or higher.</span></span>
- <span data-ttu-id="38015-122">Verze .NET core 1.0 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="38015-122">.NET Core version 1.0 or higher.</span></span>

## <a name="see-also"></a><span data-ttu-id="38015-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38015-123">See also</span></span>

- [<span data-ttu-id="38015-124">LINQ a řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38015-124">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
