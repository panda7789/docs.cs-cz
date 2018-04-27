---
title: Úvod do platformy Microsoft a nástrojů pro kontejnerové aplikace
description: Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 666d19717a29d9052be6dcd2b4c80a16f168569f
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="introduction-to-the-microsoft-platform-and-tools-for-containerized-apps"></a>Úvod do platformy Microsoft a nástrojů pro kontejnerové aplikace


Obrázek 3-1 zobrazuje hlavní pilíře v životním cyklu aplikace Docker klasifikované podle typu pracovní doručil více týmů (vývoj aplikací DevOps infrastruktury procesů a IT správu a operace). Obvykle v podnikové síti, profily "osobě" zodpovídá za každou oblast se liší. Proto jsou jejich znalostí.

![](./media/image1.png)

Obrázek 3-1: hlavní pilíře v životním cyklu kontejnerizované Docker aplikací s Microsoft platforma a nástroje

A kontejnerizované Docker životní cyklus pracovního postupu může být původně doporučený na základě "výchozím produktu voleb," usnadňuje vývojářům Začínáme rychlejší, ale je zásadní, pod pokličkou musí být otevřené rozhraní tak, aby byl flexibilní pracovního postupu schopná úpravě k odlišným kontextům z každé organizace nebo enterprise. Pracovní postup infrastruktury (součásti a produkty) musí být dostatečně flexibilní, tak, aby pokrývalo prostředí, ve kterém každá společnost má v budoucnu, i jsou schopny odkládací vývoj nebo DevOps produkty ostatním uživatelům. Tuto flexibilitu, průhlednost a široký výběr technologií platformy a infrastruktury jsou přesněji priority společnosti Microsoft pro kontejnerizované Docker aplikace, jak je popsáno v kapitolách, které následují.

Tabulka 3-1 ukazuje, že záměrem Microsoft DevOps pro kontejnerizované Docker aplikace je zajistit pracovním postupu otevřete DevOps, aby můžete vybrat, které produkty pro každou fázi (Microsoft nebo třetích stran) současně poskytují zjednodušenou pracovního postupu která zajišťuje, že již připojení "pomocí – výchozí – produkty"; Proto je můžete rychle začít s workflow DevOps podnikové úrovni pro Docker aplikace.

Tabulka 3-1: Otevřete DevOps pracovní postup jakékoli technologie

| Hostitel | Technologie Microsoft | Třetí strany – Azure modulární |
| ---------------------------| ----------------------------------------------------| --------------------------------------------------------------------------------|
| Platformu pro Docker aplikací   | • Sadu Microsoft Visual Studio a Visual Studio Code<br /> • .NET<br /> • Microsoft Azure Container Service<br /> • Azure Service Fabric<br /> • Kontejner azure registru<br /> | • Libovolného editoru kódu (například Sublime)<br /> • Žádný jazyk (Node.js, Java, přejděte atd.)<br /> • Všechny orchestrator a plánovače<br /> • Žádné Docker registru<br /> |
| DevOps pro aplikace Docker     | • Visual Studio Team Services<br /> • Microsoft Team Foundation Server<br /> • Azure Container Service<br /> • Azure Service Fabric<br /> | • Githubu, Git, Subversion, atd.<br /> • Volaných, Chef, Puppet, rychlosti, CircleCI, TravisCI atd.<br /> • Místní Docker Datacentra, pomocí Docker Swarm, Mesos DC/OS, Kubernetes, atd.<br /> |
| Správa a sledování  | • Operations Management Suite<br /> • Aplikace statistiky<br /> | • Marathon, Chronos, atd.<br />

Platforma Microsoft a nástroje pro kontejnerizované Docker aplikace, jak jsou definovány v tabulce 3-1, tvoří následující součásti:

-   **Platformu pro vývoj aplikací Docker** vývoj služby nebo kolekce služeb, které tvoří "aplikace". Vývoj pro platformu poskytuje všechny pracovní vývojáři vyžaduje před nabízení svůj kód do úložiště sdíleného kódu. Vývoj služby, které jsou nasazeny jako kontejnery, jsou velmi podobné s vývojem stejné aplikací nebo služeb bez Docker. Můžete nadále používat upřednostňovaný jazyk (.NET, Node.js, přejděte atd.) a upřednostňované editor nebo IDE jako Visual Studio nebo Visual Studio Code. Místo zvažte Docker cíl nasazení, ale vyvíjíte vašim službám v prostředí Docker. Vytvoření, spuštění, testování a ladění kódu v kontejnerech místně, poskytuje cílové prostředí v době vývoje. Zadáním cílového prostředí místně Docker kontejnery nastavte co bude výrazně vám pomůžou líp vaší DevOps životní cyklus. Visual Studio a Visual Studio Code mít rozšíření pro integraci kontejnery Docker v rámci vývojových procesech.

-   **DevOps pro aplikace Docker** vytváření aplikací pro Docker mohou vývojáři Visual Studio Team Services (VSTS) nebo libovolné jiné třetích stran, jako volaných, k vytvoření se o komplexní automatizovaná správa životního cyklu aplikací (ALM).

Pomocí služby VSTS, vývojáři můžou vytvářet DevOps zaměřené na kontejner pro rychlé, iterativní proces, který obsahuje zdrojový kód řízení odkudkoli (služby VSTS Git, GitHub, všechny vzdálené úložiště Git nebo Subversion), nepřetržité integrace konfigurace, testy částí interní, mimo kontejner nebo Služba integrace testy, průběžné doručování (CD) a správy verzí (RM). Vývojáři taky můžete automatizovat verze jejich Docker aplikace do Azure Container Service z vývojového do pracovní a provozní prostředí.

-   IT produkční správy a monitorování.

**Správa** IT může spravovat výrobní aplikace a služby v několika způsoby:

-   **Portál Azure** Pokud používáte orchestrators open source, Azure Container Service (ACS) a nástroje pro správu clusteru jako Docker Datacenter a Mesosphere Marathon dozvíte, jak nastavit a spravovat vaše Docker prostředí. Pokud používáte Azure Service Fabric, nástroj Service Fabric Exploreru umožňuje vizualizovat a nakonfigurovat cluster.

-   **Nástroje docker** můžete spravovat vaše aplikace typu kontejner pomocí známých nástrojů. Není potřeba změnit vaše stávající postupy správy Docker přesouvat úlohy kontejneru do cloudu. Pomocí nástrojů pro správu aplikaci jste již obeznámeni s a připojení přes standardní koncové body rozhraní API pro nástroj orchestrator podle svého výběru. Také můžete jiné nástroje třetích stran ke správě Docker aplikací, jako jsou i nástroje příkazového řádku Dockeru nebo Docker Datacenter.

-   **Open source nástroje** protože ACS vystavuje jsou standardní koncové body rozhraní API pro jádro Orchestrace, nejoblíbenější nástroje jsou kompatibilní se službou ACS a ve většině případů bude fungovat ihned – včetně vizualizérech, monitorování, nástroje příkazového řádku a to i budoucí nástroje Jakmile budou k dispozici.

**Monitorování** přitom běží provozní prostředí, můžete sledovat všechny úhel pomocí následujícího:

-   **Operations Management Suite (OMS)** "Kontejneru řešení OMS" můžete spravovat a monitorovat hostitelů Docker a kontejnerů, tím, že zobrazuje informace o tom, kde jsou kontejnerů a kontejner hostitelů, které kontejnery jsou spuštěné nebo neúspěšný, a protokoly démon a kontejner Docker. Také ukazuje metriky výkonu, jako je například procesoru, paměti, sítě a úložiště pro kontejner a hostitelů, které vám pomohou vyřešit a najít aktivní sousedním kontejnery.

-   **Application Insights** můžete monitorovat aplikace Docker produkční jednoduše nastavením její SDK do služeb, abyste měli telemetrická data z aplikací.

Proto společnost Microsoft nabízí kompletní základ pro začátku do konce kontejnerizované Docker životního cyklu aplikace. Je však *kolekce produkty a technologie, které vám umožní volitelně vybrat a integrovat s existujícím nástroje a zpracuje*. Flexibilita při široký přístup spolu s sílu podrobněji možnosti umístění Microsoft silné polohy pro vývoj aplikací kontejnerizované Docker.

>[!div class="step-by-step"]
[Předchozí] (.. / Docker-application-lifecycle/containers-foundation-for-devops-collaboration.md) [Další] (.. /Design-Develop-containerized-Apps/index.MD)
