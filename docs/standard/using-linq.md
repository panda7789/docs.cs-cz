---
title: LINQ (jazykový integrovaný dotaz)
description: Zjistěte, jak LINQ poskytuje možnosti dotazování na úrovni jazyka a rozhraní API pro C# a Visual Basic jako způsob psaní expresivního, deklarativního kódu.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: c00939e1-59e3-4e61-8fe9-08ad6b3f1295
ms.openlocfilehash: eafd8f78c3d8de1ba064021111f869571d5a570f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160323"
---
# <a name="linq-language-integrated-query"></a><span data-ttu-id="9c525-103">LINQ (jazykový integrovaný dotaz)</span><span class="sxs-lookup"><span data-stu-id="9c525-103">LINQ (Language Integrated Query)</span></span>

## <a name="what-is-it"></a><span data-ttu-id="9c525-104">Co je to?</span><span class="sxs-lookup"><span data-stu-id="9c525-104">What is it?</span></span>

<span data-ttu-id="9c525-105">LINQ poskytuje možnosti dotazování na úrovni jazyka a rozhraní API [funkce vyššího řádu](https://en.wikipedia.org/wiki/Higher-order_function) pro c# a visual basic jako způsob psaní expresivního deklarativního kódu.</span><span class="sxs-lookup"><span data-stu-id="9c525-105">LINQ provides language-level querying capabilities and a [higher-order function](https://en.wikipedia.org/wiki/Higher-order_function) API to C# and Visual Basic as a way to write expressive, declarative code.</span></span>

<span data-ttu-id="9c525-106">Syntaxe dotazu na úrovni jazyka:</span><span class="sxs-lookup"><span data-stu-id="9c525-106">Language-level query syntax:</span></span>

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

<span data-ttu-id="9c525-107">Stejný příklad `IEnumerable<T>` pomocí rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="9c525-107">Same example using the `IEnumerable<T>` API:</span></span>

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

```vb
Dim linqExperts = programmers.Where(Function(p) p.IsNewToLINQ).
                             Select(Function(p) New LINQExpert(p))
```

## <a name="linq-is-expressive"></a><span data-ttu-id="9c525-108">LINQ je expresivní</span><span class="sxs-lookup"><span data-stu-id="9c525-108">LINQ is Expressive</span></span>

<span data-ttu-id="9c525-109">Představte si, že máte seznam domácích mazlíčků, ale chcete jej převést do slovníku, kde můžete přistupovat k domácímu mazlíčku přímo podle jeho `RFID` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9c525-109">Imagine you have a list of pets, but want to convert it into a dictionary where you can access a pet directly by its `RFID` value.</span></span>

<span data-ttu-id="9c525-110">Tradiční imperativní kód:</span><span class="sxs-lookup"><span data-stu-id="9c525-110">Traditional imperative code:</span></span>

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

<span data-ttu-id="9c525-111">Záměrem kódu není vytvořit nový `Dictionary<int, Pet>` a přidat k němu pomocí smyčky, je převést existující seznam do slovníku!</span><span class="sxs-lookup"><span data-stu-id="9c525-111">The intention behind the code is not to create a new `Dictionary<int, Pet>` and add to it via a loop, it is to convert an existing list into a dictionary!</span></span> <span data-ttu-id="9c525-112">LINQ zachovává záměr vzhledem k tomu, že imperativní kód není.</span><span class="sxs-lookup"><span data-stu-id="9c525-112">LINQ preserves the intention whereas the imperative code does not.</span></span>

<span data-ttu-id="9c525-113">Ekvivalentní výraz LINQ:</span><span class="sxs-lookup"><span data-stu-id="9c525-113">Equivalent LINQ expression:</span></span>

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

```vb
Dim petLookup = pets.ToDictionary(Function(pet) pet.RFID)
```

<span data-ttu-id="9c525-114">Kód pomocí LINQ je cenná, protože vyrovnává hrací pole mezi záměrem a kódem při uvažování jako programátor.</span><span class="sxs-lookup"><span data-stu-id="9c525-114">The code using LINQ is valuable because it evens the playing field between intent and code when reasoning as a programmer.</span></span> <span data-ttu-id="9c525-115">Dalším bonusem je stručnost kódu.</span><span class="sxs-lookup"><span data-stu-id="9c525-115">Another bonus is code brevity.</span></span> <span data-ttu-id="9c525-116">Představte si, že snížíte velké části základu kódu o 1/3, jak je uvedeno výše.</span><span class="sxs-lookup"><span data-stu-id="9c525-116">Imagine reducing large portions of a codebase by 1/3 as done above.</span></span> <span data-ttu-id="9c525-117">Docela sladká dohoda, že?</span><span class="sxs-lookup"><span data-stu-id="9c525-117">Pretty sweet deal, right?</span></span>

## <a name="linq-providers-simplify-data-access"></a><span data-ttu-id="9c525-118">Poskytovatelé LINQ zjednodušují přístup k datům</span><span class="sxs-lookup"><span data-stu-id="9c525-118">LINQ Providers Simplify Data Access</span></span>

<span data-ttu-id="9c525-119">Pro značnou část softwaru ve volné přírodě se vše točí kolem nakládání s daty z nějakého zdroje (databáze, JSON, XML atd.).</span><span class="sxs-lookup"><span data-stu-id="9c525-119">For a significant chunk of software out in the wild, everything revolves around dealing with data from some source (Databases, JSON, XML, etc).</span></span> <span data-ttu-id="9c525-120">Často to zahrnuje učení nové rozhraní API pro každý zdroj dat, což může být nepříjemné.</span><span class="sxs-lookup"><span data-stu-id="9c525-120">Often this involves learning a new API for each data source, which can be annoying.</span></span> <span data-ttu-id="9c525-121">LINQ to zjednodušuje abstrakcí běžných prvků přístupu k datům do syntaxe dotazu, která vypadá stejně bez ohledu na to, který zdroj dat vyberete.</span><span class="sxs-lookup"><span data-stu-id="9c525-121">LINQ simplifies this by abstracting common elements of data access into a query syntax which looks the same no matter which data source you pick.</span></span>

<span data-ttu-id="9c525-122">Zvažte následující: nalezení všech elementů XML s určitou hodnotou atributu.</span><span class="sxs-lookup"><span data-stu-id="9c525-122">Consider the following: finding all XML elements with a specific attribute value.</span></span>

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

<span data-ttu-id="9c525-123">Psaní kódu pro ruční procházení dokumentu XML k provedení tohoto úkolu by bylo mnohem náročnější.</span><span class="sxs-lookup"><span data-stu-id="9c525-123">Writing code to manually traverse the XML document to perform this task would be far more challenging.</span></span>

<span data-ttu-id="9c525-124">Interakce s XML není jediná věc, kterou můžete dělat s poskytovateli LINQ.</span><span class="sxs-lookup"><span data-stu-id="9c525-124">Interacting with XML isn’t the only thing you can do with LINQ Providers.</span></span> <span data-ttu-id="9c525-125">[Linq to SQL](../../docs/framework/data/adonet/sql/linq/index.md) je poměrně holý objekt-relační mapovač (ORM) pro databázi serveru MSSQL.</span><span class="sxs-lookup"><span data-stu-id="9c525-125">[Linq to SQL](../../docs/framework/data/adonet/sql/linq/index.md) is a fairly bare-bones Object-Relational Mapper (ORM) for an MSSQL Server Database.</span></span> <span data-ttu-id="9c525-126">Knihovna [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) poskytuje efektivní průchod dokumentu JSON prostřednictvím LINQ.</span><span class="sxs-lookup"><span data-stu-id="9c525-126">The [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) library provides efficient JSON Document traversal via LINQ.</span></span> <span data-ttu-id="9c525-127">Kromě toho, pokud není knihovna, která dělá to, co potřebujete, můžete také [napsat svůj vlastní LINQ Provider](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))!</span><span class="sxs-lookup"><span data-stu-id="9c525-127">Furthermore, if there isn’t a library which does what you need, you can also [write your own LINQ Provider](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))!</span></span>

## <a name="why-use-the-query-syntax"></a><span data-ttu-id="9c525-128">Proč použít syntaxi dotazu?</span><span class="sxs-lookup"><span data-stu-id="9c525-128">Why Use the Query Syntax?</span></span>

<span data-ttu-id="9c525-129">To je otázka, která často přichází.</span><span class="sxs-lookup"><span data-stu-id="9c525-129">This is a question which often comes up.</span></span> <span data-ttu-id="9c525-130">Koneckonců, toto,</span><span class="sxs-lookup"><span data-stu-id="9c525-130">After all, this,</span></span>

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

```vb
Dim filteredItems = myItems.Where(Function(item) item.Foo)
```

<span data-ttu-id="9c525-131">je mnohem stručnější než toto:</span><span class="sxs-lookup"><span data-stu-id="9c525-131">is a lot more concise than this:</span></span>

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

<span data-ttu-id="9c525-132">Není syntaxe rozhraní API jen stručnější způsob, jak provést syntaxi dotazu?</span><span class="sxs-lookup"><span data-stu-id="9c525-132">Isn’t the API syntax just a more concise way to do the query syntax?</span></span>

<span data-ttu-id="9c525-133">Ne.</span><span class="sxs-lookup"><span data-stu-id="9c525-133">No.</span></span> <span data-ttu-id="9c525-134">Syntaxe dotazu umožňuje použití **let** klauzule, která umožňuje zavést a vázat proměnnou v rámci oboru výrazu, pomocí v následujících částech výrazu.</span><span class="sxs-lookup"><span data-stu-id="9c525-134">The query syntax allows for the use of the **let** clause, which allows you to introduce and bind a variable within the scope of the expression, using it in subsequent pieces of the expression.</span></span> <span data-ttu-id="9c525-135">Reprodukovat stejný kód pouze syntaxe rozhraní API lze provést, ale s největší pravděpodobností povede ke kódu, který je těžko čitelný.</span><span class="sxs-lookup"><span data-stu-id="9c525-135">Reproducing the same code with only the API syntax can be done, but will most likely lead to code which is hard to read.</span></span>

<span data-ttu-id="9c525-136">Takže to vyvolává otázku, **měli byste prostě použít syntaxi dotazu?**</span><span class="sxs-lookup"><span data-stu-id="9c525-136">So this begs the question, **should you just use the query syntax?**</span></span>

<span data-ttu-id="9c525-137">Odpověď na tuto otázku zní **ano,** pokud...</span><span class="sxs-lookup"><span data-stu-id="9c525-137">The answer to this question is **yes** if...</span></span>

* <span data-ttu-id="9c525-138">Stávající základ kódu již používá syntaxi dotazu.</span><span class="sxs-lookup"><span data-stu-id="9c525-138">Your existing codebase already uses the query syntax</span></span>
* <span data-ttu-id="9c525-139">Proměnné v rámci dotazů je třeba z důvodu složitosti</span><span class="sxs-lookup"><span data-stu-id="9c525-139">You need to scope variables within your queries due to complexity</span></span>
* <span data-ttu-id="9c525-140">Dáváte přednost syntaxi dotazu a nebude odvádět pozornost od základu kódu</span><span class="sxs-lookup"><span data-stu-id="9c525-140">You prefer the query syntax and it won’t distract from your codebase</span></span>

<span data-ttu-id="9c525-141">Odpověď na tuto otázku je **ne,** pokud ...</span><span class="sxs-lookup"><span data-stu-id="9c525-141">The answer to this question is **no** if...</span></span>

* <span data-ttu-id="9c525-142">Stávající základ kódu již používá syntaxi rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="9c525-142">Your existing codebase already uses the API syntax</span></span>
* <span data-ttu-id="9c525-143">Není nutné obor proměnné v rámci dotazů</span><span class="sxs-lookup"><span data-stu-id="9c525-143">You have no need to scope variables within your queries</span></span>
* <span data-ttu-id="9c525-144">Dáváte přednost syntaxi rozhraní API a nebude odvádět pozornost od vašeho základu kódu</span><span class="sxs-lookup"><span data-stu-id="9c525-144">You prefer the API syntax and it won’t distract from your codebase</span></span>

## <a name="essential-samples"></a><span data-ttu-id="9c525-145">Základní vzorky</span><span class="sxs-lookup"><span data-stu-id="9c525-145">Essential Samples</span></span>

<span data-ttu-id="9c525-146">Pro skutečně komplexní seznam linq vzorků, navštivte [101 LINQ vzorky](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).</span><span class="sxs-lookup"><span data-stu-id="9c525-146">For a truly comprehensive list of LINQ samples, visit [101 LINQ Samples](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).</span></span>

<span data-ttu-id="9c525-147">Následuje rychlá ukázka některých základních částí LINQ.</span><span class="sxs-lookup"><span data-stu-id="9c525-147">The following is a quick demonstration of some of the essential pieces of LINQ.</span></span> <span data-ttu-id="9c525-148">To není v žádném případě komplexní, protože LINQ poskytuje výrazně více funkcí, než to, co je zde prezentováno.</span><span class="sxs-lookup"><span data-stu-id="9c525-148">This is in no way comprehensive, as LINQ provides significantly more functionality than what is showcased here.</span></span>

* <span data-ttu-id="9c525-149">Chléb a máslo `Where` `Select`- `Aggregate`, a:</span><span class="sxs-lookup"><span data-stu-id="9c525-149">The bread and butter - `Where`, `Select`, and `Aggregate`:</span></span>

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

* <span data-ttu-id="9c525-150">Sloučení seznamu seznamů:</span><span class="sxs-lookup"><span data-stu-id="9c525-150">Flattening a list of lists:</span></span>

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

```vb
' Transforms the list of kennels into a list of all their dogs.
Dim allDogsFromKennels = kennels.SelectMany(Function(kennel) kennel.Dogs)
```

* <span data-ttu-id="9c525-151">Sjednocení mezi dvěma sadami (s vlastním komparátorem):</span><span class="sxs-lookup"><span data-stu-id="9c525-151">Union between two sets (with custom comparator):</span></span>

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

* <span data-ttu-id="9c525-152">Průsečík mezi dvěma sadami:</span><span class="sxs-lookup"><span data-stu-id="9c525-152">Intersection between two sets:</span></span>

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

* <span data-ttu-id="9c525-153">Objednávání:</span><span class="sxs-lookup"><span data-stu-id="9c525-153">Ordering:</span></span>

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

* <span data-ttu-id="9c525-154">Nakonec pokročilejší ukázka: určení, zda jsou hodnoty vlastností dvou instancí stejného typu stejného typu stejného typu stejného typu stejného typu stejného typu stejného typu stejného typu stejného typu jsou stejné (Vypůjčené a upravené z [tohoto stackoverflow post](https://stackoverflow.com/a/844855)):</span><span class="sxs-lookup"><span data-stu-id="9c525-154">Finally, a more advanced sample: determining if the values of the properties of two instances of the same type are equal (Borrowed and modified from [this StackOverflow post](https://stackoverflow.com/a/844855)):</span></span>

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

## <a name="plinq"></a><span data-ttu-id="9c525-155">PLINQ</span><span class="sxs-lookup"><span data-stu-id="9c525-155">PLINQ</span></span>

<span data-ttu-id="9c525-156">PLINQ, nebo Paralelní LINQ, je paralelní spuštění motoru pro výrazy LINQ.</span><span class="sxs-lookup"><span data-stu-id="9c525-156">PLINQ, or Parallel LINQ, is a parallel execution engine for LINQ expressions.</span></span> <span data-ttu-id="9c525-157">Jinými slovy regulární výraz LINQ může být triviálně paralelizován v libovolném počtu vláken.</span><span class="sxs-lookup"><span data-stu-id="9c525-157">In other words, a regular LINQ expression can be trivially parallelized across any number of threads.</span></span> <span data-ttu-id="9c525-158">To je dosaženo prostřednictvím `AsParallel()` volání před výraz.</span><span class="sxs-lookup"><span data-stu-id="9c525-158">This is accomplished via a call to `AsParallel()` preceding the expression.</span></span>

<span data-ttu-id="9c525-159">Zvažte použití těchto zdrojů:</span><span class="sxs-lookup"><span data-stu-id="9c525-159">Consider the following:</span></span>

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

<span data-ttu-id="9c525-160">Tento kód `facebookUsers` bude oddíl mezi podprocesy systému podle potřeby, shrnout celkový líbí na každém vlákně paralelně, součet výsledků vypočítaných každým vláknem a projekt, který výsledkem je do pěkný řetězec.</span><span class="sxs-lookup"><span data-stu-id="9c525-160">This code will partition `facebookUsers` across system threads as necessary, sum up the total likes on each thread in parallel, sum the results computed by each thread, and project that result into a nice string.</span></span>

<span data-ttu-id="9c525-161">Ve formě diagramu:</span><span class="sxs-lookup"><span data-stu-id="9c525-161">In diagram form:</span></span>

![PLINQ diagram](./media/using-linq/plinq-diagram.png)

<span data-ttu-id="9c525-163">Paralelní úlohy vázané na cpu, které lze snadno vyjádřit pomocí LINQ (jinými slovy, jsou čisté funkce a nemají žádné vedlejší účinky) jsou skvělým kandidátem pro PLINQ.</span><span class="sxs-lookup"><span data-stu-id="9c525-163">Parallelizable CPU-bound jobs which can be easily expressed via LINQ (in other words, are pure functions and have no side effects) are a great candidate for PLINQ.</span></span> <span data-ttu-id="9c525-164">U úloh, které _mají_ vedlejší účinek, zvažte použití [paralelní knihovny úloh](./parallel-programming/task-parallel-library-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="9c525-164">For jobs which _do_ have a side effect, consider using the [Task Parallel Library](./parallel-programming/task-parallel-library-tpl.md).</span></span>

## <a name="further-resources"></a><span data-ttu-id="9c525-165">Další zdroje informací:</span><span class="sxs-lookup"><span data-stu-id="9c525-165">Further Resources:</span></span>

* [<span data-ttu-id="9c525-166">101 VZORKŮ LINQ</span><span class="sxs-lookup"><span data-stu-id="9c525-166">101 LINQ Samples</span></span>](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)
* <span data-ttu-id="9c525-167">[Linqpad](https://www.linqpad.net/), prostředí hřiště a databázový dotazovací stroj pro c#/f#/visual basic</span><span class="sxs-lookup"><span data-stu-id="9c525-167">[Linqpad](https://www.linqpad.net/), a playground environment and Database querying engine for C#/F#/Visual Basic</span></span>
* <span data-ttu-id="9c525-168">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), e-kniha pro učení, jak linq-to-objekty jsou implementovány</span><span class="sxs-lookup"><span data-stu-id="9c525-168">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), an e-book for learning how LINQ-to-objects is implemented</span></span>
