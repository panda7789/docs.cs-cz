---
title: LINQ (Language integrovaného dotazu)
description: Zjistěte, jak LINQ poskytuje funkce dotazování úroveň jazyka a rozhraní API jazyka C# a VB jako způsob, jak napsat kód výrazovou, deklarativní.
keywords: Rozhraní .NET, .NET core
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: c00939e1-59e3-4e61-8fe9-08ad6b3f1295
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5ce6819abee90ceccc52a79f8bda794f2fd345fb
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="linq-language-integrated-query"></a>LINQ (Language integrovaného dotazu)

## <a name="what-is-it"></a>Co to je?

LINQ poskytuje funkce dotazování úroveň jazyka a [vyšší pořadí funkce](https://en.wikipedia.org/wiki/Higher-order_function) rozhraní API jazyka C# a VB jako způsob, jak napsat kód výrazovou, deklarativní.

Syntaxe dotazu úroveň jazyka:

```csharp
var linqExperts = from p in programmers
                  where p.IsNewToLINQ
                  select new LINQExpert(p);
```

Pomocí stejné příklad `IEnumerable<T>` rozhraní API:

```csharp
var linqExperts = programmers.Where(p => IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

## <a name="linq-is-expressive"></a>LINQ je Expressive

Představte si máte seznam mazlíčků, ale chcete převést do slovníku umožňující přístup mazlíčky přímo pomocí jeho `RFID` hodnotu.

Tradiční imperativní kód:

```csharp
var petLookup = new Dictionary<int, Pet>();

foreach (var pet in pets)
{
    petLookup.Add(pet.RFID, pet);
}
```

Je záměrem za kód není pro vytvoření nového `Dictionary<int, Pet>` a přidejte do ní prostřednictvím smyčku, je pro převod existujícího seznamu do slovníku! LINQ zachovává záměrem, zatímco kód imperativní neexistuje.

Ekvivalentní výrazu LINQ:

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

Kód pomocí LINQ se hodí v situaci, protože evens pole přehrávání mezi záměr a kódem, když důvody jako programátoři. Další výhoda je jako stručný výtah kódu. Představte si velké části codebase redukování 1/3 jako provést výše. Poměrně sladké pozornosti, pravé?

## <a name="linq-providers-simplify-data-access"></a>Zprostředkovatelé LINQ zjednodušit přístup k datům

U významné bloku softwaru stanovené v zástupné vše, co se pohybuje kolem práci s daty z některé zdroje (databáze, JSON, XML atd.). Často to zahrnuje nové rozhraní API pro každý zdroj dat, což může být nepříjemných učení. Technologie LINQ to zjednodušuje tím, že poskytuje abstrakci společné prvky přístup k datům do syntaxe dotazu, který vypadá stejně bez ohledu na to, jaké zdroje dat vyberte.

Vezměte v úvahu následující: vyhledání všech elementů XML s hodnotou určitým atributem.

```csharp
public static IEnumerable<XElement> FindAllElementsWithAttribute(XElement documentRoot, string elementName,
                                           string attributeName, string value)
{
    return from el in documentRoot.Elements(elementName)
           where (string)el.Element(attributeName) == value
           select el;
}
```

Psaní kódu ručně procházení v dokumentu XML k provedení této úlohy bude podstatně více náročné.

Jediné, co můžete provést zprostředkovatelům LINQ interakci se souborem XML není. [Technologie LINQ to SQL](../../docs/framework/data/adonet/sql/linq/index.md) je poměrně holou objekt relační Mapper (ORM) pro databázi MSSQL serveru. [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) knihovna nabízí efektivní traversal dokumentu JSON prostřednictvím LINQ. Kromě toho, pokud není k dispozici knihovnu, která zajišťuje, co potřebujete, můžete také [napsat vlastního zprostředkovatele LINQ](https://msdn.microsoft.com/library/Bb546158.aspx)!

## <a name="why-use-the-query-syntax"></a>Proč používat syntaxi dotazu?

Toto je otázku, která se často zobrazí. Po všech, se

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

je mnohem přesnější než toto:

```csharp
var filteredItems = from item in myItems
                    where item.Foo
                    select item;
```

Syntaxe rozhraní API není právě přesnější způsob, jak provést syntaxe dotazu?

Ne. Umožňuje použití syntaxe dotazu **let** klauzuli, která umožňuje zavádět a vytvořte vazbu proměnné v rámci oboru výrazem s použitím v další části výrazu. Reprodukci stejný kód se pouze syntaxí rozhraní API lze provést, ale pravděpodobně povede k kódu, který se těžko čitelný.

Proto to begs na otázku **by měla pouze použijete syntaxi dotazu?**

Odpověď na tuto otázku **Ano** Pokud...

*   Stávající codebase již používá syntaxi dotazu
*   Obor proměnné je potřeba v rámci své dotazy z důvodu složitosti
*   Dáváte přednost syntaxe dotazu a nebude rušil vaší základu kódu

Odpověď na tuto otázku **žádné** Pokud...

*   Stávající codebase již používá syntaxi rozhraní API
*   Máte potřeba proměnných rozsahu v rámci své dotazy
*   Dáváte přednost syntaxe rozhraní API a nebude rušil vaší základu kódu

## <a name="essential-samples"></a>Základní ukázky

Skutečně úplný seznam ukázky LINQ, najdete v článku [101 ukázky LINQ](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).

Následuje ukázka rychlé některé důležité údaje LINQ. Toto je nijak komplexní, LINQ, které poskytuje výrazně víc funkcí než co je showcased sem.

*   Másla a chléb - `Where`, `Select`, a `Aggregate`:

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

*   Vyrovnání seznam seznamů:

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

*   Spojení mezi dvěma sadami (s vlastní komparátoru):

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

*   Průnik mezi dvěma sadami:

```csharp
// Gets the volunteers who spend share time with two humane societies.
var volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     new VolunteerTimeComparer());
```

*   Řazení:

```csharp
// Get driving directions, ordering by if it's toll-free before estimated driving time.
var results = DirectionsProcessor.GetDirections(start, end)
              .OrderBy(direction => direction.HasNoTolls)
              .ThenBy(direction => direction.EstimatedTime);
```

*   Nakonec další pokročilé ukázka: určení, jestli jsou stejné hodnoty vlastnosti dvě instance stejného typu (Borrowed a upravených z [tento příspěvek StackOverflow](http://stackoverflow.com/a/844855)):

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

## <a name="plinq"></a>PLINQ

Paralelní provádění modul pro LINQ – výrazy se PLINQ nebo paralelní LINQ. Jinými slovy regulární výrazy LINQ může být trivially paralelizovaná málo napříč libovolný počet vláken. To se provádí prostřednictvím volání `AsParallel()` před výrazem.

Zvažte následující:

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

Tento kód bude oddílu `facebookUsers` napříč vlákny systému podle potřeby součet až celkový líbí na každé vlákno paralelně, aby součet výsledky počítaný jednotlivými vlákny a projektu tento výsledek na dobrý řetězec.

Ve formuláři diagram:

![PLINQ diagram](./media/using-linq/plinq-diagram.png)

Paralelní úlohy vázané na procesor, které lze snadno vyjádřit pomocí LINQ (jinými slovy, jsou čistá funkce a mít žádné vedlejší účinky) jsou skvělý kandidátem pro PLINQ. Pro úlohy, které _provést_ mít vedlejším účinkem, zvažte použití [Task Parallel Library](./parallel-programming/task-parallel-library-tpl.md).

## <a name="further-resources"></a>Další prostředky:

*   [101 ukázky LINQ](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)
*   [Linqpad](https://www.linqpad.net/), playground prostředí a databázové dotazy modul pro C# /F # / VB.
*   [EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), zde elektronickou knihu pro učení, jak je implementována LINQ na objekty
