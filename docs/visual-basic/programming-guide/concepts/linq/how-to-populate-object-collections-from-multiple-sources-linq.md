---
title: 'Postupy: Vyplňování kolekcí objektů z více zdrojů (LINQ)'
ms.date: 06/22/2018
ms.assetid: 63062a22-e6a9-42c0-b357-c7c965f58f33
ms.openlocfilehash: 9c6d8ff5165bf886d8aad87b64305819e65361ab
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396516"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-visual-basic"></a>Postupy: naplnění kolekcí objektů z více zdrojů (LINQ) (Visual Basic)

Tento příklad ukazuje, jak sloučit data z různých zdrojů do sekvence nových typů.

> [!NOTE]
> Nepokoušejte se připojit data v paměti nebo data v systému souborů s daty, která jsou stále v databázi. Takové spojení mezi doménami může vracet nedefinované výsledky z důvodu různých způsobů, kterými je možné definovat operace join pro databázové dotazy a jiné typy zdrojů. Kromě toho existuje riziko, že taková operace by mohla způsobit výjimku z důvodu nedostatku paměti, pokud je objem dat v databázi dostatečně velký. Chcete-li spojit data z databáze s daty v paměti, nejprve zavolejte `ToList` nebo `ToArray` v databázovém dotazu a potom proveďte spojení se vrácenou kolekcí.

## <a name="to-create-the-data-file"></a>Vytvoření datového souboru

- Zkopírujte soubory Names. csv a výsledků. CSV do složky projektu, jak je popsáno v tématu [Postupy: spojení obsahu z nepodobných souborů (LINQ) (Visual Basic)](how-to-join-content-from-dissimilar-files-linq.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít pojmenovaný typ `Student` k ukládání sloučených dat ze dvou kolekcí v paměti řetězců, které simulují data tabulky ve formátu CSV. První kolekce řetězců představuje jména a ID studentů a druhá kolekce představuje ID studenta (v prvním sloupci) a čtyři skóre zkoušek. ID se používá jako cizí klíč.

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

V klauzuli [Select klauzule](../../../language-reference/queries/select-clause.md) se inicializátor objektu používá k vytvoření instance každého nového `Student` objektu pomocí dat z těchto dvou zdrojů.

Pokud nepotřebujete ukládat výsledky dotazu, anonymní typy můžou být vhodnější než pojmenované typy. Pojmenované typy jsou požadovány, Pokud předáte výsledky dotazu mimo metodu, ve které je dotaz proveden. Následující příklad provádí stejný úkol jako předchozí příklad, ale používá anonymní typy namísto pojmenovaných typů:

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

## <a name="see-also"></a>Viz také

- [LINQ a řetězce (Visual Basic)](linq-and-strings.md)
