---
title: Připojovací řetězce
ms.date: 12/13/2019
description: Podporovaná klíčová slova a hodnoty připojovacích řetězců.
ms.openlocfilehash: bb54d152bac62a86c2a49192cf678a745159164e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400447"
---
# <a name="connection-strings"></a>Připojovací řetězce

Připojovací řetězec se používá k určení způsobu připojení k databázi. Připojovací řetězce v Microsoft.Data.Sqlite postupujte podle [standardní ADO.NET syntaxe](../../../framework/data/adonet/connection-strings.md) jako středník-oddělený seznam klíčových slov a hodnot.

## <a name="keywords"></a>Klíčová slova

Následující klíčová slova připojovacího řetězce lze použít s Microsoft.Data.Sqlite:

### <a name="data-source"></a>Zdroj dat

Cesta k databázovému souboru. *DataSource* (bez mezery) a *Název souboru* jsou aliasy tohoto klíčového slova.

SQLite zpracuje cesty vzhledem k aktuálnímu pracovnímu adresáři. Lze také zadat absolutní cesty.

Pokud **prázdné**, SQLite vytvoří dočasnou databázi na disku, která je odstraněna při zavření připojení.

Pokud `:memory:`se používá databáze v paměti. Další informace naleznete [v tématu In-Memory databases](in-memory-databases.md).

Cesty začínající substitučním řetězcem `|DataDirectory|` jsou považovány za relativní cesty. Pokud je nastavena, cesty jsou vyrobeny vzhledem k hodnotě vlastnosti domény aplikace DataDirectory.

Toto klíčové slovo také podporuje [názvy souborů URI](https://www.sqlite.org/uri.html).

### <a name="mode"></a>Mode

Režim připojení.

| Hodnota           | Popis                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| ReadWriteCreate | Otevře databázi pro čtení a zápis a vytvoří ji, pokud neexistuje. Toto nastavení je výchozí. |
| ReadWrite       | Otevře databázi pro čtení a zápis.                                                        |
| ReadOnly        | Otevře databázi v režimu jen pro čtení.                                                              |
| Memory (Paměť)          | Otevře databázi v paměti.                                                                       |

### <a name="cache"></a>Mezipaměť

Režim ukládání do mezipaměti používaný připojením.

| Hodnota   | Popis                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| Výchozí | Používá výchozí režim základní knihovny SQLite. Toto nastavení je výchozí.                   |
| Private | Každé připojení používá privátní mezipaměť.                                                          |
| Sdílená  | Připojení sdílejí mezipaměť. Tento režim může změnit chování transakce a zamykání tabulky. |

### <a name="password"></a>Heslo

Šifrovací klíč. Pokud je `PRAGMA key` zadán, je odeslán ihned po otevření připojení.

> [!WARNING]
> Heslo nemá žádný vliv, pokud nativní knihovna SQLite nepodporuje šifrování.

### <a name="foreign-keys"></a>Cizí klíče

Hodnota označující, zda chcete povolit omezení cizího klíče.

| Hodnota   | Popis
| ------- | --- |
| True    | Odešle `PRAGMA foreign_keys = 1` ihned po otevření připojení.
| False   | Odešle `PRAGMA foreign_keys = 0` ihned po otevření připojení.
| (prázdné) | Neposílá `PRAGMA foreign_keys`. Toto nastavení je výchozí. |

Není třeba povolit cizí klíče, pokud, stejně jako v e_sqlite3, SQLITE_DEFAULT_FOREIGN_KEYS byl použit ke kompilaci nativní knihovny SQLite.

### <a name="recursive-triggers"></a>Rekurzivní aktivační události

Hodnota, která označuje, zda chcete povolit rekurzivní aktivační události.

| Hodnota | Popis                                                                 |
| ----- | --------------------------------------------------------------------------- |
| True  | Odešle `PRAGMA recursive_triggers` ihned po otevření připojení. |
| False | Neposílá `PRAGMA recursive_triggers`. Toto nastavení je výchozí.              |

## <a name="connection-string-builder"></a>Tvůrce připojovacího řetězce

Můžete použít <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> jako silně zadaný způsob vytváření připojovacích řetězců. Může být také použit k prevenci útoků injektáže spojovacího řetězce.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a>Příklady

### <a name="basic"></a>Basic

Základní připojovací řetězec se sdílenou mezipamětí pro lepší souběžnost.

```ConnectionString
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a>Šifrované

Šifrovaná databáze.

```ConnectionString
Data Source=Encrypted.db;Password=MyEncryptionKey
```

### <a name="read-only"></a>Jen pro čtení

Databáze jen pro čtení, kterou aplikace nemůže změnit.

```ConnectionString
Data Source=Reference.db;Mode=ReadOnly
```

### <a name="in-memory"></a>V paměti

Soukromá databáze v paměti.

```ConnectionString
Data Source=:memory:
```

### <a name="sharable-in-memory"></a>Sharable v paměti

Sharable, v paměti databáze označena názvem *Sharable*.

```ConnectionString
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a>Viz také

* [Připojovací řetězce v ADO.NET](../../../framework/data/adonet/connection-strings.md)
* [Databáze v paměti](in-memory-databases.md)
* [Transakce](transactions.md)
