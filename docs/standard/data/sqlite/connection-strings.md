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
# <a name="connection-strings"></a><span data-ttu-id="91221-103">Připojovací řetězce</span><span class="sxs-lookup"><span data-stu-id="91221-103">Connection strings</span></span>

<span data-ttu-id="91221-104">Připojovací řetězec se používá k určení způsobu připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="91221-104">A connection string is used to specify how to connect to the database.</span></span> <span data-ttu-id="91221-105">Připojovací řetězce v Microsoft.Data.Sqlite postupujte podle [standardní ADO.NET syntaxe](../../../framework/data/adonet/connection-strings.md) jako středník-oddělený seznam klíčových slov a hodnot.</span><span class="sxs-lookup"><span data-stu-id="91221-105">Connection strings in Microsoft.Data.Sqlite follow the standard [ADO.NET syntax](../../../framework/data/adonet/connection-strings.md) as a semicolon-separated list of keywords and values.</span></span>

## <a name="keywords"></a><span data-ttu-id="91221-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="91221-106">Keywords</span></span>

<span data-ttu-id="91221-107">Následující klíčová slova připojovacího řetězce lze použít s Microsoft.Data.Sqlite:</span><span class="sxs-lookup"><span data-stu-id="91221-107">The following connection string keywords can be used with Microsoft.Data.Sqlite:</span></span>

### <a name="data-source"></a><span data-ttu-id="91221-108">Zdroj dat</span><span class="sxs-lookup"><span data-stu-id="91221-108">Data source</span></span>

<span data-ttu-id="91221-109">Cesta k databázovému souboru.</span><span class="sxs-lookup"><span data-stu-id="91221-109">The path to the database file.</span></span> <span data-ttu-id="91221-110">*DataSource* (bez mezery) a *Název souboru* jsou aliasy tohoto klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="91221-110">*DataSource* (without a space) and *Filename* are aliases of this keyword.</span></span>

<span data-ttu-id="91221-111">SQLite zpracuje cesty vzhledem k aktuálnímu pracovnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="91221-111">SQLite treats paths relative to the current working directory.</span></span> <span data-ttu-id="91221-112">Lze také zadat absolutní cesty.</span><span class="sxs-lookup"><span data-stu-id="91221-112">Absolute paths can also be specified.</span></span>

<span data-ttu-id="91221-113">Pokud **prázdné**, SQLite vytvoří dočasnou databázi na disku, která je odstraněna při zavření připojení.</span><span class="sxs-lookup"><span data-stu-id="91221-113">If **empty**, SQLite creates a temporary on-disk database that's deleted when the connection is closed.</span></span>

<span data-ttu-id="91221-114">Pokud `:memory:`se používá databáze v paměti.</span><span class="sxs-lookup"><span data-stu-id="91221-114">If `:memory:`, an in-memory database is used.</span></span> <span data-ttu-id="91221-115">Další informace naleznete [v tématu In-Memory databases](in-memory-databases.md).</span><span class="sxs-lookup"><span data-stu-id="91221-115">For more information, see [In-Memory databases](in-memory-databases.md).</span></span>

<span data-ttu-id="91221-116">Cesty začínající substitučním řetězcem `|DataDirectory|` jsou považovány za relativní cesty.</span><span class="sxs-lookup"><span data-stu-id="91221-116">Paths that start with the `|DataDirectory|` substitution string are treated the same as relative paths.</span></span> <span data-ttu-id="91221-117">Pokud je nastavena, cesty jsou vyrobeny vzhledem k hodnotě vlastnosti domény aplikace DataDirectory.</span><span class="sxs-lookup"><span data-stu-id="91221-117">If set, paths are made relative to the DataDirectory application domain property value.</span></span>

<span data-ttu-id="91221-118">Toto klíčové slovo také podporuje [názvy souborů URI](https://www.sqlite.org/uri.html).</span><span class="sxs-lookup"><span data-stu-id="91221-118">This keyword also supports [URI Filenames](https://www.sqlite.org/uri.html).</span></span>

### <a name="mode"></a><span data-ttu-id="91221-119">Mode</span><span class="sxs-lookup"><span data-stu-id="91221-119">Mode</span></span>

<span data-ttu-id="91221-120">Režim připojení.</span><span class="sxs-lookup"><span data-stu-id="91221-120">The connection mode.</span></span>

| <span data-ttu-id="91221-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="91221-121">Value</span></span>           | <span data-ttu-id="91221-122">Popis</span><span class="sxs-lookup"><span data-stu-id="91221-122">Description</span></span>                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="91221-123">ReadWriteCreate</span><span class="sxs-lookup"><span data-stu-id="91221-123">ReadWriteCreate</span></span> | <span data-ttu-id="91221-124">Otevře databázi pro čtení a zápis a vytvoří ji, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="91221-124">Opens the database for reading and writing, and creates it if it doesn't exist.</span></span> <span data-ttu-id="91221-125">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="91221-125">This is the default.</span></span> |
| <span data-ttu-id="91221-126">ReadWrite</span><span class="sxs-lookup"><span data-stu-id="91221-126">ReadWrite</span></span>       | <span data-ttu-id="91221-127">Otevře databázi pro čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="91221-127">Opens the database for reading and writing.</span></span>                                                        |
| <span data-ttu-id="91221-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="91221-128">ReadOnly</span></span>        | <span data-ttu-id="91221-129">Otevře databázi v režimu jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="91221-129">Opens the database in read-only mode.</span></span>                                                              |
| <span data-ttu-id="91221-130">Memory (Paměť)</span><span class="sxs-lookup"><span data-stu-id="91221-130">Memory</span></span>          | <span data-ttu-id="91221-131">Otevře databázi v paměti.</span><span class="sxs-lookup"><span data-stu-id="91221-131">Opens an in-memory database.</span></span>                                                                       |

### <a name="cache"></a><span data-ttu-id="91221-132">Mezipaměť</span><span class="sxs-lookup"><span data-stu-id="91221-132">Cache</span></span>

<span data-ttu-id="91221-133">Režim ukládání do mezipaměti používaný připojením.</span><span class="sxs-lookup"><span data-stu-id="91221-133">The caching mode used by the connection.</span></span>

| <span data-ttu-id="91221-134">Hodnota</span><span class="sxs-lookup"><span data-stu-id="91221-134">Value</span></span>   | <span data-ttu-id="91221-135">Popis</span><span class="sxs-lookup"><span data-stu-id="91221-135">Description</span></span>                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| <span data-ttu-id="91221-136">Výchozí</span><span class="sxs-lookup"><span data-stu-id="91221-136">Default</span></span> | <span data-ttu-id="91221-137">Používá výchozí režim základní knihovny SQLite.</span><span class="sxs-lookup"><span data-stu-id="91221-137">Uses the default mode of the underlying SQLite library.</span></span> <span data-ttu-id="91221-138">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="91221-138">This is the default.</span></span>                   |
| <span data-ttu-id="91221-139">Private</span><span class="sxs-lookup"><span data-stu-id="91221-139">Private</span></span> | <span data-ttu-id="91221-140">Každé připojení používá privátní mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="91221-140">Each connection uses a private cache.</span></span>                                                          |
| <span data-ttu-id="91221-141">Sdílená</span><span class="sxs-lookup"><span data-stu-id="91221-141">Shared</span></span>  | <span data-ttu-id="91221-142">Připojení sdílejí mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="91221-142">Connections share a cache.</span></span> <span data-ttu-id="91221-143">Tento režim může změnit chování transakce a zamykání tabulky.</span><span class="sxs-lookup"><span data-stu-id="91221-143">This mode can change the behavior of transaction and table locking.</span></span> |

### <a name="password"></a><span data-ttu-id="91221-144">Heslo</span><span class="sxs-lookup"><span data-stu-id="91221-144">Password</span></span>

<span data-ttu-id="91221-145">Šifrovací klíč.</span><span class="sxs-lookup"><span data-stu-id="91221-145">The encryption key.</span></span> <span data-ttu-id="91221-146">Pokud je `PRAGMA key` zadán, je odeslán ihned po otevření připojení.</span><span class="sxs-lookup"><span data-stu-id="91221-146">When specified, `PRAGMA key` is sent immediately after opening the connection.</span></span>

> [!WARNING]
> <span data-ttu-id="91221-147">Heslo nemá žádný vliv, pokud nativní knihovna SQLite nepodporuje šifrování.</span><span class="sxs-lookup"><span data-stu-id="91221-147">Password has no effect when encryption isn't supported by the native SQLite library.</span></span>

### <a name="foreign-keys"></a><span data-ttu-id="91221-148">Cizí klíče</span><span class="sxs-lookup"><span data-stu-id="91221-148">Foreign Keys</span></span>

<span data-ttu-id="91221-149">Hodnota označující, zda chcete povolit omezení cizího klíče.</span><span class="sxs-lookup"><span data-stu-id="91221-149">A value indicating whether to enable foreign key constraints.</span></span>

| <span data-ttu-id="91221-150">Hodnota</span><span class="sxs-lookup"><span data-stu-id="91221-150">Value</span></span>   | <span data-ttu-id="91221-151">Popis</span><span class="sxs-lookup"><span data-stu-id="91221-151">Description</span></span>
| ------- | --- |
| <span data-ttu-id="91221-152">True</span><span class="sxs-lookup"><span data-stu-id="91221-152">True</span></span>    | <span data-ttu-id="91221-153">Odešle `PRAGMA foreign_keys = 1` ihned po otevření připojení.</span><span class="sxs-lookup"><span data-stu-id="91221-153">Sends `PRAGMA foreign_keys = 1` immediately after opening the connection.</span></span>
| <span data-ttu-id="91221-154">False</span><span class="sxs-lookup"><span data-stu-id="91221-154">False</span></span>   | <span data-ttu-id="91221-155">Odešle `PRAGMA foreign_keys = 0` ihned po otevření připojení.</span><span class="sxs-lookup"><span data-stu-id="91221-155">Sends `PRAGMA foreign_keys = 0` immediately after opening the connection.</span></span>
| <span data-ttu-id="91221-156">(prázdné)</span><span class="sxs-lookup"><span data-stu-id="91221-156">(empty)</span></span> | <span data-ttu-id="91221-157">Neposílá `PRAGMA foreign_keys`.</span><span class="sxs-lookup"><span data-stu-id="91221-157">Doesn't send `PRAGMA foreign_keys`.</span></span> <span data-ttu-id="91221-158">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="91221-158">This is the default.</span></span> |

<span data-ttu-id="91221-159">Není třeba povolit cizí klíče, pokud, stejně jako v e_sqlite3, SQLITE_DEFAULT_FOREIGN_KEYS byl použit ke kompilaci nativní knihovny SQLite.</span><span class="sxs-lookup"><span data-stu-id="91221-159">There's no need enable foreign keys if, like in e_sqlite3, SQLITE_DEFAULT_FOREIGN_KEYS was used to compile the native SQLite library.</span></span>

### <a name="recursive-triggers"></a><span data-ttu-id="91221-160">Rekurzivní aktivační události</span><span class="sxs-lookup"><span data-stu-id="91221-160">Recursive triggers</span></span>

<span data-ttu-id="91221-161">Hodnota, která označuje, zda chcete povolit rekurzivní aktivační události.</span><span class="sxs-lookup"><span data-stu-id="91221-161">A value that indicates whether to enable recursive triggers.</span></span>

| <span data-ttu-id="91221-162">Hodnota</span><span class="sxs-lookup"><span data-stu-id="91221-162">Value</span></span> | <span data-ttu-id="91221-163">Popis</span><span class="sxs-lookup"><span data-stu-id="91221-163">Description</span></span>                                                                 |
| ----- | --------------------------------------------------------------------------- |
| <span data-ttu-id="91221-164">True</span><span class="sxs-lookup"><span data-stu-id="91221-164">True</span></span>  | <span data-ttu-id="91221-165">Odešle `PRAGMA recursive_triggers` ihned po otevření připojení.</span><span class="sxs-lookup"><span data-stu-id="91221-165">Sends `PRAGMA recursive_triggers` immediately after opening the connection.</span></span> |
| <span data-ttu-id="91221-166">False</span><span class="sxs-lookup"><span data-stu-id="91221-166">False</span></span> | <span data-ttu-id="91221-167">Neposílá `PRAGMA recursive_triggers`.</span><span class="sxs-lookup"><span data-stu-id="91221-167">Doesn't send `PRAGMA recursive_triggers`.</span></span> <span data-ttu-id="91221-168">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="91221-168">This is the default.</span></span>              |

## <a name="connection-string-builder"></a><span data-ttu-id="91221-169">Tvůrce připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="91221-169">Connection string builder</span></span>

<span data-ttu-id="91221-170">Můžete použít <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> jako silně zadaný způsob vytváření připojovacích řetězců.</span><span class="sxs-lookup"><span data-stu-id="91221-170">You can use <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> as a strongly typed way of creating connection strings.</span></span> <span data-ttu-id="91221-171">Může být také použit k prevenci útoků injektáže spojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="91221-171">It can also be used to prevent connection string injection attacks.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a><span data-ttu-id="91221-172">Příklady</span><span class="sxs-lookup"><span data-stu-id="91221-172">Examples</span></span>

### <a name="basic"></a><span data-ttu-id="91221-173">Basic</span><span class="sxs-lookup"><span data-stu-id="91221-173">Basic</span></span>

<span data-ttu-id="91221-174">Základní připojovací řetězec se sdílenou mezipamětí pro lepší souběžnost.</span><span class="sxs-lookup"><span data-stu-id="91221-174">A basic connection string with a shared cache for improved concurrency.</span></span>

```ConnectionString
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a><span data-ttu-id="91221-175">Šifrované</span><span class="sxs-lookup"><span data-stu-id="91221-175">Encrypted</span></span>

<span data-ttu-id="91221-176">Šifrovaná databáze.</span><span class="sxs-lookup"><span data-stu-id="91221-176">An encrypted database.</span></span>

```ConnectionString
Data Source=Encrypted.db;Password=MyEncryptionKey
```

### <a name="read-only"></a><span data-ttu-id="91221-177">Jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="91221-177">Read-only</span></span>

<span data-ttu-id="91221-178">Databáze jen pro čtení, kterou aplikace nemůže změnit.</span><span class="sxs-lookup"><span data-stu-id="91221-178">A read-only database that cannot be modified by the app.</span></span>

```ConnectionString
Data Source=Reference.db;Mode=ReadOnly
```

### <a name="in-memory"></a><span data-ttu-id="91221-179">V paměti</span><span class="sxs-lookup"><span data-stu-id="91221-179">In-memory</span></span>

<span data-ttu-id="91221-180">Soukromá databáze v paměti.</span><span class="sxs-lookup"><span data-stu-id="91221-180">A private, in-memory database.</span></span>

```ConnectionString
Data Source=:memory:
```

### <a name="sharable-in-memory"></a><span data-ttu-id="91221-181">Sharable v paměti</span><span class="sxs-lookup"><span data-stu-id="91221-181">Sharable in-memory</span></span>

<span data-ttu-id="91221-182">Sharable, v paměti databáze označena názvem *Sharable*.</span><span class="sxs-lookup"><span data-stu-id="91221-182">A sharable, in-memory database identified by the name *Sharable*.</span></span>

```ConnectionString
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a><span data-ttu-id="91221-183">Viz také</span><span class="sxs-lookup"><span data-stu-id="91221-183">See also</span></span>

* [<span data-ttu-id="91221-184">Připojovací řetězce v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="91221-184">Connection Strings in ADO.NET</span></span>](../../../framework/data/adonet/connection-strings.md)
* [<span data-ttu-id="91221-185">Databáze v paměti</span><span class="sxs-lookup"><span data-stu-id="91221-185">In-Memory databases</span></span>](in-memory-databases.md)
* [<span data-ttu-id="91221-186">Transakce</span><span class="sxs-lookup"><span data-stu-id="91221-186">Transactions</span></span>](transactions.md)
