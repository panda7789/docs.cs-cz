---
title: Orchestrace mikroslužeb a vícekontejnerových aplikací pro vysokou škálovatelnost a dostupnost
description: Objevte možnosti Orchestrace mikroslužeb a vícekontejnerových aplikací pro vysokou škálovatelnost a dostupnost a možnosti Azure Dev mezer při vývoji životního cyklu aplikací Kubernetes.
ms.date: 09/20/2018
ms.openlocfilehash: 3b7383f6153b787ce8bfad87e3902c34afba0fb2
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644896"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Orchestrace mikroslužeb a vícekontejnerových aplikací pro vysokou škálovatelnost a dostupnost

Využitím orchestrátorů, pro aplikace připravené pro produkční prostředí je nezbytné, pokud je vaše aplikace založené na mikroslužbách nebo jednoduše rozdělit mezi několik kontejnerů. Zavedeném dříve, v rámci přístupu založených na mikroslužbách vlastní jednotlivých mikroslužeb jeho modelu a datům tak, aby ho autonomní od vývoje a nasazení pohledu. Ale i v případě, že máte více tradiční aplikace, který se skládá z několika služeb (např. SOA), budete mít také více kontejnerů nebo služby vytvářející jednu obchodní aplikaci, která je nutné nasadit jako distribuovaný systém. Tyto druhy systémy jsou komplexní horizontální navýšení kapacity a Správa; Proto pokud chcete mít vícekontejnerová aplikace připravené pro produkční prostředí a škálovatelné se naprosto je nutné orchestrátor.

Obrázek 4 – 23 ukazuje nasazení do clusteru aplikace skládá z několika mikroslužeb (kontejnery).

![Složené aplikací Dockeru v clusteru: Použijete jeden kontejner pro každou repliku služby. Kontejnery dockeru jsou "jednotkách nasazení" a kontejner je, že instance hostitele Docker.A zpracovává mnoho kontejnerů](./media/image23.png)

**Obrázek 4 – 23**. Cluster kontejnerů

Vypadá jako logický přístup. Ale jak se vyrovnávání zatížení zpracování, směrování a orchestraci těchto aplikací skládá?

Prostý modul Docker v jedné hostitelů Docker splňuje potřeby správu instancí jedné image na jednom hostiteli, ale vrátí krátký se při rozhodování o Správa více kontejnerů, které jsou nasazeny na více hostitelích pro složitější distribuované aplikace. Ve většině případů je třeba platforma pro správu, který bude automaticky spustit kontejnery, kontejnery horizontální navýšení kapacity s více instancemi za image, je pozastavit nebo vypnout v případě potřeby a v ideálním případě také určují, jak bude přístup k prostředkům, jako je síť a data úložiště.

Se dostat nad rámec správu jednotlivých kontejnerů nebo velmi jednoduché složené aplikace a přesun směrem k větší podnikové aplikace s využitím mikroslužeb, musíte povolit orchestraci a clustering platformy.

Z pro architekturu a vývoj pohledu Pokud vytváříte velký podnik skládá z aplikací založených na mikroslužbách, je důležité znát následující platformy a produkty, které podporují pokročilé scénáře:

**Clustery a orchestrátorů.** Když potřebujete pro horizontální navýšení kapacity aplikace v mnoha hostitelích Dockeru, jako při velkých aplikací založených na mikroslužbách, je důležité mít možnost spravovat všechny tyto hostitele jako jeden cluster podle abstrahovat složitost základní platformy. Je to, co nabízejí clustery kontejnerů a orchestrátorů. Příklady orchestrátorů: Azure Service Fabric a Kubernetes. Kubernetes je k dispozici v Azure pomocí služby Azure Kubernetes Service.

**Plánovači.** *Plánování* znamená, že chcete mít možnost pro správce ke spuštění kontejnerů v clusteru, tak také poskytují uživatelské rozhraní. Plánovač clusteru má několik odpovědnosti: efektivně využívat prostředky clusteru, omezení zadaná uživatelem pro efektivní kontejnery pro vyrovnávání zatížení napříč uzly nebo hostitele a být odolnější proti chybám při zajištění vysoké dostupnost.

Koncepty cluster a Plánovač jsou úzce souvisí, takže produkty k dispozici od různých dodavatelů často zadat obě sady funkcí. Následující seznam obsahuje nejdůležitější platformy a software volby, které máte pro clustery a plánovače. Tyto orchestrátorů se obvykle nabízejí ve veřejných cloudech, jako je Azure.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Softwarové platformy pro kontejner clustering, orchestraci a plánování

### <a name="kubernetes"></a>Kubernetes

![Kubernetes logo](./media/image24.png)

> [*Kubernetes* ](https://kubernetes.io/) je opensourcový produkt, který poskytuje funkce, které od infrastruktura clusteru a kontejnerů plánování a orchestraci možnosti. Umožňuje vám automatizovat nasazování, škálování a provoz kontejnerů aplikací napříč clustery hostitelů.
>
> *Kubernetes* poskytuje infrastrukturu zaměřené na kontejner, který seskupuje kontejnerů aplikací do logické jednotky pro snadnou správu a zjišťování.
>
> *Kubernetes* je zavedený v systému Linux, méně až po zralé ve Windows.

### <a name="azure-kubernetes-service-aks"></a>Azure Kubernetes Service (AKS)

![Logo Azure Kubernetes Service](./media/image41.png)

> [Azure Kubernetes Service (AKS)](https://azure.microsoft.com/services/kubernetes-service/) je spravovaná služba Orchestrace kontejnerů Kubernetes v Azure, která zjednodušuje správu clusteru Kubernetes, nasazení a provoz.

### <a name="azure-service-fabric"></a>Azure Service Fabric

![Logo Azure Service Fabric](./media/image27.png)

> [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) je platforma mikroslužeb Microsoftu pro sestavování aplikací. Je [orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) ze služeb a vytváří clustery počítačů. Service Fabric dokáže nasadit služby, kontejnery nebo jako obyčejný procesy. Může dokonce kombinaci služby v procesech se službami v kontejnerech v rámci stejné aplikace a clusteru.
>
> *Service Fabric* clustery je možné nasadit v Azure, místně nebo v libovolném cloudu. Nasazení v Azure je však zjednodušen spravovaný přístup.
>
> *Service Fabric* poskytuje další a volitelné doporučené [programovacích modelů Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) jako [stavové služby](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) a [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction) .
>
> *Service Fabric* je zavedený ve Windows (roky vyvíjejí Windows), méně až po zralé v systému Linux.
>
> Od verze 2017 jsou podporovány kontejnery Linux i Windows v Service Fabric.

### <a name="azure-service-fabric-mesh"></a>Síť Azure Service Fabric

![Logo Azure Service Fabric mřížky](./media/image35.png)

> [*Azure Service Fabric mřížky* ](https://docs.microsoft.com/azure/service-fabric-mesh/service-fabric-mesh-overview) nabízí stejnou spolehlivost, kritických pro chod výkonu a škálování než Service Fabric, ale nabízí plně spravované a bez serveru platformy. Není nutné ke správě clusteru, virtuální počítače, úložiště nebo síťové konfigurace. Můžete soustředit jen na vývoj vaší aplikace.
>
> *Service Fabric mřížky* podporuje kontejnery Windows i Linuxem díky tomu umožňuje vývoj s využitím libovolný programovací jazyk a rozhraní dle vlastního výběru.

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a>Pomocí orchestrátorů kontejneru ve službě Microsoft Azure

Několik dodavatelů cloud nabízí podporu kontejnerů Dockeru a Docker clusterů a podporu Orchestrace, včetně Microsoft Azure, Amazon EC2 Container Service a modul kontejnerů Google. Microsoft Azure podporuje Docker clusteru a orchestrator prostřednictvím Azure Kubernetes Service (AKS) a Azure Service Fabric a Azure Service Fabric mřížky.

## <a name="using-azure-kubernetes-service"></a>Používání služby Azure Kubernetes

Kubernetes cluster fondy více hostitelů Docker a zpřístupňuje jako jednoho virtuálního hostitele Docker, abyste mohli nasadit několik kontejnerů do clusteru a horizontální navýšení kapacity s libovolným počtem instancí kontejneru. Cluster bude zpracovávat složité správy základní, jako je škálovatelnost, stavu a tak dále.

AKS zajišťuje zjednodušení vytváření, konfiguraci a správu clusterů virtuálních počítačů v Azure, které je předem nakonfigurované spouštění kontejnerizovaných aplikací. Použití optimalizovanou konfiguraci oblíbených nástrojů open source plánování a orchestraci, AKS vám umožní využívat své stávající dovednosti nebo nakreslit velké a stále se rozšiřujících odborných znalostech komunity k nasazení a správě kontejnerových aplikací v Microsoft Azure .

Azure Kubernetes Service optimalizuje konfiguraci oblíbených Docker clusteringu open source nástrojů a technologií konkrétně pro Azure. Získáte otevřené řešení, které nabízí přenositelnost pro vaše kontejnery i Konfigurace aplikací. Vyberete velikost, počet hostitelů a orchestrační nástroje a AKS postará o všechno ostatní.

![Struktura clusteru Kubernetes: Existuje jeden hlavní uzel, který zpracovává DNS, Plánovač, proxy server a podobně a několik pracovních uzlů, které jsou hostiteli kontejnerů.](media/image36.png)

**Obrázek 4 – 24**. Zjednodušenou strukturu a topologii clusteru Kubernetes

Na obrázku 4-24 uvidíte struktura cluster Kubernetes, kde hlavní uzel (VM) řídí většina koordinace clusteru a kontejnerů můžete nasadit na zbývající uzly, které se spravují jako jeden fond z hlediska aplikací a umožňuje y organizačních jednotek škálovat do tisíců nebo dokonce desítek tisíců kontejnerů.

## <a name="development-environment-for-kubernetes"></a>Vývojové prostředí pro Kubernetes

Ve vývojovém prostředí [Dockeru v červenci 2018 jsme oznámili](https://blog.docker.com/2018/07/kubernetes-is-now-available-in-docker-desktop-stable-channel/) , Kubernetes můžete také spustit v rámci jediného vývojového počítače (Windows 10 nebo macOS) jednoduše nainstalováním [Docker Desktop](https://docs.docker.com/install/). Můžete ji později nasadit do cloudu (AKS) pro další testů integrace, jak je znázorněno na obrázku 4-25.

![Docker oznámilo podporu počítač dev pro clustery Kubernetes na dne. 2018 v Desktopu Dockeru.](media/image37.png) 

**Obrázek 4 – 25**. Ve vývojovém počítači i v cloudu s Kubernetes

## <a name="getting-started-with-azure-kubernetes-service-aks"></a>Začínáme s Azure Kubernetes Service (AKS) 

Pokud chcete začít používat AKS, nasaďte cluster AKS z webu Azure portal nebo pomocí th rozhraní příkazového řádku. Další informace o nasazení clusteru Azure Container Service najdete v tématu [Nasaďte cluster Azure Kubernetes Service (AKS)](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal).

Neexistují žádné poplatky za software ve výchozím nastavení nainstalované jako součást AKS. Všechny výchozí možnosti jsou implementovány pomocí open source softwaru. AKS je k dispozici pro několik virtuálních počítačů v Azure. Platíte jenom za výpočetní instance, kterou zvolíte, jakož i jiné infrastruktury spotřebované základní prostředky, jako je například úložiště a sítě. Neúčtují žádné dodatečné poplatky pro AKS, samotného.

Pro další informace o implementaci při nasazení Kubernetes na základě kubectl a původní .yaml soubory, podívejte se na příspěvek na [aplikaci eShopOnContainers nastavení ve službě AKS (služby Azure Kubernetes Service)](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.-Setting-the-solution-up-in-AKS-(Azure-Kubernetes-Service)).

## <a name="deploying-with-helm-charts-into-kubernetes-clusters"></a>Nasazení pomocí helmu do clusterů Kubernetes

Při nasazení aplikace do clusteru Kubernetes, můžete použít původní nástroj rozhraní příkazového řádku kubectl.exe pomocí soubory nasazení na základě nativním formátu (.yaml soubory), jak již bylo uvedeno v předchozí části. Nicméně u složitějších aplikací Kubernetes, jako při nasazení složitých aplikací založených na mikroslužbách, doporučuje se použít [Helm](https://helm.sh/).

Grafy Helm umožňuje definovat, verzi, instalace, sdílené složky, upgrade nebo vrácení zpět i nejsložitější aplikaci Kubernetes.

Když budete pokračovat, Helm využití se také doporučuje, protože další prostředí Kubernetes v Azure, jako například [prostory Azure Dev](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) jsou také založeny na helmu.

Helm je spravován [Foundation nativní computingu na Cloud (CNCF)](https://www.cncf.io/) – ve spolupráci s Microsoftem, Google, Bitnami a Přispěvatel komunity Helm.

Implementace Další informace o helmu a Kubernetes najdete v příspěvku na [pomocí helmu k nasazení do AKS aplikaci eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.1-Deploying-to-AKS-using-Helm-Charts).

## <a name="use-azure-dev-spaces-for-your-kubernetes-application-lifecycle"></a>Použití Azure Dev prostorů Kubernetes životním cyklu aplikací

[Azure Dev prostory](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) poskytuje rychlý a iterativní Kubernetes vývojové prostředí pro týmy. S nastavením minimální dev počítače můžete interaktivně spustit a ladit kontejnery přímo ve službě Azure Kubernetes Service (AKS). Vývoj pro Windows, Mac nebo Linux pomocí známých nástrojů, jako je Visual Studio, Visual Studio Code nebo příkazového řádku.

Jak už bylo zmíněno, používá Azure Dev prostory helmu při nasazování aplikací založených na kontejnerech.

Azure Dev prostorech vývojové týmy být produktivnější s Kubernetes, protože umožňuje rychle iterovat a ladění kódu přímo v globální clusteru Kubernetes v Azure můžete jednoduše pomocí sady Visual Studio 2017 nebo Visual Studio Code. Že cluster Kubernetes v Azure sdílené spravuje clusteru Kubernetes, takže váš tým může spolupracovat spolupracují. Vývoj kódu v izolaci, pak můžete nasadit do clusteru globální a provést začátku do konce testování s ostatními součástmi bez replikace nebo napodobování nahoru závislosti.

Jak je znázorněno na obrázku 4-26, je většina rozdílové funkce v Azure Dev prostory funkce vytváření mezery' ", které můžou běžet integrované do zbytku globálního nasazení v clusteru.

![Azure Dev prostory můžete transparentně kombinovat a párovat produkční mikroslužeb s vývoj instance kontejneru, do testování nových verzí.](media/image38.png)

**Obrázek 4 – 26**. Použití více mezer v Azure Dev mezery

V podstatě můžete nastavit prostor sdíleném vývojovém v Azure. Každý Vývojář můžete zaměřit na pouze jejich součástí aplikace a můžete využít iterativní vývoj předběžné potvrzení změn kódu v prostoru dev, která už obsahuje všechny ostatní služby a cloudové prostředky, které jejich scénářů závisí na. Závislosti jsou vždy aktuální a vývojáři už pracují tak, aby zrcadlí produkčního prostředí.

Azure Dev prostory nabízí koncepci místa, což umožňuje práci v relativní izolaci a bez obav z přerušení práci týmu. Každý prostor vývoj je součástí hierarchickou strukturu, která umožňuje přepsání jednu mikroslužbu (nebo řada), z prostoru hlavní vývoj "top", s vlastní nedokončenou prací mikroslužeb.

Tato funkce je založená na předpony adres URL, takže pokud používáte jakoukoli předponu dev místa v adrese url, požadavek se načítají z mikroslužeb cílové pokud existuje v prostoru dev, jinak předána až po první instance cílové mikroslužeb v hierarchii , nakonec získání hlavního vývojáře prostoru v horní části.

Zobrazí se [aplikaci eShopOnContainers wiki stránky v Azure Dev prostorech](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.1-Using-Azure-Dev-Spaces-and-AKS), abyste získali praktické zobrazení na konkrétní příklad.

Další informace najdete v článku na [týmový vývoj pomocí Azure Dev prostory](https://docs.microsoft.com/azure/dev-spaces/team-development-netcore).

## <a name="additional-resources"></a>Další zdroje

- **Začínáme s Azure Kubernetes Service (AKS)** \
  <https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal>

- **Azure Dev mezery** \
  <https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces>

- **Kubernetes** oficiální web. \
  <https://kubernetes.io/>

>[!div class="step-by-step"]
>[Předchozí](resilient-high-availability-microservices.md)
>[další](using-azure-service-fabric.md)
