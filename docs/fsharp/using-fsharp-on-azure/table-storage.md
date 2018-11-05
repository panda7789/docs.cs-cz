---
title: Začínáme s Azure Table storage s využitím F#
description: Store strukturovaných dat v cloudu pomocí služby Azure Table storage nebo Azure Cosmos DB.
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: 2d793ba8653833ff384f1824e303b08e05aba69b
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "43519532"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a><span data-ttu-id="11aa7-103">Začínáme s Azure Table storage a Azure Cosmos DB Table API pomocí F#</span><span class="sxs-lookup"><span data-stu-id="11aa7-103">Get started with Azure Table storage and the Azure Cosmos DB Table API using F#</span></span> # 

<span data-ttu-id="11aa7-104">Azure Table storage je služba, která ukládá strukturovaná data NoSQL v cloudu.</span><span class="sxs-lookup"><span data-stu-id="11aa7-104">Azure Table storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="11aa7-105">Úložiště Table je úložiště klíčů/atributů s návrhem.</span><span class="sxs-lookup"><span data-stu-id="11aa7-105">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="11aa7-106">Vzhledem k tomu, že je Table storage bez schématu, je snadné data přizpůsobovat měnícím potřebám vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="11aa7-106">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="11aa7-107">Přístup k datům je rychlý a cenově výhodný pro všechny typy aplikací.</span><span class="sxs-lookup"><span data-stu-id="11aa7-107">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="11aa7-108">Table storage je obvykle znamená výrazně nižší náklady než tradiční SQL pro podobné objemy dat.</span><span class="sxs-lookup"><span data-stu-id="11aa7-108">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="11aa7-109">Table storage můžete použít k ukládání flexibilních datových sad, například uživatelských dat pro webové aplikace, adresářů, informací o zařízení a jiný typ metadat, které vaše služba vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="11aa7-109">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="11aa7-110">V tabulce můžete uložit libovolný počet entit a účet úložiště může obsahovat libovolný počet tabulek, až do limitu kapacity účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="11aa7-110">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

<span data-ttu-id="11aa7-111">Azure Cosmos DB poskytuje rozhraní API tabulky pro aplikace napsané pro službu Azure Table storage a, které vyžadují prémiové funkce jako například:</span><span class="sxs-lookup"><span data-stu-id="11aa7-111">Azure Cosmos DB provides the Table API for applications that are written for Azure Table storage and that require premium capabilities such as:</span></span>

- <span data-ttu-id="11aa7-112">Globální distribuce na klíč.</span><span class="sxs-lookup"><span data-stu-id="11aa7-112">Turnkey global distribution.</span></span>
- <span data-ttu-id="11aa7-113">Vyhrazená propustnost po celém světě.</span><span class="sxs-lookup"><span data-stu-id="11aa7-113">Dedicated throughput worldwide.</span></span>
- <span data-ttu-id="11aa7-114">Řádu milisekund na 99. percentilu.</span><span class="sxs-lookup"><span data-stu-id="11aa7-114">Single-digit millisecond latencies at the 99th percentile.</span></span>
- <span data-ttu-id="11aa7-115">Záruka vysoké dostupnosti.</span><span class="sxs-lookup"><span data-stu-id="11aa7-115">Guaranteed high availability.</span></span>
- <span data-ttu-id="11aa7-116">Automatické sekundární indexování.</span><span class="sxs-lookup"><span data-stu-id="11aa7-116">Automatic secondary indexing.</span></span>

<span data-ttu-id="11aa7-117">Aplikace napsané pro Azure Table storage můžete migrovat do služby Azure Cosmos DB pomocí rozhraní Table API s žádnými změnami kódu a začněte využívat prémiové funkce.</span><span class="sxs-lookup"><span data-stu-id="11aa7-117">Applications written for Azure Table storage can migrate to Azure Cosmos DB by using the Table API with no code changes and take advantage of premium capabilities.</span></span> <span data-ttu-id="11aa7-118">Rozhraní API tabulky má klientské sady SDK dostupné pro .NET, Java, Python a Node.js.</span><span class="sxs-lookup"><span data-stu-id="11aa7-118">The Table API has client SDKs available for .NET, Java, Python, and Node.js.</span></span>

<span data-ttu-id="11aa7-119">Další informace najdete v tématu [Úvod do služby Azure Cosmos DB Table API](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span><span class="sxs-lookup"><span data-stu-id="11aa7-119">For more information, see [Introduction to Azure Cosmos DB Table API](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span></span>

## <a name="about-this-tutorial"></a><span data-ttu-id="11aa7-120">Informace o tomto kurzu</span><span class="sxs-lookup"><span data-stu-id="11aa7-120">About this tutorial</span></span>

<span data-ttu-id="11aa7-121">Tento kurz ukazuje, jak napsat kód F# pro některé běžné úlohy pomocí služby Azure Table storage nebo rozhraní Azure Cosmos DB Table API, včetně vytváření a odstraní tabulka a vložení, aktualizace, odstranění nebo dotazování tabulkových dat.</span><span class="sxs-lookup"><span data-stu-id="11aa7-121">This tutorial shows how to write F# code to do some common tasks using Azure Table storage or the Azure Cosmos DB Table API, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="11aa7-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="11aa7-122">Prerequisites</span></span>

<span data-ttu-id="11aa7-123">K použití tohoto průvodce, musíte nejdřív [vytvoření účtu služby Azure storage](/azure/storage/storage-create-storage-account) nebo [účtu služby Azure Cosmos DB](https://azure.microsoft.com/try/cosmosdb/).</span><span class="sxs-lookup"><span data-stu-id="11aa7-123">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account) or [Azure Cosmos DB account](https://azure.microsoft.com/try/cosmosdb/).</span></span>


## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="11aa7-124">Vytvořit skript F# a začněte jazyka F# Interactive</span><span class="sxs-lookup"><span data-stu-id="11aa7-124">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="11aa7-125">Ukázky v tomto článku je možné v F# aplikace nebo skript F#.</span><span class="sxs-lookup"><span data-stu-id="11aa7-125">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="11aa7-126">Chcete-li vytvořit skript F#, vytvořte soubor s `.fsx` příponu, třeba `tables.fsx`, ve vašem vývojovém prostředí F#.</span><span class="sxs-lookup"><span data-stu-id="11aa7-126">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="11aa7-127">Pak pomocí [Správce balíčků](package-management.md) jako [Stáhnout](https://fsprojects.github.io/Paket/) nebo [NuGet](https://www.nuget.org/) k instalaci `WindowsAzure.Storage` balíčku a odkaz na `WindowsAzure.Storage.dll` ve skriptu pomocí `#r`směrnice.</span><span class="sxs-lookup"><span data-stu-id="11aa7-127">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="11aa7-128">Proveďte znovu `Microsoft.WindowsAzure.ConfigurationManager` zajistí Microsoft.Azure oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="11aa7-128">Do it again for `Microsoft.WindowsAzure.ConfigurationManager` in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="11aa7-129">Přidání deklarací oboru názvů</span><span class="sxs-lookup"><span data-stu-id="11aa7-129">Add namespace declarations</span></span>

<span data-ttu-id="11aa7-130">Přidejte následující `open` příkazy k hornímu okraji `tables.fsx` souboru:</span><span class="sxs-lookup"><span data-stu-id="11aa7-130">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a><span data-ttu-id="11aa7-131">Získání připojovacího řetězce služby Azure Storage</span><span class="sxs-lookup"><span data-stu-id="11aa7-131">Get your Azure Storage connection string</span></span>

<span data-ttu-id="11aa7-132">Pokud se připojujete ke službě Azure Storage Table, budete potřebovat připojovací řetězec pro účely tohoto kurzu.</span><span class="sxs-lookup"><span data-stu-id="11aa7-132">If you're connecting to Azure Storage Table service, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="11aa7-133">Váš připojovací řetězec můžete zkopírovat z portálu Azure portal.</span><span class="sxs-lookup"><span data-stu-id="11aa7-133">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="11aa7-134">Další informace o připojovacích řetězcích najdete v tématu [nakonfigurovat připojovací řetězce úložiště](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="11aa7-134">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

### <a name="get-your-azure-cosmos-db-connection-string"></a><span data-ttu-id="11aa7-135">Získání připojovacího řetězce služby Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="11aa7-135">Get your Azure Cosmos DB connection string</span></span>

<span data-ttu-id="11aa7-136">Pokud se připojujete ke službě Azure Cosmos DB, budete potřebovat připojovací řetězec pro účely tohoto kurzu.</span><span class="sxs-lookup"><span data-stu-id="11aa7-136">If you're connecting to Azure Cosmos DB, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="11aa7-137">Váš připojovací řetězec můžete zkopírovat z portálu Azure portal.</span><span class="sxs-lookup"><span data-stu-id="11aa7-137">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="11aa7-138">Na webu Azure Portal, v účtu služby Cosmos DB, přejděte na **nastavení** > **připojovací řetězec**a klikněte na tlačítko **kopírování** tlačítko zkopírujte primární připojovací Řetězec.</span><span class="sxs-lookup"><span data-stu-id="11aa7-138">In the Azure portal, in your Cosmos DB account, go to **Settings** > **Connection String**, and click the **Copy** button to copy your Primary Connection String.</span></span> 

<span data-ttu-id="11aa7-139">Pro tento kurz zadejte svůj připojovací řetězec ve vašem skriptu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="11aa7-139">For the tutorial, enter your connection string in your script, like the following example:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="11aa7-140">Je to ale **ale nedoporučený krok** skutečných projekty.</span><span class="sxs-lookup"><span data-stu-id="11aa7-140">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="11aa7-141">Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="11aa7-141">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="11aa7-142">Pečlivě vždy chránit váš klíč účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="11aa7-142">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="11aa7-143">Nedávejte ho jiným uživatelům pevného kódování, nebo ho uložili na soubor s prostým textem, který je přístupný ostatním uživatelům.</span><span class="sxs-lookup"><span data-stu-id="11aa7-143">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="11aa7-144">Můžete znovu vygenerovat klíč pomocí webu Azure Portal, pokud se domníváte, že je možná ohrožené.</span><span class="sxs-lookup"><span data-stu-id="11aa7-144">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="11aa7-145">Pro skutečné aplikace, je nejlepší způsob, jak udržovat připojovací řetězec úložiště v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="11aa7-145">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="11aa7-146">K načtení připojovacího řetězce z konfiguračního souboru, můžete udělat toto:</span><span class="sxs-lookup"><span data-stu-id="11aa7-146">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="11aa7-147">Použití nástroje Azure Configuration Manager není povinné.</span><span class="sxs-lookup"><span data-stu-id="11aa7-147">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="11aa7-148">Můžete také použít rozhraní API, jako je například rozhraní .NET Framework `ConfigurationManager` typu.</span><span class="sxs-lookup"><span data-stu-id="11aa7-148">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="11aa7-149">Analýza připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="11aa7-149">Parse the connection string</span></span>

<span data-ttu-id="11aa7-150">K analýze připojovacího řetězce, použijte:</span><span class="sxs-lookup"><span data-stu-id="11aa7-150">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="11aa7-151">Tím se vrátí `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="11aa7-151">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="11aa7-152">Vytvoření klienta služby Table service</span><span class="sxs-lookup"><span data-stu-id="11aa7-152">Create the Table service client</span></span>

<span data-ttu-id="11aa7-153">`CloudTableClient` Třída vám umožňuje načítat tabulky a entity ve službě Table storage.</span><span class="sxs-lookup"><span data-stu-id="11aa7-153">The `CloudTableClient` class enables you to retrieve tables and entities in Table storage.</span></span> <span data-ttu-id="11aa7-154">Tady je jeden způsob, jak vytvořit klienta služby:</span><span class="sxs-lookup"><span data-stu-id="11aa7-154">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="11aa7-155">Nyní jste připraveni napsat kód, který čte data z a zapisuje data do tabulky úložiště.</span><span class="sxs-lookup"><span data-stu-id="11aa7-155">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

### <a name="create-a-table"></a><span data-ttu-id="11aa7-156">Vytvoření tabulky</span><span class="sxs-lookup"><span data-stu-id="11aa7-156">Create a table</span></span>

<span data-ttu-id="11aa7-157">Tento příklad ukazuje, jak vytvořit tabulku, pokud ještě neexistuje:</span><span class="sxs-lookup"><span data-stu-id="11aa7-157">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a><span data-ttu-id="11aa7-158">Přidání entity do tabulky</span><span class="sxs-lookup"><span data-stu-id="11aa7-158">Add an entity to a table</span></span>

<span data-ttu-id="11aa7-159">Entita musí mít typ, který dědí z `TableEntity`.</span><span class="sxs-lookup"><span data-stu-id="11aa7-159">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="11aa7-160">Můžete rozšířit `TableEntity` v libovolné způsobem, který vám vyhovuje, ale váš typ *musí* mít konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="11aa7-160">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="11aa7-161">Pouze vlastnosti, které mají obě `get` a `set` jsou uložené v tabulce Azure.</span><span class="sxs-lookup"><span data-stu-id="11aa7-161">Only properties that have both `get` and `set` are stored in your Azure Table.</span></span>

<span data-ttu-id="11aa7-162">Entity oddílu a klíčem řádku jednoznačně identifikují entitu v tabulce.</span><span class="sxs-lookup"><span data-stu-id="11aa7-162">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="11aa7-163">Entity se stejným klíčem oddílu můžete dotazovat rychleji než ty, které mají různé klíče oddílů, ale používání různých klíčů oddílů umožňuje větší škálovatelnost paralelních operací.</span><span class="sxs-lookup"><span data-stu-id="11aa7-163">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="11aa7-164">Tady je příklad `Customer` , která používá `lastName` jako klíč oddílu a `firstName` jako klíč řádku.</span><span class="sxs-lookup"><span data-stu-id="11aa7-164">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="11aa7-165">Nyní přidejte `Customer` do tabulky.</span><span class="sxs-lookup"><span data-stu-id="11aa7-165">Now add `Customer` to the table.</span></span> <span data-ttu-id="11aa7-166">Chcete-li tak učinit, vytvořte `TableOperation` , který se spustí v tabulce.</span><span class="sxs-lookup"><span data-stu-id="11aa7-166">To do so, create a `TableOperation` that executes on the table.</span></span> <span data-ttu-id="11aa7-167">V tomto případě vytvoříte `Insert` operace.</span><span class="sxs-lookup"><span data-stu-id="11aa7-167">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a><span data-ttu-id="11aa7-168">Vložení dávky entit</span><span class="sxs-lookup"><span data-stu-id="11aa7-168">Insert a batch of entities</span></span>

<span data-ttu-id="11aa7-169">Do tabulky pomocí operace zápisu jednoho můžete vložit dávku entit.</span><span class="sxs-lookup"><span data-stu-id="11aa7-169">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="11aa7-170">Povolit dávkové operace můžete kombinovat operací do jedné provádění, ale mají určitá omezení:</span><span class="sxs-lookup"><span data-stu-id="11aa7-170">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="11aa7-171">Můžete provádět aktualizace, odstranění a vložení v rámci jedné dávkové operace.</span><span class="sxs-lookup"><span data-stu-id="11aa7-171">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="11aa7-172">Dávková operace může obsahovat až 100 entit.</span><span class="sxs-lookup"><span data-stu-id="11aa7-172">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="11aa7-173">Všechny entity v dávkové operaci musí mít stejný klíč oddílu.</span><span class="sxs-lookup"><span data-stu-id="11aa7-173">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="11aa7-174">I když je možné provést dotaz v dávkové operaci, musí být ale jediná operace v dávce.</span><span class="sxs-lookup"><span data-stu-id="11aa7-174">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="11aa7-175">Zde je kód, který spojuje dvě vloží do dávkové operace:</span><span class="sxs-lookup"><span data-stu-id="11aa7-175">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="11aa7-176">Načtení všech entit v oddílu</span><span class="sxs-lookup"><span data-stu-id="11aa7-176">Retrieve all entities in a partition</span></span>

<span data-ttu-id="11aa7-177">Chcete-li dotaz na tabulku pro všechny entity v oddílu, použijte `TableQuery` objektu.</span><span class="sxs-lookup"><span data-stu-id="11aa7-177">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="11aa7-178">Zde filtrovat pro entity, kde "Macek" je klíč oddílu.</span><span class="sxs-lookup"><span data-stu-id="11aa7-178">Here, you filter for entities where "Smith" is the partition key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

<span data-ttu-id="11aa7-179">Nyní můžete vytisknout výsledky:</span><span class="sxs-lookup"><span data-stu-id="11aa7-179">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]


### <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="11aa7-180">Načtení rozsahu entit v oddílu</span><span class="sxs-lookup"><span data-stu-id="11aa7-180">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="11aa7-181">Pokud nechcete dotaz na všechny entity v oddílu, můžete zadat rozsah nakombinováním filtru klíče oddílu s filtrem klíče řádku.</span><span class="sxs-lookup"><span data-stu-id="11aa7-181">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="11aa7-182">Zde použijete dva filtry k získání všech entit v oddílu "Macek" kde klíč řádku (jméno) začíná písmenem starší než "M" abecedy.</span><span class="sxs-lookup"><span data-stu-id="11aa7-182">Here, you use two filters to get all entities in the "Smith" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="11aa7-183">Nyní můžete vytisknout výsledky:</span><span class="sxs-lookup"><span data-stu-id="11aa7-183">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a><span data-ttu-id="11aa7-184">Načíst jednu entitu</span><span class="sxs-lookup"><span data-stu-id="11aa7-184">Retrieve a single entity</span></span>

<span data-ttu-id="11aa7-185">Můžete napsat dotaz pro načtení jedné konkrétní entity.</span><span class="sxs-lookup"><span data-stu-id="11aa7-185">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="11aa7-186">Zde raději použijte `TableOperation` k určení zákazníka "Ben Smith".</span><span class="sxs-lookup"><span data-stu-id="11aa7-186">Here, you use a `TableOperation` to specify the customer "Ben Smith".</span></span> <span data-ttu-id="11aa7-187">Místo kolekce, které získáte zpět `Customer`.</span><span class="sxs-lookup"><span data-stu-id="11aa7-187">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="11aa7-188">Zadání klíče oddílu a klíč řádku v dotazu je nejrychlejší způsob, jak načíst jednu entitu ze služby Table service.</span><span class="sxs-lookup"><span data-stu-id="11aa7-188">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="11aa7-189">Nyní můžete vytisknout výsledky:</span><span class="sxs-lookup"><span data-stu-id="11aa7-189">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]


### <a name="replace-an-entity"></a><span data-ttu-id="11aa7-190">Nahrazení entity</span><span class="sxs-lookup"><span data-stu-id="11aa7-190">Replace an entity</span></span>

<span data-ttu-id="11aa7-191">Jak aktualizovat entitu, načtěte ji ze služby Table service, upravte objekt entity a potom uložte změny zpět do tabulky pomocí služby `Replace` operace.</span><span class="sxs-lookup"><span data-stu-id="11aa7-191">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="11aa7-192">To způsobí entita, která má být na serveru plně nahradí, pokud má entita na serveru od načtení, v takovém případě se operace nezdaří.</span><span class="sxs-lookup"><span data-stu-id="11aa7-192">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation fails.</span></span> <span data-ttu-id="11aa7-193">Tato chyba je zabránit aplikaci v nechtěném přepsání změny z jiných zdrojů.</span><span class="sxs-lookup"><span data-stu-id="11aa7-193">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a><span data-ttu-id="11aa7-194">Vložení nebo nahrazení entity</span><span class="sxs-lookup"><span data-stu-id="11aa7-194">Insert-or-replace an entity</span></span>

<span data-ttu-id="11aa7-195">V některých případech nevíte, jestli entita existuje v tabulce.</span><span class="sxs-lookup"><span data-stu-id="11aa7-195">Sometimes, you don't know whether an entity exists in the table.</span></span> <span data-ttu-id="11aa7-196">A pokud ano, aktuální hodnoty uložené v ní už nejsou potřeba.</span><span class="sxs-lookup"><span data-stu-id="11aa7-196">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="11aa7-197">Můžete použít `InsertOrReplace` vytvořit entitu, nebo pokud existuje, bez ohledu na jeho stavu, nahraďte ho.</span><span class="sxs-lookup"><span data-stu-id="11aa7-197">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="11aa7-198">Dotaz na podmnožinu vlastností entity</span><span class="sxs-lookup"><span data-stu-id="11aa7-198">Query a subset of entity properties</span></span>

<span data-ttu-id="11aa7-199">Tabulkový dotaz může načíst jenom několik z entity místo všechny z nich.</span><span class="sxs-lookup"><span data-stu-id="11aa7-199">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="11aa7-200">Tato technika, říká projekce, může zlepšit výkon dotazů, zejména u velkých entit.</span><span class="sxs-lookup"><span data-stu-id="11aa7-200">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="11aa7-201">Tady, vrátí pouze e-mailové adresy, které používají `DynamicTableEntity` a `EntityResolver`.</span><span class="sxs-lookup"><span data-stu-id="11aa7-201">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="11aa7-202">Všimněte si, že projekci nepodporuje emulátor místního úložiště, takže tento kód se spustí pouze v případě, že používáte účet služby Table Service.</span><span class="sxs-lookup"><span data-stu-id="11aa7-202">Note that projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="11aa7-203">Načítání entit na stránkách asynchronně</span><span class="sxs-lookup"><span data-stu-id="11aa7-203">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="11aa7-204">Pokud načítáte velký počet entit a chcete pro jejich zpracování, jak jsou načítány, spíše než čekat na jejich všechny k vrácení, můžete pomocí segmentovaného dotazu.</span><span class="sxs-lookup"><span data-stu-id="11aa7-204">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="11aa7-205">Tady vracet výsledky na stránkách s použitím asynchronního pracovního postupu tak, aby spuštění není blokován, zatímco čekáte pro velké sady výsledků k vrácení.</span><span class="sxs-lookup"><span data-stu-id="11aa7-205">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

<span data-ttu-id="11aa7-206">Můžete teď tento výpočet synchronnímu provádění:</span><span class="sxs-lookup"><span data-stu-id="11aa7-206">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a><span data-ttu-id="11aa7-207">Odstranit entitu</span><span class="sxs-lookup"><span data-stu-id="11aa7-207">Delete an entity</span></span>

<span data-ttu-id="11aa7-208">Entitu můžete po jejím načtení odstranit.</span><span class="sxs-lookup"><span data-stu-id="11aa7-208">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="11aa7-209">Stejně jako u aktualizaci entity, to se nezdaří, pokud entita se nezměnila, protože jste získali.</span><span class="sxs-lookup"><span data-stu-id="11aa7-209">As with updating an entity, this fails if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a><span data-ttu-id="11aa7-210">Odstranit tabulku</span><span class="sxs-lookup"><span data-stu-id="11aa7-210">Delete a table</span></span>

<span data-ttu-id="11aa7-211">Můžete odstranit tabulku z účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="11aa7-211">You can delete a table from a storage account.</span></span> <span data-ttu-id="11aa7-212">Tabulku, která byla odstraněna, nebude potřeba znovu vytvořit pro určitou dobu, po odstranění.</span><span class="sxs-lookup"><span data-stu-id="11aa7-212">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a><span data-ttu-id="11aa7-213">Další kroky</span><span class="sxs-lookup"><span data-stu-id="11aa7-213">Next steps</span></span>

<span data-ttu-id="11aa7-214">Teď, když jste se naučili základy používání služby Table storage, na následujících odkazech najdete informace o složitějších úlohách úložiště a rozhraní Azure Cosmos DB Table API.</span><span class="sxs-lookup"><span data-stu-id="11aa7-214">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks and the Azure Cosmos DB Table API.</span></span>

- [<span data-ttu-id="11aa7-215">Úvod do služby Azure Cosmos DB Table API</span><span class="sxs-lookup"><span data-stu-id="11aa7-215">Introduction to Azure Cosmos DB Table API</span></span>](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [<span data-ttu-id="11aa7-216">Klientská knihovna pro úložiště pro .NET – referenční informace</span><span class="sxs-lookup"><span data-stu-id="11aa7-216">Storage Client Library for .NET reference</span></span>](https://docs.microsoft.com/dotnet/api/overview/azure/storage?view=azure-dotnet)
- [<span data-ttu-id="11aa7-217">Typ zprostředkovatele služby Azure Storage</span><span class="sxs-lookup"><span data-stu-id="11aa7-217">Azure Storage Type Provider</span></span>](http://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="11aa7-218">Blog týmu Azure Storage</span><span class="sxs-lookup"><span data-stu-id="11aa7-218">Azure Storage Team Blog</span></span>](https://blogs.msdn.com/b/windowsazurestorage/)
- [<span data-ttu-id="11aa7-219">Konfigurace připojovacích řetězců</span><span class="sxs-lookup"><span data-stu-id="11aa7-219">Configuring Connection Strings</span></span>](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="11aa7-220">Začínáme s Azure Table Storage v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="11aa7-220">Getting Started with Azure Table Storage in .NET</span></span>](https://azure.microsoft.com/resources/samples/storage-table-dotnet-getting-started/)
