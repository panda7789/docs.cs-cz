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
ms.openlocfilehash: 3c15cc0dce5b37866fd826e3d6b9adcb00724672
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2018
---
# <a name="in-parameter-modifier-c-reference"></a><span data-ttu-id="d5c2d-102">v – modifikátor parametrů (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d5c2d-102">in parameter modifier (C# Reference)</span></span>

<span data-ttu-id="d5c2d-103">`in` – Klíčové slovo způsobí, že argumenty předávané odkazem.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-103">The `in` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="d5c2d-104">Je třeba [ref](ref.md) nebo [out](out-parameter-modifier.md) klíčová slova, která kromě `in` argumenty nemůže být upraven zavolat metodu, zatímco `ref` argumenty může být změněna, `out` argumenty je třeba upravit volající, a tyto úpravy jsou lze zobrazit v volání kontextu.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-104">It is like the [ref](ref.md) or [out](out-parameter-modifier.md) keywords, except that `in` arguments cannot be modified by the called method, whereas `ref` arguments may be modified,  `out` arguments must be modified by the caller, and those modifications are observable in the calling context.</span></span>

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

<span data-ttu-id="d5c2d-105">Předchozí příklad ukazuje `in` modifikátor není nutný, obvykle v lokalitě volání.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-105">The preceding example demonstrates the `in` modifier is usually unnecessary at the call site.</span></span> <span data-ttu-id="d5c2d-106">Je potřeba jenom v deklaraci metoda.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-106">It is only required in the method declaration.</span></span>

> [!NOTE] 
> <span data-ttu-id="d5c2d-107">`in` – Klíčové slovo lze také s parametr obecného typu k určení, že parametr typu je kontravariant, jako součást `foreach` prohlášení, nebo jako součást `join` klauzuli v dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-107">The `in` keyword can also be used with a generic type parameter to specify that the type parameter is contravariant, as part of a `foreach` statement, or as part of a `join` clause in a LINQ query.</span></span> <span data-ttu-id="d5c2d-108">Další informace o použití `in` – klíčové slovo v těchto kontextů, najdete v části [v](in.md), který obsahuje odkazy na všechny tyto používá.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-108">For more information on the use of the `in` keyword in these contexts, see [in](in.md), which provides links to all those uses.</span></span>
  
 <span data-ttu-id="d5c2d-109">Proměnné předány jako `in` argumenty se musí inicializovat před předáním ve volání metody.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-109">Variables passed as `in` arguments must be initialized before being passed in a method call.</span></span> <span data-ttu-id="d5c2d-110">Volané metody však nemusí přiřadit hodnotu nebo upravte argument.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-110">However, the called method may not assign a value or modify the argument.</span></span>  
  
 <span data-ttu-id="d5c2d-111">I když `in`, `ref`, a `out` klíčová slova způsobit různé chování, nejsou považovány za součást podpis metody v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-111">Although the `in`, `ref`, and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="d5c2d-112">Proto metody nemohou být přetíženy, pokud je jediným rozdílem je, že jedna metoda má `ref` nebo `in` argument a dalších trvá `out` argument.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-112">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="d5c2d-113">Například následující kód, nebude kompilace:</span><span class="sxs-lookup"><span data-stu-id="d5c2d-113">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="d5c2d-114">Přetížení podle přítomnosti `in` je povoleno:</span><span class="sxs-lookup"><span data-stu-id="d5c2d-114">Overloading based on the presence of `in` is allowed:</span></span>  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a><span data-ttu-id="d5c2d-115">Pravidel řešení přetížení</span><span class="sxs-lookup"><span data-stu-id="d5c2d-115">Overload resolution rules</span></span>

<span data-ttu-id="d5c2d-116">Rozumíte pravidla rozlišení přetížení pro metody s hodnotou oproti `in` argumenty prostřednictvím pochopení motivace pro `in` argumenty.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-116">You can understand the overload resolution rules for methods with by value vs. `in` arguments through understanding the motivation for `in` arguments.</span></span> <span data-ttu-id="d5c2d-117">Definování metod pomocí `in` parametrů je potenciální optimalizace výkonu.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-117">Defining methods using `in` parameters is a potential performance optimization.</span></span> <span data-ttu-id="d5c2d-118">Některé `struct` argumenty typu mohou být velká velikost, a pokud jsou volány metody v úzkou smyčky nebo kód kritický pro cesty, náklady na kopírování tyto struktury je důležité.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-118">Some `struct` type arguments may be large in size, and when methods are called in tight loops or critical code paths, the cost of copying those structures is critical.</span></span> <span data-ttu-id="d5c2d-119">Metody deklarovat `in` parametry k určení, že argumenty může být předána odkazem bezpečně protože zavolat metodu nedojde ke změně stavu tohoto argumentu.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-119">Methods declare `in` parameters to specify that arguments may be passed by reference safely because the called method does not modify the state of that argument.</span></span> <span data-ttu-id="d5c2d-120">Předání těchto argumentů odkazem zabraňuje (potenciálně) nákladné kopírování.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-120">Passing those arguments by reference avoids the (potentially) expensive copy.</span></span> 

<span data-ttu-id="d5c2d-121">Určení `in` argumenty při volání lokalita je obvykle volitelné.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-121">Specifying `in` on arguments at the call site is typically optional.</span></span> <span data-ttu-id="d5c2d-122">Není žádný sémantického rozdíl mezi předání argumentů hodnotou a jejich předávání pomocí odkazu `in` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-122">There is no semantic difference between passing arguments by value and passing them by reference using the `in` modifier.</span></span> <span data-ttu-id="d5c2d-123">`in` Modifikátor v lokalitě volání je volitelný, protože nemusíte znamenat, že hodnota argumentu může být změněn.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-123">The `in` modifier at the call site is optional because you don't need to indicate that the argument's value might be changed.</span></span> <span data-ttu-id="d5c2d-124">Explicitně přidat `in` modifikátor v lokalitě volání zajistit argument odkaz, je předaná není hodnotou.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-124">You explicitly add the `in` modifier at the call site to ensure the argument is passed by reference, not by value.</span></span> <span data-ttu-id="d5c2d-125">Explicitně pomocí `in` má dva důsledky:</span><span class="sxs-lookup"><span data-stu-id="d5c2d-125">Explicitly using `in` has two effects:</span></span>

<span data-ttu-id="d5c2d-126">Nejprve zadání `in` na volání lokality vynutí kompilátoru vybrat metodu definovaný s odpovídající `in` parametr.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-126">First, specifying `in` at the call site forces the compiler to select a method defined with a matching `in` parameter.</span></span> <span data-ttu-id="d5c2d-127">Jinak, když dvě metody se liší pouze v přítomnosti z `in`, podle hodnoty přetížení je lepší shodu.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-127">Otherwise, when two methods differ only in the presence of `in`, the by value overload is a better match.</span></span>

<span data-ttu-id="d5c2d-128">Druhý, zadání `in` deklaruje vašich představ předat argument odkazem.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-128">Second, specifying `in` declares your intent to pass an argument by reference.</span></span> <span data-ttu-id="d5c2d-129">Argument použít s `in` musí představovat umístění, které lze přímo odkazovat.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-129">The argument used with `in` must represent a location that can be directly referred to.</span></span> <span data-ttu-id="d5c2d-130">Stejné obecná pravidla pro `out` a `ref` platí argumenty: konstanty, běžné vlastnosti nebo jiné výrazy, které produkují hodnoty nelze použít.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-130">The same general rules for `out` and `ref` arguments apply: You cannot use constants, ordinary properties, or other expressions that produce values.</span></span> <span data-ttu-id="d5c2d-131">Jinak hodnota vynechání `in` na volání lokality informuje kompilátor, že vám umožní vytvořit dočasnou proměnnou k předání odkazem jen pro čtení do metody.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-131">Otherwise, omitting `in` at the call site informs the compiler that you will allow it to create a temporary variable to pass by read-only reference to the method.</span></span> <span data-ttu-id="d5c2d-132">Kompilátor vytvoří dočasný proměnnou překonat několik omezení s `in` argumenty:</span><span class="sxs-lookup"><span data-stu-id="d5c2d-132">The compiler creates a temporary variable to overcome several restrictions with `in` arguments:</span></span>

- <span data-ttu-id="d5c2d-133">Dočasné proměnné umožňuje kompilaci konstanty jako `in` parametry.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-133">A temporary variable allows compile-time constants as `in` parameters.</span></span>
- <span data-ttu-id="d5c2d-134">Dočasné proměnné umožňuje vlastnosti nebo jiné výrazy pro `in` parametry.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-134">A temporary variable allows properties, or other expressions for `in` parameters.</span></span>
- <span data-ttu-id="d5c2d-135">Dočasné proměnné umožňuje argumenty níž se nachází implicitní převod z typu argument na typ parametru.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-135">A temporary variable allows arguments where there is an implicit conversion from the argument type to the parameter type.</span></span>

<span data-ttu-id="d5c2d-136">Ve všech předchozích instancích kompilátor vytvoří dočasné proměnné, která ukládá hodnotu identifikátoru konstanta, vlastnost nebo jiných výraz.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-136">In all the preceding instances, the compiler creates a temporary variable that stores the value of the constant, property, or other expression.</span></span>

<span data-ttu-id="d5c2d-137">Následující kód ukazuje tato pravidla:</span><span class="sxs-lookup"><span data-stu-id="d5c2d-137">The following code illustrates these rules:</span></span>

```csharp
static void Method(in int argument)
{
    // implementation removed
}

Method(5); // OK, temporary variable created.
Method(5L); // CS1503: no implicit conversion from long to int
short s = 0;
Method(s); // OK, temporary int created with the value 0
Method(in s); // CS1503: cannot convert from in short to in int
int i = 42;
Method(i); // passed by readonly reference
Method(in i); // passed by readonly reference, explicitly using `in`
```

<span data-ttu-id="d5c2d-138">Nyní předpokládejme, že jinou metodu, pomocí hodnot argumentů byl k dispozici.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-138">Now, suppose another method using by value arguments was available.</span></span> <span data-ttu-id="d5c2d-139">Výsledky změnit, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="d5c2d-139">The results change as shown in the following code:</span></span>

```csharp
static void Method(int argument)
{
    // implementation removed
}

static void Method(in int argument)
{
    // implementation removed
}

Method(5); // Calls overload passed by value
Method(5L); // CS1503: no implicit conversion from long to int
short s = 0;
Method(s); // Calls overload passed by value.
Method(in s); // CS1503: cannot convert from in short to in int
int i = 42;
Method(i); // Calls overload passed by value
Method(in i); // passed by readonly reference, explicitly using `in`
```

<span data-ttu-id="d5c2d-140">Jenom volání metody, kde je argument předaná odkaz je tu poslední.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-140">The only method call where the argument is passed by reference is the final one.</span></span>

> [!NOTE]
> <span data-ttu-id="d5c2d-141">Předchozí kód používá `int` jako typ argumentu pro jednoduchost.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-141">The preceding code uses `int` as the argument type for simplicity.</span></span> <span data-ttu-id="d5c2d-142">Protože `int` není větší než odkaz v většina moderních počítače, není k předání jedné `int` jako odkaz jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-142">Because `int` is no larger than a reference in most modern machines, there is no benefit to passing a single `int` as a readonly reference.</span></span> 

## <a name="limitations-on-in-parameters"></a><span data-ttu-id="d5c2d-143">Omezení `in` parametry</span><span class="sxs-lookup"><span data-stu-id="d5c2d-143">Limitations on `in` parameters</span></span>

<span data-ttu-id="d5c2d-144">Nelze použít `in`, `ref`, a `out` klíčová slova pro následující typy metod:</span><span class="sxs-lookup"><span data-stu-id="d5c2d-144">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="d5c2d-145">Asynchronní metody, které definují pomocí [asynchronní](async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-145">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="d5c2d-146">Iterator metody, které zahrnují [yield vrátit](yield.md) nebo `yield break` příkaz.</span><span class="sxs-lookup"><span data-stu-id="d5c2d-146">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="d5c2d-147">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d5c2d-147">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d5c2d-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5c2d-148">See Also</span></span>  
 [<span data-ttu-id="d5c2d-149">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d5c2d-149">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="d5c2d-150">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d5c2d-150">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="d5c2d-151">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d5c2d-151">C# Keywords</span></span>](index.md)  
 <span data-ttu-id="d5c2d-152">[Parametry metody](method-parameters.md) [odkazovat sémantiku s typy hodnot](../../reference-semantics-with-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="d5c2d-152">[Method Parameters](method-parameters.md) [Reference Semantics with Value Types](../../reference-semantics-with-value-types.md)</span></span>
