---
title: Operátory s povolenou hodnotou Null
description: Seznamte se s operátory s možnou hodnotou null F# , které jsou k dispozici v programovacím jazyce.
ms.date: 05/16/2016
ms.openlocfilehash: 9c747cf5c2e07ca9f80cef741d71d892fb437b3a
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424047"
---
# <a name="nullable-operators"></a>Operátory s povolenou hodnotou Null

Operátory s možnou hodnotou null jsou binární aritmetické nebo relační operátory, které pracují s nepovolenými aritmetickými typy na jedné nebo obou stranách. Typy s možnou hodnotou null se často vyskytují při práci s daty ze zdrojů, jako jsou databáze, které umožňují místo skutečných hodnot hodnoty null. Operátory s možnou hodnotou null se často používají ve výrazech dotazů. Kromě operátorů s možnou hodnotou null pro aritmetické a porovnání lze použít operátory převodu k převodu mezi typy s možnou hodnotou null. K dispozici jsou také verze určitých operátorů dotazů s možnou hodnotou null.

## <a name="table-of-nullable-operators"></a>Tabulka operátorů s možnou hodnotou null

V následující tabulce jsou uvedeny operátory s možnou F# hodnotou null, které jsou podporovány v jazyce.

|Nullable na levé straně|Nullable vpravo|Obě strany umožňují hodnotu null.|
|---|---|---|
|[? > =](https://msdn.microsoft.com/library/94d29e32-a204-4f60-a527-6b0af86268f3)|[> =?](https://msdn.microsoft.com/library/0a255d8e-8cae-4160-ae61-243a5d96583f)|[? > =?](https://msdn.microsoft.com/library/3051a50f-d276-4c84-9d73-bf2efeddef94)|
|[? >](https://msdn.microsoft.com/library/62dc0021-1312-4ac3-be87-798b60b81bb6)|[>?](https://msdn.microsoft.com/library/0ad1284b-de48-4a04-83d8-b6f13c9c8936)|[? >?](https://msdn.microsoft.com/library/dc18b6fa-30c4-47b0-9057-794439378a05)|
|[? < =](https://msdn.microsoft.com/library/56fddf0a-e4ca-4891-a3be-fad1876be3b6)|[< =?](https://msdn.microsoft.com/library/02454a0f-30ca-4e77-ad84-ee7837461804)|[? < =?](https://msdn.microsoft.com/library/5c37c28c-0b57-4da5-be11-5a123f7e8ee4)|
|[? <](https://msdn.microsoft.com/library/b71897f0-6e29-4c58-b0a7-a5bfa6f88917)|[<?](https://msdn.microsoft.com/library/be9ea40f-a67f-4e98-8067-a14046752e8b)|[? <?](https://msdn.microsoft.com/library/6f1962c8-5605-468c-94ae-f379ae98e17d)|
|[?=](https://msdn.microsoft.com/library/5cdc8ff6-244b-49cf-9376-69ecf249fd7c)|[=?](https://msdn.microsoft.com/library/d2102894-6a51-475d-890a-735568c31f87)|[?=?](https://msdn.microsoft.com/library/5f793f29-1084-4570-b1c1-17c1b7ef764b)|
|[? < >](https://msdn.microsoft.com/library/3643a5a8-2ea5-4ad6-82c4-83927c3884a0)|[> <?](https://msdn.microsoft.com/library/3179aace-70c4-4911-9258-619592214976)|[? < >?](https://msdn.microsoft.com/library/5da813d8-ee75-45b8-9ef4-146dcb6d394d)|
|[?+](https://msdn.microsoft.com/library/2e8ddd05-b3f3-41b3-9d73-938d9e540f3f)|[+?](https://msdn.microsoft.com/library/74772ea8-f010-493e-bdb5-ba347f2fd4f1)|[?+?](https://msdn.microsoft.com/library/57f28137-0f42-43d2-92af-cad8c6c9d05f)|
|[?-](https://msdn.microsoft.com/library/f237a7a6-89f2-48b2-a2fe-f0b98a2bedc2)|[-?](https://msdn.microsoft.com/library/4a345c07-314a-48f1-b557-ce072583589c)|[?-?](https://msdn.microsoft.com/library/e0024142-1d2a-4607-a39c-1eb1e86fa25a)|
|[?*](https://msdn.microsoft.com/library/519da708-5ad6-4075-9d74-d00441cd6078)|[*?](https://msdn.microsoft.com/library/04c47870-de7b-480d-98a0-f47593b4ffac)|[?*?](https://msdn.microsoft.com/library/e57057ba-9c3a-40ec-8401-150c2b25f75b)|
|[?/](https://msdn.microsoft.com/library/add02a42-f556-40a7-a168-fbf2053322e3)|[/?](https://msdn.microsoft.com/library/1de07646-3778-476d-8c61-5d37495d463c)|[?/?](https://msdn.microsoft.com/library/b17be0ac-bf98-4590-861d-a4dd6c6fa535)|
|[?%](https://msdn.microsoft.com/library/44297bba-1bd9-4ed2-a848-f1e1e598db87)|[%?](https://msdn.microsoft.com/library/a4c178e5-eec4-42e8-847f-90b24fc609fe)|[?%?](https://msdn.microsoft.com/library/dd555f20-1be3-4b8d-81f1-bf1921e62fda)|

## <a name="remarks"></a>Poznámky

Operátory s možnou hodnotou null jsou zahrnuté v modulu [NullableOperators](https://msdn.microsoft.com/library/2c3633c5-3f31-4d62-a9f8-272ad6b19007) v oboru názvů [Microsoft. FSharp. Linq](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d). Typ dat s možnou hodnotou null je `System.Nullable<'T>`.

V dotazech se typy s možnou hodnotou null nastanou při výběru dat ze zdroje dat, který namísto hodnot povoluje hodnoty null. V SQL Server databázi má každý datový sloupec v tabulce atribut, který označuje, zda jsou povoleny hodnoty null. Pokud jsou povoleny hodnoty null, data vrácená z databáze mohou obsahovat hodnoty null, které nemohou být reprezentovány primitivním datovým typem, například `int`, `float`a tak dále. Proto se data vrátí jako `System.Nullable<int>` namísto `int`a `System.Nullable<float>` místo `float`. Skutečnou hodnotu lze získat z objektu `System.Nullable<'T>` pomocí vlastnosti `Value` a můžete určit, zda objekt `System.Nullable<'T>` má hodnotu voláním metody `HasValue`. Další užitečnou metodou je `System.Nullable<'T>.GetValueOrDefault` metoda, která umožňuje získat hodnotu nebo výchozí hodnotu příslušného typu. Výchozí hodnota je určitá forma hodnoty "Zero", například 0, 0,0 nebo `false`.

Typy s možnou hodnotou null mohou být převedeny na primitivní typy neumožňující hodnotu null pomocí běžných operátorů převodu, jako je například `int` nebo `float`. Je také možné převést jeden typ s povolenou hodnotou null na jiný typ s možnou hodnotou null pomocí operátorů převodu pro typy s možnou hodnotou null. Příslušné operátory převodu mají stejný název jako standardní, ale jsou v samostatném modulu, což je modul s [možnou hodnotou null](https://msdn.microsoft.com/library/e7a4ea13-28cc-462e-bc3a-33131ace976e) v oboru názvů [Microsoft. FSharp. Linq](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d) . Tento obor názvů se obvykle otevírá při práci se výrazy dotazu. V takovém případě můžete použít operátory převodu s možnou hodnotou null přidáním předpony `Nullable.` k příslušnému operátoru převodu, jak je znázorněno v následujícím kódu.

```fsharp
open Microsoft.FSharp.Linq

let nullableInt = new System.Nullable<int>(10)

// Use the Nullable.float conversion operator to convert from one nullable type to another nullable type.
let nullableFloat = Nullable.float nullableInt

// Use the regular non-nullable float operator to convert to a non-nullable float.
printfn "%f" (float nullableFloat)
```

Výstup je `10.000000`.

Operátory dotazů pro datová pole s možnou hodnotou null, jako je například `sumByNullable`, existují také pro použití ve výrazech dotazů. Operátory dotazu pro typy neumožňující hodnotu null nejsou kompatibilní s typy s možnou hodnotou null, takže při práci s datovými hodnotami s možnou hodnotou null je nutné použít verzi příslušného operátoru dotazu s možnou hodnotou null. Další informace najdete v tématu [výrazy dotazů](../query-expressions.md).

Následující příklad ukazuje použití operátorů s možnou hodnotou null F# ve výrazu dotazu. První dotaz ukazuje, jak byste napsali dotaz bez operátoru s možnou hodnotou null. druhý dotaz zobrazí ekvivalentní dotaz, který používá operátor s možnou hodnotou null. Úplný kontext, včetně postupu nastavení databáze pro použití tohoto ukázkového kódu, naleznete v tématu [Návod: přístup k SQL Database pomocí zprostředkovatelů typů](../../tutorials/type-providers/index.md).

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

## <a name="see-also"></a>Viz také:

- [Zprostředkovatelé typů](../../tutorials/type-providers/index.md)
- [Výrazy dotazu](../query-expressions.md)
