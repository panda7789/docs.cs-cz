---
title: Začínáme se službou Azure Table Storage s využitím F#
description: Ukládání strukturovaných dat v cloudu pomocí služby Azure Table Storage nebo Azure Cosmos DB.
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: 23f5e40e1d9b3d5a0ee27d675362930ef86e90c5
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935590"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a><span data-ttu-id="26466-103">Začínáme s Azure Table Storage a Azure Cosmos DB rozhraní API pro tabulky pomocí F\#</span><span class="sxs-lookup"><span data-stu-id="26466-103">Get started with Azure Table storage and the Azure Cosmos DB Table API using F\#</span></span>

<span data-ttu-id="26466-104">Azure Table Storage je služba, která ukládá strukturovaná data typu NoSQL v cloudu.</span><span class="sxs-lookup"><span data-stu-id="26466-104">Azure Table storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="26466-105">Table Storage je úložiště klíčů/atributů s návrhem bez schématu.</span><span class="sxs-lookup"><span data-stu-id="26466-105">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="26466-106">Vzhledem k tomu, že je Table Storage bez schématu, je snadné data přizpůsobovat měnícím se potřebám vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="26466-106">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="26466-107">Přístup k datům je rychlý a nákladově efektivní pro všechny typy aplikací.</span><span class="sxs-lookup"><span data-stu-id="26466-107">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="26466-108">Využívání úložiště Table Storage obvykle znamená výrazně nižší náklady než tradiční SQL pro podobné objemy dat.</span><span class="sxs-lookup"><span data-stu-id="26466-108">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="26466-109">Úložiště Table Storage můžete používat k ukládání flexibilních datových sad, například uživatelských dat pro webové aplikace, adresářů, informací o zařízení a dalších typů metadat, které vaše služba vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="26466-109">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="26466-110">V tabulce můžete uložit libovolný počet entit a účet úložiště může obsahovat libovolný počet tabulek, až do limitu kapacity účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="26466-110">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

<span data-ttu-id="26466-111">Azure Cosmos DB poskytuje rozhraní API pro tabulky pro aplikace napsané pro službu Azure Table Storage, které vyžadují prémiové funkce, jako například:</span><span class="sxs-lookup"><span data-stu-id="26466-111">Azure Cosmos DB provides the Table API for applications that are written for Azure Table storage and that require premium capabilities such as:</span></span>

- <span data-ttu-id="26466-112">Globální distribuci na klíč</span><span class="sxs-lookup"><span data-stu-id="26466-112">Turnkey global distribution.</span></span>
- <span data-ttu-id="26466-113">Vyhrazená propustnost po celém světě.</span><span class="sxs-lookup"><span data-stu-id="26466-113">Dedicated throughput worldwide.</span></span>
- <span data-ttu-id="26466-114">Latence v řádu milisekund na 99. percentilu.</span><span class="sxs-lookup"><span data-stu-id="26466-114">Single-digit millisecond latencies at the 99th percentile.</span></span>
- <span data-ttu-id="26466-115">Záruka vysoké dostupnosti.</span><span class="sxs-lookup"><span data-stu-id="26466-115">Guaranteed high availability.</span></span>
- <span data-ttu-id="26466-116">Automatické sekundární indexování.</span><span class="sxs-lookup"><span data-stu-id="26466-116">Automatic secondary indexing.</span></span>

<span data-ttu-id="26466-117">Pomocí rozhraní API tabulky je možné migrovat aplikace napsané pro Azure Table Storage beze změn kódu na službu Azure Cosmos DB a využít tak prémiové funkce.</span><span class="sxs-lookup"><span data-stu-id="26466-117">Applications written for Azure Table storage can migrate to Azure Cosmos DB by using the Table API with no code changes and take advantage of premium capabilities.</span></span> <span data-ttu-id="26466-118">Rozhraní API tabulky má klientské sady SDK dostupné pro .NET, Java, Python a Node.js.</span><span class="sxs-lookup"><span data-stu-id="26466-118">The Table API has client SDKs available for .NET, Java, Python, and Node.js.</span></span>

<span data-ttu-id="26466-119">Další informace najdete v tématu [Úvod do Azure Cosmos DB rozhraní API pro tabulky](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span><span class="sxs-lookup"><span data-stu-id="26466-119">For more information, see [Introduction to Azure Cosmos DB Table API](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span></span>

## <a name="about-this-tutorial"></a><span data-ttu-id="26466-120">O tomto kurzu</span><span class="sxs-lookup"><span data-stu-id="26466-120">About this tutorial</span></span>

<span data-ttu-id="26466-121">V tomto kurzu se dozvíte F# , jak napsat kód, který provede některé běžné úlohy pomocí služby Azure Table storage nebo Azure Cosmos DB rozhraní API pro tabulky, včetně vytváření a odstraňování tabulky a vkládání, aktualizace, odstraňování a dotazování na data tabulky.</span><span class="sxs-lookup"><span data-stu-id="26466-121">This tutorial shows how to write F# code to do some common tasks using Azure Table storage or the Azure Cosmos DB Table API, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="26466-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="26466-122">Prerequisites</span></span>

<span data-ttu-id="26466-123">Pokud chcete použít tuto příručku, musíte nejdřív [vytvořit účet služby Azure Storage](/azure/storage/storage-create-storage-account) nebo [účet Azure Cosmos DB](https://azure.microsoft.com/try/cosmosdb/).</span><span class="sxs-lookup"><span data-stu-id="26466-123">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account) or [Azure Cosmos DB account](https://azure.microsoft.com/try/cosmosdb/).</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="26466-124">Vytvoření F# skriptu a spuštění F# Interactive</span><span class="sxs-lookup"><span data-stu-id="26466-124">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="26466-125">Ukázky v tomto článku se dají použít buď v F# aplikaci, nebo ve F# skriptu.</span><span class="sxs-lookup"><span data-stu-id="26466-125">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="26466-126">Chcete-li F# vytvořit skript, vytvořte soubor s příponou `.fsx`, například `tables.fsx`ve vašem F# vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="26466-126">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="26466-127">V dalším kroku pomocí [Správce balíčků](package-management.md) , jako je [paket](https://fsprojects.github.io/Paket/) nebo [NuGet](https://www.nuget.org/) , nainstalujte balíček `WindowsAzure.Storage` a odkaz `WindowsAzure.Storage.dll` ve vašem skriptu pomocí direktivy `#r`.</span><span class="sxs-lookup"><span data-stu-id="26466-127">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="26466-128">Udělejte to znovu pro `Microsoft.WindowsAzure.ConfigurationManager`, abyste získali obor názvů Microsoft. Azure.</span><span class="sxs-lookup"><span data-stu-id="26466-128">Do it again for `Microsoft.WindowsAzure.ConfigurationManager` in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="26466-129">Přidání deklarací oboru názvů</span><span class="sxs-lookup"><span data-stu-id="26466-129">Add namespace declarations</span></span>

<span data-ttu-id="26466-130">Přidejte do horní části souboru `tables.fsx` následující příkazy `open`:</span><span class="sxs-lookup"><span data-stu-id="26466-130">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a><span data-ttu-id="26466-131">Získání připojovacího řetězce Azure Storage</span><span class="sxs-lookup"><span data-stu-id="26466-131">Get your Azure Storage connection string</span></span>

<span data-ttu-id="26466-132">Pokud se připojujete k Azure Storage Table service, budete pro tento kurz potřebovat připojovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="26466-132">If you're connecting to Azure Storage Table service, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="26466-133">Připojovací řetězec můžete zkopírovat z Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="26466-133">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="26466-134">Další informace o připojovacích řetězcích najdete v tématu [Konfigurace připojovacích řetězců úložiště](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="26466-134">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

### <a name="get-your-azure-cosmos-db-connection-string"></a><span data-ttu-id="26466-135">Získání připojovacího řetězce Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="26466-135">Get your Azure Cosmos DB connection string</span></span>

<span data-ttu-id="26466-136">Pokud se připojujete k Azure Cosmos DB, budete pro tento kurz potřebovat připojovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="26466-136">If you're connecting to Azure Cosmos DB, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="26466-137">Připojovací řetězec můžete zkopírovat z Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="26466-137">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="26466-138">V Azure Portal v účtu Cosmos DB přejděte na **nastavení** > **připojovací řetězec**a kliknutím na tlačítko **Kopírovat** zkopírujte primární připojovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="26466-138">In the Azure portal, in your Cosmos DB account, go to **Settings** > **Connection String**, and click the **Copy** button to copy your Primary Connection String.</span></span>

<span data-ttu-id="26466-139">V tomto kurzu do skriptu zadejte připojovací řetězec, podobně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="26466-139">For the tutorial, enter your connection string in your script, like the following example:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="26466-140">To však **nedoporučujeme** pro skutečné projekty.</span><span class="sxs-lookup"><span data-stu-id="26466-140">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="26466-141">Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="26466-141">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="26466-142">Vždy klíč účtu úložiště pečlivě chraňte.</span><span class="sxs-lookup"><span data-stu-id="26466-142">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="26466-143">Nedávejte ho jiným uživatelům, nezakódovávejte ho ani ho neukládejte do souboru ve formátu prostého textu, který je přístupný ostatním uživatelům.</span><span class="sxs-lookup"><span data-stu-id="26466-143">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="26466-144">Klíč můžete znovu vygenerovat pomocí webu Azure Portal, pokud se domníváte, že je možné, že došlo k ohrožení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="26466-144">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="26466-145">Pro reálné aplikace je nejlepší způsob, jak udržovat připojovací řetězec úložiště, v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="26466-145">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="26466-146">Chcete-li načíst připojovací řetězec z konfiguračního souboru, můžete to provést:</span><span class="sxs-lookup"><span data-stu-id="26466-146">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="26466-147">Použití nástroje Azure Configuration Manager není povinné.</span><span class="sxs-lookup"><span data-stu-id="26466-147">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="26466-148">Můžete také použít rozhraní API, jako je například typ `ConfigurationManager` .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="26466-148">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="26466-149">Analýza připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="26466-149">Parse the connection string</span></span>

<span data-ttu-id="26466-150">K analýze připojovacího řetězce použijte:</span><span class="sxs-lookup"><span data-stu-id="26466-150">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="26466-151">Vrátí `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="26466-151">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="26466-152">Vytvoření klienta služby Table service</span><span class="sxs-lookup"><span data-stu-id="26466-152">Create the Table service client</span></span>

<span data-ttu-id="26466-153">Třída `CloudTableClient` umožňuje načíst tabulky a entity v úložišti tabulek.</span><span class="sxs-lookup"><span data-stu-id="26466-153">The `CloudTableClient` class enables you to retrieve tables and entities in Table storage.</span></span> <span data-ttu-id="26466-154">Tady je jeden ze způsobů, jak vytvořit klienta služby:</span><span class="sxs-lookup"><span data-stu-id="26466-154">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="26466-155">Teď můžete napsat kód, který bude číst data z Table Storage a bude je tam také zapisovat.</span><span class="sxs-lookup"><span data-stu-id="26466-155">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

### <a name="create-a-table"></a><span data-ttu-id="26466-156">Vytvoření tabulky</span><span class="sxs-lookup"><span data-stu-id="26466-156">Create a table</span></span>

<span data-ttu-id="26466-157">Tento příklad ukazuje, jak vytvořit tabulku, pokud ještě neexistuje:</span><span class="sxs-lookup"><span data-stu-id="26466-157">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a><span data-ttu-id="26466-158">Přidání entity do tabulky</span><span class="sxs-lookup"><span data-stu-id="26466-158">Add an entity to a table</span></span>

<span data-ttu-id="26466-159">Entita musí mít typ, který dědí z `TableEntity`.</span><span class="sxs-lookup"><span data-stu-id="26466-159">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="26466-160">`TableEntity` můžete roztáhnout jakýmkoli způsobem, ale váš typ *musí* mít konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="26466-160">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="26466-161">V tabulce Azure jsou uloženy pouze vlastnosti `get` i `set`.</span><span class="sxs-lookup"><span data-stu-id="26466-161">Only properties that have both `get` and `set` are stored in your Azure Table.</span></span>

<span data-ttu-id="26466-162">Klíč oddílu a řádku entity jednoznačně identifikují entitu v tabulce.</span><span class="sxs-lookup"><span data-stu-id="26466-162">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="26466-163">Na entity se stejným klíčem oddílu je možné se (v porovnání s těmi, které mají různé klíče oddílů) rychleji dotazovat, ale používání různých klíčů oddílů umožňuje větší škálovatelnost paralelních operací.</span><span class="sxs-lookup"><span data-stu-id="26466-163">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="26466-164">Tady je příklad `Customer`, který používá `lastName` jako klíč oddílu a `firstName` jako klíč řádku.</span><span class="sxs-lookup"><span data-stu-id="26466-164">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="26466-165">Nyní do tabulky přidejte `Customer`.</span><span class="sxs-lookup"><span data-stu-id="26466-165">Now add `Customer` to the table.</span></span> <span data-ttu-id="26466-166">Provedete to tak, že vytvoříte `TableOperation`, která se spustí v tabulce.</span><span class="sxs-lookup"><span data-stu-id="26466-166">To do so, create a `TableOperation` that executes on the table.</span></span> <span data-ttu-id="26466-167">V tomto případě vytvoříte operaci `Insert`.</span><span class="sxs-lookup"><span data-stu-id="26466-167">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a><span data-ttu-id="26466-168">Vložení dávky entit</span><span class="sxs-lookup"><span data-stu-id="26466-168">Insert a batch of entities</span></span>

<span data-ttu-id="26466-169">Do tabulky můžete vložit dávku entit pomocí jediné operace zápisu.</span><span class="sxs-lookup"><span data-stu-id="26466-169">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="26466-170">Dávkové operace umožňují kombinovat operace do jednoho spuštění, ale mají určitá omezení:</span><span class="sxs-lookup"><span data-stu-id="26466-170">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="26466-171">V rámci stejné dávkové operace můžete provádět aktualizace, odstraňování a vkládání.</span><span class="sxs-lookup"><span data-stu-id="26466-171">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="26466-172">Dávková operace může zahrnovat až 100 entit.</span><span class="sxs-lookup"><span data-stu-id="26466-172">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="26466-173">Všechny entity v dávkové operaci musí mít stejný klíč oddílu.</span><span class="sxs-lookup"><span data-stu-id="26466-173">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="26466-174">I když je možné provést dotaz v dávkové operaci, musí být jedinou operací v dávce.</span><span class="sxs-lookup"><span data-stu-id="26466-174">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="26466-175">Zde je nějaký kód, který kombinuje dvě vložení do dávkové operace:</span><span class="sxs-lookup"><span data-stu-id="26466-175">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="26466-176">Načtení všech entit v oddílu</span><span class="sxs-lookup"><span data-stu-id="26466-176">Retrieve all entities in a partition</span></span>

<span data-ttu-id="26466-177">Chcete-li zadat dotaz na tabulku pro všechny entity v oddílu, použijte objekt `TableQuery`.</span><span class="sxs-lookup"><span data-stu-id="26466-177">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="26466-178">Tady můžete filtrovat entity, kde "Smith" je klíč oddílu.</span><span class="sxs-lookup"><span data-stu-id="26466-178">Here, you filter for entities where "Smith" is the partition key.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

<span data-ttu-id="26466-179">Nyní se tisknou výsledky:</span><span class="sxs-lookup"><span data-stu-id="26466-179">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]

### <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="26466-180">Načtení rozsahu entit v oddílu</span><span class="sxs-lookup"><span data-stu-id="26466-180">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="26466-181">Pokud nechcete, aby se zadával dotaz na všechny entity v oddílu, můžete zadat rozsah nakombinováním filtru klíče oddílu s filtrem klíče řádku.</span><span class="sxs-lookup"><span data-stu-id="26466-181">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="26466-182">Tady použijete dva filtry k získání všech entit v oddílu "Smith", kde klíč řádku (jméno) začíná písmenem "M" v abecedě.</span><span class="sxs-lookup"><span data-stu-id="26466-182">Here, you use two filters to get all entities in the "Smith" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="26466-183">Nyní se tisknou výsledky:</span><span class="sxs-lookup"><span data-stu-id="26466-183">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a><span data-ttu-id="26466-184">Načtení jedné entity</span><span class="sxs-lookup"><span data-stu-id="26466-184">Retrieve a single entity</span></span>

<span data-ttu-id="26466-185">Můžete napsat dotaz pro načtení jedné konkrétní entity.</span><span class="sxs-lookup"><span data-stu-id="26466-185">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="26466-186">Tady můžete pomocí `TableOperation` zadat zákazníka "Robert Smith".</span><span class="sxs-lookup"><span data-stu-id="26466-186">Here, you use a `TableOperation` to specify the customer "Ben Smith".</span></span> <span data-ttu-id="26466-187">Místo kolekce se vrátí `Customer`.</span><span class="sxs-lookup"><span data-stu-id="26466-187">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="26466-188">Zadání klíče oddílu a klíče řádku v dotazu představuje nejrychlejší způsob, jak z Table service načíst jednu entitu.</span><span class="sxs-lookup"><span data-stu-id="26466-188">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="26466-189">Nyní se tisknou výsledky:</span><span class="sxs-lookup"><span data-stu-id="26466-189">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]

### <a name="replace-an-entity"></a><span data-ttu-id="26466-190">Nahrazení entity</span><span class="sxs-lookup"><span data-stu-id="26466-190">Replace an entity</span></span>

<span data-ttu-id="26466-191">Chcete-li aktualizovat entitu, načtěte ji z Table service, upravte objekt entity a uložte změny zpět do Table service pomocí operace `Replace`.</span><span class="sxs-lookup"><span data-stu-id="26466-191">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="26466-192">Tím dojde k tomu, že se entita na serveru úplně nahradí, pokud se entita na serveru od načtení nezměnila, a v takovém případě se operace nezdařila.</span><span class="sxs-lookup"><span data-stu-id="26466-192">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation fails.</span></span> <span data-ttu-id="26466-193">Tato chyba je zabránit tomu, aby aplikace nechtěně přepsala změny z jiných zdrojů.</span><span class="sxs-lookup"><span data-stu-id="26466-193">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a><span data-ttu-id="26466-194">Vložení nebo nahrazení entity</span><span class="sxs-lookup"><span data-stu-id="26466-194">Insert-or-replace an entity</span></span>

<span data-ttu-id="26466-195">V některých případech nevíte, zda entita v tabulce existuje.</span><span class="sxs-lookup"><span data-stu-id="26466-195">Sometimes, you don't know whether an entity exists in the table.</span></span> <span data-ttu-id="26466-196">A pokud k tomu dojde, aktuální hodnoty, které jsou v něm uložené, už nejsou potřeba.</span><span class="sxs-lookup"><span data-stu-id="26466-196">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="26466-197">Pomocí `InsertOrReplace` můžete vytvořit entitu, nebo ji nahradit, pokud existuje, bez ohledu na její stav.</span><span class="sxs-lookup"><span data-stu-id="26466-197">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="26466-198">Dotaz na podmnožinu vlastností entity</span><span class="sxs-lookup"><span data-stu-id="26466-198">Query a subset of entity properties</span></span>

<span data-ttu-id="26466-199">Dotaz na tabulku může načíst jenom několik vlastností z entity místo všech.</span><span class="sxs-lookup"><span data-stu-id="26466-199">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="26466-200">Tato technika s názvem projekce může zlepšit výkon dotazů, zejména u velkých entit.</span><span class="sxs-lookup"><span data-stu-id="26466-200">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="26466-201">Tady vrátíte jenom e-mailové adresy, které používají `DynamicTableEntity` a `EntityResolver`.</span><span class="sxs-lookup"><span data-stu-id="26466-201">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="26466-202">Poznámka: Projekci nepodporuje emulátor místního úložiště, takže tento kód bude možné spustit pouze v případě, že používáte účet služby Table service.</span><span class="sxs-lookup"><span data-stu-id="26466-202">Note that projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="26466-203">Asynchronní načítání entit na stránkách</span><span class="sxs-lookup"><span data-stu-id="26466-203">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="26466-204">Pokud čtete velký počet entit a chcete je zpracovat tak, jak jsou načteny, aniž byste čekali na jejich vrácení, můžete použít segmentický dotaz.</span><span class="sxs-lookup"><span data-stu-id="26466-204">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="26466-205">Tady vrátíte výsledky na stránkách pomocí asynchronního pracovního postupu, aby se při čekání na vrácení velké sady výsledků neblokovalo provádění.</span><span class="sxs-lookup"><span data-stu-id="26466-205">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

<span data-ttu-id="26466-206">Tento výpočet teď spustíte synchronně:</span><span class="sxs-lookup"><span data-stu-id="26466-206">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a><span data-ttu-id="26466-207">Odstranění entity</span><span class="sxs-lookup"><span data-stu-id="26466-207">Delete an entity</span></span>

<span data-ttu-id="26466-208">Entitu můžete po načtení odstranit.</span><span class="sxs-lookup"><span data-stu-id="26466-208">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="26466-209">Stejně jako u aktualizace entity se to nepovede, pokud se entita od jejího načtení změnila.</span><span class="sxs-lookup"><span data-stu-id="26466-209">As with updating an entity, this fails if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a><span data-ttu-id="26466-210">Odstranění tabulky</span><span class="sxs-lookup"><span data-stu-id="26466-210">Delete a table</span></span>

<span data-ttu-id="26466-211">Tabulku můžete odstranit z účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="26466-211">You can delete a table from a storage account.</span></span> <span data-ttu-id="26466-212">Tabulku, která byla odstraněna, nebude možné po odstranění nějakou dobu znovu vytvořit.</span><span class="sxs-lookup"><span data-stu-id="26466-212">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a><span data-ttu-id="26466-213">Další kroky</span><span class="sxs-lookup"><span data-stu-id="26466-213">Next steps</span></span>

<span data-ttu-id="26466-214">Teď, když jste se seznámili se základy úložiště tabulek, postupujte podle těchto odkazů a získejte další informace o složitějších úlohách úložiště a Azure Cosmos DB rozhraní API pro tabulky.</span><span class="sxs-lookup"><span data-stu-id="26466-214">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks and the Azure Cosmos DB Table API.</span></span>

- [<span data-ttu-id="26466-215">Úvod do rozhraní Table API služby Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="26466-215">Introduction to Azure Cosmos DB Table API</span></span>](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [<span data-ttu-id="26466-216">Klientská knihovna Storage pro .NET – referenční informace</span><span class="sxs-lookup"><span data-stu-id="26466-216">Storage Client Library for .NET reference</span></span>](https://docs.microsoft.com/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="26466-217">Poskytovatel typu Azure Storage</span><span class="sxs-lookup"><span data-stu-id="26466-217">Azure Storage Type Provider</span></span>](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="26466-218">Blog týmu Azure Storage</span><span class="sxs-lookup"><span data-stu-id="26466-218">Azure Storage Team Blog</span></span>](https://docs.microsoft.com/archive/blogs/windowsazurestorage/)
- [<span data-ttu-id="26466-219">Konfigurace připojovacích řetězců</span><span class="sxs-lookup"><span data-stu-id="26466-219">Configuring Connection Strings</span></span>](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
