---
title: Terminologie dockeru
description: Přečtěte si některé základní terminologii, která byla použita každý den, při práci s Dockerem.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 1514a2199efe52a411f61649fc21e906bba5b13c
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56218720"
---
# <a name="docker-terminology"></a>Terminologie dockeru

Tato část uvádí termíny a definice, se kterými jste byste se měli seznámit před hlubší seznamovat do Docker (pro další definice, najdete v článku rozsáhlé [Glosář](https://docs.docker.com/glossary/) poskytované Dockeru na <https://docs.docker.com/glossary/>:

-   **Image kontejneru** balíčku se všemi závislostmi a informace potřebné k vytvoření kontejneru. Obrázek zahrnuje všechny závislosti (například rozhraní) a nasazení a konfiguraci pro modul runtime kontejneru. Obvykle bitovou kopii je odvozena z více základních imagí, že jsou vrstvy skládaný jednoho nad druhým k tvoří systém souborů kontejneru. Obrázek je neměnný po jeho vytvoření.

-   **Kontejner** instance image Dockeru. Představuje kontejner modulu runtime pro jednu aplikaci, proces nebo službu. Zahrnuje obsah image Dockeru, běhové prostředí a standardní sadu pokynů. Při škálování služby, vytvoření více instancí kontejneru ze stejné image. Nebo úlohu služby batch můžete vytvořit několik kontejnerů ze stejné image, předávání různých parametrů pro každou instanci.

-   **Značka** popisek, který můžete použít na Image tak, aby různých bitových kopií nebo verzí stejnou bitovou kopii (v závislosti na číslo verze nebo cílové prostředí) lze identifikovat a označit.

-   **Soubor Dockerfile** textový soubor, který obsahuje pokyny, jak sestavit image Dockeru.

-   **Sestavení** akce vytvoření image kontejneru na základě informace a jeho soubor Dockerfile, jakož i další soubory ve složce, ve kterém image se sestavuje poskytnutému kontextu. Vytvoření imagí pomocí příkazu docker sestavení Dockeru.

-   **Úložišti (úložišti)** kolekci souvisejících imagí Dockeru, které jsou označené značkou, který označuje verzi image. Některá úložiště obsahovat více variant konkrétní image, jako je například image obsahující bitovou kopii obsahující pouze moduly runtime (světlejší), sady SDK (těžší), a tak dále. Tyto varianty, mohou být označeny značky. Jediné úložiště může obsahovat variant, platformy, jako jsou image Linuxu a Windows image.

-   **Registru** služba, která poskytuje přístup k úložištím. Je výchozím nastavení registru pro největší veřejné image [Docker Hubu](https://hub.docker.com/) (vlastněné Dockeru jako organizace). Registru obvykle obsahuje úložiště z několika týmů. Podniky mají často privátních registrů k ukládání a správě imagí, které jste vytvořili. *Služba Azure Container Registry* je další příklad.

-   **Docker Hubu** veřejného registru k nahrání imagí a práci s nimi. Docker Hubu poskytuje Docker hostování image, veřejných nebo privátních registrů, aktivačních procedur sestavení a webhooky a integraci s z Githubu nebo Bitbucketu.

-   **Služba Azure Container Registry** prostředek veřejné pro práci s imagí Dockeru a jeho komponent v Azure. To poskytuje registr, která je blízko svá nasazení v Azure díky tomu kontrolu přístupu, aby bylo možné používat skupiny Azure Active Directory a oprávnění.

-   **Docker Trusted Registry (DTR)** A služba registru Dockeru (od Dockeru), který můžete nainstalovat na místním tak, aby se nachází v rámci organizace datové centrum a síť. Je vhodné pro privátních imagí, které se mají spravovat v rámci podniku. Docker Trusted Registry je součástí produktu Docker Datacenter. Další informace najdete v části [ https://docs.docker.com/docker-trusted-registry/overview/ ](https://docs.docker.com/docker-trusted-registry/overview/).

-   **Docker Community Edition (CE)** nástroje pro vývoj pro Windows a macOS pro sestavování, spouštění a testování kontejnery místně. Docker CE pro Windows poskytuje vývojové prostředí pro kontejnery Windows i Linux. Je na základě hostitele linuxového Dockeru na Windows [Hyper-V](https://www.microsoft.com/en-us/server-cloud/solutions/virtualization.aspx) virtuálního počítače. Hostitel pro kontejnery Windows je přímo založena na Windows. Docker CE for Mac je založená na platformě Apple hypervisoru a [xhyve hypervisoru](https://github.com/mist64/xhyve), který poskytuje linuxového Dockeru hostitele virtuálního počítače na Mac OS X. Docker CE pro Windows a pro Mac nahradí nástrojů Dockeru, které se týkaly Oracle VirtualBox.

-   **Docker Enterprise Edition (EE)** na podnikové úrovni verzi nástroje Dockeru pro vývoj pro Linux a Windows.

-   **Compose** nástroj příkazového řádku a YAML soubor formátu s metadaty pro definování a spouštění vícekontejnerových aplikací. Můžete definovat jednu aplikaci založené na více bitových kopií s nejméně jeden soubor .yml, které mohou přepsat hodnoty v závislosti na prostředí. Po vytvoření definice můžete nasadit celý vícekontejnerových aplikací pomocí jediného příkazu (docker-compose up), která vytvoří kontejner na image na hostitele Dockeru.

-   **Cluster** kolekce hostitelů Docker vystavena jako by byly jednoho virtuálního hostitele Docker tak, aby aplikaci je možné škálovat na více instancí služeb rozděleny mezi více hostitelích v clusteru. Můžete vytvořit clustery Dockeru pomocí Docker Swarm, Mesosphere DC/OS, Kubernetes a Azure Service Fabric. (Pokud používáte Docker Swarm pro správu clusteru, je obvykle odkazovat do clusteru jako *swarm* namísto clusteru.)

-   **Orchestrator** nástroj, který zjednodušuje správu clusterů a hostitelů Docker. Pomocí orchestrátorů, můžete spravovat jejich bitové kopie, kontejnerů a hostitele přes rozhraní příkazového řádku nebo grafické uživatelské rozhraní. Můžete spravovat sítě kontejnerů, konfigurace, Vyrovnávání zatížení, zjišťování služby, vysokou dostupnost, konfigurace hostitele Docker a další. Orchestrátor je zodpovědný za spouštění, distribuci, škálování a opravy úloh v kolekci uzlů. Produkty orchestrator jsou obvykle stejné produkty, které poskytují clusteru infrastruktury, jako je Mesosphere DC/OS, Kubernetes, Docker Swarm a Azure Service Fabric.

>[!div class="step-by-step"]
>[Předchozí](what-is-docker.md)
>[další](docker-containers-images-and-registries.md)