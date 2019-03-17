---
title: System.Delegate a `delegate` – klíčové slovo
description: Další informace o třídách v rozhraní .NET Framework, které podporují delegáty a jak jsou mapovány – klíčové slovo 'delegáta'.
ms.date: 06/20/2016
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 88179af0ac072464d8e9903f685ff578ca591bf0
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2019
ms.locfileid: "58126172"
---
# <a name="systemdelegate-and-the-delegate-keyword"></a>System.Delegate a `delegate` – klíčové slovo

[Předchozí](delegates-overview.md)

Tento článek se zabývá třídy v rozhraní .NET framework, které podporují delegáty a jak jsou mapovány `delegate` – klíčové slovo.

## <a name="defining-delegate-types"></a>Definování typů delegátů.

Začněme s klíčovým slovem 'delegáta', protože, který se primárně se používá při práci s delegátů. Kód, který kompilátor generuje při použití `delegate` – klíčové slovo bude mapovat na volání metody, které vyvolají členy <xref:System.Delegate> a <xref:System.MulticastDelegate> třídy. 

Můžete definovat delegáta typu pomocí syntaxe, která se podobá definuje podpis metody. Stačí přidat `delegate` – klíčové slovo k definici.

Můžeme dál používat metodu List.Sort() jako náš příklad. Prvním krokem je vytvoření typu pro porovnání delegáta:

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

Kompilátor vygeneruje třídu odvozenou z `System.Delegate` , která odpovídá podpisu použít (v tomto případě metodu, která vrátí celé číslo a má dva argumenty). Je typ delegátu `Comparison`. `Comparison` Obecný typ je typ delegátu. Viz podrobnosti o obecných typů [tady](generics.md).

Všimněte si, že syntaxe může zdát, že to je deklarace proměnné, ale ve skutečnosti je deklarace *typ*. Můžete definovat typy delegátů uvnitř třídy, přímo v oborech názvů, nebo dokonce i v globálním oboru názvů.

> [!NOTE]
> Deklarace delegáta typy (nebo jiné typy) přímo v globálním oboru názvů se nedoporučuje. 

Kompilátor generuje také přidávat a odebírat obslužné rutiny pro tento nový typ tak, aby klienti této třídy můžete přidávat a odebírat metody ze seznamu vyvolání instance. Kompilátor vynutí, že podpis metody přidávání nebo odebírání odpovídá podpisu použít při deklaraci metody. 

## <a name="declaring-instances-of-delegates"></a>Deklarování instance delegátů

Po definování delegáta, můžete vytvořit instanci tohoto typu.
Všechny proměnné v, jako jsou C#, nelze deklarovat delegáta instance přímo v oboru názvů nebo v globálním oboru názvů.

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

Typ proměnné je `Comparison<T>`, typ delegáta definovali dříve. Název proměnné je `comparator`.
 
 Tento fragment kódu nad deklaraci členské proměnné uvnitř třídy. Můžete také deklarovat delegáta proměnné, které jsou lokálních proměnných nebo argumentů metody.

## <a name="invoking-delegates"></a>Vyvolání delegátů

Vyvolání metody, které jsou v seznamu vyvolání delegátu po zavolání tohoto delegátu. Uvnitř `Sort()` metoda, kód bude volat metodu porovnání k určení pořadí umístit objekty:

```csharp
int result = comparator(left, right);
```

V řádku nad kódem *vyvolá* metodu připojené k delegátu.
Proměnnou považovat za název metody a vyvolat pomocí syntaxe pro volání normální metody.

Tento řádek kódu vytvoří nebezpečné předpokladů: Není zaručeno, že cíl je přidaný do delegáta. Pokud byly připojeny žádné cíle, by způsobit, že řádek výše `NullReferenceException` vyvolání. Idiomy použít k vyřešení tohoto problému jsou složitější než jednoduchého vyhledání null a jsou popsané dále v tomto [řady](delegates-patterns.md).

## <a name="assigning-adding-and-removing-invocation-targets"></a>Přiřazení, přidávání a odebírání cílů vyvolání

To je, jak je definován typ delegáta a jak deklarovat a vyvolání delegáta instance.

Vývojáři, kteří mají používat `List.Sort()` metoda muset definovat metodu, jejíž podpis odpovídá definici typu delegáta a přiřaďte ho ke delegát používá metodu řazení. Toto přiřazení přidá metodu do seznamu vyvolání tohoto delegáta objektu.

Předpokládejme, že chcete seřadit řetězce podle jejich délky. Funkce porovnání může být následující:

```csharp
private static int CompareLength(string left, string right) =>
    left.Length.CompareTo(right.Length);
```

Metoda je deklarován jako privátní metodu. To je v pořádku. Možná nebudete chtít tuto metodu za účelem být součástí veřejného rozhraní. Může být stále použit jako metodu porovnání při připojení k delegáta. Volající kód bude mít tato metoda připojen k seznamu cílové objektů delegáta a k němu přístup prostřednictvím tohoto delegátu.

Vytvořte vztah předáním této metody `List.Sort()` metody:

```csharp
phrases.Sort(CompareLength);
```

Všimněte si, že název metody, který se používá, bez závorek. Pomocí metody jako argument instruuje kompilátor, aby metoda odkaz převést na odkaz, který lze použít jako cíl vyvolání delegáta a připojit jako cíl volání metody.

Může také byli jste explicitní deklarováním proměnné typu ' porovnání<string>"a provádění přiřazení:

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

Při využití, ve kterém metoda používá jako cíl delegáta je malý metoda, je běžné použití [výraz lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md) syntaxe provést přiřazení:

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

Použití výrazů lambda pro cíle delegáta je věnují více [později části](delegates-patterns.md).

Příklad Sort() se obvykle připojuje jedné cílové metody delegáta. Delegáta objekty však nepodporují vyvolání seznamy, které mají více cílové metody připojen k objektu delegáta.

## <a name="delegate-and-multicastdelegate-classes"></a>Třídy delegáta a MulticastDelegate, nebude

Podpora jazyků je popsáno výše poskytuje funkce a podporu, kterou budete obvykle potřebovat pro práci s delegátů. Tyto funkce jsou postavené na dvě třídy v rozhraní .NET Core: <xref:System.Delegate> a <xref:System.MulticastDelegate>.

`System.Delegate` Třídy a jednu třídu s přímým přístupem dílčí `System.MulticastDelegate`, poskytují podporu rozhraní pro vytváření delegátů, registrace metody jako delegát cíle a vyvolání všechny metody, které jsou registrovány jako cíl delegáta. 

Zajímavé `System.Delegate` a `System.MulticastDelegate` třídy nejsou sami typy delegátů. Poskytují základ pro všemi typy delegátů konkrétní. Že stejný jazyk návrhu procesu přidělených, nelze deklarovat třídu, která je odvozena z `Delegate` nebo `MulticastDelegate`. C# Jazykových pravidel zakázat.
 
Místo toho C# kompilátor vytvoří instance třídy odvozené od `MulticastDelegate` při použití C# klíčové slovo jazyka, chcete-li deklarovat typy delegátů.

Tento návrh byl jeho kořenové adresáře v první verzi C# a .NET. Jedním z cílů týmu návrhu se zajistit, že jazyk vynucuje bezpečnost typů, při použití delegátů. To znamenalo, zajištění, že s správný typ a počet argumentů, které se vyvolaly delegátů. A že jakýkoli návratový typ se správně uvedeném v době kompilace. Delegáti byly součástí verzi 1.0 rozhraní .NET, která byla před obecných typů.

Nejlepší způsob, jak vynucovat bezpečnostní tento typ byl pro kompilátor vytvoří konkrétní delegát třídy, které jsou reprezentovány podpis metody se používají.

I když odvozené třídy nelze vytvořit přímo, použijete metody definované v těchto tříd. Podívejme se nejčastěji používané metody, které budete používat při práci s delegátů.

Je první a nejdůležitější skutečnost na paměti, že každý delegát při práci s je odvozen z `MulticastDelegate`. Delegát vícesměrového vysílání znamená, že více než jeden cíl metoda může být vyvolána při volání prostřednictvím delegáta. Původní návrh považovat za rozlišovat delegáty, kde může připojené a vyvolala metodu pouze jeden cíl a delegáty, kde může připojit a vyvolána více cílové metody. Tento rozdíl dokázaly méně užitečné v praxi, než se původně mluvit. Dvě různé třídy již byly vytvořeny a byly v rámci od its vitial release veřejné.

Metody, které budou používat na maximum pomocí delegátů jsou `Invoke()` a `BeginInvoke()`  /  `EndInvoke()`. `Invoke()` všechny metody, které byly připojeny k instanci konkrétního delegáta vyvolá. Jak už jste viděli výše, je obvykle vyvoláte pomocí syntaxe volání metody delegáta proměnné. Jak uvidíte [dále v této sérii](delegates-patterns.md), jsou vzorce, které pracují přímo s těmito metodami.

Teď, když už víte, syntaxe jazyka a tříd, které podporují delegáty, Pojďme prozkoumat, jak se silnými typy delegátů jsou používány, vytvořena a vyvolána.

[Next](delegates-strongly-typed.md)
