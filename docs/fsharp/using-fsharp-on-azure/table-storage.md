---
title: "Začínáme s Azure Table storage pomocí F #"
description: "Ukládejte si strukturovaná data v cloudu pomocí Azure Table storage, úložiště dat typu NoSQL."
keywords: "Visual f #, f #, funkční programování, .NET, .NET Core, Azure"
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9e5d6cea-a98c-461e-a5cc-75f1d154eafd
ms.openlocfilehash: 905374a60261b0c2a863edb956943d41ae80f04d
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2018
---
# <a name="get-started-with-azure-table-storage-using-f"></a><span data-ttu-id="75d26-104">Začínáme s Azure Table storage pomocí F #</span><span class="sxs-lookup"><span data-stu-id="75d26-104">Get started with Azure Table storage using F#</span></span> #

<span data-ttu-id="75d26-105">Azure Table storage je služba, která ukládá strukturovaná data typu NoSQL v cloudu.</span><span class="sxs-lookup"><span data-stu-id="75d26-105">Azure Table storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="75d26-106">Úložiště Table je úložiště klíčů/atributů s návrhem.</span><span class="sxs-lookup"><span data-stu-id="75d26-106">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="75d26-107">Protože úložiště Table nemá schéma, je snadné data přizpůsobovat potřebám vaší aplikace měnícím.</span><span class="sxs-lookup"><span data-stu-id="75d26-107">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="75d26-108">Přístup k datům je rychlý a nákladově efektivní pro všechny typy aplikací.</span><span class="sxs-lookup"><span data-stu-id="75d26-108">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="75d26-109">Table storage je obvykle znamená výrazně nižší náklady než tradiční SQL pro podobné objemy dat.</span><span class="sxs-lookup"><span data-stu-id="75d26-109">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="75d26-110">Úložiště tabulek můžete použít k ukládání flexibilních datových sad, například uživatelských dat pro webové aplikace, adresáře, informace o zařízení a jiný typ metadat, které vaše služba vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="75d26-110">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="75d26-111">V tabulce můžete uložit libovolný počet entit a účet úložiště může obsahovat libovolný počet tabulek, až do limitu kapacity účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="75d26-111">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

### <a name="about-this-tutorial"></a><span data-ttu-id="75d26-112">O tomto kurzu</span><span class="sxs-lookup"><span data-stu-id="75d26-112">About this tutorial</span></span>

<span data-ttu-id="75d26-113">Tento kurz ukazuje, jak napsat kód F # pro provést některé běžné úlohy pomocí Azure Table storage, včetně vytváření a odstraňování tabulek a vkládání, aktualizaci, odstranění a dotazování dat v tabulce.</span><span class="sxs-lookup"><span data-stu-id="75d26-113">This tutorial shows how to write F# code to do some common tasks using Azure Table storage, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

<span data-ttu-id="75d26-114">Koncepční přehled služby table storage, najdete v tématu [v příručce .NET pro úložiště tabulek](/azure/storage/storage-dotnet-how-to-use-tables)</span><span class="sxs-lookup"><span data-stu-id="75d26-114">For a conceptual overview of table storage, please see [the .NET guide for table storage](/azure/storage/storage-dotnet-how-to-use-tables)</span></span>

## <a name="prerequisites"></a><span data-ttu-id="75d26-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="75d26-115">Prerequisites</span></span>

<span data-ttu-id="75d26-116">Chcete-li tohoto průvodce použijte, je nutné nejprve [vytvořit účet úložiště Azure](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="75d26-116">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="75d26-117">Budete také potřebovat přístupový klíč k úložišti pro tento účet.</span><span class="sxs-lookup"><span data-stu-id="75d26-117">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="75d26-118">Vytvoření F # skript a spusťte F # interaktivní</span><span class="sxs-lookup"><span data-stu-id="75d26-118">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="75d26-119">Ukázky v tomto článku slouží v aplikaci F # nebo skriptu F #.</span><span class="sxs-lookup"><span data-stu-id="75d26-119">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="75d26-120">Chcete-li vytvořit skript F #, vytvořte soubor s `.fsx` příponu, třeba `tables.fsx`, ve vašem vývojovém prostředí F #.</span><span class="sxs-lookup"><span data-stu-id="75d26-120">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="75d26-121">Pak pomocí [Správce balíčků](package-management.md) například [Stáhnout](https://fsprojects.github.io/Paket/) nebo [NuGet](https://www.nuget.org/) k instalaci `WindowsAzure.Storage` balíčku a referenční dokumentace `WindowsAzure.Storage.dll` ve vašem skriptu, použití `#r`– direktiva.</span><span class="sxs-lookup"><span data-stu-id="75d26-121">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="75d26-122">Proveďte ho znovu 'Microsoft.WindowsAzure.ConfigurationManager' za účelem získání Microsoft.Azure oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="75d26-122">Do it again for \`Microsoft.WindowsAzure.ConfigurationManager' in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="75d26-123">Přidání deklarace oborů názvů</span><span class="sxs-lookup"><span data-stu-id="75d26-123">Add namespace declarations</span></span>

<span data-ttu-id="75d26-124">Přidejte následující `open` příkazů do horní části `tables.fsx` souboru:</span><span class="sxs-lookup"><span data-stu-id="75d26-124">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="75d26-125">Získat připojovací řetězec</span><span class="sxs-lookup"><span data-stu-id="75d26-125">Get your connection string</span></span>

<span data-ttu-id="75d26-126">Pro účely tohoto kurzu budete potřebovat připojovací řetězec službě Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="75d26-126">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="75d26-127">Další informace o připojovacích řetězcích najdete v tématu [nakonfigurování připojovacích řetězců Storage](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="75d26-127">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="75d26-128">Pro tento kurz zadáte připojovacího řetězce ve vašem skriptu, například takto:</span><span class="sxs-lookup"><span data-stu-id="75d26-128">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="75d26-129">Je to ale **nedoporučuje** skutečných projekty.</span><span class="sxs-lookup"><span data-stu-id="75d26-129">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="75d26-130">Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="75d26-130">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="75d26-131">Vždycky pečlivě k ochraně klíče účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="75d26-131">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="75d26-132">Nedávejte ho jiným uživatelům, nezakódovávejte ho nebo ho uložit v souboru formátu prostého textu, který je přístupný ostatním uživatelům.</span><span class="sxs-lookup"><span data-stu-id="75d26-132">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="75d26-133">Můžete znovu vygenerovat klíč pomocí portálu Azure, pokud se domníváte, že by může ohrožení.</span><span class="sxs-lookup"><span data-stu-id="75d26-133">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="75d26-134">Skutečných aplikace, je nejlepší způsob, jak udržovat připojovací řetězec úložiště v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="75d26-134">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="75d26-135">K načtení připojovacího řetězce z konfiguračního souboru, můžete to udělat:</span><span class="sxs-lookup"><span data-stu-id="75d26-135">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="75d26-136">Použití nástroje Azure Configuration Manager není povinné.</span><span class="sxs-lookup"><span data-stu-id="75d26-136">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="75d26-137">Můžete také použít API jako třeba rozhraní .NET Framework `ConfigurationManager` typu.</span><span class="sxs-lookup"><span data-stu-id="75d26-137">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="75d26-138">Analýza připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="75d26-138">Parse the connection string</span></span>

<span data-ttu-id="75d26-139">Chcete-li analyzovat připojovací řetězec, použijte:</span><span class="sxs-lookup"><span data-stu-id="75d26-139">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="75d26-140">Tato možnost vrátí `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="75d26-140">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="75d26-141">Vytvoření klienta služby Table</span><span class="sxs-lookup"><span data-stu-id="75d26-141">Create the Table service client</span></span>

<span data-ttu-id="75d26-142">`CloudTableClient` Vám umožňuje načíst tabulky a entity, které jsou uložené ve službě Table storage.</span><span class="sxs-lookup"><span data-stu-id="75d26-142">The `CloudTableClient` class enables you to retrieve tables and entities stored in Table storage.</span></span> <span data-ttu-id="75d26-143">Tady je jeden způsob, jak vytvořit klienta služby:</span><span class="sxs-lookup"><span data-stu-id="75d26-143">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="75d26-144">Teď jste připravení psát kód, který načítá a zapisuje data do úložiště tabulek.</span><span class="sxs-lookup"><span data-stu-id="75d26-144">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

## <a name="create-a-table"></a><span data-ttu-id="75d26-145">Umožňuje vytvořit tabulku</span><span class="sxs-lookup"><span data-stu-id="75d26-145">Create a table</span></span>

<span data-ttu-id="75d26-146">Tento příklad ukazuje, jak vytvořit tabulku, pokud ještě neexistuje:</span><span class="sxs-lookup"><span data-stu-id="75d26-146">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

## <a name="add-an-entity-to-a-table"></a><span data-ttu-id="75d26-147">Přidání entity do tabulky</span><span class="sxs-lookup"><span data-stu-id="75d26-147">Add an entity to a table</span></span>

<span data-ttu-id="75d26-148">Entita musí mít typ, který dědí z `TableEntity`.</span><span class="sxs-lookup"><span data-stu-id="75d26-148">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="75d26-149">Můžete rozšířit `TableEntity` v jakýmkoli způsobem se vám líbí, ale typ vašeho *musí* mít konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="75d26-149">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="75d26-150">Pouze vlastnosti, které oba `get` a `set` se uloží v Azure Table.</span><span class="sxs-lookup"><span data-stu-id="75d26-150">Only properties that have both `get` and `set` will be stored in your Azure Table.</span></span>

<span data-ttu-id="75d26-151">Klíč entity oddílu a řádku entity jednoznačně identifikují entitu v tabulce.</span><span class="sxs-lookup"><span data-stu-id="75d26-151">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="75d26-152">Entity se stejným klíčem oddílu můžete zadat dotaz rychleji než ty, které se různé klíče oddílů, ale používání různých klíčů oddílů umožňuje větší škálovatelnost paralelních operací.</span><span class="sxs-lookup"><span data-stu-id="75d26-152">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="75d26-153">Tady je příklad `Customer` používající `lastName` jako klíč oddílu a `firstName` jako klíč řádku.</span><span class="sxs-lookup"><span data-stu-id="75d26-153">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="75d26-154">Teď přidáme naše `Customer` do tabulky.</span><span class="sxs-lookup"><span data-stu-id="75d26-154">Now we'll add our `Customer` to the table.</span></span> <span data-ttu-id="75d26-155">Chcete-li to provést, vytvoříte `TableOperation` , budou spuštěny v tabulce.</span><span class="sxs-lookup"><span data-stu-id="75d26-155">To do so, you create a `TableOperation` that will execute on the table.</span></span> <span data-ttu-id="75d26-156">V tomto případě vytvoříte `Insert` operaci.</span><span class="sxs-lookup"><span data-stu-id="75d26-156">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

## <a name="insert-a-batch-of-entities"></a><span data-ttu-id="75d26-157">Vložení dávky entit</span><span class="sxs-lookup"><span data-stu-id="75d26-157">Insert a batch of entities</span></span>

<span data-ttu-id="75d26-158">Do tabulky pomocí jednoho zápisu operace můžete vložit dávku entit.</span><span class="sxs-lookup"><span data-stu-id="75d26-158">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="75d26-159">Dávkové operace umožňují kombinovat operací do jednoho spuštění, ale mají určitá omezení:</span><span class="sxs-lookup"><span data-stu-id="75d26-159">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="75d26-160">Můžete provádět aktualizace, odstranění a vložení v rámci jedné dávkové operace.</span><span class="sxs-lookup"><span data-stu-id="75d26-160">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="75d26-161">Dávková operace může obsahovat až 100 entit.</span><span class="sxs-lookup"><span data-stu-id="75d26-161">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="75d26-162">Všechny entity v rámci dávkové operace musí mít stejný klíč oddílu.</span><span class="sxs-lookup"><span data-stu-id="75d26-162">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="75d26-163">I když je možné provést dotaz v rámci dávkové operace, musí být ale jediná operace v dávce.</span><span class="sxs-lookup"><span data-stu-id="75d26-163">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="75d26-164">Zde je kód, který kombinuje dvě vloží do dávkové operace:</span><span class="sxs-lookup"><span data-stu-id="75d26-164">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

## <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="75d26-165">Načtení všech entit v oddílu</span><span class="sxs-lookup"><span data-stu-id="75d26-165">Retrieve all entities in a partition</span></span>

<span data-ttu-id="75d26-166">Dotaz na tabulku pro všechny entity v oddílu, použijte `TableQuery` objektu.</span><span class="sxs-lookup"><span data-stu-id="75d26-166">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="75d26-167">Zde můžete filtr pro entity kde "Buster" je klíč oddílu.</span><span class="sxs-lookup"><span data-stu-id="75d26-167">Here, you filter for entities where "Buster" is the partition key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L80)]

<span data-ttu-id="75d26-168">Nyní vytisknout výsledky:</span><span class="sxs-lookup"><span data-stu-id="75d26-168">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]


## <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="75d26-169">Načtení rozsahu entit v oddílu</span><span class="sxs-lookup"><span data-stu-id="75d26-169">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="75d26-170">Pokud nechcete, aby k dotazování všechny entity v oddílu, můžete zadat rozsah kombinací filtru klíče oddílu s filtrem klíče řádku.</span><span class="sxs-lookup"><span data-stu-id="75d26-170">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="75d26-171">Tady můžete použít dva filtry k získání všech entit v oddílu "Buster" kde klíč řádku (jméno) začíná písmenem starší než "M" abecedy.</span><span class="sxs-lookup"><span data-stu-id="75d26-171">Here, you use two filters to get all entities in the "Buster" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="75d26-172">Nyní vytisknout výsledky:</span><span class="sxs-lookup"><span data-stu-id="75d26-172">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

## <a name="retrieve-a-single-entity"></a><span data-ttu-id="75d26-173">Načtení jedné entity</span><span class="sxs-lookup"><span data-stu-id="75d26-173">Retrieve a single entity</span></span>

<span data-ttu-id="75d26-174">Můžete napsat dotaz pro načtení jedné konkrétní entity.</span><span class="sxs-lookup"><span data-stu-id="75d26-174">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="75d26-175">Tady můžete použít `TableOperation` k určení zákazníka "Larry Buster".</span><span class="sxs-lookup"><span data-stu-id="75d26-175">Here, you use a `TableOperation` to specify the customer "Larry Buster".</span></span> <span data-ttu-id="75d26-176">Místo kolekce, můžete se vrátit `Customer`.</span><span class="sxs-lookup"><span data-stu-id="75d26-176">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="75d26-177">V dotazu zadat klíč oddílu a klíč řádku je nejrychlejší způsob, jak načíst jednu entitu ze služby Table.</span><span class="sxs-lookup"><span data-stu-id="75d26-177">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="75d26-178">Nyní vytisknout výsledky:</span><span class="sxs-lookup"><span data-stu-id="75d26-178">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]


## <a name="replace-an-entity"></a><span data-ttu-id="75d26-179">Nahrazení entity</span><span class="sxs-lookup"><span data-stu-id="75d26-179">Replace an entity</span></span>

<span data-ttu-id="75d26-180">Pokud chcete entitu aktualizovat, načtěte ji ze služby Table, upravte objekt entity a potom uložte změny zpět k tabulce služby pomocí `Replace` operaci.</span><span class="sxs-lookup"><span data-stu-id="75d26-180">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="75d26-181">To způsobí, že entita, která má být plně nahradí na serveru, pokud se entita na serveru se změnil od načtení, v takovém případě se operace nezdaří.</span><span class="sxs-lookup"><span data-stu-id="75d26-181">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation will fail.</span></span> <span data-ttu-id="75d26-182">Je toto selhání zabrání vaší aplikaci v nechtěném přepsání změny z jiných zdrojů.</span><span class="sxs-lookup"><span data-stu-id="75d26-182">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

## <a name="insert-or-replace-an-entity"></a><span data-ttu-id="75d26-183">Vložení nebo nahrazení entity</span><span class="sxs-lookup"><span data-stu-id="75d26-183">Insert-or-replace an entity</span></span>

<span data-ttu-id="75d26-184">V některých případech nevíte, jestli entita existuje v tabulce nebo ne.</span><span class="sxs-lookup"><span data-stu-id="75d26-184">Sometimes, you don't know if the entity exists in the table or not.</span></span> <span data-ttu-id="75d26-185">A pokud ano, aktuální hodnoty v ní uloženy už nejsou potřeba.</span><span class="sxs-lookup"><span data-stu-id="75d26-185">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="75d26-186">Můžete použít `InsertOrReplace` vytvořit entitu, nebo ho nahradit, pokud existuje, bez ohledu na jeho stav.</span><span class="sxs-lookup"><span data-stu-id="75d26-186">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L140)]

## <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="75d26-187">Dotaz na podmnožinu vlastností entity</span><span class="sxs-lookup"><span data-stu-id="75d26-187">Query a subset of entity properties</span></span>

<span data-ttu-id="75d26-188">Dotaz na tabulku můžete načíst jenom několik z entity, místo všechny z nich.</span><span class="sxs-lookup"><span data-stu-id="75d26-188">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="75d26-189">Tento postup volá projekce, může zlepšit výkon dotazů, hlavně pro velké entity.</span><span class="sxs-lookup"><span data-stu-id="75d26-189">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="75d26-190">Zde můžete vrátit pouze e-mailových adres, pomocí `DynamicTableEntity` a `EntityResolver`.</span><span class="sxs-lookup"><span data-stu-id="75d26-190">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="75d26-191">Všimněte si, že projekci nepodporuje emulátor místního úložiště, takže tento kód spustí pouze v případě, že používáte účet služby Table.</span><span class="sxs-lookup"><span data-stu-id="75d26-191">Note that projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L146-L157)]

## <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="75d26-192">Načtení entit na stránkách asynchronně</span><span class="sxs-lookup"><span data-stu-id="75d26-192">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="75d26-193">Pokud načítáte velký počet entit a chcete je zpracovat, protože jsou načítány místo čekání mají všechny vrátí, můžete použít segmentovaného dotazu.</span><span class="sxs-lookup"><span data-stu-id="75d26-193">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="75d26-194">Zde vracet výsledky na stránkách pomocí pracovním postupu asynchronní tak, aby provádění není blokován, zatímco čekáte pro velké sady výsledků vrátit.</span><span class="sxs-lookup"><span data-stu-id="75d26-194">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L177)]

<span data-ttu-id="75d26-195">Je teď spustit tento výpočet synchronně:</span><span class="sxs-lookup"><span data-stu-id="75d26-195">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L179-L179)]

## <a name="delete-an-entity"></a><span data-ttu-id="75d26-196">Odstranění entity</span><span class="sxs-lookup"><span data-stu-id="75d26-196">Delete an entity</span></span>

<span data-ttu-id="75d26-197">Entitu můžete po jejím načtení odstranit.</span><span class="sxs-lookup"><span data-stu-id="75d26-197">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="75d26-198">Stejně jako u aktualizaci entity, to se nezdaří, pokud došlo ke změně entity vzhledem k tomu, že jste jej získali.</span><span class="sxs-lookup"><span data-stu-id="75d26-198">As with updating an entity, this will fail if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L185-L186)]

## <a name="delete-a-table"></a><span data-ttu-id="75d26-199">Odstranění tabulky</span><span class="sxs-lookup"><span data-stu-id="75d26-199">Delete a table</span></span>

<span data-ttu-id="75d26-200">Odstranit tabulku z účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="75d26-200">You can delete a table from a storage account.</span></span> <span data-ttu-id="75d26-201">Tabulka, která byla odstraněna není k dispozici pro určitou dobu po odstranění byla znovu vytvořena.</span><span class="sxs-lookup"><span data-stu-id="75d26-201">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L192-L192)]

## <a name="next-steps"></a><span data-ttu-id="75d26-202">Další kroky</span><span class="sxs-lookup"><span data-stu-id="75d26-202">Next steps</span></span>

<span data-ttu-id="75d26-203">Teď, když jste se naučili základy používání služby Table storage, postupujte podle následujících odkazech na další informace o složitějších úlohách úložiště:</span><span class="sxs-lookup"><span data-stu-id="75d26-203">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks:</span></span>

- [<span data-ttu-id="75d26-204">Rozhraní API úložiště Azure pro .NET</span><span class="sxs-lookup"><span data-stu-id="75d26-204">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="75d26-205">Typ zprostředkovatele úložiště Azure</span><span class="sxs-lookup"><span data-stu-id="75d26-205">Azure Storage Type Provider</span></span>](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="75d26-206">Blog týmu Azure Storage</span><span class="sxs-lookup"><span data-stu-id="75d26-206">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/b/windowsazurestorage/)
- [<span data-ttu-id="75d26-207">Konfigurace připojovacích řetězců Azure Storage</span><span class="sxs-lookup"><span data-stu-id="75d26-207">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="75d26-208">Začínáme s Azure Table Storage v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="75d26-208">Getting Started with Azure Table Storage in .NET</span></span>](https://azure.microsoft.com/documentation/samples/storage-table-dotnet-getting-started/)
