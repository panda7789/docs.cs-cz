---
title: "Pracovní postup vývoje vnitřní smyčky pro Docker aplikace"
description: "Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3605a6cd53db695de3af015a777e3c1a0e92af58
ms.sourcegitcommit: 672c9cd122c13c9813f57f022c86ebdf6dd69b4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2018
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Pracovní postup vývoje vnitřní smyčky pro Docker aplikace

Před spuštěním pracovního postupu vnější smyčky pokrývání uzlů celý DevOps cyklus, vše začíná na každý vývojář počítače, kódování aplikace, pomocí jejich upřednostňované jazyky nebo platformy a místní testování (obrázek 4-14). Ale v každém případě je nutné bod velmi důležité společné, bez ohledu na to, jaké jazyk, framework nebo platformy zvolíte. V tomto pracovním postupu konkrétní jsou vždy vývoj a testování Docker kontejnery, ale místně.

![](./media/image18.png)

Obrázek 4 – 14: vnitřní smyčky vývoj kontextu

Kontejner nebo instance Docker Image bude obsahovat tyto komponenty:

-   Výběru operačního systému (například distribuční Linux nebo Windows)

-   Soubory přidal developer (například binární soubory aplikace)

-   Konfigurace (například nastavení prostředí a závislosti)

-   Pokyny pro jaké procesy spuštění pomocí Docker

Můžete nastavit vnitřní smyčky vývoj pracovního postupu, který využívá Docker jako proces (popsané v další části). Vezměte v úvahu, že počáteční kroky pro nastavení prostředí není zahrnutý, protože je potřeba udělat jenom jednou.

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>Vytvoření jednoduché aplikace v rámci kontejner Docker pomocí Visual Studio Code a příkazového řádku Dockeru

Aplikace se skládá z vlastní služby a další knihovny (závislosti).

Obrázek 4 – 15 ukazuje základní kroky, které je obvykle potřeba provádět při sestavování aplikaci pomocí Docker, za nímž následuje podrobný popis jednotlivých kroků.

![](./media/image19.png)

Obrázek 4 – 15: základní pracovní postup pro životní cyklus Docker kontejnerizované aplikace pomocí příkazového řádku Dockeru

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>Krok 1: Začínáme kódovat v kódu Visual Studio a vytvořte standardní hodnoty počáteční aplikace/služby

Způsob, jak vyvíjet aplikaci je poměrně podobným způsobem, které můžete provést bez Docker. Rozdíl je, že při vývoji, jsou nasazení a testování aplikací nebo služeb spuštěných v rámci Docker kontejnery umístěny ve vašem místním prostředí (třeba virtuální počítač s Linuxem nebo Windows).

**Nastavení místního prostředí**

Nejnovější verze Docker pro Mac a Windows je jednodušší než kdy k vývoji aplikací Docker a instalace je jednoduchá.

**Další informace o** pokyny k nastavení Docker pro systém Windows, přejděte na [https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/).

Pokyny k nastavení Docker pro Mac, přejděte na <https://docs.docker.com/docker-for-mac/>.

Kromě toho budete potřebovat editor kódu, takže ve skutečnosti můžete vyvíjet aplikace pomocí příkazového řádku Dockeru.

Společnost Microsoft poskytuje Visual Studio Code, což je editor lehký kód, který je podporován v Mac, Windows a Linux a poskytuje technologii IntelliSense, s [podporu mnoha jazyků](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, přejděte, Java, Ruby, Pythonu a většina moderních jazyků), [ladění](https://code.visualstudio.com/Docs/editor/debugging), [integrace s Gitem](https://code.visualstudio.com/Docs/editor/versioncontrol) a [rozšíření podpory](https://code.visualstudio.com/docs/extensions/overview). Tohoto editoru je skvělým přizpůsobit pro vývojáře, Mac a Linux. V systému Windows také můžete použít celou aplikaci Visual Studio.

**Další informace o** pokyny k instalaci Visual Studio pro Windows, Mac nebo Linux, přejděte na [http://code.visualstudio.com/docs/setup/setup-overview/https://docs.docker.com/docker-for-mac/](http://code.visualstudio.com/docs/setup/setup-overview/https:/docs.docker.com/docker-for-mac/).

Můžete pracovat s příkazového řádku Dockeru a zadejte kód, pomocí libovolného editoru kódu, ale pokud používáte Visual Studio Code, umožňuje se snadno vytvořit soubor Docker a docker-compose.yml soubory v pracovním prostoru. Plus můžete spustit v prostředí IDE, který zobrazí výzvu skripty, které můžou být spuštění propracována operace pomocí příkazového řádku Dockeru pod Visual Studio Code úlohy.

Visual Studio Code zajišťuje rozšíření, které budete muset nainstalovat. Uděláte to tak, stiskněte Ctrl + Shift + P, zadejte **ext nainstalovat**, a poté spusťte rozšíření: příkazu pro instalaci rozšíření se zprovoznit seznam rozšíření Marketplace. Potom zadejte **docker** filtrovat výsledky a potom vyberte soubor Docker a Docker Compose soubor (yml) podporu rozšíření, jak je to znázorněno na obrázku 4-16.

![](./media/image20.png)

Obrázek 4-16: Instalace rozšíření Docker v sadě Visual Studio kódu

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>Krok 2: Vytvořte soubor Docker související s stávající image (prostý operačního systému nebo dev prostředí jako .NET Core, Node.js a Ruby)

Budete potřebovat soubor Docker jednotlivých vlastní image má být sestaven a kontejner pro nasazení, proto, pokud vaše aplikace se skládá z jedné vlastní služba, budete potřebovat jeden soubor Docker. Ale pokud vaše aplikace se skládá z několika služeb (jako architektura mikroslužeb), budete potřebovat jeden soubor Docker pro službu.

Soubor Docker je obvykle umístit do kořenové složky vaší aplikace nebo služby a obsahuje požadované příkazy, aby věděl, že Docker může nastavit a spuštění této aplikace nebo služby. Můžete vytvořit váš soubor Docker a přidejte do projektu spolu se váš kód (node.js, .NET Core, atd.), nebo, pokud začínáte do prostředí, podívejte se na následující špičky.

> [!TIP]
> Můžete použít nástroj příkazového řádku názvem [yo docker](https://github.com/Microsoft/generator-docker), který scaffold soubory z projektu v jazyce, vyberte a přidá požadované Docker konfigurační soubory. V podstatě, pomáhá vývojářům Začínáme, vytvoří odpovídající soubor Docker, docker-compose.yml a další související skripty sestavení a spuštění Docker kontejnerů. Tento generátor yeoman zobrazí výzvu pomocí pár otázek, s dotazem, váš hostitel vývoj pro vybraný jazyk a cílový kontejner.

![Yo docker](./media/image21.png)

Například obrázek 4-17 ukazuje dva snímky obrazovky z terminály v systému Windows a na spuštěném na počítači Mac., v obou případech je docker, což způsobí vygenerování ukázkový kód projektů (aktuálně .NET Core, Golang a Node.js jako podporované jazyky) již byla konfigurována pro práci začátek Docker.

![](./media/image22.PNG)  ![](./media/image23.png)

Obrázek 4 – 17: yo docker příkaz nástroj v systému Windows (vlevo) a na Macu

Obrázek 4 až 18 představuje příklad pomocí yo docker po existujícího projektu .NET Core zavedené se vygeneroval.

![](./media/image24.PNG)

Obrázek 4 – 18: yo docker s existující .NET Core projektu na místě

Z soubor Docker zadejte co základní Docker image, které budete používat (např. pomocí "od microsoft/dotnet:1.0.0-core"). Obvykle bude vytvářet vlastní bitovou kopii na základní bitovou kopii, kterou můžete získat z jakékoli oficiální úložiště na [úložiště Docker Hub registru](https://hub.docker.com/) (jako je [bitovou kopii pro .NET Core](https://hub.docker.com/r/microsoft/dotnet/) nebo jednu [pro Node.js](https://hub.docker.com/_/node/)).

***Možnost A: použití existující bitovou kopii oficiální Docker***

Použití zásobníku jazyk oficiální úložiště s číslem verze zajistí k dispozici na všech počítačích (včetně vývoj, testování a produkci) stejné funkce jazyka.

Toto je ukázkový soubor Docker pro .NET Core kontejner:

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

V takovém případě používá verzi 1.0.1 bitovou kopii oficiální Docker jádro ASP.NET pro Linux s názvem microsoft/aspnetcore:1.0.1. Další podrobnosti naleznete [stránky ASP.NET Core Docker Image](https://hub.docker.com/r/microsoft/aspnetcore/) a [.NET Core Docker bitové](https://hub.docker.com/r/microsoft/dotnet/). Můžete také může používat jiné porovnatelný z hlediska image jako uzel: 4-onbuild pro Node.js nebo mnoha jiných předkonfigurované obrázků pro programovacích jazyků, které jsou k dispozici v [úložiště Docker Hub](https://hub.docker.com/explore/).

V soubor Docker musíte také vyzvat Docker pro naslouchání na portu TCP, který budete používat v době běhu (například port 80).

Existují další řádky konfigurace, které můžete přidat na soubor Docker v závislosti na jazyk nebo rozhraní, které používáte, takže Docker umí spuštění aplikace. Například musíte ENTRYPOINT řádek s \["dotnet", "MyCustomMicroservice.dll"\] ke spuštění aplikace .NET Core, i když můžete mít více variant v závislosti na přístup k sestavení a spuštění služby. Pokud používáte sadu SDK, dotnet rozhraní příkazového řádku k vytvoření a spuštění aplikace .NET, je mírně lišit. Dolní řádek je, že ENTRYPOINT řádku plus další řádky se budou lišit v závislosti na jazyk nebo platformy, které zvolíte pro vaši aplikaci.

**Další informace o** informace o vytváření imagí Dockeru pro aplikace .NET Core, přejděte na <https://docs.microsoft.com/dotnet/articles/core/docker/building-net-docker-images>.

Další informace o vytváření vlastních bitových kopií, přejděte na [https://docs.docker.com/engine/ \kurzy/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/).

**Úložiště s více platformami bitové kopie**

Jako kontejnery Windows začnou více běžně se vyskytujícím, jednoho úložiště může obsahovat variant platformu, například image, Linux a Windows. Toto je nová funkce brzo Docker, která umožňuje dodavatelům použít jednom úložišti pro více platforem, jako například [microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) úložiště, které je k dispozici v registru DockerHub. Jako funkci dodává zachování připojení, stahování této bitové kopie z hostitele Windows načte Windows variant, zatímco stahování stejný název bitové kopie z hostitele platformy Linux načte Linux variant.

***Možnost B: vytvořit základní bitové kopie od začátku***

Můžete vytvořit vlastní základní image Docker od začátku, jak je popsáno v tomto [článku](https://docs.docker.com/engine/userguide/eng-image/baseimages/) z Docker. Toto je scénáře, který je pravděpodobně není pro vás nejvhodnější, pokud právě začínáte s Docker, ale pokud chcete nastavit konkrétní bity základní bitové kopie, můžete to provést.

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>Krok 3: Vytvoření vlastních imagí Dockeru vložení služby v ní

Pro každý vlastní službu, která se skládá z vaší aplikace budete muset vytvořit související image. Pokud vaše aplikace se skládá z jedné služby nebo webové aplikace, budete potřebovat pouze jeden obrázek.

> [!NOTE]
> Když se vezme v úvahu "DevOps workflow Vnější smyčka", bitové kopie bude vytvořena procesem automatizované sestavení vždy, když push zdrojový kód do úložiště Git (průběžnou integraci), bitové kopie budou vytvořeny v globální prostředí z vaší zdrojový kód.

Ale předtím, než jsme zvažte má pro danou trasu vnější smyčky, potřebujeme zajistit, že aplikace Docker skutečně funguje správně, aby se nemáte push kód, který nemusí fungovat správně do správy zdrojového kódu (Git, atd.).

Proto každý vývojář nejdřív je potřeba udělat celý proces vnitřní smyčky pro testování místně a pokračovat ve vývoji, dokud chtějí push dokončení funkce nebo změňte správy zdrojového kódu.

K vytvoření image ve vašem místním prostředí a pomocí soubor Docker, můžete příkaz sestavení docker, jak je předvedeno v obrázek 4-19 (také můžete spustit docker compose nahoru – sestavení pro aplikace, které sestává z několika kontejnerů nebo služeb).

![](./media/image25.png)

Obrázek 4 – 19: spuštění docker sestavení

Volitelně můžete místo přímo spouštět docker sestavení ze složky projektu, nejprve můžete vygenerovat nasadit složku s knihovnami .NET potřeby pomocí spuštění dotnet publikování příkaz, a poté spusťte docker sestavení.

V tomto příkladu to vytvoří bitovou kopii Docker se název cesardl/netcore-webapi mikroslužbu-docker: první (: nejdřív se značky, například na konkrétní verzi). Tento krok pro každý vlastní image, které potřebujete k vytvoření aplikace skládá Docker s několika kontejnerů může trvat.

Image můžete najít existující do místního úložiště (vývojovém počítači) pomocí docker příkaz bitové kopie, jak ukazuje obrázek 4-20.

![](./media/image26.png)

Obrázek 4-20: zobrazení existujících bitových kopií pomocí docker obrázků

### <a name="step-4-optional-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>Krok 4: Definování (volitelné) vašim službám v docker-compose.yml při sestavování složený aplikace Docker s více službami

Pomocí soubor docker-compose.yml můžete definovat sadu související služby pro nasazení jako složený aplikace pomocí příkazů nasazení popsané v další části kroku.

Je potřeba vytvořit tento soubor do vaší hlavní nebo kořenové složky řešení; Podobně jako obsah musí mít pro následující soubor docker-compose.yml:

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

V tomto konkrétním případě tento soubor definuje dvě služby: webové služby (služby vlastní) a službu redis (služba oblíbených mezipaměti). Každá služba budou nasazeny jako kontejner, takže je potřeba použít konkrétní Docker bitovou kopii pro každý. Pro tuto konkrétní webovou službu bude nutné bitovou kopii postupujte takto:

-   Sestavení z soubor Docker v aktuálním adresáři

-   Předávání zveřejněné port 80 kontejneru na port 81 na hostitelském počítači

-   Připojení adresáře projektu na hostiteli, aby /code v rámci kontejneru, která umožňuje upravit kód bez nutnosti znovu vytvořit bitovou kopii

-   Webová služba propojit službu redis

Používá službu redis [nejnovější bitové kopie veřejného redis](https://hub.docker.com/_/redis/) načtený z registru úložiště Docker Hub. [redis](http://redis.io/) je systém velmi oblíbených mezipaměti pro serverové aplikace.

### <a name="step-5-build-and-run-your-docker-app"></a>Krok 5: Vytvoření a spuštění aplikace Docker

Pokud vaše aplikace obsahuje pouze jediný kontejner, stačí spustit publikovat na vašem hostiteli Docker (virtuálního počítače nebo fyzického serveru). Ale pokud vaše aplikace se skládá z několika služeb, budete muset *tvoří ho*, příliš. Podíváme se na různé možnosti.

***Možnost A: jediný kontejner nebo služby***

Bitovou kopii Docker můžete spustit pomocí docker, spusťte příkaz, jak je vidět tady:

```
docker run -t -d -p 80:5000
cesardl/netcore-webapi-microservice-docker:first
```

Všimněte si, že pro toto konkrétní nasazení, jsme budete přesměrovávat žádosti poslané na port 80 k interní port 5000. Aplikace je nyní naslouchá na externím portu 80 na úrovni hostitele.

***Možnost B: vytvářené a spusťte aplikaci více kontejneru***

Ve většině scénářů organizace Docker aplikace se skládá z několika služeb. Pro tyto případy, můžete spustit příkaz docker compose nahoru (obrázek 4 – 21), který bude použit soubor docker-compose.yml, kterou může jste vytvořili dříve. Spuštění tohoto příkazu nasadí složený aplikaci se všemi jeho související kontejnerů.

![](./media/image27.png)

Obrázek 4 – 21: výsledky spuštěním příkazu "docker-compose nahoru"

Po spuštění docker-vytvořit zálohu, nasazení aplikace a její související kontejnery do Docker hostiteli, jak ukazuje obrázek 4 – 22 reprezentace virtuálních počítačů.

![](./media/image28.png)

Obrázek 4 – 22: virtuálních počítačů s kontejnery Docker nasazení

Poznámka: docker tvoří nahoru a docker spustit mohou být dostatečné pro testování kontejnerů ve vašem vývojovém prostředí, ale pokud očekáváte pro práci s clustery Docker a orchestrators jako Docker Swarm, Mesosphere DC/OS nebo Kubernetes je nemusí použít na všech aby bylo možné škálovat. Pokud používáte cluster jako [Docker Swarm režimu](https://docs.docker.com/engine/swarm/) (k dispozici v Docker pro systém Windows a Mac od verze 1.12), musíte nasadit a otestovat s další příkazy, jako je služba docker vytvořit pro jednu službu nebo pokud jste nasazení aplikace skládá z několika kontejnerů pomocí docker compose sady a docker nasazení myBundleFile, nasazením aplikace komponovaná jako zásobník, jak je popsáno v článku [distribuované aplikace sady](https://blog.docker.com/2016/06/docker-app-bundle/) z Docker.

Pro [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) a [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment) použijete jiné nasazení příkazy a skripty, také.

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>Krok 6: Testování vaší aplikace Docker (místně, v místní virtuální počítač CD)

Tento krok se bude lišit v závislosti na tom, co je to vaše aplikace.

Ve velmi jednoduché rozhraní .NET Core webového rozhraní API "Hello, World" nasazené jako jediný kontejner nebo služby by stačí pro přístup ke službě tím, že poskytuje TCP port zadaný v soubor Docker.

Pokud localhost není zapnutá, přejděte na službě, najít IP adresu pro počítač pomocí tohoto příkazu:

počítač docker ip *si název kontejneru*

Na hostiteli Docker otevřete prohlížeč a přejděte do této lokality; měli byste vidět vaší aplikace nebo služba spuštěna, jak je předvedeno v obrázek 4 – 23.

![](./media/image29.png)

Obrázek 4 – 23: testování Docker aplikace místně pomocí místního hostitele

Všimněte si, že používá port 80, ale interně byl přesměrován na port 5000, protože se jedná o tom, jak byl zaveden pomocí docker spustit, jak je popsáno výše.

Toto můžete otestovat pomocí CURL z terminálu. V rámci Docker instalace v systému Windows je výchozí IP 10.0.75.1, jak je znázorněno v obrázek 4 – 24.

![](./media/image30.png)

Obrázek 4 – 24: testování aplikace Docker místně pomocí CURL

**Ladění kontejner Docker systémem**

Visual Studio Code podporuje ladění Docker, pokud používáte Node.js a jiných platformách, jako kontejnery .NET Core.

Také můžete ladit .NET Core kontejnery v Docker když pomocí sady Visual Studio, jak je popsáno v následující části.

**Další informace:** Další informace o ladění kontejnerů Node.js Docker, přejděte na <https://blog.docker.com/2016/07/live-debugging-docker/> a [https://blogs.msdn.microsoft.com/ \ Uživatel\_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/).


>[!div class="step-by-step"]
[Previous] (docker-apps-development-environment.md) [Next] (visual-studio-tools-for-docker.md)
