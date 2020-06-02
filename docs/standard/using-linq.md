---
title: LINQ (integrovaný dotaz jazyka)
description: Naučte se, jak LINQ poskytuje možnosti dotazování na úrovni jazyka a rozhraní API pro C# a Visual Basic jako způsob, jak napsat expresně deklarativní kód.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: c00939e1-59e3-4e61-8fe9-08ad6b3f1295
ms.openlocfilehash: cd0260de3facdd37c46e9fb2f09ddc4cac08e71b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291068"
---
# <a name="linq-language-integrated-query"></a><span data-ttu-id="d6793-103">LINQ (integrovaný dotaz jazyka)</span><span class="sxs-lookup"><span data-stu-id="d6793-103">LINQ (Language Integrated Query)</span></span>

## <a name="what-is-it"></a><span data-ttu-id="d6793-104">Co je to?</span><span class="sxs-lookup"><span data-stu-id="d6793-104">What is it?</span></span>

<span data-ttu-id="d6793-105">LINQ poskytuje funkce pro dotazování na úrovni jazyka a rozhraní API s [vyšším pořadím](https://en.wikipedia.org/wiki/Higher-order_function) pro C# a Visual Basic jako způsob, jak napsat výrazující, deklarativní kód.</span><span class="sxs-lookup"><span data-stu-id="d6793-105">LINQ provides language-level querying capabilities and a [higher-order function](https://en.wikipedia.org/wiki/Higher-order_function) API to C# and Visual Basic as a way to write expressive, declarative code.</span></span>

<span data-ttu-id="d6793-106">Syntaxe dotazu na úrovni jazyka:</span><span class="sxs-lookup"><span data-stu-id="d6793-106">Language-level query syntax:</span></span>

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

<span data-ttu-id="d6793-107">Stejný příklad s použitím `IEnumerable<T>` rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="d6793-107">Same example using the `IEnumerable<T>` API:</span></span>

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

```vb
Dim linqExperts = programmers.Where(Function(p) p.IsNewToLINQ).
                             Select(Function(p) New LINQExpert(p))
```

## <a name="linq-is-expressive"></a><span data-ttu-id="d6793-108">LINQ je vyjádření</span><span class="sxs-lookup"><span data-stu-id="d6793-108">LINQ is Expressive</span></span>

<span data-ttu-id="d6793-109">Představte si, že máte seznam domácích, ale chcete ho převést do slovníku, kde můžete získat přístup k PET přímo podle jeho `RFID` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d6793-109">Imagine you have a list of pets, but want to convert it into a dictionary where you can access a pet directly by its `RFID` value.</span></span>

<span data-ttu-id="d6793-110">Tradiční imperativní kód:</span><span class="sxs-lookup"><span data-stu-id="d6793-110">Traditional imperative code:</span></span>

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

<span data-ttu-id="d6793-111">Záměr za kódem není vytvořit novou `Dictionary<int, Pet>` a přidat do něj prostřednictvím smyčky, je převést existující seznam do slovníku.</span><span class="sxs-lookup"><span data-stu-id="d6793-111">The intention behind the code is not to create a new `Dictionary<int, Pet>` and add to it via a loop, it is to convert an existing list into a dictionary!</span></span> <span data-ttu-id="d6793-112">LINQ zachovává záměr, zatímco imperativní kód ne.</span><span class="sxs-lookup"><span data-stu-id="d6793-112">LINQ preserves the intention whereas the imperative code does not.</span></span>

<span data-ttu-id="d6793-113">Ekvivalentní výraz LINQ:</span><span class="sxs-lookup"><span data-stu-id="d6793-113">Equivalent LINQ expression:</span></span>

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

```vb
Dim petLookup = pets.ToDictionary(Function(pet) pet.RFID)
```

<span data-ttu-id="d6793-114">Kód, který používá LINQ, je užitečný, protože se jedná o hrací pole mezi záměrem a kódem v případě, kdy je důvodem jako programátor.</span><span class="sxs-lookup"><span data-stu-id="d6793-114">The code using LINQ is valuable because it evens the playing field between intent and code when reasoning as a programmer.</span></span> <span data-ttu-id="d6793-115">Další bonus je kód zkrácení.</span><span class="sxs-lookup"><span data-stu-id="d6793-115">Another bonus is code brevity.</span></span> <span data-ttu-id="d6793-116">Představte si zmenšení velkých částí základu kódu pomocí 1/3, jak bylo dokončeno.</span><span class="sxs-lookup"><span data-stu-id="d6793-116">Imagine reducing large portions of a codebase by 1/3 as done above.</span></span> <span data-ttu-id="d6793-117">Hodně sladkých, hned?</span><span class="sxs-lookup"><span data-stu-id="d6793-117">Pretty sweet deal, right?</span></span>

## <a name="linq-providers-simplify-data-access"></a><span data-ttu-id="d6793-118">Poskytovatelé LINQ zjednodušují přístup k datům</span><span class="sxs-lookup"><span data-stu-id="d6793-118">LINQ Providers Simplify Data Access</span></span>

<span data-ttu-id="d6793-119">V rámci značné škály softwaru na volném světě se všechno otáčí kolem dat z nějakého zdroje (databáze, JSON, XML atd.).</span><span class="sxs-lookup"><span data-stu-id="d6793-119">For a significant chunk of software out in the wild, everything revolves around dealing with data from some source (Databases, JSON, XML, etc).</span></span> <span data-ttu-id="d6793-120">To často zahrnuje učení nového rozhraní API pro každý zdroj dat, což může být nepříjemné.</span><span class="sxs-lookup"><span data-stu-id="d6793-120">Often this involves learning a new API for each data source, which can be annoying.</span></span> <span data-ttu-id="d6793-121">LINQ to zjednodušuje tím, že abstrakce společných prvků přístupu k datům do syntaxe dotazu, která vypadá stejně, jako vybraný zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="d6793-121">LINQ simplifies this by abstracting common elements of data access into a query syntax which looks the same no matter which data source you pick.</span></span>

<span data-ttu-id="d6793-122">Vezměte v úvahu následující: vyhledání všech elementů XML s konkrétní hodnotou atributu.</span><span class="sxs-lookup"><span data-stu-id="d6793-122">Consider the following: finding all XML elements with a specific attribute value.</span></span>

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

<span data-ttu-id="d6793-123">Psaní kódu pro ruční procházení dokumentu XML k provedení této úlohy by bylo mnohem náročnější.</span><span class="sxs-lookup"><span data-stu-id="d6793-123">Writing code to manually traverse the XML document to perform this task would be far more challenging.</span></span>

<span data-ttu-id="d6793-124">Interakce s XML není jedinou věcí, kterou můžete dělat s poskytovateli LINQ.</span><span class="sxs-lookup"><span data-stu-id="d6793-124">Interacting with XML isn’t the only thing you can do with LINQ Providers.</span></span> <span data-ttu-id="d6793-125">[LINQ to SQL](../framework/data/adonet/sql/linq/index.md) je poměrně prosté objekty – relační mapování (ORM) pro databázi serveru MSSQL.</span><span class="sxs-lookup"><span data-stu-id="d6793-125">[Linq to SQL](../framework/data/adonet/sql/linq/index.md) is a fairly bare-bones Object-Relational Mapper (ORM) for an MSSQL Server Database.</span></span> <span data-ttu-id="d6793-126">Knihovna [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) poskytuje efektivní procházení dokumentů JSON prostřednictvím LINQ.</span><span class="sxs-lookup"><span data-stu-id="d6793-126">The [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) library provides efficient JSON Document traversal via LINQ.</span></span> <span data-ttu-id="d6793-127">Kromě toho, pokud není k dispozici knihovna, která vyžaduje, můžete také [napsat vlastního poskytovatele LINQ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110)).</span><span class="sxs-lookup"><span data-stu-id="d6793-127">Furthermore, if there isn’t a library which does what you need, you can also [write your own LINQ Provider](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))!</span></span>

## <a name="why-use-the-query-syntax"></a><span data-ttu-id="d6793-128">Proč použít syntaxi dotazu?</span><span class="sxs-lookup"><span data-stu-id="d6793-128">Why Use the Query Syntax?</span></span>

<span data-ttu-id="d6793-129">Jedná se o otázku, která se často vyskytuje.</span><span class="sxs-lookup"><span data-stu-id="d6793-129">This is a question which often comes up.</span></span> <span data-ttu-id="d6793-130">Po všech těchto případech to</span><span class="sxs-lookup"><span data-stu-id="d6793-130">After all, this,</span></span>

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

```vb
Dim filteredItems = myItems.Where(Function(item) item.Foo)
```

<span data-ttu-id="d6793-131">je mnohem výstižnější než toto:</span><span class="sxs-lookup"><span data-stu-id="d6793-131">is a lot more concise than this:</span></span>

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

<span data-ttu-id="d6793-132">Není syntaxí rozhraní API jenom výstižnější způsob, jak provádět syntaxi dotazů?</span><span class="sxs-lookup"><span data-stu-id="d6793-132">Isn’t the API syntax just a more concise way to do the query syntax?</span></span>

<span data-ttu-id="d6793-133">No.</span><span class="sxs-lookup"><span data-stu-id="d6793-133">No.</span></span> <span data-ttu-id="d6793-134">Syntaxe dotazu umožňuje použití klauzule **let** , která umožňuje začlenit a vytvořit jeho proměnnou v rámci rozsahu výrazu a použít ji v následných částech výrazu.</span><span class="sxs-lookup"><span data-stu-id="d6793-134">The query syntax allows for the use of the **let** clause, which allows you to introduce and bind a variable within the scope of the expression, using it in subsequent pieces of the expression.</span></span> <span data-ttu-id="d6793-135">Reprodukce stejného kódu jenom pomocí syntaxe rozhraní API se dá provést, ale nejpravděpodobnější příčinou je, že je obtížné číst kód.</span><span class="sxs-lookup"><span data-stu-id="d6793-135">Reproducing the same code with only the API syntax can be done, but will most likely lead to code which is hard to read.</span></span>

<span data-ttu-id="d6793-136">Takže byste to begs na otázku, **měli byste pouze použít syntaxi dotazu?**</span><span class="sxs-lookup"><span data-stu-id="d6793-136">So this begs the question, **should you just use the query syntax?**</span></span>

<span data-ttu-id="d6793-137">Odpověď na tuto otázku je **Ano** , pokud...</span><span class="sxs-lookup"><span data-stu-id="d6793-137">The answer to this question is **yes** if...</span></span>

* <span data-ttu-id="d6793-138">Existující základ kódu už používá syntaxi dotazu.</span><span class="sxs-lookup"><span data-stu-id="d6793-138">Your existing codebase already uses the query syntax</span></span>
* <span data-ttu-id="d6793-139">V důsledku složitosti je potřeba oborovat proměnné v dotazech.</span><span class="sxs-lookup"><span data-stu-id="d6793-139">You need to scope variables within your queries due to complexity</span></span>
* <span data-ttu-id="d6793-140">Dáváte přednost syntaxi dotazů a nebude se navíc z vašeho základu kódu.</span><span class="sxs-lookup"><span data-stu-id="d6793-140">You prefer the query syntax and it won’t distract from your codebase</span></span>

<span data-ttu-id="d6793-141">Odpověď na tuto **otázku není v případě.** ..</span><span class="sxs-lookup"><span data-stu-id="d6793-141">The answer to this question is **no** if...</span></span>

* <span data-ttu-id="d6793-142">Existující základ kódu už používá syntaxi rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="d6793-142">Your existing codebase already uses the API syntax</span></span>
* <span data-ttu-id="d6793-143">V rámci dotazů nemusíte oborovat proměnné.</span><span class="sxs-lookup"><span data-stu-id="d6793-143">You have no need to scope variables within your queries</span></span>
* <span data-ttu-id="d6793-144">Dáváte přednost syntaxi rozhraní API a nebude se navíc z vašeho základu kódu.</span><span class="sxs-lookup"><span data-stu-id="d6793-144">You prefer the API syntax and it won’t distract from your codebase</span></span>

## <a name="essential-samples"></a><span data-ttu-id="d6793-145">Základní ukázky</span><span class="sxs-lookup"><span data-stu-id="d6793-145">Essential Samples</span></span>

<span data-ttu-id="d6793-146">Úplný seznam ukázek LINQ najdete v [101Ch ukázkách LINQ](https://docs.microsoft.com/samples/dotnet/try-samples/101-linq-samples/).</span><span class="sxs-lookup"><span data-stu-id="d6793-146">For a truly comprehensive list of LINQ samples, visit [101 LINQ Samples](https://docs.microsoft.com/samples/dotnet/try-samples/101-linq-samples/).</span></span>

<span data-ttu-id="d6793-147">Následuje rychlá ukázka některých základních částí jazyka LINQ.</span><span class="sxs-lookup"><span data-stu-id="d6793-147">The following is a quick demonstration of some of the essential pieces of LINQ.</span></span> <span data-ttu-id="d6793-148">Tato možnost není nijak ucelená, protože LINQ poskytuje výrazně více funkcí, než se tady prezentuje.</span><span class="sxs-lookup"><span data-stu-id="d6793-148">This is in no way comprehensive, as LINQ provides significantly more functionality than what is showcased here.</span></span>

* <span data-ttu-id="d6793-149">Chléb a máslo –, `Where` `Select` a `Aggregate` :</span><span class="sxs-lookup"><span data-stu-id="d6793-149">The bread and butter - `Where`, `Select`, and `Aggregate`:</span></span>

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

* <span data-ttu-id="d6793-150">Sloučení seznamu seznamů:</span><span class="sxs-lookup"><span data-stu-id="d6793-150">Flattening a list of lists:</span></span>

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

```vb
' Transforms the list of kennels into a list of all their dogs.
Dim allDogsFromKennels = kennels.SelectMany(Function(kennel) kennel.Dogs)
```

* <span data-ttu-id="d6793-151">Sjednocení mezi dvěma sadami (s vlastním komparátor):</span><span class="sxs-lookup"><span data-stu-id="d6793-151">Union between two sets (with custom comparator):</span></span>

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

* <span data-ttu-id="d6793-152">Průnik dvou sad:</span><span class="sxs-lookup"><span data-stu-id="d6793-152">Intersection between two sets:</span></span>

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

* <span data-ttu-id="d6793-153">Třídění</span><span class="sxs-lookup"><span data-stu-id="d6793-153">Ordering:</span></span>

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

* <span data-ttu-id="d6793-154">Nakonec pokročilejší vzorek: určení, jestli se hodnoty vlastností dvou instancí stejného typu rovnají (jsou vypůjčené a upravené z [tohoto příspěvku StackOverflow](https://stackoverflow.com/a/844855)):</span><span class="sxs-lookup"><span data-stu-id="d6793-154">Finally, a more advanced sample: determining if the values of the properties of two instances of the same type are equal (Borrowed and modified from [this StackOverflow post](https://stackoverflow.com/a/844855)):</span></span>

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

```vb
<System.Runtime.CompilerServices.Extension()>
Public Function PublicInstancePropertiesEqual(Of T As Class)(self As T, [to] As T, ParamArray ignore As String()) As Boolean
    If self Is Nothing OrElse [to] Is Nothing Then
        Return self Is [to]
    End If

    ' Selects the properties which have unequal values into a sequence of those properties.
    Dim unequalProperties = From [property] In GetType(T).GetProperties(BindingFlags.Public Or BindingFlags.Instance)
                            Where Not ignore.Contains([property].Name)
                            Let selfValue = [property].GetValue(self, Nothing)
                            Let toValue = [property].GetValue([to], Nothing)
                            Where Not Equals(selfValue, toValue) Select [property]
    Return Not unequalProperties.Any()
End Function
```

## <a name="plinq"></a><span data-ttu-id="d6793-155">PLINQ</span><span class="sxs-lookup"><span data-stu-id="d6793-155">PLINQ</span></span>

<span data-ttu-id="d6793-156">PLINQ nebo Paralelní LINQ je paralelní prováděcí modul pro výrazy LINQ.</span><span class="sxs-lookup"><span data-stu-id="d6793-156">PLINQ, or Parallel LINQ, is a parallel execution engine for LINQ expressions.</span></span> <span data-ttu-id="d6793-157">Jinými slovy regulární výraz LINQ může být triviální paralelní napříč libovolným počtem vláken.</span><span class="sxs-lookup"><span data-stu-id="d6793-157">In other words, a regular LINQ expression can be trivially parallelized across any number of threads.</span></span> <span data-ttu-id="d6793-158">To je provedeno prostřednictvím volání `AsParallel()` předcházejícího výrazu.</span><span class="sxs-lookup"><span data-stu-id="d6793-158">This is accomplished via a call to `AsParallel()` preceding the expression.</span></span>

<span data-ttu-id="d6793-159">Zvažte použití těchto zdrojů:</span><span class="sxs-lookup"><span data-stu-id="d6793-159">Consider the following:</span></span>

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

<span data-ttu-id="d6793-160">Tento kód bude v případě potřeby rozdělit do `facebookUsers` celého systémového vlákna a celková hodnota se v každém vlákně sečte, sečte výsledky vypočítané každým vláknem a projekt, který je výsledkem skvělého řetězce.</span><span class="sxs-lookup"><span data-stu-id="d6793-160">This code will partition `facebookUsers` across system threads as necessary, sum up the total likes on each thread in parallel, sum the results computed by each thread, and project that result into a nice string.</span></span>

<span data-ttu-id="d6793-161">Ve tvaru diagramu:</span><span class="sxs-lookup"><span data-stu-id="d6793-161">In diagram form:</span></span>

![Diagram PLINQ](./media/using-linq/plinq-diagram.png)

<span data-ttu-id="d6793-163">Paralelizovat úlohy vázané na procesor, které je možné snadno vyjádřit prostřednictvím LINQ (jinými slovy, jsou čistě funkce a nemají žádné vedlejší účinky) jsou skvělým kandidátem na PLINQ.</span><span class="sxs-lookup"><span data-stu-id="d6793-163">Parallelizable CPU-bound jobs which can be easily expressed via LINQ (in other words, are pure functions and have no side effects) are a great candidate for PLINQ.</span></span> <span data-ttu-id="d6793-164">Pro úlohy, _které mají_ vedlejší efekt, zvažte použití [paralelní knihovny Tasks](./parallel-programming/task-parallel-library-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="d6793-164">For jobs which _do_ have a side effect, consider using the [Task Parallel Library](./parallel-programming/task-parallel-library-tpl.md).</span></span>

## <a name="further-resources"></a><span data-ttu-id="d6793-165">Další zdroje informací:</span><span class="sxs-lookup"><span data-stu-id="d6793-165">Further Resources:</span></span>

* [<span data-ttu-id="d6793-166">Ukázky 101 LINQ</span><span class="sxs-lookup"><span data-stu-id="d6793-166">101 LINQ Samples</span></span>](https://docs.microsoft.com/samples/dotnet/try-samples/101-linq-samples/)
* <span data-ttu-id="d6793-167">[Linqpad](https://www.linqpad.net/), prostředí Playground a stroj pro dotazování databáze pro C#/F # webový Basic</span><span class="sxs-lookup"><span data-stu-id="d6793-167">[Linqpad](https://www.linqpad.net/), a playground environment and Database querying engine for C#/F#/Visual Basic</span></span>
* <span data-ttu-id="d6793-168">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), pro učení, jak se implementuje LINQ-to-Objects</span><span class="sxs-lookup"><span data-stu-id="d6793-168">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), an e-book for learning how LINQ-to-objects is implemented</span></span>
