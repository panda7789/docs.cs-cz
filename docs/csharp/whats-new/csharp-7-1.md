---
title: Co je nového v jazyce C# 7.1
description: Přehled nových funkcí v C# 7.1.
ms.date: 04/09/2019
ms.openlocfilehash: 5d2d6f51b6422f5b4db5c6bd275b5ffce1f695f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399705"
---
# <a name="whats-new-in-c-71"></a>Co je nového v jazyce C# 7.1

C# 7.1 je první bod vydání jazyka C#. To znamená zvýšenou kadenci uvolňování pro jazyk. Nové funkce můžete použít dříve, ideálně když je každá nová funkce připravena. C# 7.1 přidává možnost nakonfigurovat kompilátor tak, aby odpovídal zadané verzi jazyka. To umožňuje oddělit rozhodnutí o upgradu nástroje z rozhodnutí o upgradu jazykové verze.

C# 7.1 přidá prvek konfigurace [výběru jazykové verze,](../language-reference/configure-language-version.md) tři nové funkce jazyka a nové chování kompilátoru.

Nové jazykové funkce v této verzi jsou:

- [`async``Main` metoda](#async-main)
  - Vstupní bod pro aplikaci `async` může mít modifikátor.
- [`default`doslovné výrazy](#default-literal-expressions)
  - Výchozí literálové výrazy můžete použít ve výchozích výrazech hodnoty, když lze odvodit cílový typ.
- [Odvozené názvy prvků řazené kolekce členů](#inferred-tuple-element-names)
  - Názvy prvků řazené kolekce členů lze odvodit z inicializace řazené kolekce členů v mnoha případech.
- [Porovnávání vzorů u parametrů obecného typu](#pattern-matching-on-generic-type-parameters)
  - Výrazy shody vzoru můžete použít u proměnných, jejichž typ je parametrem obecného typu.

Nakonec kompilátor má `-refout` dvě `-refonly` možnosti a že generování [sestavení referenční](#reference-assembly-generation)ovládací prvek .

Chcete-li v bodové verzi používat nejnovější funkce, je třeba [nakonfigurovat jazykovou verzi kompilátoru](../language-reference/configure-language-version.md) a vybrat její verzi.

Zbývající část tohoto článku obsahuje přehled jednotlivých funkcí. U každé funkce se dozvíte důvody, které za ní stojí. Naučíte se syntaxi. Tyto funkce můžete prozkoumat ve `dotnet try` vašem prostředí pomocí globálního nástroje:

1. Nainstalujte globální nástroj [dotnet-try.](https://github.com/dotnet/try/blob/master/README.md#setup)
1. Klonovat úložiště [dotnet/try-samples.](https://github.com/dotnet/try-samples)
1. Nastavte aktuální adresář do podadresáře *csharp7* pro úložiště *try-samples.*
1. Spusťte `dotnet try`.

## <a name="async-main"></a>Asynchronní hlavní

*Asynchronní hlavní* metoda umožňuje `await` použít `Main` ve vaší metodě.
Dříve budete muset napsat:

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

Nyní můžete napsat:

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

Pokud program nevrátí ukončovací kód, můžete `Main` deklarovat metodu, která vrací <xref:System.Threading.Tasks.Task>:

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

Můžete si přečíst více o podrobnostech v hlavním článku [asynchronní](../programming-guide/main-and-command-args/index.md) v programovací příručce.

## <a name="default-literal-expressions"></a>Výchozí literálové výrazy

Výchozí literálové výrazy jsou vylepšením výchozích výrazů hodnot.
Tyto výrazy inicializují proměnnou na výchozí hodnotu. Kde jste dříve napsali:

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

Nyní můžete vynechat typ na pravé straně inicializace:

```csharp
Func<string, bool> whereClause = default;
```

Další informace naleznete ve [výchozím části literálu](../language-reference/operators/default.md#default-literal) v článku [výchozího operátora.](../language-reference/operators/default.md)

## <a name="inferred-tuple-element-names"></a>Odvozené názvy prvků řazené kolekce členů

Tato funkce je malé vylepšení funkce řazené kolekce členů zavedené v C# 7.0. Mnohokrát při inicializaci n-tice, proměnné použité pro pravé straně přiřazení jsou stejné jako názvy, které chcete pro n-tice prvky:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

Názvy n-tice prvky lze odvodit z proměnné použité k inicializaci n-tice v C# 7.1:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

Další informace o této funkci najdete v článku [n-tic.](../tuples.md)

## <a name="pattern-matching-on-generic-type-parameters"></a>Porovnávání vzorů u parametrů obecného typu

Počínaje C# 7.1, vzor `is` výraz `switch` a vzorek typu může mít typ parametru obecného typu. To může být nejužitečnější při kontrole `struct` `class` typů, které mohou být buď nebo typy a chcete se vyhnout zabalení.

## <a name="reference-assembly-generation"></a>Generování referenčního sestavení

Existují dvě nové možnosti kompilátoru, které generují *sestavení pouze pro odkazy*: [-refout](../language-reference/compiler-options/refout-compiler-option.md) a [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).
Propojené články vysvětlují tyto možnosti a referenční sestavení podrobněji.
