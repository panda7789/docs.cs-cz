---
title: Pracovní postup vývoje aplikací Dockeru
description: Seznamte se s podrobnostmi pracovního postupu pro vývoj aplikací založených na Dockeru. Začněte krok za krokem a získejte do některých podrobností pro optimalizaci dockerfiles a zakončujte zjednodušeným pracovním postupem, který je k dispozici při použití sady Visual Studio.
ms.date: 01/30/2020
ms.openlocfilehash: 2f380c840e186c345f9222aa6b0cf1097a74874e
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389200"
---
# <a name="development-workflow-for-docker-apps"></a>Pracovní postup vývoje aplikací Dockeru

Životní cyklus vývoje aplikace začíná u vašeho počítače jako vývojář, kde aplikaci kódujete pomocí upřednostňovaného jazyka a testujete ji místně. S tímto pracovním postupem, bez ohledu na to, jaký jazyk, architekturu a platformu zvolíte, vždy vyvíjíte a testujete kontejnery Dockeru, ale děláte to místně.

Každý kontejner (instance image Dockeru) obsahuje následující součásti:

- Výběr operačního systému, například linuxová distribuce, Windows Nano Server nebo Windows Server Core.

- Soubory přidané během vývoje, například zdrojový kód a binární soubory aplikace.

- Informace o konfiguraci, jako je například nastavení prostředí a závislosti.

## <a name="workflow-for-developing-docker-container-based-applications"></a>Pracovní postup pro vývoj aplikací založených na kontejnerech Dockeru

Tato část popisuje pracovní postup vývoje *vnitřní smyčky* pro aplikace založené na kontejnerech Dockeru. Pracovní postup vnitřní smyčky znamená, že nezvažuje širší pracovní postup DevOps, který může zahrnovat až do produkčního nasazení, a zaměřuje se pouze na vývojovou práci provedenou v počítači vývojáře. Počáteční kroky k nastavení prostředí nejsou zahrnuty, protože tyto kroky se provádí pouze jednou.

Aplikace se skládá z vlastních služeb a další knihovny (závislosti). Následují základní kroky, které obvykle provedete při vytváření aplikace Dockeru, jak je znázorněno na obrázku 5-1.

:::image type="complex" source="./media/docker-app-development-workflow/life-cycle-containerized-apps-docker-cli.png" alt-text="Diagram znázorňující 7 kroků potřebných k vytvoření kontejnerizované aplikace.":::
Proces vývoje pro aplikace Docker: 1 - Kód vaší aplikace, 2 - Zápis Dockerfile/s, 3 - Vytvoření bitových kopií definovaných na Dockerfile/s, 4 - (volitelné) Compose služby v docker-compose.yml souboru, 5 - Spustit kontejner nebo docker-compose aplikace, 6 - Test aplikace nebo mikroslužeb, 7 - Push to repo a opakovat.
:::image-end:::

**Obrázek 5-1.** Podrobný pracovní postup pro vývoj kontejnerizovaných aplikací Dockeru

V této části je celý tento proces podrobně popsán a každý důležitý krok je vysvětlen zaměřením na prostředí sady Visual Studio.

Pokud používáte přístup k vývoji editoru a rozhraní CLI (například Visual Studio Code plus Docker CLI v macOS nebo Windows), musíte znát každý krok, obecně podrobněji, než když používáte Visual Studio. Další informace o práci v prostředí rozhraní pro nastavení rozhraní se křidýlku najdete v tématu životní [cyklus aplikací Containerized Docker u e-knihy Containerized Docker Application s platformami a nástroji microsoftu](https://aka.ms/dockerlifecycleebook/).

Když používáte Visual Studio 2019, mnoho z těchto kroků jsou zpracovány za vás, což výrazně zvyšuje vaši produktivitu. To platí zejména v případě, že používáte Visual Studio 2019 a cílení na aplikace s více kontejnery. Například s jedním kliknutím myši, Visual `Dockerfile` `docker-compose.yml` Studio přidá a soubor do vašich projektů s konfigurací pro vaši aplikaci. Když spustíte aplikaci v sadě Visual Studio, vytvoří image Dockeru a spustí aplikaci s více kontejnery přímo v Dockeru; dokonce umožňuje ladit několik kontejnerů najednou. Tyto funkce zvýší rychlost vašeho vývoje.

Ale jen proto, že Visual Studio dělá tyto kroky automatické neznamená, že nepotřebujete vědět, co se děje pod docker. Proto následující pokyny podrobnosti každý krok.

![Obrázek kroku 1.](./media/docker-app-development-workflow/step-1-code-your-app.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a>Krok 1. Spuštění kódování a vytvoření počátečního směrného plánu aplikace nebo služby

Vývoj aplikace Dockeru je podobný způsobu vývoje aplikace bez Dockeru. Rozdíl je v tom, že při vývoji pro Docker nasazujete a testujete aplikace nebo služby spuštěné v kontejnerech Dockeru ve vašem místním prostředí (buď nastavení virtuálního počítače s Linuxem dockerem, nebo přímo Windows, pokud používáte kontejnery Windows).

### <a name="set-up-your-local-environment-with-visual-studio"></a>Nastavení místního prostředí pomocí sady Visual Studio

Chcete-li začít, ujistěte se, že máte nainstalovanou [dockerovou verzi Community Edition (CE)](https://docs.docker.com/docker-for-windows/) pro systém Windows, jak je vysvětleno v následujících pokynech:

[Začínáme s Dockerem CE pro Windows](https://docs.docker.com/docker-for-windows/)

Kromě toho potřebujete Visual Studio 2019 verze 16.4 nebo novější, s nainstalovanou **úlohou pro vývoj napříč platformami .NET Core,** jak je znázorněno na obrázku 5-2.

![Snímek obrazovky s výběrem vývoje napříč platformami .NET Core](./media/docker-app-development-workflow/dotnet-core-cross-platform-development.png)

**Obrázek 5-2**. Výběr **úlohy vývoje napříč platformami .NET Core** během instalace Visual Studia 2019

Můžete začít kódovat aplikaci ve formátu plain .NET (obvykle v .NET Core, pokud plánujete používat kontejnery) ještě před povolením Dockeru ve vaší aplikaci a nasazením a testováním v Dockeru. Doporučujeme však začít pracovat na Dockeru co nejdříve, protože to bude skutečné prostředí a všechny problémy mohou být zjištěny co nejdříve. To je doporučeno, protože Visual Studio umožňuje tak snadno pracovat s Dockeru, že se téměř cítí transparentní – nejlepší příklad při ladění aplikací s více kontejnery z Visual Studia.

### <a name="additional-resources"></a>Další zdroje

- **Začínáme s Dockerem CE pro Windows** \
  <https://docs.docker.com/docker-for-windows/>

- **Visual Studio 2019** \
  [https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

![Obrázek kroku 2.](./media/docker-app-development-workflow/step-2-write-dockerfile.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a>Krok 2. Vytvoření souboru Dockerfile souvisejícího s existující základní bitovou bitovou kopii rozhraní .NET

Potřebujete Dockerfile pro každou vlastní image, kterou chcete vytvořit; potřebujete také Dockerfile pro každý kontejner, který má být nasazen, ať už se nasadíte automaticky z Visual Studia nebo ručně pomocí Cli Dockeru (docker run a docker-compose příkazy). Pokud vaše aplikace obsahuje jednu vlastní službu, budete potřebovat jeden Dockerfile. Pokud vaše aplikace obsahuje více služeb (jako v architektuře mikroslužeb), budete potřebovat jeden Dockerfile pro každou službu.

Soubor Dockerfile je umístěn v kořenové složce aplikace nebo služby. Obsahuje příkazy, které říkají Dockeru, jak nastavit a spustit aplikaci nebo službu v kontejneru. Můžete ručně vytvořit Dockerfile v kódu a přidat jej do projektu spolu s vaše .NET závislosti.

S Visual Studio a jeho nástroje pro Docker, tato úloha vyžaduje pouze několik kliknutí myší. Když vytvoříte nový projekt v Sadě Visual Studio 2019, je k dispozici možnost s názvem **Povolit podporu Dockeru**, jak je znázorněno na obrázku 5-3.

![Snímek obrazovky s zaškrtnutím políčka Povolit podporu Dockeru](./media/docker-app-development-workflow/enable-docker-support-check-box.png)

**Obrázek 5-3**. Povolení podpory Dockeru při vytváření nového projektu ASP.NET Core ve Visual Studiu 2019

Podporu Dockeru můžete povolit také u existujícího projektu webové aplikace ASP.NET Core tak, že kliknete pravým tlačítkem myši na projekt v **Průzkumníku řešení** a vyberete **přidat** > **podporu Dockeru...**, jak je znázorněno na obrázku 5-4.

![Snímek obrazovky s možností Podpora Dockeru v nabídce Přidat](./media/docker-app-development-workflow/add-docker-support-option.png)

**Obrázek 5-4**. Povolení podpory Dockeru v existujícím projektu Visual Studia 2019

Tato akce přidá *Dockerfile* do projektu s požadovanou konfiguraci a je k dispozici pouze na ASP.NET základní projekty.

Podobně visual studio můžete také přidat `docker-compose.yml` soubor pro celé řešení s možností **Přidat > podpora kontejneru Orchestrator...**. V kroku 4 tuto možnost podrobněji prozkoumáme.

### <a name="using-an-existing-official-net-docker-image"></a>Použití existující oficiální bitové kopie .NET Docker

Obvykle vytvoříte vlastní image pro váš kontejner nad základní image, kterou získáte z oficiálního úložiště, jako je registr [Docker Hub.](https://hub.docker.com/) To je přesně to, co se stane pod kryty, když povolíte podporu Dockeru v sadě Visual Studio. Soubor Dockerfile bude `dotnet/core/aspnet` používat existující image.

Dříve jsme vysvětlili, které image dockeru a repo můžete použít, v závislosti na rámci a operačního rozhraní, které jste si vybrali. Například, pokud chcete použít ASP.NET Core (Linux nebo Windows), bitová kopie, která má být používána, je `mcr.microsoft.com/dotnet/core/aspnet:3.1`. Proto stačí zadat, jakou základní image Dockeru budete používat pro kontejner. Můžete to provést `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1` přidáním do souboru Dockerfile. To bude automaticky provedeno visual studio, ale pokud byste měli aktualizovat verzi, aktualizovat tuto hodnotu.

Použití oficiálního úložiště bitových údajů .NET z Docker Hubu s číslem verze zajišťuje, že stejné funkce jazyka jsou k dispozici na všech počítačích (včetně vývoje, testování a výroby).

Následující příklad ukazuje ukázkový soubor Dockerfile pro kontejner ASP.NET Core.

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
ARG source
WORKDIR /app
EXPOSE 80
COPY ${source:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

V tomto případě je obraz založen na verzi 3.1 oficiálního ASP.NET image Core Docker (multi-arch pro Linux a Windows). Toto je `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1`nastavení . (Další informace o této základní bitové kopii naleznete na stránce [.NET Core Docker Image.)](https://hub.docker.com/_/microsoft-dotnet-core/) V Dockerfile, musíte také pokyn Docker poslouchat na portu TCP, který budete používat za běhu (v tomto případě port 80, jak je nakonfigurován s nastavením EXPOSE).

Můžete zadat další nastavení konfigurace v Dockerfile, v závislosti na jazyku a rozhraní, které používáte. Například řádek ENTRYPOINT `["dotnet", "MySingleContainerWebApp.dll"]` s říká Docker spustit aplikaci .NET Core. Pokud používáte sadu SDK a rozhraní .NET Core CLI (dotnet CLI) k sestavení a spuštění aplikace .NET, bude toto nastavení jiné. Pointa je, že entrypoint řádek a další nastavení se bude lišit v závislosti na jazyku a platformě, kterou zvolíte pro vaši aplikaci.

### <a name="additional-resources"></a>Další zdroje

- **Vytváření imitace Dockeru pro základní aplikace .NET** \
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

- **Vytvořte si vlastní image**. V oficiální dokumentaci dockeru.\
  <https://docs.docker.com/engine/tutorials/dockerimages/>

- **Udržování aktuálního stavu s bitovými kopiemi kontejnerů .NET** \
  <https://devblogs.microsoft.com/dotnet/staying-up-to-date-with-net-container-images/>

- **Použití rozhraní .NET a dockeru společně – aktualizace DockerConu 2018** \
  <https://devblogs.microsoft.com/dotnet/using-net-and-docker-together-dockercon-2018-update/>

### <a name="using-multi-arch-image-repositories"></a>Použití víceobloukových obrazových úložišť

Jediné repo může obsahovat varianty platformy, jako je například bitová kopie Linuxu a bitová kopie systému Windows. Tato funkce umožňuje dodavatelům, jako je Microsoft (tvůrci základních obrázků), vytvořit jeden repo, který by pokrýval více platforem (tedy Linux a Windows). Například úložiště [dotnet/core,](https://hub.docker.com/_/microsoft-dotnet-core/) které je k dispozici v registru Docker Hub, poskytuje podporu pro Linux a Windows Nano Server pomocí stejného názvu úložiště.

Pokud zadáte značku, cílení na platformu, která je explicitní jako v následujících případech:

- `mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim` \
  Cíle: .NET Core 3.1 runtime-only na Linuxu

- `mcr.microsoft.com/dotnet/core/aspnet:3.1-nanoserver-1909` \
  Cíle: Pouze runtime .NET Core 3.1 na Windows Nano Server

Pokud však zadáte stejný název obrázku, a to i se stejnou `aspnet` značkou, budou víceobloukové obrazy (jako obrázek) používat verzi Linuxu nebo Windows v závislosti na hostitelském operačním systému Dockeru, který nasazujete, jak je znázorněno v následujícím příkladu:

- `mcr.microsoft.com/dotnet/core/aspnet:3.1` \
  Multi-arch: .NET Core 3.1 runtime-only na Linuxu nebo Windows Nano Server v závislosti na dockeru hostitelského operačního systému

Tímto způsobem, když vytáhnete obrázek z hostitele systému Windows, vytáhne variantu systému Windows a vytažení stejného názvu obrázku z hostitele Linuxu vytáhne variantu Linuxu.

### <a name="multi-stage-builds-in-dockerfile"></a>Vícestupňové sestavení v Dockerfile

Dockerfile je podobný dávkový skript. Podobně jako byste museli nastavit počítač z příkazového řádku.

Začíná se základním obrazem, který nastavuje počáteční kontext, je to jako spouštěcí souborový systém, který sedí nad hostitelským osem. Není to Operační os, ale můžete si myslet, že jako "" OS uvnitř kontejneru.

Spuštění každého příkazového řádku vytvoří novou vrstvu v souborovém systému se změnami z předchozího, takže v kombinaci vytvoří výsledný souborový systém.

Vzhledem k tomu, že každá nová vrstva "spočívá" nad předchozí a výsledná velikost obrázku se zvyšuje s každým příkazem, obrázky mohou být velmi velké, pokud musí zahrnovat například sdk potřebnou k vytvoření a publikování aplikace.

To je místo, kde multi-fáze staví dostat do pozemku (od Docker 17,05 a vyšší), aby se jejich kouzlo.

Základní myšlenkou je, že proces provádění dockerových souborů můžete oddělit ve fázích, kde fáze je počáteční obrázek následovaný jedním nebo více příkazy a poslední fáze určuje konečnou velikost obrázku.

Stručně řečeno, vícestupňové sestavení umožňují rozdělení tvorby v různých "fázích" a pak sestavit konečný obraz s pouze příslušné adresáře z mezilehlých fází. Obecná strategie použití této funkce je:

1. Použijte základní bitovou kopii sady SDK (nezáleží na tom, jak velký), se vším, co je potřeba k sestavení a publikování aplikace do složky a pak

2. Použijte základní, malý obrázek pouze za běhu a zkopírujte složku publikování z předchozí fáze k vytvoření malého konečného obrázku.

Pravděpodobně nejlepší způsob, jak pochopit vícestupňový prochází Dockerfile podrobně, řádek po řádku, takže začněme s počáteční Dockerfile vytvořené Visual Studio při přidávání podpory Docker u projektu a dostane se do některé optimalizace později.

Počáteční Dockerfile může vypadat nějak takto:

```Dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
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
20  RUN dotnet build Catalog.API.csproj -c Release -o /app
21
22  FROM build AS publish
23  RUN dotnet publish Catalog.API.csproj -c Release -o /app
24
25  FROM base AS final
26  WORKDIR /app
27  COPY --from=publish /app .
28  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

A toto jsou detaily, řádek po řádku:

- **#1 čáry:** Začněte fázi se základním obrázkem pouze "malý" runtime, nazvěme ji **základnou** pro referenci.

- **Linka #2:** Vytvořte adresář **/app** v obraze.

- **#3 čáry:** Vystavit port **80**.

- **Linka #5:** Začněte novou fázi s "velkým" obrazem pro vytváření/publikování. Nazvěme to **stavět** pro referenci.

- **Linka #6:** Vytvořte adresář **/src** v obraze.

- **Linka #7:** Až do řádku 16 zkopírujte odkazované soubory projektu **.csproj,** abyste mohli později obnovit balíčky.

- **Linka #17:** Obnovení balíčků pro projekt **Catalog.API** a odkazované projekty.

- **Linka #18:** Zkopírujte **všechny adresářové stromy řešení** (s výjimkou souborů/adresářů zahrnutých v souboru **.dockerignore)** do adresáře **/src** v bitové kopii.

- **Linka #19:** Změňte aktuální složku na projekt **Catalog.API.**

- **#20 čáry:** Vytvořte projekt (a další závislosti projektu) a výstup do adresáře **/app** v bitové kopii.

- **Linka #22:** Začněte novou fázi pokračovat z sestavení. Nazvěme to **publikovat** pro referenci.

- **Linka #23:** Publikujte projekt (a závislosti) a výstup do adresáře **/app** v bitové kopii.

- **#25 čáry:** Začněte novou etapu, která pokračuje od **základny,** a nazvěme ji **konečnou**.

- **Linka #26:** Změňte aktuální adresář na **/app**.

- **Linka #27:** Zkopírujte adresář **/app** z **publikování** fáze do aktuálního adresáře.

- **Linka #28:** Definujte příkaz, který chcete spustit při spuštění kontejneru.

Nyní pojďme prozkoumat některé optimalizace ke zlepšení výkonu celého procesu, který v případě eShopOnContainers znamená asi 22 minut nebo více k vytvoření kompletního řešení v kontejnerech Linuxu.

Budete využívat funkce mezipaměti vrstev Dockeru, což je poměrně jednoduché: pokud jsou základní obraz a příkazy stejné jako některé dříve provedené, můžete použít výslednou vrstvu bez nutnosti provádění příkazů, což šetří nějaký čas.

Takže se zaměřme na fázi **sestavení,** řádky 5-6 jsou většinou stejné, ale řádky 7-17 se liší pro každou službu z eShopOnContainers, takže musí provést pokaždé, když jste změnili řádky 7-16 na:

```Dockerfile
COPY . .
```

Pak by to bylo stejné pro každou službu, to by zkopírovat celé řešení a vytvoří větší vrstvu, ale:

1. Proces kopírování by byl proveden pouze poprvé (a při opětovném sestavení, pokud dojde ke změně souboru) a použil by mezipaměť pro všechny ostatní služby a

2. Vzhledem k tomu, že větší obraz se vyskytuje v mezilehlé fázi, nemá vliv na konečnou velikost obrazu.

Další významná optimalizace zahrnuje `restore` příkaz spuštěný v řádku 17, který se také liší pro každou službu eShopOnContainers. Pokud tento řádek změníte na pouze:

```Dockerfile
RUN dotnet restore
```

To by obnovit balíčky pro celé řešení, ale pak znovu, to by to jen jednou, místo 15 krát se současnou strategií.

Však `dotnet restore` pouze spustí, pokud je jeden projekt nebo soubor řešení ve složce, takže dosažení tohoto je trochu složitější a způsob, jak ji vyřešit, aniž by se do příliš mnoho detailů, je toto:

1. Do **.dockerignore**přidejte následující řádky :

   - `*.sln`, chcete-li ignorovat všechny soubory řešení ve stromu hlavních složek

   - `!eShopOnContainers-ServicesAndWebApps.sln`, aby zahrnoval pouze tento soubor řešení.

2. `/ignoreprojectextensions:.dcproj` Zahrňte `dotnet restore`argument do aplikace , takže také ignoruje projekt docker-compose a obnoví pouze balíčky pro řešení eShopOnContainers-ServicesAndWebApps.

Pro konečnou optimalizaci se prostě stane, že řádek 20 je redundantní, protože řádek 23 také vytváří aplikaci a přichází v podstatě hned po řádku 20, takže jde další časově náročný příkaz.

Výsledný soubor je pak:

```Dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS publish
 6  WORKDIR /src
 7  COPY . .
 8  RUN dotnet restore /ignoreprojectextensions:.dcproj
 9  WORKDIR /src/src/Services/Catalog/Catalog.API
10  RUN dotnet publish Catalog.API.csproj -c Release -o /app
11
12  FROM base AS final
13  WORKDIR /app
14  COPY --from=publish /app
15  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

### <a name="creating-your-base-image-from-scratch"></a>Vytvoření základního obrázku od začátku

Můžete vytvořit vlastní základní image Dockeru od začátku. Tento scénář se nedoporučuje pro někoho, kdo začíná s Docker, ale pokud chcete nastavit konkrétní bity vlastní základní image, můžete tak učinit.

### <a name="additional-resources"></a>Další zdroje

- **Víceobloukové obrázky .NET Core**.\
  <https://github.com/dotnet/announcements/issues/14>

- **Vytvořte základní bitovou kopii**. Oficiální dokumentace dockeru.\
  <https://docs.docker.com/develop/develop-images/baseimages/>

![Obrázek kroku 3.](./media/docker-app-development-workflow/step-3-create-dockerfile-defined-images.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a>Krok 3. Vytvořte si vlastní image Dockeru a vložte do nich aplikaci nebo službu.

Pro každou službu v aplikaci je třeba vytvořit související bitovou kopii. Pokud je vaše aplikace tvořena jedinou službou nebo webovou aplikací, potřebujete pouze jeden obrázek.

Všimněte si, že image Dockeru jsou vytvořeny automaticky pro vás v sadě Visual Studio. Následující kroky jsou potřebné pouze pro pracovní postup editoru/rozhraní příkazového příkazu a vysvětleno pro přehlednost o tom, co se děje pod ním.

Vy, jako vývojář, je třeba vyvíjet a testovat místně, dokud push dokončené funkce nebo změnit systém správy zdrojového kódu (například na GitHub). To znamená, že je potřeba vytvořit image Dockeru a nasadit kontejnery do místního hostitele Dockeru (Windows nebo virtuální počítač SNI) a spustit, testovat a ladit proti těmto místním kontejnerům.

Chcete-li vytvořit vlastní image v místním prostředí pomocí Docker CLI a dockerfile, můžete použít příkaz sestavení dockeru, jako na obrázku 5-5.

![Snímek obrazovky zobrazující výstup konzoly příkazu docker build.](./media/docker-app-development-workflow/run-docker-build-command.png)

**Obrázek 5-5**. Vytvoření vlastní image Dockeru

Volitelně můžete namísto přímého spuštění sestavení dockeru ze složky projektu nejprve vygenerovat nasaditelnou složku s požadovanými knihovnami a binárními soubory .NET spuštěním `dotnet publish`a potom použít `docker build` příkaz.

Tím vytvoříte image Dockeru `cesardl/netcore-webapi-microservice-docker:first`s názvem . V tomto případě : first je značka představující konkrétní verzi. Tento krok můžete zopakovat pro každou vlastní bitovou kopii, kterou potřebujete vytvořit pro komponovanou aplikaci Docker.

Pokud je aplikace vyrobena z více kontejnerů (to znamená, že se `docker-compose up --build` jedná o aplikaci s více kontejnery), můžete také použít příkaz k vytvoření všech souvisejících bitových kopií pomocí jediného příkazu pomocí metadat vystavených v souvisejících souborech docker-compose.yml.

Existující obrázky můžete najít v místním úložišti pomocí příkazu imkdocker, jak je znázorněno na obrázku 5-6.

![Konzolový výstup z iobrazů řídicího místa s existujícími obrazy.](./media/docker-app-development-workflow/view-existing-images-with-docker-images.png)

**Obrázek 5-6.** Zobrazení existujících obrazů pomocí příkazu docker images

### <a name="creating-docker-images-with-visual-studio"></a>Vytváření imitací Dockeru pomocí Sady Visual Studio

Při použití Visual Studio k vytvoření projektu s podporou Dockeru, není explicitně vytvořit image. Místo toho je obrázek vytvořen pro vás, když stisknete **Klávesu F5** (nebo **Ctrl-F5)** pro spuštění dockerized aplikace nebo služby. Tento krok je v sadě Visual Studio automatický a neuvidíte, že k tomu dojde, ale je důležité, abyste věděli, co se děje pod ním.

![Obrázek volitelného kroku 4.](./media/docker-app-development-workflow/step-4-define-services-docker-compose-yml.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a>Krok 4. Definujte své služby v docker-compose.yml při vytváření aplikace Docker u více kontejnerů

Soubor [docker-compose.yml](https://docs.docker.com/compose/compose-file/) umožňuje definovat sadu souvisejících služeb, které mají být nasazeny jako komponovaná aplikace s příkazy nasazení. Také konfiguruje jeho vztahy závislostí a konfigurace za běhu.

Chcete-li použít soubor docker-compose.yml, musíte vytvořit soubor v hlavní nebo kořenové složce řešení s obsahem podobným obsahu v následujícím příkladu:

```yml
version: '3.4'

services:

  webmvc:
    image: eshop/web
    environment:
      - CatalogUrl=http://catalog-api
      - OrderingUrl=http://ordering-api
    ports:
      - "80:80"
    depends_on:
      - catalog-api
      - ordering-api

  catalog-api:
    image: eshop/catalog-api
    environment:
      - ConnectionString=Server=sqldata;Port=1433;Database=CatalogDB;…
    ports:
      - "81:80"
    depends_on:
      - sqldata

  ordering-api:
    image: eshop/ordering-api
    environment:
      - ConnectionString=Server=sqldata;Database=OrderingDb;…
    ports:
      - "82:80"
    extra_hosts:
      - "CESARDLBOOKVHD:10.0.75.1"
    depends_on:
      - sqldata

  sqldata:
    image: mssql-server-linux:latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
```

Tento soubor docker-compose.yml je zjednodušená a sloučená verze. Obsahuje statická konfigurační data pro každý kontejner (například název vlastní bitové kopie), která je vždy vyžadována, a informace o konfiguraci, které mohou záviset na prostředí nasazení, jako je připojovací řetězec. V dalších částech se dozvíte, jak rozdělit konfiguraci docker-compose.yml do více souborů docker-compose a přepsat hodnoty v závislosti na prostředí a typu spuštění (ladění nebo vydání).

Příklad souboru docker-compose.yml definuje čtyři `webmvc` služby: službu (webovou `basket-api`aplikaci), dvě `sqldata`mikroslužby (`ordering-api` a ) a jeden kontejner zdroje dat , založený na SQL Serveru pro Linux běžícím jako kontejner. Každá služba bude nasazena jako kontejner, takže image Dockeru je vyžadována pro každou.

Soubor docker-compose.yml určuje nejen to, jaké kontejnery se používají, ale jak jsou individuálně konfigurovány. Například definice `webmvc` kontejneru v souboru YML:

- Používá předem sestavenou `eshop/web:latest` bitovou kopii. Můžete však také nakonfigurovat bitovou kopii, která má být vytvořena jako součást spuštění docker-compose s další konfigurací založenou na sestavení: části v souboru docker-compose.

- Inicializuje dvě proměnné prostředí (CatalogUrl a OrderingUrl).

- Předá exponovaný port 80 na kontejneru na externí port 80 na hostitelském počítači.

- Propojí webovou aplikaci s katalogem a objednávkovou službou s nastavením depends_on. To způsobí, že služba čekat, dokud tyto služby jsou spuštěny.

Znovu navštívíme soubor docker-compose.yml v pozdější části, když se podíváme, jak implementovat mikroslužeb a aplikace s více kontejnery.

### <a name="working-with-docker-composeyml-in-visual-studio-2019"></a>Práce s docker-compose.yml ve Visual Studiu 2019

Kromě přidání Dockerfile do projektu, jak jsme již zmínili, Visual Studio 2017 (od verze 15.8 na) můžete přidat orchestrator podporu pro Docker Compose do řešení.

Když přidáte podporu orchestrator kontejneru, jak je znázorněno na obrázku 5-7, poprvé, Visual Studio vytvoří Dockerfile pro `docker-compose*.yml` projekt a vytvoří nový projekt (část služby) ve vašem řešení s několika globálnísoubory a potom přidá projekt do těchto souborů. Potom můžete otevřít soubory docker-compose.yml a aktualizovat je dalšími funkcemi.

Tento formulář operace je třeba zopakovat každý projekt, který chcete zahrnout do souboru docker-compose.yml.

V době psaní tohoto článku Visual Studio podporuje **Docker Compose** a **Kubernetes/Helm** orchestrátory.

![Snímek obrazovky zobrazující možnost Podpora orchestrátoru kontejneru v kontextové nabídce projektu](./media/docker-app-development-workflow/add-container-orchestrator-support-option.png)

**Obrázek 5-7**. Přidání podpory Dockeru ve Visual Studiu 2019 kliknutím pravým tlačítkem myši na ASP.NET základní projekt

Po přidání podpory orchestrator do vašeho řešení v sadě Visual Studio, `docker-compose.dcproj` uvidíte také nový uzel (v souboru projektu) v Průzkumníku řešení, který obsahuje přidané soubory docker-compose.yml, jak je znázorněno na obrázku 5-8.

![Snímek obrazovky uzlu docker-compose v Průzkumníku řešení](./media/docker-app-development-workflow/docker-compose-tree-node.png)

**Obrázek 5-8**. Uzel stromu **docker-compose** přidaný v Průzkumníku řešení Visual Studia 2019

Pomocí příkazu můžete nasadit aplikaci s více kontejnery pomocí jednoho `docker-compose up` souboru docker-compose.yml. Visual Studio však přidá skupinu z nich, takže můžete přepsat hodnoty v závislosti na prostředí (vývoj nebo výroba) a typ spuštění (uvolnění nebo ladění). Tato funkce bude vysvětlena v dalších částech.

![Obrázek kroku 5.](./media/docker-app-development-workflow/step-5-run-containers-compose-app.png)

## <a name="step-5-build-and-run-your-docker-application"></a>Krok 5. Sestavení a spuštění aplikace Dockeru

Pokud vaše aplikace má jenom jeden kontejner, můžete jej spustit nasazením do hostitele Dockeru (virtuální počítač nebo fyzický server). Pokud však vaše aplikace obsahuje více služeb, můžete ji nasadit jako složenou aplikaci, a to buď pomocí jediného příkazu příkazu příkazu příkazu příkazu cli (`docker-compose up)`nebo s aplikací Visual Studio, která bude tento příkaz používat pod kryty. Podívejme se na různé možnosti.

### <a name="option-a-running-a-single-container-application"></a>Možnost A: Spuštění aplikace s jedním kontejnerem

#### <a name="using-docker-cli"></a>Použití cli Dockeru

Kontejner Dockeru můžete spustit `docker run` pomocí příkazu, jak je znázorněno na obrázku 5-9:

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

Výše uvedený příkaz vytvoří novou instanci kontejneru ze zadané bitové kopie při každém spuštění. Parametr můžete `--name` použít k poskytnutí názvu kontejneru `docker start {name}` a potom použít (nebo použít ID kontejneru nebo automatický název) ke spuštění existující instance kontejneru.

![Snímek obrazovky se spuštěním kontejneru Dockeru pomocí příkazu docker run.](./media/docker-app-development-workflow/use-docker-run-command.png)

**Obrázek 5-9**. Spuštění kontejneru Dockeru pomocí příkazu docker run

V tomto případě příkaz váže vnitřní port 5000 kontejneru na port 80 hostitelského počítače. To znamená, že hostitel naslouchá na portu 80 a přeposílá na port 5000 v kontejneru.

Zobrazená hodnota hash je ID kontejneru a je mu `--name` také přiřazen náhodný čitelný název, pokud není použita možnost.

#### <a name="using-visual-studio"></a>Pomocí sady Visual Studio

Pokud jste nepřidali podporu orchestrator kontejneru, můžete také spustit jeden kontejner aplikace v sadě Visual Studio stisknutím **Ctrl-F5** a můžete také použít **F5** k ladění aplikace v rámci kontejneru. Kontejner běží místně pomocí docker spustit.

### <a name="option-b-running-a-multi-container-application"></a>Možnost B: Spuštění aplikace s více kontejnery

Ve většině podnikových scénářů aplikace Dockeru se bude skládat z více služeb, což znamená, že je třeba spustit aplikaci s více kontejnery, jak je znázorněno na obrázku 5-10.

![Virtuální virtuální byl v ovesu s několika kontejnery Dockeru](./media/docker-app-development-workflow/vm-with-docker-containers-deployed.png)

**Obrázek 5-10**. Virtuální virtuální ms s nasazenými kontejnery Dockeru

#### <a name="using-docker-cli"></a>Použití cli Dockeru

Chcete-li spustit aplikaci s více kontejnery `docker-compose up` s příkazem příkazu Dockeru, použijte příkaz. Tento příkaz používá soubor **docker-compose.yml,** který máte na úrovni řešení k nasazení aplikace s více kontejnery. Obrázek 5-11 ukazuje výsledky při spuštění příkazu z hlavního adresáře řešení, který obsahuje soubor docker-compose.yml.

![Zobrazení obrazovky při spuštění příkazu docker-compose up](./media/docker-app-development-workflow/results-docker-compose-up.png)

**Obrázek 5-11**. Příklad výsledků při spuštění příkazu docker-compose up

Po spuštění příkazu docker-compose up se aplikace a související kontejnery nasadí do hostitele Dockeru, jak je znázorněno na obrázku 5-10.

#### <a name="using-visual-studio"></a>Pomocí sady Visual Studio

Spuštění aplikace s více kontejnery pomocí Visual Studia 2019 nemůže být jednodušší. Stačí stisknout **Ctrl-F5** spustit nebo **F5** ladit, jako obvykle, nastavení **docker-compose** projektu jako spuštění projektu.  Visual Studio zpracovává všechny potřebné nastavení, takže můžete vytvořit zarážky jako obvykle a ladit, co se nakonec stane nezávislými procesy spuštěnými na "vzdálených serverech", s ladicím programem, který je již připojen, stejně jako to.

Jak již bylo zmíněno dříve, pokaždé, když přidáte podporu řešení Docker u projektu v rámci řešení, tento projekt je nakonfigurován v globálním (řešení úrovni) docker-compose.yml souboru, který umožňuje spustit nebo ladit celé řešení najednou. Visual Studio spustí jeden kontejner pro každý projekt, který má povolenou podporu řešení Dockeru a provede všechny interní kroky za vás (dotnet publish, docker build atd.).

Pokud se chcete podívat na všechny dřiny, podívejte se na soubor:

`{root solution folder}\obj\Docker\docker-compose.vs.debug.g.yml`

Důležitým bodem je, jak je znázorněno na obrázku 5-12, v Sadě Visual Studio 2019 je další příkaz **Docker** u akce klíče F5. Tato možnost umožňuje spustit nebo ladit aplikaci s více kontejnery spuštěním všech kontejnerů, které jsou definovány v souborech docker-compose.yml na úrovni řešení. Možnost ladit řešení s více kontejnery znamená, že můžete nastavit několik zarážek, každý zarážka v jiném projektu (kontejner) a při ladění z Visual Studio se zastaví na zarážky definované v různých projektech a běží na různých kontejnerech.

![Snímek obrazovky panelu nástrojů ladění se spuštěným projektem docker-compose](./media/docker-app-development-workflow/debug-toolbar-docker-compose-project.png)

**Obrázek 5-12**. Spouštění aplikací s více kontejnery ve Visual Studiu 2019

### <a name="additional-resources"></a>Další zdroje

- **Nasazení kontejneru ASP.NET vzdálenému hostiteli Dockeru** \
  <https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a>Poznámka o testování a nasazování s orchestrátory

Příkazy pro spuštění dockeru a dockeru (nebo spuštění a ladění kontejnerů v sadě Visual Studio) jsou vhodné pro testování kontejnerů ve vývojovém prostředí. Ale neměli byste používat tento přístup pro nasazení v produkčním prostředí, kde byste měli cílit orchestrátory jako [Kubernetes](https://kubernetes.io/) nebo [Service Fabric](https://azure.microsoft.com/services/service-fabric/). Pokud používáte Kubernetes, budete muset použít [pody](https://kubernetes.io/docs/concepts/workloads/pods/pod/) uspořádat kontejnery a [služby](https://kubernetes.io/docs/concepts/services-networking/service/) pro jejich připojení k síti. Nasazení [můžete](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) také použít k uspořádání vytváření a úprav podu.

![Obrázek kroku 6.](./media/docker-app-development-workflow/step-6-test-app-microservices.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a>Krok 6. Testování aplikace Dockeru pomocí místního hostitele Dockeru

Tento krok se bude lišit v závislosti na tom, co vaše aplikace dělá. V jednoduché webové aplikaci .NET Core, která je nasazena jako jeden kontejner nebo služba, můžete ke službě přistupovat otevřením prohlížeče na hostiteli Dockeru a přechodem na tento web, jak je znázorněno na obrázku 5-13. (Pokud konfigurace v Souboru Dockerfile mapuje kontejner na port na hostiteli, který je něco jiného než 80, zahrňte port hostitele v adrese URL.)

![Snímek obrazovky s odpovědí z localhost/API/values.](./media/docker-app-development-workflow/test-docker-app-locally-localhost.png)

**Obrázek 5-13**. Příklad testování aplikace Docker místně pomocí localhost

Pokud localhost neukazuje na IP hostitele Dockeru (ve výchozím nastavení, při použití Docker CE, by měl), chcete-li přejít na vaši službu, použijte IP adresu síťové karty vašeho počítače.

Všimněte si, že tato adresa URL v prohlížeči používá port 80 pro konkrétní příklad kontejneru, který je popsán. Však interně požadavky jsou přesměrovány na port 5000, protože to bylo, jak byl nasazen s příkazem docker spustit, jak je vysvětleno v předchozím kroku.

Aplikaci můžete také otestovat pomocí zvlnění z terminálu, jak je znázorněno na obrázku 5-14. V instalaci Dockeru v systému Windows je výchozí IP hostitele Dockeru vždy 10.0.75.1 kromě skutečné IP adresy vašeho počítače.

![Konzolový výstup http://10.0.75.1/API/values od získání s curl.](./media/docker-app-development-workflow/test-docker-app-locally-curl.png)

**Obrázek 5-14**. Příklad testování aplikace Docker místně pomocí curl

### <a name="testing-and-debugging-containers-with-visual-studio-2019"></a>Testování a ladění kontejnerů pomocí Visual Studia 2019

Při spuštění a ladění kontejnerů s Visual Studio 2019, můžete ladit .NET aplikace v podstatě stejným způsobem jako při spuštění bez kontejnerů.

### <a name="testing-and-debugging-without-visual-studio"></a>Testování a ladění bez sady Visual Studio

Pokud vyvíjíte pomocí editor/CLI přístup, ladění kontejnerů je obtížnější a budete pravděpodobně chtít ladit generováním trasování.

### <a name="additional-resources"></a>Další zdroje

- **Ladění aplikací v místním kontejneru Dockeru** \
  [https://docs.microsoft.com/visualstudio/containers/edit-and-refresh](/visualstudio/containers/edit-and-refresh)

- **Steva Laskera. Sestavení, ladění, nasazení ASP.NET základních aplikací pomocí Dockeru.** Video. \
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115>

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a>Zjednodušený pracovní postup při vývoji kontejnerů pomocí sady Visual Studio

Efektivně pracovní postup při použití sady Visual Studio je mnohem jednodušší, než pokud použijete přístup editor/CLI. Většina kroků požadovaných Dockersouvisející s Dockerfile a docker-compose.yml soubory jsou skryté nebo zjednodušené Visual Studio, jak je znázorněno na obrázku 5-15.

:::image type="complex" source="./media/docker-app-development-workflow/simplified-life-cycle-containerized-apps-docker-cli.png" alt-text="Diagram znázorňující pět zjednodušených kroků, které je třeba k vytvoření aplikace.":::
Proces vývoje pro aplikace Docker: 1 - Kód vaší aplikace, 2 - Zápis Dockerfile/s, 3 - Vytvoření bitových kopií definovaných na Dockerfile/s, 4 - (volitelné) Compose služby v docker-compose.yml souboru, 5 - Spustit kontejner nebo docker-compose aplikace, 6 - Test aplikace nebo mikroslužeb, 7 - Push to repo a opakovat.
:::image-end:::

**Obrázek 5-15**. Zjednodušený pracovní postup při vývoji pomocí sady Visual Studio

Kromě toho je třeba provést krok 2 (přidání podpory Dockeru do vašich projektů) pouze jednou. Proto pracovní postup je podobný běžné vývojové úkoly při použití rozhraní .NET pro jakýkoli jiný vývoj. Musíte vědět, co se děje pod kryty (proces sestavení image, jaké základní image používáte, nasazení kontejnerů atd.) a někdy budete také muset upravit soubor Dockerfile nebo docker-compose.yml pro přizpůsobení chování. Ale většina práce je velmi zjednodušena pomocí sady Visual Studio, takže budete mnohem produktivnější.

### <a name="additional-resources"></a>Další zdroje

- **Steva Laskera. Vývoj dockeru .NET s Visual Studio (2017)** \
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a>Nastavení kontejnerů Windows pomocí powershellových příkazů v souboru Dockerfile

[Kontejnery Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/index) umožňují převést existující aplikace Systému Windows na inaimages Dockeru a nasadit je pomocí stejných nástrojů jako zbytek ekosystému Dockeru. Chcete-li použít kontejnery systému Windows, spouštět příkazy prostředí PowerShell v souboru Dockerfile, jak je znázorněno v následujícím příkladu:

```Dockerfile
FROM mcr.microsoft.com/windows/servercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

V tomto případě používáme základní bitovou kopii jádra systému Windows Server (nastavení FROM) a instalujeme službu IIS pomocí příkazu Prostředí PowerShell (nastavení RUN). Podobným způsobem můžete také použít příkazy prostředí PowerShell k nastavení dalších součástí, jako je ASP.NET 4.x, .NET 4.6 nebo jakýkoli jiný software windows. Například následující příkaz v souboru Dockerfile nastaví ASP.NET 4.5:

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a>Další zdroje

- **aspnet-docker/Dockerfile.** Příklad příkazů prostředí PowerShell pro spuštění ze souborů dockerfiles za účelem zahrnutí funkcí systému Windows.\
  <https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile>

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](../multi-container-microservice-net-applications/index.md)
