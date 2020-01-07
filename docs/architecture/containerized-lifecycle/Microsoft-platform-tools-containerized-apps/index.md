---
title: Úvod k platformě a nástrojům Microsoft pro kontejnerizované aplikace
description: Získejte informace o tom, jak Microsoft nabízí podporu životního cyklu aplikací Docker.
ms.date: 02/15/2019
ms.openlocfilehash: 9c8c0f5688bf226351abfc7bf52d4ace05f8c6d8
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/06/2020
ms.locfileid: "73738086"
---
# <a name="introduction-to-the-microsoft-platform-andtools-for-containerized-apps"></a>Seznámení s platformou a nástroji Microsoftu pro kontejnery aplikací

*Vize: Vytvořte adaptivní životní cyklus aplikací na podnikové úrovni, který pokrývá vývoj, IT operace a správu výroby.*

Obrázek 3-1 ukazuje hlavní pilíře v životním cyklu aplikací Docker klasifikovaných podle typu práce, kterou doručí více týmů (vývoj aplikací, procesy infrastruktury DevOps a správa IT a operace). V podniku obvykle jsou profily "osoby" zodpovědné za jednotlivé oblasti jiné. Takže jsou jejich dovednosti.

:::image type="complex" source="./media/index/microsoft-tools-contanerized-docker-app.png" alt-text="Diagram znázorňující nástroje Microsoftu potřebné k údržbě aplikací Docker":::
Nástroje společnosti Microsoft. Pro úlohy pro vývoj/navrhování: modul Docker pro Windows, VS a VS Code, .NET Core, Azure Kubernetes Service. Pro úlohy sestavení/testování/expedice: Azure DevOps, Team Foundation Server, Docker CLI, Azure Kubernetes Service. Pro úlohy spustit/monitor/spravovat: Azure Monitor, Azure Portal Azure Kubernetes Services, Service Fabric, dalších orchestrers.
:::image-end:::

**Obrázek 3-1.** Hlavní pilíře v životním cyklu pro kontejnerové aplikace Docker s platformou a nástroji Microsoftu

Kontejnerový pracovní postup Docker pro životní cyklus může být zpočátku zavedený podle výchozího nastavení produktu, což vývojářům usnadňuje rychlejší spuštění, ale je důležité, aby v digestoři existovala otevřená architektura, která bude flexibilní pracovní postupy, které je možné upravit na různé kontexty z každé organizace nebo podniku. Infrastruktura pracovního postupu (komponenty a produkty) musí být dostatečně flexibilní, aby pokryla prostředí, které bude mít každá společnost v budoucnu, a dokonce i to, že by bylo možné vyměnit vývoj nebo DevOps produkty jiným uživatelům. Tato flexibilita, možnosti otevření a širokou škálu technologií v infrastruktuře a infrastruktury jsou přesně priority Microsoftu pro kontejnerované aplikace Docker, jak je vysvětleno v kapitolách, které následují.

Tabulka 3-1 ukazuje, že záměrem programu Microsoft DevOps pro kontejnerové aplikace Docker je poskytnout otevřený pracovní postup DevOps, abyste si mohli vybrat, jaké produkty se mají použít pro každou fázi (Microsoft nebo třetí stranu) a zároveň zajistit zjednodušený pracovní postup. který poskytuje "po-výchozí-Products", které jsou už připojené; Proto můžete rychle začít s pracovním postupem DevOps na podnikové úrovni pro aplikace Docker.

**Tabulka 3-1.** DevOps pracovní postupy, které se otevřou v jakékoli technologii

| Hostitel | Technologie Microsoftu | Třetí strana – připojit k Azure |
| ---------------------------| ----------------------------------------------------| --------------------------------------------------------------------------------|
| Platforma pro aplikace Docker   | • Microsoft Visual Studio a Visual Studio Code<br /> • .NET<br /> • Microsoft Azure služba Kubernetes (AKS)<br /> • Service Fabric Azure<br /> • Azure Container Registry<br /> | • Jakýkoliv Editor kódu (například subvápno)<br /> • Libovolný jazyk (Node. js, Java, přejít atd.)<br /> • Všechny nástroje Orchestrator a Scheduler<br /> • Libovolný registr Docker<br /> |
| DevOps pro aplikace Docker     | • Azure DevOps Services<br /> • Microsoft Team Foundation Server<br /> • Služba Azure Kubernetes (AKS)<br /> • Service Fabric Azure<br /> | • GitHub, Git, podverze atd.<br /> • Jenkinse, Puppet, rychlost, CircleCI, Travis CI atd.<br /> • Místní prostředí Docker Datacenter, Docker Swarm, Mesos DC/OS, Kubernetes atd.<br /> |
| Monitorování a správa  | • Azure Monitor | • Marathon, Chronos atd.<br />|

Platforma a nástroje Microsoftu pro kontejnerové aplikace Docker, jak je definováno v tabulce 3-1, tvoří tyto komponenty:

- **Platforma pro vývoj aplikací Docker** Vývoj služby nebo kolekce služeb, které tvoří aplikaci. Vývojová platforma poskytuje všem pracovním vývojářům, aby před odesláním kódu do úložiště sdíleného kódu používali. Vývoj služeb, které jsou nasazené jako kontejnery, je podobný vývoji stejných aplikací nebo služeb bez Docker. Budete nadále používat preferovaný jazyk (.NET, Node. js, přejít atd.) a upřednostňovaný Editor nebo rozhraní IDE, jako je například Visual Studio nebo Visual Studio Code. Místo toho ale zvažte možnost Docker cíle nasazení, vyvíjíte své služby v prostředí Docker. Sestavíte, spouštíte, otestujete a ladíte kód v kontejnerech místně a poskytujete cílové prostředí v době vývoje. Tím, že se cílové prostředí poskytuje místně, kontejnery Docker nastavily, co se významně pomůže zlepšit životní cyklus DevOps. Visual Studio a Visual Studio Code mají rozšíření pro integraci kontejnerů Docker v rámci procesu vývoje.

- **DevOps pro aplikace Docker** Vývojáři vytvářející aplikace Docker můžou použít [Azure DevOps Services](https://azure.microsoft.com/services/devops/) nebo jakýkoli jiný produkt třetí strany, jako je Jenkinse, a sestavit komplexní automatizovanou správu životního cyklu aplikací (ALM).

  Pomocí Azure DevOps Services mohou vývojáři vytvořit DevOps zaměřené na kontejner pro rychlý a iterativní proces, který pokrývá řízení zdrojového kódu odkudkoli (Azure DevOps Services-Git, GitHub, libovolné vzdálené úložiště Git nebo dílčí verze), průběžná integrace (CI), interní testy jednotek, mezikontejnerové a integrační testy, průběžné doručování (CD) a Správa vydaných verzí (RM). Vývojáři také mohou automatizovat své verze aplikace Docker ve službě Azure Kubernetes Service (AKS), od vývoje až po pracovní a produkční prostředí.

- **Správa a monitorování** Může spravovat a monitorovat produkční aplikace a služby několika způsoby integrací obou perspektiv do konsolidovaného prostředí.

  - **Azure Portal** Pokud používáte Open Source orchestrace, služba Azure KUBERNETES (AKS), Service Fabric a další orchestrace vám pomůžou nastavit a udržovat vaše prostředí Docker. Pokud používáte Azure Service Fabric, nástroj Service Fabric Explorer umožňuje vizualizovat a konfigurovat cluster.

  - **Nástroje docker** můžete spravovat své aplikace kontejneru pomocí známých nástrojů. Pokud chcete přesunout úlohy kontejneru do cloudu, není potřeba měnit stávající postupy pro správu Docker. Použijte nástroje pro správu aplikací, které už znáte, a připojte se přes standardní koncové body rozhraní API pro Orchestrator podle vašeho výběru. Můžete také použít další nástroje třetích stran ke správě aplikací Docker, jako je Docker Datacenter nebo dokonce nástroje CLI Docker.

    I v případě, že jste obeznámeni s příkazy pro Linux, můžete spravovat aplikace typu kontejner pomocí Microsoft Windows a PowerShellu s příkazovým řádkem pro subsystém Linux a produkty (Docker, Kubernetes...), které jsou spuštěné v této schopnosti subsystému Linux. Další informace o těchto nástrojích najdete v části subsystém Linux pomocí svého oblíbeného operačního systému Microsoft Windows dále v této příručce.

  - **Open Source nástroje** protože AKS zpřístupňuje standardní koncové body rozhraní API pro modul Orchestration, nejoblíbenější nástroje jsou kompatibilní s AKS a ve většině případů budou fungovat i v případě, že jsou k dispozici, včetně nástrojů pro vizualizaci, monitorování, nástrojů příkazového řádku a dokonce i budoucích nástrojů.

  - **Azure monitor** Je řešení Azure pro monitorování každého úhlu produkčního prostředí. Aplikace v produkčním prostředí můžete monitorovat pouhým nastavením své sady SDK na vaše služby, abyste mohli z aplikací získat data protokolu generovaná systémem.

Proto Microsoft nabízí ucelenou základnu pro kompletní kontejnerový životní cyklus aplikací Docker. Jedná se však o *kolekci produktů a technologií, které vám umožní vybrat a integrovat s existujícími nástroji a procesy*. Flexibilita širokého přístupu společně s silou v hloubkě možností je Microsoft na silném místě pro vytváření kontejnerů aplikací Docker.

>[!div class="step-by-step"]
>[Předchozí](../Docker-application-lifecycle/containers-foundation-for-devops-collaboration.md)
>[Další](../design-develop-containerized-apps/index.md)
