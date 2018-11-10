---
title: Orchestrace mikroslužeb a vícekontejnerových aplikací pro vysokou škálovatelnost a dostupnost
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Orchestrace mikroslužeb a vícekontejnerových aplikací pro vysokou škálovatelnost a dostupnost
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 25175e2a4409d53be412ae72be5af1c07c3ec68d
ms.sourcegitcommit: 296183dbe35077b5c5e5e74d5fbe7f399bc507ee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2018
ms.locfileid: "50982773"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Orchestrace mikroslužeb a vícekontejnerových aplikací pro vysokou škálovatelnost a dostupnost

Využitím orchestrátorů, pro aplikace připravené pro produkční prostředí je nezbytné, pokud je vaše aplikace založené na mikroslužbách nebo jednoduše rozdělit mezi několik kontejnerů. Zavedeném dříve, v rámci přístupu založených na mikroslužbách vlastní jednotlivých mikroslužeb jeho modelu a datům tak, aby ho autonomní od vývoje a nasazení pohledu. Ale i v případě, že máte více tradiční aplikace, který se skládá z několika služeb (např. SOA), budou mít také více kontejnerů nebo služby vytvářející jednu obchodní aplikaci, která je nutné nasadit jako distribuovaný systém. Tyto druhy systémy jsou komplexní horizontální navýšení kapacity a Správa; Proto pokud chcete mít vícekontejnerová aplikace připravené pro produkční prostředí a škálovatelné se naprosto je nutné orchestrátor.

Obrázek 4 – 23 ukazuje nasazení do clusteru aplikace skládá z několika mikroslužeb (kontejnery).

![](./media/image23.PNG)

**Obrázek 4 – 23**. Cluster kontejnerů

Vypadá jako logický přístup. Ale jak se vyrovnávání zatížení zpracování, směrování a orchestraci těchto aplikací skládá?

Prostý modul Docker v jedné hostitelů Docker splňuje potřeby správu instancí jedné image na jednom hostiteli, ale vrátí krátký se při rozhodování o Správa více kontejnerů, které jsou nasazeny na více hostitelích pro složitější distribuované aplikace. Ve většině případů je třeba platforma pro správu, který bude automaticky spustit kontejnery, kontejnery horizontální navýšení kapacity s více instancemi za image, je pozastavit nebo vypnout v případě potřeby a v ideálním případě také určují, jak bude přístup k prostředkům, jako je síť a data úložiště.

Se dostat nad rámec správu jednotlivých kontejnerů nebo velmi jednoduché složené aplikace a přesun směrem k větší podnikové aplikace s využitím mikroslužeb, musíte povolit orchestraci a clustering platformy.

Z pro architekturu a vývoj pohledu Pokud vytváříte velký podnik skládá z aplikací založených na mikroslužbách, je důležité pochopit následující platformy a produkty, které podporují pokročilé scénáře:

**Clustery a orchestrátorů**. Když potřebujete pro horizontální navýšení kapacity aplikace v mnoha hostitelích Dockeru, jako při velkých aplikací založených na mikroslužbách, je důležité mít možnost spravovat všechny tyto hostitele jako jeden cluster podle abstrahovat složitost základní platformy. Je to, co nabízejí clustery kontejnerů a orchestrátorů. Příklady orchestrátorů: Azure Service Fabric, Kubernetes, Docker Swarm a Mesosphere DC/OS. Poslední tři open source orchestrátorů jsou dostupné v Azure pomocí Azure Container Service.

**Plánovači**. *Plánování* znamená, že chcete mít možnost pro správce ke spuštění kontejnerů v clusteru, tak také poskytují uživatelské rozhraní. Plánovač clusteru má několik odpovědnosti: efektivně využívat prostředky clusteru, omezení zadaná uživatelem pro efektivní kontejnery pro vyrovnávání zatížení napříč uzly nebo hostitele a být odolnější proti chybám při zajištění vysoké dostupnost.

Koncepty cluster a Plánovač jsou úzce souvisí, takže produkty k dispozici od různých dodavatelů často zadat obě sady funkcí. Následující seznam obsahuje nejdůležitější platformy a software volby, které máte pro clustery a plánovače. Tyto orchestrátorů se obvykle nabízejí ve veřejných cloudech, jako je Azure.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Softwarové platformy pro kontejner clustering, orchestraci a plánování

Kubernetes

![Kubernetes logo](./media/image24.png)

> Kubernetes je opensourcový produkt, který poskytuje funkce, které od infrastruktura clusteru a plánování k funkcím orchestrací kontejnerů. Umožňuje vám automatizovat nasazování, škálování a provoz kontejnerů aplikací napříč clustery hostitelů.
>
> Kubernetes poskytuje infrastrukturu zaměřené na kontejner, který seskupuje kontejnerů aplikací do logické jednotky pro snadnou správu a zjišťování.
>
> Kubernetes je zavedený v systému Linux, méně až po zralé ve Windows.

Docker Swarm

![Docker Swarm logo](./media/image25.png)

> Docker Swarm umožňuje clusteru a plánovat kontejnery Dockeru. Pomocí Swarm můžete zapnout fondu hostitelů Docker do jednoho, virtuálního hostitele Dockeru. Klienti mohli požadavků rozhraní API pro Swarm stejným způsobem, že se že dělají na hostitele, což znamená, že Swarm usnadňuje aplikacím škálování na více hostitelích.
>
> Docker Swarm je produkt z Dockeru, společnost.
>
> Docker v1.12 nebo novější můžete spouštět nativní a integrované režimu Swarm.

Mesosphere DC/OS

![Logo mesosphere DC/OS](./media/image26.png)

> Mesosphere Enterprise DC/OS (založená na Apache Mesos) je platforma pro produkční prostředí pro spouštění kontejnerů a distribuovaných aplikací.
>
> DC/OS, funguje tak, že poskytuje abstrakci kolekci prostředků, které jsou k dispozici v clusteru a zpřístupnění těchto prostředků komponenty sestavené dojde k jeho zvýraznění. Marathon se obvykle používá jako Plánovač integrovaná s DC/OS.
>
> DC/OS je zavedený v systému Linux, méně až po zralé ve Windows.

Azure Service Fabric

![Logo Azure Service Fabric](./media/image27.png)

> [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) je platforma mikroslužeb Microsoftu pro sestavování aplikací. Je [orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) ze služeb a vytváří clustery počítačů. Service Fabric dokáže nasadit služby, kontejnery nebo jako obyčejný procesy. Může dokonce kombinaci služby v procesech se službami v kontejnerech v rámci stejné aplikace a clusteru.
>
> Service Fabric nabízí další a volitelné doporučené [programovacích modelů Service Fabric ](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) jako [stavové služby](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) a [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).
>
> Service Fabric je zavedený ve Windows (roky vyvíjejí Windows), méně až po zralé v systému Linux. 
> Od verze 2017 jsou podporovány kontejnery Linux i Windows v Service Fabric.

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a>Pomocí orchestrátorů kontejneru ve službě Microsoft Azure

Několik dodavatelů cloud nabízí podporu kontejnerů Dockeru a Docker clusterů a podporu Orchestrace, včetně Microsoft Azure, Amazon EC2 Container Service a modul kontejnerů Google. Microsoft Azure podporuje Docker clusteru a orchestrator prostřednictvím Azure Container Service (ACS), jak je vysvětleno v další části.

Další volbou je použití Microsoft Azure Service Fabric (platforma mikroslužeb), který podporuje také založené na Linuxu a Windows kontejnery Dockeru. Service Fabric běží v Azure nebo na jiný cloud a povolí, poběží i [místní](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere).

## <a name="using-azure-container-service"></a>Pomocí služby Azure Container Service

Docker cluster fondy více hostitelů Docker a zpřístupňuje jako jednoho virtuálního hostitele Docker, abyste mohli nasadit několik kontejnerů do clusteru. Cluster bude zpracovávat složité správy základní, jako je škálovatelnost, stavu a tak dále. Obrázek 4 – 24 představuje, jak mapuje clusteru Docker pro složené aplikace do Azure Container Service (ACS).

ACS poskytuje způsob, jak zjednodušit vytváření, konfiguraci a správu clusterů virtuálních počítačů, které je předem nakonfigurované spouštění kontejnerizovaných aplikací. Použití optimalizovanou konfiguraci oblíbených nástrojů open source plánování a orchestraci, ACS vám umožní využívat své stávající dovednosti nebo nakreslit velké a stále se rozšiřujících odborných znalostech komunity k nasazení a správě kontejnerových aplikací v Microsoft Azure .

Služba Azure Container Service optimalizuje konfiguraci oblíbených opensourcových nástrojů clusteringu Dockeru a technologií konkrétně pro Azure. Získáte otevřené řešení, které nabízí přenositelnost pro vaše kontejnery i Konfigurace aplikací. Vyberete velikost, počet hostitelů a orchestrační nástroje a služby Container Service se postará o všechno ostatní.

![](./media/image28.png)

**Obrázek 4 – 24**. Clustering s možností ve službě Azure Container Service

ACS využívá Image Dockeru k zajištění, že plné přenositelnosti kontejnerů vaší aplikace. Podporuje možnost Orchestrace open-source platformy jako (používá technologii Apache Mesos) DC/OS, Kubernetes (původně vytvořil Google) a Docker Swarm, ujistěte se, že je možné tyto aplikace škálovat do tisíců nebo dokonce desítek tisíců kontejnerů.

Azure Container service můžete využívat výhody funkcí Azure na podnikové úrovni a přitom zachovávat přenositelnost aplikací, včetně v orchestračních vrstvách.

![](./media/image29.png)

**Obrázek 4 – 25**. Orchestrátorů v ACS

Jak ukazuje obrázek 4 – 25, Azure Container Service je jednoduše infrastruktury poskytovaný platformou Azure, abyste mohli nasadit DC/OS, Kubernetes a Docker Swarm, ale ACS neimplementuje žádné další nástroje orchestrator. Proto ACS není v důsledku toho orchestrátor jenom infrastruktura, která využívá existující open source orchestrátorů kontejnerů.

Z hlediska využití cílem služby Azure Container Service je poskytnout hostitelské prostředí kontejneru pomocí oblíbených opensourcových nástrojů a technologií. Za tímto účelem zpřístupňuje standardní koncové body rozhraní API pro zvolený orchestrátor. Pomocí těchto koncových bodů můžete využívat veškerý software, který může komunikovat s těmito koncovými body. V případě koncového bodu Docker Swarm můžete například použít rozhraní příkazového řádku (CLI) Dockeru. Pro DC/OS můžete zvolit použití rozhraní příkazového řádku DC/OS.

### <a name="getting-started-with-azure-container-service"></a>Začínáme se službou Azure Container Service 

Pokud chcete začít používat službu Azure Container Service, nasaďte cluster Azure Container Service z webu Azure portal s použitím šablony Azure Resource Manageru nebo [CLI](https://docs.microsoft.com/cli/azure/install-azure-cli). Dostupné šablony zahrnují [Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm), [Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes), a [DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos). Šablony rychlý start můžete upravit tak, aby zahrnout další nebo rozšířenou konfiguraci Azure. Další informace o nasazení clusteru Azure Container Service najdete v tématu [nasazení clusteru Azure Container Service](https://docs.microsoft.com/azure/container-service/container-service-deployment) na webu Azure.

Neexistují žádné poplatky za software ve výchozím nastavení nainstalované jako součást služby ACS. Všechny výchozí možnosti jsou implementovány pomocí open source softwaru.

ACS je momentálně dostupná pro standardní A, D, DS, G a GS řady virtuálních počítačů s Linuxem v Azure. Se vám účtovat jenom výpočetní instance, kterou zvolíte, jakož i jiné infrastruktury spotřebované základní prostředky, jako je například úložiště a sítě. Neúčtují žádné dodatečné poplatky pro ACS samotnou.

## <a name="additional-resources"></a>Další zdroje

-   **Úvod do řešení pomocí služby Azure Container Service pro hostování kontejnerů Docker**
    [*https://docs.microsoft.com/azure/container-service/container-service-intro*](https://docs.microsoft.com/azure/container-service/container-service-intro)

-   **Přehled dockeru Swarm**
    [*https://docs.docker.com/swarm/overview/*](https://docs.docker.com/swarm/overview/)

-   **Přehled režimu swarm**
    [*https://docs.docker.com/engine/swarm/*](https://docs.docker.com/engine/swarm/)

-   **Přehled mesosphere DC/OS**
    [*https://docs.mesosphere.com/1.7/overview/*](https://docs.mesosphere.com/1.7/overview/)

-   **Kubernetes.** Oficiální web. \
    [*https://kubernetes.io/*](https://kubernetes.io/)


>[!div class="step-by-step"]
[Předchozí](resilient-high-availability-microservices.md)
[další](using-azure-service-fabric.md)
