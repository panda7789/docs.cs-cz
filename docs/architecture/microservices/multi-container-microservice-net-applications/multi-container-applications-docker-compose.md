---
title: Definování vícekontejnerové aplikace pomocí docker-compose.yml
description: Jak určit složení mikroslužeb pro vícekontejnerovou aplikaci s docker-compose.yml.
ms.date: 01/30/2020
ms.openlocfilehash: 9143801fbbffbdc5b795a232b3333edf71f05c7c
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523655"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a>Definování vícekontejnerové aplikace pomocí docker-compose.yml

V této příručce byl soubor [docker-compose.yml](https://docs.docker.com/compose/compose-file/) představen v části [Krok 4. Definujte své služby v docker-compose.yml při vytváření aplikace Docker u více kontejnerů](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application). Existují však další způsoby, jak použít soubory docker-compose, které stojí za prozkoumání podrobněji.

Můžete například explicitně popsat, jak chcete nasadit aplikaci s více kontejnery v souboru docker-compose.yml. Volitelně můžete také popsat, jak budete vytvářet vlastní image Dockeru. (Vlastní inabité image Dockeru lze také sestavit pomocí cli Dockeru.)

V podstatě definujete každý z kontejnerů, které chcete nasadit, plus určité charakteristiky pro každé nasazení kontejneru. Jakmile máte soubor s popisem nasazení s více kontejnery, můžete nasadit celé řešení v jedné akci řízené příkazem příkazu příkazu příkazu příkazu příkazu příkazu příkazu příkazu příkazu příkazu příkazu příkazu příkazu příkazu cli [v dockeru](https://docs.docker.com/compose/overview/) nebo jej můžete nasadit transparentně z visual studia. V opačném případě budete muset použít Docker CLI k nasazení kontejneru `docker run` po kontejneru ve více krocích pomocí příkazu z příkazového řádku. Proto každá služba definovaná v docker-compose.yml musí zadat přesně jednu bitovou kopii nebo sestavení. Ostatní klíče jsou volitelné a jsou `docker run` podobné jejich protějšky příkazového řádku.

Následující kód YAML je definice možného globálního, ale jediného souboru docker-compose.yml pro ukázku eShopOnContainers. Toto není skutečný docker-compose soubor z eShopOnContainers. Místo toho se jedná o zjednodušenou a konsolidovanou verzi v jednom souboru, což není nejlepší způsob práce se soubory docker-compose, jak bude vysvětleno později.

```yml
version: '3.4'

services:
  webmvc:
    image: eshop/webmvc
    environment:
      - CatalogUrl=http://catalog-api
      - OrderingUrl=http://ordering-api
      - BasketUrl=http://basket-api
    ports:
      - "5100:80"
    depends_on:
      - catalog-api
      - ordering-api
      - basket-api

  catalog-api:
    image: eshop/catalog-api
    environment:
      - ConnectionString=Server=sqldata;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sqldata

  ordering-api:
    image: eshop/ordering-api
    environment:
      - ConnectionString=Server=sqldata;Database=Services.OrderingDb;User Id=sa;Password=your@password
    ports:
      - "5102:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sqldata

  basket-api:
    image: eshop/basket-api
    environment:
      - ConnectionString=sqldata
    ports:
      - "5103:80"
    depends_on:
      - sqldata

  sqldata:
    environment:
      - SA_PASSWORD=your@password
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"

  basketdata:
    image: redis
```

Kořenový klíč v tomto souboru jsou služby. Pod tímto klíčem definujete služby, které chcete `docker-compose up` nasadit a spustit při spuštění příkazu nebo při nasazení z Visual Studia pomocí tohoto souboru docker-compose.yml. V tomto případě má soubor docker-compose.yml více definovaných služeb, jak je popsáno v následující tabulce.

| Název služby | Popis |
|--------------|-------------|
| webmvc       | Kontejner včetně aplikace ASP.NET Core MVC, která spotřebovává mikroslužby z C na straně serveru\#|
| katalog-api  | Kontejner včetně mikroslužby katalogového ASP.NET základního webového rozhraní API |
| objednání-api | Kontejner včetně řazení ASP.NET základní webové rozhraní API mikroslužby |
| sqldata     | Kontejner se systémem SQL Server pro Linux, který drží databáze mikroslužeb |
| koš-api   | Kontejner s mikroslužbou basket ASP.NET Core Web API |
| data košíku  | Kontejner se spuštěnou službou mezipaměti REDIS s databází košíku jako mezipamětí REDIS |

### <a name="a-simple-web-service-api-container"></a>Jednoduchý kontejner rozhraní API webové služby

Zaměření na jeden kontejner, kontejner rozhraní API katalogu mikroslužby má přímočarou definici:

```yml
  catalog-api:
    image: eshop/catalog-api
    environment:
      - ConnectionString=Server=sqldata;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sqldata
```

Tato kontejnerizovaná služba má následující základní konfiguraci:

- Je založen na vlastní **image eshopu / katalog-api.** Z důvodu jednoduchosti neexistuje žádné sestavení: nastavení klíče v souboru. To znamená, že image musí být dříve sestaveny (s docker sestavení) nebo byly staženy (s příkazem docker pull) z libovolného registru Docker.

- Definuje proměnnou prostředí s názvem ConnectionString s připojovacím řetězcem, který má být použit rozhraním Entity Framework pro přístup k instanci serveru SQL Server, která obsahuje datový model katalogu. V tomto případě stejný kontejner SQL Server obsahuje více databází. Proto potřebujete méně paměti ve vývojovém počítači pro Docker. Můžete však také nasadit jeden kontejner serveru SQL Server pro každou databázi mikroslužeb.

- Název serveru SQL Server je **sqldata**, což je stejný název použitý pro kontejner, ve kterém je spuštěna instance SERVERU SQL Server pro Linux. To je výhodné; možnost používat tento překlad názvů (interní pro hostitele Dockeru) vyřeší síťovou adresu, takže nepotřebujete znát interní IP adresu pro kontejnery, ke které přistupujete z jiných kontejnerů.

Vzhledem k tomu, že připojovací řetězec je definován proměnnou prostředí, můžete tuto proměnnou nastavit prostřednictvím jiného mechanismu a v jiném čase. Můžete například nastavit jiný připojovací řetězec při nasazování do produkčního prostředí v konečných hostitelích nebo tím, že to uděláte z vašich kanálů CI/CD ve službě Azure DevOps Services nebo ve vámi upřednostňovaném systému DevOps.

- Zpřístupňuje port 80 pro interní přístup ke službě **rozhraní API katalogu** v rámci hostitele Dockeru. Hostitel je aktuálně virtuální počítač s Linuxem, protože je založen na image Dockeru pro Linux, ale místo toho můžete nakonfigurovat kontejner pro spuštění na bitové kopii systému Windows.

- Předá exponovaný port 80 na kontejneru na port 5101 na hostitelském počítači Dockeru (virtuální počítač SIF).

- Propojuje webovou službu se službou **sqldata** (instance SQL Serveru pro databázi Linuxu spuštěnou v kontejneru). Když zadáte tuto závislost, kontejner rozhraní API katalogu se nespustí, dokud již není spuštěn kontejner sqldata; To je důležité, protože rozhraní API katalogu musí mít nejprve zprovozněnou databázi serveru SQL Server. Tento druh závislosti kontejneru však není dost v mnoha případech, protože Docker kontroluje pouze na úrovni kontejneru. Někdy služba (v tomto případě SQL Server) stále není připraven, takže je vhodné implementovat logiku opakování s exponenciální backoff ve vašem mikroslužeb klienta. Tímto způsobem, pokud kontejner závislostí není připraven na krátkou dobu, aplikace bude stále odolné.

- Je nakonfigurován tak, aby umožňoval\_přístup k externím serverům: nastavení dalších hostitelů umožňuje přístup k externím serverům nebo počítačům mimo hostitele Dockeru (tj. mimo výchozí virtuální počítač s Linuxem, což je vývojový hostitel Dockeru), například místní instance SERVERU SQL Server ve vývojovém počítači.

Existují také další, pokročilejší `docker-compose.yml` nastavení, které budeme diskutovat v následujících částech.

### <a name="using-docker-compose-files-to-target-multiple-environments"></a>Použití souborů docker-compose k cílení na více prostředí

Soubory `docker-compose.*.yml` jsou definiční soubory a mohou být použity více infrastruktur, které chápou tento formát. Nejjednodušší nástroj je docker-compose příkaz.

Proto pomocí příkazu docker-compose můžete cílit na následující hlavní scénáře.

#### <a name="development-environments"></a>Vývojová prostředí

Při vývoji aplikací je důležité, aby bylo možné spustit aplikaci v izolovaném vývojovém prostředí. Příkaz příkazu příkazu příkazu příkazu příkazu příkazu příkazu příkazu příkazu příkazu příkazu příkazu cli v dockeru můžete použít k vytvoření tohoto prostředí nebo sady Visual Studio, která používá docker-compose pod kryty.

Soubor docker-compose.yml umožňuje konfigurovat a dokumentovat všechny závislosti služeb vaší aplikace (jiné služby, mezipaměť, databáze, fronty atd.). Pomocí příkazu cli docker-compose můžete vytvořit a spustit jeden nebo více kontejnerů pro každou závislost pomocí jediného příkazu (docker-compose up).

Soubory docker-compose.yml jsou konfigurační soubory interpretované modulem Docker, ale také slouží jako pohodlné soubory dokumentace o složení aplikace s více kontejnery.

#### <a name="testing-environments"></a>Testovací prostředí

Důležitou součástí procesu průběžného nasazení (CD) nebo průběžné integrace (CI) jsou testy částí a integrační testy. Tyto automatizované testy vyžadují izolované prostředí, takže nejsou ovlivněny uživateli nebo žádné jiné změny v datech aplikace.

S Docker Compose můžete vytvořit a zničit toto izolované prostředí velmi snadno v několika příkazech z příkazového řádku nebo skriptů, jako jsou následující příkazy:

```console
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml up -d
./run_unit_tests
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml down
```

#### <a name="production-deployments"></a>Produkční nasazení

Compose můžete také použít k nasazení do vzdáleného modulu Docker Engine. Typickým případem je nasazení do jedné instance hostitele Dockeru (jako je produkční virtuální počítač nebo server zřízený pomocí [Počítače dockeru).](https://docs.docker.com/machine/overview/)

Pokud používáte jiný orchestrator (Azure Service Fabric, Kubernetes atd.), budete muset přidat nastavení nastavení a nastavení konfigurace metadat, jako jsou v docker-compose.yml, ale ve formátu vyžadovaném jiným orchestrator.

V každém případě docker-compose je pohodlný nástroj a formát metadat pro vývoj, testování a produkční pracovní postupy, i když pracovní postup výroby se může lišit na orchestrátoru, který používáte.

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a>Použití více souborů docker-compose pro zpracování několika prostředí

Při cílení na různá prostředí byste měli použít více souborů pro skládání. To umožňuje vytvořit více variant konfigurace v závislosti na prostředí.

#### <a name="overriding-the-base-docker-compose-file"></a>Přepsání základního souboru docker-compose

Můžete použít jeden soubor docker-compose.yml jako ve zjednodušených příkladech uvedených v předchozích částech. To se však nedoporučuje pro většinu aplikací.

Ve výchozím nastavení compose čte dva soubory, docker-compose.yml a volitelný docker-compose.override.yml soubor. Jak je znázorněno na obrázku 6-11, když používáte Visual Studio a povolení podpory Dockeru, Visual Studio také vytvoří další soubor docker-compose.vs.debug.g.yml pro ladění aplikace, můžete se podívat na tento soubor ve složce obj\\Docker\\ v hlavní složce řešení.

![Snímek obrazovky se soubory v projektu vytvoření dockeru](./media/multi-container-applications-docker-compose/docker-compose-file-visual-studio.png)

**Obrázek 6-11**. soubory z docker-compose ve Visual Studiu 2019

**docker-compose** struktura souboru projektu:

- *.dockerignore* - používá se k ignorování souborů
- *docker-compose.yml* - používá se k komponovat mikroslužby
- *docker-compose.override.yml* - slouží ke konfiguraci prostředí mikroslužeb

Můžete upravit docker-compose soubory s libovolným editorem, jako je Visual Studio Code nebo Sublime, a spustit aplikaci pomocí příkazu docker-compose up.

Podle konvence obsahuje soubor docker-compose.yml základní konfiguraci a další statická nastavení. To znamená, že konfigurace služby by se neměla měnit v závislosti na prostředí nasazení, na které cílíte.

Soubor docker-compose.override.yml, jak naznačuje jeho název, obsahuje nastavení konfigurace, která přepíší základní konfiguraci, například konfiguraci, která závisí na prostředí nasazení. Můžete mít také více přepsání souborů s různými názvy. Přepsat soubory obvykle obsahují další informace, které aplikace potřebuje, ale specifické pro prostředí nebo nasazení.

#### <a name="targeting-multiple-environments"></a>Cílení na více prostředí

Typický případ použití je při definování více compose souborů, takže můžete cílit na více prostředí, jako je výroba, pracovní, CI nebo vývoj. Chcete-li tyto rozdíly podpořit, můžete vytvořit konfiguraci compose do více souborů, jak je znázorněno na obrázku 6-12.

![Diagram tří souborů docker-compose nastavených na přepsání základního souboru.](./media/multi-container-applications-docker-compose/multiple-docker-compose-files-override-base.png)

**Obrázek 6-12**. Více souborů docker-compose přepsání hodnot v základním souboru docker-compose.yml

Můžete kombinovat více docker-compose*.yml soubory pro zpracování různých prostředí. Začínáte se základním souborem docker-compose.yml. Tento základní soubor musí obsahovat základní nebo statické nastavení konfigurace, které se nemění v závislosti na prostředí. Například eShopOnContainers má následující docker-compose.yml soubor (zjednodušené s menším počtem služeb) jako základní soubor.

```yml
#docker-compose.yml (Base)
version: '3.4'
services:
  basket-api:
    image: eshop/basket-api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Basket/Basket.API/Dockerfile
    depends_on:
      - basketdata
      - identity-api
      - rabbitmq

  catalog-api:
    image: eshop/catalog-api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Catalog/Catalog.API/Dockerfile
    depends_on:
      - sqldata
      - rabbitmq

  marketing-api:
    image: eshop/marketing-api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Marketing/Marketing.API/Dockerfile
    depends_on:
      - sqldata
      - nosqldata
      - identity-api
      - rabbitmq

  webmvc:
    image: eshop/webmvc:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Web/WebMVC/Dockerfile
    depends_on:
      - catalog-api
      - ordering-api
      - identity-api
      - basket-api
      - marketing-api

  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest

  nosqldata:
    image: mongo

  basketdata:
    image: redis

  rabbitmq:
    image: rabbitmq:3-management

```

Hodnoty v základním souboru docker-compose.yml by se neměly měnit z důvodu různých cílových prostředí nasazení.

Pokud se například zaměříte na definici služby webmvc, můžete vidět, jak jsou tyto informace téměř stejné bez ohledu na to, na jaké prostředí se můžete zaměřit. Máte následující informace:

- Název služby: webmvc.

- Vlastní image kontejneru: eshop / webmvc.

- Příkaz k vytvoření vlastní image Dockeru označující, který dockerfile použít.

- Závislosti na jiných službách, takže tento kontejner nelze spustit, dokud ostatní kontejnery závislostí byly spuštěny.

Můžete mít další konfiguraci, ale důležité je, že v základním souboru docker-compose.yml chcete nastavit informace, které jsou běžné v různých prostředích. Potom v docker-compose.override.yml nebo podobné soubory pro produkční nebo pracovní, měli byste umístit konfiguraci, která je specifická pro každé prostředí.

Docker-compose.override.yml se obvykle používá pro vývojové prostředí, jako v následujícím příkladu z eShopOnContainers:

```yml
#docker-compose.override.yml (Extended config for DEVELOPMENT env.)
version: '3.4'

services:
# Simplified number of services here:

  basket-api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_REDIS_BASKET_DB:-basketdata}
      - identityUrl=http://identity-api
      - IdentityUrlExternal=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5105
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}
      - AzureServiceBusEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}

    ports:
      - "5103:80"

  catalog-api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_CATALOG_DB:-Server=sqldata;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word}
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_CATALOG_URL:-http://localhost:5202/api/v1/catalog/items/[0]/pic/}
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}
      - AzureStorageAccountName=${ESHOP_AZURE_STORAGE_CATALOG_NAME}
      - AzureStorageAccountKey=${ESHOP_AZURE_STORAGE_CATALOG_KEY}
      - UseCustomizationData=True
      - AzureServiceBusEnabled=False
      - AzureStorageEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
    ports:
      - "5101:80"

  marketing-api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_MARKETING_DB:-Server=sqldata;Database=Microsoft.eShopOnContainers.Services.MarketingDb;User Id=sa;Password=Pass@word}
      - MongoConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosqldata}
      - MongoDatabase=MarketingDb
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}
      - identityUrl=http://identity-api
      - IdentityUrlExternal=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5105
      - CampaignDetailFunctionUri=${ESHOP_AZUREFUNC_CAMPAIGN_DETAILS_URI}
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_MARKETING_URL:-http://localhost:5110/api/v1/campaigns/[0]/pic/}
      - AzureStorageAccountName=${ESHOP_AZURE_STORAGE_MARKETING_NAME}
      - AzureStorageAccountKey=${ESHOP_AZURE_STORAGE_MARKETING_KEY}
      - AzureServiceBusEnabled=False
      - AzureStorageEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5110:80"

  webmvc:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - PurchaseUrl=http://webshoppingapigw
      - IdentityUrl=http://10.0.75.1:5105
      - MarketingUrl=http://webmarketingapigw
      - CatalogUrlHC=http://catalog-api/hc
      - OrderingUrlHC=http://ordering-api/hc
      - IdentityUrlHC=http://identity-api/hc
      - BasketUrlHC=http://basket-api/hc
      - MarketingUrlHC=http://marketing-api/hc
      - PaymentUrlHC=http://payment-api/hc
      - SignalrHubUrl=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5202
      - UseCustomizationData=True
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5100:80"
  sqldata:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
  nosqldata:
    ports:
      - "27017:27017"
  basketdata:
    ports:
      - "6379:6379"
  rabbitmq:
    ports:
      - "15672:15672"
      - "5672:5672"

```

V tomto příkladu konfigurace přepsání vývoje zpřístupňuje některé porty hostiteli, definuje proměnné prostředí s adresami URL přesměrování a určuje připojovací řetězce pro vývojové prostředí. Tato nastavení jsou pouze pro vývojové prostředí.

Při spuštění `docker-compose up` (nebo spuštění z visual studia), příkaz přečte přepsání automaticky, jako by byly sloučení obou souborů.

Předpokládejme, že chcete jiný soubor Compose pro produkční prostředí s různými konfiguračními hodnotami, porty nebo připojovacími řetězci. Můžete vytvořit jiný soubor přepsání, například soubor pojmenovaný `docker-compose.prod.yml` s různými nastaveními a proměnnými prostředí. Tento soubor může být uložen v jiném úložišti Git nebo spravován a zabezpečen jiným týmem.

#### <a name="how-to-deploy-with-a-specific-override-file"></a>Jak nasadit s určitým přepsat soubor

Chcete-li použít více přepsání souborů nebo přepsat soubor s jiným názvem, můžete použít -f možnost s příkazem docker-compose a určit soubory. Vytvoří slučovací soubory v pořadí, v jakém jsou určeny na příkazovém řádku. Následující příklad ukazuje, jak nasadit s přepsat soubory.

```console
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a>Použití proměnných prostředí v souborech docker-compose

Je vhodné, zejména v produkčním prostředí, aby bylo možné získat informace o konfiguraci z proměnných prostředí, jak jsme ukázali v předchozích příkladech. Proměnnou prostředí můžete odkazovat na soubor y docker-compose pomocí syntaxe ${MY\_VAR}. Následující řádek ze souboru docker-compose.prod.yml ukazuje, jak odkazovat na hodnotu proměnné prostředí.

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

Proměnné prostředí jsou vytvářeny a inicializovány různými způsoby v závislosti na hostitelském prostředí (Linux, Windows, cloudový cluster atd.). Pohodlným přístupem je však použití souboru ENV. Soubory docker-compose podporují deklarování výchozích proměnných prostředí v souboru ENV. Tyto hodnoty pro proměnné prostředí jsou výchozí hodnoty. Ale mohou být přepsány hodnotami, které jste definovali v každém z vašich prostředí (hostitelského operačního systému nebo proměnných prostředí z clusteru). Tento soubor ENV umístíte do složky, ze které je příkaz docker-compose proveden.

Následující příklad ukazuje soubor ENV, jako je soubor [ENV](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) pro aplikaci eShopOnContainers.

```sh
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

Docker-compose očekává, že každý řádek v souboru \<ENV bude v hodnotě\>=\<\>proměnné formátu .

Hodnoty nastavené v prostředí za běhu vždy přepíší hodnoty definované uvnitř souboru ENV. Podobným způsobem hodnoty předané prostřednictvím argumentů příkazového řádku také přepíší výchozí hodnoty nastavené v souboru ENV.

#### <a name="additional-resources"></a>Další zdroje

- **Přehled dockerového komponu** \
    <https://docs.docker.com/compose/overview/>

- **Více compose souborů** \
    [https://docs.docker.com/compose/extends/\#multiple-compose-files](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a>Vytváření optimalizovaných ASP.NET image Core Dockeru

Pokud zkoumáte Docker a .NET Core na zdroje na Internetu, najdete Dockerfiles, které ukazují jednoduchost vytváření image Docker u kopírování zdroje do kontejneru. Tyto příklady naznačují, že pomocí jednoduché konfigurace můžete mít image Dockeru s prostředím zabaleným s vaší aplikací. Následující příklad ukazuje jednoduchý Dockerfile v této žíře.

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/sdk:3.1
WORKDIR /app
ENV ASPNETCORE_URLS http://+:80
EXPOSE 80
COPY . .
RUN dotnet restore
ENTRYPOINT ["dotnet", "run"]
```

Dockerfile jako je tento bude fungovat. Můžete však podstatně optimalizovat obrázky, zejména produkční obrázky.

V kontejneru a mikroslužeb modelu neustále spouštíkontejnery. Typický způsob použití kontejnerů nerestartuje kontejner spánku, protože kontejner je na jedno použití. Orchestratory (jako Kubernetes a Azure Service Fabric) jednoduše vytvořit nové instance ibi. To znamená, že budete muset optimalizovat předkompilací aplikace, když je sestavena, takže proces vytváření instancí bude rychlejší. Při spuštění kontejneru by měl být připraven ke spuštění. Neměli byste obnovovat a kompilovat za běhu, pomocí `dotnet restore` a `dotnet build` příkazy z dotnet CLI, které, jak vidíte v mnoha blogu o .NET Core a Docker.

Tým .NET odvádí důležitou práci, aby vytvořil rozhraní .NET Core a ASP.NET Core jako rámec optimalizovaný pro kontejner. Nejen, že je .NET Core lehký rámec s malou paměťovou stopu; tým se zaměřil na optimalizované image Dockeru pro tři hlavní scénáře a publikoval je v registru Docker Hub u *dotnet/core*, počínaje verzí 2.1:

1. **Vývoj**: Kde je prioritou schopnost rychle iterate a ladění změn a kde velikost je sekundární.

2. **Sestavení**: Prioritou je kompilace aplikace a zahrnuje binární soubory a další závislosti pro optimalizaci binárních souborů.

3. **Výroba**: Kde je fokus rychlé nasazení a spuštění kontejnerů, takže tyto obrázky jsou omezeny na binární soubory a obsah potřebný ke spuštění aplikace.

K dosažení tohoto cíle poskytuje tým .NET čtyři základní varianty v [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) (v Docker Hubu):

1. **sdk**: pro vývoj a sestavení scénářů
1. **aspnet**: pro ASP.NET produkční scénáře
1. **runtime**: pro produkční scénáře rozhraní .NET
1. **runtime-deps**: pro produkční scénáře [samostatných aplikací](../../../core/deploying/index.md#publish-self-contained).

Pro rychlejší spuštění, runtime obrázky také\_automaticky nastavit aspnetcore adresy URL na port 80 a použít Ngen vytvořit nativní image cache sestavení.

#### <a name="additional-resources"></a>Další zdroje

- **Vytváření optimalizovaných imitovaných imitacích Dockeru s ASP.NET jádrem**  
  <https://docs.microsoft.com/archive/blogs/stevelasker/building-optimized-docker-images-with-asp-net-core>

- **Vytváření imagí Dockeru pro aplikace .NET Core**  
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

> [!div class="step-by-step"]
> [Předchozí](data-driven-crud-microservice.md)
> [další](database-server-container.md)
