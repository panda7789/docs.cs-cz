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
# <a name="linq-language-integrated-query"></a>LINQ (jazykový integrovaný dotaz)

## <a name="what-is-it"></a>Co je to?

LINQ poskytuje možnosti dotazování na úrovni jazyka a rozhraní API [funkce vyššího řádu](https://en.wikipedia.org/wiki/Higher-order_function) pro c# a visual basic jako způsob psaní expresivního deklarativního kódu.

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

Stejný příklad `IEnumerable<T>` pomocí rozhraní API:

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

```vb
Dim linqExperts = programmers.Where(Function(p) p.IsNewToLINQ).
                             Select(Function(p) New LINQExpert(p))
```

## <a name="linq-is-expressive"></a>LINQ je expresivní

Představte si, že máte seznam domácích mazlíčků, ale chcete jej převést do slovníku, kde můžete přistupovat k domácímu mazlíčku přímo podle jeho `RFID` hodnoty.

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

Záměrem kódu není vytvořit nový `Dictionary<int, Pet>` a přidat k němu pomocí smyčky, je převést existující seznam do slovníku! LINQ zachovává záměr vzhledem k tomu, že imperativní kód není.

Ekvivalentní výraz LINQ:

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

```vb
Dim petLookup = pets.ToDictionary(Function(pet) pet.RFID)
```

Kód pomocí LINQ je cenná, protože vyrovnává hrací pole mezi záměrem a kódem při uvažování jako programátor. Dalším bonusem je stručnost kódu. Představte si, že snížíte velké části základu kódu o 1/3, jak je uvedeno výše. Docela sladká dohoda, že?

## <a name="linq-providers-simplify-data-access"></a>Poskytovatelé LINQ zjednodušují přístup k datům

Pro značnou část softwaru ve volné přírodě se vše točí kolem nakládání s daty z nějakého zdroje (databáze, JSON, XML atd.). Často to zahrnuje učení nové rozhraní API pro každý zdroj dat, což může být nepříjemné. LINQ to zjednodušuje abstrakcí běžných prvků přístupu k datům do syntaxe dotazu, která vypadá stejně bez ohledu na to, který zdroj dat vyberete.

Zvažte následující: nalezení všech elementů XML s určitou hodnotou atributu.

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

Psaní kódu pro ruční procházení dokumentu XML k provedení tohoto úkolu by bylo mnohem náročnější.

Interakce s XML není jediná věc, kterou můžete dělat s poskytovateli LINQ. [Linq to SQL](../../docs/framework/data/adonet/sql/linq/index.md) je poměrně holý objekt-relační mapovač (ORM) pro databázi serveru MSSQL. Knihovna [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) poskytuje efektivní průchod dokumentu JSON prostřednictvím LINQ. Kromě toho, pokud není knihovna, která dělá to, co potřebujete, můžete také [napsat svůj vlastní LINQ Provider](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))!

## <a name="why-use-the-query-syntax"></a>Proč použít syntaxi dotazu?

To je otázka, která často přichází. Koneckonců, toto,

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

```vb
Dim filteredItems = myItems.Where(Function(item) item.Foo)
```

je mnohem stručnější než toto:

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

Není syntaxe rozhraní API jen stručnější způsob, jak provést syntaxi dotazu?

Ne. Syntaxe dotazu umožňuje použití **let** klauzule, která umožňuje zavést a vázat proměnnou v rámci oboru výrazu, pomocí v následujících částech výrazu. Reprodukovat stejný kód pouze syntaxe rozhraní API lze provést, ale s největší pravděpodobností povede ke kódu, který je těžko čitelný.

Takže to vyvolává otázku, **měli byste prostě použít syntaxi dotazu?**

Odpověď na tuto otázku zní **ano,** pokud...

* Stávající základ kódu již používá syntaxi dotazu.
* Proměnné v rámci dotazů je třeba z důvodu složitosti
* Dáváte přednost syntaxi dotazu a nebude odvádět pozornost od základu kódu

Odpověď na tuto otázku je **ne,** pokud ...

* Stávající základ kódu již používá syntaxi rozhraní API.
* Není nutné obor proměnné v rámci dotazů
* Dáváte přednost syntaxi rozhraní API a nebude odvádět pozornost od vašeho základu kódu

## <a name="essential-samples"></a>Základní vzorky

Pro skutečně komplexní seznam linq vzorků, navštivte [101 LINQ vzorky](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).

Následuje rychlá ukázka některých základních částí LINQ. To není v žádném případě komplexní, protože LINQ poskytuje výrazně více funkcí, než to, co je zde prezentováno.

* Chléb a máslo `Where` `Select`- `Aggregate`, a:

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

* Sjednocení mezi dvěma sadami (s vlastním komparátorem):

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

* Průsečík mezi dvěma sadami:

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

* Objednávání:

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

* Nakonec pokročilejší ukázka: určení, zda jsou hodnoty vlastností dvou instancí stejného typu stejného typu stejného typu stejného typu stejného typu stejného typu stejného typu stejného typu stejného typu jsou stejné (Vypůjčené a upravené z [tohoto stackoverflow post](https://stackoverflow.com/a/844855)):

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

PLINQ, nebo Paralelní LINQ, je paralelní spuštění motoru pro výrazy LINQ. Jinými slovy regulární výraz LINQ může být triviálně paralelizován v libovolném počtu vláken. To je dosaženo prostřednictvím `AsParallel()` volání před výraz.

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

Tento kód `facebookUsers` bude oddíl mezi podprocesy systému podle potřeby, shrnout celkový líbí na každém vlákně paralelně, součet výsledků vypočítaných každým vláknem a projekt, který výsledkem je do pěkný řetězec.

Ve formě diagramu:

![PLINQ diagram](./media/using-linq/plinq-diagram.png)

Paralelní úlohy vázané na cpu, které lze snadno vyjádřit pomocí LINQ (jinými slovy, jsou čisté funkce a nemají žádné vedlejší účinky) jsou skvělým kandidátem pro PLINQ. U úloh, které _mají_ vedlejší účinek, zvažte použití [paralelní knihovny úloh](./parallel-programming/task-parallel-library-tpl.md).

## <a name="further-resources"></a>Další zdroje informací:

* [101 VZORKŮ LINQ](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)
* [Linqpad](https://www.linqpad.net/), prostředí hřiště a databázový dotazovací stroj pro c#/f#/visual basic
* [EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), e-kniha pro učení, jak linq-to-objekty jsou implementovány
