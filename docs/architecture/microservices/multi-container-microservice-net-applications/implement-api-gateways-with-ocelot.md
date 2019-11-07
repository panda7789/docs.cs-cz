---
title: Implementace bran rozhraní API s Ocelotem
description: Naučte se implementovat brány API pomocí Ocelot a jak používat Ocelot v prostředí založeném na kontejnerech.
ms.date: 10/02/2018
ms.openlocfilehash: 6c576a17d784777557bfb8bd99438eb111e8ec2e
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737657"
---
# <a name="implement-api-gateways-with-ocelot"></a>Implementace bran API pomocí Ocelot

Referenční aplikace [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) používá [Ocelot](https://github.com/ThreeMammals/Ocelot), jednoduchou a odlehčenou bránu API, kterou můžete nasazovat kdekoli spolu s mikroslužbami nebo kontejnery, například v některém z následujících prostředí, které používá nástroj. eShopOnContainers.

- Hostitel Docker, ve vašem místním počítači pro vývoj, místně nebo v cloudu.
- Kubernetes cluster, místní nebo ve spravovaném cloudu, jako je Azure Kubernetes Service (AKS).
- Service Fabric clusteru, místně nebo v cloudu.
- Service Fabric mesh, jako PaaS/bez serveru v Azure.

## <a name="architect-and-design-your-api-gateways"></a>Architekt a návrh vašich bran rozhraní API

Následující diagram architektury ukazuje, jak jsou brány rozhraní API implementované pomocí Ocelot v eShopOnContainers.

![Diagram znázorňující architekturu eShopOnContainers](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture.png)

**Obrázek 6-28**. Architektura eShopOnContainers s bránami API

Tento diagram znázorňuje, jak je celá aplikace nasazena do jednoho hostitele Docker nebo vývojového počítače s názvem "Docker for Windows" nebo "Docker for Mac". Nasazení do jakéhokoli nástroje Orchestrator by však bylo poměrně podobné, ale každý kontejner v diagramu může být v produktu Orchestrator zvětšený.

Kromě toho by se měly prostředky infrastruktury, jako jsou databáze, mezipaměť a zprostředkovatelé zpráv, přesměrovat z produktu Orchestrator a nasazovat na vysoce dostupné systémy pro infrastrukturu, jako je Azure SQL Database, Azure Cosmos DB, Azure Redis, Azure Service Bus, nebo jakékoli řešení clusteringu s vysokou dostupností v místním prostředí.

Vzhledem k tomu, že v diagramu můžete také všimnout, že několik bran rozhraní API umožňuje, aby více vývojových týmů bylo autonomní (v tomto případě marketingové funkce vs. nákupy) při vývoji a nasazování mikroslužeb a jejich vlastních souvisejících bran rozhraní API.

Pokud jste měli jedinou bránu rozhraní API monolitické, která by znamenala, že se jeden bod dá aktualizovat několika vývojovými týmy, může to pár všech mikroslužeb s jedinou částí aplikace.

V takovém případě je v podstatě ještě mnohem víc, ale jemně zrnitou bránu API můžete omezit na jednu jednotlivou obchodní mikroslužbu v závislosti na zvolené architektuře. Používání hranic brány API, které jsou vyřízeny firmou nebo doménou, vám pomůže dosáhnout lepšího návrhu.

Například přesnější členitost v úrovni brány rozhraní API může být obzvláště užitečná pro pokročilejší aplikace složených uživatelského rozhraní, které jsou založené na mikroslužbách, protože koncept jemně odstupňované brány rozhraní API je podobný službě složení uživatelského rozhraní.

V předchozí části se zobrazí další podrobnosti, které [vytváří složené uživatelské rozhraní založené na mikroslužbách](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md).

Jako Key poznatkem pro mnoho středních a velkých aplikací je použití předem vytvořeného produktu brány rozhraní API obvykle dobrým přístupem, ale ne jako s jedním monolitické Agregátorem nebo jedinečnou bránou rozhraní API, pokud tato brána API nepovoluje víc nezávislých. oblasti konfigurace pro několik vývojových týmů vytvářejících autonomní mikroslužby.

### <a name="sample-microservicescontainers-to-re-route-through-the-api-gateways"></a>Ukázkové mikroslužby/kontejnery pro přesměrování přes brány rozhraní API

Například eShopOnContainers má kolem šesti interních typů mikroslužeb, které je třeba publikovat prostřednictvím bran rozhraní API, jak je znázorněno na následujícím obrázku.

![Snímek obrazovky se složkou služby zobrazující její podsložky](./media/implement-api-gateways-with-ocelot/eshoponcontainers-microservice-folders.png)

**Obrázek 6-29**. Složky mikroslužeb v řešení eShopOnContainers v aplikaci Visual Studio

O službě identit, v návrhu, který je z hlediska směrování brány rozhraní API, je jediným problémem, který se týká pouze průřezů v systému, i když s Ocelot je také možné ho zahrnout jako součást seznamů opětovného směrování.

Všechny tyto služby se v současnosti implementují jako ASP.NET Core služby webového rozhraní API, jak je můžete říct od kódu. Pojďme se zaměřit na jednu z mikroslužeb, jako je kód mikroslužby katalogu.

![Snímek obrazovky Průzkumník řešení zobrazující obsah projektu Catalog. API](./media/implement-api-gateways-with-ocelot/catalog-api-microservice-folders.png)

**Obrázek 6-30**. Ukázka mikroslužby webového rozhraní API (služba katalogu mikroslužeb)

Můžete vidět, že mikroslužba katalogu je typický ASP.NET Core projektu webového rozhraní API s několika řadiči a metodami, jako v následujícím kódu.

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

Požadavek HTTP ukončí běh tohoto druhu C# kódu s přístupem k databázi mikroslužeb a všech dalších potřebných akcí.

V souvislosti s adresou URL mikroslužeb, když jsou kontejnery nasazeny na místním počítači pro vývoj (místní hostitel Docker), má každý kontejner mikroslužeb vždy interní port (obvykle port 80), který je uveden v souboru Dockerfile, jako v následujícím souboru Dockerfile:

```Dockerfile
FROM microsoft/aspnetcore:2.0.5 AS base
WORKDIR /app
EXPOSE 80
```

Port 80 zobrazený v kódu je interní v rámci hostitele Docker, takže není dostupný pro klientské aplikace.

Klientské aplikace mají přístup pouze k externím portům (pokud existuje), které jsou publikovány při nasazení pomocí `docker-compose`.

Tyto externí porty by neměly být publikovány při nasazování do produkčního prostředí. To je přesně důvod, proč chcete používat bránu rozhraní API, abyste se vyhnuli přímé komunikaci mezi klientskými aplikacemi a mikroslužbami.

Při vývoji ale chcete přímo získat přístup k mikroslužbám nebo kontejneru a spustit ho prostřednictvím Swagger. To je důvod, proč v eShopOnContainers jsou externí porty stále zadané i v případě, že se nepoužívají v bráně API ani v klientských aplikacích.

Tady je příklad souboru `docker-compose.override.yml` pro mikroslužbu katalogu:

```yml
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

Můžete zjistit, jak v konfiguraci Docker-Compose. override. yml je interním portem kontejneru katalogu port 80, ale port pro externí přístup je 5101. Tento port by ale neměl používat aplikace při použití brány API, jenom pro ladění, spouštění a testování jenom pro mikroslužby katalogu.

Za normálních okolností nebudete nasazovat do provozního prostředí Docker – to znamená, že správné provozní prostředí nasazení pro mikroslužby je Orchestrator, jako je Kubernetes nebo Service Fabric. Při nasazování do těchto prostředí budete používat jiné konfigurační soubory, kde nebudete publikovat přímo žádný externí port pro mikroslužby, ale reverzní proxy server budete vždycky používat z brány rozhraní API.

Spusťte službu cloudové služby katalogu v místním hostiteli Docker buď spuštěním úplného řešení eShopOnContainers ze sady Visual Studio (spustí všechny služby v Docker-skládání souborů), nebo stačí spustit službu Cloud Service pomocí následujícího Docker – sestavení příkaz v prostředí CMD nebo PowerShell umístěný ve složce, kde jsou umístěny `docker-compose.yml` a Docker-Compose. override. yml.

```console
docker-compose run --service-ports catalog.api
```

Tento příkaz spustí pouze závislosti kontejneru služby Catalog. API a závislostí, které jsou zadány v Docker-Compose. yml. V tomto případě kontejner SQL Server a kontejner RabbitMQ.

Pak můžete přímo získat přístup ke mikroslužbám katalogu a pomocí uživatelského rozhraní Swagger získat přístup k jeho metodám přímo prostřednictvím tohoto "externího" portu, v tomto případě `http://localhost:5101/swagger`:

![Snímek obrazovky uživatelského rozhraní Swagger zobrazující REST API katalogu. API](./media/implement-api-gateways-with-ocelot/test-catalog-microservice.png)

**Obrázek 6-31**. Testování mikroslužby katalogu pomocí uživatelského rozhraní Swagger

V tomto okamžiku můžete nastavit zarážku v C# kódu v sadě Visual Studio, testovat mikroslužbu pomocí metod vydaných v uživatelském rozhraní Swagger a nakonec vyčistit vše pomocí `docker-compose down` příkazu.

Komunikace s přímým přístupem k mikroslužbám ale v tomto případě přes externí port 5101 je přesně to, co chcete v aplikaci zabránit. A můžete se tomu vyhnout nastavením dodatečné úrovně dereference brány API (Ocelot, v tomto případě). Klientská aplikace tak nebude mít přímý přístup k mikroslužbám.

## <a name="implementing-your-api-gateways-with-ocelot"></a>Implementace bran API pomocí Ocelot

Ocelot je v podstatě sada middlewarů, které můžete použít v určitém pořadí.

Ocelot je navržená tak, aby pracovala pouze s ASP.NET Core. Zaměřuje se na netstandard 2.0, takže se dá použít kdekoli .NET Standard 2,0, včetně běhového prostředí .NET Core 2,0 a .NET Framework 4.6.1 runtime a up.

Ocelot a jeho závislosti nainstalujete v projektu ASP.NET Core pomocí [balíčku NuGet ocelot](https://www.nuget.org/packages/Ocelot/)ze sady Visual Studio.

```powershell
Install-Package Ocelot
```

V eShopOnContainers je jeho implementace brány API jednoduchý ASP.NET Core projekt webhosta a middleware Ocelot zpracovává všechny funkce brány API, jak je znázorněno na následujícím obrázku:

![Snímek obrazovky Průzkumník řešení zobrazující projekt brány API Ocelot](./media/implement-api-gateways-with-ocelot/ocelotapigw-base-project.png)

**Obrázek 6-32**. Projekt OcelotApiGw Base v eShopOnContainers

Tento ASP.NET Core projekt webhost je vytvořen v podstatě pomocí dvou jednoduchých souborů: `Program.cs` a `Startup.cs`.

Program.cs potřebuje jenom vytvořit a nakonfigurovat typické ASP.NET Core BuildWebHost.

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

Důležitým bodem pro Ocelot je soubor `configuration.json`, který musíte poskytnout tvůrci prostřednictvím metody `AddJsonFile()`. V `configuration.json` je místo, kde zadáte všechny přesměrování brány API, což znamená, že externí koncové body s konkrétními porty a korelační interní koncové body jsou obvykle pomocí různých portů.

```json
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

Existují dva oddíly konfigurace. Pole opakovaných tras a GlobalConfiguration. Přesměrování jsou objekty, které říká Ocelot, jak zacházet s nadřazeným požadavkem. Globální konfigurace umožňuje přepisovat nastavení specifická pro přesměrování. To je užitečné v případě, že nechcete spravovat spoustu nastavení konkrétního přesměrování.

Tady je zjednodušený příklad, jak [přesměrovat konfigurační soubor](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) z jedné z bran rozhraní API z eShopOnContainers.

```json
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

Hlavní funkcí brány Ocelot API je přijmout příchozí požadavky HTTP a přeslat je do služby pro příjem dat, a to v současné době jako jiný požadavek HTTP. Ocelot je popis směrování jedné žádosti na jinou jako opakované směrování.

Řekněme například, že se zaměříme na jednu z přesměrování v Configuration. JSON výše. konfigurace pro mikroslužbu koše.

```json
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

DownstreamPathTemplate, schéma a DownstreamHostAndPorts vytvoří interní adresu URL mikroslužby, na kterou se tato žádost přepošle.

Port je interní port používaný službou. Při použití kontejnerů se port zadal na jeho souboru Dockerfile.

`Host` je název služby, který závisí na překladu názvu služby, který používáte. Při použití Docker-skládání jsou názvy služeb poskytovány hostitelem Docker, který používá názvy služeb, které jsou k dispozici v souborech Docker-pro vytváření. Pokud používáte Orchestrator jako Kubernetes nebo Service Fabric, měl by tento název přeložit DNS nebo překlad IP adres, který poskytuje každý Orchestrator.

DownstreamHostAndPorts je pole, které obsahuje hostitele a port jakékoli služby pro příjem dat, na kterou chcete předávané požadavky. Obvykle bude obsahovat pouze jednu položku, někdy ale můžete chtít vyrovnávat zatížení požadavků na služby pro příjem dat a Ocelot umožňuje přidat více než jednu položku a pak vybrat nástroj pro vyrovnávání zatížení. Pokud ale používáte Azure a jakýkoli Orchestrator, je pravděpodobně lepší vyrovnávat zatížení s infrastrukturou Cloud a Orchestrator.

UpstreamPathTemplate je adresa URL, kterou Ocelot použije k identifikaci, které DownstreamPathTemplate se má použít pro daný požadavek od klienta. Nakonec se použije UpstreamHttpMethod, aby Ocelot mohl rozlišovat různé požadavky (GET, POST, PUT) na stejnou adresu URL.

V tomto okamžiku můžete mít jedinou bránu Ocelot API (ASP.NET Core webhost) pomocí jednoho nebo [několika sloučených souborů Configuration. JSON](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) nebo můžete konfiguraci uložit i [v úložišti Consul KV](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).

Jak je zavedené v sekcích architektury a návrhu, pokud opravdu chcete mít autonomní mikroslužby, může být lepší rozdělit tuto bránu monolitické API na několik bran rozhraní API a/nebo BFF (back-end pro front-end). Pro tento účel se podívejme, jak implementovat tento přístup k kontejnerům Docker.

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a>Použití jediné image kontejneru Docker pro spuštění více různých typů kontejnerů brány API/BFF

V eShopOnContainers používáme jednu Image kontejneru Docker s bránou rozhraní Ocelot API, ale za běhu vytvoříme pro každý typ rozhraní API – Gateway nebo BFF různé služby a kontejnery, a to tak, že zadáte jiný soubor Configuration. JSON, který bude používat svazek Docker pro pro každou službu získáte přístup k jiné složce počítače.

![Diagram jedné image Docker Ocelot brány pro všechny brány API](./media/implement-api-gateways-with-ocelot/reusing-single-ocelot-docker-image.png)

**Obrázek 6-33**. Opětovné použití jedné image Docker Ocelot napříč více typy brány rozhraní API

V eShopOnContainers se v projektu s názvem "OcelotApiGw" a s názvem Image "eshop/OcelotApiGw", který je uveden v souboru Docker-Compose. yml, vytvoří "Obecná image Docker brány API Ocelot". Při nasazování do Docker se pak vytvoří čtyři kontejnery API-Gateway vytvořené z stejné image Docker, jak je znázorněno v následujícím extrakci ze souboru Docker-Compose. yml.

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

Jak vidíte v následujícím souboru Docker-Compose. override. yml, jediným rozdílem mezi těmito kontejnery brány API je konfigurační soubor Ocelot, který se liší pro každý kontejner služby a je určen za běhu prostřednictvím Svazek Docker.

```yml
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

Z důvodu tohoto předchozího kódu, jak je znázorněno v Průzkumníkovi aplikace Visual Studio níže, je jediným souborem potřebným k definování každé konkrétní brány rozhraní API pro obchodní/BFF jenom soubor Configuration. JSON, protože čtyři brány rozhraní API jsou založené na stejné imagi Docker.

![Snímek obrazovky zobrazující všechny brány rozhraní API se soubory Configuration. JSON.](./media/implement-api-gateways-with-ocelot/ocelot-configuration-files.png)

**Obrázek 6-34**. Jediným souborem potřebným k definování každého rozhraní API Gateway/BFF s Ocelot je konfigurační soubor.

Díky rozdělení brány API na několik bran rozhraní API můžou různé vývojové týmy zaměřené na různé podmnožiny mikroslužeb spravovat svoje vlastní brány API pomocí nezávislých Ocelot konfiguračních souborů. Navíc zároveň můžou znovu použít stejnou image Docker Ocelot.

Když teď spustíte eShopOnContainers s branami rozhraní API (standardně ve verzi VS při otevírání řešení eShopOnContainers-ServicesAndWebApps. sln nebo spuštěním příkazu "Docker-sestavit"), provedou se následující ukázkové trasy.

Když například navštívíte nadřazený URL `http://localhost:5202/api/v1/c/catalog/items/2/` obsluhované bránou webshoppingapigw API, získáte stejný výsledek z interní adresy URL pro příjem dat `http://catalog.api/api/v1/2` v rámci hostitele Docker, jako v následujícím prohlížeči.

![Snímek obrazovky prohlížeče znázorňující odpověď procházející rozhraním API Gateway](./media/implement-api-gateways-with-ocelot/access-microservice-through-url.png)

**Obrázek 6-35**. Přístup k mikroslužbám prostřednictvím adresy URL poskytované bránou API

Z důvodu testování nebo ladění, pokud jste chtěli získat přímý přístup ke kontejneru Docker katalogu (jenom ve vývojovém prostředí) bez předávání bránou API, protože Catalog. API je interní překlad DNS na hostitele Docker (služba zjišťování, které zpracovává služba Docker – název služby: jediným způsobem, jak přímo přistupovat ke kontejneru, je externí port publikovaný v Docker-Compose. override. yml, který je k dispozici pouze pro vývojové testy, například `http://localhost:5101/api/v1/Catalog/items/1` v následujícím prohlížeči.

![Snímek obrazovky prohlížeče ukazující přímou odpověď na katalog. API](./media/implement-api-gateways-with-ocelot/direct-access-microservice-testing.png)

**Obrázek 6-36**. Přímý přístup k mikroslužbám pro účely testování

Ale aplikace je nakonfigurovaná tak, aby přístupná ke všem mikroslužbám prostřednictvím bran rozhraní API, ne i přes "zkratky" s přímým portem ".

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a>Model agregace brány v eShopOnContainers

Jak jsme představili dřív, flexibilní způsob implementace agregace požadavků je s vlastními službami, podle kódu. Můžete také implementovat agregaci požadavků s [funkcí agregace požadavků v ocelot](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation), ale nemusí být tak flexibilní, jak potřebujete. Proto je vybraný způsob implementace agregace v eShopOnContainers s explicitními ASP.NET Core službami webového rozhraní API pro každý agregátor.

V souladu s tímto přístupem je diagram kompozice brány API ve skutečnosti trochu rozšířený při zvažování agregátorových služeb, které se nezobrazuje v diagramu zjednodušené globální architektury.

V následujícím diagramu můžete také vidět, jak služby Agregátoru fungují s jejich souvisejícími bránami API.

![Diagram architektury eShopOnContainers znázorňující služby Agregátoru](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture-aggregator-services.png)

**Obrázek 6-37**. Architektura eShopOnContainers s agregátor Services

Další přiblížení: v obchodní oblasti "nakupování" na následujícím obrázku vidíte, že upovídanost mezi klientskými aplikacemi a mikroslužbami se při používání Agregátoru v bránách rozhraní API zkrátí.

![Diagram znázorňující přiblížení architektury eShopOnContainers](./media/implement-api-gateways-with-ocelot/zoom-in-vision-aggregator-services.png)

**Obrázek 6-38**. Přiblížení ve výhledu Agregátorových služeb

Můžete si všimnout, že když diagram zobrazuje možné požadavky přicházející z bran rozhraní API, může získat poměrně složitý přístup. I když vidíte, jak se budou šipky v modrém zjednodušeny, z perspektivy klientských aplikací při použití vzoru Agregátoru tím, že se omezí upovídanost a latence v komunikaci, a nakonec se tím významně zlepšuje uživatelské prostředí pro vzdálené aplikace ( mobilní a SPA aplikace), zejména.

V případě obchodní oblasti a mikroslužeb "marketing" se jedná o velmi jednoduchý případ použití, takže nemusíte používat agregátory, ale v případě potřeby to může být možné.

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a>Ověřování a autorizace v bránách rozhraní API Ocelot

V bráně rozhraní Ocelot API můžete službu ověřování, jako je ASP.NET Core služby webového rozhraní API, nastavovat pomocí [IdentityServer](https://identityserver.io/) , který poskytuje ověřovací token, a to buď nebo uvnitř brány rozhraní API.

Vzhledem k tomu, že eShopOnContainers používá více bran rozhraní API s hranicemi založenými na BFF a obchodních oblastech, služba identity/auth nepochází z bran rozhraní API, jak je zvýrazněna žlutě v následujícím diagramu.

![Diagram znázorňující mikroslužbu identity pod bránou API](./media/implement-api-gateways-with-ocelot/eshoponcontainers-identity-service-position.png)

**Obrázek 6-39**. Pozice služby identity v eShopOnContainers

Ocelot však podporuje i podřízení identity/auth mikroslužby v rámci hranice brány rozhraní API, jako v tomto jiném diagramu.

![Diagram znázorňující ověřování v bráně Ocelot API](./media/implement-api-gateways-with-ocelot/ocelot-authentication.png)

**Obrázek 6-40**. Ověřování v Ocelot

Jak ukazuje předchozí diagram, když je mikroslužba identity pod bránou API (AG): 1) AG vyžádá ověřovací token od mikroslužby identity, 2) mikroslužba identity vrátí token do AG, 3-4) žádosti AG z mikroslužeb pomocí ověřovacího tokenu. Vzhledem k tomu, že aplikace eShopOnContainers rozdělila bránu API na více BFF (back-end pro front-end) a brány rozhraní API obchodních oblastí, měla by být další možnost vytvoření další brány rozhraní API pro různé průřezy. Tato volba by byla poctivá v komplexnější architektuře založené na mikroslužbách s více aspekty, které se na mikroslužby týkají. Vzhledem k tomu, že v eShopOnContainers existuje pouze jeden problém pro průřez, bylo rozhodnuto pouze zpracovat službu zabezpečení ze sféry brány rozhraní API, a to z důvodu zjednodušení.

V každém případě platí, že pokud je aplikace zabezpečená na úrovni brány rozhraní API, při pokusu o použití zabezpečené mikroslužby se nejdřív navštíví modul ověřování brány API Ocelot. Ta přesměruje požadavek HTTP na návštěvu identity nebo auth mikroslužeb, aby získal přístupový token, takže můžete přejít k chráněným službám pomocí access_token.

Způsob zabezpečení při ověřování jakékoli služby na úrovni brány rozhraní API je nastavením AuthenticationProviderKey v souvisejícím nastavení v Configuration. JSON.

```json
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

Když se Ocelot spustí, bude se pohlížet na přesměrování AuthenticationOptions. AuthenticationProviderKey a zkontrolovat, jestli je u daného klíče zaregistrovaný zprostředkovatel ověřování. Pokud ne, Ocelot se nespustí. V takovém případě bude přesměrování používat tohoto poskytovatele při jeho spuštění.

Protože je webhost Ocelot nakonfigurovaný pomocí `authenticationProviderKey = "IdentityApiKey"`, bude vyžadovat ověření vždy, když má služba nějaké požadavky bez tokenu ověřování.

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

Pak musíte také nastavit autorizaci pomocí atributu [Authorization] u libovolného prostředku, ke kterému se mají přicházet jako mikroslužby, například v následujícím koši mikrořadiče pro registraci.

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

ValidAudiences jako "Koš" se koreluje s cílovou skupinou definovanou v každé mikroslužbě s `AddJwtBearer()` na ConfigureServices () třídy po spuštění, jako je například v následujícím kódu.

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

Pokud se pokusíte o přístup k zabezpečené mikroslužbě, jako je třeba mikroslužba košíku s adresou URL pro přesměrování na základě brány API, jako je `http://localhost:5202/api/v1/b/basket/1`, získáte 401 neautorizovaný, pokud nezadáte platný token. Na druhou stranu platí, že pokud se ověří adresa URL opětovného směrování, Ocelot vyvolá k tomu, že je k ní přiřazeno jakékoli související schéma (interní adresa URL mikroslužeb).

**Autorizace na úrovni přesměrování v Ocelot.**  Ocelot podporuje ověřování na základě deklarace identity vyhodnocené po ověření. Autorizaci nastavíte na úrovni trasy přidáním následujících řádků do konfigurace přesměrování.

```json
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

V tomto příkladu, když se volá middleware autorizace, Ocelot zjistí, jestli má uživatel v tokenu typ s deklarací UserType, a pokud je hodnota této deklarace identity Employee. Pokud ne, uživatel nebude autorizovaný a odpověď bude 403 zakázaná.

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a>Použití Kubernetes a Ocelot API Gateway

Při použití Kubernetes (jako v clusteru služby Azure Kubernetes) obvykle sjednotete všechny požadavky HTTP prostřednictvím [vrstvy Kubernetes](https://kubernetes.io/docs/concepts/services-networking/ingress/) příchozího přenosu dat založené na *Nginx*.

Pokud v Kubernetes nepoužíváte žádný přístup k příchozímu přístupu, pak vaše služby a lusky mají IP adresy směrovatelné jenom na síť s clustery.

Pokud ale použijete přístup příchozího přenosu dat, budete mít střední vrstvu mezi Internetem a vašimi službami (včetně vašich bran rozhraní API), které fungují jako reverzní proxy server.

V rámci definice příchozího přenosu dat je kolekce pravidel, která povolují příchozí připojení k dosažení clusterových služeb. Příchozí přenos dat je obvykle nakonfigurovaný tak, aby poskytoval služby externě dosažitelným adresám URL, provozu vyrovnávání zatížení, ukončení protokolu SSL a dalším. Uživatelé požadují příchozí odesílání prostředků příchozího přenosu dat na Server API.

V eShopOnContainers při vývoji místně a jenom pomocí vývojového počítače jako hostitele Docker nepoužíváte žádné příchozí přenosy, ale jenom několik bran rozhraní API.

Pokud ale zacílíte na prostředí "produkční" prostředí založené na Kubernetes, eShopOnContainers za brány rozhraní API používá příchozí přenos dat. Klienti tak budou stále volat stejnou základní adresu URL, ale požadavky jsou směrovány na více bran rozhraní API nebo BFF.

Všimněte si, že brány rozhraní API jsou front-endy nebo fasády zpřístupnění jenom služby, ale ne webové aplikace, které jsou obvykle mimo svůj rozsah. Brány rozhraní API navíc můžou některé interní mikroslužby skrýt.

Příchozí přenos dat se ale právě přesměrovává na požadavky HTTP, ale nepokouší se skrýt žádnou mikroslužbu nebo webovou aplikaci.

Mít v Kubernetes před webovými aplikacemi úroveň příchozího Nginxu a několik bran Ocelot API/BFF je ideální architekturou, jak je znázorněno v následujícím diagramu.

![Diagram znázorňující, jak úroveň příchozího připadá do prostředí AKS.](./media/implement-api-gateways-with-ocelot/eshoponcontainer-ingress-tier.png)

**Obrázek 6-41**. Úroveň příchozího přenosu v eShopOnContainers při nasazení do Kubernetes

Kubernetes příchozí připojení funguje jako reverzní proxy server pro veškerý provoz do aplikace, včetně webových aplikací, které jsou obvykle mimo rozsah brány rozhraní API. Když nasadíte eShopOnContainers do Kubernetes, zveřejňuje se v podstatě jenom pár služeb nebo koncových _bodů, a_to v podstatě následující seznam přípon v adresách URL:

- `/` webové aplikace SPA klienta
- `/webmvc` webové aplikace MVC klienta
- `/webstatus` pro webovou aplikaci klienta zobrazující stav/healthchecks
- `/webshoppingapigw` pro webové BFF a nákupní obchodní procesy
- `/webmarketingapigw` pro webové BFF a marketingové obchodní procesy
- `/mobileshoppingapigw` pro mobilní procesy BFF a nákup obchodních procesů
- `/mobilemarketingapigw` pro obchodní procesy Mobile BFF a marketing

Při nasazování do Kubernetes každá brána API Ocelot používá jiný soubor Configuration. JSON pro každý _pod_ spuštěným bránou rozhraní API. Tyto soubory "Configuration. JSON" jsou k dispozici připojením (původně pomocí skriptu Deploy. ps1) vytvořeného svazku založeného na _mapě konfigurace_ Kubernetes s názvem Ocelot. Každý kontejner připojí svůj související konfigurační soubor do složky kontejneru s názvem `/app/configuration`.

V souborech zdrojového kódu eShopOnContainers lze původní soubory "Configuration. JSON" najít v rámci `k8s/ocelot/` složky. Pro každou BFF/APIGateway existuje jeden soubor.

## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a>Další funkce pro křížové vyjmutí v bráně API Ocelot

Při použití brány Ocelot API jsou k dispozici další důležité funkce, které je potřeba prozkoumat a použít.

- **Zjišťování služby na straně klienta integrace Ocelot s Consul nebo Eureka**  \
  <https://ocelot.readthedocs.io/en/latest/features/servicediscovery.html>

- **Ukládání do mezipaměti na úrovni brány API**  \
  <https://ocelot.readthedocs.io/en/latest/features/caching.html>

- **Protokolování na úrovni brány API**  \
  <https://ocelot.readthedocs.io/en/latest/features/logging.html>

- **Kvalita služby (opakování a přerušení okruhů) na úrovni brány rozhraní API**  \
  <https://ocelot.readthedocs.io/en/latest/features/qualityofservice.html>

- **Omezení rychlosti**  \
  [https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html](https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )

> [!div class="step-by-step"]
> [Předchozí](background-tasks-with-ihostedservice.md)
> [Další](../microservice-ddd-cqrs-patterns/index.md)
