---
title: LINQ (Language integrovaného dotazu)
description: Zjistěte, jak LINQ poskytuje funkce dotazování úroveň jazyka a rozhraní API jazyka C# a VB jako způsob, jak napsat kód výrazovou, deklarativní.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: c00939e1-59e3-4e61-8fe9-08ad6b3f1295
ms.openlocfilehash: 31b0a7b9e11d46e6453d9fcad87e7beadba9a1e3
ms.sourcegitcommit: 6c480773ae896f45af4671fb3e26611a50e4dd81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2018
ms.locfileid: "35251087"
---
# <a name="linq-language-integrated-query"></a><span data-ttu-id="113ed-103">LINQ (Language integrovaného dotazu)</span><span class="sxs-lookup"><span data-stu-id="113ed-103">LINQ (Language Integrated Query)</span></span>

## <a name="what-is-it"></a><span data-ttu-id="113ed-104">Co to je?</span><span class="sxs-lookup"><span data-stu-id="113ed-104">What is it?</span></span>

<span data-ttu-id="113ed-105">LINQ poskytuje funkce dotazování úroveň jazyka a [vyšší pořadí funkce](https://en.wikipedia.org/wiki/Higher-order_function) rozhraní API jazyka C# a VB jako způsob, jak napsat kód výrazovou, deklarativní.</span><span class="sxs-lookup"><span data-stu-id="113ed-105">LINQ provides language-level querying capabilities and a [higher-order function](https://en.wikipedia.org/wiki/Higher-order_function) API to C# and VB as a way to write expressive, declarative code.</span></span>

<span data-ttu-id="113ed-106">Syntaxe dotazu úroveň jazyka:</span><span class="sxs-lookup"><span data-stu-id="113ed-106">Language-level query syntax:</span></span>

```csharp
var linqExperts = from p in programmers
                  where p.IsNewToLINQ
                  select new LINQExpert(p);
```

<span data-ttu-id="113ed-107">Pomocí stejné příklad `IEnumerable<T>` rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="113ed-107">Same example using the `IEnumerable<T>` API:</span></span>

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

## <a name="linq-is-expressive"></a><span data-ttu-id="113ed-108">LINQ je Expressive</span><span class="sxs-lookup"><span data-stu-id="113ed-108">LINQ is Expressive</span></span>

<span data-ttu-id="113ed-109">Představte si máte seznam mazlíčků, ale chcete převést do slovníku umožňující přístup mazlíčky přímo pomocí jeho `RFID` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="113ed-109">Imagine you have a list of pets, but want to convert it into a dictionary where you can access a pet directly by its `RFID` value.</span></span>

<span data-ttu-id="113ed-110">Tradiční imperativní kód:</span><span class="sxs-lookup"><span data-stu-id="113ed-110">Traditional imperative code:</span></span>

```csharp
var petLookup = new Dictionary<int, Pet>();

foreach (var pet in pets)
{
    petLookup.Add(pet.RFID, pet);
}
```

<span data-ttu-id="113ed-111">Je záměrem za kód není pro vytvoření nového `Dictionary<int, Pet>` a přidejte do ní prostřednictvím smyčku, je pro převod existujícího seznamu do slovníku!</span><span class="sxs-lookup"><span data-stu-id="113ed-111">The intention behind the code is not to create a new `Dictionary<int, Pet>` and add to it via a loop, it is to convert an existing list into a dictionary!</span></span> <span data-ttu-id="113ed-112">LINQ zachovává záměrem, zatímco kód imperativní neexistuje.</span><span class="sxs-lookup"><span data-stu-id="113ed-112">LINQ preserves the intention whereas the imperative code does not.</span></span>

<span data-ttu-id="113ed-113">Ekvivalentní výrazu LINQ:</span><span class="sxs-lookup"><span data-stu-id="113ed-113">Equivalent LINQ expression:</span></span>

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

<span data-ttu-id="113ed-114">Kód pomocí LINQ se hodí v situaci, protože evens pole přehrávání mezi záměr a kódem, když důvody jako programátoři.</span><span class="sxs-lookup"><span data-stu-id="113ed-114">The code using LINQ is valuable because it evens the playing field between intent and code when reasoning as a programmer.</span></span> <span data-ttu-id="113ed-115">Další výhoda je jako stručný výtah kódu.</span><span class="sxs-lookup"><span data-stu-id="113ed-115">Another bonus is code brevity.</span></span> <span data-ttu-id="113ed-116">Představte si velké části codebase redukování 1/3 jako provést výše.</span><span class="sxs-lookup"><span data-stu-id="113ed-116">Imagine reducing large portions of a codebase by 1/3 as done above.</span></span> <span data-ttu-id="113ed-117">Poměrně sladké pozornosti, pravé?</span><span class="sxs-lookup"><span data-stu-id="113ed-117">Pretty sweet deal, right?</span></span>

## <a name="linq-providers-simplify-data-access"></a><span data-ttu-id="113ed-118">Zprostředkovatelé LINQ zjednodušit přístup k datům</span><span class="sxs-lookup"><span data-stu-id="113ed-118">LINQ Providers Simplify Data Access</span></span>

<span data-ttu-id="113ed-119">U významné bloku softwaru stanovené v zástupné vše, co se pohybuje kolem práci s daty z některé zdroje (databáze, JSON, XML atd.).</span><span class="sxs-lookup"><span data-stu-id="113ed-119">For a significant chunk of software out in the wild, everything revolves around dealing with data from some source (Databases, JSON, XML, etc).</span></span> <span data-ttu-id="113ed-120">Často to zahrnuje nové rozhraní API pro každý zdroj dat, což může být nepříjemných učení.</span><span class="sxs-lookup"><span data-stu-id="113ed-120">Often this involves learning a new API for each data source, which can be annoying.</span></span> <span data-ttu-id="113ed-121">Technologie LINQ to zjednodušuje tím, že poskytuje abstrakci společné prvky přístup k datům do syntaxe dotazu, který vypadá stejně bez ohledu na to, jaké zdroje dat vyberte.</span><span class="sxs-lookup"><span data-stu-id="113ed-121">LINQ simplifies this by abstracting common elements of data access into a query syntax which looks the same no matter which data source you pick.</span></span>

<span data-ttu-id="113ed-122">Vezměte v úvahu následující: vyhledání všech elementů XML s hodnotou určitým atributem.</span><span class="sxs-lookup"><span data-stu-id="113ed-122">Consider the following: finding all XML elements with a specific attribute value.</span></span>

```csharp
public static IEnumerable<XElement> FindAllElementsWithAttribute(XElement documentRoot, string elementName,
                                           string attributeName, string value)
{
    return from el in documentRoot.Elements(elementName)
           where (string)el.Element(attributeName) == value
           select el;
}
```

<span data-ttu-id="113ed-123">Psaní kódu ručně procházení v dokumentu XML k provedení této úlohy bude podstatně více náročné.</span><span class="sxs-lookup"><span data-stu-id="113ed-123">Writing code to manually traverse the XML document to perform this task would be far more challenging.</span></span>

<span data-ttu-id="113ed-124">Jediné, co můžete provést zprostředkovatelům LINQ interakci se souborem XML není.</span><span class="sxs-lookup"><span data-stu-id="113ed-124">Interacting with XML isn’t the only thing you can do with LINQ Providers.</span></span> <span data-ttu-id="113ed-125">[Technologie LINQ to SQL](../../docs/framework/data/adonet/sql/linq/index.md) je poměrně holou objekt relační Mapper (ORM) pro databázi MSSQL serveru.</span><span class="sxs-lookup"><span data-stu-id="113ed-125">[Linq to SQL](../../docs/framework/data/adonet/sql/linq/index.md) is a fairly bare-bones Object-Relational Mapper (ORM) for an MSSQL Server Database.</span></span> <span data-ttu-id="113ed-126">[JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) knihovna nabízí efektivní traversal dokumentu JSON prostřednictvím LINQ.</span><span class="sxs-lookup"><span data-stu-id="113ed-126">The [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) library provides efficient JSON Document traversal via LINQ.</span></span> <span data-ttu-id="113ed-127">Kromě toho, pokud není k dispozici knihovnu, která zajišťuje, co potřebujete, můžete také [napsat vlastního zprostředkovatele LINQ](https://msdn.microsoft.com/library/Bb546158.aspx)!</span><span class="sxs-lookup"><span data-stu-id="113ed-127">Furthermore, if there isn’t a library which does what you need, you can also [write your own LINQ Provider](https://msdn.microsoft.com/library/Bb546158.aspx)!</span></span>

## <a name="why-use-the-query-syntax"></a><span data-ttu-id="113ed-128">Proč používat syntaxi dotazu?</span><span class="sxs-lookup"><span data-stu-id="113ed-128">Why Use the Query Syntax?</span></span>

<span data-ttu-id="113ed-129">Toto je otázku, která se často zobrazí.</span><span class="sxs-lookup"><span data-stu-id="113ed-129">This is a question which often comes up.</span></span> <span data-ttu-id="113ed-130">Po všech, se</span><span class="sxs-lookup"><span data-stu-id="113ed-130">After all, this,</span></span>

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

<span data-ttu-id="113ed-131">je mnohem přesnější než toto:</span><span class="sxs-lookup"><span data-stu-id="113ed-131">is a lot more concise than this:</span></span>

```csharp
var filteredItems = from item in myItems
                    where item.Foo
                    select item;
```

<span data-ttu-id="113ed-132">Syntaxe rozhraní API není právě přesnější způsob, jak provést syntaxe dotazu?</span><span class="sxs-lookup"><span data-stu-id="113ed-132">Isn’t the API syntax just a more concise way to do the query syntax?</span></span>

<span data-ttu-id="113ed-133">Ne.</span><span class="sxs-lookup"><span data-stu-id="113ed-133">No.</span></span> <span data-ttu-id="113ed-134">Umožňuje použití syntaxe dotazu **let** klauzuli, která umožňuje zavádět a vytvořte vazbu proměnné v rámci oboru výrazem s použitím v další části výrazu.</span><span class="sxs-lookup"><span data-stu-id="113ed-134">The query syntax allows for the use the **let** clause, which allows you to introduce and bind a variable within the scope of the expression, using it in subsequent pieces of the expression.</span></span> <span data-ttu-id="113ed-135">Reprodukci stejný kód se pouze syntaxí rozhraní API lze provést, ale pravděpodobně povede k kódu, který se těžko čitelný.</span><span class="sxs-lookup"><span data-stu-id="113ed-135">Reproducing the same code with only the API syntax can be done, but will most likely lead to code which is hard to read.</span></span>

<span data-ttu-id="113ed-136">Proto to begs na otázku **by měla pouze použijete syntaxi dotazu?**</span><span class="sxs-lookup"><span data-stu-id="113ed-136">So this begs the question, **should you just use the query syntax?**</span></span>

<span data-ttu-id="113ed-137">Odpověď na tuto otázku **Ano** Pokud...</span><span class="sxs-lookup"><span data-stu-id="113ed-137">The answer to this question is **yes** if...</span></span>

*   <span data-ttu-id="113ed-138">Stávající codebase již používá syntaxi dotazu</span><span class="sxs-lookup"><span data-stu-id="113ed-138">Your existing codebase already uses the query syntax</span></span>
*   <span data-ttu-id="113ed-139">Obor proměnné je potřeba v rámci své dotazy z důvodu složitosti</span><span class="sxs-lookup"><span data-stu-id="113ed-139">You need to scope variables within your queries due to complexity</span></span>
*   <span data-ttu-id="113ed-140">Dáváte přednost syntaxe dotazu a nebude rušil vaší základu kódu</span><span class="sxs-lookup"><span data-stu-id="113ed-140">You prefer the query syntax and it won’t distract from your codebase</span></span>

<span data-ttu-id="113ed-141">Odpověď na tuto otázku **žádné** Pokud...</span><span class="sxs-lookup"><span data-stu-id="113ed-141">The answer to this question is **no** if...</span></span>

*   <span data-ttu-id="113ed-142">Stávající codebase již používá syntaxi rozhraní API</span><span class="sxs-lookup"><span data-stu-id="113ed-142">Your existing codebase already uses the API syntax</span></span>
*   <span data-ttu-id="113ed-143">Máte potřeba proměnných rozsahu v rámci své dotazy</span><span class="sxs-lookup"><span data-stu-id="113ed-143">You have no need to scope variables within your queries</span></span>
*   <span data-ttu-id="113ed-144">Dáváte přednost syntaxe rozhraní API a nebude rušil vaší základu kódu</span><span class="sxs-lookup"><span data-stu-id="113ed-144">You prefer the API syntax and it won’t distract from your codebase</span></span>

## <a name="essential-samples"></a><span data-ttu-id="113ed-145">Základní ukázky</span><span class="sxs-lookup"><span data-stu-id="113ed-145">Essential Samples</span></span>

<span data-ttu-id="113ed-146">Skutečně úplný seznam ukázky LINQ, najdete v článku [101 ukázky LINQ](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).</span><span class="sxs-lookup"><span data-stu-id="113ed-146">For a truly comprehensive list of LINQ samples, visit [101 LINQ Samples](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).</span></span>

<span data-ttu-id="113ed-147">Následuje ukázka rychlé některé důležité údaje LINQ.</span><span class="sxs-lookup"><span data-stu-id="113ed-147">The following is a quick demonstration of some of the essential pieces of LINQ.</span></span> <span data-ttu-id="113ed-148">Toto je nijak komplexní, LINQ, které poskytuje výrazně víc funkcí než co je showcased sem.</span><span class="sxs-lookup"><span data-stu-id="113ed-148">This is in no way comprehensive, as LINQ provides significantly more functionality than what is showcased here.</span></span>

*   <span data-ttu-id="113ed-149">Másla a chléb - `Where`, `Select`, a `Aggregate`:</span><span class="sxs-lookup"><span data-stu-id="113ed-149">The bread and butter - `Where`, `Select`, and `Aggregate`:</span></span>

```csharp
// Filtering a list
var germanShepards = dogs.Where(dog => dog.Breed == DogBreed.GermanShepard);

// Using the query syntax
var queryGermanShepards = from dog in dogs
                          where dog.Breed == DogBreed.GermanShepard
                          select dog;

// Mapping a list from type A to type B
var cats = dogs.Select(dog => dog.TurnIntoACat());

// Using the query syntax
var queryCats = from dog in dogs
                select dog.TurnIntoACat();

// Summing the lengths of a set of strings
int seed = 0;
int sumOfStrings = strings.Aggregate(seed, (s1, s2) => s1.Length + s2.Length);
```

*   <span data-ttu-id="113ed-150">Vyrovnání seznam seznamů:</span><span class="sxs-lookup"><span data-stu-id="113ed-150">Flattening a list of lists:</span></span>

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

*   <span data-ttu-id="113ed-151">Spojení mezi dvěma sadami (s vlastní komparátoru):</span><span class="sxs-lookup"><span data-stu-id="113ed-151">Union between two sets (with custom comparator):</span></span>

```csharp
public class DogHairLengthComparer : IEqualityComparer<Dog>
{
    public bool Equals(Dog a, Dog b)
    {
        if (a == null && b == null)
        {
            return true;
        }
        else if ((a == null && b != null) ||
                 (a != null && b == null))
        {
            return false;
        }
        else
        {
            return a.HairLengthType == b.HairLengthType;
        }
    }

    public int GetHashCode(Dog d)
    {
        // default hashcode is enough here, as these are simple objects.
        return b.GetHashCode();
    }
}

...

// Gets all the short-haired dogs between two different kennels
var allShortHairedDogs = kennel1.Dogs.Union(kennel2.Dogs, new DogHairLengthComparer());
```

*   <span data-ttu-id="113ed-152">Průnik mezi dvěma sadami:</span><span class="sxs-lookup"><span data-stu-id="113ed-152">Intersection between two sets:</span></span>

```csharp
// Gets the volunteers who spend share time with two humane societies.
var volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     new VolunteerTimeComparer());
```

*   <span data-ttu-id="113ed-153">Řazení:</span><span class="sxs-lookup"><span data-stu-id="113ed-153">Ordering:</span></span>

```csharp
// Get driving directions, ordering by if it's toll-free before estimated driving time.
var results = DirectionsProcessor.GetDirections(start, end)
              .OrderBy(direction => direction.HasNoTolls)
              .ThenBy(direction => direction.EstimatedTime);
```

*   <span data-ttu-id="113ed-154">Nakonec další pokročilé ukázka: určení, jestli jsou stejné hodnoty vlastnosti dvě instance stejného typu (Borrowed a upravených z [tento příspěvek StackOverflow](http://stackoverflow.com/a/844855)):</span><span class="sxs-lookup"><span data-stu-id="113ed-154">Finally, a more advanced sample: determining if the values of the properties of two instances of the same type are equal (Borrowed and modified from [this StackOverflow post](http://stackoverflow.com/a/844855)):</span></span>

```csharp
public static bool PublicInstancePropertiesEqual<T>(this T self, T to, params string[] ignore) where T : class
{
    if (self != null && to != null)
    {
        var type = typeof(T);
        var ignoreList = new List<string>(ignore);

        // Selects the properties which have unequal values into a sequence of those properties.
        var unequalProperties = from pi in type.GetProperties(BindingFlags.Public | BindingFlags.Instance)
                                where !ignoreList.Contains(pi.Name)
                                let selfValue = type.GetProperty(pi.Name).GetValue(self, null)
                                let toValue = type.GetProperty(pi.Name).GetValue(to, null)
                                where selfValue != toValue && (selfValue == null || !selfValue.Equals(toValue))
                                select new { Prop = pi.Name, selfValue, toValue };
        return !unequalProperties.Any();
    }

    return self == to;
}
```

## <a name="plinq"></a><span data-ttu-id="113ed-155">PLINQ</span><span class="sxs-lookup"><span data-stu-id="113ed-155">PLINQ</span></span>

<span data-ttu-id="113ed-156">Paralelní provádění modul pro LINQ – výrazy se PLINQ nebo paralelní LINQ.</span><span class="sxs-lookup"><span data-stu-id="113ed-156">PLINQ, or Parallel LINQ, is a parallel execution engine for LINQ expressions.</span></span> <span data-ttu-id="113ed-157">Jinými slovy regulární výrazy LINQ může být trivially paralelizovaná málo napříč libovolný počet vláken.</span><span class="sxs-lookup"><span data-stu-id="113ed-157">In other words, a regular LINQ expressions can be trivially parallelized across any number of threads.</span></span> <span data-ttu-id="113ed-158">To se provádí prostřednictvím volání `AsParallel()` před výrazem.</span><span class="sxs-lookup"><span data-stu-id="113ed-158">This is accomplished via a call to `AsParallel()` preceding the expression.</span></span>

<span data-ttu-id="113ed-159">Zvažte následující:</span><span class="sxs-lookup"><span data-stu-id="113ed-159">Consider the following:</span></span>

```csharp
public static string GetAllFacebookUserLikesMessage(IEnumerable<FacebookUser> facebookUsers)
{
    var seed = default(UInt64);

    Func<UInt64, UInt64, UInt64> threadAccumulator = (t1, t2) => t1 + t2;
    Func<UInt64, UInt64, UInt64> threadResultAccumulator = (t1, t2) => t1 + t2;
    Func<Uint64, string> resultSelector = total => $"Facebook has {total} likes!";

    return facebookUsers.AsParallel()
                        .Aggregate(seed, threadAccumulator, threadResultAccumulator, resultSelector);
}
```

<span data-ttu-id="113ed-160">Tento kód bude oddílu `facebookUsers` napříč vlákny systému podle potřeby součet až celkový líbí na každé vlákno paralelně, aby součet výsledky počítaný jednotlivými vlákny a projektu tento výsledek na dobrý řetězec.</span><span class="sxs-lookup"><span data-stu-id="113ed-160">This code will partition `facebookUsers` across system threads as necessary, sum up the total likes on each thread in parallel, sum the results computed by each thread, and project that result into a nice string.</span></span>

<span data-ttu-id="113ed-161">Ve formuláři diagram:</span><span class="sxs-lookup"><span data-stu-id="113ed-161">In diagram form:</span></span>

![PLINQ diagram](./media/using-linq/plinq-diagram.png)

<span data-ttu-id="113ed-163">Paralelní úlohy vázané na procesor, které lze snadno vyjádřit pomocí LINQ (jinými slovy, jsou čistá funkce a mít žádné vedlejší účinky) jsou skvělý kandidátem pro PLINQ.</span><span class="sxs-lookup"><span data-stu-id="113ed-163">Parallelizable CPU-bound jobs which can be easily expressed via LINQ (in other words, are pure functions and have no side effects) are a great candidate for PLINQ.</span></span> <span data-ttu-id="113ed-164">Pro úlohy, které _provést_ mít vedlejším účinkem, zvažte použití [Task Parallel Library](./parallel-programming/task-parallel-library-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="113ed-164">For jobs which _do_ have a side effect, consider using the [Task Parallel Library](./parallel-programming/task-parallel-library-tpl.md).</span></span>

## <a name="further-resources"></a><span data-ttu-id="113ed-165">Další prostředky:</span><span class="sxs-lookup"><span data-stu-id="113ed-165">Further Resources:</span></span>

*   [<span data-ttu-id="113ed-166">101 ukázky LINQ</span><span class="sxs-lookup"><span data-stu-id="113ed-166">101 LINQ Samples</span></span>](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)
*   <span data-ttu-id="113ed-167">[Linqpad](https://www.linqpad.net/), playground prostředí a databázové dotazy modul pro C# /F # / VB.</span><span class="sxs-lookup"><span data-stu-id="113ed-167">[Linqpad](https://www.linqpad.net/), a playground environment and Database querying engine for C#/F#/VB</span></span>
*   <span data-ttu-id="113ed-168">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), zde elektronickou knihu pro učení, jak je implementována LINQ na objekty</span><span class="sxs-lookup"><span data-stu-id="113ed-168">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), an e-book for learning how LINQ-to-objects is implemented</span></span>
