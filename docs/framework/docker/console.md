---
title: "Spouštění aplikací konzoly v Docker"
description: "Zjistěte, jak využít stávající aplikace konzoly .NET Framework a spustíte ho v kontejner Windows Docker."
author: spboyer
keywords: ".NET – aplikace typu kontejner, konzoly,"
ms.date: 09/28/2016
ms.topic: article
ms.prod: .net-framework
ms.technology: vs-ide-deployment
ms.devlang: dotnet
ms.assetid: 85cca1d5-c9a4-4eb2-93e6-4f878de07fd7
ms.openlocfilehash: 037d94452dd62c06fe6d8ac7aea1143f52b96d32
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="running-console-applications-in-windows-containers"></a>Konzolové aplikace spuštěna v kontejnerech Windows

Konzolové aplikace se používají pro mnoho účely; z jednoduchý dotaz na stav pro dlouhotrvající obrázek dokumentu zpracování úlohy. Možnost spuštění a škálování tyto aplikace se v žádném případě splnění s omezeními akvizicích hardwaru, časy spuštění nebo spuštěním několika instancí.

Přesunutí aplikace konzoly používat Docker a Windows Server kontejnery umožňuje od těchto aplikací do čistého stavu tím jim umožníte provádět operace a pak vypnutí ještě jednou. Toto téma se zobrazí na základě kontejneru kroky potřebné k přesunutí konzolové aplikace pro Windows a spusťte ji pomocí skriptu prostředí PowerShell.

Ukázkovou aplikaci konzoly je jednoduchý příklad, která přebírá argument, dotaz v tomto případě a vrací náhodné odpovědí. To může trvat `customer_id` a zpracovat jejich daně, nebo vytvořte miniaturu `image_url` argument.

Kromě odpověď `Environment.MachineName` byla přidána do odpovědi na tento rozdíl mezi systémem aplikace místně a v kontejneru systému Windows. Při spuštění aplikace místně, má být vrácen název místního počítače a při spuštění v systému Windows kontejneru; je vrácen kontejner id relace.

[Kompletní příklad](https://github.com/dotnet/docs/tree/master/samples/framework/docker/ConsoleRandomAnswerGenerator) je k dispozici v úložišti dotnet/docs na Githubu. Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Musíte se seznámit s některé Docker podmínky před zahájením práce na přesunutí aplikace do kontejneru.

> A *Docker image* je jen pro čtení šablonu, která definuje prostředí pro spuštěné kontejneru, včetně operační systém (OS), součástí systému a aplikacím.

Důležitou součást imagí Dockeru je, že bitové kopie se skládají ze základní bitové kopie. Každé nové bitové kopie malých sadu funkcí, přidá do stávající image. 

> A *kontejner Docker* je spuštěné instance bitové kopie. 

Aplikace je škálovat tak, že spustíte stejnou bitovou kopii do mnoho kontejnerů.
Toto je koncepčně, podobná stejná aplikace spuštěna v několika hostitelích.

Další informace o architektuře Docker načtením [Docker přehled](https://docs.docker.com/engine/understanding-docker/) na webu Docker. 

Přesunutí aplikace konzoly se několik kroků.

1. [Sestavení aplikace](#building-the-application)
1. [Vytváření soubor Docker bitové kopie](#creating-the-dockerfile)
1. [Proces sestavení a spuštění kontejner Docker](#creating-the-image)

## <a name="prerequisites"></a>Požadavky
Kontejnery Windows jsou podporovány v [Windows 10 Anniversary Update](https://www.microsoft.com/en-us/software-download/windows10/) nebo [systému Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server).

> [!NOTE]
>Pokud používáte systém Windows Server 2016, je nutné kontejnery ručně povolit, protože instalační program Docker pro systém Windows nebude povolení této funkce. Zkontrolujte, že všechny aktualizace spustili pro operační systém a potom postupujte podle pokynů v tématu [nasazení hostitele kontejneru](https://msdn.microsoft.com/virtualization/windowscontainers/deployment/deployment) článku nainstalujte kontejnery a Docker funkce.

Je potřeba mít Docker pro systém Windows, verze 1.12 Beta 26 nebo vyšší pro podporu Windows kontejnery. Ve výchozím nastavení povoluje Docker založenými na systému Linux kontejnery; Přepněte do Windows kontejnery kliknutím pravým tlačítkem na ikonu Docker na hlavním panelu a vyberte **přepnout do kontejnerů Windows**. Docker spustí proces změny a může být nutný restart.

![Windows – kontejnery](./media/console/SwitchContainer.png)

## <a name="building-the-application"></a>Vytváření aplikace
Obvykle jsou konzolových aplikací distribuovaných přes instalačního programu, FTP nebo sdílené složky nasazení. Pokud nasazujete do kontejneru, prostředky nutné zkompilovat a dvoufázové instalace do umístění, které lze použít při vytváření bitové kopie Docker.

V *build.ps1*, tento skript využívá [MSBuild](/visualstudio/msbuild/msbuild) zkompilovat aplikace k dokončení úlohy vytváření prostředků. Existuje několik parametrů předaný MSBuild finalizace potřebné prostředky. Název souboru projektu nebo řešení, které mají být zkompilovány, do, umístění pro výstup a nakonec konfigurace (verze nebo verze pro ladění).

Ve volání `Invoke-MSBuild` `OutputPath` je nastaven na **publikování** a `Configuration` nastavena na **verze**. 

```
function Invoke-MSBuild ([string]$MSBuildPath, [string]$MSBuildParameters) {
    Invoke-Expression "$MSBuildPath $MSBuildParameters"
}

Invoke-MSBuild -MSBuildPath "MSBuild.exe" -MSBuildParameters ".\ConsoleRandomAnswerGenerator.csproj /p:OutputPath=.\publish /p:Configuration=Release"
```

## <a name="creating-the-dockerfile"></a>Vytváření soubor Docker
Základní image použitá pro konzolu aplikace rozhraní .NET Framework je `microsoft/windowsservercore`, veřejně dostupné v [úložiště Docker Hub](https://hub.docker.com/r/microsoft/windowsservercore/). Bitová kopie obsahuje minimální instalaci systému Windows Server 2016, rozhraní .NET Framework 4.6.2 a slouží jako základní bitovou kopii operačního systému Windows kontejnerů.

```
FROM microsoft/windowsservercore
ADD publish/ /
ENTRYPOINT ConsoleRandomAnswerGenerator.exe
```
V prvním řádku soubor Docker označí základní bitovou kopii pomocí [ `FROM` ](https://docs.docker.com/engine/reference/builder/#/from) instrukcí. Dále [ `ADD` ](https://docs.docker.com/engine/reference/builder/#/add) v souboru zkopíruje prostředky aplikace z **publikování** složky do kořenové složky kontejneru a poslední; nastavení [ `ENTRYPOINT` ](https://docs.docker.com/engine/reference/builder/#/entrypoint) z bitové kopie stavů že toto je příkaz nebo aplikaci, která se spustí při spuštění kontejneru. 

## <a name="creating-the-image"></a>Vytváření bitové kopie
Chcete-li vytvořit bitovou kopii Docker, následující kód je přidán do *build.ps1* skriptu. Při spuštění skriptu `console-random-answer-generator` bitové kopie je vytvořený pomocí prostředky kompilují ze MSBuild definované v [vytváření aplikace](#building-the-application) části.

```powershell
$ImageName="console-random-answer-generator"

function Invoke-Docker-Build ([string]$ImageName, [string]$ImagePath, [string]$DockerBuildArgs = "") {
    echo "docker build -t $ImageName $ImagePath $DockerBuildArgs"
    Invoke-Expression "docker build -t $ImageName $ImagePath $DockerBuildArgs"
}

Invoke-Docker-Build -ImageName $ImageName -ImagePath "."
```

Spuštění skriptu pomocí `.\build.ps1` z příkazového řádku prostředí PowerShell.

Po dokončení sestavení pomocí `docker images` příkazu z příkazového řádku nebo příkazovém řádku prostředí PowerShell; uvidíte, že obrázek je vytvořená a připravená ke spuštění.

```
REPOSITORY                        TAG                 IMAGE ID            CREATED             SIZE
console-random-answer-generator   latest              8f7c807db1b5        8 seconds ago       7.33 GB
```

## <a name="running-the-container"></a>Spuštění kontejneru
Kontejner můžete spustit z příkazového řádku pomocí Docker příkazy.

```
docker run console-random-answer-generator "Are you a square container?"
```

Výstup

```
The answer to your question: 'Are you a square container?' is Concentrate and ask again on (70C3D48F4343)
```

Pokud spustíte `docker ps -a` příkazu z prostředí PowerShell, uvidíte, že kontejner stále existuje.

```
CONTAINER ID        IMAGE                             COMMAND                  CREATED             STATUS                          
70c3d48f4343        console-random-answer-generator   "cmd /S /C ConsoleRan"   2 minutes ago       Exited (0) About a minute ago      
```

Ve sloupci Stav ukazuje na "přibližně před minutou", aplikace je úplná a může být vypnuté. Pokud tohoto příkazu Set časy, by sto levém statické kontejnery s žádnou činnost. V případě začátku ideální operace byla práci a vypnutí nebo čištění. K provedení pracovního postupu, přidání `--rm` možnost k `docker run` příkaz odebere kontejneru co nejrychleji `Exited` přijetí signál.

```
docker run --rm console-random-answer-generator "Are you a square container?"
```

Pomocí této možnosti spustíte příkaz a podívat se na výstup `docker ps -a` příkaz; Všimněte si, že id kontejneru ( `Environment.MachineName`) není v seznamu.

### <a name="running-the-container-using-powershell"></a>Spuštění kontejneru pomocí prostředí PowerShell
V ukázkových souborů projektu je také *run.ps1* což je příklad toho, jak pomocí prostředí PowerShell a spusťte aplikaci přijímá argumenty.

Pokud chcete spustit, otevřete prostředí PowerShell a použijte následující příkaz:

```
.\run.ps1 "Is this easy or what?"
```

## <a name="summary"></a>Souhrn
Stejně tak, že přidání soubor Docker a publikování aplikace, můžete containerize vaší konzolové aplikace .NET Framework a nyní využít výhod spuštění více instancí, čisté spuštění a zastavení a další funkce systému Windows Server 2016 bez provedení žádné změny kódu aplikace vůbec.
