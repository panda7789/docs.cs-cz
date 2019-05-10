---
title: Úvod k platformě a nástrojům Microsoft pro kontejnerizované aplikace
description: Seznamte se nabídky společnosti Microsoft pro podporu životního cyklu aplikace Dockeru.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: cdaac06ffd907783c7ebe9b62ecd726158a02484
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664385"
---
# <a name="introduction-to-the-microsoft-platform-andtools-for-containerized-apps"></a>Úvod do Microsoft platformu a nástroje pro kontejnerizované aplikace

*Pro zpracování obrazu: Vytvořit přizpůsobitelnou, podnikové úrovni, kontejnerizovaných životního cyklu aplikace, která zahrnuje vývoj, provoz IT a řízení výroby.*

Obrázek 3-1 zobrazuje hlavní pilíře v životním cyklu aplikace Dockeru klasifikuje typu práce od několika týmů (vývoj aplikací, infrastruktury procesy DevOps a správy IT a operace). Obvykle v podnikové síti, profily "osoba" zodpovídá za každou oblast, kterou se liší. Proto jsou své dovednosti.

![Nástroje sady Microsoft. Pro vývoj a návrh úlohy: Modul docker pro Windows, VS a VS Code, .NET Core, Azure Kubernetes Service. Úlohy sestavení/testovací/příjemce: Azure DevOps, Team Foundation Server, Docker CLI, Azure Kubernetes Service. Spuštění/monitorování a Správa úloh: Azure Monitor, Azure Portal Azure Kubernetes Services, Service Fabric, jiné orchestrátory.](./media/image1.png)

**Obrázek 3-1.** Hlavní pilíře v životní cyklus kontejnerizované aplikace Dockeru s platformou a nástroji Microsoft

Pracovní životní cyklus kontejnerizované Docker může být zpočátku doporučené na základě "ve výchozím nastavení produkt voleb," usnadňuje vývojářům začít pracovat rychleji, ale je zásadní pro pod pokličkou musí obsahovat otevřené rozhraní tak, že bude flexibilní pracovní postup umožňující úpravy do různých kontextech z každé organizace nebo podniku. Pracovní postup infrastruktury (součásti a produkty) musí být dostatečně flexibilní, aby pokryl prostředí, které každá společnost má v budoucnu, i jsou schopny prohození vývoj nebo DevOps produktů pro ostatní. Této flexibility, otevřenost a širokou škálu technologií v platforma a infrastruktura jsou přesně priority společnosti Microsoft pro kontejnerizované aplikace Dockeru, jak je vysvětleno v kapitolách, které následují.

Tabulka 3-1 ukazuje, že záměr Microsoft DevOps pro kontejnerizované aplikace Dockeru je poskytnout otevřený pracovních postupů DevOps tak, aby můžete zvolit, jaké produkty pro každou fázi (společnosti Microsoft nebo třetích stran) poskytuje zjednodušenou pracovního postupu který poskytuje již připojen "ve výchozí produktů"; Proto je můžete rychle začít s pracovních postupů DevOps podnikové úrovni pro aplikace Dockeru.

**Tabulka 3-1.** Pracovní postupy DevOps, otevřete všechny technologie

| Hostitel | Technologie společnosti Microsoft | Třetí strany, modulární Azure |
| ---------------------------| ----------------------------------------------------| --------------------------------------------------------------------------------|
| Platforma pro aplikace Dockeru   | • Microsoft Visual Studio a Visual Studio Code<br /> • .NET<br /> • Microsoft Azure Container Service<br /> • Azure Service Fabric<br /> • Azure Container Registry<br /> | • Libovolný editor kódu (například Sublime)<br /> • Libovolný jazyk (Node.js, Java, Go, atd.)<br /> • Všechny nástroje orchestrator a Plánovač<br /> • Jakýkoli registr Dockeru<br /> |
| DevOps pro aplikace Dockeru     | • Služby azure DevOps<br /> • Microsoft Team Foundation Server<br /> • Azure Container Service<br /> • Azure Service Fabric<br /> | • Githubu, Git, Subversion, atd.<br /> • Jenkinse, Chef, Puppet, rychlost, CircleCI, travis ci, atd.<br /> • V místním datovém centru Dockeru, Docker Swarm, Mesos DC/OS, Kubernetes, atd.<br /> |
| Monitorování a Správa  | Monitorování • azure | • Marathon, Chronos, atd.<br />|

Microsoft platformu a nástroje pro kontejnerizované aplikace Dockeru, jak je definováno v tabulce 3-1, zahrnuje následující součásti:

- **Platforma pro vývoj aplikace v Dockeru** vývoj služby nebo kolekce služeb, které tvoří "aplikace". Vývojová platforma poskytuje všem vývojářům práci vyžaduje před doručením (push) kód úložiště sdíleného kódu. Vývoj služby nasazené jako kontejnery, jsou podobné vývoj stejným aplikacím nebo službám bez Dockeru. Můžete dál používat upřednostňovaném jazyce (.NET, Node.js, Go, atd.) a preferovaného editoru nebo prostředí IDE, jako je Visual Studio nebo Visual Studio Code. Ale spíše než zvažte Docker cíl nasazení, při vývoji vašich služeb v prostředí Docker. Sestavení, spuštění, testování a ladění kódu v kontejnerech místně, poskytování cílového prostředí v době vývoje. Zadáním cílového prostředí místně kontejnery Dockeru nastavte co výrazně pomůžou zlepšit váš životní cyklus DevOps. Visual Studio a Visual Studio Code jsou rozšíření integrace kontejnerů Dockeru v rámci vašeho vývojového procesu.

- **DevOps pro aplikace Dockeru** vývojáře vytvářející aplikace Docker můžete použít [Azure DevOps služby](https://azure.microsoft.com/services/devops/) a všechny ostatní třetích stran produkty, jako je Jenkins, k sestavení životního cyklu komplexní automatické aplikaci Správa (aplikací ALM).

  Azure DevOps Services umožňuje vývojářům vytvářet zaměřené na kontejner řídit vývoj a provoz pro rychlý a iterativní proces, který obsahuje zdrojový kód z libovolného místa (Azure DevOps služby-Git, GitHub, žádné vzdálené úložiště Git nebo Subversion), kontinuální integrace (CI) , interní jednotkové testy, testy container mezi, služba integrace, průběžné doručování (CD) a produktu release management (SV). Vývojáři taky můžete automatizovat verzí jejich Docker aplikace do Azure Container Service, od vývoje do přípravného a produkčního prostředí.

- **Správa a monitorování** IT můžete spravovat a monitorovat aplikace v produkčním prostředí a služeb několika způsoby integrace obou perspektivy v sjednocené prostředí.

  - **Azure portal** Pokud používáte open source orchestrátorů, Azure Kubernetes Service (AKS), Service Fabric a jiných orchestrátorů vám pomůžou nastavit a spravovat prostředí Docker. Pokud používáte Azure Service Fabric, nástroj Service Fabric Explorer umožňuje vizualizovat a konfigurace clusteru.

  - **Nástroje dockeru** můžete spravovat vaše aplikace typu kontejner pomocí známých nástrojů. Není nemusíte měnit svoje dosavadní postupy správy Docker chcete přesunout úlohy kontejnerů do cloudu. Pomocí nástroje pro správu aplikace už znáte a připojte se pomocí standardních koncových bodů rozhraní API k orchestrátoru podle vaší volby. Další nástroje třetích stran také můžete použít ke správě aplikace v Dockeru, jako je například Docker Datacenter nebo dokonce nástroje rozhraní příkazového řádku Dockeru. 

    I v případě, že jste obeznámeni s Linux příkazy, můžete spravovat vašich kontejnerových aplikací pomocí Microsoft Windows a prostředí PowerShell s Linux podsystému příkazového řádku a produkty (Docker, Kubernetes...) klientů běžících na tuto funkci Linux podsystému. Můžete se dozvíte víc o použití těchto nástrojů v systému Linux podsystému pomocí oblíbeném operačním systému Microsoft Windows dále v této příručce.

  - **Open source nástroje** protože AKS zpřístupňuje standardní koncové body rozhraní API pro orchestrační modul, nejoblíbenější opensourcové nástroje jsou kompatibilní s AKS a ve většině případů fungují bez pole, včetně vizualizátorů, sledování, nástroje příkazového řádku a taky budoucích nástrojů, jakmile budou k dispozici.

  - **Azure Monitor** řešení je Azure ke sledování všech možných úhlů vašeho produkčního prostředí. Nastavením jenom její SDK do vaší služby tak, aby data systémem generovaných protokolů můžete získat z aplikace můžete monitorovat aplikace v produkčním prostředí Docker.

Proto Microsoft nabízí kompletní foundation začátku do konce kontejnerizovaných Docker životního cyklu aplikace. Je však *kolekce produktů a technologií, které můžete volitelně vybrat a integrace s existujícím nástroje a procesy*. Flexibilitu v rámci široké přístupu spolu s sílu do hloubky možnosti umístění Microsoft strong polohy pro vývoj kontejnerizovaných aplikací Dockeru.

>[!div class="step-by-step"]
>[Předchozí](../Docker-application-lifecycle/containers-foundation-for-devops-collaboration.md)
>[další](../design-develop-containerized-apps/index.md)
