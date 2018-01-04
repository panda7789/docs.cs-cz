---
title: "Definování vaší aplikace s více kontejnerů pomocí docker-compose.yml"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Definování vaší aplikace s více kontejnerů pomocí docker-compose.yml"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/30/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c4fed5c7ba5c2048d103f22bd2b463c143013280
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a>Definování vaší aplikace s více kontejnerů pomocí docker-compose.yml 

V této příručce [docker-compose.yml](https://docs.docker.com/compose/compose-file/) souboru byla zavedena v části [kroku 4. Definování vašim službám v docker-compose.yml při vytvoření aplikace s více kontejner Docker](#step4_define_svcs_in_docker_compose_yml). Existují však další způsoby, jak používat docker-compose soubory, které je vhodné využít podrobněji.

Můžete například explicitně popisují, jak chcete nasadit aplikace s více kontejneru v soubor docker-compose.yml. Volitelně můžete také popisují, jak budete k vytváření vlastních bitových kopií Docker. (Imagí Dockeru vlastní také se dají vytvářet pomocí rozhraní příkazového řádku Dockeru.)

V podstatě můžete definovat každý z kontejnerů, které chcete nasadit plus určité charakteristické vlastnosti pro každý kontejner nasazení. Až budete mít soubor popisu nasazení několika kontejnerů, můžete nasadit celé řešení v rámci jedné akce řízená [docker compose až](https://docs.docker.com/compose/overview/) příkaz rozhraní příkazového řádku, nebo můžete nasadit transparentně ze sady Visual Studio. Jinak by budete muset použít rozhraní příkazového řádku Dockeru nasazení kontejneru podle kontejneru v několika krocích pomocí docker, spusťte příkaz z příkazového řádku. Každá služba definované v docker-compose.yml proto musíte zadat přesně jednu bitovou kopii nebo sestavení. Další klíče jsou volitelné a je obdobou jejich docker spuštění příkazového řádku svými protějšky.

Následující kód YAML je definice možné globální ale jeden soubor docker-compose.yml pro ukázku eShopOnContainers. Toto není soubor skutečné docker-compose z eShopOnContainers. Místo toho je jednodušší a konsolidované verze v jednom souboru, který není nejlepší způsob, jak pracovat s docker tvoří soubory, jak bude vysvětleno později.

```yml
version: '2'

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

Kořenový klíč v tomto souboru se služeb. Pod tímto klíčem definujete služby, kterou chcete nasadit a spustit při spuštění docker compose příkaz nebo při nasazení ze sady Visual Studio pomocí tento soubor docker-compose.yml. V tomto případě soubor docker-compose.yml má více služeb definovat, jak je popsáno v následujícím seznamu.

-   webmvc kontejneru, včetně aplikace ASP.NET MVC základní využívání mikroslužeb ze serverové C\#

-   CATALOG.API včetně mikroslužbu webového rozhraní API pro jádro ASP.NET katalog kontejner

-   Ordering.API kontejneru, včetně mikroslužbu řazení rozhraní ASP.NET Web API Core

-   SQL.data kontejneru systémem SQL Server pro Linux, která uchovává mikroslužeb databáze

-   basket.API kontejner s mikroslužbu košík ASP.NET Core webového rozhraní API

-   basket.data kontejneru službu REDIS cache s databázi košík jako mezipaměti REDIS

### <a name="a-simple-web-service-api-container"></a>Kontejner jednoduché rozhraní API webové služby

Zaměřený na jediný kontejner, catalog.api kontejneru mikroslužbu má přehledné definice:

```yml
  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=catalog.data;Initial Catalog=CatalogData;User Id=sa;Password=your@password
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

Tato služba kontejnerizované má následující základní konfiguraci:

-   Je založena na bitovou kopii vlastní eshop/catalog.api. Pro saké na jednoduchost, neexistuje žádné sestavení: klíč nastavení v souboru. To znamená, že bitovou kopii musí mít byla dříve vytvořená (pomocí docker sestavení) nebo byly staženy (pomocí příkazu docker vyžádání obsahu) z jakékoli Docker registru.

-   Definuje proměnnou prostředí s názvem připojovacího řetězce připojovacím řetězcem, který bude používat pro přístup k instanci systému SQL Server, který obsahuje datový model katalogu Entity Framework. V takovém případě stejnému kontejneru systému SQL Server je podržíte více databází. Proto musíte méně paměti v počítači pro vývoj pro Docker. Můžete však také nasadit jednoho kontejneru typu SQL Server pro každou databázi mikroslužby.

-   Název systému SQL Server je sql.data, což je stejný název používá pro kontejner, ve kterém běží instance systému SQL Server pro Linux. To je vhodné; bude možné použít tento překlad (interní Docker hostitele) bude vyřešen síťová adresa, takže není nutné znát interní IP adresu pro kontejnerů, které se připojujete z jiných kontejnerů.

Protože připojovací řetězec je definované proměnné prostředí, můžete tuto proměnnou nastavit přes jiný mechanismus a v jinou dobu. Například můžete nastavit různé připojovací řetězec při nasazení do produkčního prostředí v posledním hostitelů nebo proveďte z kanály CI/CD služby VSTS nebo upřednostňovaný DevOps systému.

-   Zpřístupňuje port 80 pro interní přístup ke službě catalog.api v rámci Docker hostitele. Hostitel je aktuálně virtuálního počítače s Linuxem, protože je založena na bitovou kopii Docker pro Linux, ale může nakonfigurovat kontejner, aby místo toho spustit na bitovou kopii systému Windows.

-   Předává zveřejněné port 80 kontejneru na port 5101 na hostitelském počítači Docker (virtuálního počítače s Linuxem).

-   Webové služby se odkazuje na službu sql.data (instance systému SQL Server pro databázi Linux spuštěné v kontejneru). Pokud určíte tuto závislost, kontejneru catalog.api nespustí, dokud již bylo zahájeno sql.data kontejneru; To je důležité, protože catalog.api musí mít databázi systému SQL Server a spuštěna nejdřív. Však tento druh kontejneru závislost není dost v mnoha případech, protože Docker kontroluje jenom na úrovni kontejneru. Někdy služby (v tomto případu SQL serveru) stále možná není připravené, proto se doporučuje implementovat logiku opakovaných pokusů s exponenciálního omezení rychlosti v mikroslužeb vašeho klienta. Tímto způsobem, pokud není připraven na krátkou dobu kontejner závislost aplikace zůstanou odolný.

-   Je nakonfigurován pro povolení přístupu k externích serverů: nadbytečné\_hostitelů nastavení umožňuje přístup k externím serverům nebo počítače mimo hostitelů Docker (který je mimo výchozí virtuálních počítačů Linux, který je vývoj Docker hostitele), jako je například místní databáze SQL Instance serveru na váš vývojový počítač.

Existují také další, pokročilejší docker-compose.yml nastavení, která se budeme zabývat v následujících částech.

### <a name="using-docker-compose-files-to-target-multiple-environments"></a>Pomocí docker tvoří pro prostředí s více soubory

Soubory docker-compose.yml jsou definiční soubory a mohou být využívána více infrastruktury, které pochopit, že formát. Nástroj nejjednodušší je docker-tvoří příkazu, ale jiné nástroje, jako orchestrators (například Docker Swarm) také chápou tento soubor.

Proto pomocí docker compose příkaz můžete cílit na následující hlavní scénáře.

#### <a name="development-environments"></a>Vývojové prostředí

Při vývoji aplikací, je důležité, abyste mohli spustit aplikaci izolované vývojovém prostředí. Můžete použít docker compose rozhraní příkazového řádku příkaz k vytvoření tohoto prostředí nebo Visual Studio, který používá docker tvoří skrytě.

Soubor docker-compose.yml umožňuje nakonfigurovat a zdokumentovat všechny aplikace služby závislosti (jiných služeb, mezipaměti, databáze, fronty, atd.). Pomocí docker compose příkaz rozhraní příkazového řádku, můžete vytvořit a spustit jeden nebo více kontejnerů pro každá závislost jedním příkazem (docker tvoří nahoru).

Soubory docker-compose.yml jsou interpretovat pomocí modulu Docker konfigurační soubory, ale také fungovat jako soubory pohodlný dokumentaci o složení více kontejneru aplikace.

#### <a name="testing-environments"></a>Testovacích prostředích

Důležitou součástí žádné průběžné nasazování (CD) nebo proces průběžnou integraci (CI) jsou testy částí a integrace testy. Tyto automatizované testy vyžadují izolovaném prostředí, nebude mít dopad uživatele nebo všechny ostatní změny v datech aplikace.

Pomocí Docker Compose můžete vytvořit a zrušení izolované prostředí velmi snadno v několika příkazů z příkazového řádku nebo skripty, například následující příkazy:

```
docker-compose up -d
./run_unit_tests
docker-compose down
```

#### <a name="production-deployments"></a>Nasazení v produkčním prostředí

Můžete taky vytvořit k nasazení na vzdálené modulu Docker. Obvyklý případ je nasadit do jedné instance Docker hostitele (jako jsou například produkční virtuálního počítače nebo serveru zřizovat s [počítač Docker](https://docs.docker.com/machine/overview/)). Ale mohou být také celou [Docker Swarm](https://docs.docker.com/swarm/overview/) clusteru, protože clustery jsou kompatibilní s soubory docker-compose.yml.

Pokud používáte jiné orchestrator (Azure Service Fabric, Mesos DC/OS, Kubernetes atd.), vám může být nutné přidat nastavení konfigurace Instalační program a metadata stejně jako v nástroji docker-compose.yml, ale ve formátu vyžaduje další orchestrator.

V každém případě docker compose je vhodné nástroje a metadata formát pro vývoj, testování a provozním pracovní postupy, i když pracovním postupu mohou lišit na orchestrator, kterou používáte.

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a>Pomocí několika docker tvoří soubory pro zpracování více prostředích

Pokud je cílem různých prostředích, měli byste použít více tvoří soubory. To vám umožní vytvořit více variant konfigurace v závislosti na prostředí.

#### <a name="overriding-the-base-docker-compose-file"></a>Přepsání soubor základní docker-compose

Můžete použít soubor docker-compose.yml jeden jako zjednodušenou příklady uvedené v předchozí části. Které však není doporučeno pro většinu aplikací.

Ve výchozím nastavení přečte vytvářené ze dvou souborů, docker-compose.yml a soubor docker-compose.override.yml volitelné. Jak ukazuje obrázek 8-11, když pomocí sady Visual Studio a také povolení podpory Docker, Visual Studio vytvoří soubor docker-compose.ci.build,yml Další budete moci použít z položek konfigurace nebo CD kanálů, jako v služby VSTS.

![](./media/image12.png)

**Obrázek 8-11**. soubory ve Visual Studio 2017 docker compose

Můžete upravit soubory docker-compose pomocí libovolného editoru, jako je Visual Studio Code nebo Sublime a spusťte aplikaci pomocí docker compose až příkaz.

Podle konvence soubor docker-compose.yml obsahuje základní konfiguraci a další nastavení statické. To znamená, že v závislosti na prostředí pro nasazení, které se zaměříte neměli měnit konfiguraci služby.

Soubor docker-compose.override.yml, jak naznačuje název obsahuje nastavení konfigurace, které potlačí základní konfigurace, jako je například konfigurace, která závisí na prostředí nasazení. Také můžete mít víc přepsání souborů s různými názvy. Soubory přepsání obvykle obsahují další informace potřebné pro aplikaci, ale konkrétní prostředí a nasazení.

#### <a name="targeting-multiple-environments"></a>Cílení na více prostředí

Typické použití případ je při definování více tvoří soubory, můžete určit cílovou několika prostředích, jako výrobní, pracovní položky konfigurace nebo vývoj. Pro podporu tyto rozdíly, je možné rozdělit konfiguraci psaní do více souborů, jak ukazuje obrázek 8-12.

![](./media/image13.png)

**Obrázek 8-12**. Více docker tvoří soubory potlačení hodnot v souboru základní docker-compose.yml

Začínat soubor základní docker-compose.yml. Tento základní soubor musí obsahovat nastavení základní nebo statické konfigurace, která se nemění v závislosti na prostředí. Například eShopOnContainers má následující soubor docker-compose.yml jako základního souboru.

```yml
#docker-compose.yml (Base)
version: '3'
services:
  basket.api:
    image: eshop/basket.api:${TAG:-latest}
    build:
      context: ./src/Services/Basket/Basket.API
      dockerfile: Dockerfile    
    depends_on:
      - basket.data
      - identity.api
      - rabbitmq

  catalog.api:
    image: eshop/catalog.api:${TAG:-latest}
    build:
      context: ./src/Services/Catalog/Catalog.API
      dockerfile: Dockerfile    
    depends_on:
      - sql.data
      - rabbitmq

  marketing.api:
    image: eshop/marketing.api:${TAG:-latest}
    build:
      context: ./src/Services/Marketing/Marketing.API
      dockerfile: Dockerfile    
    depends_on:
      - sql.data
      - nosql.data
      - identity.api
      - rabbitmq

  webmvc:
    image: eshop/webmvc:${TAG:-latest}
    build:
      context: ./src/Web/WebMVC
      dockerfile: Dockerfile    
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

Z důvodu jiný cíl nasazení prostředí neměli měnit hodnoty v souboru základní docker-compose.yml.

Pokud byste se zaměřit na definici služby webmvc, například najdete v tom, jak tyto informace je podobný bez ohledu na to, jaké prostředí může cílení. Máte následující informace:

-   Název služby: webmvc.

-   Vlastní image kontejneru: eshop/webmvc.

-   Příkaz k vytvoření vlastních Docker bitovou kopii, která určuje, které soubor Docker používat.

-   Závislosti na dalších službách, proto tento kontejner se nespustí, dokud spustili jiných kontejnerů závislostí.

Můžete mít další konfiguraci, ale důležité je, že v souboru základní docker-compose.yml jenom chcete nastavit informace, které je společná pro prostředí. Pak by měl v docker compose.override.yml nebo podobné soubory pro produkční nebo pracovní umístit konfigurace, které jsou specifické pro každé prostředí.

Docker-compose.override.yml se obvykle používá pro vývojové prostředí, jako v následujícím příkladu z eShopOnContainers:

```yml
#docker-compose.override.yml (Extended config for DEVELOPMENT env.)
version: '3'

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
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_CATALOG_URL:-http://localhost:5101/api/v1/catalog/items/[0]/pic/}   
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
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
      - BasketUrl=http://basket.api
      - LocationsUrl=http://locations.api
      - IdentityUrl=http://10.0.75.1:5105
      - MarketingUrl=http://marketing.api                                                    
      - CatalogUrlHC=http://catalog.api/hc
      - OrderingUrlHC=http://ordering.api/hc
      - IdentityUrlHC=http://identity.api/hc     
      - BasketUrlHC=http://basket.api/hc
      - MarketingUrlHC=http://marketing.api/hc
      - PaymentUrlHC=http://payment.api/hc
      - UseCustomizationData=True
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5100:80"
  sql.data:
    environment:
      - MSSQL_SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
      - MSSQL_PID=Developer
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

V tomto příkladu konfigurace přepisování vývoj vystavuje některé porty na hostitele, definuje proměnných prostředí pomocí adresy URL pro přesměrování a určuje připojovací řetězce pro vývojové prostředí. Tato nastavení jsou všechny jenom pro vývojové prostředí.

Při spuštění `docker-compose up` (nebo ji spustit ze sady Visual Studio), příkaz načte přepsání automaticky jako by se měla slučování oba soubory.

Předpokládejme, že chcete jiný soubor vytvářené pro produkční prostředí, s jinou konfiguraci hodnot, porty nebo připojovací řetězce. Můžete vytvořit jiný soubor přepsat, jako je soubor s názvem `docker-compose.prod.yml` s různá nastavení a proměnných prostředí.  Tento soubor může být uložená v různých úložiště Git nebo spravovat a zabezpečené na jiný tým.

#### <a name="how-to-deploy-with-a-specific-override-file"></a>Nasazení s soubor specifické přepsání

Pokud chcete použít víc souborů přepsání nebo k přepsání souboru s jiným názvem, můžete použít možnost -f pomocí docker compose příkaz a zadejte soubory. Napište sloučení souborů v pořadí, ve kterém jsou uvedené v příkazovém řádku. Následující příklad ukazuje, jak nasadit pomocí přepsání souborů.

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a>Použití proměnných prostředí v docker nové soubory

To bude vyhovovat, zejména v produkčním prostředí, abyste mohli získat informace o konfiguraci z proměnné prostředí, jako v předchozích příkladech můžeme ukázaly. Referenční proměnné prostředí v souborech docker-compose pomocí syntaxe \${MY\_VAR}. Následující řádek ze souboru docker compose.prod.yml ukazuje, jak chcete-li hodnota proměnné prostředí.

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

Proměnné prostředí jsou vytvořeny a inicializovány různými způsoby v závislosti na prostředí hostitele (Linux, Windows, cloudu clusteru, atd.). Pohodlnější přístup je však můžete použít soubor .env. Podpora souborů docker-compose deklarace proměnné prostředí v souboru .env výchozí. Tyto hodnoty pro proměnné prostředí jsou výchozí hodnoty. Ale mohou být přepsány hodnoty, které může jste definovali v každé z vašich prostředích (hostitelský operační systém nebo proměnné prostředí z clusteru). Umístěte tento soubor .env ve složce, kde docker compose příkaz spuštěn z.

Následující příklad ukazuje soubor .env jako [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) soubor eShopOnContainers aplikace.

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

Docker compose očekává každý řádek v souboru .env být ve formátu &lt;proměnná&gt;=&lt;hodnotu&gt;.

Všimněte si, že s hodnotami nastavenými v běhové prostředí vždy přepsat hodnoty definované v souboru .env. Podobným způsobem hodnoty předány prostřednictvím argumenty příkazového řádku příkaz také přepsat výchozí hodnoty v souboru .env.

#### <a name="additional-resources"></a>Další zdroje

-   **Přehled Docker Compose**
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)

-   **Více souborů vytvářené**
    [*https://docs.docker.com/compose/extends/\#více tvoří soubory*](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a>Vytváření optimalizované imagí Dockeru jádro ASP.NET

Pokud zkoumáte Docker a .NET Core na zdroje v síti Internet, zjistíte Dockerfiles, které ukazují zjednodušení vytváření obrazem Docker zkopírováním svůj zdroj do kontejneru. Tyto příklady navrhnout pomocí jednoduchého konfigurace může mít bitovou kopii Docker s prostředím zabalit s aplikací. Následující příklad ukazuje jednoduchý soubor Docker v této souvislosti.

```
FROM microsoft/dotnet

WORKDIR /app

ENV ASPNETCORE_URLS http://+:80

EXPOSE 80

COPY . .

RUN dotnet restore

ENTRYPOINT ["dotnet", "run"]
```

Soubor Docker takto bude fungovat. Můžete však podstatně optimalizovat bitových kopií, zejména vaše produkční Image.

V kontejneru a mikroslužeb modelu jsou neustále spouštění kontejnery. Typické způsob používání kontejnerů nerestartuje kontejner režimu spánku, protože je kontejner na jedno použití. Orchestrators (například Docker Swarm, Kubernetes, orchestrátoru DC/OS nebo Azure Service Fabric) jednoduše vytvořit nové instance třídy bitové kopie. To znamená, že potřebujete optimalizovat předkompilace aplikace, když je vytvořen, proces vytváření instancí bude rychlejší. Když se spustí kontejneru, mělo by být připraven ke spuštění. Nesmí obnovit a kompilaci v době běhu, pomocí dotnet obnovení a dotnet vytváření příkazů z dotnet rozhraní příkazového řádku, jak můžete vidět v mnoha příspěvcích na blogu o .NET Core a Docker.

Tým služby rozhraní .NET byla provádění pracovní důležité, aby .NET Core a ASP.NET Core rozhraní optimalizovaný kontejner. .NET Core nejen je jednoduché rozhraní s malou paměťovou zátěž; týmu se zaměřuje na výkon při spouštění a vytváří některé optimalizované Docker Image, jako je třeba [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) bitové kopie k dispozici na [úložiště Docker Hub](https://hub.docker.com/r/microsoft/aspnetcore/), oproti běžné [ Microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) nebo [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) bitové kopie. [Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image poskytuje automatické nastavení aspnetcore\_adres URL na port 80 a mezipaměti před ngend sestavení; obě nastavení mít za následek rychlejší spuštění.

#### <a name="additional-resources"></a>Další zdroje

-   **Vytváření optimalizované Imagí Dockeru s ASP.NET Core**
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)

### <a name="building-the-application-from-a-build-ci-container"></a>Vytvoření aplikace z kontejneru sestavení (CI)

Další výhodou Docker je, že můžete vytvořit aplikaci z předkonfigurovaných kontejneru, jak ukazuje obrázek 8-13 proto není nutné k vytvoření sestavení počítače nebo virtuálního počítače k sestavení aplikace. Můžete použít, nebo tento kontejner sestavení testů spuštěním na vývojovém počítači. Ale co je ještě více zajímavé, které můžete použít stejný kontejner sestavení z vašeho kanálu CI (nepřetržité integrace).

![](./media/image14.png)

**Obrázek 8-13**. Sestavení – kontejner docker kompilování vaší binární soubory rozhraní .NET 

V tomto scénáři poskytujeme [microsoft/aspnetcore sestavení](https://hub.docker.com/r/microsoft/aspnetcore-build/) bitovou kopii, kterou můžete použít pro zkompilování a vybuildování aplikace ASP.NET Core. V obrázku na základě se umístí výstup [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) bitovou kopii, kterou je obrázek optimalizované runtime, jako v předchozí části.

Bitová kopie aspnetcore sestavení obsahuje všechno, co potřebujete, aby bylo možné kompilaci aplikace ASP.NET Core, včetně .NET Core, sady SDK technologie ASP.NET, npm, Bower, Gulp, atd.

Potřebujeme tyto závislosti v čase vytvoření buildu. Ale jsme nechcete, aby k provedení těchto aplikací za běhu, protože by byla bitovou kopii zbytečně velké. V aplikaci eShopOnContainers, můžete vytvořit aplikaci z kontejneru právě spuštěním následující docker napište příkaz.

```
  docker-compose -f docker-compose.ci.build.yml up
```

Obrázek 8-14 ukazuje tento příkaz není spuštěn v příkazovém řádku.

![](./media/image15.png)

**Obrázek 8-14.** Vytváření aplikace .NET z kontejneru

Jak můžete vidět, je kontejner, který běží ci sestavení\_1 kontejneru. To je založené na bitovou kopii aspnetcore sestavení tak, aby můžete zkompilovat a sestavit celou aplikaci z tohoto kontejneru, místo z vašeho počítače. To znamená Proč ve skutečnosti je vytváření a kompilování .NET Core projekty v systému Linux, protože tento kontejner běží na hostiteli systému Linux Docker výchozí.

[Docker compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) soubor pro této bitové kopie (součást eShopOnContainers) obsahuje následující kód. Uvidíte, že začne kontejneru sestavení pomocí [microsoft/aspnetcore sestavení](https://hub.docker.com/r/microsoft/aspnetcore-build/) bitové kopie.

```yml
version: '3'

services:

  ci-build:

    image: microsoft/aspnetcore-build:2.0

    volumes:
      - .:/src

    working_dir: /src

    command: /bin/bash -c "pushd ./src/Web/WebSPA && npm rebuild node-sass && popd && dotnet restore ./eShopOnContainers-ServicesAndWebApps.sln && dotnet publish ./eShopOnContainers-ServicesAndWebApps.sln -c Release -o ./obj/Docker/publish"

```

* Počínaje **.NET Core 2.0**, `dotnet restore` příkaz provede automaticky při `dotnet publish` se spustí příkaz.

Jakmile kontejneru sestavení spuštěná, spuštění obnovení dotnet .NET SDK a dotnet. publikování příkazy na všechny projekty v řešení pro kompilaci rozhraní .NET bits. V takovém případě eShopOnContainers obsahuje také SPA podle TypeScript a úhlová pro kód klienta, a proto ho také musí zkontrolovat závislosti jazyka JavaScript pomocí npm, ale tato akce není v relaci s .NET bits.

Dotnet publikování příkaz sestavení a publikuje kompilovaný výstup ve složce každý projekt na... Složka /obj/Docker/Publish, jak ukazuje obrázek 8 až 15.

![](./media/image16.png)

**Obrázek 8 až 15.** Příkaz Publikovat binární soubory, které jsou generované dotnet.

#### <a name="creating-the-docker-images-from-the-cli"></a>Vytvoření imagí Dockeru z rozhraní příkazového řádku

Jakmile výstupu aplikace publikována do související složek (v rámci každého projektu), dalším krokem je ve skutečnosti vytvoření imagí Dockeru. K tomuto účelu použijete docker-compose sestavení a docker tvoří příkazy, jak ukazuje obrázek 8-16.

![](./media/image17.png)

**Obrázek 8-16.** Vytváření imagí Dockeru a spouštění kontejnerů.

Obrázek 8-17 můžete zobrazit, jak docker-compose vytvářet příkaz spustí.

![](./media/image18.png)

**Obrázek 8-17**. Vytváření bitových kopií Docker pomocí docker-napište příkaz sestavení

Rozdíl mezi docker-compose sestavení a docker compose až příkazy je, že docker compose sestavení a spuštění bitové kopie.

Pokud používáte Visual Studio, jsou všechny tyto kroky provést v pozadí. Visual Studio zkompiluje aplikace .NET, vytvoří imagí Dockeru a nasadí do hostitelů Docker kontejnerů. Visual Studio nabízí další funkce, jako možnost ladění kontejnerů spuštěna v Docker, přímo ze sady Visual Studio.

Celkové takeway tady je, že budete moci sestavit aplikaci stejné svůj CI/CD kanál má sestavit způsobem ho – z kontejneru místo z místního počítače. Po s bitové kopie vytvořené, pak stačí ke spuštění imagí Dockeru pomocí docker-tvoří až příkaz.

#### <a name="additional-resources"></a>Další zdroje

-   **Vytváření bits z kontejneru: nastavení řešení eShopOnContainers v prostředí Windows rozhraní příkazového řádku (dotnet příkazového řádku Dockeru a VS Code rozhraní příkazového řádku,)**
    [*https://github.com/dotnet/eShopOnContainers/wiki/ 03.-Setting-the-eShopOnContainers-Solution-up-in-a-Windows-CLI-Environment-(DotNet-CLI,-Docker-CLI-and-vs-Code)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))


>[!div class="step-by-step"]
[Předchozí] (data řízené crud-microservice.md) [Další] (container.md databáze serveru)
