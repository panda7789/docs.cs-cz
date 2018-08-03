---
title: Vytváření Imagí Dockeru .NET Core
description: Principy imagí Dockeru a .NET Core
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e48a263334ebb93a5d281032336aeb4073d8467c
ms.sourcegitcommit: e8dc507cfdaad504fc9d4c83d28d24569dcef91c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "34827336"
---
# <a name="building-docker-images-for-net-core-applications"></a>Vytváření Imagí Dockeru pro aplikace .NET Core

 V tomto kurzu se zaměříme na tom, jak pomocí .NET Core v Dockeru. Nejprve podíváme na různé imagí Dockeru k dispozici a spravován společností Microsoft a případy použití. Potom jsme zjistěte, jak sestavit a dockerizace aplikace ASP.NET Core.

V průběhu tohoto kurzu se dozvíte:
> [!div class="checklist"]
> * Další informace o imagích Dockeru rozhraní Microsoft .NET Core 
> * Získat ASP.NET Core ukázkovou aplikaci do Dockerize
> * Spuštění ukázkové aplikace ASP.NET místně
> * Sestavte a spusťte ukázku s prostředím Docker pro kontejnery Linuxu
> * Sestavte a spusťte ukázku s kontejnery Docker pro Windows

## <a name="docker-image-optimizations"></a>Optimalizace Image dockeru

Při vytváření imagí Dockeru pro vývojáře, jsme se zaměřili na třech hlavních scénářích:

* Obrázky používané pro vývoj aplikací .NET Core
* Image sloužící k sestavení aplikace .NET Core
* Obrázky používané ke spouštění aplikací .NET Core

Proč tři Image?
Při vývoji, vytváření a spouštění kontejnerizovaných aplikací, jsme mají různé priority.

* **Vývoj:** prioritou se zaměřuje na rychle iterovat změny a možnost ladit změny. Velikost bitové kopie není důležité, místo toho můžete provést změny kódu a rychle vidět?

* **Sestavení:** tento obrázek obsahuje vše potřebné pro kompilaci aplikace, které zahrnují kompilátor a další závislosti optimalizovat binární soubory.  Sestavení image použijete k vytvoření majetek, který umístíte do produkčního prostředí image. Sestavení image se použije pro průběžnou integraci, nebo v prostředí sestavení. Tento přístup umožňuje agenta sestavení pro zkompilování a vybuildování aplikace (s všechny požadované závislosti) v instanci bitové kopie sestavení. Agenta sestavení stačí vědět, jak ke spuštění této image Dockeru.

* **Produkční:** jak rychle můžete nasadit a spustit image? Tato image je malé, takže je optimalizován výkon sítě z registru Dockeru do Docker hostitelů. Obsah je připraven ke spuštění povolení nejrychlejší doba od Dockeru, spusťte na zpracování výsledků. Dynamický kód kompilace, není nutná v modelu Dockeru. Obsah, který umístíte do této bitové kopie omezeny na binární soubory a obsah potřebný ke spuštění aplikace.

    Například `dotnet publish` výstup obsahuje:

    * kompilované binární soubory
    * soubory JS a CSS


Z důvodu chcete zahrnout `dotnet publish` výstupu příkazu v bitové kopii produkčního prostředí o jeho velikost na minimum.

Některé obrázky .NET Core sdílení vrstev mezi různých klíčových slov, takže stahování nejnovějších značka je poměrně jednoduchý proces. Pokud už máte starší verzi na svém počítači, tato architektura zmenšuje místo na disku potřebné.

Při obvyklých imagí používat více aplikací ve stejném počítači, je paměť sdílená mezi obvyklých imagí. Image se musí shodovat s ke sdílení.

## <a name="docker-image-variations"></a>Variace image dockeru

K dosažení cílů výše, poskytujeme varianty image v rámci [ `microsoft/dotnet` ](https://hub.docker.com/r/microsoft/dotnet/).

* `microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.1-sdk`) Tento obrázek obsahuje sady .NET Core SDK, která zahrnuje .NET Core a nástroje příkazového řádku (CLI). Tento obrázek mapuje **scénář vývoje**. Použít tuto bitovou kopii pro místní vývoj, ladění a testování částí. Tato image je také možné pro vaši **sestavení** scénáře. Pomocí `microsoft/dotnet:sdk` vždy obsahuje nejnovější verzi.

> [!TIP]
> Pokud si nejste jistí o vašim potřebám, kterou chcete použít `microsoft/dotnet:<version>-sdk` bitové kopie. Jako "de facto stane" image, je určený pro použití jako throw tokeny kontejneru (připojit svůj zdrojový kód a spustit kontejner pro spuštění vaší aplikace) a jako základní image k vytvoření další Image z.

* `microsoft/dotnet:<version>-runtime`: Tento obrázek obsahuje .NET Core (prostředí runtime a knihovny) a je optimalizovaná pro spouštění aplikací .NET Core **produkční**.

## <a name="alternative-images"></a>Alternativní imagí

Kromě optimalizované scénáře vývoje, sestavení a produkčním prostředí Nabízíme další Image:

* `microsoft/dotnet:<version>-runtime-deps`: **Runtime deps** bitová kopie obsahuje operační systém se všemi nativní závislosti vyžadované .NET Core. Tento obrázek pochází pro [samostatná aplikace](../deploying/index.md).

Nejnovější verze každého typu variant:

* `microsoft/dotnet` nebo `microsoft/dotnet:latest` (alias pro bitovou kopii sady SDK)
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a>Prozkoumejte ukázky

* [Tato ukázka ASP.NET Core Docker](https://github.com/dotnet/dotnet-docker/tree/master/samples/aspnetapp) ukazuje vzoru osvědčených postupů pro vytváření imagí Dockeru pro ASP.NET Core aplikace pro produkční prostředí. Ukázka funguje s kontejnery Windows i Linux.

* V této aplikaci .NET Core Docker ukázce vzoru osvědčených postupů pro [vytváření imagí Dockeru pro aplikace .NET Core pro produkční prostředí.](https://github.com/dotnet/dotnet-docker/tree/master/samples/dotnetapp)

## <a name="forward-the-request-scheme-and-original-ip-address"></a>Schéma požadavku a původní IP adresa

Proxy servery, nástroje pro vyrovnávání zatížení a jiných síťových zařízení často skryl informace o požadavku předtím, než dosáhne kontejnerizovanou aplikaci:

* Pokud požadavky HTTPS jsou směrovány přes proxy server pomocí protokolu HTTP, původní schéma (HTTPS) ztratí a musí předávat v hlavičce.
* Protože aplikace obdrží žádost z proxy serveru a není true zdroj na Internetu nebo podnikové sítě, musí v hlavičce předané původní IP adresa klienta.

Tyto informace mohou být důležité pro zpracování žádostí, například v přesměrování ověřování, generování odkazů, hodnocení zásad a informace o zeměpisné poloze klienta.

Přeposílat schéma a původní IP adresy pro kontejnerizované aplikace ASP.NET Core, používají předané Middleware záhlaví. Další informace najdete v tématu [konfigurace ASP.NET Core práci se servery proxy a nástroje pro vyrovnávání zatížení](/aspnet/core/host-and-deploy/proxy-load-balancer).

## <a name="your-first-aspnet-core-docker-app"></a>Vaše první aplikace ASP.NET Core Dockeru

Pro účely tohoto kurzu umožňuje aplikaci, kterou chceme dockerizace pomocí ukázkové aplikace ASP.NET Core Dockeru. Tato ukázková aplikace ASP.NET Core Docker ukazuje vzoru osvědčených postupů pro vytváření imagí Dockeru pro ASP.NET Core aplikace pro produkční prostředí. Ukázka funguje s kontejnery Windows i Linux.

Soubor Dockerfile vzorovým kódem se vytvoří image Dockeru aplikace ASP.NET Core na základě základní image Dockeru modulu Runtime ASP.NET Core.

Používá [Docker vícefázových sestavení funkce](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) na:

* sestavit ukázku v kontejneru na základě **větší** základní image Dockeru sestavení ASP.NET Core 
* zkopíruje výsledek poslední sestavení do image Dockeru na základě **menší** základní imagi modulu Runtime ASP.NET Core Dockeru

> [!NOTE]
> Sestavení image obsahuje potřebné nástroje pro vytváření aplikací, ale nikoli bitové kopie modulu runtime.

### <a name="prerequisites"></a>Požadavky

Sestavte a spusťte, nainstalujte následující položky:

#### <a name="net-core-21-sdk"></a>.NET core 2.1 SDK

* Nainstalujte [.NET Core SDK 2.1](https://www.microsoft.com/net/core).

* Pokud jste tak dosud neučinili, nainstalujte váš oblíbený editor kódu.

> [!TIP]
> Je potřeba nainstalovat editor kódu? Zkuste [sady Visual Studio](https://visualstudio.com/downloads)!

#### <a name="installing-docker-client"></a>Instalace klienta Dockeru

Nainstalujte [Docker 18.03](https://docs.docker.com/release-notes/docker-ce/) nebo novější klienta Dockeru.

Klienta Dockeru se dá nainstalovat ve:

* Linuxové distribuce

   * [CentOS](https://www.docker.com/docker-centos-distribution)

   * [Debian](https://www.docker.com/docker-debian)

   * [Fedora](https://www.docker.com/docker-fedora)

   * [Ubuntu](https://www.docker.com/docker-ubuntu)

* [macOS](https://docs.docker.com/docker-for-mac/)

* [Windows](https://docs.docker.com/docker-for-windows/).

#### <a name="installing-git-for-sample-repository"></a>Instalace Gitu pro ukázkové úložiště

* Nainstalujte [git](https://git-scm.com/download) Pokud budete chtít naklonujte úložiště.

### <a name="getting-the-sample-application"></a>Načítání ukázkové aplikace

Nejjednodušší způsob, jak získat ukázky je to klonováním [úložiště .NET Core Dockeru](https://github.com/dotnet/dotnet-docker) s úložištěm git, pomocí následujících pokynů: 

```console
git clone https://github.com/dotnet/dotnet-docker
```

Úložiště (je malé) můžete také stáhnout jako soubor zip z úložiště .NET Core Docker.

### <a name="run-the-aspnet-app-locally"></a>Místní spuštění aplikace ASP.NET

Pro referenční bod než jsme kontejnerizace aplikace, nejprve spusťte aplikaci místně.

Můžete sestavit a spustit aplikaci místně pomocí sady SDK .NET Core 2.1 pomocí následujících příkazů (pokyny předpokládají kořenovém adresáři úložiště):

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located
cd aspnetapp // project scope

dotnet run
```

Po spuštění aplikace, navštivte **http://localhost:5000** ve webovém prohlížeči.

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a>Sestavte a spusťte ukázku s prostředím Docker pro kontejnery Linuxu

Můžete sestavit a spustit ukázku v Dockeru pomocí kontejnerů Linuxu pomocí následujících příkazů (pokyny předpokládají kořenovém adresáři úložiště):

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located

docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!NOTE]
> `docker run` "-P" argument portu 5000 na místním počítači na port 80 v kontejneru mapy (formulář mapování portů je `host:container`). Další informace najdete v tématu [dockeru spustit](https://docs.docker.com/engine/reference/commandline/exec/) odkaz na parametry příkazového řádku.

Po spuštění aplikace, navštivte **http://localhost:5000** ve webovém prohlížeči.

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a>Sestavte a spusťte ukázku s kontejnery Docker pro Windows

Můžete sestavit a spustit ukázku v Dockeru pomocí kontejnerů Windows pomocí následujících příkazů (pokyny předpokládají kořenovém adresáři úložiště):

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located

docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> Je nutné na Přejít **IP adresu kontejneru** (nikoli http://localhost) v prohlížeči přímo při používání kontejnerů Windows. Můžete získat IP adresu vašeho kontejneru pomocí následujících kroků:

* Otevřete jiného příkazového řádku.
* Spustit `docker ps` zobrazte spuštěné kontejnery. Kontejner "aspnetcore_sample" by měl být existuje.
* Spustit `docker exec aspnetcore_sample ipconfig`.
* Zkopírujte IP adresu kontejneru a vložte do prohlížeče (například 172.29.245.43).

> [!NOTE]
> Docker exec podporuje identifikační kontejnery s názvem nebo hodnoty hash. Název (aspnetcore_sample) se používá v našem příkladu.

Podívejte se na následující příklad toho, jak získat IP adresu spuštěný kontejner Windows.

```console
docker exec aspnetcore_sample ipconfig

Windows IP Configuration

Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . : contoso.com
   Link-local IPv6 Address . . . . . : fe80::1967:6598:124:cfa3%4
   IPv4 Address. . . . . . . . . . . : 172.29.245.43
   Subnet Mask . . . . . . . . . . . : 255.255.240.0
   Default Gateway . . . . . . . . . : 172.29.240.1
```

> [!NOTE]
> Nový příkaz exec dockeru běží v spuštěný kontejner. Další informace najdete v tématu [docker exec odkaz](https://docs.docker.com/engine/reference/commandline/exec/) na parametry příkazového řádku.

Můžete vytvářet aplikace, která je připravená k nasazení do produkčního prostředí místně s použitím [dotnet publikovat](../tools/dotnet-publish.md) příkazu.

```console
dotnet publish -c Release -o published
```

> [!NOTE]
> - C verze argument sestavení aplikace v režimu vydání (výchozí hodnota je režim ladění). Další informace najdete v tématu [dotnet spusťte odkaz](../tools/dotnet-run.md) na parametry příkazového řádku.

Aplikaci můžete spustit na **Windows** pomocí následujícího příkazu.

```console
dotnet published\aspnetapp.dll
```

Aplikaci můžete spustit na **Linux** nebo **macOS** pomocí následujícího příkazu.

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a>Používané v tomto příkladu Imagí dockeru

Následující Image Dockeru se používají v této ukázce souboru dockerfile.

* `microsoft/dotnet:2.1-sdk`
* `microsoft/dotnet:2.1-aspnetcore-runtime`

Blahopřejeme! máte jen:
> [!div class="checklist"]
> * Dozvěděli jste se o imagích Dockeru rozhraní Microsoft .NET Core
> * Ukázkovou aplikaci do Dockerize je teď v ASP.NET Core
> * Spuštění ukázkové aplikace ASP.NET místně
> * Vytvořené a spustili ukázku s prostředím Docker pro kontejnery Linuxu
> * Vytvořené a spustili ukázku s kontejnery Docker pro Windows

**Další kroky**

Tady jsou některé další kroky, které si můžete:

* [Práce s nástroji Dockeru pro Visual Studio](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [Nasazování Imagí Dockeru ze služby Azure Container Registry do služby Azure Container Instances](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [Ladění ve Visual Studiu Code](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [Praktické ukázky sady Visual Studio pro Mac, kontejnery a kód bez serveru v cloudu](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [Začínáme s Dockerem a sady Visual Studio pro Mac testovacího prostředí](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

> [!NOTE]
> Pokud nemáte předplatné Azure, [zaregistrujte se ještě dnes](https://azure.microsoft.com/free/?b=16.48) pro bezplatný účet 30 dní a získat 200 USD v kreditech Azure pro vyzkoušení jakékoli kombinace služeb Azure.
