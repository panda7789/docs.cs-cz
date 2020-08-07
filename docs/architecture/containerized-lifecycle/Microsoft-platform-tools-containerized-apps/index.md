---
title: Úvod k platformě a nástrojům Microsoft pro kontejnerizované aplikace
description: Získejte informace o tom, jak Microsoft nabízí podporu životního cyklu aplikací Docker.
ms.date: 08/06/2020
ms.openlocfilehash: 72b98f945494936b7775a525297a17c5ce72c69a
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916064"
---
# <a name="introduction-to-the-microsoft-platform-andtools-for-containerized-apps"></a>Úvod k platformě a nástrojům Microsoft pro kontejnerizované aplikace

*Vize: Vytvořte adaptivní životní cyklus aplikací na podnikové úrovni, který pokrývá vývoj, IT operace a správu výroby.*

Obrázek 3-1 ukazuje hlavní pilíře v životním cyklu aplikací Docker klasifikovaných podle typu práce, kterou doručí více týmů (vývoj aplikací, procesy infrastruktury DevOps a správa IT a operace). V podniku obvykle jsou profily "osoby" zodpovědné za jednotlivé oblasti jiné. Takže jsou jejich dovednosti.

![Přidejte nové okno projektu v aplikaci Visual Studio a vyberte ASP.NET Core webové aplikace.](media/index/microsoft-tools-contanerized-docker-app.png)

**Obrázek 3-1.** Hlavní pilíře v životním cyklu pro kontejnerové aplikace Docker s platformou a nástroji Microsoftu

Kontejnerový pracovní postup Docker pro životní cyklus může být zpočátku doporučený pro vývojáře na základě výchozích možností produktu, což vývojářům usnadňuje rychlejší zprovoznění, ale je důležité, aby v digestoři existovala otevřená architektura, která bude flexibilní pracovní postup schopný upravit na různé kontexty z každé organizace nebo podniku. Infrastruktura pracovního postupu (komponenty a produkty) musí být dostatečně flexibilní, aby pokryla prostředí, které bude mít každá společnost v budoucnu, a dokonce i to, že by bylo možné vyměnit vývoj nebo DevOps produkty jiným uživatelům. Tato flexibilita, možnosti otevření a širokou škálu technologií v rámci platformy a infrastruktury jsou přesně priority Microsoftu pro kontejnerované aplikace Docker, jak je vysvětleno v kapitolách, které následují.

Tabulka 3-1 ukazuje, že záměrem Azure DevOps pro kontejnerové aplikace Docker je poskytnout otevřený pracovní postup DevOps, abyste si mohli vybrat produkty, které se mají použít pro každou fázi (Microsoft nebo třetí straně), a současně poskytovat zjednodušený pracovní postup, který poskytuje "" po "výchozím" produktům ", které jsou už připojené. Proto můžete rychle začít s pracovním postupem DevOps na podnikové úrovni pro aplikace Docker.

**Tabulka 3-1.** Pracovní postupy Azure DevOps, které se otevřou v jakékoli technologii

| Hostitel | Technologie Microsoftu | Třetí strana (připojit k Azure) |
| ---------------------------| ----------------------------------------------------| --------------------------------------------------------------------------------|
| Platforma pro aplikace Docker   | • Microsoft Visual Studio a Visual Studio Code<br /> • .NET<br /> • Microsoft Azure služba Kubernetes (AKS)<br /> • Azure Container Registry<br /> | • Jakýkoliv Editor kódu (například subvápno)<br /> • Libovolný jazyk (Node.js, Java, jít atd.)<br /> • Všechny nástroje Orchestrator a Scheduler<br />  • Libovolný registr Docker<br /> |
| DevOps pro aplikace Docker     | • Azure DevOps Services<br /> • Microsoft Team Foundation Server<br /> • Služba Azure Kubernetes (AKS)<br /> | • GitHub, Git, podverze atd.<br /> • Jenkinse, Puppet, rychlost, CircleCI, Travis CI atd.<br /> • Místní prostředí Docker Datacenter, Kubernetes, Mesos DC/OS atd.<br /> |
| Správa a monitorování  | • Azure Monitor | • Marathon, Chronos atd.<br />|

Platforma a nástroje Microsoftu pro kontejnerové aplikace Docker, jak je definováno v tabulce 3-1, tvoří tyto komponenty:

- **Platforma pro vývoj aplikací Docker** Vývoj služby nebo kolekce služeb, které tvoří aplikaci. Vývojová platforma poskytuje všem pracovním vývojářům, aby před odesláním kódu do úložiště sdíleného kódu používali. Vývoj služeb, které jsou nasazené jako kontejnery, je podobný vývoji stejných aplikací nebo služeb bez Docker. Nadále používáte preferovaný jazyk (.NET, Node.js, přejít atd.) a preferovaný Editor nebo IDE, jako je Visual Studio nebo Visual Studio Code. Místo toho ale zvažte možnost Docker cíle nasazení, vyvíjíte své služby v prostředí Docker. Sestavíte, spouštíte, otestujete a ladíte kód v kontejnerech místně a poskytujete cílové prostředí v době vývoje. Tím, že se cílové prostředí poskytuje místně, kontejnery Docker nastavily, co se významně pomůže zlepšit životní cyklus DevOps. Visual Studio a Visual Studio Code mají rozšíření pro integraci kontejnerů Docker v rámci procesu vývoje.

- **DevOps pro aplikace Docker** Vývojáři vytvářející aplikace Docker můžou použít [Azure DevOps](https://azure.microsoft.com/services/devops/) nebo jakýkoli jiný produkt třetí strany, jako je Jenkinse, a vytvořit tak komplexní automatizovanou správu životního cyklu aplikací (ALM).

  S Azure DevOps můžou vývojáři vytvořit DevOps zaměřený na kontejner pro rychlý a iterativní proces, který pokrývá řízení zdrojového kódu odkudkoli (Azure DevOps – Git, GitHub, jakékoli vzdálené úložiště Git nebo dílčí verze), průběžná integrace (CI), interní testy jednotek, mezikontejnerové a integrační testy, průběžné doručování (CD) a Správa vydaných verzí (RM). Vývojáři také mohou automatizovat své verze aplikace Docker ve službě Azure Kubernetes Service (AKS), od vývoje až po pracovní a produkční prostředí.

- **Správa a monitorování** Může spravovat a monitorovat produkční aplikace a služby několika způsoby integrací obou perspektiv do konsolidovaného prostředí.

  - **Azure Portal**   Služba Azure Kubernetes Service (AKS) vám pomůže nastavit a spravovat prostředí Docker. K vizualizaci a konfiguraci clusteru můžete použít také jiné orchestrace.

  - **Nástroje**   Docker Své aplikace kontejneru můžete spravovat pomocí známých nástrojů. Pokud chcete přesunout úlohy kontejneru do cloudu, není potřeba měnit stávající postupy pro správu Docker. Použijte nástroje pro správu aplikací, které už znáte, a připojte se přes standardní koncové body rozhraní API pro Orchestrator podle vašeho výběru. K správě aplikací Docker nebo dokonce nástrojů Docker rozhraní CLI můžete použít také další nástroje třetích stran.

    I v případě, že jste obeznámeni s příkazy pro Linux, můžete spravovat aplikace typu kontejner pomocí Microsoft Windows a PowerShellu s příkazovým řádkem pro subsystém Linux a produkty (Docker, Kubernetes...), které jsou spuštěné v této schopnosti subsystému Linux. Další informace o těchto nástrojích najdete v části subsystém Linux pomocí svého oblíbeného operačního systému Microsoft Windows dále v této příručce.

  - **Open Source nástroje**   Vzhledem k tomu, že AKS zpřístupňuje standardní koncové body rozhraní API pro modul Orchestration, nejoblíbenější nástroje jsou kompatibilní s AKS a ve většině případů budou fungovat mimo pole, včetně nástrojů pro vizualizaci, monitorování, nástrojů příkazového řádku a dokonce i budoucích nástrojů, jakmile budou k dispozici.

  - **Azure monitor** Je řešení Azure pro monitorování každého úhlu produkčního prostředí. Aplikace v produkčním prostředí můžete monitorovat pouhým nastavením své sady SDK na vaše služby, abyste mohli z aplikací získat data protokolu generovaná systémem.

Proto Microsoft nabízí ucelenou základnu pro kompletní kontejnerový životní cyklus aplikací Docker. Jedná se však o *kolekci produktů a technologií, které vám umožní vybrat a integrovat s existujícími nástroji a procesy*. Flexibilita širokého přístupu společně s silou v hloubkě možností je Microsoft na silném místě pro vytváření kontejnerů aplikací Docker.

>[!div class="step-by-step"]
>[Předchozí](../Docker-application-lifecycle/containers-foundation-for-devops-collaboration.md) 
> [Další](../design-develop-containerized-apps/index.md)
