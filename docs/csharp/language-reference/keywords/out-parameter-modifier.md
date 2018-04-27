---
title: out – modifikátor parametrů (Referenční dokumentace jazyka C#)
ms.date: 03/06/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 052416f97c1fe9ed3aa1a3bafa7410e602096991
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="1a753-102">out – modifikátor parametrů (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="1a753-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="1a753-103">`out` – Klíčové slovo způsobí, že argumenty předávané odkazem.</span><span class="sxs-lookup"><span data-stu-id="1a753-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="1a753-104">Je třeba [ref](ref.md) – klíčové slovo, vyjma toho, že `ref` vyžaduje, aby před předáním iniciována proměnnou.</span><span class="sxs-lookup"><span data-stu-id="1a753-104">It is like the [ref](ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="1a753-105">Je také jako [v](in-parameter-modifier.md) – klíčové slovo, vyjma toho, že `in` neumožňuje vyvolání metody k úpravě hodnota argumentu.</span><span class="sxs-lookup"><span data-stu-id="1a753-105">It is also like the [in](in-parameter-modifier.md) keyword, except that `in` does not allow the called method to modify the argument value.</span></span> <span data-ttu-id="1a753-106">Používat `out` nutné explicitně zadat parametr definici metody a volání metody `out` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="1a753-106">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="1a753-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1a753-107">For example:</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> <span data-ttu-id="1a753-108">`out` – Klíčové slovo lze také s parametr obecného typu k určení, že parametr typu je kovariant.</span><span class="sxs-lookup"><span data-stu-id="1a753-108">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="1a753-109">Další informace o použití `out` – klíčové slovo v tomto kontextu, najdete v části [out (generický modifikátor)](out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="1a753-109">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](out-generic-modifier.md).</span></span>
  
<span data-ttu-id="1a753-110">Proměnné předány jako `out` argumenty není nutné inicializovat před předáním ve volání metody.</span><span class="sxs-lookup"><span data-stu-id="1a753-110">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="1a753-111">Je však potřeba přiřadit hodnotu, než vrátí metoda zavolat metodu.</span><span class="sxs-lookup"><span data-stu-id="1a753-111">However, the called method is required to assign a value before the method returns.</span></span>  
  
<span data-ttu-id="1a753-112">I když `in`, `ref`, a `out` klíčová slova způsobit různé chování, nejsou považovány za součást podpis metody v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="1a753-112">Although the `in`, `ref`, and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="1a753-113">Proto metody nemohou být přetíženy, pokud je jediným rozdílem je, že jedna metoda má `ref` nebo `in` argument a dalších trvá `out` argument.</span><span class="sxs-lookup"><span data-stu-id="1a753-113">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="1a753-114">Například následující kód, nebude kompilace:</span><span class="sxs-lookup"><span data-stu-id="1a753-114">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="1a753-115">Přetížení je právní, ale pokud jedna metoda má `ref`, `in`, nebo `out` argument a dalších nemá žádný z těchto modifikátory takto:</span><span class="sxs-lookup"><span data-stu-id="1a753-115">Overloading is legal, however, if one method takes a `ref`, `in`, or `out` argument and the other has none of those modifiers, like this:</span></span>  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

<span data-ttu-id="1a753-116">Kompilátor vybere nejlepší přetížení porovnáním modifikátory parametr volání lokalitě, abyste modifikátory parametr použitá ve volání metody.</span><span class="sxs-lookup"><span data-stu-id="1a753-116">The compiler chooses the best overload by matching the parameter modifiers at the call site to the parameter modifiers used in the method call.</span></span>
 
<span data-ttu-id="1a753-117">Vlastnosti nejsou proměnné a proto ji nelze předat jako `out` parametry.</span><span class="sxs-lookup"><span data-stu-id="1a753-117">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>
  
 <span data-ttu-id="1a753-118">Informace o předávání polí najdete v tématu [předávání polí pomocí parametrů ref a out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="1a753-118">For information about passing arrays, see [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="1a753-119">Nelze použít `in`, `ref`, a `out` klíčová slova pro následující typy metod:</span><span class="sxs-lookup"><span data-stu-id="1a753-119">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
-   <span data-ttu-id="1a753-120">Asynchronní metody, které definují pomocí [asynchronní](../../../csharp/language-reference/keywords/async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="1a753-120">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
-   <span data-ttu-id="1a753-121">Iterator metody, které zahrnují [yield vrátit](../../../csharp/language-reference/keywords/yield.md) nebo `yield break` příkaz.</span><span class="sxs-lookup"><span data-stu-id="1a753-121">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

## <a name="declaring-out-arguments"></a><span data-ttu-id="1a753-122">Deklarování `out` argumenty</span><span class="sxs-lookup"><span data-stu-id="1a753-122">Declaring `out` arguments</span></span>   

 <span data-ttu-id="1a753-123">Deklarování metodu s `out` argumenty je užitečné, když chcete metody, která vrátí více hodnot.</span><span class="sxs-lookup"><span data-stu-id="1a753-123">Declaring a method with `out` arguments is useful when you want a method to return multiple values.</span></span> <span data-ttu-id="1a753-124">Následující příklad používá `out` vrátit tří proměnných pomocí volání jedné metody.</span><span class="sxs-lookup"><span data-stu-id="1a753-124">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="1a753-125">Všimněte si, že třetí argument je přiřazen na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="1a753-125">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="1a753-126">To umožňuje metody volitelně návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1a753-126">This enables methods to return values optionally.</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

 <span data-ttu-id="1a753-127">[Zkuste vzor](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) zahrnuje vrácení `bool` znamená, zda operace byla úspěšná a se nezdařilo a vrácení hodnoty vytvořeného operací v `out` argument.</span><span class="sxs-lookup"><span data-stu-id="1a753-127">The [Try pattern](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) involves returning a `bool` to indicate whether an operation succeeded and failed, and returning the value produced by the operation in an `out` argument.</span></span> <span data-ttu-id="1a753-128">Počet analýza metody, jako [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) metoda, použijte tento vzor.</span><span class="sxs-lookup"><span data-stu-id="1a753-128">A number of parsing methods, such as the [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) method, use this pattern.</span></span>
   
## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="1a753-129">Volání metody s `out` argument</span><span class="sxs-lookup"><span data-stu-id="1a753-129">Calling a method with an `out` argument</span></span>

<span data-ttu-id="1a753-130">V jazyce C# 6 a starší, před předáváme jako třeba deklarovat proměnnou v samostatný příkaz `out` argument.</span><span class="sxs-lookup"><span data-stu-id="1a753-130">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="1a753-131">Následující příklad deklaruje proměnné s názvem `number` předtím, než je předán [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metoda, která se pokusí převést řetězec na číslo.</span><span class="sxs-lookup"><span data-stu-id="1a753-131">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

<span data-ttu-id="1a753-132">Od verze 7.0 C#, můžou deklarovat `out` proměnné v seznamu argumentů volání metody, a nikoli v samostatných deklarace proměnné.</span><span class="sxs-lookup"><span data-stu-id="1a753-132">Starting with C# 7.0, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="1a753-133">To vytváří kompaktnější a čitelné kódu a taky brání nechtěně přiřazení hodnoty proměnné před volání metody.</span><span class="sxs-lookup"><span data-stu-id="1a753-133">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="1a753-134">Následující příklad je jako předchozí příklad, s tím rozdílem, že definuje `number` proměnné ve volání [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metoda.</span><span class="sxs-lookup"><span data-stu-id="1a753-134">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
<span data-ttu-id="1a753-135">V předchozím příkladu `number` proměnné je silného typu jako `int`.</span><span class="sxs-lookup"><span data-stu-id="1a753-135">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="1a753-136">Implicitně typované lokální proměnné a můžete také deklarovat, stejně jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1a753-136">You can also declare an implicitly typed local variable, as the following example does.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a><span data-ttu-id="1a753-137">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1a753-137">C# Language Specification</span></span>  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1a753-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="1a753-138">See Also</span></span>  
 [<span data-ttu-id="1a753-139">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1a753-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1a753-140">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="1a753-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1a753-141">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1a753-141">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="1a753-142">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="1a753-142">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
