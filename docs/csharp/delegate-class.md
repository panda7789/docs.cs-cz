---
title: System. Delegate a `delegate` klíčové slovo
description: Přečtěte si o třídách v rozhraní .NET, které podporují delegáty a jejich mapování na klíčové slovo Delegate.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 9df8ad68f6bfa62863ee047875b6419fc81ad779
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062460"
---
# <a name="systemdelegate-and-the-delegate-keyword"></a><span data-ttu-id="972b0-103">System. Delegate a `delegate` klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="972b0-103">System.Delegate and the `delegate` keyword</span></span>

[<span data-ttu-id="972b0-104">Předchozí</span><span class="sxs-lookup"><span data-stu-id="972b0-104">Previous</span></span>](delegates-overview.md)

<span data-ttu-id="972b0-105">Tento článek popisuje třídy v rozhraní .NET, které podporují delegáty, a způsob, jakým jsou tato mapování na `delegate` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="972b0-105">This article covers the classes in .NET that support delegates, and how those map to the `delegate` keyword.</span></span>

## <a name="define-delegate-types"></a><span data-ttu-id="972b0-106">Definování typů delegátů</span><span class="sxs-lookup"><span data-stu-id="972b0-106">Define delegate types</span></span>

<span data-ttu-id="972b0-107">Pojďme začít s klíčovým slovem Delegate, protože to je primárně to, co budete používat při práci s delegáty.</span><span class="sxs-lookup"><span data-stu-id="972b0-107">Let's start with the 'delegate' keyword, because that's primarily what you will use as you work with delegates.</span></span> <span data-ttu-id="972b0-108">Kód, který kompilátor generuje při použití `delegate` klíčového slova, se namapuje na volání metod, která vyvolávají členy <xref:System.Delegate> <xref:System.MulticastDelegate> tříd a.</span><span class="sxs-lookup"><span data-stu-id="972b0-108">The code that the compiler generates when you use the `delegate` keyword will map to method calls that invoke members of the <xref:System.Delegate> and <xref:System.MulticastDelegate> classes.</span></span>

<span data-ttu-id="972b0-109">Můžete definovat typ delegáta pomocí syntaxe, která je podobná definování signatury metody.</span><span class="sxs-lookup"><span data-stu-id="972b0-109">You define a delegate type using syntax that is similar to defining a method signature.</span></span> <span data-ttu-id="972b0-110">Stačí přidat `delegate` klíčové slovo do definice.</span><span class="sxs-lookup"><span data-stu-id="972b0-110">You just add the `delegate` keyword to the definition.</span></span>

<span data-ttu-id="972b0-111">Pojďme dál používat metodu list. Sort () jako náš příklad.</span><span class="sxs-lookup"><span data-stu-id="972b0-111">Let's continue to use the List.Sort() method as our example.</span></span> <span data-ttu-id="972b0-112">Prvním krokem je vytvoření typu pro delegáta porovnání:</span><span class="sxs-lookup"><span data-stu-id="972b0-112">The first step is to create a type for the comparison delegate:</span></span>

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

<span data-ttu-id="972b0-113">Kompilátor vygeneruje třídu odvozenou z `System.Delegate` , která odpovídá použitému podpisu (v tomto případě metoda, která vrací celé číslo a má dva argumenty).</span><span class="sxs-lookup"><span data-stu-id="972b0-113">The compiler generates a class, derived from `System.Delegate` that matches the signature used (in this case, a method that returns an integer, and has two arguments).</span></span> <span data-ttu-id="972b0-114">Typ tohoto delegáta je `Comparison` .</span><span class="sxs-lookup"><span data-stu-id="972b0-114">The type of that delegate is `Comparison`.</span></span> <span data-ttu-id="972b0-115">`Comparison`Typ delegáta je obecný typ.</span><span class="sxs-lookup"><span data-stu-id="972b0-115">The `Comparison` delegate type is a generic type.</span></span> <span data-ttu-id="972b0-116">Podrobnosti o obecných typech najdete [tady](programming-guide/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="972b0-116">For details on generics see [here](programming-guide/generics/index.md).</span></span>

<span data-ttu-id="972b0-117">Všimněte si, že se syntaxe může zobrazit, jako by deklaruje proměnnou, ale ve skutečnosti deklaruje *typ*.</span><span class="sxs-lookup"><span data-stu-id="972b0-117">Notice that the syntax may appear as though it is declaring a variable, but it is actually declaring a *type*.</span></span> <span data-ttu-id="972b0-118">Můžete definovat typy delegátů uvnitř tříd, přímo v oborech názvů nebo dokonce v globálním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="972b0-118">You can define delegate types inside classes, directly inside namespaces, or even in the global namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="972b0-119">Deklarace typů delegátů (nebo jiných typů) přímo v globálním oboru názvů se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="972b0-119">Declaring delegate types (or other types) directly in the global namespace is not recommended.</span></span>

<span data-ttu-id="972b0-120">Kompilátor také generuje přidat a odebrat obslužné rutiny pro tento nový typ tak, aby klienti této třídy mohli přidávat a odebírat metody ze seznamu volání instance.</span><span class="sxs-lookup"><span data-stu-id="972b0-120">The compiler also generates add and remove handlers for this new type so that clients of this class can add and remove methods from an instance's invocation list.</span></span> <span data-ttu-id="972b0-121">Kompilátor vyhodnotí, že signatura přidávaného nebo odebraného metody odpovídá podpisu použitému při deklaraci metody.</span><span class="sxs-lookup"><span data-stu-id="972b0-121">The compiler will enforce that the signature of the method being added or removed matches the signature used when declaring the method.</span></span>

## <a name="declare-instances-of-delegates"></a><span data-ttu-id="972b0-122">Deklarovat instance delegátů</span><span class="sxs-lookup"><span data-stu-id="972b0-122">Declare instances of delegates</span></span>

<span data-ttu-id="972b0-123">Po definování delegáta můžete vytvořit instanci tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="972b0-123">After defining the delegate, you can create an instance of that type.</span></span>
<span data-ttu-id="972b0-124">Podobně jako všechny proměnné v jazyce C# nelze deklarovat instance delegátů přímo v oboru názvů nebo v globálním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="972b0-124">Like all variables in C#, you cannot declare delegate instances directly in a namespace, or in the global namespace.</span></span>

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

<span data-ttu-id="972b0-125">Typ proměnné je `Comparison<T>` , typ delegáta byl dříve definován.</span><span class="sxs-lookup"><span data-stu-id="972b0-125">The type of the variable is `Comparison<T>`, the delegate type defined earlier.</span></span> <span data-ttu-id="972b0-126">Název proměnné je `comparator` .</span><span class="sxs-lookup"><span data-stu-id="972b0-126">The name of the variable is `comparator`.</span></span>

 <span data-ttu-id="972b0-127">Tento fragment kódu výše deklaruje členskou proměnnou uvnitř třídy.</span><span class="sxs-lookup"><span data-stu-id="972b0-127">That code snippet above declared a member variable inside a class.</span></span> <span data-ttu-id="972b0-128">Můžete také deklarovat proměnné delegáta, které jsou lokální proměnné nebo argumenty metody.</span><span class="sxs-lookup"><span data-stu-id="972b0-128">You can also declare delegate variables that are local variables, or arguments to methods.</span></span>

## <a name="invoke-delegates"></a><span data-ttu-id="972b0-129">Vyvolat delegáty</span><span class="sxs-lookup"><span data-stu-id="972b0-129">Invoke delegates</span></span>

<span data-ttu-id="972b0-130">Vyvoláte metody, které jsou v seznamu volání delegáta, voláním tohoto delegáta.</span><span class="sxs-lookup"><span data-stu-id="972b0-130">You invoke the methods that are in the invocation list of a delegate by calling that delegate.</span></span> <span data-ttu-id="972b0-131">V rámci `Sort()` metody kód zavolá metodu porovnání za účelem určení, které pořadí umístit objekty:</span><span class="sxs-lookup"><span data-stu-id="972b0-131">Inside the `Sort()` method, the code will call the comparison method to determine which order to place objects:</span></span>

```csharp
int result = comparator(left, right);
```

<span data-ttu-id="972b0-132">V řádku výše kód *vyvolá* metodu připojenou k delegátovi.</span><span class="sxs-lookup"><span data-stu-id="972b0-132">In the line above, the code *invokes* the method attached to the delegate.</span></span>
<span data-ttu-id="972b0-133">Zacházíte s proměnnou jako s názvem metody a vyvoláte ji pomocí syntaxe volání normální metody.</span><span class="sxs-lookup"><span data-stu-id="972b0-133">You treat the variable as a method name, and invoke it using normal method call syntax.</span></span>

<span data-ttu-id="972b0-134">Tento řádek kódu představuje nebezpečný předpoklad: není nijak zaručeno, že do delegáta byl přidán cíl.</span><span class="sxs-lookup"><span data-stu-id="972b0-134">That line of code makes an unsafe assumption: There's no guarantee that a target has been added to the delegate.</span></span> <span data-ttu-id="972b0-135">Pokud nebyly připojeny žádné cíle, by výše uvedený řádek způsobil `NullReferenceException` vyvolání.</span><span class="sxs-lookup"><span data-stu-id="972b0-135">If no targets have been attached, the line above would cause a `NullReferenceException` to be thrown.</span></span> <span data-ttu-id="972b0-136">Idiomy, který se používá k vyřešení tohoto problému, je složitější než jednoduchá hodnota null a jsou pokrytá později v této [sérii](delegates-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="972b0-136">The idioms used to address this problem are more complicated than a simple null-check, and are covered later in this [series](delegates-patterns.md).</span></span>

## <a name="assign-add-and-remove-invocation-targets"></a><span data-ttu-id="972b0-137">Přiřazení, přidání a odebrání cílů volání</span><span class="sxs-lookup"><span data-stu-id="972b0-137">Assign, add, and remove invocation targets</span></span>

<span data-ttu-id="972b0-138">To je způsob, jakým je definován typ delegáta a jak jsou instance delegáta deklarovány a vyvolány.</span><span class="sxs-lookup"><span data-stu-id="972b0-138">That's how a delegate type is defined, and how delegate instances are declared and invoked.</span></span>

<span data-ttu-id="972b0-139">Vývojáři, kteří chtějí použít `List.Sort()` metodu, musí definovat metodu, jejíž signatura odpovídá definici typu delegáta, a přiřadit ji k delegátovi použitému metodou řazení.</span><span class="sxs-lookup"><span data-stu-id="972b0-139">Developers that want to use the `List.Sort()` method need to define a method whose signature matches the delegate type definition, and assign it to the delegate used by the sort method.</span></span> <span data-ttu-id="972b0-140">Toto přiřazení přidá metodu do seznamu volání daného objektu Delegate.</span><span class="sxs-lookup"><span data-stu-id="972b0-140">This assignment adds the method to the invocation list of that delegate object.</span></span>

<span data-ttu-id="972b0-141">Předpokládejme, že jste chtěli seřadit seznam řetězců podle jejich délky.</span><span class="sxs-lookup"><span data-stu-id="972b0-141">Suppose you wanted to sort a list of strings by their length.</span></span> <span data-ttu-id="972b0-142">Vaše funkce porovnání může být následující:</span><span class="sxs-lookup"><span data-stu-id="972b0-142">Your comparison function might be the following:</span></span>

```csharp
private static int CompareLength(string left, string right) =>
    left.Length.CompareTo(right.Length);
```

<span data-ttu-id="972b0-143">Metoda je deklarována jako soukromá metoda.</span><span class="sxs-lookup"><span data-stu-id="972b0-143">The method is declared as a private method.</span></span> <span data-ttu-id="972b0-144">To je dobré.</span><span class="sxs-lookup"><span data-stu-id="972b0-144">That's fine.</span></span> <span data-ttu-id="972b0-145">Možná nebudete chtít, aby tato metoda byla součástí vašeho veřejného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="972b0-145">You may not want this method to be part of your public interface.</span></span> <span data-ttu-id="972b0-146">Tuto možnost lze použít jako metodu porovnání, je-li připojena k delegátovi.</span><span class="sxs-lookup"><span data-stu-id="972b0-146">It can still be used as the comparison method when attached to a delegate.</span></span> <span data-ttu-id="972b0-147">Volající kód bude mít tuto metodu připojenou k cílovému seznamu objektu delegáta a může k němu přistupovat prostřednictvím tohoto delegáta.</span><span class="sxs-lookup"><span data-stu-id="972b0-147">The calling code will have this method attached to the target list of the delegate object, and can access it through that delegate.</span></span>

<span data-ttu-id="972b0-148">Tuto relaci vytvoříte předáním této metody do `List.Sort()` metody:</span><span class="sxs-lookup"><span data-stu-id="972b0-148">You create that relationship by passing that method to the `List.Sort()` method:</span></span>

```csharp
phrases.Sort(CompareLength);
```

<span data-ttu-id="972b0-149">Všimněte si, že se používá název metody bez závorek.</span><span class="sxs-lookup"><span data-stu-id="972b0-149">Notice that the method name is used, without parentheses.</span></span> <span data-ttu-id="972b0-150">Použití metody jako argument říká kompilátoru, aby převedl odkaz na metodu na odkaz, který se dá použít jako cíl vyvolání delegáta, a připojte tuto metodu jako cíl volání.</span><span class="sxs-lookup"><span data-stu-id="972b0-150">Using the method as an argument tells the compiler to convert the method reference into a reference that can be used as a delegate invocation target, and attach that method as an invocation target.</span></span>

<span data-ttu-id="972b0-151">Mohli jste být také explicitní deklarací proměnné typu `Comparison<string>` a provedením přiřazení:</span><span class="sxs-lookup"><span data-stu-id="972b0-151">You could also have been explicit by declaring a variable of type `Comparison<string>` and doing an assignment:</span></span>

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

<span data-ttu-id="972b0-152">V použití, kde je metoda používaná jako cíl delegáta malá metoda, je běžné použít syntaxi [výrazu lambda](language-reference/operators/lambda-expressions.md) k provedení přiřazení:</span><span class="sxs-lookup"><span data-stu-id="972b0-152">In uses where the method being used as a delegate target is a small method, it's common to use [lambda expression](language-reference/operators/lambda-expressions.md) syntax to perform the assignment:</span></span>

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

<span data-ttu-id="972b0-153">Použití výrazů lambda pro cíle delegátů je podrobněji popsáno v [pozdější části](delegates-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="972b0-153">Using lambda expressions for delegate targets is covered more in a [later section](delegates-patterns.md).</span></span>

<span data-ttu-id="972b0-154">Příklad řazení () obvykle k delegátovi připojí jedinou cílovou metodu.</span><span class="sxs-lookup"><span data-stu-id="972b0-154">The Sort() example typically attaches a single target method to the delegate.</span></span> <span data-ttu-id="972b0-155">Nicméně objekty delegáta podporují seznamy vyvolání s více cílovými metodami připojenými k objektu delegáta.</span><span class="sxs-lookup"><span data-stu-id="972b0-155">However, delegate objects do support invocation lists that have multiple target methods attached to a delegate object.</span></span>

## <a name="delegate-and-multicastdelegate-classes"></a><span data-ttu-id="972b0-156">Třídy Delegate a MulticastDelegate</span><span class="sxs-lookup"><span data-stu-id="972b0-156">Delegate and MulticastDelegate classes</span></span>

<span data-ttu-id="972b0-157">Výše popsaná jazyková podpora poskytuje funkce a podporu, které obvykle budete potřebovat pro práci s delegáty.</span><span class="sxs-lookup"><span data-stu-id="972b0-157">The language support described above provides the features and support you'll typically need to work with delegates.</span></span> <span data-ttu-id="972b0-158">Tyto funkce jsou postavené na dvou třídách v rozhraní .NET Core Framework: <xref:System.Delegate> a <xref:System.MulticastDelegate> .</span><span class="sxs-lookup"><span data-stu-id="972b0-158">These features are built on two classes in the .NET Core framework: <xref:System.Delegate> and <xref:System.MulticastDelegate>.</span></span>

<span data-ttu-id="972b0-159">`System.Delegate`Třída a její jedna přímá podtřída, `System.MulticastDelegate` ,, poskytují podporu rozhraní pro vytváření delegátů, registraci metod jako cíle delegátů a vyvolání všech metod, které jsou registrovány jako cíl delegáta.</span><span class="sxs-lookup"><span data-stu-id="972b0-159">The `System.Delegate` class and its single direct subclass, `System.MulticastDelegate`, provide the framework support for creating delegates, registering methods as delegate targets, and invoking all methods that are registered as a delegate target.</span></span>

<span data-ttu-id="972b0-160">V zájmech se `System.Delegate` `System.MulticastDelegate` třídy a nesamy samy o delegované typy.</span><span class="sxs-lookup"><span data-stu-id="972b0-160">Interestingly, the `System.Delegate` and `System.MulticastDelegate` classes are not themselves delegate types.</span></span> <span data-ttu-id="972b0-161">Poskytují základ pro všechny konkrétní typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="972b0-161">They do provide the basis for all specific delegate types.</span></span> <span data-ttu-id="972b0-162">Stejný proces návrhu v rámci tohoto jazyka má pověření, že nelze deklarovat třídu, která je odvozena z `Delegate` nebo `MulticastDelegate` .</span><span class="sxs-lookup"><span data-stu-id="972b0-162">That same language design process mandated that you cannot declare a class that derives from `Delegate` or `MulticastDelegate`.</span></span> <span data-ttu-id="972b0-163">Pravidla jazyka C# je zakazují.</span><span class="sxs-lookup"><span data-stu-id="972b0-163">The C# language rules prohibit it.</span></span>

<span data-ttu-id="972b0-164">Namísto toho kompilátor jazyka C# vytvoří instance třídy odvozené z `MulticastDelegate` při použití klíčového slova jazyka c# k deklaraci typů delegátů.</span><span class="sxs-lookup"><span data-stu-id="972b0-164">Instead, the C# compiler creates instances of a class derived from `MulticastDelegate` when you use the C# language keyword to declare delegate types.</span></span>

<span data-ttu-id="972b0-165">Tento návrh má své kořeny v první verzi C# a .NET.</span><span class="sxs-lookup"><span data-stu-id="972b0-165">This design has its roots in the first release of C# and .NET.</span></span> <span data-ttu-id="972b0-166">Jedním z cílů pro návrhového týmu bylo zajistit, aby při použití delegátů byl vynutilný bezpečnost typu.</span><span class="sxs-lookup"><span data-stu-id="972b0-166">One goal for the design team was to ensure that the language enforced type safety when using delegates.</span></span> <span data-ttu-id="972b0-167">Což znamenalo, že Delegáti byli vyvoláni se správným typem a počtem argumentů.</span><span class="sxs-lookup"><span data-stu-id="972b0-167">That meant ensuring that delegates were invoked with the right type and number of arguments.</span></span> <span data-ttu-id="972b0-168">A že libovolný návratový typ byl správně uveden v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="972b0-168">And, that any return type was correctly indicated at compile time.</span></span> <span data-ttu-id="972b0-169">Delegáti byli součástí verze 1,0 .NET, která byla před obecnými typy.</span><span class="sxs-lookup"><span data-stu-id="972b0-169">Delegates were part of the 1.0 .NET release, which was before generics.</span></span>

<span data-ttu-id="972b0-170">Nejlepším způsobem, jak vyhovět této bezpečnosti typu, bylo, že kompilátor vytvoří konkrétní třídy delegátů, které představují použitou signaturu metody.</span><span class="sxs-lookup"><span data-stu-id="972b0-170">The best way to enforce this type safety was for the compiler to create the concrete delegate classes that represented the method signature being used.</span></span>

<span data-ttu-id="972b0-171">I když nemůžete vytvořit odvozené třídy přímo, budete používat metody definované na těchto třídách.</span><span class="sxs-lookup"><span data-stu-id="972b0-171">Even though you cannot create derived classes directly, you will use the methods defined on these classes.</span></span> <span data-ttu-id="972b0-172">Pojďme si projít nejběžnějšími metodami, které budete používat při práci s delegáty.</span><span class="sxs-lookup"><span data-stu-id="972b0-172">Let's go through the most common methods that you will use when you work with delegates.</span></span>

<span data-ttu-id="972b0-173">První, nejdůležitější fakt, jak si pamatovat, je, že každý delegát, se kterým pracujete, je odvozen od `MulticastDelegate` .</span><span class="sxs-lookup"><span data-stu-id="972b0-173">The first, most important fact to remember is that every delegate you work with is derived from `MulticastDelegate`.</span></span> <span data-ttu-id="972b0-174">Delegát vícesměrového vysílání znamená, že při volání prostřednictvím delegáta lze vyvolat více než jeden cíl metody.</span><span class="sxs-lookup"><span data-stu-id="972b0-174">A multicast delegate means that more than one method target can be invoked when invoking through a delegate.</span></span> <span data-ttu-id="972b0-175">Původní návrh se považuje za způsobující rozdíl mezi delegáty, kde lze připojit a vyvolat pouze jednu cílovou metodu, a delegáti, kde lze připojit a vyvolat více cílových metod.</span><span class="sxs-lookup"><span data-stu-id="972b0-175">The original design considered making a distinction between delegates where only one target method could be attached and invoked, and delegates where multiple target methods could be attached and invoked.</span></span> <span data-ttu-id="972b0-176">Toto rozlišení se ukázalo jako méně užitečné v praxi, než jsme původně mysleli.</span><span class="sxs-lookup"><span data-stu-id="972b0-176">That distinction proved to be less useful in practice than originally thought.</span></span> <span data-ttu-id="972b0-177">Dvě různé třídy již byly vytvořeny a byly v rozhraní od počáteční veřejné verze.</span><span class="sxs-lookup"><span data-stu-id="972b0-177">The two different classes were already created, and have been in the framework since its initial public release.</span></span>

<span data-ttu-id="972b0-178">Metody, které použijete nejvíce s delegáty, jsou `Invoke()` a `BeginInvoke()`  /  `EndInvoke()` .</span><span class="sxs-lookup"><span data-stu-id="972b0-178">The methods that you will use the most with delegates are `Invoke()` and `BeginInvoke()` / `EndInvoke()`.</span></span> <span data-ttu-id="972b0-179">`Invoke()`vyvolá všechny metody, které byly připojeny ke konkrétní instanci delegáta.</span><span class="sxs-lookup"><span data-stu-id="972b0-179">`Invoke()` will invoke all the methods that have been attached to a particular delegate instance.</span></span> <span data-ttu-id="972b0-180">Jak jste viděli výše, obvykle vyvoláte delegáty pomocí syntaxe volání metody v proměnné Delegate.</span><span class="sxs-lookup"><span data-stu-id="972b0-180">As you saw above, you typically invoke delegates using the method call syntax on the delegate variable.</span></span> <span data-ttu-id="972b0-181">Jak vidíte [později v této sérii](delegates-patterns.md), existují vzory, které pracují přímo s těmito metodami.</span><span class="sxs-lookup"><span data-stu-id="972b0-181">As you'll see [later in this series](delegates-patterns.md), there are patterns that work directly with these methods.</span></span>

<span data-ttu-id="972b0-182">Teď, když jste viděli syntaxi jazyka a třídy, které podporují delegáty, Podívejme se, jak se používají Delegáti silného typu, vytvoří se a vyvolají.</span><span class="sxs-lookup"><span data-stu-id="972b0-182">Now that you've seen the language syntax and the classes that support delegates, let's examine how strongly typed delegates are used, created, and invoked.</span></span>

[<span data-ttu-id="972b0-183">Další</span><span class="sxs-lookup"><span data-stu-id="972b0-183">Next</span></span>](delegates-strongly-typed.md)
