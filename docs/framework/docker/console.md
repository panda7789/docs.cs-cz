---
title: Aplikace konzoly spuštěné v Dockeru
description: Zjistěte, jak využít stávající aplikace konzoly rozhraní .NET Framework a spuštění v kontejneru Windows Docker.
author: spboyer
ms.date: 09/28/2016
ms.assetid: 85cca1d5-c9a4-4eb2-93e6-4f878de07fd7
ms.openlocfilehash: f5a38ac63db969a58e920ea79bf4bf10bcfcf64f
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193327"
---
# <a name="running-console-applications-in-windows-containers"></a>Spuštění konzolové aplikace v kontejnerech Windows

Konzolové aplikace se používají pro celou řadu účelů; od jednoduché dotazování stavu dlouhotrvající bitovou kopii dokumentu zpracování úlohy. Možnost spuštění a tyto aplikace škálovat v každém případě splnění s omezeními hardwaru akvizice, časy spuštění nebo spuštění více instancí.

Přesunutí vaší konzolové aplikace pomocí Docker a Windows Server kontejnery umožňuje spouštění těchto aplikací z čistého stavu, což jim umožňuje provádět operace a vypnutí čistě. Toto téma se zobrazí kroky potřebné k přesunutí konzolovou aplikaci pro Windows základě kontejneru, spusťte ji pomocí skriptu prostředí PowerShell.

Ukázková Konzolová aplikace je jednoduchý příklad, který v tomto případě přebírá argument, dotaz a vrátí náhodné odpovědí. To může trvat `customer_id` a zpracovat jejich daně, nebo vytvořit miniaturu pro `image_url` argument.

Kromě odpověď `Environment.MachineName` se přidal do odpovědi zobrazíte rozdíl mezi spuštěním aplikace místně a v kontejneru Windows. Při místním spuštění aplikace by měla být vrácena název místního počítače a při spuštění v kontejneru Windows; id relace kontejneru se vrátí.

[Kompletní příklad](https://github.com/dotnet/samples/tree/master/framework/docker/ConsoleRandomAnswerGenerator) je k dispozici v úložišti dotnet/samples na Githubu. Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Musíte znát některé Docker podmínky před zahájením práce ohledně přesunu aplikace do kontejneru.

> A *image Dockeru* je jen pro čtení šablona definující prostředí pro spuštěný kontejner, včetně operačního systému (OS), součásti systému a aplikací.

Důležitou součástí Image Dockeru je, že Image se skládají ze základní image. Každý nový obrázek přidá malé sadě funkcí do existující image. 

> A *kontejneru Dockeru* je spuštěna instance bitovou kopii. 

Škálování aplikace spuštěním stejnou bitovou kopii v spousta kontejnerů.
Koncepčně je podobná spuštění stejné aplikace v několika hostitelích.

Další informace o architektuře Dockeru najdete [přehled Dockeru](https://docs.docker.com/engine/understanding-docker/) na web Dockeru. 

Přesun vaší konzolové aplikace je otázkou pár kroků.

1. [Sestavení aplikace](#building-the-application)
1. [Vytváří se soubor Dockerfile pro bitovou kopii](#creating-the-dockerfile)
1. [Proces sestavení a spuštění kontejneru Dockeru](#creating-the-image)

## <a name="prerequisites"></a>Požadavky
Kontejnery Windows se podporují na [Windows 10 Anniversary Update](https://www.microsoft.com/en-us/software-download/windows10/) nebo [Windows serveru 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server).

> [!NOTE]
>Pokud používáte Windows Server 2016, je nutné kontejnery ručně povolit, protože instalační služba Docker pro Windows nebudou povolení této funkce. Ujistěte se, že všechny aktualizace spustili pro operační systém a pak postupujte podle pokynů v [nasazení hostitele kontejneru](https://msdn.microsoft.com/virtualization/windowscontainers/deployment/deployment) článku a nainstalujte kontejnery a Docker funkce.

Musíte mít Docker pro Windows, kontejnery Windows verze 1.12 Beta 26 nebo vyšší pro podporu. Ve výchozím nastavení Docker umožňuje kontejnery založené na Linuxu; Přepnout na kontejnery Windows klikněte pravým tlačítkem myši klikněte na ikonu Dockeru na hlavním panelu systému a vyberte **přepnout na kontejnery Windows**. Docker se spustí proces změny a může vyžadovat restartování.

![Kontejnery Windows](./media/console/SwitchContainer.png)

## <a name="building-the-application"></a>Sestavení aplikace
Obvykle se distribuují konzolové aplikace pomocí instalačního programu, FTP nebo sdílené složky nasazení. Při nasazování do kontejneru, třeba prostředky zkompilovat a připravené k umístění, ke kterému se dá použít při vytvoření image Dockeru.

V *build.ps1*, tento skript využívá [MSBuild](/visualstudio/msbuild/msbuild) pro kompilaci aplikace k dokončení úlohy vytváření prostředků. Existuje několik parametrů předávaným do MSBuild pro dokončení potřebné prostředky. Název souboru projektu nebo řešení ke kompilaci, umístění výstupu a nakonec požadované konfigurace (vydání nebo ladícího).

Při volání funkce `Invoke-MSBuild` `OutputPath` je nastavena na **publikovat** a `Configuration` nastavena na **vydání**. 

```
function Invoke-MSBuild ([string]$MSBuildPath, [string]$MSBuildParameters) {
    Invoke-Expression "$MSBuildPath $MSBuildParameters"
}

Invoke-MSBuild -MSBuildPath "MSBuild.exe" -MSBuildParameters ".\ConsoleRandomAnswerGenerator.csproj -p:OutputPath=.\publish -p:Configuration=Release"
```

## <a name="creating-the-dockerfile"></a>Vytvoření souboru Dockerfile
Základní image používá pro konzolu aplikace rozhraní .NET Framework je `microsoft/windowsservercore`, která je veřejně dostupná na [Docker Hubu](https://hub.docker.com/r/microsoft/windowsservercore/). Základní image obsahuje minimální instalaci Windows serveru 2016, rozhraní .NET Framework 4.6.2 a slouží jako základní image operačního systému pro kontejnery Windows.

```
FROM microsoft/windowsservercore
ADD publish/ /
ENTRYPOINT ConsoleRandomAnswerGenerator.exe
```
Určuje první řádek v souboru Dockerfile pomocí základní image [ `FROM` ](https://docs.docker.com/engine/reference/builder/#/from) instrukce. Dále [ `ADD` ](https://docs.docker.com/engine/reference/builder/#/add) v souboru zkopíruje prostředky aplikace z **publikovat** složka ke kořenové složce kontejneru a poslední; nastavení [ `ENTRYPOINT` ](https://docs.docker.com/engine/reference/builder/#/entrypoint) stavů bitové kopie, že je příkaz nebo aplikaci, která se spustí při spuštění kontejneru. 

## <a name="creating-the-image"></a>Vytváření bitové kopie
Pokud chcete vytvořit image Dockeru, následující kód je přidán do *build.ps1* skriptu. Při spuštění skriptu `console-random-answer-generator` image se vytvoří pomocí prostředky z MSBuild definované v [vytváření aplikace](#building-the-application) oddílu.

```powershell
$ImageName="console-random-answer-generator"

function Invoke-Docker-Build ([string]$ImageName, [string]$ImagePath, [string]$DockerBuildArgs = "") {
    echo "docker build -t $ImageName $ImagePath $DockerBuildArgs"
    Invoke-Expression "docker build -t $ImageName $ImagePath $DockerBuildArgs"
}

Invoke-Docker-Build -ImageName $ImageName -ImagePath "."
```

Spuštění skriptu pomocí `.\build.ps1` z příkazového řádku Powershellu.

Po dokončení sestavení pomocí `docker images` příkazu z příkazového řádku nebo příkazového řádku Powershellu, uvidíte, že na obrázku je vytvořená a připravená ke spuštění.

```
REPOSITORY                        TAG                 IMAGE ID            CREATED             SIZE
console-random-answer-generator   latest              8f7c807db1b5        8 seconds ago       7.33 GB
```

## <a name="running-the-container"></a>Spuštění kontejneru
Kontejner můžete spustit z příkazového řádku pomocí příkazu Docker.

```
docker run console-random-answer-generator "Are you a square container?"
```

Výstup je

```
The answer to your question: 'Are you a square container?' is Concentrate and ask again on (70C3D48F4343)
```

Pokud spustíte `docker ps -a` příkazu v Powershellu, uvidíte, že kontejner stále existuje.

```
CONTAINER ID        IMAGE                             COMMAND                  CREATED             STATUS                          
70c3d48f4343        console-random-answer-generator   "cmd /S /C ConsoleRan"   2 minutes ago       Exited (0) About a minute ago      
```

Sloupec stavu zobrazí v "přibližně před minutou", aplikace byl dokončen a může být vypnut. Pokud jste příkaz spustili stovek časy, by existovat sto levé statické kontejnery s žádnou činnost. Ve scénáři začátek ideální operace byla pro práci a vypnutí nebo vyčistit. K provedení tohoto postupu přidání `--rm` umožňuje `docker run` příkaz odstraní kontejner poté, co `Exited` obdrží se signál.

```
docker run --rm console-random-answer-generator "Are you a square container?"
```

Spuštění příkazu s touto možností a podívat se na výstup `docker ps -a` příkazu, Všimněte si, že id kontejneru ( `Environment.MachineName`) není v seznamu.

### <a name="running-the-container-using-powershell"></a>Spuštění kontejneru pomocí Powershellu
V ukázkových souborů projektu k dispozici je také *run.ps1* což je příklad toho, jak pomocí prostředí PowerShell a spusťte aplikaci přijímá argumenty.

Pokud chcete spustit, otevřete PowerShell a pomocí následujícího příkazu:

```
.\run.ps1 "Is this easy or what?"
```

## <a name="summary"></a>Souhrn
Pouhým přidáním souboru Dockerfile a publikování aplikace, můžete kontejnerizace aplikace konzoly rozhraní .NET Framework a nyní využít přitom žádné spuštěných víc instancí, spuštění a zastavení a další funkce Windows serveru 2016 změny kódu aplikace vůbec.
