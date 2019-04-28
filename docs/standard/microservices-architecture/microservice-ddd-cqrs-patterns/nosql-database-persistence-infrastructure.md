---
title: Použití databází NoSQL jako infrastruktury trvalosti
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Vysvětlení použití databází NoSql v obecné a Azure Cosmos DB zejména jako možnost k implementaci trvalost.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 851068b511106157a759a0600c404b4d1154e5ee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761039"
---
# <a name="use-nosql-databases-as-a-persistence-infrastructure"></a>Použití databází NoSQL jako infrastruktury trvalosti

Použijete-li databáze NoSQL pro datovou vrstvu, infrastruktury, je obvykle velmi riskantní používat ORM jako Entity Framework Core. Místo toho použijte rozhraní API poskytuje modul NoSQL, jako je Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB nebo tabulky v úložišti Azure.

Použijete-li databáze NoSQL, zvláště dokumentově orientované databázi jako službu Azure Cosmos DB, CouchDB nebo RavenDB, tak, jak při návrhu modelu pomocí agregace DDD ale částečně podobný jak to zvládnete v EF Core vztahující k identifikaci agregační kořeny podřízených tříd entit a objekt třídy hodnoty. Ale nakonec bude mít vliv výběr databáze v návrhu.

Při použití databáze dokumentově orientované implementaci agregace jako jeden dokument, serializované ve formátu JSON nebo jiný formát. Použití databáze je však transparentní z domény modelu kódu hlediska. Při použití databáze NoSQL, stále používáte tříd entit a agregační kořenové třídy, ale s větší flexibilitou než při použití EF Core, protože není relační stálost.

Rozdíl je v jak zachovat tohoto modelu. Pokud jste implementovali doménový model podle tříd entit POCO, zohledňovat trvalosti infrastruktury, může vypadat podobně, jako by mohla přesunout do jiné trvalosti infrastruktury, dokonce i z relační NoSQL. Nicméně, který by neměl být vaším cílem. Se vždy najde nějaká omezení a kompromisy v oblasti technologií jinou databázi, takže není možné mít stejný model pro relační nebo NoSQL databáze. Změna trvalost modely není jednoduchý úkol, protože transakce a operace trvalého uložení bude velmi lišit.

Například v databázi dokumentově orientované je dobrá pro agregační kořenovou mít více vlastností podřízené kolekce. V relační databázi dotazování na více vlastností podřízené kolekce není optimalizována snadno, protože příkaz jazyka SQL SJEDNOCENÍ všech získáte zpět ze EF. S modelem domény pro relační databáze nebo NoSQL databáze není jednoduché a by se neměl pokoušet provést. Musíte opravdu svůj přístup k návrhu modelu se seznámíte s jak se bude používat v každé databázi konkrétního data.

Výhoda po použití databází NoSQL, že entity jsou více Nenormalizovaná tak nenastavujte mapování tabulky. Doménový model může být flexibilnější než při použití relační databáze.

Při návrhu doménový model podle agregace, Přesun do NoSQL a dokumentově orientované databáze může být ještě jednodušší než při použití relační databázi, protože jsou podobné agregace, navrhnout serializovat dokumenty v databázi dokumentově orientované. V těchto "kontejnery objektů a dat" lze pak zahrnout všechny informace, které může být nutné pro tuto agregaci.

Například následující kód JSON je ukázková implementace agregace pořadí při použití dokumentově orientované databáze. Je to podobné agregační pořadí, implementovali jsme v ukázkové aplikaci eShopOnContainers, ale bez použití EF Core pod.

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

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a>Úvod do služby Azure Cosmos DB a nativní rozhraní API Cosmos DB

[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) je globálně distribuovaná databázová služba od Microsoftu pro klíčové aplikace. Azure Cosmos DB poskytuje [globální distribuce na klíč](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [elastické škálování propustnosti a úložiště](https://docs.microsoft.com/azure/cosmos-db/partition-data) po celém světě, řádu milisekund na 99. percentilu, [pět jasně definovaných úrovní konzistence](https://docs.microsoft.com/azure/cosmos-db/consistency-levels)a zaručenou vysokou dostupnost, vše zajištěné [špičkové smlouvy SLA](https://azure.microsoft.com/support/legal/sla/cosmos-db/). Azure Cosmos DB [automaticky indexuje data](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf), aniž by vyžadovala zapojení správy schémat a indexů. Zahrnuje více modelů a podporuje modely dokumentů, klíčových hodnot, grafů a sloupcových dat.

![Azure Cosmos DB je globálně distribuovaná databáze s nízkou latencí zaručené, kterému mají přístup s čtyři protokoly rozhraní API. ](./media/image19.1.png)
**Obrázek 7-19**. Globální distribuce služby Azure Cosmos DB

Když použijete C\# model k implementaci agregace pro rozhraní Azure Cosmos DB API, agregace může být podobně jako c\# POCO třídy používané s EF Core. Rozdíl je tak, jak používat z vrstvy aplikace a infrastruktury, jako v následujícím kódu:

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

Uvidíte, že může být podobným způsobem, jakým se použije na úrovni vrstvy modelu domény při infrastruktury je EF tak, jak pracovat s modelu domény. K zajištění konzistence, výstupních podmínek a ověření v rámci agregace nadále používat stejné agregační kořenové metody.

Ale když trvale uložíte modelu do databáze NoSQL, kód a výrazně porovnání EF Core kódu změnu rozhraní API nebo jakýkoli jiný kód související s relačních databází.

## <a name="implement-net-code-targeting-mongodb-and-azure-cosmos-db"></a>Implementace kódu .NET, které cílí na MongoDB a Azure Cosmos DB

### <a name="use-azure-cosmos-db-from-net-containers"></a>Použití služby Azure Cosmos DB z kontejnery .NET

Databáze Azure Cosmos DB můžete přistupovat z kódu .NET spuštěných v kontejnerech, stejně jako jakékoli jiné aplikace .NET. Například Locations.API a Marketing.API mikroslužeb v aplikaci eShopOnContainers jsou implementované tak spotřebují databází Azure Cosmos DB.

Existuje ale omezení ve službě Azure Cosmos DB z Dockeru vývojové prostředí hlediska. I když dojde místní [emulátor služby Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/local-emulator) možné spouštět v místním vývojovém počítači (například počítač), jako opožděné 2017 právě podporuje Windows, Linuxu ne. 

Je také možné spustit tuto emulátor v Dockeru, ale jenom v kontejnerech Windows, ne s kontejnery Linuxu. To je počáteční postižení pro vývojové prostředí, pokud vaše aplikace bude nasazena jako kontejnery Linux, od, aktuálně, nelze nasadit systémy Linux a kontejnery Windows na Docker pro Windows ve stejnou dobu. Buď všechny kontejnery, které nasazuje, musí být pro Linux nebo Windows.

Ideální a jednodušší nasazení pro vývoj/testování řešení je moct nasadit databázovými systémy jako kontejnery spolu s vlastní kontejnery tak, aby byly vždy konzistentní vývojová a testovací prostředí.

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a>Pro místní vývoj a testování systému Linux/Windows kontejnery a služby Azure Cosmos DB pomocí rozhraní MongoDB API

Databáze cosmos DB podporovat rozhraní MongoDB API pro .NET, stejně jako nativní přenosový protokol MongoDB. To znamená, že pomocí existujících ovladačů, vaše aplikace napsané pro MongoDB můžou nyní komunikovat s Cosmos DB a pomocí databáze Cosmos DB místo databází MongoDB, jak je znázorněno v obrázek 7 – 20.

![Cosmos DB podporuje MongoDB API pro .NET a MongoDB přenosový protokol, můžete snadno přepínat z MongoDb do služby Cosmos DB. ](./media/image19.2.png)
 **Obrázek 7 – 20**. Přístup k Azure Cosmos DB pomocí rozhraní MongoDB API a protokol

To je velmi efektivní přístup pro testování konceptů v prostředí Dockeru s kontejnery Linuxu, protože [image Dockeru MongoDB](https://hub.docker.com/r/_/mongo/) je více architektury image, která podporuje kontejnery Linuxu Dockeru a kontejnerech Dockeru Windows.

Jak je znázorněno na následujícím obrázku, s použitím rozhraní MongoDB API, aplikaci eShopOnContainers podporuje kontejnery MongoDB, Linux a Windows pro místní vývojové prostředí, ale pak můžete přesunout ke škálovatelným, PaaS cloudové řešení jako Azure Cosmos DB pomocí jednoduše [ Změna připojovacího řetězce MongoDB tak, aby odkazovala na službu Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).

![Umístění mikroslužeb v aplikaci eShopOnContainers je implementována pomocí databáze MongoDB, ale můžete měl přepnout do služby Cosmos DB pomocí stačí, když změníte připojovací řetězec. ](./media/image20-bis.png)
 **Obrázek 7 – 21**. pomocí kontejnerů MongoDB pro vývoj env nebo služby Azure Cosmos DB pro produkční aplikaci eShopOnContainers

Výrobní službu Azure Cosmos DB by běžet v cloudu Azure jako a škálovatelná služba PaaS.

Své vlastní kontejnery .NET Core můžete spustit na místním vývojovém hostitele Docker, (, který je používán Docker pro Windows v počítači s Windows 10) nebo nasazení do produkčního prostředí, jako je Kubernetes v Azure AKS nebo Azure Service Fabric. V tomto druhém prostředí by nasadit jenom vlastní kontejnery .NET Core, ale ne kontejner MongoDB vzhledem k tomu, že budete používat Azure Cosmos DB v cloudu pro zpracování dat v produkčním prostředí.

Vymazat výhodou pomocí rozhraní MongoDB API je, že vaše řešení může běžet v obou databázových strojů, MongoDB nebo Azure Cosmos DB, migrace do různých prostředí by tak měly být snadné. Někdy je však vhodné používat nativní rozhraní API (který je nativní rozhraní API Cosmos DB) Pokud chcete naplno využít možnosti konkrétní databázového stroje.

Další porovnání mezi jednoduše pomocí databáze MongoDB a Cosmos DB v cloudu najdete v tématu [výhody používání služby Azure Cosmos DB na této stránce](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction). 

### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a>Analyzujte svůj přístup pro aplikace v produkčním prostředí: Rozhraní MongoDB API služby vs. Rozhraní API služby cosmos DB

V aplikaci eShopOnContainers používáme rozhraní MongoDB API, protože naší prioritou je v podstatě mít konzistentní vývojového a testovacího prostředí používat databázi NoSQL, která může spolupracovat také se službami Azure Cosmos DB.

Nicméně pokud jste v úmyslu použít rozhraní MongoDB API pro přístup k Azure Cosmos DB v Azure pro aplikace v produkčním prostředí, je vhodné analyzovat, rozdíly v možnosti a výkon při přístupu k ve srovnání s použitím nativního databází Azure Cosmos DB pomocí rozhraní MongoDB API Rozhraní API služby Azure Cosmos DB. Pokud je to podobné můžete použít rozhraní API MongoDB a budete mít k dispozici podpora ve stejnou dobu dvěma motory databáze NoSQL.

Můžete také použít clustery MongoDB jako provozní databáze v cloudu Azure, s [MongoDB služby Azure](https://www.mongodb.com/scale/mongodb-azure-service). Ale to není služba PaaS poskytnutých microsoftem. V takovém případě je právě hostování Azure toto řešení z MongoDB.

V podstatě je to pouze upozornění s informacemi o tom, že byste neměli vždy používat rozhraní MongoDB API službou Azure Cosmos DB, jako jsme to udělali v aplikaci eShopOnContainers protože je vhodné volbou pro kontejnery Linuxu. Rozhodnutí by měla být podle potřeb a testy, které musíte udělat pro aplikace v produkčním prostředí.

### <a name="the-code-use-mongodb-api-in-net-core-applications"></a>Kód: Použití rozhraní API MongoDB v aplikacích .NET Core

Rozhraní MongoDB API pro .NET je založená na balíčky NuGet, které je třeba přidat do vašich projektů, jako je v projektu Locations.API je znázorněno na následujícím obrázku.

![Zobrazení Průzkumník řešení zobrazující balíčky závislostí nuget MongoDB.](./media/image21-bis.png)

**Obrázek 7 – 22**. Balíčky NuGet rozhraní API MongoDB odkazů v projektu .NET Core

Pojďme prozkoumat kód v následujících částech.

#### <a name="a-model-used-by-mongodb-api"></a>Model používaný v rozhraní MongoDB API

Nejprve budete muset definovat model, který bude obsahovat data z databáze v paměti aplikace. Tady je příklad modelu v aplikaci eShopOnContainers použito pro umístění.

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

Uvidíte, že existuje několik atributů a typy pocházející z balíčků MongoDB NuGet.

Databáze NoSQL jsou obvykle velmi dobře hodí pro práci s nerelačními hierarchická data. V tomto příkladu se používá hlavně vytvořené pro geografické umístění, jako jsou typy MongoDB `GeoJson2DGeographicCoordinates`.

#### <a name="retrieve-the-database-and-the-collection"></a>Načte se databáze a kolekce

V aplikaci eShopOnContainers vytvořili jsme kontext vlastní databáze, kde můžeme implementovat kód k načtení databáze a MongoCollections, stejně jako v následujícím kódu.

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

V kódu jazyka C#, stejně jako vlastní implementace úložiště, nebo kontrolerů rozhraní Web API můžete napsat kód podobná následující při dotazování pomocí rozhraní MongoDB API. Všimněte si, že `_context` je objekt instancí předchozího `LocationsContext` třídy.

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a>Použít env-var v souboru docker-compose.override.yml připojovacího řetězce MongoDB

Při vytváření objektu položky MongoClient, musí základní parametr, což je přesně `ConnectionString` parametr odkazuje na správnou databázi. V případě aplikaci eShopOnContainers připojovací řetězec může odkazovat na místní kontejner Dockeru MongoDB nebo k databázi Azure Cosmos DB "produkční".  Tento připojovací řetězec pochází z proměnné prostředí definované v `docker-compose.override.yml` soubory použité při nasazování s docker-compose nebo Visual Studio, stejně jako v následujícím kódu yml.

```yml
# docker-compose.override.yml
version: '3.4'
services:
  # Other services
  locations.api:
    environment:
      # Other settings
      - ConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosql.data}

```

`ConnectionString` Proměnnou prostředí je vyřešit tímto způsobem: Pokud `ESHOP_AZURE_COSMOSDB` globální proměnná je definována v `.env` soubor s připojovacím řetězcem služby Azure Cosmos DB, použije ho pro přístup k databázi Azure Cosmos DB v cloudu. Pokud není definován, bude trvat mongodb://nosql.data hodnotu a použití kontejneru vývoj mongodb.

Následující kód ukazuje `.env` souborů pomocí služby Azure Cosmos DB připojovací řetězec globální proměnnou prostředí, jak je implementován v aplikaci eShopOnContainers:

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

By měl Odkomentujte řádek ESHOP_AZURE_COSMOSDB a aktualizace je vaším připojovacím řetězcem služby Azure Cosmos DB, který jste získali z portálu Azure jako podrobně [připojení aplikace MongoDB ke službě Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).

Pokud `ESHOP_AZURE_COSMOSDB` globální proměnné je prázdný, což znamená, že je opatřený komentáři out v `.env` soubor kontejneru se použije výchozí připojovací řetězec MongoDB odkazující na místní kontejner MongoDB nasazené v aplikaci eShopOnContainers, který se nazývá `nosql.data`a byla definována v souboru docker-compose, jak je znázorněno v následujícím kódu .yml. 

``` yml
# docker-compose.yml
version: '3.4'
services:
  # ...Other services...
  nosql.data:
    image: mongo
```

#### <a name="additional-resources"></a>Další zdroje

- **Modelování dat dokumentů databází NoSQL** \
  <https://docs.microsoft.com/azure/cosmos-db/modeling-data>

- **Vaughn Vernon. Ideální řízeného doménou návrhu agregace Store?** \
  <https://kalele.io/blog-posts/the-ideal-domain-driven-design-aggregate-store/>

- **Úvod do služby Azure Cosmos DB: Rozhraní API pro MongoDB**  \
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction>

- **Azure Cosmos DB: Vytvoření webové aplikace MongoDB API s využitím .NET a webu Azure portal**  \
  [https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet](https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet )

- **Pro místní vývoj a testování používat emulátor služby Azure Cosmos DB**  \
  <https://docs.microsoft.com/azure/cosmos-db/local-emulator>

- **Připojení aplikace MongoDB ke službě Azure Cosmos DB**  \
  <https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account>

- **Image Dockeru emulátor Cosmos DB (kontejner Windows)**  \
  <https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/>

- **Image Dockeru MongoDB (Linux a Windows Container)**  \
  <https://hub.docker.com/\_/mongo/>

- **Použití MongoChef (Studio 3T) s Azure Cosmos DB: Rozhraní API pro účet MongoDB**  \
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-mongochef>

>[!div class="step-by-step"]
>[Předchozí](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
>[další](microservice-application-layer-web-api-design.md)
