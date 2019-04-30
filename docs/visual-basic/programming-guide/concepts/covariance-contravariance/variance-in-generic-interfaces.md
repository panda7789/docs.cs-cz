---
title: Odchylky obecných rozhraní (Visual Basic)
ms.date: 07/20/2015
ms.assetid: cf4096d0-4bb3-45a9-9a6b-f01e29a60333
ms.openlocfilehash: 50a1aeb5c17a0f193b9e90ca2167ef298f7ed237
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787215"
---
# <a name="variance-in-generic-interfaces-visual-basic"></a>Odchylky obecných rozhraní (Visual Basic)
Rozhraní .NET framework 4 zavedena podpora odchylku pro existující několik obecných rozhraní. Podpora Variance umožňuje implicitní převod z třídy, které implementují tato rozhraní. Následující rozhraní jsou nyní variant:  
  
- <xref:System.Collections.Generic.IEnumerable%601> (T je kovariantní)  
  
- <xref:System.Collections.Generic.IEnumerator%601> (T je kovariantní)  
  
- <xref:System.Linq.IQueryable%601> (T je kovariantní)  
  
- <xref:System.Linq.IGrouping%602> (`TKey` a `TElement` jsou kovariantní.)  
  
- <xref:System.Collections.Generic.IComparer%601> (T je kontravariantní.)  
  
- <xref:System.Collections.Generic.IEqualityComparer%601> (T je kontravariantní.)  
  
- <xref:System.IComparable%601> (T je kontravariantní.)  
  
 Kovariance povoluje metoda může mít více odvozený návratový typ, než je definován parametr obecného typu rozhraní. K ilustraci této funkce kovariance, vezměte v úvahu těmito obecnými rozhraními: `IEnumerable(Of Object)` a `IEnumerable(Of String)`. `IEnumerable(Of String)` Rozhraní nedědí `IEnumerable(Of Object)` rozhraní. Ale `String` typ dědit `Object` typ a v některých případech můžete chtít přiřadit objekty z těchto rozhraní k sobě navzájem. To je ukázáno v následujícím příkladu kódu.  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 V dřívějších verzích rozhraní .NET Framework, tento kód způsobí chybu kompilace v jazyce Visual Basic s `Option Strict On`. Nyní můžete použít, ale `strings` místo `objects`, jak je znázorněno v předchozím příkladu, protože <xref:System.Collections.Generic.IEnumerable%601> rozhraní je kovariantní.  
  
 Kontravariance umožní metoda může mít typy argumentů, které jsou méně odvozený než je určeno obecný parametr rozhraní. Pro ilustraci kontravariance se předpokládá, že jste vytvořili `BaseComparer` třídy k porovnání instance `BaseClass` třídy. `BaseComparer` Implementuje třída `IEqualityComparer(Of BaseClass)` rozhraní. Protože <xref:System.Collections.Generic.IEqualityComparer%601> rozhraní je kontravariantní, můžete použít `BaseComparer` k porovnání instance tříd, které dědí `BaseClass` třídy. To je ukázáno v následujícím příkladu kódu.  
  
```vb  
' Simple hierarchy of classes.  
Class BaseClass  
End Class  
  
Class DerivedClass  
    Inherits BaseClass  
End Class  
  
' Comparer class.  
Class BaseComparer  
    Implements IEqualityComparer(Of BaseClass)  
  
    Public Function Equals1(ByVal x As BaseClass,  
                            ByVal y As BaseClass) As Boolean _  
                            Implements IEqualityComparer(Of BaseClass).Equals  
        Return (x.Equals(y))  
    End Function  
  
    Public Function GetHashCode1(ByVal obj As BaseClass) As Integer _  
        Implements IEqualityComparer(Of BaseClass).GetHashCode  
        Return obj.GetHashCode  
    End Function  
End Class  
Sub Test()  
    Dim baseComparer As IEqualityComparer(Of BaseClass) = New BaseComparer  
    ' Implicit conversion of IEqualityComparer(Of BaseClass) to   
    ' IEqualityComparer(Of DerivedClass).  
    Dim childComparer As IEqualityComparer(Of DerivedClass) = baseComparer  
End Sub  
```  
  
 Další příklady najdete v tématu [použití odchylky v rozhraní pro obecné kolekce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).  
  
 Odchylky obecných rozhraní je podporována pouze pro typy odkazů. Typy hodnot nepodporují variance. Například `IEnumerable(Of Integer)` nejde implicitně převést na `IEnumerable(Of Object)`, protože celá čísla jsou reprezentovány hodnotového typu.  
  
```vb  
Dim integers As IEnumerable(Of Integer) = New List(Of Integer)  
' The following statement generates a compiler error  
' with Option Strict On, because Integer is a value type.  
' Dim objects As IEnumerable(Of Object) = integers  
```  
  
 Taky je dobré si uvědomit, že jsou stále invariantní třídy, které implementují rozhraní variant. Například i když <xref:System.Collections.Generic.List%601> implementuje rozhraní kovariantní <xref:System.Collections.Generic.IEnumerable%601>, nelze implicitně převést `List(Of Object)` k `List(Of String)`. To je znázorněno v následujícím příkladu kódu.  
  
```vb  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim list As List(Of Object) = New List(Of String)  
  
' You can use the interface object instead.  
Dim listObjects As IEnumerable(Of Object) = New List(Of String)  
```  
  
## <a name="see-also"></a>Viz také:

- [Použití odchylky v rozhraní pro obecné kolekce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)
- [Vytváření variantních obecných rozhraní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)
- [Obecná rozhraní](../../../../standard/generics/interfaces.md)
- [Odchylky v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
