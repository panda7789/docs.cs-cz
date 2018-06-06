---
title: Co je nového v C# 7.1
description: Přehled nových funkcí v C# 7.1.
ms.date: 08/16/2017
ms.openlocfilehash: 565db102284424f9d8f6fa04ec9c74b52c9da0e6
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728651"
---
# <a name="whats-new-in-c-71"></a>Co je nového v C# 7.1

C# 7.1 je první bod release to jazyka C#. Označuje vyšší verzi cadence pro jazyk. Můžete vytvořit nové funkce dříve, v ideálním případě při každé nové funkce je připraven. C# 7.1 přidá možnost konfigurace kompilátoru tak, aby odpovídaly zadaná verze jazyka. Která umožňuje oddělit rozhodnutí pro upgrade nástroje z rozhodnutí o upgrade jazykové verze.

C# 7.1 přidá [výběr verze jazyka](../language-reference/configure-language-version.md) konfigurační prvek, tři nové jazykové funkce a nové chování kompilátoru.

Mezi nové jazykové funkce v této verzi jsou:

* [`async` `Main` – Metoda](#async-main)
  - Vstupní bod pro aplikace může mít `async` modifikátor.
* [`default` literálové výrazy](#default-literal-expressions)
  - Výchozí literálu výrazy můžete použít ve výrazech hodnot výchozí při lze odvodit typ cíle.
* [Názvy elementů odvozené řazené kolekce členů](#inferred-tuple-element-names)
  - Názvy elementů řazené kolekce členů lze odvodit z inicializace řazené kolekce členů v mnoha případech.

Nakonec kompilátor má dvě možnosti `/refout` a `/refonly` tuto kontrolu [odkazovat vytváření sestavení](#reference-assembly-generation).

Chcete-li použít nejnovější funkce ve verzi bod, je potřeba [konfigurace jazyková verze kompilátoru](../language-reference/configure-language-version.md) a vyberte verzi.

## <a name="async-main"></a>Asynchronní hlavní

*Asynchronní hlavní* metoda umožňuje používat `await` ve vaší `Main` metoda.
Dříve museli byste zápisu:

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

Teď můžete napsat:

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

Pokud není váš program vrátí ukončovací kód, můžou deklarovat `Main` metodu, která vrátí <xref:System.Threading.Tasks.Task>:

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

Si můžete přečíst více o podrobnostech v [asynchronní hlavní](../programming-guide/main-and-command-args/index.md) tématu v Průvodci programování.

## <a name="default-literal-expressions"></a>Výchozí literálu výrazy

Výchozí literálu výrazy jsou vylepšení výrazy výchozí hodnotu.
Tyto výrazy inicializovat proměnné na výchozí hodnotu. Pokud jste dříve by zápisu:

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

Nyní můžete vynechat typ na pravé straně inicializace:

```csharp
Func<string, bool> whereClause = default;
```

Další informace o toto vylepšení v tématu Průvodce programováním v C# na [výchozí hodnotu výrazy](../programming-guide/statements-expressions-operators/default-value-expressions.md).

Toto vylepšení také změní některé analýzy pravidel pro [default – klíčové slovo](../language-reference/keywords/default.md).

## <a name="inferred-tuple-element-names"></a>Názvy elementů odvozené řazené kolekce členů

Tato funkce je malý vylepšení pro funkci řazených kolekcí členů byla zavedená v C# 7.0. Kolikrát při inicializaci řazené kolekce členů proměnných, které slouží pro pravé straně přiřazení jsou stejné jako názvy, které chcete pro elementy řazené kolekce členů:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

Názvy elementů řazené kolekce členů lze odvodit z proměnných, které slouží k chybě při inicializaci řazené kolekce členů v C# 7.1:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

Další informace o této funkci v [řazených kolekcí členů](../tuples.md) tématu.

## <a name="reference-assembly-generation"></a>Vytváření odkaz na sestavení

Existují dvě nové možnosti kompilátoru, která generují *pouze odkaz na sestavení*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) a [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).
Propojené témata popisují tyto možnosti a odkaz na sestavení podrobněji.
