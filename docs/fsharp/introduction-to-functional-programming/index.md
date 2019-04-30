---
title: Úvod do funkčního programování v F#
description: Seznamte se se základy funkčního programování v F#.
ms.date: 10/29/2018
ms.openlocfilehash: 84022e58c0f17b9e9875402c653c31e494e940da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772785"
---
# <a name="introduction-to-functional-programming-in-f"></a>Úvod do funkčního programování v F\#

Funkční programování je styl programování, které klade důraz na použití funkcí a neměnnými daty. Je zadaný funkční programování kombinaci funkční programování je pomocí statické typy, například s F#. Obecně tyto koncepty jsou zvýrazněny do funkčního programování:

* Funkce jako primární konstrukce, které používáte
* Výrazy místo příkazů
* Neměnné hodnoty v proměnné
* Deklarativní programování přes imperativní programování

V celé této sérii prozkoumáte koncepty a vzory v funkční programování pomocí F#. Cestou se dozvíte některé F# příliš.

## <a name="terminology"></a>Terminologie

Funkční programování, jako jsou jiné programovací modely obsahuje slovník, který bude časem nutné další informace. Tady jsou některé běžné podmínky zobrazí celou dobu:

* **Funkce** – funkce je konstrukce, která vytvoří výstup, když vstup. Více formálně ho _mapuje_ položky z jednoho nastavena na jinou sadu. Tato formalism je zrušeno do konkrétní mnoha způsoby, zvláště při použití funkce, které pracují na kolekce dat. Je nejvíce základní (a důležité) koncept v funkčního programování. 
* **Výraz** -výrazu je konstrukce v kódu, který vytváří hodnotu. V F#, tato hodnota musí být svázán nebo explicitně ignorovány. Výraz lze snadno nahradit volání funkce.
* **Čistota** -čistoty je vlastnost funkce tak, že vrácená hodnota je vždy stejný pro stejné argumenty a že jeho vyhodnocení nemá žádné vedlejší účinky. Čistě funkci zcela závisí na jeho argumenty.
* **Referenční transparentnosti** – referenční transparentnosti je vlastnost výrazů tak, že se dá nahradit výrazem jejich výstup bez ovlivnění chování programu.
* **Neměnnost** -neměnnosti znamená, že hodnota nemůže být změněna na místě. To je rozdíl od proměnné, které můžete změnit na místě.

## <a name="examples"></a>Příklady

Následující příklady ukazují těmito základními koncepty.

### <a name="functions"></a>Funkce

Nejvíce běžné a základní konstrukcí funkčního programování je funkce. Tady je jednoduchou funkci, která se přičte 1 k celým číslem:

```fsharp
let addOne x = x + 1
```

Typ podpisu je následujícím způsobem:

```fsharp
val addOne: x:int -> int
```

Podpis může číst jako "`addOne` přijímá `int` s názvem `x` a vytvoří `int`". Více formálně `addOne` je _mapování_ hodnotu ze sady celých čísel na sadu celých čísel. `->` Token označuje, že toto mapování. V F#, obvykle můžete se podívat na podpis funkce získali povědomí o co to dělá.

Ano, proč je podpis důležité? V typu funkčního programování, implementace funkce je často méně důležitá než podpis skutečný typ! Fakt, který `addOne` přidá hodnoty 1 na celé číslo je zajímavé za běhu, ale jsou při sestavování programu, skutečnost, že přijímá a vrací `int` je co informuje o tom, jak bude ve skutečnosti používat tuto funkci. Kromě toho po použití této funkce správně (s ohledem na její typ podpis), diagnostice potíží lze provést pouze v těle `addOne` funkce. Toto je tak za zadaný funkčního programování.

### <a name="expressions"></a>Výrazy

Výrazy jsou konstrukce, která se vyhodnotí na hodnotu. Na rozdíl od příkazů, které provádějí akci, výrazy můžete představit provést akci, která poskytuje vrátit hodnotu. Výrazy se téměř vždy používají ve prospěch příkazy do funkčního programování.

Zvažte předchozí funkci `addOne`. Tělo `addOne` je výraz:

```fsharp
// 'x + 1' is an expression!
let addOne x = x + 1
```

Výsledek tohoto výrazu, který definuje typ výsledku `addOne` funkce. Například výraz, který tvoří tuto funkci, můžete ho změnit na jiný typ, například `string`:

```fsharp
let addOne x = x.ToString() + "1"
```

Signatura funkce je teď:

```fsharp
val addOne: x:'a -> string
```

Od libovolného typu v F# může mít `ToString()` volá v něm typ `x` byl proveden obecný (volá [Automatická generalizace](../language-reference/generics/automatic-generalization.md)), a výsledný typ je `string`.

Výrazy nejsou právě těla funkce. Můžete použít výrazy, které vytvoří hodnotu, kterou můžete použít na jiném místě. Běžný je `if`:

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

`if` Výraz vytvoří hodnotu s názvem `result`. Všimněte si, že by mohla vynechat `result` úplně, aby `if` výraz text z `addOneIfOdd` funkce. Nejdůležitější informace o výrazech je, že vytvářejí hodnotu.

Je speciální typ `unit`, který se používá při není nutné nic vrátit. Představte si třeba tato jednoduchá funkce:

```fsharp
let printString (str: string) =
    printfn "String is: %s" str
```

Podpis vypadá takto:

```fsharp
val printString: str:string -> unit
```

`unit` Označuje, že neexistuje žádná skutečná hodnota se vrací. To je užitečné, když máte rutinu, která musí "pracovní" bez ohledu na žádnou hodnotu vrátit jako výsledek, které pracují s.

Toto je sharp oproti imperativní programování, kde ekvivalent `if` konstrukce je příkaz a vytváření hodnoty se často provádí pomocí mutace proměnné. Například v C#, kód může být napsán takto:

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

Je vhodné poznamenat, že C# a podpora jiných jazyků C-style [Ternární výraz](../../csharp/language-reference/operators/conditional-operator.md), což umožňuje založené na výrazu podmíněné programování.

Funkční programování v zřídka dochází k mutovat hodnoty s příkazy. I když některé funkční jazyky podporují příkazy a mutace, není běžné použití těchto konceptů v funkčního programování.

### <a name="pure-functions"></a>Čistě funkce

Dříve jsme už zmínili, čistě funkce jsou funkce:

* Vždy vyhodnoťte na stejnou hodnotu pro stejný vstup.
* Mít žádné vedlejší účinky.

Je vhodné si můžete představit matematické funkce v tomto kontextu. Funkce v matematice, záviset pouze na jejich argumenty a nemá žádné vedlejší účinky. V matematické funkce `f(x) = x + 1`, hodnota `f(x)` závisí jenom na základě hodnoty `x`. Čistě funkce do funkčního programování se stejným způsobem.

Při zápisu čistě funkce, funkce musí záviset pouze na jeho argumenty a nebude provádět žádnou akci, která má za následek vedlejší účinek.

Tady je příklad-čistě funkce, protože závisí na globální, proměnlivý stav:

```fsharp
let mutable value = 1

let addOneToValue x = x + value
```

`addOneToValue` Funkce je jasně znečištěná, protože `value` lze změnit kdykoli mít jinou hodnotu než 1. V závislosti na globální hodnoty tohoto vzoru je třeba se vyhnout do funkčního programování.

Tady je další příklad – čistě funkce, protože vykonává vedlejší účinek:

```fsharp
let addOneToValue x = 
    printfn "x is %d" x
    x + 1
```

I když tato funkce není závislý na globální hodnoty, zapíše hodnoty `x` do výstupu programu. I když není nic špatného ze své podstaty s tím, znamená, že funkce není čistě. Pokud jiné části programu, závisí na něco mimo programu, jako je například výstupní vyrovnávací paměť následným voláním této funkce může ovlivnit další část programu.

Odebírá `printfn` příkaz díky funkci čistě:

```fsharp
let addOneToValue x = x + 1
```

I když tato funkce není ze své podstaty _lepší_ než předchozí verze s `printfn` příkazu, to zaručit, že všechny této funkce je vrátit hodnotu. Libovolný počet volání této funkce vytvoří stejný výsledek: vyvolá pouze hodnotu. Předvídatelnost Dal čistoty je něco, co se snažte se o funkční mnoho programátorů.

### <a name="immutability"></a>Neměnnost

Nakonec jednou z nejvíce základní koncepty typu funkční programování je neměnnosti. V F#, všechny hodnoty jsou neměnné ve výchozím nastavení. To znamená, že pokud je explicitně označit jako mutable nemohou být místně měněna.

V praxi práce s hodnotami neměnné znamená, že změníte svůj přístup k programování z "Budu muset něco změnit" k "budu potřebovat k vytvoření nové hodnoty".

Například přidáním 1 na hodnotu znamená, že vytváří novou hodnotu, nikoli mutace stávající:

```fsharp
let value = 1
let secondValue = value + 1
```

V F#, následující kód provede **není** mutovat `value` funkce; místo toho provádí kontrolu rovnosti:

```fsharp
let value = 1
value = value + 1 // Produces a 'bool' value!
```

Některé funkční programovací jazyky nepodporují mutace vůbec. V F#, DPM ji podporuje, ale není výchozí chování pro hodnoty.

Tento koncept se rozšiřuje i dál datové struktury. Funkční programování v neměnných datové struktury, jako je sad (a mnoho dalších) mají jinou implementaci než může být zpočátku očekávat. Entity typu přidání položky do sady nedojde ke změně sady, vytváří _nové_ nastavit s přidanou hodnotou. Pod pokličkou to často provádí různé datová struktura, která umožňuje efektivní sledování hodnotu tak, aby odpovídající znázornění dat mohou být zadány ve výsledku.

Tento styl práci s hodnotami a datové struktury je důležité, jak přistupovat ke všem jakoukoli operaci, která upravuje něco, jako kdyby vytvoří novou verzi celou věc nepropojili nutí. To umožňuje například rovnosti a srovnání být konzistentní vzhledem k aplikacím ve svých programech.

## <a name="next-steps"></a>Další kroky

V další části se bude vztahovat důkladně funkce zkoumání různých způsobů, jak lze využít v funkčního programování.

[Funkce první třídy](first-class-functions.md) zkoumá funkce hluboko, zobrazuje, jak je lze využít v různých kontextech.

## <a name="further-reading"></a>Další čtení

[Uvažujete funkčně](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) series je další informace o funkční programování s dalším skvělým zdrojem F#. Popisuje základní informace o funkční programování tak pragmatický a snadné čtení pomocí F# funkce pro objasnění konceptů.
