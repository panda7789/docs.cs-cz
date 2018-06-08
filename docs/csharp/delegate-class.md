---
title: System.Delegate a `delegate` – klíčové slovo
description: Další informace o třídách v rozhraní .NET Framework, které podporují Delegáti a ty mapování do – klíčové slovo 'delegovat'.
ms.date: 06/20/2016
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 39dca1053f87a5059bdc60f8b722091ba991cbd5
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827297"
---
# <a name="systemdelegate-and-the-delegate-keyword"></a><span data-ttu-id="2d85b-103">System.Delegate a `delegate` – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="2d85b-103">System.Delegate and the `delegate` keyword</span></span>

[<span data-ttu-id="2d85b-104">Předchozí</span><span class="sxs-lookup"><span data-stu-id="2d85b-104">Previous</span></span>](delegates-overview.md)

<span data-ttu-id="2d85b-105">Tento článek se zabývá třídy v rozhraní .NET framework, které podporují Delegáti a jak jsou mapovány `delegate` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="2d85b-105">This article will cover the classes in the .NET framework that support delegates, and how those map to the `delegate` keyword.</span></span>

## <a name="defining-delegate-types"></a><span data-ttu-id="2d85b-106">Definování typů delegátů.</span><span class="sxs-lookup"><span data-stu-id="2d85b-106">Defining Delegate Types</span></span>

<span data-ttu-id="2d85b-107">Začněme s klíčovým slovem 'delegovat', protože takové je primárně co budete používat při práci s delegáti.</span><span class="sxs-lookup"><span data-stu-id="2d85b-107">Let's start with the 'delegate' keyword, because that's primarily what you will use as you work with delegates.</span></span> <span data-ttu-id="2d85b-108">Kód, který kompilátor vygeneruje při použití `delegate` – klíčové slovo bude mapovat volání metod, které vyvolají členy <xref:System.Delegate> a <xref:System.MulticastDelegate> třídy.</span><span class="sxs-lookup"><span data-stu-id="2d85b-108">The code that the compiler generates when you use the `delegate` keyword will map to method calls that invoke members of the <xref:System.Delegate> and <xref:System.MulticastDelegate> classes.</span></span> 

<span data-ttu-id="2d85b-109">Definování typu delegáta pomocí syntaxe, který je podobný definování podpis metody.</span><span class="sxs-lookup"><span data-stu-id="2d85b-109">You define a delegate type using syntax that is similar to defining a method signature.</span></span> <span data-ttu-id="2d85b-110">Stačí přidat `delegate` – klíčové slovo k definici.</span><span class="sxs-lookup"><span data-stu-id="2d85b-110">You just add the `delegate` keyword to the definition.</span></span>

<span data-ttu-id="2d85b-111">Budeme nadále používat metodu List.Sort() jako našem příkladu.</span><span class="sxs-lookup"><span data-stu-id="2d85b-111">Let's continue to use the List.Sort() method as our example.</span></span> <span data-ttu-id="2d85b-112">Prvním krokem je vytvoření typu pro delegáta porovnání:</span><span class="sxs-lookup"><span data-stu-id="2d85b-112">The first step is to create a type for the comparison delegate:</span></span>

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

<span data-ttu-id="2d85b-113">Kompilátor vygeneruje třídy, odvozené od `System.Delegate` odpovídající podpis použít (v tomto případě metodu, která vrátí celé číslo a má dva argumenty).</span><span class="sxs-lookup"><span data-stu-id="2d85b-113">The compiler generates a class, derived from `System.Delegate` that matches the signature used (in this case, a method that returns an integer, and has two arguments).</span></span> <span data-ttu-id="2d85b-114">Typ tohoto delegáta je `Comparison`.</span><span class="sxs-lookup"><span data-stu-id="2d85b-114">The type of that delegate is `Comparison`.</span></span> <span data-ttu-id="2d85b-115">`Comparison` Typ delegáta je obecného typu.</span><span class="sxs-lookup"><span data-stu-id="2d85b-115">The `Comparison` delegate type is a generic type.</span></span> <span data-ttu-id="2d85b-116">Informace o obecných typů najdete v tématu [zde](generics.md).</span><span class="sxs-lookup"><span data-stu-id="2d85b-116">For details on generics see [here](generics.md).</span></span>

<span data-ttu-id="2d85b-117">Všimněte si, že syntaxe může zdát, že ho je deklarace proměnné, ale ve skutečnosti je deklarace *typu*.</span><span class="sxs-lookup"><span data-stu-id="2d85b-117">Notice that the syntax may appear as though it is declaring a variable, but it is actually declaring a *type*.</span></span> <span data-ttu-id="2d85b-118">Můžete definovat typů delegátů uvnitř třídy, přímo v obory názvů, nebo i v globálním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2d85b-118">You can define delegate types inside classes, directly inside namespaces, or even in the global namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="2d85b-119">Deklarování delegáta (nebo jiné typy) přímo v globálním oboru názvů se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="2d85b-119">Declaring delegate types (or other types) directly in the global namespace is not recommended.</span></span> 

<span data-ttu-id="2d85b-120">Kompilátor vytvoří také přidávat a odebírat obslužné rutiny pro tento nový typ tak, aby klienti této třídy můžete přidávat a odebírat metody instance pro vyvolání seznamu.</span><span class="sxs-lookup"><span data-stu-id="2d85b-120">The compiler also generates add and remove handlers for this new type so that clients of this class can add and remove methods from an instance's invocation list.</span></span> <span data-ttu-id="2d85b-121">Kompilátor vynutí, že podpis metody přidávání nebo odebírání odpovídá podpis použít při deklarování metodu.</span><span class="sxs-lookup"><span data-stu-id="2d85b-121">The compiler will enforce that the signature of the method being added or removed matches the signature used when declaring the method.</span></span> 

## <a name="declaring-instances-of-delegates"></a><span data-ttu-id="2d85b-122">Deklarování instancí delegáti</span><span class="sxs-lookup"><span data-stu-id="2d85b-122">Declaring instances of delegates</span></span>

<span data-ttu-id="2d85b-123">Po definování delegáta, můžete vytvořit instanci daného typu.</span><span class="sxs-lookup"><span data-stu-id="2d85b-123">After defining the delegate, you can create an instance of that type.</span></span>
<span data-ttu-id="2d85b-124">Podobně jako všechny proměnné v jazyce C# nelze deklarovat delegáta instance přímo v oboru názvů, nebo obor názvů globální.</span><span class="sxs-lookup"><span data-stu-id="2d85b-124">Like all variables in C#, you cannot declare delegate instances directly in a namespace, or in the global namespace.</span></span>

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

<span data-ttu-id="2d85b-125">Typ proměnné je `Comparison<T>`, typ delegáta definovaného dříve.</span><span class="sxs-lookup"><span data-stu-id="2d85b-125">The type of the variable is `Comparison<T>`, the delegate type defined earlier.</span></span> <span data-ttu-id="2d85b-126">Název proměnné je `comparator`.</span><span class="sxs-lookup"><span data-stu-id="2d85b-126">The name of the variable is `comparator`.</span></span>
 
 <span data-ttu-id="2d85b-127">Tento fragment kódu výše deklarovat členské proměnné uvnitř třídy.</span><span class="sxs-lookup"><span data-stu-id="2d85b-127">That code snippet above declared a member variable inside a class.</span></span> <span data-ttu-id="2d85b-128">Můžete také deklarovat delegáta proměnné, které jsou místní proměnné a argumenty do metod.</span><span class="sxs-lookup"><span data-stu-id="2d85b-128">You can also declare delegate variables that are local variables, or arguments to methods.</span></span>

## <a name="invoking-delegates"></a><span data-ttu-id="2d85b-129">Volajícím delegáti</span><span class="sxs-lookup"><span data-stu-id="2d85b-129">Invoking Delegates</span></span>

<span data-ttu-id="2d85b-130">Vyvolání metody, které jsou v seznamu vyvolání delegáta voláním tohoto delegáta.</span><span class="sxs-lookup"><span data-stu-id="2d85b-130">You invoke the methods that are in the invocation list of a delegate by calling that delegate.</span></span> <span data-ttu-id="2d85b-131">Uvnitř `Sort()` metoda, kód zavolá metodu porovnání k určení, které pořadí umístit objekty:</span><span class="sxs-lookup"><span data-stu-id="2d85b-131">Inside the `Sort()` method, the code will call the comparison method to determine which order to place objects:</span></span>

```csharp
int result = comparator(left, right);
```

<span data-ttu-id="2d85b-132">V řádku výše kód *vyvolá* metodu připojené k delegát.</span><span class="sxs-lookup"><span data-stu-id="2d85b-132">In the line above, the code *invokes* the method attached to the delegate.</span></span>
<span data-ttu-id="2d85b-133">Proměnná považovat za název metody a pomocí syntaxe volání normální metody vyvolání.</span><span class="sxs-lookup"><span data-stu-id="2d85b-133">You treat the variable as a method name, and invoke it using normal method call syntax.</span></span>

<span data-ttu-id="2d85b-134">Tohoto řádku kódu umožňuje unsafe předpokládá: není zaručeno, že cíl je přidaný do delegáta.</span><span class="sxs-lookup"><span data-stu-id="2d85b-134">That line of code makes an unsafe assumption: There's no guarantee that a target has been added to the delegate.</span></span> <span data-ttu-id="2d85b-135">Pokud byly připojeny žádné cíle, by způsobilo řádku výše `NullReferenceException` vyvolání.</span><span class="sxs-lookup"><span data-stu-id="2d85b-135">If no targets have been attached, the line above would cause a `NullReferenceException` to be thrown.</span></span> <span data-ttu-id="2d85b-136">Idioms k řešení tohoto problému se složitější než jednoduché zkontrolujte hodnotu null a jsou popsané později v tomto [řady](delegates-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="2d85b-136">The idioms used to address this problem are more complicated than a simple null-check, and are covered later in this [series](delegates-patterns.md).</span></span>

## <a name="assigning-adding-and-removing-invocation-targets"></a><span data-ttu-id="2d85b-137">Přiřazení, přidávání a odebírání cílů volání</span><span class="sxs-lookup"><span data-stu-id="2d85b-137">Assigning, Adding and removing Invocation Targets</span></span>

<span data-ttu-id="2d85b-138">To je, jak je definován typ delegáta a jak deklarovat a vyvolá delegáta instancí.</span><span class="sxs-lookup"><span data-stu-id="2d85b-138">That's how a delegate type is defined, and how delegate instances are declared and invoked.</span></span>

<span data-ttu-id="2d85b-139">Vývojáři, které chcete použít `List.Sort()` metoda muset definovat metoda, jejíž podpis odpovídá definici typu delegáta a přiřaďte ho ke delegát používá metodu řazení.</span><span class="sxs-lookup"><span data-stu-id="2d85b-139">Developers that want to use the `List.Sort()` method need to define a method whose signature matches the delegate type definition, and assign it to the delegate used by the sort method.</span></span> <span data-ttu-id="2d85b-140">Toto přiřazení přidá metodu do seznamu vyvolání tohoto delegáta objektu.</span><span class="sxs-lookup"><span data-stu-id="2d85b-140">This assignment adds the method to the invocation list of that delegate object.</span></span>

<span data-ttu-id="2d85b-141">Předpokládejme, že chcete seřadit jejich délka seznamu řetězců.</span><span class="sxs-lookup"><span data-stu-id="2d85b-141">Suppose you wanted to sort a list of strings by their length.</span></span> <span data-ttu-id="2d85b-142">Porovnání funkce může být následující:</span><span class="sxs-lookup"><span data-stu-id="2d85b-142">Your comparison function might be the following:</span></span>

```csharp
private static int CompareLength(string left, string right) =>
    left.Length.CompareTo(right.Length);
```

<span data-ttu-id="2d85b-143">Metoda je deklarován jako soukromá metoda.</span><span class="sxs-lookup"><span data-stu-id="2d85b-143">The method is declared as a private method.</span></span> <span data-ttu-id="2d85b-144">Není to.</span><span class="sxs-lookup"><span data-stu-id="2d85b-144">That's fine.</span></span> <span data-ttu-id="2d85b-145">Tato metoda se jednat o část veřejné rozhraní nemusí být žádoucí.</span><span class="sxs-lookup"><span data-stu-id="2d85b-145">You may not want this method to be part of your public interface.</span></span> <span data-ttu-id="2d85b-146">Můžete se pořád použít jako metodu porovnání po připojení k delegáta.</span><span class="sxs-lookup"><span data-stu-id="2d85b-146">It can still be used as the comparison method when attached to a delegate.</span></span> <span data-ttu-id="2d85b-147">Kód volání bude mít tato metoda připojen do cílového seznamu delegáta objektu a k dispozici prostřednictvím tohoto delegáta.</span><span class="sxs-lookup"><span data-stu-id="2d85b-147">The calling code will have this method attached to the target list of the delegate object, and can access it through that delegate.</span></span>

<span data-ttu-id="2d85b-148">Vytvoření relace pomocí dané metody k předání `List.Sort()` metoda:</span><span class="sxs-lookup"><span data-stu-id="2d85b-148">You create that relationship by passing that method to the `List.Sort()` method:</span></span>

```csharp
phrases.Sort(CompareLength);
```

<span data-ttu-id="2d85b-149">Všimněte si, že se používá název metody, bez závorek.</span><span class="sxs-lookup"><span data-stu-id="2d85b-149">Notice that the method name is used, without parentheses.</span></span> <span data-ttu-id="2d85b-150">Pomocí metody jako argument říká kompilátoru převést metoda odkaz na odkaz, který lze použít jako cíl vyvolání delegáta a připojte dané metody jako cíl volání.</span><span class="sxs-lookup"><span data-stu-id="2d85b-150">Using the method as an argument tells the compiler to convert the method reference into a reference that can be used as a delegate invocation target, and attach that method as an invocation target.</span></span>

<span data-ttu-id="2d85b-151">Může také jste explicitní deklarováním proměnné typu ' porovnání<string>' a provádění přiřazení:</span><span class="sxs-lookup"><span data-stu-id="2d85b-151">You could also have been explicit by declaring a variable of type 'Comparison<string>\` and doing an assignment:</span></span>

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

<span data-ttu-id="2d85b-152">V používá tam, kde metoda používá jako cíl delegáta je malý metoda, je běžné používat [výrazu Lambda](lambda-expressions.md) syntaxe provést přiřazení:</span><span class="sxs-lookup"><span data-stu-id="2d85b-152">In uses where the method being used as a delegate target is a small method, it's common to use [Lambda Expression](lambda-expressions.md) syntax to perform the assignment:</span></span>

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

<span data-ttu-id="2d85b-153">Použití výrazů Lambda pro delegáta cíle, najdete v článku více [později části](delegates-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="2d85b-153">Using Lambda Expressions for delegate targets is covered more in a [later section](delegates-patterns.md).</span></span>

<span data-ttu-id="2d85b-154">Metoda jedním cílem příklad Sort() obvykle připojuje k delegát.</span><span class="sxs-lookup"><span data-stu-id="2d85b-154">The Sort() example typically attaches a single target method to the delegate.</span></span> <span data-ttu-id="2d85b-155">Delegát objekty však podporují seznamy volání, které mají více cílové metody připojený k objektu delegáta.</span><span class="sxs-lookup"><span data-stu-id="2d85b-155">However, delegate objects do support invocation lists that have multiple target methods attached to a delegate object.</span></span>

## <a name="delegate-and-multicastdelegate-classes"></a><span data-ttu-id="2d85b-156">Delegát a MulticastDelegate, nebude třídy</span><span class="sxs-lookup"><span data-stu-id="2d85b-156">Delegate and MulticastDelegate classes</span></span>

<span data-ttu-id="2d85b-157">Podpora jazyků, které jsou popsané výše poskytuje funkce a podporu, které obvykle budete potřebovat pro práci s delegáti.</span><span class="sxs-lookup"><span data-stu-id="2d85b-157">The language support described above provides the features and support you'll typically need to work with delegates.</span></span> <span data-ttu-id="2d85b-158">Tyto funkce jsou postaveny na dvě třídy v rozhraní .NET Core: <xref:System.Delegate> a <xref:System.MulticastDelegate>.</span><span class="sxs-lookup"><span data-stu-id="2d85b-158">These features are built on two classes in the .NET Core framework: <xref:System.Delegate> and <xref:System.MulticastDelegate>.</span></span>

<span data-ttu-id="2d85b-159">`System.Delegate` Třídy a jednu třídu přímé dílčí `System.MulticastDelegate`, poskytovat podporu framework pro vytváření delegátů, registrace metody jako delegáta cíle a vyvolání všechny metody, které jsou registrovány jako cíl delegáta.</span><span class="sxs-lookup"><span data-stu-id="2d85b-159">The `System.Delegate` class, and its single direct sub-class, `System.MulticastDelegate`, provide the framework support for creating delegates, registering methods as delegate targets, and invoking all methods that are registered as a delegate target.</span></span> 

<span data-ttu-id="2d85b-160">Interestingly `System.Delegate` a `System.MulticastDelegate` třídy nejsou sami delegovat typy.</span><span class="sxs-lookup"><span data-stu-id="2d85b-160">Interestingly, the `System.Delegate` and `System.MulticastDelegate` classes are not themselves delegate types.</span></span> <span data-ttu-id="2d85b-161">Poskytují základ pro všechny typy konkrétní delegáta.</span><span class="sxs-lookup"><span data-stu-id="2d85b-161">They do provide the basis for all specific delegate types.</span></span> <span data-ttu-id="2d85b-162">Že stejné návrhu jazyka proces vyžadováno, aby nelze deklarovat třída odvozená z `Delegate` nebo `MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="2d85b-162">That same language design process mandated that you cannot declare a class that derives from `Delegate` or `MulticastDelegate`.</span></span> <span data-ttu-id="2d85b-163">Pravidla jazyka C# zakázat ho.</span><span class="sxs-lookup"><span data-stu-id="2d85b-163">The C# language rules prohibit it.</span></span>
 
<span data-ttu-id="2d85b-164">Místo toho kompilátor jazyka C# vytvoří instance třídy odvozené od `MulticastDelegate` při použití jazyka C# klíčové slovo jazyka typy delegáta deklarovat.</span><span class="sxs-lookup"><span data-stu-id="2d85b-164">Instead, the C# compiler creates instances of a class derived from `MulticastDelegate` when you use the C# language keyword to declare delegate types.</span></span>

<span data-ttu-id="2d85b-165">Tento návrh obsahuje jeho kořeny v první verzi jazyka C# a rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="2d85b-165">This design has its roots in the first release of C# and .NET.</span></span> <span data-ttu-id="2d85b-166">Jeden cíl pro týmem návrhu se zajistit, že jazyk vynutí bezpečnost typů, při použití delegátů.</span><span class="sxs-lookup"><span data-stu-id="2d85b-166">One goal for the design team was to ensure that the language enforced type safety when using delegates.</span></span> <span data-ttu-id="2d85b-167">Který určená, zajistíte, že delegáti byly spuštěny se správný typ a počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="2d85b-167">That meant ensuring that delegates were invoked with the right type and number of arguments.</span></span> <span data-ttu-id="2d85b-168">Doba kompilace a že žádný návratový typ, byl správně uvedeném v.</span><span class="sxs-lookup"><span data-stu-id="2d85b-168">And, that any return type was correctly indicated at compile time.</span></span> <span data-ttu-id="2d85b-169">Delegáti byly součástí verzi 1.0 rozhraní .NET, která byla před obecné typy.</span><span class="sxs-lookup"><span data-stu-id="2d85b-169">Delegates were part of the 1.0 .NET release, which was before generics.</span></span>

<span data-ttu-id="2d85b-170">Nejlepší způsob, jak vynutit zabezpečení tento typ byl kompilátor pro vytváření tříd, které reprezentované podpis metody používá konkrétní delegáta.</span><span class="sxs-lookup"><span data-stu-id="2d85b-170">The best way to enforce this type safety was for the compiler to create the concrete delegate classes that represented the method signature being used.</span></span>

<span data-ttu-id="2d85b-171">I když odvozené třídy nelze vytvořit přímo, budete používat metody definované na těchto třídách.</span><span class="sxs-lookup"><span data-stu-id="2d85b-171">Even though you cannot create derived classes directly, you will use the methods defined on these classes.</span></span> <span data-ttu-id="2d85b-172">Přejděte prostřednictvím většiny běžných metod, které budete používat při práci s delegáti.</span><span class="sxs-lookup"><span data-stu-id="2d85b-172">Let's go through the most common methods that you will use when you work with delegates.</span></span>

<span data-ttu-id="2d85b-173">První, nejdůležitější fakt zapamatujte si je, že každý delegáta pracujete s je odvozený od `MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="2d85b-173">The first, most important fact to remember is that every delegate you work with is derived from `MulticastDelegate`.</span></span> <span data-ttu-id="2d85b-174">Vícesměrového vysílání delegáta znamená, že více než jeden cíl metoda lze uplatnit při vyvolání prostřednictvím delegáta.</span><span class="sxs-lookup"><span data-stu-id="2d85b-174">A multicast delegate means that more than one method target can be invoked when invoking through a delegate.</span></span> <span data-ttu-id="2d85b-175">Původní návrh za mezi delegáti, kde může připojit a vyvolá metoda pouze jeden cíl a delegáti, kde může několik metod cílový připojit a vyvolá.</span><span class="sxs-lookup"><span data-stu-id="2d85b-175">The original design considered making a distinction between delegates where only one target method could be attached and invoked, and delegates where multiple target methods could be attached and invoked.</span></span> <span data-ttu-id="2d85b-176">Tento rozdíl ukázalo jako méně užitečné v praxi než původně představit.</span><span class="sxs-lookup"><span data-stu-id="2d85b-176">That distinction proved to be less useful in practice than originally thought.</span></span> <span data-ttu-id="2d85b-177">Dvěma různými třídami již byly vytvořeny a byly v rámci od prvního vydání veřejné.</span><span class="sxs-lookup"><span data-stu-id="2d85b-177">The two different classes were already created, and have been in the framework since its initial public release.</span></span>

<span data-ttu-id="2d85b-178">Metody, které budete používat nejvíce s delegáti `Invoke()` a `BeginInvoke()`  /  `EndInvoke()`.</span><span class="sxs-lookup"><span data-stu-id="2d85b-178">The methods that you will use the most with delegates are `Invoke()` and `BeginInvoke()` / `EndInvoke()`.</span></span> <span data-ttu-id="2d85b-179">`Invoke()` vyvolá všechny metody, které byly připojeny k instanci konkrétního delegáta.</span><span class="sxs-lookup"><span data-stu-id="2d85b-179">`Invoke()` will invoke all the methods that have been attached to a particular delegate instance.</span></span> <span data-ttu-id="2d85b-180">Jak už jste viděli výše, obvykle vyvolání delegáti pomocí syntaxe volání metody na proměnnou delegáta.</span><span class="sxs-lookup"><span data-stu-id="2d85b-180">As you saw above, you typically invoke delegates using the method call syntax on the delegate variable.</span></span> <span data-ttu-id="2d85b-181">Jak uvidíte [dál v této série](delegates-patterns.md), existují vzorů, které pracovat přímo s těchto metod.</span><span class="sxs-lookup"><span data-stu-id="2d85b-181">As you'll see [later in this series](delegates-patterns.md), there are patterns that work directly with these methods.</span></span>

<span data-ttu-id="2d85b-182">Teď, když jste se seznámili syntaxe jazyka a třídy, které podporují delegáti, Podívejme se na tom, jak silného typu delegáti se používají, vytvoření a volá.</span><span class="sxs-lookup"><span data-stu-id="2d85b-182">Now that you've seen the language syntax and the classes that support delegates, let's examine how strongly typed delegates are used, created and invoked.</span></span>

[<span data-ttu-id="2d85b-183">Next</span><span class="sxs-lookup"><span data-stu-id="2d85b-183">Next</span></span>](delegates-strongly-typed.md)
