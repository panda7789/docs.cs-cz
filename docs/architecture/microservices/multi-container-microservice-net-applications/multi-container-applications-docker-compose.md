---
title: Definování vícekontejnerové aplikace pomocí docker-compose.yml
description: Jak určit složení mikroslužeb pro aplikaci s více kontejnery pomocí Docker-Compose. yml.
ms.date: 10/02/2018
ms.openlocfilehash: 02db27feb1320d8b9c6823b8f9ef51c2ddf9791c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737084"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a>Definování vícekontejnerové aplikace pomocí docker-compose.yml

V tomto průvodci byl soubor [Docker-Compose. yml](https://docs.docker.com/compose/compose-file/) představený v části [Krok 4. V Docker-Compose. yml definujte své služby při sestavování aplikace Docker pro více kontejnerů](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application). Existují však další způsoby, jak použít soubory Docker – skládání, které jsou podrobněji prozkoumání.

Můžete například explicitně popsat, jak chcete v souboru Docker-Compose. yml nasadit aplikaci s více kontejnery. Volitelně můžete také popsat, jak budete vytvářet vlastní image Docker. (Vlastní image Docker můžete také vytvořit pomocí Docker CLI.)

V podstatě definujete každý z kontejnerů, které chcete nasadit, a některé vlastnosti pro každé nasazení kontejneru. Jakmile budete mít soubor s popisem nasazení s více kontejnery, můžete nasadit celé řešení v rámci jedné akce Orchestrované příkazem [Docker-sestavit](https://docs.docker.com/compose/overview/) rozhraní příkazového řádku nebo ho můžete transparentně nasadit ze sady Visual Studio. V opačném případě byste k nasazení kontejnerů do kontejneru do více kroků použili příkaz Docker CLI pomocí příkazu `docker run` z příkazového řádku. Proto každá služba definovaná v Docker-Compose. yml musí určovat přesně jeden obrázek nebo sestavení. Další klíče jsou volitelné a jsou podobné jejich `docker run` protějškům příkazového řádku.

Následující kód YAML je definicí možného souboru Global, ale Single Docker-Compose. yml pro ukázku eShopOnContainers. Nejedná se o skutečný soubor Docker-skládání z eShopOnContainers. Místo toho je tato zjednodušená a konsolidovaná verze v jednom souboru, což není nejlepším způsobem, jak pracovat se soubory Docker-pro vytváření, jak bude vysvětleno později.

```yml
version: '3.4'

services:
  webmvc:
    image: eshop/webmvc
    environment:
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
      - BasketUrl=http://basket.api
    ports:
      - "5100:80"
    depends_on:
      - catalog.api
      - ordering.api
      - basket.api

  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=sql.data;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    environment:
      - ConnectionString=Server=sql.data;Database=Services.OrderingDb;User Id=sa;Password=your@password
    ports:
      - "5102:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data

  basket.api:
    image: eshop/basket.api
    environment:
      - ConnectionString=sql.data
    ports:
      - "5103:80"
    depends_on:
      - sql.data

  sql.data:
    environment:
      - SA_PASSWORD=your@password
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"

  basket.data:
    image: redis
```

Kořenový klíč v tomto souboru je služby. V tomto klíči definujete služby, které chcete nasadit a spustit při spuštění příkazu `docker-compose up`, nebo při nasazení ze sady Visual Studio pomocí tohoto souboru Docker-Compose. yml. V tomto případě má soubor Docker-Compose. yml definováno více služeb, jak je popsáno v následující tabulce.

| Název služby | Popis |
|--------------|-------------|
| webmvc       | Kontejner včetně aplikace ASP.NET Core MVC využívající mikroslužby na straně serveru C\#|
| catalog.api  | Kontejner včetně služby Catalog ASP.NET Core mikroslužby webového rozhraní API |
| objednávání. API | Kontejner, včetně pořadí ASP.NET Core mikroslužby webového rozhraní API |
| sql.data     | Kontejner se spuštěným SQL Server pro Linux, který uchovává databáze mikroslužeb. |
| basket.api   | Kontejner s ASP.NET Core mikroslužba webového rozhraní API pro koš |
| basket.data  | Kontejner, ve kterém je spuštěná služba REDIS cache, s databází košíku jako REDIS cache |

### <a name="a-simple-web-service-api-container"></a>Jednoduchý kontejner rozhraní API pro webové služby

Zaměření na jeden kontejner, Catalog. API Container-mikroslužba má jasné definice:

```yml
  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=sql.data;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data
```

Tato služba kontejneru má následující základní konfiguraci:

- Je založen na vlastní imagi eshop/Catalog. API. V zájmu zjednodušení není v souboru žádné nastavení pro sestavení: klíče. To znamená, že bitová kopie musí být dřív sestavená (pomocí buildu Docker) nebo se stáhla (pomocí příkazu docker pull) z libovolného registru Docker.

- Definuje proměnnou prostředí s názvem ConnectionString s připojovacím řetězcem, který má být použit Entity Framework pro přístup k instanci SQL Server, která obsahuje model dat katalogu. V takovém případě stejný kontejner SQL Server drží více databází. Proto potřebujete na svém vývojovém počítači méně paměti pro Docker. Můžete ale také nasadit jeden kontejner SQL Server pro každou databázi mikroslužeb.

- Název SQL Server je SQL. data, což je stejný název, který se používá pro kontejner, na kterém je spuštěná instance SQL Server pro Linux. To je pohodlné; možnost použít toto rozlišení názvu (interní pro hostitele Docker) vyřeší síťovou adresu, takže nemusíte znát interní IP adresy pro kontejnery, které přistupujete z jiných kontejnerů.

Vzhledem k tomu, že připojovací řetězec je definován proměnnou prostředí, můžete tuto proměnnou nastavit pomocí jiného mechanismu a v jinou dobu. Můžete například nastavit jiný připojovací řetězec při nasazování do produkčního prostředí v konečných hostitelích nebo z vašich kanálů CI/CD v Azure DevOps Services nebo preferovaného systému DevOps.

- Zpřístupňuje port 80 pro interní přístup ke službě Catalog. API v rámci hostitele Docker. Hostitelem je aktuálně virtuální počítač se systémem Linux, protože je založen na imagi Docker pro Linux, ale můžete nastavit, aby se kontejner spouštěl v imagi Windows.

- Přepošle vystavený port 80 na kontejner na port 5101 na hostitelském počítači Docker (virtuální počítač Linux).

- Propojí webovou službu s SQL. Data Service (instance SQL Server pro databázi Linux spuštěnou v kontejneru). Když zadáte tuto závislost, kontejner Catalog. API se nespustí, dokud se už nespustí kontejner SQL. data; To je důležité, protože Catalog. API vyžaduje, aby se nejdřív nastavila a běžela databáze SQL Server. Tento druh závislosti kontejneru ale v mnoha případech není dostatečný, protože kontroly Docker jsou jenom na úrovni kontejneru. Někdy může být služba (v tomto případě SQL Server) stále připravená, takže je vhodné implementovat logiku opakování pomocí exponenciálního omezení rychlostiu v klientských mikroslužbách. To znamená, že pokud kontejner závislostí není připravený na krátkou dobu, bude aplikace stále odolná.

- Je nakonfigurovaná tak, aby povolovala přístup k externím serverům: nastavení další\_hostitelé vám umožní přístup k externím serverům nebo počítačům mimo hostitele Docker (to znamená, že se nachází mimo výchozí virtuální počítač Linux, který je hostitelem Docker hosta), jako je například místní instance SQL Server na vývojovém počítači.

K dispozici jsou také další pokročilá nastavení Docker-Compose. yml, která budeme projednávat v následujících oddílech.

### <a name="using-docker-compose-files-to-target-multiple-environments"></a>Použití souborů Docker-skládání k sestavení více prostředí

Soubory Docker-Compose. yml jsou definiční soubory a mohou být používány více infrastrukturami, které tento formát porozuměly. Nejpřímější nástroj je příkaz Docker-skládání.

Proto pomocí příkazu Docker-skládání můžete cílit na následující hlavní scénáře.

#### <a name="development-environments"></a>Vývojová prostředí

Při vývoji aplikací je důležité, aby bylo možné spustit aplikaci v izolovaném vývojovém prostředí. K vytvoření prostředí můžete použít příkaz Docker-Create CLI, nebo použít aplikaci Visual Studio, která v rámci pokrývá používá Docker-skládání.

Soubor Docker-Compose. yml umožňuje konfigurovat a zdokumentovat všechny závislosti služby vaší aplikace (další služby, mezipaměť, databáze, fronty atd.). Pomocí příkazu Docker-Create CLI můžete vytvořit a spustit jeden nebo více kontejnerů pro každou závislost jediným příkazem (Docker – sestavit).

Soubory Docker-Compose. yml jsou konfigurační soubory interpretované modulem Docker, ale také slouží jako praktické dokumentační soubory o složení aplikace s více kontejnery.

#### <a name="testing-environments"></a>Testovací prostředí

Důležitou součástí jakéhokoli procesu průběžného nasazování (CD) nebo průběžná integrace (CI) jsou testy jednotek a integrační testy. Tyto automatizované testy vyžadují izolované prostředí, aby na ně neovlivnili uživatelé ani žádné jiné změny v datech aplikace.

Pomocí Docker Compose můžete toto izolované prostředí jednoduše vytvořit a zničit v několika příkazech z příkazového řádku nebo skriptů, podobně jako v následujících příkazech:

```console
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml up -d
./run_unit_tests
docker-compose -f docker-compose.yml -f docker-compose.test.override.yml down
```

#### <a name="production-deployments"></a>Produkční nasazení

K nasazení na vzdálený modul Docker můžete použít také nástroj vytvořit. Typickým případem je nasazení na jednu instanci hostitele Docker (jako produkční virtuální počítač nebo server zřízený pomocí [Docker Machine](https://docs.docker.com/machine/overview/)).

Pokud používáte jakýkoli jiný produkt Orchestrator (Azure Service Fabric, Kubernetes atd.), může být nutné přidat nastavení konfigurace nastavení a metadat, například v Docker-Compose. yml, ale ve formátu požadovaném jiným nástrojem Orchestrator.

V každém případě je Docker-napsat pohodlný nástroj a formát metadat pro pracovní postupy pro vývoj, testování a produkční prostředí, i když se produkční pracovní postup může lišit v rámci produktu Orchestrator, který používáte.

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a>Použití několika souborů Docker-skládání pro zpracování několika prostředí

Při cílení na různá prostředí byste měli použít více souborů pro vytváření. To vám umožní vytvořit několik variant konfigurace v závislosti na prostředí.

#### <a name="overriding-the-base-docker-compose-file"></a>Přepsání základního souboru Docker-skládání

Můžete použít jeden soubor Docker-Compose. yml jako v zjednodušených příkladech uvedených v předchozích částech. To však nedoporučujeme pro většinu aplikací.

Ve výchozím nastavení čte čtení dva soubory, Docker-Compose. yml a nepovinný soubor Docker-Compose. override. yml. Jak je znázorněno na obrázku 6-11, pokud používáte aplikaci Visual Studio a povolíte podporu Docker, sada Visual Studio také vytvoří další soubor Docker-Compose. vs. Debug. g. yml pro ladění aplikace. můžete se podívat na tento soubor ve složce obj\\Docker\\ v hlavní složce řešení.

![Snímek obrazovky se soubory v projektu Docker pro sestavení.](./media/multi-container-applications-docker-compose/docker-compose-file-visual-studio.png)

**Obrázek 6-11**. soubory Docker – sestavení v aplikaci Visual Studio 2017

**Docker – sestavení** struktury souborů projektu:

* *. dockerignore* – používá se k ignorování souborů
* *Docker-Compose. yml* – slouží k vytváření mikroslužeb
* *Docker-Compose. override. yml* – používá se ke konfiguraci prostředí mikroslužeb.

Soubory Docker můžete upravit pomocí libovolného editoru, například Visual Studio Code nebo subvápna, a aplikaci spustit pomocí příkazu Docker-sestavit.

Podle konvence obsahuje soubor Docker-Compose. yml základní konfiguraci a jiné statické nastavení. To znamená, že se konfigurace služby nesmí měnit v závislosti na prostředí nasazení, které cílíte.

Soubor Docker-Compose. override. yml, jak je navržen názvem, obsahuje nastavení konfigurace, které přepíše základní konfiguraci, například konfiguraci, která závisí na prostředí nasazení. Můžete mít také více souborů přepsání s různými názvy. Soubory přepsání obvykle obsahují další informace, které aplikace potřebuje, ale specifické pro prostředí nebo nasazení.

#### <a name="targeting-multiple-environments"></a>Cílení na více prostředí

Typický případ použití je při definování více souborů pro vytváření, aby bylo možné cílit na více prostředí, jako je výroba, příprava, CI nebo vývoj. Pro podporu těchto rozdílů můžete svou konfiguraci vytváření rozdělit do několika souborů, jak je znázorněno na obrázku 6-12.

![Diagram tří souborů Docker-skládání nastavených na přepsání základního souboru](./media/multi-container-applications-docker-compose/multiple-docker-compose-files-override-base.png)

**Obrázek 6-12**. Více souborů Docker – skládáním hodnot do základního souboru Docker-Compose. yml

Můžete zkombinovat více souborů Docker-Compose*. yml pro zpracování různých prostředí. Začnete se základním souborem Docker-Compose. yml. Tento základní soubor musí obsahovat základní nebo statické nastavení konfigurace, které se v závislosti na prostředí nemění. EShopOnContainers má například následující soubor Docker-Compose. yml (zjednodušený s méně službami) jako základní soubor.

```yml
#docker-compose.yml (Base)
version: '3.4'
services:
  basket.api:
    image: eshop/basket.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Basket/Basket.API/Dockerfile
    depends_on:
      - basket.data
      - identity.api
      - rabbitmq

  catalog.api:
    image: eshop/catalog.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Catalog/Catalog.API/Dockerfile
    depends_on:
      - sql.data
      - rabbitmq

  marketing.api:
    image: eshop/marketing.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Marketing/Marketing.API/Dockerfile
    depends_on:
      - sql.data
      - nosql.data
      - identity.api
      - rabbitmq

  webmvc:
    image: eshop/webmvc:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Web/WebMVC/Dockerfile
    depends_on:
      - catalog.api
      - ordering.api
      - identity.api
      - basket.api
      - marketing.api

  sql.data:
    image: microsoft/mssql-server-linux:2017-latest

  nosql.data:
    image: mongo

  basket.data:
    image: redis

  rabbitmq:
    image: rabbitmq:3-management

```

Hodnoty v základním souboru Docker-Compose. yml by se neměly měnit z důvodu různých cílových prostředí nasazení.

Pokud se zaměříte na definici služby webmvc, můžete například zjistit, jak jsou tyto informace mnohem stejné bez ohledu na to, na jaké prostředí budete chtít cílit. Máte následující informace:

- Název služby: webmvc.

- Vlastní image kontejneru: eshop/webmvc.

- Příkaz pro sestavení vlastní image Docker, která určuje, který souboru Dockerfile se má použít.

- Závislosti na jiných službách, takže tento kontejner se nespustí, dokud se nespustí ostatní kontejnery závislostí.

Můžete mít další konfiguraci, ale důležitým bodem je, že v základním souboru Docker-Compose. yml budete chtít jenom nastavit informace, které jsou v různých prostředích společné. Pak v Docker-Compose. override. yml nebo podobné soubory pro produkční prostředí nebo přípravu byste měli umístit konfiguraci, která je specifická pro každé prostředí.

Obvykle se pro vývojové prostředí používá Docker-Compose. override. yml, jako v následujícím příkladu z eShopOnContainers:

```yml
#docker-compose.override.yml (Extended config for DEVELOPMENT env.)
version: '3.4'

services:
# Simplified number of services here:

  basket.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_REDIS_BASKET_DB:-basket.data}
      - identityUrl=http://identity.api
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

  catalog.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_CATALOG_DB:-Server=sql.data;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word}
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

  marketing.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_MARKETING_DB:-Server=sql.data;Database=Microsoft.eShopOnContainers.Services.MarketingDb;User Id=sa;Password=Pass@word}
      - MongoConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosql.data}
      - MongoDatabase=MarketingDb
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}
      - identityUrl=http://identity.api
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
      - CatalogUrlHC=http://catalog.api/hc
      - OrderingUrlHC=http://ordering.api/hc
      - IdentityUrlHC=http://identity.api/hc
      - BasketUrlHC=http://basket.api/hc
      - MarketingUrlHC=http://marketing.api/hc
      - PaymentUrlHC=http://payment.api/hc
      - SignalrHubUrl=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5202
      - UseCustomizationData=True
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5100:80"
  sql.data:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
  nosql.data:
    ports:
      - "27017:27017"
  basket.data:
    ports:
      - "6379:6379"
  rabbitmq:
    ports:
      - "15672:15672"
      - "5672:5672"

```

V tomto příkladu konfigurace přepsání vývoje zpřístupňuje některé porty hostiteli, definuje proměnné prostředí s adresami URL pro přesměrování a určuje připojovací řetězce pro vývojové prostředí. Tato nastavení jsou pouze pro vývojové prostředí.

Když spustíte `docker-compose up` (nebo ho spustíte ze sady Visual Studio), příkaz automaticky přečte přepsání, jako kdyby byly oba soubory sloučeny.

Předpokládejme, že budete chtít jiný soubor pro vytváření v produkčním prostředí s různými hodnotami konfigurace, porty nebo připojovacími řetězci. Můžete vytvořit další soubor přepsání, jako je například soubor s názvem `docker-compose.prod.yml` s různými nastaveními a proměnnými prostředí. Tento soubor může být uložený v jiném úložišti Git nebo spravovaný a zabezpečený jiným týmem.

#### <a name="how-to-deploy-with-a-specific-override-file"></a>Postup nasazení s konkrétním souborem přepsání

Chcete-li použít více souborů přepsání nebo přepsat soubor s jiným názvem, můžete použít možnost-f s příkazem Docker-skládání a zadat soubory. Vytváření sloučí soubory v pořadí, v jakém jsou zadány na příkazovém řádku. Následující příklad ukazuje, jak nasadit soubory s přepsáním.

```console
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a>Použití proměnných prostředí v Docker – skládání souborů

V produkčních prostředích je to vhodné, zejména v produkčním prostředí, aby bylo možné získat informace o konfiguraci z proměnných prostředí, jak jsme ukázali v předchozích příkladech. Na proměnnou prostředí v souborech Docker můžete odkazovat pomocí syntaxe $ {MY\_VAR}. Následující řádek ze souboru Docker-Compose. prod. yml ukazuje, jak odkazovat na hodnotu proměnné prostředí.

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

Proměnné prostředí jsou vytvářeny a inicializovány různými způsoby v závislosti na hostitelském prostředí (Linux, Windows, cloudovém clusteru atd.). Pohodlný přístup ale je použít soubor. env. Soubory Docker-skládání podporují deklaraci výchozích proměnných prostředí v souboru. env. Tyto hodnoty pro proměnné prostředí jsou výchozí hodnoty. Ale můžou být přepsány hodnotami, které jste pravděpodobně definovali v každém z vašich prostředí (hostitelský operační systém nebo proměnné prostředí z vašeho clusteru). Tento soubor. env umístíte do složky, ve které je spuštěný příkaz Docker-skládání.

Následující příklad ukazuje soubor. ENV, jako je soubor [. env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) pro aplikaci eShopOnContainers.

```env
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

Docker-Format očekává, že každý řádek v souboru. env bude ve formátu \<proměnná\>=\<Value\>.

Všimněte si, že hodnoty nastavené v běhovém prostředí vždy přepisují hodnoty definované v souboru. env. Podobným způsobem hodnoty předané pomocí argumentů příkazu příkazového řádku přepisují také výchozí hodnoty nastavené v souboru. env.

#### <a name="additional-resources"></a>Další materiály a zdroje informací

- **Přehled Docker Compose** \
    <https://docs.docker.com/compose/overview/>

- **Více souborů pro vytváření** \
    [https://docs.docker.com/compose/extends/\#multiple-compose-files](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a>Vytváření optimalizovaných imagí ASP.NET Core Docker

Pokud zkoumáte Docker a .NET Core na zdrojích na internetu, najdete fázemi, které demonstrují jednoduchost vytváření imagí Docker zkopírováním zdroje do kontejneru. Tyto příklady naznačují, že pomocí jednoduché konfigurace můžete mít image Docker s prostředím zabaleným do aplikace. Následující příklad ukazuje jednoduchý souboru Dockerfile v tomto podmnožině.

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/sdk:2.2
WORKDIR /app
ENV ASPNETCORE_URLS http://+:80
EXPOSE 80
COPY . .
RUN dotnet restore
ENTRYPOINT ["dotnet", "run"]
```

Souboru Dockerfile jako to bude fungovat. Vaše image ale můžete významně optimalizovat, zejména v produkčních bitových kopiích.

V modelu kontejneru a mikroslužeb jsou stále spouštěny kontejnery. Typický způsob použití kontejnerů nerestartuje kontejner v režimu spánku, protože kontejner je na jedno použití. Orchestrace (jako Kubernetes a Azure Service Fabric) jednoduše vytvoří nové instance imagí. To znamená, že je nutné optimalizovat sestavením aplikace, když je sestavena, takže proces vytváření instancí bude rychlejší. Po spuštění kontejneru by měl být připraven ke spuštění. Za běhu byste neměli obnovovat a kompilovat pomocí příkazů `dotnet restore` a `dotnet build` z příkazu dotnet CLI, který se zobrazí v mnoha blogových příspěvcích o .NET Core a Docker.

Tým .NET prováděl důležitou práci pro zajištění .NET Core a ASP.NET Core architektury optimalizované pro kontejnery. Jenom rozhraní .NET Core a odlehčené rozhraní s malými nároky na paměť; tým se zaměřuje na optimalizované image Docker pro tři hlavní scénáře a publikovaly je v registru Docker Hub v *dotnet/Core*, počínaje verzí 2,1:

1. **Vývoj**: kde priorita je schopnost rychle iterovat a ladit změny a kde je velikost sekundární.

2. **Sestavení**: priorita kompiluje aplikaci a zahrnuje binární soubory a další závislosti pro optimalizaci binárních souborů.

3. **Produkční**: kde se zaměřuje na rychlé nasazení a spuštění kontejnerů, takže tyto image jsou omezené na binární soubory a obsah potřebný ke spuštění aplikace.

Za tímto účelem tým .NET poskytuje čtyři základní varianty v [dotnet/Core](https://hub.docker.com/_/microsoft-dotnet-core/) (v Docker Hub):

1. **SDK**: pro scénáře vývoje a sestavování
1. **ASPNET**: pro produkční scénáře ASP.NET
1. **runtime**: pro produkční scénáře .NET
1. **runtime-DEPS**: pro produkční scénáře aplikací, které jsou [samostatně obsaženy](../../../core/deploying/index.md#self-contained-deployments-scd).

V případě rychlejšího spuštění jsou bitové kopie za běhu také automaticky nastaveny\_adresy URL aspnetcore na port 80 a použít Ngen k vytvoření mezipaměti nativní bitové kopie sestavení.

#### <a name="additional-resources"></a>Další materiály a zdroje informací

- **Vytváření optimalizovaných imagí Docker pomocí ASP.NET Core**  
  <https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/>

- **Vytváření imagí Dockeru pro aplikace .NET Core**  
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

> [!div class="step-by-step"]
> [Předchozí](data-driven-crud-microservice.md)
> [Další](database-server-container.md)
