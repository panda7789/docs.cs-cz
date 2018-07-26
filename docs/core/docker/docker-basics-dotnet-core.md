---
title: Základy Dockeru s .NET Core
description: Základní kurz k .NET Core a Docker
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 02b6b3fc9e149f5d1d5d78e310c7df257be983c1
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37961544"
---
# <a name="learn-docker-basics-with-net-core"></a>Základy Dockeru s .NET Core

V tomto kurzu se dozvíte, jaké Docker, kontejner sestavení a nasazení úlohy pro aplikace .NET Core. V průběhu tohoto kurzu se dozvíte:

> [!div class="checklist"]
> * Vytvoření souboru Dockerfile
> * Postup vytvoření aplikace .NET Core.
> * Jak nasadit aplikace do kontejneru Dockeru.

[Platforma Docker](https://docs.docker.com/engine/docker-overview/#the-docker-platform) používá [modul Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) k rychlému sestavování a balíčky aplikací jako [imagí Dockeru](https://docs.docker.com/glossary/?term=image). Tyto Image jsou napsané v [soubor Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) formátu k nasazení a spouštění [vrstvy kontejneru](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).

## <a name="net-core-easiest-way-to-get-started"></a>.NET core: Nejjednodušší způsob, jak začít

Před vytvořením image Dockeru, musíte aplikaci kontejnerizace. Můžete jej vytvořit v Linuxu, MacOS nebo Windows. Nejrychlejší a nejjednodušší způsob, jak to udělat, je použití .NET Core.

Pokud nejste obeznámeni s sada nástrojů .NET Core CLI, přečtěte si [.NET Core SDK přehled](../tools/index.md).

Můžete vytvářet kontejnery Windows i Linuxu pomocí [více arch na základě značky](https://github.com/dotnet/announcements/issues/14).

## <a name="your-first-net-core-docker-app"></a>Svou první aplikaci .NET Core Dockeru

### <a name="prerequisites"></a>Požadavky

K dokončení tohoto kurzu:

#### <a name="net-core-20-sdk"></a>.NET core 2.0 SDK

* Nainstalujte [.NET Core SDK 2.0](https://www.microsoft.com/net/core).

Zobrazit [podporované verze operačního systému aplikace .NET Core 2.x](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) pro úplný seznam .NET Core 2.x podporované operační systémy, z verze podporu operačního systému a propojení zásad životního cyklu.

* Pokud jste tak dosud neučinili, nainstalujte váš oblíbený editor kódu.

> [!TIP]
> Je potřeba nainstalovat editor kódu? Zkuste [sady Visual Studio](https://visualstudio.com/downloads)!

#### <a name="installing-docker-client"></a>Instalace klienta Dockeru

Nainstalujte [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) nebo novější klienta Dockeru.

Klienta Dockeru se dá nainstalovat ve:

* Linuxové distribuce

   * [CentOS](https://www.docker.com/docker-centos-distribution)

   * [Debian](https://www.docker.com/docker-debian)

   * [Fedora](https://www.docker.com/docker-fedora)

   * [Ubuntu](https://www.docker.com/docker-ubuntu)

* [macOS](https://docs.docker.com/docker-for-mac/)

* [Windows](https://docs.docker.com/docker-for-windows/).

### <a name="create-a-net-core-20-console-app-for-dockerization"></a>Vytvoření konzolové aplikace .NET Core 2.0 pro Dockerization

Otevřete příkazový řádek a vytvořte složku s názvem *Hello*. Přejděte do složky, kterou jste vytvořili a zadejte následující příkazy:

```console
dotnet new console
dotnet run
```

Pojďme si rychlý návod:

1. `$ dotnet new console`

   [`dotnet new`](../tools/dotnet-new.md) Vytvoří aktuální `Hello.csproj` soubor projektu se závislostmi, které jsou potřebné k sestavení aplikace konzoly.  Vytvoří se také `Program.cs`, základní soubor, který obsahuje vstupní bod pro aplikaci.
   
   `Hello.csproj`:

   Soubor projektu určuje vše, co je potřeba k obnovení závislostí a sestavit program.

   * `OutputType` Značka Určuje, že vytváříme spustitelný soubor, jinými slovy konzolové aplikace.
   * `TargetFramework` Značky Určuje, jaké implementace .NET jsme cílíte. V pokročilém scénáři můžete zadat více cílových platforem a od sestavení k architekturami zadanými v rámci jedné operace. V tomto kurzu jsme integrovali pro .NET Core 2.0.

   `Program.cs`:

   Spuštění programu pomocí `using System`. Toto prohlášení znamená, "umožňuje přinést si všechno, co `System` oboru názvů do oboru tohoto souboru." `System` Obor názvů obsahuje základní konstrukce, jako `string`, nebo číselné typy.

   My pak definovat obor názvů s názvem `Hello`. Obor názvů můžete změnit na všechno, co chcete. Třída s názvem `Program` je definována v daném oboru názvů s `Main` metodu, která přijímá pole řetězců jako svůj argument. Toto pole se seznamem argumentů předaných v při volání zkompilovaný program. V našem příkladu program zapíše pouze "Hello World!" do konzoly.

2. `$ dotnet restore`

   V .NET Core 2.x, **dotnet nové** běží [ `dotnet restore` ](../tools/dotnet-restore.md) příkazu. **DotNet restore** strom závislostí se obnoví [NuGet](https://www.nuget.org/)volání (Správce balíčků .NET).
   NuGet provádí následující úlohy:
   * analyzuje *Hello.csproj* souboru 
   * stáhne soubor závislosti (nebo získá z mezipaměti počítače)
   * zapíše *obj/project.assets.json* souboru

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
   
   *Project.assets.json* soubor je kompletní sadu grafu závislostí NuGet, řešení vazby a další metadata aplikace. To vyžaduje soubor je používán jiné nástroje, jako například [ `dotnet build` ](../tools/dotnet-build.md) a [ `dotnet run` ](../tools/dotnet-run.md), správně zpracovat zdrojový kód.
   
3. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) volání [ `dotnet build` ](../tools/dotnet-build.md) potvrďte úspěšné sestavení a volání `dotnet <assembly.dll>` ke spuštění aplikace.
   
    ```console
    $ dotnet run
    
    Hello World!
    ```

    Pokročilé scénáře, naleznete v tématu [nasazení aplikace .NET Core](../deploying/index.md) podrobnosti.

## <a name="dockerize-the-net-core-application"></a>Dockerizace aplikací .NET Core

Konzolovou aplikaci Hello .NET Core úspěšně běží místně. Nyní Pojďme jít o krok dál a sestavit a spustit aplikaci v Dockeru.

### <a name="your-first-dockerfile"></a>Vaše první soubor Dockerfile

Otevřete textový editor a můžeme začít! Z adresáře Hello, kterou jsme vytvořili aplikaci v pořád pracujeme.

Přidejte následující pokyny Dockeru pro buď Linux nebo [kontejnery Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) do nového souboru. Až budete hotovi, uložte ho v kořenovém adresáři Hello jako **soubor Dockerfile**, bez přípony (budete muset nastavit vašemu typu souboru `All types (*.*)` nebo něco podobného).

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# copy and build everything else
COPY . ./
RUN dotnet publish -c Release -o out
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

Soubor Dockerfile obsahuje pokyny pro sestavení Dockeru, které se spouští sekvenčně.

Musí být první instrukce [ **FROM**](https://docs.docker.com/engine/reference/builder/#from). Tento pokyn inicializuje nové fázi sestavení a nastaví základní Image pro pokynů. Více architektury značky kontejnery Windows nebo Linuxem v závislosti na Docker pro Windows o přijetí změn [režimu kontejneru](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers). Základní Image pro naše ukázka je 2.0 sdk image z úložiště microsoft/dotnet

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
```

[ **WORKDIR** ](https://docs.docker.com/engine/reference/builder/#workdir) instrukce nastaví pracovní adresář pro všechny zbývající spuštění, CMD, ENTRYPOINT, kopírování a souboru Dockerfile přidat pokyny. Pokud adresář neexistuje, vytvoří se. V takovém případě WORKDIR nastavena na adresář aplikace.

```Dockerfile
WORKDIR /app
```

[ **Kopírování** ](https://docs.docker.com/engine/reference/builder/#copy) instrukce zkopíruje nové soubory nebo adresáře z cesty zdrojových a přidá je do cílového systému souborů kontejneru. S tuto instrukci jsme kopírujete soubor projektu C# do kontejneru.

```Dockerfile
COPY *.csproj ./
```

[ **Spustit** ](https://docs.docker.com/engine/reference/builder/#run) instrukce spustí všechny příkazy v nové vrstvě nad aktuální imagí a potvrďte výsledky. Výsledná potvrzená image se používá k dalšímu kroku v souboru Dockerfile. Spouštíme **dotnet restore** získat potřebné závislosti soubor projektu C#. 

```Dockerfile
RUN dotnet restore
```

To **kopírování** instrukce zkopíruje zbývající soubory do našich kontejneru do nové [vrstvy](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).

```Dockerfile
COPY . ./
```

Publikujeme aplikaci s tímto **spustit** instrukce. [ **Dotnet publikovat** ](../tools/dotnet-publish.md) příkaz zkompiluje aplikaci, přečte prostřednictvím jeho závislosti v souboru projektu zadána a publikuje výslednou sadu souborů do adresáře. Naše aplikace je publikována s **vydání** konfigurace a výstup do výchozí adresář.

```Dockerfile
RUN dotnet publish -c Release -o out
```

[ **ENTRYPOINT** ](https://docs.docker.com/engine/reference/builder/#entrypoint) instrukce umožňuje kontejner pro spuštění jako spustitelný soubor.

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

Nyní je třeba soubor Dockerfile, který:

* zkopíruje vaší aplikace do bitové kopie
* závislostí vaší aplikace do bitové kopie
* spuštění jako spustitelný soubor aplikace sestavení

### <a name="build-and-run-the-hello-net-core-20-app"></a>Sestavíte a spustíte aplikaci Hello .NET Core 2.0

#### <a name="essential-docker-commands"></a>Základní příkazy Dockeru

Jsou nezbytné tyto příkazy Dockeru:

* [sestavení dockeru](https://docs.docker.com/engine/reference/commandline/build/)
* [docker, spusťte](https://docs.docker.com/engine/reference/commandline/run/)
* [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
* [docker stop](https://docs.docker.com/engine/reference/commandline/stop/)
* [docker rm](https://docs.docker.com/engine/reference/commandline/rm/)
* [rmi dockeru](https://docs.docker.com/engine/reference/commandline/rmi/)
* [image dockeru](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a>Sestavit a spustit

Jste napsali soubor dockerfile; Docker teď sestavení vaší aplikace a pak spustí kontejner.

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

Výstup `docker build` příkaz by měl být podobný výstup konzoly následující:

```console
Sending build context to Docker daemon   72.7kB
Step 1/7 : FROM microsoft/dotnet:2.0-sdk
 ---> d84f64b126a6
Step 2/7 : WORKDIR /app
 ---> Using cache
 ---> 9af1fbdc7972
Step 3/7 : COPY *.csproj ./
 ---> Using cache
 ---> 86c8c332d4b3
Step 4/7 : RUN dotnet restore
 ---> Using cache
 ---> 86fcd7dd0ea4
Step 5/7 : COPY . ./
 ---> Using cache
 ---> 6faf0a53607f
Step 6/7 : RUN dotnet publish -c Release -o out
 ---> Using cache
 ---> f972328318c8
Step 7/7 : ENTRYPOINT dotnet out/Hello.dll
 ---> Using cache
 ---> 53c337887e18
Successfully built 53c337887e18
Successfully tagged dotnetapp-dev:latest
```

Jak je vidět z výstupu modulu Docker použít soubor Dockerfile k sestavení náš kontejner.

Výstup `docker run` příkaz by měl být podobný výstup konzoly následující:

```console
Hello World!
```

Blahopřejeme! máte jen:
> [!div class="checklist"]
> * Vytvoření místní aplikace .NET Core
> * Vytvoření souboru Dockerfile k vytvoření prvního kontejneru služby
> * Vytvořené a spustili aplikaci Dockerized



## <a name="next-steps"></a>Další kroky

Tady jsou některé další kroky, které si můžete:

* [Úvod do Video Image .NET Dockeru](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [Visual Studio, Docker a Azure Container Instances společně to jde líp!](https://blogs.msdn.microsoft.com/alimaz/2017/08/17/visual-studio-docker-azure-container-instances-better-together/)
* [Docker for rychlí průvodci Azure](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [Nasazení vaší aplikace v Dockeru pro Azure](https://docs.docker.com/docker-for-azure/deploy/)

> [!Note]
> Pokud nemáte předplatné Azure, [zaregistrujte se ještě dnes](https://azure.microsoft.com/free/?b=16.48) pro bezplatný účet 30 dní a získat 200 USD v kreditech Azure pro vyzkoušení jakékoli kombinace služeb Azure.

## <a name="docker-images-used-in-this-sample"></a>Používané v tomto příkladu Imagí dockeru

V této ukázce se používají následující Image Dockeru

* [`microsoft/dotnet:2.0-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a>Související prostředky

* [Ukázky Dockeru .NET core](https://github.com/dotnet/dotnet-docker-samples/README.md)
* [Soubor Docker na kontejnery Windows](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [Ukázky Dockeru rozhraní .NET framework](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [ASP.NET Core na Dockerhubu](https://hub.docker.com/r/microsoft/aspnetcore/)
* [Dockerizace aplikací .NET Core – kurz Dockeru](https://docs.docker.com/engine/examples/dotnetcore/)
* [Práce s nástroji Dockeru pro Visual Studio](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [Nasazování Imagí Dockeru ze služby Azure Container Registry do služby Azure Container Instances](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)