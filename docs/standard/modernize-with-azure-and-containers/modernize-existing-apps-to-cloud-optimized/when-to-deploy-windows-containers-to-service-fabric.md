---
title: Když k nasazení Windows kontejnery pro Service Fabric
description: Modernizovat existující aplikace .NET s kontejnery cloudu Azure a Windows | Když k nasazení Windows kontejnery pro Service Fabric
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: c41db8b37c883f9369a6b8d1f8bccbc0535f504c
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
---
# <a name="when-to-deploy-windows-containers-to-service-fabric"></a>Když k nasazení Windows kontejnery pro Service Fabric

Aplikace, které jsou založené na Windows kontejnery rychle muset platformy, které přepínají i další počítače z virtuálních počítačů IaaS. Toto je pro automatizované lepší škálovatelnost a vysokou škálovatelnost a k získání významná vylepšení v prostředí pro kompletní správu pro nasazení, upgrady, Správa verzí, odvolání a sledování stavu. S nástrojem orchestrator Azure Service Fabric, k dispozici v cloudu Microsoft Azure, ale také místní, nebo i v jiném cloudu můžete dosáhnout těchto cílů.

Mnoho organizací jsou zrušení a přejdou existující monolitický aplikace do kontejnerů dvou důvodů:

-   Snížení nákladů, buď z důvodu konsolidace a odebrání stávající hardware nebo z spouštění aplikací na vyšší hustotu.

-   Konzistentní nasazení smlouva mezi vývoj a provoz.

Provést snížení nákladů je srozumitelný a je pravděpodobné, že jsou všechny organizace následné dotazy tohoto cíle. Konzistentní nasazení je těžší k vyhodnocení, ale je stejně jako důležité. Kontraktu konzistentní nasazení říká, že se vývojáři mohou zvolit technologii, která vyhovuje, je použít a provozní tým získá jeden způsob, jak nasadit a spravovat aplikace. Tato smlouva nebude problémové s operací řešit složitosti mnoha různých technologií, nebo vynucení vývojářům pracovat pouze s určitým technologie. V podstatě každá aplikace je kontejnerizované v bitové kopii samostatná nasazení.

Některé organizace bude pokračovat modernizace přidáním mikroslužeb (nativní cloudové aplikace), ale mnoha jiných organizací se zastaví zde (optimalizovaných Cloudů aplikace). Jak ukazuje obrázek 4-8, nebude tato organizace přesunout do mikroslužeb architektury, protože nebudete muset. V každém případě se již získání výhody, že pomocí kontejnery plus Service Fabric, včetně nasazení, a poskytuje kompletní správu prostředí upgraduje, Správa verzí, odvolání a sledování stavu.

> ![Navýšení a posunutí aplikaci Service Fabric](./media/image8.png)
>
> **Obrázek 4-8.** Navýšení a posunutí aplikaci Service Fabric

Klíče přístup k Service Fabric je znovu použít stávající kód a navýšení a posunutí. Proto můžete migrovat vaše aktuální aplikace rozhraní .NET Framework, pomocí Windows kontejnery a jejich nasazení do Service Fabric. Bude snazší informovat přejdete modernizace, nakonec přidáním nové mikroslužeb.

Při porovnávání Service Fabric na jiné orchestrators, je důležité, abyste měli na očích, že Service Fabric je zavedený na spuštění služby a aplikace pro systém Windows. Service Fabric spuštění systému Windows služby a aplikace, včetně úrovně 1, zvláště důležité produkty společnosti Microsoft pro let. Bylo první orchestrator máte obecné dostupnosti k Windows kontejnery. Další kontejnery, jako je Kubernetes, DC/OS a Docker Swarm, jsou víc vyspělých v systému Linux, ale vyspělá méně než aplikacím služby infrastruktury pro systém Windows a Windows kontejnerů.

Konečným cílem Service Fabric je ke snížení složitosti sestavení aplikace pomocí mikroslužeb přístup. Nakonec chcete mikroslužeb pro některé typy aplikací, aby se zabránilo nákladná redesigns. Můžete začněte v malém rozsahu, škálovat v případě potřeby, přestat používat služby, přidat nové služby a vyvíjet aplikace s použitím zákazníka. Existuje mnoho jiné problémy, které ještě mají být vyřešeny Pokud chcete, aby mikroslužeb více srozumitelné pro Většina vývojářů. Pokud je v současné době jsou právě zrušení a s posunem aplikace s kontejnery Windows, ale přemýšlíte o přidání mikroslužeb v budoucnu podle kontejnerů, které je místo paprika Service Fabric.

>[!div class="step-by-step"]
[Předchozí](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[další](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
