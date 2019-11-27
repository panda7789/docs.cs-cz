---
title: 'Postupy: Přidávání vlastních metod do dotazů LINQ'
ms.date: 07/20/2015
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
ms.openlocfilehash: 3004a9c9c7abeffd9993b848ad765e7ae2dc8876
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353375"
---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a>Postupy: Přidání vlastních metod pro dotazy LINQ (Visual Basic)

Můžete rozšířit sadu metod, které lze použít pro dotazy LINQ přidáním rozšiřujících metod do rozhraní <xref:System.Collections.Generic.IEnumerable%601>. Například kromě standardních průměrných nebo maximálních operací můžete vytvořit vlastní agregační metodu pro výpočet jedné hodnoty z sekvence hodnot. Můžete také vytvořit metodu, která funguje jako vlastní filtr nebo konkrétní transformace dat pro sekvenci hodnot a vrátí novou sekvenci. Příklady takových metod jsou <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>a <xref:System.Linq.Enumerable.Reverse%2A>.

Když rozšíříte rozhraní <xref:System.Collections.Generic.IEnumerable%601>, můžete použít vlastní metody do jakékoli vyčíslitelné kolekce. Další informace naleznete v tématu [metody rozšíření](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).

## <a name="adding-an-aggregate-method"></a>Přidání agregační metody

Agregační metoda vypočítá jednu hodnotu ze sady hodnot. LINQ poskytuje několik agregačních metod, včetně <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>a <xref:System.Linq.Enumerable.Max%2A>. Můžete vytvořit vlastní agregační metodu přidáním metody rozšíření do rozhraní <xref:System.Collections.Generic.IEnumerable%601>.

Následující příklad kódu ukazuje, jak vytvořit metodu rozšíření nazvanou `Median` pro výpočet mediánu pro sekvenci čísel typu `double`.

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

Tuto metodu rozšíření pro každou vyčíslitelné kolekci můžete zavolat stejným způsobem jako jiné agregační metody z rozhraní <xref:System.Collections.Generic.IEnumerable%601>.

> [!NOTE]
> V Visual Basic můžete buď použít volání metody, nebo standardní syntaxi dotazu pro klauzuli `Aggregate` nebo `Group By`. Další informace naleznete v tématu [klauzule Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md) a [klauzule GROUP by](../../../../visual-basic/language-reference/queries/group-by-clause.md).

Následující příklad kódu ukazuje, jak použít metodu `Median` pro pole typu `double`.

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

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>Přetížení agregované metody pro příjem různých typů

Můžete přetížit agregační metodu tak, aby mohla přijímat sekvence různých typů. Standardní přístup je vytvořit přetížení pro každý typ. Další možností je vytvořit přetížení, které bude přebírat obecný typ a převést jej na konkrétní typ pomocí delegáta. Oba přístupy můžete také kombinovat.

#### <a name="to-create-an-overload-for-each-type"></a>Pro vytvoření přetížení pro každý typ

Můžete vytvořit konkrétní přetížení pro každý typ, který chcete podporovat. Následující příklad kódu ukazuje přetížení metody `Median` pro typ `integer`.

```vb
' Integer overload

<Extension()>
Function Median(ByVal source As IEnumerable(Of Integer)) As Double
    Return Aggregate num In source Select CDbl(num) Into med = Median()
End Function
```

Nyní můžete volat `Median` přetížení pro typy `integer` a `double`, jak je znázorněno v následujícím kódu:

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

#### <a name="to-create-a-generic-overload"></a>Vytvoření obecného přetížení

Můžete také vytvořit přetížení, které přijímá sekvenci generických objektů. Toto přetížení přebírá jako parametr delegáta a používá ho k převodu sekvence objektů obecného typu na konkrétní typ.

Následující kód ukazuje přetížení metody `Median`, která přebírá <xref:System.Func%602> delegáta jako parametr. Tento delegát přebírá objekt generického typu T a vrátí objekt typu `double`.

```vb
' Generic overload.

<Extension()>
Function Median(Of T)(ByVal source As IEnumerable(Of T),
                      ByVal selector As Func(Of T, Double)) As Double
    Return Aggregate num In source Select selector(num) Into med = Median()
End Function
```

Nyní můžete zavolat metodu `Median` pro sekvenci objektů libovolného typu. Pokud typ nemá vlastní metodu přetížení, je nutné předat parametr delegáta. V Visual Basic můžete pro tento účel použít výraz lambda. Také, pokud použijete klauzuli `Aggregate` nebo `Group By` namísto volání metody, můžete předat libovolnou hodnotu nebo výraz, který je v rozsahu této klauzule.

Následující příklad kódu ukazuje, jak zavolat metodu `Median` pro pole celých čísel a pole řetězců. Pro řetězce se počítá medián pro délky řetězců v poli. Příklad ukazuje, jak předat parametr delegáta <xref:System.Func%602> do metody `Median` pro každý případ.

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

Rozhraní <xref:System.Collections.Generic.IEnumerable%601> můžete roztáhnout vlastní metodou dotazu, která vrací sekvenci hodnot. V tomto případě musí metoda vracet kolekci typu <xref:System.Collections.Generic.IEnumerable%601>. Tyto metody lze použít k aplikování filtrů nebo transformací dat na sekvenci hodnot.

Následující příklad ukazuje, jak vytvořit metodu rozšíření s názvem `AlternateElements`, která vrátí všechny ostatní prvky v kolekci počínaje prvním prvkem.

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

Tuto metodu rozšíření můžete zavolat pro všechny vyčíslitelné kolekce stejně, jako byste volali jiné metody z rozhraní <xref:System.Collections.Generic.IEnumerable%601>, jak je znázorněno v následujícím kódu:

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
