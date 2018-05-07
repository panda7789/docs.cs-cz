---
title: Vytváření variantních obecných rozhraní (C#)
ms.date: 07/20/2015
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
ms.openlocfilehash: 882bd0aa4497a99b2cf80e96f13f433ae74aad59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="creating-variant-generic-interfaces-c"></a>Vytváření variantních obecných rozhraní (C#)
Parametry obecného typu rozhraní jako kovariantní můžou deklarovat nebo kontravariant. *Kovariance* umožňuje metody rozhraní do mají více odvozené návratové typy než definované parametry obecného typu. *Kontravariance* umožňuje metody rozhraní tak, aby měl typy argumentů, které jsou odvozené menší než je určeno obecné parametry. Obecná rozhraní, které má kovariantní nebo kontravariant se označuje jako parametry obecného typu *variant*.  
  
> [!NOTE]
>  Rozhraní .NET framework 4 zavedly odchylku podporu pro několik existujících obecných rozhraní. Seznam variantních rozhraní v rozhraní .NET Framework, naleznete v části [odchylky obecných rozhraní (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  
  
## <a name="declaring-variant-generic-interfaces"></a>Deklarující variantních obecných rozhraní  
 Je možné deklarovat variantních obecných rozhraní pomocí `in` a `out` klíčová slova pro parametry obecného typu.  
  
> [!IMPORTANT]
>  `ref`, `in`, a `out` parametry v jazyce C# nemůže být typu variant. Typy hodnot také nepodporují odchylky.  
  
 Je možné deklarovat parametr obecného typu kovariantní pomocí `out` – klíčové slovo. Typ kovariantní musí splňovat následující podmínky:  
  
-   Typ je použit pouze jako návratový typ metody rozhraní a nepoužívá jako typ metoda argumenty. To je znázorněno v následujícím příkladu, ve kterém typ `R` je deklarovaná kovariant.  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        R GetSomething();  
        // The following statement generates a compiler error.  
        // void SetSometing(R sampleArg);  
  
    }  
    ```  
  
     Existuje jedna výjimka tohoto pravidla. Pokud máte obecný delegát kontravariant jako parametru metody, můžete jako parametr obecného typu typ pro delegáta. Tento koncept je znázorněn typ `R` v následujícím příkladu. Další informace najdete v tématu [odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [pomocí odchylky pro Func a akce obecní delegáti (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        void DoSomething(Action<R> callback);  
    }  
    ```  
  
-   Typ není používána jako obecná omezení pro metody rozhraní. To je znázorněno v následujícím kódu.  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        // The following statement generates a compiler error  
        // because you can use only contravariant or invariant types  
        // in generic contstraints.  
        // void DoSomething<T>() where T : R;  
    }  
    ```  
  
 Je možné deklarovat kontravariant parametr obecného typu pomocí `in` – klíčové slovo. Typ kontravariant lze použít pouze jako typ argumenty metody a ne jako návratový typ metody rozhraní. Typ kontravariant můžete použít také pro obecná omezení. Následující kód ukazuje, jak používat obecná omezení pro jednu z jeho metod a kontravariant rozhraní deklarovat.  
  
```csharp  
interface IContravariant<in A>  
{  
    void SetSomething(A sampleArg);  
    void DoSomething<T>() where T : A;  
    // The following statement generates a compiler error.  
    // A GetSomething();              
}  
```  
  
 Je také možné podporovat kovariance a kontravariance v stejné rozhraní, ale pro jiný typ parametry, jak je znázorněno v následujícím příkladu kódu.  
  
```csharp  
interface IVariant<out R, in A>  
{  
    R GetSomething();  
    void SetSomething(A sampleArg);  
    R GetSetSometings(A sampleArg);  
}  
```  
  
## <a name="implementing-variant-generic-interfaces"></a>Implementuje variantních obecných rozhraní  
 Variantní obecná rozhraní se implementovat v třídy pomocí stejné syntaxe, který se používá pro invariantní rozhraní. Následující příklad kódu ukazuje, jak implementovat kovariantní rozhraní v obecné třídy.  
  
```csharp  
interface ICovariant<out R>  
{  
    R GetSomething();  
}  
class SampleImplementation<R> : ICovariant<R>  
{  
    public R GetSomething()  
    {  
        // Some code.  
        return default(R);  
    }  
}  
```  
  
 Třídy, které implementují rozhraní variant jsou neutrální. Zvažte například následující kód.  
  
```csharp  
// The interface is covariant.  
ICovariant<Button> ibutton = new SampleImplementation<Button>();  
ICovariant<Object> iobj = ibutton;  
  
// The class is invariant.  
SampleImplementation<Button> button = new SampleImplementation<Button>();  
// The following statement generates a compiler error  
// because classes are invariant.  
// SampleImplementation<Object> obj = button;  
```  
  
## <a name="extending-variant-generic-interfaces"></a>Rozšíření variantních obecných rozhraní  
 Když rozšíříte variantní obecná rozhraní, budete muset použít `in` a `out` klíčová slova, která explicitně zadáte, jestli podporuje rozhraní odvozené odchylky. Kompilátor nelze odvodit odchylku z rozhraní, které se rozšiřuje. Zvažte například následující rozhraní.  
  
```csharp  
interface ICovariant<out T> { }  
interface IInvariant<T> : ICovariant<T> { }  
interface IExtCovariant<out T> : ICovariant<T> { }  
```  
  
 V `IInvariant<T>` rozhraní, parametr obecného typu `T` je invariantní, zatímco v `IExtCovariant<out T>` parametr typu je kovariant, i když obě rozhraní rozšíření stejné rozhraní. Stejné pravidlo se použije pro parametry obecného typu kontravariant.  
  
 Můžete vytvořit rozhraní, které rozšiřuje rozhraní kde parametr typu Obecné `T` je kovariant a rozhraní tam, kde je kontravariant Pokud v rozšíření rozhraní parametr obecného typu `T` je neutrální. To je znázorněno v následujícím příkladu kódu.  
  
```csharp  
interface ICovariant<out T> { }  
interface IContravariant<in T> { }  
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }  
```  
  
 Ale pokud parametr obecného typu `T` je deklarován kovariantní v jedno rozhraní, nelze deklarovat je kontravariant v rozšíření rozhraní a naopak. To je znázorněno v následujícím příkladu kódu.  
  
```csharp  
interface ICovariant<out T> { }  
// The following statement generates a compiler error.  
// interface ICoContraVariant<in T> : ICovariant<T> { }  
```  
  
### <a name="avoiding-ambiguity"></a>Zamezení nejednoznačnosti  
 Při implementaci variantních obecných rozhraní odchylku může někdy dojít k nejednoznačnosti. To je nutno.  
  
 Například pokud explicitní implementace stejné variant obecná rozhraní s jinou obecné parametry typu do jedné třídy, můžete vytvořit nejednoznačnosti. Kompilátor nevytváří chybu v takovém případě ale není zadaný, které implementace rozhraní bude vybrána za běhu. To může vést k jemně chyby v kódu. Vezměte v úvahu následující příklad kódu.  
  
```csharp  
// Simple class hierarchy.  
class Animal { }  
class Cat : Animal { }  
class Dog : Animal { }  
  
// This class introduces ambiguity  
// because IEnumerable<out T> is covariant.  
class Pets : IEnumerable<Cat>, IEnumerable<Dog>  
{  
    IEnumerator<Cat> IEnumerable<Cat>.GetEnumerator()  
    {  
        Console.WriteLine("Cat");  
        // Some code.  
        return null;  
    }  
  
    IEnumerator IEnumerable.GetEnumerator()  
    {  
        // Some code.  
        return null;  
    }  
  
    IEnumerator<Dog> IEnumerable<Dog>.GetEnumerator()  
    {  
        Console.WriteLine("Dog");  
        // Some code.  
        return null;  
    }  
}  
class Program  
{  
    public static void Test()  
    {  
        IEnumerable<Animal> pets = new Pets();  
        pets.GetEnumerator();  
    }  
}  
```  
  
 V tomto příkladu neurčené jak `pets.GetEnumerator` metoda zvolí mezi `Cat` a `Dog`. To může způsobit problémy ve vašem kódu.  
  
## <a name="see-also"></a>Viz také  
 [Odchylky obecných rozhraní (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [Použití odchylek pro Func a akce obecní delegáti (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
