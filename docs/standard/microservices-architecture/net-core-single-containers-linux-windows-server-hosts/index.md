---
title: Nasazení jedním kontejnerem na základě webových aplikací .NET Core v Linuxu nebo Windows hostiteli s Nano serverem
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Nasazení jedním kontejnerem na základě webových aplikací .NET Core v Linuxu nebo Windows hostiteli s Nano serverem
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/27/2018
ms.openlocfilehash: 45be99a86a52ed450b795ca5f91c01ab82c7da47
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44197352"
---
# <a name="deploying-single-container-based-net-core-web-applications-on-linux-or-windows-nano-server-hosts"></a>Nasazování webových aplikací na základě jednoho kontejneru .NET Core v Linuxu nebo Windows hostiteli s Nano serverem

_Kontejnery Dockeru můžete použít pro monolitické nasazení jednodušší webových aplikací. Tím se zlepšuje průběžnou integraci a průběžné nasazování kanálů a pomáhá dosahovat úspěšnosti nasazení do produkčního prostředí. Už to funguje"v počítači, proč to nebude fungovat v produkčním prostředí?"_

Architektura založená na mikroslužbách má spoustu výhod, ale tyto výhody pocházet za cenu zvýšení složitosti. V některých případech se náklady převažují nad přínosy a monolitické nasazení aplikací spouštěných v kontejnerech jedné nebo několika je lepší volbou.

Monolitické aplikace nemusí být snadno decomposable do jasně oddělené mikroslužeb. Když jste se naučili, že tyto mikroslužby by měly být rozdělené podle funkce: by měly fungovat nezávisle na sobě zajistit odolnost aplikace. Pokud nelze doručit řezy funkce aplikace, oddělení pouze zvyšuje složitost.

Aplikace nemusí potřebovat ještě nezávisle škálovat funkce. Předpokládejme, který v počátečních fázích `eShopOnContainers` odkazovat na aplikace, provoz neměli zarovnání, rozdělení funkcí do různých mikroslužeb. Provoz byla dostatečně malá, přidávání prostředků do jedné služby obvykle určena přidávání prostředků do všech služeb. Další práci pro oddělení aplikací do samostatných služeb k dispozici minimální výhodu.

Také již v rané fázi při vývoji aplikace možná nebudete mít jasnou představu kde jsou přirozené hranice funkční. Při vývoji minimální přijatelné produktu, nemusí mít ještě umístila fyzické oddělení.

Některé z těchto podmínek může být dočasné. Může být začněte vytvořením jednotlivou aplikaci a později oddělení několik funkcí, které vyvinul a nasadit jako mikroslužeb. Další podmínky může být nezbytné pro aplikace problém místa, což znamená, že aplikace může být nikdy rozdělená do několika mikroslužeb.

Oddělení aplikace do mnoha samostatné procesy také zavádí režijní náklady. Rozdělení funkcí do různých procesů je složitější. Komunikační protokoly budou složitější. Namísto volání metody je nutné použít asynchronní komunikace mezi službami. Při přesunu na architekturu mikroslužeb, budete muset přidat řadu stavební bloky implementované ve verzi mikroslužeb `eShopOnContainers` aplikace: zpracování událostí Service bus, zprávy odolnost proti chybám a opakovaných pokusů, konečnou konzistenci a další.

Velmi zjednodušené verzi aplikaci eShopOnContainers (s názvem [eShopWeb](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebMonolithic) a je zahrnuté ve stejném úložišti Githubu) spouští jako monolitické aplikace MVC. Jak je popsáno, existují výhody, které nabízí široké možnosti volby návrhu. Můžete zdroj pro tuto aplikaci stáhnout z webu GitHub a spustit ho místně. Tato monolitické aplikace využívá výhod nasazení v prostředí kontejneru.

Za prvé nasazení kontejnerizované znamená, že každá instance aplikace běží ve stejném prostředí. Jedná se o prostředí pro vývojáře, kde vývoj a testování již v rané fázi probíhat. Vývojový tým můžete spustit aplikaci v kontejnerizovaných prostředí, která odpovídá produkčního prostředí.

Navíc kontejnerizovaných aplikací horizontální navýšení kapacity za nižší cenu. Jak jste viděli již dříve kontejnerové prostředí umožňuje větší prostředků sdílení než tradiční prostředí virtuálních počítačů.

Nakonec se uzavření aplikace do kontejneru vynutí oddělení mezi obchodní logiku a storage server. Jak aplikace horizontálně navýší kapacitu, budou různé kontejnery spoléhat na střední jednoho fyzického úložiště. Toto úložiště by obvykle vysokou dostupnost serveru databáze SQL serveru.

## <a name="application-tour"></a>Přehled aplikace

[EShopWeb](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebMonolithic) aplikace představuje některé aplikace aplikaci eShopOnContainers spuštěné jako monolitické aplikace – aplikace založené na technologii ASP.NET Core MVC spouštění v .NET Core. Zejména poskytuje katalogu možnosti procházení, jak je popsáno v předchozí části.

Aplikace používá pro ukládání katalogu do databáze SQL serveru. V kontejnerových nasazení této monolitické aplikace mohly přistupovat k úložišti dat jako aplikací založených na mikroslužbách. Aplikace je nakonfigurovaná pro spuštění systému SQL Server v kontejneru spolu s monolitickými aplikacemi. V produkčním prostředí SQL Server spustí na počítači s vysokou dostupností mimo hostitele Dockeru. Pro usnadnění práce v prostředí vývoj nebo testování se doporučuje systémem SQL Server do vlastního kontejneru.

Počáteční sada pouze funkcí povolí procházení katalogu. Aktualizace by umožňují úplná sada funkcí kontejnerizované aplikace. A další pokročilé architektura pro webové monolitické aplikace je popsána v [postupy architektury webové aplikace ASP.NET](https://aka.ms/webappebook) e kniha a související [eShopOnWeb ukázkovou aplikaci](https://aka.ms/WebAppArchitecture).

## <a name="docker-support"></a>Podpora dockeru

Projekt eShopOnWeb poběží v .NET Core. To znamená, že můžete spustit v kontejnerech založených na Linuxu nebo založené na Windows. Všimněte si, že pro nasazení prostředí Docker, chcete použít stejný typ hostitele pro SQL Server. Kontejnery založené na Linuxu povolit menší nároky na místo a jsou upřednostňované.

Visual Studio poskytuje šablony projektu, který se přidá podpora pro Docker do řešení. Klikněte pravým tlačítkem na projekt, klikněte na tlačítko **přidat** následovaný **podporu Dockeru**. Šablona přidá do projektu a nový soubor Dockerfile **docker-compose** projekt, který poskytuje starter *docker-compose.yml* souboru. Tento krok již byla provedena v projektu eShopOnWeb stáhnou z Githubu. Uvidíte, že obsahuje řešení **eShopOnWeb** projektu a **docker-compose** projektu jak je znázorněno v obrázek 6-1.

![](./media/image1.png)

**Obrázek 6-1**. **Docker-compose** projektu v aplikaci web jeden kontejner

Tyto soubory jsou standardní docker-compose soubory, které jsou konzistentní s žádným projektem Dockeru. Můžete je pomocí sady Visual Studio nebo z příkazového řádku. Tato aplikace běží na .NET Core a používá kontejnery Linuxu. Ano můžete také kódu, sestavení a ho spustit na počítači Mac nebo na počítači s Linuxem.

*Docker-compose.yml* soubor obsahuje informace o co k sestavení Image a jaké kontejnery ke spuštění. Tyto šablony určit způsob sestavení `eshopweb` obrázků a spuštění aplikace kontejnery. Je třeba přidat závislost na SQL serveru zahrnutím bitovou kopii pro něj (například `mssql-server-linux`) a služby pro sql.data bitovou kopii pro sestavení a spuštění kontejneru Dockeru. Tato nastavení jsou uvedeny v následujícím příkladu:

```yml
version: '2'

services:
  eshopweb:
    image: eshop/web
    build:
    context: ./eShopWeb
    dockerfile: Dockerfile
    depends_on:
      - sql.data

  sql.data:
    image: microsoft/mssql-server-linux
```

`depends_on` – Direktiva říká Dockeru, eShopWeb image závisí na imagi sql.data. Níže uvedené řádky `depends_on` jsou pokyny k sestavení image označit `sql.data` pomocí `microsoft/mssql-server-linux` bitové kopie.

**Docker-compose** projektu zobrazí další docker-compose soubory pod hlavním *docker-compose.yml* uzel poskytují vizuální označení, že se vztahují tyto soubory. *Docker compose override.yml* soubor obsahuje nastavení pro obě služby, jako je například připojovací řetězce a další nastavení aplikace.

Následující příklad ukazuje *docker compose.vs.debug.yml* soubor, který obsahuje nastavení používaná pro ladění v sadě Visual Studio. V tomto souboru eshopweb image má značku dev, připojí k němu. Který pomáhá samostatný ladicí verzi Image tak, aby se nenasazují omylem informace o ladění do produkčního prostředí:

```yml
version: '2'

services:
  eshopweb:
    image: eshop/web:dev
    build:
    args:
    source: ${DOCKER_BUILD_SOURCE}
    environment:
      - DOTNET_USE_POLLING_FILE_WATCHER=1
    volumes:
      - ./eShopWeb:/app
      - ~/.nuget/packages:/root/.nuget/packages:ro
      - ~/clrdbg:/clrdbg:ro
    entrypoint: tail -f /dev/null
    labels:
      - "com.microsoft.visualstudio.targetoperatingsystem=linux"
```

Poslední soubor přidán *docker-compose.ci.build.yml*. Tento soubor se použije z příkazového řádku pro sestavení projektu z položek konfigurace serveru. Tento soubor compose spustí kontejner Dockeru, který sestaví Image vaše aplikace potřebuje. Následující příklad ukazuje obsah *docker-compose.ci.build.yml* souboru:

```yml
version: '2'

services:
  ci-build:
    image: microsoft/aspnetcore-build:latest
    volumes:
      - .:/src
    working_dir: /src
  command: /bin/bash -c "dotnet restore ./eShopWeb.sln && dotnet publish  ./eShopWeb.sln -c Release -o ./obj/Docker/publish"
```

> [!NOTE]
> Od verze rozhraní .NET Core SDK 2.0 [dotnet restore](../../../core/tools/dotnet-restore.md) příkaz spustí automaticky při [dotnet publikovat](../../../core/tools/dotnet-publish.md) provádí.

Všimněte si, že na obrázku je v ASP.NET Core, sestavte image. Tento image obsahuje nástroje pro sadu SDK a sestavení k sestavení aplikace a vytvořte požadované Image. Spuštění **docker-compose** projekt pomocí tohoto souboru z této image spustí kontejner sestavení a poté sestaví image vaší aplikace v tomto kontejneru. Můžete určit, že *docker-compose* souboru jako součást příkazového řádku pro sestavení aplikace v kontejneru Dockeru, a spusťte jej.

V sadě Visual Studio, můžete tak, že vyberete spuštění aplikace v kontejnerech Dockeru **docker-compose** projekt jako spouštěný projekt a následným stisknutím klávesy Ctrl + F5 (F5 pro ladění), jako u jakékoli jiné aplikace. Při spuštění **docker-compose** projektu sady Visual Studio spustí **docker-compose** pomocí *docker-compose.yml* souboru  *docker-compose.override.yml* souboru a ten příkazu docker-compose.vs.\* soubory. Po zahájení aplikace Visual Studio spustí prohlížeč pro vás.

Pokud spuštění aplikace v ladicím programu sady Visual Studio připojí k běžící aplikaci v Dockeru.

## <a name="troubleshooting"></a>Poradce při potížích

Tato část popisuje několik problémů, které mohou nastat při spuštění kontejnerů místně a navrhne některé opravy.

### <a name="stop-docker-containers"></a>Zastavit kontejnery Dockeru

Po spuštění kontejnerizované aplikace i nadále spouštět, i po zastavení ladění kontejnerů. Můžete spustit `docker ps` příkazu z příkazového řádku zobrazíte, které kontejnery běží. `docker stop` Příkaz zastaví spuštěný kontejner, jak je znázorněno v obrázek 6-2.

![](./media/image2.png)

**Obrázek 6 – 2**. Výpis a zastavuje kontejnery docker a docker ps zastavit příkazy rozhraní příkazového řádku

Můžete potřebovat ukončené procesy při přepínání mezi různé konfigurace. V opačném případě kontejneru, na kterém běží webová aplikace používá port, který pro vaši aplikaci (5106 v tomto příkladu).

### <a name="add-docker-to-your-projects"></a>Přidat do vašich projektů Dockeru

Průvodce, který přidává podporu Dockeru komunikuje se spuštěným procesem Dockeru. Pokud Docker není spuštěná, když spustíte průvodce, průvodce nespustí správně. Průvodce zkontroluje zvoleného aktuálního kontejneru pro přidání správné podpory Dockeru. Přidání podpory pro kontejnery Windows, spusťte Průvodce mají Dockeru s kontejnery Windows nakonfigurovaný. Přidání podpory pro Linuxové kontejnery, spusťte Průvodce mají Dockeru s kontejnery Linuxu, které jsou nakonfigurované.

>[!div class="step-by-step"]
[Předchozí](../docker-application-development-process/docker-app-development-workflow.md)
[další](../containerize-net-framework-applications/index.md)
