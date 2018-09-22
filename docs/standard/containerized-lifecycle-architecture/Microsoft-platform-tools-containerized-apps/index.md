---
title: Úvod do Microsoft platformu a nástroje pro kontejnerizované aplikace
description: Životní cyklus aplikace kontejnerizovaných Dockeru s platformou a nástroji Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: bc13a0c8d6f14b8ea7ea2017009ba074f9a96ab3
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46580249"
---
# <a name="introduction-to-the-microsoft-platform-and-tools-for-containerized-apps"></a>Úvod do Microsoft platformu a nástroje pro kontejnerizované aplikace


Obrázek 3-1 zobrazuje hlavní pilíře v životním cyklu aplikace Dockeru klasifikuje typu práce od několika týmů (vývoj aplikací, infrastruktury procesy DevOps a správy IT a operace). Obvykle v podnikové síti, profily "osoba" zodpovídá za každou oblast, kterou se liší. Proto jsou své dovednosti.

![](./media/image1.png)

Obrázek 3-1: hlavní pilíři životní cyklus kontejnerizované aplikace Dockeru s platformou a nástroji Microsoft

A kontejnerizovaných Docker životní cyklus pracovní postup může být zpočátku doporučené na základě "ve výchozím nastavení produkt voleb," usnadňuje vývojářům začít pracovat rychleji, ale je zásadní pro pod pokličkou musí obsahovat otevřené rozhraní tak, že bude flexibilní pracovní postup umožňující úpravy do různých kontextech z každé organizace nebo podniku. Pracovní postup infrastruktury (součásti a produkty) musí být dostatečně flexibilní, aby pokryl prostředí, které každá společnost má v budoucnu, i jsou schopny prohození vývoj nebo DevOps produktů pro ostatní. Této flexibility, otevřenost a širokou škálu technologií v platforma a infrastruktura jsou přesně priority společnosti Microsoft pro kontejnerizované aplikace Dockeru, jak je vysvětleno v kapitolách, které následují.

Tabulka 3-1 ukazuje, že záměr Microsoft DevOps pro kontejnerizované aplikace Dockeru je poskytnout otevřený pracovních postupů DevOps tak, aby můžete zvolit, jaké produkty pro každou fázi (společnosti Microsoft nebo třetích stran) poskytuje zjednodušenou pracovního postupu který poskytuje již připojen "ve výchozí produktů"; Proto je můžete rychle začít s pracovních postupů DevOps podnikové úrovni pro aplikace Dockeru.

Tabulka 3 – 1: Otevřete DevOps pracovní postup pro všechny technologie

| Hostitel | Technologie společnosti Microsoft | Třetí strany, modulární Azure |
| ---------------------------| ----------------------------------------------------| --------------------------------------------------------------------------------|
| Platforma pro aplikace Dockeru   | • Microsoft Visual Studio a Visual Studio Code<br /> • .NET<br /> • Microsoft Azure Container Service<br /> • Azure Service Fabric<br /> • Azure Container Registry<br /> | • Libovolný editor kódu (například Sublime)<br /> • Libovolný jazyk (Node.js, Java, Go, atd.)<br /> • Všechny nástroje orchestrator a Plánovač<br /> • Jakýkoli registr Dockeru<br /> |
| DevOps pro aplikace Dockeru     | • Služby azure DevOps<br /> • Microsoft Team Foundation Server<br /> • Azure Container Service<br /> • Azure Service Fabric<br /> | • Githubu, Git, Subversion, atd.<br /> • Jenkinse, Chef, Puppet, rychlost, CircleCI, travis ci, atd.<br /> • V místním datovém centru Dockeru, Docker Swarm, Mesos DC/OS, Kubernetes, atd.<br /> |
| Monitorování a Správa  | • Operations Management Suite<br /> • Aplikace Insights<br /> | • Marathon, Chronos, atd.<br />

Microsoft platformu a nástroje pro kontejnerizované aplikace Dockeru, jak je definováno v tabulce 3-1, zahrnuje následující součásti:

-   **Platforma pro vývoj aplikace v Dockeru** vývoj služby nebo kolekce služeb, které tvoří "aplikace". Vývojová platforma poskytuje všem vývojářům práci vyžaduje před doručením (push) kód úložiště sdíleného kódu. Vývoj služby nasazené jako kontejnery, jsou velmi podobné k vývoji tohoto stejného aplikacím nebo službám bez Dockeru. Můžete dál používat upřednostňovaném jazyce (.NET, Node.js, Go, atd.) a preferovaného editoru nebo prostředí IDE, jako je Visual Studio nebo Visual Studio Code. Ale spíše než zvažte Docker cíl nasazení, při vývoji vašich služeb v prostředí Docker. Sestavení, spuštění, testování a ladění kódu v kontejnerech místně, poskytování cílového prostředí v době vývoje. Zadáním cílového prostředí místně kontejnery Dockeru nastavte co výrazně pomůžou zlepšit váš životní cyklus DevOps. Visual Studio a Visual Studio Code jsou rozšíření integrace kontejnerů Dockeru v rámci vašeho vývojového procesu.

-   **DevOps pro aplikace Dockeru** vývojáře vytvářející aplikace Docker můžete použít Azure DevOps služby a všechny ostatní třetích stran produkty, jako je Jenkins, k sestavení komplexního automatizované správy životního cyklu aplikací (ALM).

Azure DevOps Services umožňuje vývojářům vytvářet zaměřené na kontejner řídit vývoj a provoz pro rychlý a iterativní proces, který obsahuje zdrojový kód z libovolného místa (Azure DevOps služby-Git, GitHub, žádné vzdálené úložiště Git nebo Subversion), kontinuální integrace (CI) , interní jednotkové testy, mezi virtuálními sítěmi/služba kontejneru testů integrace, průběžné doručování (CD) a produktu release management (SV). Vývojáři taky můžete automatizovat verzí jejich Docker aplikace do Azure Container Service, od vývoje do přípravného a produkčního prostředí.
 
-   Produkční monitorování a správy IT.

**Správa** IT může spravovat aplikace v produkčním prostředí a služeb několika způsoby:

-   **Azure portal** Pokud používáte open source orchestrátorů, Azure Container Service (ACS) a nástroje pro správu clusteru, jako je Docker Datacenter a Mesosphere Marathon dozvíte, jak nastavit a spravovat prostředí Docker. Pokud používáte Azure Service Fabric, nástroj Service Fabric Explorer umožňuje vizualizovat a konfigurace clusteru.

-   **Nástroje dockeru** můžete spravovat vaše aplikace typu kontejner pomocí známých nástrojů. Není nemusíte měnit svoje dosavadní postupy správy Docker chcete přesunout úlohy kontejnerů do cloudu. Pomocí nástroje pro správu aplikace už znáte a připojte se pomocí standardních koncových bodů rozhraní API k orchestrátoru podle vaší volby. Další nástroje třetích stran také můžete použít ke správě aplikace v Dockeru, jako je například Docker Datacenter nebo dokonce nástroje rozhraní příkazového řádku Dockeru.

-   **Open source nástroje** zpřístupňuje standardní koncové body rozhraní API pro orchestrační modul ACS vzhledem k tomu, nejoblíbenější opensourcové nástroje jsou kompatibilní s ACS a ve většině případů fungují bez pole, včetně vizualizátorů, sledování, nástroje příkazového řádku a taky budoucích nástrojů, jakmile budou k dispozici.

**Monitorování** při spouštění produkční prostředí, můžete monitorovat všech možných úhlů pomocí následující:

-   **Operations Management Suite (OMS)** "Kontejneru řešení OMS" můžete spravovat a monitorovat hostitelů Docker a kontejnery tím, že zobrazuje informace o tom, kde jsou kontejnery a hostitelích kontejnerů, které kontejnery jsou spuštěné nebo chyba, a protokoly démonu a kontejneru Dockeru. Také ukazuje metriky výkonu, jako je například procesoru, paměti, sítě a úložiště pro kontejner a hostitele při řešení potíží a najít hlučného souseda kontejnery.

-   **Application Insights** jednoduše nastavením její SDK do vaší služby, takže získáte telemetrická data z aplikací můžete monitorovat aplikace v produkčním prostředí Docker.

Proto Microsoft nabízí kompletní foundation začátku do konce kontejnerizovaných Docker životního cyklu aplikace. Je však *kolekce produktů a technologií, které můžete volitelně vybrat a integrace s existujícím nástroje a procesy*. Flexibilitu v rámci široké přístupu spolu s sílu do hloubky možnosti umístění Microsoft strong polohy pro vývoj kontejnerizovaných aplikací Dockeru.

>[!div class="step-by-step"]
[Předchozí](../Docker-application-lifecycle/containers-foundation-for-devops-collaboration.md)
[další](../design-develop-containerized-apps/index.md)
