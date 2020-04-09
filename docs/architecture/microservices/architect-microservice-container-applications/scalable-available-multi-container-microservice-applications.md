---
title: Orchestrace mikroslužeb a vícekontejnerových aplikací pro vysokou škálovatelnost a dostupnost
description: Seznamte se s možnostmi orchestrace mikroslužeb a aplikací s více kontejnery pro vysokou škálovatelnost a dostupnost a možnosti Azure Dev Spaces při vývoji životního cyklu aplikací Kubernetes.
ms.date: 01/30/2020
ms.openlocfilehash: 8a67235109bed806caa7d9caa2bc26fd4fe9daca
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988905"
---
# <a name="orchestrate-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Orchestrace mikroslužeb a vícekontejnerových aplikací pro vysokou škálovatelnost a dostupnost

Použití orchestrators pro produkční aplikace je nezbytné, pokud vaše aplikace je založena na mikroslužeb nebo jednoduše rozdělit mezi více kontejnerů. Jak bylo zavedeno dříve, v přístupu založeném na mikroslužbách, každá mikroslužba vlastní svůj model a data tak, aby byla autonomní z hlediska vývoje a nasazení. Ale i v případě, že máte více tradiční aplikace, která se skládá z více služeb (jako SOA), budete mít také více kontejnerů nebo služeb, které obsahují jednu obchodní aplikaci, které je třeba nasadit jako distribuovaný systém. Tyto typy systémů jsou složité pro horizontální navýšení kapacity a správu; proto je naprosto nutné orchestrator, pokud chcete mít produkční připravené a škálovatelné vícekontejnerové aplikace.

Obrázek 4-23 znázorňuje nasazení do clusteru aplikace složené z více mikroslužeb (kontejnerů).

![Diagram znázorňující aplikace Složených Dockerů v clusteru.](./media/scalable-available-multi-container-microservice-applications/composed-docker-applications-cluster.png)

**Obrázek 4-23**. Shluk kontejnerů

Pro každou instanci služby se používá jeden kontejner. Kontejnery Dockeru jsou "jednotky nasazení" a kontejner je instancí dockeru. Hostitel zpracovává mnoho kontejnerů. Vypadá to jako logický přístup. Ale jak se vyrovnáváte zatížení, směrování a orchestrace těchto složených aplikací?

Prostý Docker Engine v jednom hostiteli Dockersplňuje potřeby správy jednotlivých instancí bitové kopie na jednom hostiteli, ale nedosahuje, pokud jde o správu více kontejnerů nasazených na více hostitelích pro složitější distribuované aplikace. Ve většině případů potřebujete platformu pro správu, která automaticky spustí kontejnery, horizontální navýšení kapacity kontejnerů s více instancemi na bitovou kopii, pozastaví je nebo v případě potřeby vypne a v ideálním případě také řídí, jak přistupují k prostředkům, jako je síť a úložiště dat.

Chcete-li jít nad rámec správy jednotlivých kontejnerů nebo velmi jednoduché složené aplikace a přejít k větší podnikové aplikace s mikroslužeb, musíte přejít na orchestraci a clustering platformy.

Z hlediska architektury a vývoje, pokud vytváříte velké podniky složené z aplikací založených na mikroslužbách, je důležité porozumět následujícím platformám a produktům, které podporují pokročilé scénáře:

**Klastry a orchestrátory.** Když potřebujete škálovat aplikace napříč mnoha hostiteli Dockeru, jako když je velká aplikace založená na mikroslužbách, je důležité, abyste mohli spravovat všechny tyto hostitele jako jeden cluster abstrahováním složitosti základní platformy. To je to, co poskytují clustery kontejnerů a orchestrátory. Kubernetes je příkladem orchestrátoru a je k dispozici v Azure prostřednictvím služby Azure Kubernetes.

**Plánovače.** *Plánování* znamená mít možnost správce spouštět kontejnery v clusteru, takže také poskytují ui. Plánovač clusteru má několik odpovědností: efektivně používat prostředky clusteru, nastavit omezení poskytovaná uživatelem, efektivně načíst kontejnery pro vyrovnávání zatížení mezi uzly nebo hostiteli a být robustní proti chybám při poskytování vysoké dostupnosti.

Koncepty clusteru a plánovače úzce souvisejí, takže produkty poskytované různými dodavateli často poskytují obě sady možností. V následujícím seznamu jsou uvedeny nejdůležitější možnosti platformy a softwaru, které máte pro clustery a plánovače. Tyto orchestrátory jsou obecně nabízeny ve veřejných cloudech, jako je Azure.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Softwarové platformy pro shlukování, orchestraci a plánování kontejnerů

|     |   |
|:---:|---|
| **Kubernetes** <br> ![Obrázek loga Kubernetes.](./media/scalable-available-multi-container-microservice-applications/kubernetes-container-orchestration-system-logo.png) | [*Kubernetes*](https://kubernetes.io/) je open source produkt, který poskytuje funkce, které sahají od infrastruktury clusteru a plánování kontejnerů až po možnosti orchestrace. Umožňuje automatizovat nasazení, škálování a operace kontejnerů aplikací napříč clustery hostitelů. <br><br> *Kubernetes* poskytuje infrastrukturu zaměřenou na kontejnery, která seskupuje kontejnery aplikací do logických jednotek pro snadnou správu a zjišťování. <br><br> *Kubernetes* je zralý v Linuxu, méně zralý ve Windows. |
| **Azure Kubernetes Service (AKS)** <br> ![Obrázek loga služby Azure Kubernetes.](./media/scalable-available-multi-container-microservice-applications/azure-kubernetes-service-logo.png) | [AKS](https://azure.microsoft.com/services/kubernetes-service/) je spravovaná služba orchestrace kontejnerů Kubernetes v Azure, která zjednodušuje správu, nasazení a operace clusteru Kubernetes. |

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a>Používání orchestrátorů založených na kontejnerech v Microsoft Azure

Několik dodavatelů cloudu nabízí podporu kontejnerů Dockeru a clustery Dockeru a podporu orchestrace, včetně Microsoft Azure, Amazon EC2 Container Service a Google Container Engine. Microsoft Azure poskytuje podporu clusteru Dockeru a orchestrátoru prostřednictvím služby Azure Kubernetes Service (AKS).

## <a name="using-azure-kubernetes-service"></a>Používání služby Azure Kubernetes

Cluster Kubernetes sdružuje více hostitelů Dockeru a zveřejňuje je jako jednoho virtuálního hostitele Dockeru, takže do clusteru můžete nasadit více kontejnerů a škálovat kapacitu s libovolným počtem instancí kontejnerů. Cluster bude zpracovávat všechny komplexní správy instalatérské, jako je škálovatelnost, zdraví a tak dále.

AKS poskytuje způsob, jak zjednodušit vytváření, konfiguraci a správu clusteru virtuálních počítačů v Azure, které jsou předem nakonfigurované pro spouštění kontejnerizovaných aplikací. Pomocí optimalizované konfigurace oblíbených nástrojů pro plánování a orchestraci s otevřeným zdrojovým kódem vám AKS umožňuje využít vaše stávající dovednosti nebo využít velké a rostoucí množství odborných znalostí komunity k nasazení a správě aplikací založených na kontejnerech v Microsoft Azure.

Služba Azure Kubernetes optimalizuje konfiguraci oblíbených nástrojů a technologií s otevřeným zdrojovým kódem Dockeru speciálně pro Azure. Získáte otevřené řešení, které nabízí přenositelnost pro kontejnery i konfiguraci aplikace. Vyberete velikost, počet hostitelů a nástroje orchestrator a AKS zpracovává všechno ostatní.

![Diagram znázorňující strukturu clusteru Kubernetes.](./media/scalable-available-multi-container-microservice-applications/kubernetes-cluster-simplified-structure.png)

**Obrázek 4-24**. Zjednodušená struktura a topologie kubernetes

Na obrázku 4-24 můžete vidět strukturu clusteru Kubernetes, kde hlavní uzel (VM) řídí většinu koordinace clusteru a můžete nasadit kontejnery do ostatních uzlů, které jsou spravovány jako jeden fond z hlediska aplikace a umožňuje škálovat na tisíce nebo dokonce desítky tisíc kontejnerů.

## <a name="development-environment-for-kubernetes"></a>Vývojové prostředí pro Kubernetes

Ve vývojovém prostředí [Docker v červenci 2018 oznámil,](https://blog.docker.com/2018/07/kubernetes-is-now-available-in-docker-desktop-stable-channel/) že Kubernetes může také běžet v jednom vývojovém počítači (Windows 10 nebo macOS) jednoduše instalací [Docker Desktop](https://docs.docker.com/install/). Později můžete nasadit do cloudu (AKS) pro další integrační testy, jak je znázorněno na obrázku 4-25.

![Diagram znázorňující Kubernetes na vývojovém počítači, který je pak nasazen do AKS](./media/scalable-available-multi-container-microservice-applications/kubernetes-development-environment.png)

**Obrázek 4-25**. Běh Kubernetes v dev stroji a cloudu

## <a name="getting-started-with-azure-kubernetes-service-aks"></a>Začínáme se službou Azure Kubernetes Service (AKS)

Chcete-li začít používat AKS, nasadit cluster AKS z portálu Azure nebo pomocí příkazového příkazového příkazu. Další informace o nasazení clusteru Kubernetes v Azure najdete v [tématu Nasazení clusteru Služby Azure Kubernetes (AKS).](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal)

Neexistují žádné poplatky za žádný software nainstalovaný ve výchozím nastavení jako součást AKS. Všechny výchozí možnosti jsou implementovány pomocí open-source softwaru. AKS je k dispozici pro více virtuálních počítačů v Azure. Účtují se vám jenom za výpočetní instance, které zvolíte, a také za další spotřebované základní prostředky infrastruktury, jako je úložiště a sítě. Neexistují žádné přírůstkové poplatky za AKS sám.

Výchozí možnost nasazení v produkčním prostředí pro Kubernetes je použití grafů Helm, které jsou zavedeny v další části.

## <a name="deploy-with-helm-charts-into-kubernetes-clusters"></a>Nasazení pomocí grafů Helm do kubernetesových clusterů

Při nasazování aplikace do clusteru Kubernetes můžete použít původní nástroj příkazového příkazu kubectl.exe pomocí souborů nasazení založených na nativním formátu (soubory.yaml), jak již bylo uvedeno v předchozí části. Pro složitější aplikace Kubernetes, například při nasazování složitých aplikací založených na mikroslužbách, se však doporučuje používat [Helm](https://helm.sh/).

Helm Charts vám pomůže definovat, verze, nainstalovat, sdílet, upgrade nebo vrácení zpět i ty nejsložitější Kubernetes aplikace.

Chystáte se dále, helm využití se také doporučuje, protože další Prostředí Kubernetes v Azure, jako je azure [dev spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) jsou také založeny na grafech Helm.

Helm je udržován [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) - ve spolupráci s Microsoft, Google, Bitnami a helm komunity přispěvatelů.

Další informace o implementaci na grafy Helm a Kubernetes, najdete [v článku použití helm grafy nasadit eShopOnContainers na AKS](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Deploy-to-Azure-Kubernetes-Service-(AKS)) post.

## <a name="use-azure-dev-spaces-for-your-kubernetes-application-lifecycle"></a>Použití Azure Dev Spaces pro váš životní cyklus aplikací Kubernetes

[Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) poskytuje rychlé a iterativní prostředí pro vývoj Kubernetes pro týmy. S minimálním nastavováním počítačů pro vývoj můžete iterativně spouštět a ladit kontejnery přímo ve službě Azure Kubernetes Service (AKS). Můžete vyvíjet pro Windows, Mac nebo Linux pomocí známých nástrojů, jako jsou Visual Studio a Visual Studio Code, nebo pomocí příkazového řádku.

Jak již bylo zmíněno, Azure Dev Spaces používá helm grafy při nasazování aplikací založených na kontejneru.

Azure Dev Spaces pomáhá vývojovým týmům zvýšit produktivitu na Kubernetes, protože umožňuje rychle iterát a ladit kód přímo v globálním clusteru Kubernetes v Azure jednoduše pomocí Visual Studia 2019 nebo Visual Studio Code. Že cluster Kubernetes v Azure je sdílený spravovaný cluster Kubernetes, takže váš tým může spolupracovat. Můžete vyvinout kód izolovaně, pak nasadit do globálního clusteru a provést testování od konce s jinými součástmi bez replikace nebo zesměšňování závislostí.

Jak je znázorněno na obrázku 4-26, nejvíce rozdílové funkce v Azure Dev Spaces je schopnost vytvářet "prostory", které lze spustit integrované do zbytku globálního nasazení v clusteru.

![Diagram znázorňující použití více prostorů v Azure Dev Spaces.](./media/scalable-available-multi-container-microservice-applications/use-multiple-spaces-azure-dev.png)

**Obrázek 4-26**. Použití více prostorů v Azure Dev Spaces

V podstatě můžete nastavit sdílený dev prostor v Azure. Každý vývojář se může zaměřit jenom na svoji část aplikace a může iterativně vyvíjet kód před potvrzením ve vývojovém prostoru, který už obsahuje všechny ostatní služby a cloudové prostředky, na kterých jsou příslušné scénáře závislé. Závislosti jsou vždycky aktuální a vývojáři pracují způsobem, který odpovídá produkčnímu prostředí.

Azure Dev Spaces poskytuje koncept prostoru, který umožňuje pracovat v relativní izolaci a bez strachu z porušení práce vašeho týmu. Každý vývojový prostor je součástí hierarchické struktury, která umožňuje přepsat jednu mikroslužbu (nebo více) z hlavního dev prostoru "top" s vlastní mikroslužeb probíhá.

Tato funkce je založena na předpony URL, takže při použití libovolné předpony dev mezery v adrese url, požadavek je obsluhován z cílové mikroslužby, pokud existuje v prostoru pro vývoj, jinak je předán a první instance cílové mikroslužby nalezené v hierarchii, nakonec se dostanete do hlavního dev prostoru v horní části.

Pokud chcete získat praktické zobrazení konkrétního příkladu, podívejte se [na wiki stránku eShopOnContainers na webu Azure Dev Spaces](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Azure-Dev-Spaces).

Další informace naleznete v článku [pro vývoj týmu pomocí Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/team-development-netcore).

## <a name="additional-resources"></a>Další zdroje

- **Začínáme se službou Azure Kubernetes Service (AKS)** \
  <https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal>

- **Azure Dev Spaces** \
  <https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces>

- **Kubernetes** Oficiální stránky. \
  <https://kubernetes.io/>

>[!div class="step-by-step"]
>[Předchozí](resilient-high-availability-microservices.md)
>[další](../docker-application-development-process/index.md)
