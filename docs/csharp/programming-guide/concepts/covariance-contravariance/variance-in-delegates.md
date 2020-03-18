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
# <a name="variance-in-delegates-c"></a><span data-ttu-id="db679-102">Odchylka v delegátech (C#)</span><span class="sxs-lookup"><span data-stu-id="db679-102">Variance in Delegates (C#)</span></span>
<span data-ttu-id="db679-103">Rozhraní .NET Framework 3.5 zavedlo podporu odchylky pro odpovídající podpisy metod s typy delegátů ve všech delegátech v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="db679-103">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C#.</span></span> <span data-ttu-id="db679-104">To znamená, že delegátům můžete přiřadit nejen metody, které mají odpovídající podpisy, ale také metody, které vracejí více odvozených typů (kovariance) nebo které přijímají parametry, které mají méně odvozených typů (kontravariance) než ty, které jsou určeny typem delegáta. .</span><span class="sxs-lookup"><span data-stu-id="db679-104">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="db679-105">To zahrnuje obecné i obecné delegáty.</span><span class="sxs-lookup"><span data-stu-id="db679-105">This includes both generic and non-generic delegates.</span></span>  
  
 <span data-ttu-id="db679-106">Zvažte například následující kód, který má dvě třídy a dva delegáty: obecné a neobecné.</span><span class="sxs-lookup"><span data-stu-id="db679-106">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 <span data-ttu-id="db679-107">Při vytváření delegátů `SampleDelegate` nebo `SampleGenericDelegate<A, R>` typy, můžete přiřadit některou z následujících metod těchto delegátů.</span><span class="sxs-lookup"><span data-stu-id="db679-107">When you create delegates of the `SampleDelegate` or `SampleGenericDelegate<A, R>` types, you can assign any one of the following methods to those delegates.</span></span>  
  
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
  
 <span data-ttu-id="db679-108">Následující příklad kódu ilustruje implicitní převod mezi podpisem metody a typem delegáta.</span><span class="sxs-lookup"><span data-stu-id="db679-108">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>  
  
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
  
 <span data-ttu-id="db679-109">Další příklady naleznete [v tématech Použití odchylky v delegátech (C#)](./using-variance-in-delegates.md) a [Použití odchylky pro obecné delegáty aplikace Func a obecné akce (C#).](./using-variance-for-func-and-action-generic-delegates.md)</span><span class="sxs-lookup"><span data-stu-id="db679-109">For more examples, see [Using Variance in Delegates (C#)](./using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="db679-110">Odchylka v parametrech obecného typu</span><span class="sxs-lookup"><span data-stu-id="db679-110">Variance in Generic Type Parameters</span></span>  
 <span data-ttu-id="db679-111">V rozhraní .NET Framework 4 nebo novějšímůžete povolit implicitní převod mezi delegáty, aby obecné delegáty, které mají různé typy určené obecnými parametry typu, mohly být vzájemně přiřazeny, pokud jsou typy navzájem zděděny podle požadavků Odchylka.</span><span class="sxs-lookup"><span data-stu-id="db679-111">In .NET Framework 4 or later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>  
  
 <span data-ttu-id="db679-112">Chcete-li povolit implicitní převod, musíte explicitně deklarovat obecné `in` parametry v delegáta jako kovariantní nebo contravariant pomocí klíčového slova nebo. `out`</span><span class="sxs-lookup"><span data-stu-id="db679-112">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>  
  
 <span data-ttu-id="db679-113">Následující příklad kódu ukazuje, jak můžete vytvořit delegáta, který má kovariantní parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="db679-113">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>  
  
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
  
 <span data-ttu-id="db679-114">Pokud používáte pouze podporu odchylky k přiřazení podpisů metod `in` `out` s typy delegátů a nepoužíváte klíčová slova a, můžete zjistit, že někdy můžete vytvořit instanci delegátů s identickými výrazy nebo metodami lambda, ale nemůžete přiřadit jednoho delegáta jinému.</span><span class="sxs-lookup"><span data-stu-id="db679-114">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>  
  
 <span data-ttu-id="db679-115">V následujícím příkladu `SampleGenericDelegate<String>` kódu nelze explicitně převést na `SampleGenericDelegate<Object>`, i když `String` dědí `Object`.</span><span class="sxs-lookup"><span data-stu-id="db679-115">In the following code example, `SampleGenericDelegate<String>` cannot be explicitly converted to `SampleGenericDelegate<Object>`, although `String` inherits `Object`.</span></span> <span data-ttu-id="db679-116">Tento problém můžete vyřešit označením obecného parametru `T` klíčovým slovem. `out`</span><span class="sxs-lookup"><span data-stu-id="db679-116">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a><span data-ttu-id="db679-117">Obecné delegáty, které mají parametry typu varianty v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="db679-117">Generic Delegates That Have Variant Type Parameters in the .NET Framework</span></span>  
 <span data-ttu-id="db679-118">Rozhraní .NET Framework 4 zavedlo podporu odchylky pro parametry obecného typu v několika existujících obecných delegátech:</span><span class="sxs-lookup"><span data-stu-id="db679-118">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>  
  
- <span data-ttu-id="db679-119">`Action`delegátů z <xref:System> oboru názvů, <xref:System.Action%601> například, a<xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="db679-119">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>  
  
- <span data-ttu-id="db679-120">`Func`delegátů z <xref:System> oboru názvů, <xref:System.Func%601> například, a<xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="db679-120">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>  
  
- <span data-ttu-id="db679-121">Delegát <xref:System.Predicate%601></span><span class="sxs-lookup"><span data-stu-id="db679-121">The <xref:System.Predicate%601> delegate</span></span>  
  
- <span data-ttu-id="db679-122">Delegát <xref:System.Comparison%601></span><span class="sxs-lookup"><span data-stu-id="db679-122">The <xref:System.Comparison%601> delegate</span></span>  
  
- <span data-ttu-id="db679-123">Delegát <xref:System.Converter%602></span><span class="sxs-lookup"><span data-stu-id="db679-123">The <xref:System.Converter%602> delegate</span></span>  
  
 <span data-ttu-id="db679-124">Další informace a příklady naleznete [v tématu Použití odchylky pro obecné delegáty aplikace Func a obecné akce (C#).](./using-variance-for-func-and-action-generic-delegates.md)</span><span class="sxs-lookup"><span data-stu-id="db679-124">For more information and examples, see [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="db679-125">Deklarování parametrů typu varianty v obecných delegátech</span><span class="sxs-lookup"><span data-stu-id="db679-125">Declaring Variant Type Parameters in Generic Delegates</span></span>  
 <span data-ttu-id="db679-126">Pokud obecný delegát má covariant nebo contravariant obecný typ parametry, může být označován jako *varianta obecný delegát*.</span><span class="sxs-lookup"><span data-stu-id="db679-126">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>  
  
 <span data-ttu-id="db679-127">Můžete deklarovat parametr obecného typu kovarianta v obecnédelegát pomocí klíčového `out` slova.</span><span class="sxs-lookup"><span data-stu-id="db679-127">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="db679-128">Kovariantní typ lze použít pouze jako návratový typ metody a nikoli jako typ argumentů metody.</span><span class="sxs-lookup"><span data-stu-id="db679-128">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="db679-129">Následující příklad kódu ukazuje, jak deklarovat kovariantní obecný delegát.</span><span class="sxs-lookup"><span data-stu-id="db679-129">The following code example shows how to declare a covariant generic delegate.</span></span>  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 <span data-ttu-id="db679-130">Můžete deklarovat parametr obecného typu contravariant `in` v obecnédelegát pomocí klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="db679-130">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="db679-131">Typ contravariant lze použít pouze jako typ argumentů metody a nikoli jako návratový typ metody.</span><span class="sxs-lookup"><span data-stu-id="db679-131">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="db679-132">Následující příklad kódu ukazuje, jak deklarovat kontravariantní obecný delegát.</span><span class="sxs-lookup"><span data-stu-id="db679-132">The following code example shows how to declare a contravariant generic delegate.</span></span>  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="db679-133">`ref`, `in`a `out` parametry v c# nelze označit jako varianta.</span><span class="sxs-lookup"><span data-stu-id="db679-133">`ref`, `in`, and `out` parameters in C# can't be marked as variant.</span></span>  
  
 <span data-ttu-id="db679-134">Je také možné podporovat odchylky a kovariance ve stejném delegáta, ale pro různé parametry typu.</span><span class="sxs-lookup"><span data-stu-id="db679-134">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="db679-135">To je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="db679-135">This is shown in the following example.</span></span>  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="db679-136">Vytváření konkretista a vyvolání obecných delegátů variant</span><span class="sxs-lookup"><span data-stu-id="db679-136">Instantiating and Invoking Variant Generic Delegates</span></span>  
 <span data-ttu-id="db679-137">Můžete vytvořit instance a vyvolat delegáty varianty stejně jako konstanci a vyvolat invariantní delegáty.</span><span class="sxs-lookup"><span data-stu-id="db679-137">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="db679-138">V následujícím příkladu delegáta je vytvořena instance lambda výraz.</span><span class="sxs-lookup"><span data-stu-id="db679-138">In the following example, the delegate is instantiated by a lambda expression.</span></span>  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="db679-139">Kombinování typových obecných delegátů variant</span><span class="sxs-lookup"><span data-stu-id="db679-139">Combining Variant Generic Delegates</span></span>  
 <span data-ttu-id="db679-140">Neměli byste kombinovat delegáty variant.</span><span class="sxs-lookup"><span data-stu-id="db679-140">You should not combine variant delegates.</span></span> <span data-ttu-id="db679-141">Metoda <xref:System.Delegate.Combine%2A> nepodporuje převod delegáta varianta a očekává, že delegáti budou přesně stejného typu.</span><span class="sxs-lookup"><span data-stu-id="db679-141">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="db679-142">To může vést k výjimce za běhu při <xref:System.Delegate.Combine%2A> kombinaci delegátů `+` pomocí metody nebo pomocí operátoru, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="db679-142">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method or by using the `+` operator, as shown in the following code example.</span></span>  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="db679-143">Odchylka v parametrech obecného typu pro typy hodnot a odkazů</span><span class="sxs-lookup"><span data-stu-id="db679-143">Variance in Generic Type Parameters for Value and Reference Types</span></span>  
 <span data-ttu-id="db679-144">Odchylka pro parametry obecného typu je podporována pouze pro typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="db679-144">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="db679-145">Nelze například `DVariant<int>` implicitně převést na `DVariant<Object>` `DVariant<long>`nebo , protože celé číslo je typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="db679-145">For example, `DVariant<int>` can't be implicitly converted to `DVariant<Object>` or `DVariant<long>`, because integer is a value type.</span></span>  
  
 <span data-ttu-id="db679-146">Následující příklad ukazuje, že odchylka v parametrech obecného typu není pro typy hodnot podporována.</span><span class="sxs-lookup"><span data-stu-id="db679-146">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="db679-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="db679-147">See also</span></span>

- [<span data-ttu-id="db679-148">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="db679-148">Generics</span></span>](../../../../standard/generics/index.md)
- [<span data-ttu-id="db679-149">Použití odchylky pro obecné delegáty aplikace Func a obecné akce (C#)</span><span class="sxs-lookup"><span data-stu-id="db679-149">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
- [<span data-ttu-id="db679-150">Jak kombinovat delegáty (delegáti vícesměrového vysílání)</span><span class="sxs-lookup"><span data-stu-id="db679-150">How to combine delegates (Multicast Delegates)</span></span>](../../delegates/how-to-combine-delegates-multicast-delegates.md)
