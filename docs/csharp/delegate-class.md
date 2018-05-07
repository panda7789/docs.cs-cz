---
title: System.Delegate a `delegate` – klíčové slovo
description: Další informace o třídách v rozhraní .NET Framework, které podporují Delegáti a ty mapování do – klíčové slovo 'delegovat'.
ms.date: 06/20/2016
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 2265d081b884a19cda6fc9d80a0f621a30c87e2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="systemdelegate-and-the-delegate-keyword"></a>System.Delegate a `delegate` – klíčové slovo

[Předchozí](delegates-overview.md)

Tento článek se zabývá třídy v rozhraní .NET framework, které podporují Delegáti a jak jsou mapovány `delegate` – klíčové slovo.

## <a name="defining-delegate-types"></a>Definování typů delegátů.

Začněme s klíčovým slovem 'delegovat', protože takové je primárně co budete používat při práci s delegáti. Kód, který kompilátor vygeneruje při použití `delegate` – klíčové slovo bude mapovat volání metod, které vyvolají členy <xref:System.Delegate> a <xref:System.MulticastDelegate> třídy. 

Definování typu delegáta pomocí syntaxe, který je podobný definování podpis metody. Stačí přidat `delegate` – klíčové slovo k definici.

Budeme nadále používat metodu List.Sort() jako našem příkladu. Prvním krokem je vytvoření typu pro delegáta porovnání:

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

Kompilátor vygeneruje třídy, odvozené od `System.Delegate` odpovídající podpis použít (v tomto případě metodu, která vrátí celé číslo a má dva argumenty). Typ tohoto delegáta je `Comparison`. `Comparison` Typ delegáta je obecného typu. Informace o obecných typů najdete v tématu [zde](generics.md).

Všimněte si, že syntaxe může zdát, že ho je deklarace proměnné, ale ve skutečnosti je deklarace *typu*. Můžete definovat typů delegátů uvnitř třídy, přímo v obory názvů, nebo i v globálním oboru názvů.

> [!NOTE]
> Deklarování delegáta (nebo jiné typy) přímo v globálním oboru názvů se nedoporučuje. 

Kompilátor vytvoří také přidávat a odebírat obslužné rutiny pro tento nový typ tak, aby klienti této třídy můžete přidávat a odebírat metody instance pro vyvolání seznamu. Kompilátor vynutí, že podpis metody přidávání nebo odebírání odpovídá podpis použít při deklarování metodu. 

## <a name="declaring-instances-of-delegates"></a>Deklarování instancí delegáti

Po definování delegáta, můžete vytvořit instanci daného typu.
Podobně jako všechny proměnné v jazyce C# nelze deklarovat delegáta instance přímo v oboru názvů, nebo obor názvů globální.

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

Typ proměnné je `Comparison<T>`, typ delegáta definovaného dříve. Název proměnné je `comparator`.
 
 Tento fragment kódu výše deklarovat členské proměnné uvnitř třídy. Můžete také deklarovat delegáta proměnné, které jsou místní proměnné a argumenty do metod.

## <a name="invoking-delegates"></a>Volajícím delegáti

Vyvolání metody, které jsou v seznamu vyvolání delegáta voláním tohoto delegáta. Uvnitř `Sort()` metoda, kód zavolá metodu porovnání k určení, které pořadí umístit objekty:

```csharp
int result = comparator(left, right);
```

V řádku výše kód *vyvolá* metodu připojené k delegát.
Proměnná považovat za název metody a pomocí syntaxe volání normální metody vyvolání.

Tohoto řádku kódu umožňuje unsafe předpokládá: není zaručeno, že cíl je přidaný do delegáta. Pokud byly připojeny žádné cíle, by způsobilo řádku výše `NullReferenceException` vyvolání. Idioms k řešení tohoto problému se složitější než jednoduché zkontrolujte hodnotu null a jsou popsané později v tomto [řady](delegates-patterns.md).

## <a name="assigning-adding-and-removing-invocation-targets"></a>Přiřazení, přidávání a odebírání cílů volání

To je, jak je definován typ delegáta a jak deklarovat a vyvolá delegáta instancí.

Vývojáři, které chcete použít `List.Sort()` metoda muset definovat metoda, jejíž podpis odpovídá definici typu delegáta a přiřaďte ho ke delegát používá metodu řazení. Toto přiřazení přidá metodu do seznamu vyvolání tohoto delegáta objektu.

Předpokládejme, že chcete seřadit jejich délka seznamu řetězců. Porovnání funkce může být následující:

```csharp
private static int CompareLength(string left, string right)
{
    return left.Length.CompareTo(right.Length);
}
```

Metoda je deklarován jako soukromá metoda. Není to. Tato metoda se jednat o část veřejné rozhraní nemusí být žádoucí. Můžete se pořád použít jako metodu porovnání po připojení k delegáta. Kód volání bude mít tato metoda připojen do cílového seznamu delegáta objektu a k dispozici prostřednictvím tohoto delegáta.

Vytvoření relace pomocí dané metody k předání `List.Sort()` metoda:

```csharp
phrases.Sort(CompareLength);
```

Všimněte si, že se používá název metody, bez závorek. Pomocí metody jako argument říká kompilátoru převést metoda odkaz na odkaz, který lze použít jako cíl vyvolání delegáta a připojte dané metody jako cíl volání.

Může také jste explicitní deklarováním proměnné typu ' porovnání<string>' a provádění přiřazení:

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

V používá tam, kde metoda používá jako cíl delegáta je malý metoda, je běžné používat [výrazu Lambda](lambda-expressions.md) syntaxe provést přiřazení:

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

Použití výrazů Lambda pro delegáta cíle, najdete v článku více [později části](delegates-patterns.md).

Metoda jedním cílem příklad Sort() obvykle připojuje k delegát. Delegát objekty však podporují seznamy volání, které mají více cílové metody připojený k objektu delegáta.

## <a name="delegate-and-multicastdelegate-classes"></a>Delegát a MulticastDelegate, nebude třídy

Podpora jazyků, které jsou popsané výše poskytuje funkce a podporu, které obvykle budete potřebovat pro práci s delegáti. Tyto funkce jsou postaveny na dvě třídy v rozhraní .NET Core: <xref:System.Delegate> a <xref:System.MulticastDelegate>.

`System.Delegate` Třídy a jednu třídu přímé dílčí `System.MulticastDelegate`, poskytovat podporu framework pro vytváření delegátů, registrace metody jako delegáta cíle a vyvolání všechny metody, které jsou registrovány jako cíl delegáta. 

Interestingly `System.Delegate` a `System.MulticastDelegate` třídy nejsou sami delegovat typy. Poskytují základ pro všechny typy konkrétní delegáta. Že stejné návrhu jazyka proces vyžadováno, aby nelze deklarovat třída odvozená z `Delegate` nebo `MulticastDelegate`. Pravidla jazyka C# zakázat ho.
 
Místo toho kompilátor jazyka C# vytvoří instance třídy odvozené od `MulticastDelegate` při použití jazyka C# klíčové slovo jazyka typy delegáta deklarovat.

Tento návrh obsahuje jeho kořeny v první verzi jazyka C# a rozhraní .NET. Jeden cíl pro týmem návrhu se zajistit, že jazyk vynutí bezpečnost typů, při použití delegátů. Který určená, zajistíte, že delegáti byly spuštěny se správný typ a počet argumentů. Doba kompilace a že žádný návratový typ, byl správně uvedeném v. Delegáti byly součástí verzi 1.0 rozhraní .NET, která byla před obecné typy.

Nejlepší způsob, jak vynutit zabezpečení tento typ byl kompilátor pro vytváření tříd, které reprezentované podpis metody používá konkrétní delegáta.

I když odvozené třídy nelze vytvořit přímo, budete používat metody definované na těchto třídách. Přejděte prostřednictvím většiny běžných metod, které budete používat při práci s delegáti.

První, nejdůležitější fakt zapamatujte si je, že každý delegáta pracujete s je odvozený od `MulticastDelegate`. Vícesměrového vysílání delegáta znamená, že více než jeden cíl metoda lze uplatnit při vyvolání prostřednictvím delegáta. Původní návrh za mezi delegáti, kde může připojit a vyvolá metoda pouze jeden cíl a delegáti, kde může několik metod cílový připojit a vyvolá. Tento rozdíl ukázalo jako méně užitečné v praxi než původně představit. Dvěma různými třídami již byly vytvořeny a byly v rámci od prvního vydání veřejné.

Metody, které budete používat nejvíce s delegáti `Invoke()` a `BeginInvoke()`  /  `EndInvoke()`. `Invoke()` vyvolá všechny metody, které byly připojeny k instanci konkrétního delegáta. Jak už jste viděli výše, obvykle vyvolání delegáti pomocí syntaxe volání metody na proměnnou delegáta. Jak uvidíte [dál v této série](delegates-patterns.md), existují vzorů, které pracovat přímo s těchto metod.

Teď, když jste se seznámili syntaxe jazyka a třídy, které podporují delegáti, Podívejme se na tom, jak silného typu delegáti se používají, vytvoření a volá.

[Next](delegates-strongly-typed.md)
