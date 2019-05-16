---
title: Kdy nasadit kontejnery Windows do Service Fabricu
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a Windows kontejnery | Kdy nasadit kontejnery Windows do Service Fabric
ms.date: 04/30/2018
ms.openlocfilehash: d29a358fb039eb3390910958b1b1080698d730e0
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65643366"
---
# <a name="when-to-deploy-windows-containers-to-service-fabric"></a>Kdy nasadit kontejnery Windows do Service Fabricu

Aplikace, které jsou založeny na kontejnery Windows rychle muset použít platformy, které přepínají ještě více pryč z virtuálních počítačů IaaS. Toto je automatizované lepší škálovatelnost a vysokou škálovatelnost a získat významná vylepšení v kompletní možnosti správy pro nasazení, inovace, správu verzí, vrácení zpět a sledování stavu. Dosažení těchto cílů s nástrojem orchestrator Azure Service Fabric, k dispozici v cloudu Microsoft Azure, ale i v místním nebo dokonce i v jiném cloudu.

Mnoho organizací se nepoužily a posunutí existující monolitické aplikace, aby kontejnery pro dva důvody:

- Snížení nákladů, buď z důvodu konsolidace a odebrání stávající hardware nebo z aplikace spuštěné ve vyšší hustota.

- Konzistentní nasazování kontrakt mezi vývojem a provozem.

Snížení nákladů ovlivňovat je srozumitelný a je pravděpodobné, že jsou všechny organizace dohledávání danému cíli. Konzistentní nasazení je těžší k vyhodnocení, ale je stejně jako důležité. Kontrakt konzistentní nasazování říká, že vývojáři zvolit použití technologie, která jim vyhovuje, a provozní tým získá jeden způsob, jak nasadit a spravovat aplikace. Tato smlouva řeší problémy s operací řešit složité mnoha různých technologií, nebo vynucení vývojářům umožňuje pracovat pouze s určitým technologie. Každá aplikace je v podstatě kontejnerizovaných v bitové kopii samostatná nasazení.

Některé organizace bude pokračovat, modernizaci přidáním mikroslužby (aplikací nativních pro Cloud), ale mnoho jiných organizací se tady zastaví (aplikace optimalizované pro Cloud). Jak je znázorněno v obrázek 4. – 8, nebudou tyto organizace přesunout do mikroslužeb, protože nebudete muset. V každém případě již dostanou výhody, že pomocí kontejnerů a Service Fabric a poskytuje kompletní možnosti správy, který zahrnuje nasazení, upgrade, Správa verzí, vrácení zpět a sledování stavu.

> ![Zvedněte a shift aplikace Service Fabric](./media/image8.png)
>
> **Obrázek 4. – 8.** Zvedněte a shift aplikace Service Fabric

Klíče přístup k Service Fabric je chcete znovu použít existující kód a navýšit a přesunout. Proto můžete migraci stávajících aplikací rozhraní .NET Framework, s využitím kontejnerů Windows a jejich nasazení do Service Fabric. Bude jednodušší zajistit, že přejdete modernizaci nakonec přidáváním nových mikroslužeb.

Při porovnávání Service Fabric do jiných orchestrátorů, je třeba zvýraznit, Service Fabric je vyspělá na spuštění služby a aplikace pro systém Windows. Service Fabric je spuštěné služby založené na Windows a aplikací, včetně úrovně 1, nejdůležitější produkty společnosti Microsoft pro roky. Byla to první orchestrator má obecnou dostupnost pro kontejnery Windows. Jiné kontejnery, jako je Kubernetes, DC/OS a Docker Swarm, jsou vyspělejší v systému Linux, ale méně až po zralé než aplikace Service Fabric pro Windows a kontejnery Windows.

Konečným cílem Service Fabric je ke snížení složitosti vytváření aplikací s použitím přístup založený na mikroslužbách. Nakonec chcete založený na mikroslužbách pro určité typy aplikací, aby vyhnout se nákladným pracovali. Můžete začít v malém, škálovat v případě potřeby, přestat používat služby, přidat nové služby a vyvíjet aplikace s využitím zákazníka. Existuje mnoho problémů, které jsou zatím mají být vyřešeny, chcete-li více přístupné mikroslužeb pro většinu vývojářů. Pokud máte aktuálně pouze zrušení a přesun aplikace s kontejnery Windows, ale jsou uvažujete o přidání mikroslužeb založené na kontejnerech v budoucnu, to je místo sladkost Service Fabric.

>[!div class="step-by-step"]
>[Předchozí](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
>[další](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
