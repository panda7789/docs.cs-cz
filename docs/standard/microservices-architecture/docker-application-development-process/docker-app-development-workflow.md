---
title: Pracovní postup vývoje aplikací Dockeru
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Pracovní postup vývoje aplikací Dockeru
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: b7115530c44321dc2a10be3996c14429591b611f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401977"
---
# <a name="development-workflow-for-docker-apps"></a>Pracovní postup vývoje aplikací Dockeru

Životní cyklus vývoje aplikací začíná každý vývojář počítače, ve kterém vývojář kódy aplikace pomocí jejich upřednostňovaný jazyk a testy místně. Bez ohledu na to, které jazyk, rozhraní a platformě vývojář rozhodne pro tento pracovní postup vývojář je vždy vývoj a testování kontejnery Dockeru, ale uděláte místně.

Každý kontejner (instance image Dockeru) zahrnuje následující součásti:

-   Výběr operačního systému, (například Linuxová distribuce vytvořená, Windows Nano serveru nebo Windows Server Core).

-   Soubory přidané vývojář (binární soubory aplikace atd.).

-   Informace o konfiguraci (nastavení prostředí a závislosti).

## <a name="workflow-for-developing-docker-container-based-applications"></a>Pracovní postup pro vývoj aplikací založených na kontejnerech Dockeru

Tato část popisuje *vnitřní smyčky* pracovní postup vývoje aplikací založených na kontejnerech Dockeru. Vnitřní smyčky pracovního postupu znamená, že se zohledněním širší pracovních postupů DevOps a právě se zaměřuje na vývojové práce vykonané na počítači pro vývojáře. Počáteční kroky k nastavení prostředí nejsou zahrnuty, protože ty se provede jen jednou.

Aplikace se skládá z vlastní služby a další knihovny (závislosti). Níže jsou uvedeny základní kroky, které obvykle provést při sestavování aplikace Dockeru, jak je znázorněno na obrázku 5-1.

![](./media/image1.png)

**Obrázek 5-1.** Krok za krokem pracovního postupu pro vývoj Docker kontejnerizovaných aplikací

V této příručce je podrobně popsán tento celý proces a všemi hlavními kroky jsou vysvětleny se zaměříte na prostředí Visual Studio.

Při použití metodiky vývoj editoru a rozhraní příkazového řádku (například Visual Studio Code a rozhraní příkazového řádku Dockeru v systému macOS nebo Windows), musíte znát každý krok, obecně podrobnější než při použití sady Visual Studio. Podrobné informace o práci v prostředí rozhraní příkazového řádku najdete v elektronické příručce [životního cyklu Kontejnerizovaných aplikací Dockeru pomocí nástrojů a Microsoft Platforms](https://aka.ms/dockerlifecycleebook/).

Pokud používáte Visual Studio 2015 nebo Visual Studio 2017, mnoho z těchto kroků se postará služba za vás, což výrazně zvyšuje vaši produktivitu. To platí zejména při používání sady Visual Studio 2017 a cílení vícekontejnerových aplikací. Například s jediným klepnutím myši, Visual Studio přidá soubor Dockerfile a docker-compose.yml do vašich projektů s konfigurací pro vaši aplikaci. Při spuštění aplikace v sadě Visual Studio sestaví image Dockeru a spustí vícekontejnerová aplikace přímo v Dockeru; dokonce i umožňuje ladit několik kontejnerů najednou. Tyto funkce budou zvýšit rychlost vývoje.

Ale to, že sada Visual Studio provádí tyto kroky automatického neznamená, že nepotřebujete vědět, co se děje v pod tím s Dockerem. Proto v dokumentu, který následuje, můžeme podrobně každý krok.

![](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a>Krok 1. Psaní kódu a vytvořte počáteční aplikace nebo služba směrného plánu

Vývoj aplikací Dockeru je podobným způsobem, jakým vyvíjíte aplikaci bez Dockeru. Rozdíl je, že při vývoji pro Docker, máte nasazení a testování vaší aplikace nebo služby v rámci kontejnerů Docker v místním prostředí. Kontejner může být kontejneru Linuxu nebo kontejner Windows.

### <a name="set-up-your-local-environment-with-visual-studio"></a>Nastavit místní prostředí pomocí sady Visual Studio

Pokud chcete začít, ujistěte se, že máte [Docker Community Edition (CE)](https://www.docker.com/community-edition) pro Windows nainstalované, jak je popsáno v následujících pokynech:

[Začínáme s Docker CE pro Windows](https://docs.docker.com/docker-for-windows/)

Kromě toho budete potřebovat nainstalovanou sadu Visual Studio 2017. To je upřednostňována před Visual Studio 2015 se sadou Visual Studio Tools for Docker – doplněk, protože Visual Studio 2017 obsahuje další pokročilé podpora pro Docker, jako je podpora pro ladění kontejnerů. Visual Studio 2017 obsahuje nástroje pro Docker, pokud jste vybrali **.NET Core a Docker** úloh během instalace, jak je znázorněno v obrázku 5-2.

![](./media/image3.png)

**Obrázek 5-2**. Výběr **.NET Core a Docker** úloh během instalace sady Visual Studio 2017

Můžete začít kódování aplikace v .NET prostý (obvykle v .NET Core, pokud máte v úmyslu používat kontejnery) ještě před povolením Docker ve vaší aplikaci a o nasazení a testování v Dockeru. Doporučujeme však začít pracovat na Docker co nejdříve, protože, které se stanou skutečnou prostředí a můžete co nejdříve zjistit všechny problémy. To je podporováno, protože Visual Studio usnadňuje tak práci s Dockerem, téměř je transparentní, představte si třeba při ladění vícekontejnerových aplikací ze sady Visual Studio.

### <a name="additional-resources"></a>Další zdroje

-   **Začínáme s Docker CE pro Windows**
    [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)

-   **Visual Studio 2017**
    [*https://visualstudio.microsoft.com/downloads/*](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

![](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a>Krok 2. Vytvoření souboru Dockerfile související s existující základní image .NET

Budete potřebovat soubor Dockerfile pro každý vlastní image, kterou chcete sestavit. soubor Dockerfile pro každý kontejner má být nasazen, musíte také, jestli nasadit automaticky ze sady Visual Studio nebo ručně pomocí rozhraní příkazového řádku Dockeru (spuštění docker a docker-compose příkazů). Pokud vaše aplikace obsahuje jeden vlastní službu, potřebujete jeden soubor Dockerfile. Pokud vaše aplikace obsahuje více služeb (stejně jako v architektuře mikroslužeb), budete potřebovat jeden soubor Dockerfile pro každou službu.

Soubor Dockerfile je umístěn v kořenové složce aplikace nebo služby. Obsahuje příkazy, které informace tom, jak nastavit a spustit vaše aplikace nebo služby v kontejneru Dockeru. Můžete ručně vytvořit soubor Dockerfile v kódu a přidejte do projektu spolu s .NET závislosti.

Pomocí sady Visual Studio a jeho nástrojů Dockeru tato úloha vyžaduje jenom několik kliknutí myší. Při vytváření nového projektu v sadě Visual Studio 2017 je k dispozici možnost s názvem **podpora povolit kontejnerů (Dockeru)**, jak je znázorněno v obrázek 5-3.

![](./media/image5.png)

**Obrázek 5 – 3**. Povolení podpory Dockeru, při vytváření nového projektu v sadě Visual Studio 2017

Můžete také povolit podporu Dockeru na nového nebo existujícího projektu tak, že pravým tlačítkem myši na soubor projektu v sadě Visual Studio a výběrem možnosti **Docker přidat projekt podporovat**, jak je znázorněno v obrázek 5 – 4.

![](./media/image6.png)

**Obrázek 5 – 4**. Povolení podpory Dockeru v existujícím projektu Visual Studio 2017

Tato akce na projektu (například webové aplikace ASP.NET nebo webové rozhraní API služby) přidá do projektu s požadovanou konfigurací souboru Dockerfile. Také přidá soubor docker-compose.yml pro celé řešení. V následujících částech popisujeme informace, které přejde do každé z těchto souborů. Visual Studio může provést tuto práci za vás, ale je užitečné k pochopení, co je potřeba k souboru Dockerfile.

### <a name="option-a-creating-a-project-using-an-existing-official-net-docker-image"></a>Odpověď: možnost Vytvoření projektu pomocí existující oficiální image .NET Dockeru

Obvykle vytvoříte vlastní image kontejneru nad základní image, můžete získat z oficiální úložiště na [Docker Hubu](https://hub.docker.com/) registru. To je přesně co se stane na pozadí, když povolíte podporu Dockeru v sadě Visual Studio. Váš soubor Dockerfile použije existující image aspnetcore.

Dříve jsme vysvětlit, které Image Dockeru a úložiště můžete použít, v závislosti na rozhraní framework a rozhodli jste se operační systém. Například pokud chcete používat ASP.NET Core (s Linuxem nebo Windows), obrázku je microsoft / aspnetcore:2.0. Proto stačí zadat jaké základní image Dockeru, který budete používat pro váš kontejner. Můžete to udělat tak, že přidáte od Microsoftu nebo aspnetcore:2.0 na vašem souboru Dockerfile. To se automaticky provede pomocí sady Visual Studio, ale pokud byste chtěli aktualizovat verzi, aktualizujte tuto hodnotu.

Použití oficiální úložiště .NET image z Docker Hubu s číslem verze zajistí, že stejné funkce jazyka jsou k dispozici na všech počítačích (včetně vývoje, testování a produkce).

Následující příklad ukazuje ukázkový soubor Dockerfile pro kontejner služby ASP.NET Core.

```Dockerfile
FROM microsoft/aspnetcore:2.0
  
ARG source
  
WORKDIR /app
  
EXPOSE 80
  
COPY ${source:-obj/Docker/publish} .
  
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

V tomto případě kontejner je založená na verzi 2.0 oficiální Image Dockeru ASP.NET Core (více arch pro systémy Linux a Windows). Toto je nastavení `FROM microsoft/aspnetcore:2.0`. (Další podrobnosti o této základní image, najdete v článku [Image Dockeru ASP.NET Core](https://hub.docker.com/r/microsoft/aspnetcore/) stránky a [Image Dockeru .NET Core](https://hub.docker.com/r/microsoft/dotnet/) stránky.) V souboru Dockerfile potřebujete také dáte pokyn, aby Docker pro naslouchání na portu TCP, které se použijí v době běhu (v tomto případě portem 80, nakonfigurované s nastavením VYSTAVENÍ).

Můžete zadat další nastavení konfigurace v souboru Dockerfile, v závislosti na jazyk a rozhraní, které používáte. Například řádek ENTRYPOINT s \["dotnet", "MySingleContainerWebApp.dll"\] říká Dockeru spustit aplikaci .NET Core. Pokud používáte sadu SDK a rozhraní .NET Core CLI (rozhraní příkazového řádku dotnet) k sestavení a spuštění aplikace .NET, toto nastavení bude jiný. Dolní řádek je, že řádku vstupního bodu a další nastavení budou lišit v závislosti na jazyku a platformě, kterou zvolíte pro vaši aplikaci.

### <a name="additional-resources"></a>Další zdroje

-   **Vytváření Imagí Dockeru pro aplikace .NET Core**
    [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)

-   **Vytvoření vlastní image**. V oficiální dokumentaci k Dockeru.
    [*https://docs.docker.com/engine/tutorials/dockerimages/*](https://docs.docker.com/engine/tutorials/dockerimages/)

### <a name="using-multi-arch-image-repositories"></a>Pomocí více architektury image úložišť

Jediné úložiště může obsahovat variant, platformy, jako jsou image Linuxu a Windows image. Tato funkce umožňuje dodavatelé, jako je Microsoft (creators základní image) k vytvoření jednoho úložiště pro víc platforem (to znamená operačních systémů Linux a Windows). Například [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) úložiště k dispozici v registru Docker Hub poskytuje podporu pro systémy Linux a Windows Nano Server pomocí stejného názvu úložiště.

Je-li zadat značky, cílení na platformu, která je explicitní jako v následujících případech:

-   **microsoft/aspnetcore:2.0.0-jessie**

        .NET Core 2.0 runtime-only on Linux 

-   **microsoft/aspnetcore:2.0.0-nanoserver**

        .NET Core 2.0 runtime-only on Windows Nano Server

Ale a toto je nový od poloviny 2017, pokud zadáte stejný název image, i se stejnou značkou, nových imagí více architektury (např. image aspnetcore, která podporuje více arch) budou používat verzi systému Linux nebo Windows v závislosti na nasazujete hostitele Docker operačního systému , jak je znázorněno v následujícím příkladu:

-   **microsoft/aspnetcore:2.0**

        Multi-arch: .NET Core 2.0 runtime-only on Linux or Windows Nano Server depending on the Docker host OS

Tímto způsobem, když si stáhnete obrázek z hostitele Windows, je přetáhne Windows variant a přebírání z hostitele platformy Linux stejný název image přetáhne varianty Linuxu.

### <a name="option-b-creating-your-base-image-from-scratch"></a>Možnost B: vytvoříte základní image od začátku

Vlastní základní image Dockeru můžete vytvořit úplně od začátku. Tento scénář se nedoporučuje pro uživatele, který se spouští s Dockerem, ale pokud chcete nastavit konkrétní bity základní image, můžete tak učinit.

### <a name="additional-resources"></a>Další zdroje

-   **Více architektury .NET Core imagí**.
https://github.com/dotnet/announcements/issues/14 
-   **Vytvoření základní image**. Oficiální dokumentace k Dockeru.
    [*https://docs.docker.com/engine/userguide/eng-image/baseimages/*](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a>Krok 3. Vytvoření vlastní Image Dockeru a vložit vaše aplikace nebo služba

Pro každou službu v aplikaci budete muset vytvořit související image. Pokud vaše aplikace se skládá z jedné služby nebo webové aplikace, potřebujete jenom jedné image.

Všimněte si, že Image Dockeru se vytváří automaticky za vás v sadě Visual Studio. Následující kroky jsou jenom potřebné pro pracovní postup editoru a rozhraní příkazového řádku a vysvětlení pro přehlednost o co se stane pod.

Jako vývojář, potřebujete pro vývoj a testování místně, než přejdete dokončené funkce nebo změňte na systému správy zdrojů (například na Githubu). To znamená, že budete muset vytvoření imagí Dockeru a nasazení kontejnerů do místního hostitele Docker (Windows nebo linuxového virtuálního počítače) a spuštění, testování a ladění pro tyto místní kontejnery.

Vytvoření vlastní image v místním prostředí pomocí rozhraní příkazového řádku Dockeru a vašem souboru Dockerfile, můžete použít příkaz sestavení dockeru, jako obrázek 5 – 5.

![](./media/image8.png)

**Obrázek 5 až 5**. Vytvoření vlastní image Dockeru

Volitelně můžete místo přímo spouštět sestavení dockeru ze složky projektu, můžete nejdřív vygenerovat nasaditelný složka se požadované knihovny .NET a binární soubory spuštěním dotnet publikovat a použijte příkaz sestavení dockeru.

Tím se vytvoří image Dockeru s název cesardl/netcore-webapi mikroslužeb – docker: první. V takovém případě: nejprve je klíčové slovo představující konkrétní verzi. Tento krok můžete opakovat pro každý vlastní image, které potřebujete k vytvoření aplikace skládá Dockeru.

Když aplikaci tvoří několik kontejnerů (to znamená, že je vícekontejnerová aplikace), můžete použít také docker-compose up - příkaz sestavení k sestavení všechny obrázky související s jediným příkazem s využitím metadat v související soubory docker-compose.yml.

Najdete existujících bitových kopií ve vašem místním úložišti s využitím dockeru příkaz bitové kopie, jak je znázorněno v obrázek 5 a 6.

![](./media/image9.png)

**Obrázek 5 a 6.** Zobrazení existujících imagí pomocí příkazu Image dockeru

### <a name="creating-docker-images-with-visual-studio"></a>Vytváření imagí Dockeru pomocí sady Visual Studio

Při použití sady Visual Studio k vytvoření projektu s podporou Dockeru, nevytvoříte explicitně bitovou kopii. Místo toho image se vytvoří za vás při stisknutí klávesy F5 a spusťte dockerized aplikaci nebo službě. Tento krok je automatické v sadě Visual Studio a to uděláme nezobrazí, ale je důležité vědět, co se děje v pod tím.

![](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a>Krok 4. Definování vašich služeb v docker-compose.yml při sestavování aplikace Dockeru

[Docker-compose.yml](https://docs.docker.com/compose/compose-file/) souboru umožňuje definovat sadu souvisejících služeb umožňující nasadit ho jako aplikace skládá pomocí příkazů nasazení.

Pokud chcete použít soubor docker-compose.yml, je potřeba vytvořit soubor ve vaší hlavní nebo kořenové složky řešení, s obsahem podobné jako v následujícím příkladu:

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

Všimněte si, že tento soubor docker-compose.yml je zjednodušený a sloučené verze. Obsahuje statické konfigurační data pro každý kontejner (např. název vlastní image), která se vždy vztahuje, a navíc informace o konfiguraci, která může záviset na prostředí pro nasazení, jako je připojovací řetězec. V dalších částech se dozvíte, jak můžete rozdělit do několika konfiguraci docker-compose.yml docker-compose soubory a hodnot v závislosti na prostředí a spuštění typu (ladění nebo vydání).

Příklad souboru docker-compose.yml definuje čtyři služby: webmvc service (webová aplikace), dva mikroslužby (catalog.api a ordering.api) a jeden datový zdroj kontejnery sql.data, založené na systému SQL Server pro Linux spuštěný jako kontejner. Každá služba se nasadí jako kontejner, takže image Dockeru je povinné pro každý.

Soubor docker-compose.yml určuje nejen jaké kontejnery jsou používány, ale jejich jednotlivě konfiguraci. Například webmvc definice kontejneru ve soubor .yml:

-   Pomocí předem sestavených eshop / webové: nejnovější verzi image. Ale můžete také nakonfigurovat na obrázku má být sestaven jako součást docker-compose spuštění další konfigurace podle sestavení: oddíl v souboru docker-compose.

-   Inicializuje dvou proměnných prostředí (adresa URL katalogu a OrderingUrl).

-   Předává vystavené port 80 v kontejneru pro externí port 80 na hostitelském počítači.

-   Odkazy webové aplikace v katalogu a řazení služby s závisí\_na nastavení. To způsobí, že služba Počkejte, dokud tyto služby jsou spuštěny.

Soubor docker-compose.yml v další části jsme se opakování při popisujeme k implementaci mikroslužeb a vícekontejnerových aplikací.

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a>Práce s docker-compose.yml v sadě Visual Studio 2017

Když přidáte podporu Dockeru řešení do projektu služby v řešení sady Visual Studio, jak je znázorněno v obrázek 5 – 7, Visual Studio do vašeho projektu přidá soubor Dockerfile a přidá oddíl služby (projekt) v rámci vašeho řešení se soubory docker-compose.yml. Je snadný způsob, jak spustit sestavování vašich řešení více kontejnerů. Pak můžete otevřít soubory docker-compose.yml a aktualizovat o další funkce.

![](./media/image6.png)

**Obrázek 5 – 7**. Přidání podpory Dockeru kliknutím pravým tlačítkem myši projekt ASP.NET Core v sadě Visual Studio 2017

Přidání podpory Dockeru v sadě Visual Studio pouze do vašeho projektu přidá soubor Dockerfile, ale přidá informace o konfiguraci na několik souborů docker-compose.yml globální, které jsou nastaveny na úrovni řešení.

Po přidání podpory Dockeru do svého řešení v sadě Visual Studio, zobrazí se také nový uzel (v souboru projektu dockeru compose.dcproj) v Průzkumníku řešení, která obsahuje soubory přidané docker-compose.yml, jak je znázorněno v obrázek 5 až 8.

![](./media/image11.PNG)

**Obrázek 5 až 8**. **Docker-compose** uzel stromu přidá v okně Průzkumník řešení Visual Studio 2017

Můžete nasadit vícekontejnerové aplikace pomocí docker-compose.yml jeden soubor s použitím docker-compose up příkazu. Ale sady Visual Studio přidá skupinu z nich, mohou přepsat hodnoty v závislosti na prostředí (vývojové oproti produkčním prostředí) a spuštění typu (vydání a ladění). Tato funkce bude je popsáno v předchozích částech.

![](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a>Krok 5. Sestavte a spusťte aplikaci v Dockeru

Pokud vaše aplikace má pouze jeden kontejner, můžete ji spustit po nasazení na hostitele Docker (virtuální počítač nebo fyzický server). Nicméně pokud vaše aplikace obsahuje několik služeb, můžete nasadit ho jako aplikace skládá buď pomocí jediného příkazu rozhraní příkazového řádku (docker-compose up), nebo pomocí sady Visual Studio, které budou používat tento příkaz na pozadí. Podívejme se na různé možnosti.

### <a name="option-a-running-a-single-container-with-docker-cli"></a>Možnost A: spuštěný jeden kontejner pomocí rozhraní příkazového řádku Dockeru

Můžete spustit kontejner Docker s využitím dockeru, spusťte příkaz jako obrázek 5 až 9:

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

![](./media/image13.png)

**Obrázek 5 až 9**. Spuštěný kontejner Docker s využitím dockeru, spusťte příkaz

Příkaz v tomto případě váže interní port 5000 z kontejneru na port 80 hostitelském počítači. To znamená, že hostitel naslouchá na portu 80 a předává na portu 5000 v kontejneru.

### <a name="option-b-running-a-multi-container-application"></a>Možnost B: systémem vícekontejnerová aplikace

Ve většině scénářů organizace aplikaci v Dockeru se skládá z více služeb, což znamená, že budete muset spustit vícekontejnerové aplikace, jak je znázorněno v obrázek 5 až 10.

![](./media/image14.png)

**Obrázek 5 až 10**. Virtuální počítač s kontejnery Dockeru nasazené

#### <a name="running-a-multi-container-application-with-the-docker-cli"></a>Spuštění vícekontejnerové aplikace pomocí rozhraní příkazového řádku Dockeru

Ke spuštění vícekontejnerové aplikace pomocí rozhraní příkazového řádku Dockeru, můžete spustit docker-compose up příkazu. Tento soubor používá docker-compose.yml příkaz, abyste měli na úrovni řešení nasazení vícekontejnerových aplikací. Obrázek 5 – 11 můžete vidět výsledky při spuštění příkazu z adresáře hlavního projektu, který obsahuje soubor docker-compose.yml.

![](./media/image15.png)

**Obrázek 5 – 11**. Příklad výsledků při spuštění docker-compose up příkaz

Po docker-compose up spuštění příkazu, aplikace a její související kontejnery se nasazují do hostitele Dockeru, jak je znázorněno v reprezentaci virtuálního počítače v obrázek 5 – 10.

#### <a name="running-and-debugging-a-multi-container-application-with-visual-studio"></a>Spouštění a ladění vícekontejnerové aplikace pomocí sady Visual Studio 

Nelze získat jednodušší systémem vícekontejnerové aplikace pomocí sady Visual Studio 2017. Nelze spustit pouze vícekontejnerové aplikace, ale budete moci ladit jejím kontejnerům přímo ze sady Visual Studio tak, že nastavíte pravidelné zarážky.

Jak už bylo zmíněno dříve, pokaždé, když přidáte řešení podpory Dockeru do projektu v rámci řešení, že projekt je nakonfigurovaný v souboru globální docker-compose.yml (na úrovni řešení), která umožňuje spustit nebo ladit celé řešení najednou. Visual Studio spustit jeden kontejner pro každý projekt, který podporuje Docker řešení povolené a provedení všech kroků interní za vás (dotnet publikovat, sestavení dockeru atd.).

Důležitý bod je, že, jak je znázorněno v obrázek 5 – 12, v sadě Visual Studio 2017 Další **Docker** příkaz pro akci klíčové F5. Tato možnost umožňuje spustit nebo ladit vícekontejnerová aplikace spuštěním všechny kontejnery, které jsou definovány v souboru docker-compose.yml na úrovni řešení. Možnost ladit více kontejnerů řešení znamená, že můžete nastavit několik zarážky, každé zarážky v jiném projektu (kontejner) a při ladění ze sady Visual Studio se zastaví na zarážkách definovány v různých projektech a běží na různé kontejnery.

![](./media/image16.png)

**Obrázek 5 – 12**. Spouštění vícekontejnerových aplikací v sadě Visual Studio 2017

### <a name="additional-resources"></a>Další zdroje

-   **Nasazení kontejneru ASP.NET na vzdáleného hostitele Docker**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a>Poznámka k testování a nasazení s orchestrátory

Docker-compose up a příkazy dockeru spustit (nebo spouštění a ladění kontejnerů v sadě Visual Studio) jsou dostatečné pro testování kontejnerů ve vašem vývojovém prostředí. Ale tento přístup byste neměli používat, pokud cílíte na clustery Dockeru a orchestrátorů, jako je Docker Swarm, Mesosphere DC/OS nebo Kubernetes. Pokud používáte cluster jako [režim Docker Swarm](https://docs.docker.com/engine/swarm/) (k dispozici v Docker CE pro Windows a Mac od verze 1.12), musíte nasadit a testovat pomocí dalších příkazů, jako jsou [vytvoření služby docker](https://docs.docker.com/engine/reference/commandline/service_create/) pro jednotné služby. Pokud nasazujete aplikace skládá z několika kontejnerů, můžete použít [docker compose sady](https://docs.docker.com/compose/reference/bundle/) a [docker nasazení myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) se nasazení skládá aplikace jako *zásobníku*. Další informace naleznete v příspěvku blogu [Představujeme experimentální distribuované aplikace sady](https://blog.docker.com/2016/06/docker-app-bundle/) v dokumentaci k Dockeru. na serveru Docker.

Pro [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) a [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/) použijete jiné nasazení příkazy a skripty také.

![](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a>Krok 6. Otestujte aplikaci Dockeru pomocí místního hostitele Docker

Tento krok se liší v závislosti na tom, co aplikace dělá. V jednoduchou aplikaci webového rozhraní .NET Core, který je nasazen jako jedním kontejnerem nebo služby můžete přístup ke službě otevřením prohlížeče na hostitele Dockeru a přechodu k této lokalitě, jak je znázorněno v obrázek 5-13. (Pokud se konfigurace v souboru Dockerfile mapuje kontejneru na port na hostiteli není nic jiného než 80, zahrnovat port hostitele v adrese URL.)

![](./media/image18.png)

**Obrázek 5-13**. Příklad testování vašich aplikací Dockeru s místním prostředí s využitím místního hostitele

Pokud localhost neukazuje na Dockeru IP adresa hostitele (ve výchozím nastavení se při použití Docker CE by měl), přejděte k vaší službě, můžete IP adresu síťové karty v počítači.

Všimněte si, že tato adresa URL v prohlížeči používá port 80, třeba konkrétní kontejner diskutovány. Ale interně požadavky přesměrováni na portu 5000, protože bylo jak nasazení s prostředím docker, spusťte příkaz, jak je popsáno v předchozím kroku.

Můžete také test aplikace pomocí curl z terminálu, jak je znázorněno v obrázek 5-14. V instalaci Dockeru na Windows IP adresa hostitele Docker výchozí hodnota je vždy 10.0.75.1 kromě vlastní IP adresu vašeho počítače.

![](./media/image19.png)

**Obrázek 5-14**. Příklad testování vašich aplikací Dockeru s místně pomocí curl

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a>Testování a ladění kontejnerů pomocí sady Visual Studio 2017

Při spouštění a ladění kontejnerů pomocí sady Visual Studio 2017, můžete ladit aplikaci .NET v podstatě stejným způsobem jako při spuštění bez kontejnery.

### <a name="testing-and-debugging-without-visual-studio"></a>Testování a ladění bez sady Visual Studio

Pokud vyvíjíte pomocí editoru/CLI přístup, je obtížnější ladění kontejnerů a budete chtít ladit vygenerováním trasování.

### <a name="additional-resources"></a>Další zdroje

-   **Ladění aplikací v místním kontejneru Dockeru**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

-   **Steve Lasker. Sestavení, ladění, nasazení aplikace ASP.NET Core s Dockerem.** Video.
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a>Zjednodušené pracovní postupy při vývoji kontejnery pomocí sady Visual Studio

Efektivně pracovní postup při používání sady Visual Studio je mnohem jednodušší než při použití editoru/CLI přístup. Většina kroků vyžadují Docker související s soubor Dockerfile a soubory docker-compose.yml jsou skryta nebo zjednodušená sada Visual Studio, jak je znázorněno v obrázek 5 – 15.

![](./media/image20.png)

**Obrázek 5 – 15**. Zjednodušené pracovní postupy při vývoji pomocí sady Visual Studio

Kromě toho budete muset provést krok 2 (Přidání podpory Dockeru do vašich projektů) pouze jednou. Proto je podobný běžné vývojářské úlohy pracovního postupu, při použití rozhraní .NET pro další vývoj. Je potřeba vědět, co se děje na pozadí (procesu sestavení, jaké základní Image, kterou používáte, nasazení kontejnerů, atd.) a v některých případech bude také nutné upravit soubor Dockerfile nebo docker-compose.yml k přizpůsobení chování. Ale většinu práce výrazně zjednodušuje použití sady Visual Studio, což je mnohem vyšší produktivitu.

### <a name="additional-resources"></a>Další zdroje

-   **Steve Lasker. Vývoj na platformě .NET dockeru pomocí sady Visual Studio 2017**
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)

-   **Jeffrey T. Fritz. Vložte aplikace .NET Core v kontejneru pomocí nového nástroje Dockeru pro Visual Studio**
    [*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a>Pomocí příkazů prostředí PowerShell v souboru Dockerfile k nastavení kontejnery Windows 

[Kontejnery Windows](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) umožňují převést svoje stávající aplikace pro Windows do Image Dockeru a nasadit je pomocí stejných nástrojů jako ostatní ekosystému Dockeru. Pokud chcete používat kontejnery Windows, spusťte příkazy Powershellu v souboru Dockerfile, jak je znázorněno v následujícím příkladu:

```Dockerfile
FROM microsoft/windowsservercore
  
LABEL Description="IIS" Vendor="Microsoft" Version="10"
  
RUN powershell -Command Add-WindowsFeature Web-Server
  
CMD [ "ping", "localhost", "-t" ]
```

V tomto případě jsme se pomocí základní image jádra serveru systému Windows (od nastavení) a instalace služby IIS pomocí příkazu prostředí PowerShell (nastavení spuštění). Podobným způsobem můžete také použít příkazy prostředí PowerShell nastavit další komponenty, jako je ASP.NET 4.x, .NET 4.6 nebo jiný software pro Windows. Například následující příkaz v souboru Dockerfile Nastaví technologii ASP.NET 4.5:

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a>Další zdroje

-   **aspnet-docker/Dockerfile.** Příklady příkazů Powershellu spouštět z soubory dockerfile začlenit funkce Windows.
    [*https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile*](https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile)

>[!div class="step-by-step"]
[Předchozí](index.md)
[další](../net-core-single-containers-linux-windows-server-hosts/index.md)
