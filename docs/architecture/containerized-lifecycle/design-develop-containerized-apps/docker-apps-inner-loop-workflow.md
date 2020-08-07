---
title: Pracovní postup vývoje vnitřní smyčky pro aplikace Dockeru
description: Přečtěte si o pracovním postupu pro vývoj vnitřních smyček pro aplikace Docker.
ms.date: 08/06/2020
ms.openlocfilehash: bf837ab53fff2b53cf141b2e621d484cff9b6889
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916183"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Pracovní postup vývoje vnitřní smyčky pro aplikace Dockeru

Předtím, než se aktivuje pracovní postup vnější smyčky zahrnující celý cyklus DevOps, začne vše v každém počítači vývojářů, bude se zakódovat vlastní aplikace, pomocí svých preferovaných jazyků nebo platforem a místně se testuje (obrázek 4-21). V každém případě ale budete mít důležitý obecný bod, bez ohledu na to, jaký jazyk, rozhraní nebo platformy si zvolíte. V tomto konkrétním pracovním postupu budete vždy vyvíjet a testovat kontejnery Docker v jiných prostředích, ale lokálně.

![Diagram znázorňující koncept prostředí pro vývoj vnitřních smyček.](./media/docker-apps-inner-loop-workflow/inner-loop-development-context.png)

**Obrázek 4-21**. Vývojový kontext pro vnitřní smyčku

Kontejner nebo instance image Docker bude obsahovat tyto komponenty:

- Výběr operačního systému (například distribuce systému Linux nebo Windows)

- Soubory přidané vývojářem (například binární soubory aplikace)

- Konfigurace (například nastavení prostředí a závislosti)

- Pokyny pro procesy, které se mají spustit přes Docker

Můžete nastavit vývojový postup pro vnitřní smyčku, který využívá Docker jako proces (popsaný v následující části). Vezměte v úvahu, že nejsou zahrnuté počáteční kroky pro nastavení prostředí, protože ho stačí udělat jenom jednou.

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>Vytvoření jedné aplikace v kontejneru Docker pomocí Visual Studio Code a Docker CLI

Aplikace se vytvářejí z vašich vlastních služeb a dalších knihoven (závislosti).

Obrázek 4-22 ukazuje základní kroky, které obvykle potřebujete provést při sestavování aplikace Docker, po kterém následují podrobné popisy jednotlivých kroků.

![Diagram znázorňující sedm kroků, které je potřeba k vytvoření kontejnerové aplikace.](./media/docker-apps-inner-loop-workflow/life-cycle-containerized-apps-docker-cli.png)

**Obrázek 4-22**. Pracovní postup vysoké úrovně pro životní cyklus aplikací Docker s využitím Docker CLI

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>Krok 1: začátek kódování Visual Studio Code a vytvoření počátečního směrného plánu aplikace nebo služby

Způsob vývoje aplikace je podobný způsobu, jakým jste to provedete bez Docker. Rozdíl je v tom, že při vývoji nasazujete a testujete svou aplikaci nebo služby běžící v kontejnerech Docker umístěných ve vašem místním prostředí (jako je třeba virtuální počítač Linux nebo Windows).

**Nastavení místního prostředí**

S nejnovějšími verzemi Docker desktopu pro Mac a Windows je snazší než kdy dřív vyvíjet aplikace Docker a instalace je jednoduchá.

> [!TIP]
> Pokyny k nastavení Docker desktopu pro Windows najdete v tématu <https://docs.docker.com/docker-for-windows/> .
>
> Pokyny, jak nastavit Docker Desktop pro Mac, najdete v tématu <https://docs.docker.com/docker-for-mac/> .

Kromě toho budete potřebovat Editor kódu, abyste mohli skutečně vyvíjet aplikace při použití Docker CLI.

Společnost Microsoft poskytuje Visual Studio Code, což je zjednodušený Editor kódu, který je podporován v systémech Windows, Linux a macOS a poskytuje technologii IntelliSense s [podporou pro řadu jazyků](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, jít, Java, Ruby, Python a většina moderních jazyků), [ladění](https://code.visualstudio.com/Docs/editor/debugging), [integrace s podporou Gitu](https://code.visualstudio.com/Docs/editor/versioncontrol) a [rozšíření](https://code.visualstudio.com/docs/extensions/overview). Tento editor je vhodný pro vývojáře v macOS a Linux. V systému Windows můžete použít také aplikaci Visual Studio.

> [!TIP]
> Pokyny, jak nainstalovat Visual Studio Code pro Windows, Linux nebo macOS, najdete v tématu <https://code.visualstudio.com/docs/setup/setup-overview/> .
>
> Pokyny, jak nastavit Docker pro Mac, najdete v tématu <https://docs.docker.com/docker-for-mac/> .

Můžete pracovat s Docker CLI a napsat svůj kód pomocí editoru kódu, ale použití Visual Studio Code s rozšířením Docker usnadňuje tvorbu `Dockerfile` a vytváření `docker-compose.yml` souborů v pracovním prostoru. Můžete také spouštět úlohy a skripty z Visual Studio Code integrované vývojové prostředí (IDE) a spustit příkazy Docker pomocí příkazu Docker CLI pod.

Rozšíření Docker pro VS Code poskytuje následující funkce:

- Automatické `Dockerfile` `docker-compose.yml` generování souborů a souborů

- Zvýrazňování syntaxe a tipy k najetí myší pro `docker-compose.yml` `Dockerfile` soubory a

- IntelliSense (dokončování) pro `Dockerfile` `docker-compose.yml` soubory a

- Linting (chyby a upozornění) pro `Dockerfile` soubory

- Integrace palet příkazů (F1) pro nejběžnější příkazy Docker

- Integrace Průzkumníka pro správu imagí a kontejnerů

- Nasazení imagí z Dockerhubu a kontejnerů Azure Container Registry do Azure App Service

Chcete-li nainstalovat rozšíření Docker, stiskněte klávesy CTRL + SHIFT + P, zadejte `ext install` a poté spusťte příkaz Install Extension a zobrazte seznam rozšíření Marketplace. Potom zadejte **Docker** pro filtrování výsledků a pak vyberte rozšíření podpora Docker, jak je znázorněno na obrázku 4-23.

![Zobrazení rozšíření Docker pro VS Code.](media/docker-apps-inner-loop-workflow/install-docker-extension-vs-code.png)

**Obrázek 4-23**. Instalace rozšíření Docker v Visual Studio Code

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>Krok 2: vytvoření souboru Dockerfile souvisejícího s existující imagí (prostého operačního systému nebo vývojového prostředí, jako je .NET Core, Node.js a Ruby)

Budete potřebovat `DockerFile` vlastní image, která se má sestavit a na kontejner, který se má nasadit. Pokud se vaše aplikace skládá z jedné vlastní služby, budete potřebovat jednu `DockerFile` . Pokud se ale vaše aplikace skládá z několika služeb (jako v architektuře mikroslužeb), budete ji potřebovat `Dockerfile` pro každou službu.

`DockerFile`Obvykle se nachází v kořenové složce vaší aplikace nebo služby a obsahuje požadované příkazy, aby Docker věděl, jak nastavit a spustit tuto aplikaci nebo službu. Můžete vytvořit `DockerFile` a přidat ho do projektu společně s vaším kódem (node.js, .NET Core atd.), nebo pokud s prostředím začínáte, podívejte se na následující tip.

> [!TIP]
> Můžete použít rozšíření Docker, které vás provede při použití `Dockerfile` `docker-compose.yml` souborů a souvisejících s kontejnery Docker. Nakonec budete pravděpodobně zapisovat tyto typy souborů bez tohoto nástroje, ale používání rozšíření Docker je dobrým výchozím bodem, který zrychlí výukovou křivku.

Na obrázku 4-24 se můžete podívat na postup přidání souborů Docker do projektu pomocí rozšíření Docker pro VS Code:

1. Otevřete paletu příkazů, zadejte "**Docker**" a vyberte**Přidat soubory Docker do pracovního prostoru**.
2. Vybrat aplikační platformu (ASP.NET Core)
3. Vybrat operační systém (Linux)
4. Zahrnout volitelné Docker Compose soubory
5. Zadejte porty k publikování (80, 443).
6. Výběr projektu

![Postup přidání souborů Docker s rozšířením Docker](media/docker-apps-inner-loop-workflow/add-docker-files-to-workspace-command.png)

**Obrázek 4-24**. Soubory Docker přidané pomocí příkazu **Přidat soubory Docker do pracovního prostoru**

Když přidáte souboru Dockerfile, určíte, jakou základní image Docker budete používat (například pomocí `FROM mcr.microsoft.com/dotnet/core/aspnet` ). Obvykle sestavíte vlastní image na základní imagi, kterou získáte z oficiálního úložiště v [registru Docker Hub](https://hub.docker.com/) (jako je [image pro .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) nebo ta [pro Node.js](https://hub.docker.com/_/node/)).

> [!TIP]
> Tento postup budete muset opakovat pro každý projekt ve vaší aplikaci. Rozšíření však vyzve k přepsání vygenerovaného souboru Docker-rekládací soubor po prvním spuštění. Měli byste odpovědět na Nepřepisovat, takže rozšíření vytvoří samostatné soubory Docker-skládání, které pak můžete sloučit před spuštěním Docker-skládání.

**_Použití stávající oficiální image Docker_**

Použití oficiálního úložiště jazykové sady s číslem verze zajišťuje, aby byly stejné funkce jazyka dostupné na všech počítačích (včetně vývoje, testování a produkčního prostředí).

Následuje ukázkový souboru Dockerfile pro kontejner .NET Core:

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /src
COPY ["src/WebApi/WebApi.csproj", "src/WebApi/"]
RUN dotnet restore "src/WebApi/WebApi.csproj"
COPY . .
WORKDIR "/src/src/WebApi"
RUN dotnet build "WebApi.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebApi.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApi.dll"]
```

V tomto případě je bitová kopie založená na verzi 3,1 oficiální image s ASP.NET Core Docker (více imagí pro Linux a Windows), jak je uvedeno na řádku `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1` . (Další informace o tomto tématu najdete na stránce [ASP.NET Core Docker image](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) a na stránce s [obrázkem rozhraní Docker .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) ).

V souboru Dockerfile můžete také dát Docker pokyn k naslouchání portu TCP, který budete používat za běhu (například port 80 nebo 443).

V souboru Dockerfile můžete určit další nastavení konfigurace v závislosti na jazyku a rozhraní, které používáte. Například `ENTRYPOINT` řádek s `["dotnet", "WebMvcApplication.dll"]` informacemi Docker pro spuštění aplikace .NET Core. Pokud používáte sadu SDK a .NET Core CLI ( `dotnet CLI` ) k sestavování a spouštění aplikace .NET, toto nastavení by se lišilo. Klíčovým bodem a dalšími nastaveními závisí na jazyku a platformě, kterou zvolíte pro vaši aplikaci.

> [!TIP]
> Další informace o vytváření imagí Docker pro aplikace .NET Core naleznete v <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images> .
>
> Další informace o vytváření vlastních imagí najdete na webu <https://docs.docker.com/engine/tutorials/dockerimages/> .

**Použití úložišť imagí s více archy**

Jeden název bitové kopie v úložišti může obsahovat varianty platformy, jako je například bitová kopie systému Linux a bitová kopie systému Windows. Tato funkce umožňuje dodavatelům, jako je Microsoft (základní tvůrci obrázků), vytvořit jedno úložiště pro pokrytí více platforem (tj. Linux a Windows). Například úložiště [dotnet/Core/ASPNET](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) dostupné v registru Docker Hub poskytuje podporu pro systémy Linux a Windows nano Server pomocí stejného názvu image.

Načtení image [dotnet/Core/ASPNET](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) z hostitele Windows vyžádá si variantu Windows, zatímco při vyřazování stejného názvu bitové kopie z hostitele se systémem Linux se zažádá o variantu systému Linux.

**_Vytvoření základní Image od začátku_**

Můžete vytvořit vlastní základní image Docker od začátku, jak je vysvětleno v tomto [článku](https://docs.docker.com/engine/userguide/eng-image/baseimages/) z Docker. Tento scénář je pravděpodobně nevhodný pro vás, pokud právě začínáte s Docker, ale pokud chcete nastavit konkrétní bity vlastní základní image, můžete to provést.

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>Krok 3: vytvořte vlastní image Docker, ve kterých se služba vkládá.

Pro každou vlastní službu, která se skládá z vaší aplikace, budete muset vytvořit související image. Pokud se vaše aplikace skládá z jediné služby nebo webové aplikace, budete potřebovat jenom jednu Image.

> [!NOTE]
> Když vezmete v úvahu "DevOps pracovní postup vnějšího cyklu", image se vytvoří pomocí automatizovaného procesu sestavení pokaždé, když nahrajete zdrojový kód do úložiště Git (průběžná integrace), takže se image vytvoří v globálním prostředí ze zdrojového kódu.
>
> Před tím, než se podíváte na tuto trasu vnější smyčky, je nutné zajistit, aby aplikace Docker správně fungovala, aby nenabízela kód, který nemusí správně fungovat pro systém správy zdrojového kódu (Git atd.).
>
> Proto každý vývojář nejprve potřebuje provést celý proces vnitřní smyčky pro místní testování a pokračovat ve vývoji, dokud nechce doručovat kompletní funkci nebo přepnout do systému správy zdrojového kódu.

Pokud chcete vytvořit image v místním prostředí a používat souboru Dockerfile, můžete použít příkaz Docker Build, jak je znázorněno na obrázku 4-25, protože tento obrázek již pro vás vypadá a sestavuje image pro všechny služby v aplikaci pomocí jednoduchého příkazu.

![Snímek obrazovky s výstupem konzoly příkazu Docker-skládání buildu](media/docker-apps-inner-loop-workflow/run-docker-build-command.png)

**Obrázek 4-25**. Spouští se sestavení Docker.

Místo toho, aby bylo možné přímo spustit `docker build` ze složky projektu, můžete nejprve vygenerovat nasazovatelné složky s knihovnami .NET potřebné pomocí příkazu Run `dotnet publish` a potom spustit `docker build` .

Tento příklad vytvoří image Docker s názvem `explore-docker-vscode/webapi:latest` ( `:latest` je značka, jako je například specifická verze). Tento krok můžete provést pro každou vlastní bitovou kopii, kterou potřebujete vytvořit pro svoji sestavenou aplikaci Docker s několika kontejnery. V další části se ale dozvíme, že to je snazší pomocí `docker-compose` .

Existující image můžete najít v místním úložišti (ve vývojovém počítači) pomocí `docker images` příkazu, jak je znázorněno na obrázku 4-26.

![Výstup z konzoly z příkazu Docker images zobrazující existující image](media/docker-apps-inner-loop-workflow/view-existing-images-with-docker-images.png)

**Obrázek 4-26**. Zobrazení existujících imagí pomocí imagí Docker

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>Krok 4: definování služeb v Docker-Compose. yml při sestavování složené aplikace Docker s více službami

Pomocí tohoto `docker-compose.yml` souboru můžete definovat sadu souvisejících služeb, které mají být nasazeny jako složená aplikace, a příkazy nasazení popsané v části Další krok.

Vytvořte tento soubor ve složce Main nebo root Solution. měl by mít podobný obsah, jako je zobrazený v tomto `docker-compose.yml` souboru:

```yml
version: "3.4"

services:
  webapi:
    image: webapi
    build:
      context: .
      dockerfile: src/WebApi/Dockerfile
    ports:
      - 51080:80
    depends_on:
      - redis
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://+:80

  webapp:
    image: webapp
    build:
      context: .
      dockerfile: src/WebApp/Dockerfile
    ports:
      - 50080:80
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://+:80
      - WebApiBaseAddress=http://webapi

  redis:
    image: redis
```

V tomto konkrétním případě tento soubor definuje tři služby: službu webového rozhraní API (vlastní služba), webovou aplikaci a službu Redis (oblíbená služba mezipaměti). Každá služba bude nasazena jako kontejner, takže pro každou z nich potřebujete použít konkrétní image Docker. Pro tuto konkrétní aplikaci:

- Služba webového rozhraní API je sestavena z souboru Dockerfile v `src/WebApi/Dockerfile` adresáři.

- Port hostitele 51080 se přepošle na vystavený port 80 na `webapi` kontejneru.

- Služba webového rozhraní API závisí na službě Redis.

- Webová aplikace přistupuje ke službě webového rozhraní API pomocí interní adresy: `http://webapi` .

- Služba Redis používá [nejnovější veřejnou image Redis](https://hub.docker.com/_/redis/) získanou z registru Docker Hub. [Redis](https://redis.io/) je oblíbený systém mezipaměti pro aplikace na straně serveru.

### <a name="step-5-build-and-run-your-docker-app"></a>Krok 5: sestavení a spuštění aplikace Docker

Pokud má vaše aplikace jenom jeden kontejner, stačí ho spustit nasazením na hostitele Docker (virtuální počítač nebo fyzický server). Pokud je ale vaše aplikace tvořená více službami, je nutné _ji vytvořit_také. Pojďme se podívat na různé možnosti.

**_Možnost A: spuštění jednoho kontejneru nebo služby_**

Bitovou kopii Docker můžete spustit pomocí příkazu Docker Run, jak je znázorněno zde:

```console
docker run -t -d -p 50080:80 explore-docker-vscode/webapp:latest
```

U tohoto konkrétního nasazení budeme přesměrování požadavků odeslaných na port 50080 na hostiteli do interního portu 80.

**_Možnost B: vytvoření a spuštění aplikace s více kontejnery_**

Ve většině podnikových scénářů se aplikace Docker skládá z několika služeb. V těchto případech můžete spustit `docker-compose up` příkaz (obrázek 4-27), který bude používat soubor Docker-Compose. yml, který jste vytvořili dříve. Spuštění tohoto příkazu vytvoří všechny vlastní image a nasadí složenou aplikaci se všemi souvisejícími kontejnery.

![Výstup konzoly z příkazu Docker-sestavit.](media/docker-apps-inner-loop-workflow/results-docker-compose-up.png)

**Obrázek 4-27**. Výsledky spuštění příkazu Docker-sestavit

Po spuštění `docker-compose up` aplikace nasadíte aplikaci a její související kontejnery do hostitele Docker, jak je znázorněno na obrázku 4-28, ve formě reprezentace virtuálního počítače.

![Virtuální počítač spouštějící aplikace s více kontejnery.](./media/docker-apps-inner-loop-workflow/vm-with-docker-containers-deployed.png)

**Obrázek 4-28**. Virtuální počítač s nasazenými kontejnery Docker

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>Krok 6: testování aplikace Docker (místně, na místním VIRTUÁLNÍm počítači CD)

Tento krok se bude lišit v závislosti na tom, co vaše aplikace dělá.

V jednoduchém webovém rozhraní API .NET Core "Hello World" nasazené jako jediný kontejner nebo služba budete potřebovat přístup ke službě pouze zadáním portu TCP určeného v souboru Dockerfile.

V hostiteli Docker otevřete prohlížeč a přejděte k této lokalitě. měla by se zobrazit vaše aplikace nebo služba, jak je znázorněno na obrázku 4-29.

![Zobrazení prohlížeče odpovědi z místního hostitele/rozhraní API/hodnot.](media/docker-apps-inner-loop-workflow/test-docker-app-locally-localhost.png)

**Obrázek 4-29**. Místní testování aplikace Docker pomocí prohlížeče

Všimněte si, že používá port 50080, ale interně se přesměruje na port 80, protože to je to, jak bylo nasazeno v `docker compose` , jak bylo vysvětleno výše.

Tuto možnost můžete otestovat pomocí prohlížeče pomocí OBLÉho z terminálu, jak je znázorněno na obrázku 4-30.

![Výsledek ze složené aplikace získaný zhttp://localhost:51080/WeatherForecast](media/docker-apps-inner-loop-workflow/test-docker-app-locally-curl.png)

**Obrázek 4-30**. Místní testování aplikace Docker pomocí OBLÉ

**Ladění kontejneru spuštěného v Docker**

Pokud používáte Node.js a jiné platformy, jako jsou kontejnery .NET Core, Visual Studio Code podporuje ladění Docker.

Při použití sady Visual Studio pro Windows nebo Mac můžete v Docker ladit také kontejnery .NET Core nebo .NET Framework, jak je popsáno v následující části.

> [!TIP]
> Další informace o ladění Node.js kontejnerů Docker naleznete v tématu <https://blog.docker.com/2016/07/live-debugging-docker/> a <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more> .

> [!div class="step-by-step"]
> [Předchozí](docker-apps-development-environment.md) 
>  [Další](visual-studio-tools-for-docker.md)
