---
title: Terminologie docker
description: "Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a622b2949c1d2277bb3e82617a5bc2d8cb432263
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="docker-terminology"></a>Terminologie docker

Tato část uvádí termíny a definice, se kterými měli byste se seznámit s před hlubší seznamovat do Docker (Další definice, naleznete rozsáhlé [Glosář](https://docs.docker.com/glossary/) poskytované Docker v <https:// docs.docker.com/glossary/>:

-   **Kontejner image** balíček s všechny závislosti a informace potřebné k vytvoření kontejneru. Obrázek zahrnuje všechny závislosti (například rozhraní) plus nasazení a konfigurace, které má být používána runtime kontejneru. Obvykle bitovou kopii je odvozena z více základní bitových kopií, vrstvy přibývají jeden na druhý k vytvoření kontejneru systému souborů. Bitová kopie je neměnný po jeho vytvoření.

-   **Kontejner** instance Docker bitové kopie. Představuje kontejner modulu runtime pro jednu aplikaci, procesu nebo služby. Skládá se z obsah bitovou kopii Docker, běhové prostředí a standardní sadu pokynů. Když škálování služby, můžete vytvořit více instancí kontejner ze stejné image. Nebo dávkovou úlohu můžete vytvořit více kontejnerů ze stejné image, předávání různé parametry pro každou instanci.

-   **Značka** označit nebo štítek, který lze použít pro obrázky, takže lze identifikovat různé obrázky nebo verzích stejnou bitovou kopii (v závislosti na číslo verze nebo cílové prostředí).

-   **Soubor Docker** textový soubor, který obsahuje pokyny k sestavení Docker bitové kopie.

-   **Sestavení** akci vytváření obrazem kontejneru na základě informací a kontext poskytované jeho soubor Docker, jakož i další soubory ve složce, ve kterém je sestavena bitovou kopii. Bitové kopie můžete vytvořit pomocí příkazu Docker docker sestavení.

-   **Úložiště (úložiště)** kolekce související imagí Dockeru s názvem bez přípony se značkou, která označuje verzi bitové kopie. Některé úložiště obsahovat více variant konkrétní image, jako je například bitovou kopii sady SDK (těžší), obsahující bitovou kopii obsahující pouze moduly runtime (světlejší), a tak dále. Těchto variant může být označen značky. Jednoho úložiště může obsahovat variant platformy, jako je například bitovou kopii systému Linux a bitové kopie systému Windows.

-   **Registru** služba, která poskytuje přístup k úložiště. Je výchozím nastavení registru pro nejvíce veřejné bitové kopie [úložiště Docker Hub](https://hub.docker.com/) (vlastníkem Docker organizace). Registru obvykle obsahuje úložiště od více týmů. Společnosti musí často privátní registrech k ukládání a správě bitových kopií, které jste vytvořili. *Azure kontejneru registru* je další příklad.

-   **Úložiště docker Hub** veřejné registru nahrát bitové kopie a pracovat s nimi. Úložiště docker Hub poskytuje Docker hostování bitové kopie, registrech veřejných nebo privátních, aktivační události sestavení a webové háky a integrace s Githubu a Bitbucket.

-   **Azure kontejneru registru** prostředek veřejné pro práci s imagí Dockeru a jeho komponenty v Azure. To poskytuje registr, která je blízko svá nasazení v Azure a udávající řízení přístupu, aby bylo možné pomocí skupin Azure Active Directory a oprávnění.

-   **Docker důvěryhodné registru (DTR)** A Docker služby registru (z Docker), který můžete nainstalovat místně tak, aby se nachází v rámci datového centra a sítě organizace. Je vhodné pro privátní bitové kopie, které se mají spravovat v rámci podniku. Docker důvěryhodné registru je součástí produktu Docker Datacenter. Další informace, přejděte na [https://docs.docker.com/docker-trusted-registry/overview/](https://docs.docker.com/docker-trusted-registry/overview/).

-   **Docker Community Edition (CE)** nástroje pro vývoj pro systém Windows a systému macOS pro vytváření, spouštění a testování kontejnery místně. CE docker pro systém Windows poskytuje vývojové prostředí pro Linux a Windows kontejnery. Je na základě hostitelů Linux Docker v systému Windows [technologie Hyper-V](https://www.microsoft.com/en-us/server-cloud/solutions/virtualization.aspx) virtuálních počítačů. Hostitel pro kontejnery Windows je přímo založená na systému Windows. Docker CE pro Mac je založené na rozhraní framework Apple hypervisoru a [xhyve hypervisoru](https://github.com/mist64/xhyve), který poskytuje Linux Docker hostitele virtuálních počítačů Mac OS X. Docker CE pro systém Windows a Mac nahrazuje Docker sada nástrojů, která je založena na Oracle VirtualBox.

-   **Docker Enterprise Edition (EE)** na podnikovém měřítku verzi Docker nástroje pro vývoj pro Linux a Windows.

-   **Napište** nástroj příkazového řádku a YAML souboru formátu s metadaty pro definování a spouštění multicontainer aplikací. Můžete definovat jednu aplikaci založené na více bitových kopií se jeden nebo více .yml soubory, které můžete přepsat hodnoty v závislosti na prostředí. Po vytvoření definice, bude celá aplikace multicontainer můžete nasadit pomocí jednoduchého příkazu (docker-tvoří nahoru) na hostiteli Docker vytvářející kontejner pro bitovou kopii.

-   **Cluster** kolekce hostitelů Docker zveřejněné jako kdyby byly jeden virtuální hostitel Docker tak, aby aplikace lze škálovat na více instancí služeb rozloženy víc hostitelích v clusteru. Můžete vytvořit clustery Docker pomocí Docker Swarm, Mesosphere DC/OS, Kubernetes a Azure Service Fabric. (Pokud používáte Docker Swarm pro správu clusteru, je obvykle podívejte se na clusteru jako *swarm* místo clusteru.)

-   **Orchestrator** nástroj, který zjednodušuje správu clusterů a hostitelů Docker. Pomocí orchestrators, můžete spravovat jejich obrázků, kontejnery a hostitelů pomocí nástroje rozhraní příkazového řádku nebo grafické uživatelské rozhraní. Můžete spravovat kontejner sítě, konfigurace, Vyrovnávání zatížení, zjišťování služby, vysokou dostupnost, konfigurace hostitelů Docker a další. Orchestrator je zodpovědná za spuštění, distribuci, škálování a opravy zatížení napříč kolekce uzlů. Produkty orchestrator jsou obvykle stejné produkty, které zajišťují infrastrukturu clusteru, jako je Mesosphere DC/OS, Kubernetes, Docker Swarm a Azure Service Fabric.


>[!div class="step-by-step"]
[Předchozí] (what-is-docker.md) [Další] (docker-containers-images-and-registries.md)
