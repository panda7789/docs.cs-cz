---
title: v modifikátoru parametrů - C# Reference
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: cbde7a571fb71ed7577077c77a5c61db553ec859
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173611"
---
# <a name="in-parameter-modifier-c-reference"></a><span data-ttu-id="15b00-102">v modifikátoru parametrů (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="15b00-102">in parameter modifier (C# Reference)</span></span>

<span data-ttu-id="15b00-103">Klíčové `in` slovo způsobí, že argumenty, které mají být předány odkazem.</span><span class="sxs-lookup"><span data-stu-id="15b00-103">The `in` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="15b00-104">Vytvoří formální parametr alias pro argument, který musí být proměnná.</span><span class="sxs-lookup"><span data-stu-id="15b00-104">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="15b00-105">Jinými slovy, každá operace na parametr je provedena na argument.</span><span class="sxs-lookup"><span data-stu-id="15b00-105">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="15b00-106">Je to jako [ref](ref.md) nebo [out](out-parameter-modifier.md) `in` klíčová slova, s tím rozdílem, že argumenty nelze změnit volanou metodou.</span><span class="sxs-lookup"><span data-stu-id="15b00-106">It is like the [ref](ref.md) or [out](out-parameter-modifier.md) keywords, except that `in` arguments cannot be modified by the called method.</span></span> <span data-ttu-id="15b00-107">Vzhledem `ref` k tomu, `out` argumenty mohou být změněny, argumenty musí být změněny volanou metodou a tyto změny jsou pozorovatelné v kontextu volání.</span><span class="sxs-lookup"><span data-stu-id="15b00-107">Whereas `ref` arguments may be modified, `out` arguments must be modified by the called method, and those modifications are observable in the calling context.</span></span>

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

<span data-ttu-id="15b00-108">Předchozí příklad ukazuje, že `in` modifikátor je obvykle zbytečné na webu volání.</span><span class="sxs-lookup"><span data-stu-id="15b00-108">The preceding example demonstrates that the `in` modifier is usually unnecessary at the call site.</span></span> <span data-ttu-id="15b00-109">Je vyžadována pouze v deklaraci metody.</span><span class="sxs-lookup"><span data-stu-id="15b00-109">It is only required in the method declaration.</span></span>

> [!NOTE]
> <span data-ttu-id="15b00-110">Klíčové `in` slovo lze také použít s parametrem obecného typu k určení, že `foreach` parametr typu je `join` kontravariantní, jako součást příkazu nebo jako součást klauzule v dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="15b00-110">The `in` keyword can also be used with a generic type parameter to specify that the type parameter is contravariant, as part of a `foreach` statement, or as part of a `join` clause in a LINQ query.</span></span> <span data-ttu-id="15b00-111">Další informace o použití `in` klíčového slova v těchto souvislostech naleznete v [části](in.md), která obsahuje odkazy na všechna tato použití.</span><span class="sxs-lookup"><span data-stu-id="15b00-111">For more information on the use of the `in` keyword in these contexts, see [in](in.md), which provides links to all those uses.</span></span>
  
<span data-ttu-id="15b00-112">Proměnné předané `in` jako argumenty musí být inicializovány před předáním ve volání metody.</span><span class="sxs-lookup"><span data-stu-id="15b00-112">Variables passed as `in` arguments must be initialized before being passed in a method call.</span></span> <span data-ttu-id="15b00-113">Volaná metoda však nesmí přiřadit hodnotu nebo upravit argument.</span><span class="sxs-lookup"><span data-stu-id="15b00-113">However, the called method may not assign a value or modify the argument.</span></span>  

<span data-ttu-id="15b00-114">Modifikátor `in` parametrů je k dispozici v c# 7.2 a novější.</span><span class="sxs-lookup"><span data-stu-id="15b00-114">The `in` parameter modifier is available in C# 7.2 and later.</span></span> <span data-ttu-id="15b00-115">Předchozí verze generovat chybu `CS8107` kompilátoru ("Funkce odkazy jen pro čtení' není k dispozici v C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="15b00-115">Previous versions generate compiler error `CS8107` ("Feature 'readonly references' is not available in C# 7.0.</span></span> <span data-ttu-id="15b00-116">Použijte prosím jazyk verze 7.2 nebo vyšší.") Informace o konfiguraci jazykové verze kompilátoru naleznete [v tématu Výběr jazykové verze jazyka C#](../configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="15b00-116">Please use language version 7.2 or greater.") To configure the compiler language version, see [Select the C# language version](../configure-language-version.md).</span></span>

<span data-ttu-id="15b00-117">`in`, `ref`a `out` klíčová slova nejsou považovány za součást podpisu metody pro účely řešení přetížení.</span><span class="sxs-lookup"><span data-stu-id="15b00-117">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="15b00-118">Proto metody nelze přetížit, pokud jediný rozdíl `ref` je, že jedna metoda trvá nebo `in` argument a druhý trvá `out` argument.</span><span class="sxs-lookup"><span data-stu-id="15b00-118">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="15b00-119">Následující kód, například, nebude kompilovat:</span><span class="sxs-lookup"><span data-stu-id="15b00-119">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="15b00-120">Přetížení na základě přítomnosti `in` je povoleno:</span><span class="sxs-lookup"><span data-stu-id="15b00-120">Overloading based on the presence of `in` is allowed:</span></span>  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a><span data-ttu-id="15b00-121">Pravidla řešení přetížení</span><span class="sxs-lookup"><span data-stu-id="15b00-121">Overload resolution rules</span></span>

<span data-ttu-id="15b00-122">Můžete pochopit pravidla řešení přetížení pro metody s `in` hodnotou vs `in` argumenty pochopením motivace pro argumenty.</span><span class="sxs-lookup"><span data-stu-id="15b00-122">You can understand the overload resolution rules for methods with by value vs. `in` arguments by understanding the motivation for `in` arguments.</span></span> <span data-ttu-id="15b00-123">Definování metod `in` pomocí parametrů je potenciální optimalizace výkonu.</span><span class="sxs-lookup"><span data-stu-id="15b00-123">Defining methods using `in` parameters is a potential performance optimization.</span></span> <span data-ttu-id="15b00-124">Některé `struct` argumenty typu mohou mít velké velikosti a při volání metod v těsných cyklických cynicích nebo kritických cestách kódu jsou náklady na kopírování těchto struktur kritické.</span><span class="sxs-lookup"><span data-stu-id="15b00-124">Some `struct` type arguments may be large in size, and when methods are called in tight loops or critical code paths, the cost of copying those structures is critical.</span></span> <span data-ttu-id="15b00-125">Metody `in` deklarují parametry, které určují, že argumenty mohou být bezpečně předány odkazem, protože volaná metoda nemění stav tohoto argumentu.</span><span class="sxs-lookup"><span data-stu-id="15b00-125">Methods declare `in` parameters to specify that arguments may be passed by reference safely because the called method does not modify the state of that argument.</span></span> <span data-ttu-id="15b00-126">Předáním těchto argumentů odkazem se vyhnete (potenciálně) nákladné kopii.</span><span class="sxs-lookup"><span data-stu-id="15b00-126">Passing those arguments by reference avoids the (potentially) expensive copy.</span></span>

<span data-ttu-id="15b00-127">Zadání `in` argumentů na webu volání je obvykle volitelné.</span><span class="sxs-lookup"><span data-stu-id="15b00-127">Specifying `in` for arguments at the call site is typically optional.</span></span> <span data-ttu-id="15b00-128">Neexistuje žádný sémantický rozdíl mezi předávání argumentů hodnotou `in` a jejich předávání odkazem pomocí modifikátoru.</span><span class="sxs-lookup"><span data-stu-id="15b00-128">There is no semantic difference between passing arguments by value and passing them by reference using the `in` modifier.</span></span> <span data-ttu-id="15b00-129">Modifikátor `in` na webu volání je volitelný, protože není nutné označit, že hodnota argumentu může být změněna.</span><span class="sxs-lookup"><span data-stu-id="15b00-129">The `in` modifier at the call site is optional because you don't need to indicate that the argument's value might be changed.</span></span> <span data-ttu-id="15b00-130">Explicitně přidáte `in` modifikátor na webu volání, abyste zajistili, že argument je předán odkazem, nikoli hodnotou.</span><span class="sxs-lookup"><span data-stu-id="15b00-130">You explicitly add the `in` modifier at the call site to ensure the argument is passed by reference, not by value.</span></span> <span data-ttu-id="15b00-131">Explicitně `in` using má následující dva efekty:</span><span class="sxs-lookup"><span data-stu-id="15b00-131">Explicitly using `in` has the following two effects:</span></span>

<span data-ttu-id="15b00-132">Nejprve zadání `in` na pracovišti volání vynutí kompilátoru `in` vybrat metodu definovanou s odpovídající parametr.</span><span class="sxs-lookup"><span data-stu-id="15b00-132">First, specifying `in` at the call site forces the compiler to select a method defined with a matching `in` parameter.</span></span> <span data-ttu-id="15b00-133">V opačném případě, pokud dvě `in`metody se liší pouze v přítomnosti , přetížení podle hodnoty je lepší shoda.</span><span class="sxs-lookup"><span data-stu-id="15b00-133">Otherwise, when two methods differ only in the presence of `in`, the by value overload is a better match.</span></span>

<span data-ttu-id="15b00-134">Za druhé, `in` zadání deklaruje váš záměr předat argument odkazem.</span><span class="sxs-lookup"><span data-stu-id="15b00-134">Second, specifying `in` declares your intent to pass an argument by reference.</span></span> <span data-ttu-id="15b00-135">Argument použitý `in` s musí představovat umístění, které lze přímo odkazovat.</span><span class="sxs-lookup"><span data-stu-id="15b00-135">The argument used with `in` must represent a location that can be directly referred to.</span></span> <span data-ttu-id="15b00-136">Stejná obecná `out` pravidla `ref` pro a argumenty platí: Nelze použít konstanty, běžné vlastnosti nebo jiné výrazy, které vytvářejí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="15b00-136">The same general rules for `out` and `ref` arguments apply: You cannot use constants, ordinary properties, or other expressions that produce values.</span></span> <span data-ttu-id="15b00-137">V opačném případě `in` vynechání na webu volání informuje kompilátor, který mu umožní vytvořit dočasnou proměnnou předat jen pro čtení odkaz na metodu.</span><span class="sxs-lookup"><span data-stu-id="15b00-137">Otherwise, omitting `in` at the call site informs the compiler that you will allow it to create a temporary variable to pass by read-only reference to the method.</span></span> <span data-ttu-id="15b00-138">Kompilátor vytvoří dočasnou proměnnou `in` k překonání několika omezení s argumenty:</span><span class="sxs-lookup"><span data-stu-id="15b00-138">The compiler creates a temporary variable to overcome several restrictions with `in` arguments:</span></span>

- <span data-ttu-id="15b00-139">Dočasná proměnná umožňuje konstanty `in` v době kompilace jako parametry.</span><span class="sxs-lookup"><span data-stu-id="15b00-139">A temporary variable allows compile-time constants as `in` parameters.</span></span>
- <span data-ttu-id="15b00-140">Dočasná proměnná umožňuje vlastnosti `in` nebo jiné výrazy pro parametry.</span><span class="sxs-lookup"><span data-stu-id="15b00-140">A temporary variable allows properties, or other expressions for `in` parameters.</span></span>
- <span data-ttu-id="15b00-141">Dočasná proměnná umožňuje argumenty, kde je implicitní převod z typu argumentu na typ parametru.</span><span class="sxs-lookup"><span data-stu-id="15b00-141">A temporary variable allows arguments where there is an implicit conversion from the argument type to the parameter type.</span></span>

<span data-ttu-id="15b00-142">Ve všech předchozích instancích kompilátor vytvoří dočasnou proměnnou, která ukládá hodnotu konstanty, vlastnosti nebo jiného výrazu.</span><span class="sxs-lookup"><span data-stu-id="15b00-142">In all the preceding instances, the compiler creates a temporary variable that stores the value of the constant, property, or other expression.</span></span>

<span data-ttu-id="15b00-143">Následující kód ilustruje tato pravidla:</span><span class="sxs-lookup"><span data-stu-id="15b00-143">The following code illustrates these rules:</span></span>

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

<span data-ttu-id="15b00-144">Nyní předpokládejme, že byla k dispozici jiná metoda používající argumenty hodnoty.</span><span class="sxs-lookup"><span data-stu-id="15b00-144">Now, suppose another method using by value arguments was available.</span></span> <span data-ttu-id="15b00-145">Výsledky se mění tak, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="15b00-145">The results change as shown in the following code:</span></span>

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

<span data-ttu-id="15b00-146">Jediná metoda volání, kde je argument předán odkazem je poslední.</span><span class="sxs-lookup"><span data-stu-id="15b00-146">The only method call where the argument is passed by reference is the final one.</span></span>

> [!NOTE]
> <span data-ttu-id="15b00-147">Předchozí kód používá `int` jako typ argumentu pro jednoduchost.</span><span class="sxs-lookup"><span data-stu-id="15b00-147">The preceding code uses `int` as the argument type for simplicity.</span></span> <span data-ttu-id="15b00-148">Protože `int` není větší než odkaz ve většině moderních počítačů, není `int` žádný přínos pro předání jeden jako odkaz jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="15b00-148">Because `int` is no larger than a reference in most modern machines, there is no benefit to passing a single `int` as a readonly reference.</span></span>

## <a name="limitations-on-in-parameters"></a><span data-ttu-id="15b00-149">Omezení `in` parametrů</span><span class="sxs-lookup"><span data-stu-id="15b00-149">Limitations on `in` parameters</span></span>

<span data-ttu-id="15b00-150">Klíčová `out` slova a `in`klíčová `ref`slova nelze použít pro následující typy metod:</span><span class="sxs-lookup"><span data-stu-id="15b00-150">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="15b00-151">Asynchronní metody, které definujete pomocí [asynchronního](async.md) modifikátoru.</span><span class="sxs-lookup"><span data-stu-id="15b00-151">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="15b00-152">Iterátor metody, které zahrnují výnos `yield break` výnos [return](yield.md) nebo příkaz.</span><span class="sxs-lookup"><span data-stu-id="15b00-152">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="15b00-153">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="15b00-153">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="15b00-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="15b00-154">See also</span></span>

- [<span data-ttu-id="15b00-155">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="15b00-155">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="15b00-156">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="15b00-156">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="15b00-157">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="15b00-157">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="15b00-158">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="15b00-158">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="15b00-159">Zapisujte bezpečný efektivní kód</span><span class="sxs-lookup"><span data-stu-id="15b00-159">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
