---
title: Odchylky v delegátech (C#)
ms.date: 07/20/2015
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
ms.openlocfilehash: 3dabac4e532198871cf05d639aa692751ab17ae1
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43884426"
---
# <a name="variance-in-delegates-c"></a><span data-ttu-id="34e64-102">Odchylky v delegátech (C#)</span><span class="sxs-lookup"><span data-stu-id="34e64-102">Variance in Delegates (C#)</span></span>
<span data-ttu-id="34e64-103">Rozhraní .NET framework 3.5 představil podporu odchylku pro spárování metod podpisů s typy delegáta v Všichni delegáti v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="34e64-103">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C#.</span></span> <span data-ttu-id="34e64-104">To znamená, že můžete přiřadit delegáty pouze metody, které mají odpovídající podpisy, ale také metody, které vracejí informace odvozené typy (kovariance) nebo, která přijímají parametry, které mají méně odvozené typy (kontravariance), než je určeno typ delegáta .</span><span class="sxs-lookup"><span data-stu-id="34e64-104">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="34e64-105">To zahrnuje obecných a neobecných delegátů.</span><span class="sxs-lookup"><span data-stu-id="34e64-105">This includes both generic and non-generic delegates.</span></span>  
  
 <span data-ttu-id="34e64-106">Zvažte například následující kód, který má dvě třídy a dvou delegátů: obecných a neobecných.</span><span class="sxs-lookup"><span data-stu-id="34e64-106">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 <span data-ttu-id="34e64-107">Při vytváření delegátů `SampleDelegate` nebo `SampleGenericDelegate<A, R>` typy, můžete přiřadit jednu z následujících metod na tyto delegáty.</span><span class="sxs-lookup"><span data-stu-id="34e64-107">When you create delegates of the `SampleDelegate` or `SampleGenericDelegate<A, R>` types, you can assign any one of the following methods to those delegates.</span></span>  
  
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
  
 <span data-ttu-id="34e64-108">Následující příklad kódu ukazuje implicitní převod mezi podpisu metody a typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="34e64-108">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>  
  
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
  
 <span data-ttu-id="34e64-109">Další příklady najdete v tématu [použití odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) a [pomocí odchylku pro delegáty Func a Action obecný (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="34e64-109">For more examples, see [Using Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="34e64-110">Variance u parametrů obecného typu</span><span class="sxs-lookup"><span data-stu-id="34e64-110">Variance in Generic Type Parameters</span></span>  
 <span data-ttu-id="34e64-111">V rozhraní .NET Framework 4 nebo novější můžete povolit implicitní převod mezi delegáty, tak, aby obecné delegáty, které mají různé typy určené parametry obecného typu lze přiřadit k sobě navzájem, pokud typ dědí od sebe navzájem podle požadavků Variance.</span><span class="sxs-lookup"><span data-stu-id="34e64-111">In .NET Framework 4 or later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>  
  
 <span data-ttu-id="34e64-112">Pokud chcete povolit implicitní převod, musíte explicitně deklarovat obecných parametrů v delegátů jako kovariantní nebo kontravariantní pomocí `in` nebo `out` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="34e64-112">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>  
  
 <span data-ttu-id="34e64-113">Následující příklad kódu ukazuje, jak můžete vytvořit delegáta, který má parametr kovariantního obecného typu.</span><span class="sxs-lookup"><span data-stu-id="34e64-113">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>  
  
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
  
 <span data-ttu-id="34e64-114">Pokud používáte podporují jenom variance tak, aby odpovídaly metod podpisů s typy delegátů a nepoužívají `in` a `out` klíčová slova, možná zjistíte, že v některých případech můžete vytvořit instanci delegáty s identické lambda výrazy nebo metody, ale nemůžete přiřaďte jeden delegáta do jiného.</span><span class="sxs-lookup"><span data-stu-id="34e64-114">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>  
  
 <span data-ttu-id="34e64-115">V následujícím příkladu kódu `SampleGenericDelegate<String>` nelze explicitně převést na `SampleGenericDelegate<Object>`, i když `String` dědí `Object`.</span><span class="sxs-lookup"><span data-stu-id="34e64-115">In the following code example, `SampleGenericDelegate<String>` cannot be explicitly converted to `SampleGenericDelegate<Object>`, although `String` inherits `Object`.</span></span> <span data-ttu-id="34e64-116">Tento problém můžete vyřešit označením obecných parametrů `T` s `out` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="34e64-116">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a><span data-ttu-id="34e64-117">Parametry typu obecné delegáty, které mají typ Variant v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="34e64-117">Generic Delegates That Have Variant Type Parameters in the .NET Framework</span></span>  
 <span data-ttu-id="34e64-118">Rozhraní .NET framework 4 zavedena podpora odchylku pro parametry obecného typu v několika existující obecné delegáty:</span><span class="sxs-lookup"><span data-stu-id="34e64-118">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>  
  
-   <span data-ttu-id="34e64-119">`Action` Deleguje z <xref:System> obor názvů, třeba <xref:System.Action%601> a <xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="34e64-119">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>  
  
-   <span data-ttu-id="34e64-120">`Func` Deleguje z <xref:System> obor názvů, třeba <xref:System.Func%601> a <xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="34e64-120">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>  
  
-   <span data-ttu-id="34e64-121"><xref:System.Predicate%601> Delegovat</span><span class="sxs-lookup"><span data-stu-id="34e64-121">The <xref:System.Predicate%601> delegate</span></span>  
  
-   <span data-ttu-id="34e64-122"><xref:System.Comparison%601> Delegovat</span><span class="sxs-lookup"><span data-stu-id="34e64-122">The <xref:System.Comparison%601> delegate</span></span>  
  
-   <span data-ttu-id="34e64-123"><xref:System.Converter%602> Delegovat</span><span class="sxs-lookup"><span data-stu-id="34e64-123">The <xref:System.Converter%602> delegate</span></span>  
  
 <span data-ttu-id="34e64-124">Další informace a příklady najdete v tématu [pomocí odchylku pro delegáty Func a Action obecný (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="34e64-124">For more information and examples, see [Using Variance for Func and Action Generic Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="34e64-125">Deklarování parametry variantního typu v obecné delegáty</span><span class="sxs-lookup"><span data-stu-id="34e64-125">Declaring Variant Type Parameters in Generic Delegates</span></span>  
 <span data-ttu-id="34e64-126">Pokud obecného delegátu má kovariantní nebo kontravariantní parametry obecného typu, jej lze odkazovat jako *variant obecného delegátu*.</span><span class="sxs-lookup"><span data-stu-id="34e64-126">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>  
  
 <span data-ttu-id="34e64-127">Je možné deklarovat parametr obecného typu Kovariance v obecných delegátů pomocí `out` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="34e64-127">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="34e64-128">Kovariantního typu lze použít pouze jako návratový typ metody a ne jako typ argumentů metody.</span><span class="sxs-lookup"><span data-stu-id="34e64-128">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="34e64-129">Následující příklad kódu ukazuje, jak deklarovat kovariantního obecného delegáta.</span><span class="sxs-lookup"><span data-stu-id="34e64-129">The following code example shows how to declare a covariant generic delegate.</span></span>  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 <span data-ttu-id="34e64-130">Kontravariantního parametru obecného typu v obecného delegátu lze deklarovat s použitím `in` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="34e64-130">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="34e64-131">Kontravariantního typu lze použít pouze jako argumenty metody typu, nikoli jako návratový typ metody.</span><span class="sxs-lookup"><span data-stu-id="34e64-131">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="34e64-132">Následující příklad kódu ukazuje, jak deklarovat delegáta obecného kontravariantního.</span><span class="sxs-lookup"><span data-stu-id="34e64-132">The following code example shows how to declare a contravariant generic delegate.</span></span>  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="34e64-133">`ref`, `in`, a `out` parametry v jazyce C# nelze označit jako typ variant.</span><span class="sxs-lookup"><span data-stu-id="34e64-133">`ref`, `in`, and `out` parameters in C# can't be marked as variant.</span></span>  
  
 <span data-ttu-id="34e64-134">Je také možné podporovat odchylky a Kovariance v stejného delegáta, ale pro jiný typ parametrů.</span><span class="sxs-lookup"><span data-stu-id="34e64-134">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="34e64-135">To je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="34e64-135">This is shown in the following example.</span></span>  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="34e64-136">Vytváření instancí a volání Variant obecných delegátů</span><span class="sxs-lookup"><span data-stu-id="34e64-136">Instantiating and Invoking Variant Generic Delegates</span></span>  
 <span data-ttu-id="34e64-137">Můžete konkretizovat a vyvoláte variant stejně jako můžete vytvořit instanci nebo vyvoláte invariantní.</span><span class="sxs-lookup"><span data-stu-id="34e64-137">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="34e64-138">V následujícím příkladu je vytvořena instance delegáta ve výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="34e64-138">In the following example, the delegate is instantiated by a lambda expression.</span></span>  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="34e64-139">Kombinování variantních obecných delegátů</span><span class="sxs-lookup"><span data-stu-id="34e64-139">Combining Variant Generic Delegates</span></span>  
 <span data-ttu-id="34e64-140">Neměli kombinovat variant delegátů.</span><span class="sxs-lookup"><span data-stu-id="34e64-140">You should not combine variant delegates.</span></span> <span data-ttu-id="34e64-141"><xref:System.Delegate.Combine%2A> Metoda nepodporuje převod variant delegáta a očekává, že delegáty být stejného typu.</span><span class="sxs-lookup"><span data-stu-id="34e64-141">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="34e64-142">To může vést k výjimce za běhu při kombinování delegátů pomocí <xref:System.Delegate.Combine%2A> metody nebo pomocí `+` operátoru, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="34e64-142">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method or by using the `+` operator, as shown in the following code example.</span></span>  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="34e64-143">Variance u parametrů obecného typu pro hodnotových a odkazových typech</span><span class="sxs-lookup"><span data-stu-id="34e64-143">Variance in Generic Type Parameters for Value and Reference Types</span></span>  
 <span data-ttu-id="34e64-144">Variance u parametrů obecného typu je podporována pouze pro typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="34e64-144">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="34e64-145">Například `DVariant<int>` nejde implicitně převést na `DVariant<Object>` nebo `DVariant<long>`, protože se hodnota typu celé číslo.</span><span class="sxs-lookup"><span data-stu-id="34e64-145">For example, `DVariant<int>` can't be implicitly converted to `DVariant<Object>` or `DVariant<long>`, because integer is a value type.</span></span>  
  
 <span data-ttu-id="34e64-146">Následující příklad ukazuje, že variance v obecném typu se nepodporuje parametry pro typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="34e64-146">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="34e64-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="34e64-147">See Also</span></span>

- [<span data-ttu-id="34e64-148">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="34e64-148">Generics</span></span>](~/docs/standard/generics/index.md)  
- [<span data-ttu-id="34e64-149">Použití odchylek pro delegáty Func a Action obecný (C#)</span><span class="sxs-lookup"><span data-stu-id="34e64-149">Using Variance for Func and Action Generic Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)  
- [<span data-ttu-id="34e64-150">Postupy: kombinování delegátů (vícesměroví delegáti)</span><span class="sxs-lookup"><span data-stu-id="34e64-150">How to: Combine Delegates (Multicast Delegates)</span></span>](../../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
