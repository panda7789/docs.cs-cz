---
title: Terminologie Dockeru
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Terminologie Docker
ms.date: 01/07/2019
ms.openlocfilehash: a5f78ea0e848ef14f6b37e2d97d7546df20096c2
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179410"
---
# <a name="docker-terminology"></a>Terminologie Dockeru

V této části jsou uvedeny pojmy a definice, se kterými byste se měli seznámit, než se dostanete do hlubšího prostředí Docker. Další definice najdete v rozsáhlých [glosářích](https://docs.docker.com/glossary/) poskytovaných Docker.

**Image kontejneru**: balíček se všemi závislostmi a informacemi potřebnými k vytvoření kontejneru. Obrázek obsahuje všechny závislosti (například architektury) a konfiguraci nasazení a spuštění, které se mají použít v modulu runtime kontejneru. Obvykle se obrázek odvodí z několika základních imagí, které jsou vrstvou vrstveny navzájem, aby tvořily systém souborů kontejneru. Obrázek je po vytvoření proměnlivý.

**Souboru Dockerfile**: textový soubor, který obsahuje pokyny pro vytvoření image Docker. Je to jako dávkový skript, první řádek uvádí základní image, která se má začít, a potom postupujte podle pokynů k instalaci požadovaných programů, kopírování souborů a tak dále, dokud nezískáte pracovní prostředí, které potřebujete.

**Sestavení**: akce vytvoření bitové kopie kontejneru na základě informací a kontextu, které poskytuje jeho souboru Dockerfile, a dalších souborů ve složce, ve které je obrázek sestaven. Image můžete vytvářet pomocí příkazu Docker **Docker Build** . 

**Container**: instance bitové kopie Docker. Kontejner představuje spuštění jedné aplikace, procesu nebo služby. Skládá se z obsahu bitové kopie Docker, spouštěcího prostředí a standardní sady instrukcí. Při škálování služby vytvoříte více instancí kontejneru ze stejné image. Nebo úloha služby Batch může vytvořit více kontejnerů ze stejné image a předat do každé instance různé parametry.

**Svazky**: nabízí zapisovatelný systém souborů, který může kontejner použít. Vzhledem k tomu, že jsou bitové kopie jen pro čtení, ale většina programů vyžaduje zápis do systému souborů, svazky přidávají zapisovatelné vrstvy, a to nad image kontejneru, takže programy mají přístup k systému souborů s možností zápisu. Program neví, že přistupuje k vrstvenému systému souborů, jedná se pouze o systém souborů obvyklým způsobem. Svazky jsou v hostitelském systému v provozu a jsou spravovány přes Docker.

**Tag**: Značka nebo popisek, který můžete použít na obrázky, aby bylo možné identifikovat různé Image nebo verze stejné Image (v závislosti na číslu verze nebo cílovém prostředí).

**Sestavení s více fázemi**: je funkce od docker 17,05 nebo vyšší, která pomáhá snižovat velikost finálních imagí. V několika větách s více fázemi sestavení můžete použít například velkou základní image, která obsahuje sadu SDK pro kompilaci a publikování aplikace a následné použití složky pro publikování s malým počtem základních imagí pouze pro modul runtime, k vytvoření mnohem menší konečné bitové kopie.

**Úložiště (úložiště)** : kolekce souvisejících imagí Docker označená značkou, která označuje verzi image. Některá úložiště obsahují několik variant určitého obrázku, jako je například Image obsahující sady SDK (těžší), image obsahující pouze běhové moduly (světlejší) atd. Tyto varianty lze označit pomocí značek. Jedno úložiště může obsahovat varianty platformy, jako je například bitová kopie systému Linux a bitová kopie systému Windows.

**Registr**: služba, která poskytuje přístup k úložištím. Výchozím registrem pro většinu veřejných imagí je [Docker Hub](https://hub.docker.com/) (vlastněné Docker jako organizace). Registr obvykle obsahuje úložiště z více týmů. Společnosti mají často privátní registry pro ukládání a správu imagí, které vytvořili. Azure Container Registry je další příklad.

**Vícestránkový obrázek**: pro více architektur je funkce, která zjednodušuje výběr příslušné image. podle platformy, kde je Docker spuštěný, například když souboru Dockerfile požaduje základní image **z MCR.Microsoft.com/dotnet/Core/SDK:2.2** z registru, který ve skutečnosti získá **2,2-SDK-nanoserver-1709**, **2,2-SDK-nanoserver-1803**, **2,2-SDK-nanoserver-1809** nebo **2,2-SDK-Stretch**, v závislosti na operačním systému a verzi, kde je Docker spuštěný. .

**Docker Hub**: veřejný registr pro nahrání obrázků a práci s nimi. Docker Hub poskytuje hostování imagí Docker, veřejné nebo privátní Registry, triggery sestavení a Webhooky a integraci s GitHubem a Bitbucket.

**Azure Container Registry**: veřejný prostředek pro práci s imagemi Docker a jejími součástmi v Azure. To poskytuje registr, který je blízko nasazení v Azure, a poskytuje vám kontrolu nad přístupem, což umožňuje používat vaše Azure Active Directory skupiny a oprávnění.

**Docker Trusted Registry (DTR)** : služba Docker Registry (z Docker), která se dá nainstalovat místně, aby byla v datacentru a síti organizace. Je vhodný pro privátní image, které by se měly spravovat v rámci podniku. Docker Trusted Registry je součástí produktu Docker Datacenter. Další informace najdete v tématu [Docker Trusted Registry (DTR)](https://docs.docker.com/docker-trusted-registry/overview/).

**Docker Community Edition (CE)** : vývojové nástroje pro Windows a MacOS pro místní vytváření, spouštění a testování kontejnerů. Docker CE for Windows poskytuje vývojová prostředí pro kontejnery Linux i Windows. Hostitel Docker pro Linux ve Windows je založený na virtuálním počítači [Hyper-V](https://www.microsoft.com/cloud-platform/server-virtualization) . Hostitel pro kontejnery Windows je přímo založený na systému Windows. Docker CE pro Mac je založený na architektuře Apple hypervisoru a [hypervisoru xhyve](https://github.com/mist64/xhyve), která poskytuje virtuální počítač hostitele Docker hosta na Mac OS X. Docker CE for Windows a pro Mac nahrazuje sadu nástrojů Docker, která byla založená na Oracle VirtualBox.

**Docker Enterprise Edition (EE)** : verze nástrojů Docker na podnikové úrovni pro vývoj pro Linux a Windows.

**Vytváření**: nástroj příkazového řádku a formát YAML souboru s metadaty pro definování a spouštění aplikací s více kontejnery. Můžete definovat jednu aplikaci založenou na několika obrázcích s jedním nebo více soubory. yml, které mohou přepsat hodnoty v závislosti na prostředí. Po vytvoření definice můžete nasadit celou aplikaci s více kontejnery pomocí jediného příkazu (Docker – sestavit), který vytvoří kontejner na obrázku na hostiteli Docker.

**Cluster**: kolekce hostitelů Docker, která byla vystavena jako jeden virtuální hostitel Docker, aby se aplikace mohla škálovat na víc instancí služeb, které jsou rozloženy mezi více hostitelů v rámci clusteru. Clustery Docker je možné vytvořit pomocí Kubernetes, Azure Service Fabric, Docker Swarm a Mesosphere DC/OS.

**Orchestrator**: nástroj, který zjednodušuje správu clusterů a hostitelů Docker. Orchestrace umožňují spravovat jejich image, kontejnery a hostitele prostřednictvím rozhraní příkazového řádku (CLI) nebo grafického uživatelského rozhraní. Můžete spravovat sítě kontejnerů, konfigurace, Vyrovnávání zatížení, zjišťování služeb, vysokou dostupnost, konfiguraci hostitele Docker a další. Produkt Orchestrator zodpovídá za spouštění, distribuci, škálování a retušovaní úloh napříč kolekcí uzlů. Produkty Orchestrator jsou obvykle stejné produkty, které poskytují infrastrukturu clusteru, jako je Kubernetes a Azure Service Fabric, mimo jiné nabídky na trhu. 

>[!div class="step-by-step"]
>[Předchozí](docker-defined.md)
>[Další](docker-containers-images-registries.md)
