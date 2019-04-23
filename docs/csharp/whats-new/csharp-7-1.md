---
title: Co je nového v C# 7.1
description: Přehled nových funkcí v C# 7.1.
ms.date: 04/09/2019
ms.openlocfilehash: c79c8576f9cbbd921ebf30bd84ee5a817d6dc6e7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59480960"
---
# <a name="whats-new-in-c-71"></a>Co je nového v C# 7.1

C#7.1 je první verzi bodu C# jazyka. Označí zvýšená četnost pro jazyk. Můžete použít nové funkce dřív, ideálně při každé nové funkce je připravený. C#7.1 přidává možnost nakonfigurovat tak, aby odpovídaly zadaná verze jazyka kompilátoru. Která umožňuje oddělit rozhodnutí o upgradu nástroje z rozhodnutí o upgradu jazykové verze.

C#7.1 přidává [výběr verze jazyka](../language-reference/configure-language-version.md) prvek konfigurace, tři nové funkce jazyků a nové chování kompilátoru.

Nové funkce jazyků v této verzi jsou:

* [`async` `Main` – Metoda](#async-main)
  - Vstupní bod pro aplikaci může mít `async` modifikátor.
* [`default` literálové výrazy](#default-literal-expressions)
  - Když jde odvodit typ cíle, můžete použít výchozí literál výrazy v výrazy s výchozími hodnotami.
* [Názvy elementů řazené kolekce členů odvozeného](#inferred-tuple-element-names)
  - Názvy elementů řazené kolekce členů lze odvodit z inicializace řazené kolekce členů v mnoha případech.
* [Porovnávání vzorů v parametrech obecného typu](#pattern-matching-on-generic-type-parameters)
  - Vzor odpovídající výrazy můžete použít pro proměnné jehož typ je parametr obecného typu.

A konečně, má kompilátor dvě možnosti `/refout` a `/refonly` ovládacího prvku [odkazovat na generování sestavení](#reference-assembly-generation).

Chcete-li používat nejnovější funkce ve verzi bod, je potřeba [konfigurace verze jazyka kompilátoru](../language-reference/configure-language-version.md) a vyberte verzi.

## <a name="async-main"></a>Asynchronní funkce main

*Asynchronní funkce main* metoda vám umožňuje používat `await` ve vaší `Main` metoda.
Dříve byste museli napsat:

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

Teď můžete psát:

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

Pokud váš program nevrací ukončovací kód, lze deklarovat `Main` metodu, která vrací <xref:System.Threading.Tasks.Task>:

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

Další informace o podrobnosti v [asynchronní funkce main](../programming-guide/main-and-command-args/index.md) článek v průvodce programováním.

## <a name="default-literal-expressions"></a>Výchozí literál výrazy

Jsou výchozí literál výrazy neboli podmínky vylepšují výrazy s výchozími hodnotami.
Tyto výrazy inicializovat proměnnou na výchozí hodnotu. Dříve by píšete:

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

Nyní můžete vynechat typu inicializace na pravé straně:

```csharp
Func<string, bool> whereClause = default;
```

Další informace o toto vylepšení v C# Průvodce programováním pro službu článek věnovaný tomu [výchozí hodnotu výrazy](../programming-guide/statements-expressions-operators/default-value-expressions.md).

Toto vylepšení se také změní některé z pravidla analýzy pro [default – klíčové slovo](../language-reference/keywords/default.md).

## <a name="inferred-tuple-element-names"></a>Názvy elementů řazené kolekce členů odvozeného

Tato funkce je malá vylepšení pro řazené kolekce členů funkce představená v C# 7.0. V mnoha případech při inicializaci řazené kolekce členů proměnných, které slouží k pravému okraji přiřazení jsou stejné jako názvy, které chcete pro elementů řazené kolekce členů:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

Názvy elementů řazené kolekce členů lze odvodit z proměnných, které slouží k inicializaci řazené kolekce členů v C# 7.1:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

Další informace o tuto funkci [řazených kolekcí členů](../tuples.md) článku.

## <a name="pattern-matching-on-generic-type-parameters"></a>Porovnávání vzorů v parametrech obecného typu

Počínaje C# 7.1, výraz vzoru `is` a `switch` vzor typu může mít typ parametru obecného typu. To může být zvláště užitečná při kontrole typy, které může být buď `struct` nebo `class` typy a chcete, aby se zabránilo zabalení.

## <a name="reference-assembly-generation"></a>Generování sestavení odkazu

Existují dvě nové možnosti kompilátoru, které generují *pouze odkaz na sestavení*: [refout](../language-reference/compiler-options/refout-compiler-option.md) a [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).
Propojené články popisují tyto možnosti a referenční sestavení podrobněji.
