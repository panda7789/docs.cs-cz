---
title: v – modifikátor parametrů (referenční dokumentace jazyka C#)
ms.date: 03/06/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9b8b21e2bdc95829c831ee71f24b47986321b7d0
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/23/2018
---
# <a name="in-parameter-modifier-c-reference"></a><span data-ttu-id="c6398-102">v – modifikátor parametrů (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c6398-102">in parameter modifier (C# Reference)</span></span>

<span data-ttu-id="c6398-103">`in` – Klíčové slovo způsobí, že argumenty předávané odkazem.</span><span class="sxs-lookup"><span data-stu-id="c6398-103">The `in` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="c6398-104">Je třeba [ref](ref.md) nebo [out](out-parameter-modifier.md) klíčová slova, která kromě `in` argumenty nemůže být upraven zavolat metodu, zatímco `ref` argumenty může být změněna, `out` argumenty je třeba upravit volající, a tyto úpravy jsou lze zobrazit v volání kontextu.</span><span class="sxs-lookup"><span data-stu-id="c6398-104">It is like the [ref](ref.md) or [out](out-parameter-modifier.md) keywords, except that `in` arguments cannot be modified by the called method, whereas `ref` arguments may be modified,  `out` arguments must be modified by the caller, and those modifications are observable in the calling context.</span></span>

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

<span data-ttu-id="c6398-105">Předchozí příklad ukazuje, který `in` modifikátor není nutný v lokalitě volání.</span><span class="sxs-lookup"><span data-stu-id="c6398-105">The preceding example demonstrates that the `in` modifier is unnecessary at the call site.</span></span> <span data-ttu-id="c6398-106">Je potřeba jenom v deklaraci metoda.</span><span class="sxs-lookup"><span data-stu-id="c6398-106">It is only required in the method declaration.</span></span>

> [!NOTE] 
> <span data-ttu-id="c6398-107">`in` – Klíčové slovo lze také s parametr obecného typu k určení, že parametr typu je kontravariant, jako součást `foreach` prohlášení, nebo jako součást `join` klauzuli v dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="c6398-107">The `in` keyword can also be used with a generic type parameter to specify that the type parameter is contravariant, as part of a `foreach` statement, or as part of a `join` clause in a LINQ query.</span></span> <span data-ttu-id="c6398-108">Další informace o použití `in` – klíčové slovo v těchto kontextů, najdete v části [v](in.md) který obsahuje odkazy na všechny tyto používá.</span><span class="sxs-lookup"><span data-stu-id="c6398-108">For more information on the use of the `in` keyword in these contexts, see [in](in.md) which provides links to all those uses.</span></span>
  
 <span data-ttu-id="c6398-109">Proměnné předány jako `in` argumenty se musí inicializovat před předáním ve volání metody.</span><span class="sxs-lookup"><span data-stu-id="c6398-109">Variables passed as `in` arguments must be initialized before being passed in a method call.</span></span> <span data-ttu-id="c6398-110">Volané metody však nemusí přiřadit hodnotu nebo upravte argument.</span><span class="sxs-lookup"><span data-stu-id="c6398-110">However, the called method may not assign a value or modify the argument.</span></span>  
  
 <span data-ttu-id="c6398-111">I když `in`, `ref`, a `out` klíčová slova způsobit různé chování, nejsou považovány za součást podpis metody v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="c6398-111">Although the `in`, `ref`, and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="c6398-112">Proto metody nemohou být přetíženy, pokud je jediným rozdílem je, že jedna metoda má `ref` nebo `in` argument a dalších trvá `out` argument.</span><span class="sxs-lookup"><span data-stu-id="c6398-112">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="c6398-113">Například následující kód, nebude kompilace:</span><span class="sxs-lookup"><span data-stu-id="c6398-113">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="c6398-114">Přetížení podle přítomnosti `in` je povoleno, ale generuje upozornění kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="c6398-114">Overloading based on the presence of `in` is allowed, but generates a compiler warning:</span></span>  
  
```csharp
class InOverloads
{
    // Discouraged. Calling SampleMethod(value) is ambiguous.
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

<span data-ttu-id="c6398-115">Vlastnosti nebo konstanty může být předána jako `in` parametry, protože volající metody nesmí změnit jejich hodnot.</span><span class="sxs-lookup"><span data-stu-id="c6398-115">Properties or constants may be passed as `in` parameters, because the calling method may not modify their values.</span></span>
  
<span data-ttu-id="c6398-116">Nelze použít `in`, `ref`, a `out` klíčová slova pro následující typy metod:</span><span class="sxs-lookup"><span data-stu-id="c6398-116">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="c6398-117">Asynchronní metody, které definují pomocí [asynchronní](../../../csharp/language-reference/keywords/async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="c6398-117">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
- <span data-ttu-id="c6398-118">Iterator metody, které zahrnují [yield vrátit](../../../csharp/language-reference/keywords/yield.md) nebo `yield break` příkaz.</span><span class="sxs-lookup"><span data-stu-id="c6398-118">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

<span data-ttu-id="c6398-119">Obvykle deklarovat `in` argumenty, aby se zabránilo operace kopírování, která je nezbytná k předání argumentů hodnotou.</span><span class="sxs-lookup"><span data-stu-id="c6398-119">You typically declare `in` arguments to avoid the copy operations necessary for passing arguments by value.</span></span> <span data-ttu-id="c6398-120">To je velmi užitečné, když argumenty jsou typy hodnot, jako je například struktury, kde jsou dražší než předání odkazem operace kopírování.</span><span class="sxs-lookup"><span data-stu-id="c6398-120">This is most useful when arguments are value types such as structures where copy operations are more expensive than passing by reference.</span></span>

> [!WARNING]
>  <span data-ttu-id="c6398-121">`in` Parametry může být i dražší, pokud došlo ke zneužití.</span><span class="sxs-lookup"><span data-stu-id="c6398-121">`in` parameters can be even more expensive if misused.</span></span> <span data-ttu-id="c6398-122">Kompilátor nemusí vědět, pokud člen metody upravit stav struct.</span><span class="sxs-lookup"><span data-stu-id="c6398-122">The compiler may not know if member methods modify the state of the struct.</span></span> <span data-ttu-id="c6398-123">Vždy, když kompilátor nebude moct zajistit, že objekt se nemění, obranu vytvoří kopii a volá člen odkazů pomocí tuto kopii.</span><span class="sxs-lookup"><span data-stu-id="c6398-123">Whenever the compiler cannot ensure that the object is not modified, it defensively creates a copy and calls member references using that copy.</span></span> <span data-ttu-id="c6398-124">Všechny možné změny se na tuto Obranným kopii.</span><span class="sxs-lookup"><span data-stu-id="c6398-124">Any possible modifications are to that defensive copy.</span></span> <span data-ttu-id="c6398-125">Dva způsoby, aby se zabránilo tyto kopie jsou předat `in` parametry jako `in` argumenty nebo k definování struktury jako `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="c6398-125">The two ways to avoid these copies are to pass `in` parameters as `in` arguments or to define structures as `readonly struct`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c6398-126">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c6398-126">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c6398-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6398-127">See Also</span></span>  
 [<span data-ttu-id="c6398-128">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c6398-128">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c6398-129">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="c6398-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c6398-130">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c6398-130">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="c6398-131">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="c6398-131">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)  
 [<span data-ttu-id="c6398-132">Odkaz na sémantiku s typy hodnot</span><span class="sxs-lookup"><span data-stu-id="c6398-132">Reference Semantics with Value Types</span></span>](../../../csharp/reference-semantics-with-value-types.md)
