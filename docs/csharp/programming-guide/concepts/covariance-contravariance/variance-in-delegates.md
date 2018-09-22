---
title: Odchylky v delegátech (C#)
ms.date: 07/20/2015
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
ms.openlocfilehash: 3dabac4e532198871cf05d639aa692751ab17ae1
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46577474"
---
# <a name="variance-in-delegates-c"></a>Odchylky v delegátech (C#)
Rozhraní .NET framework 3.5 představil podporu odchylku pro spárování metod podpisů s typy delegáta v Všichni delegáti v jazyce C#. To znamená, že můžete přiřadit delegáty pouze metody, které mají odpovídající podpisy, ale také metody, které vracejí informace odvozené typy (kovariance) nebo, která přijímají parametry, které mají méně odvozené typy (kontravariance), než je určeno typ delegáta . To zahrnuje obecných a neobecných delegátů.  
  
 Zvažte například následující kód, který má dvě třídy a dvou delegátů: obecných a neobecných.  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 Při vytváření delegátů `SampleDelegate` nebo `SampleGenericDelegate<A, R>` typy, můžete přiřadit jednu z následujících metod na tyto delegáty.  
  
```csharp  
// Matching signature.  
public static First ASecondRFirst(Second first)  
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
  
 Následující příklad kódu ukazuje implicitní převod mezi podpisu metody a typ delegáta.  
  
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
  
 Další příklady najdete v tématu [použití odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) a [pomocí odchylku pro delegáty Func a Action obecný (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
## <a name="variance-in-generic-type-parameters"></a>Variance u parametrů obecného typu  
 V rozhraní .NET Framework 4 nebo novější můžete povolit implicitní převod mezi delegáty, tak, aby obecné delegáty, které mají různé typy určené parametry obecného typu lze přiřadit k sobě navzájem, pokud typ dědí od sebe navzájem podle požadavků Variance.  
  
 Pokud chcete povolit implicitní převod, musíte explicitně deklarovat obecných parametrů v delegátů jako kovariantní nebo kontravariantní pomocí `in` nebo `out` – klíčové slovo.  
  
 Následující příklad kódu ukazuje, jak můžete vytvořit delegáta, který má parametr kovariantního obecného typu.  
  
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
  
 Pokud používáte podporují jenom variance tak, aby odpovídaly metod podpisů s typy delegátů a nepoužívají `in` a `out` klíčová slova, možná zjistíte, že v některých případech můžete vytvořit instanci delegáty s identické lambda výrazy nebo metody, ale nemůžete přiřaďte jeden delegáta do jiného.  
  
 V následujícím příkladu kódu `SampleGenericDelegate<String>` nelze explicitně převést na `SampleGenericDelegate<Object>`, i když `String` dědí `Object`. Tento problém můžete vyřešit označením obecných parametrů `T` s `out` – klíčové slovo.  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>Parametry typu obecné delegáty, které mají typ Variant v rozhraní .NET Framework  
 Rozhraní .NET framework 4 zavedena podpora odchylku pro parametry obecného typu v několika existující obecné delegáty:  
  
-   `Action` Deleguje z <xref:System> obor názvů, třeba <xref:System.Action%601> a <xref:System.Action%602>  
  
-   `Func` Deleguje z <xref:System> obor názvů, třeba <xref:System.Func%601> a <xref:System.Func%602>  
  
-   <xref:System.Predicate%601> Delegovat  
  
-   <xref:System.Comparison%601> Delegovat  
  
-   <xref:System.Converter%602> Delegovat  
  
 Další informace a příklady najdete v tématu [pomocí odchylku pro delegáty Func a Action obecný (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>Deklarování parametry variantního typu v obecné delegáty  
 Pokud obecného delegátu má kovariantní nebo kontravariantní parametry obecného typu, jej lze odkazovat jako *variant obecného delegátu*.  
  
 Je možné deklarovat parametr obecného typu Kovariance v obecných delegátů pomocí `out` – klíčové slovo. Kovariantního typu lze použít pouze jako návratový typ metody a ne jako typ argumentů metody. Následující příklad kódu ukazuje, jak deklarovat kovariantního obecného delegáta.  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 Kontravariantního parametru obecného typu v obecného delegátu lze deklarovat s použitím `in` – klíčové slovo. Kontravariantního typu lze použít pouze jako argumenty metody typu, nikoli jako návratový typ metody. Následující příklad kódu ukazuje, jak deklarovat delegáta obecného kontravariantního.  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
>  `ref`, `in`, a `out` parametry v jazyce C# nelze označit jako typ variant.  
  
 Je také možné podporovat odchylky a Kovariance v stejného delegáta, ale pro jiný typ parametrů. To je ukázáno v následujícím příkladu.  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a>Vytváření instancí a volání Variant obecných delegátů  
 Můžete konkretizovat a vyvoláte variant stejně jako můžete vytvořit instanci nebo vyvoláte invariantní. V následujícím příkladu je vytvořena instance delegáta ve výrazu lambda.  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a>Kombinování variantních obecných delegátů  
 Neměli kombinovat variant delegátů. <xref:System.Delegate.Combine%2A> Metoda nepodporuje převod variant delegáta a očekává, že delegáty být stejného typu. To může vést k výjimce za běhu při kombinování delegátů pomocí <xref:System.Delegate.Combine%2A> metody nebo pomocí `+` operátoru, jak je znázorněno v následujícím příkladu kódu.  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>Variance u parametrů obecného typu pro hodnotových a odkazových typech  
 Variance u parametrů obecného typu je podporována pouze pro typy odkazů. Například `DVariant<int>` nejde implicitně převést na `DVariant<Object>` nebo `DVariant<long>`, protože se hodnota typu celé číslo.  
  
 Následující příklad ukazuje, že variance v obecném typu se nepodporuje parametry pro typy hodnot.  
  
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

- [Obecné typy](~/docs/standard/generics/index.md)  
- [Použití odchylek pro delegáty Func a Action obecný (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)  
- [Postupy: kombinování delegátů (vícesměroví delegáti)](../../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
