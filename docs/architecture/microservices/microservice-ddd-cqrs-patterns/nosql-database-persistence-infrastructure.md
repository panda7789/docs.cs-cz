---
title: Použití databází NoSQL jako infrastruktury trvalosti
description: Pochopení použití databází NoSql obecně a Azure Cosmos DB zejména jako možnosti implementace trvalosti.
ms.date: 01/30/2020
ms.openlocfilehash: 7da4141d9aadc4aaa265ac97d328bc4b7569a0cb
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77502378"
---
# <a name="use-nosql-databases-as-a-persistence-infrastructure"></a>Použití databází NoSQL jako infrastruktury trvalosti

Pokud pro vrstvu dat infrastruktury používáte databáze NoSQL, obvykle nepoužíváte ORM, jako je Entity Framework Core. Místo toho použijete rozhraní API poskytované modulem NoSQL, jako jsou například Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB nebo Azure Storage tabulky.

Pokud však použijete databázi NoSQL, zejména databázi orientovanou na dokument, jako je například Azure Cosmos DB, CouchDB nebo RavenDB, způsob návrhu modelu s DDD agregovanými částmi je částečně podobný tomu, jak to lze provést v EF Core, v souvislosti s identifikací agregované kořeny, třídy podřízených entit a třídy objektů hodnot. Ale v konečném důsledku bude mít výběr databáze vliv na váš návrh.

Když použijete databázi orientovanou na dokument, implementujete agregaci jako jediný dokument, který je serializován ve formátu JSON nebo v jiném formátu. Použití databáze je ale transparentní z hlediska kódu doménového modelu. Při použití databáze NoSQL stále používáte třídy entit a agregované kořenové třídy, ale s větší flexibilitou než při použití EF Core, protože trvalost není relační.

Rozdíl je v tom, jak tento model zachovat. Pokud jste model domény implementovali na základě tříd entit POCO, nezávislá se na trvalost infrastruktury, může to vypadat jako v případě, že se můžete přesunout do jiné infrastruktury trvalosti, a to i z relačního na NoSQL. To ale by nemělo být vaším cílem. Existují vždy omezení a kompromisy v různých databázových technologiích, takže nebudete mít stejný model pro relační databáze nebo databáze NoSQL. Změna modelů trvalosti není triviální úloha, protože transakce a operace trvalého uložení budou velmi rozdílné.

Například v databázi orientované na dokument je v pořádku, aby agregovaný kořen měl více vlastností podřízené kolekce. V relační databázi se dotazování na více podřízených vlastností kolekce snadno neoptimalizuje, protože z EF získáte všechny příkazy SQL pro SJEDNOCENí. Stejný doménový model pro relační databáze nebo databáze NoSQL není jednoduchý a neměli byste se ho pokoušet udělat. Model budete opravdu navrhovat s porozuměním, jak se data budou používat v každé konkrétní databázi.

Výhodou při používání databází NoSQL je to, že entity jsou více denormalizované, takže nenastavíte mapování tabulky. Model domény může být pružnější než při použití relační databáze.

Při návrhu doménového modelu založeného na agregacích může být přechod na NoSQL a databáze orientované na dokument ještě snazší než použití relační databáze, protože agregované modely, které navrhujete, jsou podobné serializovaným dokumentům v databázi orientované na dokument. Pak můžete zahrnout do těchto "penalt" všechny informace, které můžete pro tuto agregaci potřebovat.

Například následující kód JSON je ukázková implementace agregační objednávky při použití databáze orientované na dokument. Je podobný agregačnímu pořadí, které jsme implementovali v ukázce eShopOnContainers, ale bez použití EF Core pod ní.

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

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a>Úvod do Azure Cosmos DB a nativní rozhraní API Cosmos DB

[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) je globálně distribuovaná databázová služba Microsoftu pro klíčové aplikace. Azure Cosmos DB poskytuje [globální distribuci na klíč](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [elastické škálování propustnosti a úložiště](https://docs.microsoft.com/azure/cosmos-db/partition-data) po celém světě, latence v řádu milisekund na 99. percentilu, [pět jasně definovaných úrovní konzistence](https://docs.microsoft.com/azure/cosmos-db/consistency-levels) a zaručenou vysokou dostupnost. To vše je podloženo [nejlepšími smlouvami SLA v oboru](https://azure.microsoft.com/support/legal/sla/cosmos-db/). Azure Cosmos DB [automaticky indexuje data](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf), aniž by vyžadovala zapojení správy schémat a indexů. Zahrnuje více modelů a podporuje modely dokumentů, klíčových hodnot, grafů a sloupcových dat.

![Diagram znázorňující Azure Cosmos DB globální distribuce.](./media/nosql-database-persistence-infrastructure/azure-cosmos-db-global-distribution.png)

**Obrázek 7-19**. Globální distribuce služby Azure Cosmos DB

Použijete-li model C\# k implementaci agregace pro použití rozhraní Azure Cosmos DB API, agregace může být podobná třídám jazyka C\# POCO použitým v EF Core. Rozdíl je ve způsobu, jak je používat z vrstev aplikace a infrastruktury, jak je uvedeno v následujícím kódu:

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

Můžete vidět, že jak pracujete s modelem domény, může být podobný způsobu, jakým ho používáte ve vrstvě doménového modelu, pokud je to infrastruktura EF. Stále používáte stejné agregační kořenové metody pro zajištění konzistence, invariant a ověření v rámci agregace.

Když však model zachová do databáze NoSQL, kód a rozhraní API se výrazně v porovnání s EF Core kódem nebo jakýmkoli jiným kódem, který souvisí s relačními databázemi.

## <a name="implement-net-code-targeting-mongodb-and-azure-cosmos-db"></a>Implementace .NET kódu cílící na MongoDB a Azure Cosmos DB

### <a name="use-azure-cosmos-db-from-net-containers"></a>Použití Azure Cosmos DB z kontejnerů .NET

K Azure Cosmos DB databází můžete přistupovat z kódu .NET, který běží v kontejnerech, podobně jako z jakékoli jiné aplikace .NET. Například umístění. API a marketing. mikroslužby pro rozhraní API v eShopOnContainers jsou implementovaná tak, aby mohly využívat databáze Azure Cosmos DB.

Existují však omezení Azure Cosmos DB z pohledu na vývojové prostředí Docker. I když existuje místní [emulátor Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/local-emulator) , který může běžet na místním vývojovém počítači, podporuje jenom Windows. Linux a macOS se nepodporují.

Existuje také možnost spustit tento emulátor v Docker, ale pouze v kontejnerech Windows, nikoli v kontejnerech Linux. To je prvotní nevýhody pro vývojové prostředí, pokud je vaše aplikace nasazena jako kontejnery Linux, protože v současné době nemůžete nasazovat kontejnery Linux a Windows na Docker for Windows současně. Všechny nasazené kontejnery musí být pro Linux nebo Windows.

Ideální a pružně nasazené řešení pro vývoj/testování je schopnost nasadit databázové systémy jako kontejnery spolu s vlastními kontejnery, aby vaše prostředí pro vývoj a testování byla vždy konzistentní.

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a>Použití rozhraní MongoDB API pro místní vývojové/testovací Linux/kontejnery Windows Plus Azure Cosmos DB

Cosmos DB databáze podporují rozhraní API MongoDB pro .NET a také nativní MongoDB síťový protokol. To znamená, že aplikace napsaná pro MongoDB nyní může komunikovat s Cosmos DB a používat Cosmos DB databáze namísto MongoDB databází, jak je znázorněno na obrázku 7-20.

![Diagram znázorňující, že Cosmos DB podporuje síťový protokol .NET a MongoDB.](./media/nosql-database-persistence-infrastructure/mongodb-api-wire-protocol.png)

**Obrázek 7-20**. Přístup k Azure Cosmos DB pomocí rozhraní API a protokolu MongoDB

To je velice pohodlný přístup k ověření konceptů v prostředích Docker s kontejnery Linux, protože [Image Docker MongoDB](https://hub.docker.com/r/_/mongo/) je vícestránkový obrázek, který podporuje kontejnery Docker Linux a Docker Windows Containers.

Jak je znázorněno na následujícím obrázku, používá rozhraní API MongoDB, eShopOnContainers podporuje MongoDB Linux a kontejnery Windows pro místní vývojové prostředí, ale pak můžete přejít na škálovatelné cloudové řešení PaaS jako Azure Cosmos DB, a to jednoduše [změnou připojovacího řetězce MongoDB tak, aby odkazoval na Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).

![Diagram znázorňující, že mikroslužba umístění v eShopOnContainers může používat databázi Cosmos DB nebo Mongo DB.](./media/nosql-database-persistence-infrastructure/eshoponcontainers-mongodb-containers.png)

**Obrázek 7-21**. eShopOnContainers s využitím kontejnerů MongoDB pro vývoj-ENV nebo Azure Cosmos DB pro produkci

Produkční Azure Cosmos DB by běžela v cloudu Azure jako PaaSá a škálovatelná služba.

Vaše vlastní kontejnery .NET Core můžete spustit na místním hostiteli Docker (který používá Docker for Windows v počítači s Windows 10) nebo nasadit do produkčního prostředí, jako je Kubernetes v Azure AKS nebo Azure Service Fabric. V tomto druhém prostředí byste nasadili jenom vlastní kontejnery .NET Core, ale ne kontejner MongoDB, protože byste při zpracování dat v produkčním prostředí použili Azure Cosmos DB v cloudu.

Nejasnou výhodou použití rozhraní MongoDB API je, že vaše řešení může běžet v databázových modulech, MongoDB nebo Azure Cosmos DB, takže migrace do různých prostředí by měla být snadná. Někdy je však vhodné použít nativní rozhraní API (které je nativní Cosmos DB rozhraní API), aby bylo možné plně využít možnosti konkrétního databázového stroje.

Pro další porovnání jednoduchého použití MongoDB a Cosmos DB v cloudu si přečtěte [výhody použití Azure Cosmos DB na této stránce](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction).

### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a>Analýza přístupu k produkčním aplikacím: rozhraní API MongoDB vs. Cosmos DB API

V eShopOnContainers používáme rozhraní MongoDB API, protože naše priorita má zásadní význam pro prostředí pro vývoj a testování s využitím databáze NoSQL, která by mohla spolupracovat i s Azure Cosmos DB.

Pokud ale plánujete používat rozhraní MongoDB API pro přístup k Azure Cosmos DB v Azure pro produkční aplikace, měli byste analyzovat rozdíly v možnostech a výkonu při použití rozhraní MongoDB API pro přístup k databázím Azure Cosmos DB v porovnání s používáním nativního. Azure Cosmos DB rozhraní API. Pokud je to podobné, můžete použít rozhraní MongoDB API a získáte výhodu podpory dvou databázových strojů NoSQL současně.

Clustery MongoDB můžete také použít jako provozní databázi v cloudu Azure pomocí [služby MongoDB Azure](https://www.mongodb.com/scale/mongodb-azure-service). Nejedná se ale o službu PaaS poskytovanou společností Microsoft. V tomto případě je Azure jenom hostitelem tohoto řešení z MongoDB.

V podstatě je to jenom právní omezení, které uvádí, že byste neměli vždycky používat rozhraní MongoDB API proti Azure Cosmos DB, stejně jako v eShopOnContainers, protože to byla vhodná volba pro kontejnery Linux. Rozhodnutí by mělo být založené na konkrétních potřebách a testech, které musíte udělat pro produkční aplikaci.

### <a name="the-code-use-mongodb-api-in-net-core-applications"></a>Kód: použití rozhraní MongoDB API v aplikacích .NET Core

Rozhraní MongoDB API pro .NET je založené na balíčcích NuGet, které musíte přidat do projektů, jako je například v projektu umístění. API na následujícím obrázku.

![Snímek obrazovky se závislostmi v balíčcích NuGet MongoDB](./media/nosql-database-persistence-infrastructure/mongodb-api-nuget-packages.png)

**Obrázek 7-22**. Odkazy na balíčky NuGet rozhraní MongoDB API v projektu .NET Core

Pojďme prozkoumat kód v následujících oddílech.

#### <a name="a-model-used-by-mongodb-api"></a>Model používaný rozhraním API MongoDB

Nejprve je třeba definovat model, který bude obsahovat data přicházející z databáze v paměťovém prostoru aplikace. Tady je příklad modelu používaného pro umístění na adrese eShopOnContainers.

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

Můžete vidět, že z balíčků NuGet MongoDB přicházejí některé atributy a typy.

Databáze NoSQL jsou obvykle velmi vhodné pro práci s nerelačními hierarchickými daty. V tomto příkladu používáme typy MongoDB, hlavně vytvořené pro geografická umístění, jako je `GeoJson2DGeographicCoordinates`.

#### <a name="retrieve-the-database-and-the-collection"></a>Načtení databáze a kolekce

V eShopOnContainers jsme vytvořili vlastní kontext databáze, kde implementujeme kód pro načtení databáze a MongoCollections, jak je uvedeno v následujícím kódu.

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

V C# kódu, jako jsou například řadiče webového rozhraní API nebo implementace vlastních úložišť, můžete při dotazování prostřednictvím rozhraní MongoDB API napsat podobný kód jako následující. Všimněte si, že objekt `_context` je instancí předchozí třídy `LocationsContext`.

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a>V souboru Docker-Compose. override. yml pro připojovací řetězec MongoDB použijte ENV-var.

Při vytváření objektu MongoClient potřebuje základní parametr, který je přesně `ConnectionString` parametr odkazující na správnou databázi. V případě eShopOnContainers může připojovací řetězec ukazovat na místní kontejner Docker MongoDB nebo na produkční Azure Cosmos DBovou databázi.  Tento připojovací řetězec pochází z proměnných prostředí definovaných v `docker-compose.override.yml` soubory používané při nasazení pomocí Docker-YML nebo Visual Studio, jako v následujícím kódu.

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

Proměnná prostředí `ConnectionString` se vyřeší tímto způsobem: Pokud je v souboru `.env` definovaná `ESHOP_AZURE_COSMOSDB` globální proměnná s připojovacím řetězcem Azure Cosmos DB, použije se pro přístup k databázi Azure Cosmos DB v cloudu. Pokud není definovaný, převezme `mongodb://nosqldata` hodnotu a použije MongoDB kontejner pro vývoj.

Následující kód ukazuje `.env` soubor s proměnnou prostředí Azure Cosmos DB připojovacího řetězce, jak je implementováno v eShopOnContainers:

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

Odkomentujte ESHOP_AZURE_COSMOSDB řádek a aktualizujte ho pomocí připojovacího řetězce Azure Cosmos DB získaného z Azure Portal, jak je vysvětleno v tématu [připojení aplikace MongoDB k Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).

Pokud je globální proměnná `ESHOP_AZURE_COSMOSDB` prázdná, znamená to, že je zakomentována do `.env` souboru, pak kontejner používá výchozí připojovací řetězec MongoDB. Tento připojovací řetězec odkazuje na místní kontejner MongoDB nasazený v eShopOnContainers s názvem `nosqldata` a byl definován v souboru Docker-skládání, jak je znázorněno v následujícím kódu. yml:

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

- **Vaughn Vernon. Ideální úložiště s agregovaným návrhem na základě domény?** \
  <https://kalele.io/blog-posts/the-ideal-domain-driven-design-aggregate-store/>

- **Úvod do Azure Cosmos DB: rozhraní API pro MongoDB**  \
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction>

- **Azure Cosmos DB: sestavení webové aplikace API MongoDB pomocí .NET a Azure Portal**  \
  <https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet>

- **Použití emulátoru Azure Cosmos DB pro místní vývoj a testování**  \
  <https://docs.microsoft.com/azure/cosmos-db/local-emulator>

- **Připojení aplikace v MongoDB k Azure Cosmos DB**  \
  <https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account>

- **Obrázek Docker emulátoru Cosmos dB (kontejner Windows)**   \
  <https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/>

- **Image Docker MongoDB (Linux a kontejner Windows)**   \
  <https://hub.docker.com/_/mongo/>

- **Použijte MongoChef (Studio 3T) s Azure Cosmos DB: API pro účet MongoDB**  \
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-mongochef>

>[!div class="step-by-step"]
>[Předchozí](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
>[Další](microservice-application-layer-web-api-design.md)
