---
title: Variance v delegátechC#()
ms.date: 07/20/2015
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
ms.openlocfilehash: cdf7cad97ececbf4baae8328b1df55318c627cbb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345168"
---
# <a name="variance-in-delegates-c"></a><span data-ttu-id="0dec4-102">Variance v delegátechC#()</span><span class="sxs-lookup"><span data-stu-id="0dec4-102">Variance in Delegates (C#)</span></span>
<span data-ttu-id="0dec4-103">.NET Framework 3,5 zavedl podporu variance pro párové signatury metod s typy delegátů ve C#všech delegátech v.</span><span class="sxs-lookup"><span data-stu-id="0dec4-103">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C#.</span></span> <span data-ttu-id="0dec4-104">To znamená, že můžete přiřadit delegáty nejen metody, které mají odpovídající signatury, ale také metody, které vracejí více odvozené typy (kovariance), nebo které přijímají parametry, které mají méně odvozené typy (kontravariance), než které jsou určeny typem delegáta. .</span><span class="sxs-lookup"><span data-stu-id="0dec4-104">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="0dec4-105">To zahrnuje obecné i neobecné delegáty.</span><span class="sxs-lookup"><span data-stu-id="0dec4-105">This includes both generic and non-generic delegates.</span></span>  
  
 <span data-ttu-id="0dec4-106">Zvažte například následující kód, který má dvě třídy a dva delegáty: Obecné a neobecné.</span><span class="sxs-lookup"><span data-stu-id="0dec4-106">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 <span data-ttu-id="0dec4-107">Když vytváříte delegáty `SampleDelegate` nebo `SampleGenericDelegate<A, R>`ch typů, můžete těmto delegátům přiřadit jednu z následujících metod.</span><span class="sxs-lookup"><span data-stu-id="0dec4-107">When you create delegates of the `SampleDelegate` or `SampleGenericDelegate<A, R>` types, you can assign any one of the following methods to those delegates.</span></span>  
  
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
  
 <span data-ttu-id="0dec4-108">Následující příklad kódu ukazuje implicitní převod mezi signaturou metody a typem delegáta.</span><span class="sxs-lookup"><span data-stu-id="0dec4-108">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>  
  
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
  
 <span data-ttu-id="0dec4-109">Další příklady naleznete v tématu [použití variance v delegátechC#()](./using-variance-in-delegates.md) a [použití odchylky pro obecné delegáty Func aC#Action ()](./using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="0dec4-109">For more examples, see [Using Variance in Delegates (C#)](./using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="0dec4-110">Variance v parametrech obecného typu</span><span class="sxs-lookup"><span data-stu-id="0dec4-110">Variance in Generic Type Parameters</span></span>  
 <span data-ttu-id="0dec4-111">V .NET Framework 4 nebo novější lze povolit implicitní převod mezi delegáty, aby byly Obecné delegáti, kteří mají různé typy určené parametry obecného typu, vzájemně přiřazeny, pokud jsou typy děděny od sebe navzájem vyžadované odchylk.</span><span class="sxs-lookup"><span data-stu-id="0dec4-111">In .NET Framework 4 or later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>  
  
 <span data-ttu-id="0dec4-112">Chcete-li povolit implicitní převod, je nutné explicitně deklarovat Obecné parametry delegáta jako kovariantu nebo kontravariantní pomocí klíčového slova `in` nebo `out`.</span><span class="sxs-lookup"><span data-stu-id="0dec4-112">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>  
  
 <span data-ttu-id="0dec4-113">Následující příklad kódu ukazuje, jak lze vytvořit delegáta s parametrem kovariantního obecného typu.</span><span class="sxs-lookup"><span data-stu-id="0dec4-113">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>  
  
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
  
 <span data-ttu-id="0dec4-114">Použijete-li pouze podporu variance pro spárování signatur metod s typy delegátů a nepoužíváte klíčová slova `in` a `out`, je možné, že někdy lze vytvořit instanci delegátů se stejnými výrazy lambda nebo metodami, ale nelze přiřadit jednoho delegáta jinému.</span><span class="sxs-lookup"><span data-stu-id="0dec4-114">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>  
  
 <span data-ttu-id="0dec4-115">V následujícím příkladu kódu `SampleGenericDelegate<String>` nelze explicitně převést na `SampleGenericDelegate<Object>`, i když `String` dědí `Object`.</span><span class="sxs-lookup"><span data-stu-id="0dec4-115">In the following code example, `SampleGenericDelegate<String>` cannot be explicitly converted to `SampleGenericDelegate<Object>`, although `String` inherits `Object`.</span></span> <span data-ttu-id="0dec4-116">Tento problém můžete vyřešit tak, že označíte obecný parametr `T` s klíčovým slovem `out`.</span><span class="sxs-lookup"><span data-stu-id="0dec4-116">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a><span data-ttu-id="0dec4-117">Obecní delegáti, kteří mají parametry typu variant v .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0dec4-117">Generic Delegates That Have Variant Type Parameters in the .NET Framework</span></span>  
 <span data-ttu-id="0dec4-118">.NET Framework 4 představil podporu variance pro parametry obecného typu v několika stávajících obecných delegátech:</span><span class="sxs-lookup"><span data-stu-id="0dec4-118">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>  
  
- <span data-ttu-id="0dec4-119">`Action` delegáty z oboru názvů <xref:System>, například <xref:System.Action%601> a <xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="0dec4-119">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>  
  
- <span data-ttu-id="0dec4-120">`Func` delegáty z oboru názvů <xref:System>, například <xref:System.Func%601> a <xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="0dec4-120">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>  
  
- <span data-ttu-id="0dec4-121">Delegát <xref:System.Predicate%601></span><span class="sxs-lookup"><span data-stu-id="0dec4-121">The <xref:System.Predicate%601> delegate</span></span>  
  
- <span data-ttu-id="0dec4-122">Delegát <xref:System.Comparison%601></span><span class="sxs-lookup"><span data-stu-id="0dec4-122">The <xref:System.Comparison%601> delegate</span></span>  
  
- <span data-ttu-id="0dec4-123">Delegát <xref:System.Converter%602></span><span class="sxs-lookup"><span data-stu-id="0dec4-123">The <xref:System.Converter%602> delegate</span></span>  
  
 <span data-ttu-id="0dec4-124">Další informace a příklady naleznete v tématu [using variance for Func and Action Generic DelegatesC#()](./using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="0dec4-124">For more information and examples, see [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="0dec4-125">Deklarace parametrů typu variant v obecných delegátech</span><span class="sxs-lookup"><span data-stu-id="0dec4-125">Declaring Variant Type Parameters in Generic Delegates</span></span>  
 <span data-ttu-id="0dec4-126">Pokud má obecný delegát kovariantní nebo kontravariantní parametry obecného typu, může být odkazováno jako *obecný delegát typu variant*.</span><span class="sxs-lookup"><span data-stu-id="0dec4-126">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>  
  
 <span data-ttu-id="0dec4-127">Pomocí klíčového slova `out` lze deklarovat parametr kovariantního typu v obecném delegátu.</span><span class="sxs-lookup"><span data-stu-id="0dec4-127">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="0dec4-128">Typ kovariantního typu se dá použít jenom jako návratový typ metody, a ne jako typ argumentů metody.</span><span class="sxs-lookup"><span data-stu-id="0dec4-128">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="0dec4-129">Následující příklad kódu ukazuje, jak deklarovat kovariantní obecný delegát.</span><span class="sxs-lookup"><span data-stu-id="0dec4-129">The following code example shows how to declare a covariant generic delegate.</span></span>  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 <span data-ttu-id="0dec4-130">Pomocí klíčového slova `in` můžete deklarovat parametr kontravariantního obecného typu v obecném delegátu.</span><span class="sxs-lookup"><span data-stu-id="0dec4-130">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="0dec4-131">Kontravariantní typ lze použít pouze jako typ argumentů metody a nikoli jako návratový typ metody.</span><span class="sxs-lookup"><span data-stu-id="0dec4-131">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="0dec4-132">Následující příklad kódu ukazuje, jak deklarovat kontravariantního obecného delegáta.</span><span class="sxs-lookup"><span data-stu-id="0dec4-132">The following code example shows how to declare a contravariant generic delegate.</span></span>  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="0dec4-133">parametry `ref`, `in`a `out` C# nelze označit jako typ variant.</span><span class="sxs-lookup"><span data-stu-id="0dec4-133">`ref`, `in`, and `out` parameters in C# can't be marked as variant.</span></span>  
  
 <span data-ttu-id="0dec4-134">Je také možné podporovat odchylku i kovarianci v rámci stejného delegáta, ale pro různé parametry typu.</span><span class="sxs-lookup"><span data-stu-id="0dec4-134">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="0dec4-135">To je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0dec4-135">This is shown in the following example.</span></span>  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="0dec4-136">Vytváření instancí a volání variantních generických delegátů</span><span class="sxs-lookup"><span data-stu-id="0dec4-136">Instantiating and Invoking Variant Generic Delegates</span></span>  
 <span data-ttu-id="0dec4-137">Můžete vytvořit instanci a vyvolat delegáty variant stejně jako při vytváření instance a vyvolat invariantní delegáty.</span><span class="sxs-lookup"><span data-stu-id="0dec4-137">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="0dec4-138">V následujícím příkladu je vytvořena instance delegáta ve výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="0dec4-138">In the following example, the delegate is instantiated by a lambda expression.</span></span>  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="0dec4-139">Kombinovaná obecná Delegáti variant</span><span class="sxs-lookup"><span data-stu-id="0dec4-139">Combining Variant Generic Delegates</span></span>  
 <span data-ttu-id="0dec4-140">Neměli byste kombinovat delegáty variant.</span><span class="sxs-lookup"><span data-stu-id="0dec4-140">You should not combine variant delegates.</span></span> <span data-ttu-id="0dec4-141">Metoda <xref:System.Delegate.Combine%2A> nepodporuje převod delegáta variant a očekává, že Delegáti budou mít naprosto stejný typ.</span><span class="sxs-lookup"><span data-stu-id="0dec4-141">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="0dec4-142">To může vést k výjimce za běhu, Pokud kombinujete delegáty buď pomocí metody <xref:System.Delegate.Combine%2A>, nebo pomocí operátoru `+`, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="0dec4-142">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method or by using the `+` operator, as shown in the following code example.</span></span>  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="0dec4-143">Variance v parametrech obecného typu pro typy hodnot a odkazů</span><span class="sxs-lookup"><span data-stu-id="0dec4-143">Variance in Generic Type Parameters for Value and Reference Types</span></span>  
 <span data-ttu-id="0dec4-144">Variance pro parametry obecného typu je podporována pouze pro typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="0dec4-144">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="0dec4-145">Například `DVariant<int>` nelze implicitně převést na `DVariant<Object>` nebo `DVariant<long>`, protože integer je typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0dec4-145">For example, `DVariant<int>` can't be implicitly converted to `DVariant<Object>` or `DVariant<long>`, because integer is a value type.</span></span>  
  
 <span data-ttu-id="0dec4-146">Následující příklad ukazuje, že variance v parametrech obecného typu není pro typy hodnot podporována.</span><span class="sxs-lookup"><span data-stu-id="0dec4-146">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0dec4-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0dec4-147">See also</span></span>

- [<span data-ttu-id="0dec4-148">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="0dec4-148">Generics</span></span>](../../../../standard/generics/index.md)
- [<span data-ttu-id="0dec4-149">Použití odchylky pro obecné delegáty Func a ActionC#()</span><span class="sxs-lookup"><span data-stu-id="0dec4-149">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
- [<span data-ttu-id="0dec4-150">Postup kombinování delegátů (Delegáti vícesměrového vysílání)</span><span class="sxs-lookup"><span data-stu-id="0dec4-150">How to combine delegates (Multicast Delegates)</span></span>](../../delegates/how-to-combine-delegates-multicast-delegates.md)
