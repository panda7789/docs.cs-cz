---
title: Co je nového v C# 7,1
description: Přehled nových funkcí v C# 7,1.
ms.date: 04/09/2019
ms.openlocfilehash: 18306da709ea30f03f6c42b4a917e9b39695eb16
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796592"
---
# <a name="whats-new-in-c-71"></a>Co je nového v C# 7,1

C#7,1 je první bod verze pro C# jazyk. Označuje zvýšené verze tempo pro daný jazyk. Nové funkce můžete použít dřív, v ideálním případě, kdy je každá nová funkce připravená. C#7,1 přidává schopnost nakonfigurovat kompilátor tak, aby odpovídal zadané verzi jazyka. To umožňuje oddělit rozhodnutí o upgradu nástrojů od rozhodnutí upgradovat jazykové verze.

C#7,1 přidá prvek konfigurace [výběru jazykové verze](../language-reference/configure-language-version.md) , tři nové funkce jazyka a nové chování kompilátoru.

Nové funkce jazyka v této verzi jsou:

* [`async``Main` metoda](#async-main)
  - Vstupní bod aplikace může mít `async` modifikátor.
* [`default`literálové výrazy](#default-literal-expressions)
  - Můžete použít výchozí literálové výrazy ve výchozích hodnotových výrazech, pokud cílový typ lze odvodit.
* [Odvozené názvy elementů řazené kolekce členů](#inferred-tuple-element-names)
  - Názvy prvků řazené kolekce členů lze odvodit z inicializace řazené kolekce členů v mnoha případech.
* [Porovnávání vzorů v parametrech obecného typu](#pattern-matching-on-generic-type-parameters)
  - Můžete použít výrazy porovnávání vzorů u proměnných, jejichž typ je parametr obecného typu.

Nakonec má kompilátor dvě možnosti `-refout` a odkaz na `-refonly` [generování sestavení odkazu](#reference-assembly-generation).

Chcete-li používat nejnovější funkce v bodu vydání, je nutné [nakonfigurovat verzi jazyka kompilátoru](../language-reference/configure-language-version.md) a vybrat verzi.

Zbývající část tohoto článku poskytuje přehled jednotlivých funkcí. U každé funkce se dozvíte, co je důvod na pozadí. Naučíte se syntaxí. Pomocí `dotnet try` globálního nástroje můžete prozkoumat tyto funkce ve vašem prostředí:

1. Nainstalujte nástroj [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) Global.
1. Naklonujte úložiště [dotnet/try-Samples](https://github.com/dotnet/try-samples) .
1. Nastavte aktuální adresář do podadresáře *csharp7* pro úložiště *Try-Samples* .
1. Spusťte `dotnet try`.

## <a name="async-main"></a>Asynchronní – hlavní

*Asynchronní metoda Main* umožňuje použití `await` v `Main` metodě.
Dříve byste museli psát:

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

Pokud program nevrátí ukončovací kód, můžete deklarovat `Main` metodu, která <xref:System.Threading.Tasks.Task>vrátí:

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

Další informace o podrobnostech najdete v tématu [asynchronní Hlavní](../programming-guide/main-and-command-args/index.md) článek v příručce pro programování.

## <a name="default-literal-expressions"></a>Výchozí literálové výrazy

Výchozí literálové výrazy představují vylepšení výchozích hodnotových výrazů.
Tyto výrazy inicializují proměnnou na výchozí hodnotu. Kam jste předtím napsali:

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

Nyní můžete vynechat typ na pravé straně inicializace:

```csharp
Func<string, bool> whereClause = default;
```

Další informace naleznete v části [výchozí literály](../language-reference/operators/default.md#default-literal) v článku [výchozí operátor](../language-reference/operators/default.md) .

## <a name="inferred-tuple-element-names"></a>Odvozené názvy elementů řazené kolekce členů

Tato funkce představuje malé vylepšení funkce řazené kolekce členů představené v C# 7,0. V mnoha případech, kdy inicializujete řazenou kolekci členů, jsou proměnné používané pro pravou stranu přiřazení stejné jako názvy, které byste chtěli použít pro prvky řazené kolekce členů:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

Názvy prvků řazené kolekce členů lze odvodit z proměnných používaných k inicializaci řazené kolekce členů v C# 7,1:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

Další informace o této funkci najdete v článku o [řazených kolekcích členů](../tuples.md) .

## <a name="pattern-matching-on-generic-type-parameters"></a>Porovnávání vzorů v parametrech obecného typu

Počínaje C# 7,1, výraz vzoru pro `is` a `switch` vzor typu může mít typ parametru obecného typu. To může být nejužitečnější při kontrole typů, které mohou `struct` být `class` buď nebo typy, a chcete se vyhnout zabalení.

## <a name="reference-assembly-generation"></a>Generování referenčního sestavení

Existují dvě nové možnosti kompilátoru, které generují *pouze referenční sestavení*: [-refout](../language-reference/compiler-options/refout-compiler-option.md) a [-nepoužívejte refout](../language-reference/compiler-options/refonly-compiler-option.md).
Odkazované články vysvětlují tyto možnosti a odkazují na sestavení podrobněji.
