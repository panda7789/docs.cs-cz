---
title: 'Postupy: vyplňování kolekcí objektů z více zdrojů (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 63062a22-e6a9-42c0-b357-c7c965f58f33
ms.openlocfilehash: e890900cd2f53e62a55adef56bfdb27b9787d598
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643312"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-visual-basic"></a>Postupy: vyplňování kolekcí objektů z více zdrojů (LINQ) (Visual Basic)
Tento příklad ukazuje postup slučovat data z různých zdrojů do sekvence nových typů.  
  
> [!NOTE]
>  Nepokoušejte se připojit k data v paměti nebo dat v systému souborů s daty, která je stále v databázi. Takové spojení mezi doménami přispět nedefinované výsledky z důvodu různé způsoby, ve kterém může být definovaná operace spojení pro dotazy na databázi a jiné typy zdrojů. Kromě toho existuje riziko, že takovou operaci může způsobit výjimku z důvodu nedostatku paměti Pokud dostatečně velká množství dat v databázi. K připojení dat z databáze k datům v paměti, první volání `ToList` nebo `ToArray` v databázi dotazu a potom proveďte spojení na vrácená kolekce.  
  
### <a name="to-create-the-data-file"></a>K vytvoření datového souboru  
  
-   Zkopírujte soubory names.csv a scores.csv do složky projektu, jak je popsáno v [postupy: připojení k obsahu z odlišných typů souborů (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat typ s názvem `Student` k uložení sloučenými daty z dvě kolekce v paměti řetězců, které simulují data z tabulky ve formátu CSV. První kolekce řetězců reprezentuje student názvy a ID, a druhá kolekce reprezentuje ID student (ve sloupci první) a čtyři skóre zkoušku. ID je použít jako cizí klíč.  
  
```vb  
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
        ' ExamScores member. We skip the first item in the split string   
        ' because it is the student ID, not an exam score.  
        Dim queryNamesScores = From nameLine In names  
                          Let splitName = nameLine.Split(New Char() {","})  
                          From scoreLine In scores  
                          Let splitScoreLine = scoreLine.Split(New Char() {","})  
                          Where splitName(2) = splitScoreLine(0)  
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
  
 V [klauzule Select](../../../../visual-basic/language-reference/queries/select-clause.md) klauzuli inicializátoru objektu se používá k vytvoření instance každé nové `Student` objekt pomocí dat z těchto dvou zdrojů.  
  
 Pokud nemáte k ukládání výsledků dotazu, může být vhodnější než pojmenované typy anonymní typy. Pokud předáte mimo metodu, ve kterém se spustí dotaz výsledky dotazu jsou požadovány pojmenované typy. Následující příklad provede úlohu stejný jako předchozí příklad, ale místo pojmenované typy používá anonymní typy:  
  
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
    Where splitName(2) = splitScoreLine(0)  
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
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vytvoření projektu, jehož cílem rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na System.Core.dll a `Imports` příkaz pro obor názvů System.Linq.  
  
## <a name="see-also"></a>Viz také  
 [LINQ a řetězce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
