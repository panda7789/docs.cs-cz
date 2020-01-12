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
# <a name="adonet-limitations"></a><span data-ttu-id="3c276-103">Omezení ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3c276-103">ADO.NET limitations</span></span>

<span data-ttu-id="3c276-104">Microsoft. data. sqlite poskytuje implementace mnoha abstrakcí ADO.NET, ale existují určitá omezení.</span><span class="sxs-lookup"><span data-stu-id="3c276-104">Microsoft.Data.Sqlite provides implementations of many of the ADO.NET abstractions, but there are some limitations.</span></span>

## <a name="database-schema-information"></a><span data-ttu-id="3c276-105">Informace o schématu databáze</span><span class="sxs-lookup"><span data-stu-id="3c276-105">Database schema information</span></span>

<span data-ttu-id="3c276-106">Metadata k výsledkům dotazu jsou k dispozici pomocí metody <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A>.</span><span class="sxs-lookup"><span data-stu-id="3c276-106">Metadata about query results is available using the <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> method.</span></span>

<span data-ttu-id="3c276-107">`DbConnection.GetSchema()` není implementováno.</span><span class="sxs-lookup"><span data-stu-id="3c276-107">`DbConnection.GetSchema()` isn't implemented.</span></span> <span data-ttu-id="3c276-108">Toto rozhraní API není správně definované, proto doporučujeme načíst metadata databáze přímo pomocí standardních rozhraní API SQLite, jako je [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) tabulka a direktiva [TABLE_INFO](https://www.sqlite.org/pragma.html#pragma_table_info) pragma.</span><span class="sxs-lookup"><span data-stu-id="3c276-108">This API isn't well-defined, so we recommend retrieving database metadata directly using standard SQLite APIs like the [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) table and the [table_info](https://www.sqlite.org/pragma.html#pragma_table_info) PRAGMA.</span></span>

<span data-ttu-id="3c276-109">Další informace najdete v tématu [metadata](metadata.md).</span><span class="sxs-lookup"><span data-stu-id="3c276-109">For more information, see [Metadata](metadata.md).</span></span>

## <a name="systemtransactions"></a><span data-ttu-id="3c276-110">System. Transactions</span><span class="sxs-lookup"><span data-stu-id="3c276-110">System.Transactions</span></span>

<span data-ttu-id="3c276-111">Microsoft. data. sqlite zatím nepodporuje System. Transactions.</span><span class="sxs-lookup"><span data-stu-id="3c276-111">Microsoft.Data.Sqlite doesn't yet support System.Transactions.</span></span> <span data-ttu-id="3c276-112">Místo toho použijte transakce ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="3c276-112">Use ADO.NET transactions instead.</span></span> <span data-ttu-id="3c276-113">Další informace najdete v tématu [transakce](transactions.md).</span><span class="sxs-lookup"><span data-stu-id="3c276-113">For more information, see [Transactions](transactions.md).</span></span>

<span data-ttu-id="3c276-114">Poskytněte zpětnou vazbu o nedostatečné podpoře pro System. Transactions při vydávání [#13825](https://github.com/dotnet/efcore/issues/13825).</span><span class="sxs-lookup"><span data-stu-id="3c276-114">Provide feedback about the lack of support for System.Transactions on issue [#13825](https://github.com/dotnet/efcore/issues/13825).</span></span>

## <a name="data-adapters"></a><span data-ttu-id="3c276-115">Datové adaptéry</span><span class="sxs-lookup"><span data-stu-id="3c276-115">Data adapters</span></span>

<span data-ttu-id="3c276-116">`DbDataAdapter` ještě neimplementuje Microsoft. data. sqlite.</span><span class="sxs-lookup"><span data-stu-id="3c276-116">`DbDataAdapter` isn't yet implemented by Microsoft.Data.Sqlite.</span></span> <span data-ttu-id="3c276-117">To znamená, že můžete použít jenom ADO.NET `DataSet` a `DataTable` načíst data a neaktualizovat je.</span><span class="sxs-lookup"><span data-stu-id="3c276-117">This means you can only use ADO.NET `DataSet` and `DataTable` to load data and not update it.</span></span>

<span data-ttu-id="3c276-118">K poskytnutí zpětné vazby k implementaci `DbDataAdapter`použijte [#13838](https://github.com/dotnet/efcore/issues/13838) problému.</span><span class="sxs-lookup"><span data-stu-id="3c276-118">Use issue [#13838](https://github.com/dotnet/efcore/issues/13838) to provide feedback about implementing `DbDataAdapter`.</span></span>

## <a name="output-parameters"></a><span data-ttu-id="3c276-119">Výstupní parametry</span><span class="sxs-lookup"><span data-stu-id="3c276-119">Output parameters</span></span>

<span data-ttu-id="3c276-120">SQLite nepodporuje výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="3c276-120">SQLite doesn't support output parameters.</span></span>

## <a name="positional-parameters"></a><span data-ttu-id="3c276-121">Poziční parametry</span><span class="sxs-lookup"><span data-stu-id="3c276-121">Positional parameters</span></span>

<span data-ttu-id="3c276-122">Microsoft. data. sqlite podporuje jenom pojmenované [parametry](parameters.md).</span><span class="sxs-lookup"><span data-stu-id="3c276-122">Microsoft.Data.Sqlite only supports named [parameters](parameters.md).</span></span> <span data-ttu-id="3c276-123">Poziční parametry se nepodporují.</span><span class="sxs-lookup"><span data-stu-id="3c276-123">Positional parameters aren't supported.</span></span>

## <a name="stored-procedures"></a><span data-ttu-id="3c276-124">Uložené procedury</span><span class="sxs-lookup"><span data-stu-id="3c276-124">Stored procedures</span></span>

<span data-ttu-id="3c276-125">SQLite nepodporuje uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="3c276-125">SQLite doesn't support stored procedures.</span></span>

## <a name="isolation-levels"></a><span data-ttu-id="3c276-126">Úrovně izolace</span><span class="sxs-lookup"><span data-stu-id="3c276-126">Isolation levels</span></span>

<span data-ttu-id="3c276-127">Úrovně izolace `Chaos` a `Snapshot` nejsou v transakcích SQLite podporovány.</span><span class="sxs-lookup"><span data-stu-id="3c276-127">The `Chaos` and `Snapshot` isolation levels aren't supported in SQLite transactions.</span></span>

## <a name="see-also"></a><span data-ttu-id="3c276-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3c276-128">See also</span></span>

* [<span data-ttu-id="3c276-129">Asynchronní omezení</span><span class="sxs-lookup"><span data-stu-id="3c276-129">Async limitations</span></span>](async.md)
* [<span data-ttu-id="3c276-130">Datové typy</span><span class="sxs-lookup"><span data-stu-id="3c276-130">Data types</span></span>](types.md)
* [<span data-ttu-id="3c276-131">Transakce</span><span class="sxs-lookup"><span data-stu-id="3c276-131">Transactions</span></span>](transactions.md)
