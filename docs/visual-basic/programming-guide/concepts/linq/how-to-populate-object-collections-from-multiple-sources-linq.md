---
title: 'Postupy: Vyplňování kolekcí objektů z více zdrojů (LINQ) (Visual Basic)'
ms.date: 06/22/2018
ms.assetid: 63062a22-e6a9-42c0-b357-c7c965f58f33
ms.openlocfilehash: 65c7e2c791ba8331416ee2eee292f1e8c4888712
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836354"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-visual-basic"></a>Postupy: Vyplňování kolekcí objektů z více zdrojů (LINQ) (Visual Basic)

Tento příklad ukazuje, jak sloučit data z různých zdrojů do sekvence nových typů.

> [!NOTE]
> Nedoporučujeme připojení dat v paměti nebo dat v systému souborů s daty, která je stále v databázi. Takové spojení mezi doménami může přinést nedefinované výsledky z důvodu různé způsoby, ve kterém mohou být definovány operace spojení pro databázové dotazy a jiné druhy zdrojů. Kromě toho existuje riziko, že tato operace může způsobit výjimku paměti, pokud je příliš velká množství dat v databázi. K připojení dat z databáze pro data v paměti, nejprve volat `ToList` nebo `ToArray` v databázi dotaz a pak provedením příkazu join na vrácené kolekci.

## <a name="to-create-the-data-file"></a>Vytvoření datového souboru

- Zkopírujte soubory names.csv a scores.csv do složky vašeho projektu, jak je popsáno v [jak: Připojte se k obsahu z Nepodobných souborů (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití pojmenovaného typu `Student` k uložení sloučených data ze dvou kolekcích v paměti řetězců, které simulují data z tabulky ve formátu .csv. První kolekce řetězců představuje jména studentů a ID, a druhá kolekce, kterou představuje ID studenta (v prvním sloupci) a čtyři skóre zkoušku. ID je použít jako cizí klíč.

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

V [klauzule Select](../../../../visual-basic/language-reference/queries/select-clause.md) klauzule inicializátoru objektu se používá k vytvoření instance každé nové `Student` s použitím data ze dvou zdrojů.

Pokud nemáte k dispozici pro ukládání výsledků dotazu, může být vhodnější než pojmenované typy anonymních typů. Pokud předáte výsledky dotazu mimo metodu spuštění dotazu, je nutné pojmenovaných typů. Následující příklad provede stejné úkoly, jako předchozí příklad, ale místo pojmenované typy používá anonymní typy:

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

## <a name="compiling-the-code"></a>Kompilování kódu

Vytvoření a kompilace projektu, který cílí na jednu z následujících možností:

- Rozhraní .NET framework verze 3.5 s odkazem na knihovnu System.Core.dll.
- Rozhraní .NET framework verze 4.0 nebo vyšší.
- Verze .NET core 1.0 nebo vyšší.

## <a name="see-also"></a>Viz také:

- [LINQ a řetězce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
