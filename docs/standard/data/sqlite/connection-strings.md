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

Připojovací řetězec se používá k určení, jak se připojit k databázi. Připojovací řetězce v Microsoft. data. sqlite následují jako standardní [syntaxi ADO.NET](../../../framework/data/adonet/connection-strings.md) jako seznam klíčových slov a hodnot oddělených středníkem.

## <a name="keywords"></a>Klíčová slova

Následující klíčová slova připojovacího řetězce se dají použít s Microsoft. data. sqlite:

### <a name="data-source"></a>Zdroj dat

Cesta k databázovému souboru. *DataSource* (bez mezer) a *filename* jsou aliasy tohoto klíčového slova.

SQLite považuje cesty vzhledem k aktuálnímu pracovnímu adresáři. Lze také zadat absolutní cesty.

Pokud je **prázdná**, SQLite vytvoří dočasnou databázi na disku, která se odstraní při zavření připojení.

Pokud `:memory:`se používá databáze v paměti. Další informace najdete v tématu [databáze v paměti](in-memory-databases.md).

Cesty, které začínají `|DataDirectory|` náhradním řetězcem, jsou považovány za stejné jako relativní cesty. Je-li nastavena, cesty jsou relativní vzhledem k hodnotě vlastnosti doména aplikace DataDirectory.

Toto klíčové slovo také podporuje [názvy souborů identifikátorů URI](https://www.sqlite.org/uri.html).

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
| Private | Každé připojení používá soukromou mezipaměť.                                                          |
| Sdílená  | Připojení sdílejí mezipaměť. Tento režim může změnit chování při zamykání transakce a tabulky. |

### <a name="password"></a>Heslo

Šifrovací klíč Když se zadá `PRAGMA key` , pošle se hned po otevření připojení.

> [!WARNING]
> Heslo nemá žádný vliv, pokud šifrování nepodporuje nativní knihovna SQLite.

### <a name="foreign-keys"></a>Cizí klíče

Hodnota, která označuje, jestli se mají povolit omezení cizího klíče

| Hodnota   | Popis
| ------- | --- |
| True    | Odesílá `PRAGMA foreign_keys = 1` se hned po otevření připojení.
| False   | Odesílá `PRAGMA foreign_keys = 0` se hned po otevření připojení.
| obsahovat | Neposílá `PRAGMA foreign_keys`. Toto nastavení je výchozí. |

Není nutné povolit cizí klíče, pokud by jako v e_sqlite3 SQLITE_DEFAULT_FOREIGN_KEYS byl použit ke kompilaci nativní knihovny SQLite.

### <a name="recursive-triggers"></a>Rekurzivní triggery

Hodnota, která označuje, jestli se mají povolit rekurzivní triggery

| Hodnota | Popis                                                                 |
| ----- | --------------------------------------------------------------------------- |
| True  | Odesílá `PRAGMA recursive_triggers` se hned po otevření připojení. |
| False | Neposílá `PRAGMA recursive_triggers`. Toto nastavení je výchozí.              |

## <a name="connection-string-builder"></a>Tvůrce připojovacích řetězců

Můžete použít <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> jako silně typované způsoby vytváření připojovacích řetězců. Můžete ji také použít k zabránění útokům prostřednictvím injektáže připojovacího řetězce.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a>Příklady

### <a name="basic"></a>Základní

Základní připojovací řetězec se sdílenou mezipamětí pro zlepšení souběžnosti.

```ConnectionString
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a>Šifrované

Zašifrovaná databáze.

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

### <a name="sharable-in-memory"></a>Sdíletelné v paměti

Databáze v paměti, kterou může *sdílet název,* který je určený k jeho vytvoření.

```ConnectionString
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a>Viz také

* [Připojovací řetězce v ADO.NET](../../../framework/data/adonet/connection-strings.md)
* [Databáze v paměti](in-memory-databases.md)
* [Transakce](transactions.md)
