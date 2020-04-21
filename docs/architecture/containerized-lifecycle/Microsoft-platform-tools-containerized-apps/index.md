---
title: Úvod k platformě a nástrojům Microsoft pro kontejnerizované aplikace
description: Seznamte se s nabídkami Microsoftu pro podporu životního cyklu aplikací Dockeru.
ms.date: 02/15/2019
ms.openlocfilehash: 8cb7870035003e956ee57684a2a2528732849379
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738451"
---
# <a name="introduction-to-the-microsoft-platform-andtools-for-containerized-apps"></a>Úvod k platformě a nástrojům Microsoft pro kontejnerizované aplikace

*Vize: Vytvořte adaptabilní, projektovaný, kontejnerizovaný životní cyklus aplikací, který zahrnuje vývoj, it operace a řízení výroby.*

Obrázek 3-1 znázorňuje hlavní pilíře životního cyklu aplikací Dockeru klasifikovaných podle typu práce poskytované více týmy (vývoj aplikací, procesy infrastruktury DevOps a správa it a provoz). Obvykle se v podniku liší profily "persona" odpovědné za každou oblast. Stejně jako jejich schopnosti.

:::image type="complex" source="./media/index/microsoft-tools-contanerized-docker-app.png" alt-text="Diagram znázorňující nástroje Microsoftu potřebné k údržbě aplikací Dockeru.":::
Nástroje společnosti Microsoft. Pro zatížení vývoj/návrh: Docker engine pro Windows, VS a VS code, .NET Core, Azure Kubernetes Service. Pro úlohy sestavení/testování/doručení: Azure DevOps, Team Foundation Server, Docker CLI, Azure Kubernetes Service. Pro úlohy Spuštění/Monitorování/Správa: Azure Monitor, Azure Portal Azure Kubernetes Services, Service Fabric, ostatní orchestrátory.
:::image-end:::

**Obrázek 3-1.** Hlavní pilíře životního cyklu pro kontejnerizované aplikace Dockeru s platformou a nástroji Microsoftu

Kontejnerizovaný pracovní postup životního cyklu Dockeru může být zpočátku normativní na základě "možností produktu podle výchozích nastavení", což vývojářům usnadňuje rychlejší práci, ale je zásadní, že pod kapotou musí existovat otevřený rámec, aby se mohl pružný pracovní postup přizpůsobit různým kontextům z každé organizace nebo podniku. Infrastruktura pracovních postupů (součásti a produkty) musí být dostatečně flexibilní, aby pokryla prostředí, které bude mít každá společnost v budoucnu, a dokonce může vyměňovat vývoj nebo produkty DevOps s ostatními. Tato flexibilita, otevřenost a široký výběr technologií v platformě a infrastruktuře jsou přesně prioritami Společnosti Microsoft pro kontejnerizované aplikace Dockeru, jak je vysvětleno v následujících kapitolách.

Tabulka 3-1 ukazuje, že záměrem Microsoft DevOps pro kontejnerizované aplikace Dockeru je poskytnout otevřený pracovní postup DevOps, abyste si mohli vybrat, jaké produkty chcete použít pro každou fázi (Microsoft nebo třetí strana) a zároveň poskytnout zjednodušený pracovní postup, který poskytuje "výchozí produkty", které jsou již připojeny; proto můžete rychle začít s pracovním postupem DevOps na podnikové úrovni pro aplikace Dockeru.

**Tabulka 3-1.** Pracovní postupy DevOps, otevřené jakékoli technologii

| Hostitel | Technologie společnosti Microsoft | Třetí strana – připojitelný Azure |
| ---------------------------| ----------------------------------------------------| --------------------------------------------------------------------------------|
| Platforma pro aplikace Dockeru   | • Kód microsoft visual studio a visual studio<br /> • .NET<br /> • Služba Microsoft Azure Kubernetes (AKS)<br /> • Azure Service Fabric<br /> • Registr kontejnerů Azure<br /> | • Jakýkoli editor kódu (například Sublime)<br /> • Jakýkoli jazyk (Node.js, Java, Go, atd.)<br /> • Každý orchestrátor a plánovač<br /> • Jakýkoli registr Dockeru<br /> |
| DevOps pro aplikace Dockeru     | • Služby Azure DevOps<br /> • Server Microsoft Team Foundation<br /> • Služba Azure Kubernetes (AKS)<br /> • Azure Service Fabric<br /> | • GitHub, Git, Subversion atd.<br /> • Jenkins, Kuchař, Loutka, Rychlost, CircleCI, TravisCI, atd.<br /> • Místní Docker Datacenter, Docker Swarm, Mesos DC/OS, Kubernetes atd.<br /> |
| Správa a monitorování  | • Azure Monitor | • Maraton, Chronos, atd.<br />|

Platforma Microsoft a nástroje pro kontejnerizované aplikace Dockeru, jak je definováno v tabulce 3-1, obsahují následující součásti:

- **Platforma pro vývoj Docker Apps** Vývoj služby nebo kolekce služeb, které tvoří "aplikaci". Vývojová platforma poskytuje všechny práce vývojáři vyžaduje před odesláním jejich kód do úložiště sdíleného kódu. Vývoj služeb nasazených jako kontejnery se podobají vývoji stejných aplikací nebo služeb bez Dockeru. Můžete pokračovat v používání upřednostňovaného jazyka (.NET, Node.js, Go, atd.) a upřednostňovaného editoru nebo ide jako Visual Studio nebo Visual Studio Code. Však spíše než považovat Docker určení nasazení, můžete rozvíjet služby v prostředí Dockeru. Sestavení, spuštění, testování a ladění kódu v kontejnerech místně, poskytuje cílové prostředí v době vývoje. Tím, že poskytuje cílové prostředí místně, kontejnery Dockernastavit, co vám výrazně pomůže zlepšit váš životní cyklus DevOps. Visual Studio a Visual Studio Code mají rozšíření pro integraci kontejnerů Dockeru v rámci procesu vývoje.

- **DevOps pro aplikace Docker** Vývojáři vytvářející aplikace Dockeru můžou používat [služby Azure DevOps Services](https://azure.microsoft.com/services/devops/) nebo jakýkoli jiný produkt třetích stran, jako je Jenkins, k vytvoření komplexní automatizované správy životního cyklu aplikací (ALM).

  Pomocí služeb Azure DevOps mohou vývojáři vytvářet devops zaměřené na kontejnery pro rychlý a iterativní proces, který zahrnuje řízení zdrojového kódu odkudkoli (Azure DevOps Services-Git, GitHub, jakékoli vzdálené úložiště Git nebo Subversion), průběžné integrace (CI), interní testy částí, testy integrace mezi kontejnery a službami, průběžné doručování (CD) a správa verzí (RM). Vývojáři můžou taky automatizovat svoje verze aplikací Dockeru do služby Azure Kubernetes Service (AKS), od vývoje až po pracovní a produkční prostředí.

- **Řízení a monitorování** IT může spravovat a monitorovat produkční aplikace a služby několika způsoby a integrovat obě perspektivy do konsolidovaného prostředí.

  - **Azure portal** Pokud používáte orchestrátory s otevřeným zdrojovým kódem, Azure Kubernetes Service (AKS), Service Fabric a další orchestrátory vám pomůžou nastavit a udržovat prostředí Dockeru. Pokud používáte Azure Service Fabric, nástroj Service Fabric Explorer umožňuje vizualizovat a konfigurovat cluster.

  - **Nástroje Dockeru:** Aplikace kontejnerů můžete spravovat pomocí známých nástrojů. Není třeba měnit stávající postupy správy Dockeru, abyste přesunuli úlohy kontejnerů do cloudu. Použijte nástroje pro správu aplikací, které už znáte, a připojte se přes standardní koncové body rozhraní API pro orchestrátorpodle vašeho výběru. Ke správě aplikací Dockeru můžete také použít jiné nástroje třetích stran, jako je například Docker Datacenter nebo dokonce nástroje CLI Docker.

    I když jste obeznámeni s příkazy Linuxu, můžete spravovat aplikace kontejnerů pomocí Microsoft Windows a PowerShell s příkazovým řádkem Linux Subsystem a produkty (Docker, Kubernetes...) klienti běžící na této funkci linuxového podsystému. Další informace o používání těchto nástrojů v systému Linux Subsystem pomocí vašeho oblíbeného operačního systému Microsoft Windows dále v této knize.

  - **Nástroje s otevřeným** zdrojovým kódem Vzhledem k tomu, že AKS zveřejňuje standardní koncové body rozhraní API pro modul orchestrace, nejoblíbenější nástroje jsou kompatibilní s AKS a ve většině případů budou fungovat izv.

  - **Azure Monitor** Je řešení Azure pro monitorování každého úhlu vašeho produkčního prostředí. Produkční aplikace Dockeru můžete sledovat pouhým nastavením sady SDK do svých služeb, abyste z aplikací mohli získat data protokolu generovaná systémem.

Microsoft tedy nabízí kompletní základ pro komplexní kontejnerizovaný životní cyklus aplikací Dockeru. Jedná se však *o kolekci produktů a technologií, které umožňují volitelně vybírat a integrovat se stávajícími nástroji a procesy*. Flexibilita v širokém přístupu spolu se silou v hloubce schopností staví Microsoft do silné pozice pro kontejnerizovaný vývoj aplikací Dockeru.

>[!div class="step-by-step"]
>[Předchozí](../Docker-application-lifecycle/containers-foundation-for-devops-collaboration.md)
>[další](../design-develop-containerized-apps/index.md)
