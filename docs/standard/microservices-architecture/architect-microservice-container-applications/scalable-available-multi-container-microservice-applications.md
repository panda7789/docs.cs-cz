---
title: "Orchestrace mikroslužeb a aplikace služby kontejneru pro vysokou škálovatelnost a dostupnost"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Orchestrace mikroslužeb a aplikace služby kontejneru pro vysokou škálovatelnost a dostupnost"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: ec33901a0ddc9e5b58263440b0e4399e687c6904
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Orchestrace mikroslužeb a aplikace služby kontejneru pro vysokou škálovatelnost a dostupnost

Použití orchestrators pro produkční prostředí aplikací je nezbytné, pokud vaše aplikace je založena na mikroslužeb nebo jednoduše rozdělit do několika kontejnerů. Zavedeném dříve, v rámci přístupu na základě mikroslužbu každý mikroslužbu vlastní jeho modelu a data tak, že bude autonomního z hlediska vývoje a nasazení hlediska. Ale i v případě, že máte více tradiční aplikace, která se skládá z několika služeb (například SOA), bude také nutné více kontejnerů nebo služby vytvářející jeden obchodní aplikace, které je potřeba nasadit jako distribuovaného systému. Tyto typy systémů jsou složité škálovat a spravovat; Proto pokud budete chtít mít produkční prostředí a škálovatelné aplikace s více kontejneru se absolutně je nutné produktu orchestrator.

Obrázek 4 – 23 znázorňuje nasazení do clusteru s podporou aplikace skládá z několika mikroslužeb (kontejnerů).

![](./media/image23.PNG)

**Obrázek 4 – 23**. Cluster kontejnery

To vypadá logického přístupu. Ale jak jsou vyrovnávání zatížení zpracování, směrování a Orchestrace tyto sestavit aplikace?

Modul prostý Docker v jednom hostitelů Docker splňuje potřeby správy instancí jedné image na jednoho hostitele, ale spadá krátký, pokud jde o správě několika kontejnerů, které jsou nasazené na několika hostitelích pro složitější distribuované aplikace. Ve většině případů potřebujete platforma pro správu, který bude automaticky spustit kontejnery, kontejnery Škálováním na více systémů s více instancí na bitovou kopii, pozastavit je nebo je vypnout v případě potřeby a v ideálním případě taky řídit, jak se přístup k prostředkům, jako jsou sítě a data úložiště.

Chcete-li překročila správu jednotlivých kontejnery nebo velmi jednoduché složený aplikace a přesuňte směrem k větší podnikové aplikace s mikroslužeb, musíte povolit orchestration a clustering platformy.

Z architektury a vývoj hlediska Pokud vytváříte velký podnik tvořený mikroslužeb li aplikace, je důležité si uvědomit následující platformy a produkty, které podporují pokročilé scénáře:

**Clustery a orchestrators**. Když potřebujete škálování aplikace napříč mnoha hostitelů Docker, jako když rozsáhlé na základě mikroslužbu aplikace, je důležité mít možnost spravovat všechny tyto hostitele jako jeden cluster pomocí poskytuje abstrakci složitost základní platformy. To je, co kontejneru clustery a orchestrators poskytují. Příklady orchestrators: Azure Service Fabric, Kubernetes, Docker Swarm a Mesosphere DC/OS. Poslední tři orchestrators open-source jsou k dispozici v Azure pomocí Azure Container Service.

**Plánovače**. *Plánování* znamená schopnost pro správce ke spuštění kontejnery v clusteru, tak také obsahují uživatelského rozhraní. Scheduler clusteru má několik odpovědnosti: efektivně využívat prostředky do clusteru, nastavit omezení zadané uživatelem, efektivně kontejnery Vyrovnávání zatížení mezi uzly nebo hostitele a být odolnosti proti chybám při současném poskytování základní dostupnost.

Koncepty cluster a plánovače jsou úzce související, takže produkty od různých výrobců často poskytují obě sady funkcí. Následující seznam obsahuje nejdůležitější platformy a softwaru možnosti dostupné pro clustery a plánovače. Tyto orchestrators jsou obecně nabízena v veřejných cloudů, jako je například Azure.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Softwarovými platformami pro kontejner clustering, orchestration a plánování

Kubernetes

![https://PBS.twimg.com/Media/BT\_pEfqCAAAiVyz.png](./media/image24.png)

> Kubernetes je produkt open source, který poskytuje funkce, které rozsahy z infrastruktura clusteru a kontejner plánování k funkcím Orchestrace. Umožňuje vám automatizovat nasazení, škálování a operace kontejnery aplikací napříč clustery hostitelů.
>
> Kubernetes poskytuje infrastrukturu zaměřené na kontejneru, která skupiny kontejnery aplikací do logické jednotky pro snadnou správu a zjišťování.
>
> Kubernetes je zavedený v systému Linux, méně vyspělá v systému Windows.

Docker Swarm

![http://rancher.com/WP-Content/Themes/rancher-2016/Assets/Images/swarm.PNG?v=2016-07-10-AM](./media/image25.png)

> Docker Swarm umožňuje clusteru a naplánovat Docker kontejnery. Pomocí Swarm, můžete upravit fond hostitelů Docker na jednu virtuální hostitel Docker. Klienty můžete nastavit žádostí o rozhraní API pro Swarm stejným způsobem, že dělají na hostitele, což znamená, že Swarm usnadňuje aplikace škálovat na více hostitelů.
>
> Docker Swarm je produkt z Docker společnosti.
>
> Docker v1.12 nebo můžete později spustit nativní a integrované Swarm režimu.

Mesosphere DC/OS

![https://mesosphere.com/WP-Content/uploads/2016/04/logo-Horizontal-styled.PNG](./media/image26.png)

> Mesosphere Enterprise DC/OS (podle Apache Mesos) je platforma pro produkční prostředí pro spouštění kontejnery a distribuovaných aplikací.
>
> DC/OS funguje tak, že poskytuje abstrakci kolekce prostředků, které jsou k dispozici v clusteru a zpřístupnění těchto prostředků postavená na jeho součástí. Marathon se obvykle používá jako plánovače integrovat DC/OS.
>
> DC/OS je zavedený v systému Linux, méně vyspělá v systému Windows.

Azure Service Fabric

![https://Azure.microsoft.com/svghandler/Service-Fabric?Width=600&Height=315](./media/image27.png)

> [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) je platforma Microsoft mikroslužeb pro vytváření aplikací. Je [orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) z služby a vytvoří clustery počítačů. Service Fabric můžete nasadit služby jako kontejnery nebo jako prostý procesy. Může i kombinaci služby v procesech se službami v kontejnery v rámci stejné aplikace a cluster.
>
> Service Fabric nabízí další a volitelné doporučený [Service Fabric programovací modely ](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) jako [stavové služby](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) a [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).
>
> Service Fabric je zavedený v systému Windows (vznikajícími letopočty v systému Windows), méně vyspělá v systému Linux. 
> Kontejnery pro Linux a Windows jsou podporovány v Service Fabric od 2017.

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a>Pomocí orchestrators na základě kontejneru ve službě Microsoft Azure

Několik cloudu dodavatelé nabízejí podporu kontejnery Docker plus Docker clustery a podporu orchestration, včetně Microsoft Azure, Amazon EC2 Container Service a modul kontejneru Google. Microsoft Azure poskytuje Docker podpora clusteru a orchestrator prostřednictvím Azure Container Service (ACS), jak je popsáno v následující části.

Další možnost je použít Microsoft Azure Service Fabric (mikroslužeb platformu), který podporuje i Docker založené na Linuxu a Windows kontejnery. Service Fabric běží v Azure nebo jiné cloudové a také běží [místní](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere).

## <a name="using-azure-container-service"></a>Pomocí Azure Container Service

Cluster s podporou Docker fondy více hostitelů Docker a zpřístupní jako jediného virtuálního Docker hostitele, abyste mohli nasadit víc kontejnerů do clusteru. Cluster bude zpracovávat všechny komplexní správu záležitosti, jako je škálovatelnost, stavu a tak dále. Obrázek 4 – 24 představuje, jak mapuje clusteru Docker pro složený aplikace do Azure Container Service (ACS).

Služba ACS poskytuje způsob, jak zjednodušení vytváření, konfiguraci a správu cluster virtuálních počítačů, které jsou předem nakonfigurován ke spuštění kontejnerizované aplikací. Pomocí konfigurace aplikace optimalizované oblíbených open-source plánování a orchestraci nástrojů, ACS umožňuje použití existujících dovedností a kreslení na text velké a stále se rozrůstající komunita odborných znalostí nasazovat a spravovat aplikace založené na kontejneru v Microsoft Azure .

Azure Container Service optimalizuje konfigurace oblíbených nástrojů clusteringu s otevřeným zdrojem Docker a technologie speciálně pro Azure. Získáte otevřete řešení, která nabízí přenositelnost kontejnerů a konfigurace aplikace. Vyberte velikost, počtu hostitelů a nástroje orchestrator a kontejneru služba zpracovává nic jiného.

![](./media/image28.png)

**Obrázek 4 – 24**. Clustering volbám v Azure Container Service

Služba ACS využívá imagí Dockeru zajistit, že jsou vaše kontejnery aplikace plně přenositelné. Podporuje vaší volby open-source orchestration platformách, jako je DC/OS (používá technologii Apache Mesos), Kubernetes (původně vytvořil Google) a nástrojem Docker Swarm, ujistěte se, že tyto aplikace je možné rozšířit tisíc nebo dokonce desetitisíce kontejnerů.

Azure Container service umožňuje využít výhod funkce podnikové úrovni Azure současně se zachovává přenositelnost aplikace, včetně na vrstvy orchestration.

![](./media/image29.png)

**Obrázek 4 – 25**. Orchestrators v rámci služby ACS

Jak ukazuje obrázek 4 – 25, Azure Container Service je jednoduše infrastruktury služby Azure za účelem nasazení DC/OS, Kubernetes nebo Docker Swarm, ale ACS neimplementuje žádné další orchestrator. Proto služby ACS není orchestrator jako takový jenom infrastruktura, která využívá existující orchestrators open source pro kontejnery.

Z hlediska využití je cílem Azure Container Service poskytuje hostitelské prostředí kontejneru pomocí Oblíbené open source nástroje a technologie. Za tímto účelem zpřístupní standardní koncové body rozhraní API pro vaši zvolenou orchestrator. Pomocí těchto koncových bodů, můžete využít veškerý software, který může komunikovat těchto koncových bodů. V případě koncového bodu Docker Swarm, můžete například použít Docker rozhraní příkazového řádku (CLI). Pro DC/OS je možné pomocí rozhraní příkazového řádku DC/OS.

### <a name="getting-started-with-azure-container-service"></a>Začínáme s Azure Container Service 

Pokud chcete začít používat Azure Container Service, nasazení clusteru Azure Container Service z portálu Azure pomocí šablony Azure Resource Manager nebo [rozhraní příkazového řádku](https://docs.microsoft.com/cli/azure/install-azure-cli). K dispozici šablony zahrnují [Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm), [Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes), a [DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos). Šablony rychlý start můžete upravit tak, aby zahrnout další nebo pokročilá konfigurace Azure. Další informace o nasazení clusteru Azure Container Service najdete v tématu [nasazení clusteru Azure Container Service](https://docs.microsoft.com/azure/container-service/container-service-deployment) na webu Azure.

Neexistují žádné poplatky za software nainstalovaný ve výchozím nastavení jako součást služby ACS. Všechny výchozí možnosti jsou implementovány pomocí open-source softwaru.

Služby ACS je aktuálně dostupné pro standardní A, D, DS, G a GS řady virtuální počítače s Linuxem v Azure. Budou se účtovat pouze pro výpočetní instance, který zvolíte, stejně jako ostatní základní prostředky infrastruktury využívat, jako je například úložiště a sítě. Neexistují žádné přírůstkové poplatky za služby ACS, sám sebe.

## <a name="additional-resources"></a>Další zdroje

-   **Úvod k hostování řešení s Azure Container Service kontejner Docker**
    [*https://docs.microsoft.com/azure/container-service/container-service-intro*](https://docs.microsoft.com/azure/container-service/container-service-intro)

-   **Přehled docker Swarm**
    [*https://docs.docker.com/swarm/overview/*](https://docs.docker.com/swarm/overview/)

-   **Přehled režimu swarm**
    [*https://docs.docker.com/engine/swarm/*](https://docs.docker.com/engine/swarm/)

-   **Přehled DC/OS mesosphere**
    [*https://docs.mesosphere.com/1.7/overview/*](https://docs.mesosphere.com/1.7/overview/)

-   **Kubernetes.** Oficiální web. \
    [*http://kubernetes.IO/*](http://kubernetes.io/)


>[!div class="step-by-step"]
[Předchozí] (odolné vysokou dostupnosti microservices.md) [Další] (pomocí azure-service-fabric.md)
