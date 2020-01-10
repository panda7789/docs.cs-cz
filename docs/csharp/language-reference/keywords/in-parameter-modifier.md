---
title: v modifikátoru parametru C# – referenční informace
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: 10e7b91f9a6bf280c5f0654b243492bac8cde1e0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715255"
---
# <a name="in-parameter-modifier-c-reference"></a><span data-ttu-id="31aba-102">in – modifikátor parametruC# (odkaz)</span><span class="sxs-lookup"><span data-stu-id="31aba-102">in parameter modifier (C# Reference)</span></span>

<span data-ttu-id="31aba-103">Klíčové slovo `in` způsobí, že argumenty budou předány odkazem.</span><span class="sxs-lookup"><span data-stu-id="31aba-103">The `in` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="31aba-104">Nastaví formální parametr jako alias pro argument, který musí být proměnná.</span><span class="sxs-lookup"><span data-stu-id="31aba-104">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="31aba-105">Jinými slovy, každá operace s parametrem je provedena na argumentu.</span><span class="sxs-lookup"><span data-stu-id="31aba-105">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="31aba-106">Je podobný klíčovým slovem [ref](ref.md) nebo [out](out-parameter-modifier.md) s tím rozdílem, že `in` argumenty nelze upravovat pomocí volané metody.</span><span class="sxs-lookup"><span data-stu-id="31aba-106">It is like the [ref](ref.md) or [out](out-parameter-modifier.md) keywords, except that `in` arguments cannot be modified by the called method.</span></span> <span data-ttu-id="31aba-107">Vzhledem k tomu, že lze upravit argumenty `ref`, `out` argumenty musí být upraveny volanou metodou a tyto úpravy jsou pozorovatelně v volajícím kontextu.</span><span class="sxs-lookup"><span data-stu-id="31aba-107">Whereas `ref` arguments may be modified, `out` arguments must be modified by the called method, and those modifications are observable in the calling context.</span></span>

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

<span data-ttu-id="31aba-108">Předchozí příklad ukazuje, že modifikátor `in` je obvykle zbytečný na webu volání.</span><span class="sxs-lookup"><span data-stu-id="31aba-108">The preceding example demonstrates that the `in` modifier is usually unnecessary at the call site.</span></span> <span data-ttu-id="31aba-109">Vyžaduje se pouze v deklaraci metody.</span><span class="sxs-lookup"><span data-stu-id="31aba-109">It is only required in the method declaration.</span></span>

> [!NOTE] 
> <span data-ttu-id="31aba-110">Klíčové slovo `in` lze také použít s parametrem obecného typu k určení toho, že parametr typu je kontravariantní, jako součást příkazu `foreach` nebo jako součást klauzule `join` v dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="31aba-110">The `in` keyword can also be used with a generic type parameter to specify that the type parameter is contravariant, as part of a `foreach` statement, or as part of a `join` clause in a LINQ query.</span></span> <span data-ttu-id="31aba-111">Další informace o použití klíčového slova `in` v těchto kontextech naleznete [v části v](in.md)tématu, která poskytuje odkazy na všechna tato použití.</span><span class="sxs-lookup"><span data-stu-id="31aba-111">For more information on the use of the `in` keyword in these contexts, see [in](in.md), which provides links to all those uses.</span></span>
  
<span data-ttu-id="31aba-112">Proměnné předané jako argumenty `in` musí být před předáním do volání metody inicializovány.</span><span class="sxs-lookup"><span data-stu-id="31aba-112">Variables passed as `in` arguments must be initialized before being passed in a method call.</span></span> <span data-ttu-id="31aba-113">Volaná metoda ale nemůže přiřadit hodnotu ani upravovat argument.</span><span class="sxs-lookup"><span data-stu-id="31aba-113">However, the called method may not assign a value or modify the argument.</span></span>  

<span data-ttu-id="31aba-114">Modifikátor parametru `in` je k dispozici C# v 7,2 a novějších.</span><span class="sxs-lookup"><span data-stu-id="31aba-114">The `in` parameter modifier is available in C# 7.2 and later.</span></span> <span data-ttu-id="31aba-115">Předchozí verze generují chybu kompilátoru `CS8107` ("funkce" odkazy jen pro čtení "není v C# 7,0 k dispozici.</span><span class="sxs-lookup"><span data-stu-id="31aba-115">Previous versions generate compiler error `CS8107` ("Feature 'readonly references' is not available in C# 7.0.</span></span> <span data-ttu-id="31aba-116">Použijte prosím jazyk verze 7,2 nebo vyšší. ") Chcete-li nakonfigurovat verzi jazyka kompilátoru, přečtěte si téma [ C# výběr jazykové verze](../configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="31aba-116">Please use language version 7.2 or greater.") To configure the compiler language version, see [Select the C# language version](../configure-language-version.md).</span></span>

<span data-ttu-id="31aba-117">Klíčová slova `in`, `ref`a `out` nejsou považována za součást signatury metody pro účely překladu přetížení.</span><span class="sxs-lookup"><span data-stu-id="31aba-117">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="31aba-118">Proto metody nemohou být přetíženy, pokud jediným rozdílem je, že jedna metoda přebírá `ref` nebo `in` argument a druhý přebírá `out` argument.</span><span class="sxs-lookup"><span data-stu-id="31aba-118">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="31aba-119">Následující kód například nebude zkompilován:</span><span class="sxs-lookup"><span data-stu-id="31aba-119">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="31aba-120">Přetížení na základě přítomnosti `in` je povoleno:</span><span class="sxs-lookup"><span data-stu-id="31aba-120">Overloading based on the presence of `in` is allowed:</span></span>  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a><span data-ttu-id="31aba-121">Pravidla řešení přetížení</span><span class="sxs-lookup"><span data-stu-id="31aba-121">Overload resolution rules</span></span>

<span data-ttu-id="31aba-122">Pravidla řešení přetížení můžete pochopit pro metody s hodnotou a `in` argumenty vysvětlením motivace pro `in` argumenty.</span><span class="sxs-lookup"><span data-stu-id="31aba-122">You can understand the overload resolution rules for methods with by value vs. `in` arguments by understanding the motivation for `in` arguments.</span></span> <span data-ttu-id="31aba-123">Definování metod pomocí `in`ch parametrů je potenciální optimalizace výkonu.</span><span class="sxs-lookup"><span data-stu-id="31aba-123">Defining methods using `in` parameters is a potential performance optimization.</span></span> <span data-ttu-id="31aba-124">Některé argumenty typu `struct` mohou být velké a když jsou metody volány v těsných smyčkách nebo kritických cestách kódu, náklady na kopírování těchto struktur jsou kritické.</span><span class="sxs-lookup"><span data-stu-id="31aba-124">Some `struct` type arguments may be large in size, and when methods are called in tight loops or critical code paths, the cost of copying those structures is critical.</span></span> <span data-ttu-id="31aba-125">Metody deklarují `in` parametrů pro určení, že argumenty mohou být předány odkazem bezpečně, protože volaná metoda neupravuje stav tohoto argumentu.</span><span class="sxs-lookup"><span data-stu-id="31aba-125">Methods declare `in` parameters to specify that arguments may be passed by reference safely because the called method does not modify the state of that argument.</span></span> <span data-ttu-id="31aba-126">Předání těchto argumentů odkazem se vyhne (potenciálně) nákladné kopii.</span><span class="sxs-lookup"><span data-stu-id="31aba-126">Passing those arguments by reference avoids the (potentially) expensive copy.</span></span> 

<span data-ttu-id="31aba-127">Určení `in` argumentů na webu volání je obvykle volitelné.</span><span class="sxs-lookup"><span data-stu-id="31aba-127">Specifying `in` for arguments at the call site is typically optional.</span></span> <span data-ttu-id="31aba-128">Neexistuje žádný sémantický rozdíl mezi předáním argumentů podle hodnoty a jejich předáním odkazem pomocí modifikátoru `in`.</span><span class="sxs-lookup"><span data-stu-id="31aba-128">There is no semantic difference between passing arguments by value and passing them by reference using the `in` modifier.</span></span> <span data-ttu-id="31aba-129">Modifikátor `in` na webu volání je nepovinný, protože nemusíte označovat, že hodnota argumentu může být změněna.</span><span class="sxs-lookup"><span data-stu-id="31aba-129">The `in` modifier at the call site is optional because you don't need to indicate that the argument's value might be changed.</span></span> <span data-ttu-id="31aba-130">Explicitně přidáte modifikátor `in` na webu volání, aby se zajistilo, že argument je předán odkazem, nikoli hodnotou.</span><span class="sxs-lookup"><span data-stu-id="31aba-130">You explicitly add the `in` modifier at the call site to ensure the argument is passed by reference, not by value.</span></span> <span data-ttu-id="31aba-131">Explicitní použití `in` má následující dva účinky:</span><span class="sxs-lookup"><span data-stu-id="31aba-131">Explicitly using `in` has the following two effects:</span></span>

<span data-ttu-id="31aba-132">Nejprve zadáním `in` na webu volání vynutí kompilátor vybrat metodu definovanou s parametrem odpovídajícího `in`.</span><span class="sxs-lookup"><span data-stu-id="31aba-132">First, specifying `in` at the call site forces the compiler to select a method defined with a matching `in` parameter.</span></span> <span data-ttu-id="31aba-133">V opačném případě, pokud se dvě metody liší pouze v přítomnosti `in`, je přetížení hodnotou pomocí lepší shody.</span><span class="sxs-lookup"><span data-stu-id="31aba-133">Otherwise, when two methods differ only in the presence of `in`, the by value overload is a better match.</span></span>

<span data-ttu-id="31aba-134">Dále zadáním `in` deklarujete záměr k předání argumentu odkazem.</span><span class="sxs-lookup"><span data-stu-id="31aba-134">Second, specifying `in` declares your intent to pass an argument by reference.</span></span> <span data-ttu-id="31aba-135">Argument použitý v `in` musí představovat umístění, na které lze přímo odkazovat.</span><span class="sxs-lookup"><span data-stu-id="31aba-135">The argument used with `in` must represent a location that can be directly referred to.</span></span> <span data-ttu-id="31aba-136">Platí stejná obecná pravidla pro argumenty `out` a `ref`: nemůžete použít konstanty, běžné vlastnosti nebo jiné výrazy, které vytváří hodnoty.</span><span class="sxs-lookup"><span data-stu-id="31aba-136">The same general rules for `out` and `ref` arguments apply: You cannot use constants, ordinary properties, or other expressions that produce values.</span></span> <span data-ttu-id="31aba-137">V opačném případě vynechání `in` na webu volání informuje kompilátor, že umožňuje vytvořit dočasnou proměnnou, která bude předána odkazem jen pro čtení k metodě.</span><span class="sxs-lookup"><span data-stu-id="31aba-137">Otherwise, omitting `in` at the call site informs the compiler that you will allow it to create a temporary variable to pass by read-only reference to the method.</span></span> <span data-ttu-id="31aba-138">Kompilátor vytvoří dočasnou proměnnou k překonání několika omezení s `in` argumenty:</span><span class="sxs-lookup"><span data-stu-id="31aba-138">The compiler creates a temporary variable to overcome several restrictions with `in` arguments:</span></span>

- <span data-ttu-id="31aba-139">Dočasná proměnná umožňuje konstanty v čase kompilace jako parametry `in`.</span><span class="sxs-lookup"><span data-stu-id="31aba-139">A temporary variable allows compile-time constants as `in` parameters.</span></span>
- <span data-ttu-id="31aba-140">Dočasná proměnná povoluje vlastnosti nebo jiné výrazy pro parametry `in`.</span><span class="sxs-lookup"><span data-stu-id="31aba-140">A temporary variable allows properties, or other expressions for `in` parameters.</span></span>
- <span data-ttu-id="31aba-141">Dočasná proměnná umožňuje argumenty, kde existuje implicitní převod typu argumentu na typ parametru.</span><span class="sxs-lookup"><span data-stu-id="31aba-141">A temporary variable allows arguments where there is an implicit conversion from the argument type to the parameter type.</span></span>

<span data-ttu-id="31aba-142">Ve všech předchozích instancích vytvoří kompilátor dočasnou proměnnou, která ukládá hodnotu konstanty, vlastnosti nebo jiného výrazu.</span><span class="sxs-lookup"><span data-stu-id="31aba-142">In all the preceding instances, the compiler creates a temporary variable that stores the value of the constant, property, or other expression.</span></span>

<span data-ttu-id="31aba-143">Následující kód ilustruje tato pravidla:</span><span class="sxs-lookup"><span data-stu-id="31aba-143">The following code illustrates these rules:</span></span>

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

<span data-ttu-id="31aba-144">Nyní předpokládejme, že je k dispozici jiná metoda používající argumenty hodnoty.</span><span class="sxs-lookup"><span data-stu-id="31aba-144">Now, suppose another method using by value arguments was available.</span></span> <span data-ttu-id="31aba-145">Změny výsledků, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="31aba-145">The results change as shown in the following code:</span></span>

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

<span data-ttu-id="31aba-146">Jediným voláním metody, kde je argument předána odkazem, je ten poslední.</span><span class="sxs-lookup"><span data-stu-id="31aba-146">The only method call where the argument is passed by reference is the final one.</span></span>

> [!NOTE]
> <span data-ttu-id="31aba-147">Předchozí kód používá `int` jako typ argumentu pro zjednodušení.</span><span class="sxs-lookup"><span data-stu-id="31aba-147">The preceding code uses `int` as the argument type for simplicity.</span></span> <span data-ttu-id="31aba-148">Vzhledem k tomu, že `int` není větší než odkaz ve většině moderních počítačů, neexistuje žádná výhoda k předání jednoho `int` jako odkazu jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="31aba-148">Because `int` is no larger than a reference in most modern machines, there is no benefit to passing a single `int` as a readonly reference.</span></span> 

## <a name="limitations-on-in-parameters"></a><span data-ttu-id="31aba-149">Omezení parametrů `in`</span><span class="sxs-lookup"><span data-stu-id="31aba-149">Limitations on `in` parameters</span></span>

<span data-ttu-id="31aba-150">Klíčová slova `in`, `ref`a `out` nelze použít pro následující typy metod:</span><span class="sxs-lookup"><span data-stu-id="31aba-150">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="31aba-151">Asynchronní metody, které definujete pomocí modifikátoru [Async](async.md) .</span><span class="sxs-lookup"><span data-stu-id="31aba-151">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="31aba-152">Metody iterátoru, které zahrnují příkaz [yield return](yield.md) nebo `yield break`.</span><span class="sxs-lookup"><span data-stu-id="31aba-152">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="31aba-153">C# – jazyková specifikace</span><span class="sxs-lookup"><span data-stu-id="31aba-153">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="31aba-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="31aba-154">See also</span></span>

- [<span data-ttu-id="31aba-155">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="31aba-155">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="31aba-156">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="31aba-156">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="31aba-157">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="31aba-157">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="31aba-158">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="31aba-158">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="31aba-159">Zapisovat bezpečný efektivní kód</span><span class="sxs-lookup"><span data-stu-id="31aba-159">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
