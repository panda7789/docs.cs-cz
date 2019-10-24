---
title: Variance v delegátechC#()
ms.date: 07/20/2015
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
ms.openlocfilehash: a65b2fb84e2eae57eecaf5307ca76fbce412d44c
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72772045"
---
# <a name="variance-in-delegates-c"></a>Variance v delegátechC#()
.NET Framework 3,5 zavedl podporu variance pro párové signatury metod s typy delegátů ve C#všech delegátech v. To znamená, že můžete přiřadit delegáty nejen metody, které mají odpovídající signatury, ale také metody, které vracejí více odvozené typy (kovariance), nebo které přijímají parametry, které mají méně odvozené typy (kontravariance), než které jsou určeny typem delegáta. . To zahrnuje obecné i neobecné delegáty.  
  
 Zvažte například následující kód, který má dvě třídy a dva delegáty: Obecné a neobecné.  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 Když vytváříte delegáty `SampleDelegate` nebo `SampleGenericDelegate<A, R>`ch typů, můžete těmto delegátům přiřadit jednu z následujících metod.  
  
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
  
 Následující příklad kódu ukazuje implicitní převod mezi signaturou metody a typem delegáta.  
  
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
  
 Další příklady naleznete v tématu [použití variance v delegátechC#()](./using-variance-in-delegates.md) a [použití odchylky pro obecné delegáty Func aC#Action ()](./using-variance-for-func-and-action-generic-delegates.md).  
  
## <a name="variance-in-generic-type-parameters"></a>Variance v parametrech obecného typu  
 V .NET Framework 4 nebo novější lze povolit implicitní převod mezi delegáty, aby byly Obecné delegáti, kteří mají různé typy určené parametry obecného typu, vzájemně přiřazeny, pokud jsou typy děděny od sebe navzájem vyžadované odchylk.  
  
 Chcete-li povolit implicitní převod, je nutné explicitně deklarovat Obecné parametry delegáta jako kovariantu nebo kontravariantní pomocí klíčového slova `in` nebo `out`.  
  
 Následující příklad kódu ukazuje, jak lze vytvořit delegáta s parametrem kovariantního obecného typu.  
  
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
  
 Použijete-li pouze podporu variance pro spárování signatur metod s typy delegátů a nepoužíváte klíčová slova `in` a `out`, je možné, že někdy lze vytvořit instanci delegátů se stejnými výrazy lambda nebo metodami, ale nemůžete přiřadit jednu delegovat na jiný  
  
 V následujícím příkladu kódu `SampleGenericDelegate<String>` nelze explicitně převést na `SampleGenericDelegate<Object>`, i když `String` dědí `Object`. Tento problém můžete vyřešit tak, že označíte obecný parametr `T` s klíčovým slovem `out`.  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>Obecní delegáti, kteří mají parametry typu variant v .NET Framework  
 .NET Framework 4 představil podporu variance pro parametry obecného typu v několika stávajících obecných delegátech:  
  
- `Action` delegáty z oboru názvů <xref:System>, například <xref:System.Action%601> a <xref:System.Action%602>  
  
- `Func` delegáty z oboru názvů <xref:System>, například <xref:System.Func%601> a <xref:System.Func%602>  
  
- Delegát <xref:System.Predicate%601>  
  
- Delegát <xref:System.Comparison%601>  
  
- Delegát <xref:System.Converter%602>  
  
 Další informace a příklady naleznete v tématu [using variance for Func and Action Generic DelegatesC#()](./using-variance-for-func-and-action-generic-delegates.md).  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>Deklarace parametrů typu variant v obecných delegátech  
 Pokud má obecný delegát kovariantní nebo kontravariantní parametry obecného typu, může být odkazováno jako *obecný delegát typu variant*.  
  
 Pomocí klíčového slova `out` lze deklarovat parametr kovariantního typu v obecném delegátu. Typ kovariantního typu se dá použít jenom jako návratový typ metody, a ne jako typ argumentů metody. Následující příklad kódu ukazuje, jak deklarovat kovariantní obecný delegát.  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 Pomocí klíčového slova `in` můžete deklarovat parametr kontravariantního obecného typu v obecném delegátu. Kontravariantní typ lze použít pouze jako typ argumentů metody a nikoli jako návratový typ metody. Následující příklad kódu ukazuje, jak deklarovat kontravariantního obecného delegáta.  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
> parametry `ref`, `in` a `out` C# nelze označit jako typ variant.  
  
 Je také možné podporovat odchylku i kovarianci v rámci stejného delegáta, ale pro různé parametry typu. To je ukázáno v následujícím příkladu.  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a>Vytváření instancí a volání variantních generických delegátů  
 Můžete vytvořit instanci a vyvolat delegáty variant stejně jako při vytváření instance a vyvolat invariantní delegáty. V následujícím příkladu je vytvořena instance delegáta ve výrazu lambda.  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a>Kombinovaná obecná Delegáti variant  
 Neměli byste kombinovat delegáty variant. Metoda <xref:System.Delegate.Combine%2A> nepodporuje převod delegáta variant a očekává, že Delegáti budou mít naprosto stejný typ. To může vést k výjimce za běhu, Pokud kombinujete delegáty buď pomocí metody <xref:System.Delegate.Combine%2A>, nebo pomocí operátoru `+`, jak je znázorněno v následujícím příkladu kódu.  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>Variance v parametrech obecného typu pro typy hodnot a odkazů  
 Variance pro parametry obecného typu je podporována pouze pro typy odkazů. Například `DVariant<int>` nelze implicitně převést na `DVariant<Object>` nebo `DVariant<long>`, protože integer je typ hodnoty.  
  
 Následující příklad ukazuje, že variance v parametrech obecného typu není pro typy hodnot podporována.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Obecné typy](../../../../standard/generics/index.md)
- [Použití odchylky pro obecné delegáty Func a ActionC#()](./using-variance-for-func-and-action-generic-delegates.md)
- [Postupy: kombinování delegátů (vícesměrové Delegáti)](../../delegates/how-to-combine-delegates-multicast-delegates.md)
