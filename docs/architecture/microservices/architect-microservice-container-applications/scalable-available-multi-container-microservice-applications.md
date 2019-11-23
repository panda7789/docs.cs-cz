---
title: Orchestrace mikroslužeb a vícekontejnerových aplikací pro vysokou škálovatelnost a dostupnost
description: Seznamte se s možnostmi pro orchestraci mikroslužeb a aplikací s více kontejnery pro vysokou škálovatelnost a dostupnost a možnosti Azure Dev Spaces během vývoje životního cyklu aplikace Kubernetes.
ms.date: 09/20/2018
ms.openlocfilehash: 3915e6386e66d40bedc92368bfbcda81790c6923
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090145"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Orchestrace mikroslužeb a vícekontejnerových aplikací pro vysokou škálovatelnost a dostupnost

Použití orchestrací pro aplikace připravené pro produkční prostředí je nezbytné, pokud je vaše aplikace založená na mikroslužbách nebo jednoduše rozdělená mezi několik kontejnerů. Jak jsme už dřív představili, v rámci přístupu na základě mikroslužeb každá mikroslužba vlastní svůj model a data tak, že bude autonomní z pohledu vývoje a nasazení. I když máte obecnější aplikaci, která se skládá z několika služeb (například SOA), budete mít také více kontejnerů nebo služeb tvořících jednu obchodní aplikaci, která musí být nasazena jako distribuovaný systém. Tyto druhy systémů jsou složité pro horizontální navýšení kapacity a správu. Proto budete potřebovat Orchestrator, pokud chcete mít aplikaci s více kontejnery připravenou pro produkční prostředí a škálovatelnost.

Obrázek 4-23 znázorňuje nasazení do clusteru aplikace tvořené několika mikroslužbami (kontejnery).

![Diagram znázorňující sestavené aplikace Docker v clusteru](./media/scalable-available-multi-container-microservice-applications/composed-docker-applications-cluster.png)

**Obrázek 4-23**. Cluster kontejnerů

Pro každou instanci služby použijete jeden kontejner. Kontejnery Docker jsou "jednotky nasazení" a kontejner je instance Docker. Hostitel zpracovává mnoho kontejnerů. Vypadá to, že se jedná o logický přístup. Ale jak zpracováváte vyrovnávání zatížení, směrování a orchestraci těchto složených aplikací?

Modul pro prostý Docker v hostitelích s jedním Docker splňuje požadavky na správu jedné instance imagí na jednom hostiteli, ale je krátký, pokud je k dispozici pro správu více kontejnerů nasazených na více hostitelích pro složitější distribuované aplikace. Ve většině případů potřebujete platformu pro správu, která bude automaticky spouštět kontejnery, škálovat kontejnery s více instancemi na jeden obrázek, potlačit je nebo vypnout v případě potřeby a v ideálním případě také řídit, jak přistupují k prostředkům, jako je síť a data. pamì.

Aby bylo možné nad rámec správy jednotlivých kontejnerů nebo velmi jednoduchých složených aplikací a přecházet k většímu počtu podnikových aplikací pomocí mikroslužeb, je nutné přepínat na orchestraci a clusteringu platforem.

Pokud vytváříte velký podnik tvořený aplikacemi založenými na mikroslužbách, je z hlediska architektury a vývoje důležité pochopit následující platformy a produkty, které podporují pokročilé scénáře:

**Clustery a orchestrace.** Pokud potřebujete škálovat aplikace v mnoha hostitelích Docker, jako když máte rozsáhlou aplikaci založenou na mikroslužbách, je důležité, abyste mohli spravovat všechny tyto hostitele jako jediný cluster abstrakcí složitosti základní platformy. To je to, co poskytují clustery kontejnerů a orchestrace. Kubernetes je příkladem produktu Orchestrator a je k dispozici v Azure prostřednictvím služby Azure Kubernetes.

**Plánovače.** *Plánování* znamená, že může správce spouštět kontejnery v clusteru, aby jim taky poskytoval uživatelské rozhraní. Plánovač clusteru má několik odpovědností: k efektivnímu využití prostředků clusteru, k nastavení omezení poskytovaných uživatelem, k efektivnímu vyrovnávání zatížení kontejnerů napříč uzly nebo hostiteli a k zajištění odolnosti proti chybám při vysokém dosahu dostupnosti.

Koncepty clusteru a plánovače úzce souvisejí, takže produkty poskytované různými dodavateli často poskytují obě sady funkcí. Následující seznam obsahuje nejdůležitější možnosti platformy a softwaru pro clustery a plánovače. Tyto orchestrace jsou všeobecně nabízeny ve veřejných cloudech, jako je Azure.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Softwarové platformy pro clusteringu kontejnerů, Orchestrace a plánování

|     |   |
|-----|---|
| **Kubernetes** <br> ![obrázek loga Kubernetes](./media/scalable-available-multi-container-microservice-applications/kubernetes-container-orchestration-system-logo.png) | [*Kubernetes*](https://kubernetes.io/) je open source produkt, který poskytuje funkce, které jsou v rozsahu od infrastruktury clusteru a plánování kontejneru až po orchestraci možností. Umožňuje automatizovat nasazení, škálování a provoz kontejnerů aplikací napříč clustery hostitelů. <br><br> *Kubernetes* poskytuje infrastrukturu zaměřenou na kontejner, která seskupuje kontejnery aplikací do logických jednotek pro jednoduchou správu a zjišťování. <br><br> *Kubernetes* je vyspělá v systému Linux a méně vyspělá ve Windows. |
| **Azure Kubernetes Service (AKS)** <br> ![obrázek loga služby Azure Kubernetes.](./media/scalable-available-multi-container-microservice-applications/azure-kubernetes-service-logo.png) | [AKS](https://azure.microsoft.com/services/kubernetes-service/) je spravovaná služba orchestrace kontejnerů Kubernetes v Azure, která zjednodušuje správu, nasazení a provoz clusteru Kubernetes. |

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a>Použití orchestrací založených na kontejnerech v Microsoft Azure

Několik dodavatelů cloudu nabízí podporu kontejnerů Docker a clustery Docker a podporu orchestrace, včetně Microsoft Azure, služby kontejneru Amazon EC2 a modulu pro kontejner Google. Microsoft Azure poskytuje cluster Docker a podporu nástroje Orchestrator prostřednictvím služby Azure Kubernetes Service (AKS).

## <a name="using-azure-kubernetes-service"></a>Pomocí služby Azure Kubernetes

Cluster Kubernetes fonduje několik hostitelů Docker a zpřístupňuje je jako jeden virtuální hostitel Docker, takže můžete do clusteru nasadit více kontejnerů a škálovat je pomocí libovolného počtu instancí kontejnerů. Cluster bude zpracovávat všechny komplexní instalace správy, jako je škálovatelnost, stav a tak dále.

AKS poskytuje způsob, jak zjednodušit vytváření, konfiguraci a správu clusteru virtuálních počítačů v Azure, které jsou předem nakonfigurované tak, aby se spouštěly aplikace s využitím kontejnerů. Díky optimalizované konfiguraci oblíbených open source nástrojů pro plánování a orchestraci vám AKS umožňuje využívat stávající dovednosti nebo nakládat na velký a rostoucí tělo odborného posudku komunity k nasazení a správě kontejnerových aplikací na Microsoft Azure .

Služba Azure Kubernetes optimalizuje konfiguraci oblíbených nástrojů a technologií open-source pro clustery Docker, konkrétně pro Azure. Získáte otevřené řešení, které nabízí přenositelnost pro vaše kontejnery i konfiguraci vaší aplikace. Vyberte velikost, počet hostitelů a nástroje Orchestrator a AKS zpracuje všechno ostatní.

![Diagram znázorňující strukturu clusteru Kubernetes.](./media/scalable-available-multi-container-microservice-applications/kubernetes-cluster-simplified-structure.png)

**Obrázek 4-24**. Zjednodušená struktura a topologie clusteru Kubernetes

Na obrázku 4-24 můžete zobrazit strukturu clusteru Kubernetes, kde hlavní uzel (VM) ovládá většinu koordinace clusteru, a můžete nasazovat kontejnery do zbývajících uzlů, které se spravují jako jeden fond z aplikačního bodu zobrazení a umožňují y. organizační jednotka pro škálování na tisíce nebo dokonce desítky tisíc kontejnerů.

## <a name="development-environment-for-kubernetes"></a>Vývojové prostředí pro Kubernetes

V vývojovém prostředí [Docker oznámil v červenci 2018](https://blog.docker.com/2018/07/kubernetes-is-now-available-in-docker-desktop-stable-channel/) , že Kubernetes může také běžet na jednom vývojovém počítači (Windows 10 nebo MacOS) pouhou instalací [Docker desktopu](https://docs.docker.com/install/). Později můžete nasadit do cloudu (AKS) pro další testy integrace, jak je znázorněno na obrázku 4-25.

![Diagram znázorňující Kubernetes na vývojovém počítači, který se pak nasadí do AKS](./media/scalable-available-multi-container-microservice-applications/kubernetes-development-environment.png)

**Obrázek 4-25**. Spuštění Kubernetes ve vývojovém počítači a v cloudu

## <a name="getting-started-with-azure-kubernetes-service-aks"></a>Začínáme se službou Azure Kubernetes (AKS)

Chcete-li začít používat AKS, nasaďte cluster AKS z Azure Portal nebo pomocí rozhraní příkazového řádku. Další informace o nasazení clusteru Kubernetes v Azure najdete v tématu [nasazení clusteru Azure Kubernetes Service (AKS)](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal).

Neexistují žádné poplatky za žádný software nainstalovaný ve výchozím nastavení jako součást AKS. Všechny výchozí možnosti jsou implementované pomocí Open source softwaru. AKS je k dispozici pro více virtuálních počítačů v Azure. Účtují se vám jenom výpočetní instance, které zvolíte, a také ostatní základní prostředky infrastruktury spotřebované jako úložiště a sítě. Za AKS se neúčtují žádné dodatečné poplatky.

Další informace o implementaci nasazení na Kubernetes na základě kubectl a originálních souborů. yaml najdete v příspěvku k [Nastavení eShopOnContainers v AKS (služba Azure Kubernetes)](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.-Setting-the-solution-up-in-AKS-(Azure-Kubernetes-Service)).

## <a name="deploying-with-helm-charts-into-kubernetes-clusters"></a>Nasazení pomocí Helm grafů do clusterů Kubernetes

Když nasazujete aplikaci do clusteru Kubernetes, můžete použít původní nástroj kubectl. exe CLI pomocí souborů nasazení založených na nativním formátu (soubory. yaml), jak je to již popsáno v předchozí části. U složitějších aplikací Kubernetes, jako je například při nasazení složitých aplikací založených na mikroslužbách, se doporučuje použít [Helm](https://helm.sh/).

Grafy Helm vám pomůžou definovat, verze, nainstalovat, sdílet, upgradovat nebo vrátit zpět, a to i v nejsložitější aplikaci Kubernetes.

Dál se doporučuje používat Helm použití, protože další prostředí Kubernetes v Azure, jako je například [Azure dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) , jsou také založená na Helm grafech.

Helm je udržována ve spolupráci s Microsoftem [(Cloud Native Computing Foundation) (CNCF)](https://www.cncf.io/) – ve spolupráci s Microsoftem, Google, Bitnami a komunitou přispěvatelů Helm.

Další informace o implementaci Helm grafů a Kubernetes najdete v příspěvku [použití Helm grafů k nasazení eShopOnContainers na AKS](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.1-Deploying-to-AKS-using-Helm-Charts).

## <a name="use-azure-dev-spaces-for-your-kubernetes-application-lifecycle"></a>Použití Azure Dev Spaces pro životní cyklus aplikace Kubernetes

[Azure dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) poskytuje rychlé a iterativní vývojové prostředí Kubernetes pro týmy. S minimálním nastavením pro vývoj počítačů můžete iterativní spouštění a ladění kontejnerů přímo ve službě Azure Kubernetes Service (AKS). Vývoj v systémech Windows, Mac nebo Linux pomocí známých nástrojů, jako je Visual Studio, Visual Studio Code nebo příkazového řádku.

Jak bylo zmíněno, Azure Dev Spaces používá při nasazování aplikací založených na kontejneru Helm grafy.

Azure Dev Spaces pomáhá vývojovým týmům zvýšit produktivitu na Kubernetes, protože umožňuje rychle iterovat a ladit kód přímo v globálním clusteru Kubernetes v Azure, a to jednoduše pomocí sady Visual Studio 2017 nebo Visual Studio Code. Tento cluster Kubernetes v Azure je sdílený spravovaný cluster Kubernetes, takže váš tým může spolupracovat společně. Můžete vyvíjet kód v izolovaném prostředí a pak ho nasadit do globálního clusteru a provést komplexní testování s ostatními komponentami bez replikace nebo napodobování závislostí.

Jak je znázorněno na obrázku 4-26, nejrozdílnou funkcí v Azure Dev Spaces je schopnost vytvořit "Spaces", která se dá spustit integrovaná do zbytku globálního nasazení v clusteru.

![Diagram znázorňující použití více mezer v Azure Dev Spaces.](./media/scalable-available-multi-container-microservice-applications/use-multiple-spaces-azure-dev.png)

**Obrázek 4-26**. Použití více mezer v Azure Dev Spaces

V podstatě můžete nastavit sdílený prostor pro vývoj v Azure. Každý vývojář se může zaměřit jenom na jejich část aplikace a může iterativním způsobem vyvíjet kód před potvrzením ve vývojovém prostoru, který už obsahuje všechny ostatní služby a cloudové prostředky, na kterých jsou závislé jejich scénáře. Závislosti jsou vždycky aktuální a vývojáři pracují způsobem, který zrcadlí produkci.

Azure Dev Spaces poskytuje koncept prostoru, který vám umožní pracovat v relativní izolaci a bez obav, že váš tým funguje. Každé vývojové místo je součástí hierarchické struktury, která umožňuje potlačit jednu mikroslužbu (nebo mnoho) z hlavního vývojového prostoru "nejdůležitější" a vlastní mikroslužba probíhající v práci.

Tato funkce je založena na předponách adres URL, takže při použití předpony prostoru pro vývoj v adrese URL je požadavek obsluhován z cílové mikroslužby, pokud existuje v prostoru pro vývoj, v opačném případě je předaný na první instanci cílové mikroslužby nalezené v hierarchii. a nakonec se dostanete k hlavnímu vývojovému prostoru v horní části.

[Stránku wiki eShopOnContainers můžete zobrazit na Azure dev Spaces](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.1-Using-Azure-Dev-Spaces-and-AKS), abyste získali praktické zobrazení na konkrétní příklad.

Další informace najdete v článku o [vývoji týmu pomocí Azure dev Spaces](https://docs.microsoft.com/azure/dev-spaces/team-development-netcore).

## <a name="additional-resources"></a>Další materiály a zdroje informací

- **Začínáme se službou Azure Kubernetes Service (AKS)**  \
  <https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal>

- **Azure Dev Spaces** \
  <https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces>

- **Kubernetes** Oficiální lokalita. \
  <https://kubernetes.io/>

>[!div class="step-by-step"]
>[Předchozí](resilient-high-availability-microservices.md)
>[Další](../docker-application-development-process/index.md)
