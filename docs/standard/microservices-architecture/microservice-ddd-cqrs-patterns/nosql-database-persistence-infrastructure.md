---
title: "Použití databáze NoSQL jako trvalost infrastruktury"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Použití databáze NoSQL jako trvalost infrastruktury"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: e4b63511069b89cc5761ce7ed64f09e9035a56a3
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="using-nosql-databases-as-a-persistence-infrastructure"></a><span data-ttu-id="e7083-104">Použití databáze NoSQL jako trvalost infrastruktury</span><span class="sxs-lookup"><span data-stu-id="e7083-104">Using NoSQL databases as a persistence infrastructure</span></span>

<span data-ttu-id="e7083-105">Použijete-li databáze NoSQL pro vaši infrastrukturu datové vrstvy, obvykle použijete ORM jako Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="e7083-105">When you use NoSQL databases for your infrastructure data tier, you typically do not use an ORM like Entity Framework Core.</span></span> <span data-ttu-id="e7083-106">Místo toho můžete použít rozhraní API poskytované modul NoSQL, jako je například Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB nebo úložiště tabulek Azure.</span><span class="sxs-lookup"><span data-stu-id="e7083-106">Instead you use the API provided by the NoSQL engine, such as Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB, or Azure Storage Tables.</span></span>

<span data-ttu-id="e7083-107">Při použití databáze NoSQL, zejména orientované dokumentu databázi jako Azure Cosmos DB, CouchDB nebo RavenDB, způsob návrhu modelu pomocí DDD agregace je však částečně podobná jak vám to provést základní EF namapoval identifikace agregační kořeny, tříd podřízených entit a tříd objektů hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e7083-107">However, when you use a NoSQL database, especially a document-oriented database like Azure Cosmos DB, CouchDB, or RavenDB, the way you design your model with DDD aggregates is partially similar to how you can do it in EF Core, in regards to the identification of aggregate roots, child entity classes, and value object classes.</span></span> <span data-ttu-id="e7083-108">Ale nakonec, bude mít vliv na výběr databáze při návrhu.</span><span class="sxs-lookup"><span data-stu-id="e7083-108">But, ultimately, the database selection will impact in your design.</span></span>

<span data-ttu-id="e7083-109">Pokud používáte databázi orientované na dokument, implementaci agregace jako jeden dokument, serializované ve formátu JSON nebo jiného formátu.</span><span class="sxs-lookup"><span data-stu-id="e7083-109">When you use a document-oriented database, you implement an aggregate as a single document, serialized in JSON or another format.</span></span> <span data-ttu-id="e7083-110">Použití databáze je však transparentní z domény modelu kódu hlediska.</span><span class="sxs-lookup"><span data-stu-id="e7083-110">However, the use of the database is transparent from a domain model code point of view.</span></span> <span data-ttu-id="e7083-111">Při použití databáze NoSQL, stále používáte agregační kořenové třídy a tříd entit, ale s více flexibility než při použití EF jádra, protože trvalost není relační.</span><span class="sxs-lookup"><span data-stu-id="e7083-111">When using a NoSQL database, you still are using entity classes and aggregate root classes, but with more flexibility than when using EF Core because the persistence is not relational.</span></span>

<span data-ttu-id="e7083-112">Rozdíl je v jak zachovat tohoto modelu.</span><span class="sxs-lookup"><span data-stu-id="e7083-112">The difference is in how you persist that model.</span></span> <span data-ttu-id="e7083-113">Pokud jste implementovali modelu domény podle třídy entity objektů POCO, lhostejné trvalost infrastruktury, může vypadat jako by mohla přesunout do infrastruktury, a jinou trvalost i z relační k NoSQL.</span><span class="sxs-lookup"><span data-stu-id="e7083-113">If you implemented your domain model based on POCO entity classes, agnostic to the infrastructure persistence, it might look like you could move to a different persistence infrastructure, even from relational to NoSQL.</span></span> <span data-ttu-id="e7083-114">Nicméně, který by neměl být vaším cílem.</span><span class="sxs-lookup"><span data-stu-id="e7083-114">However, that should not be your goal.</span></span> <span data-ttu-id="e7083-115">Stále existují omezení v různých databází předá jste zpátky, takže nebudete moci mít stejný model pro relační nebo databáze NoSQL.</span><span class="sxs-lookup"><span data-stu-id="e7083-115">There are always constraints in the different databases will push you back, so you will not be able to have the same model for relational or NoSQL databases.</span></span> <span data-ttu-id="e7083-116">Změna trvalost modely nebude triviální, protože transakce a trvalost operace se příliš neliší.</span><span class="sxs-lookup"><span data-stu-id="e7083-116">Changing persistence models would not be trivial, because transactions and persistence operations will be very different.</span></span>

<span data-ttu-id="e7083-117">Například v databázi orientované dokumentu, je v pořádku pole agregační kořenového tak, aby měl více vlastností podřízené kolekce.</span><span class="sxs-lookup"><span data-stu-id="e7083-117">For example, in a document-oriented database, it is okay for an aggregate root to have multiple child collection properties.</span></span> <span data-ttu-id="e7083-118">Dotaz na více vlastností podřízené kolekce je awful, v relační databázi, protože návratu příkazu SJEDNOCENÍ všech SQL z EF.</span><span class="sxs-lookup"><span data-stu-id="e7083-118">In a relational database, querying multiple child collection properties is awful, because you get a UNION ALL SQL statement back from EF.</span></span> <span data-ttu-id="e7083-119">Má stejný model domény pro relační databáze nebo databáze NoSQL není jednoduché a vyzkoušet by neměl.</span><span class="sxs-lookup"><span data-stu-id="e7083-119">Having the same domain model for relational databases or NoSQL databases is not simple, and you should not try it.</span></span> <span data-ttu-id="e7083-120">Máte skutečně návrhu modelu pomocí představu o tom, jak je bude používat v každé konkrétní databázi data.</span><span class="sxs-lookup"><span data-stu-id="e7083-120">You really have to design your model with an understanding of how the data is going to be used in each particular database.</span></span>

<span data-ttu-id="e7083-121">Výhody při použití databáze NoSQL je, že entity více nenormalizované, takže není nastaveno mapování tabulky.</span><span class="sxs-lookup"><span data-stu-id="e7083-121">A benefit when using NoSQL databases is that the entities are more denormalized, so you do not set a table mapping.</span></span> <span data-ttu-id="e7083-122">Váš model domény může být flexibilnější než při použití relační databáze.</span><span class="sxs-lookup"><span data-stu-id="e7083-122">Your domain model can be more flexible than when using a relational database.</span></span>

<span data-ttu-id="e7083-123">Při návrhu modelu domény podle agregace, přesunutí NoSQL a orientované dokumentu databáze může být i jednodušší než použití relační databázi, protože agregace, které vám navrhnout jsou podobné serializovat dokumenty v databázi orientované dokumentu.</span><span class="sxs-lookup"><span data-stu-id="e7083-123">When you design your domain model based on aggregates, moving to NoSQL and document-oriented databases might be even easier than using a relational database, because the aggregates you design are similar to serialized documents in a document-oriented database.</span></span> <span data-ttu-id="e7083-124">Potom můžete zahrnout tyto "obalů" všechny informace, které může být nutné pro tuto agregace.</span><span class="sxs-lookup"><span data-stu-id="e7083-124">Then you can include in those “bags” all the information you might need for that aggregate.</span></span>

<span data-ttu-id="e7083-125">Například následující kód JSON je příklad implementace agregace pořadí při použití databáze orientované dokumentu.</span><span class="sxs-lookup"><span data-stu-id="e7083-125">For instance, the following JSON code is a sample implementation of an order aggregate when using a document-oriented database.</span></span> <span data-ttu-id="e7083-126">Je to podobné agregační pořadí implementovali jsme v ukázce eShopOnContainers, ale bez použití EF základní pod.</span><span class="sxs-lookup"><span data-stu-id="e7083-126">It is similar to the order aggregate we implemented in the eShopOnContainers sample, but without using EF Core underneath.</span></span>

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

<span data-ttu-id="e7083-127">Při použití a C\# modelu k implementaci agregace má být používána něco podobného jako Azure SDK DB Cosmos, agregace je podobná C\# objektů POCO třídy používané s EF jádra.</span><span class="sxs-lookup"><span data-stu-id="e7083-127">When you use a C\# model to implement the aggregate to be used by something like the Azure Cosmos DB SDK, the aggregate is similar to the C\# POCO classes used with EF Core.</span></span> <span data-ttu-id="e7083-128">Rozdíl je způsobem je použít z aplikace a infrastrukturu vrstvy, jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="e7083-128">The difference is in the way to use them from the application and infrastructure layers, as in the following code:</span></span>

```csharp
// C# EXAMPLE OF AN ORDER AGGREGATE BEING PERSISTED WITH DOCUMENTDB API
// *** Domain Model Code ***
// Aggregate: Create an Order object with its child entities and/or value objects.
// Then, use AggregateRoot’s methods to add the nested objects so invariants and
// logic is consistent across the nested properties (value objects and entities).
// This can be saved as JSON as is without converting into rows/columns.
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

OrderItem orderItem2 = new OrderItem
{
    Id = 20170012,
    ProductId = "123457",
    ProductName = ".NET Mug",
    UnitPrice = 15,
    Units = 1,
    Discount = 0;
};

//Using methods with domain logic within the entity. No anemic-domain model
orderAggregate.AddOrderItem(orderItem1);
orderAggregate.AddOrderItem(orderItem2);

// *** End of Domain Model Code ***
//...
// *** Infrastructure Code using Cosmos DB Client API ***
Uri collectionUri = UriFactory.CreateDocumentCollectionUri(databaseName,
    collectionName);

await client.CreateDocumentAsync(collectionUri, order);

// As your app evolves, let's say your object has a new schema. You can insert
// OrderV2 objects without any changes to the database tier.
Order2 newOrder = GetOrderV2Sample("IdForSalesOrder2");
await client.CreateDocumentAsync(collectionUri, newOrder);
```

<span data-ttu-id="e7083-129">Uvidíte, že způsob práce se svým modelem domény mohou být podobným způsobem, můžete ho použít k vrstvě modelu domény EF po infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="e7083-129">You can see that the way you work with your domain model can be similar to the way you use it in your domain model layer when the infrastructure is EF.</span></span> <span data-ttu-id="e7083-130">Když nadále používat stejné metody agregační kořenové pro zajištění konzistence, výstupních podmínek a ověření v rámci agregace.</span><span class="sxs-lookup"><span data-stu-id="e7083-130">You still use the same aggregate root methods to ensure consistency, invariants, and validations within the aggregate.</span></span>

<span data-ttu-id="e7083-131">Ale když můžete zachovat modelu do databáze NoSQL, kód a rozhraní API změnu výrazně ve srovnání s EF základní kódu nebo jakýkoli jiný kód související s relačních databází.</span><span class="sxs-lookup"><span data-stu-id="e7083-131">However, when you persist your model into the NoSQL database, the code and API change dramatically compared to EF Core code or any other code related to relational databases.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="e7083-132">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="e7083-132">Additional resources</span></span>

-   <span data-ttu-id="e7083-133">**Modelování data v DocumentDB**
    [*https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data*](https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data)</span><span class="sxs-lookup"><span data-stu-id="e7083-133">**Modeling data in DocumentDB**
[*https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data*](https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data)</span></span>

-   <span data-ttu-id="e7083-134">**Vaughn Vernon. Ideální řízené domény návrhu agregace úložišti? ** 
     [ *https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)</span><span class="sxs-lookup"><span data-stu-id="e7083-134">**Vaughn Vernon. The Ideal Domain-Driven Design Aggregate Store?**
[*https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)</span></span>

-   <span data-ttu-id="e7083-135">**Trvalost vznikl událostí úložiště pro .NET.**</span><span class="sxs-lookup"><span data-stu-id="e7083-135">**A persistence agnostic Event Store for .NET.**</span></span> <span data-ttu-id="e7083-136">Úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="e7083-136">GitHub repo.</span></span>
    [<span data-ttu-id="e7083-137">*https://github.com/NEventStore/NEventStore*</span><span class="sxs-lookup"><span data-stu-id="e7083-137">*https://github.com/NEventStore/NEventStore*</span></span>](https://github.com/NEventStore/NEventStore)


>[!div class="step-by-step"]
<span data-ttu-id="e7083-138">[Předchozí] (infrastructure-persistence-layer-implemenation-entity-framework-core.md) [Další] (microservice-application-layer-web-api-design.md)</span><span class="sxs-lookup"><span data-stu-id="e7083-138">[Previous] (infrastructure-persistence-layer-implemenation-entity-framework-core.md) [Next] (microservice-application-layer-web-api-design.md)</span></span>
