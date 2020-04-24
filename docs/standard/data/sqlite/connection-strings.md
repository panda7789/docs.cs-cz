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
# <a name="connection-strings"></a><span data-ttu-id="a1e10-103">Připojovací řetězce</span><span class="sxs-lookup"><span data-stu-id="a1e10-103">Connection strings</span></span>

<span data-ttu-id="a1e10-104">Připojovací řetězec se používá k určení, jak se připojit k databázi.</span><span class="sxs-lookup"><span data-stu-id="a1e10-104">A connection string is used to specify how to connect to the database.</span></span> <span data-ttu-id="a1e10-105">Připojovací řetězce v Microsoft. data. sqlite následují jako standardní [syntaxi ADO.NET](../../../framework/data/adonet/connection-strings.md) jako seznam klíčových slov a hodnot oddělených středníkem.</span><span class="sxs-lookup"><span data-stu-id="a1e10-105">Connection strings in Microsoft.Data.Sqlite follow the standard [ADO.NET syntax](../../../framework/data/adonet/connection-strings.md) as a semicolon-separated list of keywords and values.</span></span>

## <a name="keywords"></a><span data-ttu-id="a1e10-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="a1e10-106">Keywords</span></span>

<span data-ttu-id="a1e10-107">Následující klíčová slova připojovacího řetězce se dají použít s Microsoft. data. sqlite:</span><span class="sxs-lookup"><span data-stu-id="a1e10-107">The following connection string keywords can be used with Microsoft.Data.Sqlite:</span></span>

### <a name="data-source"></a><span data-ttu-id="a1e10-108">Zdroj dat</span><span class="sxs-lookup"><span data-stu-id="a1e10-108">Data source</span></span>

<span data-ttu-id="a1e10-109">Cesta k databázovému souboru.</span><span class="sxs-lookup"><span data-stu-id="a1e10-109">The path to the database file.</span></span> <span data-ttu-id="a1e10-110">*DataSource* (bez mezer) a *filename* jsou aliasy tohoto klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="a1e10-110">*DataSource* (without a space) and *Filename* are aliases of this keyword.</span></span>

<span data-ttu-id="a1e10-111">SQLite považuje cesty vzhledem k aktuálnímu pracovnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="a1e10-111">SQLite treats paths relative to the current working directory.</span></span> <span data-ttu-id="a1e10-112">Lze také zadat absolutní cesty.</span><span class="sxs-lookup"><span data-stu-id="a1e10-112">Absolute paths can also be specified.</span></span>

<span data-ttu-id="a1e10-113">Pokud je **prázdná**, SQLite vytvoří dočasnou databázi na disku, která se odstraní při zavření připojení.</span><span class="sxs-lookup"><span data-stu-id="a1e10-113">If **empty**, SQLite creates a temporary on-disk database that's deleted when the connection is closed.</span></span>

<span data-ttu-id="a1e10-114">Pokud `:memory:`se používá databáze v paměti.</span><span class="sxs-lookup"><span data-stu-id="a1e10-114">If `:memory:`, an in-memory database is used.</span></span> <span data-ttu-id="a1e10-115">Další informace najdete v tématu [databáze v paměti](in-memory-databases.md).</span><span class="sxs-lookup"><span data-stu-id="a1e10-115">For more information, see [In-Memory databases](in-memory-databases.md).</span></span>

<span data-ttu-id="a1e10-116">Cesty, které začínají `|DataDirectory|` náhradním řetězcem, jsou považovány za stejné jako relativní cesty.</span><span class="sxs-lookup"><span data-stu-id="a1e10-116">Paths that start with the `|DataDirectory|` substitution string are treated the same as relative paths.</span></span> <span data-ttu-id="a1e10-117">Je-li nastavena, cesty jsou relativní vzhledem k hodnotě vlastnosti doména aplikace DataDirectory.</span><span class="sxs-lookup"><span data-stu-id="a1e10-117">If set, paths are made relative to the DataDirectory application domain property value.</span></span>

<span data-ttu-id="a1e10-118">Toto klíčové slovo také podporuje [názvy souborů identifikátorů URI](https://www.sqlite.org/uri.html).</span><span class="sxs-lookup"><span data-stu-id="a1e10-118">This keyword also supports [URI Filenames](https://www.sqlite.org/uri.html).</span></span>

### <a name="mode"></a><span data-ttu-id="a1e10-119">Mode</span><span class="sxs-lookup"><span data-stu-id="a1e10-119">Mode</span></span>

<span data-ttu-id="a1e10-120">Režim připojení.</span><span class="sxs-lookup"><span data-stu-id="a1e10-120">The connection mode.</span></span>

| <span data-ttu-id="a1e10-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a1e10-121">Value</span></span>           | <span data-ttu-id="a1e10-122">Popis</span><span class="sxs-lookup"><span data-stu-id="a1e10-122">Description</span></span>                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="a1e10-123">ReadWriteCreate</span><span class="sxs-lookup"><span data-stu-id="a1e10-123">ReadWriteCreate</span></span> | <span data-ttu-id="a1e10-124">Otevře databázi pro čtení a zápis a vytvoří ji, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="a1e10-124">Opens the database for reading and writing, and creates it if it doesn't exist.</span></span> <span data-ttu-id="a1e10-125">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="a1e10-125">This is the default.</span></span> |
| <span data-ttu-id="a1e10-126">ReadWrite</span><span class="sxs-lookup"><span data-stu-id="a1e10-126">ReadWrite</span></span>       | <span data-ttu-id="a1e10-127">Otevře databázi pro čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="a1e10-127">Opens the database for reading and writing.</span></span>                                                        |
| <span data-ttu-id="a1e10-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="a1e10-128">ReadOnly</span></span>        | <span data-ttu-id="a1e10-129">Otevře databázi v režimu jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="a1e10-129">Opens the database in read-only mode.</span></span>                                                              |
| <span data-ttu-id="a1e10-130">Memory (Paměť)</span><span class="sxs-lookup"><span data-stu-id="a1e10-130">Memory</span></span>          | <span data-ttu-id="a1e10-131">Otevře databázi v paměti.</span><span class="sxs-lookup"><span data-stu-id="a1e10-131">Opens an in-memory database.</span></span>                                                                       |

### <a name="cache"></a><span data-ttu-id="a1e10-132">Mezipaměť</span><span class="sxs-lookup"><span data-stu-id="a1e10-132">Cache</span></span>

<span data-ttu-id="a1e10-133">Režim ukládání do mezipaměti používaný připojením.</span><span class="sxs-lookup"><span data-stu-id="a1e10-133">The caching mode used by the connection.</span></span>

| <span data-ttu-id="a1e10-134">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a1e10-134">Value</span></span>   | <span data-ttu-id="a1e10-135">Popis</span><span class="sxs-lookup"><span data-stu-id="a1e10-135">Description</span></span>                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| <span data-ttu-id="a1e10-136">Výchozí</span><span class="sxs-lookup"><span data-stu-id="a1e10-136">Default</span></span> | <span data-ttu-id="a1e10-137">Používá výchozí režim základní knihovny SQLite.</span><span class="sxs-lookup"><span data-stu-id="a1e10-137">Uses the default mode of the underlying SQLite library.</span></span> <span data-ttu-id="a1e10-138">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="a1e10-138">This is the default.</span></span>                   |
| <span data-ttu-id="a1e10-139">Private</span><span class="sxs-lookup"><span data-stu-id="a1e10-139">Private</span></span> | <span data-ttu-id="a1e10-140">Každé připojení používá soukromou mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="a1e10-140">Each connection uses a private cache.</span></span>                                                          |
| <span data-ttu-id="a1e10-141">Sdílená</span><span class="sxs-lookup"><span data-stu-id="a1e10-141">Shared</span></span>  | <span data-ttu-id="a1e10-142">Připojení sdílejí mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="a1e10-142">Connections share a cache.</span></span> <span data-ttu-id="a1e10-143">Tento režim může změnit chování při zamykání transakce a tabulky.</span><span class="sxs-lookup"><span data-stu-id="a1e10-143">This mode can change the behavior of transaction and table locking.</span></span> |

### <a name="password"></a><span data-ttu-id="a1e10-144">Heslo</span><span class="sxs-lookup"><span data-stu-id="a1e10-144">Password</span></span>

<span data-ttu-id="a1e10-145">Šifrovací klíč</span><span class="sxs-lookup"><span data-stu-id="a1e10-145">The encryption key.</span></span> <span data-ttu-id="a1e10-146">Když se zadá `PRAGMA key` , pošle se hned po otevření připojení.</span><span class="sxs-lookup"><span data-stu-id="a1e10-146">When specified, `PRAGMA key` is sent immediately after opening the connection.</span></span>

> [!WARNING]
> <span data-ttu-id="a1e10-147">Heslo nemá žádný vliv, pokud šifrování nepodporuje nativní knihovna SQLite.</span><span class="sxs-lookup"><span data-stu-id="a1e10-147">Password has no effect when encryption isn't supported by the native SQLite library.</span></span>

### <a name="foreign-keys"></a><span data-ttu-id="a1e10-148">Cizí klíče</span><span class="sxs-lookup"><span data-stu-id="a1e10-148">Foreign Keys</span></span>

<span data-ttu-id="a1e10-149">Hodnota, která označuje, jestli se mají povolit omezení cizího klíče</span><span class="sxs-lookup"><span data-stu-id="a1e10-149">A value indicating whether to enable foreign key constraints.</span></span>

| <span data-ttu-id="a1e10-150">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a1e10-150">Value</span></span>   | <span data-ttu-id="a1e10-151">Popis</span><span class="sxs-lookup"><span data-stu-id="a1e10-151">Description</span></span>
| ------- | --- |
| <span data-ttu-id="a1e10-152">True</span><span class="sxs-lookup"><span data-stu-id="a1e10-152">True</span></span>    | <span data-ttu-id="a1e10-153">Odesílá `PRAGMA foreign_keys = 1` se hned po otevření připojení.</span><span class="sxs-lookup"><span data-stu-id="a1e10-153">Sends `PRAGMA foreign_keys = 1` immediately after opening the connection.</span></span>
| <span data-ttu-id="a1e10-154">False</span><span class="sxs-lookup"><span data-stu-id="a1e10-154">False</span></span>   | <span data-ttu-id="a1e10-155">Odesílá `PRAGMA foreign_keys = 0` se hned po otevření připojení.</span><span class="sxs-lookup"><span data-stu-id="a1e10-155">Sends `PRAGMA foreign_keys = 0` immediately after opening the connection.</span></span>
| <span data-ttu-id="a1e10-156">obsahovat</span><span class="sxs-lookup"><span data-stu-id="a1e10-156">(empty)</span></span> | <span data-ttu-id="a1e10-157">Neposílá `PRAGMA foreign_keys`.</span><span class="sxs-lookup"><span data-stu-id="a1e10-157">Doesn't send `PRAGMA foreign_keys`.</span></span> <span data-ttu-id="a1e10-158">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="a1e10-158">This is the default.</span></span> |

<span data-ttu-id="a1e10-159">Není nutné povolit cizí klíče, pokud by jako v e_sqlite3 SQLITE_DEFAULT_FOREIGN_KEYS byl použit ke kompilaci nativní knihovny SQLite.</span><span class="sxs-lookup"><span data-stu-id="a1e10-159">There's no need enable foreign keys if, like in e_sqlite3, SQLITE_DEFAULT_FOREIGN_KEYS was used to compile the native SQLite library.</span></span>

### <a name="recursive-triggers"></a><span data-ttu-id="a1e10-160">Rekurzivní triggery</span><span class="sxs-lookup"><span data-stu-id="a1e10-160">Recursive triggers</span></span>

<span data-ttu-id="a1e10-161">Hodnota, která označuje, jestli se mají povolit rekurzivní triggery</span><span class="sxs-lookup"><span data-stu-id="a1e10-161">A value that indicates whether to enable recursive triggers.</span></span>

| <span data-ttu-id="a1e10-162">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a1e10-162">Value</span></span> | <span data-ttu-id="a1e10-163">Popis</span><span class="sxs-lookup"><span data-stu-id="a1e10-163">Description</span></span>                                                                 |
| ----- | --------------------------------------------------------------------------- |
| <span data-ttu-id="a1e10-164">True</span><span class="sxs-lookup"><span data-stu-id="a1e10-164">True</span></span>  | <span data-ttu-id="a1e10-165">Odesílá `PRAGMA recursive_triggers` se hned po otevření připojení.</span><span class="sxs-lookup"><span data-stu-id="a1e10-165">Sends `PRAGMA recursive_triggers` immediately after opening the connection.</span></span> |
| <span data-ttu-id="a1e10-166">False</span><span class="sxs-lookup"><span data-stu-id="a1e10-166">False</span></span> | <span data-ttu-id="a1e10-167">Neposílá `PRAGMA recursive_triggers`.</span><span class="sxs-lookup"><span data-stu-id="a1e10-167">Doesn't send `PRAGMA recursive_triggers`.</span></span> <span data-ttu-id="a1e10-168">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="a1e10-168">This is the default.</span></span>              |

## <a name="connection-string-builder"></a><span data-ttu-id="a1e10-169">Tvůrce připojovacích řetězců</span><span class="sxs-lookup"><span data-stu-id="a1e10-169">Connection string builder</span></span>

<span data-ttu-id="a1e10-170">Můžete použít <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> jako silně typované způsoby vytváření připojovacích řetězců.</span><span class="sxs-lookup"><span data-stu-id="a1e10-170">You can use <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> as a strongly typed way of creating connection strings.</span></span> <span data-ttu-id="a1e10-171">Můžete ji také použít k zabránění útokům prostřednictvím injektáže připojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="a1e10-171">It can also be used to prevent connection string injection attacks.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a><span data-ttu-id="a1e10-172">Příklady</span><span class="sxs-lookup"><span data-stu-id="a1e10-172">Examples</span></span>

### <a name="basic"></a><span data-ttu-id="a1e10-173">Základní</span><span class="sxs-lookup"><span data-stu-id="a1e10-173">Basic</span></span>

<span data-ttu-id="a1e10-174">Základní připojovací řetězec se sdílenou mezipamětí pro zlepšení souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="a1e10-174">A basic connection string with a shared cache for improved concurrency.</span></span>

```ConnectionString
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a><span data-ttu-id="a1e10-175">Šifrované</span><span class="sxs-lookup"><span data-stu-id="a1e10-175">Encrypted</span></span>

<span data-ttu-id="a1e10-176">Zašifrovaná databáze.</span><span class="sxs-lookup"><span data-stu-id="a1e10-176">An encrypted database.</span></span>

```ConnectionString
Data Source=Encrypted.db;Password=MyEncryptionKey
```

### <a name="read-only"></a><span data-ttu-id="a1e10-177">Jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a1e10-177">Read-only</span></span>

<span data-ttu-id="a1e10-178">Databáze jen pro čtení, kterou aplikace nemůže změnit.</span><span class="sxs-lookup"><span data-stu-id="a1e10-178">A read-only database that cannot be modified by the app.</span></span>

```ConnectionString
Data Source=Reference.db;Mode=ReadOnly
```

### <a name="in-memory"></a><span data-ttu-id="a1e10-179">V paměti</span><span class="sxs-lookup"><span data-stu-id="a1e10-179">In-memory</span></span>

<span data-ttu-id="a1e10-180">Soukromá databáze v paměti.</span><span class="sxs-lookup"><span data-stu-id="a1e10-180">A private, in-memory database.</span></span>

```ConnectionString
Data Source=:memory:
```

### <a name="sharable-in-memory"></a><span data-ttu-id="a1e10-181">Sdíletelné v paměti</span><span class="sxs-lookup"><span data-stu-id="a1e10-181">Sharable in-memory</span></span>

<span data-ttu-id="a1e10-182">Databáze v paměti, kterou může *sdílet název,* který je určený k jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="a1e10-182">A sharable, in-memory database identified by the name *Sharable*.</span></span>

```ConnectionString
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a><span data-ttu-id="a1e10-183">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1e10-183">See also</span></span>

* [<span data-ttu-id="a1e10-184">Připojovací řetězce v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a1e10-184">Connection Strings in ADO.NET</span></span>](../../../framework/data/adonet/connection-strings.md)
* [<span data-ttu-id="a1e10-185">Databáze v paměti</span><span class="sxs-lookup"><span data-stu-id="a1e10-185">In-Memory databases</span></span>](in-memory-databases.md)
* [<span data-ttu-id="a1e10-186">Transakce</span><span class="sxs-lookup"><span data-stu-id="a1e10-186">Transactions</span></span>](transactions.md)
