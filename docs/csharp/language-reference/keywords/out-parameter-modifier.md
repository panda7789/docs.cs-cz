---
title: "out – modifikátor parametrů (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.assetid: 3fce0dc5-03f4-4faa-bd61-36c41bc6baf1
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 68ef554f95fe71f925cfa22cc49758cec3da237e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="37b1d-102">out – modifikátor parametrů (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="37b1d-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="37b1d-103">`out` – Klíčové slovo způsobí, že argumenty předávané odkazem.</span><span class="sxs-lookup"><span data-stu-id="37b1d-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="37b1d-104">Je třeba [ref](../../../csharp/language-reference/keywords/ref.md) – klíčové slovo, vyjma toho, že `ref` vyžaduje, aby před předáním iniciována proměnnou.</span><span class="sxs-lookup"><span data-stu-id="37b1d-104">It is like the [ref](../../../csharp/language-reference/keywords/ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="37b1d-105">Používat `out` nutné explicitně zadat parametr definici metody a volání metody `out` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="37b1d-105">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="37b1d-106">Příklad:</span><span class="sxs-lookup"><span data-stu-id="37b1d-106">For example:</span></span>  
  
 [!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/out/out-1.cs)]  

> [!NOTE] 
> <span data-ttu-id="37b1d-107">`out` – Klíčové slovo lze také s parametr obecného typu k určení, že parametr typu je kovariant.</span><span class="sxs-lookup"><span data-stu-id="37b1d-107">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="37b1d-108">Další informace o použití `out` – klíčové slovo v tomto kontextu, najdete v části [out (generický modifikátor)](../../../csharp/language-reference/keywords/out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="37b1d-108">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](../../../csharp/language-reference/keywords/out-generic-modifier.md).</span></span>
  
 <span data-ttu-id="37b1d-109">Proměnné předány jako `out` argumenty není nutné inicializovat před předáním ve volání metody.</span><span class="sxs-lookup"><span data-stu-id="37b1d-109">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="37b1d-110">Je však potřeba přiřadit hodnotu, než vrátí metoda zavolat metodu.</span><span class="sxs-lookup"><span data-stu-id="37b1d-110">However, the called method is required to assign a value before the method returns.</span></span>  
  
 <span data-ttu-id="37b1d-111">I když `ref` a `out` klíčová slova způsobit různé chování, nejsou považovány za součást podpis metody v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="37b1d-111">Although the `ref` and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="37b1d-112">Proto metody nemohou být přetíženy, pokud je jediným rozdílem je, že jedna metoda má `ref` argument a dalších trvá `out` argument.</span><span class="sxs-lookup"><span data-stu-id="37b1d-112">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="37b1d-113">Například následující kód, nebude kompilace:</span><span class="sxs-lookup"><span data-stu-id="37b1d-113">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="37b1d-114">Přetížení je právní, ale pokud jedna metoda má `ref` nebo `out` argument a dalších používá ani takto:</span><span class="sxs-lookup"><span data-stu-id="37b1d-114">Overloading is legal, however, if one method takes a `ref` or `out` argument and the other uses neither, like this:</span></span>  
  
 [!code-csharp[csrefKeywordsMethodParams#3](../../../../samples/snippets/csharp/language-reference/keywords/out/out-3.cs)]  
  
 <span data-ttu-id="37b1d-115">Vlastnosti nejsou proměnné a proto ji nelze předat jako `out` parametry.</span><span class="sxs-lookup"><span data-stu-id="37b1d-115">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>  
  
 <span data-ttu-id="37b1d-116">Informace o předávání polí najdete v tématu [předávání polí pomocí parametrů ref a out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="37b1d-116">For information about passing arrays, see [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="37b1d-117">Nelze použít `ref` a `out` klíčová slova pro následující typy metod:</span><span class="sxs-lookup"><span data-stu-id="37b1d-117">You can't use the `ref` and `out` keywords for the following kinds of methods:</span></span>  
  
-   <span data-ttu-id="37b1d-118">Asynchronní metody, které definují pomocí [asynchronní](../../../csharp/language-reference/keywords/async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="37b1d-118">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
-   <span data-ttu-id="37b1d-119">Iterator metody, které zahrnují [yield vrátit](../../../csharp/language-reference/keywords/yield.md) nebo `yield break` příkaz.</span><span class="sxs-lookup"><span data-stu-id="37b1d-119">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

## <a name="declaring-out-arguments"></a><span data-ttu-id="37b1d-120">Deklarování `out` argumenty</span><span class="sxs-lookup"><span data-stu-id="37b1d-120">Declaring `out` arguments</span></span>   

 <span data-ttu-id="37b1d-121">Deklarování metodu s `out` argumenty je užitečné, když chcete metody, která vrátí více hodnot.</span><span class="sxs-lookup"><span data-stu-id="37b1d-121">Declaring a method with `out` arguments is useful when you want a method to return multiple values.</span></span> <span data-ttu-id="37b1d-122">Následující příklad používá `out` vrátit tří proměnných pomocí volání jedné metody.</span><span class="sxs-lookup"><span data-stu-id="37b1d-122">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="37b1d-123">Všimněte si, že třetí argument je přiřazen na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="37b1d-123">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="37b1d-124">To umožňuje metody volitelně návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="37b1d-124">This enables methods to return values optionally.</span></span>  
  
 [!code-csharp[csrefKeywordsMethodParams#4](../../../../samples/snippets/csharp/language-reference/keywords/out/out-4.cs)]  

 <span data-ttu-id="37b1d-125">[Zkuste vzor](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) zahrnuje vrácení `bool` znamená, zda operace byla úspěšná a se nezdařilo a vrácení hodnoty vytvořeného operací v `out` argument.</span><span class="sxs-lookup"><span data-stu-id="37b1d-125">The [Try pattern](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) involves returning a `bool` to indicate whether an operation succeeded and failed, and returning the value produced by the operation in an `out` argument.</span></span> <span data-ttu-id="37b1d-126">Počet analýza metody, jako [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) metoda, použijte tento vzor.</span><span class="sxs-lookup"><span data-stu-id="37b1d-126">A number of parsing methods, such as the [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) method, use this pattern.</span></span>
   
## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="37b1d-127">Volání metody s `out` argument</span><span class="sxs-lookup"><span data-stu-id="37b1d-127">Calling a method with an `out` argument</span></span>

<span data-ttu-id="37b1d-128">V jazyce C# 6 a starší, před předáváme jako třeba deklarovat proměnnou v samostatný příkaz `out` argument.</span><span class="sxs-lookup"><span data-stu-id="37b1d-128">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="37b1d-129">Následující příklad deklaruje proměnné s názvem `number` předtím, než je předán [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metoda, která se pokusí převést řetězec na číslo.</span><span class="sxs-lookup"><span data-stu-id="37b1d-129">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

 [!code-csharp[csrefKeywordsMethodParams#5](../../../../samples/snippets/csharp/language-reference/keywords/out/out-5.cs)]  

<span data-ttu-id="37b1d-130">Od verze jazyka C# 7, můžou deklarovat `out` proměnné v seznamu argumentů volání metody, a nikoli v samostatných deklarace proměnné.</span><span class="sxs-lookup"><span data-stu-id="37b1d-130">Starting with C# 7, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="37b1d-131">To vytváří kompaktnější a čitelné kódu a taky brání nechtěně přiřazení hodnoty proměnné před volání metody.</span><span class="sxs-lookup"><span data-stu-id="37b1d-131">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="37b1d-132">Následující příklad je jako předchozí příklad, s tím rozdílem, že definuje `number` proměnné ve volání [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metoda.</span><span class="sxs-lookup"><span data-stu-id="37b1d-132">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

 [!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/out/out-6.cs)]  
   
<span data-ttu-id="37b1d-133">V předchozím příkladu `number` proměnné je silného typu jako `int`.</span><span class="sxs-lookup"><span data-stu-id="37b1d-133">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="37b1d-134">Implicitně typované lokální proměnné a můžete také deklarovat, stejně jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="37b1d-134">You can also declare an implicitly typed local variable, as the following example does.</span></span>

 [!code-csharp[csrefKeywordsMethodParams#7](../../../../samples/snippets/csharp/language-reference/keywords/out/out-7.cs)]  
   
## <a name="c-language-specification"></a><span data-ttu-id="37b1d-135">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="37b1d-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="37b1d-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="37b1d-136">See Also</span></span>  
 [<span data-ttu-id="37b1d-137">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="37b1d-137">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="37b1d-138">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="37b1d-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="37b1d-139">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="37b1d-139">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="37b1d-140">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="37b1d-140">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
