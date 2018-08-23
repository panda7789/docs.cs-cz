---
title: LINQ (Language Integrated Query)
description: Zjistěte, jak LINQ poskytuje možnosti dotazování úrovni jazyka a rozhraní API pro C# a VB jako způsob, jak napsat kód výrazová, deklarativní.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: c00939e1-59e3-4e61-8fe9-08ad6b3f1295
ms.openlocfilehash: 4e6e361666b6b6ae36b7d4bf02af55a379c8e16e
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2018
ms.locfileid: "42752194"
---
# <a name="linq-language-integrated-query"></a>LINQ (Language Integrated Query)

## <a name="what-is-it"></a>Co to je?

LINQ poskytuje možnosti dotazování úrovni jazyka a [funkce vyššího řádu](https://en.wikipedia.org/wiki/Higher-order_function) rozhraní API pro C# a VB jako způsob, jak napsat kód výrazová, deklarativní.

Syntaxe dotazu na úrovni jazyka:

```csharp
var linqExperts = from p in programmers
                  where p.IsNewToLINQ
                  select new LINQExpert(p);
```

Stejný příklad použití `IEnumerable<T>` rozhraní API:

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

## <a name="linq-is-expressive"></a>LINQ je Expressive

Představte si máte seznam mazlíčků, ale má být převeden do slovníku, kam máte přístup mazlíčky přímo nástrojem jeho `RFID` hodnotu.

Tradiční imperativního kódu:

```csharp
var petLookup = new Dictionary<int, Pet>();

foreach (var pet in pets)
{
    petLookup.Add(pet.RFID, pet);
}
```

Záměrem za kód je nechcete vytvářet novou `Dictionary<int, Pet>` a přidejte do ní prostřednictvím smyčku, je pro převod existujícího seznamu do slovníku! LINQ zachová záměrem služba nepodporuje imperativního kódu.

Ekvivalentní výraz LINQ:

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

Kód pomocí jazyka LINQ je užitečné, protože evens hrací pole mezi cílem a kódem, když důvody jako programátor. Jiné bonusové je zkrácení kódu. Představte si redukování 1/3 dělalo nad velkých částech základ kódu. Poměrně sladké záležitost, pravé?

## <a name="linq-providers-simplify-data-access"></a>Zprostředkovatelé dotazů LINQ zjednodušit přístup k datům

Významné blok softwaru v reálném světě všechno, co zásadní kolem práci s daty z některé zdroje (databáze, JSON, XML atd.). Často to zahrnuje nové rozhraní API pro každý zdroj dat, které vám můžou jít učení. LINQ to zjednodušuje tím, že poskytuje abstrakci společné prvky přístup k datům do syntaxe dotazu, která vypadá stejně bez ohledu na zdroj dat, který vyberete.

Vezměte v úvahu následující: vyhledání všech elementů XML pomocí konkrétní atribut hodnotu.

```csharp
public static IEnumerable<XElement> FindAllElementsWithAttribute(XElement documentRoot, string elementName,
                                           string attributeName, string value)
{
    return from el in documentRoot.Elements(elementName)
           where (string)el.Element(attributeName) == value
           select el;
}
```

Psaní kódu ručně procházet dokumentu XML k provedení této úlohy by bylo mnohem složitější.

Interakce s XML není jediné, co můžete dělat s zprostředkovatelé dotazů LINQ. [Technologie LINQ to SQL](../../docs/framework/data/adonet/sql/linq/index.md) je poměrně holou objektově-relační Mapovač (ORM) určené pro databázi MSSQL serveru. [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) knihovna poskytuje efektivní procházení dokumentu JSON prostřednictvím LINQ. Kromě toho, pokud není k dispozici knihovna, která zajišťuje, co potřebujete, můžete také [napsat vlastního zprostředkovatele LINQ](https://msdn.microsoft.com/library/Bb546158.aspx)!

## <a name="why-use-the-query-syntax"></a>Proč používat syntaxi dotazu?

To je otázka, které často se zobrazí. Po všech tento,

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

je mnohem přesnější než toto:

```csharp
var filteredItems = from item in myItems
                    where item.Foo
                    select item;
```

Syntaxe rozhraní API není právě přesnější způsob, jak provést syntaxi dotazu?

Ne. Syntaxe dotazu umožňuje použití **nechat** klauzule, které umožňuje zavést a vytvoření vazby proměnné v rámci oboru výrazem s použitím v další části výrazu. Reprodukce stejný kód s pouze syntaxi rozhraní API můžete udělat, ale pravděpodobně povede k kódu, který se těžko čitelný.

Takže to si žádá otázku, **by měl pouze použijete syntaxi dotazu?**

Odpověď na tuto otázku se **Ano** Pokud...

*   Stávající základ kódu už používá syntaxi dotazu
*   Je potřeba proměnné s rozsahem v rámci své dotazy z důvodu složitosti
*   Dáváte přednost syntaxi dotazů a nebude odklánět pozornost od vašeho základu kódu

Odpověď na tuto otázku se **žádné** Pokud...

*   Stávající základ kódu už používá syntaxi rozhraní API
*   Nemáte žádné požadavky na rozsah proměnné v dotazech
*   Dáváte přednost syntaxi rozhraní API a nebude odklánět pozornost od vašeho základu kódu

## <a name="essential-samples"></a>Základní ukázky

Seznam skutečně komplexní ukázky dotazů LINQ naleznete [101 ukázek pro LINQ](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).

Tady je rychlý ukázku některé základní údaje LINQ. To není nijak komplexní, protože LINQ poskytuje výrazně víc funkcí než co se tady zobrazují.

*   A másle bread - `Where`, `Select`, a `Aggregate`:

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

*   Sloučení seznamů:

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

*   Sjednocení mezi dvěma sadami (s vlastní Komparátor):

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
        return d.GetHashCode();
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

*   Pořadí:

```csharp
// Get driving directions, ordering by if it's toll-free before estimated driving time.
var results = DirectionsProcessor.GetDirections(start, end)
              .OrderBy(direction => direction.HasNoTolls)
              .ThenBy(direction => direction.EstimatedTime);
```

*   Nakonec více advanced vzorku: určení, jestli jsou stejné hodnoty vlastností dvě instance stejného typu (Borrowed a upravené z [tento příspěvek na StackOverflow](http://stackoverflow.com/a/844855)):

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

## <a name="plinq"></a>PLINQ

PLINQ nebo paralelní LINQ, je modul pro paralelní provádění pro výrazy LINQ. Regulární výrazy LINQ jinými slovy, může být triviálně paralelizován, napříč libovolným počtem vláken. To lze provést prostřednictvím volání `AsParallel()` před výrazem.

Vezměte v úvahu následující:

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

Tento kód bude oddílu `facebookUsers` napříč systémová vlákna podle potřeby, součet celkový počet lajků. v každém vláknu paralelně, součtu výsledky počítají tak, že každé vlákno a projektů, které do nice řetězce.

Ve formuláři diagramu:

![PLINQ diagram](./media/using-linq/plinq-diagram.png)

Paralelizovat úlohy vázané na procesor, které lze snadno vyjádřit pomocí LINQ (jinými slovy, jsou čistě funkce a žádné vedlejší účinky) jsou skvělé Release candidate pro PLINQ. Pro úlohy, které _proveďte_ mají vedlejší účinek, zvažte použití [Task Parallel Library](./parallel-programming/task-parallel-library-tpl.md).

## <a name="further-resources"></a>Další materiály:

*   [101 ukázek pro LINQ](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)
*   [Linqpad](https://www.linqpad.net/), playground prostředí a dotazování databáze modul pro C# /F #/VB
*   [EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), e knihu naučí, jak je implementovaná LINQ na objekty
