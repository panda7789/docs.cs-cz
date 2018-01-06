---
title: "Úvod do rozhraní .NET a Docker"
description: Principy Docker a .NET Core
keywords: "Rozhraní .NET, rozhraní .NET core, Docker"
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
manager: wpickett
ms.custom: mvc
ms.workload: dotnetcore
ms.openlocfilehash: e5f420df6c5cf4f9d517dd6ce2c6b33d3d3479d1
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2018
---
# <a name="introduction-to-net-and-docker"></a>Úvod do rozhraní .NET a Docker

Tento článek poskytuje úvod a koncepční základní informace o práci s .NET v nástroji Docker.

## <a name="docker-packaging-your-apps-to-deploy-and-run-anywhere"></a>Docker: Zabalení aplikace nasadit a spustit odkudkoli

[Docker](../../standard/microservices-architecture/container-docker-introduction/docker-defined.md) je otevřená platforma, která umožňuje vývojáři a správci sestavení [bitové kopie](https://docs.docker.com/glossary/?term=image), odeslání a spustit distribuované aplikace v prostředí volně izolované názvem [kontejneru](https://www.docker.com/what-container). Tento přístup umožňuje správu životního cyklu aplikací efektivní mezi vývoj, QA a provozní prostředí.
 
[Docker platformy](https://docs.docker.com/engine/docker-overview/#the-docker-platform) používá [modulu Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) rychle vytvářet a balíček aplikace jako [imagí Dockeru](https://docs.docker.com/glossary/?term=image) vytvořený soubory, které jsou napsané v [soubor Docker ](https://docs.docker.com/glossary/?term=Dockerfile) formátu, který pak je nasadit a spustit [vrstvený kontejneru](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).

Můžete buď vytvořit vlastní [na základě bitové kopie](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) jako dockerfiles nebo použijte existující z [registru](https://docs.docker.com/glossary/?term=registry), například [úložiště Docker Hub](https://docs.docker.com/glossary/?term=Docker%20Hub).

[Vztah mezi Docker kontejnery, Image a registrech](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md) je důležité koncept při [architektury a sestavování kontejnerové aplikace nebo mikroslužeb](../../standard/microservices-architecture/architect-microservice-container-applications/index.md). Tento přístup výrazně zkracuje doba mezi vývoj a nasazení.

### <a name="further-reading-and-watching"></a>Další čtení (a sledování)

* [Kontejnery založené na systému Windows: vývoj moderních aplikací pomocí řízení podnikové úrovni.](https://www.youtube.com/watch?v=Ryx3o0rD5lY&feature=youtu.be)
* [Přehled docker](https://docs.docker.com/engine/docker-overview/)
* [Soubor Docker kontejnerům Windows](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile.md)
* [Osvědčené postupy pro psaní Dockerfiles](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/)
* [Vytváření Imagí Dockeru pro aplikace .NET Core](../docker/building-net-docker-images.md)


### <a name="getting-net-docker-images"></a>Získávání Imagí Dockeru rozhraní .NET

Oficiální Docker .NET bitové kopie se vytváří a optimalizované společností Microsoft. Jsou veřejně dostupné v Microsoft úložiště na úložiště Docker Hub. Každý úložiště může obsahovat více bitových kopií, v závislosti na rozhraní .NET verze a na verze operačního systému. Většina úložiště image poskytují rozsáhlé označení vám pomohou vybrat konkrétní framework verze a operační systém (verze Windows nebo Linux distro).

## <a name="scenario-based-guidance"></a>Scénář na základě pokyny

Záměr společnosti Microsoft pro rozhraní .NET úložiště je získat podrobné a zaměřují se úložiště, které představují konkrétní scénář nebo zatížení.

`microsoft/aspnetcore` Bitové kopie jsou optimalizované pro aplikace ASP.NET Core na Docker, takže kontejnery můžete spustit rychlejší.

Obrázky .NET Core (`microsoft/dotnet`) jsou určené pro konzolu aplikace založené na .NET Core. Například procesy batch, Azure WebJobs a scénáře konzoly by měl používat optimalizované Image .NET Core.

Nejobvyklejší vodorovné scénář pro použití aplikací Docker a .NET je pro produkční nasazení a hostování. Ukazuje se, že produkční je jenom jedním scénářem, a další ty, které jsou rovnoměrně užitečné. Tyto scénáře nejsou specifické pro rozhraní .NET, ale měli použít pro většině platforem developer.

* **Nainstalujte nízkým třením** – .NET můžete vyzkoušet bez místní instalace. Stáhněte pouze bitovou kopii Docker s .NET v ní.

* **Vývoj v kontejneru** – můžete vyvíjet v prostředí konzistentní provedení vývoj a produkční prostředí podobné (zabraňující problémy jako globální stav na počítačích vývojářů). Nástroje sady Visual Studio pro Docker i umožňují spusťte kontejner přímo ze sady Visual Studio.

* **Testování v kontejneru** – můžete otestovat v kontejneru, snižuje chyby způsobené nesprávnou konfigurací prostředí nebo jiné změny zanechat z poslední test.

* **Sestavení v kontejneru** – můžete vytvořit kód v kontejneru, takže není nutné správně nakonfigurovat počítačů sdílené sestavení pro prostředí s více, ale místo toho přesunout do "BYOC" (přineste si vlastní kontejner) přístup.

* **Nasazení ve všech prostředích** – můžete nasadit bitovou prochází všechna prostředí. Tento přístup snižuje chyby způsobené konfigurace rozdílů, obvykle změny chování bitovou kopii prostřednictvím externí konfigurace (například vloženého prostředí proměnné).

[Obecné pokyny](../../standard/microservices-architecture/net-core-net-framework-containers/general-guidance.md) rozhodování mezi .NET Core a rozhraní .NET Framework pro vývoj kontejner Docker.

### <a name="common-docker-development-scenarios"></a>Běžné scénáře vývoj Docker

#### <a name="net-core"></a>.NET Core

**.NET core prostředky**

 Vyberte ukázky .NET Core splňující vaše scénáře, které vás zajímají. Všechny ukázkové pokyny popisují, jak cílových bitových kopií systému Windows nebo Linux Docker ze systému Windows, Linux nebo systému macOS hostitelů.

Ukázky použití .NET Core 2.0. Používají Docker [více fáze sestavení](https://github.com/dotnet/announcements/issues/18) a [více architektury značky](https://github.com/dotnet/announcements/issues/14) podle potřeby.

* [.NET core Image na DockerHub](https://hub.docker.com/r/microsoft/dotnet/)

* [Dockerize aplikace .NET Core](https://docs.docker.com/engine/examples/dotnetcore/)

* Tento příklad .NET Core Docker znázorňuje postup [pomocí Docker ve vývojových procesech .NET Core](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev). Ukázka funguje s kontejnery Linux a Windows.

* Tento příklad .NET Core Docker znázorňuje osvědčených postupů vzor [vytváření imagí Dockeru pro aplikace .NET Core pro produkční prostředí.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod) Ukázka funguje s kontejnery Linux a Windows.

* To [ukázka .NET Core Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) ukazuje osvědčených postupů vzor pro vytváření imagí Dockeru pro [nezávislý aplikace .NET Core](../deploying/index.md). Použít pro kontejner nejmenší provozní bez výhody z [sdílení základní Image mezi kontejnery](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/). Nižších vrstvách Docker však může sdílet.

#### <a name="arm32--raspberry-pi"></a>ARM32 / malin pí

* [.NET core Runtime ARM32 sestavení oznámení](https://github.com/dotnet/announcements/issues/29)

* [ARM32 / malin platformy .NET Core bitové kopie na DockerHub](https://hub.docker.com/r/microsoft/dotnet/)

* [ARM32 / Malinová platformy .NET Core Docker ukázky na Githubu](https://github.com/dotnet/dotnet-docker-samples#arm32--raspberry-pi)

#### <a name="net-framework"></a>.NET Framework

* [Rozhraní .NET framework Image na DockerHub](https://hub.docker.com/r/microsoft/dotnet-framework/)

Toto úložiště obsahovat ukázky, která ukazují různých konfiguracích Docker rozhraní .NET Framework. Tyto Image můžete použít jako základ imagí Dockeru.

**Rozhraní .NET framework 4.7**

[Dotnet – ukázka framework: 4.7](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) ukazuje základní "text hello world" použití [4.7 rozhraní .NET Framework](../../framework/whats-new/index.md#v47). Ho se dozvíte, jak můžete sestavit a nasazení aplikace spoléhat na [rozhraní .NET Framework 4.7 docker image](https://github.com/Microsoft/dotnet-framework-docker/blob/master/4.7/Dockerfile).

**Rozhraní .NET framework 4.6.2**

[Dotnet – ukázka framework: 4.6.2](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) ukazuje základní "text hello world" použití [rozhraní .NET Framework 4.6.2](../../framework/whats-new/index.md#v462). Ho se dozvíte, jak můžete sestavit a nasazení aplikace spoléhat na [rozhraní .NET Framework 4.6.2 docker image](https://github.com/Microsoft/dotnet-framework-docker/tree/master/4.6.2).

**Rozhraní .NET framework 3.5**

 [Dotnet – ukázka framework: 3.5](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) ukazuje základní "text hello world" použití [rozhraní .NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker/tree/master/3.5). Ho ukazuje, jak můžete sestavit a nasazení projektu spoléhat na rozhraní .NET Framework 3.5 v Docker.

#### <a name="aspnet-core"></a>ASP.NET Core

* [Tato ukázka ASP.NET Core Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) ukazuje osvědčených postupů vzor pro vytváření imagí Dockeru pro ASP.NET Core aplikace pro produkční prostředí. Ukázka funguje s kontejnery Linux a Windows.

* [ASP.NET Core Image na DockerHub](https://hub.docker.com/r/microsoft/aspnetcore-build/)

* [ASP.NET Core bitové kopie na Githubu](https://github.com/aspnet/aspnet-docker)

#### <a name="aspnet-framework"></a>Rozhraní ASP.NET

* [Rozhraní ASP.NET Image na DockerHub](https://hub.docker.com/r/microsoft/aspnet/)

* [Aplikace webových formulářů ASP.NET na rozhraní .NET Framework 4.6.2 vzorku](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/aspnetapp)

#### <a name="windows-communication-framework-wcf"></a>Windows Communication Framework (WCF)

* [Image Windows Communication Framework (WCF) na DockerHub](https://hub.docker.com/r/microsoft/wcf/)

* [Bitové kopie služby Windows Communication Framework (WCF) na Githubu](https://github.com/microsoft/iis-docker)

* [Ukázky Windows Communication Framework (WCF) Docker pomocí rozhraní .NET Full Framework 4.6.2](https://github.com/Microsoft/wcf-docker-samples)

#### <a name="internet-information-server-iis"></a>Internet Information Server (IIS)

* [Image Internet Information Server (IIS) na DockerHub](https://hub.docker.com/r/microsoft/iis/)

* [Obrázky Internet Information Server (IIS) na Githubu](https://github.com/microsoft/wcf-docker)

### <a name="interact-with-other-microsoft-stack-container-images"></a>Komunikovat s jiných Microsoft zásobníku kontejneru obrázků

#### <a name="microsoft-sql-server"></a>Microsoft SQL Server

* [Spusťte Microsoft SQL Server pro Linux 2017 kontejneru image s Docker rychlý start](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)

* [Microsoft SQL Server pro Linux bitové kopie na DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [Microsoft SQL serveru pro Windows kontejnery Image na DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [Microsoft SQL Server Express Edition bitových kopií pro Windows kontejnerů v DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows-express/)

* [Microsoft SQL Server Developer Edition bitových kopií pro Windows kontejnerů v DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)

#### <a name="visual-studio-team-services-vsts-agent"></a>Visual Studio Team Services (služby VSTS) agenta

* [Visual Studio Team Services (služby VSTS) agenta Image na DockerHub](https://hub.docker.com/r/microsoft/vsts-agent/)

* [Visual Studio Team Services (služby VSTS) agenta obrázků na Githubu](https://github.com/Microsoft/vsts-agent-docker)

#### <a name="operations-management-suite-oms-linux-agent"></a>Agent nástroje Operations Management Suite (OMS) Linux

* [Přehled agenta Operations Management Suite (OMS) Linux](https://github.com/Microsoft/OMS-Agent-for-Linux/blob/master/docs/Docker-Instructions.md#overview)

* [Operations Management Suite (OMS) Image na DockerHub](https://hub.docker.com/r/microsoft/vsts-agent/)

* [Obrázky Operations Management Suite (OMS) na Githubu](https://github.com/Microsoft/OMS-docker)

#### <a name="microsoft-azure-command-line-interface-cli"></a>Rozhraní příkazového řádku Microsoft Azure (CLI)

* [Microsoft Azure rozhraní příkazového řádku (CLI) Image na DockerHub](https://hub.docker.com/r/microsoft/azure-cli/) 

* [Microsoft Azure rozhraní příkazového řádku (CLI) bitové kopie na Githubu](https://github.com/Microsoft/OMS-docker)

> [!NOTE]
> Pokud nemáte předplatné Azure, [Přihlaste se ještě dnes](https://azure.microsoft.com/free/?b=16.48) bezplatný účet 30 dnů a 200 USD get v kredity Azure můžete vyzkoušet na libovolnou kombinaci služby Azure.

#### <a name="microsoft-azure-cosmos-db-emulator-windows-containers-only"></a>Emulátor systému Cosmos DB Microsoft Azure (pouze Windows kontejnery)

* [Microsoft Azure Cosmos DB emulátoru Image na DockerHub](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator) 

* [Použití emulátoru DB Cosmos Azure pro místní vývoj a testování](/azure/cosmos-db/local-emulator.md#developing-with-the-emulator)

## <a name="exploring-the-rich-docker-development-ecosystem"></a>Zkoumání bohatý ekosystém vývoj Docker

Teď, když jste se naučili o Docker platformy a jiné imagí Dockeru, dalším krokem je prozkoumat bohatý ekosystém Docker. Následující odkazy vám ukážou, jak nástroje Microsoft doplňují vývoj kontejneru.

* [Společně pomocí rozhraní .NET a Docker](https://blogs.msdn.microsoft.com/dotnet/2017/05/25/using-net-and-docker-together/)
* [Návrh a vývoj aplikace s více kontejneru a na základě Mikroslužbu .NET](../../standard/microservices-architecture/multi-container-microservice-net-applications/index.md)
* [Rozšíření sady Visual Studio Code Docker](https://code.visualstudio.com/docs/languages/dockerfile)
* [Naučte se používat Azure Service Fabric](/azure/service-fabric/index.md)
* [Ukázka spuštění získávání Service Fabric](https://azure.microsoft.com/resources/samples/service-fabric-dotnet-getting-started/)
* [Výhody Windows kontejnery](/virtualization/windowscontainers/about/index.md#video-overview)
* [Práce s nástroji Visual Studio Docker](/aspnet/core/publishing/visual-studio-tools-for-docker/index.md)
* [Nasazení bitových kopií Docker z registru kontejner Azure do Azure kontejner instancí](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [Ladění pomocí kódu v sadě Visual Studio](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container)
* [Načítání rukou pomocí sady Visual Studio pro Mac, kontejnery a bez serveru kódu v cloudu](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [Začínáme s Docker a Visual Studio pro Mac testovacího prostředí](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

## <a name="next-steps"></a>Další kroky

* [Základy Dockeru s .NET Core](docker-basics-dotnet-core.md)
* [Vytváření bitových kopií Docker .NET Core](building-net-docker-images.md)
\
