---
title: Terminologie Dockeru
description: Naučte se některé základní terminologie, která se používá každý den při práci s Docker.
ms.date: 02/15/2019
ms.openlocfilehash: c352bf7235e8a3dc2d52bbbfe4390863fff9991f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295678"
---
# <a name="docker-terminology"></a>Terminologie Dockeru

V této části jsou uvedeny termíny a definice, které byste měli znát, než se dostanete hlouběji do Dockeru. Další definice naleznete v rozsáhlém [glosáři](https://docs.docker.com/glossary/) poskytovaném dockerem.

**Image kontejneru**: Balíček se všemi závislostmi a informacemi potřebnými k vytvoření kontejneru. Bitová kopie obsahuje všechny závislosti (například architektury) plus konfigurace nasazení a spuštění, které mají být použity v době runtime kontejneru. Obraz obvykle pochází z více základních obrazů, které jsou vrstvy naskládané nad sebou a tvoří souborový systém kontejneru. Obrázek je neměnný, jakmile byl vytvořen.

**Dockerfile**: Textový soubor, který obsahuje pokyny, jak vytvořit image Dockeru. Je to jako dávkový skript, první řádek uvádí základní bitovou kopii a pak postupujte podle pokynů k instalaci požadovaných programů, kopírování souborů a tak dále, dokud nezískáte pracovní prostředí, které potřebujete.

**Sestavení**: Akce vytváření image kontejneru na základě informací a kontextu poskytované jeho Dockerfile, plus další soubory ve složce, kde je vytvořena image. Můžete vytvářet image **`docker build`** pomocí příkazu Docker.

**Kontejner**: Instance image Dockeru. Kontejner představuje spuštění jedné aplikace, procesu nebo služby. Skládá se z obsahu image Dockeru, prostředí spuštění a standardní sady instrukcí. Při škálování služby vytvoříte více instancí kontejneru ze stejné bitové kopie. Nebo dávková úloha můžete vytvořit více kontejnerů ze stejného obrázku, předávání různých parametrů pro každou instanci.

**Svazky**: Nabídněte zapisovatelný souborový systém, který může kontejner používat. Vzhledem k tomu, že obrázky jsou jen pro čtení, ale většina programů musí zapisovat do souborového systému, svazky přidávají zapisovatelnou vrstvu nad obraz kontejneru, takže programy mají přístup k zapisovatelnému souborovému systému. Program neví, že přistupuje k vrstvené souborové soustavě, je to jen souborový systém jako obvykle. Svazky jsou aktivní v hostitelském systému a jsou spravovány Dockerem.

**Značka**: Značka nebo popisek, který můžete použít na obrázky, aby bylo možné identifikovat různé obrázky nebo verze stejného obrázku (v závislosti na čísle verze nebo cílovém prostředí).

**Vícestupňové sestavení**: Je funkce, protože Docker 17.05 nebo vyšší, který pomáhá snížit velikost konečné image. V několika větách, s vícestupňovým sestavením můžete použít například velkou základní bitovou kopii obsahující sdk, pro kompilaci a publikování aplikace a následné použití složky publikování s malou základní bitovou kopii pouze za běhu, abyste vytvořili mnohem menší konečnou bitovou kopii

**Úložiště (úložiště)**: Kolekce souvisejících imitek Dockeru, označená značkou, která označuje verzi bitové kopie. Některá repo repo obsahují více variant určitého obrázku, například obrázek obsahující sady SDK (těžší), obrázek obsahující pouze runtimes (světlejší) atd. Tyto varianty mohou být označeny značkami. Jediné repo může obsahovat varianty platformy, jako je například bitová kopie Linuxu a bitová kopie systému Windows.

**Registr**: Služba, která poskytuje přístup k úložištím. Výchozí registr pro většinu veřejných bitových kopií je [Docker Hub](https://hub.docker.com/) (vlastněný Dockerem jako organizace). Registr obvykle obsahuje úložiště z více týmů. Společnosti mají často soukromé registry pro ukládání a správu obrázků, které vytvořily. Dalším příkladem je Azure Container Registry.

**Víceobloukový obraz**: Pro vícearchitekturje funkce, která zjednodušuje výběr příslušné bitové kopie podle platformy, na které je **`FROM mcr.microsoft.com/dotnet/core/sdk:2.2`** spuštěný Docker, **`2.2-nanoserver-1709`** například když soubor Dockerfile požaduje základní bitovou kopii z registru, který skutečně získá , **`2.2-nanoserver-1803`** **`2.2-nanoserver-1809`** nebo **`2.2-stretch`**, v závislosti na operačním systému a verzi, kde je docker spuštěn.

**Docker Hub**: Veřejný registr pro nahrávání obrázků a práci s nimi. Docker Hub poskytuje hostování image Dockeru, veřejné nebo soukromé registry, aktivační události sestavení a webové háčky a integraci s GitHuba a Bitbucket.

**Azure Container Registry**: Veřejný prostředek pro práci s ibi Dockeru a jeho součástmi v Azure. To poskytuje registr, který je blízko k vašim nasazením v Azure a který vám dává kontrolu nad přístupem, takže je možné používat skupiny a oprávnění Služby Azure Active Directory.

**Docker Trusted Registry (DTR)**: Služba registru Dockeru (z Dockeru), kterou lze nainstalovat místně, aby se stěžejně v datovém centru a síti organizace. Je vhodný pro soukromé obrázky, které by měly být spravovány v rámci podniku. Důvěryhodný registr Dockeru je součástí produktu Docker Datacenter. Další informace naleznete v [tématu Docker Trusted Registry (DTR)](https://docs.docker.com/docker-trusted-registry/overview/).

**Docker Community Edition (CE):** Vývojové nástroje pro Windows a macOS pro místní vytváření, spouštění a testování kontejnerů. Docker CE pro Windows poskytuje vývojová prostředí pro linuxové i windowsové kontejnery. Linux Docker host v systému Windows je založen na virtuálním počítači [Hyper-V.](https://www.microsoft.com/cloud-platform/server-virtualization) Hostitel pro kontejnery systému Windows je přímo založen na systému Windows. Docker CE for Mac je založen na rozhraní Apple Hypervisor a [hypervisoru xhyve](https://github.com/mist64/xhyve), který poskytuje virtuální počítač hostitele Linux Docker u Mac OS X. Docker CE pro Windows a pro Mac nahrazuje Docker Toolbox, který byl založen na Oracle VirtualBox.

**Docker Enterprise Edition (EE):** Verze nástrojů Dockeru v podnikovém měřítku pro vývoj Linuxu a Windows.

**Compose**: Nástroj příkazového řádku a formát souboru YAML s metadaty pro definování a spouštění aplikací s více kontejnery. Definujete jednu aplikaci založenou na více obrazech s jedním nebo více soubory .yml, které mohou přepsat hodnoty v závislosti na prostředí. Po vytvoření definic můžete nasadit celou aplikaci s více kontejnery pomocí jediného příkazu (docker-compose up), který vytvoří kontejner na bitovou kopii na hostiteli Dockeru.

**Cluster**: Kolekce hostitelů Dockeru vystavená, jako by se jednalo o jednoho virtuálního hostitele Dockeru, takže aplikace může škálovat na více instancí služeb rozložených mezi více hostitelů v rámci clusteru. Clustery Dockeru lze vytvářet pomocí Kubernetes, Azure Service Fabric, Docker Swarm a Mesosphere DC/OS.

**Orchestrator**: Nástroj, který zjednodušuje správu clusterů a hostitelů Dockeru. Orchestrators umožňují spravovat své obrázky, kontejnery a hostitele prostřednictvím rozhraní příkazového řádku (CLI) nebo grafického uživatelského rozhraní. Můžete spravovat sítě kontejnerů, konfigurace, vyrovnávání zatížení, zjišťování služeb, vysokou dostupnost, konfiguraci hostitele Dockeru a další. Orchestrator je zodpovědný za spouštění, distribuci, škálování a retušování úloh y napříč kolekcí uzlů. Produkty orchestrator jsou obvykle stejné produkty, které poskytují infrastrukturu clusteru, jako je Kubernetes a Azure Service Fabric, mimo jiné nabídky na trhu.

>[!div class="step-by-step"]
>[Předchozí](what-is-docker.md)
>[další](docker-containers-images-and-registries.md)
