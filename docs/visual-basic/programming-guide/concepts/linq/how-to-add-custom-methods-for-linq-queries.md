---
title: 'Postupy: Přidání vlastních metod pro dotazy LINQ (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
ms.openlocfilehash: 6fa212ff05547e8edd3964a6e1c9f76c11cdbe08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a>Postupy: Přidání vlastních metod pro dotazy LINQ (Visual Basic)
Můžete rozšířit sadu metody, které můžete použít pro dotazy LINQ přidáním rozšiřující metody, které <xref:System.Collections.Generic.IEnumerable%601> rozhraní. Kromě standardní průměr nebo maximální operace, například můžete vytvořit vlastní metoda aggregate vypočítat jednu hodnotu z pořadí hodnot. Můžete také vytvořit metodu, která funguje jako vlastní nebo konkrétní data transformace pro pořadí hodnot a vrátí nové pořadí. Příkladem takové metody jsou <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, a <xref:System.Linq.Enumerable.Reverse%2A>.  
  
 Pokud rozšíříte <xref:System.Collections.Generic.IEnumerable%601> rozhraní, můžete použít pro jakékoli vyčíslitelná kolekce vlastních metod. Další informace najdete v tématu [rozšiřující metody](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
## <a name="adding-an-aggregate-method"></a>Přidání agregační metoda  
 Agregační metoda vypočítá jednu hodnotu ze sady hodnot. LINQ poskytuje několik metod agregační, včetně <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, a <xref:System.Linq.Enumerable.Max%2A>. Přidáním metodu rozšíření k můžete vytvořit vlastní metoda aggregate <xref:System.Collections.Generic.IEnumerable%601> rozhraní.  
  
 Následující příklad kódu ukazuje, jak vytvořit volat metody rozšíření `Median` vypočítat medián pro pořadí čísel typu `double`.  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module LINQExtension  
  
    ' Extension method for the IEnumerable(of T) interface.   
    ' The method accepts only values of the Double type.  
    <Extension()>   
    Function Median(ByVal source As IEnumerable(Of Double)) As Double  
        If source.Count = 0 Then  
            Throw New InvalidOperationException("Cannot compute median for an empty set.")  
        End If  
  
        Dim sortedSource = From number In source   
                           Order By number  
  
        Dim itemIndex = sortedSource.Count \ 2  
  
        If sortedSource.Count Mod 2 = 0 Then  
            ' Even number of items in list.  
            Return (sortedSource(itemIndex) + sortedSource(itemIndex - 1)) / 2  
        Else  
            ' Odd number of items in list.  
            Return sortedSource(itemIndex)  
        End If  
    End Function  
End Module  
```  
  
 Volání této metody rozšíření pro jakoukoli kolekci, výčtové stejným způsobem volání z jiné agregační metody <xref:System.Collections.Generic.IEnumerable%601> rozhraní.  
  
> [!NOTE]
>  V jazyce Visual Basic, můžete použít buď volání metody nebo standardní dotaz syntaxe `Aggregate` nebo `Group By` klauzule. Další informace najdete v tématu [Aggregate – klauzule](../../../../visual-basic/language-reference/queries/aggregate-clause.md) a [skupiny pomocí klauzule](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
 Následující příklad kódu ukazuje, jak používat `Median` metodu pro pole typu `double`.  
  
```vb  
Dim numbers1() As Double = {1.9, 2, 8, 4, 5.7, 6, 7.2, 0}  
  
Dim query1 = Aggregate num In numbers1 Into Median()  
  
Console.WriteLine("Double: Median = " & query1)  
```  
  
```vb  
' This code produces the following output:  
'  
' Double: Median = 4.85  
```  
  

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>Přetížení metody agregační tak, aby přijímal různých typů  
 Může dojít k přetížení agregační metodu tak, aby přijímá pořadí různých typů. Standardní přístupu je vytvoření přetížení pro každý typ. Další možností je vytvořit přetížení, které bude trvat obecného typu a převést jej do konkrétního typu pomocí delegáta. Můžete také kombinovat obou přístupů.  
  
#### <a name="to-create-an-overload-for-each-type"></a>Chcete-li vytvořit přetížení pro každý typ  
 Můžete vytvořit na konkrétní přetížení pro každý typ, který chcete podporovat. Následující příklad kódu ukazuje přetížení `Median` metodu `integer` typu.  
  
```vb  
' Integer overload  
  
<Extension()>   
Function Median(ByVal source As IEnumerable(Of Integer)) As Double  
    Return Aggregate num In source Select CDbl(num) Into med = Median()  
End Function  
```  
 Nyní můžete volat `Median` přetížení pro obě `integer` a `double` typů, jak je znázorněno v následujícím kódu:  
  
```vb  
Dim numbers1() As Double = {1.9, 2, 8, 4, 5.7, 6, 7.2, 0}  
  
Dim query1 = Aggregate num In numbers1 Into Median()  
  
Console.WriteLine("Double: Median = " & query1)  
```  
  
```vb  
Dim numbers2() As Integer = {1, 2, 3, 4, 5}  
  
Dim query2 = Aggregate num In numbers2 Into Median()  
  
Console.WriteLine("Integer: Median = " & query2)  
```  
  
```vb  
' This code produces the following output:  
'  
' Double: Median = 4.85  
' Integer: Median = 3  
```  
  
 
#### <a name="to-create-a-generic-overload"></a>Chcete-li vytvořit obecné přetížení  
 Můžete také vytvořit přetížení, které přijímá pořadí obecné objektů. Toto přetížení trvá delegáta jako parametr a používá ho převést na určitý typ pořadí objektů obecného typu.  
  
 Následující kód ukazuje přetížení `Median` metody, která přijímá <xref:System.Func%602> delegovat jako parametr. Tento delegát přebírá objekt obecného typu T a vrátí objekt typu `double`.  
  
```vb  
' Generic overload.  
  
<Extension()>   
Function Median(Of T)(ByVal source As IEnumerable(Of T),   
                      ByVal selector As Func(Of T, Double)) As Double  
    Return Aggregate num In source Select selector(num) Into med = Median()  
End Function  
```  
  
 Nyní můžete volat `Median` metoda sekvenci objekty libovolného typu. Pokud není typ vlastního přetížení metody, budete muset předání parametru delegáta. Výraz lambda v jazyce Visual Basic slouží pro tento účel. Navíc pokud použijete `Aggregate` nebo `Group By` klauzule namísto volání metody, které můžete předat libovolná hodnota nebo výraz, který je v oboru tuto klauzuli.  
  
 Následující příklad kódu ukazuje způsob volání `Median` metodu pro pole celých čísel a pole řetězců. Pro řetězce je vypočítána Medián pro délky v poli řetězců. Příklad ukazuje, jak předat <xref:System.Func%602> delegovat parametru `Median` metoda pro každý případ.  
  
```vb  
Dim numbers3() As Integer = {1, 2, 3, 4, 5}  
  
' You can use num as a parameter for the Median method   
' so that the compiler will implicitly convert its value to double.  
' If there is no implicit conversion, the compiler will  
' display an error message.  
  
Dim query3 = Aggregate num In numbers3 Into Median(num)  
  
Console.WriteLine("Integer: Median = " & query3)  
  
Dim numbers4() As String = {"one", "two", "three", "four", "five"}  
  
' With the generic overload, you can also use numeric properties of objects.  
  
Dim query4 = Aggregate str In numbers4 Into Median(str.Length)  
  
Console.WriteLine("String: Median = " & query4)  
  
' This code produces the following output:  
'  
' Integer: Median = 3  
' String: Median = 4  
```  
## <a name="adding-a-method-that-returns-a-collection"></a>Přidání metody, která vrátí kolekci  
 Můžete rozšířit <xref:System.Collections.Generic.IEnumerable%601> rozhraní s vlastního dotazu metodu, která vrátí pořadí hodnot. V takovém případě metodu musí vracet kolekci typu <xref:System.Collections.Generic.IEnumerable%601>. Tyto metody lze použít filtry nebo data transformací pořadí hodnot.  
  
 Následující příklad ukazuje, jak vytvořit metody rozšíření s názvem `AlternateElements` , vrátí každý další element v kolekci, od první prvek.  
  
```vb  
' Extension method for the IEnumerable(of T) interface.   
' The method returns every other element of a sequence.  
  
<Extension()>   
Function AlternateElements(Of T)(  
    ByVal source As IEnumerable(Of T)  
    ) As IEnumerable(Of T)  
  
    Dim list As New List(Of T)  
    Dim i = 0  
    For Each element In source  
        If (i Mod 2 = 0) Then  
            list.Add(element)  
        End If  
        i = i + 1  
    Next  
    Return list  
End Function  
```  
 Můžete tuto metodu lze volat rozšíření pro jakoukoli kolekci, výčtové stejně, jako by volání z jiné metody <xref:System.Collections.Generic.IEnumerable%601> rozhraní, jak je znázorněno v následujícím kódu:  
  
```vb  
Dim strings() As String = {"a", "b", "c", "d", "e"}  
  
Dim query = strings.AlternateElements()  
  
For Each element In query  
    Console.WriteLine(element)  
Next  
  
' This code produces the following output:  
'  
' a  
' c  
' e  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [Rozšiřující metody](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
