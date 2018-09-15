---
title: Úvod k .NET a Dockeru
description: Principy Dockeru a .NET Core
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.custom: mvc
ms.openlocfilehash: d578ec5a25dbb5de3c88386e212e68cf3b267749
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2018
ms.locfileid: "45638961"
---
# <a name="introduction-to-net-and-docker"></a>Úvod k .NET a Dockeru

Tento článek poskytuje úvod a koncepční znalosti potřebné k práci s využitím .NET v Dockeru.

## <a name="docker-packaging-your-apps-to-deploy-and-run-anywhere"></a>Docker: Vytváření balíčků aplikací k nasazení a spouštění kdekoli

[Docker](../../standard/microservices-architecture/container-docker-introduction/docker-defined.md) je otevřená platforma, která umožňuje vývojářům a správcům sestavení [image](https://docs.docker.com/glossary/?term=image), dodávat a spouštět distribuované aplikace v volně izolovaného prostředí volá [kontejneru](https://www.docker.com/what-container). Tento přístup umožňuje správu životního cyklu aplikací efektivní mezi vývojovým, dotazů a odpovědí a produkční prostředí.
 
[Platforma Docker](https://docs.docker.com/engine/docker-overview/#the-docker-platform) používá [modul Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) k rychlému sestavování a balíčky aplikací jako [imagí Dockeru](https://docs.docker.com/glossary/?term=image) vytvořené pomocí souborů, které jsou napsané v [souboru Dockerfile ](https://docs.docker.com/glossary/?term=Dockerfile) formát, který pak je nasadit a spustit [vrstvy kontejneru](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).

Můžete buď vytvořit svoje vlastní [Image na základě úrovní](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) jako soubory dockerfile nebo použijte existující z [registru](https://docs.docker.com/glossary/?term=registry), třeba [Docker Hubu](https://docs.docker.com/glossary/?term=Docker%20Hub).

[Vztah mezi kontejnery Dockeru, obrázky a registry](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md) je důležitý koncept při [navrhování a sestavování kontejnerizovaných aplikací nebo mikroslužeb](../../standard/microservices-architecture/architect-microservice-container-applications/index.md). Tento postup značně zkracuje dobu mezi vývojem a nasazení.

### <a name="further-reading-and-watching"></a>Další čtení (a sledování)

* [Kontejnery založené na Windows: vývoj moderních aplikací s ovládacím prvkem na podnikové úrovni.](https://www.youtube.com/watch?v=Ryx3o0rD5lY&feature=youtu.be)
* [Přehled dockeru](https://docs.docker.com/engine/docker-overview/)
* [Soubor Docker na kontejnery Windows](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [Osvědčené postupy pro psaní soubory Dockerfile](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/)
* [Vytváření Imagí Dockeru pro aplikace .NET Core](../docker/building-net-docker-images.md)


### <a name="getting-net-docker-images"></a>Získat Image .NET Dockeru

Image Dockeru oficiální .NET jsou vytvořené a optimalizované od Microsoftu. Jsou veřejně dostupné v Microsoft úložišť v Docker Hubu. Každé úložiště může obsahovat více bitových kopií, v závislosti na rozhraní .NET verze a verze operačního systému. Většina úložišť image poskytují rozsáhlé označování můžete vybrat konkrétní verzi rozhraní framework verze a operační systém (distribuce Linuxu nebo verze Windows).

## <a name="scenario-based-guidance"></a>Pokyny na základě scénáře

Záměrem Microsoftu je pro úložiště .NET je detailní a zaměřují se úložiště, které představují konkrétní scénář nebo úlohy.

`microsoft/aspnetcore` Bitové kopie jsou optimalizované pro aplikace ASP.NET Core na Docker, kontejnery můžete začít rychleji.

.NET Core imagí (`microsoft/dotnet`) jsou určené pro konzolové aplikace založené na .NET Core. Třeba dávkové procesy, Azure WebJobs a další scénáře konzoly používali optimalizované bitové kopie .NET Core.

Nejobvyklejšími vodorovné scénář pro používání aplikací Dockeru a .NET je pro produkční nasazení a hostování. Ukázalo se, že je jenom jedním scénářem produkce a ostatní jsou rovnoměrně užitečné. Tyto scénáře nejsou specifická pro .NET, ale mají používat pro většinu platforem pro vývojáře.

* **Nainstalujte překážek** – .NET si můžete vyzkoušet bez místní instalace. Stačí stáhněte image Dockeru s .NET v ní.

* **Vývoj v kontejneru** – což vývojovém a produkčním prostředí podobné (předcházení problémů, jako jsou globální stav počítače pro vývojáře) konzistentní prostředí můžete vyvíjet. Visual Studio Tools for Docker i umožňují spuštění kontejneru přímo ze sady Visual Studio.

* **Testování v kontejneru** – můžete otestovat v kontejneru, snižuje chyby způsobené nesprávně nakonfigurované prostředí nebo jiné změny zůstat z poslední sady testů.

* **Sestavení v kontejneru** – můžete vytvářet kód v kontejneru, takže není nutné správně nakonfigurovat sdílené sestavení počítače pro více prostředí, ale místo toho přesuňte do "BYOC" (přineste si vlastní kontejner) přístup.

* **Nasazení ve všech prostředích** – nasazujete bitovou kopii prostřednictvím všech vašich prostředích. Tento přístup snižuje chyby způsobené rozdíly konfigurací, obvykle změny chování bitové kopie pomocí externího konfigurace (například vložené proměnné).

[Obecné pokyny](../../standard/microservices-architecture/net-core-net-framework-containers/general-guidance.md) pro rozhodování mezi .NET Core a .NET Framework pro vývoj kontejnerů Dockeru.

### <a name="common-docker-development-scenarios"></a>Běžné scénáře vývoje Dockeru

#### <a name="net-core"></a>.NET Core

**.NET core prostředky**

 Vyberte si ukázky .NET Core, které odpovídají vaší scénáře, které vás zajímají. Všechny ukázky pokyny popisují, jak cílit na Windows nebo linuxového Dockeru imagí z hostitele Windows, Linux nebo macOS.

Ukázky použití .NET Core 2.0. Použití Docker [vícefázových sestavení](https://github.com/dotnet/announcements/issues/18) a [více architektury značky](https://github.com/dotnet/announcements/issues/14) spouštějte podle potřeby.

* [.NET core Image v Dockerhubu](https://hub.docker.com/r/microsoft/dotnet/)

* [Dockerizace aplikací .NET Core](https://docs.docker.com/engine/examples/dotnetcore/)

* V této ukázce .NET Core Docker jak [použít Docker ve vývojových procesech .NET Core](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev). Ukázka funguje s kontejnery Windows i Linux.

* V této aplikaci .NET Core Docker ukázce vzoru osvědčených postupů pro [vytváření imagí Dockeru pro aplikace .NET Core pro produkční prostředí.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod) Ukázka funguje s kontejnery Windows i Linux.

* To [.NET Core Docker ukázka](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) ukazuje vzor osvědčených postupů pro vytváření imagí Dockeru pro [samostatné aplikace .NET Core](../deploying/index.md). Použít nejmenší kontejneru produkční bez na výhodu plynoucí z [sdílení základní Image mezi kontejnery](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/). Však může sdílet nižších vrstvách Dockeru.

#### <a name="arm32--raspberry-pi"></a>ARM32 / Raspberry Pi

* [Oznámení sestavení .NET core Runtime ARM32](https://github.com/dotnet/announcements/issues/29)

* [ARM32 / Raspberry Pi .NET Core Image v Dockerhubu](https://hub.docker.com/r/microsoft/dotnet/)

* [ARM32 / Raspberry Pi .NET Core Docker ukázky na Githubu](https://github.com/dotnet/dotnet-docker-samples#arm32--raspberry-pi)

#### <a name="net-framework"></a>.NET Framework

* [Rozhraní .NET framework Image v Dockerhubu](https://hub.docker.com/r/microsoft/dotnet-framework/)

Toto úložiště obsahuje ukázky, které demonstrují různé konfigurace Dockeru rozhraní .NET Framework. Tyto Image můžete použít jako základ pro vlastní Image Dockeru.

**Rozhraní .NET framework 4.7**

[Dotnet-ukázkové rozhraní framework: 4.7](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) ukazuje základní "hello world" použití [rozhraní .NET Framework 4.7](../../framework/whats-new/index.md#v47). To se dozvíte, jak můžete sestavení a nasazení aplikace na přijímající [image dockeru pro .NET Framework 4.7](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-4.7/Dockerfile).

**Rozhraní .NET framework 4.6.2**

[Dotnet-ukázkové rozhraní framework: 4.6.2](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) ukazuje základní "hello world" použití [rozhraní .NET Framework 4.6.2](../../framework/whats-new/index.md#v462). To se dozvíte, jak můžete sestavení a nasazení aplikace na přijímající [image dockeru rozhraní .NET Framework 4.6.2](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-4.6.2/Dockerfile).

**Rozhraní .NET framework 3.5**

 [Dotnet-framework: 3.5 ukázka](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) ukazuje základní "hello world" použití [rozhraní .NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-3.5/dotnetapp-3.5/Dockerfile). To se dozvíte, jak můžete sestavit a nasadit projekt spoléhat na rozhraní .NET Framework 3.5 v Dockeru.

#### <a name="aspnet-core"></a>ASP.NET Core

* [Tato ukázka ASP.NET Core Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) ukazuje vzoru osvědčených postupů pro vytváření imagí Dockeru pro ASP.NET Core aplikace pro produkční prostředí. Ukázka funguje s kontejnery Windows i Linux.

* [ASP.NET Core Image v Dockerhubu](https://hub.docker.com/r/microsoft/aspnetcore-build/)

* [Imagí pro ASP.NET Core na Githubu](https://github.com/aspnet/aspnet-docker)

#### <a name="aspnet-framework"></a>Rozhraní ASP.NET

* [ASP.NET Framework Image v Dockerhubu](https://hub.docker.com/r/microsoft/aspnet/)

* [Aplikace webových formulářů ASP.NET v ukázce rozhraní .NET Framework 4.6.2](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/aspnetapp)

#### <a name="windows-communication-framework-wcf"></a>Windows Communication Framework (WCF)

* [Windows Communication Framework (WCF) Image v Dockerhubu](https://hub.docker.com/r/microsoft/wcf/)

* [Image Windows Communication Framework (WCF) na Githubu](https://github.com/microsoft/wcf-docker)

* [Ukázky Windows Communication Framework (WCF) Docker pomocí rozhraní .NET Framework 4.6.2](https://github.com/Microsoft/wcf-docker-samples)

#### <a name="internet-information-server-iis"></a>Internet Information Server (IIS)

* [Internet Information Server (IIS) Image v Dockerhubu](https://hub.docker.com/r/microsoft/iis/)

* [Obrázky Internet Information Server (IIS) na Githubu](https://github.com/microsoft/iis-docker)

### <a name="interact-with-other-microsoft-stack-container-images"></a>Pracovat s další Image kontejneru Microsoft zásobníku

#### <a name="microsoft-sql-server"></a>Microsoft SQL Server

* [Spusťte Microsoft SQL Server pro Linux 2017 image kontejneru s Docker rychlý start](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)

* [Microsoft SQL Server pro Linuxové Image v Dockerhubu](https://hub.docker.com/r/microsoft/mssql-server-linux/)

* [Image Microsoft SQL Server Express Edition pro kontejnery Windows na Dockerhubu](https://hub.docker.com/r/microsoft/mssql-server-windows-express/)

* [Image Microsoft SQL Server Developer Edition pro kontejnery Windows na Dockerhubu](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)

#### <a name="azure-devops-services-agent"></a>Agent Azure DevOps služby

* [Azure DevOps služby agenta Image v Dockerhubu](https://hub.docker.com/r/microsoft/vsts-agent/)

* [Azure DevOps služby agenta imagí na Githubu](https://github.com/Microsoft/vsts-agent-docker)

#### <a name="operations-management-suite-oms-linux-agent"></a>Operations Management Suite (OMS) linuxového agenta

* [Přehled Operations Management Suite (OMS) Linux agent](https://github.com/Microsoft/OMS-Agent-for-Linux/blob/master/docs/Docker-Instructions.md)

* [Operations Management Suite (OMS) Image v Dockerhubu](https://hub.docker.com/r/microsoft/oms/)

* [Operations Management Suite (OMS) Image na Githubu](https://github.com/Microsoft/OMS-docker)

#### <a name="microsoft-azure-command-line-interface-cli"></a>Rozhraní příkazového řádku Microsoft Azure (CLI)

* [Microsoft Azure rozhraní příkazového řádku (CLI) Image v Dockerhubu](https://hub.docker.com/r/microsoft/azure-cli/) 

* [Image Microsoft rozhraní příkazového řádku (CLI) Azure na Githubu](https://github.com/Azure/azure-cli#Docker)

> [!NOTE]
> Pokud nemáte předplatné Azure, [zaregistrujte se ještě dnes](https://azure.microsoft.com/free/?b=16.48) pro bezplatný účet 30 dní a získat 200 USD v kreditech Azure pro vyzkoušení jakékoli kombinace služeb Azure.

#### <a name="microsoft-azure-cosmos-db-emulator-windows-containers-only"></a>Emulátor služby Microsoft Azure Cosmos DB (pouze kontejnery Windows)

* [Emulátor služby Microsoft Azure Cosmos DB Image v Dockerhubu](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator) 

* [Pro místní vývoj a testování používat emulátor služby Azure Cosmos DB](/azure/cosmos-db/local-emulator#developing-with-the-emulator)

## <a name="exploring-the-rich-docker-development-ecosystem"></a>Zkoumání pestrého ekosystému Dockeru vývoj

Teď, když jste se dozvěděli o platforma Docker a různé imagí Dockeru, dalším krokem je prozkoumat pestrého ekosystému Dockeru. Jak nástroje Microsoftu doplňují vývojových zobrazí následující odkazy.

* [Společně pomocí .NET a Dockeru](https://blogs.msdn.microsoft.com/dotnet/2017/05/25/using-net-and-docker-together/)
* [Návrh a vývoj aplikací .NET více kontejnerů a založených na Mikroslužbách](../../standard/microservices-architecture/multi-container-microservice-net-applications/index.md)
* [Rozšíření sady Visual Studio Code Dockeru](https://code.visualstudio.com/docs/languages/dockerfile)
* [Zjistěte, jak používat Azure Service Fabric](/azure/service-fabric/index)
* [Service Fabric získávání ukázka Začínáme](https://azure.microsoft.com/resources/samples/service-fabric-dotnet-getting-started/)
* [Výhody kontejnerů Windows](/virtualization/windowscontainers/about/index#video-overview)
* [Práce s nástroji Dockeru pro Visual Studio](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker)
* [Nasazování Imagí Dockeru ze služby Azure Container Registry do služby Azure Container Instances](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [Ladění ve Visual Studiu Code](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container)
* [Praktické ukázky sady Visual Studio pro Mac, kontejnery a kód bez serveru v cloudu](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [Začínáme s Dockerem a sady Visual Studio pro Mac testovacího prostředí](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

## <a name="next-steps"></a>Další kroky

* [Základy Dockeru s .NET Core](docker-basics-dotnet-core.md)
* [Vytváření Imagí Dockeru .NET Core](building-net-docker-images.md)
