---
title: Pracovní postup vývoje aplikací Dockeru
description: Pochopte podrobnosti pracovního postupu pro vývoj aplikací založených na Docker. Zahajte krok za krokem a získejte do některých podrobností, abyste mohli optimalizovat fázemi a skončit s zjednodušeným pracovním postupem, který je dostupný při používání sady Visual Studio.
ms.date: 01/07/2019
ms.openlocfilehash: 0c2789377bc388b8ac7373ee7fa46e3141f1b518
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740360"
---
# <a name="development-workflow-for-docker-apps"></a>Pracovní postup vývoje aplikací Dockeru

Životní cyklus vývoje aplikací začíná ve vašem počítači, jako vývojář, kde aplikaci nakódujete pomocí preferovaného jazyka a otestujete ji místně. V tomto pracovním postupu bez ohledu na to, jaký jazyk, architekturu a platformu zvolíte, budete vždycky vyvíjet a testovat kontejnery Docker, ale děláte je místně.

Každý kontejner (instance image Docker) obsahuje následující komponenty:

- Výběr operačního systému, například distribuce systému Linux, Windows nano Server nebo jádro Windows serveru.

- Soubory přidané během vývoje, například zdrojový kód a binární soubory aplikace.

- Konfigurační informace, například nastavení prostředí a závislosti.

## <a name="workflow-for-developing-docker-container-based-applications"></a>Pracovní postup pro vývoj aplikací založených na kontejnerech Docker

Tato část popisuje pracovní postup vývoje *vnitřních smyček* pro aplikace založené na kontejnerech Docker. Pracovní postup vnitřní smyčky znamená, že se nepovažuje za širší DevOps pracovní postup, který může zahrnovat až produkční nasazení, a zaměřuje se na vývojovou práci, která se provádí na počítači vývojáře. Úvodní kroky pro nastavení prostředí nejsou zahrnuté, protože se tyto kroky provádějí jenom jednou.

Aplikace se skládá z vašich vlastních služeb a dalších knihoven (závislosti). Následují základní kroky, které obvykle provádíte při sestavování aplikace Docker, jak je znázorněno na obrázku 5-1.

:::image type="complex" source="./media/docker-app-development-workflow/life-cycle-containerized-apps-docker-cli.png" alt-text="Diagram znázorňující 7 kroků, které je potřeba k vytvoření kontejnerové aplikace.":::
Proces vývoje pro aplikace Docker: 1 – kódování vaší aplikace, 2-zápis souboru Dockerfile/s, 3-vytváření imagí definovaných na souboru Dockerfile/s, 4 – (volitelné) psaní služeb v souboru Docker-Compose. yml, 5 spuštění kontejneru nebo Docker – sestavování aplikací, 6 – testování vaší aplikace nebo mikroslužeb, 7 – Vložení do úložiště a opakování
:::image-end:::

**Obrázek 5-1.** Podrobný pracovní postup pro vývoj aplikací s kontejnerem Docker

V této části je tento celý proces podrobný a každý hlavní krok je vysvětlen tak, že zaměříte na prostředí sady Visual Studio.

Pokud používáte přístup pro vývoj Editor/CLI (například Visual Studio Code plus Docker CLI v systému macOS nebo Windows), musíte znát každý krok, obecně více podrobností, než Pokud používáte Visual Studio. Další informace o práci v prostředí CLI najdete v části elektronický [životní cyklus aplikací Docker v kontejneru s platformami a nástroji Microsoftu](https://aka.ms/dockerlifecycleebook/).

Pokud používáte sadu Visual Studio 2017, mnohé z těchto kroků jsou zpracovávány za vás, což výrazně zvyšuje vaši produktivitu. To platí hlavně v případě, že používáte Visual Studio 2017 a cílíte na aplikace s více kontejnery. Například když jediným kliknutím myši, Visual Studio přidá do vašich projektů soubor souboru Dockerfile a Docker-Compose. yml s konfigurací vaší aplikace. Při spuštění aplikace v aplikaci Visual Studio se vytvoří image Docker a aplikace s více kontejnery se spustí přímo v Docker; i když vám umožní ladit několik kontejnerů najednou. Tyto funkce zvýší vaši rychlost vývoje.

Nicméně, protože Visual Studio neprovede tyto kroky automaticky, neznamená to, že nepotřebujete, abyste věděli, co se právě nachází pod nástrojem Docker. Proto následující pokyny podrobně popisuje každý krok.

![Obrázek pro krok 1](./media/docker-app-development-workflow/step-1-code-your-app.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a>Krok 1. Spuštění kódování a vytvoření počátečního směrného plánu aplikace nebo služby

Vývoj aplikace Docker je podobný jako při vývoji aplikace bez Docker. Rozdíl je v tom, že při vývoji pro Docker nasazujete a testujete svou aplikaci nebo služby běžící v kontejnerech Docker ve vašem místním prostředí (buď nastavení virtuálního počítače Linux pomocí Docker, nebo přímo Windows, pokud používáte kontejnery Windows).

### <a name="set-up-your-local-environment-with-visual-studio"></a>Nastavení místního prostředí pomocí sady Visual Studio

Pokud chcete začít, ujistěte se, že máte nainstalovánu [verzi Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) pro Windows, jak je vysvětleno v následujících pokynech:

[Začínáme s Docker CE for Windows](https://docs.docker.com/docker-for-windows/)

Kromě toho potřebujete Visual Studio 2017 verze 15,7 nebo novější s nainstalovanou úlohou **vývoje .NET Core pro různé platformy** , jak je znázorněno na obrázku 5-2.

![Snímek obrazovky s výběrem pro vývoj pro různé platformy .NET Core](./media/docker-app-development-workflow/dotnet-core-cross-platform-development.png)

**Obrázek 5-2**. Výběr úlohy **vývoje .NET Core pro různé platformy** během instalace sady Visual Studio 2017

Můžete spustit kódování aplikace v jednoduchém rozhraní .NET (obvykle v .NET Core, pokud plánujete používat kontejnery) dokonce ještě před povolením Docker ve vaší aplikaci a nasazením a testováním v Docker. Doporučuje se ale co nejdříve začít pracovat na Docker, protože to bude reálné prostředí a jakékoli problémy, které je možné zjistit co nejdříve. To je doporučováno, protože Visual Studio usnadňuje práci s Docker, který je skoro průhledný, což je nejlepší příklad při ladění aplikací s více kontejnery ze sady Visual Studio.

### <a name="additional-resources"></a>Další zdroje

- **Začínáme s Docker CE for Windows** \
  <https://docs.docker.com/docker-for-windows/>

- **Visual Studio 2017** \
  [https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)

![Obrázek pro krok 2.](./media/docker-app-development-workflow/step-2-write-dockerfile.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a>Krok 2. Vytvoření souboru Dockerfile souvisejícího s existující imagí .NET Base

Pro každou vlastní image, kterou chcete sestavit, potřebujete souboru Dockerfile; také potřebujete souboru Dockerfile pro každý kontejner, který chcete nasadit, bez ohledu na to, jestli nasazujete automaticky ze sady Visual Studio, nebo ručně pomocí příkazů Docker CLI (příkazy Docker Run a Docker-skládání). Pokud vaše aplikace obsahuje jednu vlastní službu, budete potřebovat jeden souboru Dockerfile. Pokud vaše aplikace obsahuje více služeb (jako v architektuře mikroslužeb), budete pro každou službu potřebovat jeden souboru Dockerfile.

Souboru Dockerfile je umístěn v kořenové složce aplikace nebo služby. Obsahuje příkazy, které informují Docker, jak nastavit a spustit vaši aplikaci nebo službu v kontejneru. Můžete ručně vytvořit souboru Dockerfile v kódu a přidat ho do svého projektu společně s vašimi závislostmi .NET.

Pomocí sady Visual Studio a jejích nástrojů pro Docker Tato úloha vyžaduje jenom několik kliknutí myší. Při vytváření nového projektu v aplikaci Visual Studio 2017 existuje možnost s názvem **Povolit podporu kontejneru (Docker)** , jak je znázorněno na obrázku 5-3.

![Snímek obrazovky, který ukazuje zaškrtávací políčko Povolit podporu Docker.](./media/docker-app-development-workflow/enable-docker-support-check-box.png)

**Obrázek 5-3**. Povolení podpory Docker při vytváření nového projektu ASP.NET Core v aplikaci Visual Studio 2017

Podporu Docker můžete povolit také pro existující projekt ASP.NET Core webové aplikace tak, že kliknete pravým tlačítkem na projekt v **Průzkumník řešení** a vyberete **Přidat** **podporu Docker** > , jak je znázorněno na obrázku 5-4.

![Snímek obrazovky s možností podpora Docker v nabídce Přidat](./media/docker-app-development-workflow/add-docker-support-option.png)

**Obrázek 5-4**. Povolení podpory Docker v existujícím projektu sady Visual Studio 2017

Tato akce přidá do projektu *souboru Dockerfile* s požadovanou konfigurací a je k dispozici pouze pro ASP.NET Core projekty.

Podobným způsobem může Visual Studio také přidat soubor Docker-Compose. yml pro celé řešení s možností **přidat > kontejner Orchestrator support**. V kroku 4 si tuto možnost podrobněji prozkoumáme.

### <a name="using-an-existing-official-net-docker-image"></a>Použití stávající oficiální image rozhraní .NET Docker

Obvykle vytvoříte vlastní image pro kontejner nad základní imagí, kterou získáte z oficiálního úložiště, jako je registr [Docker Hub](https://hub.docker.com/) . To je přesně to, co se stane v rámci pokrývání, když povolíte podporu Docker v aplikaci Visual Studio. Vaše souboru Dockerfile použije existující image `aspnetcore`.

Dříve jsme zjistili, které image a úložiště Docker můžete použít v závislosti na zvoleném rozhraní a operačním systému. Například pokud chcete použít ASP.NET Core (Linux nebo Windows), obrázek, který se má použít, je `mcr.microsoft.com/dotnet/core/aspnet:2.2`. Proto stačí určit, jakou základní image Docker budete pro svůj kontejner používat. To uděláte tak, že do souboru Dockerfile přidáte `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`. To se automaticky provede v aplikaci Visual Studio, ale pokud byste chtěli verzi aktualizovat, aktualizujete tuto hodnotu.

Použití oficiálního úložiště imagí .NET z dokovacího centra s číslem verze zajišťuje, aby byly na všech počítačích dostupné stejné funkce jazyka (včetně vývoje, testování a produkčního prostředí).

Následující příklad ukazuje vzorový souboru Dockerfile pro kontejner ASP.NET Core.

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
ARG source
WORKDIR /app
EXPOSE 80
COPY ${source:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

V tomto případě je image založená na verzi 2,2 oficiální image ASP.NET Core Docker (více imagí pro Linux a Windows). Toto nastavení je `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`. (Další informace o této základní imagi najdete na stránce s [obrázkem Docker .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) .) V souboru Dockerfile musíte také dát Docker pokyn, aby naslouchal na portu TCP, který budete používat při běhu (v tomto případě port 80, jak je nakonfigurovaný s nastavením zpřístupnit).

V souboru Dockerfile můžete určit další nastavení konfigurace v závislosti na jazyku a rozhraní, které používáte. Například řádek ENTRYPOINT s `["dotnet", "MySingleContainerWebApp.dll"]` instruuje Docker ke spuštění aplikace .NET Core. Pokud k sestavení a spuštění aplikace .NET používáte sadu SDK a .NET Core CLI (dotnet CLI), toto nastavení se liší. Dolním řádkem je, že se řádek ENTRYPOINT a další nastavení liší v závislosti na jazyku a platformě, kterou zvolíte pro vaši aplikaci.

### <a name="additional-resources"></a>Další zdroje

- **Vytváření imagí Docker pro aplikace .NET Core** \
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

- **Sestavte si vlastní image**. V oficiální dokumentaci k Docker. \
  <https://docs.docker.com/engine/tutorials/dockerimages/>

- **Udržování aktuálnosti pomocí imagí kontejnerů .net** \
  <https://devblogs.microsoft.com/dotnet/staying-up-to-date-with-net-container-images/>

- **Použití .NET a Docker společně – DockerCon 2018 Update** \
  <https://devblogs.microsoft.com/dotnet/using-net-and-docker-together-dockercon-2018-update/>

### <a name="using-multi-arch-image-repositories"></a>Použití úložišť imagí s více archy

Jedno úložiště může obsahovat varianty platformy, jako je například bitová kopie systému Linux a bitová kopie systému Windows. Tato funkce umožňuje dodavatelům, jako je Microsoft (základní tvůrci obrázků), vytvořit jedno úložiště pro pokrytí více platforem (které jsou Linux a Windows). Například úložiště [dotnet/Core](https://hub.docker.com/_/microsoft-dotnet-core/) dostupné v registru Docker Hub poskytuje podporu pro systémy Linux a Windows nano Server pomocí stejného názvu úložiště.

Pokud zadáte značku, cílící na platformu, která je explicitní, podobně jako v následujících případech:

- `microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim` \
  Cíle: modul runtime .NET Core 2,2 – pouze v systému Linux

- `microsoft/dotnet:2.2-aspnetcore-runtime-nanoserver-1809` \
  Cíle: modul runtime .NET Core 2,2 – pouze v systému Windows nano Server

Pokud ale zadáte stejný název bitové kopie, a to i se stejnou značkou, používají se pro více imagí (například bitová kopie `aspnetcore`) verze systému Linux nebo Windows v závislosti na operačním systému hostitele Docker, který nasazujete, jak je znázorněno v následujícím příkladu:

- `microsoft/dotnet:2.2-aspnetcore-runtime` \
  Vícenásobný arch: rozhraní .NET Core 2,2 runtime – pouze v systémech Linux nebo Windows nano Server v závislosti na hostitelském operačním systému Docker

Tímto způsobem načteme variantu systému Windows, když nasadíte image z hostitele Windows, vyžádá si variantu Windows a vyžádá si stejný název image z hostitele Linux.

### <a name="multi-stage-builds-in-dockerfile"></a>Sestavení s více fázemi v souboru Dockerfile

Souboru Dockerfile je podobný dávkovému skriptu. Podobně jako v případě, že jste museli nastavit počítač z příkazového řádku.

Začíná základní imagí, která nastavuje počáteční kontext, jako spouštěcí systém souborů, který je umístěný na hostitelském operačním systému. Nejedná se o operační systém, ale můžete si ho představit jako "operační systém uvnitř kontejneru".

Spuštění každého příkazového řádku vytvoří v systému souborů novou vrstvu se změnami z předchozí verze, takže v případě kombinace vyprodukuje výsledný systém souborů.

Vzhledem k tomu, že všechny nové vrstvy "jsou" na začátku a výslednou velikost obrazu se zvětšují s každým příkazem, obrázky můžou být velmi velké, pokud je potřeba je zahrnout, například sada SDK potřebná k sestavení a publikování aplikace.

Toto je místo, kde se sestavení s více fázemi dostanou do grafu (od Docker 17,05 a vyšší), aby se dosáhlo svého Magic.

Základní nápad je, že můžete oddělit proces spuštění souboru Dockerfile ve fázích, kde fáze je počáteční obrázek následovaný jedním nebo více příkazy a poslední fáze určuje konečnou velikost obrázku.

V krátkém buildu s více fázemi umožňuje rozdělit vytváření v různých fázích a potom sestavit konečný obraz, který převezme pouze relevantní adresáře z mezilehlé fáze. Obecnou strategií pro použití této funkce je:

1. Použijte základní image sady SDK (nezáleží na tom, jak velká) se všemi potřebnými k sestavování a publikování aplikace do složky a potom

2. Použijte základní bitovou kopii pouze za běhu a zkopírujte složku pro publikování z předchozí fáze, aby se vytvořila nízká finální bitová kopie.

Nejlepším způsobem, jak porozumět více fázím, je souboru Dockerfile detailně, řádek po řádku, takže pojďme začít s počátečními souboru Dockerfile vytvořenými sadou Visual Studio při přidání podpory Docker do projektu a později se dostanete k optimalizaci.

Počáteční souboru Dockerfile by měl vypadat nějak takto:

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

A jsou to podrobnosti, řádek po řádku:

- **#1 řádku:** Zahajte fázi s "malým" pouze modulem runtime základní image, zavolejte **základ** pro referenci.

- **#2 řádku:** Vytvořte v imagi adresář **/App** .

- **#3 řádku:** Vystavte port **80**.

- **#5 řádku:** Zahajte novou fázi s imagí "Velká" pro vytváření a publikování. Pro referenci zavolejte **sestavení** IT.

- **#6 řádku:** Vytvořte v imagi adresář **/Src** .

- **#7 řádku:** Až na řádek 16, zkopírujte odkazované soubory projektu **. csproj** , abyste mohli balíčky později obnovit.

- **#17 řádku:** Obnovte balíčky pro projekt **Catalog. API** a odkazované projekty.

- **#18 řádku:** Zkopírujte **všechny adresářové stromové struktury pro řešení** (kromě souborů/adresářů obsažených v souboru **. dockerignore** ) do adresáře **/Src** v imagi.

- **#19 řádku:** Změňte aktuální složku na projekt **Catalog. API** .

- **#20 řádku:** Sestavte projekt (a další závislosti projektu) a výstup do adresáře **/App** v imagi.

- **#22 řádku:** Zahajte pokračování nové fáze ze sestavení. Pro referenci zavolejte **publikování** .

- **#23 řádku:** Publikujte projekt (a závislosti) a výstup do adresáře **/App** v imagi.

- **#25 řádku:** Začněte novou fázi od **základu** a zavolejte ji **finální**.

- **#26 řádku:** Změňte aktuální adresář na **/App**.

- **#27 řádku:** Zkopírujte adresář **/App** z fáze **publikovat** do aktuálního adresáře.

- **#28 řádku:** Zadejte příkaz, který se má spustit při spuštění kontejneru.

Nyní se podívejme na několik optimalizací, které vám pomůžou zlepšit výkon celého procesu, který v případě eShopOnContainers znamená přibližně 22 minut nebo více pro sestavení kompletního řešení v kontejnerech Linux.

Budete využívat výhod funkce mezipaměti Docker, která je poměrně jednoduchá: Pokud je základní image a příkazy stejné jako u dříve spuštěných, může ji použít jenom výslednou vrstvu bez nutnosti spouštět příkazy, takže se ušetří nějaký čas.

Proto se zaměřte na fázi **sestavení** , řádky 5-6 jsou většinou stejné, ale řádky 7-17 jsou pro každou službu z eShopOnContainers odlišné, takže je nutné je spustit vždy, když jste změnili řádky 7-16 na:

```Dockerfile
COPY . .
```

Pak by byl stejný jako u každé služby, mohl by zkopírovat celé řešení a vytvořit větší vrstvu, ale:

1. Proces kopírování se spustí jenom poprvé (a když se znovu sestaví při změně souboru) a použije mezipaměť pro všechny ostatní služby.

2. Vzhledem k tomu, že větší obrázek probíhá v mezilehlé fázi, nemá vliv na konečnou velikost obrázku.

Další významná optimalizace zahrnuje příkaz `restore` provedený na řádku 17, který je také odlišný pro každou službu eShopOnContainers. Pokud tento řádek změníte jenom na:

```Dockerfile
RUN dotnet restore
```

To by obnovilo balíčky pro celé řešení, ale pak to udělá znovu jenom jednou, a to v rámci aktuální strategie za 15 krát.

Nicméně `dotnet restore` se spustí pouze v případě, že je v této složce jeden soubor projektu nebo řešení, takže se jedná o trochu složitější a způsob, jak ho vyřešit, aniž by bylo možné získat příliš mnoho podrobností:

1. Přidejte následující řádky do **. dockerignore**:

   - `*.sln` pro ignorování všech souborů řešení ve stromu hlavní složky

   - `!eShopOnContainers-ServicesAndWebApps.sln`, chcete-li zahrnout pouze tento soubor řešení.

2. Do `dotnet restore` zahrňte argument `/ignoreprojectextensions:.dcproj`, takže se taky ignoruje projekt Docker-eShopOnContainers a obnoví se jenom balíčky pro řešení-ServicesAndWebApps.

Pro konečnou optimalizaci se k tomu dochází pouze v případě, že řádek 20 je redundantní, protože řádek 23 také sestaví aplikaci a v podstatě je hned po řádku 20, takže existuje další časově náročný příkaz.

Výsledný soubor je pak:

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

### <a name="creating-your-base-image-from-scratch"></a>Vytváření základní Image od začátku

Můžete vytvořit vlastní základní image Docker od začátku. Tento scénář se nedoporučuje pro někoho, kdo začíná s Docker, ale pokud chcete nastavit konkrétní bity vlastní základní image, můžete to udělat.

### <a name="additional-resources"></a>Další zdroje

- **Vícevrstvé image .NET Core**. \
  <https://github.com/dotnet/announcements/issues/14>

- **Vytvoří základní image**. Oficiální dokumentace k Docker. \
  <https://docs.docker.com/develop/develop-images/baseimages/>

![Obrázek pro krok 3](./media/docker-app-development-workflow/step-3-create-dockerfile-defined-images.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a>Krok 3. Vytvořte vlastní image Docker a vložte do nich svou aplikaci nebo službu.

Pro každou službu ve vaší aplikaci je potřeba vytvořit související image. Pokud se vaše aplikace skládá z jediné služby nebo webové aplikace, stačí pouze jeden obrázek.

Všimněte si, že image Docker jsou sestaveny automaticky pro vás v aplikaci Visual Studio. Následující postup je nutný jenom pro pracovní postup Editor/CLI a vysvětluje, co se děje pod.

Jako vývojář budete potřebovat místní vývoj a testování, dokud nenainstalujete dokončenou funkci nebo nezměníte systém správy zdrojového kódu (například na GitHub). To znamená, že potřebujete vytvořit image Docker a nasazovat kontejnery na místního hostitele Docker (virtuální počítač se systémem Windows nebo Linux) a spouštět, testovat a ladit tyto místní kontejnery.

Pokud chcete vytvořit vlastní image v místním prostředí pomocí rozhraní Docker CLI a svého souboru Dockerfile, můžete použít příkaz Docker Build, jak je znázorněno na obrázku 5-5.

![Snímek obrazovky znázorňující výstup konzoly příkazu Docker Build](./media/docker-app-development-workflow/run-docker-build-command.png)

**Obrázek 5-5**. Vytvoření vlastní image Docker

Místo toho, aby bylo možné přímo spustit sestavení Docker ze složky projektu, můžete nejprve vygenerovat nasazenou složku s požadovanými knihovnami a binárními soubory .NET spuštěním `dotnet publish` a potom použít příkaz `docker build`.

Tím se vytvoří obrázek Docker s názvem `cesardl/netcore-webapi-microservice-docker:first`. V tomto případě: první je značka reprezentující konkrétní verzi. Tento krok můžete opakovat pro každou vlastní bitovou kopii, kterou potřebujete vytvořit pro svoji sestavenou aplikaci Docker.

Pokud je aplikace vytvořena více kontejnerů (tj. jde o vícevláknovou aplikaci), můžete použít příkaz `docker-compose up --build` k sestavení všech souvisejících imagí s jediným příkazem pomocí metadat zveřejněných v souvisejících souborech Docker-Compose. yml.

Existující image můžete najít v místním úložišti pomocí příkazu Docker images, jak je znázorněno na obrázku 5-6.

![Výstup z konzoly z příkazu Docker images zobrazující existující image](./media/docker-app-development-workflow/view-existing-images-with-docker-images.png)

**Obrázek 5-6.** Zobrazení existujících imagí pomocí příkazu Docker images

### <a name="creating-docker-images-with-visual-studio"></a>Vytváření imagí Docker pomocí sady Visual Studio

Když použijete Visual Studio k vytvoření projektu s podporou Docker, nevytvoříte explicitně image. Místo toho se obrázek vytvoří, když stisknete klávesu **F5** (nebo **CTRL-F5**) a spustíte aplikaci dockerized nebo službu. Tento krok je automaticky v aplikaci Visual Studio a neuvidíte, že k tomu dochází, ale je důležité, abyste věděli, co se děje pod.

![Obrázek pro volitelný krok 4](./media/docker-app-development-workflow/step-4-define-services-docker-compose-yml.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a>Krok 4. Definování služeb v Docker-Compose. yml při sestavování aplikace Docker s více kontejnery

Soubor [Docker-Compose. yml](https://docs.docker.com/compose/compose-file/) umožňuje definovat sadu souvisejících služeb, které mají být nasazeny jako složená aplikace s příkazy pro nasazení. Také nakonfiguruje vztahy závislosti a konfiguraci runtime.

Chcete-li použít soubor Docker-Compose. yml, je třeba vytvořit soubor ve složce hlavního nebo kořenového řešení s obsahem podobným v následujícím příkladu:

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

Tento soubor Docker-Compose. yml je zjednodušená a Sloučená verze. Obsahuje statická konfigurační data pro každý kontejner (jako je název vlastní image), který je vždy vyžadován, a informace o konfiguraci, které mohou být závislé na prostředí nasazení, jako je například připojovací řetězec. V dalších částech se dozvíte, jak rozdělit konfiguraci Docker-Compose. yml do více souborů Docker – pro vytváření souborů a přepis hodnot v závislosti na prostředí a typu spuštění (ladění nebo vydání).

Příklad souboru Docker-Compose. yml definuje čtyři služby: služba `webmvc` (webová aplikace), dvě mikroslužby (`ordering.api` a `basket.api`) a jeden kontejner zdrojů dat, `sql.data`, na základě SQL Server pro Linux spuštěný jako kontejner. Každá služba bude nasazena jako kontejner, takže se pro každý z nich vyžaduje image Docker.

Soubor Docker-Compose. yml určuje nejen to, jaké kontejnery jsou používány, ale jak jsou konfigurovány samostatně. Například definice kontejneru `webmvc` v souboru. yml:

- Používá předem sestavenou bitovou kopii `eshop/web:latest`. Můžete ale také nakonfigurovat, aby se image vytvořila jako součást spuštění v Docker – pomocí dodatečné konfigurace založené na sestavení: oddíl v souboru Docker-skládání.

- Inicializuje dvě proměnné prostředí (CatalogUrl a OrderingUrl).

- Přepošle vystavený port 80 na kontejner na externí port 80 na hostitelském počítači.

- Propojí webovou aplikaci s katalogem a službou řazení s nastavením depends_on. Tím dojde k tomu, že služba počká, až budou tyto služby spuštěné.

Až budeme pokrývat, jak implementovat mikroslužby a aplikace pro více kontejnerů, provedeme znovu soubor Docker-Compose. yml v pozdější části.

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a>Práce s Docker-Compose. yml v aplikaci Visual Studio 2017

Kromě přidání souboru Dockerfile do projektu může Visual Studio 2017 (od 15,8) přidat do řešení podporu nástroje Orchestrator pro Docker Compose.

Když přidáte podporu nástroje Orchestrator pro kontejner, jak je znázorněno na obrázku 5-7, Visual Studio vytvoří souboru Dockerfile pro projekt a vytvoří nový projekt (oddíl služby) ve vašem řešení s několika globálními soubory `docker-compose*.yml` a potom projekt přidá do Tyto soubory. Pak můžete otevřít soubory Docker-Compose. yml a aktualizovat je pomocí dalších funkcí.

Tuto operaci je nutné opakovat v každém projektu, který chcete zahrnout do souboru Docker-Compose. yml.

V době psaní tohoto zápisu aplikace Visual Studio podporuje orchestraci Docker Compose a Service Fabric.

![Snímek obrazovky s možností podpora pro produkt Orchestrator pro kontejner v místní nabídce projektu](./media/docker-app-development-workflow/add-container-orchestrator-support-option.png)

**Obrázek 5-7**. Přidání podpory Docker do sady Visual Studio 2017 tak, že kliknete pravým tlačítkem na projekt ASP.NET Core

Po přidání podpory nástroje Orchestrator do řešení v aplikaci Visual Studio se v Průzkumník řešení zobrazí také nový uzel (v souboru projektu `docker-compose.dcproj`), který obsahuje přidané soubory Docker-Compose. yml, jak je znázorněno na obrázku 5-8.

![Snímek obrazovky s uzlem Docker-psací v Průzkumník řešení.](./media/docker-app-development-workflow/docker-compose-tree-node.png)

**Obrázek 5-8**. Uzel stromu **Docker-psacího** uzlu přidaný do sady Visual Studio 2017 Průzkumník řešení

Pomocí příkazu `docker-compose up` můžete nasadit aplikaci s více kontejnery s jedním souborem Docker-Compose. yml. Visual Studio však přidá skupinu, takže můžete přepsat hodnoty v závislosti na prostředí (vývoj nebo produkce) a typu spuštění (vydání nebo ladění). Tato funkce bude vysvětlena v dalších částech.

![Obrázek pro krok 5](./media/docker-app-development-workflow/step-5-run-containers-compose-app.png)

## <a name="step-5-build-and-run-your-docker-application"></a>Krok 5. Sestavení a spuštění aplikace Docker

Pokud má vaše aplikace jenom jeden kontejner, můžete ho spustit nasazením na hostitele Docker (virtuální počítač nebo fyzický server). Pokud však vaše aplikace obsahuje více služeb, můžete ji nasadit jako složenou aplikaci, a to buď pomocí jednoho příkazu CLI (Docker-sestavit), nebo pomocí sady Visual Studio, která bude tento příkaz používat v rámci pokrývání. Pojďme se podívat na různé možnosti.

### <a name="option-a-running-a-single-container-application"></a>Možnost A: spuštění aplikace s jedním kontejnerem

#### <a name="using-docker-cli"></a>Použití rozhraní Docker CLI

Kontejner Docker můžete spustit pomocí příkazu `docker run`, jak je znázorněno na obrázku 5-9:

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

Výše uvedený příkaz vytvoří novou instanci kontejneru ze zadané image pokaždé, když se spustí. Ke spuštění existující instance kontejneru můžete použít parametr `--name` a pak použít `docker start {name}` (nebo použít ID kontejneru nebo automatické jméno).

![Snímek obrazovky s kontejnerem Docker pomocí příkazu Docker run](./media/docker-app-development-workflow/use-docker-run-command.png)

**Obrázek 5-9**. Spuštění kontejneru Docker pomocí příkazu Docker run

V takovém případě příkaz váže interní port 5000 kontejneru na port 80 hostitelského počítače. To znamená, že hostitel naslouchá na portu 80 a přesměrovává na port 5000 na kontejneru.

Zobrazená hodnota hash je ID kontejneru a je mu přiřazen také náhodný čitelný název, pokud není použita možnost `--name`.

#### <a name="using-visual-studio"></a>Pomocí sady Visual Studio

Pokud jste nepřidali podporu nástroje Orchestrator pro kontejner, můžete také spustit jednu aplikaci kontejneru v sadě Visual Studio stisknutím **kombinace kláves CTRL + F5** a můžete také pomocí **F5** ladit aplikaci v rámci kontejneru. Kontejner se spouští místně pomocí Docker run.

### <a name="option-b-running-a-multi-container-application"></a>Možnost B: spuštění aplikace s více kontejnery

Ve většině podnikových scénářů se aplikace Docker skládá z několika služeb, což znamená, že je nutné spustit aplikaci s více kontejnery, jak je znázorněno na obrázku 5-10.

![Virtuální počítač s několika kontejnery Docker](./media/docker-app-development-workflow/vm-with-docker-containers-deployed.png)

**Obrázek 5-10**. Virtuální počítač s nasazenými kontejnery Docker

#### <a name="using-docker-cli"></a>Použití rozhraní Docker CLI

Chcete-li spustit aplikaci s více kontejnery pomocí Docker CLI, použijte příkaz `docker-compose up`. Tento příkaz používá soubor **Docker-Compose. yml** , který máte na úrovni řešení k nasazení aplikace s více kontejnery. Obrázek 5-11 zobrazuje výsledky při spuštění příkazu z hlavního adresáře řešení, který obsahuje soubor Docker-Compose. yml.

![Zobrazení obrazovky při spuštění příkazu Docker – vytvořit](./media/docker-app-development-workflow/results-docker-compose-up.png)

**Obrázek 5-11**. Příklady výsledků při spuštění příkazu Docker-sestavit

Po spuštění příkazu Docker-sestavit je aplikace a její související kontejnery nasazeny do hostitele Docker, jak je znázorněno na obrázku 5-10.

#### <a name="using-visual-studio"></a>Pomocí sady Visual Studio

Spuštění aplikace s více kontejnery pomocí sady Visual Studio 2017 nemůže získat jednodušší. Stačí stisknout **kombinaci kláves CTRL + F5** ke spuštění nebo **F5** pro ladění, jako obvykle, nastavení projektu **Docker-sestavit** jako spouštěného projektu.  Visual Studio zpracuje všechna potřebná nastavení, takže můžete vytvořit zarážky jako obvykle a ladit tak, co se stane samostatnými procesy běžícími na vzdálených serverech stejným způsobem.

Jak bylo zmíněno dříve, pokaždé, když přidáte podporu řešení Docker do projektu v rámci řešení, je tento projekt konfigurován v souboru Global (Solution-Level) Docker-Compose. yml, který umožňuje spustit nebo ladit celé řešení najednou. Visual Studio spustí jeden kontejner pro každý projekt, který má povolenou podporu řešení Docker, a provede všechny interní kroky (dotnet publish, Docker Build atd.).

Pokud si chcete prohlédnout všechny drudgery, podívejte se na soubor:

`{root solution folder}\obj\Docker\docker-compose.vs.debug.g.yml`

Důležitým bodem je, jak je znázorněno na obrázku 5-12, v aplikaci Visual Studio 2017 je k dispozici další příkaz **Docker** pro akci klávesy F5. Tato možnost umožňuje spustit nebo ladit aplikaci s více kontejnery spuštěním všech kontejnerů, které jsou definovány v souborech Docker-Compose. yml na úrovni řešení. Možnost ladit řešení s více kontejnery znamená, že můžete nastavit několik zarážek, každou zarážku v jiném projektu (kontejneru) a při ladění ze sady Visual Studio se zastavíte na zarážekch definovaných v různých projektech a v systému různé kontejnery.

![Snímek obrazovky s panelem ladění, na kterém je spuštěný projekt Docker-sestavit](./media/docker-app-development-workflow/debug-toolbar-docker-compose-project.png)

**Obrázek 5-12**. Spouštění aplikací s více kontejnery v aplikaci Visual Studio 2017

### <a name="additional-resources"></a>Další zdroje

- **Nasazení kontejneru ASP.NET na hostitele vzdáleného docker** \
  <https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a>Poznámka k testování a nasazení s orchestrací

Příkazy Docker-sestavit a Docker spouštějí (nebo spouštějí a ladí kontejnery v aplikaci Visual Studio) jsou vhodné pro testování kontejnerů ve vašem vývojovém prostředí. Tento přístup ale byste neměli používat pro produkční nasazení, kde byste měli cílit na orchestraci, jako je [Kubernetes](https://kubernetes.io/) nebo [Service Fabric](https://azure.microsoft.com/services/service-fabric/). Pokud používáte Kubernetes, musíte k uspořádání kontejnerů a [služeb](https://kubernetes.io/docs/concepts/services-networking/service/) do sítě použít [lusky](https://kubernetes.io/docs/concepts/workloads/pods/pod/) . K uspořádání a úpravám pod můžete také použít [nasazení](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) .

![Obrázek pro krok 6.](./media/docker-app-development-workflow/step-6-test-app-microservices.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a>Krok 6. Otestování aplikace Docker pomocí místního hostitele Docker

Tento krok se bude lišit v závislosti na tom, co vaše aplikace dělá. V jednoduché webové aplikaci .NET Core, která je nasazena jako jediný kontejner nebo služba, můžete ke službě přistupovat otevřením prohlížeče na hostiteli Docker a přechodem na tuto lokalitu, jak je znázorněno na obrázku 5-13. (Pokud konfigurace v souboru Dockerfile mapuje kontejner na port na hostiteli, který je cokoli jiného než 80, zahrňte do adresy URL port hostitele.)

![Snímek obrazovky odpovědi z místního hostitele/rozhraní API/hodnot](./media/docker-app-development-workflow/test-docker-app-locally-localhost.png)

**Obrázek 5-13**. Příklad testování aplikace Docker místně pomocí místního hostitele

Pokud localhost neukazuje na IP adresu hostitele Docker (ve výchozím nastavení při použití Docker CE, měla by) přejít na vaši službu a použít IP adresu síťové karty vašeho počítače.

Všimněte si, že tato adresa URL v prohlížeči používá port 80 pro konkrétní popsanou ukázku kontejneru. Interní požadavky se ale přesměrují na port 5000, protože to bylo, jak bylo nasazeno pomocí příkazu Docker Run, jak je vysvětleno v předchozím kroku.

Aplikaci můžete také otestovat pomocí oblého terminálu, jak je znázorněno na obrázku 5-14. V instalaci Docker ve Windows je výchozí IP adresa hostitele Docker vždycky 10.0.75.1a kromě skutečné IP adresy vašeho počítače.

![Výstup na konzole z části získání http://10.0.75.1/API/values pomocí oblé.](./media/docker-app-development-workflow/test-docker-app-locally-curl.png)

**Obrázek 5-14**. Příklad testování aplikace Docker v místním prostředí pomocí formátu kudrlinkou

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a>Testování a ladění kontejnerů pomocí sady Visual Studio 2017

Při spuštění a ladění kontejnerů pomocí sady Visual Studio 2017 můžete ladit aplikaci .NET podobným způsobem jako při spuštění bez kontejnerů.

### <a name="testing-and-debugging-without-visual-studio"></a>Testování a ladění bez sady Visual Studio

Pokud vyvíjíte pomocí přístupu Editor/CLI, kontejnery ladění jsou obtížnější a vy budete chtít ladit vygenerováním trasování.

### <a name="additional-resources"></a>Další zdroje

- **Ladění aplikací v místním kontejneru docker** \
  [https://docs.microsoft.com/visualstudio/containers/edit-and-refresh](/visualstudio/containers/edit-and-refresh)

- **Steve Lasker. Sestavování, ladění, nasazení ASP.NET Core aplikací pomocí Docker.** Obrazový. \
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115>

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a>Zjednodušený pracovní postup při vývoji kontejnerů pomocí sady Visual Studio

Pracovní postup při použití sady Visual Studio je efektivně mnohem jednodušší než při použití přístupu Editor/CLI. Většina kroků požadovaných v Docker související se soubory souboru Dockerfile a Docker-Compose. yml jsou v aplikaci Visual Studio skryté nebo zjednodušené, jak je znázorněno na obrázku 5-15.

:::image type="complex" source="./media/docker-app-development-workflow/simplified-life-cycle-containerized-apps-docker-cli.png" alt-text="Diagram znázorňující pět zjednodušených kroků potřebných k vytvoření aplikace.":::
Proces vývoje pro aplikace Docker: 1 – kódování vaší aplikace, 2-zápis souboru Dockerfile/s, 3-vytváření imagí definovaných na souboru Dockerfile/s, 4 – (volitelné) psaní služeb v souboru Docker-Compose. yml, 5 spuštění kontejneru nebo Docker – sestavování aplikací, 6 – testování vaší aplikace nebo mikroslužeb, 7 – Vložení do úložiště a opakování
:::image-end:::

**Obrázek 5-15**. Zjednodušený pracovní postup při vývoji se sadou Visual Studio

Kromě toho je nutné provést krok 2 (přidání podpory Docker do vašich projektů) pouze jednou. Proto je pracovní postup podobný obvyklým vývojářským úlohám při použití rozhraní .NET pro jakýkoliv jiný vývoj. Potřebujete zjistit, co se týká pokrývání (proces sestavení obrazu, jaké základní image používáte, nasazení kontejnerů atd.), a někdy budete také muset upravit soubor souboru Dockerfile nebo Docker-Compose. yml, abyste mohli chování přizpůsobit. Ale většina práce je výrazně zjednodušená pomocí sady Visual Studio, což vám umožní mnohem větší produktivitu.

### <a name="additional-resources"></a>Další zdroje

- **Steve Lasker. .NET Docker – vývoj s využitím sady Visual Studio 2017** \
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a>Použití příkazů PowerShellu v souboru Dockerfile k nastavení kontejnerů Windows

[Kontejnery Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/index) umožňují převést existující aplikace pro Windows na Image Docker a nasadit je pomocí stejných nástrojů jako zbytek ekosystému Docker. Chcete-li použít kontejnery Windows, spusťte příkazy prostředí PowerShell v souboru Dockerfile, jak je znázorněno v následujícím příkladu:

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

V tomto případě používáme základní bitovou kopii Windows serveru (nastavení z) a instalujete službu IIS pomocí příkazu PowerShellu (nastavení spuštění). Podobným způsobem můžete také použít příkazy PowerShellu k nastavení dalších komponent, jako jsou ASP.NET 4. x, .NET 4,6 nebo jakýkoli jiný software pro Windows. Například následující příkaz v souboru Dockerfile nastaví ASP.NET 4,5:

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a>Další zdroje

- **ASPNET-Docker/souboru Dockerfile.** Příklady příkazů PowerShellu, které se mají spustit z fázemi a zahrnutí funkcí Windows. \
  <https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile>

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[Další](../multi-container-microservice-net-applications/index.md)
