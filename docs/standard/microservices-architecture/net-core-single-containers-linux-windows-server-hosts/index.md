---
title: Nasazení jednoho kontejneru na základě webových aplikací .NET Core na hostitelích Nano Server systému Windows nebo Linux
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Nasazení jednoho kontejneru na základě webových aplikací .NET Core na hostitelích Nano Server systému Windows nebo Linux
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: f429bc0c6e76c2be2e4f491768a15ab36ecb0d34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591091"
---
# <a name="deploying-single-container-based-net-core-web-applications-on-linux-or-windows-nano-server-hosts"></a>Nasazení webových aplikací na základě jednoho kontejneru .NET Core na hostitelích Nano Server systému Windows nebo Linux

*Kontejnery Docker můžete použít pro nasazení monolitický jednodušší webových aplikací. Tím se zlepšuje průběžnou integraci a průběžné nasazování kanálů a pomáhá dosáhnout úspěšné nasazení produkční. Žádné další "funguje v počítači, proč nefunguje v produkčním prostředí?"*

Architektura se na základě mikroslužeb má mnoho výhod, ale tyto výhody pocházet s náklady zvýšenou složitostí. V některých případech náklady převažují nad přínosy a můžete se s aplikací monolitický nasazení spuštěn v jednom kontejneru nebo v několika kontejnerů lépe vyhovovat. 

Monolitický aplikace nemusí být snadno decomposable do dobře oddělených mikroslužeb. Jste se naučili tyto by měl být oddíly podle funkce: mikroslužeb by měla fungovat nezávisle na sobě zajistit pružnější aplikace. Pokud nelze doručit řezy funkce aplikace, oddělení ho přidá jenom složitost.

Aplikace nemusí ještě nezávisle škálovat funkce. Předpokládejme, že již v rané fázi v dobu životnosti naší eShopOnContainers odkaz na aplikaci, provoz není justify funkce rozdělit do různých mikroslužeb. Provoz se dostatečně malé, obvykle přidávání zdrojů do jedné služby určené přidávání zdrojů ke všem službám. Další kroky k oddělení aplikaci do samostatné služby k dispozici minimální výhody.

Časná ve vývoji aplikace nemusí být také jasno kde přirozené funkční hranice jsou. Když budete vyvíjet minimální přijatelná produktu, fyzické oddělení nemusí ještě této služby.

Některé z těchto podmínek může být dočasné. Můžete začít tak, že vytvoříte monolitický aplikace a později oddělit některé funkce vyvinuté a nasadit jako mikroslužeb. Další podmínky může být nezbytné pro aplikace problém místa, což znamená, že aplikace může být nikdy rozdělen do více mikroslužeb.

Oddělení aplikace do mnoha diskrétní procesů také zavádí režijní náklady. Rozdělit funkce do různých procesů je složitější. S růstem složitosti komunikační protokoly. Místo volání metod je nutné použít asynchronní komunikaci mezi službami. Když přesouváte mikroslužeb architektury, budete muset přidat řadu stavební bloky implementované v mikroslužeb verze aplikace eShopOnContainers: sběrnice zpracování událostí, zprávy odolnost proti chybám a opakovaných pokusů, konzistence typu případné a další.

Velmi zjednodušené verzi eShopOnContainers (s názvem [eShopWeb](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebMonolithic) a zahrnuté ve stejném úložišti GitHub) spustí jako monolitický aplikace MVC a jako právě popsáno, existují výhod nabízených volbou tohoto návrhu. Můžete stáhnout z webu GitHub zdroj pro tuto aplikaci a ji spustit místně. Výhody této monolitický aplikace z nasazuje v prostředí kontejneru.

Pro jeden kontejnerizované nasazení znamená, že každá instance aplikace běží ve stejném prostředí. To zahrnuje vývojářského prostředí, kde již v rané fázi testování a vývoje probíhat. Vývojový tým aplikaci můžete spustit v prostředí s kontejnerizované, které odpovídá produkčního prostředí.

Kromě toho kontejnerizované aplikace škálování při nižších nákladech. Jak už jste viděli dříve, kontejner prostředí umožňuje sdílení než tradiční prostředí virtuálního počítače větší prostředků.

Nakonec containerizing aplikace vynutí oddělení mezi obchodní logiky a storage server. Jak aplikace horizontálně navýší kapacitu, bude několika kontejnerů spoléhají na střední jedno fyzické úložiště. Obvykle to může být vysoká dostupnost serveru se systémem databázi systému SQL Server.

## <a name="application-tour"></a>Prohlídka aplikace

[EShopWeb](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebMonolithic) aplikace představuje část aplikace eShopOnContainers běžící jako monolitický aplikace – aplikace ASP.NET MVC jádra na základě běžící na .NET Core. Poskytuje především katalogu procházení možností, které jsme popsané v předchozích částech.

Aplikace používá databázi systému SQL Server pro úložiště katalogu. V nasazení založené na kontejner můžete tato monolitický aplikace přístup k úložišti dat stejné jako aplikace založené na mikroslužeb. Aplikace je nakonfigurovaná pro spuštění systému SQL Server v kontejneru spolu s monolitický aplikace. V produkčním prostředí by systému SQL Server spustit na počítači vysokou dostupnost, mimo Docker hostitele. Pro usnadnění práce v dev nebo testovací prostředí doporučujeme systémem SQL Server v jeho vlastní kontejneru.

Funkci počáteční nastavení pouze povolí procházení katalogu. Aktualizace by povolit úplnou sadu funkcí kontejnerové aplikace. Pokročilejší architektura monolitický webové aplikace A je popsána v [webové aplikace ASP.NET architektura postupy](https://aka.ms/webappebook) elektronickou knihu a související [eShopOnWeb ukázkovou aplikaci](http://aka.ms/WebAppArchitecture), i když v takovém případě není spuštěna na Docker kontejnery, protože tento scénář se zaměřuje na vývoj prostý webové s ASP.NET Core.

Zjednodušené verzi k dispozici v eShopOnContainers (eShopWeb) ale běží v kontejner Docker.

## <a name="docker-support"></a>Podpora docker

Spustí eShopOnWeb projektu na .NET Core. Proto můžete spustit v kontejnerech systémem Linux nebo systému Windows. Všimněte si, že pro nasazení Docker chcete použít stejný typ hostitele pro SQL Server. Systémem Linux kontejnery umožňují menší nároky a mají přednost.

Visual Studio poskytuje šablony projektu, který přidává podporu pro Docker řešení. Klikněte pravým tlačítkem na projekt, klikněte na tlačítko **přidat** následuje **Docker podporu**. Šablona přidá do projektu a nový soubor Docker **docker compose** projekt, který poskytuje počáteční soubor docker-compose.yml. Tento krok již byla provedena v projektu eShopOnWeb stáhnout z webu GitHub. Zobrazí se, že obsahuje řešení **eShopOnWeb** projektu a **docker compose** projektu jak je znázorněno v obrázek 6-1.

![](./media/image1.png)

**Obrázek 6-1**. **Docker compose** projekt v kontejneru jedné webové aplikace

Tyto soubory jsou standardní docker-soubory, které jsou konzistentní s žádným projektem Docker compose. Můžete je používat pomocí sady Visual Studio nebo z příkazového řádku. Tato aplikace běží na .NET Core a používá Linux kontejnery, takže můžete také code, sestavit a spustit na Macu nebo na počítač s Linuxem.

Soubor docker-compose.yml obsahuje informace o co bitové kopie k sestavení a jaké kontejnerů ke spuštění. Šablony zadejte, jak vytvořit bitovou kopii eshopweb a spusťte kontejnery aplikace. Je nutné přidat závislost na serveru SQL Server tak, že začleníte bitovou kopii pro něj (například mssql. server linux) a služby pro bitovou kopii sql.data pro Docker sestavení a spuštění tohoto kontejneru. Tato nastavení jsou zobrazena v následujícím příkladu:

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

Závisí\_na direktiva uvádějí Docker že bitovou kopii eShopWeb závisí na bitovou kopii sql.data. Řádky níže, které jsou pokyny k vytvoření image označené sql.data pomocí bitové kopie microsoft/mssql-server-linux.

**Docker compose** projektu zobrazí další soubory docker-compose pod uzlem hlavní docker-compose.yml zajistit vizuální označení, že tyto soubory souvisí. Soubor docker compose override.yml obsahuje nastavení pro obě služby, jako je například připojovací řetězce a další nastavení aplikace.

Následující příklad ukazuje soubor docker-compose.vs.debug.yml, který obsahuje nastavení používaná pro ladění v sadě Visual Studio. V tomto souboru má obrázek eshopweb značce vývojářů, přidá se k němu. Který pomáhá samostatné ladění z bitové kopie verze tak, aby nenasazujte omylem informace o ladění do provozního prostředí:

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

Přidat posledního souboru je docker compose.ci.build.yml. Tím se použije z příkazového řádku pro sestavení projektu ze serveru položek konfigurace. Tento soubor vytvářené spustí kontejner Docker, který vytvoří bitové kopie pro vaši aplikaci. Následující příklad ukazuje obsah souboru docker compose.ci.build.yml.

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

**Poznámka:**: od verze rozhraní .NET 2.0 jádra, dotnet obnovení příkaz provede automaticky při publikování dotnet se spustí.

Všimněte si, že obrázek je obrázek, který ASP.NET Core sestavení. Této bitové kopie zahrnuje sady SDK a sestavení nástroje pro sestavení aplikace a vytvořte požadované obrázky. Spuštění **docker compose** projekt pomocí tento soubor spustí kontejneru sestavení z bitové kopie, pak sestavení vaší aplikace bitové kopie v tomto kontejneru. Zadejte tento docker-jako součást příkazového řádku k vytvoření aplikace v kontejner Docker compose souboru a potom ho spusťte.

V sadě Visual Studio, můžete spustit svoji aplikaci v Docker kontejnery výběrem **docker-tvoří** projekt jako spouštěný projekt a stisknutím klávesy Ctrl + F5 (F5 k ladění), jako u jakékoli jiné aplikace. Při prvním spuštění **docker compose** projektu sady Visual Studio spustí **docker compose** pomocí soubor docker-compose.yml, soubor docker-compose.override.yml a jeden z docker-compose.vs.\* soubory. Po spuštění aplikace Visual Studio spustí prohlížeč za vás.

Pokud je spuštění aplikace v ladicím programu, připojí se k běžící aplikaci v Docker Visual Studio.

## <a name="troubleshooting"></a>Poradce při potížích

Tato část popisuje několik problémů, které by mohly nastat při spuštění kontejnery místně a navrhne některé opravy.

### <a name="stopping-docker-containers"></a>Zastavení Docker kontejnery 

Po spuštění aplikace kontejnerizované kontejnery nadále spouštět, i když je nutné zastavit ladění. Spuštěním docker ps příkazu z příkazového řádku kontejnery, které jsou spuštěny. Příkaz k ukončení docker zastaví kontejner spuštěné, jak je znázorněno na obrázku 6-2.

![](./media/image2.png)

**Obrázek 6-2**. Výpis a zastavení kontejnerů pomocí docker ps a docker zastavit rozhraní příkazového řádku

Možná budete muset zastavit spuštěné procesy při přepínání mezi různými konfiguracemi. V opačném kontejner, ve kterém běží webová aplikace používá port pro vaši aplikaci (5106 v tomto příkladu).

### <a name="adding-docker-to-your-projects"></a>Přidání Docker do vašich projektů

Průvodce, který přidává podporu Docker komunikuje s běžící proces Docker. Průvodce nebude pracovat správně, pokud Docker není spuštěn, když spustíte průvodce. Kromě toho Průvodce prověří zvoleného aktuální kontejner přidání správné Docker podpory. Pokud chcete přidat podporu pro Windows kontejnery, budete muset spustit průvodce, dokud máte Docker s kontejnery Windows nakonfigurovat. Pokud chcete přidat podporu pro kontejnery Linux, spusťte Průvodce při Docker s kontejnery Linux nakonfigurované.

>[!div class="step-by-step"]
[Předchozí] (.. / docker-application-development-process/docker-app-development-workflow.md) [Další] (.. /containerize-NET-Framework-Applications/index.MD)
