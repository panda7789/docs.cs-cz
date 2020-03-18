---
title: System.Delegate a `delegate` klíčové slovo
description: Další informace o třídách v rozhraní .NET, které podporují delegáty a jak se tyto mapovat na 'delegate' klíčové slovo.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 87fdf19c4ea810c5ac4409fe16c3cba9d5fc6574
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146278"
---
# <a name="systemdelegate-and-the-delegate-keyword"></a><span data-ttu-id="fb2d8-103">System.Delegate a `delegate` klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="fb2d8-103">System.Delegate and the `delegate` keyword</span></span>

[<span data-ttu-id="fb2d8-104">Předchozí</span><span class="sxs-lookup"><span data-stu-id="fb2d8-104">Previous</span></span>](delegates-overview.md)

<span data-ttu-id="fb2d8-105">Tento článek popisuje třídy v rozhraní .NET, které `delegate` podporují delegáty a jak tyto mapování na klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-105">This article covers the classes in .NET that support delegates, and how those map to the `delegate` keyword.</span></span>

## <a name="define-delegate-types"></a><span data-ttu-id="fb2d8-106">Definování typů delegátů</span><span class="sxs-lookup"><span data-stu-id="fb2d8-106">Define delegate types</span></span>

<span data-ttu-id="fb2d8-107">Začněme s klíčovým slovem "delegate", protože to je především to, co budete používat při práci s delegáty.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-107">Let's start with the 'delegate' keyword, because that's primarily what you will use as you work with delegates.</span></span> <span data-ttu-id="fb2d8-108">Kód, který kompilátor generuje při `delegate` použití klíčového slova, bude <xref:System.Delegate> mapovat na volání metody, které vyvolávají členy tříd y a. <xref:System.MulticastDelegate></span><span class="sxs-lookup"><span data-stu-id="fb2d8-108">The code that the compiler generates when you use the `delegate` keyword will map to method calls that invoke members of the <xref:System.Delegate> and <xref:System.MulticastDelegate> classes.</span></span>

<span data-ttu-id="fb2d8-109">Typ delegáta definujete pomocí syntaxe, která je podobná definování podpisu metody.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-109">You define a delegate type using syntax that is similar to defining a method signature.</span></span> <span data-ttu-id="fb2d8-110">Stačí přidat `delegate` klíčové slovo do definice.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-110">You just add the `delegate` keyword to the definition.</span></span>

<span data-ttu-id="fb2d8-111">Pojďme pokračovat v používání List.Sort() metoda jako náš příklad.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-111">Let's continue to use the List.Sort() method as our example.</span></span> <span data-ttu-id="fb2d8-112">Prvním krokem je vytvoření typu pro delegáta porovnání:</span><span class="sxs-lookup"><span data-stu-id="fb2d8-112">The first step is to create a type for the comparison delegate:</span></span>

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

<span data-ttu-id="fb2d8-113">Kompilátor generuje třídu odvozenou `System.Delegate` od které odpovídá použitému podpisu (v tomto případě metoda, která vrací celé číslo a má dva argumenty).</span><span class="sxs-lookup"><span data-stu-id="fb2d8-113">The compiler generates a class, derived from `System.Delegate` that matches the signature used (in this case, a method that returns an integer, and has two arguments).</span></span> <span data-ttu-id="fb2d8-114">Typ tohoto delegáta `Comparison`je .</span><span class="sxs-lookup"><span data-stu-id="fb2d8-114">The type of that delegate is `Comparison`.</span></span> <span data-ttu-id="fb2d8-115">Typ `Comparison` delegáta je obecný typ.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-115">The `Comparison` delegate type is a generic type.</span></span> <span data-ttu-id="fb2d8-116">Podrobnosti o generických léčivých přípravcích naleznete [zde](programming-guide/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="fb2d8-116">For details on generics see [here](programming-guide/generics/index.md).</span></span>

<span data-ttu-id="fb2d8-117">Všimněte si, že syntaxe může vypadat, jako by deklarovala proměnnou, ale ve skutečnosti deklaruje *typ*.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-117">Notice that the syntax may appear as though it is declaring a variable, but it is actually declaring a *type*.</span></span> <span data-ttu-id="fb2d8-118">Můžete definovat typy delegátů uvnitř tříd, přímo uvnitř oborů názvů nebo dokonce v globálním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-118">You can define delegate types inside classes, directly inside namespaces, or even in the global namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="fb2d8-119">Deklarování typů delegátů (nebo jiných typů) přímo v globálním oboru názvů se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-119">Declaring delegate types (or other types) directly in the global namespace is not recommended.</span></span>

<span data-ttu-id="fb2d8-120">Kompilátor také generuje přidat a odebrat obslužné rutiny pro tento nový typ tak, aby klienti této třídy můžete přidat a odebrat metody ze seznamu vyvolání instance.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-120">The compiler also generates add and remove handlers for this new type so that clients of this class can add and remove methods from an instance's invocation list.</span></span> <span data-ttu-id="fb2d8-121">Kompilátor vynucuje, že podpis přidané nebo odebrané metody odpovídá podpisu použitému při deklarování metody.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-121">The compiler will enforce that the signature of the method being added or removed matches the signature used when declaring the method.</span></span>

## <a name="declare-instances-of-delegates"></a><span data-ttu-id="fb2d8-122">Deklarovat instance delegátů</span><span class="sxs-lookup"><span data-stu-id="fb2d8-122">Declare instances of delegates</span></span>

<span data-ttu-id="fb2d8-123">Po definování delegáta můžete vytvořit instanci tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-123">After defining the delegate, you can create an instance of that type.</span></span>
<span data-ttu-id="fb2d8-124">Stejně jako všechny proměnné v systému C#nelze deklarovat instance delegáta přímo v oboru názvů nebo v globálním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-124">Like all variables in C#, you cannot declare delegate instances directly in a namespace, or in the global namespace.</span></span>

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

<span data-ttu-id="fb2d8-125">Typ proměnné je `Comparison<T>`, typ delegáta definovaný dříve.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-125">The type of the variable is `Comparison<T>`, the delegate type defined earlier.</span></span> <span data-ttu-id="fb2d8-126">Název proměnné je `comparator`.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-126">The name of the variable is `comparator`.</span></span>

 <span data-ttu-id="fb2d8-127">Tento fragment kódu nad deklaroval proměnnou člena uvnitř třídy.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-127">That code snippet above declared a member variable inside a class.</span></span> <span data-ttu-id="fb2d8-128">Můžete také deklarovat proměnné delegáta, které jsou místní proměnné nebo argumenty pro metody.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-128">You can also declare delegate variables that are local variables, or arguments to methods.</span></span>

## <a name="invoke-delegates"></a><span data-ttu-id="fb2d8-129">Vyvolat delegáty</span><span class="sxs-lookup"><span data-stu-id="fb2d8-129">Invoke delegates</span></span>

<span data-ttu-id="fb2d8-130">Můžete vyvolat metody, které jsou v seznamu vyvolání delegáta voláním tohoto delegáta.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-130">You invoke the methods that are in the invocation list of a delegate by calling that delegate.</span></span> <span data-ttu-id="fb2d8-131">Uvnitř `Sort()` metody bude kód volat metodu porovnání k určení pořadí, které mají být objekty umístit:</span><span class="sxs-lookup"><span data-stu-id="fb2d8-131">Inside the `Sort()` method, the code will call the comparison method to determine which order to place objects:</span></span>

```csharp
int result = comparator(left, right);
```

<span data-ttu-id="fb2d8-132">Ve výše uvedeném řádku kód *vyvolá* metodu připojenou k delegátovi.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-132">In the line above, the code *invokes* the method attached to the delegate.</span></span>
<span data-ttu-id="fb2d8-133">Proměnnou zacházíte jako s názvem metody a vyvoláte ji pomocí syntaxe volání normální metody.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-133">You treat the variable as a method name, and invoke it using normal method call syntax.</span></span>

<span data-ttu-id="fb2d8-134">Tento řádek kódu vytváří nebezpečný předpoklad: Neexistuje žádná záruka, že cíl byl přidán do delegáta.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-134">That line of code makes an unsafe assumption: There's no guarantee that a target has been added to the delegate.</span></span> <span data-ttu-id="fb2d8-135">Pokud nebyly připojeny žádné cíle, výše `NullReferenceException` uvedená čára by způsobila, že by byla hozena.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-135">If no targets have been attached, the line above would cause a `NullReferenceException` to be thrown.</span></span> <span data-ttu-id="fb2d8-136">Idiomy používané k řešení tohoto problému jsou složitější než jednoduchá kontrola null a jsou zahrnuty dále v této [řadě](delegates-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="fb2d8-136">The idioms used to address this problem are more complicated than a simple null-check, and are covered later in this [series](delegates-patterns.md).</span></span>

## <a name="assign-add-and-remove-invocation-targets"></a><span data-ttu-id="fb2d8-137">Přiřazení, přidání a odebrání cílů vyvolání</span><span class="sxs-lookup"><span data-stu-id="fb2d8-137">Assign, add, and remove invocation targets</span></span>

<span data-ttu-id="fb2d8-138">To je, jak je definován typ delegáta a jak jsou deklarovány a vyvolány instance delegáta.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-138">That's how a delegate type is defined, and how delegate instances are declared and invoked.</span></span>

<span data-ttu-id="fb2d8-139">Vývojáři, kteří `List.Sort()` chtějí použít metodu, musí definovat metodu, jejíž podpis odpovídá definici typu delegáta, a přiřadit ji delegátovi používanému metodou sort.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-139">Developers that want to use the `List.Sort()` method need to define a method whose signature matches the delegate type definition, and assign it to the delegate used by the sort method.</span></span> <span data-ttu-id="fb2d8-140">Toto přiřazení přidá metodu do seznamu vyvolání tohoto objektu delegáta.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-140">This assignment adds the method to the invocation list of that delegate object.</span></span>

<span data-ttu-id="fb2d8-141">Předpokládejme, že chcete seřadit seznam řetězců podle jejich délky.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-141">Suppose you wanted to sort a list of strings by their length.</span></span> <span data-ttu-id="fb2d8-142">Funkce porovnání může být následující:</span><span class="sxs-lookup"><span data-stu-id="fb2d8-142">Your comparison function might be the following:</span></span>

```csharp
private static int CompareLength(string left, string right) =>
    left.Length.CompareTo(right.Length);
```

<span data-ttu-id="fb2d8-143">Metoda je deklarována jako soukromá metoda.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-143">The method is declared as a private method.</span></span> <span data-ttu-id="fb2d8-144">To je v pořádku.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-144">That's fine.</span></span> <span data-ttu-id="fb2d8-145">Pravděpodobně nechcete, aby tato metoda byla součástí vašeho veřejného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-145">You may not want this method to be part of your public interface.</span></span> <span data-ttu-id="fb2d8-146">Stále lze použít jako metodu porovnání při připojení k delegátovi.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-146">It can still be used as the comparison method when attached to a delegate.</span></span> <span data-ttu-id="fb2d8-147">Volající kód bude mít tuto metodu připojenou k cílovému seznamu objektu delegáta a může k němu přistupovat prostřednictvím tohoto delegáta.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-147">The calling code will have this method attached to the target list of the delegate object, and can access it through that delegate.</span></span>

<span data-ttu-id="fb2d8-148">Tento vztah vytvoříte předáním `List.Sort()` této metody metodě:</span><span class="sxs-lookup"><span data-stu-id="fb2d8-148">You create that relationship by passing that method to the `List.Sort()` method:</span></span>

```csharp
phrases.Sort(CompareLength);
```

<span data-ttu-id="fb2d8-149">Všimněte si, že název metody se používá, bez závorek.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-149">Notice that the method name is used, without parentheses.</span></span> <span data-ttu-id="fb2d8-150">Použití metody jako argument udává kompilátoru převést odkaz na metodu na odkaz, který lze použít jako cíl vyvolání delegáta, a připojit tuto metodu jako cíl vyvolání.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-150">Using the method as an argument tells the compiler to convert the method reference into a reference that can be used as a delegate invocation target, and attach that method as an invocation target.</span></span>

<span data-ttu-id="fb2d8-151">Můžete také být explicitní deklarováním `Comparison<string>` proměnné typu a provedením přiřazení:</span><span class="sxs-lookup"><span data-stu-id="fb2d8-151">You could also have been explicit by declaring a variable of type `Comparison<string>` and doing an assignment:</span></span>

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

<span data-ttu-id="fb2d8-152">V použitích, kde je metoda používaná jako cíl delegáta malou metodou, je běžné použít syntaxi [výrazu lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md) k provedení přiřazení:</span><span class="sxs-lookup"><span data-stu-id="fb2d8-152">In uses where the method being used as a delegate target is a small method, it's common to use [lambda expression](./programming-guide/statements-expressions-operators/lambda-expressions.md) syntax to perform the assignment:</span></span>

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

<span data-ttu-id="fb2d8-153">Použití lambda výrazy pro delegáta cíle je popsána více v [pozdější části](delegates-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="fb2d8-153">Using lambda expressions for delegate targets is covered more in a [later section](delegates-patterns.md).</span></span>

<span data-ttu-id="fb2d8-154">Sort() příklad obvykle připojí jednu cílovou metodu delegáta.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-154">The Sort() example typically attaches a single target method to the delegate.</span></span> <span data-ttu-id="fb2d8-155">Delegát objekty však podporují seznamy vyvolání, které mají více cílových metod připojených k objektu delegáta.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-155">However, delegate objects do support invocation lists that have multiple target methods attached to a delegate object.</span></span>

## <a name="delegate-and-multicastdelegate-classes"></a><span data-ttu-id="fb2d8-156">Třídy Delegate a MulticastDelegate</span><span class="sxs-lookup"><span data-stu-id="fb2d8-156">Delegate and MulticastDelegate classes</span></span>

<span data-ttu-id="fb2d8-157">Jazyková podpora popsaná výše poskytuje funkce a podporu, které budete obvykle potřebovat pro práci s delegáty.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-157">The language support described above provides the features and support you'll typically need to work with delegates.</span></span> <span data-ttu-id="fb2d8-158">Tyto funkce jsou postaveny na dvou třídách v rámci .NET Core: <xref:System.Delegate> a <xref:System.MulticastDelegate>.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-158">These features are built on two classes in the .NET Core framework: <xref:System.Delegate> and <xref:System.MulticastDelegate>.</span></span>

<span data-ttu-id="fb2d8-159">Třída `System.Delegate` a její jediná přímá podtřída , `System.MulticastDelegate`poskytují podporu rozhraní pro vytváření delegátů, registraci metod jako cílů delegáta a vyvolání všech metod, které jsou registrovány jako cíl delegáta.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-159">The `System.Delegate` class and its single direct subclass, `System.MulticastDelegate`, provide the framework support for creating delegates, registering methods as delegate targets, and invoking all methods that are registered as a delegate target.</span></span>

<span data-ttu-id="fb2d8-160">Zajímavé je, `System.Delegate` `System.MulticastDelegate` že a třídy nejsou samy o sobě typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-160">Interestingly, the `System.Delegate` and `System.MulticastDelegate` classes are not themselves delegate types.</span></span> <span data-ttu-id="fb2d8-161">Poskytují základ pro všechny konkrétní typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-161">They do provide the basis for all specific delegate types.</span></span> <span data-ttu-id="fb2d8-162">Stejný proces návrhu jazyka nařízen, že nelze `Delegate` deklarovat třídu, která je odvozena od nebo `MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-162">That same language design process mandated that you cannot declare a class that derives from `Delegate` or `MulticastDelegate`.</span></span> <span data-ttu-id="fb2d8-163">Pravidla jazyka C# zakázat.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-163">The C# language rules prohibit it.</span></span>

<span data-ttu-id="fb2d8-164">Místo toho kompilátor Jazyka C# vytvoří instance `MulticastDelegate` třídy odvozené z při použití klíčového slova jazyka C# k deklarování typů delegátů.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-164">Instead, the C# compiler creates instances of a class derived from `MulticastDelegate` when you use the C# language keyword to declare delegate types.</span></span>

<span data-ttu-id="fb2d8-165">Tento návrh má své kořeny v první verzi C# a .NET.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-165">This design has its roots in the first release of C# and .NET.</span></span> <span data-ttu-id="fb2d8-166">Jedním z cílů pro návrhářský tým bylo zajistit, aby jazyk vynucený typ bezpečnosti při použití delegátů.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-166">One goal for the design team was to ensure that the language enforced type safety when using delegates.</span></span> <span data-ttu-id="fb2d8-167">To znamenalo zajistit, že delegáti byli vyvoláni se správným typem a počtem argumentů.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-167">That meant ensuring that delegates were invoked with the right type and number of arguments.</span></span> <span data-ttu-id="fb2d8-168">A že všechny návratové typy byla správně označena v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-168">And, that any return type was correctly indicated at compile time.</span></span> <span data-ttu-id="fb2d8-169">Delegáti byli součástí verze 1.0 .NET, která byla před obecnými typy.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-169">Delegates were part of the 1.0 .NET release, which was before generics.</span></span>

<span data-ttu-id="fb2d8-170">Nejlepší způsob, jak vynutit tento typ bezpečnosti bylo pro kompilátor vytvořit konkrétní delegát třídy, které představovaly metodu podpisu používá.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-170">The best way to enforce this type safety was for the compiler to create the concrete delegate classes that represented the method signature being used.</span></span>

<span data-ttu-id="fb2d8-171">I když nelze vytvořit odvozené třídy přímo, budete používat metody definované na tyto třídy.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-171">Even though you cannot create derived classes directly, you will use the methods defined on these classes.</span></span> <span data-ttu-id="fb2d8-172">Pojďme projít nejběžnější metody, které budete používat při práci s delegáty.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-172">Let's go through the most common methods that you will use when you work with delegates.</span></span>

<span data-ttu-id="fb2d8-173">První, nejdůležitější skutečností je, že každý delegát, se `MulticastDelegate`kterým pracujete, je odvozen z .</span><span class="sxs-lookup"><span data-stu-id="fb2d8-173">The first, most important fact to remember is that every delegate you work with is derived from `MulticastDelegate`.</span></span> <span data-ttu-id="fb2d8-174">Delegát vícesměrového vysílání znamená, že při vyvolání prostřednictvím delegáta lze vyvolat více než jeden cíl metody.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-174">A multicast delegate means that more than one method target can be invoked when invoking through a delegate.</span></span> <span data-ttu-id="fb2d8-175">Původní návrh zvažoval rozlišení mezi delegáty, kde by mohla být připojena a vyvolána pouze jedna cílová metoda, a delegáty, kde by mohlo být připojeno a vyvoláno více cílových metod.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-175">The original design considered making a distinction between delegates where only one target method could be attached and invoked, and delegates where multiple target methods could be attached and invoked.</span></span> <span data-ttu-id="fb2d8-176">Toto rozlišení se v praxi ukázalo jako méně užitečné, než se původně předpokládalo.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-176">That distinction proved to be less useful in practice than originally thought.</span></span> <span data-ttu-id="fb2d8-177">Dvě různé třídy byly již vytvořeny a byly v rámci od jeho počátečního veřejného vydání.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-177">The two different classes were already created, and have been in the framework since its initial public release.</span></span>

<span data-ttu-id="fb2d8-178">Metody, které budete používat nejvíce `Invoke()` s `BeginInvoke()`  /  `EndInvoke()`delegáty jsou a .</span><span class="sxs-lookup"><span data-stu-id="fb2d8-178">The methods that you will use the most with delegates are `Invoke()` and `BeginInvoke()` / `EndInvoke()`.</span></span> <span data-ttu-id="fb2d8-179">`Invoke()`vyvolá všechny metody, které byly připojeny k určité instanci delegáta.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-179">`Invoke()` will invoke all the methods that have been attached to a particular delegate instance.</span></span> <span data-ttu-id="fb2d8-180">Jak jste viděli výše, obvykle vyvoláte delegáty pomocí syntaxe volání metody na proměnné delegáta.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-180">As you saw above, you typically invoke delegates using the method call syntax on the delegate variable.</span></span> <span data-ttu-id="fb2d8-181">Jak uvidíte [dále v této sérii](delegates-patterns.md), existují vzory, které pracují přímo s těmito metodami.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-181">As you'll see [later in this series](delegates-patterns.md), there are patterns that work directly with these methods.</span></span>

<span data-ttu-id="fb2d8-182">Teď, když jste viděli syntaxi jazyka a třídy, které podporují delegáty, podívejme se, jak silně zadali delegáti jsou používány, vytvořeny a vyvolány.</span><span class="sxs-lookup"><span data-stu-id="fb2d8-182">Now that you've seen the language syntax and the classes that support delegates, let's examine how strongly typed delegates are used, created, and invoked.</span></span>

[<span data-ttu-id="fb2d8-183">Další</span><span class="sxs-lookup"><span data-stu-id="fb2d8-183">Next</span></span>](delegates-strongly-typed.md)
