---
title: v modifikátor parametru - C# odkaz
ms.custom: seodec18
ms.date: 02/12/2019
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: 5a765a330e4d9efe22943538503c0822e1c9dfdb
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219552"
---
# <a name="in-parameter-modifier-c-reference"></a><span data-ttu-id="e0692-102">v parametru modifikátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e0692-102">in parameter modifier (C# Reference)</span></span>

<span data-ttu-id="e0692-103">`in` – Klíčové slovo způsobí, že argumenty, které mají být předány podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="e0692-103">The `in` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="e0692-104">Je třeba [ref](ref.md) nebo [si](out-parameter-modifier.md) klíčová slova, kromě toho, že `in` nemůže upravit argumentů volané metody.</span><span class="sxs-lookup"><span data-stu-id="e0692-104">It is like the [ref](ref.md) or [out](out-parameter-modifier.md) keywords, except that `in` arguments cannot be modified by the called method.</span></span> <span data-ttu-id="e0692-105">Vzhledem k tomu `ref` argumenty se dají měnit, `out` argumenty musí být upravena klíčovým volané metody a jsou tyto změny pozorovat ve volání kontextu.</span><span class="sxs-lookup"><span data-stu-id="e0692-105">Whereas `ref` arguments may be modified,  `out` arguments must be modified by the called method, and those modifications are observable in the calling context.</span></span>

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

<span data-ttu-id="e0692-106">Předchozí příklad ukazuje, že `in` Modifikátor je obvykle zbytečné na lokalitu volání.</span><span class="sxs-lookup"><span data-stu-id="e0692-106">The preceding example demonstrates that the `in` modifier is usually unnecessary at the call site.</span></span> <span data-ttu-id="e0692-107">Je potřeba jenom v deklaraci metody.</span><span class="sxs-lookup"><span data-stu-id="e0692-107">It is only required in the method declaration.</span></span>


> [!NOTE] 
> <span data-ttu-id="e0692-108">`in` – Klíčové slovo je také možné pomocí parametru obecného typu k určení, že parametr typu je kontravariant, jako součást `foreach` příkazu, nebo jako součást `join` klauzule v dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="e0692-108">The `in` keyword can also be used with a generic type parameter to specify that the type parameter is contravariant, as part of a `foreach` statement, or as part of a `join` clause in a LINQ query.</span></span> <span data-ttu-id="e0692-109">Další informace týkající se použití `in` – klíčové slovo v těchto kontextech najdete v článku [v](in.md), který obsahuje odkazy na tato použití.</span><span class="sxs-lookup"><span data-stu-id="e0692-109">For more information on the use of the `in` keyword in these contexts, see [in](in.md), which provides links to all those uses.</span></span>
  
 <span data-ttu-id="e0692-110">Proměnné se předaly jako `in` argumenty musí být inicializován před předáním ve volání metody.</span><span class="sxs-lookup"><span data-stu-id="e0692-110">Variables passed as `in` arguments must be initialized before being passed in a method call.</span></span> <span data-ttu-id="e0692-111">Volané metody však nelze přiřadit hodnotu nebo upravujete argument.</span><span class="sxs-lookup"><span data-stu-id="e0692-111">However, the called method may not assign a value or modify the argument.</span></span>  

<span data-ttu-id="e0692-112">`in` Modifikátor parametru je k dispozici v C# 7.2 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="e0692-112">The `in` parameter modifier is available in C# 7.2 and later.</span></span> <span data-ttu-id="e0692-113">Chyba kompilátoru generovat předchozí verze `CS8107` ("funkce"odkazů jen pro čtení"není k dispozici v C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="e0692-113">Previous versions generate compiler error `CS8107` ("Feature 'readonly references' is not available in C# 7.0.</span></span> <span data-ttu-id="e0692-114">Použijte prosím jazyk verze 7.2 nebo novější.") Verze jazyka kompilátoru nakonfigurovat, najdete v části [vyberte C# jazykovou verzi](../configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="e0692-114">Please use language version 7.2 or greater.") To configure the compiler language version, see [Select the C# language version](../configure-language-version.md).</span></span>

 <span data-ttu-id="e0692-115">I když `in`, `ref`, a `out` klíčová slova způsobit různé chování za běhu, nejsou považovány za součást podpisu metody v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="e0692-115">Although the `in`, `ref`, and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="e0692-116">Proto metody nemohou být přetíženy, pokud je jediným rozdílem je, že jedna metoda má `ref` nebo `in` argument a druhý bere `out` argument.</span><span class="sxs-lookup"><span data-stu-id="e0692-116">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="e0692-117">Například následující kód, nebude kompilovat:</span><span class="sxs-lookup"><span data-stu-id="e0692-117">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="e0692-118">Přetížení založené na přítomnost `in` může:</span><span class="sxs-lookup"><span data-stu-id="e0692-118">Overloading based on the presence of `in` is allowed:</span></span>  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a><span data-ttu-id="e0692-119">Pravidla pro řešení přetížení</span><span class="sxs-lookup"><span data-stu-id="e0692-119">Overload resolution rules</span></span>

<span data-ttu-id="e0692-120">Rozumíte pravidla rozlišení přetížení pro metody s hodnotou versus `in` argumenty Pochopením motivace pro `in` argumenty.</span><span class="sxs-lookup"><span data-stu-id="e0692-120">You can understand the overload resolution rules for methods with by value vs. `in` arguments by understanding the motivation for `in` arguments.</span></span> <span data-ttu-id="e0692-121">Definování metody pomocí `in` parametrů je potenciální optimalizaci výkonu.</span><span class="sxs-lookup"><span data-stu-id="e0692-121">Defining methods using `in` parameters is a potential performance optimization.</span></span> <span data-ttu-id="e0692-122">Některé `struct` argumenty typu mohou být velké a při volání metody v těsné smyčky nebo cesty kritického kódu, náklady na kopírování těchto struktur je velmi důležité.</span><span class="sxs-lookup"><span data-stu-id="e0692-122">Some `struct` type arguments may be large in size, and when methods are called in tight loops or critical code paths, the cost of copying those structures is critical.</span></span> <span data-ttu-id="e0692-123">Metody deklarovat `in` parametry k určení, že argumenty mohou být předány podle odkazu bezpečně protože volané metody neprovede žádné změny stavu tento argument.</span><span class="sxs-lookup"><span data-stu-id="e0692-123">Methods declare `in` parameters to specify that arguments may be passed by reference safely because the called method does not modify the state of that argument.</span></span> <span data-ttu-id="e0692-124">Předání těchto argumentů odkazem se vyhnete (potenciálně) nákladné kopírování.</span><span class="sxs-lookup"><span data-stu-id="e0692-124">Passing those arguments by reference avoids the (potentially) expensive copy.</span></span> 

<span data-ttu-id="e0692-125">Určení `in` pro argumenty při volání lokalita je obvykle volitelné.</span><span class="sxs-lookup"><span data-stu-id="e0692-125">Specifying `in` for arguments at the call site is typically optional.</span></span> <span data-ttu-id="e0692-126">Neexistuje žádné sémantické rozdíly mezi předávání argumentů podle hodnoty a jejich předání pomocí odkazu `in` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="e0692-126">There is no semantic difference between passing arguments by value and passing them by reference using the `in` modifier.</span></span> <span data-ttu-id="e0692-127">`in` Modifikátor na lokalitu volání je volitelný, protože není nutné k označení, že hodnota argumentu může být změněn.</span><span class="sxs-lookup"><span data-stu-id="e0692-127">The `in` modifier at the call site is optional because you don't need to indicate that the argument's value might be changed.</span></span> <span data-ttu-id="e0692-128">Explicitně přidat `in` modifikátor lokality volání k zajištění argument se předá odkazem, ne podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e0692-128">You explicitly add the `in` modifier at the call site to ensure the argument is passed by reference, not by value.</span></span> <span data-ttu-id="e0692-129">Explicitně pomocí `in` má následující dva důsledky:</span><span class="sxs-lookup"><span data-stu-id="e0692-129">Explicitly using `in` has the following two effects:</span></span>

<span data-ttu-id="e0692-130">Nejprve zadání `in` při volání webu vynutí, aby kompilátor výběr metody definované k odpovídajícímu `in` parametru.</span><span class="sxs-lookup"><span data-stu-id="e0692-130">First, specifying `in` at the call site forces the compiler to select a method defined with a matching `in` parameter.</span></span> <span data-ttu-id="e0692-131">Jinak, pokud dvě metody se liší pouze v nichž se nachází z `in`, podle hodnoty přetížení představuje lepší shodu.</span><span class="sxs-lookup"><span data-stu-id="e0692-131">Otherwise, when two methods differ only in the presence of `in`, the by value overload is a better match.</span></span>

<span data-ttu-id="e0692-132">Za druhé, určení `in` deklaruje vaším záměrem pro předání argumentu podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="e0692-132">Second, specifying `in` declares your intent to pass an argument by reference.</span></span> <span data-ttu-id="e0692-133">Argument použitý s `in` musí představovat umístění, které lze přímo odkazovat.</span><span class="sxs-lookup"><span data-stu-id="e0692-133">The argument used with `in` must represent a location that can be directly referred to.</span></span> <span data-ttu-id="e0692-134">Stejné obecná pravidla pro `out` a `ref` použít argumenty: Nelze použít konstanty, běžné vlastnosti nebo dalších výrazů, které vracet hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e0692-134">The same general rules for `out` and `ref` arguments apply: You cannot use constants, ordinary properties, or other expressions that produce values.</span></span> <span data-ttu-id="e0692-135">V opačném případě vynechání `in` při volání webu informuje kompilátor, že vám umožní vytvořit dočasnou proměnnou předávání pomocí odkazu pouze pro čtení k metodě.</span><span class="sxs-lookup"><span data-stu-id="e0692-135">Otherwise, omitting `in` at the call site informs the compiler that you will allow it to create a temporary variable to pass by read-only reference to the method.</span></span> <span data-ttu-id="e0692-136">Kompilátor vytvoří dočasnou proměnnou několik omezení s `in` argumenty:</span><span class="sxs-lookup"><span data-stu-id="e0692-136">The compiler creates a temporary variable to overcome several restrictions with `in` arguments:</span></span>

- <span data-ttu-id="e0692-137">Dočasná proměnná umožňuje konstanty z doby kompilace jako `in` parametry.</span><span class="sxs-lookup"><span data-stu-id="e0692-137">A temporary variable allows compile-time constants as `in` parameters.</span></span>
- <span data-ttu-id="e0692-138">Dočasná proměnná umožňuje vlastnosti nebo dalších výrazů pro `in` parametry.</span><span class="sxs-lookup"><span data-stu-id="e0692-138">A temporary variable allows properties, or other expressions for `in` parameters.</span></span>
- <span data-ttu-id="e0692-139">Dočasná proměnná umožňuje argumenty tam, kde je implicitní převod z typu argumentu na typ parametru.</span><span class="sxs-lookup"><span data-stu-id="e0692-139">A temporary variable allows arguments where there is an implicit conversion from the argument type to the parameter type.</span></span>

<span data-ttu-id="e0692-140">Ve všech předchozích instancích kompilátor vytvoří dočasnou proměnnou, která ukládá hodnotu konstanty, vlastnosti nebo jiný výraz.</span><span class="sxs-lookup"><span data-stu-id="e0692-140">In all the preceding instances, the compiler creates a temporary variable that stores the value of the constant, property, or other expression.</span></span>

<span data-ttu-id="e0692-141">Následující kód znázorňuje tato pravidla:</span><span class="sxs-lookup"><span data-stu-id="e0692-141">The following code illustrates these rules:</span></span>

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

<span data-ttu-id="e0692-142">Předpokládejme, že byla k dispozici jinou metodu pomocí hodnot argumentů.</span><span class="sxs-lookup"><span data-stu-id="e0692-142">Now, suppose another method using by value arguments was available.</span></span> <span data-ttu-id="e0692-143">Výsledky změnit, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="e0692-143">The results change as shown in the following code:</span></span>

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

<span data-ttu-id="e0692-144">Pouze volání metody, kde se argument předaný odkazem je finální.</span><span class="sxs-lookup"><span data-stu-id="e0692-144">The only method call where the argument is passed by reference is the final one.</span></span>

> [!NOTE]
> <span data-ttu-id="e0692-145">Předchozí kód používá `int` jako typ argumentu pro zjednodušení.</span><span class="sxs-lookup"><span data-stu-id="e0692-145">The preceding code uses `int` as the argument type for simplicity.</span></span> <span data-ttu-id="e0692-146">Protože `int` není větší než odkaz na většině moderních počítačů není žádná výhoda pro předání jednoho `int` jako jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="e0692-146">Because `int` is no larger than a reference in most modern machines, there is no benefit to passing a single `int` as a readonly reference.</span></span> 

## <a name="limitations-on-in-parameters"></a><span data-ttu-id="e0692-147">Omezení `in` parametry</span><span class="sxs-lookup"><span data-stu-id="e0692-147">Limitations on `in` parameters</span></span>

<span data-ttu-id="e0692-148">Nelze použít `in`, `ref`, a `out` klíčová slova pro následující druhy metod:</span><span class="sxs-lookup"><span data-stu-id="e0692-148">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="e0692-149">Asynchronní metody, které definujete pomocí [asynchronní](async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="e0692-149">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="e0692-150">Metody iterátorů, mezi které patří [yield return](yield.md) nebo `yield break` příkazu.</span><span class="sxs-lookup"><span data-stu-id="e0692-150">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="e0692-151">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e0692-151">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e0692-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0692-152">See also</span></span>

- [<span data-ttu-id="e0692-153">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e0692-153">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e0692-154">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e0692-154">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e0692-155">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e0692-155">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e0692-156">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="e0692-156">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="e0692-157">Psát bezpečný kód efektivní</span><span class="sxs-lookup"><span data-stu-id="e0692-157">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
