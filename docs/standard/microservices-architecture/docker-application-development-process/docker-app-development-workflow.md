---
title: "Pracovní postup vývoje pro Docker aplikace"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Pracovní postup vývoje pro Docker aplikace"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8537b1db27f512ec0bfc2f23589efe8199ca3287
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2018
---
# <a name="development-workflow-for-docker-apps"></a>Pracovní postup vývoje pro Docker aplikace

Životního cyklu aplikace spustí na každý vývojář počítače, kde vývojář kódy aplikace pomocí jejich upřednostňovaný jazyk a testy ho místně. Bez ohledu na to, které jazyk, architektura a platforma vývojář vybere, se tento pracovní postup vývojář je vždy vývoj a testování Docker kontejnery, ale tak místně.

Každý kontejner (instance Docker Image) zahrnuje následující součásti:

-   Výběr operačního systému, (například distribuce systému Linux, Windows Nano Server nebo jádro systému Windows Server).

-   Soubory přidal developer (binární soubory aplikace, atd.).

-   Informace o konfiguraci (nastavení prostředí a závislosti).

## <a name="workflow-for-developing-docker-container-based-applications"></a>Pracovní postup pro vývoj aplikací na základě kontejner Docker

Tato část popisuje *vnitřní smyčky* pracovní postup vývoje pro aplikace založené na kontejner Docker. Pracovní postup vnitřní smyčky znamená ji není přihlédnutím k širší DevOps pracovního postupu a právě se zaměřuje na vývoj pro práci na počítači pro vývojáře. Počáteční kroky pro nastavení prostředí nejsou zahrnuty, od těch, které se provádějí pouze jednou.

Aplikace se skládá z vlastní služby a další knihovny (závislosti). Následují základní kroky, které obvykle podniknout při vytvoření aplikace Docker, jak ukazuje následující obrázek 5-1.

![](./media/image1.png)

**Obrázek 5-1.** Krok za krokem pracovního postupu pro vývoj aplikací kontejnerizované Docker

V této příručce je podrobně popsán tento celý proces a každé hlavní fázi se vysvětluje zaměřené na prostředí sady Visual Studio.

Pokud používáte přístup vývoj editor nebo rozhraní příkazového řádku (například Visual Studio Code a příkazového řádku Dockeru v systému macOS nebo Windows), je třeba vědět každý krok, obecně podrobněji, než pokud používáte Visual Studio. Další podrobnosti o práci v prostředí rozhraní příkazového řádku najdete v části elektronická kniha [životního cyklu aplikace Kontejnerizované Docker s Platforms Microsoft a nástrojů](http://aka.ms/dockerlifecycleebook/).

Pokud používáte Visual Studio 2015 nebo Visual Studio 2017, mnoho z těchto kroků jsou zpracovávány pro vás, což výrazně zvyšuje produktivitu. To platí hlavně pokud používáte Visual Studio 2017 a cílení na více kontejneru aplikace. Například s jediným klepnutím myši, přidá Visual Studio soubor Docker a docker-compose.yml soubor do vašich projektů s konfigurací pro vaši aplikaci. Při spuštění aplikace v sadě Visual Studio, bitovou kopii Docker sestavení a spuštění aplikace s více kontejnerů přímo v Docker; i umožňuje ladit několik kontejnerů najednou. Tyto funkce budou zvýšení rychlosti vývoj.

Ale stejně, protože sada Visual Studio provádí tyto kroky automatické neznamená, že nepotřebujete vědět, co se děje v dole s Docker. Proto v pokyny, který následuje, jsme podrobnosti každý krok.

![](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a>Krok 1. Psaní a vytvořit počáteční aplikace nebo služby směrného plánu

Vývoj aplikace s Docker je podobným způsobem můžete vyvíjet aplikace bez Docker. Rozdíl je, že při vývoji pro Docker, jsou nasazení a testování aplikací nebo služeb spuštěných v rámci Docker kontejnerů ve vašem místním prostředí. Kontejner může být kontejner Linux nebo kontejneru systému Windows.

### <a name="set-up-your-local-environment-with-visual-studio"></a>Nastavení místního prostředí pomocí sady Visual Studio

Pokud chcete začít, zajistěte, aby byla [Docker Community Edition (CE)](https://www.docker.com/community-edition) pro Windows nainstalované, jak je popsáno v následujících pokynech:

[Začínáme s Docker CE pro Windows](https://docs.docker.com/docker-for-windows/)

Kromě toho je nutné nainstalovat Visual Studio 2017. Je to upřednostňovaný přes Visual Studio 2015 s nástroji Visual Studio Tools pro Docker add-in, proto Visual Studio 2017 má pokročilejší podporu pro Docker, jako je podpora pro ladění kontejnerů. Visual Studio 2017 zahrnuje nástroje pro Docker, pokud jste vybrali **.NET Core a Docker** zatížení během instalace, jak je znázorněno na obrázku 5-2.

![](./media/image3.png)

**Obrázek 5-2**. Výběr **.NET Core a Docker** zatížení během instalace Visual Studio 2017

Kódování svoji aplikaci v prostý .NET (obvykle v .NET Core, pokud máte v úmyslu použít kontejnery) můžete spustit i před povolením Docker v aplikaci a nasazení a testování v Docker. Doporučujeme však spustit pracující na Docker co nejdříve vzhledem k tomu, který bude reálného prostředí a problémy s můžete zjistit co nejdříve. To je podporováno, protože Visual Studio usnadňuje tak pracovat s Docker, téměř funguje transparentní – nejlepší příklad při ladění aplikace s více kontejner ze sady Visual Studio.

### <a name="additional-resources"></a>Další zdroje

-   **Začínáme s CE Docker pro systém Windows**
    [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)

-   **Visual Studio 2017**
    [*https://www.visualstudio.com/downloads/*](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

![](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a>Krok 2. Vytvořit soubor Docker související s existující základní image rozhraní .NET

Je třeba soubor Docker pro každý vlastní image, kterou chcete vytvořit; soubor Docker pro každý kontejner k nasazení, musíte taky jestli nasadit automaticky ze sady Visual Studio nebo ručně pomocí rozhraní příkazového řádku Dockeru (docker spustit a docker-tvoří příkazů). Pokud vaše aplikace obsahuje jeden vlastní službu, je třeba jeden soubor Docker. Pokud vaše aplikace obsahuje více služeb (jako architektura mikroslužeb), je třeba jeden soubor Docker pro každou službu.

Soubor Docker je umístěn v kořenové složce aplikace nebo služby. Obsahuje příkazy, které informují Docker, jak nastavit a spustit aplikaci nebo službě v kontejneru. Můžete ručně vytvořit soubor Docker v kódu a přidejte do projektu spolu s .NET závislosti.

Visual Studio a jeho nástroje pro Docker tato úloha vyžaduje pouze pomocí několika kliknutí myší. Když vytvoříte nový projekt ve Visual Studio 2017, je možnost s názvem **podporu povolit kontejneru (Docker)**, jak ukazuje obrázek 5-3.

![](./media/image5.png)

**Obrázek 5-3**. Povolení podpory Docker při vytvoření nového projektu ve Visual Studio 2017

Můžete také povolit podporu Docker na nový nebo existující projekt tak, že kliknete pravým tlačítkem na soubor projektu v sadě Visual Studio a vyberete možnost **Docker přidat projekt podporovat**, jak je znázorněno na obrázku 5-4.

![](./media/image6.png)

**Obrázek 5-4**. Povolení podpory Docker v existující projekt Visual Studio 2017

Tato akce na projektu (například webové aplikace ASP.NET nebo služby webového rozhraní API) přidá soubor Docker do projektu s požadovanou konfigurací. Také přidá soubor docker-compose.yml pro celé řešení. V následujících částech se popisují jsme informace, které jde do každé z těchto souborů. Visual Studio může tento pracovní to pro vás, ale je užitečné zjistit, co do soubor Docker.

### <a name="option-a-creating-a-project-using-an-existing-official-net-docker-image"></a>Možnost A: vytvoření projektu pomocí stávající image oficiální Docker rozhraní .NET

Obvykle sestavení vlastní image pro váš kontejner nad základní image můžete získat z oficiálního úložiště na [úložiště Docker Hub](https://hub.docker.com/) registru. Přesněji, se stane v pozadí, když povolíte podporu Docker v sadě Visual Studio. Váš soubor Docker bude používat stávající aspnetcore image.

Dříve jsme vysvětlit, které imagí Dockeru a úložiště můžete použít, v závislosti na framework a rozhodli jste se verze operačního systému. Například pokud chcete použít ASP.NET Core (Linux nebo Windows), obrázek, který má používat je společnosti microsoft nebo aspnetcore:2.0. Proto stačí zadat jaké základní image Docker budete používat pro vaše kontejneru. To uděláte tak, že přidáte od společnosti microsoft nebo aspnetcore:2.0 pro váš soubor Docker. Tím se automaticky provede Visual Studio, ale pokud jste aktualizaci verze, můžete aktualizovat tuto hodnotu.

Použití oficiální úložiště bitové kopie .NET z úložiště Docker Hub s číslem verze zajišťuje, že jsou k dispozici na všech počítačích (včetně vývoj, testování a produkci) stejné funkce jazyka.

Následující příklad ukazuje ukázkový soubor Docker pro kontejner ASP.NET Core.

```
FROM microsoft/aspnetcore:2.0
  
ARG source
  
WORKDIR /app
  
EXPOSE 80
  
COPY ${source:-obj/Docker/publish} .
  
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

V tomto případě kontejner je založen na verzi 2.0 oficiální ASP.NET Core Docker bitovou kopii (více architektura pro Linux a Windows). Toto je nastavení `FROM microsoft/aspnetcore:2.0`. (Další podrobnosti o této základní bitovou kopii, najdete v článku [ASP.NET Core Docker Image](https://hub.docker.com/r/microsoft/aspnetcore/) stránky a [.NET Core Docker Image](https://hub.docker.com/r/microsoft/dotnet/) stránky.) V soubor Docker musíte také vyzvat Docker naslouchat na portu TCP, které budete používat v době běhu (v tomto případě port 80 a jak je nakonfigurováno nastavení ZVEŘEJNĚTE).

Můžete zadat další konfiguraci nastavení v soubor Docker, v závislosti na jazyk a framework, který používáte. Například ENTRYPOINT řádek s \["dotnet", "MySingleContainerWebApp.dll"\] informuje Docker ke spuštění aplikace .NET Core. Pokud používáte sady SDK a rozhraní .NET Core příkazového řádku (dotnet rozhraní příkazového řádku) sestavení a spuštění aplikace .NET, toto nastavení by lišit. Dolní řádek je, že řádku vstupní bod a další nastavení, bude lišit v závislosti na jazyk a platformy, které zvolíte pro vaši aplikaci.

### <a name="additional-resources"></a>Další zdroje

-   **Vytváření Imagí Dockeru pro aplikace .NET Core**
    [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)

-   **Sestavení vlastní image**. V oficiální dokumentaci Docker.
    [*https://docs.docker.com/engine/tutorials/dockerimages/*](https://docs.docker.com/engine/tutorials/dockerimages/)

### <a name="using-multi-arch-image-repositories"></a>Použití více architektury image úložiště

Jednoho úložiště může obsahovat variant platformy, jako je například bitovou kopii systému Linux a bitové kopie systému Windows. Tato funkce umožňuje dodavatelům jako Microsoft (creators základní image) k vytvoření jedné úložiště tak, aby pokrývalo více platforem (který je Linux a Windows). Například [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) úložiště dostupné v registru úložiště Docker Hub poskytuje podporu pro Linux a Windows Nano Server za použití stejného názvu úložišti.

Pokud zadáte značku, cílení na platformu, která je explicitní jako v následujících případech:

-   **microsoft/aspnetcore:2.0.0-jessie**

        .NET Core 2.0 runtime-only on Linux 

-   **microsoft/aspnetcore:2.0.0-nanoserver**

        .NET Core 2.0 runtime-only on Windows Nano Server

Ale a to je nového od mid 2017, pokud zadáte stejný název bitové kopie, i se stejnou značkou, nových více architektury bitových kopií (například obrázek aspnetcore, která podporuje více architektura) bude používat verzi systému Linux nebo Windows v závislosti na Docker hostitelský operační systém, který nasazujete , jak je znázorněno v následujícím příkladu:

-   **microsoft/aspnetcore:2.0**

        Multi-arch: .NET Core 2.0 runtime-only on Linux or Windows Nano Server depending on the Docker host OS

Tímto způsobem, když načítat bitovou kopii z hostitele Windows, bude ji stáhněte Windows variant a stahování stejný název bitové kopie z hostitele platformy Linux načte Linux variant.

### <a name="option-b-creating-your-base-image-from-scratch"></a>Možnost B: vytvoření základní bitové kopie od začátku

Můžete vytvořit vlastní základní image Docker od začátku. Tento scénář se nedoporučuje pro někoho, kdo je počínaje Docker, ale pokud chcete nastavit konkrétní bity základní bitové kopie, můžete tak učinit.

### <a name="additional-resources"></a>Další zdroje

-   **Více architektury .NET Core image**.
https://github.com/dotnet/announcements/issues/14 
-   **Vytvořte základní image**. Oficiální dokumentaci Docker.
    [*https://docs.docker.com/engine/userguide/eng-image/baseimages/*](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a>Krok 3. Vytvoření vlastních imagí Dockeru a vložit vaše aplikace nebo služba

U každé služby v aplikaci musíte vytvořit související bitové kopie. Pokud vaše aplikace se skládá z jedné služby nebo webovou aplikaci, bude třeba jen jedné image.

Všimněte si, že imagí Dockeru jsou pro vás vytvořen automaticky v sadě Visual Studio. Následující kroky jsou pouze potřebné pro pracovní postup editor nebo rozhraní příkazového řádku a vysvětlení pro přehlednost o co se stane pod.

Jako vývojáře, musíte pro vývoj a testování místně, dokud nabízené dokončené funkci nebo změňte systému správy zdrojů (například na Githubu). To znamená, že potřebujete k vytvoření imagí Dockeru a k nasazení kontejnerů do místního hostitele Docker (Windows nebo virtuálního počítače s Linuxem) a spustit, testování a ladění pro tyto místní kontejnery.

Pokud chcete vytvořit vlastní image ve vašem místním prostředí pomocí příkazového řádku Dockeru a váš soubor Docker, můžete použít příkaz sestavení docker, jako obrázek 5-5.

![](./media/image8.png)

**Obrázek 5-5**. Vytvoření vlastní image Docker

Volitelně můžete místo přímo spouštět docker sestavení ze složky projektu, můžete nejdřív generovat nasadit složka se požadované knihovny .NET a binární soubory spuštěním dotnet publikování a pak použít příkaz docker sestavení.

Tím se vytvoří bitovou kopii Docker s název cesardl/netcore-webapi mikroslužbu-docker: první. V takovém případě: nejdřív se značku představující na konkrétní verzi. Tento krok můžete opakovat pro každý vlastní image, které potřebujete k vytvoření aplikace skládá Docker.

Pokud existuje žádost několika kontejnerů (to znamená, že je aplikace s více kontejnerů), můžete použít také docker compose nahoru – příkaz sestavení pro sestavení všechny související bitové kopie pomocí jednoho příkazu na základě metadat v související soubory docker-compose.yml.

Image můžete najít existující v místním úložišti pomocí docker příkaz bitové kopie, jak je znázorněno v obrázku 5 a 6.

![](./media/image9.png)

**Obrázek 5 a 6.** Zobrazení existujících bitových kopií, pomocí příkazu docker bitové kopie

### <a name="creating-docker-images-with-visual-studio"></a>Vytvoření imagí Dockeru pomocí sady Visual Studio

Pokud používáte Visual Studio k vytvoření projektu s podporou Docker, nevytvoříte explicitně bitovou kopii. Místo toho se pro vás vytvoří bitovou kopii, při stisknutím klávesy F5 a spusťte dockerized aplikace nebo služby. Tento krok je automatické v sadě Visual Studio a nebude se zobrazovat dojít, ale je důležité vědět, co se děje v dole.

![](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a>Krok 4. Definování vašim službám v docker-compose.yml při vytvoření aplikace s více kontejner Docker

[Docker-compose.yml](https://docs.docker.com/compose/compose-file/) souboru umožňuje definovat sadu související služby pro nasazení jako složený aplikace pomocí příkazů pro nasazení.

Pokud chcete použít soubor docker-compose.yml, budete muset vytvořit soubor ve vaší hlavní nebo kořenové složky řešení, s obsahem, které jsou podobné jako v následujícím příkladu:

```yml
version: '3'
  
services:

  webmvc:
    image: eshop/web
    environment:
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
    ports:
      - "80:80"
    depends_on:
      - catalog.api
      - ordering.api

  catalog.api:
    image: eshop/catalog.api
    environment: 
      - ConnectionString=Server=sql.data;Database=CatalogDB;…
    ports:
      - "81:80"
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    environment:
      - ConnectionString=Server=sql.data;Database=OrderingDb;…
    ports:
      - "82:80"
    extra_hosts:
      - "CESARDLBOOKVHD:10.0.75.1"
    depends_on:
      - sql.data

  sql.data:
    image: mssql-server-linux:latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"

```

Všimněte si, že tento soubor docker-compose.yml je zjednodušená sloučené verze. Obsahuje statický konfigurační data pro každý kontejner (jako je třeba název vlastní image), která se vztahuje vždy plus informace o konfiguraci, které může závisí na prostředí pro nasazení, jako je připojovací řetězec. V pozdějších částech se dozvíte, jak můžete rozdělit konfigurace docker-compose.yml do několika docker compose soubory a přepisujících hodnot v závislosti na typu prostředí a provádění (ladění nebo verze).

Příklad soubor docker-compose.yml definuje pět služby: službu webmvc (webová aplikace), dva mikroslužeb (catalog.api a ordering.api) a jeden datový zdroj kontejneru sql.data, založené na systému SQL Server pro Linux spuštěný jako kontejner. Každá služba je nasazený jako kontejner, a bitovou kopii Docker se vyžaduje pro každou.

Soubor docker-compose.yml určuje pouze kontejnery, které jsou používány, ale jejich jednotlivě konfiguraci. Například webmvc kontejneru definice v souboru .yml:

-   Pomocí předdefinovaných eshop / webové: nejnovější bitové kopie. Však můžete také nakonfigurovat obrázek, který má být sestaven jako součást docker compose spuštění s další konfigurací podle sestavení: v souboru docker-compose.

-   Inicializuje dvou proměnných prostředí (adresa URL katalogu a OrderingUrl).

-   Předává zveřejněné port 80 kontejneru na externím portu 80 na hostitelském počítači.

-   Odkazy na katalogu a řazení služby s webovou aplikaci závisí\_na nastavení. To způsobí, že služba Počkejte, dokud jsou tyto služby spuštěny.

Soubor docker-compose.yml v další části jsme se pokroku při nabídneme postupy pro implementaci mikroslužeb a více kontejneru aplikace.

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a>Práce s docker-compose.yml v Visual Studio 2017

Když přidáte podporu Docker řešení do projektu služby v řešení sady Visual Studio, jak je znázorněno na obrázku 5 – 7, Visual Studio přidá soubor Docker do projektu a přidá oddíl služby (projekt) ve vašem řešení se soubory docker-compose.yml. Je snadný způsob, jak spustit sestavování řešení více kontejneru. Můžete otevřít soubory docker-compose.yml a provede jejich aktualizaci s další funkce.

![](./media/image6.png)

**Obrázek 5 – 7**. Přidání podpory Docker v aplikaci Visual Studio 2017 kliknutím pravým tlačítkem na projekt ASP.NET Core

Přidání podpory Docker v sadě Visual Studio pouze přidá soubor Docker do projektu, ale přidá informace o konfiguraci několik globální docker-compose.yml souborů, které jsou nastaveny na úrovni řešení.

Po přidání podpory Docker do řešení v sadě Visual Studio, zobrazí se také nový uzel (v souboru projektu docker compose.dcproj) v Průzkumníku řešení, která obsahuje soubory přidané docker-compose.yml, jak je znázorněno v obrázku 5 až 8.

![](./media/image11.PNG)

**Obrázek 5 až 8**. **Docker compose** uzel stromu přidán do Průzkumníka řešení 2017 Visual Studio

Můžete nasadit aplikace s více kontejnerů pomocí docker-compose.yml jednoho souboru pomocí docker compose až příkaz. Však sady Visual Studio přidá skupiny, můžete přepsat hodnoty v závislosti na prostředí (vývoj a produkční) a provádění typu (vydání a ladění). Tato funkce bude vysvětlené v pozdějších částech.

![](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a>Krok 5. Sestavení a spuštění aplikace Docker

Pokud vaše aplikace má pouze jediný kontejner, můžete ho spustit publikovat na vašem hostiteli Docker (virtuálního počítače nebo fyzického serveru). Ale pokud vaše aplikace obsahuje více služeb, můžete nasadit jako složený aplikace, buď pomocí jednoduchého příkazu rozhraní příkazového řádku (docker tvoří nahoru), nebo pomocí sady Visual Studio, které budou používat tento příkaz v pozadí. Podívejme se na různé možnosti.

### <a name="option-a-running-a-single-container-with-docker-cli"></a>Možnost A: spuštěna pomocí příkazového řádku Dockeru kontejner jedním

Můžete spustit kontejner Docker pomocí docker, spusťte příkaz, stejně jako obrázek 5 – 9:

```
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

![](./media/image13.png)

**Obrázek 5-9**. Spuštění kontejner Docker pomocí docker, spusťte příkaz

V takovém případě příkaz váže interní port 5000 kontejneru na port 80 hostitelský počítač. To znamená, že je Hostitel naslouchá na portu 80 a předávání na port 5000 na kontejneru.

### <a name="option-b-running-a-multi-container-application"></a>Možnost B: spuštěna aplikace typu kontejner s více

Ve většině scénářů organizace Docker aplikace se skládá z více služeb, což znamená, že budete muset spustit aplikaci více kontejneru, jak je znázorněno v obrázku 5-10.

![](./media/image14.png)

**Obrázek 5-10**. Virtuální počítač s kontejnery Docker nasazení

#### <a name="running-a-multi-container-application-with-the-docker-cli"></a>Spuštění aplikace s více kontejnerů pomocí rozhraní příkazového řádku Dockeru

Ke spuštění aplikace s více kontejnerů pomocí rozhraní příkazového řádku Dockeru, můžete spustit docker-tvoří až příkaz. Tento soubor docker-compose.yml používá příkaz, abyste měli na úrovni řešení pro nasazení aplikace s více kontejnerů. Obrázek 5-11 zobrazuje výsledky, když spustíte příkaz z adresáře hlavní projekt, který obsahuje soubor docker-compose.yml.

![](./media/image15.png)

**Obrázek 5-11**. Příklad výsledků při spuštění docker compose až příkaz

Po docker-tvoří spuštění příkazu, aplikace a související kontejnerů jsou nasazeny do Docker hostiteli, jak je ukázáno v reprezentace virtuálních počítačů v obrázku 5-10.

#### <a name="running-and-debugging-a-multi-container-application-with-visual-studio"></a>Spuštění a ladění aplikace s více kontejnerů pomocí sady Visual Studio 

Spuštěna aplikace typu kontejner s více pomocí Visual Studio 2017 nelze získat jednodušší. Nelze spustit jenom aplikace s více kontejnerů, ale budete moci nastavení zarážek regulární ladění všechny kontejnery přímo ze sady Visual Studio.

Jak je uvedeno před pokaždé, když přidáte podporu řešení Docker na projekt v rámci řešení, tento projekt je nakonfigurovaný v souboru globální docker-compose.yml (řešení úrovni), který umožňuje spustit nebo ladění celé řešení najednou. Visual Studio spustit jeden kontejner pro každý projekt, který má povolenou podporou řešení Docker a provedení všech kroků interní pro vás (dotnet publikovat, sestavení docker atd.).

Je nutné zdůraznit, jak ukazuje obrázek 5-12, v aplikaci Visual Studio 2017 se další **Docker** příkazu pro reakce na stisknutí klávesy F5. Tato možnost umožňuje spustit nebo ladění aplikace s více kontejneru spuštěním všechny kontejnery, které jsou definovány v souborech docker-compose.yml na úrovni řešení. Možnost ladění řešení více kontejneru znamená, že můžete nastavit zarážky několik, každé zarážky v na jiný projekt (kontejner) a při ladění ze sady Visual Studio přestanete na zarážkách definované v různých projektů a systémem jiných kontejnerů.

![](./media/image16.png)

**Obrázek 5-12**. Spouštění aplikací využívajících službu kontejneru v Visual Studio 2017

### <a name="additional-resources"></a>Další zdroje

-   **Nasaďte kontejner ASP.NET vzdáleného hostitele Docker**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a>Poznámka o testování a nasazení s orchestrators

Docker compose nahoru a docker spustit příkazy (nebo spuštění a ladění kontejnerů v sadě Visual Studio) jsou pro testování kontejnery ve vašem vývojovém prostředí. Ale pokud cílíte na Docker clustery a orchestrators jako Docker Swarm, Mesosphere DC/OS nebo Kubernetes byste neměli používat tento přístup. Pokud používáte cluster jako [Docker Swarm režimu](https://docs.docker.com/engine/swarm/) (k dispozici v CE Docker pro systém Windows a Mac od verze 1.12), musíte nasadit a otestovat s další příkazy, jako je [vytvoření služby docker](https://docs.docker.com/engine/reference/commandline/service_create/) pro jeden služby. Pokud nasazujete aplikace skládá z několika kontejnerů, můžete použít [docker compose sady](https://docs.docker.com/compose/reference/bundle/) a [docker nasazení myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) se nasazení skládá aplikace jako *zásobníku*. Další informace naleznete v příspěvku blogu [představení experimentální distribuované aplikace sady](https://blog.docker.com/2016/06/docker-app-bundle/) v dokumentaci k nástroji Docker. na webu Docker.

Pro [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) a [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/) použijete jiné nasazení příkazy a skripty také.

![](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a>Krok 6. Testování aplikace Docker pomocí vašeho místního hostitele Docker

Tento krok se bude lišit v závislosti na tom, co je to vaše aplikace. Ve jednoduché rozhraní .NET Core webové aplikaci, která je nasazena jako jediný kontejner nebo služby mají přístup ke službě otevřením prohlížeče na hostiteli Docker a přejdete na tuto lokalitu, jak je znázorněno v obrázek 5 – 13. (Pokud se konfigurace v soubor Docker mapuje kontejneru na port hostitele, který je jakoukoli jinou hodnotu než 80, zahrnují hostitele se po v adrese URL.)

![](./media/image18.png)

**Obrázek 5 – 13**. Příklad testování Docker aplikace místně pomocí místního hostitele

Pokud localhost neukazuje na Docker hostitele IP (ve výchozím nastavení se při použití Docker CE by měl), přejděte na služby, použijte IP adresu vašeho počítače síťové karty.

Všimněte si, že tuto adresu URL v prohlížeči používá port 80 například konkrétním kontejneru, který je právě popsané. Však interně žádosti se protože přesměrováni na port 5000, který byl, jak byl zaveden pomocí docker, spusťte příkaz, jak je popsáno v předchozím kroku.

Také můžete testovat aplikaci pomocí curl z terminálu, jak je znázorněno v obrázku 5-14. V rámci Docker instalace v systému Windows je výchozí Docker hostitele IP vždy 10.0.75.1 kromě skutečná adresa IP počítače.

![](./media/image19.png)

**Obrázek 5-14**. Příklad testování Docker aplikace místně pomocí curl

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a>Testování a ladění kontejnery s Visual Studio 2017

Při spuštění a ladění kontejnery s Visual Studio 2017, můžete ladit aplikace .NET mnohem stejným způsobem jako při spuštění bez kontejnery.

### <a name="testing-and-debugging-without-visual-studio"></a>Testování a ladění bez sady Visual Studio

Pokud vyvíjíte pomocí editoru/CLI přístup, je obtížnější ladění kontejnerů a budete chtít ladění pomocí generování trasování.

### <a name="additional-resources"></a>Další zdroje

-   **Ladění aplikací v místním kontejner Docker**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

-   **Steve Lasker. Vytvoření, ladění, nasazení aplikací ASP.NET Core pomocí Docker.** Video.
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a>Zjednodušená pracovního postupu při vývoji kontejnery pomocí sady Visual Studio

Efektivně pracovní postup, když pomocí sady Visual Studio je mnohem jednodušší než když použijete metodu editor nebo rozhraní příkazového řádku. Většina kroky podle Docker související s soubor Docker a docker-compose.yml soubory jsou skrytý nebo zjednodušené Visual Studio, jak je znázorněno v obrázku 5-15.

![](./media/image20.png)

**Obrázek 5-15**. Zjednodušené pracovní postup, když vývoj pomocí sady Visual Studio

Kromě toho budete muset provést krok 2 (Přidání podpory Docker do vašich projektů) pouze jednou. Proto je podobná obvyklé vývojářských úloh pracovního postupu, při použití rozhraní .NET pro další vývoj. Je třeba vědět, co se děje skrytě (proces vytváření bitové kopie, jaké základní bitové kopie, kterou používáte, nasazení kontejnerů, atd.) a v některých případech, že budete také muset upravit soubor soubor Docker nebo docker-compose.yml k přizpůsobení chování. Ale většinu práce je výrazně jednodušší pomocí sady Visual Studio, což je mnohem vyšší produktivitu.

### <a name="additional-resources"></a>Další zdroje

-   **Steve Lasker. .NET – vývoj docker s Visual Studio 2017**
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)

-   **Jeffrey T. Fritz. Uveďte základní aplikace .NET v kontejneru s nové nástroje Docker pro sadu Visual Studio**
    [*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a>Nastavení Windows kontejnery pomocí příkazů prostředí PowerShell v soubor Docker 

[Kontejnery Windows](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) vám umožní převést existující aplikace Windows imagí Dockeru a nasadit je stejné nástroje jako zbytek ekosystému Docker. Pokud chcete používat Windows kontejnery, spusťte příkazy prostředí PowerShell v soubor Docker, jak je znázorněno v následujícím příkladu:

```
FROM microsoft/windowsservercore
  
LABEL Description="IIS" Vendor="Microsoft" Version="10"
  
RUN powershell -Command Add-WindowsFeature Web-Server
  
CMD [ "ping", "localhost", "-t" ]
```

V takovém případě jsme používáte základní bitovou kopii systému Windows Server Core (FROM nastavení) a instalace služby IIS pomocí příkazu prostředí PowerShell (nastavení spuštění). Podobným způsobem můžete také použít příkazy prostředí PowerShell pro nastavení dalších komponent, jako je ASP.NET 4.x, .NET 4.6 nebo jiný software pro Windows. Například následující příkaz v soubor Docker Nastaví technologii ASP.NET 4.5:

```
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a>Další zdroje

-   **aspnet-docker/Dockerfile.** Příklady příkazů prostředí Powershell pro spouštění z dockerfiles zahrnout funkce systému Windows.
    [*https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile*](https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile)

>[!div class="step-by-step"]
[Previous] (index.md) [Next] (../net-core-single-containers-linux-windows-server-hosts/index.md)
