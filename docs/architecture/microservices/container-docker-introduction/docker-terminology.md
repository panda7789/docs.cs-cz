---
title: Terminologie Dockeru
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Terminologie Dockeru
ms.date: 01/30/2020
ms.openlocfilehash: fdcc5ec3603579c36d7339bd3ff651713b8eba88
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523336"
---
# <a name="docker-terminology"></a>Terminologie Dockeru

V této části jsou uvedeny termíny a definice, které byste měli znát, než se dostanete hlouběji do Dockeru. Další definice naleznete v rozsáhlém [glosáři](https://docs.docker.com/glossary/) poskytovaném dockerem.

**Image kontejneru**: Balíček se všemi závislostmi a informacemi potřebnými k vytvoření kontejneru. Bitová kopie obsahuje všechny závislosti (například architektury) plus konfigurace nasazení a spuštění, které mají být použity v době runtime kontejneru. Obraz obvykle pochází z více základních obrazů, které jsou vrstvy naskládané nad sebou a tvoří souborový systém kontejneru. Obrázek je neměnný, jakmile byl vytvořen.

**Dockerfile**: Textový soubor, který obsahuje pokyny pro vytvoření image Dockeru. Je to jako dávkový skript, první řádek uvádí základní obraz začít a pak postupujte podle pokynů k instalaci požadovaných programů, kopírování souborů a tak dále, dokud se dostanete pracovní prostředí, které potřebujete.

**Sestavení**: Akce vytváření image kontejneru na základě informací a kontextu poskytované jeho Dockerfile, plus další soubory ve složce, kde je vytvořena image. Můžete vytvářet image pomocí příkazu Docker:

> `docker build`

**Kontejner**: Instance image Dockeru. Kontejner představuje spuštění jedné aplikace, procesu nebo služby. Skládá se z obsahu image Dockeru, prostředí spuštění a standardní sady instrukcí. Při škálování služby vytvoříte více instancí kontejneru ze stejné bitové kopie. Nebo dávková úloha můžete vytvořit více kontejnerů ze stejného obrázku, předávání různých parametrů pro každou instanci.

**Svazky**: Nabídněte zapisovatelný souborový systém, který může kontejner používat. Vzhledem k tomu, že obrázky jsou jen pro čtení, ale většina programů musí zapisovat do souborového systému, svazky přidávají zapisovatelnou vrstvu nad obraz kontejneru, takže programy mají přístup k zapisovatelnému souborovému systému. Program neví, že přistupuje k vrstvené souborové soustavě, je to jen souborový systém jako obvykle. Svazky jsou aktivní v hostitelském systému a jsou spravovány Dockerem.

**Značka**: Značka nebo popisek, který můžete použít na obrázky, aby bylo možné identifikovat různé obrázky nebo verze stejného obrázku (v závislosti na čísle verze nebo cílovém prostředí).

**Vícestupňové sestavení**: Je funkce, protože Docker 17.05 nebo vyšší, který pomáhá snížit velikost konečné image. V několika větách, s vícestupňové sestavení můžete použít, například, velké základní image, obsahující SDK, pro kompilaci a publikování aplikace a pak pomocí složky publikování s malou bitovou kopii pouze za běhu, k vytvoření mnohem menší konečné image.

**Úložiště (úložiště)**: Kolekce souvisejících imitek Dockeru, označená značkou, která označuje verzi bitové kopie. Některá repo repo obsahují více variant určitého obrázku, například obrázek obsahující sady SDK (těžší), obrázek obsahující pouze runtimes (světlejší) atd. Tyto varianty mohou být označeny značkami. Jediné repo může obsahovat varianty platformy, jako je například bitová kopie Linuxu a bitová kopie systému Windows.

**Registr**: Služba, která poskytuje přístup k úložištím. Výchozí registr pro většinu veřejných bitových kopií je [Docker Hub](https://hub.docker.com/) (vlastněný Dockerem jako organizace). Registr obvykle obsahuje úložiště z více týmů. Společnosti mají často soukromé registry pro ukládání a správu obrázků, které vytvořily. Dalším příkladem je Azure Container Registry.

**Víceobloukový obraz**: Pro vícearchitektura je to funkce, která zjednodušuje výběr příslušného obrázku podle platformy, na které docker běží. Například když Dockerfile požaduje základní image **FROM mcr.microsoft.com/dotnet/core/sdk:3.1** z registru, ve skutečnosti získá **3.1-sdk-nanoserver-1909**, **3.1-sdk-nanoserver-1809** nebo **3.1-sdk buster-slim**, v závislosti na operačním systému a verzi, kde je spuštěn Docker.

**Docker Hub**: Veřejný registr pro nahrávání obrázků a práci s nimi. Docker Hub poskytuje hostování image Dockeru, veřejné nebo soukromé registry, aktivační události sestavení a webové háčky a integraci s GitHuba a Bitbucket.

**Azure Container Registry**: Veřejný prostředek pro práci s ibi Dockeru a jeho součástmi v Azure. To poskytuje registr, který se nachází v blízkosti vašich nasazení v Azure a který vám dává kontrolu nad přístupem, takže je možné používat skupiny a oprávnění služby Azure Active Directory.

**Docker Trusted Registry (DTR)**: Služba registru Dockeru (z Dockeru), kterou lze nainstalovat místně, aby se stěžejně v datovém centru a síti organizace. Je vhodný pro soukromé obrázky, které by měly být spravovány v rámci podniku. Důvěryhodný registr Dockeru je součástí produktu Docker Datacenter. Další informace naleznete v [tématu Docker Trusted Registry (DTR)](https://docs.docker.com/docker-trusted-registry/overview/).

**Docker Community Edition (CE):** Vývojové nástroje pro Windows a macOS pro místní vytváření, spouštění a testování kontejnerů. Docker CE pro Windows poskytuje vývojová prostředí pro linuxové i windowsové kontejnery. Linux Docker host v systému Windows je založen na virtuálním počítači [Hyper-V.](https://www.microsoft.com/cloud-platform/server-virtualization) Hostitel pro kontejnery systému Windows je přímo založen na systému Windows. Docker CE for Mac je založen na rozhraní Apple Hypervisor a [hypervisoru xhyve](https://github.com/mist64/xhyve), který poskytuje virtuální počítač hostitele Linux Docker u Mac OS X. Docker CE pro Windows a pro Mac nahrazuje Docker Toolbox, který byl založen na Oracle VirtualBox.

**Docker Enterprise Edition (EE):** Verze nástrojů Dockeru v podnikovém měřítku pro vývoj Linuxu a Windows.

**Compose**: Nástroj příkazového řádku a formát souboru YAML s metadaty pro definování a spouštění aplikací s více kontejnery. Definujete jednu aplikaci založenou na více obrazech s jedním nebo více soubory .yml, které mohou přepsat hodnoty v závislosti na prostředí. Po vytvoření definice, můžete nasadit celou aplikaci s více kontejnery s jedním příkazem (docker-compose up), který vytvoří kontejner na image na hostiteli Dockeru.

**Cluster**: Kolekce hostitelů Dockeru vystavená, jako by se jednalo o jednoho virtuálního hostitele Dockeru, takže aplikace může škálovat na více instancí služeb rozložených mezi více hostitelů v rámci clusteru. Clustery Dockeru lze vytvářet pomocí Kubernetes, Azure Service Fabric, Docker Swarm a Mesosphere DC/OS.

**Orchestrator**: Nástroj, který zjednodušuje správu clusterů a hostitelů Dockeru. Orchestrators umožňují spravovat své obrázky, kontejnery a hostitele prostřednictvím cli nebo grafické uživatelské ho uživatelského prostředí. Můžete spravovat sítě kontejnerů, konfigurace, vyrovnávání zatížení, zjišťování služeb, vysokou dostupnost, konfiguraci hostitele Dockeru a další. Orchestrator je zodpovědný za spouštění, distribuci, škálování a retušování úloh y napříč kolekcí uzlů. Produkty orchestrator jsou obvykle stejné produkty, které poskytují infrastrukturu clusteru, jako je Kubernetes a Azure Service Fabric, mimo jiné nabídky na trhu.

>[!div class="step-by-step"]
>[Předchozí](docker-defined.md)
>[další](docker-containers-images-registries.md)
