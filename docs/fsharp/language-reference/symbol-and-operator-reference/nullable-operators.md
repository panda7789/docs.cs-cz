---
title: Operátory s povolenou hodnotou Null
description: 'Seznamte se s operátory s možnou hodnotou null, které jsou k dispozici v programovacím jazyce F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 951692ba22781f7f9e759c55bc708fc24f7a5014
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559138"
---
# <a name="nullable-operators"></a>Operátory s povolenou hodnotou Null

Operátory s možnou hodnotou null jsou binární aritmetické nebo relační operátory, které pracují s nepovolenými aritmetickými typy na jedné nebo obou stranách. Typy s možnou hodnotou null se často vyskytují při práci s daty ze zdrojů, jako jsou databáze, které umožňují místo skutečných hodnot hodnoty null. Operátory s možnou hodnotou null se často používají ve výrazech dotazů. Kromě operátorů s možnou hodnotou null pro aritmetické a porovnání lze použít operátory převodu k převodu mezi typy s možnou hodnotou null. K dispozici jsou také verze určitých operátorů dotazů s možnou hodnotou null.

## <a name="table-of-nullable-operators"></a>Tabulka operátorů s možnou hodnotou null

V následující tabulce jsou uvedeny operátory s možnou hodnotou null podporované v jazyce F #.

|Nullable na levé straně|Nullable vpravo|Obě strany umožňují hodnotu null.|
|---|---|---|
|[? >=](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3E=%20))|[>=?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%3E=?%20))|[? >=?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3E=?%20))|
|[? >](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3E%20))|[>?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%3E?%20))|[? >?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3E?%20))|
|[? <=](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C=%20))|[<=?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%3C=?%20))|[? <=?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C=?%20))|
|[? <](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C%20))|[<?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%3C?%20))|[? <?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C?%20))|
|[?=](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?=%20))|[=?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20=?%20))|[?=?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?=?%20))|
|[? <>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C%3E%20))|[<>?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%3C%3E?%20))|[? <>?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C%3E?%20))|
|[?+](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?+%20))|[+?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20+?%20))|[?+?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?+?%20))|
|[?-](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?-%20))|[-?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20-?%20))|[?-?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?-?%20))|
|[?*](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?*%20))|[*?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20*?%20))|[?*?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?*?%20))|
|[?/](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?/%20))|[/?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20/?%20))|[?/?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?/?%20))|
|[?%](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%%20))|[%?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%?%20))|[?%?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%?%20))|

## <a name="remarks"></a>Poznámky

Operátory s možnou hodnotou null jsou zahrnuty v modulu [NullableOperators](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html) v oboru názvů [FSharp. Linq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq.html). Typ pro data s možnou hodnotou null je `System.Nullable<'T>` .

V dotazech se typy s možnou hodnotou null nastanou při výběru dat ze zdroje dat, který namísto hodnot povoluje hodnoty null. V SQL Server databázi má každý datový sloupec v tabulce atribut, který označuje, zda jsou povoleny hodnoty null. Pokud jsou povoleny hodnoty null, data vrácená z databáze mohou obsahovat hodnoty null, které nemohou být reprezentovány primitivním datovým typem `int` , například, `float` a tak dále. Proto se data vrátí jako `System.Nullable<int>` místo `int` a `System.Nullable<float>` místo `float` . Skutečnou hodnotu lze získat z `System.Nullable<'T>` objektu pomocí `Value` vlastnosti a lze určit, zda `System.Nullable<'T>` má objekt hodnotu voláním `HasValue` metody. Další užitečnou metodou je `System.Nullable<'T>.GetValueOrDefault` metoda, která umožňuje získat hodnotu nebo výchozí hodnotu příslušného typu. Výchozí hodnota je určitá forma hodnoty "Zero", například 0, 0,0 nebo `false` .

Typy s možnou hodnotou null mohou být převedeny na primitivní typy neumožňující hodnotu null pomocí běžných operátorů převodu, například `int` nebo `float` . Je také možné převést jeden typ s povolenou hodnotou null na jiný typ s možnou hodnotou null pomocí operátorů převodu pro typy s možnou hodnotou null. Příslušné operátory převodu mají stejný název jako standardní, ale jsou v samostatném modulu, v oboru názvů [FSharp. Linq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq.html) , který je modulem [Nullable](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullablemodule.html) . Tento obor názvů se obvykle otevírá při práci se výrazy dotazu. V takovém případě můžete použít operátory převodu s možnou hodnotou null přidáním předpony `Nullable.` příslušnému operátoru převodu, jak je znázorněno v následujícím kódu.

```fsharp
open Microsoft.FSharp.Linq

let nullableInt = new System.Nullable<int>(10)

// Use the Nullable.float conversion operator to convert from one nullable type to another nullable type.
let nullableFloat = Nullable.float nullableInt

// Use the regular non-nullable float operator to convert to a non-nullable float.
printfn "%f" (float nullableFloat)
```

Výstup je `10.000000` .

Operátory dotazů v datových polích s možnou hodnotou null, jako například `sumByNullable` , existují také pro použití ve výrazech dotazů. Operátory dotazu pro typy neumožňující hodnotu null nejsou kompatibilní s typy s možnou hodnotou null, takže při práci s datovými hodnotami s možnou hodnotou null je nutné použít verzi příslušného operátoru dotazu s možnou hodnotou null. Další informace najdete v tématu [výrazy dotazů](../query-expressions.md).

Následující příklad ukazuje použití operátorů s možnou hodnotou null ve výrazu dotazu jazyka F #. První dotaz ukazuje, jak byste napsali dotaz bez operátoru s možnou hodnotou null. druhý dotaz zobrazí ekvivalentní dotaz, který používá operátor s možnou hodnotou null. Úplný kontext, včetně postupu nastavení databáze pro použití tohoto ukázkového kódu, naleznete v tématu [Návod: přístup k SQL Database pomocí zprostředkovatelů typů](../../tutorials/type-providers/index.md).

```fsharp
open System
open System.Data
open System.Data.Linq
open Microsoft.FSharp.Data.TypeProviders
open Microsoft.FSharp.Linq

[<Generate>]
type dbSchema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;">

let db = dbSchema.GetDataContext()

query {
    for row in db.Table2 do
    where (row.TestData1.HasValue && row.TestData1.Value > 2)
    select row
} |> Seq.iter (fun row -> printfn "%d %s" row.TestData1.Value row.Name)

query {
    for row in db.Table2 do
    // Use a nullable operator ?>
    where (row.TestData1 ?> 2)
    select row
} |> Seq.iter (fun row -> printfn "%d %s" (row.TestData1.GetValueOrDefault()) row.Name)
```

## <a name="see-also"></a>Viz také

- [Zprostředkovatelé typů](../../tutorials/type-providers/index.md)
- [Výrazy dotazu](../query-expressions.md)
