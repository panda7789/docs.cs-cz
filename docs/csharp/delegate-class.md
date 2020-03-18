---
title: System.Delegate a `delegate` klíčové slovo
description: Další informace o třídách v rozhraní .NET, které podporují delegáty a jak se tyto mapovat na 'delegate' klíčové slovo.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 87fdf19c4ea810c5ac4409fe16c3cba9d5fc6574
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146278"
---
# <a name="systemdelegate-and-the-delegate-keyword"></a>System.Delegate a `delegate` klíčové slovo

[Předchozí](delegates-overview.md)

Tento článek popisuje třídy v rozhraní .NET, které `delegate` podporují delegáty a jak tyto mapování na klíčové slovo.

## <a name="define-delegate-types"></a>Definování typů delegátů

Začněme s klíčovým slovem "delegate", protože to je především to, co budete používat při práci s delegáty. Kód, který kompilátor generuje při `delegate` použití klíčového slova, bude <xref:System.Delegate> mapovat na volání metody, které vyvolávají členy tříd y a. <xref:System.MulticastDelegate>

Typ delegáta definujete pomocí syntaxe, která je podobná definování podpisu metody. Stačí přidat `delegate` klíčové slovo do definice.

Pojďme pokračovat v používání List.Sort() metoda jako náš příklad. Prvním krokem je vytvoření typu pro delegáta porovnání:

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

Kompilátor generuje třídu odvozenou `System.Delegate` od které odpovídá použitému podpisu (v tomto případě metoda, která vrací celé číslo a má dva argumenty). Typ tohoto delegáta `Comparison`je . Typ `Comparison` delegáta je obecný typ. Podrobnosti o generických léčivých přípravcích naleznete [zde](programming-guide/generics/index.md).

Všimněte si, že syntaxe může vypadat, jako by deklarovala proměnnou, ale ve skutečnosti deklaruje *typ*. Můžete definovat typy delegátů uvnitř tříd, přímo uvnitř oborů názvů nebo dokonce v globálním oboru názvů.

> [!NOTE]
> Deklarování typů delegátů (nebo jiných typů) přímo v globálním oboru názvů se nedoporučuje.

Kompilátor také generuje přidat a odebrat obslužné rutiny pro tento nový typ tak, aby klienti této třídy můžete přidat a odebrat metody ze seznamu vyvolání instance. Kompilátor vynucuje, že podpis přidané nebo odebrané metody odpovídá podpisu použitému při deklarování metody.

## <a name="declare-instances-of-delegates"></a>Deklarovat instance delegátů

Po definování delegáta můžete vytvořit instanci tohoto typu.
Stejně jako všechny proměnné v systému C#nelze deklarovat instance delegáta přímo v oboru názvů nebo v globálním oboru názvů.

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

Typ proměnné je `Comparison<T>`, typ delegáta definovaný dříve. Název proměnné je `comparator`.

 Tento fragment kódu nad deklaroval proměnnou člena uvnitř třídy. Můžete také deklarovat proměnné delegáta, které jsou místní proměnné nebo argumenty pro metody.

## <a name="invoke-delegates"></a>Vyvolat delegáty

Můžete vyvolat metody, které jsou v seznamu vyvolání delegáta voláním tohoto delegáta. Uvnitř `Sort()` metody bude kód volat metodu porovnání k určení pořadí, které mají být objekty umístit:

```csharp
int result = comparator(left, right);
```

Ve výše uvedeném řádku kód *vyvolá* metodu připojenou k delegátovi.
Proměnnou zacházíte jako s názvem metody a vyvoláte ji pomocí syntaxe volání normální metody.

Tento řádek kódu vytváří nebezpečný předpoklad: Neexistuje žádná záruka, že cíl byl přidán do delegáta. Pokud nebyly připojeny žádné cíle, výše `NullReferenceException` uvedená čára by způsobila, že by byla hozena. Idiomy používané k řešení tohoto problému jsou složitější než jednoduchá kontrola null a jsou zahrnuty dále v této [řadě](delegates-patterns.md).

## <a name="assign-add-and-remove-invocation-targets"></a>Přiřazení, přidání a odebrání cílů vyvolání

To je, jak je definován typ delegáta a jak jsou deklarovány a vyvolány instance delegáta.

Vývojáři, kteří `List.Sort()` chtějí použít metodu, musí definovat metodu, jejíž podpis odpovídá definici typu delegáta, a přiřadit ji delegátovi používanému metodou sort. Toto přiřazení přidá metodu do seznamu vyvolání tohoto objektu delegáta.

Předpokládejme, že chcete seřadit seznam řetězců podle jejich délky. Funkce porovnání může být následující:

```csharp
private static int CompareLength(string left, string right) =>
    left.Length.CompareTo(right.Length);
```

Metoda je deklarována jako soukromá metoda. To je v pořádku. Pravděpodobně nechcete, aby tato metoda byla součástí vašeho veřejného rozhraní. Stále lze použít jako metodu porovnání při připojení k delegátovi. Volající kód bude mít tuto metodu připojenou k cílovému seznamu objektu delegáta a může k němu přistupovat prostřednictvím tohoto delegáta.

Tento vztah vytvoříte předáním `List.Sort()` této metody metodě:

```csharp
phrases.Sort(CompareLength);
```

Všimněte si, že název metody se používá, bez závorek. Použití metody jako argument udává kompilátoru převést odkaz na metodu na odkaz, který lze použít jako cíl vyvolání delegáta, a připojit tuto metodu jako cíl vyvolání.

Můžete také být explicitní deklarováním `Comparison<string>` proměnné typu a provedením přiřazení:

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

V použitích, kde je metoda používaná jako cíl delegáta malou metodou, je běžné použít syntaxi [výrazu lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md) k provedení přiřazení:

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

Použití lambda výrazy pro delegáta cíle je popsána více v [pozdější části](delegates-patterns.md).

Sort() příklad obvykle připojí jednu cílovou metodu delegáta. Delegát objekty však podporují seznamy vyvolání, které mají více cílových metod připojených k objektu delegáta.

## <a name="delegate-and-multicastdelegate-classes"></a>Třídy Delegate a MulticastDelegate

Jazyková podpora popsaná výše poskytuje funkce a podporu, které budete obvykle potřebovat pro práci s delegáty. Tyto funkce jsou postaveny na dvou třídách v rámci .NET Core: <xref:System.Delegate> a <xref:System.MulticastDelegate>.

Třída `System.Delegate` a její jediná přímá podtřída , `System.MulticastDelegate`poskytují podporu rozhraní pro vytváření delegátů, registraci metod jako cílů delegáta a vyvolání všech metod, které jsou registrovány jako cíl delegáta.

Zajímavé je, `System.Delegate` `System.MulticastDelegate` že a třídy nejsou samy o sobě typy delegátů. Poskytují základ pro všechny konkrétní typy delegátů. Stejný proces návrhu jazyka nařízen, že nelze `Delegate` deklarovat třídu, která je odvozena od nebo `MulticastDelegate`. Pravidla jazyka C# zakázat.

Místo toho kompilátor Jazyka C# vytvoří instance `MulticastDelegate` třídy odvozené z při použití klíčového slova jazyka C# k deklarování typů delegátů.

Tento návrh má své kořeny v první verzi C# a .NET. Jedním z cílů pro návrhářský tým bylo zajistit, aby jazyk vynucený typ bezpečnosti při použití delegátů. To znamenalo zajistit, že delegáti byli vyvoláni se správným typem a počtem argumentů. A že všechny návratové typy byla správně označena v době kompilace. Delegáti byli součástí verze 1.0 .NET, která byla před obecnými typy.

Nejlepší způsob, jak vynutit tento typ bezpečnosti bylo pro kompilátor vytvořit konkrétní delegát třídy, které představovaly metodu podpisu používá.

I když nelze vytvořit odvozené třídy přímo, budete používat metody definované na tyto třídy. Pojďme projít nejběžnější metody, které budete používat při práci s delegáty.

První, nejdůležitější skutečností je, že každý delegát, se `MulticastDelegate`kterým pracujete, je odvozen z . Delegát vícesměrového vysílání znamená, že při vyvolání prostřednictvím delegáta lze vyvolat více než jeden cíl metody. Původní návrh zvažoval rozlišení mezi delegáty, kde by mohla být připojena a vyvolána pouze jedna cílová metoda, a delegáty, kde by mohlo být připojeno a vyvoláno více cílových metod. Toto rozlišení se v praxi ukázalo jako méně užitečné, než se původně předpokládalo. Dvě různé třídy byly již vytvořeny a byly v rámci od jeho počátečního veřejného vydání.

Metody, které budete používat nejvíce `Invoke()` s `BeginInvoke()`  /  `EndInvoke()`delegáty jsou a . `Invoke()`vyvolá všechny metody, které byly připojeny k určité instanci delegáta. Jak jste viděli výše, obvykle vyvoláte delegáty pomocí syntaxe volání metody na proměnné delegáta. Jak uvidíte [dále v této sérii](delegates-patterns.md), existují vzory, které pracují přímo s těmito metodami.

Teď, když jste viděli syntaxi jazyka a třídy, které podporují delegáty, podívejme se, jak silně zadali delegáti jsou používány, vytvořeny a vyvolány.

[Další](delegates-strongly-typed.md)
