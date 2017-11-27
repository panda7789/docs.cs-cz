---
title: "Vytváření variantních obecných rozhraní (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4037dd2-dfe9-4811-9150-93d4e8b20113
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 380af3b29172b1fa13d42d33e574201607cb804b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="creating-variant-generic-interfaces-visual-basic"></a>Vytváření variantních obecných rozhraní (Visual Basic)
Parametry obecného typu rozhraní jako kovariantní můžou deklarovat nebo kontravariant. *Kovariance* umožňuje metody rozhraní do mají více odvozené návratové typy než definované parametry obecného typu. *Kontravariance* umožňuje metody rozhraní tak, aby měl typy argumentů, které jsou odvozené menší než je určeno obecné parametry. Obecná rozhraní, které má kovariantní nebo kontravariant se označuje jako parametry obecného typu *variant*.  
  
> [!NOTE]
>  Rozhraní .NET framework 4 zavedly odchylku podporu pro několik existujících obecných rozhraní. Seznam variantních rozhraní v rozhraní .NET Framework, naleznete v části [odchylky obecných rozhraní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  
  
## <a name="declaring-variant-generic-interfaces"></a>Deklarující variantních obecných rozhraní  
 Je možné deklarovat variantních obecných rozhraní pomocí `in` a `out` klíčová slova pro parametry obecného typu.  
  
> [!IMPORTANT]
>  `ByRef`Parametry v jazyce Visual Basic nelze variant. Typy hodnot také nepodporují odchylky.  
  
 Je možné deklarovat parametr obecného typu kovariantní pomocí `out` – klíčové slovo. Typ kovariantní musí splňovat následující podmínky:  
  
-   Typ je použit pouze jako návratový typ metody rozhraní a nepoužívá jako typ metoda argumenty. To je znázorněno v následujícím příkladu, ve kterém typ `R` je deklarovaná kovariant.  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Function GetSomething() As R  
        ' The following statement generates a compiler error.  
        ' Sub SetSomething(ByVal sampleArg As R)  
    End Interface  
    ```  
  
     Existuje jedna výjimka tohoto pravidla. Pokud máte obecný delegát kontravariant jako parametru metody, můžete jako parametr obecného typu typ pro delegáta. Tento koncept je znázorněn typ `R` v následujícím příkladu. Další informace najdete v tématu [odchylky v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [pomocí odchylky pro Func a akce obecní delegáti (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Sub DoSomething(ByVal callback As Action(Of R))  
    End Interface  
    ```  
  
-   Typ není používána jako obecná omezení pro metody rozhraní. To je znázorněno v následujícím kódu.  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        ' The following statement generates a compiler error  
        ' because you can use only contravariant or invariant types  
        ' in generic contstraints.  
        ' Sub DoSomething(Of T As R)()  
    End Interface  
    ```  
  
 Je možné deklarovat kontravariant parametr obecného typu pomocí `in` – klíčové slovo. Typ kontravariant lze použít pouze jako typ argumenty metody a ne jako návratový typ metody rozhraní. Typ kontravariant můžete použít také pro obecná omezení. Následující kód ukazuje, jak používat obecná omezení pro jednu z jeho metod a kontravariant rozhraní deklarovat.  
  
```vb  
Interface IContravariant(Of In A)  
    Sub SetSomething(ByVal sampleArg As A)  
    Sub DoSomething(Of T As A)()  
    ' The following statement generates a compiler error.  
    ' Function GetSomething() As A  
End Interface  
```  
  
 Je také možné podporovat kovariance a kontravariance v stejné rozhraní, ale pro jiný typ parametry, jak je znázorněno v následujícím příkladu kódu.  
  
```vb  
Interface IVariant(Of Out R, In A)  
    Function GetSomething() As R  
    Sub SetSomething(ByVal sampleArg As A)  
    Function GetSetSomething(ByVal sampleArg As A) As R  
End Interface  
```  
  
 V jazyce Visual Basic nelze deklarovat události v variantních rozhraní bez zadání typu delegáta. Navíc variant rozhraní vnořené třídy, výčty a struktury, ale mohou mít vnořené rozhraní. To je znázorněno v následujícím kódu.  
  
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
  
## <a name="implementing-variant-generic-interfaces"></a>Implementuje variantních obecných rozhraní  
 Variantní obecná rozhraní se implementovat v třídy pomocí stejné syntaxe, který se používá pro invariantní rozhraní. Následující příklad kódu ukazuje, jak implementovat kovariantní rozhraní v obecné třídy.  
  
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
  
 Třídy, které implementují rozhraní variant jsou neutrální. Zvažte například následující kód.  
  
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
  
## <a name="extending-variant-generic-interfaces"></a>Rozšíření variantních obecných rozhraní  
 Když rozšíříte variantní obecná rozhraní, budete muset použít `in` a `out` klíčová slova, která explicitně zadáte, jestli podporuje rozhraní odvozené odchylky. Kompilátor nelze odvodit odchylku z rozhraní, které se rozšiřuje. Zvažte například následující rozhraní.  
  
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
  
 V `Invariant(Of T)` rozhraní, parametr obecného typu `T` je invariantní, zatímco v `IExtCovariant (Of Out T)`parametr typu je kovariant, i když obě rozhraní rozšíření stejné rozhraní. Stejné pravidlo se použije pro parametry obecného typu kontravariant.  
  
 Můžete vytvořit rozhraní, které rozšiřuje rozhraní kde parametr typu Obecné `T` je kovariant a rozhraní tam, kde je kontravariant Pokud v rozšíření rozhraní parametr obecného typu `T` je neutrální. To je znázorněno v následujícím příkladu kódu.  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
Interface IContravariant(Of In T)  
End Interface  
  
Interface IInvariant(Of T)  
    Inherits ICovariant(Of T), IContravariant(Of T)  
End Interface  
```  
  
 Ale pokud parametr obecného typu `T` je deklarován kovariantní v jedno rozhraní, nelze deklarovat je kontravariant v rozšíření rozhraní a naopak. To je znázorněno v následujícím příkladu kódu.  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
' The following statements generate a compiler error.  
' Interface ICoContraVariant(Of In T)  
'     Inherits ICovariant(Of T)  
' End Interface  
```  
  
### <a name="avoiding-ambiguity"></a>Zamezení nejednoznačnosti  
 Při implementaci variantních obecných rozhraní odchylku může někdy dojít k nejednoznačnosti. To je nutno.  
  
 Například pokud explicitní implementace stejné variant obecná rozhraní s jinou obecné parametry typu do jedné třídy, můžete vytvořit nejednoznačnosti. Kompilátor nevytváří chybu v takovém případě ale není zadaný, které implementace rozhraní bude vybrána za běhu. To může vést k jemně chyby v kódu. Vezměte v úvahu následující příklad kódu.  
  
> [!NOTE]
>  S `Option Strict Off`, Visual Basic vygeneruje upozornění kompilátoru po implementaci rozhraní nejednoznačných. S `Option Strict On`, vygeneruje chybu kompilátoru jazyka Visual Basic.  
  
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
  
 V tomto příkladu neurčené jak `pets.GetEnumerator` metoda zvolí mezi `Cat` a `Dog`. To může způsobit problémy ve vašem kódu.  
  
## <a name="see-also"></a>Viz také  
 [Odchylky obecných rozhraní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [Použití odchylek pro Func a akce obecní delegáti (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
