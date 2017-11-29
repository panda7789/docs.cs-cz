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
# <a name="using-nosql-databases-as-a-persistence-infrastructure"></a>Použití databáze NoSQL jako trvalost infrastruktury

Použijete-li databáze NoSQL pro vaši infrastrukturu datové vrstvy, obvykle použijete ORM jako Entity Framework Core. Místo toho můžete použít rozhraní API poskytované modul NoSQL, jako je například Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB nebo úložiště tabulek Azure.

Při použití databáze NoSQL, zejména orientované dokumentu databázi jako Azure Cosmos DB, CouchDB nebo RavenDB, způsob návrhu modelu pomocí DDD agregace je však částečně podobná jak vám to provést základní EF namapoval identifikace agregační kořeny, tříd podřízených entit a tříd objektů hodnotu. Ale nakonec, bude mít vliv na výběr databáze při návrhu.

Pokud používáte databázi orientované na dokument, implementaci agregace jako jeden dokument, serializované ve formátu JSON nebo jiného formátu. Použití databáze je však transparentní z domény modelu kódu hlediska. Při použití databáze NoSQL, stále používáte agregační kořenové třídy a tříd entit, ale s více flexibility než při použití EF jádra, protože trvalost není relační.

Rozdíl je v jak zachovat tohoto modelu. Pokud jste implementovali modelu domény podle třídy entity objektů POCO, lhostejné trvalost infrastruktury, může vypadat jako by mohla přesunout do infrastruktury, a jinou trvalost i z relační k NoSQL. Nicméně, který by neměl být vaším cílem. Stále existují omezení v různých databází předá jste zpátky, takže nebudete moci mít stejný model pro relační nebo databáze NoSQL. Změna trvalost modely nebude triviální, protože transakce a trvalost operace se příliš neliší.

Například v databázi orientované dokumentu, je v pořádku pole agregační kořenového tak, aby měl více vlastností podřízené kolekce. Dotaz na více vlastností podřízené kolekce je awful, v relační databázi, protože návratu příkazu SJEDNOCENÍ všech SQL z EF. Má stejný model domény pro relační databáze nebo databáze NoSQL není jednoduché a vyzkoušet by neměl. Máte skutečně návrhu modelu pomocí představu o tom, jak je bude používat v každé konkrétní databázi data.

Výhody při použití databáze NoSQL je, že entity více nenormalizované, takže není nastaveno mapování tabulky. Váš model domény může být flexibilnější než při použití relační databáze.

Při návrhu modelu domény podle agregace, přesunutí NoSQL a orientované dokumentu databáze může být i jednodušší než použití relační databázi, protože agregace, které vám navrhnout jsou podobné serializovat dokumenty v databázi orientované dokumentu. Potom můžete zahrnout tyto "obalů" všechny informace, které může být nutné pro tuto agregace.

Například následující kód JSON je příklad implementace agregace pořadí při použití databáze orientované dokumentu. Je to podobné agregační pořadí implementovali jsme v ukázce eShopOnContainers, ale bez použití EF základní pod.

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

Při použití a C\# modelu k implementaci agregace má být používána něco podobného jako Azure SDK DB Cosmos, agregace je podobná C\# objektů POCO třídy používané s EF jádra. Rozdíl je způsobem je použít z aplikace a infrastrukturu vrstvy, jako v následujícím kódu:

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

Uvidíte, že způsob práce se svým modelem domény mohou být podobným způsobem, můžete ho použít k vrstvě modelu domény EF po infrastruktury. Když nadále používat stejné metody agregační kořenové pro zajištění konzistence, výstupních podmínek a ověření v rámci agregace.

Ale když můžete zachovat modelu do databáze NoSQL, kód a rozhraní API změnu výrazně ve srovnání s EF základní kódu nebo jakýkoli jiný kód související s relačních databází.

#### <a name="additional-resources"></a>Další zdroje

-   **Modelování data v DocumentDB**
    [*https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data*](https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data)

-   **Vaughn Vernon. Ideální řízené domény návrhu agregace úložišti? ** 
     [ *https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)

-   **Trvalost vznikl událostí úložiště pro .NET.** Úložiště GitHub.
    [*https://github.com/NEventStore/NEventStore*](https://github.com/NEventStore/NEventStore)


>[!div class="step-by-step"]
[Předchozí] (infrastructure-persistence-layer-implemenation-entity-framework-core.md) [Další] (microservice-application-layer-web-api-design.md)
