---
title: Odchylky v delegátech (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
ms.openlocfilehash: d857f120be0fe810489ba69edb55af9cc0dd6940
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="variance-in-delegates-visual-basic"></a>Odchylky v delegátech (Visual Basic)
Rozhraní .NET framework 3.5 byla zavedena podpora odchylku odpovídající metoda podpisy s typy delegáta v všechny Delegáti v C# a Visual Basic. To znamená, že můžete přiřadit deleguje pouze metody, které mají odpovídající podpisy, ale také metody, které vracejí informace odvozené typy (kovariance) nebo pracujících s parametry, které mají méně odvozené typy (kontravariance) než je určeno typ delegáta . To zahrnuje obecné a neobecné delegáti.  
  
 Zvažte například následující kód, který má dvě třídy a dvě delegáti: Obecné a neobecné.  
  
```vb  
Public Class First  
End Class  
  
Public Class Second  
    Inherits First  
End Class  
  
Public Delegate Function SampleDelegate(ByVal a As Second) As First  
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R  
```  
  
 Při vytváření delegátů `SampleDelegate` nebo `SampleDelegate(Of A, R)` typy, můžete přiřadit jednu z následujících metod těchto delegáti.  
  
```vb  
' Matching signature.  
Public Shared Function ASecondRFirst(  
    ByVal second As Second) As First  
    Return New First()  
End Function  
  
' The return type is more derived.  
Public Shared Function ASecondRSecond(  
    ByVal second As Second) As Second  
    Return New Second()  
End Function  
  
' The argument type is less derived.  
Public Shared Function AFirstRFirst(  
    ByVal first As First) As First  
    Return New First()  
End Function  
  
' The return type is more derived   
' and the argument type is less derived.  
Public Shared Function AFirstRSecond(  
    ByVal first As First) As Second  
    Return New Second()  
End Function  
```  
  
 Následující příklad kódu ukazuje implicitní převod mezi podpis metody a typu delegáta.  
  
```vb  
' Assigning a method with a matching signature   
' to a non-generic delegate. No conversion is necessary.  
Dim dNonGeneric As SampleDelegate = AddressOf ASecondRFirst  
' Assigning a method with a more derived return type   
' and less derived argument type to a non-generic delegate.  
' The implicit conversion is used.  
Dim dNonGenericConversion As SampleDelegate = AddressOf AFirstRSecond  
  
' Assigning a method with a matching signature to a generic delegate.  
' No conversion is necessary.  
Dim dGeneric As SampleGenericDelegate(Of Second, First) = AddressOf ASecondRFirst  
' Assigning a method with a more derived return type   
' and less derived argument type to a generic delegate.  
' The implicit conversion is used.  
Dim dGenericConversion As SampleGenericDelegate(Of Second, First) = AddressOf AFirstRSecond  
```  
  
 Další příklady najdete v tématu [použití odchylky v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) a [pomocí odchylky pro Func a akce obecní delegáti (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
## <a name="variance-in-generic-type-parameters"></a>Odchylky v obecné parametry typu  
 V rozhraní .NET Framework 4 a novější implicitní převod mezi delegáti, můžete povolit, aby obecní delegáti, které mají různé typy určeného parametry obecného typu lze přiřadit k sobě navzájem, pokud jsou typy zděděn od sebe navzájem podle požadavků odchylky.  
  
 Pokud chcete povolit implicitní převod, je potřeba explicitně deklarovat obecné parametry v delegáta jako kovariantní nebo kontravariant pomocí `in` nebo `out` – klíčové slovo.  
  
 Následující příklad kódu ukazuje, jak můžete vytvořit delegáta, který má parametr kovariantní obecného typu.  
  
```vb  
' Type T is declared covariant by using the out keyword.  
Public Delegate Function SampleGenericDelegate(Of Out T)() As T  
Sub Test()  
    Dim dString As SampleGenericDelegate(Of String) = Function() " "  
    ' You can assign delegates to each other,  
    ' because the type T is declared covariant.  
    Dim dObject As SampleGenericDelegate(Of Object) = dString  
End Sub  
```  
  
 Pokud používáte pouze odchylky podporu tak, aby odpovídaly podpisy, metoda delegovat typy a nepoužívejte `in` a `out` klíčová slova, můžete zjistit, že v některých případech může vytvořit instanci delegáti s identické lambda – výrazy nebo metod, ale nemůžete Přiřaďte jednoho delegáta do jiného.  
  
 V následujícím příkladu kódu `SampleGenericDelegate(Of String)` nelze explicitně převést na `SampleGenericDelegate(Of Object)`, i když `String` dědí `Object`. Tento problém lze vyřešit označení obecný parametr `T` s `out` – klíčové slovo.  
  
```vb  
Public Delegate Function SampleGenericDelegate(Of T)() As T  
Sub Test()  
    Dim dString As SampleGenericDelegate(Of String) = Function() " "  
  
    ' You can assign the dObject delegate  
    ' to the same lambda expression as dString delegate  
    ' because of the variance support for   
    ' matching method signatures with delegate types.  
    Dim dObject As SampleGenericDelegate(Of Object) = Function() " "  
  
    ' The following statement generates a compiler error  
    ' because the generic type T is not marked as covariant.  
    ' Dim dObject As SampleGenericDelegate(Of Object) = dString  
  
End Sub  
```  
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>Obecní delegáti, které mají typ Variant parametry typu v rozhraní .NET Framework  
 Rozhraní .NET framework 4 zavedl podporu odchylky pro parametry obecného typu v několika existující obecní delegáti:  
  
-   `Action` Deleguje z <xref:System> obor názvů, například <xref:System.Action%601> a <xref:System.Action%602>  
  
-   `Func` Deleguje z <xref:System> obor názvů, například <xref:System.Func%601> a <xref:System.Func%602>  
  
-   <xref:System.Predicate%601> Delegovat  
  
-   <xref:System.Comparison%601> Delegovat  
  
-   <xref:System.Converter%602> Delegovat  
  
 Další informace a příklady naleznete v tématu [pomocí odchylky pro Func a akce obecní delegáti (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>Deklarující typ varianty parametry v obecní delegáti  
 Pokud má obecný delegát kovariantní nebo kontravariant parametry obecného typu, ho lze odkazovat jako *variant obecný delegát*.  
  
 Je možné deklarovat parametr obecného typu kovariantní v obecný delegát pomocí `out` – klíčové slovo. Typ kovariantní lze použít pouze jako návratový typ metody a ne jako typ metoda argumenty. Následující příklad kódu ukazuje, jak deklarovat kovariantní obecný delegát.  
  
```vb  
Public Delegate Function DCovariant(Of Out R)() As R  
```  
  
 Je možné deklarovat kontravariant parametr obecného typu v obecný delegát pomocí `in` – klíčové slovo. Typ kontravariant lze použít pouze jako typ argumenty metody a ne jako návratový typ. metoda. Následující příklad kódu ukazuje, jak deklarovat obecný delegát kontravariant.  
  
```vb  
Public Delegate Sub DContravariant(Of In A)(ByVal a As A)  
```  
  
> [!IMPORTANT]
>  `ByRef` Parametry v jazyce Visual Basic nelze označit jako typ variant.  
  
 Je také možné podporovat odchylky a Kovariance v stejného delegáta, ale pro jiný typ parametry. To je ukázáno v následujícím příkladu.  
  
```vb  
Public Delegate Function DVariant(Of In A, Out R)(ByVal a As A) As R  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a>Vytváření instancí a vyvolání Variant obecní delegáti  
 Můžete vytvořit instanci a vyvolání variant delegáti stejně, jako je vytváření instancí a vyvolání invariantní delegáti. V následujícím příkladu je vytvořena instance delegáta pomocí výrazu lambda.  
  
```vb  
Dim dvariant As DVariant(Of String, String) = Function(str) str + " "  
dvariant("test")  
```  
  
### <a name="combining-variant-generic-delegates"></a>Kombinování Variant obecní delegáti  
 Nesmí kombinovat variant delegáti. <xref:System.Delegate.Combine%2A> Metoda nepodporuje převod variant delegáta a očekává delegáti být přesně stejného typu. To může vést ke spuštění výjimka při kombinování delegátů buď pomocí <xref:System.Delegate.Combine%2A> – metoda (v C# a Visual Basic) nebo pomocí `+` – operátor (v jazyku C#), jak je uvedené v následujícím příkladu kódu.  
  
```vb  
Dim actObj As Action(Of Object) = Sub(x) Console.WriteLine("object: {0}", x)  
Dim actStr As Action(Of String) = Sub(x) Console.WriteLine("string: {0}", x)  
  
' The following statement throws an exception at run time.  
' Dim actCombine = [Delegate].Combine(actStr, actObj)  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>Odchylky v parametry obecného typu pro hodnotových a odkazových typech  
 Odchylky pro parametry obecného typu je podporována pro odkazové typy pouze. Například `DVariant(Of Int)`nelze implicitně převést na `DVariant(Of Object)` nebo `DVariant(Of Long)`, protože typ hodnoty je celé číslo.  
  
 Následující příklad ukazuje, že odchylky v obecného typu parametry není podporována u typů hodnot.  
  
```vb  
' The type T is covariant.  
Public Delegate Function DVariant(Of Out T)() As T  
' The type T is invariant.  
Public Delegate Function DInvariant(Of T)() As T  
Sub Test()  
    Dim i As Integer = 0  
    Dim dInt As DInvariant(Of Integer) = Function() i  
    Dim dVaraintInt As DVariant(Of Integer) = Function() i  
  
    ' All of the following statements generate a compiler error  
    ' because type variance in generic parameters is not supported  
    ' for value types, even if generic type parameters are declared variant.  
    ' Dim dObject As DInvariant(Of Object) = dInt  
    ' Dim dLong As DInvariant(Of Long) = dInt  
    ' Dim dVaraintObject As DInvariant(Of Object) = dInt  
    ' Dim dVaraintLong As DInvariant(Of Long) = dInt  
End Sub  
```  
  
## <a name="relaxed-delegate-conversion-in-visual-basic"></a>Volný převod delegáta v jazyce Visual Basic  
 Volný převod delegáta umožňuje větší flexibilitu v odpovídající metoda podpisy s typy delegáta. Například umožňuje vynechejte parametr specifikace a návratové hodnoty funkce vynechat, pokud přiřadíte metody delegáta. Další informace najdete v tématu [volný převod delegáta](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="see-also"></a>Viz také  
 [Obecné typy](~/docs/standard/generics/index.md)  
 [Použití odchylek pro Func a akce obecní delegáti (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
