---
title: System.Delegate a `delegate` – klíčové slovo
description: Další informace o třídách v rozhraní .NET Framework, které podporují delegáty a jak jsou mapovány – klíčové slovo 'delegáta'.
ms.date: 06/20/2016
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 4cf2b113fc9e2c6621f648af7ecb272a42b1f056
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646706"
---
# <a name="systemdelegate-and-the-delegate-keyword"></a><span data-ttu-id="17610-103">System.Delegate a `delegate` – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="17610-103">System.Delegate and the `delegate` keyword</span></span>

[<span data-ttu-id="17610-104">Předchozí</span><span class="sxs-lookup"><span data-stu-id="17610-104">Previous</span></span>](delegates-overview.md)

<span data-ttu-id="17610-105">Tento článek se zabývá třídy v rozhraní .NET framework, které podporují delegáty a jak jsou mapovány `delegate` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="17610-105">This article will cover the classes in the .NET framework that support delegates, and how those map to the `delegate` keyword.</span></span>

## <a name="defining-delegate-types"></a><span data-ttu-id="17610-106">Definování typů delegátů.</span><span class="sxs-lookup"><span data-stu-id="17610-106">Defining Delegate Types</span></span>

<span data-ttu-id="17610-107">Začněme s klíčovým slovem 'delegáta', protože, který se primárně se používá při práci s delegátů.</span><span class="sxs-lookup"><span data-stu-id="17610-107">Let's start with the 'delegate' keyword, because that's primarily what you will use as you work with delegates.</span></span> <span data-ttu-id="17610-108">Kód, který kompilátor generuje při použití `delegate` – klíčové slovo bude mapovat na volání metody, které vyvolají členy <xref:System.Delegate> a <xref:System.MulticastDelegate> třídy.</span><span class="sxs-lookup"><span data-stu-id="17610-108">The code that the compiler generates when you use the `delegate` keyword will map to method calls that invoke members of the <xref:System.Delegate> and <xref:System.MulticastDelegate> classes.</span></span> 

<span data-ttu-id="17610-109">Můžete definovat delegáta typu pomocí syntaxe, která se podobá definuje podpis metody.</span><span class="sxs-lookup"><span data-stu-id="17610-109">You define a delegate type using syntax that is similar to defining a method signature.</span></span> <span data-ttu-id="17610-110">Stačí přidat `delegate` – klíčové slovo k definici.</span><span class="sxs-lookup"><span data-stu-id="17610-110">You just add the `delegate` keyword to the definition.</span></span>

<span data-ttu-id="17610-111">Můžeme dál používat metodu List.Sort() jako náš příklad.</span><span class="sxs-lookup"><span data-stu-id="17610-111">Let's continue to use the List.Sort() method as our example.</span></span> <span data-ttu-id="17610-112">Prvním krokem je vytvoření typu pro porovnání delegáta:</span><span class="sxs-lookup"><span data-stu-id="17610-112">The first step is to create a type for the comparison delegate:</span></span>

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

<span data-ttu-id="17610-113">Kompilátor vygeneruje třídu odvozenou z `System.Delegate` , která odpovídá podpisu použít (v tomto případě metodu, která vrátí celé číslo a má dva argumenty).</span><span class="sxs-lookup"><span data-stu-id="17610-113">The compiler generates a class, derived from `System.Delegate` that matches the signature used (in this case, a method that returns an integer, and has two arguments).</span></span> <span data-ttu-id="17610-114">Je typ delegátu `Comparison`.</span><span class="sxs-lookup"><span data-stu-id="17610-114">The type of that delegate is `Comparison`.</span></span> <span data-ttu-id="17610-115">`Comparison` Obecný typ je typ delegátu.</span><span class="sxs-lookup"><span data-stu-id="17610-115">The `Comparison` delegate type is a generic type.</span></span> <span data-ttu-id="17610-116">Viz podrobnosti o obecných typů [tady](generics.md).</span><span class="sxs-lookup"><span data-stu-id="17610-116">For details on generics see [here](generics.md).</span></span>

<span data-ttu-id="17610-117">Všimněte si, že syntaxe může zdát, že to je deklarace proměnné, ale ve skutečnosti je deklarace *typ*.</span><span class="sxs-lookup"><span data-stu-id="17610-117">Notice that the syntax may appear as though it is declaring a variable, but it is actually declaring a *type*.</span></span> <span data-ttu-id="17610-118">Můžete definovat typy delegátů uvnitř třídy, přímo v oborech názvů, nebo dokonce i v globálním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="17610-118">You can define delegate types inside classes, directly inside namespaces, or even in the global namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="17610-119">Deklarace delegáta typy (nebo jiné typy) přímo v globálním oboru názvů se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="17610-119">Declaring delegate types (or other types) directly in the global namespace is not recommended.</span></span> 

<span data-ttu-id="17610-120">Kompilátor generuje také přidávat a odebírat obslužné rutiny pro tento nový typ tak, aby klienti této třídy můžete přidávat a odebírat metody ze seznamu vyvolání instance.</span><span class="sxs-lookup"><span data-stu-id="17610-120">The compiler also generates add and remove handlers for this new type so that clients of this class can add and remove methods from an instance's invocation list.</span></span> <span data-ttu-id="17610-121">Kompilátor vynutí, že podpis metody přidávání nebo odebírání odpovídá podpisu použít při deklaraci metody.</span><span class="sxs-lookup"><span data-stu-id="17610-121">The compiler will enforce that the signature of the method being added or removed matches the signature used when declaring the method.</span></span> 

## <a name="declaring-instances-of-delegates"></a><span data-ttu-id="17610-122">Deklarování instance delegátů</span><span class="sxs-lookup"><span data-stu-id="17610-122">Declaring instances of delegates</span></span>

<span data-ttu-id="17610-123">Po definování delegáta, můžete vytvořit instanci tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="17610-123">After defining the delegate, you can create an instance of that type.</span></span>
<span data-ttu-id="17610-124">Všechny proměnné v, jako jsou C#, nelze deklarovat delegáta instance přímo v oboru názvů nebo v globálním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="17610-124">Like all variables in C#, you cannot declare delegate instances directly in a namespace, or in the global namespace.</span></span>

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

<span data-ttu-id="17610-125">Typ proměnné je `Comparison<T>`, typ delegáta definovali dříve.</span><span class="sxs-lookup"><span data-stu-id="17610-125">The type of the variable is `Comparison<T>`, the delegate type defined earlier.</span></span> <span data-ttu-id="17610-126">Název proměnné je `comparator`.</span><span class="sxs-lookup"><span data-stu-id="17610-126">The name of the variable is `comparator`.</span></span>
 
 <span data-ttu-id="17610-127">Tento fragment kódu nad deklaraci členské proměnné uvnitř třídy.</span><span class="sxs-lookup"><span data-stu-id="17610-127">That code snippet above declared a member variable inside a class.</span></span> <span data-ttu-id="17610-128">Můžete také deklarovat delegáta proměnné, které jsou lokálních proměnných nebo argumentů metody.</span><span class="sxs-lookup"><span data-stu-id="17610-128">You can also declare delegate variables that are local variables, or arguments to methods.</span></span>

## <a name="invoking-delegates"></a><span data-ttu-id="17610-129">Vyvolání delegátů</span><span class="sxs-lookup"><span data-stu-id="17610-129">Invoking Delegates</span></span>

<span data-ttu-id="17610-130">Vyvolání metody, které jsou v seznamu vyvolání delegátu po zavolání tohoto delegátu.</span><span class="sxs-lookup"><span data-stu-id="17610-130">You invoke the methods that are in the invocation list of a delegate by calling that delegate.</span></span> <span data-ttu-id="17610-131">Uvnitř `Sort()` metoda, kód bude volat metodu porovnání k určení pořadí umístit objekty:</span><span class="sxs-lookup"><span data-stu-id="17610-131">Inside the `Sort()` method, the code will call the comparison method to determine which order to place objects:</span></span>

```csharp
int result = comparator(left, right);
```

<span data-ttu-id="17610-132">V řádku nad kódem *vyvolá* metodu připojené k delegátu.</span><span class="sxs-lookup"><span data-stu-id="17610-132">In the line above, the code *invokes* the method attached to the delegate.</span></span>
<span data-ttu-id="17610-133">Proměnnou považovat za název metody a vyvolat pomocí syntaxe pro volání normální metody.</span><span class="sxs-lookup"><span data-stu-id="17610-133">You treat the variable as a method name, and invoke it using normal method call syntax.</span></span>

<span data-ttu-id="17610-134">Tento řádek kódu vytvoří nebezpečné předpokladů: Není zaručeno, že cíl je přidaný do delegáta.</span><span class="sxs-lookup"><span data-stu-id="17610-134">That line of code makes an unsafe assumption: There's no guarantee that a target has been added to the delegate.</span></span> <span data-ttu-id="17610-135">Pokud byly připojeny žádné cíle, by způsobit, že řádek výše `NullReferenceException` vyvolání.</span><span class="sxs-lookup"><span data-stu-id="17610-135">If no targets have been attached, the line above would cause a `NullReferenceException` to be thrown.</span></span> <span data-ttu-id="17610-136">Idiomy použít k vyřešení tohoto problému jsou složitější než jednoduchého vyhledání null a jsou popsané dále v tomto [řady](delegates-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="17610-136">The idioms used to address this problem are more complicated than a simple null-check, and are covered later in this [series](delegates-patterns.md).</span></span>

## <a name="assigning-adding-and-removing-invocation-targets"></a><span data-ttu-id="17610-137">Přiřazení, přidávání a odebírání cílů vyvolání</span><span class="sxs-lookup"><span data-stu-id="17610-137">Assigning, Adding and removing Invocation Targets</span></span>

<span data-ttu-id="17610-138">To je, jak je definován typ delegáta a jak deklarovat a vyvolání delegáta instance.</span><span class="sxs-lookup"><span data-stu-id="17610-138">That's how a delegate type is defined, and how delegate instances are declared and invoked.</span></span>

<span data-ttu-id="17610-139">Vývojáři, kteří mají používat `List.Sort()` metoda muset definovat metodu, jejíž podpis odpovídá definici typu delegáta a přiřaďte ho ke delegát používá metodu řazení.</span><span class="sxs-lookup"><span data-stu-id="17610-139">Developers that want to use the `List.Sort()` method need to define a method whose signature matches the delegate type definition, and assign it to the delegate used by the sort method.</span></span> <span data-ttu-id="17610-140">Toto přiřazení přidá metodu do seznamu vyvolání tohoto delegáta objektu.</span><span class="sxs-lookup"><span data-stu-id="17610-140">This assignment adds the method to the invocation list of that delegate object.</span></span>

<span data-ttu-id="17610-141">Předpokládejme, že chcete seřadit řetězce podle jejich délky.</span><span class="sxs-lookup"><span data-stu-id="17610-141">Suppose you wanted to sort a list of strings by their length.</span></span> <span data-ttu-id="17610-142">Funkce porovnání může být následující:</span><span class="sxs-lookup"><span data-stu-id="17610-142">Your comparison function might be the following:</span></span>

```csharp
private static int CompareLength(string left, string right) =>
    left.Length.CompareTo(right.Length);
```

<span data-ttu-id="17610-143">Metoda je deklarován jako privátní metodu.</span><span class="sxs-lookup"><span data-stu-id="17610-143">The method is declared as a private method.</span></span> <span data-ttu-id="17610-144">To je v pořádku.</span><span class="sxs-lookup"><span data-stu-id="17610-144">That's fine.</span></span> <span data-ttu-id="17610-145">Možná nebudete chtít tuto metodu za účelem být součástí veřejného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="17610-145">You may not want this method to be part of your public interface.</span></span> <span data-ttu-id="17610-146">Může být stále použit jako metodu porovnání při připojení k delegáta.</span><span class="sxs-lookup"><span data-stu-id="17610-146">It can still be used as the comparison method when attached to a delegate.</span></span> <span data-ttu-id="17610-147">Volající kód bude mít tato metoda připojen k seznamu cílové objektů delegáta a k němu přístup prostřednictvím tohoto delegátu.</span><span class="sxs-lookup"><span data-stu-id="17610-147">The calling code will have this method attached to the target list of the delegate object, and can access it through that delegate.</span></span>

<span data-ttu-id="17610-148">Vytvořte vztah předáním této metody `List.Sort()` metody:</span><span class="sxs-lookup"><span data-stu-id="17610-148">You create that relationship by passing that method to the `List.Sort()` method:</span></span>

```csharp
phrases.Sort(CompareLength);
```

<span data-ttu-id="17610-149">Všimněte si, že název metody, který se používá, bez závorek.</span><span class="sxs-lookup"><span data-stu-id="17610-149">Notice that the method name is used, without parentheses.</span></span> <span data-ttu-id="17610-150">Pomocí metody jako argument instruuje kompilátor, aby metoda odkaz převést na odkaz, který lze použít jako cíl vyvolání delegáta a připojit jako cíl volání metody.</span><span class="sxs-lookup"><span data-stu-id="17610-150">Using the method as an argument tells the compiler to convert the method reference into a reference that can be used as a delegate invocation target, and attach that method as an invocation target.</span></span>

<span data-ttu-id="17610-151">Může také byli jste explicitní deklarováním proměnné typu `Comparison<string>` a provádění přiřazení:</span><span class="sxs-lookup"><span data-stu-id="17610-151">You could also have been explicit by declaring a variable of type `Comparison<string>` and doing an assignment:</span></span>

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

<span data-ttu-id="17610-152">Při využití, ve kterém metoda používá jako cíl delegáta je malý metoda, je běžné použití [výraz lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md) syntaxe provést přiřazení:</span><span class="sxs-lookup"><span data-stu-id="17610-152">In uses where the method being used as a delegate target is a small method, it's common to use [lambda expression](./programming-guide/statements-expressions-operators/lambda-expressions.md) syntax to perform the assignment:</span></span>

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

<span data-ttu-id="17610-153">Použití výrazů lambda pro cíle delegáta je věnují více [později části](delegates-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="17610-153">Using lambda expressions for delegate targets is covered more in a [later section](delegates-patterns.md).</span></span>

<span data-ttu-id="17610-154">Příklad Sort() se obvykle připojuje jedné cílové metody delegáta.</span><span class="sxs-lookup"><span data-stu-id="17610-154">The Sort() example typically attaches a single target method to the delegate.</span></span> <span data-ttu-id="17610-155">Delegáta objekty však nepodporují vyvolání seznamy, které mají více cílové metody připojen k objektu delegáta.</span><span class="sxs-lookup"><span data-stu-id="17610-155">However, delegate objects do support invocation lists that have multiple target methods attached to a delegate object.</span></span>

## <a name="delegate-and-multicastdelegate-classes"></a><span data-ttu-id="17610-156">Třídy delegáta a MulticastDelegate, nebude</span><span class="sxs-lookup"><span data-stu-id="17610-156">Delegate and MulticastDelegate classes</span></span>

<span data-ttu-id="17610-157">Podpora jazyků je popsáno výše poskytuje funkce a podporu, kterou budete obvykle potřebovat pro práci s delegátů.</span><span class="sxs-lookup"><span data-stu-id="17610-157">The language support described above provides the features and support you'll typically need to work with delegates.</span></span> <span data-ttu-id="17610-158">Tyto funkce jsou postavené na dvě třídy v rozhraní .NET Core: <xref:System.Delegate> a <xref:System.MulticastDelegate>.</span><span class="sxs-lookup"><span data-stu-id="17610-158">These features are built on two classes in the .NET Core framework: <xref:System.Delegate> and <xref:System.MulticastDelegate>.</span></span>

<span data-ttu-id="17610-159">`System.Delegate` Třídy a jednu třídu s přímým přístupem dílčí `System.MulticastDelegate`, poskytují podporu rozhraní pro vytváření delegátů, registrace metody jako delegát cíle a vyvolání všechny metody, které jsou registrovány jako cíl delegáta.</span><span class="sxs-lookup"><span data-stu-id="17610-159">The `System.Delegate` class, and its single direct sub-class, `System.MulticastDelegate`, provide the framework support for creating delegates, registering methods as delegate targets, and invoking all methods that are registered as a delegate target.</span></span> 

<span data-ttu-id="17610-160">Zajímavé `System.Delegate` a `System.MulticastDelegate` třídy nejsou sami typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="17610-160">Interestingly, the `System.Delegate` and `System.MulticastDelegate` classes are not themselves delegate types.</span></span> <span data-ttu-id="17610-161">Poskytují základ pro všemi typy delegátů konkrétní.</span><span class="sxs-lookup"><span data-stu-id="17610-161">They do provide the basis for all specific delegate types.</span></span> <span data-ttu-id="17610-162">Že stejný jazyk návrhu procesu přidělených, nelze deklarovat třídu, která je odvozena z `Delegate` nebo `MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="17610-162">That same language design process mandated that you cannot declare a class that derives from `Delegate` or `MulticastDelegate`.</span></span> <span data-ttu-id="17610-163">C# Jazykových pravidel zakázat.</span><span class="sxs-lookup"><span data-stu-id="17610-163">The C# language rules prohibit it.</span></span>
 
<span data-ttu-id="17610-164">Místo toho C# kompilátor vytvoří instance třídy odvozené od `MulticastDelegate` při použití C# klíčové slovo jazyka, chcete-li deklarovat typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="17610-164">Instead, the C# compiler creates instances of a class derived from `MulticastDelegate` when you use the C# language keyword to declare delegate types.</span></span>

<span data-ttu-id="17610-165">Tento návrh byl jeho kořenové adresáře v první verzi C# a .NET.</span><span class="sxs-lookup"><span data-stu-id="17610-165">This design has its roots in the first release of C# and .NET.</span></span> <span data-ttu-id="17610-166">Jedním z cílů týmu návrhu se zajistit, že jazyk vynucuje bezpečnost typů, při použití delegátů.</span><span class="sxs-lookup"><span data-stu-id="17610-166">One goal for the design team was to ensure that the language enforced type safety when using delegates.</span></span> <span data-ttu-id="17610-167">To znamenalo, zajištění, že s správný typ a počet argumentů, které se vyvolaly delegátů.</span><span class="sxs-lookup"><span data-stu-id="17610-167">That meant ensuring that delegates were invoked with the right type and number of arguments.</span></span> <span data-ttu-id="17610-168">A že jakýkoli návratový typ se správně uvedeném v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="17610-168">And, that any return type was correctly indicated at compile time.</span></span> <span data-ttu-id="17610-169">Delegáti byly součástí verzi 1.0 rozhraní .NET, která byla před obecných typů.</span><span class="sxs-lookup"><span data-stu-id="17610-169">Delegates were part of the 1.0 .NET release, which was before generics.</span></span>

<span data-ttu-id="17610-170">Nejlepší způsob, jak vynucovat bezpečnostní tento typ byl pro kompilátor vytvoří konkrétní delegát třídy, které jsou reprezentovány podpis metody se používají.</span><span class="sxs-lookup"><span data-stu-id="17610-170">The best way to enforce this type safety was for the compiler to create the concrete delegate classes that represented the method signature being used.</span></span>

<span data-ttu-id="17610-171">I když odvozené třídy nelze vytvořit přímo, použijete metody definované v těchto tříd.</span><span class="sxs-lookup"><span data-stu-id="17610-171">Even though you cannot create derived classes directly, you will use the methods defined on these classes.</span></span> <span data-ttu-id="17610-172">Podívejme se nejčastěji používané metody, které budete používat při práci s delegátů.</span><span class="sxs-lookup"><span data-stu-id="17610-172">Let's go through the most common methods that you will use when you work with delegates.</span></span>

<span data-ttu-id="17610-173">Je první a nejdůležitější skutečnost na paměti, že každý delegát při práci s je odvozen z `MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="17610-173">The first, most important fact to remember is that every delegate you work with is derived from `MulticastDelegate`.</span></span> <span data-ttu-id="17610-174">Delegát vícesměrového vysílání znamená, že více než jeden cíl metoda může být vyvolána při volání prostřednictvím delegáta.</span><span class="sxs-lookup"><span data-stu-id="17610-174">A multicast delegate means that more than one method target can be invoked when invoking through a delegate.</span></span> <span data-ttu-id="17610-175">Původní návrh považovat za rozlišovat delegáty, kde může připojené a vyvolala metodu pouze jeden cíl a delegáty, kde může připojit a vyvolána více cílové metody.</span><span class="sxs-lookup"><span data-stu-id="17610-175">The original design considered making a distinction between delegates where only one target method could be attached and invoked, and delegates where multiple target methods could be attached and invoked.</span></span> <span data-ttu-id="17610-176">Tento rozdíl dokázaly méně užitečné v praxi, než se původně mluvit.</span><span class="sxs-lookup"><span data-stu-id="17610-176">That distinction proved to be less useful in practice than originally thought.</span></span> <span data-ttu-id="17610-177">Dvě různé třídy již byly vytvořeny a byly v rámci od its vitial release veřejné.</span><span class="sxs-lookup"><span data-stu-id="17610-177">The two different classes were already created, and have been in the framework since its initial public release.</span></span>

<span data-ttu-id="17610-178">Metody, které budou používat na maximum pomocí delegátů jsou `Invoke()` a `BeginInvoke()`  /  `EndInvoke()`.</span><span class="sxs-lookup"><span data-stu-id="17610-178">The methods that you will use the most with delegates are `Invoke()` and `BeginInvoke()` / `EndInvoke()`.</span></span> <span data-ttu-id="17610-179">`Invoke()` všechny metody, které byly připojeny k instanci konkrétního delegáta vyvolá.</span><span class="sxs-lookup"><span data-stu-id="17610-179">`Invoke()` will invoke all the methods that have been attached to a particular delegate instance.</span></span> <span data-ttu-id="17610-180">Jak už jste viděli výše, je obvykle vyvoláte pomocí syntaxe volání metody delegáta proměnné.</span><span class="sxs-lookup"><span data-stu-id="17610-180">As you saw above, you typically invoke delegates using the method call syntax on the delegate variable.</span></span> <span data-ttu-id="17610-181">Jak uvidíte [dále v této sérii](delegates-patterns.md), jsou vzorce, které pracují přímo s těmito metodami.</span><span class="sxs-lookup"><span data-stu-id="17610-181">As you'll see [later in this series](delegates-patterns.md), there are patterns that work directly with these methods.</span></span>

<span data-ttu-id="17610-182">Teď, když už víte, syntaxe jazyka a tříd, které podporují delegáty, Pojďme prozkoumat, jak se silnými typy delegátů jsou používány, vytvořena a vyvolána.</span><span class="sxs-lookup"><span data-stu-id="17610-182">Now that you've seen the language syntax and the classes that support delegates, let's examine how strongly typed delegates are used, created and invoked.</span></span>

[<span data-ttu-id="17610-183">Next</span><span class="sxs-lookup"><span data-stu-id="17610-183">Next</span></span>](delegates-strongly-typed.md)
