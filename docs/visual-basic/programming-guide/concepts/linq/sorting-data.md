---
title: Řazení dat (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
ms.openlocfilehash: f52000d37df45c97754463de1e81cd523806e9c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="sorting-data-visual-basic"></a>Řazení dat (Visual Basic)
Operace řazení řadí elementy pořadí na základě jednoho nebo více atributů. První kritérium řazení provede primární řazení elementů. Zadáním druhý kritérium řazení lze seřadit elementů v rámci jednotlivých skupin primární řazení.  
  
 Následující obrázek znázorňuje výsledky operace abecedním řazení na posloupnost znaků.  
  
 ![LINQ řazení operaci](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")  
  
 Operátor metody standardní dotazů, které řazení dat jsou uvedené v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka Visual Basic|Další informace|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Řadit podle|Seřadí hodnoty ve vzestupném pořadí.|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|OrderByDescending|Seřadí hodnoty v sestupném pořadí.|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|ThenBy|Provede sekundární řazení ve vzestupném pořadí.|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|ThenByDescending|Provede sekundární řazení v sestupném pořadí.|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|Reverse|Obrátí pořadí prvků v kolekci.|Nelze použít.|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Příklady syntaxe výrazu dotazu  
  
### <a name="primary-sort-examples"></a>Příklady primární řazení  
  
#### <a name="primary-ascending-sort"></a>Primární vzestupné řazení  
 Následující příklad ukazuje, jak používat `Order By` klauzuli v dotazu LINQ pro řazení řetězců v pole podle délka řetězce ve vzestupném pořadí.  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' fox  
' quick  
' brown  
' jumps  
```  
  
#### <a name="primary-descending-sort"></a>Primární sestupné řazení  
 Další příklad ukazuje, jak používat `Order By Descending` klauzuli v dotazu LINQ řetězce seřadit podle jejich první písmeno v sestupném pořadí.  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Substring(0, 1) Descending   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' quick  
' jumps  
' fox  
' brown  
```  
  
### <a name="secondary-sort-examples"></a>Příklady sekundární řazení  
  
#### <a name="secondary-ascending-sort"></a>Sekundární vzestupné řazení  
 Následující příklad ukazuje, jak používat `Order By` klauzuli v dotazu LINQ provádět primární a sekundární řazení řetězců v pole. Řetězce jsou seřazeny primárně podle délky a sekundárně první písmeno řetězce, oba ve vzestupném pořadí.  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length, word.Substring(0, 1)   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' fox  
' the  
' brown  
' jumps  
' quick  
```  
  
#### <a name="secondary-descending-sort"></a>Sekundární sestupné řazení  
 Další příklad ukazuje, jak používat `Order By Descending` klauzuli v dotazu LINQ provést primární řazení ve vzestupném pořadí a sekundární řazení, v sestupném pořadí. Řetězce jsou seřazeny primárně podle délky a sekundárně první písmeno řetězce.  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length, word.Substring(0, 1) Descending   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' fox  
' the  
' quick  
' jumps  
' brown  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq>  
 [Přehled standardních operátorů dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Klauzule Order By](../../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Postupy: řazení výsledků dotazu](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md)  
 [Postupy: řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
