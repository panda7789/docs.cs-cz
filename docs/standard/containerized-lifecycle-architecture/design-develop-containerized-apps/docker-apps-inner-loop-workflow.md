---
title: Pracovní postup vývoje vnitřní smyčky pro aplikace Dockeru
description: Přečtěte si pracovní postup "vnitřní smyčky" pro vývoj aplikací Dockeru.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 2d592f92153040d910dcf529ec21770693f5973c
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442318"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Pracovní postup vývoje vnitřní smyčky pro aplikace Dockeru

Před aktivací pracovního postupu vnější smyčky pokrývající celý DevOps cyklu, to všechno začíná každý vývojář počítače, psaní kódu aplikace pomocí jejich preferované jazyky a platformy a jejím místním otestováním (obrázek 4 – 14). Ale v každém případě budete mít velmi důležitý bod v běžném, bez ohledu na to, jaký jazyk, rozhraní nebo platformy zvolíte. V tomto konkrétním pracovním postupu jsou vždy vývoj a testování kontejnery Dockeru, ale místně.

![](./media/image18.png)

Obrázek 4 – 14: Kontext vývoje vnitřní smyčky

Kontejner nebo instance image Dockeru, bude obsahovat tyto komponenty:

-   Výběru operačního systému (například distribuci Linuxu nebo Windows)

-   Soubory přidané vývojář (třeba binární soubory aplikace)

-   Konfigurace (například nastavení prostředí a závislosti)

-   Pokyny pro jaké procesy spuštění pomocí Dockeru

Můžete nastavit pracovní postup vývoje vnitřní smyčky, s využitím Dockeru jako proces (popsané v další části). Vezměte v úvahu, že počáteční kroky k nastavení prostředí není zahrnuta, protože je potřeba udělat jenom jednou.

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>Vytvoření jednoduché aplikace v kontejneru Dockeru pomocí Visual Studio Code a rozhraní příkazového řádku Dockeru

Aplikace se skládá z vlastní služby a další knihovny (závislosti).

Obrázek 4 – 15 ukazuje základní kroky, které je obvykle potřeba provádět při vytváření aplikace Dockeru, za nímž následuje podrobný popis jednotlivých kroků.

![](./media/image19.png)

Obrázek 4 – 15: Pracovní postup vysoké úrovně pro životní cyklus pro Docker kontejnerizovaných aplikací pomocí rozhraní příkazového řádku Dockeru

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>Krok 1: Pusťte se do programování ve Visual Studio Code a vytvořit směrný plán počáteční aplikace nebo služby

Způsob, jak vyvíjet aplikace je hodně podobné způsobu práce bez Dockeru. Rozdíl je, že při vývoji, máte nasazení a testování vaší aplikace nebo služby v rámci kontejnery Dockeru, které jsou umístěny v místním prostředí (např. virtuální počítač s Linuxem nebo Windows).

**Nastavení místního prostředí**

S nejnovější verzí Dockeru pro Mac a Windows je jednodušší než dříve k vývoji aplikací Dockeru a instalační program je jednoduché.

**Další informace o** pokyny týkající se nastavení Dockeru pro Windows, přejděte na [ https://docs.docker.com/docker-for-windows/ ](https://docs.docker.com/docker-for-windows/).

Pokyny k nastavení Dockeru pro Mac, přejděte na <https://docs.docker.com/docker-for-mac/>.

Kromě toho budete potřebovat editor kódu tak, aby ve skutečnosti můžete vyvíjet aplikace pomocí rozhraní příkazového řádku Dockeru.

Společnost Microsoft poskytuje Visual Studio Code, který je ve zjednodušeném editoru kódu, který se podporuje na Macu, Windows a Linux a nabízí technologii IntelliSense s [podporu mnoha jazyků](https://code.visualstudio.com/docs/languages/overview) (jazyk JavaScript, .NET, Go, Java, Ruby, Python a většinu Moderní jazyky), [ladění](https://code.visualstudio.com/Docs/editor/debugging), [integrace s úložištěm Git](https://code.visualstudio.com/Docs/editor/versioncontrol) a [rozšíření podpory](https://code.visualstudio.com/docs/extensions/overview). Tento editor se skvěle hodí pro vývojáře Mac a Linux. Ve Windows také můžete použít celou aplikaci Visual Studio.

**Další informace o** pokyny k instalaci Visual Studio pro Windows, Mac nebo Linux, přejděte na <https://code.visualstudio.com/docs/setup/setup-overview/>.

Můžete pracovat pomocí rozhraní příkazového řádku Dockeru a napište svůj kód pomocí editoru kódu, ale pokud používáte Visual Studio Code, umožní snadno vytvořit soubor Dockerfile a soubory docker-compose.yml ve vašem pracovním prostoru. Navíc můžete spouštět úlohy Visual Studio Code z integrovaného vývojového prostředí, který vás vyzve k skripty, které mohou běžet elaborované operací s použitím rozhraní příkazového řádku Dockeru pod.

Poskytuje rozšíření, které budete muset nainstalovat Visual Studio Code. Chcete-li to provést, stiskněte kombinaci kláves Ctrl + Shift + P, zadejte **ext, přípona instalace**, a pak spusťte rozšíření: Instalace rozšíření příkazu zobrazíte seznam rozšíření Marketplace. Dále zadejte **docker** filtrování výsledků a potom vyberte soubor Dockerfile a Docker Compose souboru (yml) rozšíření podpory, jak je znázorněno v obrázek 4-16.

![](./media/image20.png)

Obrázek 4 – 16: Instaluje se rozšíření Dockeru v aplikaci Visual Studio Code

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>Krok 2: Vytvoření souboru DockerFile související s existující image (plain operačního systému nebo vývoj prostředí, jako je .NET Core, Node.js a Ruby)

Budete potřebovat soubor DockerFile na vlastní image má být sestaven a na kontejneru pro nasazení, proto pokud vaše aplikace se skládá z jedné vlastní službě, budete potřebovat jeden soubor DockerFile. Ale pokud se vaše aplikace skládá z více služeb (stejně jako v architektuře mikroslužeb), budete potřebovat jeden soubor Dockerfile každou službu.

Soubor DockerFile je obvykle umístěn v kořenové složce aplikace nebo služby a obsahuje požadované příkazy tak, které Docker ví, jak nastavit a spustit aplikaci nebo službu. Můžete vytvořit váš soubor DockerFile a přidejte do projektu spolu s kódu (node.js, .NET Core, atd.), nebo pokud jsou pro vás nové prostředí, podívejte se na následující vrcholu.

> [!TIP]
> Můžete použít nástroj příkazového řádku, který volá [yo docker](https://github.com/Microsoft/generator-docker), který vygeneruje uživatelské rozhraní soubory z projektu v jazyce, výběru a přidá požadované soubory konfigurace Dockeru. V podstatě, abychom vývojářům Začínáme vytvoří odpovídající soubor DockerFile, docker-compose.yml a jiné přidružené skripty pro sestavení a spouští vaše kontejnery Dockeru. Tento generátor yeoman zobrazí výzvu na pár otázek, s výzvou hostitele vývoj pro vybraný jazyk a cílový kontejner.

![Yo docker](./media/image21.png)

Například obrázek 4-17 ukazuje dvě snímky obrazovky z terminály ve Windows a na Macu, v obou případech se systémem yo docker, která bude generovat ukázkové kódové projekty (aktuálně .NET Core, go a Node.js jako seznam podporovaných jazyků) ještě nakonfigurováno pro práci na horní Dockeru.

![](./media/image22.PNG)  ![](./media/image23.png)

Obrázek 4 – 17: docker příkazu yo nástroje ve Windows (vlevo) a na Macu

Obrázek 4 – 18 představuje příklad použití yo docker až budete mít existující projekt .NET Core v místo, kde můžete být automaticky.

![](./media/image24.PNG)

Obrázek 4 – 18: yo docker pomocí stávající .NET Core probíhá projekt

Ze souboru DockerFile zadejte co základní image Dockeru, který budete používat (například "FROM microsoft/dotnet:1.0.0-core"). Obvykle vytvoříte vlastní bitovou kopii nad základní image, který můžete získat z jakékoli oficiální úložiště [registru Docker Hub](https://hub.docker.com/) (stejně jako [bitovou kopii pro .NET Core](https://hub.docker.com/r/microsoft/dotnet/) nebo jeden [pro Node.js](https://hub.docker.com/_/node/)).

***Možnost A: Použít existující oficiální image Dockeru***

Použití zásobníku jazyka oficiální úložiště s číslem verze zajistí, že stejné funkce jazyka jsou k dispozici na všech počítačích (včetně vývoje, testování a produkce).

Následuje ukázkový soubor DockerFile pro .NET Core kontejneru:

```
# Base Docker image to use
FROM microsoft/aspnetcore:1.0.1\

# Set the Working Directory and files to be copied to the image
ARG source
WORKDIR /app
COPY ${source:-bin/Release/PublishOutput} .

# Configure the listening port to 80 (Internal/Secured port within Docker host)
EXPOSE 80

# Application entry point
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

V tomto případě používá verzi 1.0.1 oficiální image Dockeru ASP.NET Core pro Linux s názvem microsoft/aspnetcore:1.0.1. Pro další podrobnosti najdete [Image Dockeru ASP.NET Core stránky](https://hub.docker.com/r/microsoft/aspnetcore/) a [Image Dockeru .NET Core stránky](https://hub.docker.com/r/microsoft/dotnet/). Je také může použít jiné srovnatelné image jako uzel: 4-onbuild pro Node.js nebo mnoha jiných předem nakonfigurovaným imagím pro vývojářské jazyky, které jsou k dispozici v [Docker Hubu](https://hub.docker.com/explore/).

V souboru DockerFile potřebujete také dáte pokyn, aby Docker nenaslouchá na portu TCP, který budete používat v době běhu (například port 80).

Existují další řádky konfigurace, které můžete přidat v souboru DockerFile v závislosti na jazyk a rozhraní, které používáte, takže Docker ví, jak spustit aplikaci. Pro instanci, potřebujete ENTRYPOINT uspokojování \["dotnet", "MyCustomMicroservice.dll"\] ke spuštění aplikace .NET Core, i když můžete mít více variant v závislosti na přístup k sestavení a spuštění služby. Pokud chcete sestavovat a spouštět aplikace .NET při použití sady SDK a rozhraní příkazového řádku dotnet, bylo by mírně liší. Dolní řádek je, že vstupní bod řádku plus další řádky budou lišit v závislosti na jazyk nebo platformu vybraných pro vaše aplikace.

**Další informace o** informace o vytváření imagí Dockeru pro aplikace .NET Core, přejděte na [ https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images ](../../../core/docker/building-net-docker-images.md).

Další informace o vytváření vlastních imagí, přejděte na [ https://docs.docker.com/engine/\ kurzy/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/).

**Úložiště s více platformami image**

Kontejnery Windows jsou více běžně se vyskytujícím, jednoho úložiště může obsahovat variant, platformy, jako jsou bitové kopie operačních systémů Linux a Windows. Toto je nová funkce přicházející v Dockeru, který umožňuje dodavatelům použít jednoho úložiště pro různé platformy, například [microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) úložiště, které je k dispozici na Dockerhubu registru. Jako funkci přicházejí k životu, přebírání tuto bitovou kopii z hostitele Windows přetáhne Windows variant, zatímco přebírání stejný název image z hostitele platformy Linux přetáhne varianty Linuxu.

***Možnost B: Vytvoření zcela nové základní image***

Můžete vytvořit vlastní základní image Dockeru od začátku, jak je popsáno v tomto [článku](https://docs.docker.com/engine/userguide/eng-image/baseimages/) od Dockeru. Scénář, který je pravděpodobně není pro vás nejvhodnější, pokud právě začínáte s Dockerem, ale pokud chcete nastavit konkrétní bity základní image, můžete to provést.

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>Krok 3: Vytvoření vlastní Image Dockeru vložení služby

U každé aplikace se skládá z vlastní služby budete muset vytvořit související image. Pokud vaše aplikace skládá z jedné služby nebo webové aplikace, budete potřebovat jenom jedné image.

> [!NOTE]
> Když se vezme v úvahu "workflow pro DevOps vnější smyčky", Image se vytvoří pomocí automatizovaného procesu sestavení pokaždé, když nahrajete váš zdrojový kód do úložiště Git (průběžná integrace), obrázky budou vytvořeny v globálním prostředí z vaší zdrojový kód.

Ale předtím, než jsme zvažte, že přejdete na tuto trasu vnější smyčky, potřebujeme zajistit, že aplikace Dockeru ve skutečnosti funguje správně tak, aby jejich není push kód, který nemusí správně fungovat do systému správy zdrojového kódu (Git atd.).

Každý vývojář proto nejprve musí udělat celý proces vnitřní smyčky, místně ji otestovat a pokračovat ve vývoji, dokud chtějí push kompletní funkce nebo změňte na systém správy zdrojového kódu.

Pro vytvoření image v místním prostředí a pomocí souboru DockerFile, můžete použít příkaz sestavení dockeru, jak je ukázáno v obrázek 4-19 (můžete také spustit docker-compose up – sestavení pro aplikace, které sestává z několika kontejnerů nebo služeb Team Foundation).

![](./media/image25.png)

Obrázek 4 – 19: Spouštění sestavení dockeru

Volitelně můžete místo přímo spouštět docker sestavení ze složky projektu, nejprve můžete vygenerovat nasaditelný složku s knihovnami .NET, třeba pomocí spuštění dotnet příkazu pro publikování a pak spusťte sestavení dockeru.

V tomto příkladu, tím se vytvoří image Dockeru s název cesardl/netcore-webapi mikroslužeb – docker: first (: nejprve je značka, jako jsou konkrétní verzi). Je-li provést tento krok pro každou vlastní image, které je potřeba vytvořit složené aplikace Dockeru s několika kontejnery.

Najdete existujících bitových kopií ve vašem místním úložišti (vývojovém počítači) s využitím dockeru příkaz bitové kopie, jak je znázorněno na obrázku 4-20.

![](./media/image26.png)

Obrázek 4-20: Zobrazení existujících obrázků s využitím Image dockeru

### <a name="step-4-optional-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>Krok 4: (Volitelné) Definování vašich služeb v docker-compose.yml při vytváření složené aplikace Dockeru s více službami

Pomocí souboru docker-compose.yml můžete definovat sadu souvisejících služeb umožňující nasadit ho jako aplikace skládá pomocí příkazů nasazení je vysvětleno v další části kroku.

Je potřeba vytvořit tento soubor do vašeho hlavního nebo kořenové složky řešení; do následujícího souboru docker-compose.yml to měl být podobný obsah:

```yml
version: '2'
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

-   Sestavení z soubor DockerFile v aktuálním adresáři

-   Dál vystavené port 80 v kontejneru na port 81 na hostitelském počítači

-   Připojení adresáře projektu v hostiteli /code v rámci kontejneru, takže budete moct změnit kód bez nutnosti znovu sestavovat image

-   Odkaz webové služby ke službě redis

Použití služby redis [nejnovější veřejné redis image](https://hub.docker.com/_/redis/) získaných z registru Docker Hub. [redis](https://redis.io/) je systém velmi populární mezipaměti pro aplikace na straně serveru.

### <a name="step-5-build-and-run-your-docker-app"></a>Krok 5: Sestavení a spuštění aplikace Dockeru

Pokud vaše aplikace má pouze jeden kontejner, stačí ji spustit nasazení na hostitele Docker (virtuální počítač nebo fyzický server). Nicméně pokud vaše aplikace se skládá z několika služeb, budete muset *tvoří ji*také. Podívejme se na různé možnosti.

***Možnost A: Spustit jedním kontejnerem nebo služby***

Image Dockeru můžete spustit pomocí dockeru, spusťte příkaz, jak je znázorněno zde:

```
docker run -t -d -p 80:5000
cesardl/netcore-webapi-microservice-docker:first
```

Všimněte si, že pro toto konkrétní nasazení jsme budete se přesměruje požadavky odeslané na portu 80 na interní port 5000. Aplikace teď naslouchá na externím portu 80 na úrovni hostitele.

***Možnost B: Vytvářet a spouštět aplikace typu kontejner více***

Ve většině scénářů organizace aplikaci v Dockeru se skládá z více služeb. Pro tyto případy můžete spuštění příkazu docker-compose up (obrázek 4 – 21), které použije soubor docker-compose.yml, kterou může jste vytvořili dříve. Spustí tento příkaz nasadí složené aplikaci se všemi jeho související kontejnerů.

![](./media/image27.png)

Obrázek 4 – 21: Výsledky spuštění příkazu "docker-compose up"

Po spuštění docker-compose up, budete nasazovat aplikace a její související kontejnerů do hostitele Dockeru, jak ukazuje obrázek 4 – 22 reprezentaci virtuálního počítače.

![](./media/image28.png)

Obrázek 4 – 22: Virtuální počítač s kontejnery Dockeru nasazené

Poznámka: docker-compose up a docker, spusťte mohou být dostatečné k testování kontejnerů ve vašem vývojovém prostředí, ale pokud očekáváte pro práci s clustery Dockeru a orchestrátorů, jako je Docker Swarm, Mesosphere DC/OS nebo Kubernetes je nemusí použít na všech aby bylo možné vertikálně navýšit kapacitu. Pokud používáte cluster jako [režim Docker Swarm](https://docs.docker.com/engine/swarm/) (k dispozici v Docker pro Windows a Mac od verze 1.12), musíte nasadit a testovat pomocí dalších příkazů, jako je služba docker vytvořit pro jednu službu nebo pokud jste nasazení aplikace skládá z několika kontejnerů pomocí docker compose svazku a docker nasazení myBundleFile, nasazením složené aplikace jako zásobník, jak je popsáno v článku [distribuované aplikace sady](https://blog.docker.com/2016/06/docker-app-bundle/) od Dockeru.

Pro [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) a [Kubernetes](https://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment) použijete jiné nasazení příkazy a skripty, také.

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>Krok 6: Otestujte aplikaci Docker (místně, v místní virtuální počítač CD)

Tento krok se liší v závislosti na tom, co vaše aplikace stojí.

Ve velmi jednoduché rozhraní .NET Core webového rozhraní API "Hello World" nasadit jako jedním kontejnerem nebo služby by stačí pro přístup ke službě zadáním TCP port zadaný v souboru DockerFile.

Pokud localhost není zapnutý, přejděte k vaší službě zjistit IP adresu počítače pomocí tohoto příkazu:

docker-machine ip *svůj název kontejneru*

Na hostitele Docker spusťte prohlížeč a přejděte na web; vaše aplikace nebo služby spuštěné, měli byste vidět, jak je ukázáno v obrázek 4 – 23.

![](./media/image29.png)

Obrázek 4 – 23: Testování aplikace místně s použitím místního hostitele Docker

Všimněte si, že používá port 80, ale interně byl přesměrován na portu 5000, protože to je, jak nasazení pomocí dockeru spustíte tak, jak je vysvětleno výše.

Můžete ho otestovat pomocí příkazu CURL z terminálu. V instalaci Dockeru na Windows je výchozí IP 10.0.75.1, jak je znázorněno v obrázek 4 – 24.

![](./media/image30.png)

Obrázek 4 – 24: Testování aplikace Docker místně pomocí CURL

**Ladění kontejneru spuštěného v Dockeru**

Visual Studio Code podporuje ladění Dockeru, pokud používáte Node.js a jiných platformách, jako je .NET Core kontejnery.

Můžete také ladit kontejnery .NET Core v Dockeru při používání sady Visual Studio, jak je popsáno v další části.

**Další informace:** Další informace o ladění kontejnerů Dockeru Node.js, přejděte na <https://blog.docker.com/2016/07/live-debugging-docker/> a [ https://blogs.msdn.microsoft.com/\ uživatele\_ed/2016/02/27 nebo Visual-Studio-Code-New-features-13-Big-Debugging-Updates-Rich-Object-hover-Conditional-breakpoints-node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/).

>[!div class="step-by-step"]
>[Předchozí](docker-apps-development-environment.md)
>[další](visual-studio-tools-for-docker.md)