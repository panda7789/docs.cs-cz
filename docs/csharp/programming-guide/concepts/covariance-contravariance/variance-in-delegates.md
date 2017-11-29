---
title: "Odchylky v delegátech (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6eacc9f6ac815e01c446f7cdea6026904ad2ba90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="variance-in-delegates-c"></a><span data-ttu-id="9f842-102">Odchylky v delegátech (C#)</span><span class="sxs-lookup"><span data-stu-id="9f842-102">Variance in Delegates (C#)</span></span>
<span data-ttu-id="9f842-103">Rozhraní .NET framework 3.5 byla zavedena podpora odchylku odpovídající metoda podpisy s typy delegáta v všechny Delegáti v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="9f842-103">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C#.</span></span> <span data-ttu-id="9f842-104">To znamená, že můžete přiřadit deleguje pouze metody, které mají odpovídající podpisy, ale také metody, které vracejí informace odvozené typy (kovariance) nebo pracujících s parametry, které mají méně odvozené typy (kontravariance) než je určeno typ delegáta .</span><span class="sxs-lookup"><span data-stu-id="9f842-104">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="9f842-105">To zahrnuje obecné a neobecné delegáti.</span><span class="sxs-lookup"><span data-stu-id="9f842-105">This includes both generic and non-generic delegates.</span></span>  
  
 <span data-ttu-id="9f842-106">Zvažte například následující kód, který má dvě třídy a dvě delegáti: Obecné a neobecné.</span><span class="sxs-lookup"><span data-stu-id="9f842-106">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 <span data-ttu-id="9f842-107">Při vytváření delegátů `SampleDelegate` nebo `SampleGenericDelegate<A, R>` typy, můžete přiřadit jednu z následujících metod těchto delegáti.</span><span class="sxs-lookup"><span data-stu-id="9f842-107">When you create delegates of the `SampleDelegate` or `SampleGenericDelegate<A, R>` types, you can assign any one of the following methods to those delegates.</span></span>  
  
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
  
 <span data-ttu-id="9f842-108">Následující příklad kódu ukazuje implicitní převod mezi podpis metody a typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="9f842-108">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>  
  
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
  
 <span data-ttu-id="9f842-109">Další příklady najdete v tématu [použití odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) a [pomocí odchylky pro Func a akce obecní delegáti (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="9f842-109">For more examples, see [Using Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="9f842-110">Odchylky v obecné parametry typu</span><span class="sxs-lookup"><span data-stu-id="9f842-110">Variance in Generic Type Parameters</span></span>  
 <span data-ttu-id="9f842-111">V rozhraní .NET Framework 4 nebo novější můžete povolit implicitní převod mezi delegáti, tak, aby obecní delegáti, které mají různé typy určeného parametry obecného typu lze přiřadit k sobě navzájem, pokud jsou typy zděděn od sebe navzájem podle požadavků odchylky.</span><span class="sxs-lookup"><span data-stu-id="9f842-111">In .NET Framework 4 or later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>  
  
 <span data-ttu-id="9f842-112">Pokud chcete povolit implicitní převod, je potřeba explicitně deklarovat obecné parametry v delegáta jako kovariantní nebo kontravariant pomocí `in` nebo `out` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="9f842-112">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>  
  
 <span data-ttu-id="9f842-113">Následující příklad kódu ukazuje, jak můžete vytvořit delegáta, který má parametr kovariantní obecného typu.</span><span class="sxs-lookup"><span data-stu-id="9f842-113">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>  
  
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
  
 <span data-ttu-id="9f842-114">Pokud používáte pouze odchylky podporu tak, aby odpovídaly podpisy, metoda delegovat typy a nepoužívejte `in` a `out` klíčová slova, můžete zjistit, že v některých případech může vytvořit instanci delegáti s identické lambda – výrazy nebo metod, ale nemůžete Přiřaďte jednoho delegáta do jiného.</span><span class="sxs-lookup"><span data-stu-id="9f842-114">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>  
  
 <span data-ttu-id="9f842-115">V následujícím příkladu kódu `SampleGenericDelegate<String>` nelze explicitně převést na `SampleGenericDelegate<Object>`, i když `String` dědí `Object`.</span><span class="sxs-lookup"><span data-stu-id="9f842-115">In the following code example, `SampleGenericDelegate<String>` cannot be explicitly converted to `SampleGenericDelegate<Object>`, although `String` inherits `Object`.</span></span> <span data-ttu-id="9f842-116">Tento problém lze vyřešit označení obecný parametr `T` s `out` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="9f842-116">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a><span data-ttu-id="9f842-117">Obecní delegáti, které mají typ Variant parametry typu v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9f842-117">Generic Delegates That Have Variant Type Parameters in the .NET Framework</span></span>  
 <span data-ttu-id="9f842-118">Rozhraní .NET framework 4 zavedl podporu odchylky pro parametry obecného typu v několika existující obecní delegáti:</span><span class="sxs-lookup"><span data-stu-id="9f842-118">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>  
  
-   <span data-ttu-id="9f842-119">`Action`Deleguje z <xref:System> obor názvů, například <xref:System.Action%601> a<xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="9f842-119">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>  
  
-   <span data-ttu-id="9f842-120">`Func`Deleguje z <xref:System> obor názvů, například <xref:System.Func%601> a<xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="9f842-120">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>  
  
-   <span data-ttu-id="9f842-121"><xref:System.Predicate%601> Delegovat</span><span class="sxs-lookup"><span data-stu-id="9f842-121">The <xref:System.Predicate%601> delegate</span></span>  
  
-   <span data-ttu-id="9f842-122"><xref:System.Comparison%601> Delegovat</span><span class="sxs-lookup"><span data-stu-id="9f842-122">The <xref:System.Comparison%601> delegate</span></span>  
  
-   <span data-ttu-id="9f842-123"><xref:System.Converter%602> Delegovat</span><span class="sxs-lookup"><span data-stu-id="9f842-123">The <xref:System.Converter%602> delegate</span></span>  
  
 <span data-ttu-id="9f842-124">Další informace a příklady naleznete v tématu [pomocí odchylky pro Func a akce obecní delegáti (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="9f842-124">For more information and examples, see [Using Variance for Func and Action Generic Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="9f842-125">Deklarující typ varianty parametry v obecní delegáti</span><span class="sxs-lookup"><span data-stu-id="9f842-125">Declaring Variant Type Parameters in Generic Delegates</span></span>  
 <span data-ttu-id="9f842-126">Pokud má obecný delegát kovariantní nebo kontravariant parametry obecného typu, ho lze odkazovat jako *variant obecný delegát*.</span><span class="sxs-lookup"><span data-stu-id="9f842-126">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>  
  
 <span data-ttu-id="9f842-127">Je možné deklarovat parametr obecného typu kovariantní v obecný delegát pomocí `out` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="9f842-127">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="9f842-128">Typ kovariantní lze použít pouze jako návratový typ metody a ne jako typ metoda argumenty.</span><span class="sxs-lookup"><span data-stu-id="9f842-128">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="9f842-129">Následující příklad kódu ukazuje, jak deklarovat kovariantní obecný delegát.</span><span class="sxs-lookup"><span data-stu-id="9f842-129">The following code example shows how to declare a covariant generic delegate.</span></span>  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 <span data-ttu-id="9f842-130">Je možné deklarovat kontravariant parametr obecného typu v obecný delegát pomocí `in` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="9f842-130">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="9f842-131">Typ kontravariant lze použít pouze jako typ argumenty metody a ne jako návratový typ. metoda.</span><span class="sxs-lookup"><span data-stu-id="9f842-131">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="9f842-132">Následující příklad kódu ukazuje, jak deklarovat obecný delegát kontravariant.</span><span class="sxs-lookup"><span data-stu-id="9f842-132">The following code example shows how to declare a contravariant generic delegate.</span></span>  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="9f842-133">`ref`a `out` parametry v jazyce C# nelze označit jako typ variant.</span><span class="sxs-lookup"><span data-stu-id="9f842-133">`ref` and `out` parameters in C# can't be marked as variant.</span></span>  
  
 <span data-ttu-id="9f842-134">Je také možné podporovat odchylky a Kovariance v stejného delegáta, ale pro jiný typ parametry.</span><span class="sxs-lookup"><span data-stu-id="9f842-134">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="9f842-135">To je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9f842-135">This is shown in the following example.</span></span>  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="9f842-136">Vytváření instancí a vyvolání Variant obecní delegáti</span><span class="sxs-lookup"><span data-stu-id="9f842-136">Instantiating and Invoking Variant Generic Delegates</span></span>  
 <span data-ttu-id="9f842-137">Můžete vytvořit instanci a vyvolání variant delegáti stejně, jako je vytváření instancí a vyvolání invariantní delegáti.</span><span class="sxs-lookup"><span data-stu-id="9f842-137">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="9f842-138">V následujícím příkladu je vytvořena instance delegáta pomocí výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="9f842-138">In the following example, the delegate is instantiated by a lambda expression.</span></span>  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="9f842-139">Kombinování Variant obecní delegáti</span><span class="sxs-lookup"><span data-stu-id="9f842-139">Combining Variant Generic Delegates</span></span>  
 <span data-ttu-id="9f842-140">Nesmí kombinovat variant delegáti.</span><span class="sxs-lookup"><span data-stu-id="9f842-140">You should not combine variant delegates.</span></span> <span data-ttu-id="9f842-141"><xref:System.Delegate.Combine%2A> Metoda nepodporuje převod variant delegáta a očekává delegáti být přesně stejného typu.</span><span class="sxs-lookup"><span data-stu-id="9f842-141">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="9f842-142">To může vést ke spuštění výjimka při kombinování delegátů buď pomocí <xref:System.Delegate.Combine%2A> metoda nebo pomocí `+` operátor, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="9f842-142">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method or by using the `+` operator, as shown in the following code example.</span></span>  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="9f842-143">Odchylky v parametry obecného typu pro hodnotových a odkazových typech</span><span class="sxs-lookup"><span data-stu-id="9f842-143">Variance in Generic Type Parameters for Value and Reference Types</span></span>  
 <span data-ttu-id="9f842-144">Odchylky pro parametry obecného typu je podporována pro odkazové typy pouze.</span><span class="sxs-lookup"><span data-stu-id="9f842-144">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="9f842-145">Například `DVariant<int>` nelze implicitně převést na `DVariant<Object>` nebo `DVariant<long>`, protože typ hodnoty je celé číslo.</span><span class="sxs-lookup"><span data-stu-id="9f842-145">For example, `DVariant<int>` can't be implicitly converted to `DVariant<Object>` or `DVariant<long>`, because integer is a value type.</span></span>  
  
 <span data-ttu-id="9f842-146">Následující příklad ukazuje, že odchylky v obecného typu parametry není podporována u typů hodnot.</span><span class="sxs-lookup"><span data-stu-id="9f842-146">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9f842-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f842-147">See Also</span></span>  
 [<span data-ttu-id="9f842-148">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="9f842-148">Generics</span></span>](~/docs/standard/generics/index.md)  
 [<span data-ttu-id="9f842-149">Použití odchylek pro Func a akce obecní delegáti (C#)</span><span class="sxs-lookup"><span data-stu-id="9f842-149">Using Variance for Func and Action Generic Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)  
 [<span data-ttu-id="9f842-150">Postupy: kombinování delegátů (vícesměroví delegáti)</span><span class="sxs-lookup"><span data-stu-id="9f842-150">How to: Combine Delegates (Multicast Delegates)</span></span>](../../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
