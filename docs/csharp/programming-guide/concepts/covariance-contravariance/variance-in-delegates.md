---
title: Odchylka v delegátech (C#)
ms.date: 07/20/2015
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
ms.openlocfilehash: fd1b4824dc3d8f12347e01b804a6e39fe2e086c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169711"
---
# <a name="variance-in-delegates-c"></a>Odchylka v delegátech (C#)
Rozhraní .NET Framework 3.5 zavedlo podporu odchylky pro odpovídající podpisy metod s typy delegátů ve všech delegátech v jazyce C#. To znamená, že delegátům můžete přiřadit nejen metody, které mají odpovídající podpisy, ale také metody, které vracejí více odvozených typů (kovariance) nebo které přijímají parametry, které mají méně odvozených typů (kontravariance) než ty, které jsou určeny typem delegáta. . To zahrnuje obecné i obecné delegáty.  
  
 Zvažte například následující kód, který má dvě třídy a dva delegáty: obecné a neobecné.  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 Při vytváření delegátů `SampleDelegate` nebo `SampleGenericDelegate<A, R>` typy, můžete přiřadit některou z následujících metod těchto delegátů.  
  
```csharp  
// Matching signature.  
public static First ASecondRFirst(Second second)  
{ return new First(); }  
  
// The return type is more derived.  
public static Second ASecondRSecond(Second second)  
{ return new Second(); }  
  
// The argument type is less derived.  
public static First AFirstRFirst(First first)  
{ return new First(); }  
  
// The return type is more derived
// and the argument type is less derived.  
public static Second AFirstRSecond(First first)  
{ return new Second(); }  
```  
  
 Následující příklad kódu ilustruje implicitní převod mezi podpisem metody a typem delegáta.  
  
```csharp  
// Assigning a method with a matching signature
// to a non-generic delegate. No conversion is necessary.  
SampleDelegate dNonGeneric = ASecondRFirst;  
// Assigning a method with a more derived return type
// and less derived argument type to a non-generic delegate.  
// The implicit conversion is used.  
SampleDelegate dNonGenericConversion = AFirstRSecond;  
  
// Assigning a method with a matching signature to a generic delegate.  
// No conversion is necessary.  
SampleGenericDelegate<Second, First> dGeneric = ASecondRFirst;  
// Assigning a method with a more derived return type
// and less derived argument type to a generic delegate.  
// The implicit conversion is used.  
SampleGenericDelegate<Second, First> dGenericConversion = AFirstRSecond;  
```  
  
 Další příklady naleznete [v tématech Použití odchylky v delegátech (C#)](./using-variance-in-delegates.md) a [Použití odchylky pro obecné delegáty aplikace Func a obecné akce (C#).](./using-variance-for-func-and-action-generic-delegates.md)  
  
## <a name="variance-in-generic-type-parameters"></a>Odchylka v parametrech obecného typu  
 V rozhraní .NET Framework 4 nebo novějšímůžete povolit implicitní převod mezi delegáty, aby obecné delegáty, které mají různé typy určené obecnými parametry typu, mohly být vzájemně přiřazeny, pokud jsou typy navzájem zděděny podle požadavků Odchylka.  
  
 Chcete-li povolit implicitní převod, musíte explicitně deklarovat obecné `in` parametry v delegáta jako kovariantní nebo contravariant pomocí klíčového slova nebo. `out`  
  
 Následující příklad kódu ukazuje, jak můžete vytvořit delegáta, který má kovariantní parametr obecného typu.  
  
```csharp  
// Type T is declared covariant by using the out keyword.  
public delegate T SampleGenericDelegate <out T>();  
  
public static void Test()  
{  
    SampleGenericDelegate <String> dString = () => " ";  
  
    // You can assign delegates to each other,  
    // because the type T is declared covariant.  
    SampleGenericDelegate <Object> dObject = dString;
}  
```  
  
 Pokud používáte pouze podporu odchylky k přiřazení podpisů metod `in` `out` s typy delegátů a nepoužíváte klíčová slova a, můžete zjistit, že někdy můžete vytvořit instanci delegátů s identickými výrazy nebo metodami lambda, ale nemůžete přiřadit jednoho delegáta jinému.  
  
 V následujícím příkladu `SampleGenericDelegate<String>` kódu nelze explicitně převést na `SampleGenericDelegate<Object>`, i když `String` dědí `Object`. Tento problém můžete vyřešit označením obecného parametru `T` klíčovým slovem. `out`  
  
```csharp  
public delegate T SampleGenericDelegate<T>();  
  
public static void Test()  
{  
    SampleGenericDelegate<String> dString = () => " ";  
  
    // You can assign the dObject delegate  
    // to the same lambda expression as dString delegate  
    // because of the variance support for
    // matching method signatures with delegate types.  
    SampleGenericDelegate<Object> dObject = () => " ";  
  
    // The following statement generates a compiler error  
    // because the generic type T is not marked as covariant.  
    // SampleGenericDelegate <Object> dObject = dString;  
  
}  
```  
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>Obecné delegáty, které mají parametry typu varianty v rozhraní .NET Framework  
 Rozhraní .NET Framework 4 zavedlo podporu odchylky pro parametry obecného typu v několika existujících obecných delegátech:  
  
- `Action`delegátů z <xref:System> oboru názvů, <xref:System.Action%601> například, a<xref:System.Action%602>  
  
- `Func`delegátů z <xref:System> oboru názvů, <xref:System.Func%601> například, a<xref:System.Func%602>  
  
- Delegát <xref:System.Predicate%601>  
  
- Delegát <xref:System.Comparison%601>  
  
- Delegát <xref:System.Converter%602>  
  
 Další informace a příklady naleznete [v tématu Použití odchylky pro obecné delegáty aplikace Func a obecné akce (C#).](./using-variance-for-func-and-action-generic-delegates.md)  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>Deklarování parametrů typu varianty v obecných delegátech  
 Pokud obecný delegát má covariant nebo contravariant obecný typ parametry, může být označován jako *varianta obecný delegát*.  
  
 Můžete deklarovat parametr obecného typu kovarianta v obecnédelegát pomocí klíčového `out` slova. Kovariantní typ lze použít pouze jako návratový typ metody a nikoli jako typ argumentů metody. Následující příklad kódu ukazuje, jak deklarovat kovariantní obecný delegát.  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 Můžete deklarovat parametr obecného typu contravariant `in` v obecnédelegát pomocí klíčového slova. Typ contravariant lze použít pouze jako typ argumentů metody a nikoli jako návratový typ metody. Následující příklad kódu ukazuje, jak deklarovat kontravariantní obecný delegát.  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
> `ref`, `in`a `out` parametry v c# nelze označit jako varianta.  
  
 Je také možné podporovat odchylky a kovariance ve stejném delegáta, ale pro různé parametry typu. To je ukázáno v následujícím příkladu.  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a>Vytváření konkretista a vyvolání obecných delegátů variant  
 Můžete vytvořit instance a vyvolat delegáty varianty stejně jako konstanci a vyvolat invariantní delegáty. V následujícím příkladu delegáta je vytvořena instance lambda výraz.  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a>Kombinování typových obecných delegátů variant  
 Neměli byste kombinovat delegáty variant. Metoda <xref:System.Delegate.Combine%2A> nepodporuje převod delegáta varianta a očekává, že delegáti budou přesně stejného typu. To může vést k výjimce za běhu při <xref:System.Delegate.Combine%2A> kombinaci delegátů `+` pomocí metody nebo pomocí operátoru, jak je znázorněno v následujícím příkladu kódu.  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>Odchylka v parametrech obecného typu pro typy hodnot a odkazů  
 Odchylka pro parametry obecného typu je podporována pouze pro typy odkazů. Nelze například `DVariant<int>` implicitně převést na `DVariant<Object>` `DVariant<long>`nebo , protože celé číslo je typ hodnoty.  
  
 Následující příklad ukazuje, že odchylka v parametrech obecného typu není pro typy hodnot podporována.  
  
```csharp  
// The type T is covariant.  
public delegate T DVariant<out T>();  
  
// The type T is invariant.  
public delegate T DInvariant<T>();  
  
public static void Test()  
{  
    int i = 0;  
    DInvariant<int> dInt = () => i;  
    DVariant<int> dVariantInt = () => i;  
  
    // All of the following statements generate a compiler error  
    // because type variance in generic parameters is not supported  
    // for value types, even if generic type parameters are declared variant.  
    // DInvariant<Object> dObject = dInt;  
    // DInvariant<long> dLong = dInt;  
    // DVariant<Object> dVariantObject = dVariantInt;  
    // DVariant<long> dVariantLong = dVariantInt;
}  
```  
  
## <a name="see-also"></a>Viz také

- [Obecné typy](../../../../standard/generics/index.md)
- [Použití odchylky pro obecné delegáty aplikace Func a obecné akce (C#)](./using-variance-for-func-and-action-generic-delegates.md)
- [Jak kombinovat delegáty (delegáti vícesměrového vysílání)](../../delegates/how-to-combine-delegates-multicast-delegates.md)
