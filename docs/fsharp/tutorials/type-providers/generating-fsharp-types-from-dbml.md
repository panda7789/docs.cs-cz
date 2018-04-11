---
title: 'Návod: Generování typů F# ze souboru DBML (F#)'
description: 'Informace o vytvoření typů F # pro data z databáze v F # 3.0, pokud máte v souboru DBML kódování informace o schématu.'
keywords: 'Visual f #, f #, funkční programování'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 6fbb6ccc-248f-4226-95e9-f6f99541dbe4
ms.openlocfilehash: 3cd8df9becac0d1a8842eb22e2f772eee6307acf
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/10/2018
---
# <a name="walkthrough-generating-f-types-from-a-dbml-file"></a>Návod: Generování typů F# ze souboru DBML

> [!NOTE]
Tento průvodce byl vytvořen pro F # 3.0 a budou aktualizovány.  V tématu [FSharp.Data](https://fsharp.github.io/FSharp.Data/) pro různé platformy, aktuální typ poskytovatele.

> [!NOTE]
Rozhraní API referenčních odkazů se dostanete na webu MSDN.  Referenční dokumentace rozhraní API docs.microsoft.com není dokončena.

Tento názorný postup pro F # 3.0 popisuje postup vytvoření typů dat z databáze, pokud máte v souboru DBML kódování informace o schématu. Technologie LINQ to SQL používá k reprezentaci schéma databáze tohoto formátu souboru. Technologie LINQ to SQL souboru schématu v sadě Visual Studio můžete vygenerovat pomocí Návrhář relací objektů (relací objektů). Další informace najdete v tématu [přehled Návrhář relací objektů](https://msdn.microsoft.com/library/bb384511.aspx) a [generování kódu v technologii LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).

Typ zprostředkovatele databáze Markup Language (DBML) umožňuje psát kód, který používá typy podle schématu databáze, aniž by bylo potřeba zadat statické připojovací řetězec v době kompilace. Který může být užitečné, pokud je potřeba povolit možnost, že poslední aplikace bude používat jiné databázi, jiné přihlašovací údaje nebo jiné připojovací řetězec než ten, který použijete k vývoji aplikace. Pokud máte připojení k databázi direct, který můžete použít při kompilaci a jedná se o stejné databáze a přihlašovacích údajů, které bude nakonec použijete v integrované aplikaci, můžete taky sqldataconnection – zprostředkovatel typu. Další informace najdete v tématu [návod: přístup k databázi SQL pomocí zprostředkovatelé typu](accessing-a-sql-database.md).

Tento návod ukazuje následující úlohy. Mají být provedeny v uvedeném pořadí návod úspěšné:


- Vytvoření souboru DBML
<br />

- Vytvoření a nastavení projektu F #
<br />

- Konfigurace zprostředkovatele typů a generování typy
<br />

- Dotazování na databázi
<br />


## <a name="prerequisites"></a>Požadavky

## <a name="creating-a-dbml-file"></a>Vytvoření souboru DBML
Pokud nemáte k testování v databázi, vytvořit podle pokynů uvedených v dolní části [návod: přístup k databázi SQL pomocí zprostředkovatelé typu](accessing-a-sql-database.md). Pokud budete postupovat podle těchto pokynů, vytvoříte databázi názvem databáze, která obsahuje několik jednoduchých tabulek a uložených procedur v systému SQL Server.

Pokud již máte soubor DBML, můžete přeskočit k části **vytvořit a nastavit si F # projekt**. Jinak můžete vytvořit soubor DBML danou existující databázi SQL a pomocí příkazového řádku nástroje SqlMetal.exe.


#### <a name="to-create-a-dbml-file-by-using-sqlmetalexe"></a>Vytvoření souboru DBML pomocí SqlMetal.exe

1. Otevřete **příkazový řádek vývojáře**.
<br />

2. Zajistěte, abyste měli přístup k SqlMetal.exe zadáním `SqlMetal.exe /?` na příkazovém řádku. SqlMetal.exe je obvykle nainstalovaný v části **Microsoft SDKs** složky v **Program Files** nebo **Program Files (x86)**.
<br />

3. Spusťte SqlMetal.exe s následujících možností příkazového řádku. Nahraďte správnou cestu místě `c:\destpath` pro vytvoření souboru dbml a vkládání odpovídající hodnoty pro databázový server, instanci název a název databáze.
<br />

```
  SqlMetal.exe /sprocs /dbml:C:\destpath\MyDatabase.dbml /server:SERVER\INSTANCE /database:MyDatabase
```

>[!NOTE]
Pokud SqlMetal.exe má potíže při vytváření souboru problémy s oprávněními, změňte do složky, ke které máte oprávnění k zápisu do aktuální adresář.


4. Můžete také prohlédnout další dostupné možnosti příkazového řádku. Například jsou možnosti, které můžete použít, pokud chcete, zobrazení a funkcí SQL, které jsou součástí generovaného typy. Další informace najdete v tématu [SqlMetal.exe &#40;nástroj pro vytváření kódu&#41;](https://msdn.microsoft.com/library/bb386987).
<br />


## <a name="creating-and-setting-up-an-f-project"></a>Vytvoření a nastavení projektu F #
V tomto kroku vytvořte projekt a přidejte příslušné odkazy na použití DBML typ poskytovatele.


#### <a name="to-create-and-set-up-an-f-project"></a>Postup vytvoření a nastavení projektu jazyka F#

1. Přidáte nový projekt konzolové aplikace v F # do řešení.
<br />

2. V **Průzkumníku řešení**, otevřete místní nabídku pro **odkazy**a potom zvolte **přidat odkaz na**.
<br />

3. V **sestavení** oblasti, vyberte **Framework** uzel a potom v seznamu dostupných sestavení, vyberte **System.Data** a **System.Data.Linq**  sestavení.
<br />

4. V **sestavení** oblasti, zvolte **rozšíření**a potom v seznamu dostupných sestavení, zvolte **FSharp.Data.TypeProviders**.
<br />

5. Vyberte **OK** tlačítko přidáte odkazy na tyto sestavení do projektu.
<br />

6. (Volitelné). Zkopírujte dbml soubor, který jste vytvořili v předchozím kroku a vložte soubor ve složce hlavní pro váš projekt. Tato složka obsahuje soubor projektu (.fsproj) a soubory kódu. Na řádku nabídek zvolte **projektu**, **přidat existující položku**a pak zadejte souboru DBML ho přidejte do projektu. Pokud tyto kroky dokončíte, můžete vynechat statický parametr resolutionfolder – v dalším kroku.
<br />

## <a name="configuring-the-type-provider"></a>Konfigurace poskytovatele typu
V této části vytvoříte zprostředkovatele typů a generovat typy ze schématu, která je popsána v souboru DBML.


#### <a name="to-configure-the-type-provider-and-generate-the-types"></a>Ke konfiguraci poskytovatele za typ a generování typy

- Přidejte kód, který otevře **TypeProviders** obor názvů a vytvoří instanci zprostředkovatele typu DBML souboru, který chcete použít. Pokud jste přidali soubor DBML do projektu, můžete vynechat statický parametr resolutionfolder –.
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type dbml = DbmlFile<"MyDatabase.dbml", ResolutionFolder = @"<path-to-folder-that-contains-.dbml-file>">

// This connection string can be specified at run time.
let connectionString = "Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;"
let dataContext = new dbml.Mydatabase(connectionString)
```

Typ DataContext poskytuje přístup k všechny vygenerované typy a dědí z `System.Data.Linq.DataContext`. Dbmlfile – poskytovatel typů má různých statických parametry, které můžete nastavit. Například můžete použít jiný název pro typ DataContext zadáním `DataContext=MyDataContext`. V takovém případě kódu podobá následujícímu příkladu:
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type dbml = DbmlFile<"MyDatabase.dbml", ContextTypeName = "MyDataContext">

// This connection string can be specified at run time.
let connectionString = "Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;"
let db = new dbml.MyDataContext(connectionString)
```

## <a name="querying-the-database"></a>Dotazování na databázi
V této části použijete F # – výrazy dotazů k dotazování databáze.


#### <a name="to-query-the-data"></a>Postup dotazování na data

- Přidáte kód pro dotazování databáze.
<br />

```fsharp
  query {
    for row in db.Table1 do
    where (row.TestData1 > 2)
    select row
  } |> Seq.iter (fun row -> printfn "%d %s" row.TestData1 row.Name)
```

## <a name="next-steps"></a>Další kroky
Můžete pokračovat pro ostatní výrazy dotazu nebo získání připojení k databázi z kontextu dat a provádět běžné operace dat ADO.NET. Další kroky, najdete v částech po "dotazu Data" v [návod: přístup k databázi SQL pomocí zprostředkovatelé typu](accessing-a-sql-database.md).


## <a name="see-also"></a>Viz také
[Dbmlfile – zprostředkovatel typu](https://msdn.microsoft.com/visualfsharpdocs/conceptual/dbmlfile-type-provider-%5bfsharp%5d)

[Zprostředkovatelé typů](index.md)

[Návod: Přístup k databázi SQL s použitím zprostředkovatelů typů](accessing-a-sql-database.md)

[SqlMetal.exe &#40;nástroj pro vytváření kódu&#41;](https://msdn.microsoft.com/library/bb386987)

[Výrazy dotazu](../../language-reference/query-expressions.md)
