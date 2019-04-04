---
title: Pracovní postup vývoje aplikací Dockeru
description: Zjistěte podrobnosti pracovního postupu pro vývoj aplikací založených na Dockeru. Krok za krokem začít a získat některé podrobnosti pro optimalizaci soubory Dockerfile a končit zjednodušený pracovní postup k dispozici, když pomocí sady Visual Studio.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: d494dba829d8065e2bc1424bc9bcc11e265fbcc0
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/04/2019
ms.locfileid: "58921088"
---
# <a name="development-workflow-for-docker-apps"></a>Pracovní postup vývoje aplikací Dockeru

Životním cyklu vývoje aplikací se spustí na počítači, jako vývojář, pokud kód aplikace s použitím upřednostňovaný jazyk a místně ji otestovat. S tímto pracovním postupem, bez ohledu na to, které jazyk, rozhraní a platformu zvolíte se vždy vývoj a testování kontejnery Dockeru ale uděláte místně.

Každý kontejner (instance image Dockeru) zahrnuje následující součásti:

- Operačního systému výběru, například Linux distribuce, Windows Nano Server nebo jádra serveru systému Windows.

- Soubory přidat během vývoje, například zdrojový kód a aplikace binární soubory.

- Informace o konfiguraci, jako je například nastavení prostředí a závislosti.

## <a name="workflow-for-developing-docker-container-based-applications"></a>Pracovní postup pro vývoj aplikací založených na kontejnerech Dockeru

Tato část popisuje *vnitřní smyčky* pracovní postup vývoje aplikací založených na kontejnerech Dockeru. Vnitřní smyčky pracovního postupu znamená, že není vzhledem k tomu širší DevOps pracovního postupu, který může obsahovat až po produkční nasazení a právě se zaměřuje na vývojové práce vykonané na počítači pro vývojáře. Počáteční kroky k nastavení prostředí nejsou zahrnuté, protože tyto kroky se provádějí jenom jednou.

Aplikace se skládá z vlastní služby a další knihovny (závislosti). Níže jsou uvedeny základní kroky, které obvykle provést při sestavování aplikace Dockeru, jak je znázorněno na obrázku 5-1.

![Proces vývoje aplikací Dockeru: 1 - kód vaší aplikace, 2 - zápis souboru Dockerfile/s, 3 – vytváření imagí, které jsou definovány v souboru Dockerfile/s, 4 – (volitelné) psaní služby v souboru docker-compose.yml, 5, - spuštění kontejneru nebo docker-compose aplikace, 6 – testování aplikace nebo mikroslužeb, 7 – nahrání do úložiště a opakujte tento postup. ](./media/image1.png)

**Obrázek 5-1.** Krok za krokem pracovního postupu pro vývoj Docker kontejnerizovaných aplikací

V této části je podrobně popsán tento celý proces a všemi hlavními kroky jsou vysvětleny se zaměříte na prostředí Visual Studio.

Pokud používáte metodiky vývoj editoru a rozhraní příkazového řádku (například Visual Studio Code a rozhraní příkazového řádku Dockeru v systému macOS nebo Windows), musíte znát každý krok, obecně podrobněji, než pokud používáte Visual Studio. Další informace o práci v prostředí rozhraní příkazového řádku, najdete v e kniha [životního cyklu Kontejnerizovaných aplikací Dockeru pomocí nástrojů a Microsoft Platforms](https://aka.ms/dockerlifecycleebook/).

Pokud používáte Visual Studio 2017, mnoho z těchto kroků se postará služba za vás, což výrazně zvyšuje vaši produktivitu. To platí zejména při používání sady Visual Studio 2017 a cílení vícekontejnerových aplikací. Například s jediným klepnutím myši, Visual Studio přidá soubor Dockerfile a docker-compose.yml do vašich projektů s konfigurací pro vaši aplikaci. Při spuštění aplikace v sadě Visual Studio sestaví image Dockeru a spustí vícekontejnerová aplikace přímo v Dockeru; dokonce i umožňuje ladit několik kontejnerů najednou. Tyto funkce budou zvýšit rychlost vývoje.

Ale to, že sada Visual Studio provádí tyto kroky automatického neznamená, že nepotřebujete vědět, co se děje v pod tím s Dockerem. Proto následující pokyny obsahuje podrobnosti o každém kroku.

![1 - kódu vaší aplikace](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a>Krok 1. Psaní kódu a vytvořte počáteční aplikace nebo služba směrného plánu

Vývoj aplikací Dockeru je podobným způsobem, jakým vyvíjíte aplikaci bez Dockeru. Rozdíl je, že při vývoji pro Docker, jste nasazení a testování vaší aplikace nebo služby v rámci kontejnerů Docker v místním prostředí buď (nastavení virtuálního počítače s Linuxem pomocí Dockeru), nebo přímo Windows při použití kontejnerů Windows.

### <a name="set-up-your-local-environment-with-visual-studio"></a>Nastavit místní prostředí pomocí sady Visual Studio

Pokud chcete začít, ujistěte se, že máte [Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) pro Windows nainstalované, jak je popsáno v následujících pokynech:

[Začínáme s Docker CE pro Windows](https://docs.docker.com/docker-for-windows/)

Kromě toho je třeba Visual Studio 2017 verze 15.7 nebo novější, se **vývoj pro různé platformy .NET Core** úlohy, které jsou nainstalovány, jak je znázorněno v obrázku 5-2.

![.NET core vývoj multiplatformních aplikací úloh výběru během instalace sady Visual Studio.](./media/image3.png)

**Obrázek 5-2**. Výběr **vývoj pro různé platformy .NET Core** úloh během instalace sady Visual Studio 2017

Spuštění aplikace v .NET prostý (obvykle v případě, že používání kontejnerů .NET Core) kódování ještě před povolením Docker ve vaší aplikaci a o nasazení a testování v Dockeru. Doporučujeme však začít pracovat na Docker co nejdříve, protože, které se stanou skutečnou prostředí a můžete co nejdříve zjistit všechny problémy. To je podporováno, protože Visual Studio usnadňuje tak práci s Dockerem, téměř je transparentní, představte si třeba při ladění vícekontejnerových aplikací ze sady Visual Studio.

### <a name="additional-resources"></a>Další zdroje

- **Začínáme s Docker CE pro Windows** \
  [https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/)

- **Visual Studio 2017** \
  [https://visualstudio.microsoft.com/downloads/](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

![2 - zapisovat soubory Dockerfile](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a>Krok 2. Vytvoření souboru Dockerfile související s existující základní image .NET

Budete potřebovat soubor Dockerfile pro každý vlastní image, kterou chcete sestavit. soubor Dockerfile pro každý kontejner má být nasazen, musíte také, jestli nasadit automaticky ze sady Visual Studio nebo ručně pomocí rozhraní příkazového řádku Dockeru (spuštění docker a docker-compose příkazů). Pokud vaše aplikace obsahuje jeden vlastní službu, potřebujete jeden soubor Dockerfile. Pokud vaše aplikace obsahuje více služeb (stejně jako v architektuře mikroslužeb), budete potřebovat jeden soubor Dockerfile pro každou službu.

Soubor Dockerfile je umístěn v kořenové složce aplikace nebo služby. Obsahuje příkazy, které informace tom, jak nastavit a spustit vaše aplikace nebo služby v kontejneru Dockeru. Můžete ručně vytvořit soubor Dockerfile v kódu a přidejte do projektu spolu s .NET závislosti.

Pomocí sady Visual Studio a jeho nástrojů Dockeru tato úloha vyžaduje jenom několik kliknutí myší. Při vytváření nového projektu v sadě Visual Studio 2017 je k dispozici možnost s názvem **podpora povolit kontejnerů (Dockeru)**, jak je znázorněno v obrázek 5-3.

![Povolit podporu Dockeru políčko při vytváření nového projektu ASP.NET Core v sadě Visual Studio 2017](./media/image5.png)

**Obrázek 5 – 3**. Povolení podpory Dockeru, při vytváření nového projektu ASP.NET Core v sadě Visual Studio 2017

Můžete také povolit podporu Dockeru na existující projekt webové aplikace ASP.NET Core kliknutím pravým tlačítkem myši na projekt v **Průzkumníka řešení** a vyberete **přidat** > **podporu Dockeru** , jak je znázorněno v obrázek 5 – 4.

![Přidat možnost nabídky podpory Dockeru v sadě Visual Studio](./media/image6.png)

**Obrázek 5 – 4**. Povolení podpory Dockeru v existujícím projektu Visual Studio 2017

Tato akce přidá *soubor Dockerfile* do projektu s požadovanou konfigurací a je dostupná pouze na projekty ASP.NET Core.

Podobným způsobem můžete sady Visual Studio také přidat soubor docker-compose.yml pro celé řešení s možností **Přidat > Podpora Orchestrátoru kontejnerů**. V kroku 4 se podíváme podrobněji tuto možnost.

### <a name="using-an-existing-official-net-docker-image"></a>Použití existující oficiální image .NET Dockeru

Obvykle vytvoříte vlastní image kontejneru nad základní image, můžete získat z oficiální úložiště, třeba [Docker Hubu](https://hub.docker.com/) registru. To je přesně co se stane na pozadí, když povolíte podporu Dockeru v sadě Visual Studio. Váš soubor Dockerfile použije existující `aspnetcore` bitové kopie.

Dříve jsme vysvětlit, které Image Dockeru a úložiště můžete použít, v závislosti na rozhraní framework a rozhodli jste se operační systém. Například pokud chcete používat ASP.NET Core (s Linuxem nebo Windows), obrázku je `mcr.microsoft.com/dotnet/core/aspnet:2.2`. Proto stačí zadat jaké základní image Dockeru, který budete používat pro váš kontejner. Můžete to udělat tak, že přidáte `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2` na vašem souboru Dockerfile. To se automaticky provede pomocí sady Visual Studio, ale pokud byste chtěli aktualizovat verzi, aktualizujte tuto hodnotu.

Použití oficiální úložiště .NET image z Docker Hubu s číslem verze zajistí, že stejné funkce jazyka jsou k dispozici na všech počítačích (včetně vývoje, testování a produkce).

Následující příklad ukazuje ukázkový soubor Dockerfile pro kontejner služby ASP.NET Core.

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
ARG source
WORKDIR /app
EXPOSE 80
COPY ${source:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

V tomto případě bitovou kopii podle verze 2.2 oficiální image Dockeru ASP.NET Core (více arch pro systémy Linux a Windows). Toto je nastavení `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`. (Další informace o této základní image, najdete v článku [Image Dockeru .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) stránky.) V souboru Dockerfile potřebujete také dáte pokyn, aby Docker pro naslouchání na portu TCP, které se použijí v době běhu (v tomto případě portem 80, nakonfigurované s nastavením VYSTAVENÍ).

Můžete zadat další nastavení konfigurace v souboru Dockerfile, v závislosti na jazyk a rozhraní, které používáte. Například řádek ENTRYPOINT s `["dotnet", "MySingleContainerWebApp.dll"]` říká Dockeru spustit aplikaci .NET Core. Pokud používáte sadu SDK a rozhraní .NET Core CLI (rozhraní příkazového řádku dotnet) k sestavení a spuštění aplikace .NET, toto nastavení bude jiný. Dolní řádek je, že řádku vstupního bodu a další nastavení budou lišit v závislosti na jazyku a platformě, kterou zvolíte pro vaši aplikaci.

### <a name="additional-resources"></a>Další zdroje

- **Vytváření Imagí Dockeru pro aplikace .NET Core** \
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](../../../core/docker/building-net-docker-images.md)

- **Vytvoření vlastní image**. V oficiální dokumentaci k Dockeru. \
  [https://docs.docker.com/engine/tutorials/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/)

- **Udržování aktuálnosti s Imagí kontejnerů v rozhraní .NET** \
  <https://devblogs.microsoft.com/dotnet/staying-up-to-date-with-net-container-images/>

- **Pomocí .NET a Dockeru společně - DockerCon 2018 Update** \
  <https://devblogs.microsoft.com/dotnet/using-net-and-docker-together-dockercon-2018-update/>

### <a name="using-multi-arch-image-repositories"></a>Pomocí více architektury image úložišť

Jediné úložiště může obsahovat variant, platformy, jako jsou image Linuxu a Windows image. Tato funkce umožňuje dodavatelé, jako je Microsoft (creators základní image) k vytvoření jednoho úložiště pro víc platforem (to znamená operačních systémů Linux a Windows). Například [dotnet/jádro](https://hub.docker.com/_/microsoft-dotnet-core/) úložiště k dispozici v registru Docker Hub poskytuje podporu pro systémy Linux a Windows Nano Server pomocí stejného názvu úložiště.

Je-li zadat značky, cílení na platformu, která je explicitní jako v následujících případech:

- `microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim` \
  Cíle: .NET Core 2.2 pouze modul runtime v Linuxu

- `microsoft/dotnet:2.2-aspnetcore-runtime-nanoserver-1809` \
  Cíle: .NET Core 2.2 pouze modul runtime Windows Nano server

Ale pokud zadáte stejný název image, i se stejnou značkou, více architektury obrázky (jako `aspnetcore` image) používat verzi systému Linux nebo Windows v závislosti na operačním systému hostitele Docker, že nasazujete, jak je znázorněno v následujícím příkladu:

- `microsoft/dotnet:2.2-aspnetcore-runtime` \
  Více arch: .NET Core 2.2 runtime jen v systému Linux nebo Windows Nano serveru v závislosti na operačním systému hostitele Docker

Tímto způsobem, když si stáhnete obrázek z hostitele Windows, je přetáhne Windows variant a přebírání z hostitele platformy Linux stejný název image přetáhne varianty Linuxu.

### <a name="multi-stage-builds-in-dockerfile"></a>Vícefázových sestavení v souboru Dockerfile

Soubor Dockerfile je podobný dávkový skript. Podobně jako co děláte, pokud jste museli nainstalovat počítač z příkazového řádku.

Začíná základní image, který nastaví kolekci počáteční kontextu, je stejně jako při spuštění systému souborů, který je umístěný na hostitelském operačním systému. Není operační systém, ale můžete si představit Pokud jako "the" OS uvnitř kontejneru.

Spuštění každou příkazového řádku vytvoří novou vrstvu v systému souborů se změnami z předchozí, tak, aby v kombinaci, vytvářejí výsledný systému souborů.

Protože každé nové vrstvě "ponechá" nad předchozí a výsledné velikost bitové kopie se zvyšuje s každý příkaz, bitové kopie mohou být velmi rozsáhlé, že pokud se mají zahrnout, například sady SDK potřebných k vytváření a publikování aplikace.

Je to, kde získat vícefázových sestavení do diagramů (od Dockeru 17.05 a vyšší) provedete jejich magic.

Cílem core je, že můžete oddělit proces spuštění souboru Dockerfile ve fázích, kde fázi je počáteční obrázek za nímž následuje jedna nebo více příkazů, a poslední fáze Určuje velikost finální bitové kopie.

Stručně řečeno vícefázových sestavení povolit rozdělení vytvoření v jiné "fáze" a pak sestavit finální image trvá pouze relevantní adresářů z dílčích etap. Obecná strategie pro použití této funkce je:

1. Pomocí základní image SDK (nebude vadit, jak velké), se vším potřebným k sestavení a publikování aplikace do složky a potom

2. Použít bitovou kopii základní, malé, pouze modul runtime a zkopírujte složky pro publikování z předchozí fáze k vytvoření malé konečném obrazu.

Pravděpodobně nejlepší způsob, jak porozumět vícefázové prochází souboru Dockerfile podrobně, řádek po řádku, můžeme začít s počáteční soubor Dockerfile vytvořených pomocí Visual Studia při přidání Dockeru k projektu a později se dostat do některé optimalizace.

Počáteční souboru Docker může vypadat přibližně takto:

```Dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:2.2 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS build
 6  WORKDIR /src
 7  COPY src/Services/Catalog/Catalog.API/Catalog.API.csproj …
 8  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.AspNetCore.HealthChecks … 
 9  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions.HealthChecks …
10  COPY src/BuildingBlocks/EventBus/IntegrationEventLogEF/ …
11  COPY src/BuildingBlocks/EventBus/EventBus/EventBus.csproj …
12  COPY src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.csproj …
13  COPY src/BuildingBlocks/EventBus/EventBusServiceBus/EventBusServiceBus.csproj …
14  COPY src/BuildingBlocks/WebHostCustomization/WebHost.Customization …
15  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions …
16  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions …
17  RUN dotnet restore src/Services/Catalog/Catalog.API/Catalog.API.csproj
18  COPY . .
19  WORKDIR /src/src/Services/Catalog/Catalog.API
20  RUN dotnet build Catalog.API.csproj -c Release -0 /app
21
22  FROM build AS publish
23  RUN dotnet publish Catalog.API.csproj -c Release -0 /app
24
25  FROM base AS final
26  WORKDIR /app
27  COPY --from=publish /app
28  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

A jedná se o řádek po řádku:

1.  Začít fáze "malé" pouze modul runtime základní Image, pojmenujte ji **základní** pro referenci.
2.  Vytvoření **/app** adresáře v bitové kopii.
3.  Zveřejnit port **80**.
<!-- skip -->
5.  Volání begin nové fáze "velký" Image pro vytváření a publikování **sestavení** pro referenci.
6.  Vytvořit adresář **/src** na obrázku.
7.  Až po řádek 16 kopírovat odkazované projekty **.csproj** soubory, abyste mohli později obnovit balíčky.
<!-- skip -->
17. Obnovení balíčků pro **Catalog.API** projektu a odkazované projekty.
18. Kopírování **strom volání adresář pro řešení** (s výjimkou součástí soubory a adresáře **.dockerignore** souboru) z k **/src** adresáře v bitové kopii.
19. Změna aktuální složku na **Catalog.API** projektu.
20. Sestavení projektu (a další závislosti projektu) a výstup do **/app** adresáře v bitové kopii.
<!-- skip -->
22. Začít nový fázi budete pokračovat z buildu, pojmenujte ji **publikovat** pro referenci.
23. Publikování projektu (a závislostí) a výstup do **/app** adresáře v bitové kopii.
<!-- skip -->
25. Začít nový fázi pokračováním z **základní** a volejte jej **konečný**
26. Změňte aktuální adresář na **/app**
27. Kopírovat **/app** z fáze **publikovat** do aktuálního adresáře
28. Definování příkazu ke spuštění při spuštění kontejneru.

Nyní Pojďme prozkoumat některé optimalizace pro zlepšení výkonu celého procesu, v případě aplikaci eShopOnContainers, to znamená asi 22 minut nebo déle vytvářet kompletní řešení v kontejnery Linuxu.

Budete využívat Docker vrstva mezipaměti funkci, která je poměrně jednoduchý: Pokud základní image a příkazy jsou stejné jako některé dříve spuštěn, může použít pouze výsledné vrstvy bez nutnosti provádět příkazy, a ušetřit tak nějakou dobu.

Tedy zaměřme se na **sestavení** řádky 5 až 6 jsou většinou stejné fázi, ale řádky 7-17 se liší pro každou službu v aplikaci eShopOnContainers, tak mají k provedení pokaždé, když jeden, ale pokud jste změnili řádky 7 – 16:

```
COPY . .
```

Pak budou platit stejně pro každou službu budou zkopírovány celé řešení a vytvořila větší vrstvy, ale:

1) Proces kopírování by být provedeny pouze první (a při opětovném sestavování při změně souboru) a bude používat mezipaměť pro všechny ostatní služby a

2) Protože větší obrázek k ve stadiu zprostředkující ho, nemá vliv na velikost finální bitové kopie.

Zahrnuje další významné optimalizace `restore` příkaz proveden v řádku 17, které se také pro každou službu aplikaci eShopOnContainers. Pokud změníte tento řádek jenom:

```console
RUN dotnet restore
```

To by obnovení balíčků pro celé řešení, ale pak znovu ji by udělat jenom jednou, namísto 15 časy s aktuální strategie.

Ale `dotnet restore` spuštěna pouze pokud je jeden projekt nebo soubor řešení ve složce, takže dosažení tohoto cíle je o něco složitější a způsob, jak vyřešit, aniž do příliš mnoho podrobností, je to:

1) Přidejte následující řádky do **.dockerignore**:

   - `*.sln`, chcete-li ignorovat všechny soubory řešení ve stromové struktuře složek hlavní

   - `!eShopOnContainers-ServicesAndWebApps.sln`, chcete-li zahrnout pouze tento soubor řešení.

2) Zahrnout `/ignoreprojectextensions:.dcproj` argument `dotnet restore`, tak také ignoruje docker-compose projektu a obnoví pouze zadané balíčky pro aplikaci eShopOnContainers ServicesAndWebApps řešení.

Poslední optimalizace prostě se to děje, že řádek 20 je redundantní, jako řádku 23 také sestavení aplikace a dodává, v podstatě hned po řádku 20, takže existuje přejde jiného příkazu časově náročné.

Výsledný soubor bude:

```Dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:2.2 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS publish
 6  WORKDIR /src
 7  COPY . .
 8  RUN dotnet restore /ignoreprojectextensions:.dcproj
 9  WORKDIR /src/src/Services/Catalog/Catalog.API
10  RUN dotnet publish Catalog.API.csproj -c Release -0 /app
11
12  FROM base AS final
13  WORKDIR /app
14  COPY --from=publish /app
15  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

### <a name="creating-your-base-image-from-scratch"></a>Vytvoření základní image od začátku

Vlastní základní image Dockeru můžete vytvořit úplně od začátku. Tento scénář se nedoporučuje pro uživatele, který se spouští s Dockerem, ale pokud chcete nastavit konkrétní bity základní image, můžete tak učinit.

### <a name="additional-resources"></a>Další zdroje

- **Více architektury .NET Core imagí**. \
  [https://github.com/dotnet/announcements/issues/14](https://github.com/dotnet/announcements/issues/14)

- **Vytvoření základní image**. Oficiální dokumentace k Dockeru. \
  [https://docs.docker.com/engine/userguide/eng-image/baseimages/](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![3. vytvoření imagí, které jsou definované na soubory Dockerfile](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a>Krok 3. Vytvoření vlastní Image Dockeru a vložit vaše aplikace nebo služba

Pro každou službu v aplikaci budete muset vytvořit související image. Pokud vaše aplikace se skládá z jedné služby nebo webové aplikace, potřebujete jenom jedné image.

Všimněte si, že Image Dockeru se vytváří automaticky za vás v sadě Visual Studio. Následující kroky jsou jenom potřebné pro pracovní postup editoru a rozhraní příkazového řádku a vysvětlení pro přehlednost o co se stane pod.

Jako vývojář, potřebujete pro vývoj a testování místně, než přejdete dokončené funkce nebo změňte na systému správy zdrojů (například na Githubu). To znamená, že budete muset vytvoření imagí Dockeru a nasazení kontejnerů do místního hostitele Docker (Windows nebo linuxového virtuálního počítače) a spuštění, testování a ladění pro tyto místní kontejnery.

Vytvoření vlastní image v místním prostředí pomocí rozhraní příkazového řádku Dockeru a vašem souboru Dockerfile, můžete použít příkaz sestavení dockeru, jako obrázek 5 – 5.

![Obrazovka průběhu sestavování image Dockeru](./media/image8.png)

**Obrázek 5 až 5**. Vytvoření vlastní image Dockeru

Volitelně můžete místo přímo spouštět sestavení dockeru ze složky projektu, můžete nejdřív vygenerovat nasaditelný složka se požadované knihovny .NET a binární soubory spuštěním `dotnet publish`a pak použít `docker build` příkazu.

Tím se vytvoří image Dockeru s názvem `cesardl/netcore-webapi-microservice-docker:first`. V takovém případě: nejprve je klíčové slovo představující konkrétní verzi. Tento krok můžete opakovat pro každý vlastní image, které potřebujete k vytvoření aplikace skládá Dockeru.

Když aplikaci tvoří několik kontejnerů (to znamená, že je vícekontejnerová aplikace), můžete použít také `docker-compose up --build` příkazu sestavte všechny obrázky související s jediným příkazem s využitím metadat v souboru docker-compose.yml související .

Najdete existujících bitových kopií ve vašem místním úložišti s využitím dockeru příkaz bitové kopie, jak je znázorněno v obrázek 5 a 6.

![Zobrazení imagí výpis z příkazu Image dockeru](./media/image9.png)

**Obrázek 5 a 6.** Zobrazení existujících imagí pomocí příkazu Image dockeru

### <a name="creating-docker-images-with-visual-studio"></a>Vytváření imagí Dockeru pomocí sady Visual Studio

Při vytvoření projektu s podporou Dockeru pomocí sady Visual Studio, není explicitně vytvořit bitovou kopii. Místo toho na obrázku je vytvořen po stisknutí klávesy **F5** (nebo **Ctrl-F5**) pro spuštění dockerized aplikace nebo služby. Tento krok je automatické v sadě Visual Studio a neuvidíte to uděláme, ale je důležité vědět, co se děje v pod tím.

![4 – (volitelné) psaní služby v souboru docker-compose.yml](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a>Krok 4. Definování vašich služeb v docker-compose.yml při sestavování aplikace Dockeru

[Docker-compose.yml](https://docs.docker.com/compose/compose-file/) souboru umožňuje definovat sadu souvisejících služeb umožňující nasadit ho jako aplikace skládá pomocí příkazů nasazení. Nakonfiguruje taky její vztahy závislostí a konfiguraci za běhu.

Pokud chcete použít soubor docker-compose.yml, je potřeba vytvořit soubor ve vaší hlavní nebo kořenové složky řešení, s obsahem podobné jako v následujícím příkladu:

```yml
version: '3.4'

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
      - ConnectionString=Server=sql.data;Port=1433;Database=CatalogDB;…
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

Tento soubor docker-compose.yml je zjednodušený a sloučené verze. Obsahuje statické konfigurační data pro každý kontejner (např. název vlastní image), které je vždycky potřeba a konfigurační informace, které může záviset na prostředí pro nasazení, jako je připojovací řetězec. V dalších částech se dozvíte, jak k rozdělení docker-compose.yml konfigurace do několika docker-compose soubory a hodnot v závislosti na prostředí a spuštění typu (ladění nebo vydání).

Příklad souboru docker-compose.yml definuje čtyři služby: `webmvc` service (webová aplikace), dva mikroslužby (`ordering.api` a `basket.api`) a jedním datovým zdrojového kontejneru `sql.data`založená na systému SQL Server pro Linux spuštěný jako kontejner. Každá služba se nasadí jako kontejner, takže image Dockeru je povinné pro každý.

Soubor docker-compose.yml určuje nejen jaké kontejnery jsou používány, ale jejich jednotlivě konfiguraci. Například `webmvc` definice kontejneru ve soubor .yml:

- Používá předem připravené `eshop/web:latest` bitové kopie. Ale můžete také nakonfigurovat na obrázku má být sestaven jako součást docker-compose spuštění další konfigurace podle sestavení: oddíl v souboru docker-compose.

- Inicializuje dvou proměnných prostředí (adresa URL katalogu a OrderingUrl).

- Předává vystavené port 80 v kontejneru pro externí port 80 na hostitelském počítači.

- Odkazy webové aplikace v katalogu a řazení služby s nastavením depends_on. To způsobí, že služba Počkejte, dokud tyto služby jsou spuštěny.

Soubor docker-compose.yml v další části jsme se opakování při popisujeme k implementaci mikroslužeb a vícekontejnerových aplikací.

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a>Práce s docker-compose.yml v sadě Visual Studio 2017

Kromě souboru Dockerfile přidat do projektu, jak už jsme zmínili dřív, a sady Visual Studio 2017 (od 15.8 na) můžete přidat podporu orchestrátoru Docker Compose do řešení.

Když přidat podporu orchestrátoru kontejnerů, jak ukazuje obrázek 5 – 7 pro první spuštění sady Visual Studio vytvoří soubor Dockerfile pro projekt a vytvoří nový projekt (oddíl služby) ve vašem řešení s několika globálních `docker-compose*.yml` soubory a pak přidá projekt na tyto soubory. Pak můžete otevřít soubory docker-compose.yml a aktualizovat o další funkce.

Budete muset opakovat tento formulář operace každý projekt, který chcete zahrnout do souboru docker-compose.yml.

V době psaní tohoto návodu Visual Studio podporuje Docker Compose a Service Fabric, orchestrátorů.

![Možnost místní nabídky do projektu aplikace ASP.NET Core přidat podporu orchestrátoru](./media/image21.png)

**Obrázek 5 – 7**. Přidání podpory Dockeru kliknutím pravým tlačítkem myši projekt ASP.NET Core v sadě Visual Studio 2017

Po přidání podpory nástroje orchestrator do svého řešení v sadě Visual Studio se zobrazí nový uzel (v `docker-compose.dcproj` souboru projektu) v Průzkumníku řešení, která obsahuje soubory přidané docker-compose.yml, jak je znázorněno v obrázek 5 až 8.

![docker-compose uzlu v Průzkumníkovi řešení](./media/image11.png)

**Obrázek 5 až 8**. **Docker-compose** uzel stromu přidá v okně Průzkumník řešení Visual Studio 2017

Můžete nasadit vícekontejnerové aplikace pomocí docker-compose.yml jeden soubor s použitím `docker-compose up` příkazu. Visual Studio, ale přidá skupinu z nich tak mohou přepsat hodnoty v závislosti na prostředí (vývojové nebo produkční prostředí) a typu spuštění (vydání nebo ladícího). Tato funkce bude je popsáno v předchozích částech.

![5 – spouštění kontejnerů nebo vytvořit aplikaci](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a>Krok 5. Sestavte a spusťte aplikaci v Dockeru

Pokud vaše aplikace má pouze jeden kontejner, můžete ji spustit po nasazení na hostitele Docker (virtuální počítač nebo fyzický server). Nicméně pokud vaše aplikace obsahuje několik služeb, můžete nasadit ho jako aplikace skládá buď pomocí jediného příkazu rozhraní příkazového řádku (docker-compose up), nebo pomocí sady Visual Studio, které budou používat tento příkaz na pozadí. Podívejme se na různé možnosti.

### <a name="option-a-running-a-single-container-application"></a>Možnost A: Spuštění aplikace jeden kontejner

#### <a name="using-docker-cli"></a>Pomocí rozhraní příkazového řádku Dockeru

Můžete spustit pomocí kontejneru Dockeru `docker run` příkaz, jak je znázorněno v obrázek 5 až 9:

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

Výše uvedený příkaz vytvoří novou instanci kontejneru ze zadané bitové kopie, pokaždé, když je spuštěn. Můžete použít `--name` parametr zadejte název kontejneru a pak použijte `docker start {name}` (nebo použijte id kontejneru a název automatického) ke spuštění existující instanci kontejneru.

![Zobrazení při spuštění kontejneru Dockeru pomocí dockeru, spusťte příkaz](./media/image13.png)

**Obrázek 5 až 9**. Spuštěný kontejner Docker s využitím dockeru, spusťte příkaz

Příkaz v tomto případě váže interní port 5000 z kontejneru na port 80 hostitelském počítači. To znamená, že hostitel naslouchá na portu 80 a předává na portu 5000 v kontejneru.

Hodnota hash uvedené je id kontejneru a jí také přiřazena náhodné čitelný název Pokud `--name` není použita možnost.

#### <a name="using-visual-studio"></a>Pomocí sady Visual Studio

Pokud jste nepřidali podporu orchestrátoru kontejnerů, můžete použít také aplikaci s jedním kontejnerem v sadě Visual Studio stisknutím klávesy **Ctrl-F5** a můžete také použít **F5** pro ladění aplikace v kontejneru. Kontejner spustí v místním prostředí s využitím dockeru, spusťte.

### <a name="option-b-running-a-multi-container-application"></a>Možnost B: Spuštění aplikace

Ve většině scénářů organizace aplikaci v Dockeru se skládá z více služeb, což znamená, že budete muset spustit vícekontejnerové aplikace, jak je znázorněno v obrázek 5 až 10.

![Virtuální počítač s několika kontejnery Dockeru](./media/image14.png)

**Obrázek 5 až 10**. Virtuální počítač s kontejnery Dockeru nasazené

#### <a name="using-docker-cli"></a>Pomocí rozhraní příkazového řádku Dockeru

Ke spuštění vícekontejnerové aplikace pomocí rozhraní příkazového řádku Dockeru, můžete použít `docker-compose up` příkazu. Tento příkaz používá **docker-compose.yml** souboru, abyste měli na úrovni řešení nasazení vícekontejnerových aplikací. Obrázek 5 – 11 můžete vidět výsledky při spuštění příkazu z adresáře hlavní řešení, která obsahuje soubor docker-compose.yml.

![Obrazovky zobrazení při spuštění docker-compose up příkaz](./media/image15.png)

**Obrázek 5 – 11**. Příklad výsledků při spuštění docker-compose up příkaz

Po docker-compose up spuštění příkazu, aplikace a její související kontejnery se nasazují do hostitele Dockeru, jak je znázorněno v obrázek 5 – 10.

#### <a name="using-visual-studio"></a>Pomocí sady Visual Studio

Spuštění vícekontejnerové aplikace pomocí sady Visual Studio 2017 nejde získat žádná jednodušší. Stačí stisknout **Ctrl-F5** ke spuštění nebo **F5** ladění, jako obvykle, nastavení **docker-compose** projekt jako spouštěný projekt.  Visual Studio zpracovává všechny potřebné instalační program, tak můžete vytvořit obvyklým zarážky a ladit co nakonec stanou nezávislé procesů spuštěných ve "vzdálené servery", stejně jako je například.

Jak už bylo zmíněno dříve, pokaždé, když přidáte řešení podpory Dockeru do projektu v rámci řešení, že projekt je nakonfigurovaný v souboru globální docker-compose.yml (na úrovni řešení), která umožňuje spustit nebo ladit celé řešení najednou. Visual Studio spustit jeden kontejner pro každý projekt, který podporuje Docker řešení povolené a provedení všech kroků interní za vás (dotnet publikovat, sestavení dockeru atd.).

Pokud chcete provést náhled vůbec drudgery, podívejte se na soubor:

`{root solution folder}\obj\Docker\docker-compose.vs.debug.g.yml`

Důležitý bod je, že, jak je znázorněno v obrázek 5 – 12, v sadě Visual Studio 2017 Další **Docker** příkaz pro akci klíčové F5. Tato možnost umožňuje spustit nebo ladit vícekontejnerová aplikace spuštěním všechny kontejnery, které jsou definovány v souboru docker-compose.yml na úrovni řešení. Možnost ladit více kontejnerů řešení znamená, že můžete nastavit několik zarážky, každé zarážky v jiném projektu (kontejner) a při ladění ze sady Visual Studio se zastaví na zarážkách definovány v různých projektech a běží na různé kontejnery.

![Visual Studio ladění nástrojů spuštění docker-compose projektu](./media/image16.png)

**Obrázek 5 – 12**. Spouštění vícekontejnerových aplikací v sadě Visual Studio 2017

### <a name="additional-resources"></a>Další zdroje

- **Nasazení kontejneru ASP.NET na vzdáleného hostitele Docker** \
  [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a>Poznámka k testování a nasazení s orchestrátory

Docker-compose up a příkazy dockeru spustit (nebo spouštění a ladění kontejnerů v sadě Visual Studio) jsou dostatečné pro testování kontejnerů ve vašem vývojovém prostředí. Ale tento přístup byste neměli používat v produkčních prostředích, kde je orchestrátorů, jako je cílem [Kubernetes](https://kubernetes.io/) nebo [Service Fabric](https://azure.microsoft.com/services/service-fabric/). Pokud používáte Kubernetes je nutné použít [podů](https://kubernetes.io/docs/concepts/workloads/pods/pod/) k uspořádání kontejnery a [služby](https://kubernetes.io/docs/concepts/services-networking/service/) k síti je. Můžete také použít [nasazení](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) k uspořádání pod vytváření a úpravy.

![6 – testování aplikace nebo mikroslužeb](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a>Krok 6. Otestujte aplikaci Dockeru pomocí místního hostitele Docker

Tento krok se liší v závislosti na tom, co aplikace dělá. V jednoduchou aplikaci webového rozhraní .NET Core, který je nasazen jako jedním kontejnerem nebo služby můžete přístup ke službě otevřením prohlížeče na hostitele Dockeru a přejdete na tomto webu, jak je znázorněno v obrázek 5-13. (Pokud se konfigurace v souboru Dockerfile mapuje kontejneru na port na hostiteli není nic jiného než 80, zahrnovat port hostitele v adrese URL.)

![Zobrazit v prohlížeči reakce na koncový bod rozhraní API](./media/image18.png)

**Obrázek 5-13**. Příklad testování vašich aplikací Dockeru s místním prostředí s využitím místního hostitele

Pokud localhost neukazuje na Dockeru IP adresa hostitele (ve výchozím nastavení se při použití Docker CE by měl), přejděte k vaší službě, můžete IP adresu síťové karty v počítači.

Všimněte si, že tato adresa URL v prohlížeči používá port 80, třeba konkrétní kontejner diskutovány. Ale interně požadavky přesměrováni na portu 5000, protože bylo jak nasazení s prostředím docker, spusťte příkaz, jak je popsáno v předchozím kroku.

Můžete také test aplikace pomocí curl z terminálu, jak je znázorněno v obrázek 5-14. V instalaci Dockeru na Windows IP adresa hostitele Docker výchozí hodnota je vždy 10.0.75.1 kromě vlastní IP adresu vašeho počítače.

![Zobrazení reakce na koncový bod rozhraní API pomocí curl](./media/image19.png)

**Obrázek 5-14**. Příklad testování vašich aplikací Dockeru s místně pomocí curl

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a>Testování a ladění kontejnerů pomocí sady Visual Studio 2017

Při spouštění a ladění kontejnerů pomocí sady Visual Studio 2017, můžete ladit aplikaci .NET v podstatě stejným způsobem jako při spuštění bez kontejnery.

### <a name="testing-and-debugging-without-visual-studio"></a>Testování a ladění bez sady Visual Studio

Pokud vyvíjíte pomocí editoru/CLI přístup, ladění kontejnerů je obtížnější a budete chtít ladit vygenerováním trasování.

### <a name="additional-resources"></a>Další zdroje

- **Ladění aplikací v místním kontejneru Dockeru** \
  [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

- **Steve Lasker. Sestavení, ladění, nasazení aplikace ASP.NET Core s Dockerem.** Video. \
  [https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a>Zjednodušené pracovní postupy při vývoji kontejnery pomocí sady Visual Studio

Efektivně pracovní postup při používání sady Visual Studio je mnohem jednodušší než při použití editoru/CLI přístup. Většina kroků vyžadují Docker související s soubor Dockerfile a soubory docker-compose.yml jsou skryta nebo zjednodušená sada Visual Studio, jak je znázorněno v obrázek 5 – 15.

![Zjednodušená pracovního postupu vývoje kontejneru pomocí sady Visual Studio: 1 - kódu vaší aplikace, 2 - podporu Dockeru přidat do projektů (jen jednou), 3 – spuštění kontejneru nebo docker-compose aplikace, 4 – testování aplikace nebo mikroslužeb, 5 – nahrání do úložiště a opakujte tento postup.](./media/image20.png)

**Obrázek 5 – 15**. Zjednodušené pracovní postupy při vývoji pomocí sady Visual Studio

Kromě toho budete muset provést krok 2 (Přidání podpory Dockeru do vašich projektů) pouze jednou. Proto je podobný běžné vývojářské úlohy pracovního postupu, při použití rozhraní .NET pro další vývoj. Je potřeba vědět, co se děje na pozadí (procesu sestavení, jaké základní Image, kterou používáte, nasazení kontejnerů, atd.) a v některých případech bude také nutné upravit soubor Dockerfile nebo docker-compose.yml k přizpůsobení chování. Ale většinu práce výrazně zjednodušuje použití sady Visual Studio, což je mnohem vyšší produktivitu.

### <a name="additional-resources"></a>Další zdroje

- **Steve Lasker. Vývoj na platformě .NET dockeru pomocí sady Visual Studio 2017** \
  [https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a>Pomocí příkazů prostředí PowerShell v souboru Dockerfile k nastavení kontejnery Windows 

[Kontejnery Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/index) umožňují převést svoje stávající aplikace pro Windows do Image Dockeru a nasadit je pomocí stejných nástrojů jako ostatní ekosystému Dockeru. Pokud chcete používat kontejnery Windows, spusťte příkazy Powershellu v souboru Dockerfile, jak je znázorněno v následujícím příkladu:

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

- **ASPNET dockeru/Dockerfile.** Příklady příkazů Powershellu spouštět z soubory dockerfile začlenit funkce Windows. \
  [https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile](https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile)

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](../multi-container-microservice-net-applications/index.md)
