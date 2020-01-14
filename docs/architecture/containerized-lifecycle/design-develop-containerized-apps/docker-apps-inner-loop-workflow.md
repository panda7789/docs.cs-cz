---
title: Pracovní postup vývoje vnitřní smyčky pro aplikace Dockeru
description: Seznamte se s pracovním postupem "vnitřní smyčka" pro vývoj aplikací Docker.
ms.date: 02/15/2019
ms.openlocfilehash: 3d2fc889d22dbf02acccfbf9231ad98fca224cff
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75936801"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Pracovní postup vývoje vnitřní smyčky pro aplikace Dockeru

Předtím, než se aktivuje pracovní postup vnější smyčky zahrnující celý cyklus DevOps, začne vše v každém počítači vývojářů, bude se zakódovat vlastní aplikace, pomocí svých preferovaných jazyků nebo platforem a místně se testuje (obrázek 4-21). V každém případě ale budete mít důležitý obecný bod, bez ohledu na to, jaký jazyk, rozhraní nebo platformy si zvolíte. V tomto konkrétním pracovním postupu budete vždy vyvíjet a testovat kontejnery Docker, ale lokálně.

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

S nejnovějšími verzemi Docker pro Mac a Windows je snazší než kdy dřív vyvíjet aplikace Docker a instalace je jednoduchá.

> [!TIP]
> Pokyny, jak nastavit Docker for Windows, najdete v <https://docs.docker.com/docker-for-windows/>.
>
>Pokyny, jak nastavit Docker pro Mac, najdete v tématu <https://docs.docker.com/docker-for-mac/>.

Kromě toho budete potřebovat Editor kódu, abyste mohli skutečně vyvíjet aplikace při použití Docker CLI.

Společnost Microsoft poskytuje Visual Studio Code, což je zjednodušený Editor kódu, který je podporován v systémech Windows, Linux a macOS a poskytuje technologii IntelliSense s [podporou pro řadu jazyků](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, jít, Java, Ruby, Python a většina moderních jazyků), [ladění](https://code.visualstudio.com/Docs/editor/debugging), [integrace s podporou Gitu](https://code.visualstudio.com/Docs/editor/versioncontrol) a [rozšíření](https://code.visualstudio.com/docs/extensions/overview). Tento editor je vhodný pro vývojáře v macOS a Linux. V systému Windows můžete použít také aplikaci Visual Studio.

> [!TIP]
> Pokyny k instalaci Visual Studio Code pro Windows, Linux nebo macOS najdete v článku <https://code.visualstudio.com/docs/setup/setup-overview/>.
>
> Pokyny, jak nastavit Docker pro Mac, najdete v tématu <https://docs.docker.com/docker-for-mac/>.

Můžete pracovat s Docker CLI a napsat kód pomocí editoru kódu, ale použití Visual Studio Code s rozšířením Docker usnadňuje tvorbu `Dockerfile` a `docker-compose.yml` souborů v pracovním prostoru. Můžete také spouštět úlohy a skripty z Visual Studio Code integrované vývojové prostředí (IDE) a spustit příkazy Docker pomocí příkazu Docker CLI pod.

Rozšíření Docker pro VS Code poskytuje následující funkce:

- Automatické generování `Dockerfile` a `docker-compose.yml` souborů

- Zvýrazňování syntaxe a tipy k najetí myší pro soubory `docker-compose.yml` a `Dockerfile`

- IntelliSense (dokončování) pro soubory `Dockerfile` a `docker-compose.yml`

- Linting (chyby a upozornění) pro soubory `Dockerfile`

- Integrace palet příkazů (F1) pro nejběžnější příkazy Docker

- Integrace Průzkumníka pro správu imagí a kontejnerů

- Nasazení imagí z Dockerhubu a kontejnerů Azure Container Registry do Azure App Service

Pokud chcete nainstalovat rozšíření Docker, stiskněte kombinaci kláves CTRL + SHIFT + P, zadejte `ext install`a pak spuštěním příkazu instalovat rozšíření zobrazte seznam rozšíření Marketplace. Potom zadejte **Docker** pro filtrování výsledků a pak vyberte rozšíření podpora Docker, jak je znázorněno na obrázku 4-23.

![Zobrazení rozšíření Docker pro VS Code.](./media/docker-apps-inner-loop-workflow/install-docker-extension-vs-code.png)

**Obrázek 4-23**. Instalace rozšíření Docker v Visual Studio Code

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>Krok 2: vytvoření souboru Dockerfile souvisejícího s existující imagí (prostého operačního systému nebo vývojového prostředí, jako je .NET Core, Node. js a Ruby)

Budete potřebovat `DockerFile` pro vlastní image, která se má sestavit a na kontejner, který se má nasadit. Pokud se vaše aplikace skládá z jedné vlastní služby, budete potřebovat jednu `DockerFile`. Pokud se ale vaše aplikace skládá z několika služeb (jako v architektuře mikroslužeb), budete potřebovat jednu `Dockerfile` na službu.

`DockerFile` se běžně umísťují do kořenové složky vaší aplikace nebo služby a obsahuje požadované příkazy, aby Docker věděl, jak tuto aplikaci nebo službu spustit. Můžete vytvořit své `DockerFile` a přidat je do projektu společně s vaším kódem (Node. js, .NET Core atd.), nebo pokud s prostředím začínáte, podívejte se na následující tip.

> [!TIP]
> Pomocí rozšíření Docker můžete postupovat při použití `Dockerfile` a `docker-compose.yml` souborů souvisejících s kontejnery Docker. Nakonec budete pravděpodobně zapisovat tyto typy souborů bez tohoto nástroje, ale používání rozšíření Docker je dobrým výchozím bodem, který zrychlí výukovou křivku.

Na obrázku 4-24 se můžete podívat, jak se přidávají soubor Docker-skládání pomocí rozšíření Docker pro VS Code.

![Zobrazení konzoly rozšíření Docker pro VS Code.](./media/docker-apps-inner-loop-workflow/add-docker-files-to-workspace-command.png)

**Obrázek 4-24**. Soubory Docker přidané pomocí **příkazu přidat soubory Docker do pracovního prostoru**

Když přidáte souboru Dockerfile, určíte, jakou základní image Docker budete používat (například pomocí `FROM mcr.microsoft.com/dotnet/core/aspnet`). Obvykle sestavíte vlastní image na základní imagi, kterou získáte z oficiálního úložiště v [registru Docker Hub](https://hub.docker.com/) (jako je [image pro .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) nebo [pro Node. js](https://hub.docker.com/_/node/)).

***Použití stávající oficiální image Docker***

Použití oficiálního úložiště jazykové sady s číslem verze zajišťuje, aby byly stejné funkce jazyka dostupné na všech počítačích (včetně vývoje, testování a produkčního prostředí).

Následuje ukázkový souboru Dockerfile pro kontejner .NET Core:

```Dockerfile
# Base Docker image to use  
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
  
# Set the Working Directory and files to be copied to the image  
ARG source  
WORKDIR /app  
COPY ${source:-bin/Release/PublishOutput} .  
  
# Configure the listening port to 80 (Internal/Secured port within Docker host)  
EXPOSE 80  
  
# Application entry point  
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

V tomto případě je bitová kopie založená na verzi 2,2 oficiální bitové kopie ASP.NET Core Docker (pro Linux a Windows), jak na řádku `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`. (Další informace o tomto tématu najdete na stránce [ASP.NET Core Docker image](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) a na stránce s [obrázkem rozhraní Docker .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) ).

V souboru Dockerfile můžete také dát Docker pokyn k naslouchání portu TCP, který budete používat za běhu (například port 80).

V souboru Dockerfile můžete určit další nastavení konfigurace v závislosti na jazyku a rozhraní, které používáte. Například `ENTRYPOINT` řádek s `["dotnet", "MySingleContainerWebApp.dll"]` instruuje Docker na spuštění aplikace .NET Core. Pokud používáte sadu SDK a .NET Core CLI (`dotnet CLI`) k sestavování a spouštění aplikace .NET, toto nastavení by se lišilo. Klíčovým bodem a dalšími nastaveními závisí na jazyku a platformě, kterou zvolíte pro vaši aplikaci.

> [!TIP]
> Další informace o vytváření imagí Docker pro aplikace .NET Core najdete v <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.
>
> Pokud se chcete dozvědět víc o vytváření vlastních imagí, navštivte <https://docs.docker.com/engine/tutorials/dockerimages/>.

**Použití úložišť imagí s více archy**

Jeden název bitové kopie v úložišti může obsahovat varianty platformy, jako je například bitová kopie systému Linux a bitová kopie systému Windows. Tato funkce umožňuje dodavatelům, jako je Microsoft (základní tvůrci obrázků), vytvořit jedno úložiště pro pokrytí více platforem (tj. Linux a Windows). Například úložiště [dotnet/Core/ASPNET](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) dostupné v registru Docker Hub poskytuje podporu pro systémy Linux a Windows nano Server pomocí stejného názvu image.

Načtení image [dotnet/Core/ASPNET](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) z hostitele Windows vyžádá si variantu Windows, zatímco při vyřazování stejného názvu bitové kopie z hostitele se systémem Linux se zažádá o variantu systému Linux.

***Vytvoření základní Image od začátku***

Můžete vytvořit vlastní základní image Docker od začátku, jak je vysvětleno v tomto [článku](https://docs.docker.com/engine/userguide/eng-image/baseimages/) z Docker. Tento scénář je pravděpodobně nevhodný pro vás, pokud právě začínáte s Docker, ale pokud chcete nastavit konkrétní bity vlastní základní image, můžete to provést.

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>Krok 3: vytvořte vlastní image Docker, ve kterých se služba vkládá.

Pro každou vlastní službu, která se skládá z vaší aplikace, budete muset vytvořit související image. Pokud se vaše aplikace skládá z jediné služby nebo webové aplikace, budete potřebovat jenom jednu Image.

> [!NOTE]
> Když vezmete v úvahu "DevOps pracovní postup vnějšího cyklu", image se vytvoří pomocí automatizovaného procesu sestavení pokaždé, když nahrajete zdrojový kód do úložiště Git (průběžná integrace), takže se image vytvoří v globálním prostředí z vašich zdrojový kód.
>
> Ale předtím, než se podíváme na tuto trasu vnější smyčky, musíme zajistit správné fungování aplikace Docker, aby nedošlo k tomu, že neobsahují kód, který nemusí správně fungovat v systému správy zdrojového kódu (Git atd.).
>
> Proto každý vývojář nejprve potřebuje provést celý proces vnitřní smyčky pro místní testování a pokračovat ve vývoji, dokud nechce doručovat kompletní funkci nebo přepnout do systému správy zdrojového kódu.

Pokud chcete vytvořit image v místním prostředí a používat souboru Dockerfile, můžete použít příkaz Docker Build, jak je znázorněno na obrázku 4-25 (můžete také spustit `docker-compose up --build` pro aplikace složené z několika kontejnerů/služeb).

![Snímek obrazovky znázorňující výstup konzoly příkazu Docker Build](./media/docker-apps-inner-loop-workflow/run-docker-build-command.png)

**Obrázek 4-25**. Spouští se sestavení Docker.

V případě potřeby můžete místo přímého spuštění `docker build` ze složky projektu vygenerovat nasazovatelné složky s knihovnami .NET potřebné pomocí příkazu Run `dotnet publish` a pak spustit `docker build`.

Tento příklad vytvoří bitovou kopii Docker s názvem `cesardl/netcore-webapi-microservice-docker:first` (`:first` je značka, jako je například specifická verze). Tento krok můžete provést pro každou vlastní bitovou kopii, kterou potřebujete vytvořit pro svoji sestavenou aplikaci Docker s několika kontejnery.

Existující image můžete najít v místním úložišti (ve vývojovém počítači) pomocí příkazu Docker images, jak je znázorněno na obrázku 4-26.

![Výstup z konzoly z příkazu Docker images zobrazující existující image](./media/docker-apps-inner-loop-workflow/view-existing-images-with-docker-images.png)

**Obrázek 4-26**. Zobrazení existujících imagí pomocí imagí Docker

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>Krok 4: definování služeb v Docker-Compose. yml při sestavování složené aplikace Docker s více službami

Pomocí souboru `docker-compose.yml` můžete definovat sadu souvisejících služeb, které mají být nasazeny jako složená aplikace, a příkazy nasazení popsané v části Další krok.

Vytvořte tento soubor ve složce Main nebo root Solution. měl by mít podobný obsah, jako je zobrazený v tomto souboru `docker-compose.yml`:

```yml
version: '3.4'
services:
  web:
    build: .
    ports:
     - "81:80"
    volumes:
     - .:/code
    depends_on:
     - redis
  redis:
    image: redis
```

V tomto konkrétním případě tento soubor definuje dvě služby: webovou službu (vlastní služba) a službu Redis (oblíbená služba mezipaměti). Každá služba bude nasazena jako kontejner, takže musíme pro každou z nich použít konkrétní image Docker. Pro tuto konkrétní webovou službu bude bitová kopie potřebovat následující:

- Sestavte z souboru Dockerfile v aktuálním adresáři

- Předejte vystavený port 80 na kontejner na port 81 na hostitelském počítači.

- Připojte adresář projektu na hostiteli, aby se/Code v rámci kontejneru, což vám umožní upravit kód bez nutnosti opětovného sestavení image.

- Propojení webové služby se službou Redis

Služba Redis používá [nejnovější veřejnou image Redis](https://hub.docker.com/_/redis/) získanou z registru Docker Hub. [Redis](https://redis.io/) je oblíbený systém mezipaměti pro aplikace na straně serveru.

### <a name="step-5-build-and-run-your-docker-app"></a>Krok 5: sestavení a spuštění aplikace Docker

Pokud má vaše aplikace jenom jeden kontejner, stačí ho spustit nasazením na hostitele Docker (virtuální počítač nebo fyzický server). Pokud je ale vaše aplikace tvořená více službami, je nutné *ji vytvořit*také. Pojďme se podívat na různé možnosti.

***Možnost A: spuštění jednoho kontejneru nebo služby***

Bitovou kopii Docker můžete spustit pomocí příkazu Docker Run, jak je znázorněno zde:

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

U tohoto konkrétního nasazení budeme přesměrování požadavků odeslaných na port 80 na interní port 5000. Aplikace nyní naslouchá na externím portu 80 na úrovni hostitele.

***Možnost B: vytvoření a spuštění aplikace s více kontejnery***

Ve většině podnikových scénářů se aplikace Docker skládá z několika služeb. V těchto případech můžete spustit příkaz `docker-compose up` (obrázek 4-27), který bude používat soubor Docker-Compose. yml, který jste mohli dříve vytvořit. Spuštěním tohoto příkazu nasadíte složenou aplikaci se všemi souvisejícími kontejnery.

![Výstup konzoly z příkazu Docker-sestavit.](./media/docker-apps-inner-loop-workflow/results-docker-compose-up.png)

**Obrázek 4-27**. Výsledky spuštění příkazu Docker-sestavit

Po spuštění `docker-compose up`nasadíte aplikaci a její související kontejnery do hostitele Docker, jak je znázorněno na obrázku 4-28 ve formě reprezentace virtuálního počítače.

![Virtuální počítač spouštějící aplikace s více kontejnery.](./media/docker-apps-inner-loop-workflow/vm-with-docker-containers-deployed.png)

**Obrázek 4-28**. Virtuální počítač s nasazenými kontejnery Docker

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>Krok 6: testování aplikace Docker (místně, na místním VIRTUÁLNÍm počítači CD)

Tento krok se bude lišit v závislosti na tom, co vaše aplikace dělá.

V jednoduchém webovém rozhraní API .NET Core "Hello World" nasazené jako jediný kontejner nebo služba budete potřebovat přístup ke službě pouze zadáním portu TCP určeného v souboru Dockerfile.

Pokud není místní počítač zapnutý, přejděte k vaší službě a vyhledejte IP adresu počítače pomocí tohoto příkazu:

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

V hostiteli Docker otevřete prohlížeč a přejděte k této lokalitě. měla by se zobrazit vaše aplikace nebo služba, jak je znázorněno na obrázku 4-29.

![Zobrazení prohlížeče odpovědi z místního hostitele/rozhraní API/hodnot.](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-localhost.png)

**Obrázek 4-29**. Místní testování aplikace Docker pomocí místního hostitele

Všimněte si, že používá port 80, ale interně se přesměruje na port 5000, protože to je jak bylo nasazeno v `docker run`, jak bylo vysvětleno výše.

Tuto možnost můžete otestovat pomocí OBLÉ z terminálu. V instalaci Docker ve Windows je výchozí IP adresa 10.0.75.1, jak je znázorněno na obrázku 4-30.

![Výstup na konzole z části získání http://10.0.75.1/API/values s kudrlinkou](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-curl.png)

**Obrázek 4-30**. Místní testování aplikace Docker pomocí OBLÉ

**Ladění kontejneru spuštěného v Docker**

Visual Studio Code podporuje ladění Docker, pokud používáte Node. js a jiné platformy, jako jsou kontejnery .NET Core.

Při použití sady Visual Studio pro Windows nebo Mac můžete v Docker ladit také kontejnery .NET Core nebo .NET Framework, jak je popsáno v následující části.

> [!TIP]
> Další informace o ladění kontejnerů Docker Node. js naleznete v tématu <https://blog.docker.com/2016/07/live-debugging-docker/> a <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more>.

>[!div class="step-by-step"]
>[Předchozí](docker-apps-development-environment.md)
>[Další](visual-studio-tools-for-docker.md)
