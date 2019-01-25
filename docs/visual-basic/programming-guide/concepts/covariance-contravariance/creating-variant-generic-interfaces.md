---
title: Vytváření variantních obecných rozhraní (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d4037dd2-dfe9-4811-9150-93d4e8b20113
ms.openlocfilehash: d6afddf018b4608418f82fa851d018f2c3e1d0fb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663255"
---
# <a name="creating-variant-generic-interfaces-visual-basic"></a>Vytváření variantních obecných rozhraní (Visual Basic)
Je možné deklarovat parametry obecného typu v rozhraní jako kovariantní nebo kontravariantní. *Kovariance* umožňuje mají více odvozené návratové typy než určené parametry obecného typu metody rozhraní. *Kontravariance* umožňuje mít typy argumentů, které jsou méně odvozený než je určeno obecné parametry metody rozhraní. Obecná rozhraní, který má kovariantní nebo kontravariantní parametry obecného typu se nazývá *variant*.  
  
> [!NOTE]
>  Rozhraní .NET framework 4 zavedena podpora odchylku pro existující několik obecných rozhraní. Seznam variantních rozhraní v rozhraní .NET Framework najdete v tématu [odchylky obecných rozhraní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  
  
## <a name="declaring-variant-generic-interfaces"></a>Deklarující variantních obecných rozhraní  
 Je možné deklarovat s použitím variantních obecných rozhraní `in` a `out` klíčová slova pro parametry obecného typu.  
  
> [!IMPORTANT]
>  `ByRef` Parametry v jazyce Visual Basic nemůže být typu variant. Typy hodnot také nepodporují variance.  
  
 Je možné deklarovat parametr obecného typu kovariantní s použitím `out` – klíčové slovo. Typ kovariantního musí splňovat následující podmínky:  
  
-   Typ je použít jenom jako návratový typ metody rozhraní a nelze použít jako typ argumentů metody. To je znázorněno v následujícím příkladu, ve kterém typ `R` je deklarována jako kovariantní.  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Function GetSomething() As R  
        ' The following statement generates a compiler error.  
        ' Sub SetSomething(ByVal sampleArg As R)  
    End Interface  
    ```  
  
     Existuje jedna výjimka tohoto pravidla. Pokud máte kontravariantní obecného delegáta jako parametr metody, můžete použít typ jako parametr obecného typu pro delegáta. To je znázorněno typem `R` v následujícím příkladu. Další informace najdete v tématu [odchylky v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [pomocí odchylku pro delegáty Func a Action obecný (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Sub DoSomething(ByVal callback As Action(Of R))  
    End Interface  
    ```  
  
-   Typ se nepoužívá jako obecná omezení pro metody rozhraní. To je znázorněno v následujícím kódu.  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        ' The following statement generates a compiler error  
        ' because you can use only contravariant or invariant types  
        ' in generic contstraints.  
        ' Sub DoSomething(Of T As R)()  
    End Interface  
    ```  
  
 Můžete deklarovat kontravariantního parametru obecného typu pomocí `in` – klíčové slovo. Kontravariantního typu lze použít pouze jako argumenty metody typu, nikoli jako návratový typ metody rozhraní. Kontravariantního typu můžete použít také pro obecná omezení. Následující kód ukazuje, jak deklarovat kontravariantní rozhraní a používat obecná omezení pro jednu z jeho metod.  
  
```vb  
Interface IContravariant(Of In A)  
    Sub SetSomething(ByVal sampleArg As A)  
    Sub DoSomething(Of T As A)()  
    ' The following statement generates a compiler error.  
    ' Function GetSomething() As A  
End Interface  
```  
  
 Je také možné podporují kovarianci a kontravarianci ve stejné rozhraní, ale pro jiný typ parametrů, jak je znázorněno v následujícím příkladu kódu.  
  
```vb  
Interface IVariant(Of Out R, In A)  
    Function GetSomething() As R  
    Sub SetSomething(ByVal sampleArg As A)  
    Function GetSetSomething(ByVal sampleArg As A) As R  
End Interface  
```  
  
 V jazyce Visual Basic nelze deklarovat události v rozhraní typu variant bez zadání typu delegáta. Také variant rozhraní nemůžou být vnořené třídy, výčty a struktury, ale mohou být vnořené rozhraní. To je znázorněno v následujícím kódu.  
  
```vb  
Interface ICovariant(Of Out R)  
    ' The following statement generates a compiler error.  
    ' Event SampleEvent()  
    ' The following statement specifies the delegate type and   
    ' does not generate an error.  
    Event AnotherEvent As EventHandler  
  
    ' The following statements generate compiler errors,  
    ' because a variant interface cannot have  
    ' nested enums, classes, or structures.  
  
    'Enum SampleEnum : test : End Enum  
    'Class SampleClass : End Class  
    'Structure SampleStructure : Dim value As Integer : End Structure  
  
    ' Variant interfaces can have nested interfaces.  
    Interface INested : End Interface  
End Interface  
```  
  
## <a name="implementing-variant-generic-interfaces"></a>Implementující variantních obecných rozhraní  
 Implementujete variantních obecných rozhraní v třídy pomocí stejné syntaxe, který se používá pro invariantní rozhraní. Následující příklad kódu ukazuje, jak implementovat kovariantní rozhraní v obecné třídě.  
  
```vb  
Interface ICovariant(Of Out R)  
    Function GetSomething() As R  
End Interface  
  
Class SampleImplementation(Of R)  
    Implements ICovariant(Of R)  
    Public Function GetSomething() As R _  
    Implements ICovariant(Of R).GetSomething  
        ' Some code.  
    End Function  
End Class  
```  
  
 Třídy, které implementují rozhraní varianty se nebudou měnit. Zvažte například následující kód.  
  
```vb  
 The interface is covariant.  
Dim ibutton As ICovariant(Of Button) =  
    New SampleImplementation(Of Button)  
Dim iobj As ICovariant(Of Object) = ibutton  
  
' The class is invariant.  
Dim button As SampleImplementation(Of Button) =  
    New SampleImplementation(Of Button)  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim obj As SampleImplementation(Of Object) = button  
```  
  
## <a name="extending-variant-generic-interfaces"></a>Rozšiřování variantních obecných rozhraní  
 Když rozšíříte variantních obecných rozhraní, je nutné použít `in` a `out` klíčových slov pro explicitně určit, zda odvozená rozhraní podporuje variance. Kompilátor nelze odvodit odchýlení od rozhraní, které se rozšiřuje. Zvažte například následující rozhraní.  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
Interface IInvariant(Of T)  
    Inherits ICovariant(Of T)  
End Interface  
  
Interface IExtCovariant(Of Out T)  
    Inherits ICovariant(Of T)  
End Interface  
```  
  
 V `Invariant(Of T)` rozhraní, parametr obecného typu `T` je neutrální, zatímco v `IExtCovariant (Of Out T)`parametr typu je kovariant, i když obě rozhraní rozšíření stejné rozhraní. Stejné pravidlo platí pro parametry obecného typu kontravariantní.  
  
 Můžete vytvořit rozhraní, které rozšiřuje rozhraní kde obecný parametr typu `T` je kovariantní a rozhraní, kde jsou kontravariantní Pokud ve rozšíření rozhraní parametr obecného typu `T` je neutrální. To je znázorněno v následujícím příkladu kódu.  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
Interface IContravariant(Of In T)  
End Interface  
  
Interface IInvariant(Of T)  
    Inherits ICovariant(Of T), IContravariant(Of T)  
End Interface  
```  
  
 Ale pokud parametr obecného typu `T` je deklarován kovariantního v jednom rozhraní, nelze deklarovat je kontravariantní rozšíření rozhraní nebo naopak. To je znázorněno v následujícím příkladu kódu.  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
' The following statements generate a compiler error.  
' Interface ICoContraVariant(Of In T)  
'     Inherits ICovariant(Of T)  
' End Interface  
```  
  
### <a name="avoiding-ambiguity"></a>Jak se vyhnout nejednoznačnosti  
 Při implementaci variantních obecných rozhraní variance může někdy vést k nejednoznačnosti. To by se jim vyhnout.  
  
 Například pokud se explicitně implementovat stejné variantních obecné rozhraní s parametry různých obecného typu v jedné třídy, můžete vytvořit nejednoznačnosti. Kompilátor nevytváří chybu v tomto případě ale není zadaný, která implementace rozhraní se zvolí za běhu. To může vést k drobným chybám v kódu. Zvažte následující příklad kódu.  
  
> [!NOTE]
>  S `Option Strict Off`, Visual Basic generuje upozornění kompilátoru při implementaci rozhraní nejednoznačný. S `Option Strict On`, Visual Basic vygeneruje chybu kompilátoru.  
  
```vb  
' Simple class hierarchy.  
Class Animal  
End Class  
  
Class Cat  
    Inherits Animal  
End Class  
  
Class Dog  
    Inherits Animal  
End Class  
  
' This class introduces ambiguity  
' because IEnumerable(Of Out T) is covariant.  
Class Pets  
    Implements IEnumerable(Of Cat), IEnumerable(Of Dog)  
  
    Public Function GetEnumerator() As IEnumerator(Of Cat) _  
        Implements IEnumerable(Of Cat).GetEnumerator  
        Console.WriteLine("Cat")  
        ' Some code.  
    End Function  
  
    Public Function GetEnumerator1() As IEnumerator(Of Dog) _  
        Implements IEnumerable(Of Dog).GetEnumerator  
        Console.WriteLine("Dog")  
        ' Some code.  
    End Function  
  
    Public Function GetEnumerator2() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
        ' Some code.  
    End Function  
End Class  
  
Sub Main()  
    Dim pets As IEnumerable(Of Animal) = New Pets()  
    pets.GetEnumerator()  
End Sub  
```  
  
 V tomto příkladu neurčená jak `pets.GetEnumerator` metoda zvolí mezi `Cat` a `Dog`. To může způsobit problémy v kódu.  
  
## <a name="see-also"></a>Viz také:
- [Odchylky obecných rozhraní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [Použití odchylek pro delegáty Func a Action obecný (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
