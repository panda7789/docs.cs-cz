---
title: Pracovní postup vývoje vnitřní smyčky pro aplikace Dockeru
description: Přečtěte si pracovní postup "vnitřní smyčky" pro vývoj aplikací Dockeru.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 1134ff439235609db840c85a1e67bc9fe4ccec84
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835678"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Pracovní postup vývoje vnitřní smyčky pro aplikace Dockeru

Před aktivací pracovního postupu vnější smyčky pokrývající celý DevOps cyklu, to všechno začíná každý vývojář počítače, psaní kódu aplikace pomocí jejich preferované jazyky a platformy a jejím místním otestováním (obrázek 4 – 21). Ale v každém případě budete mít o důležitý fakt v běžných bez ohledu na to, jaký jazyk, rozhraní nebo platformy zvolíte. V tomto konkrétním pracovním postupu jsou vždy vývoj a testování kontejnery Dockeru, ale místně.

![Krok 1 – kód/spuštění/ladění](./media/image18.png)

**Obrázek 4 – 21**. Kontext vývoje vnitřní smyčky

Kontejner nebo instance image Dockeru, bude obsahovat tyto komponenty:

-   Výběru operačního systému (například distribuci Linuxu nebo Windows)

- Soubory přidané vývojář (třeba binární soubory aplikace)

-   Konfigurace (například nastavení prostředí a závislosti)

- Pokyny pro jaké procesy spuštění pomocí Dockeru

Můžete nastavit pracovní postup vývoje vnitřní smyčky, s využitím Dockeru jako proces (popsané v další části). Vezměte v úvahu, že počáteční kroky k nastavení prostředí nejsou zahrnuty, protože je potřeba jenom jednou.

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>Vytvoření jednoduché aplikace v kontejneru Dockeru pomocí Visual Studio Code a rozhraní příkazového řádku Dockeru

Aplikace se skládá z vlastní služby a další knihovny (závislosti).

Obrázek 4 – 22 uvedeny základní kroky, které je obvykle potřeba provádět při vytváření aplikace Dockeru, za nímž následuje podrobný popis jednotlivých kroků.

![Přehled pracovního postupu: Krok 1 – kód, krok 2 – zapisovat soubory Dockerfile, krok 3 – vytváření imagí, které jsou definovány soubory Dockerfile, krok 4 – definovat souborem docker-compose krok 5: spuštění kontejnerů služby nebo aplikace skládá, krok 6 – Test aplikace, krok 7 – doručit na začátku vnější smyčky (kanálů CI/CD) ani pokračovat de veloping.](./media/image19.png)

**Obrázek 4 – 22**. Pracovní postup vysoké úrovně pro životní cyklus pro Docker kontejnerizovaných aplikací pomocí rozhraní příkazového řádku Dockeru

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>Krok 1: Pusťte se do programování ve Visual Studio Code a vytvořit směrný plán počáteční aplikace nebo služby

Způsob, jak vyvíjet aplikace je podobný způsobu práce bez Dockeru. Rozdíl je, že při vývoji, máte nasazení a testování vaší aplikace nebo služby v rámci kontejnery Dockeru, které jsou umístěny v místním prostředí (např. virtuální počítač s Linuxem nebo Windows).

**Nastavení místního prostředí**

S nejnovější verzí Dockeru pro Mac a Windows je jednodušší než dříve k vývoji aplikací Dockeru a instalační program je jednoduché.

> [! INFORMACE O]
>
> Pokyny k nastavení Dockeru pro Windows, přejděte na <https://docs.docker.com/docker-for-windows/>.
>
>Pokyny k nastavení Dockeru pro Mac, přejděte na <https://docs.docker.com/docker-for-mac/>.

Kromě toho budete potřebovat editor kódu tak, aby ve skutečnosti můžete vyvíjet aplikace pomocí rozhraní příkazového řádku Dockeru.

Společnost Microsoft poskytuje Visual Studio Code, který je ve zjednodušeném editoru kódu, který se podporuje na Macu, Windows a Linux a nabízí technologii IntelliSense s [podporu mnoha jazyků](https://code.visualstudio.com/docs/languages/overview) (jazyk JavaScript, .NET, Go, Java, Ruby, Python a většinu Moderní jazyky), [ladění](https://code.visualstudio.com/Docs/editor/debugging), [integrace s úložištěm Git](https://code.visualstudio.com/Docs/editor/versioncontrol) a [rozšíření podpory](https://code.visualstudio.com/docs/extensions/overview). Tento editor se skvěle hodí pro vývojáře Mac a Linux. Ve Windows také můžete použít celou aplikaci Visual Studio.

> [! INFORMACE O]
>
> Pokyny k instalaci Visual Studio Code pro Windows, Mac nebo Linux, přejděte na <https://code.visualstudio.com/docs/setup/setup-overview/>.
>
> Pokyny k nastavení Dockeru pro Mac, přejděte na <https://docs.docker.com/docker-for-mac/>.

Můžete pracovat pomocí rozhraní příkazového řádku Dockeru a napište svůj kód pomocí editoru kódu, ale pomocí Visual Studio Code se rozšíření Docker umožňuje snadno autorovi `Dockerfile` a `docker-compose.yml` soubory ve vašem pracovním prostoru. Na Visual Studio IDE kód ke spuštění příkazů Docker pomocí rozhraní příkazového řádku Dockeru pod můžete spouštět úlohy a skripty.

Rozšíření Docker pro VS Code poskytuje následující funkce:

- Automatické `Dockerfile` a `docker-compose.yml` generování souborů

- Syntaxe zvýrazňování a při najetí myší tipy pro `docker-compose.yml` a `Dockerfile` soubory

- Technologie IntelliSense (dokončování) pro `Dockerfile` a `docker-compose.yml` soubory

- Linting (chyby a upozornění) pro `Dockerfile` soubory

- Příkaz integrace palety (F1) pro nejčastěji používané příkazy Dockeru

- Integrace Průzkumníka správy Imagí a kontejnery

- Nasadit Image v Dockerhubu a Azure Container registry do služby Azure App Service

Chcete-li nainstalovat rozšíření Docker, stiskněte klávesy Ctrl + Shift + P, zadejte `ext install`, a potom spusťte instalaci rozšíření příkazu zobrazíte seznam rozšíření Marketplace. Dále zadejte **docker** k filtrování výsledků a pak vyberte rozšíření podpory Dockeru, jak je znázorněno v obrázek 4 – 23.

![Přehled rozšíření Dockeru pro VS Code.](./media/image20.png)

**Obrázek 4 – 23**. Instaluje se rozšíření Dockeru v aplikaci Visual Studio Code

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>Krok 2: Vytvoření souboru DockerFile související s existující image (plain operačního systému nebo vývoj prostředí, jako je .NET Core, Node.js a Ruby)

Budete potřebovat `DockerFile` na vlastní image má být sestaven a na kontejneru pro nasazení. Pokud vaše aplikace se skládá z jedné vlastní službě, budete potřebovat jeden `DockerFile`. Ale pokud se vaše aplikace skládá z více služeb (stejně jako v architektuře mikroslužeb), budete potřebovat `Dockerfile` každou službu.

`DockerFile` Je obvykle umístěn v kořenové složce aplikace nebo služby a obsahuje požadované příkazy tak, které Docker ví, jak nastavit a spustit aplikaci nebo službu. Můžete vytvořit vaše `DockerFile` a přidejte ho do svého projektu spolu s kódu (node.js, .NET Core, atd.), nebo pokud jsou pro vás nové prostředí, podívejte se na následující vrcholu.

> [!TIP]
>
> Můžete použít rozšíření Docker a provede vás při použití `Dockerfile` a `docker-compose.yml` soubory související s kontejnery Dockeru. Nakonec pravděpodobně napíšete tyto typy souborů bez tento nástroj, ale použití rozšíření Docker je dobrým výchozím bodem, který urychlí vaše křivka.

Obrázek 4 – 24 můžete zobrazit, jak docker-compose se přidá soubor s použitím rozšíření Dockeru pro VS Code.

![Zobrazení konzoly rozšíření Dockeru pro VS Code.](./media/image24.png)

**Obrázek 4 – 24**. Přidat pomocí souborů dockeru **Docker přidat soubory do příkazu pracovního prostoru**

Když přidáte soubor DockerFile, zadejte co základní image Dockeru, který budete používat (například `FROM microsoft/aspnetcore`). Obvykle vytvoříte vlastní bitovou kopii nad základní image, kterou můžete získat z jakékoli oficiální úložiště [registru Docker Hub](https://hub.docker.com/) (stejně jako [bitovou kopii pro .NET Core](https://hub.docker.com/r/microsoft/dotnet/) nebo [pro Node.js](https://hub.docker.com/_/node/)).

***Použít existující oficiální image Dockeru***

Použití zásobníku jazyka oficiální úložiště s číslem verze zajistí, že stejné funkce jazyka jsou k dispozici na všech počítačích (včetně vývoje, testování a produkce).

Následuje ukázkový soubor DockerFile pro .NET Core kontejneru:

```Dockerfile
# Base Docker image to use  
FROM microsoft/dotnet:2.1-aspnetcore-runtime
  
# Set the Working Directory and files to be copied to the image  
ARG source  
WORKDIR /app  
COPY ${source:-bin/Release/PublishOutput} .  
  
# Configure the listening port to 80 (Internal/Secured port within Docker host)  
EXPOSE 80  
  
# Application entry point  
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

V tomto případě bitovou kopii podle verze 2.1 oficiální image Dockeru ASP.NET Core (více arch pro systémy Linux a Windows), podle řádku `FROM microsoft/dotnet:2.1-aspnetcore-runtime`. (Další informace o tomto tématu najdete v článku [Image Dockeru ASP.NET Core](https://hub.docker.com/r/microsoft/aspnetcore/) stránky a [Image Dockeru .NET Core](https://hub.docker.com/r/microsoft/dotnet/) stránky).

V souboru DockerFile se dá taky nastavit Docker nenaslouchá na portu TCP, který budete používat v době běhu (například port 80).

Můžete zadat další nastavení konfigurace v souboru Dockerfile, v závislosti na jazyk a rozhraní, které používáte. Například `ENTRYPOINT` čára s `["dotnet", "MySingleContainerWebApp.dll"]` říká Dockeru spustit aplikaci .NET Core. Pokud používáte sadu SDK a rozhraní příkazového řádku .NET Core (`dotnet CLI`) k sestavení a spuštění aplikace .NET, toto nastavení bude odlišná. Klíčovým bodem tedy je, že vstupní bod řádku a další nastavení závisí na jazyk a platformu, kterou zvolíte pro vaši aplikaci.

> [! INFORMACE O]
>
> Další informace o vytváření imagí Dockeru pro aplikace .NET Core, přejděte na <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.
>
> Další informace o vytváření vlastních imagí, přejděte na <https://docs.docker.com/engine/tutorials/dockerimages/>.

**Použití úložiště image více architektury**

Název jedné image do úložiště může obsahovat variant, platformy, jako jsou image Linuxu a Windows image. Tato funkce umožňuje dodavatelé, jako je Microsoft (creators základní image) k vytvoření jednoho úložiště pro víc platforem (to znamená, Linux a Windows). Například [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) úložiště k dispozici v registru Docker Hub poskytuje podporu pro systémy Linux a Windows Nano Server pomocí stejného názvu image.

Souhrnné informace [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image z hostitele Windows si vyžádá Windows variant, zatímco přebírání stejný název image z hostitele platformy Linux si vyžádá varianty Linuxu.

***Vytvoření zcela nové základní image***

Můžete vytvořit vlastní základní image Dockeru od začátku, jak je popsáno v tomto [článku](https://docs.docker.com/engine/userguide/eng-image/baseimages/) od Dockeru. Tento scénář není pravděpodobně pro vás nejvýhodnější Pokud právě začínáte s Dockerem, ale pokud chcete nastavit konkrétní bity základní image, můžete to provést.

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>Krok 3: Vytvoření vlastní Image Dockeru vložení služby

U každé aplikace se skládá z vlastní služby budete muset vytvořit související image. Pokud vaše aplikace skládá z jedné služby nebo webové aplikace, budete potřebovat jenom jedné image.

> [!NOTE]
>
> Když se vezme v úvahu "workflow pro DevOps vnější smyčky", obrázky, bude vytvořen pomocí automatizovaného procesu sestavení pokaždé, když vložíte změny zdrojového kódu do úložiště Git (Nepřetržitá integrace), takže Image se vytvoří v globálním prostředí z vaší zdrojový kód.
>
> Ale předtím, než jsme zvažte, že přejdete na tuto trasu vnější smyčky, potřebujeme zajistit, že aplikace Dockeru ve skutečnosti funguje správně tak, aby jejich není push kód, který nemusí správně fungovat do systému správy zdrojového kódu (Git atd.).
>
> Každý vývojář proto nejprve musí udělat celý proces vnitřní smyčky, místně ji otestovat a pokračovat ve vývoji, dokud chtějí push kompletní funkce nebo změňte na systém správy zdrojového kódu.

Pro vytvoření image v místním prostředí a pomocí souboru DockerFile, můžete použít příkaz sestavení dockeru, jak je ukázáno v obrázek 4 – 25 (můžete také spustit `docker-compose up --build` pro aplikace, které sestává z několika kontejnerů nebo služeb Team Foundation).

![Výstup na konzole docker-compose sestavení, zobrazuje průběh stahování imagí.](./media/image25.png)

**Obrázek 4 – 25**. Spouštění sestavení dockeru

Volitelně můžete místo přímo spouštět `docker build` ze složky projektu, nejprve můžete vygenerovat nasaditelný složku s knihovnami .NET potřebuje používat spuštění `dotnet publish` příkaz a poté spusťte `docker build`.

Tento příklad vytvoří image Dockeru s názvem `cesardl/netcore-webapi-microservice-docker:first` (`:first` jsou klíčová slova, jako jsou konkrétní verzi). Je-li provést tento krok pro každou vlastní image, které je potřeba vytvořit složené aplikace Dockeru s několika kontejnery.

Najdete existujících bitových kopií ve vašem místním úložišti (vývojovém počítači) s využitím dockeru příkaz bitové kopie, jak je znázorněno v obrázek 4 – 26.

![Výstup z příkazu imagí dockeru, zobrazení existujících imagí konzoly.](./media/image26.png)

**Obrázek 4 – 26**. Zobrazení existujících obrázků s využitím Image dockeru

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>Krok 4: Definování vašich služeb v docker-compose.yml při vytváření složené aplikace Dockeru s více službami

S `docker-compose.yml` soubor, můžete definovat sadu souvisejících služeb umožňující nasadit ho jako aplikace skládá pomocí příkazů nasazení je vysvětleno v další části kroku.

Vytvoření tohoto souboru ve vaší hlavní nebo kořenové složky řešení; měl by mít podobný zobrazená v tomto obsahu `docker-compose.yml` souboru:

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

V tomto konkrétním případě tento soubor definuje dvě služby: webové služby (vaše vlastní služba) a službu redis (Oblíbené mezipaměti služby). Každá služba se nasadí jako kontejner, proto musíme pomocí konkrétní image Dockeru pro každý. Pro tento konkrétní webovou službu na obrázku potřebovat provést následující kroky:

- Sestavení z soubor DockerFile v aktuálním adresáři

- Dál vystavené port 80 v kontejneru na port 81 na hostitelském počítači

- Připojení adresáře projektu v hostiteli /code v rámci kontejneru, takže budete moct změnit kód bez nutnosti znovu sestavovat image

- Odkaz webové služby ke službě redis

Použití služby redis [nejnovější veřejné redis image](https://hub.docker.com/_/redis/) získaných z registru Docker Hub. [redis](https://redis.io/) je systém Oblíbené mezipaměti pro aplikace na straně serveru.

### <a name="step-5-build-and-run-your-docker-app"></a>Krok 5: Sestavení a spuštění aplikace Dockeru

Pokud vaše aplikace má pouze jeden kontejner, stačí ji spustit nasazení na hostitele Docker (virtuální počítač nebo fyzický server). Nicméně pokud vaše aplikace se skládá z několika služeb, budete muset *tvoří ji*také. Podívejme se na různé možnosti.

***Možnost A: Spustit jedním kontejnerem nebo služby***

Image Dockeru můžete spustit pomocí dockeru, spusťte příkaz, jak je znázorněno zde:

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

Pro toto konkrétní nasazení jsme budete přesměruje požadavky odeslané na portu 80 na interní port 5000. Aplikace je teď naslouchá na externím portu 80 na úrovni hostitele.

***Možnost B: Vytvářet a spouštět aplikace typu kontejner více***

Ve většině scénářů organizace aplikaci v Dockeru se skládá z více služeb. Pro tyto případy můžete spustit `docker-compose up` příkazu (obrázek 4 – 27), který použije soubor docker-compose.yml, kterou může jste vytvořili dříve. Spustí tento příkaz nasadí složené aplikaci se všemi jeho související kontejnerů.

![Výstup z konzoly docker-compose up příkazu.](./media/image27.png)

**Obrázek 4 – 27**. Výsledky spuštění příkazu "docker-compose up"

Po spuštění `docker-compose up`, budete nasazovat aplikace a její související kontejnerů do hostitele Dockeru, jak je znázorněno v obrázek 4 – 28, v reprezentaci virtuálního počítače.

![Virtuální počítač spuštěný vícekontejnerových aplikací.](./media/image28.png)

**Obrázek 4 – 28**. Virtuální počítač s kontejnery Dockeru nasazené

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>Krok 6: Otestujte aplikaci Docker (místně, v místní virtuální počítač CD)

Tento krok se liší v závislosti na tom, co vaše aplikace stojí.

V jednoduchých .NET Core webového rozhraní API "Hello World" nasadit jako jedním kontejnerem nebo služby by stačí pro přístup ke službě zadáním TCP port zadaný v souboru DockerFile.

Pokud localhost není zapnutý, přejděte k vaší službě zjistit IP adresu počítače pomocí tohoto příkazu:

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

Na hostitele Docker spusťte prohlížeč a přejděte na web; vaše aplikace nebo služby spuštěné, měli byste vidět, jak je ukázáno v obrázek 4 – 29.

![Zobrazit v prohlížeči neodpověděla localhost/API/hodnoty.](./media/image29.png)

**Obrázek 4 – 29**. Testování aplikace místně s použitím místního hostitele Docker

Všimněte si, že používá port 80, ale interně se přesměruje na port 5000, protože to je, jak byla nasazena s `docker run`, jak je vysvětleno výše.

Můžete ho otestovat pomocí příkazu CURL z terminálu. V instalaci Dockeru na Windows je výchozí IP 10.0.75.1, jak je znázorněno v obrázek 4-30.

![Získávání výstupu konzoly http://10.0.75.1/API/values pomocí curl](./media/image30.png)

**Obrázek 4-30**. Testování aplikace Docker místně pomocí CURL

**Ladění kontejneru spuštěného v Dockeru**

Visual Studio Code podporuje ladění Dockeru, pokud používáte Node.js a jiných platformách, jako je .NET Core kontejnery.

Můžete také ladit kontejnery .NET Core nebo .NET Framework v Dockeru při použití Visual Studio pro Windows nebo Mac, jak je popsáno v další části.

> [! INFORMACE O]
>
> Další informace o ladění kontejnerů Dockeru Node.js, přejděte na <https://blog.docker.com/2016/07/live-debugging-docker/> a <https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/>.

>[!div class="step-by-step"]
>[Předchozí](docker-apps-development-environment.md)
>[další](visual-studio-tools-for-docker.md)
