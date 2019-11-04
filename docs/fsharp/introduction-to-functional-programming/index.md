---
title: Úvod do funkčního programování v F#
description: Seznamte se se základy funkčního programování F#v nástroji.
ms.date: 10/29/2018
ms.openlocfilehash: e1a0edc61dbe13012c48e166d490e22ebc70d6a0
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424700"
---
# <a name="introduction-to-functional-programming-in-f"></a>Úvod do funkčního programování v F\#

Funkční programování je styl programování, který zdůrazňuje použití funkcí a neměnných dat. Typované funkční programování je v případě, že je funkční programování kombinováno se statickými F#typy, například s. Obecně platí, že následující pojmy jsou zvýrazněny v části funkční programování:

* Funguje jako primární konstrukce, které používáte.
* Výrazy místo příkazů
* Neměnné hodnoty nad proměnnými
* Deklarativní programování v rámci imperativního programování

V celé této sérii budete zkoumat koncepty a vzory v rámci funkčního F#programování pomocí. V takovém případě se naučíte F# také.

## <a name="terminology"></a>Terminologie

Funkční programování, podobně jako jiné programovací paradigma, je dodáváno se slovníkem, který budete nakonec potřebovat vědět. Tady jsou některé běžné výrazy, které se zobrazí po celou dobu:

* **Funkce** – funkce je konstrukce, která při zadání vstupu vytvoří výstup. V tuto dobu _namapuje_ položku z jedné sady na jinou sadu. Tento formální způsob se přenese do konkrétního množství způsobů, zejména při použití funkcí, které pracují s kolekcemi dat. Je to nejzákladnější koncept (a důležité) v rámci funkčního programování.
* **Expression** – výraz je konstruktor v kódu, který vytváří hodnotu. V F#nástroji musí být tato hodnota svázaná nebo explicitně ignorována. Výraz může být triviálním nahrazen voláním funkce.
* **Čistota** -čistota je vlastnost funkce tak, že vrácená hodnota je vždy stejná pro stejné argumenty a že její vyhodnocení nemá žádné vedlejší účinky. Funkce Pure závisí výhradně na svých argumentech.
* **Referenční** transparentnost – referenční transparentnost je vlastnost výrazů, jako je například, že mohou být nahrazeny jejich výstupem, aniž by to ovlivnilo chování programu.
* **Neměnnosti** -neměnnosti znamená, že hodnotu nelze změnit na místě. To je v kontrastu s proměnnými, které se mohou změnit na místě.

## <a name="examples"></a>Příklady

Následující příklady znázorňují tyto základní koncepty.

### <a name="functions"></a>Funkce

Nejběžnější a základní konstrukce v funkčním programování je funkce. Tady je jednoduchá funkce, která přidá 1 k celému číslu:

```fsharp
let addOne x = x + 1
```

Jeho signatura typu je následující:

```fsharp
val addOne: x:int -> int
```

Podpis lze číst jako, "`addOne` přijímá `int` s názvem `x` a vytvoří `int`". `addOne` je _mapována_ hodnota ze sady celých čísel na sadu celých čísel. Token `->` znamená toto mapování. V F#nástroji se můžete obvykle podívat na signaturu funkce, abyste získali představu o tom, co dělá.

Proč je podpis důležitý? V psaní funkčního programování je implementace funkce často méně důležitá než skutečný podpis typu! Skutečnost, že `addOne` přidá hodnotu 1 k celému číslu, je zajímavá za běhu, ale při sestavování programu je fakt, že přijímá a vrací `int` je to, co informuje o tom, jak tuto funkci skutečně používáte. Navíc po správném použití této funkce (s ohledem na signaturu jejího typu) je možné diagnostikovat jakékoli problémy pouze v těle funkce `addOne`. Jedná se o podněty za psaní funkčního programování.

### <a name="expressions"></a>Výrazy

Výrazy jsou konstrukce, které se vyhodnotí na hodnotu. Na rozdíl od příkazů, které provádějí akci, lze výrazy považovat za provedení akce, která vrací hodnotu. Výrazy se téměř vždycky používají ve prospěch příkazů ve funkčním programování.

Zvažte předchozí funkci `addOne`. Text `addOne` je výraz:

```fsharp
// 'x + 1' is an expression!
let addOne x = x + 1
```

Jedná se o výsledek tohoto výrazu, který definuje typ výsledku funkce `addOne`. Například výraz, který tvoří tuto funkci, může být změněn na jiný typ, například `string`:

```fsharp
let addOne x = x.ToString() + "1"
```

Signatura funkce je teď:

```fsharp
val addOne: x:'a -> string
```

Vzhledem k tomu, F# že kterýkoli typ v může mít `ToString()` volána, byl typ `x` vytvořen jako obecný (tzv. [Automatická generalizace](../language-reference/generics/automatic-generalization.md)) a výsledný typ je `string`.

Výrazy nejsou jenom orgány funkcí. Můžete mít výrazy, které vytvoří hodnotu, kterou použijete jinde. Jednou z nich je `if`:

```fsharp
// Checks if 'x' is odd by using the mod operator
let isOdd x = x % 2 <> 0

let addOneIfOdd input =
    let result =
        if isOdd input then
            input + 1
        else
            input

    result
```

Výraz `if` vytvoří hodnotu nazvanou `result`. Všimněte si, že můžete `result` zcela vynechat, což `if` výrazu `addOneIfOdd` funkce. Klíčovým aspektem pro zapamatování výrazů je, že vytvoří hodnotu.

Existuje speciální typ, `unit`, který se používá v případě, že není nic vráceno. Zvažte například tuto jednoduchou funkci:

```fsharp
let printString (str: string) =
    printfn "String is: %s" str
```

Signatura vypadá takto:

```fsharp
val printString: str:string -> unit
```

Typ `unit` označuje, že není vrácena žádná skutečná hodnota. To je užitečné, když máte rutinu, která musí "dělat práci" Navzdory tomu, že nevrátí hodnotu, která by se měla vrátit jako výsledek této práce.

To je prudký kontrast vůči imperativnímu programování, kde ekvivalentní `if` konstrukce je příkaz a vytváření hodnot se často provádí s použitím obdobných proměnných. Například v C#nástroji může být kód napsán takto:

```csharp
bool IsOdd(int x) => x % 2 != 0;

int AddOneIfOdd(int input)
{
    var result = input;

    if (IsOdd(input))
    {
        result = input + 1;
    }

    return result;
}
```

Je vhodné poznamenat, C# že a jiné jazyky ve stylu jazyka C podporují [výraz Ternární](../../csharp/language-reference/operators/conditional-operator.md), který umožňuje podmíněné programování založené na výrazu.

V funkčním programování je zřídka možné hodnoty pomocí příkazů. I když některé funkční jazyky podporují příkazy a mutace, není běžné používat tyto koncepty v funkčním programování.

### <a name="pure-functions"></a>Čisté funkce

Jak už jsme uvedli, funkce Pure jsou funkce, které:

* Vždy se vyhodnotí na stejnou hodnotu pro stejný vstup.
* Nemají žádné vedlejší účinky.

Je vhodné si v tomto kontextu představit matematické funkce. V matematice jsou funkce závislé jenom na jejich argumentech a nemají žádné vedlejší účinky. V matematické funkci `f(x) = x + 1`, hodnota `f(x)` závisí pouze na hodnotě `x`. Čisté funkce v funkčním programování jsou stejné jako.

Při psaní čistě funkce musí být funkce závislá pouze na jejích argumentech a nesmí provádět žádnou akci, která má za následek vedlejší efekt.

Tady je příklad nečisté funkce, protože závisí na globálním, proměnlivém stavu:

```fsharp
let mutable value = 1

let addOneToValue x = x + value
```

Funkce `addOneToValue` je jasně nečistá, protože `value` možné kdykoli změnit tak, aby měla jinou hodnotu než 1. Tento model v závislosti na globální hodnotě se vyhne v funkčním programování.

Tady je další příklad nečisté funkce, protože provádí vedlejší efekt:

```fsharp
let addOneToValue x =
    printfn "x is %d" x
    x + 1
```

I když tato funkce není závislá na globální hodnotě, zapíše hodnotu `x` do výstupu programu. I když se to nestane nepodstatným chybou, znamená to, že funkce není čistá. Pokud jiná část programu závisí na něčem externím programu, jako je výstupní vyrovnávací paměť, pak volání této funkce může ovlivnit tuto jinou část programu.

Odebrání příkazu `printfn` provede čistou funkci:

```fsharp
let addOneToValue x = x + 1
```

I když tato funkce není ve své podstatě _lepší_ než předchozí verze s příkazem `printfn`, zaručuje, že všechny této funkce vrátí hodnotu. Voláním této funkce libovolným počtem opakování vznikne stejný výsledek: pouze vytvoří hodnotu. Předvídatelnost vydaná pomocí čistoty je mnoho funkčních programátorů, které se snaží.

### <a name="immutability"></a>Neměnnosti

Nakonec jedna z nejdůležitějších konceptů typovaného programování je neměnnosti. Ve F#výchozím nastavení jsou všechny hodnoty neměnné. To znamená, že nemohou být umístěny místně, pokud je explicitně neoznačíte jako proměnlivé.

V praxi pracujete s neproměnlivými hodnotami, protože měníte přístup k programování z, "Potřebuji změnit něco", na "Potřebuji vytvořit novou hodnotu".

Například přidání hodnoty 1 k hodnotě znamená vytvoření nové hodnoty, která nezpůsobuje existující hodnotu:

```fsharp
let value = 1
let secondValue = value + 1
```

V F#, následující kód **není** obdobou funkce `value`; místo toho provede kontrolu rovnosti:

```fsharp
let value = 1
value = value + 1 // Produces a 'bool' value!
```

Některé funkční programovací jazyky nepodporují mutace vůbec. V F#je podporováno, ale není to výchozí chování pro hodnoty.

Tento koncept rozšiřuje ještě více datových struktur. V funkčním programování mají neměnné datové struktury, jako jsou například sady (a mnoho dalších) odlišnou implementaci, než na začátku očekávat. V koncepčních případech, například když přidáte položku do sady, se nezmění sada, vytvoří _novou_ sadu s přidanou hodnotou. V rámci pokrývá to často používá jiná datová struktura, která umožňuje efektivně sledovat hodnotu tak, aby se v důsledku mohla předávat odpovídající reprezentace dat.

Tento styl práce s hodnotami a datovými strukturami je kritický, protože se vynutí, aby se pocházela s jakoukoli operací, jako kdyby vytvořila novou verzi této věci. To umožňuje, aby byly v aplikacích konzistentní, jako je rovnost a srovnatelnost.

## <a name="next-steps"></a>Další kroky

V další části najdete funkce, které prozkoumejte různé způsoby, jak je můžete používat při funkčním programování.

[Funkce první třídy](first-class-functions.md) zkoumá funkce a ukazuje, jak je lze použít v různých kontextech.

## <a name="further-reading"></a>Další čtení

[Funkce přemýšlení](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) je dalším skvělým zdrojem informací o funkčním programování s F#. Zabývá se základy funkčního programování v rámci náročného a snadno čitelného způsobu použití F# funkcí k ilustraci konceptů.
