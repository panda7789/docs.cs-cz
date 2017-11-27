---
title: "Další základní informace o Docker s .NET Core"
description: "Základní kurz .NET Core a Docker"
keywords: "Rozhraní .NET, rozhraní .NET core, Docker, kurzu"
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
ms.custom: mvc
manager: wpickett
ms.openlocfilehash: 5935f67d7e4ca9c9e8768373e2bcaa9febccfdc5
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/08/2017
---
# <a name="learn-docker-basics-with-net-core"></a>Další základní informace o Docker s .NET Core

V tomto kurzu se dozvíte, jaké Docker kontejneru sestavení a nasazení úlohy pro aplikace .NET Core. V průběhu tohoto kurzu se seznámíte:

> [!div class="checklist"]
> * Jak vytvořit soubor Docker
> * Jak vytvořit aplikaci .NET Core.
> * Postup nasazení aplikace do kontejner Docker.

[Docker platformy](https://docs.docker.com/engine/docker-overview/#the-docker-platform) používá [modulu Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) rychle vytvářet a balíček aplikace jako [imagí Dockeru](https://docs.docker.com/glossary/?term=image). Tyto Image jsou zapsány v [soubor Docker](https://docs.docker.com/glossary/?term=Dockerfile) formát, který se nasadit a spustit [vrstvený kontejneru](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).

## <a name="net-core-easiest-way-to-get-started"></a>.NET core: Nejjednodušším způsobem Začínáme

Před vytvořením bitové kopie Docker, musíte aplikaci containerize. Můžete ho vytvořit v systému Linux, systému MacOS nebo systému Windows. Nejrychlejší a nejjednodušší způsob, jak to udělat, je použití .NET Core.

Pokud jste obeznámeni s .NET Core rozhraní příkazového řádku sady nástrojů, přečtěte si [.NET Core SDK přehled](../tools/index.md).

Můžete vytvořit kontejnery Windows a Linux s [architektura více na základě značek](https://github.com/dotnet/announcements/issues/14).

## <a name="your-first-net-core-docker-app"></a>První aplikace .NET Core Docker

### <a name="prerequisites"></a>Požadavky

K dokončení tohoto kurzu:

#### <a name="net-core-20-sdk"></a>Základní rozhraní .NET 2.0 SDK

* Nainstalujte [.NET Core SDK 2.0](https://www.microsoft.com/net/core).

V tématu [2.x .NET Core, podporované verze operačního systému](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) pro úplný seznam .NET Core 2.x podporované operační systémy, mimo verze podporu operačního systému a odkazy na zásady životního cyklu.

* Pokud jste to ještě neudělali, nainstalujte editor vaše oblíbené kódu.

> [!TIP]
> Je potřeba nainstalovat editor kódu? Zkuste [sady Visual Studio](https://visualstudio.com/downloads)!

#### <a name="installing-docker-client"></a>Instalace klienta Docker

Nainstalujte [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) nebo novější Docker klienta.

Klient Docker může být nainstalován v:

* Distribuce systému Linux

   * [CentOS](https://www.docker.com/docker-centos-distribution)

   * [Debian](https://www.docker.com/docker-debian)

   * [Fedora](https://www.docker.com/docker-fedora)

   * [Ubuntu](https://www.docker.com/docker-ubuntu)

* [systému macOS](https://docs.docker.com/docker-for-mac/)

* [Windows](https://docs.docker.com/docker-for-windows/).

### <a name="create-a-net-core-20-console-app-for-dockerization"></a>Vytvoření aplikace konzoly .NET Core 2.0 pro Dockerization

Otevřete příkazový řádek a vytvořte složku s názvem *Hello*. Přejděte do složky, kterou jste vytvořili a zadejte následující příkazy:

```console
dotnet new console
dotnet run
```

Umožňuje provést rychlé názorný postup:

1. `$ dotnet new console`

   [`dotnet new`](../tools/dotnet-new.md)Vytvoří aktuální `Hello.csproj` souboru projektu se závislostmi, které jsou potřebné k vytvoření konzolové aplikace.  Vytvoří také `Program.cs`, základní souboru, který obsahuje vstupní bod pro aplikaci.
   
   `Hello.csproj`:

   Soubor projektu určuje vše, co je potřeba k obnovení závislosti a sestavte program.

   * `OutputType` Značky Určuje, že vytváříme spustitelný soubor, jinými slovy konzolové aplikace.
   * `TargetFramework` Značky Určuje, jaké implementace rozhraní .NET jsme se cílení na. V pokročilém scénáři můžete zadat několik cílové architektury a sestavení k zadané architektury v rámci jedné operace. V tomto kurzu jsme sestavení pro rozhraní .NET 2.0 jádra.

   `Program.cs`:

   Program se spustí `using System`. Toto prohlášení znamená, "předány všechno, co `System` oboru názvů do oboru pro tento soubor." `System` Obor názvů obsahuje základní konstrukce, jako `string`, nebo číselnými typy.

   Potom jsme definovali obor názvů s názvem `Hello`. Obor názvů, můžete změnit na nic, co chcete. Třída s názvem `Program` je definována v daném oboru názvů pomocí `Main` metody, která přijímá pole řetězců jako její argument. Toto pole obsahuje seznam argumentů předaná při volání zkompilovaný program. V našem příkladu program pouze zapíše "Hello, World!" ke konzole.

2. `$ dotnet restore`

   V .NET Core 2.x, **dotnet nové** běží [ `dotnet restore` ](../tools/dotnet-restore.md) příkaz. **Obnovení DotNet** obnoví stromu závislosti s [NuGet](https://www.nuget.org/)volání (Správce balíčků .NET).
   NuGet provede následující úlohy:
   * analyzuje *Hello.csproj* souboru 
   * Načtení souboru závislosti (nebo získá z vašeho počítače mezipaměti)
   * zapíše *obj/project.assets.json* souboru

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
   
   *Project.assets.json* soubor je kompletní sada grafu závislostí NuGet, řešení vazby a další metadata aplikace. To vyžadováno, soubor je používán jiných nástrojů, jako například [ `dotnet build` ](../tools/dotnet-build.md) a [ `dotnet run` ](../tools/dotnet-run.md), správně zpracovat zdrojový kód.
   
3. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md)volání [ `dotnet build` ](../tools/dotnet-build.md) potvrďte úspěšném sestavení a poté zavolá `dotnet <assembly.dll>` ke spuštění aplikace.
   
    ```console
    $ dotnet run
    
    Hello World!
    ```

    Složitější scénáře, najdete v části [nasazení aplikace .NET Core](../deploying/index.md) podrobnosti.

## <a name="dockerize-the-net-core-application"></a>Dockerize aplikace .NET Core

Konzolové aplikace Hello .NET Core úspěšně běží místně. Teď umožňuje provádět ho další krok a sestavení a spuštění aplikace v nástroji Docker.

### <a name="your-first-dockerfile"></a>Vaše první soubor Docker

Otevřete textový editor a můžeme začít! Z Hello adresáře, které jsme vytvořili aplikaci v stále pracujeme.

Přidejte následující pokyny Docker buď Linux nebo [Windows kontejnery](https://docs.microsoft.com/virtualization/windowscontainers/about/) do nového souboru. Po dokončení uložte jej v kořenovém adresáři Hello jako **soubor Docker**, bez přípony (budete muset nastavit vašeho typu souboru `All types (*.*)` nebo něco podobné).

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

Soubor Docker obsahuje pokyny Docker sestavení, které spouští sekvenčně.

Musí být první pokyn [ **FROM**](https://docs.docker.com/engine/reference/builder/#from). Tento pokyn inicializuje nové fáze sestavení a nastaví pro základní bitovou kopii podle zbývajících pokynů. Více architektury značky pro vyžádání obsahu systému Windows nebo Linux kontejnery v závislosti na Docker pro systém Windows [režim kontejneru](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers). Pro základní bitovou kopii naše ukázka je 2.0 sdk image z úložiště microsoft/dotnet.

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
```

[ **WORKDIR** ](https://docs.docker.com/engine/reference/builder/#workdir) instrukce nastaví pracovní adresář pro všechny zbývající spustit, CMD, vstupní bod, kopírování a přidat soubor Docker pokyny. Pokud adresář neexistuje, vytvoří se. V takovém případě WORKDIR nastavena na adresář aplikace.

```Dockerfile
WORKDIR /app
```

[ **Kopie** ](https://docs.docker.com/engine/reference/builder/#copy) instrukce zkopíruje nových souborů nebo adresářů z cesty zdrojových a přidá je do systému cílový kontejner souborů. S Tento pokyn jsme se kopírování souboru projektu C# do kontejneru.

```Dockerfile
COPY *.csproj ./
```

[ **Spustit** ](https://docs.docker.com/engine/reference/builder/#run) instrukce spustí všechny příkazy v novou vrstvu nad aktuální image a potvrďte výsledky. Výsledný potvrdit bitovou kopii se používá pro další krok v soubor Docker. Používáme **dotnet obnovení** získat potřebné závislosti souboru projektu C#. 

```Dockerfile
RUN dotnet restore
```

To **kopie** instrukce zkopíruje zbytek soubory do našich kontejneru do nové [vrstvy](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).

```Dockerfile
COPY . ./
```

Jsme publikují aplikace s tímto **spustit** instrukcí. [ **Dotnet publikování** ](../tools/dotnet-publish.md) příkaz kompilaci aplikace, čte prostřednictvím jeho závislé součásti, zadaný v souboru projektu a publikuje výslednou sadu soubory do adresáře. Naše aplikace je publikována s **verze** konfigurace a výstup do výchozí adresář.

```Dockerfile
RUN dotnet publish -c Release -o out
```

[ **ENTRYPOINT** ](https://docs.docker.com/engine/reference/builder/#entrypoint) instrukce umožňuje kontejneru spustit jako spustitelný soubor.

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

Nyní máte soubor Docker který:

* zkopíruje vaší aplikace do bitové kopie
* závislosti vaší aplikace do bitové kopie
* sestavení v aplikaci spustit jako spustitelný soubor

### <a name="build-and-run-the-hello-net-core-20-app"></a>Sestavení a spuštění aplikace Hello .NET Core 2.0

#### <a name="essential-docker-commands"></a>Základní příkazy Docker

Tyto příkazy Docker je nezbytné:

* [docker sestavení](https://docs.docker.com/engine/reference/commandline/build/)
* [Spustit docker](https://docs.docker.com/engine/reference/commandline/run/)
* [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
* [zastavení docker](https://docs.docker.com/engine/reference/commandline/stop/)
* [docker rm](https://docs.docker.com/engine/reference/commandline/rm/)
* [docker rmi](https://docs.docker.com/engine/reference/commandline/rmi/)
* [Obrázek docker](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a>Sestavení a spuštění

Jste napsali soubor docker; Teď Docker sestavení vaší aplikace a pak spustí kontejneru.

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

Výstup `docker build` příkaz by mělo být podobné výstupu v následujícím konzoly:

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

Jak je vidět z výstupu modulu Docker soubor Docker použita k vytvoření naše kontejneru.

Výstup `docker run` příkaz by mělo být podobné výstupu v následujícím konzoly:

```console
Hello World!
```

Blahopřejeme! máte právě:
> [!div class="checklist"]
> * Vytvořit místní aplikace .NET Core
> * Vytvořit soubor Docker k vytvoření vaší první kontejneru
> * Vytvořené a spustil aplikaci Dockerized



## <a name="next-steps"></a>Další kroky

Zde jsou některé další kroky, které můžete provést:

* [Úvod do rozhraní .NET Docker bitové kopie Video](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [Visual Studio, Docker & instancí kontejnerů Azure lepší společně!](https://blogs.msdn.microsoft.com/alimaz/2017/08/17/visual-studio-docker-azure-container-instances-better-together/)
* [Docker pro Azure – elementy QuickStart](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [Nasazení aplikace na Docker pro Azure.](https://docs.docker.com/docker-for-azure/deploy/)

> [!Note]
> Pokud nemáte předplatné Azure, [Přihlaste se ještě dnes](https://azure.microsoft.com/free/?b=16.48) bezplatný účet 30 dnů a 200 USD get v kredity Azure můžete vyzkoušet na libovolnou kombinaci služby Azure.

## <a name="docker-images-used-in-this-sample"></a>Docker obrázků použitých v této ukázce

V této ukázce se používají na následujících obrázcích Docker

* [`microsoft/dotnet:2.0-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a>Související informační zdroje

* [Ukázky rozhraní .NET core Docker](https://github.com/dotnet/dotnet-docker-samples/README.md)
* [Soubor Docker kontejnerům Windows](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [Ukázky rozhraní .NET framework Docker](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [Jádro ASP.NET na DockerHub](https://hub.docker.com/r/microsoft/aspnetcore/)
* [Dockerize aplikace .NET Core – kurz Docker](https://docs.docker.com/engine/examples/dotnetcore/)
* [Práce s nástroji Visual Studio Docker](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [Nasazení bitových kopií Docker z registru kontejner Azure do Azure kontejner instancí](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)