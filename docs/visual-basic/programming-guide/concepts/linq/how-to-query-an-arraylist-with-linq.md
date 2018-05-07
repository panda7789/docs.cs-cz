---
title: 'Postupy: dotazu na ArrayList pomocí LINQ (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 176358a9-d765-4b57-9557-7feb4428138d
ms.openlocfilehash: 56533c4453129a676ed6b97e9afcc008d6ce1137
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-query-an-arraylist-with-linq-visual-basic"></a>Postupy: dotazu na ArrayList pomocí LINQ (Visual Basic)
Při použití LINQ k dotazu neobecnou <xref:System.Collections.IEnumerable> kolekcí, jako <xref:System.Collections.ArrayList>, je potřeba explicitně deklarovat druh proměnné rozsahu tak, aby odrážela konkrétní typy objektů v kolekci. Pokud máte například <xref:System.Collections.ArrayList> z `Student` objekty, vaše [klauzule From](../../../../visual-basic/language-reference/queries/from-clause.md) by měla vypadat takto:  
  
```  
Dim query = From student As Student In arrList   
...  
```  
  
 Zadáním druh proměnné rozsahu jsou přetypování jednotlivé položky <xref:System.Collections.ArrayList> k `Student`.  
  
 Použití proměnné explicitně typové rozsah ve výrazu dotazu je ekvivalentní volání <xref:System.Linq.Enumerable.Cast%2A> metoda. <xref:System.Linq.Enumerable.Cast%2A> vyvolá výjimku, pokud zadané přetypování nelze provést. <xref:System.Linq.Enumerable.Cast%2A> a <xref:System.Linq.Enumerable.OfType%2A> jsou tyto dvě metody standardní – operátor dotazu, které působí na neobecnou <xref:System.Collections.IEnumerable> typy. V jazyce Visual Basic, musíte explicitně zavolat <xref:System.Linq.Enumerable.Cast%2A> metoda ve zdroji dat, aby typ proměnné určitého rozsahu. Další informace najdete v tématu[vztahy typů v operacích dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje jednoduchý dotaz přes <xref:System.Collections.ArrayList>. Všimněte si, že tento příklad používá inicializátory objektů při volání kódu <xref:System.Collections.ArrayList.Add%2A> metoda, ale to není povinné.  
  
```vb  
Imports System.Collections  
Imports System.Linq  
  
Module Module1  
  
    Public Class Student  
        Public Property FirstName As String  
        Public Property LastName As String  
        Public Property Scores As Integer()  
    End Class  
  
    Sub Main()  
  
        Dim student1 As New Student With {.FirstName = "Svetlana",   
                                     .LastName = "Omelchenko",   
                                     .Scores = New Integer() {98, 92, 81, 60}}  
        Dim student2 As New Student With {.FirstName = "Claire",   
                                    .LastName = "O'Donnell",   
                                    .Scores = New Integer() {75, 84, 91, 39}}  
        Dim student3 As New Student With {.FirstName = "Cesar",   
                                    .LastName = "Garcia",   
                                    .Scores = New Integer() {97, 89, 85, 82}}  
        Dim student4 As New Student With {.FirstName = "Sven",   
                                    .LastName = "Mortensen",   
                                    .Scores = New Integer() {88, 94, 65, 91}}  
  
        Dim arrList As New ArrayList()  
        arrList.Add(student1)  
        arrList.Add(student2)  
        arrList.Add(student3)  
        arrList.Add(student4)  
  
        ' Use an explicit type for non-generic collections  
        Dim query = From student As Student In arrList   
                    Where student.Scores(0) > 95   
                    Select student  
  
        For Each student As Student In query  
            Console.WriteLine(student.LastName & ": " & student.Scores(0))  
        Next  
        ' Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
End Module  
' Output:  
'   Omelchenko: 98  
'   Garcia: 97  
```  
  
## <a name="see-also"></a>Viz také  
 [LINQ na objekty (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
