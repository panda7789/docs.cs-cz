---
title: "Operátory s povolenou hodnotou Null (F#)"
description: "Seznamte se s možnou hodnotou Null operátory, které jsou k dispozici v programovací jazyk F #."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3108c4ac-9e13-464d-a829-084a6eba038f
ms.openlocfilehash: b3c55dcbfd70c9bcddcc4a990b19a5b92620f822
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="nullable-operators"></a>Operátory s povolenou hodnotou Null

Operátory s povolenou hodnotou Null jsou binární operátory aritmetické nebo porovnání, které pracují s typy s možnou hodnotou Null aritmetické na jednoho nebo obou stranách. Typy s možnou hodnotou Null jsou vyvolány často, při práci s daty ze zdrojů, jako jsou třeba databáze, které umožňují hodnoty Null místo skutečných hodnot. Operátory s povolenou hodnotou Null se často používají ve výrazech dotazů. Kromě s možnou hodnotou Null operátory pro porovnání a aritmetické operátory převodu slouží pro převod mezi typy s možnou hodnotou Null. Existují také s možnou hodnotou Null verzích určité operátory dotazu.


## <a name="table-of-nullable-operators"></a>Tabulka operátory s povolenou hodnotou Null
Následující tabulka uvádí s možnou hodnotou Null operátory podporované v jazyce F #.

|Na levé straně s možnou hodnotou Null|S možnou hodnotou Null vpravo|Na obou stranách s možnou hodnotou Null|
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

Typy s možnou hodnotou Null ve výrazech dotazů nastat při výběru dat ze zdroje dat, která umožňuje hodnoty Null místo hodnoty. Každý datový sloupec v tabulce v databázi systému SQL Server má atribut, který označuje, zda jsou hodnoty Null povoleny. Pokud jsou hodnoty Null povoleny, s daty vrácenými z databáze může obsahovat hodnoty Null, která nemůže být reprezentovaná primitivní datový typ jako `int`, `float`a tak dále. Proto, že data jsou vrácena jako `System.Nullable<int>` místo `int`, a `System.Nullable<float>` místo `float`. Skutečné hodnoty lze získat z `System.Nullable<'T>` objekt pomocí `Value` vlastnost a můžete zjistit, zda `System.Nullable<'T>` objekt má hodnotu voláním `HasValue` metoda. Další užitečné metodou je `System.Nullable<'T>.GetValueOrDefault` metodu, která umožňuje získat hodnotu nebo výchozí hodnotu příslušného typu. Výchozí hodnota je určitou formu "nula" hodnotu, třeba 0, 0,0, nebo `false`.

Typy s možnou hodnotou Null může převést na hodnotu Null primitivní typy, jako použití operátorů obvyklé převodu `int` nebo `float`. Je také možné převést jeden typ s možnou hodnotou Null na jiný typ s možnou hodnotou Null pomocí operátory převodu pro typy s možnou hodnotou Null. Operátory převodu odpovídající mají stejný název jako standardní, ale jsou v samostatný modul, [Nullable](https://msdn.microsoft.com/library/e7a4ea13-28cc-462e-bc3a-33131ace976e) modulu v [Microsoft.fsharp.Linq –](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d) oboru názvů. Při práci s výrazy dotazů se obvykle, otevřete tento obor názvů. V takovém případě můžete použít operátory s povolenou hodnotou Null převodu přidáním předpony `Nullable.` operátor odpovídající převodu, jak je znázorněno v následujícím kódu.

```fsharp
open Microsoft.FSharp.Linq

let nullableInt = new System.Nullable<int>(10)

// Use the Nullable.float conversion operator to convert from one nullable type to another nullable type.
let nullableFloat = Nullable.float nullableInt

// Use the regular non-nullable float operator to convert to a non-nullable float.
printfn "%f" (float nullableFloat)
```

Výstupem je `10.000000`.

Dotaz na hodnotu Null datová pole, operátory, jako `sumByNullable`, existují také pro použití ve výrazech dotazů. Operátory dotazu pro použití hodnot Null typy nejsou typu kompatibilní s typy s možnou hodnotou Null, je nutné použít s možnou hodnotou Null verzi operátor odpovídající dotazu při práci s hodnotami dat s možnou hodnotou Null. Další informace najdete v tématu [výrazy dotazů](../query-expressions.md).

Následující příklad ukazuje použití operátory s povolenou hodnotou Null ve výrazu dotazu F #. První dotaz ukazuje, jak by napsat dotaz bez s možnou hodnotou Null operátor; druhý dotaz zobrazí ekvivalentní dotaz, který používá operátor s možnou hodnotou Null. Kontext úplné, včetně toho, jak nastavit databázi použít tento ukázkový kód, najdete v části [návod: přístup k databázi SQL pomocí zprostředkovatelé typu](../../tutorials/type-providers/accessing-a-sql-database.md).

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

[Zprostředkovatelé typů](../../tutorials/type-providers/index.md)

[Výrazy dotazů](../query-expressions.md)
