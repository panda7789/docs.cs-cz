---
title: Porovnání s System. data. SQLite
ms.date: 12/13/2019
description: Popisuje některé rozdíly mezi knihovnami Microsoft. data. sqlite a System. data. SQLite.
ms.openlocfilehash: 076bbc6f746cf9296c96ec73047397a21a3b2558
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900716"
---
# <a name="comparison-to-systemdatasqlite"></a>Porovnání s System. data. SQLite

V 2005 vytvoří Robert Simpson vytvořenou hodnotu System. data. SQLite, zprostředkovatele SQLite pro ADO.NET 2,0. V 2010 se týmu SQLite prováděla údržba a vývoj projektu. Je také vhodné poznamenat, že tým mono rozvětvení kód v 2007 jako mono. data. sqlite. System. data. SQLite má dlouhou historii a vyvinula do stabilního a plně funkčního poskytovatele ADO.NET kompletní s nástroji sady Visual Studio. Nové verze pokračují v dodávání sestavení kompatibilních se všemi verzemi .NET Framework zpět na verzi 2,0 a dokonce i prostředí .NET Compact Framework 3,5.

První verze .NET Core (vydaná v 2016) byla jednou, odlehčená, moderní a meziplatformovaná implementace .NET. Vystaralá rozhraní API a rozhraní API s dalšími moderními alternativami byly záměrně odebrány. ADO.NET neobsahují žádná rozhraní API datové sady (včetně DataTable a DataAdapter).

Entity Framework tým byl trochu obeznámen se základem kódu System. data. SQLite. Brice Lambson, člen týmu EF dřív pomohl týmu SQLite přidat podporu pro Entity Framework verze 5 a 6. Brice také experimentování s vlastní implementací zprostředkovatele ADO.NET od stejného okamžiku, kdy se naplánovalo rozhraní .NET Core. Po dlouhé diskuzi se tým Entity Framework rozhodl vytvořit Microsoft. data. sqlite na základě prototypu Brice. To jim umožní vytvořit novou odlehčenou a moderní implementaci, která by odpovídala cílům .NET Core.

Jako příklad toho, co je to více moderní, je zde kód pro vytvoření [uživatelsky definované funkce](user-defined-functions.md) v System. data. sqlite a Microsoft. data. sqlite.

```csharp
// System.Data.SQLite
connection.BindFunction(
    new SQLiteFunctionAttribute("ceiling", 1, FunctionType.Scalar),
    (Func<object[], object>)((object[] args) => Math.Ceiling((double)((object[])args[1])[0])),
    null);

// Microsoft.Data.Sqlite
connection.CreateFunction(
    "ceiling",
    (double arg) => Math.Ceiling(arg));
```

V 2017 se v .NET Core 2,0 došlo ke změně strategie. Bylo rozhodnuto, že kompatibilita s .NET Framework byla zásadní pro úspěch .NET Core. Mnohé z odebraných rozhraní API, včetně rozhraní API datových sad, se přidaly zpátky. Stejně jako u mnoha dalších souborů je tato odblokovaná systémová. data. SQLite, což umožňuje také jeho přenos do .NET Core. Původní cíl Microsoft. data. sqlite, který je lehký a moderní, ale stále zůstává. Podrobnosti o rozhraních API ADO.NET, která nejsou implementována společností Microsoft. data. sqlite, najdete v tématu [ADO.NET omezení](adonet-limitations.md) .

Při přidání nových funkcí do Microsoft. data. sqlite se vezme v úvahu návrh System. data. SQLite. Zkusíme, pokud je to možné, aby se mezi nimi minimalizovaly změny mezi dvěma, aby se mezi nimi usnadnily přechody.

## <a name="data-types"></a>Typy dat

Největší rozdíl mezi Microsoft. data. sqlite a System. data. SQLite je způsob, jakým jsou zpracovávány datové typy. Jak je popsáno v [datových typech](types.md), Microsoft. data. sqlite se nepokouší skrýt základní quirkinessy SQLite, což umožňuje zadat libovolný řetězec jako typ sloupce a má pouze čtyři primitivní typy: integer, Real, text a BLOB.

System. data. SQLite aplikuje další sémantiku na typy sloupců mapování přímo na typy .NET. To dává poskytovateli podrobnější dojem, ale obsahuje nějaké hrubá okraje. Například museli zavést nový příkaz SQL (typy) pro určení typů sloupců výrazů v příkazech SELECT.

## <a name="connection-strings"></a>Připojovací řetězce

Microsoft. data. sqlite má mnoho méně klíčových slov pro [připojovací řetězec](connection-strings.md) . V následující tabulce jsou uvedeny alternativy, které lze použít místo toho.

| Klíčové slovo          | Jiné                                         |
| ---------------- | --------------------------------------------------- |
| Velikost mezipaměti       | Posílají`PRAGMA cache_size = <pages>`                  |
| Výchozí časový limit  | Použití vlastnosti DefaultTimeout v SqliteConnection |
| FailIfMissing    | Použití `Mode=ReadWrite`                                |
| FullUri          | Použití klíčového slova zdroje dat                         |
| Režim deníku     | Posílají`PRAGMA journal_mode = <mode>`                 |
| Starší verze formátu    | Posílají`PRAGMA legacy_file_format = 1`                |
| Maximální počet stránek   | Posílají`PRAGMA max_page_count = <pages>`              |
| Velikost stránky        | Posílají`PRAGMA page_size = <bytes>`                   |
| Jen pro čtení        | Použití `Mode=ReadOnly`                                 |
| Synchronní      | Posílají`PRAGMA synchronous = <mode>`                  |
| Identifikátor URI              | Použití klíčového slova zdroje dat                         |
| UseUTF16Encoding | Posílají`PRAGMA encoding = 'UTF-16'`                   |

## <a name="authorization"></a>Autorizace

Microsoft. data. sqlite nemá žádné rozhraní API k odhalení zpětného volání autorizačního subjektu. K poskytnutí zpětné vazby k této funkci použijte [#13835](https://github.com/dotnet/efcore/issues/13835) problému.

## <a name="data-change-notifications"></a>Oznámení o změnách dat

Microsoft. data. sqlite nemá žádná rozhraní API, která zveřejňují oznámení o změnách dat SQLite. K poskytnutí zpětné vazby k této funkci použijte [#13827](https://github.com/dotnet/efcore/issues/13827) problému.

## <a name="virtual-table-modules"></a>Moduly virtuálních tabulek

Microsoft. data. sqlite nemá žádné rozhraní API pro vytváření modulů virtuálních tabulek. K poskytnutí zpětné vazby k této funkci použijte [#13823](https://github.com/dotnet/efcore/issues/13823) problému.

## <a name="see-also"></a>Viz také

* [Typy dat](types.md)
* [Připojovací řetězce](connection-strings.md)
* [Šifrování](encryption.md)
* [Omezení ADO.NET](adonet-limitations.md)
* [Omezení dapperem](dapper-limitations.md)
