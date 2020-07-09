---
title: Použití databází NoSQL jako infrastruktury trvalosti
description: Pochopení použití databází NoSql obecně a Azure Cosmos DB zejména jako možnosti implementace trvalosti.
ms.date: 01/30/2020
ms.openlocfilehash: a478809895b0c20824f08f20558f2d47e10223d0
ms.sourcegitcommit: 4ad2f8920251f3744240c3b42a443ffbe0a46577
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/08/2020
ms.locfileid: "86100805"
---
# <a name="use-nosql-databases-as-a-persistence-infrastructure"></a><span data-ttu-id="1399f-103">Použití databází NoSQL jako infrastruktury trvalosti</span><span class="sxs-lookup"><span data-stu-id="1399f-103">Use NoSQL databases as a persistence infrastructure</span></span>

<span data-ttu-id="1399f-104">Pokud pro vrstvu dat infrastruktury používáte databáze NoSQL, obvykle nepoužíváte ORM, jako je Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="1399f-104">When you use NoSQL databases for your infrastructure data tier, you typically do not use an ORM like Entity Framework Core.</span></span> <span data-ttu-id="1399f-105">Místo toho použijete rozhraní API poskytované modulem NoSQL, jako jsou například Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB nebo Azure Storage tabulky.</span><span class="sxs-lookup"><span data-stu-id="1399f-105">Instead you use the API provided by the NoSQL engine, such as Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB, or Azure Storage Tables.</span></span>

<span data-ttu-id="1399f-106">Pokud však použijete databázi NoSQL, zejména databázi orientovaný na dokumenty, jako je například Azure Cosmos DB, CouchDB nebo RavenDB, způsob návrhu modelu s DDD agregovanými hodnotami je částečně podobný tomu, jak to lze provést v EF Core, v souvislosti s identifikací agregačních kořenových adresářů, podřízených tříd entit a hodnotových tříd objektů.</span><span class="sxs-lookup"><span data-stu-id="1399f-106">However, when you use a NoSQL database, especially a document-oriented database like Azure Cosmos DB, CouchDB, or RavenDB, the way you design your model with DDD aggregates is partially similar to how you can do it in EF Core, in regards to the identification of aggregate roots, child entity classes, and value object classes.</span></span> <span data-ttu-id="1399f-107">Ale v konečném důsledku bude mít výběr databáze vliv na váš návrh.</span><span class="sxs-lookup"><span data-stu-id="1399f-107">But, ultimately, the database selection will impact in your design.</span></span>

<span data-ttu-id="1399f-108">Když použijete databázi orientovanou na dokument, implementujete agregaci jako jediný dokument, který je serializován ve formátu JSON nebo v jiném formátu.</span><span class="sxs-lookup"><span data-stu-id="1399f-108">When you use a document-oriented database, you implement an aggregate as a single document, serialized in JSON or another format.</span></span> <span data-ttu-id="1399f-109">Použití databáze je ale transparentní z hlediska kódu doménového modelu.</span><span class="sxs-lookup"><span data-stu-id="1399f-109">However, the use of the database is transparent from a domain model code point of view.</span></span> <span data-ttu-id="1399f-110">Při použití databáze NoSQL stále používáte třídy entit a agregované kořenové třídy, ale s větší flexibilitou než při použití EF Core, protože trvalost není relační.</span><span class="sxs-lookup"><span data-stu-id="1399f-110">When using a NoSQL database, you still are using entity classes and aggregate root classes, but with more flexibility than when using EF Core because the persistence is not relational.</span></span>

<span data-ttu-id="1399f-111">Rozdíl je v tom, jak tento model zachovat.</span><span class="sxs-lookup"><span data-stu-id="1399f-111">The difference is in how you persist that model.</span></span> <span data-ttu-id="1399f-112">Pokud jste model domény implementovali na základě tříd entit POCO, nezávislá se na trvalost infrastruktury, může to vypadat jako v případě, že se můžete přesunout do jiné infrastruktury trvalosti, a to i z relačního na NoSQL.</span><span class="sxs-lookup"><span data-stu-id="1399f-112">If you implemented your domain model based on POCO entity classes, agnostic to the infrastructure persistence, it might look like you could move to a different persistence infrastructure, even from relational to NoSQL.</span></span> <span data-ttu-id="1399f-113">To ale by nemělo být vaším cílem.</span><span class="sxs-lookup"><span data-stu-id="1399f-113">However, that should not be your goal.</span></span> <span data-ttu-id="1399f-114">Existují vždy omezení a kompromisy v různých databázových technologiích, takže nebudete mít stejný model pro relační databáze nebo databáze NoSQL.</span><span class="sxs-lookup"><span data-stu-id="1399f-114">There are always constraints and trade-offs in the different database technologies, so you will not be able to have the same model for relational or NoSQL databases.</span></span> <span data-ttu-id="1399f-115">Změna modelů trvalosti není triviální úloha, protože transakce a operace trvalého uložení budou velmi rozdílné.</span><span class="sxs-lookup"><span data-stu-id="1399f-115">Changing persistence models is not a trivial task, because transactions and persistence operations will be very different.</span></span>

<span data-ttu-id="1399f-116">Například v databázi orientované na dokument je v pořádku, aby agregovaný kořen měl více vlastností podřízené kolekce.</span><span class="sxs-lookup"><span data-stu-id="1399f-116">For example, in a document-oriented database, it is okay for an aggregate root to have multiple child collection properties.</span></span> <span data-ttu-id="1399f-117">V relační databázi se dotazování na více podřízených vlastností kolekce snadno neoptimalizuje, protože z EF získáte všechny příkazy SQL pro SJEDNOCENí.</span><span class="sxs-lookup"><span data-stu-id="1399f-117">In a relational database, querying multiple child collection properties is not easily optimized, because you get a UNION ALL SQL statement back from EF.</span></span> <span data-ttu-id="1399f-118">Stejný doménový model pro relační databáze nebo databáze NoSQL není jednoduchý a neměli byste se ho pokoušet udělat.</span><span class="sxs-lookup"><span data-stu-id="1399f-118">Having the same domain model for relational databases or NoSQL databases is not simple, and you should not try to do it.</span></span> <span data-ttu-id="1399f-119">Model budete opravdu navrhovat s porozuměním, jak se data budou používat v každé konkrétní databázi.</span><span class="sxs-lookup"><span data-stu-id="1399f-119">You really have to design your model with an understanding of how the data is going to be used in each particular database.</span></span>

<span data-ttu-id="1399f-120">Výhodou při používání databází NoSQL je to, že entity jsou více denormalizované, takže nenastavíte mapování tabulky.</span><span class="sxs-lookup"><span data-stu-id="1399f-120">A benefit when using NoSQL databases is that the entities are more denormalized, so you do not set a table mapping.</span></span> <span data-ttu-id="1399f-121">Model domény může být pružnější než při použití relační databáze.</span><span class="sxs-lookup"><span data-stu-id="1399f-121">Your domain model can be more flexible than when using a relational database.</span></span>

<span data-ttu-id="1399f-122">Při návrhu doménového modelu založeného na agregacích může být přechod na NoSQL a databáze orientované na dokument ještě snazší než použití relační databáze, protože agregované modely, které navrhujete, jsou podobné serializovaným dokumentům v databázi orientované na dokument.</span><span class="sxs-lookup"><span data-stu-id="1399f-122">When you design your domain model based on aggregates, moving to NoSQL and document-oriented databases might be even easier than using a relational database, because the aggregates you design are similar to serialized documents in a document-oriented database.</span></span> <span data-ttu-id="1399f-123">Pak můžete zahrnout do těchto "penalt" všechny informace, které můžete pro tuto agregaci potřebovat.</span><span class="sxs-lookup"><span data-stu-id="1399f-123">Then you can include in those "bags" all the information you might need for that aggregate.</span></span>

<span data-ttu-id="1399f-124">Například následující kód JSON je ukázková implementace agregační objednávky při použití databáze orientované na dokument.</span><span class="sxs-lookup"><span data-stu-id="1399f-124">For instance, the following JSON code is a sample implementation of an order aggregate when using a document-oriented database.</span></span> <span data-ttu-id="1399f-125">Je podobný agregačnímu pořadí, které jsme implementovali v ukázce eShopOnContainers, ale bez použití EF Core pod ní.</span><span class="sxs-lookup"><span data-stu-id="1399f-125">It is similar to the order aggregate we implemented in the eShopOnContainers sample, but without using EF Core underneath.</span></span>

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

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a><span data-ttu-id="1399f-126">Úvod do Azure Cosmos DB a nativní rozhraní API Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="1399f-126">Introduction to Azure Cosmos DB and the native Cosmos DB API</span></span>

<span data-ttu-id="1399f-127">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) je globálně distribuovaná databázová služba Microsoftu pro klíčové aplikace.</span><span class="sxs-lookup"><span data-stu-id="1399f-127">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) is Microsoft's globally distributed database service for mission-critical applications.</span></span> <span data-ttu-id="1399f-128">Azure Cosmos DB poskytuje [globální distribuci na klíč](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [elastické škálování propustnosti a úložiště](https://docs.microsoft.com/azure/cosmos-db/partition-data) po celém světě, latence v řádu milisekund na 99. percentilu, [pět jasně definovaných úrovní konzistence](https://docs.microsoft.com/azure/cosmos-db/consistency-levels) a zaručenou vysokou dostupnost. To vše je podloženo [nejlepšími smlouvami SLA v oboru](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span><span class="sxs-lookup"><span data-stu-id="1399f-128">Azure Cosmos DB provides [turn-key global distribution](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [elastic scaling of throughput and storage](https://docs.microsoft.com/azure/cosmos-db/partition-data) worldwide, single-digit millisecond latencies at the 99th percentile, [five well-defined consistency levels](https://docs.microsoft.com/azure/cosmos-db/consistency-levels), and guaranteed high availability, all backed by [industry-leading SLAs](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span></span> <span data-ttu-id="1399f-129">Azure Cosmos DB [automaticky indexuje data](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf), aniž by vyžadovala zapojení správy schémat a indexů.</span><span class="sxs-lookup"><span data-stu-id="1399f-129">Azure Cosmos DB [automatically indexes data](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) without requiring you to deal with schema and index management.</span></span> <span data-ttu-id="1399f-130">Zahrnuje více modelů a podporuje modely dokumentů, klíčových hodnot, grafů a sloupcových dat.</span><span class="sxs-lookup"><span data-stu-id="1399f-130">It is multi-model and supports document, key-value, graph, and columnar data models.</span></span>

![Diagram znázorňující Azure Cosmos DB globální distribuce.](./media/nosql-database-persistence-infrastructure/azure-cosmos-db-global-distribution.png)

<span data-ttu-id="1399f-132">**Obrázek 7-19**.</span><span class="sxs-lookup"><span data-stu-id="1399f-132">**Figure 7-19**.</span></span> <span data-ttu-id="1399f-133">Globální distribuce služby Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="1399f-133">Azure Cosmos DB global distribution</span></span>

<span data-ttu-id="1399f-134">Použijete-li model jazyka C \# k implementaci agregace pro použití rozhraní Azure Cosmos DB API, agregace může být podobná \# třídám jazyka c POCO použitým v EF Core.</span><span class="sxs-lookup"><span data-stu-id="1399f-134">When you use a C\# model to implement the aggregate to be used by the Azure Cosmos DB API, the aggregate can be similar to the C\# POCO classes used with EF Core.</span></span> <span data-ttu-id="1399f-135">Rozdíl je ve způsobu, jak je používat z vrstev aplikace a infrastruktury, jak je uvedeno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="1399f-135">The difference is in the way to use them from the application and infrastructure layers, as in the following code:</span></span>

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

<span data-ttu-id="1399f-136">Můžete vidět, že jak pracujete s modelem domény, může být podobný způsobu, jakým ho používáte ve vrstvě doménového modelu, pokud je to infrastruktura EF.</span><span class="sxs-lookup"><span data-stu-id="1399f-136">You can see that the way you work with your domain model can be similar to the way you use it in your domain model layer when the infrastructure is EF.</span></span> <span data-ttu-id="1399f-137">Stále používáte stejné agregační kořenové metody pro zajištění konzistence, invariant a ověření v rámci agregace.</span><span class="sxs-lookup"><span data-stu-id="1399f-137">You still use the same aggregate root methods to ensure consistency, invariants, and validations within the aggregate.</span></span>

<span data-ttu-id="1399f-138">Když však model zachová do databáze NoSQL, kód a rozhraní API se výrazně v porovnání s EF Core kódem nebo jakýmkoli jiným kódem, který souvisí s relačními databázemi.</span><span class="sxs-lookup"><span data-stu-id="1399f-138">However, when you persist your model into the NoSQL database, the code and API change dramatically compared to EF Core code or any other code related to relational databases.</span></span>

## <a name="implement-net-code-targeting-mongodb-and-azure-cosmos-db"></a><span data-ttu-id="1399f-139">Implementace .NET kódu cílící na MongoDB a Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="1399f-139">Implement .NET code targeting MongoDB and Azure Cosmos DB</span></span>

### <a name="use-azure-cosmos-db-from-net-containers"></a><span data-ttu-id="1399f-140">Použití Azure Cosmos DB z kontejnerů .NET</span><span class="sxs-lookup"><span data-stu-id="1399f-140">Use Azure Cosmos DB from .NET containers</span></span>

<span data-ttu-id="1399f-141">K Azure Cosmos DB databází můžete přistupovat z kódu .NET, který běží v kontejnerech, podobně jako z jakékoli jiné aplikace .NET.</span><span class="sxs-lookup"><span data-stu-id="1399f-141">You can access Azure Cosmos DB databases from .NET code running in containers, like from any other .NET application.</span></span> <span data-ttu-id="1399f-142">Například umístění. API a marketing. mikroslužby pro rozhraní API v eShopOnContainers jsou implementovaná tak, aby mohly využívat databáze Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="1399f-142">For instance, the Locations.API and Marketing.API microservices in eShopOnContainers are implemented so they can consume Azure Cosmos DB databases.</span></span>

<span data-ttu-id="1399f-143">Existují však omezení Azure Cosmos DB z pohledu na vývojové prostředí Docker.</span><span class="sxs-lookup"><span data-stu-id="1399f-143">However, there’s a limitation in Azure Cosmos DB from a Docker development environment point of view.</span></span> <span data-ttu-id="1399f-144">I když existuje místní [emulátor Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/local-emulator) , který může běžet na místním vývojovém počítači, podporuje jenom Windows.</span><span class="sxs-lookup"><span data-stu-id="1399f-144">Even though there’s an on-premises [Azure Cosmos DB Emulator](https://docs.microsoft.com/azure/cosmos-db/local-emulator) that can run in a local development machine, it only supports Windows.</span></span> <span data-ttu-id="1399f-145">Linux a macOS se nepodporují.</span><span class="sxs-lookup"><span data-stu-id="1399f-145">Linux and macOS aren't supported.</span></span>

<span data-ttu-id="1399f-146">Existuje také možnost spustit tento emulátor v Docker, ale pouze v kontejnerech Windows, nikoli v kontejnerech Linux.</span><span class="sxs-lookup"><span data-stu-id="1399f-146">There's also the possibility to run this emulator on Docker, but just on Windows Containers, not with Linux Containers.</span></span> <span data-ttu-id="1399f-147">To je prvotní nevýhody pro vývojové prostředí, pokud je vaše aplikace nasazena jako kontejnery Linux, protože v současné době nemůžete nasazovat kontejnery Linux a Windows na Docker for Windows současně.</span><span class="sxs-lookup"><span data-stu-id="1399f-147">That's an initial handicap for the development environment if your application is deployed as Linux containers, since, currently, you can't deploy Linux and Windows Containers on Docker for Windows at the same time.</span></span> <span data-ttu-id="1399f-148">Všechny nasazené kontejnery musí být pro Linux nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="1399f-148">Either all containers being deployed have to be for Linux or for Windows.</span></span>

<span data-ttu-id="1399f-149">Ideální a pružně nasazené řešení pro vývoj/testování je schopnost nasadit databázové systémy jako kontejnery spolu s vlastními kontejnery, aby vaše prostředí pro vývoj a testování byla vždy konzistentní.</span><span class="sxs-lookup"><span data-stu-id="1399f-149">The ideal and more straightforward deployment for a dev/test solution is to be able to deploy your database systems as containers along with your custom containers so your dev/test environments are always consistent.</span></span>

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a><span data-ttu-id="1399f-150">Použití rozhraní MongoDB API pro místní vývojové/testovací Linux/kontejnery Windows Plus Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="1399f-150">Use MongoDB API for local dev/test Linux/Windows containers plus Azure Cosmos DB</span></span>

<span data-ttu-id="1399f-151">Cosmos DB databáze podporují rozhraní API MongoDB pro .NET a také nativní MongoDB síťový protokol.</span><span class="sxs-lookup"><span data-stu-id="1399f-151">Cosmos DB databases support MongoDB API for .NET as well as the native MongoDB wire protocol.</span></span> <span data-ttu-id="1399f-152">To znamená, že aplikace napsaná pro MongoDB nyní může komunikovat s Cosmos DB a používat Cosmos DB databáze namísto MongoDB databází, jak je znázorněno na obrázku 7-20.</span><span class="sxs-lookup"><span data-stu-id="1399f-152">This means that by using existing drivers, your application written for MongoDB can now communicate with Cosmos DB and use Cosmos DB databases instead of MongoDB databases, as shown in Figure 7-20.</span></span>

![Diagram znázorňující, že Cosmos DB podporuje síťový protokol .NET a MongoDB.](./media/nosql-database-persistence-infrastructure/mongodb-api-wire-protocol.png)

<span data-ttu-id="1399f-154">**Obrázek 7-20**.</span><span class="sxs-lookup"><span data-stu-id="1399f-154">**Figure 7-20**.</span></span> <span data-ttu-id="1399f-155">Přístup k Azure Cosmos DB pomocí rozhraní API a protokolu MongoDB</span><span class="sxs-lookup"><span data-stu-id="1399f-155">Using MongoDB API and protocol to access Azure Cosmos DB</span></span>

<span data-ttu-id="1399f-156">To je velice pohodlný přístup k ověření konceptů v prostředích Docker s kontejnery Linux, protože [Image Docker MongoDB](https://hub.docker.com/r/_/mongo/) je vícestránkový obrázek, který podporuje kontejnery Docker Linux a Docker Windows Containers.</span><span class="sxs-lookup"><span data-stu-id="1399f-156">This is a very convenient approach for proof of concepts in Docker environments with Linux containers because the [MongoDB Docker image](https://hub.docker.com/r/_/mongo/) is a multi-arch image that supports Docker Linux containers and Docker Windows containers.</span></span>

<span data-ttu-id="1399f-157">Jak je znázorněno na následujícím obrázku, používá rozhraní API MongoDB, eShopOnContainers podporuje MongoDB Linux a kontejnery Windows pro místní vývojové prostředí, ale pak můžete přejít na škálovatelné cloudové řešení PaaS jako Azure Cosmos DB, a to jednoduše [změnou připojovacího řetězce MongoDB tak, aby odkazoval na Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="1399f-157">As shown in the following image, by using the MongoDB API, eShopOnContainers supports MongoDB Linux and Windows containers for the local development environment but then, you can move to a scalable, PaaS cloud solution as Azure Cosmos DB by simply [changing the MongoDB connection string to point to Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span></span>

![Diagram znázorňující, že mikroslužba umístění v eShopOnContainers může používat databázi Cosmos DB nebo Mongo DB.](./media/nosql-database-persistence-infrastructure/eshoponcontainers-mongodb-containers.png)

<span data-ttu-id="1399f-159">**Obrázek 7-21**.</span><span class="sxs-lookup"><span data-stu-id="1399f-159">**Figure 7-21**.</span></span> <span data-ttu-id="1399f-160">eShopOnContainers s využitím kontejnerů MongoDB pro vývoj-ENV nebo Azure Cosmos DB pro produkci</span><span class="sxs-lookup"><span data-stu-id="1399f-160">eShopOnContainers using MongoDB containers for dev-env or Azure Cosmos DB for production</span></span>

<span data-ttu-id="1399f-161">Produkční Azure Cosmos DB by běžela v cloudu Azure jako PaaSá a škálovatelná služba.</span><span class="sxs-lookup"><span data-stu-id="1399f-161">The production Azure Cosmos DB would be running in Azure's cloud as a PaaS and scalable service.</span></span>

<span data-ttu-id="1399f-162">Vaše vlastní kontejnery .NET Core můžete spustit na místním hostiteli Docker (který používá Docker for Windows v počítači s Windows 10) nebo nasadit do produkčního prostředí, jako je Kubernetes v Azure AKS nebo Azure Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="1399f-162">Your custom .NET Core containers can run on a local development Docker host (that is using Docker for Windows in a Windows 10 machine) or be deployed into a production environment, like Kubernetes in Azure AKS or Azure Service Fabric.</span></span> <span data-ttu-id="1399f-163">V tomto druhém prostředí byste nasadili jenom vlastní kontejnery .NET Core, ale ne kontejner MongoDB, protože byste při zpracování dat v produkčním prostředí použili Azure Cosmos DB v cloudu.</span><span class="sxs-lookup"><span data-stu-id="1399f-163">In this second environment, you would deploy only the .NET Core custom containers but not the MongoDB container since you'd be using Azure Cosmos DB in the cloud for handling the data in production.</span></span>

<span data-ttu-id="1399f-164">Nejasnou výhodou použití rozhraní MongoDB API je, že vaše řešení může běžet v databázových modulech, MongoDB nebo Azure Cosmos DB, takže migrace do různých prostředí by měla být snadná.</span><span class="sxs-lookup"><span data-stu-id="1399f-164">A clear benefit of using the MongoDB API is that your solution could run in both database engines, MongoDB or Azure Cosmos DB, so migrations to different environments should be easy.</span></span> <span data-ttu-id="1399f-165">Někdy je však vhodné použít nativní rozhraní API (které je nativní Cosmos DB rozhraní API), aby bylo možné plně využít možnosti konkrétního databázového stroje.</span><span class="sxs-lookup"><span data-stu-id="1399f-165">However, sometimes it is worthwhile to use a native API (that is the native Cosmos DB API) in order to take full advantage of the capabilities of a specific database engine.</span></span>

<span data-ttu-id="1399f-166">Pro další porovnání jednoduchého použití MongoDB a Cosmos DB v cloudu si přečtěte [výhody použití Azure Cosmos DB na této stránce](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction).</span><span class="sxs-lookup"><span data-stu-id="1399f-166">For further comparison between simply using MongoDB versus Cosmos DB in the cloud, see the [Benefits of using Azure Cosmos DB in this page](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction).</span></span>

### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a><span data-ttu-id="1399f-167">Analýza přístupu k produkčním aplikacím: rozhraní API MongoDB vs. Cosmos DB API</span><span class="sxs-lookup"><span data-stu-id="1399f-167">Analyze your approach for production applications: MongoDB API vs. Cosmos DB API</span></span>

<span data-ttu-id="1399f-168">V eShopOnContainers používáme rozhraní MongoDB API, protože naše priorita má zásadní význam pro prostředí pro vývoj a testování s využitím databáze NoSQL, která by mohla spolupracovat i s Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="1399f-168">In eShopOnContainers, we're using MongoDB API because our priority was fundamentally to have a consistent dev/test environment using a NoSQL database that could also work with Azure Cosmos DB.</span></span>

<span data-ttu-id="1399f-169">Pokud ale plánujete používat rozhraní MongoDB API pro přístup k Azure Cosmos DB v Azure pro produkční aplikace, měli byste analyzovat rozdíly v možnostech a výkonu při použití rozhraní MongoDB API pro přístup k databázím Azure Cosmos DB v porovnání s používáním nativního rozhraní API Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="1399f-169">However, if you planning to use MongoDB API to access Azure Cosmos DB in Azure for production applications, you should analyze the differences in capabilities and performance when using MongoDB API to access Azure Cosmos DB databases compared to using the native Azure Cosmos DB API.</span></span> <span data-ttu-id="1399f-170">Pokud je to podobné, můžete použít rozhraní MongoDB API a získáte výhodu podpory dvou databázových strojů NoSQL současně.</span><span class="sxs-lookup"><span data-stu-id="1399f-170">If it is similar you can use MongoDB API and you get the benefit of supporting two NoSQL database engines at the same time.</span></span>

<span data-ttu-id="1399f-171">Clustery MongoDB můžete také použít jako provozní databázi v cloudu Azure pomocí [služby MongoDB Azure](https://www.mongodb.com/scale/mongodb-azure-service).</span><span class="sxs-lookup"><span data-stu-id="1399f-171">You could also use MongoDB clusters as the production database in Azure's cloud, too, with [MongoDB Azure Service](https://www.mongodb.com/scale/mongodb-azure-service).</span></span> <span data-ttu-id="1399f-172">Nejedná se ale o službu PaaS poskytovanou společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1399f-172">But that is not a PaaS service provided by Microsoft.</span></span> <span data-ttu-id="1399f-173">V tomto případě je Azure jenom hostitelem tohoto řešení z MongoDB.</span><span class="sxs-lookup"><span data-stu-id="1399f-173">In this case, Azure is just hosting that solution coming from MongoDB.</span></span>

<span data-ttu-id="1399f-174">V podstatě je to jenom právní omezení, které uvádí, že byste neměli vždycky používat rozhraní MongoDB API proti Azure Cosmos DB, stejně jako v eShopOnContainers, protože to byla vhodná volba pro kontejnery Linux.</span><span class="sxs-lookup"><span data-stu-id="1399f-174">Basically, this is just a disclaimer stating that you shouldn't always use MongoDB API against Azure Cosmos DB, as we did in eShopOnContainers because it was a convenient choice for Linux containers.</span></span> <span data-ttu-id="1399f-175">Rozhodnutí by mělo být založené na konkrétních potřebách a testech, které musíte udělat pro produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1399f-175">The decision should be based on the specific needs and tests you need to do for your production application.</span></span>

### <a name="the-code-use-mongodb-api-in-net-core-applications"></a><span data-ttu-id="1399f-176">Kód: použití rozhraní MongoDB API v aplikacích .NET Core</span><span class="sxs-lookup"><span data-stu-id="1399f-176">The code: Use MongoDB API in .NET Core applications</span></span>

<span data-ttu-id="1399f-177">Rozhraní MongoDB API pro .NET je založené na balíčcích NuGet, které musíte přidat do projektů, jako je například v projektu umístění. API na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="1399f-177">MongoDB API for .NET is based on NuGet packages that you need to add to your projects, like in the Locations.API project shown in the following figure.</span></span>

![Snímek obrazovky se závislostmi v balíčcích NuGet MongoDB](./media/nosql-database-persistence-infrastructure/mongodb-api-nuget-packages.png)

<span data-ttu-id="1399f-179">**Obrázek 7-22**.</span><span class="sxs-lookup"><span data-stu-id="1399f-179">**Figure 7-22**.</span></span> <span data-ttu-id="1399f-180">Odkazy na balíčky NuGet rozhraní MongoDB API v projektu .NET Core</span><span class="sxs-lookup"><span data-stu-id="1399f-180">MongoDB API NuGet packages references in a .NET Core project</span></span>

<span data-ttu-id="1399f-181">Pojďme prozkoumat kód v následujících oddílech.</span><span class="sxs-lookup"><span data-stu-id="1399f-181">Let's investigate the code in the following sections.</span></span>

#### <a name="a-model-used-by-mongodb-api"></a><span data-ttu-id="1399f-182">Model používaný rozhraním API MongoDB</span><span class="sxs-lookup"><span data-stu-id="1399f-182">A Model used by MongoDB API</span></span>

<span data-ttu-id="1399f-183">Nejprve je třeba definovat model, který bude obsahovat data přicházející z databáze v paměťovém prostoru aplikace.</span><span class="sxs-lookup"><span data-stu-id="1399f-183">First, you need to define a model that will hold the data coming from the database in your application's memory space.</span></span> <span data-ttu-id="1399f-184">Tady je příklad modelu používaného pro umístění na adrese eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="1399f-184">Here's an example of the model used for Locations at eShopOnContainers.</span></span>

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

<span data-ttu-id="1399f-185">Můžete vidět, že z balíčků NuGet MongoDB přicházejí některé atributy a typy.</span><span class="sxs-lookup"><span data-stu-id="1399f-185">You can see there are a few attributes and types coming from the MongoDB NuGet packages.</span></span>

<span data-ttu-id="1399f-186">Databáze NoSQL jsou obvykle velmi vhodné pro práci s nerelačními hierarchickými daty.</span><span class="sxs-lookup"><span data-stu-id="1399f-186">NoSQL databases are usually very well suited for working with non-relational hierarchical data.</span></span> <span data-ttu-id="1399f-187">V tomto příkladu používáme typy MongoDB hlavně vytvořené pro geografická umístění, jako je `GeoJson2DGeographicCoordinates` .</span><span class="sxs-lookup"><span data-stu-id="1399f-187">In this example, we are using MongoDB types especially made for geo-locations, like `GeoJson2DGeographicCoordinates`.</span></span>

#### <a name="retrieve-the-database-and-the-collection"></a><span data-ttu-id="1399f-188">Načtení databáze a kolekce</span><span class="sxs-lookup"><span data-stu-id="1399f-188">Retrieve the database and the collection</span></span>

<span data-ttu-id="1399f-189">V eShopOnContainers jsme vytvořili vlastní kontext databáze, kde implementujeme kód pro načtení databáze a MongoCollections, jak je uvedeno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="1399f-189">In eShopOnContainers, we have created a custom database context where we implement the code to retrieve the database and the MongoCollections, as in the following code.</span></span>

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

#### <a name="retrieve-the-data"></a><span data-ttu-id="1399f-190">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="1399f-190">Retrieve the data</span></span>

<span data-ttu-id="1399f-191">V kódu jazyka C#, jako jsou řadiče webového rozhraní API nebo implementace vlastních úložišť, můžete při dotazování prostřednictvím rozhraní MongoDB API zapsat podobný kód do následujících.</span><span class="sxs-lookup"><span data-stu-id="1399f-191">In C# code, like Web API controllers or custom Repositories implementation, you can write similar code to the following when querying through the MongoDB API.</span></span> <span data-ttu-id="1399f-192">Všimněte si, že `_context` objekt je instancí předchozí `LocationsContext` třídy.</span><span class="sxs-lookup"><span data-stu-id="1399f-192">Note that the `_context` object is an instance of the previous `LocationsContext` class.</span></span>

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a><span data-ttu-id="1399f-193">V souboru Docker-Compose. override. yml pro připojovací řetězec MongoDB použijte ENV-var.</span><span class="sxs-lookup"><span data-stu-id="1399f-193">Use an env-var in the docker-compose.override.yml file for the MongoDB connection string</span></span>

<span data-ttu-id="1399f-194">Při vytváření objektu MongoClient potřebuje základní parametr, který je přesně `ConnectionString` parametr ukazující na správnou databázi.</span><span class="sxs-lookup"><span data-stu-id="1399f-194">When creating a MongoClient object, it needs a fundamental parameter which is precisely the `ConnectionString` parameter pointing to the right database.</span></span> <span data-ttu-id="1399f-195">V případě eShopOnContainers může připojovací řetězec ukazovat na místní kontejner Docker MongoDB nebo na produkční Azure Cosmos DBovou databázi.</span><span class="sxs-lookup"><span data-stu-id="1399f-195">In the case of eShopOnContainers, the connection string can point to a local MongoDB Docker container or to a "production" Azure Cosmos DB database.</span></span>  <span data-ttu-id="1399f-196">Tento připojovací řetězec pochází z proměnných prostředí definovaných v `docker-compose.override.yml` souborech, které se používají při nasazení pomocí Docker-psací nebo Visual studia, jako v následujícím kódu YML.</span><span class="sxs-lookup"><span data-stu-id="1399f-196">That connection string comes from the environment variables defined in the `docker-compose.override.yml` files used when deploying with docker-compose or Visual Studio, as in the following yml code.</span></span>

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

<span data-ttu-id="1399f-197">`ConnectionString`Proměnná prostředí se vyřeší tímto způsobem: Pokud `ESHOP_AZURE_COSMOSDB` je globální proměnná definovaná v `.env` souboru s připojovacím řetězcem Azure Cosmos DB, použije se pro přístup k databázi Azure Cosmos DB v cloudu.</span><span class="sxs-lookup"><span data-stu-id="1399f-197">The `ConnectionString` environment variable is resolved this way: If the `ESHOP_AZURE_COSMOSDB` global variable is defined in the `.env` file with the Azure Cosmos DB connection string, it will use it to access the Azure Cosmos DB database in the cloud.</span></span> <span data-ttu-id="1399f-198">Pokud není definován, bude přebírat `mongodb://nosqldata` hodnotu a používat MongoDB kontejner pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="1399f-198">If it’s not defined, it will take the `mongodb://nosqldata` value and use the development MongoDB container.</span></span>

<span data-ttu-id="1399f-199">Následující kód ukazuje `.env` soubor s globální proměnnou prostředí Azure Cosmos DB připojovací řetězec, jak je implementováno v eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="1399f-199">The following code shows the `.env` file with the Azure Cosmos DB connection string global environment variable, as implemented in eShopOnContainers:</span></span>

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

<span data-ttu-id="1399f-200">Odkomentujte ESHOP_AZURE_COSMOSDB řádek a aktualizujte ho pomocí připojovacího řetězce Azure Cosmos DB získaného z Azure Portal, jak je vysvětleno v tématu [připojení aplikace MongoDB k Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="1399f-200">Uncomment the ESHOP_AZURE_COSMOSDB line and update it with your Azure Cosmos DB connection string obtained from the Azure portal as explained in [Connect a MongoDB application to Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span></span>

<span data-ttu-id="1399f-201">Pokud `ESHOP_AZURE_COSMOSDB` je globální proměnná prázdná, znamená to, že je v souboru zakomentována `.env` , pak kontejner používá výchozí připojovací řetězec MongoDB.</span><span class="sxs-lookup"><span data-stu-id="1399f-201">If the `ESHOP_AZURE_COSMOSDB` global variable is empty, meaning it's commented out in the `.env` file, then the container uses a default MongoDB connection string.</span></span> <span data-ttu-id="1399f-202">Tento připojovací řetězec odkazuje na místní kontejner MongoDB nasazený v eShopOnContainers, který má název `nosqldata` a byl definován v souboru Docker – sestavení, jak je znázorněno v následujícím kódu. yml:</span><span class="sxs-lookup"><span data-stu-id="1399f-202">This connection string points to the local MongoDB container deployed in eShopOnContainers that is named `nosqldata` and was defined at the docker-compose file, as shown in the following .yml code:</span></span>

``` yml
# docker-compose.yml
version: '3.4'
services:
  # ...Other services...
  nosqldata:
    image: mongo
```

#### <a name="additional-resources"></a><span data-ttu-id="1399f-203">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="1399f-203">Additional resources</span></span>

- <span data-ttu-id="1399f-204">**Modelování dat dokumentů pro databáze NoSQL** </span><span class="sxs-lookup"><span data-stu-id="1399f-204">**Modeling document data for NoSQL databases** </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/modeling-data>

- <span data-ttu-id="1399f-205">**Vaughn Vernon. Ideální úložiště s agregovaným návrhem na základě domény?**</span><span class="sxs-lookup"><span data-stu-id="1399f-205">**Vaughn Vernon. The Ideal Domain-Driven Design Aggregate Store?**</span></span> \
  <https://kalele.io/blog-posts/the-ideal-domain-driven-design-aggregate-store/>

- <span data-ttu-id="1399f-206">**Úvod do Azure Cosmos DB: API pro MongoDB**  </span><span class="sxs-lookup"><span data-stu-id="1399f-206">**Introduction to Azure Cosmos DB: API for MongoDB**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction>

- <span data-ttu-id="1399f-207">**Azure Cosmos DB: sestavení webové aplikace API MongoDB pomocí .NET a Azure Portal**  </span><span class="sxs-lookup"><span data-stu-id="1399f-207">**Azure Cosmos DB: Build a MongoDB API web app with .NET and the Azure portal**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet>

- <span data-ttu-id="1399f-208">**Použití emulátoru Azure Cosmos DB pro místní vývoj a testování**  </span><span class="sxs-lookup"><span data-stu-id="1399f-208">**Use the Azure Cosmos DB Emulator for local development and testing**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/local-emulator>

- <span data-ttu-id="1399f-209">**Připojení aplikace MongoDB k Azure Cosmos DB**  </span><span class="sxs-lookup"><span data-stu-id="1399f-209">**Connect a MongoDB application to Azure Cosmos DB**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account>

- <span data-ttu-id="1399f-210">**Obrázek Docker emulátoru Cosmos DB (kontejner Windows)**  </span><span class="sxs-lookup"><span data-stu-id="1399f-210">**The Cosmos DB Emulator Docker image (Windows Container)**  </span></span>\
  <https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/>

- <span data-ttu-id="1399f-211">**Image Docker MongoDB (Linux a kontejner Windows)**  </span><span class="sxs-lookup"><span data-stu-id="1399f-211">**The MongoDB Docker image (Linux and Windows Container)**  </span></span>\
  <https://hub.docker.com/_/mongo/>

- <span data-ttu-id="1399f-212">**Použití MongoChef (Studio 3T) s Azure Cosmos DB: API pro účet MongoDB**  </span><span class="sxs-lookup"><span data-stu-id="1399f-212">**Use MongoChef (Studio 3T) with an Azure Cosmos DB: API for MongoDB account**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-mongochef>

>[!div class="step-by-step"]
><span data-ttu-id="1399f-213">[Předchozí](infrastructure-persistence-layer-implementation-entity-framework-core.md) 
> [Další](microservice-application-layer-web-api-design.md)</span><span class="sxs-lookup"><span data-stu-id="1399f-213">[Previous](infrastructure-persistence-layer-implementation-entity-framework-core.md)
[Next](microservice-application-layer-web-api-design.md)</span></span>
