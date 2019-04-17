---
title: Návody a přehled technických začátků
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a kontejnery Windows | Návody a technický přehled Začínáme
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 2202e2f972951e4074ed1941f0a0cfe352ab4b85
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612950"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a>Návody a přehled technických začátků

Omezení velikosti tuto elektronickou příručku, další technickou dokumentaci a úplné názorné postupy byly k dispozici v úložišti GitHub. Online řada návodů, který je popsaný v této kapitole zahrnuje podrobné nastavení více prostředí, které jsou založeny na kontejnery Windows a nasazení do Azure.

Následující části popisují, co každého návodu je o cílech a vysoké úrovně pro zpracování obrazu a poskytuje diagramu úloh, které jsou zahrnuty. Můžete získat návody sami v *eShopModernizing* wiki úložiště GitHub aplikace na <https://github.com/dotnet-architecture/eShopModernizing/wiki>.

## <a name="technical-walkthrough-list"></a>Seznam průvodcem produktem

Následující návody pro get-started poskytují komplexní a konzistentní technické pokyny pro ukázkové aplikace, které můžete přenést a shift pomocí kontejnerů a přesuňte pomocí několika možností nasazení v Azure.

Každá z následujících návodech používá nové ukázkové eShopLegacy a eShopModernizing aplikace, které jsou k dispozici na Githubu v <https://github.com/dotnet-architecture/eShopModernizing>.

- **Prohlídka eShop starší verze aplikací (aplikace pro směrný plán pro modernizaci)**

- **Kontejnerizace existující webových aplikací ASP.NET (WebForms & MVC) s kontejnery Windows**

- **Kontejnerizovat stávající službu WCF (aplikace pro N-vrstvá) s kontejnery Windows**

- **Nasazení aplikace založené na kontejnery Windows na virtuálních počítačích Azure**

- **Nasazení aplikací na základě kontejnerů Windows v Kubernetes ve službě Azure Container Service**

- **Nasazení aplikace založené na kontejnery Windows do Azure Service Fabric**

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a>Návod 1: Prohlídka eShop starší verze aplikací

### <a name="technical-walkthrough-availability"></a>Dostupnost průvodcem produktem

Je k dispozici v wiki úložiště GitHub eShopModernizing plnou technickou názorný postup:

[návody eShopModernizing wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a>Přehled

V tomto podrobném návodu můžete prozkoumat počáteční implementace tři ukázkové starší verze aplikace. První dva ukázkové webové aplikace mají monolitické architektury a byly vytvořeny pomocí klasického rozhraní ASP.NET. Jedna aplikace je založena na technologii ASP.NET 4.x MVC; Druhá aplikace je založena na webových formulářů ASP.NET 4.x.
Třetí aplikace je 3vrstvé aplikace skládající se tak, že klientská aplikace WinForms a na straně serveru [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) služby.

Všechny tyto aplikace jsou k dispozici na [úložiště GitHub eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).

### <a name="goals"></a>Cíle

Hlavním cílem tohoto návodu je jednoduše a seznamte se s těmito aplikacemi a s jejich kódu a konfigurace. Aplikace můžete nakonfigurovat tak, aby generovat a používat mock data bez použití databáze SQL pro účely testování. Tato volitelná konfigurace je založen na vkládání závislostí oddělující způsobem.

### <a name="scenario-1-aspnet-web-apps"></a>Scénář 1: Webových aplikací ASP.NET

Následující obrázek znázorňuje jednoduchý scénář původní starší verze webových aplikací ASP.NET.

![Jednoduchá architektura scénář původní starší verze webových aplikací ASP.NET](./media/image5-1.png)

Z hlediska domény firmy obě aplikace nabízejí katalogu stejné funkce pro správu. Členové týmu enterprise eShop využije aplikace k zobrazení a úprava katalog produktů.

Následující obrázek ukazuje na snímcích obrazovky počáteční aplikace.

![Aplikace ASP.NET MVC a ASP.NET Web Forms (technologie existující/starší verze)](./media/image5-2.png)

Závislosti v technologii ASP.NET 4.x a předchozími verzemi (buď pro MVC nebo pro webové formuláře) znamená, že se tyto aplikace nespustí v rozhraní .NET Core, pokud kód je úplně přepsán pomocí ASP.NET Core MVC.

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a>Scénář 2: Aplikace WinForms klienta (3vrstvé aplikace) a služby WCF

Následující obrázek znázorňuje jednoduchý scénář původní 3vrstvá starší verze aplikace.

![Jednoduchá architektura scénář být vybavené klientskou aplikací WinForms a původní starší verze 3vrstvé aplikace se službou WCF](./media/image5-1.5.png)

### <a name="benefits"></a>Výhody

Výhody tohoto názorného postupu jsou jednoduché: Získejte zkušenosti s kódem a počáteční aplikace.

### <a name="next-steps"></a>Další kroky

Tento obsah podrobnější zkoumání na Wiki úložiště GitHub:

- [Prohlídka na základní technologie ASP.NET MVC a aplikace webových formulářů "starší"](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [Prohlídka na aplikace WinForms v "starší" (3 vrstvy) a služby WCF směrného plánu](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a>Návod 2: Kontejnerizace existující aplikace .NET s kontejnery Windows

### <a name="overview"></a>Přehled

Kontejnery Windows použijte ke zlepšení nasazení existujících aplikací .NET, jako jsou systémy založené na MVC, webových formulářů nebo WCF, do produkčního prostředí, vývojová a testovací prostředí.

### <a name="goals"></a>Cíle

Cílem tohoto návodu je zobrazit několik možností pro uzavření do kontejneru existující aplikaci .NET Framework. Můžete:

- Kontejnerizujte své aplikace pomocí [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 nebo novější verze).

- Kontejnerizujte své aplikace tak, že ručně přidáte [soubor Dockerfile](https://docs.docker.com/engine/reference/builder/)a následným použitím [rozhraní příkazového řádku Dockeru](https://docs.docker.com/engine/reference/commandline/cli/).

- Kontejnerizujte své aplikace pomocí [Img2Docker](https://github.com/docker/communitytools-image2docker-win) nástroje (nástroj open source od Dockeru).

Tento návod se zaměřuje na Visual Studio 2017 Tools for Docker přístup, ale ostatní dva přístupy jsou podobné ve vztahu pomocí soubory Dockerfile.

### <a name="scenario-1-containerized-aspnet-web-apps"></a>Scénář 1: Kontejnerizované webové aplikace ASP.NET

Následující obrázek znázorňuje scénář pro kontejnerizované eShop starší verze webové aplikace aplikace.

![Diagram architektury zjednodušené kontejnerizovaných aplikací technologie ASP.NET ve vývojovém prostředí](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a>Scénář 2: Kontejnerizovaná služba WCF

Následující obrázek znázorňuje scénář 3vrstvé aplikace s kontejnerizovaná služba WCF.

![Zjednodušená diagram architektury kontejnerizované služby WCF ve vývojovém prostředí](./media/image5-3.5.png)

### <a name="benefits"></a>Výhody

Existují výhody používání monolitické aplikace v kontejneru. Nejprve vytvořte image pro aplikaci. Od tohoto okamžiku v každé nasazení běží ve stejném prostředí. Každý kontejner používá stejnou verzi operačního systému, má stejnou verzi závislosti nainstalované, používá stejnou verzi rozhraní .NET framework a je vytvořena pomocí stejného procesu. V podstatě řízení závislostí vaší aplikace pomocí image Dockeru. Závislosti cestují s aplikací při nasazování kontejnerů.

Další výhodou je, že vývojáři spuštěním aplikace v prostředí konzistentní vzhledem k aplikacím, které poskytuje kontejnery Windows. Problémy, které se zobrazují pouze u některých verzí můžete okamžitě, nanese místo zpřístupnění v přípravném nebo produkčním prostředí. Rozdíly ve vývojovém prostředí, které používají členové vývojového týmu méně důležitá, když aplikace běží v kontejnerech.

Kontejnerizované aplikace také mít plošší křivky horizontální navýšení kapacity. Kontejnerizovaných aplikací umožňují další aplikace a instance služby (podle kontejnerů) virtuálního počítače nebo fyzického počítače, ve srovnání s nasazení aplikace pravidelně na počítač. Výsledkem je vyšší hustota a méně požadované prostředky, zejména v případě, že používáte orchestrátorů, jako je Kubernetes nebo Service Fabric.

Kontejnerizace v situacích, ideální, nevyžaduje změny kódu aplikace (C\#). Ve většině případů stačí Docker nasazení metadat souborů (soubory Dockerfile a Docker Compose soubory).

### <a name="next-steps"></a>Další kroky

Tento obsah podrobnější zkoumání na Wiki úložiště GitHub:

- [Jak kontejnerizovat aplikace webového rozhraní .NET Framework s kontejnery Windows a Dockeru](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [Přidání podpory Dockeru do služby WCF](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a>Návod 3: Nasazení aplikace založené na kontejnery Windows na virtuálních počítačích Azure

### <a name="technical-walkthrough-availability"></a>Dostupnost průvodcem produktem

Je k dispozici v wiki úložiště GitHub eShopModernizing plnou technickou názorný postup: <https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

### <a name="overview"></a>Přehled

Nasazení na hostitele Docker na Windows serveru 2016 virtuálního počítače (počítače) v Azure umožňuje rychle nastavit vývojové/testovací/přípravných prostředí. Také poskytuje společné místo pro testery nebo firemním uživatelům ověřovat aplikace. Virtuální počítač také může být platný infrastruktury jako služby (IaaS) produkční prostředí.

### <a name="goals"></a>Cíle

Cílem tohoto návodu je zobrazit více alternativy, které jste při nasazování kontejnerů Windows na virtuální počítače Azure, které jsou založené na Windows Server 2016 nebo novější verze.

### <a name="scenarios"></a>Scénáře

Několik scénáře jsou popsané v tomto názorném postupu.

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a>Scénář A: Nasazení na Virtuálním počítači Azure z vývojář počítače přes připojení modul Docker

![Nasazení na Virtuálním počítači Azure z vývojář PC prostřednictvím připojení k modulu Docker](./media/image5-4.png)

**Obrázek 5 – 4.** Nasazení na Virtuálním počítači Azure z vývojář PC prostřednictvím připojení k modulu Docker

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a>Scénář B: Nasazení do virtuálního počítače Azure pomocí registru Dockeru

![Nasazení do virtuálního počítače Azure pomocí registru Dockeru](./media/image5-5.png)

**Obrázek 5 – 5.** Nasazení do virtuálního počítače Azure pomocí registru Dockeru

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a>Scénář C: Nasazení na Virtuálním počítači Azure z kanálů CI/CD ve službách Azure DevOps

![Nasazení na Virtuálním počítači Azure z kanálů CI/CD ve službách Azure DevOps](./media/image5-6.png)

**Obrázek 5 a 6.** Nasazení na Virtuálním počítači Azure z kanálů CI/CD ve službách Azure DevOps

### <a name="azure-vms-for-windows-containers"></a>Virtuální počítače Azure pro kontejnery Windows

Virtuální počítače pro Windows kontejnery služby Azure jsou virtuálních počítačů založených na Windows serveru 2016, Windows 10 nebo novější verze, s modul Docker nastavení. Ve většině případů se používá Windows Server 2016 ve virtuálních počítačích Azure.

Azure v současné době poskytuje virtuální počítač s názvem **Windows serveru 2016 s kontejnery**. Tento virtuální počítač můžete vyzkoušet nové funkce kontejneru Windows serveru s Windows Server Core nebo Windows Nano Server. Kontejnerové Image operačního systému jsou nainstalovány a pak je virtuální počítač připravený k použití s Dockerem.

### <a name="benefits"></a>Výhody

I když se dají nasadit kontejnery Windows pro místní Windows Server 2016 virtuální počítače, při nasazování do Azure, budete mít snadný způsob, jak začít s virtuálními počítači kontejneru připravené k použití Windows serveru. Získáte také běžné online umístění, která je přístupná pro testery a automatické škálovatelnosti pomocí škálovací sady virtuálních počítačů Azure.

### <a name="next-steps"></a>Další kroky

Tento obsah podrobnější zkoumání na Wiki úložiště GitHub:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a>Návod 4: Nasazovat aplikace založené na kontejnery Windows do služby Azure Container Instances (ACI)

### <a name="technical-walkthrough-availability"></a>Dostupnost průvodcem produktem

Je k dispozici v wiki úložiště GitHub eShopModernizing plnou technickou názorný postup:

[Nasazení aplikace do služby ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

### <a name="overview"></a>Přehled

[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) je nejrychlejší způsob, jak prostředí dev/test/přípravy kontejnerů, kde můžete nasadit jeden instancí kontejnerů.

### <a name="goals"></a>Cíle

Tento návod ukazuje základní scénáře při nasazování kontejnerů Windows do Azure Container Instances (ACI) a jak můžete nasadit aplikace eShopModernizing do ACI.

### <a name="scenarios"></a>Scénáře

Může existovat variace o nasazení aplikací eShopModernizing do ACI, jako je nasazení jenom v jednom nebo všechny aplikace (aplikace MVC, webových formulářů aplikaci nebo službu WCF). V následujícím scénáři je uvedeno níže můžete vidět aplikaci ASP.NET MVC a kontejner SQL serveru, jejich nasazení jako kontejnery do ACI (Azure Container Instances).

![Nasazení do služby ACI z vývojového prostředí](./media/image5-3.5.6.png)

### <a name="benefits"></a>Výhody

Služba Azure Container Instances usnadňuje vytváření a správu kontejnerů Dockeru v Azure, aniž byste museli zřizovat virtuální počítače nebo používat službu. Pomocí ACI můžete přímo nasadit kontejner Windows ve službě Azure a zveřejníte ho na Internetu s použitím plně kvalifikovaného názvu domény (FQDN) v řádu sekund (za předpokladu, že budete mít připravený kontejner Windows image v registru Dockeru jako Docker Hubu nebo služby Azure Container Registru).

### <a name="considerations"></a>Požadavky

Nasazování kontejnerů Windows s buď úplné rozhraní .NET Framework / technologie ASP.NET nebo SQL serveru do Azure Container Instances (ACI) není úplně tak rychlý jako při nasazování na regulární hostitele Docker (např. Windows Server 2016 s kontejnery Windows), protože image Dockeru, musí být stažení (načtený z registru Dockeru) pokaždé, když a i když je mnohem levnější než udržování vašeho vlastního hostitele docker (trvale online jsou výrazně velké velikosti image kontejneru SQL (15.1 GB) a image kontejneru ASP.NET (13.9 GB) Windows Server 2016 s virtuálním Počítačem kontejnery Windows v Azure) nemluvě celý orchestrator, jako je Kubernetes v Azure (/ služby AKS ACS) nebo Azure Service Fabric, které jsou na druhé straně skvělou možností pro nasazení v produkčním prostředí.

Jako hlavní uzavření pomocí služby Azure Container Instances je velice přesvědčivý argument možnost pro scénáře vývoje/testování a pro kanály CI/CD.

## <a name="next-steps"></a>Další kroky

Tento obsah podrobnější zkoumání na Wiki úložiště GitHub:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)TBD)

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a>Návod 5: Nasazení aplikací na základě kontejnerů Windows v Kubernetes ve službě Azure Container Service

### <a name="technical-walkthrough-availability"></a>Dostupnost průvodcem produktem

Je k dispozici v wiki úložiště GitHub eShopModernizing plnou technickou názorný postup:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)>

### <a name="overview"></a>Přehled

Aplikace, která je založena na kontejnery Windows rychle muset použít platformy, přesunutí ještě více pryč z virtuálních počítačů IaaS. To je potřeba provést snadno dosáhnout vysoké škálovatelnosti a lépe automatizované škálovatelnost a přináší značné vylepšení v automatické nasazení a správy verzí. Tyto cíle lze dosáhnout pomocí orchestrátoru [Kubernetes](https://kubernetes.io/), která je dostupná v [služby Azure Container Service](https://azure.microsoft.com/services/container-service/).

### <a name="goals"></a>Cíle

Cílem tohoto návodu je naučit se nasazovat aplikace založené na Windows kontejnerů Kubernetes (také nazývané *K8s*) ve službě Azure Container Service. Nasazování do Kubernetes úplně od začátku je dvoustupňový proces:

1. Nasazení clusteru Kubernetes do služby Azure Container Service.

2. Nasazení aplikace a související prostředky do clusteru Kubernetes.

### <a name="scenarios"></a>Scénáře

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a>Scénář A: Nasadit do clusteru Kubernetes z vývojového prostředí

![Nasadit do clusteru Kubernetes z vývojového prostředí](./media/image5-7.png)

**Obrázek 5 – 7.** Nasadit do clusteru Kubernetes z vývojového prostředí

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a>Scénář B: Nasazení do clusteru Kubernetes z kanálů CI/CD ve službách Azure DevOps

![Nasazení do clusteru Kubernetes z kanálů CI/CD ve službách Azure DevOps](./media/image5-8.png)

**Obrázek 5 až 8.** Nasazení do clusteru Kubernetes z kanálů CI/CD ve službách Azure DevOps

### <a name="benefits"></a>Výhody

Existuje mnoho výhod pro nasazení do clusteru v Kubernetes. Největší výhodou je, že dostanete prostředí připravené pro produkční prostředí, ve kterém můžete aplikace založená na počet instancí kontejneru chcete použít (vnitřní škálovatelnost v existujících uzlů) a na základě počtu virtuálních počítačů nebo uzly v clusteru (horizontálně navýšit Globální škálovatelnost clusteru).

Služba Azure Container Service optimalizuje oblíbených opensourcových nástrojů a technologií konkrétně pro Azure. Získáte otevřené řešení, které nabízí přenositelnost pro vaše kontejnery i Konfigurace aplikací. Vyberete velikost, počet hostitelů, a nástroje orchestrator – kontejner služby postará o všechno ostatní.

S využitím Kubernetes můžete průběh vývojáře od přemýšlení o fyzické a virtuální počítače, k plánování zaměřené na kontejner infrastruktury, která usnadňuje následující funkce, mimo jiné:

- Aplikace založené na několika kontejnerů

- Replikace container instances a automatické horizontální škálování

- Pojmenování a zjišťování (například interní DNS)

- Vyrovnávání zatížení

- Aktualizace se zajištěním provozu

- Distribuce tajných kódů

- Kontroly stavu aplikace

## <a name="next-steps"></a>Další kroky

Tento obsah podrobnější zkoumání na Wiki úložiště GitHub: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a>Návod 6: Nasazení aplikace založené na kontejnery Windows do Azure Service Fabric

### <a name="technical-walkthrough-availability"></a>Dostupnost průvodcem produktem

Je k dispozici v wiki úložiště GitHub eShopModernizing plnou technickou názorný postup:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)>

### <a name="overview"></a>Přehled

Aplikace založené na kontejnery Windows rychle musí používat platformy, přesunutí ještě více pryč z virtuálních počítačů IaaS. To je potřeba provést snadno dosáhnout vysoké škálovatelnosti a lépe automatizované škálovatelnost a přináší značné vylepšení v automatické nasazení a správy verzí. Pomocí Azure Service Fabric, která je k dispozici v cloudu Azure, ale také k dispozici pro použití v místním, orchestrator nebo dokonce i v různých veřejného cloudu, můžete dosáhnout těchto cílů.

### <a name="goals"></a>Cíle

Cílem tohoto návodu je naučit se nasazovat aplikace založené na Windows kontejnerů do clusteru Service Fabric v Azure. Nasazení do Service Fabric úplně od začátku je dvoustupňový proces:

1. Nasazení clusteru Service Fabric do Azure (nebo do jiného prostředí).

2. Nasazení aplikace a související prostředky do clusteru Service Fabric.

### <a name="scenarios"></a>Scénáře

#### <a name="scenario-a-deploy-directly-to-a-service-fabric-cluster-from-a-dev-environment"></a>Scénář A: Nasadit do clusteru Service Fabric z vývojového prostředí

![Nasadit do clusteru Service Fabric z vývojového prostředí](./media/image5-9.png)

> **Obrázek 5 až 9.** Nasadit do clusteru Service Fabric z vývojového prostředí

### <a name="scenario-b-deploy-to-a-service-fabric-cluster-from-cicd-pipelines-in-azure-devops-services"></a>Scénář B: Nasazení do clusteru Service Fabric z kanálů CI/CD ve službách Azure DevOps

![Nasazení do clusteru Service Fabric z kanálů CI/CD ve službách Azure DevOps](./media/image5-10.png)

**Obrázek 5 – 10.** Nasazení do clusteru Service Fabric z kanálů CI/CD ve službách Azure DevOps

## <a name="benefits"></a>Výhody

Výhody nasazení do clusteru v Service Fabric jsou podobné výhody používání Kubernetes. Jedním z rozdílů, ale je, že Service Fabric je vyspělejší produkčním prostředí pro aplikace Windows ve srovnání s Kubernetes, který je ve fázi beta pro kontejnery Windows v Kubernetes verze 1.9 (prosinec 2017). Kubernetes je vyspělejší prostředí pro Linux.

Hlavní výhodou použití Azure Service Fabric je, že dostanete prostředí připravené pro produkční prostředí, ve kterém můžete škálovat aplikace založená na počet instancí kontejneru chcete použít (vnitřní škálovatelnost v existujících uzlů) a podle počtu uzly nebo virtuální počítače v clusteru (globální škálovatelnost clusteru).

Azure Service Fabric nabízí přenositelnost pro vaše kontejnery i Konfigurace aplikací. Můžete použít Service Fabric cluster v Azure, nebo ji nainstalovat lokálně ve vašem vlastním datovém centru. Můžete nainstalovat i cluster Service Fabric v jiný cloud, jako je třeba [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).

S využitím Service Fabric můžete průběh vývojáře od přemýšlení o fyzické a virtuální počítače k plánování zaměřené na kontejner infrastruktury, která usnadňuje následující funkce, mimo jiné:

- Aplikace založené na několik kontejnerů.

- Replikace container instances a automatické horizontální škálování.

- Pojmenování a zjišťování (například interní DNS).

- Vyrovnávání zatížení.

- Aktualizace se zajištěním provozu.

- Distribuce tajných kódů.

- Kontroluje se stav aplikace.

Tyto možnosti jsou výhradně v Service Fabric (ve srovnání se jiných orchestrátorů):

- Funkce stavové služby, prostřednictvím aplikačního modelu Reliable Services.

- Model objektů actor, prostřednictvím aplikačního modelu Reliable Actors.

- Nasazení úplné kost procesy, kromě kontejnery Windows nebo Linux.

- Pokročilé kumulativní aktualizace a kontroly stavu.

### <a name="next-steps"></a>Další kroky

Tento obsah podrobnější zkoumání na Wiki úložiště GitHub:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)>

> [!div class="step-by-step"]
> [Předchozí](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
> [další](conclusions.md)
