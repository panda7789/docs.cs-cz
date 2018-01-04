---
title: "Postupy a technická získat Začínáme přehled"
description: "Modernizovat existující aplikace .NET s cloudu Azure a Windows kontejnery | postupy a technická získat Začínáme přehled"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b8226e588bddc0872c68580006d86a570c6be2b6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="walkthroughs-and-technical-get-started-overview"></a>Postupy a technická získat Začínáme přehled 

Omezit velikost této e knihy, jsme provedli další technickou dokumentaci a úplné návody k dispozici v úložišti GitHub. Online řada návodů, která je popsána v tato kapitola obsahuje podrobné nastavení několika prostředí, které jsou založeny na Windows kontejnery a nasazení do Azure.

Následující části popisují, co každý postup je o její cíle, jeho vysoké úrovně vize- a poskytuje diagram úlohy, které se podílejí. Můžete získat sami názorné postupy v *eShopModernizing* wiki úložišti GitHub aplikace v [https://github.com/dotnet-architecture/eShopModernizing/wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki).

# <a name="technical-walkthrough-list"></a>Seznamu technických návod

Následující kurzy get-started poskytovat konzistentní a komplexní technické pokyny pro ukázkové aplikace, které se dají navýšení a posunutí pomocí kontejnery a potom přesunout tak, že pomocí více možností nasazení v Azure.

Každá z následující kurzy používá nové ukázkových eShopLegacy a eShopModernizing aplikací, které jsou k dispozici na webu GitHub na [https://github.com/dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).

-   **Prohlídka eShop starší verze aplikací**

-   **Containerize existující aplikace .NET s kontejnery Windows**

-   **Nasazení aplikace systému Windows na základě kontejnery pro virtuální počítače Azure**

-   **Nasazení aplikace na základě kontejnery Windows do Kubernetes v Azure Container Service**

-   **Nasazení aplikace na základě kontejnery Windows do Azure Service Fabric**

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a>Návod 1: Prohlídka eShop starší verze aplikací

### <a name="technical-walkthrough-availability"></a>Technické návod dostupnosti

Úplné technické návod je k dispozici na stránkách wiki úložišti GitHub eShopModernizing:

[https://github.com/DotNet-Architecture/eShopModernizing/Wiki/01.-Tour-on-eShopModernizing-Apps-Implementation-Code](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code)

### <a name="overview"></a>Přehled

V tomto návodu můžete prozkoumat počáteční implementace dva ukázkové starší verze aplikace. Obě ukázkových aplikací mít monolitický architektura a byly vytvořeny pomocí klasického ASP.NET. Jeden aplikace je založena na technologii ASP.NET 4.x MVC; druhý aplikace je založena na webových formulářů ASP.NET 4.x. Obě aplikace jsou v [úložiště GitHub eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).

Můžete containerize obě ukázkové aplikace, podobným způsobem můžete containerize klasický [Windows Communication Foundation](https://docs.microsoft.com/dotnet/framework/wcf/whats-wcf) aplikace (WCF), který se má používat jako desktopová aplikace. Příklad, naleznete v části [eShopModernizingWCFWinForms](https://github.com/dotnet-architecture/eShopModernizingWCFWinForms).

### <a name="goals"></a>Cíle

Hlavním cílem tohoto návodu je jednoduše a seznamte se s těmito aplikacemi a s jejich kódu a konfigurace. Aplikace můžete nakonfigurovat tak, aby se vygenerování a použití imitovaná data bez použití databáze SQL pro účely testování. Toto volitelné konfigurace je založená na vkládání závislostí odpojeného způsobem.

### <a name="scenario"></a>Scénář

Obrázek 5-1 znázorňuje jednoduchý scénář původní starší verze aplikací.

> ![Scénář jednoduchého architektura původní starší verze aplikací](./media/image5-1.png)
>
> **Obrázek 5-1.** Scénář jednoduchého architektura původní starší verze aplikací

Z hlediska domény obchodní obě aplikace nabízejí katalogu stejné funkce pro správu. Členové týmu enterprise eShop využije aplikace k zobrazení a úpravy katalogu produktů. Obrázek 5-2 je znázorněný na snímcích obrazovky počáteční aplikace.

![Aplikace ASP.NET MVC a webových formulářů ASP.NET (technologie existující nebo starší)](./media/image5-2.png)

> **Obrázek 5-2.** Aplikace ASP.NET MVC a webových formulářů ASP.NET (technologie existující nebo starší)

Toto jsou webové aplikace, které se používají k procházení a upravit položky katalogu. Fakt, že obě aplikace poskytovat stejné funkce obchodní/funkční je jednoduše pro účely porovnání. Můžete zobrazit podobný proces modernizace pro aplikace, které byly vytvořeny pomocí architektury ASP.NET MVC a webových formulářů ASP.NET.

Závislosti v technologii ASP.NET 4.x nebo starší verze (buď pro MVC nebo webových formulářů) znamená, že tyto aplikace se na .NET Core nespustí, pokud kód je plně přepsaná pomocí ASP.NET MVC jádra. Tento příklad ukazuje bodu, pokud nechcete, aby přepracování nebo přepisovat kód, můžete containerize existující aplikace a nadále používat stejné technologie .NET a má stejný kód. Uvidíte, jak můžete spouštět aplikace, jako jsou ty do kontejnerů bez uložení změn do starší verze kódu.

### <a name="benefits"></a>Výhody

Výhody tohoto návodu jsou jednoduché: právě Seznamte se s konfigurací kód a aplikace založené na vkládání závislostí. Potom můžete experimentovat s tímto přístupem při containerize a nasazení do několika prostředí v budoucnu.

### <a name="next-steps"></a>Další kroky

Prozkoumejte podrobnější tento obsah na stránkách wiki Githubu:

[https://github.com/DotNet-Architecture/eShopModernizing/Wiki/01.-Tour-on-eShopModernizing-Apps-Implementation-Code](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a>Návod 2: Containerize existující aplikace .NET s kontejnery Windows

### <a name="technical-walkthrough-availability"></a>Technické návod dostupnosti

Úplné technické návod je k dispozici na stránkách wiki úložišti GitHub eShopModernizing:

[https://github.com/DotNet-Architecture/eShopModernizing/Wiki/02.-How-to-containerized-the-.NET-Framework-Web-Apps-with-Windows-Containers-and-Docker](https://https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerized-the-.NET-Framework-web-apps-with-Windows-Containers-and-DockerTBD)

### <a name="overview"></a>Přehled

Použití Windows kontejnerů ke zlepšení nasazení existujících aplikací .NET, například algoritmů založených na rozhraní MVC a webových formulářů, WCF, výroby, vývoj a testovací prostředí.

### <a name="goals"></a>Cíle

Cílem tohoto návodu je tak, aby zobrazovalo několik možností pro containerizing stávající aplikace rozhraní .NET Framework. Můžeš:

-   Containerize vaší aplikace pomocí [2017 nástroje sady Visual Studio pro Docker](https://docs.microsoft.com/dotnet/core/docker/visual-studio-tools-for-docker) (Visual Studio 2017 nebo novější verze).

-   Containerize aplikace tak, že ručně přidáte [soubor Docker](https://docs.docker.com/engine/reference/builder/)a potom pomocí [příkazového řádku Dockeru](https://docs.docker.com/engine/reference/commandline/cli/).

-   Containerize vaší aplikace pomocí [Img2Docker](https://github.com/docker/communitytools-image2docker-win) (nástroj open-source z Docker).

Tento názorný postup se zaměřuje na Visual Studio Tools 2017 Docker přístup, ale jsou tyto dva přístupy dost podobné namapoval pomocí Dockerfiles.

### <a name="scenario"></a>Scénář

Obrázek 5-3 ukazuje tento scénář pro kontejnerizované eShop starší verze aplikací.

> ![Diagram architektury zjednodušené kontejnerizované aplikací ve vývojovém prostředí](./media/image5-3.png)
>
> **Obrázek 5-3.** Diagram architektury zjednodušené kontejnerizované aplikací ve vývojovém prostředí

### <a name="benefits"></a>Výhody

Existují výhody používání aplikace monolitický v kontejneru. Nejprve je třeba vytvořit bitovou kopii pro aplikaci. Od tohoto okamžiku v každé nasazení běží ve stejném prostředí. Každý kontejner používá stejnou verzi operačního systému, má stejnou verzi závislostí nainstalována, používá stejnou verzi rozhraní .NET framework a je vytvořen pomocí stejného procesu. V podstatě řídit závislostí vaší aplikace pomocí Docker bitové kopie. Závislosti cestují k aplikaci při nasazení kontejnerů.

Další výhodou je, že vývojáři aplikaci můžete spustit v konzistentní prostředí, které poskytuje Windows kontejnery. Problémy, které se zobrazují pouze u některých verzí můžete okamžitě, nanese místo zpřístupnění v pracovním nebo produkčním prostředí. Rozdíly ve vývojovém prostředí používá členové týmu pro vývoj podstatné menší při spuštění aplikace v kontejnerech.

Kontejnerizované aplikací mít také plošší křivky Škálováním na více systémů. Kontejnerizované aplikací umožňují mít další aplikace a instance služby (podle kontejnery) v virtuálního počítače nebo fyzického počítače ve srovnání s nasazení regulární aplikací na počítač. Výsledkem je vyšší hustotu a méně požadované prostředky, zejména v případě, že používáte orchestrators jako Kubernetes nebo Service Fabric.

Rozdělení do kontejnerů v situacích, ideální, není nutné provádět jakékoliv změny kódu aplikace (C\#). Ve většině scénářů bude třeba jen soubory metadat nasazení Docker (soubory Dockerfiles a Docker Compose).

### <a name="next-steps"></a>Další kroky

Prozkoumat podrobnější tento obsah na stránkách wiki Githubu: [https://https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerized-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerized-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a>Návod 3: Nasazení aplikace systému Windows na základě kontejnery pro virtuální počítače Azure

### <a name="technical-walkthrough-availability"></a>Technické návod dostupnosti

Úplné technické návod je k dispozici na stránkách wiki úložišti GitHub eShopModernizing:

[https://github.com/DotNet-Architecture/eShopModernizing/Wiki/03.-How-to-deploy-Your-Windows-Containers-Based-App-INTO-Azure-VMs-(Including-ci-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

### <a name="overview"></a>Přehled

Nasazení na Docker hostitele na virtuální počítač Windows serveru 2016 v Azure umožňuje rychle nastavit dev/testovací/přípravného prostředí. Také poskytuje společné místo pro testery nebo podnikoví uživatelé k ověření aplikace. Virtuální počítače mohou být také platný IaaS provozní prostředí.

### <a name="goals"></a>Cíle

Cílem tohoto návodu je tak, aby zobrazovalo více alternativy, které máte, když nasadíte kontejnery Windows na virtuálních počítačích Azure, které jsou založené na systému Windows Server 2016 nebo novější verze.

### <a name="scenarios"></a>Scénáře

Několik scénáře jsou popsané v tomto návodu.

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a>Scénář A: nasazení na virtuální počítač Azure ze dev počítače prostřednictvím připojení modulu Docker

![Nasazení na virtuální počítač Azure z vývojářů počítače prostřednictvím připojení k modulu Docker](./media/image5-4.png)

> **Obrázek 5 – 4.** Nasazení na virtuální počítač Azure z vývojářů počítače prostřednictvím připojení k modulu Docker

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a>Scénář B: nasazení na virtuální počítač Azure prostřednictvím registru Docker

![Nasazení na virtuální počítač Azure prostřednictvím registru Docker](./media/image5-5.png)

> **Obrázek 5-5.** Nasazení na virtuální počítač Azure prostřednictvím registru Docker

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-visual-studio-team-services"></a>Scénář C: nasazení na virtuální počítač Azure z položek konfigurace nebo CD kanály v sadě Visual Studio Team Services

![Nasazení z položek konfigurace nebo CD kanály v sadě Visual Studio Team Services na virtuální počítač Azure](./media/image5-6.png)

> **Obrázek 5 a 6.** Nasazení z položek konfigurace nebo CD kanály v sadě Visual Studio Team Services na virtuální počítač Azure

### <a name="azure-vms-for-windows-containers"></a>Virtuální počítače Azure pro Windows kontejnery

Azure kontejnery virtuálních počítačů pro Windows jsou jednoduše virtuálních počítačů, které jsou založené na systému Windows Server 2016, Windows 10 nebo novější verze, jak k modulu Docker nastavit. Ve většině případů bude používat systém Windows Server 2016 ve virtuálních počítačích Azure.

Virtuální počítač s názvem aktuálně poskytuje Azure **systému Windows Server 2016 s kontejnery**. Můžete vyzkoušet nové funkce kontejneru systému Windows Server s Windows Server Core nebo Windows Nano Server můžete použít tento virtuální počítač. Kontejner imagí operačního systému jsou nainstalované a je připravený k použití s Docker virtuálního počítače.

### <a name="benefits"></a>Výhody

I když Windows kontejnery mohou být nasazeny do místní 2016 virtuálních počítačů Windows serveru, když nasadíte do Azure, můžete získat snadný způsob, jak začít pracovat s virtuálními počítači kontejneru připravené k použití Windows serveru. Můžete také získat běžné online umístění, které je přístupné pro testery a automatické škálovatelnost prostřednictvím sady škálování virtuálního počítače Azure.

### <a name="next-steps"></a>Další kroky

Prozkoumejte podrobnější tento obsah na stránkách wiki Githubu:

[https://github.com/DotNet-Architecture/eShopModernizing/Wiki/03.-How-to-deploy-Your-Windows-Containers-Based-App-INTO-Azure-VMs-(Including-ci-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a>Návod 4: Nasazení aplikace na základě kontejnery Windows do Kubernetes v Azure Container Service

### <a name="technical-walkthrough-availability"></a>Technické návod dostupnosti

Úplné technické návod je k dispozici na stránkách wiki úložišti GitHub eShopModernizing:

[https://github.com/DotNet-Architecture/eShopModernizing/Wiki/04.-How-to-deploy-Your-Windows-Containers-Based-Apps-INTO-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

### <a name="overview"></a>Přehled

Aplikace, která je založena na systému Windows kontejnery rychle muset platformy, přesunutí i další počítače z virtuálních počítačů IaaS. To je potřeba snadno dosáhnout vysoké škálovatelnost a lépe automatizované škálovatelnost a pro přináší značné vylepšení v automatizované nasazení a správa verzí. Tyto cíle můžete dosáhnout pomocí orchestrator [Kubernetes](https://kubernetes.io/), k dispozici v [služby kontejneru Azure](https://azure.microsoft.com/services/container-service/).

### <a name="goals"></a>Cíle

Cílem tohoto návodu je další informace o nasazení aplikace na základě kontejneru systému Windows k Kubernetes (také nazývané *K8s*) v Azure Container Service. Nasazení do Kubernetes od začátku je dvoustupňový proces:

1.  Nasaďte Kubernetes clusteru Azure Container Service.

2.  Nasazení aplikace a související prostředky do clusteru Kubernetes.

### <a name="scenarios"></a>Scénáře

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a>Scénář A: nasadit přímo do clusteru s podporou Kubernetes z prostředí vývojářů

![Nasazení přímo na clusteru s podporou Kubernetes z prostředí pro vývoj](./media/image5-7.png)

> **Obrázek 5 – 7.** Nasazení přímo na clusteru s podporou Kubernetes z prostředí pro vývoj

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-team-services"></a>Scénář B: nasadit do clusteru s podporou Kubernetes z položek konfigurace nebo CD kanálů v Team Services

![Nasazení do clusteru s podporou Kubernetes z položek konfigurace nebo CD kanály v Team Services](./media/image5-8.png)

> **Obrázek 5-8.** Nasazení do clusteru s podporou Kubernetes z položek konfigurace nebo CD kanály v Team Services

### <a name="benefits"></a>Výhody

Existuje mnoho výhod nasazení do clusteru s podporou v Kubernetes. Největší výhodou je, že dostanete prostředí produkční prostředí, ve kterém můžete můžete škálování aplikace založené na počet instancí kontejneru, které chcete použít (vnitřní škálovatelnost v existujícím uzlům) a na základě počtu uzlů nebo virtuální počítače v clusteru ( Globální škálovatelnost clusteru).

Azure Container Service optimalizuje oblíbených open-source nástrojů a technologií speciálně pro Azure. Získat otevřete řešení, která nabízí přenositelnost pro vaše kontejnery i pro konfiguraci aplikace. Vyberte velikost, počtu hostitelů, a nástrojů orchestrator-kontejneru služby zpracovává nic jiného.

S Kubernetes mohou vývojáři průběhu od přemýšlení o fyzické a virtuální počítače k plánování zaměřené na kontejner infrastruktury, která usnadňuje následující funkce, mimo jiné:

-   Aplikace založené na několika kontejnerů

-   Replikace instancí kontejnerů a vodorovné automatické škálování

-   Pojmenování a zjišťování (například interní DNS)

-   Vyrovnávání zatížení

-   Vrácení aktualizace

-   Distribuce tajné klíče

-   Kontroly stavu aplikace

## <a name="next-steps"></a>Další kroky

Prozkoumat podrobnější tento obsah na stránkách wiki Githubu: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-() Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a>Návod 5: Nasazení aplikace na základě kontejnery Windows do Azure Service Fabric

### <a name="technical-walkthrough-availability"></a>Technické návod dostupnosti

Úplné technické návod je k dispozici na stránkách wiki úložišti GitHub eShopModernizing:

[https://github.com/DotNet-Architecture/eShopModernizing/Wiki/05.-How-to-deploy-Your-Windows-Containers-Based-Apps-INTO-Azure-Service-Fabric-(Including-ci-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

### <a name="overview"></a>Přehled

Aplikace, která je založena na systému Windows kontejnery rychle muset platformy, přesunutí i další počítače z virtuálních počítačů IaaS. To je potřeba snadno dosáhnout vysoké škálovatelnost a lépe automatizované škálovatelnost a pro přináší značné vylepšení v automatizované nasazení a správa verzí. Pomocí orchestrator Azure Service Fabric, která je k dispozici v cloudu Azure, ale také k dispozici pro použití v místě, nebo i v různých veřejného cloudu, můžete dosáhnout těchto cílů.

### <a name="goals"></a>Cíle

Cílem tohoto návodu je další informace o nasazení aplikace na základě kontejneru systému Windows do clusteru Service Fabric v Azure. Nasazení do Service Fabric od začátku je dvoustupňový proces:

1.  Cluster Service Fabric nasaďte do Azure (nebo do různých prostředí).

2.  Nasaďte aplikace a související prostředky do clusteru Service Fabric.

### <a name="scenarios"></a>Scénáře

#### <a name="scenario-a-deploy-directly-to-a-service-fabric-cluster-from-a-dev-environment"></a>Scénář A: nasadit přímo na clusteru Service Fabric z prostředí vývojářů

![Nasazení z prostředí pro vývoj přímo na clusteru Service Fabric](./media/image5-9.png)

> **Obrázek 5-9.** Nasazení z prostředí pro vývoj přímo na clusteru Service Fabric

### <a name="scenario-b-deploy-to-a-service-fabric-cluster-from-cicd-pipelines-in-team-services"></a>Scénář B: nasadit do clusteru Service Fabric z položek konfigurace nebo CD kanálů v Team Services

![Nasazení na cluster Service Fabric z položek konfigurace nebo CD kanály v sadě Visual Studio Team Services](./media/image5-10.png)

> **Obrázek 5-10.** Nasazení na cluster Service Fabric z položek konfigurace nebo CD kanály v sadě Visual Studio Team Services

## <a name="benefits"></a>Výhody

Výhody nasazení na cluster Service Fabric se podobá výhody použití Kubernetes. Jeden rozdíl, ale je, že Service Fabric je velmi vyspělá produkčním prostředí pro aplikace systému Windows ve srovnání s Kubernetes, která byla ve verzi preview pro kontejnery Windows dokud již v rané fázi spadají 2017. (Kubernetes je víc vyspělých prostředí pro Linux). 

Hlavní výhodou používání Azure Service Fabric je, že dostanete prostředí produkční prostředí, ve kterém můžete můžete škálování aplikace založené na počet instancí kontejneru, které chcete použít (vnitřní škálovatelnost v existujícím uzlům) a na základě počtu uzly nebo virtuální počítače v clusteru (globální škálovatelnost clusteru).

Azure Service Fabric nabízí přenositelnost pro vaše kontejnery i pro konfiguraci aplikace. Můžete mít Service Fabric cluster v Azure a nainstalujte ji na místě ve svém vlastním datovém centru. Můžete nainstalovat i clusteru Service Fabric v jiném cloudu, jako je třeba [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).

Pomocí Service Fabric mohou vývojáři průběhu od přemýšlení o fyzické a virtuální počítače k plánování zaměřené na kontejner infrastruktury, která usnadňuje následující funkce, mimo jiné:

-   Aplikace založené na několika kontejnerů.

-   Replikace instancí kontejnerů a vodorovné automatické škálování.

-   Pojmenování a zjišťování (například interní DNS).

-   Vyrovnávání zatížení.

-   Vrácení aktualizace.

-   Distribuce tajných klíčů.

-   Kontroluje stav aplikací.

Následující funkce jsou výhradní v Service Fabric (ve srovnání s další orchestrators):

-   Funkce stavové služby prostřednictvím modelu aplikací spolehlivé služby.

-   Vzor aktéři prostřednictvím aplikačního modelu Reliable Actors.

-   Nasaďte úplné kost procesy, kromě kontejnery systému Windows nebo Linux.

-   Rozšířené kumulativní aktualizace a kontroly stavu.

### <a name="next-steps"></a>Další kroky

Prozkoumejte podrobnější tento obsah na stránkách wiki Githubu:

[https://github.com/DotNet-Architecture/eShopModernizing/Wiki/05.-How-to-deploy-Your-Windows-Containers-Based-Apps-INTO-Azure-Service-Fabric-(Including-ci-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

>[!div class="step-by-step"]
[Předchozí](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[další](conclusions.md)
