---
title: Implementace brány rozhraní API s Ocelot
description: Zjistěte, jak implementovat brány rozhraní API s Ocelot a použití Ocelot v prostředí založené na kontejnerech.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 07/03/2018
ms.openlocfilehash: dbb3fdb27175a86291d3a942ff168a5aae787c0c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43453072"
---
# <a name="implementing-api-gateways-with-ocelot"></a>Implementace brány rozhraní API s Ocelot

Aplikace mikroslužeb odkaz [aplikaci eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) používá [Ocelot](https://github.com/ThreeMammals/Ocelot) protože Ocelot je jednoduché a jednoduchý bránu rozhraní API, kterou můžete nasadit kdekoli spolu s mikroslužby / kontejnery například v některé z následujících prostředích používají aplikaci eShopOnContainers.

- Hostitele docker, do vašeho místního vývojového počítače, v místním nebo v cloudu.
- Kubernetes cluster, místní nebo v cloudu spravované jako je Azure Kubernetes Service (AKS).
- Cluster Service Fabric, místní nebo v cloudu.
- Service Fabric sítě jako PaaS a bez serveru v Azure.

## <a name="architect-and-design-your-api-gateways"></a>Architektury a návrhu vaší brány rozhraní API

Následující diagram architektury ukazuje, jak se implementují brány rozhraní API s Ocelot v aplikaci eShopOnContainers.

![diagram architektury aplikaci eShopOnContainers zobrazující klientské aplikace, mikroslužby a brány rozhraní API mezi](./media/image28.png)

**Obrázek 8-27.** aplikaci eShopOnContainers architektury s využitím brány rozhraní API

Tento diagram znázorňuje, jak celá aplikace je nasazená do jednoho hostitele Docker nebo vývojové počítače s "Docker pro Windows" nebo "Dockeru pro Mac". Nasazení do jakékoli produktu orchestrator by hodně podobné ale žádný kontejner ve diagram může být horizontálním navýšením kapacity v nástroji orchestrator. 

Kromě toho prostředky infrastruktury, jako jsou databáze, mezipaměť a zprostředkovatele zpráv by měl být se sníženou zátěží z orchestrator a nasadí do vysoce dostupné systémy pro infrastrukturu, jako je Azure SQL Database, Azure Cosmos DB, Azure redis cache, Azure Service Bus nebo jakékoli HA clustering řešení místní.

Jak vám může také Všimněte si, že v diagramu, s několika brány rozhraní API umožňuje několika vývojovým týmům autonomní (v tomto případě marketingové funkcí vs. Nákupní funkce) při vývoji a nasazování mikroslužeb jejich plus své vlastní brány související rozhraní API. 

Pokud jste měli jedné monolitické rozhraní API brány, který by znamenal jediný bod aktualizovat několik vývojové týmy, které by mohly spojit všechny mikroslužby s jednou částí aplikace.

Mnohem víc do toho pustit v návrhu, někdy podrobných Brána rozhraní API může být také omezená na jednu obchodní mikroslužeb v závislosti na zvolené architektury. Brána rozhraní API hranice závisí firmy nebo domény s vám pomůže získat lepší návrh. 

Jemnou rozlišovací schopnost na úrovni rozhraní API brány, může být užitečné zejména pro pokročilejší kompozitních aplikací uživatelského rozhraní, které jsou založené na mikroslužbách, protože koncept podrobných Brána rozhraní API se podobá službě kompozici uživatelského rozhraní. 

Další informace o službách kompozici uživatelského rozhraní, naleznete v tématu [vytvoření složeného uživatelského rozhraní založeného na mikroslužbách](https://docs.microsoft.com/dotnet/standard/microservices-architecture/architect-microservice-container-applications/microservice-based-composite-ui-shape-layout).

Jako hlavní, co vyplývá, pro mnoho aplikací střední a velké velikosti pomocí vlastními silami sestavených Brána rozhraní API produktu je obvykle dobrý nápad, ale ne jako jeden agregátor monolitické nebo jedinečné centrální vlastní bránu rozhraní API není-li tuto bránu rozhraní API umožňuje více nezávislých Konfigurace oblasti pro několik vývojové týmy vytváření autonomní mikroslužeb.

### <a name="sample-microservicescontainers-to-reroute-through-the-api-gateways"></a>Ukázkových mikroslužeb a kontejnerů pro přesměrování prostřednictvím brány rozhraní API

Jako příklad `eShopOnContainers` má přibližně šest interní mikroslužeb – typy, které mají zveřejnit prostřednictvím brány rozhraní API, jak je znázorněno na následujícím obrázku.
 
![](./media/image29.png)

**Obrázek 8-28.** Mikroslužby složek v aplikaci eShopOnContainers řešení v sadě Visual Studio

V návrhu je dostupný ze Brána rozhraní API týkající se služby Identity, směrování, protože se jedná pouze vyskytující se týkají systému ale Ocelot je taky možné zahrnout ho jako součást přesměrování seznamy.

Všechny tyto služby jsou aktuálně implementováno jako služby webového rozhraní API ASP.NET Core, jak vidíte z důvodu kód. Zaměřme se na jednu z mikroslužeb, jako je kód mikroslužeb katalogu.

![](./media/image30.png)

**Obrázek 8 – 29.** Ukázka webového rozhraní API mikroslužby (katalogu mikroslužeb)

Uvidíte, že katalog mikroslužba je obvyklou pro projekty webového rozhraní API ASP.NET Core s několika řadičů a metod, jako jsou v následujícím kódu.

```csharp
[HttpGet]
[Route("items/{id:int}")]
[ProducesResponseType((int)HttpStatusCode.BadRequest)]
[ProducesResponseType((int)HttpStatusCode.NotFound)]
[ProducesResponseType(typeof(CatalogItem),(int)HttpStatusCode.OK)]
public async Task<IActionResult> GetItemById(int id)
{
    if (id <= 0)
    {
        return BadRequest();
    }
    var item = await _catalogContext.CatalogItems.
                                          SingleOrDefaultAsync(ci => ci.Id == id);
    //…

    if (item != null)
    {
        return Ok(item);
    }
    return NotFound();
}
```
Požadavek protokolu HTTP bude uplatněna tento druh kódu jazyka C# přístup k databázi mikroslužeb a žádnou další akci.

Vztahující se k adrese URL mikroslužeb když kontejnery se nasazují do vašeho místního vývojového počítače (místního hostitele Dockeru), má vždy interní port, obvykle port 80, zadaný v jeho souboru dockerfile, stejně jako v následujícím souboru dockerfile jednotlivých mikroslužeb kontejneru:

```
FROM microsoft/aspnetcore:2.0.5 AS base
WORKDIR /app
EXPOSE 80
```

Port 80, které jsou uvedené v kódu je interní v rámci hostitele Docker, takže nemůže být dosažitelný podle klientské aplikace. Klientské aplikace přístupné pouze na externí porty (pokud existuje) publikované při nasazování s `docker-compose`.

Tyto externí porty nemůže být publikována při nasazení do produkčního prostředí. To je přesně proč chcete použít bránu rozhraní API, aby se zabránilo přímou komunikaci mezi klientské aplikace a mikroslužeb.

Ale při vývoji, chcete získat přímo přístup k mikroslužeb a kontejnerů a spusťte ho pomocí Swaggeru. To je důvod, proč v aplikaci eShopOnContainers, externích portů jsou stále zadat i v případě, že se nebude používat bránu rozhraní API nebo klientských aplikací.

Tady je příklad `docker-compose.override.yml` soubor pro mikroslužby katalogu:

```
catalog.api:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - ASPNETCORE_URLS=http://0.0.0.0:80
    - ConnectionString=YOUR_VALUE
    - ... Other Environment Variables
  ports:
    - "5101:80"   # Important: In a production environment you should remove the external port (5101) kept here for microservice debugging purposes. 
                  # The API Gateway redirects and access through the internal port (80).
```

Uvidíte jak v konfiguraci docker-compose.override.yml interní port kontejneru katalogu je port 80, ale 5101 je port pro externí přístup. By ale neměly používat tento port aplikace při použití brány rozhraní API pouze pro ladění, spouštění a testování pouze mikroslužeb katalogu.

Za normálních okolností bude nasazení pomocí docker-compose do provozního prostředí vzhledem k tomu, že provozním prostředí nasazení mikroslužeb je orchestrátor Kubernetes nebo Service Fabric. Při nasazování do těchto prostředí použijete jiný konfigurační soubory, pokud nebude publikovat přímo všechny externí port pro mikroslužby ale budete vždy použít reverzní proxy server ze Brána rozhraní API.

Spustit mikroslužeb katalogu v místního hostitele Docker buď spuštěním řešení úplnou aplikaci eShopOnContainers ze sady Visual Studio (spouští se všechny služby v dockeru-compose soubory) nebo právě spouští mikroslužeb katalogu s následujícím docker-compose příkaz do příkazového řádku nebo Powershellu, které jsou umístěné ve složce kde `docker-compose.yml` a jsou umístěny docker-compose.override.yml.

```
docker-compose run --service-ports catalog.api
```

Tento příkaz spustí jenom v kontejneru služby catalog.api plus závislosti, které jsou určené v docker-compose.yml. V takovém kontejner SQL serveru a RabbitMQ kontejneru.

Potom můžete přímo přístup ke katalogu mikroslužeb a zobrazit její metody prostřednictvím uživatelského rozhraní Swagger, že "externí" port, v tomto případě přístup přímo prostřednictvím k `http://localhost:5101`. 

![](./media/image31.png)

**Obrázek 8 – 30.** Testování katalogu mikroslužeb s jeho uživatelské rozhraní Swagger

V tomto okamžiku můžete nastavit zarážku v kódu jazyka C# v sadě Visual Studio, testování mikroslužby pomocí metod zveřejněných v uživatelské rozhraní Swagger a nakonec Vyčistit vše, co se `docker-compose down` příkazu.

Tato komunikace přímý přístup do mikroslužeb, v tomto případě přes externí port 5101 ale přesně chcete, aby ve vaší aplikaci. A, který se můžete vyhnout tak, že nastavíte další úroveň dereference brány rozhraní API (v tomto případě Ocelot). Tímto způsobem, klientská aplikace nebude mít přístup k přímo mikroslužbách.

## <a name="implementing-your-api-gateways-with-ocelot"></a>Implementace vaší brány rozhraní API s Ocelot

Ocelot je v podstatě sadu middlewares, které můžete použít v určitém pořadí.

Ocelot je navržen pro práci s ASP.NET Core pouze. Je cílena netstandard2.0, takže ho můžete použít, všude, kde se podporuje .NET Standard 2.0, včetně modulu runtime .NET Core 2.0 a modul runtime rozhraní .NET Framework 4.6.1 a novějšími verzemi.

Nainstalujte Ocelot a jeho závislosti ve vašem projektu ASP.NET Core s [balíček NuGet pro Ocelot](https://www.nuget.org/packages/Ocelot/), ze sady Visual Studio.

```
Install-Package Ocelot
```

V aplikaci eShopOnContainers jeho implementace Brána rozhraní API je jednoduchý projekt hostitele ASP.NET Core a jeho Ocelot middlewares zpracovat všechny funkce brány rozhraní API, jak je znázorněno na následujícím obrázku:

![](./media/image32.png)

**Obrázek 8-31.** OcelotApiGw základního projektu v aplikaci eShopOnContainers

Tento projekt hostitele ASP.NET Core provádí dva jednoduché soubory `Program.cs` a `Startup.cs`.

Soubor Program.cs stejně musí vytvořit a nakonfigurovat typické BuildWebHost ASP.NET Core. 

```csharp
namespace OcelotApiGw
{
    public class Program
    {
        public static void Main(string[] args)
        {
            BuildWebHost(args).Run();
        }

        public static IWebHost BuildWebHost(string[] args)
        {
            var builder = WebHost.CreateDefaultBuilder(args);

            builder.ConfigureServices(s => s.AddSingleton(builder))                
                                                          .ConfigureAppConfiguration(
                              ic => ic.AddJsonFile(Path.Combine("configuration",
                                                                "configuration.json")))
                                                                .UseStartup<Startup>();
            var host = builder.Build();
            return host;
        }
    }
}
```

Je důležité zde pro Ocelot `configuration.json` soubor, který je nutné zadat do Tvůrce prostřednictvím `AddJsonFile()` metoda. Že `configuration.json` zadávat všechny rozhraní API brány ReRoutes, což znamená externí koncové body s konkrétní porty a korelační koncovým bodům s interním, obvykle pomocí jiné porty.

```
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

Existují dvě části ke konfiguraci. Pole zpětného odeslání a GlobalConfiguration. Znovu směruje jsou objekty, které informují Ocelot jak zacházet s nadřazeného požadavku. Globální konfigurace umožňuje přepsání znovu směrovat konkrétní nastavení. To je užitečné, pokud nechcete spravovat velké množství znovu směrovat konkrétní nastavení.

Tady je zjednodušený příklad [přesměrovat konfigurace](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) souborů z jednoho z brány rozhraní API v aplikaci eShopOnContainers.

```
{
  "ReRoutes": [
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "catalog.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/c/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ]
    },
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
    }
    
  ],
    "GlobalConfiguration": {
      "RequestIdKey": "OcRequestId",
      "AdministrationPath": "/administration"
    }
  }
```

Hlavní funkce brány rozhraní API Ocelot je využívat příchozích požadavků HTTP a předat je do podřízené služby, aktuálně jako jiný HTTP žádosti. Společnosti ocelot popisuje směrování jeden požadavek na jiný jako znovu směrovat.

Například zaměřme se na jednu z znovu směruje v configuration.json uvedeného konfigurace pro mikroslužby nákupní košík.

```
{
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
}
```

DownstreamPathTemplate, schéma a DownstreamHostAndPorts je možné tento požadavek se předají do adresy URL interní mikroslužeb. 

Port, který je interní port používaný službou. Při používání kontejnerů, port zadaný v příslušným souborem dockerfile.

`Host` Je název služby, který závisí na rozlišení názvu služby používáte. Při použití docker-compose, služby názvy jsou poskytované hostitele Dockeru, který používá názvy služeb v dockeru-compose soubory. Pokud používáte orchestrátoru, jako je Kubernetes nebo Service Fabric, tento název se mají překládat pomocí DNS nebo překlad poskytované jednotlivých orchestrátorů liší.

DownstreamHostAndPorts je pole, která obsahuje hostitele a port příjem dat, které chcete přesměrovat požadavky do služeb. Obvykle bude obsahovat pouze jednu položku, ale v některých případech můžete chtít načíst z žádostí vyvažovat mezi službami pro příjem dat a Ocelot umožňuje přidat více než jednu položku a pak vyberte nástroj pro vyrovnávání zatížení. Ale pokud používáte Azure a všechny nástroje orchestrator je pravděpodobně lepší představu vyrovnávat zatížení pomocí infrastruktury cloudu a nástroje orchestrator.

UpstreamPathTemplate je adresa URL, kterou Ocelot použije k identifikaci DownstreamPathTemplate, které chcete použít pro daný požadavek od klienta. Nakonec UpstreamHttpMethod se používá, takže můžete Ocelot rozlišovat mezi různými požadavky (GET, POST, PUT) na stejnou adresu URL.

V tomto okamžiku můžete mít jednu Ocelot rozhraní API brány (hostitele ASP.NET Core) pomocí některého nebo [více sloučit soubory configuration.json](http://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) nebo také můžete uložit [konfigurace v úložišti konzul KV](http://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul). 

Ale zavedení v částech architektury a návrhu, pokud Opravdu chcete mít autonomní mikroslužeb, může být lepší rozdělit jeden monolitické Brána rozhraní API do více bran rozhraní API a/nebo BFF (back-endu pro front-endu). Pro tento účel Podívejme se na tom, jak implementovat tento přístup se kontejnery Dockeru.

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a>Pomocí jedné image kontejneru Dockeru pro spuštění více jinou bránu rozhraní API / typy BFF kontejneru 

Návrh v aplikaci eShopOnContainers implementuje jednu image kontejneru Dockeru s bránou Ocelot rozhraní API, ale pak při nasazování do služby Docker, vytváří různé služby/kontejnery pro každý typ rozhraní API – brána/BFF zadáním různých configuration.json soubor pro každý kontejner.

![](./media/image33.png)

**Obrázek 8 – 32.** Opětovné použití jedné image Dockeru Ocelot napříč více typy brány rozhraní API

V aplikaci eShopOnContainers, "Obecný Ocelot rozhraní API brány Image Dockeru" Vytvoření projektu s názvem 'OcelotApiGw' a obrázek název "eshop/ocelotapigw", který je zadaný v souboru docker-compose.yml. Potom při nasazování do služby Docker, bude čtyři kontejnery Brána rozhraní API, které jsou vytvořené z této stejnou image Dockeru, jak je znázorněno v následujícím výpisu ze souboru docker-compose.yml.

```
PARTIAL DOCKER-COMPOSE.YML

  mobileshoppingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile
 
  mobilemarketingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile
 
  webshoppingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  webmarketingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile
```

Kromě toho jak můžete vidět v souboru docker-compose.override.yml, jediným rozdílem mezi těchto kontejnerů Brána rozhraní API se Ocelot konfigurační soubor, který se liší pro každý kontejner služby a je určena v době běhu pomocí Dockeru svazku, jak je znázorněno v následujícím souboru docker-compose.override.yml.

```
mobileshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api              
  ports:
    - "5200:80"   
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Shopping/apigw:/app/configuration
 
mobilemarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api              
  ports:
    - "5201:80"   
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Marketing/apigw:/app/configuration

webshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api              
  ports:
    - "5202:80"   
  volumes:
    - ./src/ApiGateways/Web.Bff.Shopping/apigw:/app/configuration

webmarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api              
  ports:
    - "5203:80"   
  volumes:
    - ./src/ApiGateways/Web.Bff.Marketing/apigw:/app/configuration
```

Z důvodu této předchozí kód a jak je znázorněno v Průzkumníku Visual Studio pod jediným souborem zapotřebí k definování každé konkrétní obchodní/BFF Brána rozhraní API je jenom configuration.json soubor, protože čtyři brány rozhraní API jsou založeny na stejnou image Dockeru.

![](./media/image34.png)

**Obrázek 8-33.** Pouze soubor zapotřebí k definování každou bránu rozhraní API / BFF s Ocelot je konfigurační soubor 

Rozdělením brány rozhraní API do více bran rozhraní API můžete spravovat různé vývojové týmy, zaměřuje se na různé podmnožiny mikroslužeb své vlastní brány rozhraní API pomocí nezávislé Ocelot konfigurační soubory. Kromě toho ve stejnou dobu mohli znovu použít stejná image Dockeru Ocelot. 

Nyní Pokud spouštíte aplikaci eShopOnContainers pomocí brány rozhraní API (zahrnuté ve výchozím nastavení v sadě Visual Studio při otevírání řešení aplikaci eShopOnContainers ServicesAndWebApps.sln nebo pokud běží "docker-compose up"), budou provedeny následující ukázka trasy. 

Například při návštěvě adresa URL upstreamu http://localhost:5202/api/v1/c/catalog/items/2/ obsluhuje webshoppingapigw Brána rozhraní API, můžete získat výsledek z interní adresy URL pro příjem dat http://catalog.api/api/v1/2 v rámci hostitele Docker, stejně jako v následující prohlížeče.

![](./media/image35.png)

**Obrázek 8-34.** Přístup prostřednictvím adresy URL poskytnuté brány rozhraní API mikroslužby 

Z důvodu testování nebo ladění z důvodů, pokud byste chtěli přímý přístup ke kontejneru Dockeru katalogu (pouze ve vývojovém prostředí) bez průchodu přes bránu rozhraní API, protože je "catalog.api" překlad názvů DNS, která je interní pro hostitele Docker (služba zjišťování zpracována docker-compose názvy služeb), je jediný způsob, jak přímý přístup k kontejneru prostřednictvím externího portu publikované v docker-compose.override.yml, která se poskytuje jenom pro vývoj pro testy, například http://localhost:5101/api/v1/Catalog/items/1 v následujícím prohlížeč.

![](./media/image36.png)

**Obrázek 8 – 35.** Přímý přístup k mikroslužby pro účely testování 

Ale aplikace je nakonfigurovaná tak přistupuje všechny mikroslužby prostřednictvím brány rozhraní API, ale není přímo portovaný "zástupce". 

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a>Model agregace pomocí brány v aplikaci eShopOnContainers

Zavedeném dříve, je flexibilní způsob, jak implementovat agregace požadavků s vlastní služby pomocí kódu. Agregace požadavků s funkcí agregace požadavků může také implementovat v Ocelot, ale nemusí být tak flexibilní podle potřeby. Vybraný způsob implementace agregace v aplikaci eShopOnContainers tedy s explicitní služby webového rozhraní API ASP.NET Core pro každý agregátoru. 

Podle tohoto přístupu složení diagram brány rozhraní API je ve skutečnosti o něco více rozšířené, když se vezme v úvahu služby agregátoru, které nejsou uvedeny v dříve uvedeném diagramu zjednodušení globální architektury. 

V následujícím diagramu můžete také zobrazit, fungování služby agregátoru s jejich související brány rozhraní API.

![](./media/image37.png)

**Obrázek 8 – 36.** aplikaci eShopOnContainers architektury s využitím služby agregátoru

Na následujícím obrázku je přiblížit dále, takže si všimnete, jak pro obchodní oblast "Nákupní" klientské aplikace lze zlepšit díky snížení nadměrné komunikace s využitím mikroslužeb, při použití těchto služeb agregátoru pod sféry brány rozhraní API. 

 ![](./media/image38.png)

**Obrázek 8-37.** Přiblížit vizi služby agregátoru

Můžete Všimněte si, jak při diagram znázorňuje možné požadavky přicházející z brány rozhraní API dostane poměrně složité. I když se zobrazí, jak šipky modře by se dá zjednodušit, z pohledu klientských aplikací, při použití vzoru agregátoru díky snížení nadměrné komunikace a latence při komunikaci, takže v konečném důsledku výrazně zlepšuje uživatel prostředí pro vzdálené aplikace ( mobilní zařízení a aplikace SPA), zvlášť. 

V případě "Marketing" obchodní oblast a mikroslužeb je velmi jednoduchý případ použití tak nemusíme používat agregátorů, ale je také možné, je to možné, v případě potřeby.

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a>Ověřování a autorizace ve Ocelot brány rozhraní API

V rozhraní API brány Ocelot můžete pohodlně ověřovací služby, jako je například služba webového rozhraní API ASP.NET Core pomocí [IdentityServer](http://identityserver.io/) poskytuje ověřovací token, out nebo uvnitř brány rozhraní API.

Protože je v aplikaci eShopOnContainers více bran rozhraní API pomocí hranice založené na BFF a v oblastech obchodu, službu Identity/Auth zůstane mimo brány rozhraní API, jako zvýrazněné žlutou barvou v následujícím diagramu.

 ![](./media/image39.png)

**Obrázek 8-38.** Pozice služba identit v aplikaci eShopOnContainers

Nicméně Ocelot podporuje také se vám sedět identita a ověřování mikroslužby v rámci hranice Brána rozhraní API, stejně jako v tomto diagramu.

 ![](./media/image40.png)

**Obrázek 8-39.** Ověřování v Ocelot Brána rozhraní API

Protože aplikace aplikaci eShopOnContainers rozdělil brány rozhraní API do více BFF (back-endu pro front-endu) a by obchodní oblasti brány rozhraní API, Další možností je vytvořit další bránu rozhraní API pro vyskytující aspekty. Volba bude veletrh v mikroslužbě složitější na základě architektury s různými mikroslužbami vyskytující aspekty. Vzhledem k tomu, že existuje pouze jeden problém vyskytující v aplikaci eShopOnContainers, rozhodla se právě zpracování služby zabezpečení ze sféry Brána rozhraní API pro jednoduchost společnosti saké.

V každém případě aplikace je zabezpečena na úrovni rozhraní API brány, modul ověřování brány rozhraní API Ocelot návštěvě zpočátku při pokusu o použití jakékoli zabezpečené mikroslužeb. Znovu, který přesměruje požadavek HTTP na web nebo ověření Identity mikroslužeb k získání tokenu přístupu proto tedy že můžete navštívit chráněným službám s access_token.

Způsob zabezpečení pomocí ověřování jakékoli služby na úrovni rozhraní API brány je tak, že nastavíte AuthenticationProviderKey v jeho související nastavení na configuration.json.

```
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
    }
```

Při spuštění Ocelot ho se podívá na AuthenticationOptions.AuthenticationProviderKey přesměruje a ověřte, zda je zaregistrován zprostředkovatele ověřování s daným klíčem. Pokud není k dispozici, Ocelot nespustí. Pokud existuje, pak přesměrovat použije tohoto zprostředkovatele při provádění.

Protože má nakonfigurovanou Ocelot WebHost `authenticationProviderKey = "IdentityApiKey"`, vždy, když má libovolné požadavky bez jakékoli ověřovací token služby, které se vyžadují ověřování. 

```csharp
namespace OcelotApiGw
{
    public class Startup
    {
        private readonly IConfiguration _cfg;

        public Startup(IConfiguration configuration) => _cfg = configuration;

        public void ConfigureServices(IServiceCollection services)
        {
            var identityUrl = _cfg.GetValue<string>("IdentityUrl");
            var authenticationProviderKey = "IdentityApiKey";
                         //…
            services.AddAuthentication()
                .AddJwtBearer(authenticationProviderKey, x =>
                {
                    x.Authority = identityUrl;
                    x.RequireHttpsMetadata = false;
                    x.TokenValidationParameters = new Microsoft.IdentityModel.Tokens.TokenValidationParameters()
                    {
                        ValidAudiences = new[] { "orders", "basket", "locations", "marketing", "mobileshoppingagg", "webshoppingagg" }
                    };                   
                });
            //...
```

Pak také musíte nastavit autorizace pomocí atributu [Authorize] na prostředek, ke kterému lze přistupovat jako jsou mikroslužby, jako například následující mikroslužeb řadič nákupního košíku.

```csharp
namespace Microsoft.eShopOnContainers.Services.Basket.API.Controllers
{
    [Route("api/v1/[controller]")]
    [Authorize]
    public class BasketController : Controller
    {   
      //...
    }
}
```

ValidAudiences, jako je například "nákupní košík" se korelují s cílovou skupinou definované v jednotlivých mikroslužeb s `AddJwtBearer()` na ConfigureServices() třídu pro spuštění, jako je například následující kód.

```csharp
// prevent from mapping "sub" claim to nameidentifier.
JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear();

var identityUrl = Configuration.GetValue<string>("IdentityUrl"); 
                
services.AddAuthentication(options =>
{
    options.DefaultAuthenticateScheme = JwtBearerDefaults.AuthenticationScheme;
    options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;

}).AddJwtBearer(options =>
{
    options.Authority = identityUrl;
    options.RequireHttpsMetadata = false;
    options.Audience = "basket";
});
```

Jako další krok, pokud se pokusíte o přístup k jakékoli zabezpečené mikroslužeb, jako jsou mikroslužby nákupní košík s adresou URL znovu směrovat založené na bránu rozhraní API, jako je http://localhost:5202/api/v1/b/basket/1 pak dostanete 401 Neautorizováno. Pokud nezadáte token platný. Na druhé straně Pokud ověření adresy URL znovu směrovat Ocelot vyvolá jakékoli podřízené schéma je k ní (adresu URL interní mikroslužeb) přidružen.

**Autorizace na úrovni společnosti Ocelot přesměruje.**  Ocelot podporuje ověřování na základě deklarací identity vyhodnocen po ověření. Přidáním následujícího kódu do konfigurace znovu směrovat nastavíte autorizaci na úrovni směrování. 

```
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

V tomto příkladu se nazývá autorizace middleware, Ocelot najdete Pokud má uživatel "UserType" typ deklarace identity v tokenu, a pokud tuto žádost má hodnotu "zaměstnance". Pokud tomu tak není, uživatel nebude oprávnění a odpověď bude 403 Zakázáno. 

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a>Pomocí příchozího přenosu dat Kubernetes plus Ocelot rozhraní API brány

Při použití Kubernetes (jako v clusteru Azure Kubernetes Service), obvykle sjednocení všechny požadavky HTTP přes [Kuberentes příchozí přenos dat vrstvy](https://kubernetes.io/docs/concepts/services-networking/ingress/) na základě *Nginx*. 

V Kuberentes Pokud nepoužíváte žádné příchozí přístup, pak vaše služby a podů mají pouze směrovatelné IP adresy ve síť s clustery. 

Ale pokud používáte metodiky příchozího přenosu dat, budete mít střední vrstvy mezi Internetem a služby (včetně vaší brány rozhraní API), který funguje jako reverzní proxy server.

Příchozí přenos dat jako definice, je kolekce pravidel, která povolí příchozí připojení k dosažení Clusterové služby. Příchozí přenos dat je nakonfigurovaná k poskytují externě dostupný adresy URL služby, načíst vyrovnávání provozu, ukončování protokolu SSL a dalších. Uživatelé požadují příchozího přenosu dat tím, že publikuje příchozího přenosu dat prostředků do serveru rozhraní API.

V aplikaci eShopOnContainers, při vývoji místně a pomocí právě svého vývojového počítače jako hostitele Docker nepoužíváte žádné příchozí přenos dat, ale více bran rozhraní API. 

Při cílení na "produkční" prostředí založené na Kuberentes, ale aplikaci eShopOnCOntainers používá příchozí přenos dat před brány rozhraní API. Tímto způsobem klienti stále volat stejnou základní adresu URL, ale jsou požadavky směrovány do více bran rozhraní API nebo BFF. 

Všimněte si, že brány rozhraní API jsou front endů nebo fasády zpřístupnění pouze služby, ale ne webové aplikace, které jsou obvykle mimo jejich rozsah. Kromě toho brány rozhraní API může skrýt některé interní mikroslužeb. 

Příchozí přenos, ale je stejně přesměrovávání požadavků HTTP, ale pokus o skrýt všechny mikroslužby nebo do webové aplikace.

S vrstvou Nginx příchozího přenosu dat ve Kuberentes před webových aplikací a navíc několik bran rozhraní API Ocelot / BFF je ideální architekturu, jak je znázorněno v následujícím diagramu.

 ![](./media/image41.png)

**Obrázek 8-40.** Úroveň příchozího přenosu dat v aplikaci eShopOnContainers při nasazení do Kubernetes

Když nasadíte aplikaci eShopOnContainers do Kuberentes, zpřístupní několika služeb nebo na koncové body prostřednictvím _příchozího přenosu dat_, v podstatě postfixes na adresy URL v následujícím seznamu:

-   `/` pro klienta webové aplikace SPA
-   `/webmvc` pro klienta webové aplikace MVC
-   `/webstatus` Zobrazení stavu/healthchecks klienta webové aplikace
-   `/webshoppingapigw` pro web BFF a nákupního obchodních procesů
-   `/webmarketingapigw` pro web BFF a marketingové obchodních procesů
-   `/mobileshoppingapigw` pro mobilní BFF a nákupního obchodních procesů
-   `/mobilemarketingapigw` mobilní BFF a marketingové obchodních procesů

Při nasazování do Kubernetes, každá brána rozhraní API Ocelot používá různé "configuration.json" soubor pro každý _pod_ spuštění brány rozhraní API. Jsou k dispozici tyto soubory "configuration.json" tak, že připojí (původně se skriptem deploy.ps1) svazek vytvořený podle Kuberentes _mapování pro config_ s názvem "ocelot". Každý kontejner připojí souvisejících konfiguračních souborů ve složce kontejneru s názvem `/app/configuration`.

V souborech zdrojového kódu aplikaci eShopOnContainers, původní soubory "configuration.json" lze nalézt v rámci `k8s/ocelot/` složky. Existuje jeden soubor pro každý BFF APIGateway.


## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a>Další společné funkce v bránu rozhraní API Ocelot

Existují další důležité funkce pro výzkum a použít, při použití brány rozhraní API Ocelot popsané v následujících odkazů.

-   **Zjišťování služby na straně klienta Ocelot integrování konzul nebo Eureka** 
    [*http://ocelot.readthedocs.io/en/latest/features/servicediscovery.html*](http://ocelot.readthedocs.io/en/latest/features/servicediscovery.html)

-   **Ukládání do mezipaměti na úrovni rozhraní API brány** 
    [*http://ocelot.readthedocs.io/en/latest/features/caching.html*](http://ocelot.readthedocs.io/en/latest/features/caching.html)

-   **Protokolování na úrovni rozhraní API brány** 
    [*http://ocelot.readthedocs.io/en/latest/features/logging.html*](http://ocelot.readthedocs.io/en/latest/features/logging.html)

-   **Kvalita služby (opakovaných pokusů a jističe) na úrovni rozhraní API brány** 
    [*http://ocelot.readthedocs.io/en/latest/features/qualityofservice.html*](http://ocelot.readthedocs.io/en/latest/features/qualityofservice.html)

-   **Omezení četnosti** 
    [*http://ocelot.readthedocs.io/en/latest/features/ratelimiting.html*](http://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )




>[!div class="step-by-step"]
[Předchozí](background-tasks-with-ihostedservice.md) [Další](../microservice-ddd-cqrs-patterns/index.md)
