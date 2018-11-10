---
title: Operátory s povolenou hodnotou Null (F#)
description: Další informace o operátorech s možnou hodnotou Null, které jsou k dispozici v programovacím jazyce F#.
ms.date: 05/16/2016
ms.openlocfilehash: 42df74a56831fb0a5d6df34db4321f5b228993c2
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "44086280"
---
# <a name="nullable-operators"></a>Operátory s povolenou hodnotou Null

Operátory s povolenou hodnotou Null jsou binární operátory aritmetický nebo jejich porovnávání, které využívají službu na jednu nebo obě strany aritmetické typy připouštějící hodnotu Null. Typy s možnou hodnotou Null jsou vyvolány často při práci s daty ze zdrojů, jako jsou databáze, které povolit hodnoty Null místo skutečných hodnot. Operátory s povolenou hodnotou Null jsou často použít ve výrazech dotazů. Kromě s možnou hodnotou Null operátory pro aritmetické operace a porovnání operátory převodu lze pro převod mezi typy připouštějící hodnotu Null. Existují také s možnou hodnotou Null verze některých operátorů pro dotazování.

## <a name="table-of-nullable-operators"></a>Tabulka operátory s povolenou hodnotou Null

V následující tabulce jsou uvedeny podporovány v jazyce F# operátory s povolenou hodnotou Null.

|Na levé straně s možnou hodnotou Null|S povolenou hodnotou Null vpravo|Obě strany s možnou hodnotou Null|
|---|---|---|
|[?>=](https://msdn.microsoft.com/library/94d29e32-a204-4f60-a527-6b0af86268f3)|[>=?](https://msdn.microsoft.com/library/0a255d8e-8cae-4160-ae61-243a5d96583f)|[?>=?](https://msdn.microsoft.com/library/3051a50f-d276-4c84-9d73-bf2efeddef94)|
|[?>](https://msdn.microsoft.com/library/62dc0021-1312-4ac3-be87-798b60b81bb6)|[>?](https://msdn.microsoft.com/library/0ad1284b-de48-4a04-83d8-b6f13c9c8936)|[?>?](https://msdn.microsoft.com/library/dc18b6fa-30c4-47b0-9057-794439378a05)|
|[?<=](https://msdn.microsoft.com/library/56fddf0a-e4ca-4891-a3be-fad1876be3b6)|[<=?](https://msdn.microsoft.com/library/02454a0f-30ca-4e77-ad84-ee7837461804)|[?<=?](https://msdn.microsoft.com/library/5c37c28c-0b57-4da5-be11-5a123f7e8ee4)|
|[?<](https://msdn.microsoft.com/library/b71897f0-6e29-4c58-b0a7-a5bfa6f88917)|[<?](https://msdn.microsoft.com/library/be9ea40f-a67f-4e98-8067-a14046752e8b)|[?<?](https://msdn.microsoft.com/library/6f1962c8-5605-468c-94ae-f379ae98e17d)|
|[?=](https://msdn.microsoft.com/library/5cdc8ff6-244b-49cf-9376-69ecf249fd7c)|[=?](https://msdn.microsoft.com/library/d2102894-6a51-475d-890a-735568c31f87)|[?=?](https://msdn.microsoft.com/library/5f793f29-1084-4570-b1c1-17c1b7ef764b)|
|[?<>](https://msdn.microsoft.com/library/3643a5a8-2ea5-4ad6-82c4-83927c3884a0)|[<>?](https://msdn.microsoft.com/library/3179aace-70c4-4911-9258-619592214976)|[?<>?](https://msdn.microsoft.com/library/5da813d8-ee75-45b8-9ef4-146dcb6d394d)|
|[?+](https://msdn.microsoft.com/library/2e8ddd05-b3f3-41b3-9d73-938d9e540f3f)|[+?](https://msdn.microsoft.com/library/74772ea8-f010-493e-bdb5-ba347f2fd4f1)|[?+?](https://msdn.microsoft.com/library/57f28137-0f42-43d2-92af-cad8c6c9d05f)|
|[?-](https://msdn.microsoft.com/library/f237a7a6-89f2-48b2-a2fe-f0b98a2bedc2)|[-?](https://msdn.microsoft.com/library/4a345c07-314a-48f1-b557-ce072583589c)|[?-?](https://msdn.microsoft.com/library/e0024142-1d2a-4607-a39c-1eb1e86fa25a)|
|[?*](https://msdn.microsoft.com/library/519da708-5ad6-4075-9d74-d00441cd6078)|[*?](https://msdn.microsoft.com/library/04c47870-de7b-480d-98a0-f47593b4ffac)|[?*?](https://msdn.microsoft.com/library/e57057ba-9c3a-40ec-8401-150c2b25f75b)|
|[?/](https://msdn.microsoft.com/library/add02a42-f556-40a7-a168-fbf2053322e3)|[/?](https://msdn.microsoft.com/library/1de07646-3778-476d-8c61-5d37495d463c)|[?/?](https://msdn.microsoft.com/library/b17be0ac-bf98-4590-861d-a4dd6c6fa535)|
|[?%](https://msdn.microsoft.com/library/44297bba-1bd9-4ed2-a848-f1e1e598db87)|[%?](https://msdn.microsoft.com/library/a4c178e5-eec4-42e8-847f-90b24fc609fe)|[?%?](https://msdn.microsoft.com/library/dd555f20-1be3-4b8d-81f1-bf1921e62fda)|

## <a name="remarks"></a>Poznámky

Operátory s povolenou hodnotou Null jsou součástí [NullableOperators](https://msdn.microsoft.com/library/2c3633c5-3f31-4d62-a9f8-272ad6b19007) modulu v oboru názvů [Microsoft.fsharp.Linq –](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d). Typ s možnou hodnotou NULL dat je `System.Nullable<'T>`.

Typy připouštějící hodnotu Null ve výrazech dotazů nastat při výběru dat ze zdroje dat, která umožňuje místo hodnoty Null. Každý datový sloupec v tabulce v databázi serveru SQL Server má atribut, který určuje, zda jsou povoleny hodnoty Null. Pokud jsou hodnoty Null povoleny, data vrácená z databáze může obsahovat hodnoty Null, které nemůže být reprezentována primitivní datový typ jako `int`, `float`, a tak dále. Proto, data jsou vrácena jako `System.Nullable<int>` místo `int`, a `System.Nullable<float>` místo `float`. Skutečnou hodnotu lze získat z `System.Nullable<'T>` s použitím `Value` vlastnosti kde můžete zjistit, zda `System.Nullable<'T>` objekt má hodnotu voláním `HasValue` metoda. Další užitečné metodou je `System.Nullable<'T>.GetValueOrDefault` metodu, která vám umožní získat hodnotu nebo výchozí hodnotu příslušného typu. Výchozí hodnota je nějakou formu "žádný" hodnotu, například 0, 0.0, nebo `false`.

Typy s možnou hodnotou Null se může převést na primitivní typy neumožňující pomocí operátorů převodu obvyklé například `int` nebo `float`. Je také možné převést z jednoho typu s možnou hodnotou Null na jiný typ připouštějící hodnotu Null pomocí operátorů převodu pro typy připouštějící hodnotu Null. Operátory převodu vhodné mít stejný název jako standardní, ale jsou v samostatný modul [Nullable](https://msdn.microsoft.com/library/e7a4ea13-28cc-462e-bc3a-33131ace976e) v modulu [Microsoft.fsharp.Linq –](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d) oboru názvů. Obvykle je tento obor názvů otevřít při práci s výrazy dotazu. V takovém případě můžete použít operátory převodu s možnou hodnotou Null přidáním předpony `Nullable.` operátoru odpovídající převodu, jak je znázorněno v následujícím kódu.

```fsharp
open Microsoft.FSharp.Linq

let nullableInt = new System.Nullable<int>(10)

// Use the Nullable.float conversion operator to convert from one nullable type to another nullable type.
let nullableFloat = Nullable.float nullableInt

// Use the regular non-nullable float operator to convert to a non-nullable float.
printfn "%f" (float nullableFloat)
```

Výstup je `10.000000`.

Dotazování na s možnou hodnotou Null datová pole, operátory, jako `sumByNullable`, existují také pro použití ve výrazech dotazů. Operátory dotazu pro typy neumožňující nejsou kompatibilního s typy s možnou hodnotou Null, proto při práci s hodnotami dat s možnou hodnotou null je nutné použít s možnou hodnotou Null verzi operátoru odpovídající dotaz. Další informace najdete v tématu [– výrazy dotazů](../query-expressions.md).

Následující příklad ukazuje použití operátory s povolenou hodnotou Null ve výrazu dotazu F#. První dotaz zobrazí, jak byste napsat dotaz bez operátor s možnou hodnotou Null; druhý dotaz zobrazí ekvivalentní dotaz, který používá operátor s možnou hodnotou Null. Úplný kontext, včetně postupu nastavení databáze při použití tohoto ukázkového kódu, naleznete v tématu [návod: přístup k SQL Database s použitím zprostředkovatelů typů](../../tutorials/type-providers/accessing-a-sql-database.md).

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
