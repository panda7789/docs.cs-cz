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
# <a name="use-nosql-databases-as-a-persistence-infrastructure"></a>Použití databází NoSQL jako infrastruktury trvalosti

Při použití NoSQL databáze pro databázi infrastruktury data, obvykle nepoužíváte ORM jako entity framework core. Místo toho použijete rozhraní API poskytované modulem NoSQL, jako je Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB nebo Tabulky úložiště Azure.

Pokud však používáte databázi NoSQL, zejména databázi orientovanou na dokumenty, jako je Azure Cosmos DB, CouchDB nebo RavenDB, způsob návrhu modelu s agregacemi DDD je částečně podobný tomu, jak to můžete provést v EF Core, pokud jde o identifikaci agregačních kořenů, tříd podřízených entit a tříd hodnotových objektů. Ale nakonec výběr databáze bude mít vliv na váš návrh.

Při použití databáze orientované na dokumenty implementujete agregaci jako jeden dokument serializovaný v JSON nebo jiném formátu. Použití databáze je však transparentní z hlediska kódu modelu domény. Při použití databáze NoSQL stále používáte třídy entit a agregační kořenové třídy, ale s větší flexibilitou než při použití EF Core, protože perzistence není relační.

Rozdíl je v tom, jak zachovat tento model. Pokud jste implementovali model domény na základě tříd entit POCO, agnostik k přetrvávání infrastruktury, může to vypadat, že byste se mohli přesunout do jiné infrastruktury trvalosti, dokonce i z relační na NoSQL. To by však neměl být vaším cílem. V různých databázových technologiích vždy existují omezení a kompromisy, takže nebudete moci mít stejný model pro relační nebo NoSQL databáze. Změna modelů trvalosti není triviální úkol, protože transakce a operace trvalosti se budou velmi lišit.

Například v databázi orientované na dokument je v pořádku, aby agregační kořen měl více vlastností podřízené kolekce. V relační databázi dotazování více podřízených vlastností kolekce není snadno optimalizovat, protože získáte příkaz UNION ALL SQL zpět z EF. Mít stejný model domény pro relační databáze nebo NoSQL databáze není jednoduché a neměli byste se o to pokoušet. Opravdu musíte navrhnout model s pochopením toho, jak budou data použita v každé konkrétní databázi.

Výhodou při použití nosql databází je, že entity jsou více denormalized, takže není nastaveno mapování tabulky. Model domény může být flexibilnější než při použití relační databáze.

Při návrhu modelu domény na základě agregace, přechod na NoSQL a databáze orientované na dokumenty může být ještě jednodušší než pomocí relační databáze, protože agregáty, které navrhujete, jsou podobné serializovaných dokumentů v databázi orientované na dokumenty. Pak můžete zahrnout do těchto "tašky" všechny informace, které byste mohli potřebovat pro tento agregát.

Například následující kód JSON je ukázkovou implementací agregace pořadí při použití databáze orientované na dokumenty. Je to podobné pořadí agregace jsme implementovali v eShopOnContainers vzorku, ale bez použití EF Core pod.

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

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a>Úvod do Azure Cosmos DB a nativního rozhraní COSMOS DB API

[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) je globálně distribuovaná databázová služba Microsoftu pro klíčové aplikace. Azure Cosmos DB poskytuje [globální distribuci na klíč](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [elastické škálování propustnosti a úložiště](https://docs.microsoft.com/azure/cosmos-db/partition-data) po celém světě, latence v řádu milisekund na 99. percentilu, [pět jasně definovaných úrovní konzistence](https://docs.microsoft.com/azure/cosmos-db/consistency-levels) a zaručenou vysokou dostupnost. To vše je podloženo [nejlepšími smlouvami SLA v oboru](https://azure.microsoft.com/support/legal/sla/cosmos-db/). Azure Cosmos DB [automaticky indexuje data](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf), aniž by vyžadovala zapojení správy schémat a indexů. Zahrnuje více modelů a podporuje modely dokumentů, klíčových hodnot, grafů a sloupcových dat.

![Diagram znázorňující globální distribuci Azure Cosmos DB.](./media/nosql-database-persistence-infrastructure/azure-cosmos-db-global-distribution.png)

**Obrázek 7-19**. Globální distribuce služby Azure Cosmos DB

Při použití modelu\# C k implementaci agregace, které mají být použity rozhraní\# API Azure Cosmos DB, agregace může být podobná C POCO třídy používané s EF Core. Rozdíl je ve způsobu jejich použití z vrstev aplikace a infrastruktury, jako v následujícím kódu:

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

Můžete vidět, že způsob práce s modelem domény může být podobný způsobu, jakým jej používáte ve vrstvě modelu domény, když je infrastruktura EF. Stále používáte stejné agregační kořenové metody k zajištění konzistence, invariants a ověření v rámci agregace.

Však při zachování modelu do databáze NoSQL, kód a rozhraní API změnit dramaticky ve srovnání s EF základní kód nebo jakýkoli jiný kód související s relační databáze.

## <a name="implement-net-code-targeting-mongodb-and-azure-cosmos-db"></a>Implementace kódu .NET cílení MongoDB a Azure Cosmos DB

### <a name="use-azure-cosmos-db-from-net-containers"></a>Použití azure cosmos db z kontejnerů .NET

K databázím Azure Cosmos DB můžete přistupovat z kódu .NET spuštěného v kontejnerech, stejně jako z jakékoli jiné aplikace .NET. Například microservices Locations.API a Marketing.API v eShopOnContainers jsou implementovány tak, aby mohly využívat databáze Azure Cosmos DB.

Existuje však omezení v Azure Cosmos DB z hlediska vývojového prostředí Dockeru. I když existuje místní [emulátor Azure Cosmos DB,](https://docs.microsoft.com/azure/cosmos-db/local-emulator) který se dá spouštět v místním vývojovém počítači, podporuje jenom Windows. Linux a macOS nejsou podporované.

K dispozici je také možnost spustit tento emulátor na Dockeru, ale pouze na kontejnerech Windows, nikoli s kontejnery Linux. To je počáteční nevýhoda pro vývojové prostředí, pokud je vaše aplikace nasazená jako kontejnery Linuxu, protože v současné době nemůžete nasadit linuxové a windows kontejnery v Dockeru pro Windows současně. Buď všechny nasazené kontejnery musí být pro Linux nebo pro Windows.

Ideální a jednodušší nasazení pro řešení pro vývoj a testování je možnost nasadit databázové systémy jako kontejnery spolu s vlastní kontejnery, takže vaše vývojová a testovací prostředí jsou vždy konzistentní.

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a>Použití rozhraní MongoDB API pro místní vývoj a testování kontejnerů linux/windows plus Azure Cosmos DB

Databáze Cosmos DB podporují rozhraní MongoDB API pro rozhraní .NET i nativní drátový protokol MongoDB. To znamená, že pomocí existujícíovladače, aplikace napsané pro MongoDB nyní můžete komunikovat s Cosmos DB a používat databáze Cosmos DB namísto databáze MongoDB, jak je znázorněno na obrázku 7-20.

![Diagram znázorňující, že Cosmos DB podporuje .NET a MongoDB drátový protokol.](./media/nosql-database-persistence-infrastructure/mongodb-api-wire-protocol.png)

**Obrázek 7-20**. Použití rozhraní MongoDB API a protokolu pro přístup k Azure Cosmos DB

Toto je velmi pohodlný přístup pro prokazované koncepty v prostředí dockeru s kontejnery Linux, protože [image MongoDB Docker](https://hub.docker.com/r/_/mongo/) je víceoblouková image, která podporuje kontejnery Docker Linux a kontejnery Docker Windows.

Jak je znázorněno na následujícím obrázku, pomocí rozhraní MongoDB API eShopOnContainers podporuje kontejnery MongoDB Linux a Windows pro místní vývojové prostředí, ale pak se můžete přesunout do škálovatelného cloudového řešení PaaS jako Azure Cosmos DB jednoduše [změnou připojovacího řetězce MongoDB na odkaz Na Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).

![Diagram znázorňující, že umístění mikroslužby v eShopOnContainers můžete použít buď Cosmos DB nebo Mongo DB.](./media/nosql-database-persistence-infrastructure/eshoponcontainers-mongodb-containers.png)

**Obrázek 7-21**. eShopOnContainers pomocí kontejnerů MongoDB pro dev-env nebo Azure Cosmos DB pro produkční prostředí

Produkční Azure Cosmos DB by běželv cloudu Azure jako PaaS a škálovatelné služby.

Vaše vlastní kontejnery .NET Core můžou běžet na místním vývojovém hostiteli Dockeru (který používá Docker pro Windows v počítači s Windows 10) nebo se nasadit do produkčního prostředí, jako je Kubernetes v Azure AKS nebo Azure Service Fabric. V tomto druhém prostředí byste nasadili pouze vlastní kontejnery .NET Core, ale ne kontejner MongoDB, protože byste používali Azure Cosmos DB v cloudu pro zpracování dat v produkčním prostředí.

Jasnou výhodou použití rozhraní MongoDB API je, že vaše řešení může běžet v databázových strojích, MongoDB nebo Azure Cosmos DB, takže migrace do různých prostředí by měla být snadná. Někdy však stojí za to použít nativní rozhraní API (to je nativní rozhraní API Cosmos DB), aby bylo možné plně využít možnosti konkrétního databázového stroje.

Další porovnání mezi jednoduše pomocí MongoDB versus Cosmos DB v cloudu, najdete [v tématu výhody používání Azure Cosmos DB na této stránce](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction).

### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a>Analyzujte svůj přístup k produkčním aplikacím: MongoDB API vs. Cosmos DB API

V eShopOnContainers používáme rozhraní MongoDB API, protože naší prioritou bylo zásadně mít konzistentní prostředí pro vývoj a testování pomocí databáze NoSQL, která by mohla fungovat i s Azure Cosmos DB.

Pokud ale plánujete používat rozhraní MongoDB API pro přístup k Azure Cosmos DB v Azure pro produkční aplikace, měli byste analyzovat rozdíly ve schopnostech a výkonu při použití rozhraní API MongoDB pro přístup k databázím Azure Cosmos DB ve srovnání s použitím nativního rozhraní API Azure Cosmos DB. Pokud je to podobné, můžete použít MongoDB API a získáte výhodu podpory dvou databázových strojů NoSQL současně.

Clustery MongoDB můžete také použít jako produkční databázi v cloudu Azure také se [službou MongoDB Azure Service](https://www.mongodb.com/scale/mongodb-azure-service). Ale to není služba PaaS poskytovaná společností Microsoft. V tomto případě Azure právě hostuje toto řešení pocházející z MongoDB.

V podstatě je to jen prohlášení o tom, že byste neměli vždy používat rozhraní MongoDB API proti Azure Cosmos DB, jako jsme to udělali v eShopOnContainers, protože to byla vhodná volba pro linuxové kontejnery. Rozhodnutí by mělo být založeno na konkrétních potřebách a testech, které je třeba provést pro produkční aplikaci.

### <a name="the-code-use-mongodb-api-in-net-core-applications"></a>Kód: Použití rozhraní MongoDB API v aplikacích .NET Core

MongoDB API pro rozhraní .NET je založen na balíčcích NuGet, které je potřeba přidat do vašich projektů, jako v projektu Locations.API zobrazeném na následujícím obrázku.

![Snímek obrazovky závislostí v balíčcích MongoDB NuGet.](./media/nosql-database-persistence-infrastructure/mongodb-api-nuget-packages.png)

**Obrázek 7-22**. Odkazy na balíčky MongoDB API NuGet v projektu .NET Core

Pojďme prozkoumat kód v následujících částech.

#### <a name="a-model-used-by-mongodb-api"></a>Model používaný rozhraním MongoDB API

Nejprve je třeba definovat model, který bude obsahovat data pocházející z databáze v paměťovém prostoru aplikace. Tady je příklad modelu používaného pro umístění v eShopOnContainers.

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

Můžete vidět, že existuje několik atributů a typů pocházejících z balíčků MongoDB NuGet.

NoSQL databáze jsou obvykle velmi vhodné pro práci s non-relačníhierarchická data. V tomto příkladu používáme typy MongoDB speciálně `GeoJson2DGeographicCoordinates`pro geografické lokality, jako je .

#### <a name="retrieve-the-database-and-the-collection"></a>Načíst databázi a kolekci

V eShopOnContainers jsme vytvořili vlastní kontext databáze, kde implementujeme kód pro načtení databáze a MongoCollections, jako v následujícím kódu.

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

V kódu Jazyka C#, jako jsou řadiče webového rozhraní API nebo implementace vlastních úložišť, můžete při dotazování prostřednictvím rozhraní MONGODB API napsat podobný kód následujícímu. Všimněte `_context` si, že objekt `LocationsContext` je instancí předchozí třídy.

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a>Použití env-var v souboru docker-compose.override.yml pro připojovací řetězec MongoDB

Při vytváření objektu MongoClient potřebuje základní parametr, `ConnectionString` který je přesně parametr směřující na správnou databázi. V případě eShopOnContainers může připojovací řetězec směřovat na místní kontejner MongoDB Docker nebo na "produkční" databázi Azure Cosmos DB.  Tento připojovací řetězec pochází z `docker-compose.override.yml` proměnných prostředí definovaných v souborech používaných při nasazování s docker-compose nebo Visual Studio, jako v následujícím kódu yml.

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

Proměnná `ConnectionString` prostředí je vyřešena `ESHOP_AZURE_COSMOSDB` takto: Pokud `.env` je globální proměnná definována v souboru pomocí připojovacího řetězce Azure Cosmos DB, použije ji pro přístup k databázi Azure Cosmos DB v cloudu. Pokud není definována, bude trvat hodnotu `mongodb://nosqldata` a použít vývoj MongoDB kontejneru.

Následující kód zobrazuje `.env` soubor s proměnnou globálního prostředí připojovacího řetězce Azure Cosmos DB, jak je implementováno v eShopOnContainers:

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

Odkomentujte ESHOP_AZURE_COSMOSDB řádek a aktualizujte ho pomocí připojovacího řetězce Azure Cosmos DB získaného z portálu Azure, jak je vysvětleno v [části Připojení aplikace MongoDB k Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).

Pokud `ESHOP_AZURE_COSMOSDB` je globální proměnná prázdná, což znamená, že je v souboru `.env` zakomentována, pak kontejner používá výchozí připojovací řetězec MongoDB. Tento připojovací řetězec odkazuje na místní kontejner MongoDB `nosqldata` nasazený v eShopOnContainers, který je pojmenován a definován v souboru docker-compose, jak je znázorněno v následujícím kódu .yml:

``` yml
# docker-compose.yml
version: '3.4'
services:
  # ...Other services...
  nosqldata:
    image: mongo
```

#### <a name="additional-resources"></a>Další zdroje

- **Modelování dat dokumentů pro databáze NoSQL** \
  <https://docs.microsoft.com/azure/cosmos-db/modeling-data>

- **Vaughn Vernon, to je můj zástupce. Ideální domény-řízený design agregát obchod?** \
  <https://kalele.io/blog-posts/the-ideal-domain-driven-design-aggregate-store/>

- **Úvod do Azure Cosmos DB: ROZHRANÍ API pro MongoDB**  \
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction>

- **Azure Cosmos DB: Vytvoření webové aplikace rozhraní API MongoDB s rozhraním .NET a portálem Azure**  \
  <https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet>

- **Použití emulátoru Azure Cosmos DB pro místní vývoj a testování**  \
  <https://docs.microsoft.com/azure/cosmos-db/local-emulator>

- **Připojení aplikace MongoDB k Azure Cosmos DB**  \
  <https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account>

- **Image Cosmos DB Emulátor Docker (Windows Container)**  \
  <https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/>

- **Image MongoDB Docker (Linux a Windows Container)**  \
  <https://hub.docker.com/_/mongo/>

- **Použití MongoChefa (Studio 3T) s Azure Cosmos DB: API pro účet MongoDB**  \
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-mongochef>

>[!div class="step-by-step"]
>[Předchozí](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
>[další](microservice-application-layer-web-api-design.md)
