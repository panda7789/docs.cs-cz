---
title: 'Začínáme s Azure Table storage pomocí F #'
description: Ukládejte si strukturovaná data v cloudu pomocí Azure Table storage nebo Azure Cosmos DB.
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: ac81bc88db1436aa4d5f576da61a90839df04b99
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575391"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a><span data-ttu-id="8169e-103">Začínáme s Azure Table storage a Cosmos DB tabulky rozhraní API služby Azure pomocí F #</span><span class="sxs-lookup"><span data-stu-id="8169e-103">Get started with Azure Table storage and the Azure Cosmos DB Table API using F#</span></span> # 

<span data-ttu-id="8169e-104">Azure Table storage je služba, která ukládá strukturovaná data typu NoSQL v cloudu.</span><span class="sxs-lookup"><span data-stu-id="8169e-104">Azure Table storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="8169e-105">Úložiště Table je úložiště klíčů/atributů s návrhem.</span><span class="sxs-lookup"><span data-stu-id="8169e-105">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="8169e-106">Protože úložiště Table nemá schéma, je snadné data přizpůsobovat potřebám vaší aplikace měnícím.</span><span class="sxs-lookup"><span data-stu-id="8169e-106">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="8169e-107">Přístup k datům je rychlý a nákladově efektivní pro všechny typy aplikací.</span><span class="sxs-lookup"><span data-stu-id="8169e-107">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="8169e-108">Table storage je obvykle znamená výrazně nižší náklady než tradiční SQL pro podobné objemy dat.</span><span class="sxs-lookup"><span data-stu-id="8169e-108">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="8169e-109">Úložiště tabulek můžete použít k ukládání flexibilních datových sad, například uživatelských dat pro webové aplikace, adresáře, informace o zařízení a jiný typ metadat, které vaše služba vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="8169e-109">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="8169e-110">V tabulce můžete uložit libovolný počet entit a účet úložiště může obsahovat libovolný počet tabulek, až do limitu kapacity účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="8169e-110">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

<span data-ttu-id="8169e-111">Azure Cosmos DB poskytuje rozhraní API tabulky pro aplikace, které jsou napsané pro Azure Table storage a které vyžadují premium možnosti, jako:</span><span class="sxs-lookup"><span data-stu-id="8169e-111">Azure Cosmos DB provides the Table API for applications that are written for Azure Table storage and that require premium capabilities such as:</span></span>

- <span data-ttu-id="8169e-112">To globální distribuce.</span><span class="sxs-lookup"><span data-stu-id="8169e-112">Turnkey global distribution.</span></span>
- <span data-ttu-id="8169e-113">Vyhrazené propustnost po celém světě.</span><span class="sxs-lookup"><span data-stu-id="8169e-113">Dedicated throughput worldwide.</span></span>
- <span data-ttu-id="8169e-114">Jednociferné milisekundu latence v 99th percentil.</span><span class="sxs-lookup"><span data-stu-id="8169e-114">Single-digit millisecond latencies at the 99th percentile.</span></span>
- <span data-ttu-id="8169e-115">Zaručit vysoká dostupnost.</span><span class="sxs-lookup"><span data-stu-id="8169e-115">Guaranteed high availability.</span></span>
- <span data-ttu-id="8169e-116">Automatické sekundární indexování.</span><span class="sxs-lookup"><span data-stu-id="8169e-116">Automatic secondary indexing.</span></span>

<span data-ttu-id="8169e-117">Aplikace napsané pro Azure Table storage můžete migrovat do databáze Cosmos Azure pomocí rozhraní API tabulky beze změn kódu a využívat možnosti úrovně premium.</span><span class="sxs-lookup"><span data-stu-id="8169e-117">Applications written for Azure Table storage can migrate to Azure Cosmos DB by using the Table API with no code changes and take advantage of premium capabilities.</span></span> <span data-ttu-id="8169e-118">Rozhraní API tabulka má k dispozici klientské sady SDK pro .NET, Java, Python a Node.js.</span><span class="sxs-lookup"><span data-stu-id="8169e-118">The Table API has client SDKs available for .NET, Java, Python, and Node.js.</span></span>

<span data-ttu-id="8169e-119">Další informace najdete v tématu [Úvod do rozhraní API služby Azure Cosmos DB tabulky](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span><span class="sxs-lookup"><span data-stu-id="8169e-119">For more information, see [Introduction to Azure Cosmos DB Table API](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span></span>

## <a name="about-this-tutorial"></a><span data-ttu-id="8169e-120">O tomto kurzu</span><span class="sxs-lookup"><span data-stu-id="8169e-120">About this tutorial</span></span>

<span data-ttu-id="8169e-121">Tento kurz ukazuje, jak napsat kód F # pro provést některé běžné úlohy pomocí Azure Table storage nebo Cosmos DB tabulky rozhraní API služby Azure, včetně vytváření a odstraňování tabulek a vkládání, aktualizaci, odstranění a dotazování dat v tabulce.</span><span class="sxs-lookup"><span data-stu-id="8169e-121">This tutorial shows how to write F# code to do some common tasks using Azure Table storage or the Azure Cosmos DB Table API, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8169e-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8169e-122">Prerequisites</span></span>

<span data-ttu-id="8169e-123">Chcete-li tohoto průvodce použijte, je nutné nejprve [vytvořit účet úložiště Azure](/azure/storage/storage-create-storage-account) nebo [účet Azure Cosmos DB](https://azure.microsoft.com/try/cosmosdb/).</span><span class="sxs-lookup"><span data-stu-id="8169e-123">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account) or [Azure Cosmos DB account](https://azure.microsoft.com/try/cosmosdb/).</span></span>


## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="8169e-124">Vytvoření F # skript a spusťte F # interaktivní</span><span class="sxs-lookup"><span data-stu-id="8169e-124">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="8169e-125">Ukázky v tomto článku slouží v aplikaci F # nebo skriptu F #.</span><span class="sxs-lookup"><span data-stu-id="8169e-125">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="8169e-126">Chcete-li vytvořit skript F #, vytvořte soubor s `.fsx` příponu, třeba `tables.fsx`, ve vašem vývojovém prostředí F #.</span><span class="sxs-lookup"><span data-stu-id="8169e-126">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="8169e-127">Pak pomocí [Správce balíčků](package-management.md) například [Stáhnout](https://fsprojects.github.io/Paket/) nebo [NuGet](https://www.nuget.org/) k instalaci `WindowsAzure.Storage` balíčku a referenční dokumentace `WindowsAzure.Storage.dll` ve vašem skriptu, použití `#r`– direktiva.</span><span class="sxs-lookup"><span data-stu-id="8169e-127">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="8169e-128">Provést akci pro `Microsoft.WindowsAzure.ConfigurationManager` k získání Microsoft.Azure oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8169e-128">Do it again for `Microsoft.WindowsAzure.ConfigurationManager` in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="8169e-129">Přidání deklarace oborů názvů</span><span class="sxs-lookup"><span data-stu-id="8169e-129">Add namespace declarations</span></span>

<span data-ttu-id="8169e-130">Přidejte následující `open` příkazů do horní části `tables.fsx` souboru:</span><span class="sxs-lookup"><span data-stu-id="8169e-130">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a><span data-ttu-id="8169e-131">Získat připojovací řetězec úložiště Azure</span><span class="sxs-lookup"><span data-stu-id="8169e-131">Get your Azure Storage connection string</span></span>

<span data-ttu-id="8169e-132">Pokud se připojujete ke službě Azure Storage Table, budete potřebovat připojovací řetězec pro účely tohoto kurzu.</span><span class="sxs-lookup"><span data-stu-id="8169e-132">If you're connecting to Azure Storage Table service, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="8169e-133">Připojovací řetězec můžete zkopírovat z portálu Azure.</span><span class="sxs-lookup"><span data-stu-id="8169e-133">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="8169e-134">Další informace o připojovacích řetězcích najdete v tématu [nakonfigurování připojovacích řetězců Storage](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="8169e-134">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

### <a name="get-your-azure-cosmos-db-connection-string"></a><span data-ttu-id="8169e-135">Získání připojovacího řetězce Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="8169e-135">Get your Azure Cosmos DB connection string</span></span>

<span data-ttu-id="8169e-136">Pokud se připojujete k databázi Cosmos Azure, budete potřebovat připojovací řetězec pro účely tohoto kurzu.</span><span class="sxs-lookup"><span data-stu-id="8169e-136">If you're connecting to Azure Cosmos DB, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="8169e-137">Připojovací řetězec můžete zkopírovat z portálu Azure.</span><span class="sxs-lookup"><span data-stu-id="8169e-137">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="8169e-138">Na portálu Azure v účtu Cosmos DB, přejděte na **nastavení** > **připojovací řetězec**a klikněte na tlačítko **kopie** tlačítko Kopírovat primární připojení Řetězec.</span><span class="sxs-lookup"><span data-stu-id="8169e-138">In the Azure portal, in your Cosmos DB account, go to **Settings** > **Connection String**, and click the **Copy** button to copy your Primary Connection String.</span></span> 

<span data-ttu-id="8169e-139">Pro tento kurz zadejte připojovací řetězec ve vašem skriptu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="8169e-139">For the tutorial, enter your connection string in your script, like the following example:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="8169e-140">Je to ale **nedoporučuje** skutečných projekty.</span><span class="sxs-lookup"><span data-stu-id="8169e-140">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="8169e-141">Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="8169e-141">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="8169e-142">Vždycky pečlivě k ochraně klíče účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="8169e-142">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="8169e-143">Nedávejte ho jiným uživatelům, nezakódovávejte ho nebo ho uložit v souboru formátu prostého textu, který je přístupný ostatním uživatelům.</span><span class="sxs-lookup"><span data-stu-id="8169e-143">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="8169e-144">Můžete znovu vygenerovat klíč pomocí portálu Azure, pokud se domníváte, že by může ohrožení.</span><span class="sxs-lookup"><span data-stu-id="8169e-144">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="8169e-145">Skutečných aplikace, je nejlepší způsob, jak udržovat připojovací řetězec úložiště v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="8169e-145">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="8169e-146">K načtení připojovacího řetězce z konfiguračního souboru, můžete to udělat:</span><span class="sxs-lookup"><span data-stu-id="8169e-146">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="8169e-147">Použití nástroje Azure Configuration Manager není povinné.</span><span class="sxs-lookup"><span data-stu-id="8169e-147">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="8169e-148">Můžete také použít API jako třeba rozhraní .NET Framework `ConfigurationManager` typu.</span><span class="sxs-lookup"><span data-stu-id="8169e-148">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="8169e-149">Analýza připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="8169e-149">Parse the connection string</span></span>

<span data-ttu-id="8169e-150">Chcete-li analyzovat připojovací řetězec, použijte:</span><span class="sxs-lookup"><span data-stu-id="8169e-150">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="8169e-151">Tento příkaz vrátí `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="8169e-151">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="8169e-152">Vytvoření klienta služby Table</span><span class="sxs-lookup"><span data-stu-id="8169e-152">Create the Table service client</span></span>

<span data-ttu-id="8169e-153">`CloudTableClient` Vám umožňuje načíst tabulky a entity ve službě Table storage.</span><span class="sxs-lookup"><span data-stu-id="8169e-153">The `CloudTableClient` class enables you to retrieve tables and entities in Table storage.</span></span> <span data-ttu-id="8169e-154">Tady je jeden způsob, jak vytvořit klienta služby:</span><span class="sxs-lookup"><span data-stu-id="8169e-154">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="8169e-155">Teď jste připravení psát kód, který načítá a zapisuje data do úložiště tabulek.</span><span class="sxs-lookup"><span data-stu-id="8169e-155">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

### <a name="create-a-table"></a><span data-ttu-id="8169e-156">Umožňuje vytvořit tabulku</span><span class="sxs-lookup"><span data-stu-id="8169e-156">Create a table</span></span>

<span data-ttu-id="8169e-157">Tento příklad ukazuje, jak vytvořit tabulku, pokud ještě neexistuje:</span><span class="sxs-lookup"><span data-stu-id="8169e-157">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a><span data-ttu-id="8169e-158">Přidání entity do tabulky</span><span class="sxs-lookup"><span data-stu-id="8169e-158">Add an entity to a table</span></span>

<span data-ttu-id="8169e-159">Entita musí mít typ, který dědí z `TableEntity`.</span><span class="sxs-lookup"><span data-stu-id="8169e-159">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="8169e-160">Můžete rozšířit `TableEntity` v jakýmkoli způsobem se vám líbí, ale typ vašeho *musí* mít konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="8169e-160">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="8169e-161">Pouze vlastnosti, které oba `get` a `set` jsou uložené v Azure Table.</span><span class="sxs-lookup"><span data-stu-id="8169e-161">Only properties that have both `get` and `set` are stored in your Azure Table.</span></span>

<span data-ttu-id="8169e-162">Klíč entity oddílu a řádku entity jednoznačně identifikují entitu v tabulce.</span><span class="sxs-lookup"><span data-stu-id="8169e-162">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="8169e-163">Entity se stejným klíčem oddílu můžete zadat dotaz rychleji než ty, které se různé klíče oddílů, ale používání různých klíčů oddílů umožňuje větší škálovatelnost paralelních operací.</span><span class="sxs-lookup"><span data-stu-id="8169e-163">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="8169e-164">Tady je příklad `Customer` používající `lastName` jako klíč oddílu a `firstName` jako klíč řádku.</span><span class="sxs-lookup"><span data-stu-id="8169e-164">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="8169e-165">Nyní přidejte `Customer` do tabulky.</span><span class="sxs-lookup"><span data-stu-id="8169e-165">Now add `Customer` to the table.</span></span> <span data-ttu-id="8169e-166">Chcete-li tak učinit, vytvořte `TableOperation` , která se spouští v tabulce.</span><span class="sxs-lookup"><span data-stu-id="8169e-166">To do so, create a `TableOperation` that executes on the table.</span></span> <span data-ttu-id="8169e-167">V tomto případě vytvoříte `Insert` operaci.</span><span class="sxs-lookup"><span data-stu-id="8169e-167">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a><span data-ttu-id="8169e-168">Vložení dávky entit</span><span class="sxs-lookup"><span data-stu-id="8169e-168">Insert a batch of entities</span></span>

<span data-ttu-id="8169e-169">Do tabulky pomocí jednoho zápisu operace můžete vložit dávku entit.</span><span class="sxs-lookup"><span data-stu-id="8169e-169">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="8169e-170">Dávkové operace umožňují kombinovat operací do jednoho spuštění, ale mají určitá omezení:</span><span class="sxs-lookup"><span data-stu-id="8169e-170">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="8169e-171">Můžete provádět aktualizace, odstranění a vložení v rámci jedné dávkové operace.</span><span class="sxs-lookup"><span data-stu-id="8169e-171">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="8169e-172">Dávková operace může obsahovat až 100 entit.</span><span class="sxs-lookup"><span data-stu-id="8169e-172">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="8169e-173">Všechny entity v rámci dávkové operace musí mít stejný klíč oddílu.</span><span class="sxs-lookup"><span data-stu-id="8169e-173">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="8169e-174">I když je možné provést dotaz v rámci dávkové operace, musí být ale jediná operace v dávce.</span><span class="sxs-lookup"><span data-stu-id="8169e-174">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="8169e-175">Zde je kód, který kombinuje dvě vloží do dávkové operace:</span><span class="sxs-lookup"><span data-stu-id="8169e-175">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="8169e-176">Načtení všech entit v oddílu</span><span class="sxs-lookup"><span data-stu-id="8169e-176">Retrieve all entities in a partition</span></span>

<span data-ttu-id="8169e-177">Dotaz na tabulku pro všechny entity v oddílu, použijte `TableQuery` objektu.</span><span class="sxs-lookup"><span data-stu-id="8169e-177">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="8169e-178">Zde můžete filtr pro entity kde "Smith" je klíč oddílu.</span><span class="sxs-lookup"><span data-stu-id="8169e-178">Here, you filter for entities where "Smith" is the partition key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

<span data-ttu-id="8169e-179">Nyní vytisknout výsledky:</span><span class="sxs-lookup"><span data-stu-id="8169e-179">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]


### <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="8169e-180">Načtení rozsahu entit v oddílu</span><span class="sxs-lookup"><span data-stu-id="8169e-180">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="8169e-181">Pokud nechcete, aby k dotazování všechny entity v oddílu, můžete zadat rozsah kombinací filtru klíče oddílu s filtrem klíče řádku.</span><span class="sxs-lookup"><span data-stu-id="8169e-181">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="8169e-182">Tady můžete použít dva filtry k získání všech entit v oddílu "Smith" kde klíč řádku (jméno) začíná písmenem starší než "M" abecedy.</span><span class="sxs-lookup"><span data-stu-id="8169e-182">Here, you use two filters to get all entities in the "Smith" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="8169e-183">Nyní vytisknout výsledky:</span><span class="sxs-lookup"><span data-stu-id="8169e-183">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a><span data-ttu-id="8169e-184">Načtení jedné entity</span><span class="sxs-lookup"><span data-stu-id="8169e-184">Retrieve a single entity</span></span>

<span data-ttu-id="8169e-185">Můžete napsat dotaz pro načtení jedné konkrétní entity.</span><span class="sxs-lookup"><span data-stu-id="8169e-185">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="8169e-186">Tady můžete použít `TableOperation` k určení zákazníka "Ben Smith".</span><span class="sxs-lookup"><span data-stu-id="8169e-186">Here, you use a `TableOperation` to specify the customer "Ben Smith".</span></span> <span data-ttu-id="8169e-187">Místo kolekce, můžete se vrátit `Customer`.</span><span class="sxs-lookup"><span data-stu-id="8169e-187">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="8169e-188">V dotazu zadat klíč oddílu a klíč řádku je nejrychlejší způsob, jak načíst jednu entitu ze služby Table.</span><span class="sxs-lookup"><span data-stu-id="8169e-188">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="8169e-189">Nyní vytisknout výsledky:</span><span class="sxs-lookup"><span data-stu-id="8169e-189">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]


### <a name="replace-an-entity"></a><span data-ttu-id="8169e-190">Nahrazení entity</span><span class="sxs-lookup"><span data-stu-id="8169e-190">Replace an entity</span></span>

<span data-ttu-id="8169e-191">Pokud chcete entitu aktualizovat, načtěte ji ze služby Table, upravte objekt entity a potom uložte změny zpět k tabulce služby pomocí `Replace` operaci.</span><span class="sxs-lookup"><span data-stu-id="8169e-191">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="8169e-192">To způsobí, že entita, která má být plně nahradí na serveru, pokud se entita na serveru se změnil od načtení, v takovém případě se operace nezdaří.</span><span class="sxs-lookup"><span data-stu-id="8169e-192">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation fails.</span></span> <span data-ttu-id="8169e-193">Je toto selhání zabrání vaší aplikaci v nechtěném přepsání změny z jiných zdrojů.</span><span class="sxs-lookup"><span data-stu-id="8169e-193">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a><span data-ttu-id="8169e-194">Vložení nebo nahrazení entity</span><span class="sxs-lookup"><span data-stu-id="8169e-194">Insert-or-replace an entity</span></span>

<span data-ttu-id="8169e-195">V některých případech nevíte, zda entita existuje v tabulce.</span><span class="sxs-lookup"><span data-stu-id="8169e-195">Sometimes, you don't know whether an entity exists in the table.</span></span> <span data-ttu-id="8169e-196">A pokud ano, aktuální hodnoty v ní uloženy už nejsou potřeba.</span><span class="sxs-lookup"><span data-stu-id="8169e-196">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="8169e-197">Můžete použít `InsertOrReplace` vytvořit entitu, nebo ho nahradit, pokud existuje, bez ohledu na jeho stav.</span><span class="sxs-lookup"><span data-stu-id="8169e-197">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="8169e-198">Dotaz na podmnožinu vlastností entity</span><span class="sxs-lookup"><span data-stu-id="8169e-198">Query a subset of entity properties</span></span>

<span data-ttu-id="8169e-199">Dotaz na tabulku můžete načíst jenom několik z entity, místo všechny z nich.</span><span class="sxs-lookup"><span data-stu-id="8169e-199">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="8169e-200">Tento postup volá projekce, může zlepšit výkon dotazů, hlavně pro velké entity.</span><span class="sxs-lookup"><span data-stu-id="8169e-200">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="8169e-201">Zde můžete vrátit pouze e-mailových adres, pomocí `DynamicTableEntity` a `EntityResolver`.</span><span class="sxs-lookup"><span data-stu-id="8169e-201">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="8169e-202">Všimněte si, že projekci nepodporuje emulátor místního úložiště, takže tento kód spustí pouze v případě, že používáte účet služby Table.</span><span class="sxs-lookup"><span data-stu-id="8169e-202">Note that projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="8169e-203">Načtení entit na stránkách asynchronně</span><span class="sxs-lookup"><span data-stu-id="8169e-203">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="8169e-204">Pokud načítáte velký počet entit a chcete je zpracovat, protože jsou načítány místo čekání mají všechny vrátí, můžete použít segmentovaného dotazu.</span><span class="sxs-lookup"><span data-stu-id="8169e-204">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="8169e-205">Zde vracet výsledky na stránkách pomocí pracovním postupu asynchronní tak, aby provádění není blokován, zatímco čekáte pro velké sady výsledků vrátit.</span><span class="sxs-lookup"><span data-stu-id="8169e-205">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

<span data-ttu-id="8169e-206">Je teď spustit tento výpočet synchronně:</span><span class="sxs-lookup"><span data-stu-id="8169e-206">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a><span data-ttu-id="8169e-207">Odstranění entity</span><span class="sxs-lookup"><span data-stu-id="8169e-207">Delete an entity</span></span>

<span data-ttu-id="8169e-208">Entitu můžete po jejím načtení odstranit.</span><span class="sxs-lookup"><span data-stu-id="8169e-208">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="8169e-209">Stejně jako u aktualizaci entity se to nezdaří, pokud entity došlo ke změně vzhledem k tomu, že jste jej získali.</span><span class="sxs-lookup"><span data-stu-id="8169e-209">As with updating an entity, this fails if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a><span data-ttu-id="8169e-210">Odstranění tabulky</span><span class="sxs-lookup"><span data-stu-id="8169e-210">Delete a table</span></span>

<span data-ttu-id="8169e-211">Odstranit tabulku z účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="8169e-211">You can delete a table from a storage account.</span></span> <span data-ttu-id="8169e-212">Tabulka, která byla odstraněna není k dispozici pro určitou dobu po odstranění byla znovu vytvořena.</span><span class="sxs-lookup"><span data-stu-id="8169e-212">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a><span data-ttu-id="8169e-213">Další kroky</span><span class="sxs-lookup"><span data-stu-id="8169e-213">Next steps</span></span>

<span data-ttu-id="8169e-214">Teď, když jste se naučili základy používání služby Table storage, postupujte podle následujících odkazech na další informace o složitějších úlohách úložiště a rozhraní API služby Azure DB Cosmos tabulky.</span><span class="sxs-lookup"><span data-stu-id="8169e-214">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks and the Azure Cosmos DB Table API.</span></span>

- [<span data-ttu-id="8169e-215">Úvod do Azure Cosmos DB tabulky API</span><span class="sxs-lookup"><span data-stu-id="8169e-215">Introduction to Azure Cosmos DB Table API</span></span>](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [<span data-ttu-id="8169e-216">Klientská knihovna pro úložiště pro .NET – referenční informace</span><span class="sxs-lookup"><span data-stu-id="8169e-216">Storage Client Library for .NET reference</span></span>](https://docs.microsoft.com/dotnet/api/overview/azure/storage?view=azure-dotnet)
- [<span data-ttu-id="8169e-217">Typ zprostředkovatele úložiště Azure</span><span class="sxs-lookup"><span data-stu-id="8169e-217">Azure Storage Type Provider</span></span>](http://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="8169e-218">Blog týmu Azure Storage</span><span class="sxs-lookup"><span data-stu-id="8169e-218">Azure Storage Team Blog</span></span>](http://blogs.msdn.com/b/windowsazurestorage/)
- [<span data-ttu-id="8169e-219">Konfigurace připojovacích řetězců</span><span class="sxs-lookup"><span data-stu-id="8169e-219">Configuring Connection Strings</span></span>](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="8169e-220">Začínáme s Azure Table Storage v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="8169e-220">Getting Started with Azure Table Storage in .NET</span></span>](https://azure.microsoft.com/resources/samples/storage-table-dotnet-getting-started/)
