---
title: Definování vícekontejnerové aplikace pomocí docker-compose.yml
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Definování vícekontejnerové aplikace pomocí docker-compose.yml
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/30/2017
ms.openlocfilehash: d1c4166129716ccbbc86855e38d631f493b82290
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2018
ms.locfileid: "46937602"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a>Definování vícekontejnerové aplikace pomocí docker-compose.yml 

V této příručce [docker-compose.yml](https://docs.docker.com/compose/compose-file/) souboru byla zavedena v části [kroku 4. Definování vašich služeb v docker-compose.yml při sestavování aplikace více kontejnerů Dockeru](#step4_define_svcs_in_docker_compose_yml). Existují však další způsoby, jak používat docker-compose soubory, které stojí za prozkoumání podrobněji.

Například můžete výslovně popsat, jak chcete nasadit vícekontejnerové aplikace v souboru docker-compose.yml. Volitelně může také popisovat, jak chcete sestavit vlastní Image Dockeru. (Vlastní Image Dockeru se dají taky vytvářet pomocí rozhraní příkazového řádku Dockeru.)

V podstatě definování všech kontejnerů, které chcete nasadit, a navíc určité vlastnosti pro každý kontejner nasazení. Jakmile budete mít soubor s popisem nasazení více kontejnerů, můžete nasadit celé řešení v rámci jedné akce orchestrované systémem [docker-compose up](https://docs.docker.com/compose/overview/) příkazu rozhraní příkazového řádku, nebo ji můžete nasadit transparentně ze sady Visual Studio. V opačném případě musíte použít rozhraní příkazového řádku Dockeru k nasazení kontejnerů pomocí kontejneru v několika krocích pomocí dockeru, spusťte příkaz z příkazového řádku. Jednotlivé služby definované v docker-compose.yml proto musíte zadat právě jednu image nebo sestavení. Další klíče jsou volitelné a odpovídají jejich docker, spusťte příkazový řádek protějšky.

Následující kód YAML je definice je to možné globální, ale jeden soubor docker-compose.yml pro vzorovou aplikaci eShopOnContainers. Toto není skutečný docker-compose soubor v aplikaci eShopOnContainers. Místo toho je zjednodušený a konsolidované verze jednoho souboru, který není nejlepší způsob, jak pracovat s souborů docker-compose, jak budou vysvětlena dále.

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

Kořenový klíč z tohoto souboru se služby. Pod tímto klíčem definujete služby chcete nasadit a spustit při spouštění docker-compose up příkaz nebo při nasazení ze sady Visual Studio s použitím tohoto souboru docker-compose.yml. V tomto případě soubor docker-compose.yml má několik služeb, které jsou definovány, jak je popsáno v následujícím seznamu.

-   webmvc kontejneru, včetně aplikací ASP.NET Core MVC využívání mikroslužeb from C na straně serveru\#

-   CATALOG.API kontejneru, včetně katalogu ASP.NET Core webového rozhraní API mikroslužby

-   Ordering.API kontejneru, včetně řazení ASP.NET Core webového rozhraní API mikroslužby

-   SQL.data kontejneru systémem SQL Server pro Linux, uchovávající databází mikroslužeb

-   basket.API kontejneru s nákupní košík ASP.NET Core webového rozhraní API mikroslužby

-   basket.data kontejneru Služba mezipaměti REDIS s databází nákupní košík jako mezipaměť REDIS

### <a name="a-simple-web-service-api-container"></a>Jednoduchý kontejner rozhraní API webové služby

Se zaměříte na jediný kontejner, kontejner catalog.api-mikroslužeb má jednoduché definici:

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

Tato kontejnerizovaná služba má následující základní konfigurace:

-   Je založena na imagi vlastní eshop/catalog.api. Pro jednoduchost saké neexistuje žádné sestavení: nastavení v souboru klíče. To znamená, že obrázek musí mít byla dříve vytvořena (pomocí sestavení dockeru) se stáhly (pomocí příkazu docker pull) z libovolného registru Dockeru.

-   Definuje proměnnou prostředí s názvem připojovací řetězec připojovacím řetězcem Entity Framework používané pro přístup k instanci serveru SQL Server, který obsahuje datový model katalogu. V takovém případě stejného kontejneru systému SQL Server obsahuje více databází. Proto je nutné méně paměti v počítači pro vývoj pro Docker. Můžete však také nasadit jeden kontejner systému SQL Server pro každou databázi mikroslužeb.

-   Název systému SQL Server je sql.data, které se stejným názvem, který pro kontejner, na kterém běží instance systému SQL Server pro Linux. Tato možnost je pohodlná; bude možné použít tento překlad (interní hostitele Dockeru) vyřeší síťovou adresu, takže není nutné znát interní IP adresa pro kontejnery, které spouštíte z jiných kontejnerů.

Vzhledem k tomu, že připojovací řetězec je určené proměnnou prostředí, můžete tuto proměnnou nastavit prostřednictvím jiným způsobem a jiný čas. Například můžete nastavit různé připojovací řetězec při nasazení do produkčního prostředí v posledním hostitele nebo provedením z vašich kanálů CI/CD v Azure DevOps služby nebo systému upřednostňované DevOps.

-   Zpřístupňuje port 80 pro interní přístup ke službě catalog.api v rámci hostitele Dockeru. Hostitel je aktuálně virtuálního počítače s Linuxem, protože je založen na image Dockeru pro Linux, ale můžete nakonfigurovat tak, kontejner pro spuštění v imagi Windows místo.

-   Předá vystavené port 80 v kontejneru na port 5101 hostitele Docker Machine (virtuálního počítače s Linuxem).

-   Webové služby odkazuje ve službě sql.data (instance systému SQL Server pro Linux databáze spuštěné v kontejneru). Pokud zadáte tuto závislost, kontejneru catalog.api nespustí, dokud již bylo zahájeno sql.data kontejneru; To je důležité, protože catalog.api musí být databáze serveru SQL Server a spuštěna nejprve. Však tento druh závislosti kontejneru není dostatečně v mnoha případech, protože Docker zkontroluje pouze na úrovni kontejneru. Někdy služby (v tomto případě systému SQL Server) nemusí nadále budete mít, proto se doporučuje implementovat logiku opakování pomocí exponenciálního omezení rychlosti mikroslužby klienta. Tímto způsobem, pokud kontejner závislosti není připravený na krátkou dobu, aplikace bude nadále odolný.

-   Je nakonfigurována pro povolení přístupu k externím serverům: nadbytečné\_hostitelů nastavení vám umožní přistupovat k externí servery nebo počítače mimo hostitele Docker (tedy mimo výchozí linuxového virtuálního počítače, který je vývoj Docker hostitele), jako je například místní databáze SQL Instance serveru na vašem počítači.

Existují také jiné, pokročilejší docker-compose.yml nastavení, které se budeme zabývat v dalších částech.

### <a name="using-docker-compose-files-to-target-multiple-environments"></a>Pomocí souborů docker-compose cílit na více prostředí

Soubory docker-compose.yml jsou soubory definic a mohou být využívána více infrastruktury, které rozumí formátu. Nástroj nejjednodušší je docker-compose příkazu, ale další nástroje, jako je srozuměni tento soubor s orchestrátory (například Docker Swarm).

Proto se s použitím příkazu je možné cílit na následující hlavní scénáře docker-compose.

#### <a name="development-environments"></a>Vývojová prostředí

Při vývoji aplikací, je důležité, aby bylo možné spouštět aplikace v izolovaném vývojové prostředí. Můžete použít příkazu rozhraní příkazového řádku k vytvoření tohoto prostředí nebo pomocí sady Visual Studio, který používá docker-compose pod pokličkou docker-compose.

Soubor docker-compose.yml umožňuje konfigurovat a dokumentovat závislosti služby všechny aplikace (jiné služby, mezipaměti, databáze, fronty atd.). Použití docker-compose příkazu rozhraní příkazového řádku, můžete vytvořit a spustit jeden nebo více kontejnerů pro každý závislosti pomocí jediného příkazu (docker-compose up).

Soubory docker-compose.yml jsou konfigurační soubory interpretovat modul Docker, ale sloužit také jako soubory pohodlný dokumentace o složení vícekontejnerovou aplikaci.

#### <a name="testing-environments"></a>Testovací prostředí

Důležitou součástí procesu kontinuální integrace (CI) ani průběžného nasazování (CD) jsou testy jednotek a integrační testy. Tyto automatizované testy vyžadují izolovaného prostředí, takže nejsou ovlivněny uživatelů nebo jiné změny v datech vaší aplikace.

Pomocí Docker Compose můžete vytvořit a odstranit izolované prostředí velmi snadno v několika příkazů z příkazového řádku nebo skripty, například následující příkazy:

```
docker-compose up -d
./run_unit_tests
docker-compose down
```

#### <a name="production-deployments"></a>Nasazení v produkčním prostředí

Compose můžete použít také k nasazení na vzdálený modul Docker. Obvyklý případ je nasadit do jedné instance hostitele Docker (jako jsou produkční virtuální počítač nebo server opatřena [Docker Machine](https://docs.docker.com/machine/overview/)). Ale mohou být také celý [Docker Swarm](https://docs.docker.com/swarm/overview/) clusteru, protože v clusterech, budou také kompatibilní se soubory docker-compose.yml.

Pokud používáte jiné orchestrator (Azure Service Fabric, Mesos DC/OS, Kubernetes, atd.), můžete potřebovat přidat instalační program a metadata nastavení konfigurace podobné těm v docker-compose.yml, ale ve formátu vyžaduje další nástroje orchestrator.

V každém případě docker-compose je vhodné nástroje a metadata formát pro vývoj, testování a produkční pracovní postupy, i když pracovním postupu se může lišit na orchestrátoru, který používáte.

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a>Použití více souborů docker-compose pro zpracování několika prostředí

Při cílení na jiné prostředí, byste měli použít více soubory compose. To vám umožní vytvořit několik variant konfigurace v závislosti na prostředí.

#### <a name="overriding-the-base-docker-compose-file"></a>Přepsání souboru základní docker-compose

Můžete použít soubor jednoho docker-compose.yml jako zjednodušené příkladů uvedených v předchozí části. Který však není doporučeno pro většinu aplikací.

Ve výchozím nastavení přečte vytvořit dva soubory, docker-compose.yml a docker-compose.override.yml volitelné soubor. Jak ukazuje obrázek 8-11, když pomocí sady Visual Studio a povolení podpory Dockeru, Visual Studio také vytvoří soubor docker-compose.ci.build,yml další pro použití z vašich kanálů CI/CD jako ve službách Azure DevOps.

![](./media/image12.png)

**Obrázek 8-11**. docker-compose soubory v sadě Visual Studio 2017

Můžete upravit docker-compose soubory v libovolném editoru, jako je Visual Studio Code nebo Sublime a spusťte aplikaci docker-compose up příkazu.

Podle konvence soubor docker-compose.yml obsahuje základní konfiguraci a další nastavení statické. To znamená, že konfigurace služby by neměly měnit v závislosti na prostředí, na které cílíte.

Soubor docker-compose.override.yml jako její název napovídá, obsahuje konfigurační nastavení přepsat základní konfigurace, jako je například konfigurace, která závisí na prostředí nasazení. Také můžete mít více přepsání souborů s různými názvy. Přepsat soubory obvykle obsahují další informace potřebné pro aplikaci, ale konkrétní prostředí nebo nasazení.

#### <a name="targeting-multiple-environments"></a>Cílení na více prostředí

Typický případ použití je při definování více compose soubory, je možné cílit na více prostředí, jako jsou výroba, Fázování importu, průběžná integrace a vývoje. Pro podporu těchto rozdílů, můžete rozdělit konfiguraci psaní do více souborů, jak ukazuje obrázek 8 – 12.

![](./media/image13.png)

**Obrázek 8-12**. Několik souborů docker-compose přepsání hodnot v souboru docker-compose.yml základní

Začněte s soubor základní docker-compose.yml. Tuto základní soubor musí obsahovat nastavení konfigurace základní nebo statické, které se nemění v závislosti na prostředí. Například aplikaci eShopOnContainers má následující soubor docker-compose.yml jako základního souboru.

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

Hodnoty v souboru základní docker-compose.yml by neměly měnit z důvodu různých cílových prostředí nasazení.

Pokud vám soustředit se na definici služby webmvc, například uvidíte jak tyto informace je skoro stejné bez ohledu na to, co prostředí, které vám může cílí. Máte následující informace:

-   Název služby: webmvc.

-   Vlastní image kontejneru: eshop/webmvc.

-   Příkaz k vytvoření vlastní image Dockeru, určující, které soubor Dockerfile používat.

-   Závislosti na dalších službách, takže tento kontejner se nespustí, dokud jste spustili dalších kontejnerů závislostí.

Můžete mít další konfiguraci, ale důležité je, že v souboru docker-compose.yml základní jenom chcete nastavit informace, které jsou společné napříč prostředími. Potom v docker-compose.override.yml nebo podobné soubory provozního nebo testovacího měli umístit konfigurace, které jsou specifické pro každé prostředí.

Docker-compose.override.yml se obvykle používá pro vaše vývojové prostředí, jako v následujícím příkladu v aplikaci eShopOnContainers:

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

V tomto příkladu konfigurace přepisování vývoj uvádí některé porty na hostitele, definuje proměnných prostředí pomocí adresy URL pro přesměrování a určuje připojovací řetězce pro vývojové prostředí. Tato nastavení jsou všechny jenom pro vývojové prostředí.

Při spuštění `docker-compose up` (nebo ji spustit ze sady Visual Studio), tento příkaz načte přepsání automaticky jako kdyby to byly sloučení oba soubory.

Předpokládejme, že má jiný soubor Compose pro produkční prostředí s jinou konfiguraci hodnoty, porty nebo připojovací řetězce. Můžete vytvořit soubor přepsání, jako je soubor s názvem `docker-compose.prod.yml` s různými nastaveními a proměnných prostředí.  Tento soubor může být uložená v různých úložiště Git nebo spravovat a zabezpečit jiný tým.

#### <a name="how-to-deploy-with-a-specific-override-file"></a>Nasazení se souborem specifické přepsání

Pokud chcete použít více souborů přepsání nebo přepsání souboru s jiným názvem, můžete použít možnost -f s příkazu docker-compose a zadejte soubory. Vytvoření souborů sloučení v pořadí, v jakém jsou uvedeny v příkazovém řádku. Následující příklad ukazuje, jak nasadit pomocí přepsání souborů.

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a>Použití proměnných prostředí v souborů docker-compose

Je vhodné, zejména v produkčním prostředí, abyste mohli získat informace o konfiguraci z proměnných prostředí, jak budeme mít je znázorněno v předchozích příkladech. Odkaz na proměnnou prostředí v souborech docker-compose pomocí syntaxe \${MY\_VAR}. Následující řádek ze souboru dockeru compose.prod.yml ukazuje, jak odkazovat na hodnotu proměnné prostředí.

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

Proměnné prostředí jsou vytvořeny a inicializovány různými způsoby v závislosti na hostitelské prostředí (Linux, Windows, Cloudový cluster atd.). Pohodlný přístup je však použití souboru .env. Podpora souborů docker-compose deklarování proměnných prostředí v souboru .env výchozí. Tyto hodnoty pro proměnné prostředí jsou výchozí hodnoty. Ale může být přepsána hodnoty, které může jste definovali ve všech vašich prostředích (hostitelský operační systém nebo proměnné prostředí z clusteru). Umístění tohoto souboru .env ve složce kde docker-compose ze spuštění příkazu.

Následující příklad ukazuje souboru .env stejně jako [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) soubor pro aplikaci eShopOnContainers aplikaci.

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

Docker-compose očekává, že každý řádek v souboru .env být ve formátu &lt;proměnnou&gt;=&lt;hodnota&gt;.

Všimněte si, že hodnoty nastavené v běhovém prostředí vždy přepsat hodnoty definované v souboru .env. Podobným způsobem hodnoty předané prostřednictvím argumentů příkazového řádku příkaz také přepsat výchozí hodnoty nastavené v souboru .env.

#### <a name="additional-resources"></a>Další zdroje

-   **Přehled služby Docker Compose**
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)

-   **Více soubory Compose**
    [*https://docs.docker.com/compose/extends/\#multiple-compose-files*](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a>Vytváření optimalizované Image Dockeru ASP.NET Core

Pokud zkoumáte Dockeru a .NET Core na zdroje v síti Internet, zjistíte soubory Dockerfile, které ukazují zjednodušení vytváření image Dockeru pomocí kopírování zdroje do kontejneru. Tyto příklady navrhnout pomocí jednoduchou konfiguraci a může mít image Dockeru s prostředím zabalit s aplikací. Následující příklad ukazuje jednoduchý soubor Dockerfile v této souvislosti.

```
FROM microsoft/dotnet

WORKDIR /app

ENV ASPNETCORE_URLS http://+:80

EXPOSE 80

COPY . .

RUN dotnet restore

ENTRYPOINT ["dotnet", "run"]
```

Soubor Dockerfile takto bude fungovat. Je ale podstatně optimalizovat Image, zejména produkčních imagí.

V modelu mikroslužeb a kontejnerů jsou neustále spouštění kontejnerů. Typické způsob, jak pomocí kontejnerů nerestartuje spící kontejner, protože kontejneru je jedno použití. Orchestrátory (jako je Docker Swarm, Kubernetes, DC/OS nebo Azure Service Fabric) jednoduše vytvořte nové instance z imagí. To znamená, že potřebujete optimalizovat předkompilace aplikace, když je sestaven tak proces vytváření instancí bude rychlejší. Při spuštění kontejneru musí být připraveny ke spuštění. Nesmí obnovit a kompilaci za běhu, dotnet restore a dotnet sestavovací příkazy z rozhraní příkazového řádku dotnet, jak vidíte v mnoha blogové příspěvky o .NET Core a Docker.

Tým .NET má způsobem důležitou práci provést optimalizovaný kontejner rozhraní .NET Core a ASP.NET Core. Nejen .NET Core je jednoduché rozhraní s malé paměťové nároky; tým zaměřený na výkon při spouštění a vytváří některé optimalizované Image Dockeru, jako je třeba [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) bitové kopie, které jsou k dispozici na [Docker Hubu](https://hub.docker.com/r/microsoft/aspnetcore/), porovnání standardní [ Microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) nebo [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) bitové kopie. [Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image poskytuje automatické nastavení aspnetcore\_adresy URL na port 80 a mezipaměti pre-ngend sestavení; obě nastavení za následek rychlejší spuštění.

#### <a name="additional-resources"></a>Další zdroje

-   **Vytváření optimalizované Image Dockeru s ASP.NET Core**
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)

### <a name="building-the-application-from-a-build-ci-container"></a>Vytvoření aplikace z kontejneru sestavení (CI)

Další výhodou Dockeru je, že můžete vytvářet aplikace z předkonfigurovaných kontejneru, jak je znázorněno v obrázek 8-13, takže není nutné k vytvoření sestavení počítače nebo virtuálního počítače pro sestavení aplikace. Můžete použít nebo otestování tohoto sestavení kontejneru spuštěním na vývojovém počítači. Ale co je ještě zajímavější, které můžete použít stejný kontejner sestavení z vašeho kanálu CI (průběžná integrace).

![](./media/image14.png)

**Obrázek 8-13**. Sestavení – kontejner docker kompilace .NET binární soubory 

V tomto scénáři zajišťuje [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image, kterou můžete použít ke kompilaci a vytváření aplikací ASP.NET Core. Výstup se umístí do image založenou na [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) bitovou kopii, která je obrázek optimalizovaný modul runtime, jako v předchozí části.

Image aspnetcore-build obsahuje všechno, co potřebujete, aby bylo možné zkompilovat aplikaci ASP.NET Core, včetně .NET Core, sady SDK technologie ASP.NET, npm, Bower, Gulp, atd.

Potřebujeme tyto závislosti v okamžiku sestavení. Ale jsme nechcete, aby tyto aplikace provádět za běhu, protože by byla image zbytečně velký. V aplikaci eShopOnContainers aplikaci, můžete vytvořit aplikaci z kontejneru jednoduše spuštěním tohoto příkazu docker-compose.

```
  docker-compose -f docker-compose.ci.build.yml up
```

Obrázek 8-14 ukazuje tento příkaz spouštění na příkazovém řádku.

![](./media/image15.png)

**Obrázek 8-14.** Vytvoření aplikace .NET v kontejneru

Jak vidíte, je kontejner, na kterém běží sestavení ci\_počet kontejnerů: 1. To je založené na image aspnetcore-build tak, aby jeho kompilace a sestavení celé aplikace z v rámci tohoto kontejneru, nikoli z vašeho počítače. To znamená Proč ve skutečnosti je sestavení a kompilace projektů .NET Core v systému Linux, protože tento kontejner běží na hostiteli systému Linux Docker výchozí.

[Docker-compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) soubor pro tuto bitovou kopii (součást aplikaci eShopOnContainers) obsahuje následující kód. Uvidíte, že začne sestavení kontejneru pomocí [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) bitové kopie.

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

* Počínaje **.NET Core 2.0**, `dotnet restore` příkaz spustí automaticky při `dotnet publish` spuštění příkazu.

Po sestavení kontejneru je v provozu, spouští příkaz dotnet restore sady .NET SDK a dotnet publikovat příkazy spouštěly pro všechny projekty v řešení mohli zkompilovat .NET bits. V takovém případě aplikaci eShopOnContainers také obsahuje SPA podle TypeScript a Angular pro klientský kód, a proto potřebuje také kontrolovat závislosti jazyka JavaScript pomocí npm, ale tato akce není v relaci s bity .NET.

Dotnet publikovat příkaz sestavení a publikuje kompilovaný výstup v rámci složky projektu, každý... Složka /obj/Docker/Publish, jak ukazuje obrázek 8 – 15.

![](./media/image16.png)

**Obrázek 8 – 15.** Binární soubory generované záznamem pro dotnet příkazu pro publikování

#### <a name="creating-the-docker-images-from-the-cli"></a>Vytvoření Image Dockeru z rozhraní příkazového řádku

Po publikování výstup aplikace do souvisejících složek (v rámci každého projektu), dalším krokem je ve skutečnosti sestavit Image Dockeru. K tomuto účelu použijte docker-compose sestavení a docker-compose up příkazy, jak ukazuje obrázek 8 – 16.

![](./media/image17.png)

**Obrázek 8 – 16.** Vytváření imagí Dockeru a spuštění kontejnerů

Obrázek 8-17 můžete zobrazit, jak vytvářet docker-compose spuštění příkazu.

![](./media/image18.png)

**Obrázek 8-17**. Vytváření imagí Dockeru docker-compose příkaz sestavení

Rozdíl mezi docker-compose sestavení a docker-compose up příkazy je, že docker-compose up sestavení a spuštění imagí.

Při použití sady Visual Studio jsou všechny tyto kroky provést na pozadí. Visual Studio zkompiluje aplikaci .NET, vytvoří Image Dockeru a umožňuje nasazení kontejnerů do hostitele Dockeru. Visual Studio nabízí další funkce, jako je schopnost ladit vaše kontejnery spuštěné v Dockeru, přímo ze sady Visual Studio.

Celkové takeway zde je, že se můžete k sestavení aplikace stejný způsobem by měl svůj kanál CI/CD sestavte ho – z kontejneru místo z místního počítače. Po s obrázky vytvořené, pak stačí pro spuštění imagí Dockeru pomocí dockeru-compose up příkazu.

#### <a name="additional-resources"></a>Další zdroje

-   **Vytváření bitů z kontejneru: nastavení řešení aplikaci eShopOnContainers v prostředí Windows CLI (rozhraní příkazového řádku dotnet, rozhraní příkazového řádku Dockeru a VS Code)**
    [*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI, - Docker – rozhraní příkazového řádku- a -VS-kódu)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))


>[!div class="step-by-step"]
[Předchozí](data-driven-crud-microservice.md)
[další](database-server-container.md)
