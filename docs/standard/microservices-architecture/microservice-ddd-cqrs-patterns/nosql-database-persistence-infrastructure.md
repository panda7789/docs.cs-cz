---
title: Použití databáze NoSQL jako trvalost infrastruktury
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Použití databáze NoSQL jako trvalost infrastruktury
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: 2618e8c068ec538f5bfed2f8243d1c594478fcb0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578960"
---
# <a name="using-nosql-databases-as-a-persistence-infrastructure"></a><span data-ttu-id="98fa2-103">Použití databáze NoSQL jako trvalost infrastruktury</span><span class="sxs-lookup"><span data-stu-id="98fa2-103">Using NoSQL databases as a persistence infrastructure</span></span>

<span data-ttu-id="98fa2-104">Použijete-li databáze NoSQL pro vaši infrastrukturu datové vrstvy, obvykle použijete ORM jako Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="98fa2-104">When you use NoSQL databases for your infrastructure data tier, you typically do not use an ORM like Entity Framework Core.</span></span> <span data-ttu-id="98fa2-105">Místo toho můžete použít rozhraní API poskytované modul NoSQL, jako je například Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB nebo úložiště tabulek Azure.</span><span class="sxs-lookup"><span data-stu-id="98fa2-105">Instead you use the API provided by the NoSQL engine, such as Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB, or Azure Storage Tables.</span></span>

<span data-ttu-id="98fa2-106">Při použití databáze NoSQL, zejména orientované dokumentu databázi jako Azure Cosmos DB, CouchDB nebo RavenDB, způsob návrhu modelu pomocí DDD agregace je však částečně podobná jak vám to provést základní EF namapoval identifikace agregační kořeny, tříd podřízených entit a tříd objektů hodnotu.</span><span class="sxs-lookup"><span data-stu-id="98fa2-106">However, when you use a NoSQL database, especially a document-oriented database like Azure Cosmos DB, CouchDB, or RavenDB, the way you design your model with DDD aggregates is partially similar to how you can do it in EF Core, in regards to the identification of aggregate roots, child entity classes, and value object classes.</span></span> <span data-ttu-id="98fa2-107">Ale nakonec, bude mít vliv na výběr databáze při návrhu.</span><span class="sxs-lookup"><span data-stu-id="98fa2-107">But, ultimately, the database selection will impact in your design.</span></span>

<span data-ttu-id="98fa2-108">Pokud používáte databázi orientované na dokument, implementaci agregace jako jeden dokument, serializované ve formátu JSON nebo jiného formátu.</span><span class="sxs-lookup"><span data-stu-id="98fa2-108">When you use a document-oriented database, you implement an aggregate as a single document, serialized in JSON or another format.</span></span> <span data-ttu-id="98fa2-109">Použití databáze je však transparentní z domény modelu kódu hlediska.</span><span class="sxs-lookup"><span data-stu-id="98fa2-109">However, the use of the database is transparent from a domain model code point of view.</span></span> <span data-ttu-id="98fa2-110">Při použití databáze NoSQL, stále používáte agregační kořenové třídy a tříd entit, ale s více flexibility než při použití EF jádra, protože trvalost není relační.</span><span class="sxs-lookup"><span data-stu-id="98fa2-110">When using a NoSQL database, you still are using entity classes and aggregate root classes, but with more flexibility than when using EF Core because the persistence is not relational.</span></span>

<span data-ttu-id="98fa2-111">Rozdíl je v jak zachovat tohoto modelu.</span><span class="sxs-lookup"><span data-stu-id="98fa2-111">The difference is in how you persist that model.</span></span> <span data-ttu-id="98fa2-112">Pokud jste implementovali modelu domény podle třídy entity objektů POCO, lhostejné trvalost infrastruktury, může vypadat jako by mohla přesunout do infrastruktury, a jinou trvalost i z relační k NoSQL.</span><span class="sxs-lookup"><span data-stu-id="98fa2-112">If you implemented your domain model based on POCO entity classes, agnostic to the infrastructure persistence, it might look like you could move to a different persistence infrastructure, even from relational to NoSQL.</span></span> <span data-ttu-id="98fa2-113">Nicméně, který by neměl být vaším cílem.</span><span class="sxs-lookup"><span data-stu-id="98fa2-113">However, that should not be your goal.</span></span> <span data-ttu-id="98fa2-114">Stále existují omezení v různých databází předá jste zpátky, takže nebudete moci mít stejný model pro relační nebo databáze NoSQL.</span><span class="sxs-lookup"><span data-stu-id="98fa2-114">There are always constraints in the different databases will push you back, so you will not be able to have the same model for relational or NoSQL databases.</span></span> <span data-ttu-id="98fa2-115">Změna trvalost modely nebude triviální, protože transakce a trvalost operace se příliš neliší.</span><span class="sxs-lookup"><span data-stu-id="98fa2-115">Changing persistence models would not be trivial, because transactions and persistence operations will be very different.</span></span>

<span data-ttu-id="98fa2-116">Například v databázi orientované dokumentu, je v pořádku pole agregační kořenového tak, aby měl více vlastností podřízené kolekce.</span><span class="sxs-lookup"><span data-stu-id="98fa2-116">For example, in a document-oriented database, it is okay for an aggregate root to have multiple child collection properties.</span></span> <span data-ttu-id="98fa2-117">Dotaz na více vlastností podřízené kolekce je awful, v relační databázi, protože návratu příkazu SJEDNOCENÍ všech SQL z EF.</span><span class="sxs-lookup"><span data-stu-id="98fa2-117">In a relational database, querying multiple child collection properties is awful, because you get a UNION ALL SQL statement back from EF.</span></span> <span data-ttu-id="98fa2-118">Má stejný model domény pro relační databáze nebo databáze NoSQL není jednoduché a vyzkoušet by neměl.</span><span class="sxs-lookup"><span data-stu-id="98fa2-118">Having the same domain model for relational databases or NoSQL databases is not simple, and you should not try it.</span></span> <span data-ttu-id="98fa2-119">Máte skutečně návrhu modelu pomocí představu o tom, jak je bude používat v každé konkrétní databázi data.</span><span class="sxs-lookup"><span data-stu-id="98fa2-119">You really have to design your model with an understanding of how the data is going to be used in each particular database.</span></span>

<span data-ttu-id="98fa2-120">Výhody při použití databáze NoSQL je, že entity více nenormalizované, takže není nastaveno mapování tabulky.</span><span class="sxs-lookup"><span data-stu-id="98fa2-120">A benefit when using NoSQL databases is that the entities are more denormalized, so you do not set a table mapping.</span></span> <span data-ttu-id="98fa2-121">Váš model domény může být flexibilnější než při použití relační databáze.</span><span class="sxs-lookup"><span data-stu-id="98fa2-121">Your domain model can be more flexible than when using a relational database.</span></span>

<span data-ttu-id="98fa2-122">Při návrhu modelu domény podle agregace, přesunutí NoSQL a orientované dokumentu databáze může být i jednodušší než použití relační databázi, protože agregace, které vám navrhnout jsou podobné serializovat dokumenty v databázi orientované dokumentu.</span><span class="sxs-lookup"><span data-stu-id="98fa2-122">When you design your domain model based on aggregates, moving to NoSQL and document-oriented databases might be even easier than using a relational database, because the aggregates you design are similar to serialized documents in a document-oriented database.</span></span> <span data-ttu-id="98fa2-123">Potom můžete zahrnout tyto "obalů" všechny informace, které může být nutné pro tuto agregace.</span><span class="sxs-lookup"><span data-stu-id="98fa2-123">Then you can include in those “bags” all the information you might need for that aggregate.</span></span>

<span data-ttu-id="98fa2-124">Například následující kód JSON je příklad implementace agregace pořadí při použití databáze orientované dokumentu.</span><span class="sxs-lookup"><span data-stu-id="98fa2-124">For instance, the following JSON code is a sample implementation of an order aggregate when using a document-oriented database.</span></span> <span data-ttu-id="98fa2-125">Je to podobné agregační pořadí implementovali jsme v ukázce eShopOnContainers, ale bez použití EF základní pod.</span><span class="sxs-lookup"><span data-stu-id="98fa2-125">It is similar to the order aggregate we implemented in the eShopOnContainers sample, but without using EF Core underneath.</span></span>

```json
{
    "id": "2017001",
    "orderDate": "2/25/2017",
    "buyerId": "1234567",
    "address": [
        {
        "street": "100 One Microsoft Way",
        "city": "Redmond",
        "state": "WA",
        "zip": "98052",
        "country": "U.S."
        }
    ],
    "orderItems": [
        {"id": 20170011, "productId": "123456", "productName": ".NET T-Shirt",
        "unitPrice": 25, "units": 2, "discount": 0},
        {"id": 20170012, "productId": "123457", "productName": ".NET Mug",
        "unitPrice": 15, "units": 1, "discount": 0}
    ]
}
```

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a><span data-ttu-id="98fa2-126">Úvod do Azure Cosmos DB a nativní API DB Cosmos</span><span class="sxs-lookup"><span data-stu-id="98fa2-126">Introduction to Azure Cosmos DB and the native Cosmos DB API</span></span>

<span data-ttu-id="98fa2-127">[Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/introduction) je globálně distribuované databáze služby společnosti Microsoft pro kritické aplikace.</span><span class="sxs-lookup"><span data-stu-id="98fa2-127">[Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/introduction) is Microsoft's globally distributed database service for mission-critical applications.</span></span> <span data-ttu-id="98fa2-128">Poskytuje Azure Cosmos DB [globální distribuční klíč](https://docs.microsoft.com/en-us/azure/cosmos-db/distribute-data-globally), [elastické škálování propustnost a úložiště](https://docs.microsoft.com/en-us/azure/cosmos-db/partition-data) po celém světě, jednociferné milisekundu latence v 99th percentilu [pět dobře definované úrovně konzistence](https://docs.microsoft.com/en-us/azure/cosmos-db/consistency-levels)a zaručit vysoká dostupnost, všechny zálohovány pomocí [špičkový SLA](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span><span class="sxs-lookup"><span data-stu-id="98fa2-128">Azure Cosmos DB provides [turn-key global distribution](https://docs.microsoft.com/en-us/azure/cosmos-db/distribute-data-globally), [elastic scaling of throughput and storage](https://docs.microsoft.com/en-us/azure/cosmos-db/partition-data) worldwide, single-digit millisecond latencies at the 99th percentile, [five well-defined consistency levels](https://docs.microsoft.com/en-us/azure/cosmos-db/consistency-levels), and guaranteed high availability, all backed by [industry-leading SLAs](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span></span> <span data-ttu-id="98fa2-129">Azure Cosmos DB [automaticky indexuje data](http://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) bez nutnosti zabývat Správa schématu a index.</span><span class="sxs-lookup"><span data-stu-id="98fa2-129">Azure Cosmos DB [automatically indexes data](http://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) without requiring you to deal with schema and index management.</span></span> <span data-ttu-id="98fa2-130">Je více modelu a podporuje dokumentu, klíč hodnota, grafu a sloupcová datové modely.</span><span class="sxs-lookup"><span data-stu-id="98fa2-130">It is multi-model and supports document, key-value, graph, and columnar data models.</span></span>

<span data-ttu-id="98fa2-131">![](./media/image19.1.png) Obrázek 9-19.</span><span class="sxs-lookup"><span data-stu-id="98fa2-131">![](./media/image19.1.png) Figure 9-19.</span></span> <span data-ttu-id="98fa2-132">Globální distribuční Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="98fa2-132">Azure Cosmos DB global distribution</span></span>

<span data-ttu-id="98fa2-133">Při použití a C\# modelu k implementaci agregace má být používána Cosmos DB rozhraní API služby Azure, agregace může být podobná C\# objektů POCO třídy používané s EF jádra.</span><span class="sxs-lookup"><span data-stu-id="98fa2-133">When you use a C\# model to implement the aggregate to be used by the Azure Cosmos DB API, the aggregate can be similar to the C\# POCO classes used with EF Core.</span></span> <span data-ttu-id="98fa2-134">Rozdíl je způsobem je použít z aplikace a infrastrukturu vrstvy, jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="98fa2-134">The difference is in the way to use them from the application and infrastructure layers, as in the following code:</span></span>

```csharp
// C# EXAMPLE OF AN ORDER AGGREGATE BEING PERSISTED WITH AZURE COSMOS DB API
// *** Domain Model Code ***
// Aggregate: Create an Order object with its child entities and/or value objects.
// Then, use AggregateRoot’s methods to add the nested objects so invariants and
// logic is consistent across the nested properties (value objects and entities).

Order orderAggregate = new Order
{
    Id = "2017001",
    OrderDate = new DateTime(2005, 7, 1),
    BuyerId = "1234567",
    PurchaseOrderNumber = "PO18009186470"
}

Address address = new Address
{
    Street = "100 One Microsoft Way",
    City = "Redmond",
    State = "WA",
    Zip = "98052",
    Country = "U.S."
}

orderAggregate.UpdateAddress(address);

OrderItem orderItem1 = new OrderItem
{
    Id = 20170011,
    ProductId = "123456",
    ProductName = ".NET T-Shirt",
    UnitPrice = 25,
    Units = 2,
    Discount = 0;
};

//Using methods with domain logic within the entity. No anemic-domain model
orderAggregate.AddOrderItem(orderItem1);
orderAggregate.AddOrderItem(orderItem2);
// *** End of Domain Model Code ***

// *** Infrastructure Code using Cosmos DB Client API ***
Uri collectionUri = UriFactory.CreateDocumentCollectionUri(databaseName,
    collectionName);

await client.CreateDocumentAsync(collectionUri, orderAggregate);

// As your app evolves, let's say your object has a new schema. You can insert
// OrderV2 objects without any changes to the database tier.
Order2 newOrder = GetOrderV2Sample("IdForSalesOrder2");
await client.CreateDocumentAsync(collectionUri, newOrder);
```

<span data-ttu-id="98fa2-135">Uvidíte, že způsob práce se svým modelem domény mohou být podobným způsobem, můžete ho použít k vrstvě modelu domény EF po infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="98fa2-135">You can see that the way you work with your domain model can be similar to the way you use it in your domain model layer when the infrastructure is EF.</span></span> <span data-ttu-id="98fa2-136">Když nadále používat stejné metody agregační kořenové pro zajištění konzistence, výstupních podmínek a ověření v rámci agregace.</span><span class="sxs-lookup"><span data-stu-id="98fa2-136">You still use the same aggregate root methods to ensure consistency, invariants, and validations within the aggregate.</span></span>

<span data-ttu-id="98fa2-137">Ale když můžete zachovat modelu do databáze NoSQL, kód a rozhraní API změnu výrazně ve srovnání s EF základní kódu nebo jakýkoli jiný kód související s relačních databází.</span><span class="sxs-lookup"><span data-stu-id="98fa2-137">However, when you persist your model into the NoSQL database, the code and API change dramatically compared to EF Core code or any other code related to relational databases.</span></span>

## <a name="implementing-net-code-targeting-mongodb-and-azure-cosmos-db"></a><span data-ttu-id="98fa2-138">Implementace kód .NET cílené na MongoDB a Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="98fa2-138">Implementing .NET code targeting MongoDB and Azure Cosmos DB</span></span>

### <a name="using-azure-cosmos-db-from-net-containers"></a><span data-ttu-id="98fa2-139">Pomocí Azure DB Cosmos z kontejnerů rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="98fa2-139">Using Azure Cosmos DB from .NET containers</span></span>

<span data-ttu-id="98fa2-140">Azure Cosmos DB databází můžete přistupovat z kódu .NET spuštění v kontejnerech, jako je z jiné aplikace .NET.</span><span class="sxs-lookup"><span data-stu-id="98fa2-140">You can access Azure Cosmos DB databases from .NET code running in containers, like from any other .NET application.</span></span> <span data-ttu-id="98fa2-141">Například Locations.API a Marketing.API mikroslužeb v eShopOnContainers se implementují tak mohou spotřebovat databáze Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="98fa2-141">For instance, the Locations.API and Marketing.API microservices in eShopOnContainers are implemented so they can consume Azure Cosmos DB databases.</span></span>

<span data-ttu-id="98fa2-142">Existuje ale omezení v Azure Cosmos DB z Docker vývoj prostředí hlediska.</span><span class="sxs-lookup"><span data-stu-id="98fa2-142">However, there’s a limitation in Azure Cosmos DB from a Docker development environment point of view.</span></span> <span data-ttu-id="98fa2-143">I když dojde místní [emulátoru DB Cosmos Azure](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator) moci spustit v místním vývojovém počítači (například počítač), jako opožděného 2017 právě podporuje Windows, Linux není.</span><span class="sxs-lookup"><span data-stu-id="98fa2-143">Even when there’s a on-premises [Azure Cosmos DB Emulator](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator) able to run in a local development machine (like a PC), as of late 2017, it just supports Windows, not Linux.</span></span> 

<span data-ttu-id="98fa2-144">Je také možné spustit tuto emulátoru na Docker, ale jenom na Windows kontejnery s, nikoli kontejnery Linux.</span><span class="sxs-lookup"><span data-stu-id="98fa2-144">There is also the possibility to run this emulator on Docker, but just on Windows Containers with the , not Linux Containers.</span></span> <span data-ttu-id="98fa2-145">Který je počáteční postižení pro vývojové prostředí, pokud vaše aplikace je nasazená jako kontejnery Linux od, aktuálně, Linux a Windows kontejnerů v Docker pro systém Windows nemůže nasadit ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="98fa2-145">That is an initial handicap for the development environment if your application is deployed as Linux containers, since, currently, you cannot deploy Linux and Windows Containers on Docker for Windows at the same time.</span></span> <span data-ttu-id="98fa2-146">Buď všechny kontejnery nasazení musí být pro Linux nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="98fa2-146">Either all containers being deployed have to be for Linux or for Windows.</span></span>  

<span data-ttu-id="98fa2-147">Abyste mohli nasadit databázovými systémy jako kontejnery spolu s vlastní kontejnerů, aby se vaše prostředí pro vývoj/testování jsou vždy konzistentní je ideální a více přehledné nasazení řešení pro vývoj/testování.</span><span class="sxs-lookup"><span data-stu-id="98fa2-147">The ideal and more straightforward deployment for a dev/test solution is to be able to deploy your database systems as containers along with your custom containers so your dev/test environments are always consistent.</span></span>

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a><span data-ttu-id="98fa2-148">Použít rozhraní API MongoDB pro místní vývoj/testování Linux a Windows kontejnery plus Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="98fa2-148">Use MongoDB API for local dev/test Linux/Windows containers plus Azure Cosmos DB</span></span>

<span data-ttu-id="98fa2-149">Databáze DB cosmos podporují rozhraní API MongoDB pro rozhraní .NET a také nativní síťový protokol MongoDB.</span><span class="sxs-lookup"><span data-stu-id="98fa2-149">Cosmos DB databases support MongoDB API for .NET as well as the native MongoDB wire protocol.</span></span> <span data-ttu-id="98fa2-150">To znamená, že vaše aplikace napsané pro MongoDB pomocí existujících ovladačů, můžete nyní komunikovat s Cosmos DB a používat Cosmos DB databáze místo databáze MongoDB, jak je znázorněno v obrázek 9-20.</span><span class="sxs-lookup"><span data-stu-id="98fa2-150">This means that by using existing drivers, your application written for MongoDB can now communicate with Cosmos DB and use Cosmos DB databases instead of MongoDB databases, as shown in Figure 9-20.</span></span>

<span data-ttu-id="98fa2-151">![](./media/image19.2.png) Obrázek 9-20.</span><span class="sxs-lookup"><span data-stu-id="98fa2-151">![](./media/image19.2.png) Figure 9-20.</span></span> <span data-ttu-id="98fa2-152">Pomocí rozhraní API MongoDB a protokol pro přístup k databázi Azure Cosmos</span><span class="sxs-lookup"><span data-stu-id="98fa2-152">Using MongoDB API and protocol to access Azure Cosmos DB</span></span>

<span data-ttu-id="98fa2-153">Toto je velmi praktické přístup pro ověření koncepty v prostředích Docker s kontejnery Linux, protože [image MongoDB Docker](https://hub.docker.com/r/_/mongo/) je více architektury bitovou kopii, která podporuje kontejnery Docker Linux a Docker Windows kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="98fa2-153">This is a very convenient approach for proof of concepts in Docker environments with Linux containers because the [MongoDB Docker image](https://hub.docker.com/r/_/mongo/) is a multi-arch image that supports Docker Linux containers and Docker Windows containers.</span></span>

<span data-ttu-id="98fa2-154">Jak je znázorněno na obrázku 9 – 21, pomocí rozhraní API MongoDB eShopOnContainers podporuje kontejnery MongoDB Linux a Windows pro místní vývojové prostředí, ale pak můžete přesunout na škálovatelné, PaaS cloudové řešení jako Azure DB Cosmos podle jednoduše [změna připojovací řetězec MongoDB tak, aby odkazoval na databázi Azure Cosmos](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="98fa2-154">As shown in the image 9-21, by using the MongoDB API, eShopOnContainers supports MongoDB Linux and Windows containers for the local development environment but then, you can move to a scalable, PaaS cloud solution as Azure Cosmos DB by simply [changing the MongoDB connection string to point to Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account).</span></span> 

<span data-ttu-id="98fa2-155">![](./media/image20-bis.png) Obrázek 9 – 21.</span><span class="sxs-lookup"><span data-stu-id="98fa2-155">![](./media/image20-bis.png) Figure 9-21.</span></span> <span data-ttu-id="98fa2-156">eShopOnContainers používat MongoDB kontejnery pro vývojáře env nebo Azure Cosmos DB v provozním prostředí</span><span class="sxs-lookup"><span data-stu-id="98fa2-156">eShopOnContainers using MongoDB containers for dev-env or Azure Cosmos DB for production</span></span>

<span data-ttu-id="98fa2-157">Provozní Azure Cosmos DB budou pracovat v cloudu Azure jako PaaS a škálovatelné služby.</span><span class="sxs-lookup"><span data-stu-id="98fa2-157">The production Azure Cosmos DB would be running in Azure’s cloud as a PaaS and scalable service.</span></span>

<span data-ttu-id="98fa2-158">Vlastní kontejnerů .NET Core lze spustit na hostiteli Docker místní vývoj (který je používán Docker pro Windows v počítači Windows 10) nebo nasadit do provozního prostředí, jako je Kubernetes v Azure AKS nebo Azure Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="98fa2-158">Your custom .NET Core containers can run on a local development Docker host (that is using Docker for Windows in a Windows 10 machine) or be deployed into a production environment, like Kubernetes in Azure AKS or Azure Service Fabric.</span></span> <span data-ttu-id="98fa2-159">V tomto prostředí druhý by nasadit jenom vlastní kontejnery .NET Core, ale není kontejneru MongoDB vzhledem k tomu, že budete používat databázi Cosmos Azure v cloudu pro zpracování dat v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="98fa2-159">In this second environment, you would deploy only the .NET Core custom containers but not the MongoDB container since you’d be using Azure Cosmos DB in the cloud for handling the data in production.</span></span>

<span data-ttu-id="98fa2-160">Vymazat výhodou používání rozhraní API MongoDB je, že vaše řešení by mohl spustit v oba motory databázi MongoDB nebo Cosmos databáze Azure, takže migrace do různých prostředí by mělo být snadné.</span><span class="sxs-lookup"><span data-stu-id="98fa2-160">A clear benefit of using the MongoDB API is that your solution could run in both database engines, MongoDB or Azure Cosmos DB, so migrations to different environments should be easy.</span></span> <span data-ttu-id="98fa2-161">V některých případech je však smysl pomocí nativních rozhraní API (který je nativní API DB Cosmos) chcete naplno využít možnosti konkrétní databázového stroje.</span><span class="sxs-lookup"><span data-stu-id="98fa2-161">However, sometimes it is worthwhile to use a native API (that is the native Cosmos DB API) in order to take full advantage of the capabilities of a specific database engine.</span></span>

<span data-ttu-id="98fa2-162">Další porovnání mezi jednoduše pomocí MongoDB versus Cosmos DB v cloudu najdete v tématu [výhody používání Azure Cosmos DB na této stránce](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction).</span><span class="sxs-lookup"><span data-stu-id="98fa2-162">For further comparison between simply using MongoDB versus Cosmos DB in the cloud, see the [Benefits of using Azure Cosmos DB in this page](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction).</span></span> 


### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a><span data-ttu-id="98fa2-163">Analýza budete přistupovat (aplikacích v produkčním prostředí): rozhraní API MongoDB vs. Rozhraní API cosmos DB</span><span class="sxs-lookup"><span data-stu-id="98fa2-163">Analyze your approach for production applications: MongoDB API vs. Cosmos DB API</span></span>

<span data-ttu-id="98fa2-164">V eShopOnContainers používáme rozhraní API MongoDB, protože naše priority je zásadně tak, aby měl konzistentní vývoj/testování prostředí pomocí databáze NoSQL, která může spolupracovat taky s nástrojem Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="98fa2-164">In eShopOnContainers, we’re using MongoDB API because our priority was fundamentally to have a consistent dev/test environment using a NoSQL database that could also work with Azure Cosmos DB.</span></span>

<span data-ttu-id="98fa2-165">Ale pokud jste v úmyslu použít pro přístup k databázi Azure Cosmos v Azure pro výrobní aplikace MongoDB API, byste měli provést analýzu rozdíly v možnosti a výkon při použití MongoDB rozhraní API pro přístup k databázím Azure Cosmos DB ve srovnání s pomocí nativního Rozhraní API Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="98fa2-165">However, if you planning to use MongoDB API to access Azure Cosmos DB in Azure for production applications, you should analyze the differences in capabilities and performance when using MongoDB API to access Azure Cosmos DB databases compared to using the native Azure Cosmos DB API.</span></span> <span data-ttu-id="98fa2-166">Pokud je to podobné můžete použít MongoDB API a získat výhody podporuje dva stroje databáze NoSQL ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="98fa2-166">If it is similar you can use MongoDB API, and you get the benefit of supporting two NoSQL database engines at the same time.</span></span> 

<span data-ttu-id="98fa2-167">Můžete také použít MongoDB clustery jako produkční databázi v cloudu Azure, s [MongoDB Azure Service](https://www.mongodb.com/scale/mongodb-azure-service).</span><span class="sxs-lookup"><span data-stu-id="98fa2-167">You could also use MongoDB clusters as the production database in Azure’s cloud, too, with [MongoDB Azure Service](https://www.mongodb.com/scale/mongodb-azure-service).</span></span> <span data-ttu-id="98fa2-168">Je to ale není PaaS služby poskytované společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="98fa2-168">But that is not a PaaS service provided by Microsoft.</span></span> <span data-ttu-id="98fa2-169">V takovém případě je Azure hostitelem právě toto řešení pocházejících z MongoDB.</span><span class="sxs-lookup"><span data-stu-id="98fa2-169">In this case, Azure is just hosting that solution coming from MongoDB.</span></span>

<span data-ttu-id="98fa2-170">To je v zásadě platí, pouze upozornění s informacemi o tom, nepoužívejte vždy MongoDB rozhraní API pro Azure Cosmos DB, podle kroků v eShopOnContainers, protože je vhodné volbou pro kontejnery Linux.</span><span class="sxs-lookup"><span data-stu-id="98fa2-170">Basically, this is just a disclaimer stating that you shouldn’t always use MongoDB API against Azure Cosmos DB, as we did in eShopOnContainers because it was a convenient choice for Linux containers.</span></span> <span data-ttu-id="98fa2-171">Rozhodnutí by měla být na základě potřeb a testy, které musíte udělat pro produkční aplikace.</span><span class="sxs-lookup"><span data-stu-id="98fa2-171">The decision should be based on the specific needs and tests you need to do for your production application.</span></span>  

### <a name="the-code-using-mongodb-api-in-net-core-applications"></a><span data-ttu-id="98fa2-172">Kód: použití rozhraní API MongoDB v aplikacích .NET Core</span><span class="sxs-lookup"><span data-stu-id="98fa2-172">The code: Using MongoDB API in .NET Core applications</span></span>

<span data-ttu-id="98fa2-173">MongoDB rozhraní API pro .NET je založená na balíčky NuGet, které je nutné přidat do vašich projektů, jako je Locations.API zobrazí obrázek 9 – 22.</span><span class="sxs-lookup"><span data-stu-id="98fa2-173">MongoDB API for .NET is based on NuGet packages that you need to add to your projects, like the Locations.API shown in Figure 9-22.</span></span>

<span data-ttu-id="98fa2-174">![](./media/image21-bis.png) Obrázek 9 22.</span><span class="sxs-lookup"><span data-stu-id="98fa2-174">![](./media/image21-bis.png) Figure 9-22.</span></span> <span data-ttu-id="98fa2-175">Balíčky NuGet MongoDB rozhraní API odkazů v projektu .NET Core</span><span class="sxs-lookup"><span data-stu-id="98fa2-175">MongoDB API NuGet packages references in a .NET Core project</span></span>

<span data-ttu-id="98fa2-176">Umožňuje prozkoumat kód v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="98fa2-176">Let's investigate the code in the following sections.</span></span>

#### <a name="a-model-used-by-mongodb-api"></a><span data-ttu-id="98fa2-177">Model používá rozhraní API MongoDB</span><span class="sxs-lookup"><span data-stu-id="98fa2-177">A Model used by MongoDB API</span></span>

<span data-ttu-id="98fa2-178">Nejdřív musíte definovat model, který bude obsahovat dat pocházejících z databáze v paměti vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="98fa2-178">First, you need to define a model that will hold the data coming from the database in your application’s memory space.</span></span> <span data-ttu-id="98fa2-179">Tady je příklad modelu v eShopOnContainers použito pro umístění.</span><span class="sxs-lookup"><span data-stu-id="98fa2-179">Here’s an example of the model used for Locations at eShopOnContainers.</span></span>

```csharp
using MongoDB.Bson;
using MongoDB.Bson.Serialization.Attributes;
using MongoDB.Driver.GeoJsonObjectModel;
using System.Collections.Generic;

public class Locations
{
    [BsonId]
    [BsonRepresentation(BsonType.ObjectId)]
    public string Id { get; set; }
    public int LocationId { get; set; }
    public string Code { get; set; }
    [BsonRepresentation(BsonType.ObjectId)]
    public string Parent_Id { get; set; }
    public string Description { get; set; }
    public double Latitude { get; set; }
    public double Longitude { get; set; }
    public GeoJsonPoint<GeoJson2DGeographicCoordinates> Location 
                                                             { get; private set; }
    public GeoJsonPolygon<GeoJson2DGeographicCoordinates> Polygon 
                                                             { get; private set; }
    public void SetLocation(double lon, double lat) => SetPosition(lon, lat);
    public void SetArea(List<GeoJson2DGeographicCoordinates> coordinatesList) 
                                                    => SetPolygon(coordinatesList);

    private void SetPosition(double lon, double lat)
    {
        Latitude = lat;
        Longitude = lon;
        Location = new GeoJsonPoint<GeoJson2DGeographicCoordinates>(
            new GeoJson2DGeographicCoordinates(lon, lat));
    }

    private void SetPolygon(List<GeoJson2DGeographicCoordinates> coordinatesList)
    {
        Polygon = new GeoJsonPolygon<GeoJson2DGeographicCoordinates>(
                  new GeoJsonPolygonCoordinates<GeoJson2DGeographicCoordinates>(
                  new GeoJsonLinearRingCoordinates<GeoJson2DGeographicCoordinates>(
                                                                 coordinatesList)));
    }
}
```

<span data-ttu-id="98fa2-180">Uvidíte, že se několik atributů a typy pocházejících z balíčky MongoDB NuGet.</span><span class="sxs-lookup"><span data-stu-id="98fa2-180">You can see there are a few attributes and types coming from the MongoDB NuGet packages.</span></span>

<span data-ttu-id="98fa2-181">Databáze NoSQL jsou obvykle velmi dobře hodí pro práci s nerelačními daty hierarchické.</span><span class="sxs-lookup"><span data-stu-id="98fa2-181">NoSQL databases are usually very well suited for working with non-relational hierarchical data.</span></span> <span data-ttu-id="98fa2-182">V tomto příkladu používáme expecially typy MongoDB vytvořené pro zeměpisných míst, jako je `GeoJson2DGeographicCoordinates`.</span><span class="sxs-lookup"><span data-stu-id="98fa2-182">In this example, we are using MongoDB types expecially made for geo-locations, like `GeoJson2DGeographicCoordinates`.</span></span>

#### <a name="retrieve-the-database-and-the-collection"></a><span data-ttu-id="98fa2-183">Načtení databáze a kolekce</span><span class="sxs-lookup"><span data-stu-id="98fa2-183">Retrieve the database and the collection</span></span>

<span data-ttu-id="98fa2-184">V eShopOnContainers jsme vytvořili vlastní databázi kontextu, kde implementaci kód pro načtení databáze a MongoCollections, jako v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="98fa2-184">In eShopOnContainers, we have created a custom database context where we implement the code to retrieve the database and the MongoCollections, as in the following code.</span></span>

```csharp
public class LocationsContext
{
    private readonly IMongoDatabase _database = null;

    public LocationsContext(IOptions<LocationSettings> settings)
    {
        var client = new MongoClient(settings.Value.ConnectionString);
        if (client != null)
            _database = client.GetDatabase(settings.Value.Database);
    }

    public IMongoCollection<Locations> Locations
    {
        get
        {
            return _database.GetCollection<Locations>("Locations");
        }
    }       
}
```

#### <a name="retrieve-the-data"></a><span data-ttu-id="98fa2-185">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="98fa2-185">Retrieve the data</span></span>

<span data-ttu-id="98fa2-186">V kódu jazyka C#, jako řadiče webového rozhraní API nebo vlastní implementace úložiště můžete napsat podobný kód pro následující při dotazování prostřednictvím rozhraní API MongoDB.</span><span class="sxs-lookup"><span data-stu-id="98fa2-186">In C# code, like Web API controllers or custom Repositories implementation, you can write similar code to the following when querying through the MongoDB API.</span></span> <span data-ttu-id="98fa2-187">Všimněte si, že `_context` je objekt instancí předchozího `LocationsContext` třídy.</span><span class="sxs-lookup"><span data-stu-id="98fa2-187">Note that the `_context` object is an instance of the previous `LocationsContext` class.</span></span>

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a><span data-ttu-id="98fa2-188">Použít env-var v souboru docker compose.override.yml pro MongoDB připojovací řetězec</span><span class="sxs-lookup"><span data-stu-id="98fa2-188">Use an env-var in the docker-compose.override.yml file for the MongoDB connection string</span></span>

<span data-ttu-id="98fa2-189">Při vytváření objektu MongoClient, je nutné základní parametr, který je přesně `ConnectionString` parametr odkazující na správné databázi.</span><span class="sxs-lookup"><span data-stu-id="98fa2-189">When creating a MongoClient object, it needs a fundamental parameter which is precisely the `ConnectionString` parameter pointing to the right database.</span></span> <span data-ttu-id="98fa2-190">V případě eShopOnContainers může bod připojovací řetězec místní kontejner MongoDB Docker nebo k databázi Azure Cosmos DB "výroba".</span><span class="sxs-lookup"><span data-stu-id="98fa2-190">In the case of eShopOnContainers, the connection string can point to a local MongoDB Docker container or to a “production” Azure Cosmos DB database.</span></span>  <span data-ttu-id="98fa2-191">Tento připojovací řetězec pochází z proměnné definované v `docker-compose.override.yml` soubory používané při nasazení s docker-compose nebo Visual Studio, jako v následujícím kódu yml.</span><span class="sxs-lookup"><span data-stu-id="98fa2-191">That connection string comes from the environment variables defined in the `docker-compose.override.yml` files used when deploying with docker-compose or Visual Studio, as in the following yml code.</span></span>

```yml
# docker-compose.override.yml
version: '3'
services:
  # Other services
  locations.api:
    environment:
      # Other settings
      - ConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosql.data}

```

<span data-ttu-id="98fa2-192">`ConnectionString` – Proměnná prostředí je vyřešit tímto způsobem: Pokud `ESHOP_AZURE_COSMOSDB` – globální proměnná je definována v `.env` souboru připojovacím řetězcem Azure Cosmos DB, použije ho pro přístup k databázi Azure Cosmos DB v cloudu.</span><span class="sxs-lookup"><span data-stu-id="98fa2-192">The `ConnectionString` environment variable is resolved this way: If the `ESHOP_AZURE_COSMOSDB` global variable is defined in the `.env` file with the Azure Cosmos DB connection string, it will use it to access the Azure Cosmos DB database in the cloud.</span></span> 

<span data-ttu-id="98fa2-193">Následující kód ukazuje `.env` soubor s proměnnou globální prostředí Azure Cosmos DB připojovacího řetězce, jak jsou implementované ve eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="98fa2-193">The following code shows the `.env` file with the Azure Cosmos DB connection string global environment variable, as implemented in eShopOnContainers:</span></span>

```yml
# .env file, in eShopOnContainers root folder
# Other Docker environment variables

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost
ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=<YourDockerHostIP>

#ESHOP_AZURE_COSMOSDB=<YourAzureCosmosDBConnData>

#Other environment variables for additional Azure infrastructure assets
#ESHOP_AZURE_REDIS_BASKET_DB=<YourAzureRedisBasketInfo>
#ESHOP_AZURE_STORAGE_CATALOG_URL=<YourAzureStorage_Catalog_BLOB_URL>
#ESHOP_AZURE_SERVICE_BUS=<YourAzureServiceBusInfo>
```

<span data-ttu-id="98fa2-194">Měli zrušte komentář u ESHOP_AZURE_COSMOSDB řádku a aktualizace se službou Azure Cosmos DB připojovací řetězec získali z portálu Azure jako vysvětlené v [připojit MongoDB aplikace pro Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="98fa2-194">You should uncomment the ESHOP_AZURE_COSMOSDB line and update it with your Azure Cosmos DB connection string obtained from the Azure portal as explained in [Connect a MongoDB application to Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account).</span></span>

<span data-ttu-id="98fa2-195">Pokud `ESHOP_AZURE_COSMOSDB` – globální proměnná je prázdná, což znamená, že je odhlašování komentář v `.env` souboru kontejneru se použije výchozí MongoDB připojovací řetězec odkazující na místní MongoDB kontejneru nasazené v eShopOnContainers, která se nazývá `nosql.data`, jak je znázorněno v následujícím kódu .yml.</span><span class="sxs-lookup"><span data-stu-id="98fa2-195">If the `ESHOP_AZURE_COSMOSDB` global variable is empty, meaning that it is commented out in the `.env` file, then the container uses a default MongoDB connection string pointing to the local MongoDB container deployed in eShopOnContainers which is named `nosql.data`, as shown in the following .yml code.</span></span> 

#### <a name="additional-resources"></a><span data-ttu-id="98fa2-196">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="98fa2-196">Additional resources</span></span>

-   <span data-ttu-id="98fa2-197">**Data dokumentu pro databáze NoSQL modelování**
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/modeling-data*](https://docs.microsoft.com/en-us/azure/cosmos-db/modeling-data)</span><span class="sxs-lookup"><span data-stu-id="98fa2-197">**Modeling document data for NoSQL databases**
[*https://docs.microsoft.com/en-us/azure/cosmos-db/modeling-data*](https://docs.microsoft.com/en-us/azure/cosmos-db/modeling-data)</span></span>

-   <span data-ttu-id="98fa2-198">**Vaughn Vernon. Ideální řízené domény návrhu agregace úložišti?**
    [*https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)</span><span class="sxs-lookup"><span data-stu-id="98fa2-198">**Vaughn Vernon. The Ideal Domain-Driven Design Aggregate Store?**
[*https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)</span></span>

-   <span data-ttu-id="98fa2-199">**Úvod do Azure Cosmos DB: rozhraní API pro MongoDB** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction*](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction)</span><span class="sxs-lookup"><span data-stu-id="98fa2-199">**Introduction to Azure Cosmos DB: API for MongoDB** 
[*https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction*](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction)</span></span>

-   <span data-ttu-id="98fa2-200">**Azure Cosmos DB: Vytvoření webové aplikace MongoDB API pomocí rozhraní .NET a portálu Azure** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/create-mongodb-dotnet *](https://docs.microsoft.com/en-us/azure/cosmos-db/create-mongodb-dotnet )</span><span class="sxs-lookup"><span data-stu-id="98fa2-200">**Azure Cosmos DB: Build a MongoDB API web app with .NET and the Azure portal** 
[*https://docs.microsoft.com/en-us/azure/cosmos-db/create-mongodb-dotnet *](https://docs.microsoft.com/en-us/azure/cosmos-db/create-mongodb-dotnet )</span></span>

-   <span data-ttu-id="98fa2-201">**Použití emulátoru DB Cosmos Azure pro místní vývoj a testování** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator*](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator)</span><span class="sxs-lookup"><span data-stu-id="98fa2-201">**Use the Azure Cosmos DB Emulator for local development and testing** 
[*https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator*](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator)</span></span>

-   <span data-ttu-id="98fa2-202">**Připojení aplikace MongoDB pro Azure Cosmos DB** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account*](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account)</span><span class="sxs-lookup"><span data-stu-id="98fa2-202">**Connect a MongoDB application to Azure Cosmos DB** 
[*https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account*](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account)</span></span>

-   <span data-ttu-id="98fa2-203">**Obrázek Cosmos DB emulátoru Docker (kontejneru systému Windows)** 
    [*https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/*](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/)</span><span class="sxs-lookup"><span data-stu-id="98fa2-203">**The Cosmos DB Emulator Docker image (Windows Container)** 
[*https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/*](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/)</span></span>

-   <span data-ttu-id="98fa2-204">**Image MongoDB Docker (Linux a kontejneru systému Windows)** 
    [*https://hub.docker.com/r/_/mongo/*](https://hub.docker.com/r/_/mongo/)</span><span class="sxs-lookup"><span data-stu-id="98fa2-204">**The MongoDB Docker image (Linux and Windows Container)** 
[*https://hub.docker.com/r/_/mongo/*](https://hub.docker.com/r/_/mongo/)</span></span>

-   <span data-ttu-id="98fa2-205">**Pomocí Azure DB Cosmos MongoChef (Studio 3T): rozhraní API pro MongoDB účet** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-mongochef*](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-mongochef)</span><span class="sxs-lookup"><span data-stu-id="98fa2-205">**Use MongoChef (Studio 3T) with an Azure Cosmos DB: API for MongoDB account** 
[*https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-mongochef*](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-mongochef)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="98fa2-206">[Předchozí] (infrastructure-persistence-layer-implemenation-entity-framework-core.md) [Další] (microservice-application-layer-web-api-design.md)</span><span class="sxs-lookup"><span data-stu-id="98fa2-206">[Previous] (infrastructure-persistence-layer-implemenation-entity-framework-core.md) [Next] (microservice-application-layer-web-api-design.md)</span></span>
