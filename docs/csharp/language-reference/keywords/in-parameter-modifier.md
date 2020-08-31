---
description: v modifikátoru parametru – reference jazyka C#
title: v modifikátoru parametru – reference jazyka C#
ms.date: 03/19/2020
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: 613be9248e6ce9b974bcab1b59abd30469e9e180
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118401"
---
# <a name="in-parameter-modifier-c-reference"></a><span data-ttu-id="72602-103">in – modifikátor parametru (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="72602-103">in parameter modifier (C# Reference)</span></span>

<span data-ttu-id="72602-104">`in`Klíčové slovo způsobuje argumenty předávané odkazem.</span><span class="sxs-lookup"><span data-stu-id="72602-104">The `in` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="72602-105">Nastaví formální parametr jako alias pro argument, který musí být proměnná.</span><span class="sxs-lookup"><span data-stu-id="72602-105">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="72602-106">Jinými slovy, každá operace s parametrem je provedena na argumentu.</span><span class="sxs-lookup"><span data-stu-id="72602-106">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="72602-107">Je podobný klíčovým slovem [ref](ref.md) nebo [out](out-parameter-modifier.md) s tím rozdílem, že `in` argumenty nemohou být upraveny metodou volané.</span><span class="sxs-lookup"><span data-stu-id="72602-107">It is like the [ref](ref.md) or [out](out-parameter-modifier.md) keywords, except that `in` arguments cannot be modified by the called method.</span></span> <span data-ttu-id="72602-108">Vzhledem k tomu, že je `ref` možné upravit argumenty, `out` musí být argumenty upraveny metodou volané a tyto úpravy lze v kontextu volání pozorovatelit.</span><span class="sxs-lookup"><span data-stu-id="72602-108">Whereas `ref` arguments may be modified, `out` arguments must be modified by the called method, and those modifications are observable in the calling context.</span></span>

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

<span data-ttu-id="72602-109">Předchozí příklad ukazuje, že `in` Modifikátor je obvykle zbytečný na webu volání.</span><span class="sxs-lookup"><span data-stu-id="72602-109">The preceding example demonstrates that the `in` modifier is usually unnecessary at the call site.</span></span> <span data-ttu-id="72602-110">Vyžaduje se pouze v deklaraci metody.</span><span class="sxs-lookup"><span data-stu-id="72602-110">It is only required in the method declaration.</span></span>

> [!NOTE]
> <span data-ttu-id="72602-111">`in`Klíčové slovo lze také použít s parametrem obecného typu k určení toho, že parametr typu je kontravariantní, jako součást `foreach` příkazu nebo jako součást `join` klauzule v dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="72602-111">The `in` keyword can also be used with a generic type parameter to specify that the type parameter is contravariant, as part of a `foreach` statement, or as part of a `join` clause in a LINQ query.</span></span> <span data-ttu-id="72602-112">Další informace o použití `in` klíčového slova v těchto kontextech naleznete [v části v](in.md)tématu, který poskytuje odkazy na všechna tato použití.</span><span class="sxs-lookup"><span data-stu-id="72602-112">For more information on the use of the `in` keyword in these contexts, see [in](in.md), which provides links to all those uses.</span></span>
  
<span data-ttu-id="72602-113">Proměnné předané jako `in` argumenty musí být před předáním do volání metody inicializovány.</span><span class="sxs-lookup"><span data-stu-id="72602-113">Variables passed as `in` arguments must be initialized before being passed in a method call.</span></span> <span data-ttu-id="72602-114">Volaná metoda ale nemůže přiřadit hodnotu ani upravovat argument.</span><span class="sxs-lookup"><span data-stu-id="72602-114">However, the called method may not assign a value or modify the argument.</span></span>  

<span data-ttu-id="72602-115">`in`Modifikátor parametru je k dispozici v C# 7,2 a novějším.</span><span class="sxs-lookup"><span data-stu-id="72602-115">The `in` parameter modifier is available in C# 7.2 and later.</span></span> <span data-ttu-id="72602-116">Předchozí verze generují chybu kompilátoru `CS8107` ("funkce" odkazy jen pro čtení "není v jazyce C# 7,0 k dispozici.</span><span class="sxs-lookup"><span data-stu-id="72602-116">Previous versions generate compiler error `CS8107` ("Feature 'readonly references' is not available in C# 7.0.</span></span> <span data-ttu-id="72602-117">Použijte prosím jazyk verze 7,2 nebo vyšší. ") Chcete-li nakonfigurovat verzi jazyka kompilátoru, přečtěte si téma [Výběr verze jazyka C#](../configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="72602-117">Please use language version 7.2 or greater.") To configure the compiler language version, see [Select the C# language version](../configure-language-version.md).</span></span>

<span data-ttu-id="72602-118">`in` `ref` `out` Klíčová slova, a nejsou považována za součást signatury metody pro účely řešení přetížení.</span><span class="sxs-lookup"><span data-stu-id="72602-118">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="72602-119">Proto metody nemohou být přetíženy, pokud jediným rozdílem je, že jedna metoda přebírá `ref` `in` argument or a druhý přebírá `out` argument.</span><span class="sxs-lookup"><span data-stu-id="72602-119">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="72602-120">Následující kód například nebude zkompilován:</span><span class="sxs-lookup"><span data-stu-id="72602-120">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="72602-121">Přetížení na základě přítomnosti `in` je povolené:</span><span class="sxs-lookup"><span data-stu-id="72602-121">Overloading based on the presence of `in` is allowed:</span></span>  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a><span data-ttu-id="72602-122">Pravidla řešení přetížení</span><span class="sxs-lookup"><span data-stu-id="72602-122">Overload resolution rules</span></span>

<span data-ttu-id="72602-123">Můžete pochopit pravidla rozlišení přetížení pro metody s hodnotou a `in` argumenty pomocí pochopení motivace pro `in` argumenty.</span><span class="sxs-lookup"><span data-stu-id="72602-123">You can understand the overload resolution rules for methods with by value vs. `in` arguments by understanding the motivation for `in` arguments.</span></span> <span data-ttu-id="72602-124">Definování metod pomocí `in` parametrů je potenciální optimalizace výkonu.</span><span class="sxs-lookup"><span data-stu-id="72602-124">Defining methods using `in` parameters is a potential performance optimization.</span></span> <span data-ttu-id="72602-125">Některé `struct` argumenty typu můžou být velké a při volání metod v těsných smyčkách nebo kritických cestách kódu jsou náklady na kopírování těchto struktur kritické.</span><span class="sxs-lookup"><span data-stu-id="72602-125">Some `struct` type arguments may be large in size, and when methods are called in tight loops or critical code paths, the cost of copying those structures is critical.</span></span> <span data-ttu-id="72602-126">Metody deklaruje `in` parametry pro určení, že argumenty mohou být předány odkazem bezpečně, protože volaná metoda neupravuje stav tohoto argumentu.</span><span class="sxs-lookup"><span data-stu-id="72602-126">Methods declare `in` parameters to specify that arguments may be passed by reference safely because the called method does not modify the state of that argument.</span></span> <span data-ttu-id="72602-127">Předání těchto argumentů odkazem se vyhne (potenciálně) nákladné kopii.</span><span class="sxs-lookup"><span data-stu-id="72602-127">Passing those arguments by reference avoids the (potentially) expensive copy.</span></span>

<span data-ttu-id="72602-128">Zadání `in` argumentů na webu volání je obvykle volitelné.</span><span class="sxs-lookup"><span data-stu-id="72602-128">Specifying `in` for arguments at the call site is typically optional.</span></span> <span data-ttu-id="72602-129">Neexistuje žádný sémantický rozdíl mezi předáním argumentů podle hodnoty a jejich předáním odkazem pomocí `in` modifikátoru.</span><span class="sxs-lookup"><span data-stu-id="72602-129">There is no semantic difference between passing arguments by value and passing them by reference using the `in` modifier.</span></span> <span data-ttu-id="72602-130">`in`Modifikátor na webu volání je nepovinný, protože nemusíte označovat, že hodnota argumentu může být změněna.</span><span class="sxs-lookup"><span data-stu-id="72602-130">The `in` modifier at the call site is optional because you don't need to indicate that the argument's value might be changed.</span></span> <span data-ttu-id="72602-131">Explicitně přidáte `in` Modifikátor na webu volání, aby se zajistilo, že argument je předán odkazem, nikoli hodnotou.</span><span class="sxs-lookup"><span data-stu-id="72602-131">You explicitly add the `in` modifier at the call site to ensure the argument is passed by reference, not by value.</span></span> <span data-ttu-id="72602-132">Explicitní použití `in` má následující dva účinky:</span><span class="sxs-lookup"><span data-stu-id="72602-132">Explicitly using `in` has the following two effects:</span></span>

<span data-ttu-id="72602-133">Nejprve zadáním `in` na webu volání vynutí kompilátor vybrat metodu definovanou s parametrem, který je s ním shodný `in` .</span><span class="sxs-lookup"><span data-stu-id="72602-133">First, specifying `in` at the call site forces the compiler to select a method defined with a matching `in` parameter.</span></span> <span data-ttu-id="72602-134">V opačném případě, pokud se dvě metody liší pouze v přítomnosti `in` , je přetížení podle hodnot lepší shodu.</span><span class="sxs-lookup"><span data-stu-id="72602-134">Otherwise, when two methods differ only in the presence of `in`, the by value overload is a better match.</span></span>

<span data-ttu-id="72602-135">Za druhé, zadáním `in` deklarujete záměr k předání argumentu odkazem.</span><span class="sxs-lookup"><span data-stu-id="72602-135">Second, specifying `in` declares your intent to pass an argument by reference.</span></span> <span data-ttu-id="72602-136">Argument použitý spolu `in` musí představovat umístění, na které lze přímo odkazovat.</span><span class="sxs-lookup"><span data-stu-id="72602-136">The argument used with `in` must represent a location that can be directly referred to.</span></span> <span data-ttu-id="72602-137">Platí stejná obecná pravidla pro `out` `ref` argumenty a. nemůžete použít konstanty, běžné vlastnosti nebo jiné výrazy, které vytváří hodnoty.</span><span class="sxs-lookup"><span data-stu-id="72602-137">The same general rules for `out` and `ref` arguments apply: You cannot use constants, ordinary properties, or other expressions that produce values.</span></span> <span data-ttu-id="72602-138">V opačném případě vynechání `in` na webu volání informuje kompilátor, že umožňuje vytvořit dočasnou proměnnou, která bude předána odkazem jen pro čtení k metodě.</span><span class="sxs-lookup"><span data-stu-id="72602-138">Otherwise, omitting `in` at the call site informs the compiler that you will allow it to create a temporary variable to pass by read-only reference to the method.</span></span> <span data-ttu-id="72602-139">Kompilátor vytvoří dočasnou proměnnou k překonání několika omezení s `in` argumenty:</span><span class="sxs-lookup"><span data-stu-id="72602-139">The compiler creates a temporary variable to overcome several restrictions with `in` arguments:</span></span>

- <span data-ttu-id="72602-140">Dočasná proměnná umožňuje jako parametry konstanty v čase kompilace `in` .</span><span class="sxs-lookup"><span data-stu-id="72602-140">A temporary variable allows compile-time constants as `in` parameters.</span></span>
- <span data-ttu-id="72602-141">Dočasná proměnná povoluje vlastnosti nebo jiné výrazy pro `in` parametry.</span><span class="sxs-lookup"><span data-stu-id="72602-141">A temporary variable allows properties, or other expressions for `in` parameters.</span></span>
- <span data-ttu-id="72602-142">Dočasná proměnná umožňuje argumenty, kde existuje implicitní převod typu argumentu na typ parametru.</span><span class="sxs-lookup"><span data-stu-id="72602-142">A temporary variable allows arguments where there is an implicit conversion from the argument type to the parameter type.</span></span>

<span data-ttu-id="72602-143">Ve všech předchozích instancích vytvoří kompilátor dočasnou proměnnou, která ukládá hodnotu konstanty, vlastnosti nebo jiného výrazu.</span><span class="sxs-lookup"><span data-stu-id="72602-143">In all the preceding instances, the compiler creates a temporary variable that stores the value of the constant, property, or other expression.</span></span>

<span data-ttu-id="72602-144">Následující kód ilustruje tato pravidla:</span><span class="sxs-lookup"><span data-stu-id="72602-144">The following code illustrates these rules:</span></span>

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

<span data-ttu-id="72602-145">Nyní předpokládejme, že je k dispozici jiná metoda používající argumenty hodnoty.</span><span class="sxs-lookup"><span data-stu-id="72602-145">Now, suppose another method using by value arguments was available.</span></span> <span data-ttu-id="72602-146">Změny výsledků, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="72602-146">The results change as shown in the following code:</span></span>

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

<span data-ttu-id="72602-147">Jediným voláním metody, kde je argument předána odkazem, je ten poslední.</span><span class="sxs-lookup"><span data-stu-id="72602-147">The only method call where the argument is passed by reference is the final one.</span></span>

> [!NOTE]
> <span data-ttu-id="72602-148">Předchozí kód používá `int` jako typ argumentu pro zjednodušení.</span><span class="sxs-lookup"><span data-stu-id="72602-148">The preceding code uses `int` as the argument type for simplicity.</span></span> <span data-ttu-id="72602-149">Vzhledem k tomu `int` , že se ve většině moderních počítačů nejedná o větší než odkaz, není výhoda pro předání jediného `int` odkazu jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="72602-149">Because `int` is no larger than a reference in most modern machines, there is no benefit to passing a single `int` as a readonly reference.</span></span>

## <a name="limitations-on-in-parameters"></a><span data-ttu-id="72602-150">Omezení `in` parametrů</span><span class="sxs-lookup"><span data-stu-id="72602-150">Limitations on `in` parameters</span></span>

<span data-ttu-id="72602-151">`in` `ref` Klíčová slova, a nelze použít `out` pro následující typy metod:</span><span class="sxs-lookup"><span data-stu-id="72602-151">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="72602-152">Asynchronní metody, které definujete pomocí modifikátoru [Async](async.md) .</span><span class="sxs-lookup"><span data-stu-id="72602-152">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="72602-153">Metody iterátoru, které zahrnují [návratový návrat](yield.md) nebo `yield break` příkaz yield.</span><span class="sxs-lookup"><span data-stu-id="72602-153">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>
- <span data-ttu-id="72602-154">První argument metody rozšíření nemůže mít `in` modifikátor, pokud tento argument není struktura.</span><span class="sxs-lookup"><span data-stu-id="72602-154">The first argument of an extension method cannot have the `in` modifier unless that argument is a struct.</span></span>
- <span data-ttu-id="72602-155">První argument metody rozšíření, kde je tento argument obecný typ (i když je tento typ omezen na strukturu)</span><span class="sxs-lookup"><span data-stu-id="72602-155">The first argument of an extension method where that argument is a generic type (even when that type is constrained to be a struct.)</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="72602-156">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="72602-156">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="72602-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="72602-157">See also</span></span>

- [<span data-ttu-id="72602-158">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="72602-158">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="72602-159">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="72602-159">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="72602-160">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="72602-160">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="72602-161">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="72602-161">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="72602-162">Zapisovat bezpečný efektivní kód</span><span class="sxs-lookup"><span data-stu-id="72602-162">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
