---
title: Připojovací řetězce
ms.date: 12/13/2019
description: Podporovaná klíčová slova a hodnoty připojovacích řetězců.
ms.openlocfilehash: bb54d152bac62a86c2a49192cf678a745159164e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447011"
---
# <a name="connection-strings"></a><span data-ttu-id="f8e33-103">Připojovací řetězce</span><span class="sxs-lookup"><span data-stu-id="f8e33-103">Connection strings</span></span>

<span data-ttu-id="f8e33-104">Připojovací řetězec se používá k určení, jak se připojit k databázi.</span><span class="sxs-lookup"><span data-stu-id="f8e33-104">A connection string is used to specify how to connect to the database.</span></span> <span data-ttu-id="f8e33-105">Připojovací řetězce v Microsoft. data. sqlite následují jako standardní [syntaxi ADO.NET](../../../framework/data/adonet/connection-strings.md) jako seznam klíčových slov a hodnot oddělených středníkem.</span><span class="sxs-lookup"><span data-stu-id="f8e33-105">Connection strings in Microsoft.Data.Sqlite follow the standard [ADO.NET syntax](../../../framework/data/adonet/connection-strings.md) as a semicolon-separated list of keywords and values.</span></span>

## <a name="keywords"></a><span data-ttu-id="f8e33-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="f8e33-106">Keywords</span></span>

<span data-ttu-id="f8e33-107">Následující klíčová slova připojovacího řetězce se dají použít s Microsoft. data. sqlite:</span><span class="sxs-lookup"><span data-stu-id="f8e33-107">The following connection string keywords can be used with Microsoft.Data.Sqlite:</span></span>

### <a name="data-source"></a><span data-ttu-id="f8e33-108">Zdroj dat</span><span class="sxs-lookup"><span data-stu-id="f8e33-108">Data source</span></span>

<span data-ttu-id="f8e33-109">Cesta k databázovému souboru.</span><span class="sxs-lookup"><span data-stu-id="f8e33-109">The path to the database file.</span></span> <span data-ttu-id="f8e33-110">*DataSource* (bez mezer) a *filename* jsou aliasy tohoto klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="f8e33-110">*DataSource* (without a space) and *Filename* are aliases of this keyword.</span></span>

<span data-ttu-id="f8e33-111">SQLite považuje cesty vzhledem k aktuálnímu pracovnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="f8e33-111">SQLite treats paths relative to the current working directory.</span></span> <span data-ttu-id="f8e33-112">Lze také zadat absolutní cesty.</span><span class="sxs-lookup"><span data-stu-id="f8e33-112">Absolute paths can also be specified.</span></span>

<span data-ttu-id="f8e33-113">Pokud je **prázdná**, SQLite vytvoří dočasnou databázi na disku, která se odstraní při zavření připojení.</span><span class="sxs-lookup"><span data-stu-id="f8e33-113">If **empty**, SQLite creates a temporary on-disk database that's deleted when the connection is closed.</span></span>

<span data-ttu-id="f8e33-114">V případě `:memory:`se používá databáze v paměti.</span><span class="sxs-lookup"><span data-stu-id="f8e33-114">If `:memory:`, an in-memory database is used.</span></span> <span data-ttu-id="f8e33-115">Další informace najdete v tématu [databáze v paměti](in-memory-databases.md).</span><span class="sxs-lookup"><span data-stu-id="f8e33-115">For more information, see [In-Memory databases](in-memory-databases.md).</span></span>

<span data-ttu-id="f8e33-116">Cesty, které začínají řetězcem nahrazení `|DataDirectory|`, jsou považovány za stejné jako relativní cesty.</span><span class="sxs-lookup"><span data-stu-id="f8e33-116">Paths that start with the `|DataDirectory|` substitution string are treated the same as relative paths.</span></span> <span data-ttu-id="f8e33-117">Je-li nastavena, cesty jsou relativní vzhledem k hodnotě vlastnosti doména aplikace DataDirectory.</span><span class="sxs-lookup"><span data-stu-id="f8e33-117">If set, paths are made relative to the DataDirectory application domain property value.</span></span>

<span data-ttu-id="f8e33-118">Toto klíčové slovo také podporuje [názvy souborů identifikátorů URI](https://www.sqlite.org/uri.html).</span><span class="sxs-lookup"><span data-stu-id="f8e33-118">This keyword also supports [URI Filenames](https://www.sqlite.org/uri.html).</span></span>

### <a name="mode"></a><span data-ttu-id="f8e33-119">Režim</span><span class="sxs-lookup"><span data-stu-id="f8e33-119">Mode</span></span>

<span data-ttu-id="f8e33-120">Režim připojení.</span><span class="sxs-lookup"><span data-stu-id="f8e33-120">The connection mode.</span></span>

| <span data-ttu-id="f8e33-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f8e33-121">Value</span></span>           | <span data-ttu-id="f8e33-122">Popis</span><span class="sxs-lookup"><span data-stu-id="f8e33-122">Description</span></span>                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="f8e33-123">ReadWriteCreate</span><span class="sxs-lookup"><span data-stu-id="f8e33-123">ReadWriteCreate</span></span> | <span data-ttu-id="f8e33-124">Otevře databázi pro čtení a zápis a vytvoří ji, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="f8e33-124">Opens the database for reading and writing, and creates it if it doesn't exist.</span></span> <span data-ttu-id="f8e33-125">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="f8e33-125">This is the default.</span></span> |
| <span data-ttu-id="f8e33-126">ReadWrite</span><span class="sxs-lookup"><span data-stu-id="f8e33-126">ReadWrite</span></span>       | <span data-ttu-id="f8e33-127">Otevře databázi pro čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="f8e33-127">Opens the database for reading and writing.</span></span>                                                        |
| <span data-ttu-id="f8e33-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="f8e33-128">ReadOnly</span></span>        | <span data-ttu-id="f8e33-129">Otevře databázi v režimu jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="f8e33-129">Opens the database in read-only mode.</span></span>                                                              |
| <span data-ttu-id="f8e33-130">Paměť</span><span class="sxs-lookup"><span data-stu-id="f8e33-130">Memory</span></span>          | <span data-ttu-id="f8e33-131">Otevře databázi v paměti.</span><span class="sxs-lookup"><span data-stu-id="f8e33-131">Opens an in-memory database.</span></span>                                                                       |

### <a name="cache"></a><span data-ttu-id="f8e33-132">Mezipaměť</span><span class="sxs-lookup"><span data-stu-id="f8e33-132">Cache</span></span>

<span data-ttu-id="f8e33-133">Režim ukládání do mezipaměti používaný připojením.</span><span class="sxs-lookup"><span data-stu-id="f8e33-133">The caching mode used by the connection.</span></span>

| <span data-ttu-id="f8e33-134">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f8e33-134">Value</span></span>   | <span data-ttu-id="f8e33-135">Popis</span><span class="sxs-lookup"><span data-stu-id="f8e33-135">Description</span></span>                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| <span data-ttu-id="f8e33-136">Výchozí</span><span class="sxs-lookup"><span data-stu-id="f8e33-136">Default</span></span> | <span data-ttu-id="f8e33-137">Používá výchozí režim základní knihovny SQLite.</span><span class="sxs-lookup"><span data-stu-id="f8e33-137">Uses the default mode of the underlying SQLite library.</span></span> <span data-ttu-id="f8e33-138">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="f8e33-138">This is the default.</span></span>                   |
| <span data-ttu-id="f8e33-139">Soukromé</span><span class="sxs-lookup"><span data-stu-id="f8e33-139">Private</span></span> | <span data-ttu-id="f8e33-140">Každé připojení používá soukromou mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="f8e33-140">Each connection uses a private cache.</span></span>                                                          |
| <span data-ttu-id="f8e33-141">Sdílené</span><span class="sxs-lookup"><span data-stu-id="f8e33-141">Shared</span></span>  | <span data-ttu-id="f8e33-142">Připojení sdílejí mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="f8e33-142">Connections share a cache.</span></span> <span data-ttu-id="f8e33-143">Tento režim může změnit chování při zamykání transakce a tabulky.</span><span class="sxs-lookup"><span data-stu-id="f8e33-143">This mode can change the behavior of transaction and table locking.</span></span> |

### <a name="password"></a><span data-ttu-id="f8e33-144">Heslo</span><span class="sxs-lookup"><span data-stu-id="f8e33-144">Password</span></span>

<span data-ttu-id="f8e33-145">Šifrovací klíč</span><span class="sxs-lookup"><span data-stu-id="f8e33-145">The encryption key.</span></span> <span data-ttu-id="f8e33-146">Po zadání se `PRAGMA key` odešle hned po otevření připojení.</span><span class="sxs-lookup"><span data-stu-id="f8e33-146">When specified, `PRAGMA key` is sent immediately after opening the connection.</span></span>

> [!WARNING]
> <span data-ttu-id="f8e33-147">Heslo nemá žádný vliv, pokud šifrování nepodporuje nativní knihovna SQLite.</span><span class="sxs-lookup"><span data-stu-id="f8e33-147">Password has no effect when encryption isn't supported by the native SQLite library.</span></span>

### <a name="foreign-keys"></a><span data-ttu-id="f8e33-148">Cizí klíče</span><span class="sxs-lookup"><span data-stu-id="f8e33-148">Foreign Keys</span></span>

<span data-ttu-id="f8e33-149">Hodnota, která označuje, jestli se mají povolit omezení cizího klíče</span><span class="sxs-lookup"><span data-stu-id="f8e33-149">A value indicating whether to enable foreign key constraints.</span></span>

| <span data-ttu-id="f8e33-150">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f8e33-150">Value</span></span>   | <span data-ttu-id="f8e33-151">Popis</span><span class="sxs-lookup"><span data-stu-id="f8e33-151">Description</span></span>
| ------- | --- |
| <span data-ttu-id="f8e33-152">Pravda</span><span class="sxs-lookup"><span data-stu-id="f8e33-152">True</span></span>    | <span data-ttu-id="f8e33-153">Odesílá `PRAGMA foreign_keys = 1` hned po otevření připojení.</span><span class="sxs-lookup"><span data-stu-id="f8e33-153">Sends `PRAGMA foreign_keys = 1` immediately after opening the connection.</span></span>
| <span data-ttu-id="f8e33-154">Nepravda</span><span class="sxs-lookup"><span data-stu-id="f8e33-154">False</span></span>   | <span data-ttu-id="f8e33-155">Odesílá `PRAGMA foreign_keys = 0` hned po otevření připojení.</span><span class="sxs-lookup"><span data-stu-id="f8e33-155">Sends `PRAGMA foreign_keys = 0` immediately after opening the connection.</span></span>
| <span data-ttu-id="f8e33-156">obsahovat</span><span class="sxs-lookup"><span data-stu-id="f8e33-156">(empty)</span></span> | <span data-ttu-id="f8e33-157">Neodesílá `PRAGMA foreign_keys`.</span><span class="sxs-lookup"><span data-stu-id="f8e33-157">Doesn't send `PRAGMA foreign_keys`.</span></span> <span data-ttu-id="f8e33-158">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="f8e33-158">This is the default.</span></span> |

<span data-ttu-id="f8e33-159">Není nutné povolit cizí klíče, pokud by jako v e_sqlite3 SQLITE_DEFAULT_FOREIGN_KEYS byl použit ke kompilaci nativní knihovny SQLite.</span><span class="sxs-lookup"><span data-stu-id="f8e33-159">There's no need enable foreign keys if, like in e_sqlite3, SQLITE_DEFAULT_FOREIGN_KEYS was used to compile the native SQLite library.</span></span>

### <a name="recursive-triggers"></a><span data-ttu-id="f8e33-160">Rekurzivní triggery</span><span class="sxs-lookup"><span data-stu-id="f8e33-160">Recursive triggers</span></span>

<span data-ttu-id="f8e33-161">Hodnota, která označuje, jestli se mají povolit rekurzivní triggery</span><span class="sxs-lookup"><span data-stu-id="f8e33-161">A value that indicates whether to enable recursive triggers.</span></span>

| <span data-ttu-id="f8e33-162">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f8e33-162">Value</span></span> | <span data-ttu-id="f8e33-163">Popis</span><span class="sxs-lookup"><span data-stu-id="f8e33-163">Description</span></span>                                                                 |
| ----- | --------------------------------------------------------------------------- |
| <span data-ttu-id="f8e33-164">Pravda</span><span class="sxs-lookup"><span data-stu-id="f8e33-164">True</span></span>  | <span data-ttu-id="f8e33-165">Odesílá `PRAGMA recursive_triggers` hned po otevření připojení.</span><span class="sxs-lookup"><span data-stu-id="f8e33-165">Sends `PRAGMA recursive_triggers` immediately after opening the connection.</span></span> |
| <span data-ttu-id="f8e33-166">Nepravda</span><span class="sxs-lookup"><span data-stu-id="f8e33-166">False</span></span> | <span data-ttu-id="f8e33-167">Neodesílá `PRAGMA recursive_triggers`.</span><span class="sxs-lookup"><span data-stu-id="f8e33-167">Doesn't send `PRAGMA recursive_triggers`.</span></span> <span data-ttu-id="f8e33-168">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="f8e33-168">This is the default.</span></span>              |

## <a name="connection-string-builder"></a><span data-ttu-id="f8e33-169">Tvůrce připojovacích řetězců</span><span class="sxs-lookup"><span data-stu-id="f8e33-169">Connection string builder</span></span>

<span data-ttu-id="f8e33-170">Můžete použít <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> jako silně typovaného způsobu vytváření připojovacích řetězců.</span><span class="sxs-lookup"><span data-stu-id="f8e33-170">You can use <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> as a strongly typed way of creating connection strings.</span></span> <span data-ttu-id="f8e33-171">Můžete ji také použít k zabránění útokům prostřednictvím injektáže připojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="f8e33-171">It can also be used to prevent connection string injection attacks.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a><span data-ttu-id="f8e33-172">Příklady</span><span class="sxs-lookup"><span data-stu-id="f8e33-172">Examples</span></span>

### <a name="basic"></a><span data-ttu-id="f8e33-173">Základní</span><span class="sxs-lookup"><span data-stu-id="f8e33-173">Basic</span></span>

<span data-ttu-id="f8e33-174">Základní připojovací řetězec se sdílenou mezipamětí pro zlepšení souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="f8e33-174">A basic connection string with a shared cache for improved concurrency.</span></span>

```ConnectionString
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a><span data-ttu-id="f8e33-175">Šifrované</span><span class="sxs-lookup"><span data-stu-id="f8e33-175">Encrypted</span></span>

<span data-ttu-id="f8e33-176">Zašifrovaná databáze.</span><span class="sxs-lookup"><span data-stu-id="f8e33-176">An encrypted database.</span></span>

```ConnectionString
Data Source=Encrypted.db;Password=MyEncryptionKey
```

### <a name="read-only"></a><span data-ttu-id="f8e33-177">Jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f8e33-177">Read-only</span></span>

<span data-ttu-id="f8e33-178">Databáze jen pro čtení, kterou aplikace nemůže změnit.</span><span class="sxs-lookup"><span data-stu-id="f8e33-178">A read-only database that cannot be modified by the app.</span></span>

```ConnectionString
Data Source=Reference.db;Mode=ReadOnly
```

### <a name="in-memory"></a><span data-ttu-id="f8e33-179">V paměti</span><span class="sxs-lookup"><span data-stu-id="f8e33-179">In-memory</span></span>

<span data-ttu-id="f8e33-180">Soukromá databáze v paměti.</span><span class="sxs-lookup"><span data-stu-id="f8e33-180">A private, in-memory database.</span></span>

```ConnectionString
Data Source=:memory:
```

### <a name="sharable-in-memory"></a><span data-ttu-id="f8e33-181">Sdíletelné v paměti</span><span class="sxs-lookup"><span data-stu-id="f8e33-181">Sharable in-memory</span></span>

<span data-ttu-id="f8e33-182">Databáze v paměti, kterou může *sdílet název,* který je určený k jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="f8e33-182">A sharable, in-memory database identified by the name *Sharable*.</span></span>

```ConnectionString
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a><span data-ttu-id="f8e33-183">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8e33-183">See also</span></span>

* [<span data-ttu-id="f8e33-184">Připojovací řetězce v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f8e33-184">Connection Strings in ADO.NET</span></span>](../../../framework/data/adonet/connection-strings.md)
* [<span data-ttu-id="f8e33-185">Databáze v paměti</span><span class="sxs-lookup"><span data-stu-id="f8e33-185">In-Memory databases</span></span>](in-memory-databases.md)
* [<span data-ttu-id="f8e33-186">Transakce</span><span class="sxs-lookup"><span data-stu-id="f8e33-186">Transactions</span></span>](transactions.md)
