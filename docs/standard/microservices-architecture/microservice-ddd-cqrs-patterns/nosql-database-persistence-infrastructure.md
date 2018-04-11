---
title: Použití databáze NoSQL jako trvalost infrastruktury
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Použití databáze NoSQL jako trvalost infrastruktury
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a6f3a991529aea6560eb12f1400ba2750795ebff
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/10/2018
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

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a>Úvod do Azure Cosmos DB a nativní API DB Cosmos

[Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/introduction) je globálně distribuované databáze služby společnosti Microsoft pro kritické aplikace. Poskytuje Azure Cosmos DB [globální distribuční klíč](https://docs.microsoft.com/en-us/azure/cosmos-db/distribute-data-globally), [elastické škálování propustnost a úložiště](https://docs.microsoft.com/en-us/azure/cosmos-db/partition-data) po celém světě, jednociferné milisekundu latence v 99th percentilu [pět dobře definované úrovně konzistence](https://docs.microsoft.com/en-us/azure/cosmos-db/consistency-levels)a zaručit vysoká dostupnost, všechny zálohovány pomocí [špičkový SLA](https://azure.microsoft.com/support/legal/sla/cosmos-db/). Azure Cosmos DB [automaticky indexuje data](http://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) bez nutnosti zabývat Správa schématu a index. Je více modelu a podporuje dokumentu, klíč hodnota, grafu a sloupcová datové modely.

![](./media/image19.1.png) Obrázek 9-19. Globální distribuční Azure Cosmos DB

Při použití a C\# modelu k implementaci agregace má být používána Cosmos DB rozhraní API služby Azure, agregace může být podobná C\# objektů POCO třídy používané s EF jádra. Rozdíl je způsobem je použít z aplikace a infrastrukturu vrstvy, jako v následujícím kódu:

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

Uvidíte, že způsob práce se svým modelem domény mohou být podobným způsobem, můžete ho použít k vrstvě modelu domény EF po infrastruktury. Když nadále používat stejné metody agregační kořenové pro zajištění konzistence, výstupních podmínek a ověření v rámci agregace.

Ale když můžete zachovat modelu do databáze NoSQL, kód a rozhraní API změnu výrazně ve srovnání s EF základní kódu nebo jakýkoli jiný kód související s relačních databází.

## <a name="implementing-net-code-targeting-mongodb-and-azure-cosmos-db"></a>Implementace kód .NET cílené na MongoDB a Azure Cosmos DB

### <a name="using-azure-cosmos-db-from-net-containers"></a>Pomocí Azure DB Cosmos z kontejnerů rozhraní .NET

Azure Cosmos DB databází můžete přistupovat z kódu .NET spuštění v kontejnerech, jako je z jiné aplikace .NET. Například Locations.API a Marketing.API mikroslužeb v eShopOnContainers se implementují tak mohou spotřebovat databáze Azure Cosmos DB.

Existuje ale omezení v Azure Cosmos DB z Docker vývoj prostředí hlediska. I když dojde místní [emulátoru DB Cosmos Azure](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator) moci spustit v místním vývojovém počítači (například počítač), jako opožděného 2017 právě podporuje Windows, Linux není. 

Je také možné spustit tuto emulátoru na Docker, ale jenom na Windows kontejnery s, nikoli kontejnery Linux. Který je počáteční postižení pro vývojové prostředí, pokud vaše aplikace je nasazená jako kontejnery Linux od, aktuálně, Linux a Windows kontejnerů v Docker pro systém Windows nemůže nasadit ve stejnou dobu. Buď všechny kontejnery nasazení musí být pro Linux nebo Windows.  

Abyste mohli nasadit databázovými systémy jako kontejnery spolu s vlastní kontejnerů, aby se vaše prostředí pro vývoj/testování jsou vždy konzistentní je ideální a více přehledné nasazení řešení pro vývoj/testování.

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a>Použít rozhraní API MongoDB pro místní vývoj/testování Linux a Windows kontejnery plus Azure Cosmos DB

Databáze DB cosmos podporují rozhraní API MongoDB pro rozhraní .NET a také nativní síťový protokol MongoDB. To znamená, že vaše aplikace napsané pro MongoDB pomocí existujících ovladačů, můžete nyní komunikovat s Cosmos DB a používat Cosmos DB databáze místo databáze MongoDB, jak je znázorněno v obrázek 9-20.

![](./media/image19.2.png) Obrázek 9-20. Pomocí rozhraní API MongoDB a protokol pro přístup k databázi Azure Cosmos

Toto je velmi praktické přístup pro ověření koncepty v prostředích Docker s kontejnery Linux, protože [image MongoDB Docker](https://hub.docker.com/r/_/mongo/) je více architektury bitovou kopii, která podporuje kontejnery Docker Linux a Docker Windows kontejnerů.

Jak je znázorněno na obrázku 9 – 21, pomocí rozhraní API MongoDB eShopOnContainers podporuje kontejnery MongoDB Linux a Windows pro místní vývojové prostředí, ale pak můžete přesunout na škálovatelné, PaaS cloudové řešení jako Azure DB Cosmos podle jednoduše [změna připojovací řetězec MongoDB tak, aby odkazoval na databázi Azure Cosmos](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account). 

![](./media/image20-bis.png) Obrázek 9 – 21. eShopOnContainers používat MongoDB kontejnery pro vývojáře env nebo Azure Cosmos DB v provozním prostředí

Provozní Azure Cosmos DB budou pracovat v cloudu Azure jako PaaS a škálovatelné služby.

Vlastní kontejnerů .NET Core lze spustit na hostiteli Docker místní vývoj (který je používán Docker pro Windows v počítači Windows 10) nebo nasadit do provozního prostředí, jako je Kubernetes v Azure AKS nebo Azure Service Fabric. V tomto prostředí druhý by nasadit jenom vlastní kontejnery .NET Core, ale není kontejneru MongoDB vzhledem k tomu, že budete používat databázi Cosmos Azure v cloudu pro zpracování dat v produkčním prostředí.

Vymazat výhodou používání rozhraní API MongoDB je, že vaše řešení by mohl spustit v oba motory databázi MongoDB nebo Cosmos databáze Azure, takže migrace do různých prostředí by mělo být snadné. V některých případech je však smysl pomocí nativních rozhraní API (který je nativní API DB Cosmos) chcete naplno využít možnosti konkrétní databázového stroje.

Další porovnání mezi jednoduše pomocí MongoDB versus Cosmos DB v cloudu najdete v tématu [výhody používání Azure Cosmos DB na této stránce](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction). 


### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a>Analýza budete přistupovat (aplikacích v produkčním prostředí): rozhraní API MongoDB vs. Rozhraní API cosmos DB

V eShopOnContainers používáme rozhraní API MongoDB, protože naše priority je zásadně tak, aby měl konzistentní vývoj/testování prostředí pomocí databáze NoSQL, která může spolupracovat taky s nástrojem Azure Cosmos DB.

Ale pokud jste v úmyslu použít pro přístup k databázi Azure Cosmos v Azure pro výrobní aplikace MongoDB API, byste měli provést analýzu rozdíly v možnosti a výkon při použití MongoDB rozhraní API pro přístup k databázím Azure Cosmos DB ve srovnání s pomocí nativního Rozhraní API Azure Cosmos DB. Pokud je to podobné můžete použít MongoDB API a získat výhody podporuje dva stroje databáze NoSQL ve stejnou dobu. 

Můžete také použít MongoDB clustery jako produkční databázi v cloudu Azure, s [MongoDB Azure Service](https://www.mongodb.com/scale/mongodb-azure-service). Je to ale není PaaS služby poskytované společností Microsoft. V takovém případě je Azure hostitelem právě toto řešení pocházejících z MongoDB.

To je v zásadě platí, pouze upozornění s informacemi o tom, nepoužívejte vždy MongoDB rozhraní API pro Azure Cosmos DB, podle kroků v eShopOnContainers, protože je vhodné volbou pro kontejnery Linux. Rozhodnutí by měla být na základě potřeb a testy, které musíte udělat pro produkční aplikace.  

### <a name="the-code-using-mongodb-api-in-net-core-applications"></a>Kód: použití rozhraní API MongoDB v aplikacích .NET Core

MongoDB rozhraní API pro .NET je založená na balíčky NuGet, které je nutné přidat do vašich projektů, jako je Locations.API zobrazí obrázek 9 – 22.

![](./media/image21-bis.png) Obrázek 9 22. Balíčky NuGet MongoDB rozhraní API odkazů v projektu .NET Core

Umožňuje prozkoumat kód v následujících částech.

#### <a name="a-model-used-by-mongodb-api"></a>Model používá rozhraní API MongoDB

Nejdřív musíte definovat model, který bude obsahovat dat pocházejících z databáze v paměti vaší aplikace. Tady je příklad modelu v eShopOnContainers použito pro umístění.

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

Uvidíte, že se několik atributů a typy pocházejících z balíčky MongoDB NuGet.

Databáze NoSQL jsou obvykle velmi dobře hodí pro práci s nerelačními daty hierarchické. V tomto příkladu používáme expecially typy MongoDB vytvořené pro zeměpisných míst, jako je `GeoJson2DGeographicCoordinates`.

#### <a name="retrieve-the-database-and-the-collection"></a>Načtení databáze a kolekce

V eShopOnContainers jsme vytvořili vlastní databázi kontextu, kde implementaci kód pro načtení databáze a MongoCollections, jako v následujícím kódu.

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

#### <a name="retrieve-the-data"></a>Načtení dat

V kódu jazyka C#, jako řadiče webového rozhraní API nebo vlastní implementace úložiště můžete napsat podobný kód pro následující při dotazování prostřednictvím rozhraní API MongoDB. Všimněte si, že `_context` je objekt instancí předchozího `LocationsContext` třídy.

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a>Použít env-var v souboru docker compose.override.yml pro MongoDB připojovací řetězec

Při vytváření objektu MongoClient, je nutné základní parametr, který je přesně `ConnectionString` parametr odkazující na správné databázi. V případě eShopOnContainers může bod připojovací řetězec místní kontejner MongoDB Docker nebo k databázi Azure Cosmos DB "výroba".  Tento připojovací řetězec pochází z proměnné definované v `docker-compose.override.yml` soubory používané při nasazení s docker-compose nebo Visual Studio, jako v následujícím kódu yml.

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

`ConnectionString` – Proměnná prostředí je vyřešit tímto způsobem: Pokud `ESHOP_AZURE_COSMOSDB` – globální proměnná je definována v `.env` souboru připojovacím řetězcem Azure Cosmos DB, použije ho pro přístup k databázi Azure Cosmos DB v cloudu. 

Následující kód ukazuje `.env` soubor s proměnnou globální prostředí Azure Cosmos DB připojovacího řetězce, jak jsou implementované ve eShopOnContainers:

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

Měli zrušte komentář u ESHOP_AZURE_COSMOSDB řádku a aktualizace se službou Azure Cosmos DB připojovací řetězec získali z portálu Azure jako vysvětlené v [připojit MongoDB aplikace pro Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account).

Pokud `ESHOP_AZURE_COSMOSDB` – globální proměnná je prázdná, což znamená, že je odhlašování komentář v `.env` souboru kontejneru se použije výchozí MongoDB připojovací řetězec odkazující na místní MongoDB kontejneru nasazené v eShopOnContainers, která se nazývá `nosql.data`, jak je znázorněno v následujícím kódu .yml. 

#### <a name="additional-resources"></a>Další zdroje

-   **Data dokumentu pro databáze NoSQL modelování**
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/modeling-data*](https://docs.microsoft.com/en-us/azure/cosmos-db/modeling-data)

-   **Vaughn Vernon. Ideální řízené domény návrhu agregace úložišti?**
    [*https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)

-   **Úvod do Azure Cosmos DB: rozhraní API pro MongoDB** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction*](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction)

-   **Azure Cosmos DB: Vytvoření webové aplikace MongoDB API pomocí rozhraní .NET a portálu Azure** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/create-mongodb-dotnet *](https://docs.microsoft.com/en-us/azure/cosmos-db/create-mongodb-dotnet )

-   **Použití emulátoru DB Cosmos Azure pro místní vývoj a testování** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator*](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator)

-   **Připojení aplikace MongoDB pro Azure Cosmos DB** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account*](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account)

-   **Obrázek Cosmos DB emulátoru Docker (kontejneru systému Windows)** 
    [*https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/*](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/)

-   **Image MongoDB Docker (Linux a kontejneru systému Windows)** 
    [*https://hub.docker.com/r/_/mongo/*](https://hub.docker.com/r/_/mongo/)

-   **Pomocí Azure DB Cosmos MongoChef (Studio 3T): rozhraní API pro MongoDB účet** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-mongochef*](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-mongochef)


>[!div class="step-by-step"]
[Předchozí] (infrastructure-persistence-layer-implemenation-entity-framework-core.md) [Další] (microservice-application-layer-web-api-design.md)
