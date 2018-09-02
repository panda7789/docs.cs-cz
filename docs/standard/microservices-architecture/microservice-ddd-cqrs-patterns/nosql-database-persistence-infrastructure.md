---
title: Použití databází NoSQL jako infrastruktury trvalosti
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Použití databází NoSQL jako infrastruktury trvalosti
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: a5fce347193921305c264df34be99063920af715
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43416494"
---
# <a name="using-nosql-databases-as-a-persistence-infrastructure"></a><span data-ttu-id="76d9f-103">Použití databází NoSQL jako infrastruktury trvalosti</span><span class="sxs-lookup"><span data-stu-id="76d9f-103">Using NoSQL databases as a persistence infrastructure</span></span>

<span data-ttu-id="76d9f-104">Použijete-li databáze NoSQL pro datovou vrstvu, infrastruktury, je obvykle velmi riskantní používat ORM jako Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="76d9f-104">When you use NoSQL databases for your infrastructure data tier, you typically do not use an ORM like Entity Framework Core.</span></span> <span data-ttu-id="76d9f-105">Místo toho použijte rozhraní API poskytuje modul NoSQL, jako je Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB nebo tabulky v úložišti Azure.</span><span class="sxs-lookup"><span data-stu-id="76d9f-105">Instead you use the API provided by the NoSQL engine, such as Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB, or Azure Storage Tables.</span></span>

<span data-ttu-id="76d9f-106">Použijete-li databáze NoSQL, zvláště dokumentově orientované databázi jako službu Azure Cosmos DB, CouchDB nebo RavenDB, tak, jak při návrhu modelu pomocí agregace DDD ale částečně podobný jak to zvládnete v EF Core vztahující k identifikaci agregační kořeny podřízených tříd entit a objekt třídy hodnoty.</span><span class="sxs-lookup"><span data-stu-id="76d9f-106">However, when you use a NoSQL database, especially a document-oriented database like Azure Cosmos DB, CouchDB, or RavenDB, the way you design your model with DDD aggregates is partially similar to how you can do it in EF Core, in regards to the identification of aggregate roots, child entity classes, and value object classes.</span></span> <span data-ttu-id="76d9f-107">Ale nakonec bude mít vliv výběr databáze v návrhu.</span><span class="sxs-lookup"><span data-stu-id="76d9f-107">But, ultimately, the database selection will impact in your design.</span></span>

<span data-ttu-id="76d9f-108">Při použití databáze dokumentově orientované implementaci agregace jako jeden dokument, serializované ve formátu JSON nebo jiný formát.</span><span class="sxs-lookup"><span data-stu-id="76d9f-108">When you use a document-oriented database, you implement an aggregate as a single document, serialized in JSON or another format.</span></span> <span data-ttu-id="76d9f-109">Použití databáze je však transparentní z domény modelu kódu hlediska.</span><span class="sxs-lookup"><span data-stu-id="76d9f-109">However, the use of the database is transparent from a domain model code point of view.</span></span> <span data-ttu-id="76d9f-110">Při použití databáze NoSQL, stále používáte tříd entit a agregační kořenové třídy, ale s větší flexibilitou než při použití EF Core, protože není relační stálost.</span><span class="sxs-lookup"><span data-stu-id="76d9f-110">When using a NoSQL database, you still are using entity classes and aggregate root classes, but with more flexibility than when using EF Core because the persistence is not relational.</span></span>

<span data-ttu-id="76d9f-111">Rozdíl je v jak zachovat tohoto modelu.</span><span class="sxs-lookup"><span data-stu-id="76d9f-111">The difference is in how you persist that model.</span></span> <span data-ttu-id="76d9f-112">Pokud jste implementovali doménový model podle tříd entit POCO, zohledňovat trvalosti infrastruktury, může vypadat podobně, jako by mohla přesunout do jiné trvalosti infrastruktury, dokonce i z relační NoSQL.</span><span class="sxs-lookup"><span data-stu-id="76d9f-112">If you implemented your domain model based on POCO entity classes, agnostic to the infrastructure persistence, it might look like you could move to a different persistence infrastructure, even from relational to NoSQL.</span></span> <span data-ttu-id="76d9f-113">Nicméně, který by neměl být vaším cílem.</span><span class="sxs-lookup"><span data-stu-id="76d9f-113">However, that should not be your goal.</span></span> <span data-ttu-id="76d9f-114">Se vždy najde nějaká omezení v různých databázích budou nabízená oznámení vám zpět, takže není možné mít stejný model pro relační nebo NoSQL databáze.</span><span class="sxs-lookup"><span data-stu-id="76d9f-114">There are always constraints in the different databases will push you back, so you will not be able to have the same model for relational or NoSQL databases.</span></span> <span data-ttu-id="76d9f-115">Změna modely trvalosti by se triviální, protože transakce a operace trvalého uložení bude velmi lišit.</span><span class="sxs-lookup"><span data-stu-id="76d9f-115">Changing persistence models would not be trivial, because transactions and persistence operations will be very different.</span></span>

<span data-ttu-id="76d9f-116">Například v databázi dokumentově orientované je dobrá pro agregační kořenovou mít více vlastností podřízené kolekce.</span><span class="sxs-lookup"><span data-stu-id="76d9f-116">For example, in a document-oriented database, it is okay for an aggregate root to have multiple child collection properties.</span></span> <span data-ttu-id="76d9f-117">Dotazování více vlastností podřízené kolekce je awful, v relační databázi, protože SJEDNOCENÍ všech SQL příkazu získáte zpět ze EF.</span><span class="sxs-lookup"><span data-stu-id="76d9f-117">In a relational database, querying multiple child collection properties is awful, because you get a UNION ALL SQL statement back from EF.</span></span> <span data-ttu-id="76d9f-118">S modelem domény pro relační databáze nebo NoSQL databáze není jednoduché a by neměl vyzkoušet.</span><span class="sxs-lookup"><span data-stu-id="76d9f-118">Having the same domain model for relational databases or NoSQL databases is not simple, and you should not try it.</span></span> <span data-ttu-id="76d9f-119">Musíte opravdu svůj přístup k návrhu modelu se seznámíte s jak se bude používat v každé databázi konkrétního data.</span><span class="sxs-lookup"><span data-stu-id="76d9f-119">You really have to design your model with an understanding of how the data is going to be used in each particular database.</span></span>

<span data-ttu-id="76d9f-120">Výhoda po použití databází NoSQL, že entity jsou více Nenormalizovaná tak nenastavujte mapování tabulky.</span><span class="sxs-lookup"><span data-stu-id="76d9f-120">A benefit when using NoSQL databases is that the entities are more denormalized, so you do not set a table mapping.</span></span> <span data-ttu-id="76d9f-121">Doménový model může být flexibilnější než při použití relační databáze.</span><span class="sxs-lookup"><span data-stu-id="76d9f-121">Your domain model can be more flexible than when using a relational database.</span></span>

<span data-ttu-id="76d9f-122">Při návrhu doménový model podle agregace, Přesun do NoSQL a dokumentově orientované databáze může být ještě jednodušší než při použití relační databázi, protože jsou podobné agregace, navrhnout serializovat dokumenty v databázi dokumentově orientované.</span><span class="sxs-lookup"><span data-stu-id="76d9f-122">When you design your domain model based on aggregates, moving to NoSQL and document-oriented databases might be even easier than using a relational database, because the aggregates you design are similar to serialized documents in a document-oriented database.</span></span> <span data-ttu-id="76d9f-123">V těchto "kontejnery objektů a dat" lze pak zahrnout všechny informace, které může být nutné pro tuto agregaci.</span><span class="sxs-lookup"><span data-stu-id="76d9f-123">Then you can include in those “bags” all the information you might need for that aggregate.</span></span>

<span data-ttu-id="76d9f-124">Například následující kód JSON je ukázková implementace agregace pořadí při použití dokumentově orientované databáze.</span><span class="sxs-lookup"><span data-stu-id="76d9f-124">For instance, the following JSON code is a sample implementation of an order aggregate when using a document-oriented database.</span></span> <span data-ttu-id="76d9f-125">Je to podobné agregační pořadí, implementovali jsme v ukázkové aplikaci eShopOnContainers, ale bez použití EF Core pod.</span><span class="sxs-lookup"><span data-stu-id="76d9f-125">It is similar to the order aggregate we implemented in the eShopOnContainers sample, but without using EF Core underneath.</span></span>

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

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a><span data-ttu-id="76d9f-126">Úvod do služby Azure Cosmos DB a nativní rozhraní API Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="76d9f-126">Introduction to Azure Cosmos DB and the native Cosmos DB API</span></span>

<span data-ttu-id="76d9f-127">[Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/introduction) je globálně distribuovaná databázová služba od Microsoftu pro klíčové aplikace.</span><span class="sxs-lookup"><span data-stu-id="76d9f-127">[Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/introduction) is Microsoft's globally distributed database service for mission-critical applications.</span></span> <span data-ttu-id="76d9f-128">Azure Cosmos DB poskytuje [globální distribuce na klíč](https://docs.microsoft.com/en-us/azure/cosmos-db/distribute-data-globally), [elastické škálování propustnosti a úložiště](https://docs.microsoft.com/en-us/azure/cosmos-db/partition-data) po celém světě, řádu milisekund na 99. percentilu, [pět jasně definovaných úrovní konzistence](https://docs.microsoft.com/en-us/azure/cosmos-db/consistency-levels)a zaručenou vysokou dostupnost, vše zajištěné [špičkové smlouvy SLA](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span><span class="sxs-lookup"><span data-stu-id="76d9f-128">Azure Cosmos DB provides [turn-key global distribution](https://docs.microsoft.com/en-us/azure/cosmos-db/distribute-data-globally), [elastic scaling of throughput and storage](https://docs.microsoft.com/en-us/azure/cosmos-db/partition-data) worldwide, single-digit millisecond latencies at the 99th percentile, [five well-defined consistency levels](https://docs.microsoft.com/en-us/azure/cosmos-db/consistency-levels), and guaranteed high availability, all backed by [industry-leading SLAs](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span></span> <span data-ttu-id="76d9f-129">Azure Cosmos DB [automaticky indexuje data](http://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) aniž byste se museli starat o správu schémat a indexů.</span><span class="sxs-lookup"><span data-stu-id="76d9f-129">Azure Cosmos DB [automatically indexes data](http://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) without requiring you to deal with schema and index management.</span></span> <span data-ttu-id="76d9f-130">Více modelů a podporuje dokument, klíč hodnota, graf a úložiště se sloupcovou strukturou datových modelů.</span><span class="sxs-lookup"><span data-stu-id="76d9f-130">It is multi-model and supports document, key-value, graph, and columnar data models.</span></span>

<span data-ttu-id="76d9f-131">![](./media/image19.1.png) Obrázek 9-19.</span><span class="sxs-lookup"><span data-stu-id="76d9f-131">![](./media/image19.1.png) Figure 9-19.</span></span> <span data-ttu-id="76d9f-132">Globální distribuce služby Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="76d9f-132">Azure Cosmos DB global distribution</span></span>

<span data-ttu-id="76d9f-133">Když použijete C\# model k implementaci agregace pro rozhraní Azure Cosmos DB API, agregace může být podobně jako c\# POCO třídy používané s EF Core.</span><span class="sxs-lookup"><span data-stu-id="76d9f-133">When you use a C\# model to implement the aggregate to be used by the Azure Cosmos DB API, the aggregate can be similar to the C\# POCO classes used with EF Core.</span></span> <span data-ttu-id="76d9f-134">Rozdíl je tak, jak používat z vrstvy aplikace a infrastruktury, jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="76d9f-134">The difference is in the way to use them from the application and infrastructure layers, as in the following code:</span></span>

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

<span data-ttu-id="76d9f-135">Uvidíte, že může být podobným způsobem, jakým se použije na úrovni vrstvy modelu domény při infrastruktury je EF tak, jak pracovat s modelu domény.</span><span class="sxs-lookup"><span data-stu-id="76d9f-135">You can see that the way you work with your domain model can be similar to the way you use it in your domain model layer when the infrastructure is EF.</span></span> <span data-ttu-id="76d9f-136">K zajištění konzistence, výstupních podmínek a ověření v rámci agregace nadále používat stejné agregační kořenové metody.</span><span class="sxs-lookup"><span data-stu-id="76d9f-136">You still use the same aggregate root methods to ensure consistency, invariants, and validations within the aggregate.</span></span>

<span data-ttu-id="76d9f-137">Ale když trvale uložíte modelu do databáze NoSQL, kód a výrazně porovnání EF Core kódu změnu rozhraní API nebo jakýkoli jiný kód související s relačních databází.</span><span class="sxs-lookup"><span data-stu-id="76d9f-137">However, when you persist your model into the NoSQL database, the code and API change dramatically compared to EF Core code or any other code related to relational databases.</span></span>

## <a name="implementing-net-code-targeting-mongodb-and-azure-cosmos-db"></a><span data-ttu-id="76d9f-138">Implementace kódu .NET, které cílí na MongoDB a Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="76d9f-138">Implementing .NET code targeting MongoDB and Azure Cosmos DB</span></span>

### <a name="using-azure-cosmos-db-from-net-containers"></a><span data-ttu-id="76d9f-139">Pomocí služby Azure Cosmos DB z kontejnery .NET</span><span class="sxs-lookup"><span data-stu-id="76d9f-139">Using Azure Cosmos DB from .NET containers</span></span>

<span data-ttu-id="76d9f-140">Databáze Azure Cosmos DB můžete přistupovat z kódu .NET spuštěných v kontejnerech, stejně jako jakékoli jiné aplikace .NET.</span><span class="sxs-lookup"><span data-stu-id="76d9f-140">You can access Azure Cosmos DB databases from .NET code running in containers, like from any other .NET application.</span></span> <span data-ttu-id="76d9f-141">Například Locations.API a Marketing.API mikroslužeb v aplikaci eShopOnContainers jsou implementované tak spotřebují databází Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="76d9f-141">For instance, the Locations.API and Marketing.API microservices in eShopOnContainers are implemented so they can consume Azure Cosmos DB databases.</span></span>

<span data-ttu-id="76d9f-142">Existuje ale omezení ve službě Azure Cosmos DB z Dockeru vývojové prostředí hlediska.</span><span class="sxs-lookup"><span data-stu-id="76d9f-142">However, there’s a limitation in Azure Cosmos DB from a Docker development environment point of view.</span></span> <span data-ttu-id="76d9f-143">I když dojde místní [emulátor služby Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator) možné spouštět v místním vývojovém počítači (například počítač), jako opožděné 2017 právě podporuje Windows, Linuxu ne.</span><span class="sxs-lookup"><span data-stu-id="76d9f-143">Even when there’s a on-premises [Azure Cosmos DB Emulator](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator) able to run in a local development machine (like a PC), as of late 2017, it just supports Windows, not Linux.</span></span> 

<span data-ttu-id="76d9f-144">Je také možné spustit tuto emulátor v Dockeru, ale jen na kontejnery Windows s, nikoli kontejnery Linuxu.</span><span class="sxs-lookup"><span data-stu-id="76d9f-144">There is also the possibility to run this emulator on Docker, but just on Windows Containers with the , not Linux Containers.</span></span> <span data-ttu-id="76d9f-145">To je počáteční postižení pro vývojové prostředí, pokud vaše aplikace bude nasazena jako kontejnery Linux, od, aktuálně, nelze nasadit systémy Linux a kontejnery Windows na Docker pro Windows ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="76d9f-145">That is an initial handicap for the development environment if your application is deployed as Linux containers, since, currently, you cannot deploy Linux and Windows Containers on Docker for Windows at the same time.</span></span> <span data-ttu-id="76d9f-146">Buď všechny kontejnery, které nasazuje, musí být pro Linux nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="76d9f-146">Either all containers being deployed have to be for Linux or for Windows.</span></span>  

<span data-ttu-id="76d9f-147">Ideální a jednodušší nasazení pro vývoj/testování řešení je moct nasadit databázovými systémy jako kontejnery spolu s vlastní kontejnery tak, aby byly vždy konzistentní vývojová a testovací prostředí.</span><span class="sxs-lookup"><span data-stu-id="76d9f-147">The ideal and more straightforward deployment for a dev/test solution is to be able to deploy your database systems as containers along with your custom containers so your dev/test environments are always consistent.</span></span>

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a><span data-ttu-id="76d9f-148">Pro místní vývoj a testování systému Linux/Windows kontejnery a služby Azure Cosmos DB pomocí rozhraní MongoDB API</span><span class="sxs-lookup"><span data-stu-id="76d9f-148">Use MongoDB API for local dev/test Linux/Windows containers plus Azure Cosmos DB</span></span>

<span data-ttu-id="76d9f-149">Databáze cosmos DB podporovat rozhraní MongoDB API pro .NET, stejně jako nativní přenosový protokol MongoDB.</span><span class="sxs-lookup"><span data-stu-id="76d9f-149">Cosmos DB databases support MongoDB API for .NET as well as the native MongoDB wire protocol.</span></span> <span data-ttu-id="76d9f-150">To znamená, že pomocí existujících ovladačů, vaše aplikace napsané pro MongoDB můžou nyní komunikovat s Cosmos DB a pomocí databáze Cosmos DB místo databází MongoDB, jak je znázorněno v obrázek 9-20.</span><span class="sxs-lookup"><span data-stu-id="76d9f-150">This means that by using existing drivers, your application written for MongoDB can now communicate with Cosmos DB and use Cosmos DB databases instead of MongoDB databases, as shown in Figure 9-20.</span></span>

<span data-ttu-id="76d9f-151">![](./media/image19.2.png) Obrázek 9 – 20.</span><span class="sxs-lookup"><span data-stu-id="76d9f-151">![](./media/image19.2.png) Figure 9-20.</span></span> <span data-ttu-id="76d9f-152">Přístup k Azure Cosmos DB pomocí rozhraní MongoDB API a protokol</span><span class="sxs-lookup"><span data-stu-id="76d9f-152">Using MongoDB API and protocol to access Azure Cosmos DB</span></span>

<span data-ttu-id="76d9f-153">To je velmi efektivní přístup pro testování konceptů v prostředí Dockeru s kontejnery Linuxu, protože [image Dockeru MongoDB](https://hub.docker.com/r/_/mongo/) je více architektury image, která podporuje kontejnery Linuxu Dockeru a kontejnerech Dockeru Windows.</span><span class="sxs-lookup"><span data-stu-id="76d9f-153">This is a very convenient approach for proof of concepts in Docker environments with Linux containers because the [MongoDB Docker image](https://hub.docker.com/r/_/mongo/) is a multi-arch image that supports Docker Linux containers and Docker Windows containers.</span></span>

<span data-ttu-id="76d9f-154">Jak je znázorněno na obrázku 9-21, pomocí rozhraní MongoDB API aplikaci eShopOnContainers podporuje kontejnery MongoDB, Linux a Windows pro místní vývojové prostředí, ale pak můžete přesunout ke škálovatelným, PaaS cloudové řešení jako Azure Cosmos DB pomocí jednoduše [změna připojovací řetězec MongoDB tak, aby odkazovala na službu Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="76d9f-154">As shown in the image 9-21, by using the MongoDB API, eShopOnContainers supports MongoDB Linux and Windows containers for the local development environment but then, you can move to a scalable, PaaS cloud solution as Azure Cosmos DB by simply [changing the MongoDB connection string to point to Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account).</span></span> 

<span data-ttu-id="76d9f-155">![](./media/image20-bis.png) Obrázek 9-21.</span><span class="sxs-lookup"><span data-stu-id="76d9f-155">![](./media/image20-bis.png) Figure 9-21.</span></span> <span data-ttu-id="76d9f-156">pomocí kontejnerů MongoDB pro vývoj env nebo služby Azure Cosmos DB pro produkční aplikaci eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="76d9f-156">eShopOnContainers using MongoDB containers for dev-env or Azure Cosmos DB for production</span></span>

<span data-ttu-id="76d9f-157">Výrobní službu Azure Cosmos DB by běžet v cloudu Azure jako a škálovatelná služba PaaS.</span><span class="sxs-lookup"><span data-stu-id="76d9f-157">The production Azure Cosmos DB would be running in Azure’s cloud as a PaaS and scalable service.</span></span>

<span data-ttu-id="76d9f-158">Své vlastní kontejnery .NET Core můžete spustit na místním vývojovém hostitele Docker, (, který je používán Docker pro Windows v počítači s Windows 10) nebo nasazení do produkčního prostředí, jako je Kubernetes v Azure AKS nebo Azure Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="76d9f-158">Your custom .NET Core containers can run on a local development Docker host (that is using Docker for Windows in a Windows 10 machine) or be deployed into a production environment, like Kubernetes in Azure AKS or Azure Service Fabric.</span></span> <span data-ttu-id="76d9f-159">V tomto druhém prostředí by nasadit jenom vlastní kontejnery .NET Core, ale ne kontejner MongoDB vzhledem k tomu, že budete používat Azure Cosmos DB v cloudu pro zpracování dat v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="76d9f-159">In this second environment, you would deploy only the .NET Core custom containers but not the MongoDB container since you’d be using Azure Cosmos DB in the cloud for handling the data in production.</span></span>

<span data-ttu-id="76d9f-160">Vymazat výhodou pomocí rozhraní MongoDB API je, že vaše řešení může běžet v obou databázových strojů, MongoDB nebo Azure Cosmos DB, migrace do různých prostředí by tak měly být snadné.</span><span class="sxs-lookup"><span data-stu-id="76d9f-160">A clear benefit of using the MongoDB API is that your solution could run in both database engines, MongoDB or Azure Cosmos DB, so migrations to different environments should be easy.</span></span> <span data-ttu-id="76d9f-161">Někdy je však vhodné používat nativní rozhraní API (který je nativní rozhraní API Cosmos DB) Pokud chcete naplno využít možnosti konkrétní databázového stroje.</span><span class="sxs-lookup"><span data-stu-id="76d9f-161">However, sometimes it is worthwhile to use a native API (that is the native Cosmos DB API) in order to take full advantage of the capabilities of a specific database engine.</span></span>

<span data-ttu-id="76d9f-162">Další porovnání mezi jednoduše pomocí databáze MongoDB a Cosmos DB v cloudu najdete v tématu [výhody používání služby Azure Cosmos DB na této stránce](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction).</span><span class="sxs-lookup"><span data-stu-id="76d9f-162">For further comparison between simply using MongoDB versus Cosmos DB in the cloud, see the [Benefits of using Azure Cosmos DB in this page](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction).</span></span> 


### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a><span data-ttu-id="76d9f-163">Analyzovat svůj přístup pro aplikace v produkčním prostředí: rozhraní MongoDB API služby vs. Rozhraní API služby cosmos DB</span><span class="sxs-lookup"><span data-stu-id="76d9f-163">Analyze your approach for production applications: MongoDB API vs. Cosmos DB API</span></span>

<span data-ttu-id="76d9f-164">V aplikaci eShopOnContainers používáme rozhraní MongoDB API, protože naší prioritou je v podstatě mít konzistentní vývojového a testovacího prostředí používat databázi NoSQL, která může spolupracovat také se službami Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="76d9f-164">In eShopOnContainers, we’re using MongoDB API because our priority was fundamentally to have a consistent dev/test environment using a NoSQL database that could also work with Azure Cosmos DB.</span></span>

<span data-ttu-id="76d9f-165">Nicméně pokud jste v úmyslu použít rozhraní MongoDB API pro přístup k Azure Cosmos DB v Azure pro aplikace v produkčním prostředí, je vhodné analyzovat, rozdíly v možnosti a výkon při přístupu k ve srovnání s použitím nativního databází Azure Cosmos DB pomocí rozhraní MongoDB API Rozhraní API služby Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="76d9f-165">However, if you planning to use MongoDB API to access Azure Cosmos DB in Azure for production applications, you should analyze the differences in capabilities and performance when using MongoDB API to access Azure Cosmos DB databases compared to using the native Azure Cosmos DB API.</span></span> <span data-ttu-id="76d9f-166">Pokud je to podobné použijete rozhraní MongoDB API služby a budete mít k dispozici podpora ve stejnou dobu dvěma motory databáze NoSQL.</span><span class="sxs-lookup"><span data-stu-id="76d9f-166">If it is similar you can use MongoDB API, and you get the benefit of supporting two NoSQL database engines at the same time.</span></span> 

<span data-ttu-id="76d9f-167">Můžete také použít clustery MongoDB jako provozní databáze v cloudu Azure, s [MongoDB služby Azure](https://www.mongodb.com/scale/mongodb-azure-service).</span><span class="sxs-lookup"><span data-stu-id="76d9f-167">You could also use MongoDB clusters as the production database in Azure’s cloud, too, with [MongoDB Azure Service](https://www.mongodb.com/scale/mongodb-azure-service).</span></span> <span data-ttu-id="76d9f-168">Ale to není služba PaaS poskytnutých microsoftem.</span><span class="sxs-lookup"><span data-stu-id="76d9f-168">But that is not a PaaS service provided by Microsoft.</span></span> <span data-ttu-id="76d9f-169">V takovém případě je právě hostování Azure toto řešení z MongoDB.</span><span class="sxs-lookup"><span data-stu-id="76d9f-169">In this case, Azure is just hosting that solution coming from MongoDB.</span></span>

<span data-ttu-id="76d9f-170">V podstatě je to pouze upozornění s informacemi o tom, že byste neměli vždy používat rozhraní MongoDB API službou Azure Cosmos DB, jako jsme to udělali v aplikaci eShopOnContainers protože je vhodné volbou pro kontejnery Linuxu.</span><span class="sxs-lookup"><span data-stu-id="76d9f-170">Basically, this is just a disclaimer stating that you shouldn’t always use MongoDB API against Azure Cosmos DB, as we did in eShopOnContainers because it was a convenient choice for Linux containers.</span></span> <span data-ttu-id="76d9f-171">Rozhodnutí by měla být podle potřeb a testy, které musíte udělat pro aplikace v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="76d9f-171">The decision should be based on the specific needs and tests you need to do for your production application.</span></span>  

### <a name="the-code-using-mongodb-api-in-net-core-applications"></a><span data-ttu-id="76d9f-172">Kód: pomocí rozhraní MongoDB API v aplikacích .NET Core</span><span class="sxs-lookup"><span data-stu-id="76d9f-172">The code: Using MongoDB API in .NET Core applications</span></span>

<span data-ttu-id="76d9f-173">Rozhraní MongoDB API pro .NET je založená na balíčky NuGet, které je třeba přidat do vašich projektů, jako je Locations.API zobrazí obrázek 9 – 22.</span><span class="sxs-lookup"><span data-stu-id="76d9f-173">MongoDB API for .NET is based on NuGet packages that you need to add to your projects, like the Locations.API shown in Figure 9-22.</span></span>

<span data-ttu-id="76d9f-174">![](./media/image21-bis.png) Obrázek 9 – 22.</span><span class="sxs-lookup"><span data-stu-id="76d9f-174">![](./media/image21-bis.png) Figure 9-22.</span></span> <span data-ttu-id="76d9f-175">Balíčky NuGet rozhraní API MongoDB odkazů v projektu .NET Core</span><span class="sxs-lookup"><span data-stu-id="76d9f-175">MongoDB API NuGet packages references in a .NET Core project</span></span>

<span data-ttu-id="76d9f-176">Pojďme prozkoumat kód v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="76d9f-176">Let's investigate the code in the following sections.</span></span>

#### <a name="a-model-used-by-mongodb-api"></a><span data-ttu-id="76d9f-177">Model používaný v rozhraní MongoDB API</span><span class="sxs-lookup"><span data-stu-id="76d9f-177">A Model used by MongoDB API</span></span>

<span data-ttu-id="76d9f-178">Nejprve budete muset definovat model, který bude obsahovat data z databáze v paměti aplikace.</span><span class="sxs-lookup"><span data-stu-id="76d9f-178">First, you need to define a model that will hold the data coming from the database in your application’s memory space.</span></span> <span data-ttu-id="76d9f-179">Tady je příklad modelu v aplikaci eShopOnContainers použito pro umístění.</span><span class="sxs-lookup"><span data-stu-id="76d9f-179">Here’s an example of the model used for Locations at eShopOnContainers.</span></span>

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

<span data-ttu-id="76d9f-180">Uvidíte, že existuje několik atributů a typy pocházející z balíčků MongoDB NuGet.</span><span class="sxs-lookup"><span data-stu-id="76d9f-180">You can see there are a few attributes and types coming from the MongoDB NuGet packages.</span></span>

<span data-ttu-id="76d9f-181">Databáze NoSQL jsou obvykle velmi dobře hodí pro práci s nerelačními hierarchická data.</span><span class="sxs-lookup"><span data-stu-id="76d9f-181">NoSQL databases are usually very well suited for working with non-relational hierarchical data.</span></span> <span data-ttu-id="76d9f-182">V tomto příkladu se používá hlavně vytvořené pro geografické umístění, jako jsou typy MongoDB `GeoJson2DGeographicCoordinates`.</span><span class="sxs-lookup"><span data-stu-id="76d9f-182">In this example, we are using MongoDB types especially made for geo-locations, like `GeoJson2DGeographicCoordinates`.</span></span>

#### <a name="retrieve-the-database-and-the-collection"></a><span data-ttu-id="76d9f-183">Načte se databáze a kolekce</span><span class="sxs-lookup"><span data-stu-id="76d9f-183">Retrieve the database and the collection</span></span>

<span data-ttu-id="76d9f-184">V aplikaci eShopOnContainers vytvořili jsme kontext vlastní databáze, kde můžeme implementovat kód k načtení databáze a MongoCollections, stejně jako v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="76d9f-184">In eShopOnContainers, we have created a custom database context where we implement the code to retrieve the database and the MongoCollections, as in the following code.</span></span>

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

#### <a name="retrieve-the-data"></a><span data-ttu-id="76d9f-185">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="76d9f-185">Retrieve the data</span></span>

<span data-ttu-id="76d9f-186">V kódu jazyka C#, stejně jako vlastní implementace úložiště, nebo kontrolerů rozhraní Web API můžete napsat kód podobná následující při dotazování pomocí rozhraní MongoDB API.</span><span class="sxs-lookup"><span data-stu-id="76d9f-186">In C# code, like Web API controllers or custom Repositories implementation, you can write similar code to the following when querying through the MongoDB API.</span></span> <span data-ttu-id="76d9f-187">Všimněte si, že `_context` je objekt instancí předchozího `LocationsContext` třídy.</span><span class="sxs-lookup"><span data-stu-id="76d9f-187">Note that the `_context` object is an instance of the previous `LocationsContext` class.</span></span>

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a><span data-ttu-id="76d9f-188">Použít env-var v souboru docker-compose.override.yml připojovacího řetězce MongoDB</span><span class="sxs-lookup"><span data-stu-id="76d9f-188">Use an env-var in the docker-compose.override.yml file for the MongoDB connection string</span></span>

<span data-ttu-id="76d9f-189">Při vytváření objektu položky MongoClient, musí základní parametr, což je přesně `ConnectionString` parametr odkazuje na správnou databázi.</span><span class="sxs-lookup"><span data-stu-id="76d9f-189">When creating a MongoClient object, it needs a fundamental parameter which is precisely the `ConnectionString` parameter pointing to the right database.</span></span> <span data-ttu-id="76d9f-190">V případě aplikaci eShopOnContainers připojovací řetězec může odkazovat na místní kontejner Dockeru MongoDB nebo k databázi Azure Cosmos DB "produkční".</span><span class="sxs-lookup"><span data-stu-id="76d9f-190">In the case of eShopOnContainers, the connection string can point to a local MongoDB Docker container or to a “production” Azure Cosmos DB database.</span></span>  <span data-ttu-id="76d9f-191">Tento připojovací řetězec pochází z proměnné prostředí definované v `docker-compose.override.yml` soubory použité při nasazování s docker-compose nebo Visual Studio, stejně jako v následujícím kódu yml.</span><span class="sxs-lookup"><span data-stu-id="76d9f-191">That connection string comes from the environment variables defined in the `docker-compose.override.yml` files used when deploying with docker-compose or Visual Studio, as in the following yml code.</span></span>

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

<span data-ttu-id="76d9f-192">`ConnectionString` Proměnnou prostředí je vyřešit tímto způsobem: Pokud `ESHOP_AZURE_COSMOSDB` globální proměnná je definována v `.env` soubor s připojovacím řetězcem služby Azure Cosmos DB, použije ho pro přístup k databázi Azure Cosmos DB v cloudu.</span><span class="sxs-lookup"><span data-stu-id="76d9f-192">The `ConnectionString` environment variable is resolved this way: If the `ESHOP_AZURE_COSMOSDB` global variable is defined in the `.env` file with the Azure Cosmos DB connection string, it will use it to access the Azure Cosmos DB database in the cloud.</span></span> 

<span data-ttu-id="76d9f-193">Následující kód ukazuje `.env` souborů pomocí služby Azure Cosmos DB připojovací řetězec globální proměnnou prostředí, jak je implementován v aplikaci eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="76d9f-193">The following code shows the `.env` file with the Azure Cosmos DB connection string global environment variable, as implemented in eShopOnContainers:</span></span>

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

<span data-ttu-id="76d9f-194">By měl Odkomentujte řádek ESHOP_AZURE_COSMOSDB a aktualizace je vaším připojovacím řetězcem služby Azure Cosmos DB, který jste získali z portálu Azure jako podrobně [připojení aplikace MongoDB ke službě Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="76d9f-194">You should uncomment the ESHOP_AZURE_COSMOSDB line and update it with your Azure Cosmos DB connection string obtained from the Azure portal as explained in [Connect a MongoDB application to Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account).</span></span>

<span data-ttu-id="76d9f-195">Pokud `ESHOP_AZURE_COSMOSDB` globální proměnné je prázdný, což znamená, že je opatřený komentáři out v `.env` soubor kontejneru se použije výchozí připojovací řetězec MongoDB odkazující na místní kontejner MongoDB nasazené v aplikaci eShopOnContainers, který se nazývá `nosql.data`, jak je znázorněno v následujícím kódu .yml.</span><span class="sxs-lookup"><span data-stu-id="76d9f-195">If the `ESHOP_AZURE_COSMOSDB` global variable is empty, meaning that it is commented out in the `.env` file, then the container uses a default MongoDB connection string pointing to the local MongoDB container deployed in eShopOnContainers which is named `nosql.data`, as shown in the following .yml code.</span></span> 

#### <a name="additional-resources"></a><span data-ttu-id="76d9f-196">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="76d9f-196">Additional resources</span></span>

-   <span data-ttu-id="76d9f-197">**Modelování dat dokumentů databází NoSQL**
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/modeling-data*](https://docs.microsoft.com/en-us/azure/cosmos-db/modeling-data)</span><span class="sxs-lookup"><span data-stu-id="76d9f-197">**Modeling document data for NoSQL databases**
[*https://docs.microsoft.com/en-us/azure/cosmos-db/modeling-data*](https://docs.microsoft.com/en-us/azure/cosmos-db/modeling-data)</span></span>

-   <span data-ttu-id="76d9f-198">**Vaughn Vernon. Ideální řízeného doménou návrhu agregace Store?**
    [*https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)</span><span class="sxs-lookup"><span data-stu-id="76d9f-198">**Vaughn Vernon. The Ideal Domain-Driven Design Aggregate Store?**
[*https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)</span></span>

-   <span data-ttu-id="76d9f-199">**Úvod do služby Azure Cosmos DB: rozhraní API pro MongoDB** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction*](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction)</span><span class="sxs-lookup"><span data-stu-id="76d9f-199">**Introduction to Azure Cosmos DB: API for MongoDB** 
[*https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction*](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction)</span></span>

-   <span data-ttu-id="76d9f-200">**Azure Cosmos DB: Sestavení webové aplikace MongoDB API pomocí .NET a webu Azure portal** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/create-mongodb-dotnet *](https://docs.microsoft.com/en-us/azure/cosmos-db/create-mongodb-dotnet )</span><span class="sxs-lookup"><span data-stu-id="76d9f-200">**Azure Cosmos DB: Build a MongoDB API web app with .NET and the Azure portal** 
[*https://docs.microsoft.com/en-us/azure/cosmos-db/create-mongodb-dotnet *](https://docs.microsoft.com/en-us/azure/cosmos-db/create-mongodb-dotnet )</span></span>

-   <span data-ttu-id="76d9f-201">**Pro místní vývoj a testování používat emulátor služby Azure Cosmos DB** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator*](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator)</span><span class="sxs-lookup"><span data-stu-id="76d9f-201">**Use the Azure Cosmos DB Emulator for local development and testing** 
[*https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator*](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator)</span></span>

-   <span data-ttu-id="76d9f-202">**Připojení aplikace MongoDB ke službě Azure Cosmos DB** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account*](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account)</span><span class="sxs-lookup"><span data-stu-id="76d9f-202">**Connect a MongoDB application to Azure Cosmos DB** 
[*https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account*](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account)</span></span>

-   <span data-ttu-id="76d9f-203">**Image Dockeru emulátor Cosmos DB (kontejner Windows)** 
    [*https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/*](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/)</span><span class="sxs-lookup"><span data-stu-id="76d9f-203">**The Cosmos DB Emulator Docker image (Windows Container)** 
[*https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/*](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/)</span></span>

-   <span data-ttu-id="76d9f-204">**Image Dockeru MongoDB (Linux a Windows Container)** 
    [*https://hub.docker.com/r/_/mongo/*](https://hub.docker.com/r/_/mongo/)</span><span class="sxs-lookup"><span data-stu-id="76d9f-204">**The MongoDB Docker image (Linux and Windows Container)** 
[*https://hub.docker.com/r/_/mongo/*](https://hub.docker.com/r/_/mongo/)</span></span>

-   <span data-ttu-id="76d9f-205">**Použití MongoChef (Studio 3T) pomocí služby Azure Cosmos DB: rozhraní API pro účet MongoDB** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-mongochef*](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-mongochef)</span><span class="sxs-lookup"><span data-stu-id="76d9f-205">**Use MongoChef (Studio 3T) with an Azure Cosmos DB: API for MongoDB account** 
[*https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-mongochef*](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-mongochef)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="76d9f-206">[Předchozí](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
[další](microservice-application-layer-web-api-design.md)</span><span class="sxs-lookup"><span data-stu-id="76d9f-206">[Previous](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
[Next](microservice-application-layer-web-api-design.md)</span></span>
