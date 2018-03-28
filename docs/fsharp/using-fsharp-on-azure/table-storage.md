---
title: 'Začínáme s Azure Table storage pomocí F #'
description: Ukládejte si strukturovaná data v cloudu pomocí Azure Table storage nebo Azure Cosmos DB.
keywords: 'Visual f #, f #, funkční programování, .NET, .NET Core, Azure'
author: sylvanc
ms.author: phcart
ms.date: 03/26/2018
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9e5d6cea-a98c-461e-a5cc-75f1d154eafd
ms.openlocfilehash: 6d40211e13e8d213aa5a40d585dd384abf49ddfa
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2018
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a><span data-ttu-id="75618-104">Začínáme s Azure Table storage a Cosmos DB tabulky rozhraní API služby Azure pomocí F #</span><span class="sxs-lookup"><span data-stu-id="75618-104">Get started with Azure Table storage and the Azure Cosmos DB Table API using F#</span></span> # 

<span data-ttu-id="75618-105">Azure Table storage je služba, která ukládá strukturovaná data typu NoSQL v cloudu.</span><span class="sxs-lookup"><span data-stu-id="75618-105">Azure Table storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="75618-106">Úložiště Table je úložiště klíčů/atributů s návrhem.</span><span class="sxs-lookup"><span data-stu-id="75618-106">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="75618-107">Protože úložiště Table nemá schéma, je snadné data přizpůsobovat potřebám vaší aplikace měnícím.</span><span class="sxs-lookup"><span data-stu-id="75618-107">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="75618-108">Přístup k datům je rychlý a nákladově efektivní pro všechny typy aplikací.</span><span class="sxs-lookup"><span data-stu-id="75618-108">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="75618-109">Table storage je obvykle znamená výrazně nižší náklady než tradiční SQL pro podobné objemy dat.</span><span class="sxs-lookup"><span data-stu-id="75618-109">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="75618-110">Úložiště tabulek můžete použít k ukládání flexibilních datových sad, například uživatelských dat pro webové aplikace, adresáře, informace o zařízení a jiný typ metadat, které vaše služba vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="75618-110">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="75618-111">V tabulce můžete uložit libovolný počet entit a účet úložiště může obsahovat libovolný počet tabulek, až do limitu kapacity účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="75618-111">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

<span data-ttu-id="75618-112">Azure Cosmos DB poskytuje rozhraní API tabulky pro aplikace, které jsou napsané pro Azure Table storage a které vyžadují premium možnosti, jako:</span><span class="sxs-lookup"><span data-stu-id="75618-112">Azure Cosmos DB provides the Table API for applications that are written for Azure Table storage and that require premium capabilities such as:</span></span>

- <span data-ttu-id="75618-113">To globální distribuce.</span><span class="sxs-lookup"><span data-stu-id="75618-113">Turnkey global distribution.</span></span>
- <span data-ttu-id="75618-114">Vyhrazené propustnost po celém světě.</span><span class="sxs-lookup"><span data-stu-id="75618-114">Dedicated throughput worldwide.</span></span>
- <span data-ttu-id="75618-115">Jednociferné milisekundu latence v 99th percentil.</span><span class="sxs-lookup"><span data-stu-id="75618-115">Single-digit millisecond latencies at the 99th percentile.</span></span>
- <span data-ttu-id="75618-116">Zaručit vysoká dostupnost.</span><span class="sxs-lookup"><span data-stu-id="75618-116">Guaranteed high availability.</span></span>
- <span data-ttu-id="75618-117">Automatické sekundární indexování.</span><span class="sxs-lookup"><span data-stu-id="75618-117">Automatic secondary indexing.</span></span>

<span data-ttu-id="75618-118">Aplikace napsané pro Azure Table storage můžete migrovat do databáze Cosmos Azure pomocí rozhraní API tabulky beze změn kódu a využívat možnosti úrovně premium.</span><span class="sxs-lookup"><span data-stu-id="75618-118">Applications written for Azure Table storage can migrate to Azure Cosmos DB by using the Table API with no code changes and take advantage of premium capabilities.</span></span> <span data-ttu-id="75618-119">Rozhraní API tabulka má k dispozici klientské sady SDK pro .NET, Java, Python a Node.js.</span><span class="sxs-lookup"><span data-stu-id="75618-119">The Table API has client SDKs available for .NET, Java, Python, and Node.js.</span></span>

<span data-ttu-id="75618-120">Další informace najdete v tématu [Úvod do rozhraní API služby Azure Cosmos DB tabulky](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span><span class="sxs-lookup"><span data-stu-id="75618-120">For more information, see [Introduction to Azure Cosmos DB Table API](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span></span>

## <a name="about-this-tutorial"></a><span data-ttu-id="75618-121">O tomto kurzu</span><span class="sxs-lookup"><span data-stu-id="75618-121">About this tutorial</span></span>

<span data-ttu-id="75618-122">Tento kurz ukazuje, jak napsat kód F # pro provést některé běžné úlohy pomocí Azure Table storage nebo Cosmos DB tabulky rozhraní API služby Azure, včetně vytváření a odstraňování tabulek a vkládání, aktualizaci, odstranění a dotazování dat v tabulce.</span><span class="sxs-lookup"><span data-stu-id="75618-122">This tutorial shows how to write F# code to do some common tasks using Azure Table storage or the Azure Cosmos DB Table API, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="75618-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="75618-123">Prerequisites</span></span>

<span data-ttu-id="75618-124">Chcete-li tohoto průvodce použijte, je nutné nejprve [vytvořit účet úložiště Azure](/azure/storage/storage-create-storage-account) nebo [účet Azure Cosmos DB](https://azure.microsoft.com/try/cosmosdb/).</span><span class="sxs-lookup"><span data-stu-id="75618-124">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account) or [Azure Cosmos DB account](https://azure.microsoft.com/try/cosmosdb/).</span></span>


## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="75618-125">Vytvoření F # skript a spusťte F # interaktivní</span><span class="sxs-lookup"><span data-stu-id="75618-125">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="75618-126">Ukázky v tomto článku slouží v aplikaci F # nebo skriptu F #.</span><span class="sxs-lookup"><span data-stu-id="75618-126">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="75618-127">Chcete-li vytvořit skript F #, vytvořte soubor s `.fsx` příponu, třeba `tables.fsx`, ve vašem vývojovém prostředí F #.</span><span class="sxs-lookup"><span data-stu-id="75618-127">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="75618-128">Pak pomocí [Správce balíčků](package-management.md) například [Stáhnout](https://fsprojects.github.io/Paket/) nebo [NuGet](https://www.nuget.org/) k instalaci `WindowsAzure.Storage` balíčku a referenční dokumentace `WindowsAzure.Storage.dll` ve vašem skriptu, použití `#r`– direktiva.</span><span class="sxs-lookup"><span data-stu-id="75618-128">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="75618-129">Provést akci pro `Microsoft.WindowsAzure.ConfigurationManager` k získání Microsoft.Azure oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="75618-129">Do it again for `Microsoft.WindowsAzure.ConfigurationManager` in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="75618-130">Přidání deklarace oborů názvů</span><span class="sxs-lookup"><span data-stu-id="75618-130">Add namespace declarations</span></span>

<span data-ttu-id="75618-131">Přidejte následující `open` příkazů do horní části `tables.fsx` souboru:</span><span class="sxs-lookup"><span data-stu-id="75618-131">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a><span data-ttu-id="75618-132">Získat připojovací řetězec úložiště Azure</span><span class="sxs-lookup"><span data-stu-id="75618-132">Get your Azure Storage connection string</span></span>

<span data-ttu-id="75618-133">Pokud se připojujete ke službě Azure Storage Table, budete potřebovat připojovací řetězec pro účely tohoto kurzu.</span><span class="sxs-lookup"><span data-stu-id="75618-133">If you're connecting to Azure Storage Table service, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="75618-134">Připojovací řetězec můžete zkopírovat z portálu Azure.</span><span class="sxs-lookup"><span data-stu-id="75618-134">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="75618-135">Další informace o připojovacích řetězcích najdete v tématu [nakonfigurování připojovacích řetězců Storage](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="75618-135">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

### <a name="get-your-azure-cosmos-db-connection-string"></a><span data-ttu-id="75618-136">Získání připojovacího řetězce Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="75618-136">Get your Azure Cosmos DB connection string</span></span>

<span data-ttu-id="75618-137">Pokud se připojujete k databázi Cosmos Azure, budete potřebovat připojovací řetězec pro účely tohoto kurzu.</span><span class="sxs-lookup"><span data-stu-id="75618-137">If you're connecting to Azure Cosmos DB, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="75618-138">Připojovací řetězec můžete zkopírovat z portálu Azure.</span><span class="sxs-lookup"><span data-stu-id="75618-138">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="75618-139">Na portálu Azure v účtu Cosmos DB, přejděte na **nastavení** > **připojovací řetězec**a klikněte na tlačítko **kopie** tlačítko Kopírovat primární připojení Řetězec.</span><span class="sxs-lookup"><span data-stu-id="75618-139">In the Azure portal, in your Cosmos DB account, go to **Settings** > **Connection String**, and click the **Copy** button to copy your Primary Connection String.</span></span> 

<span data-ttu-id="75618-140">Pro tento kurz zadejte připojovací řetězec ve vašem skriptu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="75618-140">For the tutorial, enter your connection string in your script, like the following example:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="75618-141">Je to ale **nedoporučuje** skutečných projekty.</span><span class="sxs-lookup"><span data-stu-id="75618-141">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="75618-142">Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="75618-142">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="75618-143">Vždycky pečlivě k ochraně klíče účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="75618-143">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="75618-144">Nedávejte ho jiným uživatelům, nezakódovávejte ho nebo ho uložit v souboru formátu prostého textu, který je přístupný ostatním uživatelům.</span><span class="sxs-lookup"><span data-stu-id="75618-144">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="75618-145">Můžete znovu vygenerovat klíč pomocí portálu Azure, pokud se domníváte, že by může ohrožení.</span><span class="sxs-lookup"><span data-stu-id="75618-145">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="75618-146">Skutečných aplikace, je nejlepší způsob, jak udržovat připojovací řetězec úložiště v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="75618-146">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="75618-147">K načtení připojovacího řetězce z konfiguračního souboru, můžete to udělat:</span><span class="sxs-lookup"><span data-stu-id="75618-147">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="75618-148">Použití nástroje Azure Configuration Manager není povinné.</span><span class="sxs-lookup"><span data-stu-id="75618-148">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="75618-149">Můžete také použít API jako třeba rozhraní .NET Framework `ConfigurationManager` typu.</span><span class="sxs-lookup"><span data-stu-id="75618-149">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="75618-150">Analýza připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="75618-150">Parse the connection string</span></span>

<span data-ttu-id="75618-151">Chcete-li analyzovat připojovací řetězec, použijte:</span><span class="sxs-lookup"><span data-stu-id="75618-151">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="75618-152">Tento příkaz vrátí `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="75618-152">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="75618-153">Vytvoření klienta služby Table</span><span class="sxs-lookup"><span data-stu-id="75618-153">Create the Table service client</span></span>

<span data-ttu-id="75618-154">`CloudTableClient` Vám umožňuje načíst tabulky a entity ve službě Table storage.</span><span class="sxs-lookup"><span data-stu-id="75618-154">The `CloudTableClient` class enables you to retrieve tables and entities in Table storage.</span></span> <span data-ttu-id="75618-155">Tady je jeden způsob, jak vytvořit klienta služby:</span><span class="sxs-lookup"><span data-stu-id="75618-155">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="75618-156">Teď jste připravení psát kód, který načítá a zapisuje data do úložiště tabulek.</span><span class="sxs-lookup"><span data-stu-id="75618-156">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

### <a name="create-a-table"></a><span data-ttu-id="75618-157">Umožňuje vytvořit tabulku</span><span class="sxs-lookup"><span data-stu-id="75618-157">Create a table</span></span>

<span data-ttu-id="75618-158">Tento příklad ukazuje, jak vytvořit tabulku, pokud ještě neexistuje:</span><span class="sxs-lookup"><span data-stu-id="75618-158">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a><span data-ttu-id="75618-159">Přidání entity do tabulky</span><span class="sxs-lookup"><span data-stu-id="75618-159">Add an entity to a table</span></span>

<span data-ttu-id="75618-160">Entita musí mít typ, který dědí z `TableEntity`.</span><span class="sxs-lookup"><span data-stu-id="75618-160">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="75618-161">Můžete rozšířit `TableEntity` v jakýmkoli způsobem se vám líbí, ale typ vašeho *musí* mít konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="75618-161">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="75618-162">Pouze vlastnosti, které oba `get` a `set` jsou uložené v Azure Table.</span><span class="sxs-lookup"><span data-stu-id="75618-162">Only properties that have both `get` and `set` are stored in your Azure Table.</span></span>

<span data-ttu-id="75618-163">Klíč entity oddílu a řádku entity jednoznačně identifikují entitu v tabulce.</span><span class="sxs-lookup"><span data-stu-id="75618-163">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="75618-164">Entity se stejným klíčem oddílu můžete zadat dotaz rychleji než ty, které se různé klíče oddílů, ale používání různých klíčů oddílů umožňuje větší škálovatelnost paralelních operací.</span><span class="sxs-lookup"><span data-stu-id="75618-164">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="75618-165">Tady je příklad `Customer` používající `lastName` jako klíč oddílu a `firstName` jako klíč řádku.</span><span class="sxs-lookup"><span data-stu-id="75618-165">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="75618-166">Nyní přidejte `Customer` do tabulky.</span><span class="sxs-lookup"><span data-stu-id="75618-166">Now add `Customer` to the table.</span></span> <span data-ttu-id="75618-167">Chcete-li tak učinit, vytvořte `TableOperation` , která se spouští v tabulce.</span><span class="sxs-lookup"><span data-stu-id="75618-167">To do so, create a `TableOperation` that executes on the table.</span></span> <span data-ttu-id="75618-168">V tomto případě vytvoříte `Insert` operaci.</span><span class="sxs-lookup"><span data-stu-id="75618-168">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a><span data-ttu-id="75618-169">Vložení dávky entit</span><span class="sxs-lookup"><span data-stu-id="75618-169">Insert a batch of entities</span></span>

<span data-ttu-id="75618-170">Do tabulky pomocí jednoho zápisu operace můžete vložit dávku entit.</span><span class="sxs-lookup"><span data-stu-id="75618-170">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="75618-171">Dávkové operace umožňují kombinovat operací do jednoho spuštění, ale mají určitá omezení:</span><span class="sxs-lookup"><span data-stu-id="75618-171">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="75618-172">Můžete provádět aktualizace, odstranění a vložení v rámci jedné dávkové operace.</span><span class="sxs-lookup"><span data-stu-id="75618-172">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="75618-173">Dávková operace může obsahovat až 100 entit.</span><span class="sxs-lookup"><span data-stu-id="75618-173">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="75618-174">Všechny entity v rámci dávkové operace musí mít stejný klíč oddílu.</span><span class="sxs-lookup"><span data-stu-id="75618-174">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="75618-175">I když je možné provést dotaz v rámci dávkové operace, musí být ale jediná operace v dávce.</span><span class="sxs-lookup"><span data-stu-id="75618-175">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="75618-176">Zde je kód, který kombinuje dvě vloží do dávkové operace:</span><span class="sxs-lookup"><span data-stu-id="75618-176">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="75618-177">Načtení všech entit v oddílu</span><span class="sxs-lookup"><span data-stu-id="75618-177">Retrieve all entities in a partition</span></span>

<span data-ttu-id="75618-178">Dotaz na tabulku pro všechny entity v oddílu, použijte `TableQuery` objektu.</span><span class="sxs-lookup"><span data-stu-id="75618-178">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="75618-179">Zde můžete filtr pro entity kde "Smith" je klíč oddílu.</span><span class="sxs-lookup"><span data-stu-id="75618-179">Here, you filter for entities where "Smith" is the partition key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

<span data-ttu-id="75618-180">Nyní vytisknout výsledky:</span><span class="sxs-lookup"><span data-stu-id="75618-180">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]


### <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="75618-181">Načtení rozsahu entit v oddílu</span><span class="sxs-lookup"><span data-stu-id="75618-181">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="75618-182">Pokud nechcete, aby k dotazování všechny entity v oddílu, můžete zadat rozsah kombinací filtru klíče oddílu s filtrem klíče řádku.</span><span class="sxs-lookup"><span data-stu-id="75618-182">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="75618-183">Tady můžete použít dva filtry k získání všech entit v oddílu "Smith" kde klíč řádku (jméno) začíná písmenem starší než "M" abecedy.</span><span class="sxs-lookup"><span data-stu-id="75618-183">Here, you use two filters to get all entities in the "Smith" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="75618-184">Nyní vytisknout výsledky:</span><span class="sxs-lookup"><span data-stu-id="75618-184">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a><span data-ttu-id="75618-185">Načtení jedné entity</span><span class="sxs-lookup"><span data-stu-id="75618-185">Retrieve a single entity</span></span>

<span data-ttu-id="75618-186">Můžete napsat dotaz pro načtení jedné konkrétní entity.</span><span class="sxs-lookup"><span data-stu-id="75618-186">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="75618-187">Tady můžete použít `TableOperation` k určení zákazníka "Ben Smith".</span><span class="sxs-lookup"><span data-stu-id="75618-187">Here, you use a `TableOperation` to specify the customer "Ben Smith".</span></span> <span data-ttu-id="75618-188">Místo kolekce, můžete se vrátit `Customer`.</span><span class="sxs-lookup"><span data-stu-id="75618-188">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="75618-189">V dotazu zadat klíč oddílu a klíč řádku je nejrychlejší způsob, jak načíst jednu entitu ze služby Table.</span><span class="sxs-lookup"><span data-stu-id="75618-189">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="75618-190">Nyní vytisknout výsledky:</span><span class="sxs-lookup"><span data-stu-id="75618-190">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]


### <a name="replace-an-entity"></a><span data-ttu-id="75618-191">Nahrazení entity</span><span class="sxs-lookup"><span data-stu-id="75618-191">Replace an entity</span></span>

<span data-ttu-id="75618-192">Pokud chcete entitu aktualizovat, načtěte ji ze služby Table, upravte objekt entity a potom uložte změny zpět k tabulce služby pomocí `Replace` operaci.</span><span class="sxs-lookup"><span data-stu-id="75618-192">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="75618-193">To způsobí, že entita, která má být plně nahradí na serveru, pokud se entita na serveru se změnil od načtení, v takovém případě se operace nezdaří.</span><span class="sxs-lookup"><span data-stu-id="75618-193">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation fails.</span></span> <span data-ttu-id="75618-194">Je toto selhání zabrání vaší aplikaci v nechtěném přepsání změny z jiných zdrojů.</span><span class="sxs-lookup"><span data-stu-id="75618-194">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a><span data-ttu-id="75618-195">Vložení nebo nahrazení entity</span><span class="sxs-lookup"><span data-stu-id="75618-195">Insert-or-replace an entity</span></span>

<span data-ttu-id="75618-196">V některých případech nevíte, zda entita existuje v tabulce.</span><span class="sxs-lookup"><span data-stu-id="75618-196">Sometimes, you don't know whether an entity exists in the table.</span></span> <span data-ttu-id="75618-197">A pokud ano, aktuální hodnoty v ní uloženy už nejsou potřeba.</span><span class="sxs-lookup"><span data-stu-id="75618-197">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="75618-198">Můžete použít `InsertOrReplace` vytvořit entitu, nebo ho nahradit, pokud existuje, bez ohledu na jeho stav.</span><span class="sxs-lookup"><span data-stu-id="75618-198">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="75618-199">Dotaz na podmnožinu vlastností entity</span><span class="sxs-lookup"><span data-stu-id="75618-199">Query a subset of entity properties</span></span>

<span data-ttu-id="75618-200">Dotaz na tabulku můžete načíst jenom několik z entity, místo všechny z nich.</span><span class="sxs-lookup"><span data-stu-id="75618-200">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="75618-201">Tento postup volá projekce, může zlepšit výkon dotazů, hlavně pro velké entity.</span><span class="sxs-lookup"><span data-stu-id="75618-201">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="75618-202">Zde můžete vrátit pouze e-mailových adres, pomocí `DynamicTableEntity` a `EntityResolver`.</span><span class="sxs-lookup"><span data-stu-id="75618-202">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="75618-203">Všimněte si, že projekci nepodporuje emulátor místního úložiště, takže tento kód spustí pouze v případě, že používáte účet služby Table.</span><span class="sxs-lookup"><span data-stu-id="75618-203">Note that projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="75618-204">Načtení entit na stránkách asynchronně</span><span class="sxs-lookup"><span data-stu-id="75618-204">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="75618-205">Pokud načítáte velký počet entit a chcete je zpracovat, protože jsou načítány místo čekání mají všechny vrátí, můžete použít segmentovaného dotazu.</span><span class="sxs-lookup"><span data-stu-id="75618-205">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="75618-206">Zde vracet výsledky na stránkách pomocí pracovním postupu asynchronní tak, aby provádění není blokován, zatímco čekáte pro velké sady výsledků vrátit.</span><span class="sxs-lookup"><span data-stu-id="75618-206">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

<span data-ttu-id="75618-207">Je teď spustit tento výpočet synchronně:</span><span class="sxs-lookup"><span data-stu-id="75618-207">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a><span data-ttu-id="75618-208">Odstranění entity</span><span class="sxs-lookup"><span data-stu-id="75618-208">Delete an entity</span></span>

<span data-ttu-id="75618-209">Entitu můžete po jejím načtení odstranit.</span><span class="sxs-lookup"><span data-stu-id="75618-209">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="75618-210">Stejně jako u aktualizaci entity se to nezdaří, pokud entity došlo ke změně vzhledem k tomu, že jste jej získali.</span><span class="sxs-lookup"><span data-stu-id="75618-210">As with updating an entity, this fails if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a><span data-ttu-id="75618-211">Odstranění tabulky</span><span class="sxs-lookup"><span data-stu-id="75618-211">Delete a table</span></span>

<span data-ttu-id="75618-212">Odstranit tabulku z účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="75618-212">You can delete a table from a storage account.</span></span> <span data-ttu-id="75618-213">Tabulka, která byla odstraněna není k dispozici pro určitou dobu po odstranění byla znovu vytvořena.</span><span class="sxs-lookup"><span data-stu-id="75618-213">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a><span data-ttu-id="75618-214">Další kroky</span><span class="sxs-lookup"><span data-stu-id="75618-214">Next steps</span></span>

<span data-ttu-id="75618-215">Teď, když jste se naučili základy používání služby Table storage, postupujte podle následujících odkazech na další informace o složitějších úlohách úložiště a rozhraní API služby Azure DB Cosmos tabulky.</span><span class="sxs-lookup"><span data-stu-id="75618-215">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks and the Azure Cosmos DB Table API.</span></span>

- [<span data-ttu-id="75618-216">Úvod do Azure Cosmos DB tabulky API</span><span class="sxs-lookup"><span data-stu-id="75618-216">Introduction to Azure Cosmos DB Table API</span></span>](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [<span data-ttu-id="75618-217">Klientská knihovna pro úložiště pro .NET – referenční informace</span><span class="sxs-lookup"><span data-stu-id="75618-217">Storage Client Library for .NET reference</span></span>](https://docs.microsoft.com/dotnet/api/overview/azure/storage?view=azure-dotnet)
- [<span data-ttu-id="75618-218">Typ zprostředkovatele úložiště Azure</span><span class="sxs-lookup"><span data-stu-id="75618-218">Azure Storage Type Provider</span></span>](http://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="75618-219">Blog týmu Azure Storage</span><span class="sxs-lookup"><span data-stu-id="75618-219">Azure Storage Team Blog</span></span>](http://blogs.msdn.com/b/windowsazurestorage/)
- [<span data-ttu-id="75618-220">Konfigurace připojovacích řetězců</span><span class="sxs-lookup"><span data-stu-id="75618-220">Configuring Connection Strings</span></span>](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="75618-221">Začínáme s Azure Table Storage v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="75618-221">Getting Started with Azure Table Storage in .NET</span></span>](https://azure.microsoft.com/resources/samples/storage-table-dotnet-getting-started/)
