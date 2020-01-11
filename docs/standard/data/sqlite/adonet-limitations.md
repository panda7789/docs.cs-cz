---
title: Omezení ADO.NET
ms.date: 12/13/2019
description: Popisuje některá omezení ADO.NET, se kterými se můžete setkat.
ms.openlocfilehash: 8664b73071fc859ed30080f549b05e7d6ed020f4
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901253"
---
# <a name="adonet-limitations"></a>Omezení ADO.NET

Microsoft. data. sqlite poskytuje implementace mnoha abstrakcí ADO.NET, ale existují určitá omezení.

## <a name="database-schema-information"></a>Informace o schématu databáze

Metadata k výsledkům dotazu jsou k dispozici pomocí metody <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A>.

`DbConnection.GetSchema()` není implementováno. Toto rozhraní API není správně definované, proto doporučujeme načíst metadata databáze přímo pomocí standardních rozhraní API SQLite, jako je [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) tabulka a direktiva [TABLE_INFO](https://www.sqlite.org/pragma.html#pragma_table_info) pragma.

Další informace najdete v tématu [metadata](metadata.md).

## <a name="systemtransactions"></a>System. Transactions

Microsoft. data. sqlite zatím nepodporuje System. Transactions. Místo toho použijte transakce ADO.NET. Další informace najdete v tématu [transakce](transactions.md).

Poskytněte zpětnou vazbu o nedostatečné podpoře pro System. Transactions při vydávání [#13825](https://github.com/dotnet/efcore/issues/13825).

## <a name="data-adapters"></a>Datové adaptéry

`DbDataAdapter` ještě neimplementuje Microsoft. data. sqlite. To znamená, že můžete použít jenom ADO.NET `DataSet` a `DataTable` načíst data a neaktualizovat je.

K poskytnutí zpětné vazby k implementaci `DbDataAdapter`použijte [#13838](https://github.com/dotnet/efcore/issues/13838) problému.

## <a name="output-parameters"></a>Výstupní parametry

SQLite nepodporuje výstupní parametry.

## <a name="positional-parameters"></a>Poziční parametry

Microsoft. data. sqlite podporuje jenom pojmenované [parametry](parameters.md). Poziční parametry se nepodporují.

## <a name="stored-procedures"></a>Uložené procedury

SQLite nepodporuje uložené procedury.

## <a name="isolation-levels"></a>Úrovně izolace

Úrovně izolace `Chaos` a `Snapshot` nejsou v transakcích SQLite podporovány.

## <a name="see-also"></a>Viz také:

* [Asynchronní omezení](async.md)
* [Datové typy](types.md)
* [Transakce](transactions.md)
