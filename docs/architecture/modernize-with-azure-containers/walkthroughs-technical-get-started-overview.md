---
title: Návody a přehled technických začátků
description: Modernizace existujících aplikací .NET pomocí Azure Cloudu a kontejnerů Windows | Přehled návodů a technických začátků
ms.date: 04/28/2018
ms.openlocfilehash: cff418d9b6e931a3082d8a2f8b818e7275139578
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987866"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a>Návody a přehled technických začátků

Chcete-li omezit velikost této e-knihy, další technická dokumentace a úplné návody byly k dispozici v úložišti GitHub. Online série návodů, která je popsána v této kapitole, zahrnuje podrobné nastavení více prostředí, která jsou založená na kontejnerech Windows, a nasazení do Azure.

V následujících částech je vysvětleno, o čem je každý návod, jeho cíle a vize na vysoké úrovni a poskytuje diagram úkolů, které jsou zapojeny. Návody můžete získat sami v *eShopmodernizing* apps GitHub <https://github.com/dotnet-architecture/eShopModernizing/wiki>repo wiki na .

## <a name="technical-walkthrough-list"></a>Technický seznam návodu

Následující návody pro získání práce poskytují konzistentní a komplexní technické pokyny pro ukázkové aplikace, které můžete zvedat a přesouvat pomocí kontejnerů a pak se přesunout pomocí několika možností nasazení v Azure.

Každý z následujících návodů používá nové ukázkové aplikace eShopLegacy a eShopModernizing, které jsou dostupné na GitHubu na adrese <https://github.com/dotnet-architecture/eShopModernizing>.

- **Prohlídka starších aplikací eShopu (základní aplikace pro modernizaci)**

- **Kontejnerujte stávající ASP.NET webové aplikace (WebForms & MVC) pomocí kontejnerů s Windows**

- **Kontejnerujte stávající služby WCF (aplikace N-Tier) pomocí kontejnerů windows**

- **Nasazení aplikace založené na kontejnerech Windows do virtuálních aplikací Azure**

- **Nasazení aplikací založených na kontejnerech Windows do Kubernetes ve službě Azure Container Service**

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a>Návod 1: Prohlídka starších aplikací eShopu

### <a name="technical-walkthrough-availability"></a>Dostupnost technického návodu

Úplný technický návod je k dispozici v eShopModernizing GitHub repo wiki:

[eShopModernizing wiki návody](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a>Přehled

V tomto návodu můžete prozkoumat počáteční implementaci tří ukázkových starších aplikací. První dvě ukázkové webové aplikace mají monolitickou architekturu a byly vytvořeny pomocí klasické ASP.NET. Jedna aplikace je založena na ASP.NET 4.x MVC; druhá aplikace je založena na ASP.NET 4.x Web Forms.
Třetí aplikace je 3vrstvá aplikace složená z klientské aplikace WinForms a služby [WCF (Windows Communication Foundation)](../../framework/wcf/whats-wcf.md) na straně serveru.

Všechny tyto aplikace jsou k dispozici v [eShopmodernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).

### <a name="goals"></a>Cíle

Hlavním cílem tohoto návodu je jednoduše seznámit se s těmito aplikacemi a s jejich kódem a konfigurací. Aplikace můžete nakonfigurovat tak, aby generovaly a používaly falešná data bez použití databáze SQL pro účely testování. Tato volitelná konfigurace je založena na vkládání závislostí, a to odděleným způsobem.

### <a name="scenario-1-aspnet-web-apps"></a>Scénář 1: ASP.NET webových aplikací

Na obrázku níže je uveden jednoduchý scénář původní starší ASP.NET webových aplikací.

![Jednoduchý scénář architektury původních starších ASP.NET webových aplikací](./media/image5-1.png)

Z pohledu obchodní domény nabízejí obě aplikace stejné funkce správy katalogu. Členové podnikového týmu eShopu by aplikaci používali k zobrazení a úpravám katalogu produktů.

Následující obrázek znázorňuje úvodní snímky obrazovky aplikace.

![ASP.NET aplikace MVC a ASP.NET webových formulářů (stávající/starší technologie)](./media/image5-2.png)

Závislosti v ASP.NET verze4.x nebo starší (buď pro MVC nebo pro webové formuláře) znamená, že tyto aplikace nebudou spuštěny na .NET Core, pokud není kód plně přepsán pomocí ASP.NET Core MVC.

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a>Scénář 2: Služba WCF a klientská aplikace WinForms (třívrstvá aplikace)

Na obrázku níže je uveden jednoduchý scénář původní verze 3 vrstvé aplikace.

![Jednoduchý scénář architektury původní původní třívrstvé aplikace se službou WCF a klientskou aplikací WinForms](./media/image5-1.5.png)

### <a name="benefits"></a>Výhody

Výhody tohoto návodu jsou jednoduché: Stačí se seznámit s kódem a počátečními aplikacemi.

### <a name="next-steps"></a>Další kroky

Prozkoumejte tento obsah podrobněji na wiki GitHubu:

- [Prohlídka základních ASP.NET "starších" aplikací MVC a webových formulářů](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [Prohlídka základní služby WCF a "starší) aplikace WinForms (3-Tier)](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a>Návod 2: Kontejnerizaci stávajících aplikací .NET pomocí kontejnerů windows

### <a name="overview"></a>Přehled

Kontejnery systému Windows slouží ke zlepšení nasazení existujících aplikací .NET, jako jsou aplikace založené na MVC, webových formulářích nebo WCF, do produkčního, vývojového a testovacího prostředí.

### <a name="goals"></a>Cíle

Cílem tohoto návodu je zobrazit několik možností pro kontejnerizaci existující aplikace rozhraní .NET Framework. Můžete:

- Kontejnerize aplikace pomocí [Visual Studio 2017 Nástroje pro Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 nebo novější verze).

- Kontejnerize aplikace ručním přidáním [Dockerfile](https://docs.docker.com/engine/reference/builder/)a potom pomocí [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).

- Kontejnerize aplikace pomocí nástroje [Img2Docker](https://github.com/docker/communitytools-image2docker-win) (open source nástroj z Dockeru).

Tento návod se zaměřuje na visual studio 2017 nástroje pro přístup Docker, ale další dva přístupy jsou poměrně podobné s ohledem na použití Dockerfiles.

### <a name="scenario-1-containerized-aspnet-web-apps"></a>Scénář 1: Kontejnerizované ASP.NET webových aplikací

Obrázek níže ukazuje scénář pro kontejnerizované aplikace eShop starších webových aplikací.

![Zjednodušený diagram architektury kontejnerizovaných ASP.NET aplikací ve vývojovém prostředí](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a>Scénář 2: Kontejnerizovaná služba WCF

Obrázek níže ukazuje scénář pro 3vrstvé aplikace s kontejnerizované WCF služby.

![Diagram zjednodušené architektury kontejnerizované služby WCF ve vývojovém prostředí](./media/image5-3.5.png)

### <a name="benefits"></a>Výhody

Spuštění monolitické aplikace v kontejneru má své výhody. Nejprve vytvoříte bitovou kopii pro aplikaci. Od tohoto okamžiku je každé nasazení spuštěno ve stejném prostředí. Každý kontejner používá stejnou verzi operačního systému, má nainstalovanou stejnou verzi závislostí, používá stejnou verzi rozhraní .NET framework a je sestaven pomocí stejného procesu. V podstatě můžete řídit závislosti vaší aplikace pomocí image Dockeru. Závislosti cestovat s aplikací při nasazení kontejnerů.

Další výhodou je, že vývojáři můžete spustit aplikaci v konzistentním prostředí, které je k dispozici kontejnery systému Windows. Problémy, které se zobrazují pouze u určitých verzí, mohou být zveřejnky okamžitě, namísto vynoření v pracovní nebo produkční prostředí. Rozdíly ve vývojových prostředích používaných členy vývojového týmu záleží méně, když aplikace spustit v kontejnerech.

Kontejnerizované aplikace mají také plošší křivku škálování. Kontejnerizované aplikace umožňují mít více instancí aplikací a služeb (založených na kontejnerech) ve virtuálním počítači nebo fyzickém počítači ve srovnání s běžnými nasazeními aplikací na počítač. To znamená vyšší hustotu a méně požadovaných prostředků, zejména při použití orchestrátorů, jako je Kubernetes.

Kontejnerizace v ideálních situacích nevyžaduje provedení jakýchkoli změn\#v kódu aplikace (C). Ve většině scénářů potřebujete pouze soubory metadat nasazení Dockeru (Dockerfiles a Docker Compose files).

### <a name="next-steps"></a>Další kroky

Prozkoumejte tento obsah podrobněji na wiki GitHubu:

- [Jak kontejnerizovat webové aplikace rozhraní .NET Framework pomocí kontejnerů windows a Dockeru](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [Přidání podpory Dockeru ke službě WCF](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a>Návod 3: Nasazení aplikace založené na kontejnerech Windows do virtuálních aplikací Azure

### <a name="technical-walkthrough-availability"></a>Dostupnost technického návodu

Úplný technický návod je k dispozici v eShopModernizing GitHub repo wiki:<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

### <a name="overview"></a>Přehled

Nasazení do hostitele Dockeru na virtuálním počítači (VM) Windows Serveru 2016 v Azure vám umožní rychle nastavit vývojová/testovací/pracovní prostředí. Poskytuje také společné místo pro testery nebo firemní uživatele k ověření aplikace. Virtuální virtuální servery mohou být také platné infrastruktury jako služby (IaaS) produkční prostředí.

### <a name="goals"></a>Cíle

Cílem tohoto návodu je zobrazit více alternativ, které máte při nasazování kontejnerů Windows do virtuálních aplikací Azure, které jsou založené na windows serverových nebo novějších verzích.

### <a name="scenarios"></a>Scénáře

V tomto návodu je popsáno několik scénářů.

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a>Scénář A: Nasazení na virtuální počítač Azure z počítače pro dev prostřednictvím připojení Docker Engine

![Nasazení na virtuální počítač Azure z počítače pro dev pc přes připojení Docker Engine](./media/image5-4.png)

**Obrázek 5-4.** Nasazení na virtuální počítač Azure z počítače pro dev pc přes připojení Docker Engine

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a>Scénář B: Nasazení na virtuální počítač Azure prostřednictvím registru Dockeru

![Nasazení na virtuální počítač Azure prostřednictvím registru Dockeru](./media/image5-5.png)

**Obrázek 5-5.** Nasazení na virtuální počítač Azure prostřednictvím registru Dockeru

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a>Scénář C: Nasazení na virtuální počítač Azure z kanálů CI/CD ve službách Azure DevOps Services

![Nasazení do virtuálního počítače Azure z kanálů CI/CD ve službách Azure DevOps Services](./media/image5-6.png)

**Obrázek 5-6.** Nasazení do virtuálního počítače Azure z kanálů CI/CD ve službách Azure DevOps Services

### <a name="azure-vms-for-windows-containers"></a>Virtuální počítače Azure pro kontejnery s Windows

Virtuální počítače Azure pro kontejnery s Windows jsou virtuální počítače založené na Windows Serveru 2016, Windows 10 nebo novějších verzích, obojí s nastaveným Docker Engine. Ve většině případů se Windows Server 2016 používá ve virtuálních počítačích Azure.

Azure aktuálně poskytuje virtuální počítač s názvem **Windows Server 2016 s kontejnery**. Pomocí tohoto virtuálního virtuálního serveru můžete vyzkoušet novou funkci Kontejner windows serveru, a to buď s Windows Server Core, nebo Windows Nano Server. Image operačního systému kontejneru jsou nainstalované a pak virtuální hovirtuální ms je připraven k použití s Dockeru.

### <a name="benefits"></a>Výhody

I když kontejnery Windows lze nasadit na místní virtuální počítače Windows Server 2016, při nasazení do Azure, získáte jednodušší způsob, jak začít, s ready-to-use Windows Server Kontejner virtuálnípočítače. Získáte také společné online umístění, které je přístupné testerům, a automatickou škálovatelnost prostřednictvím škálovacích sad virtuálních strojů Azure.

### <a name="next-steps"></a>Další kroky

Prozkoumejte tento obsah podrobněji na wiki GitHubu:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a>Návod 4: Nasazení aplikací založených na kontejnerech Windows do instancí kontejnerů Azure (ACI)

### <a name="technical-walkthrough-availability"></a>Dostupnost technického návodu

Úplný technický návod je k dispozici v eShopModernizing GitHub repo wiki:

[Nasazení aplikací do ACI (instance kontejnerů Azure)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

### <a name="overview"></a>Přehled

[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) je nejrychlejší způsob, jak mít kontejnery dev/test/pracovní prostředí, kde můžete nasadit jednotlivé instance kontejnerů.

### <a name="goals"></a>Cíle

Tento návod ukazuje hlavní scénáře při nasazování kontejnerů Windows do azure kontejnerů instance (ACI) a jak můžete nasadit eShopModernizing Apps do ACI.

### <a name="scenarios"></a>Scénáře

K dispozici mohou být různé informace o nasazení aplikací eShopModernizing do ACI, jako je nasazení pouze jedné nebo všech aplikací (aplikace MVC, aplikace WebForms nebo služba WCF). V následujícím scénáři je uvedeno níže uvidíte ASP.NET mvc aplikace plus kontejner SQL Server oba nasazené jako kontejnery do ACI (Azure Container Instances).

![Nasazení do ACI z vývojového prostředí](./media/image5-3.5.6.png)

### <a name="benefits"></a>Výhody

Služba Azure Container Instances usnadňuje vytváření a správu kontejnerů Dockeru v Azure, aniž byste museli zřizovat virtuální počítače nebo používat službu vyšší úrovně. S ACI můžete přímo nasadit kontejner Windows v Azure a vystavit ho na internet s plně kvalifikovaným názvem domény (FQDN) během několika sekund (za předpokladu, že máte image kontejneru Windows připraven v registru Docker, jako je Docker Hub nebo Azure Container Registry).

### <a name="considerations"></a>Požadavky

Nasazení kontejnerů Windows s úplnou rozhraním .NET Framework / ASP.NET nebo SQL Server do instancí kontejnerů Azure (ACI) není tak rychlé jako nasazení na běžném hostiteli Dockeru (jako je Windows Server 2016 s kontejnery Windows), protože bitová kopie Dockeru se musí stáhnout (vytáhnout z registru Dockeru) pokaždé a velikosti bitové kopie kontejneru SQL (15,1 GB) a image kontejneru ASP.NET (13,9 GB) jsou výrazně velké, je však mnohem levnější než údržba vlastního hostitele dockeru (trvale on-line Windows Server 2016 s virtuálním počítačem Windows Containers v Azure) nemluvě o celém orchestrátoru, jako je Kubernetes v Azure (AKS), což je na druhou stranu skvělá volba pro produkční nasazení.

Jako hlavní závěr pomocí Azure Container Instances je velmi přesvědčivá možnost pro scénáře pro vývoj a testování a pro kanály CI/CD.

## <a name="next-steps"></a>Další kroky

Prozkoumejte tento obsah podrobněji na wiki GitHubu:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a>Návod 5: Nasazení aplikací založených na kontejnerech Windows do Kubernetes ve službě Azure Container Service

### <a name="technical-walkthrough-availability"></a>Dostupnost technického návodu

Úplný technický návod je k dispozici v eShopModernizing GitHub repo wiki:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a>Přehled

Aplikace založená na kontejnerech Windows bude rychle muset používat platformy a posune se ještě dál od virtuálních aplikací IaaS. To je potřeba ke snadnému dosažení vysoké škálovatelnosti a lepší automatizované škálovatelnosti a k významnému zlepšení v automatizovaných nasazeních a správě verzí. Těchto cílů můžete dosáhnout pomocí orchestrátoru [Kubernetes](https://kubernetes.io/), který je k dispozici ve [službě Azure Container Services](https://azure.microsoft.com/services/container-service/).

### <a name="goals"></a>Cíle

Cílem tohoto návodu je naučit se nasadit aplikaci založenou na kontejneru Windows do Kubernetes (označované také jako *K8s)* ve službě Azure Container Service. Nasazení do Kubernetes od nuly je dvoustupňový proces:

1. Nasazení clusteru Kubernetes do služby Azure Container Service.

2. Nasazení aplikace a souvisejících prostředků do clusteru Kubernetes.

### <a name="scenarios"></a>Scénáře

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a>Scénář A: Nasazení přímo do clusteru Kubernetes z dev prostředí

![Nasazení přímo do clusteru Kubernetes z vývojového prostředí](./media/image5-7.png)

**Obrázek 5-7.** Nasazení přímo do clusteru Kubernetes z vývojového prostředí

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a>Scénář B: Nasazení do clusteru Kubernetes z kanálů CI/CD ve službách Azure DevOps Services

![Nasazení do clusteru Kubernetes z kanálů CI/CD ve službách Azure DevOps Services](./media/image5-8.png)

**Obrázek 5-8.** Nasazení do clusteru Kubernetes z kanálů CI/CD ve službách Azure DevOps Services

### <a name="benefits"></a>Výhody

Nasazení do clusteru v Kubernetes má mnoho výhod. Největší výhodou je, že získáte prostředí připravené k produkčnímu prostředí, ve kterém můžete škálovat na základě počtu instancí kontejneru, které chcete použít (vnitřní škálovatelnost v existujících uzlech), a na základě počtu uzlů nebo virtuálních počítačů v clusteru (globální škálovatelnost clusteru).

Azure Container Service optimalizuje oblíbené open source nástroje a technologie speciálně pro Azure. Získáte otevřené řešení, které nabízí přenositelnost, a to jak pro vaše kontejnery a pro konfiguraci aplikace. Vyberete velikost, počet hostitelů a orchestrator nástroje kontejnerové služby zpracovává vše ostatní.

S Kubernetes mohou vývojáři postupovat od přemýšlení o fyzických a virtuálních počítačích až po plánování infrastruktury zaměřené na kontejnery, která mimo jiné usnadňuje následující funkce:

- Aplikace založené na více kontejnerech

- Replikace instancí kontejneru a horizontální automatické škálování

- Pojmenování a zjišťování (například interní DNS)

- Vyvažovací zatížení

- Postupné aktualizace

- Distribuce tajných kódů

- Kontroly stavu aplikace

## <a name="next-steps"></a>Další kroky

Prozkoumejte tento obsah podrobněji na wiki GitHubu:<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a>Návod 6: Nasazení aplikací založených na kontejnerech Windows do služby Azure App Service for Containers

### <a name="technical-walkthrough-availability"></a>Dostupnost technického návodu

Úplný technický návod je k dispozici v eShopModernizing GitHub repo wiki:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a>Přehled

Jednoduchou kontejnerizovanou aplikaci pomocí kontejnerů Windows lze snadno nasadit do služby Azure App Service for Containers. Toto je doporučený přístup pro většinu aplikací založených na kontejneru systému Windows.

### <a name="goals"></a>Cíle

Cílem tohoto návodu je zjistit, jak nasadit aplikaci založenou na kontejnerech Windows do služby Azure App Service for Containers z registru (Docker Hub nebo Azure Container Registry).

### <a name="scenario"></a>Scénář

![Nasazení aplikace založené na kontejnerech Windows do služby Azure App Service pro kontejnery](./media/image5-11.png)

### <a name="benefits"></a>Výhody

Nasazení do služby Azure App Service for Containers nabízí výhody kontejnerů spárovaných s výhodami služby PaaS služby Azure App Service. App service lze snadno škálovat vertikálně i horizontálně a lze ji nakonfigurovat tak, aby automaticky škálovala tak, aby splňovala měnící se požadavky. Aktualizace lze provádět s nulovými prostoji a konfigurace průběžného nasazení z registru je také snadno konfigurovat.

## <a name="next-steps"></a>Další kroky

Prozkoumejte tento obsah podrobněji na wiki GitHubu:<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

> [!div class="step-by-step"]
> [Předchozí](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
> [další](conclusions.md) <!-- Next Chapter -->
