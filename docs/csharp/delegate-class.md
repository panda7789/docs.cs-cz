---
title: System. Delegate a klíčové slovo `delegate`
description: Přečtěte si o třídách v rozhraní .NET, které podporují delegáty a jejich mapování na klíčové slovo Delegate.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 3cfc9925be0f191dc3fc93c02f4a8f9a40b71895
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450918"
---
# <a name="systemdelegate-and-the-delegate-keyword"></a>System. Delegate a klíčové slovo `delegate`

[Předchozí](delegates-overview.md)

Tento článek popisuje třídy v rozhraní .NET, které podporují delegáty, a způsob mapování na klíčové slovo `delegate`.

## <a name="define-delegate-types"></a>Definování typů delegátů

Pojďme začít s klíčovým slovem Delegate, protože to je primárně to, co budete používat při práci s delegáty. Kód, který kompilátor generuje při použití klíčového slova `delegate`, se namapuje na volání metod, která vyvolávají členy třídy <xref:System.Delegate> a <xref:System.MulticastDelegate>. 

Můžete definovat typ delegáta pomocí syntaxe, která je podobná definování signatury metody. Pouze přidáte klíčové slovo `delegate` do definice.

Pojďme dál používat metodu list. Sort () jako náš příklad. Prvním krokem je vytvoření typu pro delegáta porovnání:

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

Kompilátor vygeneruje třídu odvozenou z `System.Delegate`, která odpovídá použitému podpisu (v tomto případě metoda, která vrací celé číslo a má dva argumenty). Typ delegáta je `Comparison`. Typ delegáta `Comparison` je obecný typ. Podrobnosti o obecných typech najdete [tady](programming-guide/generics/index.md).

Všimněte si, že se syntaxe může zobrazit, jako by deklaruje proměnnou, ale ve skutečnosti deklaruje *typ*. Můžete definovat typy delegátů uvnitř tříd, přímo v oborech názvů nebo dokonce v globálním oboru názvů.

> [!NOTE]
> Deklarace typů delegátů (nebo jiných typů) přímo v globálním oboru názvů se nedoporučuje. 

Kompilátor také generuje přidat a odebrat obslužné rutiny pro tento nový typ tak, aby klienti této třídy mohli přidávat a odebírat metody ze seznamu volání instance. Kompilátor vyhodnotí, že signatura přidávaného nebo odebraného metody odpovídá podpisu použitému při deklaraci metody. 

## <a name="declare-instances-of-delegates"></a>Deklarovat instance delegátů

Po definování delegáta můžete vytvořit instanci tohoto typu.
Podobně jako všechny proměnné C#v nemůžete deklarovat instance delegátů přímo v oboru názvů nebo v globálním oboru názvů.

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

Typ proměnné je `Comparison<T>`, dříve definovaný typ delegáta. Název proměnné je `comparator`.
 
 Tento fragment kódu výše deklaruje členskou proměnnou uvnitř třídy. Můžete také deklarovat proměnné delegáta, které jsou lokální proměnné nebo argumenty metody.

## <a name="invoke-delegates"></a>Vyvolat delegáty

Vyvoláte metody, které jsou v seznamu volání delegáta, voláním tohoto delegáta. V rámci metody `Sort()` kód zavolá metodu porovnání k určení, které pořadí umístit objekty:

```csharp
int result = comparator(left, right);
```

V řádku výše kód *vyvolá* metodu připojenou k delegátovi.
Zacházíte s proměnnou jako s názvem metody a vyvoláte ji pomocí syntaxe volání normální metody.

Tento řádek kódu představuje nebezpečný předpoklad: není nijak zaručeno, že do delegáta byl přidán cíl. Pokud nejsou k dispozici žádné cíle, by výše uvedený řádek způsobil vyvolání `NullReferenceException`. Idiomy, který se používá k vyřešení tohoto problému, je složitější než jednoduchá hodnota null a jsou pokrytá později v této [sérii](delegates-patterns.md).

## <a name="assign-add-and-remove-invocation-targets"></a>Přiřazení, přidání a odebrání cílů volání

To je způsob, jakým je definován typ delegáta a jak jsou instance delegáta deklarovány a vyvolány.

Vývojáři, kteří chtějí používat metodu `List.Sort()`, musí definovat metodu, jejíž signatura odpovídá definici typu delegáta, a přiřadit ji k delegátovi použitému metodou řazení. Toto přiřazení přidá metodu do seznamu volání daného objektu Delegate.

Předpokládejme, že jste chtěli seřadit seznam řetězců podle jejich délky. Vaše funkce porovnání může být následující:

```csharp
private static int CompareLength(string left, string right) =>
    left.Length.CompareTo(right.Length);
```

Metoda je deklarována jako soukromá metoda. To je dobré. Možná nebudete chtít, aby tato metoda byla součástí vašeho veřejného rozhraní. Tuto možnost lze použít jako metodu porovnání, je-li připojena k delegátovi. Volající kód bude mít tuto metodu připojenou k cílovému seznamu objektu delegáta a může k němu přistupovat prostřednictvím tohoto delegáta.

Tuto relaci vytvoříte předáním této metody metodě `List.Sort()`:

```csharp
phrases.Sort(CompareLength);
```

Všimněte si, že se používá název metody bez závorek. Použití metody jako argument říká kompilátoru, aby převedl odkaz na metodu na odkaz, který se dá použít jako cíl vyvolání delegáta, a připojte tuto metodu jako cíl volání.

Mohli jste být také explicitní deklarací proměnné typu `Comparison<string>` a provedením přiřazení:

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

V použití, kde je metoda používaná jako cíl delegáta malá metoda, je běžné použít syntaxi [výrazu lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md) k provedení přiřazení:

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

Použití výrazů lambda pro cíle delegátů je podrobněji popsáno v [pozdější části](delegates-patterns.md).

Příklad řazení () obvykle k delegátovi připojí jedinou cílovou metodu. Nicméně objekty delegáta podporují seznamy vyvolání s více cílovými metodami připojenými k objektu delegáta.

## <a name="delegate-and-multicastdelegate-classes"></a>Třídy Delegate a MulticastDelegate

Výše popsaná jazyková podpora poskytuje funkce a podporu, které obvykle budete potřebovat pro práci s delegáty. Tyto funkce jsou postavené na dvou třídách v rozhraní .NET Core Framework: <xref:System.Delegate> a <xref:System.MulticastDelegate>.

Třídu `System.Delegate` a její jednu přímou podtřídou, `System.MulticastDelegate`, poskytují podporu rozhraní pro vytváření delegátů, registraci metod jako cíle delegátů a vyvolání všech metod, které jsou registrovány jako cíl delegáta. 

V zájmech se třídy `System.Delegate` a `System.MulticastDelegate` samy nedelegovaní sami. Poskytují základ pro všechny konkrétní typy delegátů. Stejný proces návrhu jazyka má pověření, že nelze deklarovat třídu, která je odvozena z `Delegate` nebo `MulticastDelegate`. C# Jazyková pravidla zakazují.
 
Místo toho C# kompilátor vytvoří instance třídy odvozené z `MulticastDelegate` při použití klíčového slova C# jazyka k deklaraci typů delegátů.

Tento návrh má své kořeny v první verzi C# a .NET. Jedním z cílů pro návrhového týmu bylo zajistit, aby při použití delegátů byl vynutilný bezpečnost typu. Což znamenalo, že Delegáti byli vyvoláni se správným typem a počtem argumentů. A že libovolný návratový typ byl správně uveden v době kompilace. Delegáti byli součástí verze 1,0 .NET, která byla před obecnými typy.

Nejlepším způsobem, jak vyhovět této bezpečnosti typu, bylo, že kompilátor vytvoří konkrétní třídy delegátů, které představují použitou signaturu metody.

I když nemůžete vytvořit odvozené třídy přímo, budete používat metody definované na těchto třídách. Pojďme si projít nejběžnějšími metodami, které budete používat při práci s delegáty.

První, nejdůležitější fakt, jak si pamatovat, je, že každý delegát, se kterým pracujete, je odvozen z `MulticastDelegate`. Delegát vícesměrového vysílání znamená, že při volání prostřednictvím delegáta lze vyvolat více než jeden cíl metody. Původní návrh se považuje za způsobující rozdíl mezi delegáty, kde lze připojit a vyvolat pouze jednu cílovou metodu, a delegáti, kde lze připojit a vyvolat více cílových metod. Toto rozlišení se ukázalo jako méně užitečné v praxi, než jsme původně mysleli. Dvě různé třídy již byly vytvořeny a byly v rozhraní od počáteční veřejné verze.

Metody, které použijete nejvíce s delegáty, jsou `Invoke()` a `BeginInvoke()` / `EndInvoke()`. `Invoke()` vyvolá všechny metody, které byly připojeny ke konkrétní instanci delegáta. Jak jste viděli výše, obvykle vyvoláte delegáty pomocí syntaxe volání metody v proměnné Delegate. Jak vidíte [později v této sérii](delegates-patterns.md), existují vzory, které pracují přímo s těmito metodami.

Teď, když jste viděli syntaxi jazyka a třídy, které podporují delegáty, Podívejme se, jak se používají Delegáti silného typu, vytvoří se a vyvolají.

[Next](delegates-strongly-typed.md)
