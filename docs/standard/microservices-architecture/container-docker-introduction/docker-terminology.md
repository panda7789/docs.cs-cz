---
title: Terminologie dockeru
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Terminologie dockeru
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: 2229599ab2fdc008c1668fb317f6cbe7dae95380
ms.sourcegitcommit: dcc8feeff4718664087747529638ec9b47e65234
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/31/2019
ms.locfileid: "55479994"
---
# <a name="docker-terminology"></a>Terminologie dockeru

Tato část uvádí termíny a definice, měli byste se seznámit s před získáním Dockeru věnovat podrobněji. Další definice, najdete v článku rozsáhlé [Glosář](https://docs.docker.com/glossary/) poskytované Dockeru.

**Image kontejneru**: Balíček se závislostí a informace potřebné k vytvoření kontejneru. Obrázek zahrnuje všechny závislosti (například rozhraní) plus konfigurace nasazení a spuštění pro modul runtime kontejneru. Image obvykle, je odvozena z více základních imagí, které jsou vrstvy sebe k systému souborů kontejneru. Obrázek je neměnný po jeho vytvoření.

**Soubor Dockerfile**: Textový soubor, který obsahuje pokyny, jak sestavit image Dockeru. Je to jako dávkový skript, první řádek začínající uvádí základní image a pak postupujte podle pokynů k instalaci požadované programy, zkopírujte soubory a tak dále, dokud se nedostanete pracovního prostředí budete potřebovat.

**Sestavení**: Akce sestavení image kontejneru na základě informací a kontext poskytované jeho soubor Dockerfile a navíc další soubory ve složce, ve kterém je postavená na obrázku. Můžete vytvořit Image pomocí Dockeru **sestavení dockeru** příkazu. 

**kontejner**: Instance image Dockeru. Kontejner představuje spuštění jedné aplikace, procesu nebo služby. Zahrnuje obsah image Dockeru, spouštěcí prostředí a standardní sadu pokynů. Při škálování služby, vytvoření více instancí kontejneru ze stejné image. Nebo úlohu služby batch můžete vytvořit několik kontejnerů ze stejné image, předávání různých parametrů pro každou instanci.

**Svazky**: Nabízí s možností zápisu systému souborů, které kontejner může použít. Protože bitové kopie jsou jen pro čtení, ale většina aplikací potřebují k zápisu do systému souborů, přidejte svazky zapisovatelné vrstvě nad image kontejneru, aby programy přístup pro zápis systému souborů. Program nebude vědět, přistupuje vrstvami systému souborů, ale pouze ze systému souborů jako obvykle. Svazky v hostitelském systému za provozu a jsou spravované pomocí Dockeru.

**Značka**: Označit nebo popisku, který můžete použít na Image tak, aby lze identifikovat různých bitových kopií nebo verzí stejnou bitovou kopii (v závislosti na číslo verze nebo cílové prostředí).

**Vícefázových sestavení**: Je funkce, od Dockeru 17.05 nebo vyšší, pomáhá omezit velikost finální bitové kopie. V několika větách vícefázových sestavení používáte, třeba velký základní image obsahující sadu SDK pro kompilaci a publikování aplikace a pak pomocí složky pro publikování s malé pouze modul runtime základní image, k vytvoření mnohem menší finální bitové kopie

**Úložišti (úložišti)**: Kolekce související imagí Dockeru, označené značkou, který označuje verzi image. Některá úložiště obsahovat více variant konkrétní image, jako je například obrázek (těžší), sady SDK obsahující bitovou kopii obsahující pouze moduly runtime (světlejší), atd. Tyto varianty, mohou být označeny značky. Jediné úložiště může obsahovat variant, platformy, jako jsou image Linuxu a Windows image.

**Registru**: Služba, která poskytuje přístup k úložištím. Je výchozím nastavení registru pro největší veřejné image [Docker Hubu](https://hub.docker.com/) (vlastněné Dockeru jako organizace). Registru obvykle obsahuje úložiště z několika týmů. Podniky mají často privátních registrů k ukládání a správě imagí, které jste vytvořili. Služba Azure Container Registry je další příklad.

**Více architektury image**: Více architektury, je funkce, která zjednodušuje výběr příslušné bitové kopie, podle platformy, na kterém je spuštěný Docker, třeba když soubor Dockerfile požádá o základní image **od Microsoftu nebo dotnet:2.2-sdk** z ve skutečnosti získá registru **2.2-sdk-nanoserver-1709**, **2.2-sdk-nanoserver-1803**, **2.2-sdk-nanoserver-1809** nebo **2.2-sdkalpine**, v závislosti na operačním systému a verze se spuštěným Dockerem.

**Docker Hubu**: Veřejného registru k nahrání imagí a práci s nimi. Docker Hubu poskytuje Docker hostování image, veřejných nebo privátních registrů, aktivačních procedur sestavení a webhooky a integraci s z Githubu nebo Bitbucketu.

**Azure Container Registry**: Prostředek veřejné pro práci s imagí Dockeru a jeho komponent v Azure. To poskytuje registr, která je blízko svá nasazení v Azure díky tomu kontrolu přístupu, aby bylo možné používat skupiny Azure Active Directory a oprávnění.

**Docker Trusted Registry (DTR)**: Služba registru Dockeru (od Dockeru), která může být nainstalovaný místně, takže umístěná kdekoli v rámci organizace datové centrum a síť. Je vhodné pro privátních imagí, které se mají spravovat v rámci podniku. Docker Trusted Registry je součástí produktu Docker Datacenter. Další informace najdete v tématu [Docker Trusted Registry (DTR)](https://docs.docker.com/docker-trusted-registry/overview/).

**Docker Community Edition (CE)**: Nástroje pro vývoj pro Windows a macOS pro sestavování, spouštění a testování kontejnery místně. Docker CE pro Windows poskytuje vývojové prostředí pro kontejnery Windows i Linux. Je na základě hostitele linuxového Dockeru na Windows [Hyper-V](https://www.microsoft.com/cloud-platform/server-virtualization) virtuálního počítače. Hostitel pro kontejnery Windows je přímo založena na Windows. Docker CE for Mac je založená na platformě Apple hypervisoru a [xhyve hypervisoru](https://github.com/mist64/xhyve), který poskytuje linuxového Dockeru hostitele virtuálního počítače na Mac OS X. Docker CE pro Windows a pro Mac nahradí nástrojů Dockeru, který byl založen na Oracle VirtualBox.

**Docker Enterprise Edition (EE)**: Verzi celého podniku nástroje Dockeru pro vývoj pro Linux a Windows.

**Compose**: Nástroj pro příkazový řádek a YAML soubor formátu s metadaty pro definování a spouštění vícekontejnerových aplikací. Můžete definovat jednu aplikaci založené na více bitových kopií s nejméně jeden soubor .yml, které mohou přepsat hodnoty v závislosti na prostředí. Po vytvoření definice můžete nasadit celý vícekontejnerové aplikace pomocí jediného příkazu (docker-compose up), která vytvoří kontejner na image na hostitele Dockeru.

**Cluster**: Soubor hostitelů Docker vystavena jako by šlo jednoho virtuálního hostitele Docker, tak, aby aplikaci je možné škálovat na více instancí služeb rozděleny mezi více hostitelích v clusteru. Clustery docker lze vytvořit pomocí Kubernetes, Azure Service Fabric, Docker Swarm a Mesosphere DC/OS.

**Orchestrator**: Nástroj, který zjednodušuje správu clusterů a hostitelů Docker. Orchestrátory umožňují spravovat jejich imagí kontejnerů a hostitele přes rozhraní příkazového řádku (CLI) nebo grafického uživatelského rozhraní. Můžete spravovat sítě kontejnerů, konfigurace, Vyrovnávání zatížení, zjišťování služby, vysokou dostupnost, konfigurace hostitele Docker a další. Orchestrátor je zodpovědný za spouštění, distribuci, škálování a opravy úloh v kolekci uzlů. Produkty orchestrator jsou obvykle stejné produkty, které poskytují infrastrukturu clusteru, jako je Kubernetes a Azure Service Fabric, mezi další nabídky na trhu. 

>[!div class="step-by-step"]
>[Předchozí](docker-defined.md)
>[další](docker-containers-images-registries.md)