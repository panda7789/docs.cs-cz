---
title: 'Postupy: Přidávání vlastních metod do dotazů LINQ (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
ms.openlocfilehash: e45dfc6b516f1e5f5e9f7f667bbbfd5768330ffa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645584"
---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a>Postupy: Přidávání vlastních metod do dotazů LINQ (Visual Basic)
Můžete rozšířit sadu metod, které můžete použít pro LINQ dotazy přidáním rozšiřující metody, které <xref:System.Collections.Generic.IEnumerable%601> rozhraní. Kromě standardní průměr nebo maximální operace, například můžete vytvořit vlastní agregační metody pro výpočet jednu hodnotu ze sekvence hodnot. Můžete také vytvořit metodu, která funguje jako vlastní filtr a transformovat data specifická pro sekvenci hodnot a vrátí novou sekvenci. Příklady těchto metod jsou <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, a <xref:System.Linq.Enumerable.Reverse%2A>.  
  
 Když rozšíříte <xref:System.Collections.Generic.IEnumerable%601> rozhraní, vlastních metod můžete použít na jakékoli vyčíslitelné kolekce. Další informace najdete v tématu [rozšiřující metody](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
## <a name="adding-an-aggregate-method"></a>Přidání agregované – metoda  
 Metodu agregace vypočítá jedna hodnota ze sady hodnot. LINQ poskytuje několik metod agregace, včetně <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, a <xref:System.Linq.Enumerable.Max%2A>. Můžete vytvořit vlastní metoda aggregate přidáním metodu rozšíření k <xref:System.Collections.Generic.IEnumerable%601> rozhraní.  
  
 Následující příklad kódu ukazuje, jak vytvořit rozšiřující metoda volá `Median` vypočítat medián pro sekvenci čísel typu `double`.  
  
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
  
 Volání této metody rozšíření pro jakékoli vyčíslitelné kolekce stejným způsobem, volání metod agregační z <xref:System.Collections.Generic.IEnumerable%601> rozhraní.  
  
> [!NOTE]
>  V jazyce Visual Basic můžete použít buď volání metody nebo syntaxe standardního dotazu `Aggregate` nebo `Group By` klauzuli. Další informace najdete v tématu [Aggregate – klauzule](../../../../visual-basic/language-reference/queries/aggregate-clause.md) a [klauzule Group](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
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
  

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>Přetížení agregační metodu tak, aby přijímal různé typy  
 Můžete použít přetížení agregační metodu tak, aby přijímá pořadí podle různých typů. Standardní přístup je přetížení pro každý typ vytvoření. Další možností je vytvořit přetížení, které bude trvat obecného typu a proveďte převod na určitý typ pomocí delegáta. Oba přístupy můžete také kombinovat.  
  
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
 Můžete také vytvořit přetížení přijímající posloupnost obecných objektů. Toto přetížení přebírá jako parametr delegáta a použije ho k převedení sekvence objektů obecného typu určitého typu.  
  
 Následující kód ukazuje přetížení `Median` metodu, která přebírá <xref:System.Func%602> jako parametr. Tento delegát přebírá objekt obecný typ a vrátí objekt typu `double`.  
  
```vb  
' Generic overload.  
  
<Extension()>   
Function Median(Of T)(ByVal source As IEnumerable(Of T),   
                      ByVal selector As Func(Of T, Double)) As Double  
    Return Aggregate num In source Select selector(num) Into med = Median()  
End Function  
```  
  
 Nyní můžete volat `Median` metodu pro sekvenci objektů libovolného typu. Pokud typ nemá žádné vlastní přetížení metody, musíte předat parametr delegátu. V jazyce Visual Basic můžete použít výraz lambda pro tento účel. Navíc pokud použijete `Aggregate` nebo `Group By` klauzule namísto volání metody, které můžete předat libovolná hodnota nebo výraz, který je v oboru tuto klauzuli.  
  
 Následující příklad kódu ukazuje, jak volat `Median` metodu pro pole celých čísel a pole řetězců. Pro řetězce se vypočítá Medián pro délky řetězce v poli. Tento příklad ukazuje, jak předat <xref:System.Func%602> parametr do delegáta `Median` metodu pro každý případ.  
  
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
 Můžete rozšířit <xref:System.Collections.Generic.IEnumerable%601> rozhraní s metodou vlastního dotazu, která vrátí sekvenci hodnot. V takovém případě metoda musí vracet kolekci typu <xref:System.Collections.Generic.IEnumerable%601>. Tyto metody slouží k použití filtrů nebo data transformací na sekvenci hodnot.  
  
 Následující příklad ukazuje, jak vytvořit metodu rozšíření s názvem `AlternateElements` , která vrací každý prvek v kolekci, počínaje prvním prvkem.  
  
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
 Lze tuto metodu lze volat rozšíření pro jakékoli vyčíslitelné kolekce stejně, jako by volání z jiné metody <xref:System.Collections.Generic.IEnumerable%601> rozhraní, jak je znázorněno v následujícím kódu:  
  
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
  
## <a name="see-also"></a>Viz také:
- <xref:System.Collections.Generic.IEnumerable%601>
- [Rozšiřující metody](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
