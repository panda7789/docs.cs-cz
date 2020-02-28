---
title: LINQ (integrovaný dotaz jazyka)
description: Naučte se, jak LINQ poskytuje možnosti dotazování na úrovni jazyka a C# rozhraní API pro a Visual Basic jako způsob, jak napsat výrazující, deklarativní kód.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: c00939e1-59e3-4e61-8fe9-08ad6b3f1295
ms.openlocfilehash: eafd8f78c3d8de1ba064021111f869571d5a570f
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160323"
---
# <a name="linq-language-integrated-query"></a>LINQ (integrovaný dotaz jazyka)

## <a name="what-is-it"></a>Co je to?

LINQ poskytuje funkce pro dotazování na úrovni jazyka a rozhraní API s [vyšším pořadím](https://en.wikipedia.org/wiki/Higher-order_function) pro C# a Visual Basic jako způsob, jak napsat expresně deklarativní kód.

Syntaxe dotazu na úrovni jazyka:

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

Stejný příklad s použitím rozhraní `IEnumerable<T>` API:

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

```vb
Dim linqExperts = programmers.Where(Function(p) p.IsNewToLINQ).
                             Select(Function(p) New LINQExpert(p))
```

## <a name="linq-is-expressive"></a>LINQ je vyjádření

Představte si, že máte seznam domácích, ale chcete ho převést do slovníku, kde můžete získat přístup k PET přímo podle jeho `RFID` hodnoty.

Tradiční imperativní kód:

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

Záměr za kódem není vytvořit novou `Dictionary<int, Pet>` a přidat do něj prostřednictvím smyčky, je převést existující seznam do slovníku. LINQ zachovává záměr, zatímco imperativní kód ne.

Ekvivalentní výraz LINQ:

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

```vb
Dim petLookup = pets.ToDictionary(Function(pet) pet.RFID)
```

Kód, který používá LINQ, je užitečný, protože se jedná o hrací pole mezi záměrem a kódem v případě, kdy je důvodem jako programátor. Další bonus je kód zkrácení. Představte si zmenšení velkých částí základu kódu pomocí 1/3, jak bylo dokončeno. Hodně sladkých, hned?

## <a name="linq-providers-simplify-data-access"></a>Poskytovatelé LINQ zjednodušují přístup k datům

V rámci značné škály softwaru na volném světě se všechno otáčí kolem dat z nějakého zdroje (databáze, JSON, XML atd.). To často zahrnuje učení nového rozhraní API pro každý zdroj dat, což může být nepříjemné. LINQ to zjednodušuje tím, že abstrakce společných prvků přístupu k datům do syntaxe dotazu, která vypadá stejně, jako vybraný zdroj dat.

Vezměte v úvahu následující: vyhledání všech elementů XML s konkrétní hodnotou atributu.

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

Psaní kódu pro ruční procházení dokumentu XML k provedení této úlohy by bylo mnohem náročnější.

Interakce s XML není jedinou věcí, kterou můžete dělat s poskytovateli LINQ. [LINQ to SQL](../../docs/framework/data/adonet/sql/linq/index.md) je poměrně prosté objekty – relační mapování (ORM) pro databázi serveru MSSQL. Knihovna [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) poskytuje efektivní procházení dokumentů JSON prostřednictvím LINQ. Kromě toho, pokud není k dispozici knihovna, která vyžaduje, můžete také [napsat vlastního poskytovatele LINQ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110)).

## <a name="why-use-the-query-syntax"></a>Proč použít syntaxi dotazu?

Jedná se o otázku, která se často vyskytuje. Po všech těchto případech to

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

```vb
Dim filteredItems = myItems.Where(Function(item) item.Foo)
```

je mnohem výstižnější než toto:

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

Není syntaxí rozhraní API jenom výstižnější způsob, jak provádět syntaxi dotazů?

Ne. Syntaxe dotazu umožňuje použití klauzule **let** , která umožňuje začlenit a vytvořit jeho proměnnou v rámci rozsahu výrazu a použít ji v následných částech výrazu. Reprodukce stejného kódu jenom pomocí syntaxe rozhraní API se dá provést, ale nejpravděpodobnější příčinou je, že je obtížné číst kód.

Takže byste to begs na otázku, **měli byste pouze použít syntaxi dotazu?**

Odpověď na tuto otázku je **Ano** , pokud...

* Existující základ kódu už používá syntaxi dotazu.
* V důsledku složitosti je potřeba oborovat proměnné v dotazech.
* Dáváte přednost syntaxi dotazů a nebude se navíc z vašeho základu kódu.

Odpověď na tuto **otázku není v případě.** ..

* Existující základ kódu už používá syntaxi rozhraní API.
* V rámci dotazů nemusíte oborovat proměnné.
* Dáváte přednost syntaxi rozhraní API a nebude se navíc z vašeho základu kódu.

## <a name="essential-samples"></a>Základní ukázky

Úplný seznam ukázek LINQ najdete v [101Ch ukázkách LINQ](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).

Následuje rychlá ukázka některých základních částí jazyka LINQ. Tato možnost není nijak ucelená, protože LINQ poskytuje výrazně více funkcí, než se tady prezentuje.

* Chléb a `Where`másla, `Select`a `Aggregate`:

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

* Sloučení seznamu seznamů:

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

```vb
' Transforms the list of kennels into a list of all their dogs.
Dim allDogsFromKennels = kennels.SelectMany(Function(kennel) kennel.Dogs)
```

* Sjednocení mezi dvěma sadami (s vlastním komparátor):

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

* Průnik dvou sad:

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

* Třídění

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

* Nakonec pokročilejší vzorek: určení, jestli se hodnoty vlastností dvou instancí stejného typu rovnají (jsou vypůjčené a upravené z [tohoto příspěvku StackOverflow](https://stackoverflow.com/a/844855)):

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

## <a name="plinq"></a>PLINQ

PLINQ nebo Paralelní LINQ je paralelní prováděcí modul pro výrazy LINQ. Jinými slovy regulární výraz LINQ může být triviální paralelní napříč libovolným počtem vláken. To je provedeno prostřednictvím volání `AsParallel()` před výrazem.

Zvažte použití těchto zdrojů:

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

Tento kód bude v případě potřeby rozdělit `facebookUsers` mezi systémová vlákna a celková hodnota by měla být rozložená v každém vlákně, sečte výsledky vypočítané každým vláknem a projekt, jehož výsledkem je dobrý řetězec.

Ve tvaru diagramu:

![Diagram PLINQ](./media/using-linq/plinq-diagram.png)

Paralelizovat úlohy vázané na procesor, které je možné snadno vyjádřit prostřednictvím LINQ (jinými slovy, jsou čistě funkce a nemají žádné vedlejší účinky) jsou skvělým kandidátem na PLINQ. Pro úlohy, _které mají_ vedlejší efekt, zvažte použití [paralelní knihovny Tasks](./parallel-programming/task-parallel-library-tpl.md).

## <a name="further-resources"></a>Další zdroje informací:

* [Ukázky 101 LINQ](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)
* [Linqpad](https://www.linqpad.net/), prostředí Playground a stroj pro dotazování databáze pro C#/F#webový Basic
* [EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), pro učení, jak se implementuje LINQ-to-Objects
