---
title: Pracovní postup vývoje vnitřní smyčky pro aplikace Dockeru
description: Naučte se pracovní postup "vnitřní smyčka" pro vývoj aplikací Dockeru.
ms.date: 02/15/2019
ms.openlocfilehash: bce047bd5ba75f9ef652a294ff6a15656fc5ac34
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738410"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Pracovní postup vývoje vnitřní smyčky pro aplikace Dockeru

Před aktivací vnější smyčky pracovního postupu zahrnující celý cyklus DevOps, to vše začíná na počítači každého vývojáře, kódování samotné aplikace, pomocí jejich preferované jazyky nebo platformy a testování místně (Obrázek 4-21). Ale v každém případě budete mít důležitý společný bod, bez ohledu na to, jaký jazyk, rámec nebo platformy si vyberete. V tomto konkrétním pracovním postupu vždy vyvíjíte a testujete kontejnery Dockeru, ale místně.

![Diagram znázorňující koncept vývojového prostředí vnitřní smyčky.](./media/docker-apps-inner-loop-workflow/inner-loop-development-context.png)

**Obrázek 4-21**. Kontext vývoje vnitřní smyčky

Kontejner nebo instance image Dockeru bude obsahovat tyto součásti:

- Výběr operačního systému (například linuxová distribuce nebo Windows)

- Soubory přidané vývojářem (například binární soubory aplikací)

- Konfigurace (například nastavení prostředí a závislosti)

- Pokyny pro to, jaké procesy má Docker spouštět

Můžete nastavit pracovní postup vývoje vnitřní smyčky, který využívá Docker jako proces (popsané v další části). Zvažte, že počáteční kroky k nastavení prostředí nejsou zahrnuty, protože stačí to udělat jednou.

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>Vytváření jedné aplikace v kontejneru Dockeru pomocí kódu Visual Studio a cli Dockeru

Aplikace se shodnou z vašich vlastních služeb a dalších knihoven (závislostí).

Obrázek 4-22 ukazuje základní kroky, které obvykle potřebujete provést při vytváření aplikace Dockeru, následované podrobnými popisy každého kroku.

![Diagram znázorňující sedm kroků potřebných k vytvoření kontejnerizované aplikace.](./media/docker-apps-inner-loop-workflow/life-cycle-containerized-apps-docker-cli.png)

**Obrázek 4-22**. Pracovní postup na vysoké úrovni pro životní cyklus kontejnerizovaných aplikací Dockeru pomocí cli Dockeru

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>Krok 1: Začněte kódovat v kódu Visual Studia a vytvořte počáteční směrný plán aplikace nebo služby

Způsob, jakým vyvíjíte aplikaci, je podobný způsobu, jakým to děláte bez Dockeru. Rozdíl je v tom, že při vývoji nasazujete a testujete aplikaci nebo služby spuštěné v kontejnerech Dockeru umístěných v místním prostředí (jako je virtuální počítač s Linuxem nebo Windows).

**Nastavení místního prostředí**

S nejnovějšími verzemi Dockeru pro Mac a Windows je vývoj aplikací Dockeru jednodušší než kdy dřív a nastavení je jednoduché.

> [!TIP]
> Pokyny k nastavení Dockeru pro <https://docs.docker.com/docker-for-windows/>Windows najdete v .
>
>Pokyny k nastavení Dockeru pro <https://docs.docker.com/docker-for-mac/>Mac najdete v .

Kromě toho budete potřebovat editor kódu, takže můžete skutečně rozvíjet aplikaci při použití rozhraní se kdispozici jako rozhraní se kšak dockeru.

Microsoft poskytuje Visual Studio Code, což je lehký editor kódu, který je podporován v systémech Windows, Linux a macOS a poskytuje intelliSense [podporu pro mnoho jazyků](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python a většina moderních jazyků), [ladění](https://code.visualstudio.com/Docs/editor/debugging), integrace [s Git](https://code.visualstudio.com/Docs/editor/versioncontrol) a podpora [rozšíření](https://code.visualstudio.com/docs/extensions/overview). Tento editor je skvělý pro vývojáře macOS a Linux. V systému Windows můžete také použít Visual Studio.

> [!TIP]
> Pokyny k instalaci kódu Sady Visual Studio pro Windows, <https://code.visualstudio.com/docs/setup/setup-overview/>Linux nebo macOS najdete na .
>
> Pokyny k nastavení Dockeru pro <https://docs.docker.com/docker-for-mac/>Mac najdete v .

Můžete pracovat s Rozhraním řízení chování dockeru a psát kód pomocí libovolného editoru `Dockerfile` kódu, ale pomocí kódu Visual Studio s rozšířením Dockeru usnadňuje vytváření souborů a `docker-compose.yml` soubory ve vašem pracovním prostoru. Můžete také spustit úlohy a skripty z IDE kódu Visual Studio ke spuštění příkazů Dockeru pomocí cli Dockeru pod ním.

Rozšíření Dockeru pro Kód VS poskytuje následující funkce:

- Automatické `Dockerfile` `docker-compose.yml` generování souborů

- Tipy pro zvýraznění syntaxe a najetí na jev `docker-compose.yml` a `Dockerfile` soubory

- Technologie IntelliSense (dokončení) a `Dockerfile` `docker-compose.yml` souborů

- Linting (chyby a `Dockerfile` upozornění) pro soubory

- Integrace palety příkazů (F1) pro nejběžnější příkazy Dockeru

- Integrace Průzkumníka pro správu obrázků a kontejnerů

- Nasazení ibi z DockerHubu a registrů kontejnerů Azure do azure app služby

Pokud chcete nainstalovat rozšíření Dockeru, stiskněte `ext install`Ctrl+Shift+P, zadejte a spusťte příkaz Instalovat rozšíření, abyste zoátrali seznam rozšíření Marketplace. Dále zadejte **docker** pro filtrování výsledků a pak vyberte rozšíření podpory Dockeru, jak je znázorněno na obrázku 4-23.

![Zobrazení rozšíření Docker pro Kód VS.](./media/docker-apps-inner-loop-workflow/install-docker-extension-vs-code.png)

**Obrázek 4-23**. Instalace rozšíření Dockeru v kódu Visual Studia

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>Krok 2: Vytvoření souboru DockerFile souvisejícího s existující bitovou kopii (prostředí prostého operačního systému nebo dev, jako je .NET Core, Node.js a Ruby)

Budete potřebovat `DockerFile` vlastní image, která má být sestavena a na kontejner, který chcete nasadit. Pokud je vaše aplikace tvořena jedinou vlastní službou, budete potřebovat jednu `DockerFile`. Ale pokud se vaše aplikace skládá z více služeb (jako v `Dockerfile` architektuře mikroslužeb), budete potřebovat jednu na službu.

Obvykle `DockerFile` se umisťuje do kořenové složky vaší aplikace nebo služby a obsahuje požadované příkazy, aby Docker věděl, jak tuto aplikaci nebo službu nastavit a spustit. Můžete vytvořit `DockerFile` a přidat do projektu spolu s kódem (node.js, .NET Core, atd.), nebo pokud jste v prostředí noví, podívejte se na následující tip.

> [!TIP]
> Můžete použít rozšíření Docker u vás `Dockerfile` při `docker-compose.yml` použití a soubory související s kontejnery Dockeru. Nakonec budete pravděpodobně psát tyto druhy souborů bez tohoto nástroje, ale pomocí rozšíření Docker je dobrým výchozím bodem, který urychlí křivku učení.

Na obrázku 4-24 můžete vidět, jak se přidá soubor docker-compose pomocí rozšíření Dockeru pro kód VS.

![Zobrazení konzoly rozšíření Dockeru pro Kód VS.](./media/docker-apps-inner-loop-workflow/add-docker-files-to-workspace-command.png)

**Obrázek 4-24**. Soubory Dockeru přidané pomocí **příkazu Přidat soubory Dockeru do pracovního prostoru**

Když přidáte DockerFile, určíte, jakou základní image Dockeru `FROM mcr.microsoft.com/dotnet/core/aspnet`budete používat (například pomocí ). Obvykle vytvoříte vlastní bitovou kopii nad základní bitovou kopii, kterou získáte z libovolného oficiálního úložiště v [registru Docker Hub](https://hub.docker.com/) (jako je [obrázek pro .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) nebo obrázek pro [Node.js).](https://hub.docker.com/_/node/)

***Použití existujícího oficiálního obrázku Dockeru***

Pomocí oficiálníúložiště zásobníku jazyka s číslem verze zajišťuje, že stejné funkce jazyka jsou k dispozici na všech počítačích (včetně vývoje, testování a výroby).

Následuje ukázkový soubor DockerFile pro kontejner .NET Core:

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

V tomto případě je obraz založen na verzi 2.2 oficiálního ASP.NET Image Core Docker (multi-arch pro Linux a Windows), podle řádku `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`. (Další informace o tomto tématu najdete na stránce [ASP.NET core dockerimage](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) a na stránce [.NET Core Docker Image).](https://hub.docker.com/_/microsoft-dotnet-core/)

V DockerFile můžete také pokyn Docker poslouchat tcp port, který budete používat za běhu (například port 80).

Můžete zadat další nastavení konfigurace v Dockerfile, v závislosti na jazyku a rozhraní, které používáte. Například `ENTRYPOINT` řádek s `["dotnet", "MySingleContainerWebApp.dll"]` říká Docker spustit aplikaci .NET Core. Pokud k sestavení a spuštění aplikace .NET používáte`dotnet CLI`sadu SDK a rozhraní .NET Core CLI ( ), bude toto nastavení jiné. Klíčovým bodem je, že řádek ENTRYPOINT a další nastavení závisí na jazyku a platformě, kterou zvolíte pro vaši aplikaci.

> [!TIP]
> Další informace o vytváření iniciál Dockeru pro aplikace .NET Core najdete v . <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>
>
> Další informace o vytváření vlastních <https://docs.docker.com/engine/tutorials/dockerimages/>obrázků naleznete v najdete v aplikaci .

**Použití víceobloukových úložišť obrázků**

Název jedné bitové kopie v repo může obsahovat varianty platformy, jako je například bitová kopie Linuxu a bitová kopie systému Windows. Tato funkce umožňuje dodavatelům, jako je Microsoft (tvůrci základních obrázků), vytvořit jeden repo, který by pokrýval více platforem (tedy Linux a Windows). Například úložiště [dotnet/core/aspnet,](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) které je k dispozici v registru Docker Hub, poskytuje podporu pro Linux a Windows Nano Server pomocí stejného názvu bitové kopie.

Vytažením bitové kopie [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) z hostitele systému Windows se vyžádá varianta systému Windows, zatímco vytažení stejného názvu bitové kopie z hostitele Linuxu vytáhne variantu Linuxu.

***Vytvoření základního obrázku od začátku***

Můžete vytvořit vlastní základní image Dockeru od začátku, jak je vysvětleno v tomto [článku](https://docs.docker.com/engine/userguide/eng-image/baseimages/) z Dockeru. Tento scénář pravděpodobně není nejlepší pro vás, pokud jste právě začínás Docker, ale pokud chcete nastavit konkrétní bity vlastní základní image, můžete to udělat.

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>Krok 3: Vytvoření vlastních ireček Dockeru, které do ní vloží vaši službu

Pro každou vlastní službu, která obsahuje vaši aplikaci, budete muset vytvořit související obrázek. Pokud se vaše aplikace skládá z jedné služby nebo webové aplikace, budete potřebovat jen jeden obrázek.

> [!NOTE]
> Vezmeme-li v úvahu "vnější smyčka DevOps workflow", budou obrázky vytvořeny automatizovaným procesem sestavení při každém nabízení zdrojového kódu do úložiště Git (průběžná integrace), takže obrázky budou vytvořeny v tomto globálním prostředí z vašeho zdrojového kódu.
>
> Ale předtím, než budeme uvažovat o tom, že vnější smyčka trasy, musíme zajistit, že aplikace Docker je skutečně funguje správně tak, aby nebyly push kód, který nemusí fungovat správně do systému správy zdrojového kódu (Git, atd.).
>
> Proto každý vývojář nejprve musí provést celý proces vnitřní smyčky k testování místně a pokračovat ve vývoji, dokud chtějí push kompletní funkce nebo změnit systém správy zdrojového kódu.

Chcete-li vytvořit image v místním prostředí a pomocí DockerFile, můžete použít příkaz sestavení dockeru, jak `docker-compose up --build` je znázorněno na obrázku 4-25 (můžete také spustit pro aplikace složené z několika kontejnerů/služeb).

![Snímek obrazovky zobrazující výstup konzoly příkazu docker build.](./media/docker-apps-inner-loop-workflow/run-docker-build-command.png)

**Obrázek 4-25**. Spuštění sestavení dockeru

Volitelně můžete namísto `docker build` přímého spuštění ze složky projektu nejprve vygenerovat nasaditelnou `dotnet publish` složku s `docker build`knihovnami .NET potřebnými pomocí příkazu run a poté spustit .

Tento příklad vytvoří image Dockeru s názvem `cesardl/netcore-webapi-microservice-docker:first` (`:first` je značka, jako konkrétní verze). Tento krok můžete provést pro každou vlastní bitovou kopii, kterou potřebujete vytvořit pro komponoci aplikace Docker s několika kontejnery.

Existující obrázky najdete v místním úložišti (vývojovém počítači) pomocí příkazu ilustračních zařízení, jak je znázorněno na obrázku 4-26.

![Konzolový výstup z iobrazů řídicího místa s existujícími obrazy.](./media/docker-apps-inner-loop-workflow/view-existing-images-with-docker-images.png)

**Obrázek 4-26**. Zobrazení existujících obrazů pomocí imitací dockeru

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>Krok 4: Definování služeb v docker-compose.yml při vytváření složené aplikace Docker u více služeb

Pomocí `docker-compose.yml` souboru můžete definovat sadu souvisejících služeb, které mají být nasazeny jako komponovaná aplikace s příkazy nasazení vysvětlenými v části dalšího kroku.

Vytvořte tento soubor v hlavní nebo kořenové složce řešení; měl by mít podobný obsah, `docker-compose.yml` který je uveden v tomto souboru:

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

V tomto konkrétním případě tento soubor definuje dvě služby: webovou službu (vlastní službu) a službu redis (oblíbenou službu mezipaměti). Každá služba bude nasazena jako kontejner, takže pro každou z nich musíme použít konkrétní image Dockeru. Pro tuto konkrétní webovou službu bude nutné obrázek provést následující kroky:

- Sestavení z DockerFile v aktuálním adresáři

- Přepošlete exponovaný port 80 na kontejner u portu 81 na hostitelském počítači

- Připojení adresáře projektu na hostiteli do /code v kontejneru, takže můžete upravit kód bez nutnosti znovu sestavit bitovou kopii

- Propojení webové služby se službou redis

Služba redis používá [nejnovější veřejnou image redis](https://hub.docker.com/_/redis/) z registru Docker Hub. [redis](https://redis.io/) je populární cache systém pro aplikace na straně serveru.

### <a name="step-5-build-and-run-your-docker-app"></a>Krok 5: Vytvoření a spuštění aplikace Docker

Pokud vaše aplikace má jenom jeden kontejner, stačí ho spustit nasazením do hostitele Dockeru (virtuálnípočítač nebo fyzický server). Pokud je však vaše aplikace tvořena více službami, musíte *ji také sestavit*. Podívejme se na různé možnosti.

***Možnost A: Spuštění jednoho kontejneru nebo služby***

Image Dockeru můžete spustit pomocí příkazu docker run, jak je znázorněno zde:

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

Pro toto konkrétní nasazení přesměrujeme požadavky odeslané na port 80 na interní port 5000. Nyní aplikace naslouchá na externím portu 80 na úrovni hostitele.

***Možnost B: Vytvoření a spuštění aplikace s více kontejnery***

Ve většině podnikových scénářů aplikace Dockeru se bude skládat z více služeb. V těchto případech můžete `docker-compose up` spustit příkaz (obrázek 4-27), který bude používat soubor docker-compose.yml, který jste vytvořili dříve. Spuštění tohoto příkazu nasadí složenou aplikaci se všemi souvisejícími kontejnery.

![Výstup konzoly z příkazu docker-compose up.](./media/docker-apps-inner-loop-workflow/results-docker-compose-up.png)

**Obrázek 4-27**. Výsledky spuštění příkazu "docker-compose up"

Po spuštění `docker-compose up`nasadíte aplikaci a související kontejnery do hostitele Dockeru, jak je znázorněno na obrázku 4-28, v reprezentaci virtuálního počítače.

![Virtuální montovny se spouštějí aplikace s více kontejnery.](./media/docker-apps-inner-loop-workflow/vm-with-docker-containers-deployed.png)

**Obrázek 4-28**. Virtuální virtuální ms s nasazenými kontejnery Dockeru

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>Krok 6: Otestujte aplikaci Dockeru (místně, v místním virtuálním počítači CD)

Tento krok se bude lišit v závislosti na tom, co vaše aplikace dělá.

V jednoduchém webovém rozhraní .NET Core Web API "Hello World" nasazeném jako jeden kontejner nebo služba byste měli získat přístup ke službě poskytnutím portu TCP určeného v souboru DockerFile.

Pokud localhost není zapnuta, chcete-li přejít na službu, vyhledejte IP adresu pro počítač pomocí tohoto příkazu:

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

Na hostiteli Dockeru otevřete prohlížeč a přejděte na tento web. měli byste vidět vaše aplikace / služba běží, jak je znázorněno na obrázku 4-29.

![Zobrazení prohlížeče odpovědi z localhost/API/values.](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-localhost.png)

**Obrázek 4-29**. Testování aplikace Docker místně pomocí localhost

Všimněte si, že používá port 80, ale interně je přesměrován na port 5000, `docker run`protože tak to bylo nasazeno s , jak bylo vysvětleno dříve.

Můžete to vyzkoušet pomocí CURL z terminálu. V instalaci Dockeru v systému Windows je výchozí ADRESA IP 10.0.75.1, jak je znázorněno na obrázku 4-30.

![Konzolový výstup http://10.0.75.1/API/values od získání s curl](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-curl.png)

**Obrázek 4-30**. Testování aplikace Docker místně pomocí CURL

**Ladění kontejneru spuštěného v Dockeru**

Visual Studio Code podporuje ladění Dockeru, pokud používáte Node.js a další platformy, jako jsou kontejnery .NET Core.

Při použití Visual Studia pro Windows nebo Mac můžete také ladit kontejnery .NET Core nebo .NET Framework v Dockeru, jak je popsáno v další části.

> [!TIP]
> Další informace o ladění kontejnerů Node.js <https://blog.docker.com/2016/07/live-debugging-docker/> Dockeru naleznete v tématu a <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more>.

>[!div class="step-by-step"]
>[Předchozí](docker-apps-development-environment.md)
>[další](visual-studio-tools-for-docker.md)
