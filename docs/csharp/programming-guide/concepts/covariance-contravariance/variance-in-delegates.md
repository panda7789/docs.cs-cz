---
title: Odchylky v delegátech (C#)
ms.date: 07/20/2015
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
ms.openlocfilehash: 8b74c29d8d94a31d30408131009d92e2b2a4281c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33326225"
---
# <a name="variance-in-delegates-c"></a>Odchylky v delegátech (C#)
Rozhraní .NET framework 3.5 byla zavedena podpora odchylku odpovídající metoda podpisy s typy delegáta v všechny Delegáti v jazyce C#. To znamená, že můžete přiřadit deleguje pouze metody, které mají odpovídající podpisy, ale také metody, které vracejí informace odvozené typy (kovariance) nebo pracujících s parametry, které mají méně odvozené typy (kontravariance) než je určeno typ delegáta . To zahrnuje obecné a neobecné delegáti.  
  
 Zvažte například následující kód, který má dvě třídy a dvě delegáti: Obecné a neobecné.  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 Při vytváření delegátů `SampleDelegate` nebo `SampleGenericDelegate<A, R>` typy, můžete přiřadit jednu z následujících metod těchto delegáti.  
  
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
  
 Následující příklad kódu ukazuje implicitní převod mezi podpis metody a typu delegáta.  
  
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
  
 Další příklady najdete v tématu [použití odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) a [pomocí odchylky pro Func a akce obecní delegáti (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
## <a name="variance-in-generic-type-parameters"></a>Odchylky v obecné parametry typu  
 V rozhraní .NET Framework 4 nebo novější můžete povolit implicitní převod mezi delegáti, tak, aby obecní delegáti, které mají různé typy určeného parametry obecného typu lze přiřadit k sobě navzájem, pokud jsou typy zděděn od sebe navzájem podle požadavků odchylky.  
  
 Pokud chcete povolit implicitní převod, je potřeba explicitně deklarovat obecné parametry v delegáta jako kovariantní nebo kontravariant pomocí `in` nebo `out` – klíčové slovo.  
  
 Následující příklad kódu ukazuje, jak můžete vytvořit delegáta, který má parametr kovariantní obecného typu.  
  
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
  
 Pokud používáte pouze odchylky podporu tak, aby odpovídaly podpisy, metoda delegovat typy a nepoužívejte `in` a `out` klíčová slova, můžete zjistit, že v některých případech může vytvořit instanci delegáti s identické lambda – výrazy nebo metod, ale nemůžete Přiřaďte jednoho delegáta do jiného.  
  
 V následujícím příkladu kódu `SampleGenericDelegate<String>` nelze explicitně převést na `SampleGenericDelegate<Object>`, i když `String` dědí `Object`. Tento problém lze vyřešit označení obecný parametr `T` s `out` – klíčové slovo.  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>Obecní delegáti, které mají typ Variant parametry typu v rozhraní .NET Framework  
 Rozhraní .NET framework 4 zavedl podporu odchylky pro parametry obecného typu v několika existující obecní delegáti:  
  
-   `Action` Deleguje z <xref:System> obor názvů, například <xref:System.Action%601> a <xref:System.Action%602>  
  
-   `Func` Deleguje z <xref:System> obor názvů, například <xref:System.Func%601> a <xref:System.Func%602>  
  
-   <xref:System.Predicate%601> Delegovat  
  
-   <xref:System.Comparison%601> Delegovat  
  
-   <xref:System.Converter%602> Delegovat  
  
 Další informace a příklady naleznete v tématu [pomocí odchylky pro Func a akce obecní delegáti (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>Deklarující typ varianty parametry v obecní delegáti  
 Pokud má obecný delegát kovariantní nebo kontravariant parametry obecného typu, ho lze odkazovat jako *variant obecný delegát*.  
  
 Je možné deklarovat parametr obecného typu kovariantní v obecný delegát pomocí `out` – klíčové slovo. Typ kovariantní lze použít pouze jako návratový typ metody a ne jako typ metoda argumenty. Následující příklad kódu ukazuje, jak deklarovat kovariantní obecný delegát.  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 Je možné deklarovat kontravariant parametr obecného typu v obecný delegát pomocí `in` – klíčové slovo. Typ kontravariant lze použít pouze jako typ argumenty metody a ne jako návratový typ. metoda. Následující příklad kódu ukazuje, jak deklarovat obecný delegát kontravariant.  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
>  `ref`, `in`, a `out` parametry v jazyce C# nelze označit jako typ variant.  
  
 Je také možné podporovat odchylky a Kovariance v stejného delegáta, ale pro jiný typ parametry. To je ukázáno v následujícím příkladu.  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a>Vytváření instancí a vyvolání Variant obecní delegáti  
 Můžete vytvořit instanci a vyvolání variant delegáti stejně, jako je vytváření instancí a vyvolání invariantní delegáti. V následujícím příkladu je vytvořena instance delegáta pomocí výrazu lambda.  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a>Kombinování Variant obecní delegáti  
 Nesmí kombinovat variant delegáti. <xref:System.Delegate.Combine%2A> Metoda nepodporuje převod variant delegáta a očekává delegáti být přesně stejného typu. To může vést ke spuštění výjimka při kombinování delegátů buď pomocí <xref:System.Delegate.Combine%2A> metoda nebo pomocí `+` operátor, jak je znázorněno v následujícím příkladu kódu.  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>Odchylky v parametry obecného typu pro hodnotových a odkazových typech  
 Odchylky pro parametry obecného typu je podporována pro odkazové typy pouze. Například `DVariant<int>` nelze implicitně převést na `DVariant<Object>` nebo `DVariant<long>`, protože typ hodnoty je celé číslo.  
  
 Následující příklad ukazuje, že odchylky v obecného typu parametry není podporována u typů hodnot.  
  
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
 [Obecné typy](~/docs/standard/generics/index.md)  
 [Použití odchylek pro Func a akce obecní delegáti (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)  
 [Postupy: kombinování delegátů (vícesměroví delegáti)](../../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
