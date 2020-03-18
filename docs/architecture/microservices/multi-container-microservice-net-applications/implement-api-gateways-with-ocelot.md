---
title: Implementace bran rozhraní API s Ocelotem
description: Zjistěte, jak implementovat brány rozhraní API s Ocelotem a jak používat Ocelot v prostředí založeném na kontejnerech.
ms.date: 03/02/2020
ms.openlocfilehash: 28b9ca22d232baf3545d71b876cecf72fea05c92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846943"
---
# <a name="implement-api-gateways-with-ocelot"></a>Implementace bran rozhraní API s Ocelotem

> [!IMPORTANT]
> Referenční aplikace mikroslužeb [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) v současné době používá funkce poskytované [vyslancem](https://www.envoyproxy.io/) k implementaci brány rozhraní API namísto dříve odkazovaného [Ocelotu](https://github.com/ThreeMammals/Ocelot).
> Tuto volbu návrhu jsme provedli z důvodu integrované podpory protokolu WebSocket, kterou vyžaduje nová mezioborová komunikace gRPC implementovaná v eShopOnContainers.
> Tuto část jsme však v průvodci zachovái, takže můžete Ocelot považovat za jednoduchou, schopnou a lehkou bránu rozhraní API vhodnou pro scénáře produkčního prostředí.

## <a name="architect-and-design-your-api-gateways"></a>Navrhněte a navrhněte brány rozhraní API

Následující diagram architektury ukazuje, jak byly brány rozhraní API implementovány pomocí Ocelotu v eShopOnContainers.

![Diagram znázorňující architekturu eShopOnContainers.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture.png)

**Obrázek 6-28**. Architektura eShopOnContainers s bránami API

Tento diagram ukazuje, jak se celá aplikace nasadí do jednoho hostitele Dockeru nebo vývojového počítače s "Docker pro Windows" nebo "Docker pro Mac". Nasazení do libovolného orchestrator by však podobné, ale všechny kontejnery v diagramu může být škálovat v orchestrator.

Kromě toho by měly být prostředky infrastruktury, jako jsou databáze, mezipaměti a zprostředkovatele zpráv, převedeny z orchestrátoru a nasazeny do vysoce dostupných systémů pro infrastrukturu, jako je Azure SQL Database, Azure Cosmos DB, Azure Redis, Azure Service Bus, nebo jakékoli řešení clustering HA v místním prostředí.

Jak si můžete také všimnout v diagramu, s několika brány rozhraní API umožňuje více vývojových týmů být autonomní (v tomto případě funkce marketingu vs. nákupní funkce) při vývoji a nasazování svých mikroslužeb a jejich vlastní související brány rozhraní API.

Pokud jste měli jednu monolitickou bránu rozhraní API, což by znamenalo jeden bod, který by měl být aktualizován několika vývojovými týmy, které by mohly spojit všechny mikroslužby s jednou částí aplikace.

Chystáte mnohem dále v návrhu, někdy jemně odstupňované brány rozhraní API může být také omezena na jednu obchodní mikroslužeb v závislosti na zvolené architektuře. S hranice brány rozhraní API diktované firmou nebo doménou vám pomůže získat lepší návrh.

Například jemné rozlišovací schopnost ve vrstvě brány rozhraní API může být užitečné zejména pro pokročilejší aplikace složené ui, které jsou založeny na mikroslužeb, protože koncept jemně odstupňované brány rozhraní API je podobný službě složení rozhraní.

Ponoříme se do dalšípodrobnosti v předchozí části [Vytváření složené houfně založené na mikroslužeb](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md).

Jako klíčový stánek s jídlem, pro mnoho středně velkých a velkých aplikací, pomocí vlastní-postavený API Gateway produkt je obvykle dobrý přístup, ale ne jako jeden monolitický agregátor nebo unikátní centrální vlastní brána rozhraní API, pokud, že brána rozhraní API umožňuje více nezávislých konfigurační oblasti pro několik vývojových týmů, které vytvářejí autonomní mikroslužby.

### <a name="sample-microservicescontainers-to-reroute-through-the-api-gateways"></a>Ukázka mikroslužeb/kontejnerů pro přesměrování přes brány rozhraní API

Jako příklad eShopOnContainers má kolem šesti typů interních mikroslužeb, které mají být publikovány prostřednictvím brány rozhraní API, jak je znázorněno na následujícím obrázku.

![Snímek obrazovky složky Služby zobrazující její podsložky](./media/implement-api-gateways-with-ocelot/eshoponcontainers-microservice-folders.png)

**Obrázek 6-29**. Složky mikroslužeb v řešení eShopOnContainers v sadě Visual Studio

O službě Identity je v návrhu ponechána mimo směrování brány rozhraní API, protože je to jediný průřezový problém v systému, ačkoli s Ocelotem je také možné jej zahrnout jako součást seznamů přesměrování.

Všechny tyto služby jsou aktuálně implementovány jako ASP.NET služby základního webového rozhraní API, jak můžete zjistit z kódu. Zaměřme se na jednu z mikroslužeb, jako je kód mikroslužeb katalogu.

![Snímek obrazovky Průzkumníka řešení zobrazující obsah projektu Catalog.API](./media/implement-api-gateways-with-ocelot/catalog-api-microservice-folders.png)

**Obrázek 6-30**. Ukázková mikroslužba webového rozhraní API (katalogová mikroslužba)

Uvidíte, že mikroslužba katalogu je typický ASP.NET core web api projektu s několika řadiče a metody, jako je v následujícím kódu.

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

Požadavek HTTP skončí spuštěním tohoto druhu kódu Jazyka C# s přístupem k databázi mikroslužeb a jakékoli další požadované akce.

Pokud jde o adresu URL mikroslužeb, když jsou kontejnery nasazeny ve vašem místním vývojovém počítači (místní hostitel Dockeru), kontejner každé mikroslužby má vždy interní port (obvykle port 80) zadaný v jeho dockerfile, jako v následujícím dockerfile:

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
```

Port 80 zobrazený v kódu je interní v rámci hostitele Dockeru, takže ho klientské aplikace nemohou oslovit.

Klientské aplikace mají přístup pouze k externím portům `docker-compose`(pokud existuje) publikovaným při nasazování pomocí aplikace .

Tyto externí porty by neměly být publikovány při nasazování do produkčního prostředí. To je přesně důvod, proč chcete použít bránu rozhraní API, abyste se vyhnuli přímé komunikaci mezi klientskými aplikacemi a mikroslužbami.

Však při vývoji, chcete získat přístup k mikroslužeb/kontejnerpřímo a spusťte jej přes Swagger. To je důvod, proč v eShopOnContainers externí porty jsou stále určeny i v případě, že nebudou použity brány rozhraní API nebo klientské aplikace.

Tady je příklad souboru `docker-compose.override.yml` pro mikroslužbu katalogu:

```yml
catalog-api:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - ASPNETCORE_URLS=http://0.0.0.0:80
    - ConnectionString=YOUR_VALUE
    - ... Other Environment Variables
  ports:
    - "5101:80"   # Important: In a production environment you should remove the external port (5101) kept here for microservice debugging purposes.
                  # The API Gateway redirects and access through the internal port (80).
```

Můžete vidět, jak v konfiguraci docker-compose.override.yml vnitřní port pro kontejner katalogu je port 80, ale port pro externí přístup je 5101. Ale tento port by neměl být používán aplikací při použití brány rozhraní API, pouze k ladění, spuštění a testování pouze mikroslužeb katalogu.

Normálně nebudete nasazovat s docker-compose do produkčního prostředí, protože správné produkční nasazení prostředí pro mikroslužby je orchestrátor jako Kubernetes nebo Service Fabric. Při nasazování do těchto prostředí používáte různé konfigurační soubory, kde nebudete publikovat přímo žádný externí port pro mikroslužby, ale budete vždy používat reverzní proxy z brány rozhraní API.

Spusťte mikroslužbu katalogu v místním hostiteli Dockeru. Buď spusťte úplné řešení eShopOnContainers z Visual Studia (spustí všechny služby v souborech docker-compose) nebo spusťte mikroslužbu katalogu `docker-compose.yml` s `docker-compose.override.yml` následujícím příkazem docker-compose v CMD nebo PowerShellu umístěném ve složce, kde jsou umístěny a.

```console
docker-compose run --service-ports catalog-api
```

Tento příkaz spustí pouze kontejner služby rozhraní katalogu api plus závislosti, které jsou zadány v docker-compose.yml. V tomto případě kontejner sql serveru a Kontejner RabbitMQ.

Potom můžete přímo přistupovat k mikroslužbě katalogu a vidět jeho metody prostřednictvím uživatelského rozhraní Swagger, které přistupuje přímo prostřednictvím tohoto "externího" portu, v tomto případě `http://localhost:5101/swagger`:

![Snímek obrazovky uživatelského rozhraní Swagger zobrazující rozhraní API REST rozhraní Catalog.API ROZHRANÍ API](./media/implement-api-gateways-with-ocelot/test-catalog-microservice.png)

**Obrázek 6-31**. Testování mikroslužby katalogu s jeho uživatelskérozhraní Swagger

V tomto okamžiku můžete nastavit zarážku v kódu Jazyka C# v sadě Visual Studio, otestovat mikroslužbu s `docker-compose down` metodami vystavenými v unovém jazyce Swagger a nakonec vyčistit vše pomocí příkazu.

Však komunikace přímého přístupu k mikroslužbě, v tomto případě prostřednictvím externího portu 5101, je přesně to, co chcete vyhnout ve vaší aplikaci. A můžete se tomu vyhnout nastavením další úrovně dereference brány rozhraní API (Ocelot, v tomto případě). Tímto způsobem klientská aplikace nebude mít přímý přístup k mikroslužeb.

## <a name="implementing-your-api-gateways-with-ocelot"></a>Implementace brány rozhraní API s Ocelotem

Ocelot je v podstatě sada middlewares, které můžete použít v určitém pořadí.

Ocelot je určen pro práci pouze s ASP.NET Core. Nejnovější verze cílů `.NETCoreApp 3.1` balíčku a proto není vhodná pro aplikace rozhraní .NET Framework.

Nainstalujete Ocelot a jeho závislosti v projektu ASP.NET Core s [balíčkem NuGet společnosti Ocelot](https://www.nuget.org/packages/Ocelot/)z aplikace Visual Studio.

```powershell
Install-Package Ocelot
```

V eShopOnContainers je implementace brány API jednoduchým ASP.NET projektu Core WebHost a middleware Ocelot zpracovává všechny funkce brány ROZHRANÍ API, jak je znázorněno na následujícím obrázku:

![Snímek obrazovky Průzkumníka řešení zobrazující projekt brány rozhraní API Ocelot](./media/implement-api-gateways-with-ocelot/ocelotapigw-base-project.png)

**Obrázek 6-32**. Základní projekt OcelotApiGw v eShopOnContainers

Tento ASP.NET core webhost projekt je v `Program.cs` podstatě postaven se dvěma jednoduchými soubory: a `Startup.cs`.

Program.cs stačí vytvořit a nakonfigurovat typické ASP.NET Core BuildWebHost.

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

Důležitým bodem zde pro Ocelot je `configuration.json` soubor, který musíte `AddJsonFile()` poskytnout stavitelprostřednictvím metody. To `configuration.json` je místo, kde zadáte všechny brány rozhraní API ReRoutes, což znamená externí koncové body s konkrétní porty a korelované vnitřní koncové body, obvykle pomocí různých portů.

```json
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

Konfigurace má dvě části. Pole ReRoutes a GlobalConfiguration. ReRoutes jsou objekty, které říkají Ocelot, jak zacházet s požadavkem upstream. Globální konfigurace umožňuje přepsání nastavení specifických pro reroute. Je to užitečné, pokud nechcete spravovat velké množství nastavení specifických pro ReRoute.

Tady je zjednodušený příklad [konfiguračního souboru ReRoute](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) z jedné z bran rozhraní API z eShopOnContainers.

```json
{
  "ReRoutes": [
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "catalog-api",
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
          "Host": "basket-api",
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

Hlavní funkcí brány rozhraní API Ocelot je převzetí příchozích požadavků HTTP a jejich předání na příjem dat služby, v současné době jako další požadavek HTTP. Ocelot popisuje směrování jednoho požadavku do druhého jako ReRoute.

Například pojďme se zaměřit na jeden z ReRoutes v configuration.json shora, konfigurace pro mikroslužbu košíku.

```json
{
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket-api",
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

DownstreamPathTemplate, Scheme a DownstreamHostAndPorts provést adresu URL interní mikroslužby, že tento požadavek bude předán.

Port je vnitřní port používaný službou. Při použití kontejnerů, port zadaný v jeho dockerfile.

Jedná `Host` se o název služby, který závisí na překladu názvů služeb, který používáte. Při použití docker-compose jsou názvy služeb poskytovány hostitelem Dockeru, který používá názvy služeb poskytované v souborech docker-compose. Pokud používáte orchestrator jako Kubernetes nebo Service Fabric, tento název by měl být vyřešen překladem DNS nebo názvů poskytovaným každým orchestratorem.

DownstreamHostAndPorts je pole, které obsahuje hostitele a port všech podřízené služby, které chcete předat požadavky. Obvykle to bude obsahovat pouze jednu položku, ale někdy budete chtít požadavky na vyrovnávání zatížení na vaše služby navazujícím vysílání a Ocelot umožňuje přidat více než jednu položku a pak vybrat vyrovnávání zatížení. Ale pokud používáte Azure a jakýkoli orchestrátor, je pravděpodobně lepší nápad nazatížení rovnováhy s cloudovou a orchestrator infrastruktury.

UpstreamPathTemplate je adresa URL, kterou Ocelot použije k identifikaci šablony DownstreamPathTemplate, která má být pro daný požadavek od klienta používána. Nakonec upstreamHttpMethod se používá tak Ocelot můžete rozlišovat mezi různými požadavky (GET, POST, PUT) na stejnou adresu URL.

V tomto okamžiku můžete mít jednu bránu Rozhraní API Ocelot (ASP.NET Core WebHost) pomocí jednoho nebo [více sloučených souborů configuration.json](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) nebo můžete také uložit [konfiguraci v úložišti Consul KV](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).

Ale jak je zavedeno v části architektury a návrhu, pokud opravdu chcete mít autonomní mikroslužeb, může být lepší rozdělit tuto jednu monolitickou bránu rozhraní API do více bran rozhraní API a/nebo BFF (Backend pro front-end). Za tímto účelem se podívejme, jak implementovat tento přístup s kontejnery Dockeru.

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a>Použití jedné image kontejneru Dockeru ke spuštění několika různých typů kontejnerů brány rozhraní API / BFF

V eShopOnContainers používáme jednu bitovou kopii kontejneru Dockeru s bránou rozhraní API Ocelot, ale pak za běhu vytvoříme různé služby/kontejnery pro každý typ brány ROZHRANÍ API/BFF tím, že poskytujeme jiný soubor configuration.json pomocí svazku dockeru pro přístup k jiné složce PC pro každou službu.

![Diagram jedné image Dockeru brány Ocelot pro všechny brány rozhraní API.](./media/implement-api-gateways-with-ocelot/reusing-single-ocelot-docker-image.png)

**Obrázek 6-33**. Opětovné použití jedné bitové kopie Ocelot Docker u více typů brány rozhraní API

V eShopOnContainers je "Obecný Obrázek Docker u brány Rozhraní API" vytvořen s projektem s názvem OcelotApiGw a názvem obrázku "eshop/ocelotapigw", který je zadán v souboru docker-compose.yml. Potom při nasazování do Dockeru budou čtyři kontejnery brány ROZHRANÍ API vytvořené ze stejné image Dockeru, jak je znázorněno na následujícím výňatku ze souboru docker-compose.yml.

```yml
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

Navíc, jak můžete vidět v následujícím souboru docker-compose.override.yml, jediný rozdíl mezi těmito kontejnery brány rozhraní API je konfigurační soubor Ocelot, který se liší pro každý kontejner služby a je určen za běhu prostřednictvím Svazek Dockeru.

```yml
mobileshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5200:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Shopping/apigw:/app/configuration

mobilemarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5201:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Marketing/apigw:/app/configuration

webshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5202:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Shopping/apigw:/app/configuration

webmarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5203:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Marketing/apigw:/app/configuration
```

Z důvodu předchozího kódu a jak je znázorněno v průzkumníku Sady Visual Studio níže, jediný soubor potřebný k definování každé konkrétní obchodní/BFF brány rozhraní API je pouze configuration.json soubor, protože čtyři brány rozhraní API jsou založeny na stejné image Dockeru.

![Snímek obrazovky zobrazující všechny brány rozhraní API se soubory configuration.json](./media/implement-api-gateways-with-ocelot/ocelot-configuration-files.png)

**Obrázek 6-34**. Jediný soubor potřebný k definování každé brány ROZHRANÍ API / BFF s Ocelotem je konfigurační soubor

Rozdělením brány rozhraní API do více bran rozhraní API mohou různé vývojové týmy zaměřené na různé podmnožiny mikroslužeb spravovat své vlastní brány rozhraní API pomocí nezávislých konfiguračních souborů Ocelot. Navíc mohou současně znovu použít stejnou image Ocelot Docker.

Nyní, pokud spustíte eShopOnContainers s bránami rozhraní API (zahrnuty ve výchozím nastavení ve VS při otevírání eShopOnContainers-ServicesAndWebApps.sln řešení, nebo pokud běží "docker-compose up"), budou provedeny následující ukázkové trasy.

Například při návštěvě upstream `http://localhost:5202/api/v1/c/catalog/items/2/` URL obsluhované webshoppingapigw API Gateway, dostanete stejný výsledek `http://catalog-api/api/v1/2` z interní downstream URL v rámci hostitele Dockeru, jako v následujícím prohlížeči.

![Snímek obrazovky s prohlížečem zobrazujícím odpověď procházející bránou rozhraní API](./media/implement-api-gateways-with-ocelot/access-microservice-through-url.png)

**Obrázek 6-35**. Přístup k mikroslužbě prostřednictvím adresy URL poskytované bránou rozhraní API

Z důvodů testování nebo ladění, pokud jste chtěli přímý přístup ke kontejneru Katalog Docker (pouze ve vývojovém prostředí) bez průchodu bránou rozhraní API, protože 'catalog-api' je interní překlad DNS pro hostitele Dockeru (zjišťování služby zpracované názvy služeb docker-compose), jediný způsob, jak `http://localhost:5101/api/v1/Catalog/items/1` přímo přistupovat ke kontejneru, je prostřednictvím externího portu publikovaného v docker-compose.override.yml, který je k dispozici pouze pro vývojové testy, například v následujícím prohlížeči.

![Snímek obrazovky prohlížeče zobrazující přímou odpověď na soubor Catalog.api](./media/implement-api-gateways-with-ocelot/direct-access-microservice-testing.png)

**Obrázek 6-36**. Přímý přístup k mikroslužbě pro testovací účely

Ale aplikace je nakonfigurovántak, aby přistupuje ke všem mikroslužeb prostřednictvím brány rozhraní API, ne i když přímý port "zkratky".

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a>Vzor agregace brány v eShopOnContainers

Jak bylo zavedeno dříve, flexibilní způsob implementace požadavků agregace je s vlastní služby, podle kódu. Můžete také implementovat agregaci požadavků pomocí [funkce Agregace požadavků v Ocelotu](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation), ale nemusí být tak flexibilní, jak potřebujete. Proto je vybraný způsob implementace agregace v eShopOnContainers s explicitní ASP.NET služby Core Web API pro každý agregátor.

Podle tohoto přístupu je diagram složení brány rozhraní API ve skutečnosti o něco rozšířenější při zvažování služeb agregátoru, které nejsou zobrazeny ve zjednodušeném diagramu globální architektury, který byl zobrazen dříve.

V následujícím diagramu můžete také zobrazit, jak služby agregátoru pracují s jejich souvisejícíbrány rozhraní API.

![Diagram architektury eShopOnContainers znázorňující agregátorové služby.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture-aggregator-services.png)

**Obrázek 6-37**. architektura eShopOnContainers s agregátorovými službami

Dalším přiblížením v obchodní oblasti "Nakupování" na následujícím obrázku uvidíte, že chattiness mezi klientskými aplikacemi a mikroslužbami se snižuje při použití agregátorových služeb v gatewayrozhraní API.

![Diagram znázorňující přiblížení architektury eShopOnContainers.](./media/implement-api-gateways-with-ocelot/zoom-in-vision-aggregator-services.png)

**Obrázek 6-38**. Zvětšete vizi agregátorových služeb

Můžete si všimnout, jak když diagram zobrazuje možné požadavky pocházející z brány rozhraní API může získat složité. I když můžete vidět, jak by se šipky v modré barvě zjednodušily, z pohledu klientských aplikací, při použití vzoru agregátoru snížením chattiness a latence v komunikaci, což v konečném důsledku výrazně zlepšuje uživatelské prostředí pro vzdálené aplikace ( mobilní a SPA), zejména.

V případě obchodní oblasti "Marketing" a mikroslužeb se jedná o jednoduchý případ použití, takže nebylo nutné používat agregátory, ale v případě potřeby by to mohlo být také možné.

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a>Ověřování a autorizace v branách rozhraní API Ocelot

V bráně rozhraní API Ocelot můžete sedět ověřovací služby, jako je například ASP.NET služby Core Web API pomocí [IdentityServer](https://identityserver.io/) poskytující ověřovací token, a to buď ven nebo uvnitř brány rozhraní API.

Vzhledem k tomu, že eShopOnContainers používá více bran rozhraní API s hranicemi založenými na BFF a obchodních oblastech, služba Identity/Auth je vynechána z bran rozhraní API, jak je zvýrazněno žlutě v následujícím diagramu.

![Diagram znázorňující mikroslužbu Identity pod bránou rozhraní API.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-identity-service-position.png)

**Obrázek 6-39**. Pozice služby Identity v eShopOnContainers

Ocelot však také podporuje sedící mikroslužbu Identity/Auth v rámci hranice brány rozhraní API, jako v tomto jiném diagramu.

![Diagram znázorňující ověřování v bráně rozhraní API Ocelot.](./media/implement-api-gateways-with-ocelot/ocelot-authentication.png)

**Obrázek 6-40**. Autentizace v Ocelotu

Jak ukazuje předchozí diagram, když je mikroslužba Identity pod bránou rozhraní API (AG): 1) AG požaduje auth token z mikroslužby identity, 2) Mikroslužba identity vrátí token AG, 3-4) AG požadavky z mikroslužeb pomocí tokenu ověření. Vzhledem k tomu, že aplikace eShopOnContainers rozdělila bránu rozhraní API na více bff (Backend pro front-end) a obchodní oblasti brány rozhraní API, další možností by bylo vytvořit další bránu rozhraní API pro průřezové obavy. Tato volba by byla spravedlivá ve složitější architektuře založené na mikroslužbách s více průřezovými obavami mikroslužeb. Vzhledem k tomu, že v eShopOnContainers existuje pouze jeden průřezový problém, bylo rozhodnuto, že bude pouze zpracovávat bezpečnostní službu z oblasti brány ROZHRANÍ API, pro jednoduchost.

V každém případě pokud je aplikace zabezpečená na úrovni brány rozhraní API, ověřovací modul brány rozhraní API Ocelot je nejprve navštíven při pokusu o použití jakékoli zabezpečené mikroslužby. To přesměruje požadavek HTTP na návštěvu identity nebo ověření mikroslužby získat přístupový token, takže můžete navštívit chráněné služby s access_token.

Způsob zabezpečení s ověřováním libovolné služby na úrovni brány rozhraní API je nastavení authenticationProviderKey v souvisejícínastavení na configuration.json.

```json
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket-api",
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

Při spuštění Ocelot, se podíváme na ReRoutes AuthenticationOptions.AuthenticationProviderKey a zkontrolujte, zda je u daného klíče registrován poskytovatel ověřování. Pokud není, pak Ocelot nezačne. Pokud existuje, pak ReRoute bude používat tohoto zprostředkovatele při spuštění.

Vzhledem k tomu, že Ocelot WebHost je nakonfigurován s `authenticationProviderKey = "IdentityApiKey"`, které budou vyžadovat ověření vždy, když tato služba má nějaké požadavky bez tokenu ověření.

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
        }
    }
}
```

Potom je také nutné nastavit autorizaci s atributem [Authorize] na libovolném prostředku, ke kterým má být přistupovat jako mikroslužby, například v následujícím řadiči mikroslužeb košíku.

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

ValidAudiences jako "košík" jsou korelovány s publikem `AddJwtBearer()` definované v každé mikroslužbě s na ConfigureServices() třídy Startup, například v kódu níže.

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

Pokud se pokusíte o přístup k jakékoli zabezpečené mikroslužby, jako je `http://localhost:5202/api/v1/b/basket/1`mikroslužba košíku s reroute adresu URL na základě brány rozhraní API jako , pak dostanete 401 neoprávněné, pokud zadáte platný token. Na druhou stranu pokud je ověřena adresa URL ReRoute, Ocelot vyvolá jakékoli podřízené schéma, které je s ním spojeno (adresa URL interní mikroslužby).

**Autorizace na úrovni ReRoutes společnosti Ocelot.**  Ocelot podporuje autorizaci založenou na deklaracích identity vyhodnocenou po ověření. Autorizaci nastavíte na úrovni postupu přidáním následujících řádků do konfigurace ReRoute.

```json
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

V tomto příkladu při volání autorizace middleware Ocelot zjistí, zda uživatel má typ deklarace "UserType" v tokenu a pokud je hodnota této deklarace "zaměstnanec". Pokud tomu tak není, pak uživatel nebude autorizován a odpověď bude zakázána 403.

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a>Použití kubernetes ingress plus Ocelot API brány

Při použití Kubernetes (jako v clusteru služby Azure Kubernetes) obvykle sjednocujete všechny požadavky HTTP prostřednictvím [úrovně Kubernetes Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/) založené na *Nginx*.

V Kubernetes, pokud nepoužíváte žádný přístup příchozího přenosu dat, pak vaše služby a pody mají IP adresy pouze směrovatelné v síti clusteru.

Ale pokud používáte přístup příchozího přenosu dat, budete mít střední vrstvu mezi Internetem a vašimi službami (včetně vašich bran rozhraní API), která funguje jako reverzní proxy server.

Jako definice příchozí přenos dat je kolekce pravidel, která umožňují příchozí připojení k dosažení clusterových služeb. Příchozí přenos dat je obvykle nakonfigurován tak, aby poskytoval služby externě dosažitelné adresy URL, provoz vyvažování zatížení, ukončení SSL a další. Uživatelé požadují příchozí přenos dat posting ingress prostředku na server rozhraní API.

V eShopOnContainers při vývoji místně a pomocí pouze váš vývojový počítač jako hostitele Dockeru, nepoužíváte žádné příchozí přenos dat, ale pouze více bran rozhraní API.

Však při cílení "produkční" prostředí založené na Kubernetes, eShopOnContainers používá příchozí přenos dat před brány rozhraní API. Tímto způsobem klienti stále volat stejnou základní adresu URL, ale požadavky jsou směrovány do více bran rozhraní API nebo BFF.

Brány rozhraní API jsou front-endy nebo fasády, které vynořují pouze služby, ale ne webové aplikace, které jsou obvykle mimo jejich rozsah. Kromě toho brány rozhraní API může skrýt některé interní mikroslužeb.

Příchozí přenos dat je však pouze přesměrování požadavků HTTP, ale ne snaží skrýt žádné mikroslužby nebo webové aplikace.

S ingress Nginx vrstvy v Kubernetes před webových aplikací plus několik Ocelot API brány / BFF je ideální architektura, jak je znázorněno na následujícím diagramu.

![Diagram znázorňující, jak úroveň příchozího přenosu dat zapadá do prostředí AKS.](./media/implement-api-gateways-with-ocelot/eshoponcontainer-ingress-tier.png)

**Obrázek 6-41**. Ingress vrstva v eShopOnContainers při nasazení do Kubernetes

Příchozí přenos dat Kubernetes funguje jako reverzní proxy pro veškerý provoz do aplikace, včetně webových aplikací, které jsou obvykle mimo obor brány rozhraní API. Když nasadíte eShopOnContainers do Kubernetes, zpřístupní jen několik služeb nebo koncových bodů prostřednictvím _příchozího přenosu dat_, v podstatě následující seznam příponek na adresách URL:

- `/`pro klientskou webovou aplikaci SPA
- `/webmvc`pro klientskou webovou aplikaci MVC
- `/webstatus`pro klientskou webovou aplikaci zobrazující stav/kontroly stavu
- `/webshoppingapigw`pro web BFF a nákupní obchodní procesy
- `/webmarketingapigw`pro web BFF a marketingové obchodní procesy
- `/mobileshoppingapigw`pro mobilní BFF a nákupní obchodní procesy
- `/mobilemarketingapigw`pro mobilní BFF a marketingové obchodní procesy

Při nasazování do Kubernetes, každý Ocelot API Gateway používá jiný soubor "configuration.json" pro každý _pod_ běží brány rozhraní API. Tyto soubory "configuration.json" jsou poskytovány připojením (původně se skriptem deploy.ps1) svazku vytvořeného na základě _konfigurační mapy_ Kubernetes s názvem "ocelot". Každý kontejner připojí svůj související konfigurační `/app/configuration`soubor do složky kontejneru s názvem .

Ve zdrojových kódech eShopOnContainers lze původní soubory "configuration.json" `k8s/ocelot/` nalézt ve složce. Je tu jeden soubor pro každý BFF/APIGateway.

## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a>Další průřezové funkce v bráně API Ocelot

Existují další důležité funkce pro výzkum a použití, při použití Brány rozhraní API Ocelot, popsané v následujících odkazech.

- **Zjišťování služeb na straně klienta integrující Ocelot s konzulem nebo Eurekou** \
  <https://ocelot.readthedocs.io/en/latest/features/servicediscovery.html>

- **Ukládání do mezipaměti na úrovni brány rozhraní API** \
  <https://ocelot.readthedocs.io/en/latest/features/caching.html>

- **Protokolování na úrovni brány rozhraní API** \
  <https://ocelot.readthedocs.io/en/latest/features/logging.html>

- **Kvalita služeb (opakování a jističe) na úrovni brány ROZHRANÍ API** \
  <https://ocelot.readthedocs.io/en/latest/features/qualityofservice.html>

- **Omezení rychlosti** \
  [https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html](https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )

> [!div class="step-by-step"]
> [Předchozí](background-tasks-with-ihostedservice.md)
> [další](../microservice-ddd-cqrs-patterns/index.md)
