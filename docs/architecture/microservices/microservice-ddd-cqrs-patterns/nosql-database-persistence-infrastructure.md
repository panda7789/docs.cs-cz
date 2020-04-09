---
title: Použití databází NoSQL jako infrastruktury trvalosti
description: Pochopit použití databází NoSql obecně a Azure Cosmos DB zejména jako možnost implementovat trvalost.
ms.date: 01/30/2020
ms.openlocfilehash: 9c51e48d82aa0cf0234275f09df43f7a654f0ca8
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988437"
---
# <a name="use-nosql-databases-as-a-persistence-infrastructure"></a><span data-ttu-id="6152e-103">Použití databází NoSQL jako infrastruktury trvalosti</span><span class="sxs-lookup"><span data-stu-id="6152e-103">Use NoSQL databases as a persistence infrastructure</span></span>

<span data-ttu-id="6152e-104">Při použití NoSQL databáze pro databázi infrastruktury data, obvykle nepoužíváte ORM jako entity framework core.</span><span class="sxs-lookup"><span data-stu-id="6152e-104">When you use NoSQL databases for your infrastructure data tier, you typically do not use an ORM like Entity Framework Core.</span></span> <span data-ttu-id="6152e-105">Místo toho použijete rozhraní API poskytované modulem NoSQL, jako je Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB nebo Tabulky úložiště Azure.</span><span class="sxs-lookup"><span data-stu-id="6152e-105">Instead you use the API provided by the NoSQL engine, such as Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB, or Azure Storage Tables.</span></span>

<span data-ttu-id="6152e-106">Pokud však používáte databázi NoSQL, zejména databázi orientovanou na dokumenty, jako je Azure Cosmos DB, CouchDB nebo RavenDB, způsob návrhu modelu s agregacemi DDD je částečně podobný tomu, jak to můžete provést v EF Core, pokud jde o identifikaci agregačních kořenů, tříd podřízených entit a tříd hodnotových objektů.</span><span class="sxs-lookup"><span data-stu-id="6152e-106">However, when you use a NoSQL database, especially a document-oriented database like Azure Cosmos DB, CouchDB, or RavenDB, the way you design your model with DDD aggregates is partially similar to how you can do it in EF Core, in regards to the identification of aggregate roots, child entity classes, and value object classes.</span></span> <span data-ttu-id="6152e-107">Ale nakonec výběr databáze bude mít vliv na váš návrh.</span><span class="sxs-lookup"><span data-stu-id="6152e-107">But, ultimately, the database selection will impact in your design.</span></span>

<span data-ttu-id="6152e-108">Při použití databáze orientované na dokumenty implementujete agregaci jako jeden dokument serializovaný v JSON nebo jiném formátu.</span><span class="sxs-lookup"><span data-stu-id="6152e-108">When you use a document-oriented database, you implement an aggregate as a single document, serialized in JSON or another format.</span></span> <span data-ttu-id="6152e-109">Použití databáze je však transparentní z hlediska kódu modelu domény.</span><span class="sxs-lookup"><span data-stu-id="6152e-109">However, the use of the database is transparent from a domain model code point of view.</span></span> <span data-ttu-id="6152e-110">Při použití databáze NoSQL stále používáte třídy entit a agregační kořenové třídy, ale s větší flexibilitou než při použití EF Core, protože perzistence není relační.</span><span class="sxs-lookup"><span data-stu-id="6152e-110">When using a NoSQL database, you still are using entity classes and aggregate root classes, but with more flexibility than when using EF Core because the persistence is not relational.</span></span>

<span data-ttu-id="6152e-111">Rozdíl je v tom, jak zachovat tento model.</span><span class="sxs-lookup"><span data-stu-id="6152e-111">The difference is in how you persist that model.</span></span> <span data-ttu-id="6152e-112">Pokud jste implementovali model domény na základě tříd entit POCO, agnostik k přetrvávání infrastruktury, může to vypadat, že byste se mohli přesunout do jiné infrastruktury trvalosti, dokonce i z relační na NoSQL.</span><span class="sxs-lookup"><span data-stu-id="6152e-112">If you implemented your domain model based on POCO entity classes, agnostic to the infrastructure persistence, it might look like you could move to a different persistence infrastructure, even from relational to NoSQL.</span></span> <span data-ttu-id="6152e-113">To by však neměl být vaším cílem.</span><span class="sxs-lookup"><span data-stu-id="6152e-113">However, that should not be your goal.</span></span> <span data-ttu-id="6152e-114">V různých databázových technologiích vždy existují omezení a kompromisy, takže nebudete moci mít stejný model pro relační nebo NoSQL databáze.</span><span class="sxs-lookup"><span data-stu-id="6152e-114">There are always constraints and trade-offs in the different database technologies, so you will not be able to have the same model for relational or NoSQL databases.</span></span> <span data-ttu-id="6152e-115">Změna modelů trvalosti není triviální úkol, protože transakce a operace trvalosti se budou velmi lišit.</span><span class="sxs-lookup"><span data-stu-id="6152e-115">Changing persistence models is not a trivial task, because transactions and persistence operations will be very different.</span></span>

<span data-ttu-id="6152e-116">Například v databázi orientované na dokument je v pořádku, aby agregační kořen měl více vlastností podřízené kolekce.</span><span class="sxs-lookup"><span data-stu-id="6152e-116">For example, in a document-oriented database, it is okay for an aggregate root to have multiple child collection properties.</span></span> <span data-ttu-id="6152e-117">V relační databázi dotazování více podřízených vlastností kolekce není snadno optimalizovat, protože získáte příkaz UNION ALL SQL zpět z EF.</span><span class="sxs-lookup"><span data-stu-id="6152e-117">In a relational database, querying multiple child collection properties is not easily optimized, because you get a UNION ALL SQL statement back from EF.</span></span> <span data-ttu-id="6152e-118">Mít stejný model domény pro relační databáze nebo NoSQL databáze není jednoduché a neměli byste se o to pokoušet.</span><span class="sxs-lookup"><span data-stu-id="6152e-118">Having the same domain model for relational databases or NoSQL databases is not simple, and you should not try to do it.</span></span> <span data-ttu-id="6152e-119">Opravdu musíte navrhnout model s pochopením toho, jak budou data použita v každé konkrétní databázi.</span><span class="sxs-lookup"><span data-stu-id="6152e-119">You really have to design your model with an understanding of how the data is going to be used in each particular database.</span></span>

<span data-ttu-id="6152e-120">Výhodou při použití nosql databází je, že entity jsou více denormalized, takže není nastaveno mapování tabulky.</span><span class="sxs-lookup"><span data-stu-id="6152e-120">A benefit when using NoSQL databases is that the entities are more denormalized, so you do not set a table mapping.</span></span> <span data-ttu-id="6152e-121">Model domény může být flexibilnější než při použití relační databáze.</span><span class="sxs-lookup"><span data-stu-id="6152e-121">Your domain model can be more flexible than when using a relational database.</span></span>

<span data-ttu-id="6152e-122">Při návrhu modelu domény na základě agregace, přechod na NoSQL a databáze orientované na dokumenty může být ještě jednodušší než pomocí relační databáze, protože agregáty, které navrhujete, jsou podobné serializovaných dokumentů v databázi orientované na dokumenty.</span><span class="sxs-lookup"><span data-stu-id="6152e-122">When you design your domain model based on aggregates, moving to NoSQL and document-oriented databases might be even easier than using a relational database, because the aggregates you design are similar to serialized documents in a document-oriented database.</span></span> <span data-ttu-id="6152e-123">Pak můžete zahrnout do těchto "tašky" všechny informace, které byste mohli potřebovat pro tento agregát.</span><span class="sxs-lookup"><span data-stu-id="6152e-123">Then you can include in those "bags" all the information you might need for that aggregate.</span></span>

<span data-ttu-id="6152e-124">Například následující kód JSON je ukázkovou implementací agregace pořadí při použití databáze orientované na dokumenty.</span><span class="sxs-lookup"><span data-stu-id="6152e-124">For instance, the following JSON code is a sample implementation of an order aggregate when using a document-oriented database.</span></span> <span data-ttu-id="6152e-125">Je to podobné pořadí agregace jsme implementovali v eShopOnContainers vzorku, ale bez použití EF Core pod.</span><span class="sxs-lookup"><span data-stu-id="6152e-125">It is similar to the order aggregate we implemented in the eShopOnContainers sample, but without using EF Core underneath.</span></span>

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

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a><span data-ttu-id="6152e-126">Úvod do Azure Cosmos DB a nativního rozhraní COSMOS DB API</span><span class="sxs-lookup"><span data-stu-id="6152e-126">Introduction to Azure Cosmos DB and the native Cosmos DB API</span></span>

<span data-ttu-id="6152e-127">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) je globálně distribuovaná databázová služba Microsoftu pro klíčové aplikace.</span><span class="sxs-lookup"><span data-stu-id="6152e-127">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) is Microsoft's globally distributed database service for mission-critical applications.</span></span> <span data-ttu-id="6152e-128">Azure Cosmos DB poskytuje [globální distribuci na klíč](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [elastické škálování propustnosti a úložiště](https://docs.microsoft.com/azure/cosmos-db/partition-data) po celém světě, latence v řádu milisekund na 99. percentilu, [pět jasně definovaných úrovní konzistence](https://docs.microsoft.com/azure/cosmos-db/consistency-levels) a zaručenou vysokou dostupnost. To vše je podloženo [nejlepšími smlouvami SLA v oboru](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span><span class="sxs-lookup"><span data-stu-id="6152e-128">Azure Cosmos DB provides [turn-key global distribution](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [elastic scaling of throughput and storage](https://docs.microsoft.com/azure/cosmos-db/partition-data) worldwide, single-digit millisecond latencies at the 99th percentile, [five well-defined consistency levels](https://docs.microsoft.com/azure/cosmos-db/consistency-levels), and guaranteed high availability, all backed by [industry-leading SLAs](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span></span> <span data-ttu-id="6152e-129">Azure Cosmos DB [automaticky indexuje data](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf), aniž by vyžadovala zapojení správy schémat a indexů.</span><span class="sxs-lookup"><span data-stu-id="6152e-129">Azure Cosmos DB [automatically indexes data](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) without requiring you to deal with schema and index management.</span></span> <span data-ttu-id="6152e-130">Zahrnuje více modelů a podporuje modely dokumentů, klíčových hodnot, grafů a sloupcových dat.</span><span class="sxs-lookup"><span data-stu-id="6152e-130">It is multi-model and supports document, key-value, graph, and columnar data models.</span></span>

![Diagram znázorňující globální distribuci Azure Cosmos DB.](./media/nosql-database-persistence-infrastructure/azure-cosmos-db-global-distribution.png)

<span data-ttu-id="6152e-132">**Obrázek 7-19**.</span><span class="sxs-lookup"><span data-stu-id="6152e-132">**Figure 7-19**.</span></span> <span data-ttu-id="6152e-133">Globální distribuce služby Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="6152e-133">Azure Cosmos DB global distribution</span></span>

<span data-ttu-id="6152e-134">Při použití modelu\# C k implementaci agregace, které mají být použity rozhraní\# API Azure Cosmos DB, agregace může být podobná C POCO třídy používané s EF Core.</span><span class="sxs-lookup"><span data-stu-id="6152e-134">When you use a C\# model to implement the aggregate to be used by the Azure Cosmos DB API, the aggregate can be similar to the C\# POCO classes used with EF Core.</span></span> <span data-ttu-id="6152e-135">Rozdíl je ve způsobu jejich použití z vrstev aplikace a infrastruktury, jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="6152e-135">The difference is in the way to use them from the application and infrastructure layers, as in the following code:</span></span>

```csharp
// C# EXAMPLE OF AN ORDER AGGREGATE BEING PERSISTED WITH AZURE COSMOS DB API
// *** Domain Model Code ***
// Aggregate: Create an Order object with its child entities and/or value objects.
// Then, use AggregateRoot's methods to add the nested objects so invariants and
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

<span data-ttu-id="6152e-136">Můžete vidět, že způsob práce s modelem domény může být podobný způsobu, jakým jej používáte ve vrstvě modelu domény, když je infrastruktura EF.</span><span class="sxs-lookup"><span data-stu-id="6152e-136">You can see that the way you work with your domain model can be similar to the way you use it in your domain model layer when the infrastructure is EF.</span></span> <span data-ttu-id="6152e-137">Stále používáte stejné agregační kořenové metody k zajištění konzistence, invariants a ověření v rámci agregace.</span><span class="sxs-lookup"><span data-stu-id="6152e-137">You still use the same aggregate root methods to ensure consistency, invariants, and validations within the aggregate.</span></span>

<span data-ttu-id="6152e-138">Však při zachování modelu do databáze NoSQL, kód a rozhraní API změnit dramaticky ve srovnání s EF základní kód nebo jakýkoli jiný kód související s relační databáze.</span><span class="sxs-lookup"><span data-stu-id="6152e-138">However, when you persist your model into the NoSQL database, the code and API change dramatically compared to EF Core code or any other code related to relational databases.</span></span>

## <a name="implement-net-code-targeting-mongodb-and-azure-cosmos-db"></a><span data-ttu-id="6152e-139">Implementace kódu .NET cílení MongoDB a Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="6152e-139">Implement .NET code targeting MongoDB and Azure Cosmos DB</span></span>

### <a name="use-azure-cosmos-db-from-net-containers"></a><span data-ttu-id="6152e-140">Použití azure cosmos db z kontejnerů .NET</span><span class="sxs-lookup"><span data-stu-id="6152e-140">Use Azure Cosmos DB from .NET containers</span></span>

<span data-ttu-id="6152e-141">K databázím Azure Cosmos DB můžete přistupovat z kódu .NET spuštěného v kontejnerech, stejně jako z jakékoli jiné aplikace .NET.</span><span class="sxs-lookup"><span data-stu-id="6152e-141">You can access Azure Cosmos DB databases from .NET code running in containers, like from any other .NET application.</span></span> <span data-ttu-id="6152e-142">Například microservices Locations.API a Marketing.API v eShopOnContainers jsou implementovány tak, aby mohly využívat databáze Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="6152e-142">For instance, the Locations.API and Marketing.API microservices in eShopOnContainers are implemented so they can consume Azure Cosmos DB databases.</span></span>

<span data-ttu-id="6152e-143">Existuje však omezení v Azure Cosmos DB z hlediska vývojového prostředí Dockeru.</span><span class="sxs-lookup"><span data-stu-id="6152e-143">However, there’s a limitation in Azure Cosmos DB from a Docker development environment point of view.</span></span> <span data-ttu-id="6152e-144">I když existuje místní [emulátor Azure Cosmos DB,](https://docs.microsoft.com/azure/cosmos-db/local-emulator) který se dá spouštět v místním vývojovém počítači, podporuje jenom Windows.</span><span class="sxs-lookup"><span data-stu-id="6152e-144">Even though there’s an on-premises [Azure Cosmos DB Emulator](https://docs.microsoft.com/azure/cosmos-db/local-emulator) that can run in a local development machine, it only supports Windows.</span></span> <span data-ttu-id="6152e-145">Linux a macOS nejsou podporované.</span><span class="sxs-lookup"><span data-stu-id="6152e-145">Linux and macOS aren't supported.</span></span>

<span data-ttu-id="6152e-146">K dispozici je také možnost spustit tento emulátor na Dockeru, ale pouze na kontejnerech Windows, nikoli s kontejnery Linux.</span><span class="sxs-lookup"><span data-stu-id="6152e-146">There's also the possibility to run this emulator on Docker, but just on Windows Containers, not with Linux Containers.</span></span> <span data-ttu-id="6152e-147">To je počáteční nevýhoda pro vývojové prostředí, pokud je vaše aplikace nasazená jako kontejnery Linuxu, protože v současné době nemůžete nasadit linuxové a windows kontejnery v Dockeru pro Windows současně.</span><span class="sxs-lookup"><span data-stu-id="6152e-147">That's an initial handicap for the development environment if your application is deployed as Linux containers, since, currently, you can't deploy Linux and Windows Containers on Docker for Windows at the same time.</span></span> <span data-ttu-id="6152e-148">Buď všechny nasazené kontejnery musí být pro Linux nebo pro Windows.</span><span class="sxs-lookup"><span data-stu-id="6152e-148">Either all containers being deployed have to be for Linux or for Windows.</span></span>

<span data-ttu-id="6152e-149">Ideální a jednodušší nasazení pro řešení pro vývoj a testování je možnost nasadit databázové systémy jako kontejnery spolu s vlastní kontejnery, takže vaše vývojová a testovací prostředí jsou vždy konzistentní.</span><span class="sxs-lookup"><span data-stu-id="6152e-149">The ideal and more straightforward deployment for a dev/test solution is to be able to deploy your database systems as containers along with your custom containers so your dev/test environments are always consistent.</span></span>

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a><span data-ttu-id="6152e-150">Použití rozhraní MongoDB API pro místní vývoj a testování kontejnerů linux/windows plus Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="6152e-150">Use MongoDB API for local dev/test Linux/Windows containers plus Azure Cosmos DB</span></span>

<span data-ttu-id="6152e-151">Databáze Cosmos DB podporují rozhraní MongoDB API pro rozhraní .NET i nativní drátový protokol MongoDB.</span><span class="sxs-lookup"><span data-stu-id="6152e-151">Cosmos DB databases support MongoDB API for .NET as well as the native MongoDB wire protocol.</span></span> <span data-ttu-id="6152e-152">To znamená, že pomocí existujícíovladače, aplikace napsané pro MongoDB nyní můžete komunikovat s Cosmos DB a používat databáze Cosmos DB namísto databáze MongoDB, jak je znázorněno na obrázku 7-20.</span><span class="sxs-lookup"><span data-stu-id="6152e-152">This means that by using existing drivers, your application written for MongoDB can now communicate with Cosmos DB and use Cosmos DB databases instead of MongoDB databases, as shown in Figure 7-20.</span></span>

![Diagram znázorňující, že Cosmos DB podporuje .NET a MongoDB drátový protokol.](./media/nosql-database-persistence-infrastructure/mongodb-api-wire-protocol.png)

<span data-ttu-id="6152e-154">**Obrázek 7-20**.</span><span class="sxs-lookup"><span data-stu-id="6152e-154">**Figure 7-20**.</span></span> <span data-ttu-id="6152e-155">Použití rozhraní MongoDB API a protokolu pro přístup k Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="6152e-155">Using MongoDB API and protocol to access Azure Cosmos DB</span></span>

<span data-ttu-id="6152e-156">Toto je velmi pohodlný přístup pro prokazované koncepty v prostředí dockeru s kontejnery Linux, protože [image MongoDB Docker](https://hub.docker.com/r/_/mongo/) je víceoblouková image, která podporuje kontejnery Docker Linux a kontejnery Docker Windows.</span><span class="sxs-lookup"><span data-stu-id="6152e-156">This is a very convenient approach for proof of concepts in Docker environments with Linux containers because the [MongoDB Docker image](https://hub.docker.com/r/_/mongo/) is a multi-arch image that supports Docker Linux containers and Docker Windows containers.</span></span>

<span data-ttu-id="6152e-157">Jak je znázorněno na následujícím obrázku, pomocí rozhraní MongoDB API eShopOnContainers podporuje kontejnery MongoDB Linux a Windows pro místní vývojové prostředí, ale pak se můžete přesunout do škálovatelného cloudového řešení PaaS jako Azure Cosmos DB jednoduše [změnou připojovacího řetězce MongoDB na odkaz Na Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="6152e-157">As shown in the following image, by using the MongoDB API, eShopOnContainers supports MongoDB Linux and Windows containers for the local development environment but then, you can move to a scalable, PaaS cloud solution as Azure Cosmos DB by simply [changing the MongoDB connection string to point to Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span></span>

![Diagram znázorňující, že umístění mikroslužby v eShopOnContainers můžete použít buď Cosmos DB nebo Mongo DB.](./media/nosql-database-persistence-infrastructure/eshoponcontainers-mongodb-containers.png)

<span data-ttu-id="6152e-159">**Obrázek 7-21**.</span><span class="sxs-lookup"><span data-stu-id="6152e-159">**Figure 7-21**.</span></span> <span data-ttu-id="6152e-160">eShopOnContainers pomocí kontejnerů MongoDB pro dev-env nebo Azure Cosmos DB pro produkční prostředí</span><span class="sxs-lookup"><span data-stu-id="6152e-160">eShopOnContainers using MongoDB containers for dev-env or Azure Cosmos DB for production</span></span>

<span data-ttu-id="6152e-161">Produkční Azure Cosmos DB by běželv cloudu Azure jako PaaS a škálovatelné služby.</span><span class="sxs-lookup"><span data-stu-id="6152e-161">The production Azure Cosmos DB would be running in Azure's cloud as a PaaS and scalable service.</span></span>

<span data-ttu-id="6152e-162">Vaše vlastní kontejnery .NET Core můžou běžet na místním vývojovém hostiteli Dockeru (který používá Docker pro Windows v počítači s Windows 10) nebo se nasadit do produkčního prostředí, jako je Kubernetes v Azure AKS nebo Azure Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="6152e-162">Your custom .NET Core containers can run on a local development Docker host (that is using Docker for Windows in a Windows 10 machine) or be deployed into a production environment, like Kubernetes in Azure AKS or Azure Service Fabric.</span></span> <span data-ttu-id="6152e-163">V tomto druhém prostředí byste nasadili pouze vlastní kontejnery .NET Core, ale ne kontejner MongoDB, protože byste používali Azure Cosmos DB v cloudu pro zpracování dat v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="6152e-163">In this second environment, you would deploy only the .NET Core custom containers but not the MongoDB container since you'd be using Azure Cosmos DB in the cloud for handling the data in production.</span></span>

<span data-ttu-id="6152e-164">Jasnou výhodou použití rozhraní MongoDB API je, že vaše řešení může běžet v databázových strojích, MongoDB nebo Azure Cosmos DB, takže migrace do různých prostředí by měla být snadná.</span><span class="sxs-lookup"><span data-stu-id="6152e-164">A clear benefit of using the MongoDB API is that your solution could run in both database engines, MongoDB or Azure Cosmos DB, so migrations to different environments should be easy.</span></span> <span data-ttu-id="6152e-165">Někdy však stojí za to použít nativní rozhraní API (to je nativní rozhraní API Cosmos DB), aby bylo možné plně využít možnosti konkrétního databázového stroje.</span><span class="sxs-lookup"><span data-stu-id="6152e-165">However, sometimes it is worthwhile to use a native API (that is the native Cosmos DB API) in order to take full advantage of the capabilities of a specific database engine.</span></span>

<span data-ttu-id="6152e-166">Další porovnání mezi jednoduše pomocí MongoDB versus Cosmos DB v cloudu, najdete [v tématu výhody používání Azure Cosmos DB na této stránce](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction).</span><span class="sxs-lookup"><span data-stu-id="6152e-166">For further comparison between simply using MongoDB versus Cosmos DB in the cloud, see the [Benefits of using Azure Cosmos DB in this page](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction).</span></span>

### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a><span data-ttu-id="6152e-167">Analyzujte svůj přístup k produkčním aplikacím: MongoDB API vs. Cosmos DB API</span><span class="sxs-lookup"><span data-stu-id="6152e-167">Analyze your approach for production applications: MongoDB API vs. Cosmos DB API</span></span>

<span data-ttu-id="6152e-168">V eShopOnContainers používáme rozhraní MongoDB API, protože naší prioritou bylo zásadně mít konzistentní prostředí pro vývoj a testování pomocí databáze NoSQL, která by mohla fungovat i s Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="6152e-168">In eShopOnContainers, we're using MongoDB API because our priority was fundamentally to have a consistent dev/test environment using a NoSQL database that could also work with Azure Cosmos DB.</span></span>

<span data-ttu-id="6152e-169">Pokud ale plánujete používat rozhraní MongoDB API pro přístup k Azure Cosmos DB v Azure pro produkční aplikace, měli byste analyzovat rozdíly ve schopnostech a výkonu při použití rozhraní API MongoDB pro přístup k databázím Azure Cosmos DB ve srovnání s použitím nativního rozhraní API Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="6152e-169">However, if you planning to use MongoDB API to access Azure Cosmos DB in Azure for production applications, you should analyze the differences in capabilities and performance when using MongoDB API to access Azure Cosmos DB databases compared to using the native Azure Cosmos DB API.</span></span> <span data-ttu-id="6152e-170">Pokud je to podobné, můžete použít MongoDB API a získáte výhodu podpory dvou databázových strojů NoSQL současně.</span><span class="sxs-lookup"><span data-stu-id="6152e-170">If it is similar you can use MongoDB API and you get the benefit of supporting two NoSQL database engines at the same time.</span></span>

<span data-ttu-id="6152e-171">Clustery MongoDB můžete také použít jako produkční databázi v cloudu Azure také se [službou MongoDB Azure Service](https://www.mongodb.com/scale/mongodb-azure-service).</span><span class="sxs-lookup"><span data-stu-id="6152e-171">You could also use MongoDB clusters as the production database in Azure's cloud, too, with [MongoDB Azure Service](https://www.mongodb.com/scale/mongodb-azure-service).</span></span> <span data-ttu-id="6152e-172">Ale to není služba PaaS poskytovaná společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6152e-172">But that is not a PaaS service provided by Microsoft.</span></span> <span data-ttu-id="6152e-173">V tomto případě Azure právě hostuje toto řešení pocházející z MongoDB.</span><span class="sxs-lookup"><span data-stu-id="6152e-173">In this case, Azure is just hosting that solution coming from MongoDB.</span></span>

<span data-ttu-id="6152e-174">V podstatě je to jen prohlášení o tom, že byste neměli vždy používat rozhraní MongoDB API proti Azure Cosmos DB, jako jsme to udělali v eShopOnContainers, protože to byla vhodná volba pro linuxové kontejnery.</span><span class="sxs-lookup"><span data-stu-id="6152e-174">Basically, this is just a disclaimer stating that you shouldn't always use MongoDB API against Azure Cosmos DB, as we did in eShopOnContainers because it was a convenient choice for Linux containers.</span></span> <span data-ttu-id="6152e-175">Rozhodnutí by mělo být založeno na konkrétních potřebách a testech, které je třeba provést pro produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6152e-175">The decision should be based on the specific needs and tests you need to do for your production application.</span></span>

### <a name="the-code-use-mongodb-api-in-net-core-applications"></a><span data-ttu-id="6152e-176">Kód: Použití rozhraní MongoDB API v aplikacích .NET Core</span><span class="sxs-lookup"><span data-stu-id="6152e-176">The code: Use MongoDB API in .NET Core applications</span></span>

<span data-ttu-id="6152e-177">MongoDB API pro rozhraní .NET je založen na balíčcích NuGet, které je potřeba přidat do vašich projektů, jako v projektu Locations.API zobrazeném na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="6152e-177">MongoDB API for .NET is based on NuGet packages that you need to add to your projects, like in the Locations.API project shown in the following figure.</span></span>

![Snímek obrazovky závislostí v balíčcích MongoDB NuGet.](./media/nosql-database-persistence-infrastructure/mongodb-api-nuget-packages.png)

<span data-ttu-id="6152e-179">**Obrázek 7-22**.</span><span class="sxs-lookup"><span data-stu-id="6152e-179">**Figure 7-22**.</span></span> <span data-ttu-id="6152e-180">Odkazy na balíčky MongoDB API NuGet v projektu .NET Core</span><span class="sxs-lookup"><span data-stu-id="6152e-180">MongoDB API NuGet packages references in a .NET Core project</span></span>

<span data-ttu-id="6152e-181">Pojďme prozkoumat kód v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="6152e-181">Let's investigate the code in the following sections.</span></span>

#### <a name="a-model-used-by-mongodb-api"></a><span data-ttu-id="6152e-182">Model používaný rozhraním MongoDB API</span><span class="sxs-lookup"><span data-stu-id="6152e-182">A Model used by MongoDB API</span></span>

<span data-ttu-id="6152e-183">Nejprve je třeba definovat model, který bude obsahovat data pocházející z databáze v paměťovém prostoru aplikace.</span><span class="sxs-lookup"><span data-stu-id="6152e-183">First, you need to define a model that will hold the data coming from the database in your application's memory space.</span></span> <span data-ttu-id="6152e-184">Tady je příklad modelu používaného pro umístění v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="6152e-184">Here's an example of the model used for Locations at eShopOnContainers.</span></span>

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

<span data-ttu-id="6152e-185">Můžete vidět, že existuje několik atributů a typů pocházejících z balíčků MongoDB NuGet.</span><span class="sxs-lookup"><span data-stu-id="6152e-185">You can see there are a few attributes and types coming from the MongoDB NuGet packages.</span></span>

<span data-ttu-id="6152e-186">NoSQL databáze jsou obvykle velmi vhodné pro práci s non-relačníhierarchická data.</span><span class="sxs-lookup"><span data-stu-id="6152e-186">NoSQL databases are usually very well suited for working with non-relational hierarchical data.</span></span> <span data-ttu-id="6152e-187">V tomto příkladu používáme typy MongoDB speciálně `GeoJson2DGeographicCoordinates`pro geografické lokality, jako je .</span><span class="sxs-lookup"><span data-stu-id="6152e-187">In this example, we are using MongoDB types especially made for geo-locations, like `GeoJson2DGeographicCoordinates`.</span></span>

#### <a name="retrieve-the-database-and-the-collection"></a><span data-ttu-id="6152e-188">Načíst databázi a kolekci</span><span class="sxs-lookup"><span data-stu-id="6152e-188">Retrieve the database and the collection</span></span>

<span data-ttu-id="6152e-189">V eShopOnContainers jsme vytvořili vlastní kontext databáze, kde implementujeme kód pro načtení databáze a MongoCollections, jako v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="6152e-189">In eShopOnContainers, we have created a custom database context where we implement the code to retrieve the database and the MongoCollections, as in the following code.</span></span>

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

#### <a name="retrieve-the-data"></a><span data-ttu-id="6152e-190">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="6152e-190">Retrieve the data</span></span>

<span data-ttu-id="6152e-191">V kódu Jazyka C#, jako jsou řadiče webového rozhraní API nebo implementace vlastních úložišť, můžete při dotazování prostřednictvím rozhraní MONGODB API napsat podobný kód následujícímu.</span><span class="sxs-lookup"><span data-stu-id="6152e-191">In C# code, like Web API controllers or custom Repositories implementation, you can write similar code to the following when querying through the MongoDB API.</span></span> <span data-ttu-id="6152e-192">Všimněte `_context` si, že objekt `LocationsContext` je instancí předchozí třídy.</span><span class="sxs-lookup"><span data-stu-id="6152e-192">Note that the `_context` object is an instance of the previous `LocationsContext` class.</span></span>

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a><span data-ttu-id="6152e-193">Použití env-var v souboru docker-compose.override.yml pro připojovací řetězec MongoDB</span><span class="sxs-lookup"><span data-stu-id="6152e-193">Use an env-var in the docker-compose.override.yml file for the MongoDB connection string</span></span>

<span data-ttu-id="6152e-194">Při vytváření objektu MongoClient potřebuje základní parametr, `ConnectionString` který je přesně parametr směřující na správnou databázi.</span><span class="sxs-lookup"><span data-stu-id="6152e-194">When creating a MongoClient object, it needs a fundamental parameter which is precisely the `ConnectionString` parameter pointing to the right database.</span></span> <span data-ttu-id="6152e-195">V případě eShopOnContainers může připojovací řetězec směřovat na místní kontejner MongoDB Docker nebo na "produkční" databázi Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="6152e-195">In the case of eShopOnContainers, the connection string can point to a local MongoDB Docker container or to a "production" Azure Cosmos DB database.</span></span>  <span data-ttu-id="6152e-196">Tento připojovací řetězec pochází z `docker-compose.override.yml` proměnných prostředí definovaných v souborech používaných při nasazování s docker-compose nebo Visual Studio, jako v následujícím kódu yml.</span><span class="sxs-lookup"><span data-stu-id="6152e-196">That connection string comes from the environment variables defined in the `docker-compose.override.yml` files used when deploying with docker-compose or Visual Studio, as in the following yml code.</span></span>

```yml
# docker-compose.override.yml
version: '3.4'
services:
  # Other services
  locations-api:
    environment:
      # Other settings
      - ConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosqldata}

```

<span data-ttu-id="6152e-197">Proměnná `ConnectionString` prostředí je vyřešena `ESHOP_AZURE_COSMOSDB` takto: Pokud `.env` je globální proměnná definována v souboru pomocí připojovacího řetězce Azure Cosmos DB, použije ji pro přístup k databázi Azure Cosmos DB v cloudu.</span><span class="sxs-lookup"><span data-stu-id="6152e-197">The `ConnectionString` environment variable is resolved this way: If the `ESHOP_AZURE_COSMOSDB` global variable is defined in the `.env` file with the Azure Cosmos DB connection string, it will use it to access the Azure Cosmos DB database in the cloud.</span></span> <span data-ttu-id="6152e-198">Pokud není definována, bude trvat hodnotu `mongodb://nosqldata` a použít vývoj MongoDB kontejneru.</span><span class="sxs-lookup"><span data-stu-id="6152e-198">If it’s not defined, it will take the `mongodb://nosqldata` value and use the development MongoDB container.</span></span>

<span data-ttu-id="6152e-199">Následující kód zobrazuje `.env` soubor s proměnnou globálního prostředí připojovacího řetězce Azure Cosmos DB, jak je implementováno v eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="6152e-199">The following code shows the `.env` file with the Azure Cosmos DB connection string global environment variable, as implemented in eShopOnContainers:</span></span>

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

<span data-ttu-id="6152e-200">Odkomentujte ESHOP_AZURE_COSMOSDB řádek a aktualizujte ho pomocí připojovacího řetězce Azure Cosmos DB získaného z portálu Azure, jak je vysvětleno v [části Připojení aplikace MongoDB k Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="6152e-200">Uncomment the ESHOP_AZURE_COSMOSDB line and update it with your Azure Cosmos DB connection string obtained from the Azure portal as explained in [Connect a MongoDB application to Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span></span>

<span data-ttu-id="6152e-201">Pokud `ESHOP_AZURE_COSMOSDB` je globální proměnná prázdná, což znamená, že je v souboru `.env` zakomentována, pak kontejner používá výchozí připojovací řetězec MongoDB.</span><span class="sxs-lookup"><span data-stu-id="6152e-201">If the `ESHOP_AZURE_COSMOSDB` global variable is empty, meaning it's commented out in the `.env` file, then the container uses a default MongoDB connection string.</span></span> <span data-ttu-id="6152e-202">Tento připojovací řetězec odkazuje na místní kontejner MongoDB `nosqldata` nasazený v eShopOnContainers, který je pojmenován a definován v souboru docker-compose, jak je znázorněno v následujícím kódu .yml:</span><span class="sxs-lookup"><span data-stu-id="6152e-202">This connection string points to the local MongoDB container deployed in eShopOnContainers that is named `nosqldata` and was defined at the docker-compose file, as shown in the following .yml code:</span></span>

``` yml
# docker-compose.yml
version: '3.4'
services:
  # ...Other services...
  nosqldata:
    image: mongo
```

#### <a name="additional-resources"></a><span data-ttu-id="6152e-203">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="6152e-203">Additional resources</span></span>

- <span data-ttu-id="6152e-204">**Modelování dat dokumentů pro databáze NoSQL** </span><span class="sxs-lookup"><span data-stu-id="6152e-204">**Modeling document data for NoSQL databases** </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/modeling-data>

- <span data-ttu-id="6152e-205">**Vaughn Vernon, to je můj zástupce. Ideální domény-řízený design agregát obchod?**</span><span class="sxs-lookup"><span data-stu-id="6152e-205">**Vaughn Vernon. The Ideal Domain-Driven Design Aggregate Store?**</span></span> \
  <https://kalele.io/blog-posts/the-ideal-domain-driven-design-aggregate-store/>

- <span data-ttu-id="6152e-206">**Úvod do Azure Cosmos DB: ROZHRANÍ API pro MongoDB**  </span><span class="sxs-lookup"><span data-stu-id="6152e-206">**Introduction to Azure Cosmos DB: API for MongoDB**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction>

- <span data-ttu-id="6152e-207">**Azure Cosmos DB: Vytvoření webové aplikace rozhraní API MongoDB s rozhraním .NET a portálem Azure**  </span><span class="sxs-lookup"><span data-stu-id="6152e-207">**Azure Cosmos DB: Build a MongoDB API web app with .NET and the Azure portal**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet>

- <span data-ttu-id="6152e-208">**Použití emulátoru Azure Cosmos DB pro místní vývoj a testování**  </span><span class="sxs-lookup"><span data-stu-id="6152e-208">**Use the Azure Cosmos DB Emulator for local development and testing**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/local-emulator>

- <span data-ttu-id="6152e-209">**Připojení aplikace MongoDB k Azure Cosmos DB**  </span><span class="sxs-lookup"><span data-stu-id="6152e-209">**Connect a MongoDB application to Azure Cosmos DB**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account>

- <span data-ttu-id="6152e-210">**Image Cosmos DB Emulátor Docker (Windows Container)**  </span><span class="sxs-lookup"><span data-stu-id="6152e-210">**The Cosmos DB Emulator Docker image (Windows Container)**  </span></span>\
  <https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/>

- <span data-ttu-id="6152e-211">**Image MongoDB Docker (Linux a Windows Container)**  </span><span class="sxs-lookup"><span data-stu-id="6152e-211">**The MongoDB Docker image (Linux and Windows Container)**  </span></span>\
  <https://hub.docker.com/_/mongo/>

- <span data-ttu-id="6152e-212">**Použití MongoChefa (Studio 3T) s Azure Cosmos DB: API pro účet MongoDB**  </span><span class="sxs-lookup"><span data-stu-id="6152e-212">**Use MongoChef (Studio 3T) with an Azure Cosmos DB: API for MongoDB account**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-mongochef>

>[!div class="step-by-step"]
><span data-ttu-id="6152e-213">[Předchozí](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
>[další](microservice-application-layer-web-api-design.md)</span><span class="sxs-lookup"><span data-stu-id="6152e-213">[Previous](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
[Next](microservice-application-layer-web-api-design.md)</span></span>
