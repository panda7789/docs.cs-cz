---
title: LINQ (Language Integrated Query)
description: Zjistěte, jak LINQ poskytuje možnosti dotazování úrovni jazyka a rozhraní API pro C# a VB jako způsob, jak napsat kód výrazová, deklarativní.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: c00939e1-59e3-4e61-8fe9-08ad6b3f1295
ms.openlocfilehash: 9b80ab37c883978a116417ebd6cb001c75f0c071
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661932"
---
# <a name="linq-language-integrated-query"></a><span data-ttu-id="bcfa4-103">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="bcfa4-103">LINQ (Language Integrated Query)</span></span>

## <a name="what-is-it"></a><span data-ttu-id="bcfa4-104">Co je to?</span><span class="sxs-lookup"><span data-stu-id="bcfa4-104">What is it?</span></span>

<span data-ttu-id="bcfa4-105">LINQ poskytuje možnosti dotazování úrovni jazyka a [funkce vyššího řádu](https://en.wikipedia.org/wiki/Higher-order_function) rozhraní API pro C# a VB jako způsob, jak napsat kód výrazová, deklarativní.</span><span class="sxs-lookup"><span data-stu-id="bcfa4-105">LINQ provides language-level querying capabilities and a [higher-order function](https://en.wikipedia.org/wiki/Higher-order_function) API to C# and VB as a way to write expressive, declarative code.</span></span>

<span data-ttu-id="bcfa4-106">Syntaxe dotazu na úrovni jazyka:</span><span class="sxs-lookup"><span data-stu-id="bcfa4-106">Language-level query syntax:</span></span>

```csharp
var linqExperts = from p in programmers
                  where p.IsNewToLINQ
                  select new LINQExpert(p);
```

```vb
Dim linqExperts = From p in programmers
                  Where p.IsNewToLINQ
                  Select New LINQExpert(p)
```

<span data-ttu-id="bcfa4-107">Stejný příklad použití `IEnumerable<T>` rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="bcfa4-107">Same example using the `IEnumerable<T>` API:</span></span>

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

```vb
Dim linqExperts = programmers.Where(Function(p) p.IsNewToLINQ).
                             Select(Function(p) New LINQExpert(p))
```

## <a name="linq-is-expressive"></a><span data-ttu-id="bcfa4-108">LINQ je Expressive</span><span class="sxs-lookup"><span data-stu-id="bcfa4-108">LINQ is Expressive</span></span>

<span data-ttu-id="bcfa4-109">Představte si máte seznam mazlíčků, ale má být převeden do slovníku, kam máte přístup mazlíčky přímo nástrojem jeho `RFID` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bcfa4-109">Imagine you have a list of pets, but want to convert it into a dictionary where you can access a pet directly by its `RFID` value.</span></span>

<span data-ttu-id="bcfa4-110">Tradiční imperativního kódu:</span><span class="sxs-lookup"><span data-stu-id="bcfa4-110">Traditional imperative code:</span></span>

```csharp
var petLookup = new Dictionary<int, Pet>();

foreach (var pet in pets)
{
    petLookup.Add(pet.RFID, pet);
}
```

```vb
Dim petLookup = New Dictionary(Of Integer, Pet)()

For Each pet in pets
    petLookup.Add(pet.RFID, pet)
Next
```

<span data-ttu-id="bcfa4-111">Záměrem za kód je nechcete vytvářet novou `Dictionary<int, Pet>` a přidejte do ní prostřednictvím smyčku, je pro převod existujícího seznamu do slovníku!</span><span class="sxs-lookup"><span data-stu-id="bcfa4-111">The intention behind the code is not to create a new `Dictionary<int, Pet>` and add to it via a loop, it is to convert an existing list into a dictionary!</span></span> <span data-ttu-id="bcfa4-112">LINQ zachová záměrem služba nepodporuje imperativního kódu.</span><span class="sxs-lookup"><span data-stu-id="bcfa4-112">LINQ preserves the intention whereas the imperative code does not.</span></span>

<span data-ttu-id="bcfa4-113">Ekvivalentní výraz LINQ:</span><span class="sxs-lookup"><span data-stu-id="bcfa4-113">Equivalent LINQ expression:</span></span>

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

```vb
Dim petLookup = pets.ToDictionary(Function(pet) pet.RFID)
```

<span data-ttu-id="bcfa4-114">Kód pomocí jazyka LINQ je užitečné, protože evens hrací pole mezi cílem a kódem, když důvody jako programátor.</span><span class="sxs-lookup"><span data-stu-id="bcfa4-114">The code using LINQ is valuable because it evens the playing field between intent and code when reasoning as a programmer.</span></span> <span data-ttu-id="bcfa4-115">Jiné bonusové je zkrácení kódu.</span><span class="sxs-lookup"><span data-stu-id="bcfa4-115">Another bonus is code brevity.</span></span> <span data-ttu-id="bcfa4-116">Představte si redukování 1/3 dělalo nad velkých částech základ kódu.</span><span class="sxs-lookup"><span data-stu-id="bcfa4-116">Imagine reducing large portions of a codebase by 1/3 as done above.</span></span> <span data-ttu-id="bcfa4-117">Poměrně sladké záležitost, pravé?</span><span class="sxs-lookup"><span data-stu-id="bcfa4-117">Pretty sweet deal, right?</span></span>

## <a name="linq-providers-simplify-data-access"></a><span data-ttu-id="bcfa4-118">Zprostředkovatelé dotazů LINQ zjednodušit přístup k datům</span><span class="sxs-lookup"><span data-stu-id="bcfa4-118">LINQ Providers Simplify Data Access</span></span>

<span data-ttu-id="bcfa4-119">Významné blok softwaru v reálném světě všechno, co zásadní kolem práci s daty z některé zdroje (databáze, JSON, XML atd.).</span><span class="sxs-lookup"><span data-stu-id="bcfa4-119">For a significant chunk of software out in the wild, everything revolves around dealing with data from some source (Databases, JSON, XML, etc).</span></span> <span data-ttu-id="bcfa4-120">Často to zahrnuje nové rozhraní API pro každý zdroj dat, které vám můžou jít učení.</span><span class="sxs-lookup"><span data-stu-id="bcfa4-120">Often this involves learning a new API for each data source, which can be annoying.</span></span> <span data-ttu-id="bcfa4-121">LINQ to zjednodušuje tím, že poskytuje abstrakci společné prvky přístup k datům do syntaxe dotazu, která vypadá stejně bez ohledu na zdroj dat, který vyberete.</span><span class="sxs-lookup"><span data-stu-id="bcfa4-121">LINQ simplifies this by abstracting common elements of data access into a query syntax which looks the same no matter which data source you pick.</span></span>

<span data-ttu-id="bcfa4-122">Vezměte v úvahu následující: vyhledání všech elementů XML pomocí konkrétní atribut hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bcfa4-122">Consider the following: finding all XML elements with a specific attribute value.</span></span>

```csharp
public static IEnumerable<XElement> FindAllElementsWithAttribute(XElement documentRoot, string elementName,
                                           string attributeName, string value)
{
    return from el in documentRoot.Elements(elementName)
           where (string)el.Element(attributeName) == value
           select el;
}
```

```vb
Public Shared Function FindAllElementsWithAttribute(documentRoot As XElement, elementName As String,
                                           attributeName As String, value As String) As IEnumerable(Of XElement)
    Return From el In documentRoot.Elements(elementName)
           Where el.Element(attributeName).ToString() = value
           Select el
End Function

```

<span data-ttu-id="bcfa4-123">Psaní kódu ručně procházet dokumentu XML k provedení této úlohy by bylo mnohem složitější.</span><span class="sxs-lookup"><span data-stu-id="bcfa4-123">Writing code to manually traverse the XML document to perform this task would be far more challenging.</span></span>

<span data-ttu-id="bcfa4-124">Interakce s XML není jediné, co můžete dělat s zprostředkovatelé dotazů LINQ.</span><span class="sxs-lookup"><span data-stu-id="bcfa4-124">Interacting with XML isn’t the only thing you can do with LINQ Providers.</span></span> <span data-ttu-id="bcfa4-125">[Technologie LINQ to SQL](../../docs/framework/data/adonet/sql/linq/index.md) je poměrně holou objektově-relační Mapovač (ORM) určené pro databázi MSSQL serveru.</span><span class="sxs-lookup"><span data-stu-id="bcfa4-125">[Linq to SQL](../../docs/framework/data/adonet/sql/linq/index.md) is a fairly bare-bones Object-Relational Mapper (ORM) for an MSSQL Server Database.</span></span> <span data-ttu-id="bcfa4-126">[JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) knihovna poskytuje efektivní procházení dokumentu JSON prostřednictvím LINQ.</span><span class="sxs-lookup"><span data-stu-id="bcfa4-126">The [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) library provides efficient JSON Document traversal via LINQ.</span></span> <span data-ttu-id="bcfa4-127">Kromě toho, pokud není k dispozici knihovna, která zajišťuje, co potřebujete, můžete také [napsat vlastního zprostředkovatele LINQ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))!</span><span class="sxs-lookup"><span data-stu-id="bcfa4-127">Furthermore, if there isn’t a library which does what you need, you can also [write your own LINQ Provider](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))!</span></span>

## <a name="why-use-the-query-syntax"></a><span data-ttu-id="bcfa4-128">Proč používat syntaxi dotazu?</span><span class="sxs-lookup"><span data-stu-id="bcfa4-128">Why Use the Query Syntax?</span></span>

<span data-ttu-id="bcfa4-129">To je otázka, které často se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="bcfa4-129">This is a question which often comes up.</span></span> <span data-ttu-id="bcfa4-130">Po všech tento,</span><span class="sxs-lookup"><span data-stu-id="bcfa4-130">After all, this,</span></span>

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

```vb
Dim filteredItems = myItems.Where(Function(item) item.Foo)
```

<span data-ttu-id="bcfa4-131">je mnohem přesnější než toto:</span><span class="sxs-lookup"><span data-stu-id="bcfa4-131">is a lot more concise than this:</span></span>

```csharp
var filteredItems = from item in myItems
                    where item.Foo
                    select item;
```

```vb
Dim filteredItems = From item In myItems
                    Where item.Foo
                    Select item
```

<span data-ttu-id="bcfa4-132">Syntaxe rozhraní API není právě přesnější způsob, jak provést syntaxi dotazu?</span><span class="sxs-lookup"><span data-stu-id="bcfa4-132">Isn’t the API syntax just a more concise way to do the query syntax?</span></span>

<span data-ttu-id="bcfa4-133">Ne.</span><span class="sxs-lookup"><span data-stu-id="bcfa4-133">No.</span></span> <span data-ttu-id="bcfa4-134">Syntaxe dotazu umožňuje použití **nechat** klauzule, které umožňuje zavést a vytvoření vazby proměnné v rámci oboru výrazem s použitím v další části výrazu.</span><span class="sxs-lookup"><span data-stu-id="bcfa4-134">The query syntax allows for the use of the **let** clause, which allows you to introduce and bind a variable within the scope of the expression, using it in subsequent pieces of the expression.</span></span> <span data-ttu-id="bcfa4-135">Reprodukce stejný kód s pouze syntaxi rozhraní API můžete udělat, ale pravděpodobně povede k kódu, který se těžko čitelný.</span><span class="sxs-lookup"><span data-stu-id="bcfa4-135">Reproducing the same code with only the API syntax can be done, but will most likely lead to code which is hard to read.</span></span>

<span data-ttu-id="bcfa4-136">Takže to si žádá otázku, **by měl pouze použijete syntaxi dotazu?**</span><span class="sxs-lookup"><span data-stu-id="bcfa4-136">So this begs the question, **should you just use the query syntax?**</span></span>

<span data-ttu-id="bcfa4-137">Odpověď na tuto otázku se **Ano** Pokud...</span><span class="sxs-lookup"><span data-stu-id="bcfa4-137">The answer to this question is **yes** if...</span></span>

* <span data-ttu-id="bcfa4-138">Stávající základ kódu už používá syntaxi dotazu</span><span class="sxs-lookup"><span data-stu-id="bcfa4-138">Your existing codebase already uses the query syntax</span></span>
* <span data-ttu-id="bcfa4-139">Je potřeba proměnné s rozsahem v rámci své dotazy z důvodu složitosti</span><span class="sxs-lookup"><span data-stu-id="bcfa4-139">You need to scope variables within your queries due to complexity</span></span>
* <span data-ttu-id="bcfa4-140">Dáváte přednost syntaxi dotazů a nebude odklánět pozornost od vašeho základu kódu</span><span class="sxs-lookup"><span data-stu-id="bcfa4-140">You prefer the query syntax and it won’t distract from your codebase</span></span>

<span data-ttu-id="bcfa4-141">Odpověď na tuto otázku se **žádné** Pokud...</span><span class="sxs-lookup"><span data-stu-id="bcfa4-141">The answer to this question is **no** if...</span></span>

* <span data-ttu-id="bcfa4-142">Stávající základ kódu už používá syntaxi rozhraní API</span><span class="sxs-lookup"><span data-stu-id="bcfa4-142">Your existing codebase already uses the API syntax</span></span>
* <span data-ttu-id="bcfa4-143">Nemáte žádné požadavky na rozsah proměnné v dotazech</span><span class="sxs-lookup"><span data-stu-id="bcfa4-143">You have no need to scope variables within your queries</span></span>
* <span data-ttu-id="bcfa4-144">Dáváte přednost syntaxi rozhraní API a nebude odklánět pozornost od vašeho základu kódu</span><span class="sxs-lookup"><span data-stu-id="bcfa4-144">You prefer the API syntax and it won’t distract from your codebase</span></span>

## <a name="essential-samples"></a><span data-ttu-id="bcfa4-145">Základní ukázky</span><span class="sxs-lookup"><span data-stu-id="bcfa4-145">Essential Samples</span></span>

<span data-ttu-id="bcfa4-146">Seznam skutečně komplexní ukázky dotazů LINQ naleznete [101 ukázek pro LINQ](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).</span><span class="sxs-lookup"><span data-stu-id="bcfa4-146">For a truly comprehensive list of LINQ samples, visit [101 LINQ Samples](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).</span></span>

<span data-ttu-id="bcfa4-147">Tady je rychlý ukázku některé základní údaje LINQ.</span><span class="sxs-lookup"><span data-stu-id="bcfa4-147">The following is a quick demonstration of some of the essential pieces of LINQ.</span></span> <span data-ttu-id="bcfa4-148">To není nijak komplexní, protože LINQ poskytuje výrazně víc funkcí než co se tady zobrazují.</span><span class="sxs-lookup"><span data-stu-id="bcfa4-148">This is in no way comprehensive, as LINQ provides significantly more functionality than what is showcased here.</span></span>

* <span data-ttu-id="bcfa4-149">A másle bread - `Where`, `Select`, a `Aggregate`:</span><span class="sxs-lookup"><span data-stu-id="bcfa4-149">The bread and butter - `Where`, `Select`, and `Aggregate`:</span></span>

```csharp
// Filtering a list.
var germanShepards = dogs.Where(dog => dog.Breed == DogBreed.GermanShepard);

// Using the query syntax.
var queryGermanShepards = from dog in dogs
                          where dog.Breed == DogBreed.GermanShepard
                          select dog;

// Mapping a list from type A to type B.
var cats = dogs.Select(dog => dog.TurnIntoACat());

// Using the query syntax.
var queryCats = from dog in dogs
                select dog.TurnIntoACat();

// Summing the lengths of a set of strings.
int seed = 0;
int sumOfStrings = strings.Aggregate(seed, (s1, s2) => s1.Length + s2.Length);
```

```vb
' Filtering a list.
Dim germanShepards = dogs.Where(Function(dog) dog.Breed = DogBreed.GermanShepard)

' Using the query syntax.
Dim queryGermanShepards = From dog In dogs
                          Where dog.Breed = DogBreed.GermanShepard
                          Select dog

' Mapping a list from type A to type B.
Dim cats = dogs.Select(Function(dog) dog.TurnIntoACat())

' Using the query syntax.
Dim queryCats = From dog In dogs
                Select dog.TurnIntoACat()

' Summing the lengths of a set of strings.
Dim seed As Integer = 0
Dim sumOfStrings As Integer = strings.Aggregate(seed, Function(s1, s2) s1.Length + s2.Length)
```

* <span data-ttu-id="bcfa4-150">Sloučení seznamů:</span><span class="sxs-lookup"><span data-stu-id="bcfa4-150">Flattening a list of lists:</span></span>

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

```vb
' Transforms the list of kennels into a list of all their dogs.
Dim allDogsFromKennels = kennels.SelectMany(Function(kennel) kennel.Dogs)
```

* <span data-ttu-id="bcfa4-151">Sjednocení mezi dvěma sadami (s vlastní Komparátor):</span><span class="sxs-lookup"><span data-stu-id="bcfa4-151">Union between two sets (with custom comparator):</span></span>

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
        // Default hashcode is enough here, as these are simple objects.
        return d.GetHashCode();
    }
}

...

// Gets all the short-haired dogs between two different kennels.
var allShortHairedDogs = kennel1.Dogs.Union(kennel2.Dogs, new DogHairLengthComparer());
```

```vb
Public Class DogHairLengthComparer 
  Inherits IEqualityComparer(Of Dog)

  Public Function Equals(a As Dog,b As Dog) As Boolean
      If a Is Nothing AndAlso b Is Nothing Then
          Return True
      ElseIf (a Is Nothing AndAlso b IsNot Nothing) OrElse (a IsNot Nothing AndAlso b Is Nothing) Then
          Return False
      Else
          Return a.HairLengthType = b.HairLengthType
      End If
  End Function

  Public Function GetHashCode(d As Dog) As Integer
      ' Default hashcode is enough here, as these are simple objects.
      Return d.GetHashCode()
  End Function
End Class

...

' Gets all the short-haired dogs between two different kennels.
Dim allShortHairedDogs = kennel1.Dogs.Union(kennel2.Dogs, New DogHairLengthComparer())
```


* <span data-ttu-id="bcfa4-152">Průnik mezi dvěma sadami:</span><span class="sxs-lookup"><span data-stu-id="bcfa4-152">Intersection between two sets:</span></span>

```csharp
// Gets the volunteers who spend share time with two humane societies.
var volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     new VolunteerTimeComparer());
```

```vb
' Gets the volunteers who spend share time with two humane societies.
Dim volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     New VolunteerTimeComparer())
```

* <span data-ttu-id="bcfa4-153">Pořadí:</span><span class="sxs-lookup"><span data-stu-id="bcfa4-153">Ordering:</span></span>

```csharp
// Get driving directions, ordering by if it's toll-free before estimated driving time.
var results = DirectionsProcessor.GetDirections(start, end)
              .OrderBy(direction => direction.HasNoTolls)
              .ThenBy(direction => direction.EstimatedTime);
```

```vb
' Get driving directions, ordering by if it's toll-free before estimated driving time.
Dim results = DirectionsProcessor.GetDirections(start, end).
                OrderBy(Function(direction) direction.HasNoTolls).
                ThenBy(Function(direction) direction.EstimatedTime)
```

* <span data-ttu-id="bcfa4-154">Nakonec více advanced vzorku: určení, jestli jsou stejné hodnoty vlastností dvě instance stejného typu (Borrowed a upravené z [tento příspěvek na StackOverflow](https://stackoverflow.com/a/844855)):</span><span class="sxs-lookup"><span data-stu-id="bcfa4-154">Finally, a more advanced sample: determining if the values of the properties of two instances of the same type are equal (Borrowed and modified from [this StackOverflow post](https://stackoverflow.com/a/844855)):</span></span>

```csharp
public static bool PublicInstancePropertiesEqual<T>(this T self, T to, params string[] ignore) where T : class
{
    if (self == null || to == null)
    {
        return self == to;
    }
    
    // Selects the properties which have unequal values into a sequence of those properties.
    var unequalProperties = from property in typeof(T).GetProperties(BindingFlags.Public | BindingFlags.Instance)
                            where !ignore.Contains(property.Name)
                            let selfValue = property.GetValue(self, null)
                            let toValue = property.GetValue(to, null)
                            where !Equals(selfValue, toValue)
                            select property;
    return !unequalProperties.Any();
}
```


## <a name="plinq"></a><span data-ttu-id="bcfa4-155">PLINQ</span><span class="sxs-lookup"><span data-stu-id="bcfa4-155">PLINQ</span></span>

<span data-ttu-id="bcfa4-156">PLINQ nebo paralelní LINQ, je modul pro paralelní provádění pro výrazy LINQ.</span><span class="sxs-lookup"><span data-stu-id="bcfa4-156">PLINQ, or Parallel LINQ, is a parallel execution engine for LINQ expressions.</span></span> <span data-ttu-id="bcfa4-157">Regulární výraz LINQ jinými slovy, může být triviálně paralelizován, napříč libovolným počtem vláken.</span><span class="sxs-lookup"><span data-stu-id="bcfa4-157">In other words, a regular LINQ expression can be trivially parallelized across any number of threads.</span></span> <span data-ttu-id="bcfa4-158">To lze provést prostřednictvím volání `AsParallel()` před výrazem.</span><span class="sxs-lookup"><span data-stu-id="bcfa4-158">This is accomplished via a call to `AsParallel()` preceding the expression.</span></span>

<span data-ttu-id="bcfa4-159">Zvažte použití těchto zdrojů:</span><span class="sxs-lookup"><span data-stu-id="bcfa4-159">Consider the following:</span></span>

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

```vb
Public Shared GetAllFacebookUserLikesMessage(facebookUsers As IEnumerable(Of FacebookUser)) As String
{
    Dim seed As UInt64 = 0

    Dim threadAccumulator As Func(Of UInt64, UInt64, UInt64) = Function(t1, t2) t1 + t2
    Dim threadResultAccumulator As Func(Of UInt64, UInt64, UInt64) = Function(t1, t2) t1 + t2
    Dim resultSelector As Func(Of Uint64, string) = Function(total) $"Facebook has {total} likes!"

    Return facebookUsers.AsParallel().
                        Aggregate(seed, threadAccumulator, threadResultAccumulator, resultSelector)
}
```

<span data-ttu-id="bcfa4-160">Tento kód bude oddílu `facebookUsers` napříč systémová vlákna podle potřeby, součet celkový počet lajků. v každém vláknu paralelně, součtu výsledky počítají tak, že každé vlákno a projektů, které do nice řetězce.</span><span class="sxs-lookup"><span data-stu-id="bcfa4-160">This code will partition `facebookUsers` across system threads as necessary, sum up the total likes on each thread in parallel, sum the results computed by each thread, and project that result into a nice string.</span></span>

<span data-ttu-id="bcfa4-161">Ve formuláři diagramu:</span><span class="sxs-lookup"><span data-stu-id="bcfa4-161">In diagram form:</span></span>

![PLINQ diagram](./media/using-linq/plinq-diagram.png)

<span data-ttu-id="bcfa4-163">Paralelizovat úlohy vázané na procesor, které lze snadno vyjádřit pomocí LINQ (jinými slovy, jsou čistě funkce a žádné vedlejší účinky) jsou skvělé Release candidate pro PLINQ.</span><span class="sxs-lookup"><span data-stu-id="bcfa4-163">Parallelizable CPU-bound jobs which can be easily expressed via LINQ (in other words, are pure functions and have no side effects) are a great candidate for PLINQ.</span></span> <span data-ttu-id="bcfa4-164">Pro úlohy, které _proveďte_ mají vedlejší účinek, zvažte použití [Task Parallel Library](./parallel-programming/task-parallel-library-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="bcfa4-164">For jobs which _do_ have a side effect, consider using the [Task Parallel Library](./parallel-programming/task-parallel-library-tpl.md).</span></span>

## <a name="further-resources"></a><span data-ttu-id="bcfa4-165">Další materiály:</span><span class="sxs-lookup"><span data-stu-id="bcfa4-165">Further Resources:</span></span>

* [<span data-ttu-id="bcfa4-166">101 ukázek pro LINQ</span><span class="sxs-lookup"><span data-stu-id="bcfa4-166">101 LINQ Samples</span></span>](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)
* <span data-ttu-id="bcfa4-167">[Linqpad](https://www.linqpad.net/), playground prostředí a dotazování databáze modul pro C#/F#/VB</span><span class="sxs-lookup"><span data-stu-id="bcfa4-167">[Linqpad](https://www.linqpad.net/), a playground environment and Database querying engine for C#/F#/VB</span></span>
* <span data-ttu-id="bcfa4-168">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), e knihu naučí, jak je implementovaná LINQ na objekty</span><span class="sxs-lookup"><span data-stu-id="bcfa4-168">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), an e-book for learning how LINQ-to-objects is implemented</span></span>
