---
title: Návody a přehled technických začátků
description: Modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows | Návody a přehled technických informací Začínáme
ms.date: 04/28/2018
ms.openlocfilehash: 81f7d9fbf596a23b83e2dc9251788b33a8817e16
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676883"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a>Návody a přehled technických začátků

Pokud chcete omezit velikost této elektronické knihy, měla by být v úložišti GitHubu dostupná další technická dokumentace a kompletní návody. Online série návodů popsaných v této kapitole obsahuje podrobné nastavení více prostředí, která jsou založená na kontejnerech Windows, a nasazení do Azure.

V následujících částech se dozvíte, co se týká každého návodu, jeho cíle a špičkového výhledu a poskytuje diagram úloh, které jsou součástí. Návody můžete získat sami na wikiwebu úložiště GitHub pro aplikace *eShopModernizing* na adrese <https://github.com/dotnet-architecture/eShopModernizing/wiki>.

## <a name="technical-walkthrough-list"></a>Seznam technických postupů

Následující návody Začínáme poskytují konzistentní a komplexní technické pokyny pro ukázkové aplikace, které můžete nasazovat a Shift pomocí kontejnerů, a pak je přesunout pomocí několika možností nasazení v Azure.

Každý z následujících návodů používá nové ukázkové aplikace eShopLegacy a eShopModernizing, které jsou dostupné na GitHubu na adrese <https://github.com/dotnet-architecture/eShopModernizing>.

- **Prohlídka aplikací eShop Legacy (základní aplikace do modernizovat)**

- **Kontejnerizace své stávající webové aplikace ASP.NET (WebForms & MVC) pomocí kontejnerů Windows**

- **Kontejnerizace své stávající služby WCF (N-vrstvých aplikací) pomocí kontejnerů Windows**

- **Nasazení aplikace založené na kontejnerech Windows do virtuálních počítačů Azure**

- **Nasaďte aplikace založené na kontejnerech Windows do Kubernetes v Azure Container Service**

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a>Návod 1: Prohlídka starších verzí aplikací eShop

### <a name="technical-walkthrough-availability"></a>Dostupnost technického návodu

Úplný technický návod je k dispozici na wikiwebu eShopModernizing GitHub:

[názorné postupy pro eShopModernizing wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a>Přehled

V tomto návodu můžete prozkoumat počáteční implementaci tří ukázkových starších verzí aplikací. První dvě ukázkové webové aplikace mají architekturu monolitické a vytvořily se pomocí klasického ASP.NET. Jedna aplikace je založena na ASP.NET 4. x MVC; Druhá aplikace je založena na webových formulářích ASP.NET 4. x.
Třetí aplikace je 3 vrstva, která se skládá z aplikace typu klient-server a služby [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) na straně serveru.

Všechny tyto aplikace jsou dostupné v [úložišti GitHub eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).

### <a name="goals"></a>Cíle

Hlavním cílem tohoto návodu je jednoduše seznámit se s těmito aplikacemi a s jejich kódem a konfigurací. Aplikace můžete nakonfigurovat tak, aby vygenerovaly a používaly přípravou data bez použití databáze SQL pro účely testování. Tato volitelná konfigurace je založena na injektáže závislosti v odděleném způsobu.

### <a name="scenario-1-aspnet-web-apps"></a>Scénář 1: Webové aplikace v ASP.NET

Následující obrázek ukazuje jednoduchý scénář původní starší verze ASP.NET webových aplikací.

![Scénář jednoduché architektury pro původní starší verze webových aplikací v ASP.NET](./media/image5-1.png)

V perspektivě obchodní domény obě aplikace nabízejí stejné funkce správy katalogu. Členové týmu eShop Enterprise by tuto aplikaci mohli používat k zobrazení a úpravám katalogu produktů.

Následující obrázek ukazuje úvodní snímky obrazovky aplikace.

![Aplikace webových formulářů ASP.NET MVC a ASP.NET (existující/starší technologie)](./media/image5-2.png)

Závislosti v ASP.NET 4. x nebo starších verzích (pro MVC nebo pro webové formuláře) znamenají, že tyto aplikace nebudou běžet v .NET Core, pokud není kód plně přepsaný pomocí ASP.NET Core MVC.

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a>Scénář 2: Klientská aplikace služby WCF a WinForms (aplikace na úrovni 3)

Následující obrázek ukazuje jednoduchý scénář původní starší verze aplikace 3 vrstvy.

![Scénář jednoduché architektury původní starší verze aplikace na 3 vrstvě se službou WCF a klientskou aplikací WinForms](./media/image5-1.5.png)

### <a name="benefits"></a>Výhody

Výhody tohoto návodu jsou jednoduché: Stačí, abyste obeznámeni s kódem a počátečními aplikacemi.

### <a name="next-steps"></a>Další kroky

Podrobnější zkoumání tohoto obsahu najdete na wikiwebu GitHub:

- [Projděte si základní aplikace ASP.NET MVC a webové formuláře "starší".](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [Prohlídku na základní úrovni služby WCF a WinForms (3 vrstvy) "starší" aplikace](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a>Návod 2: Kontejnerizace své stávající aplikace .NET pomocí kontejnerů Windows

### <a name="overview"></a>Přehled

Pomocí kontejnerů Windows můžete zlepšit nasazení stávajících aplikací .NET, jako jsou ty, které jsou založené na MVC, webových formulářích nebo WCF, do produkčních, vývojových a testovacích prostředí.

### <a name="goals"></a>Cíle

Cílem tohoto návodu je zobrazit několik možností pro uzavření existující aplikace .NET Framework. Můžete:

- Kontejnerizace aplikaci pomocí [nástrojů sady Visual studio 2017 pro Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (visual Studio 2017 nebo novější verze).

- Kontejnerizace aplikaci ručním přidáním [souboru Dockerfile](https://docs.docker.com/engine/reference/builder/)a pak pomocí [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).

- Kontejnerizace aplikaci pomocí nástroje [Img2Docker](https://github.com/docker/communitytools-image2docker-win) (Open source nástroj z Docker).

Tento názorný postup se zaměřuje na nástroje sady Visual Studio 2017 pro přístup k Docker, ale ostatní dva přístupy jsou v souvislosti s používáním fázemi poměrně podobné.

### <a name="scenario-1-containerized-aspnet-web-apps"></a>Scénář 1: ASP.NET webové aplikace v kontejneru

Obrázek níže ukazuje scénář pro kontejnerové aplikace eShop starší verze webových aplikací.

![Zjednodušený diagram architektury kontejnerových aplikací ASP.NET ve vývojovém prostředí](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a>Scénář 2: Kontejnerová služba WCF

Obrázek níže ukazuje scénář pro aplikaci se třemi úrovněmi s kontejnerovou službou WCF.

![Zjednodušený diagram architektury kontejnerové služby WCF ve vývojovém prostředí](./media/image5-3.5.png)

### <a name="benefits"></a>Výhody

Existují výhody spuštění aplikace v monolitické v kontejneru. Nejprve vytvoříte obrázek pro aplikaci. Od tohoto okamžiku se každé nasazení spouští ve stejném prostředí. Každý kontejner používá stejnou verzi operačního systému, má nainstalovanou stejnou verzi závislostí, používá stejnou verzi rozhraní .NET Framework a je vytvořen pomocí stejného procesu. V podstatě budete řídit závislosti aplikace pomocí Image Docker. Závislosti při nasazení kontejnerů cestují k aplikaci.

Další výhodou je, že vývojáři můžou aplikaci spouštět v konzistentním prostředí, které poskytuje kontejnery Windows. Problémy, které se objeví jenom s určitými verzemi, můžou být hned Spotted místo zpřístupnění v pracovním nebo produkčním prostředí. Rozdíly ve vývojových prostředích, která používají členové vývojového týmu, se týkají méně, když aplikace běží v kontejnerech.

Kontejnerové aplikace mají také plošší křivku škálování na více instancí. Aplikace s využitím kontejnerů umožňují mít více instancí aplikací a služeb (na základě kontejnerů) ve VIRTUÁLNÍm počítači nebo fyzickém počítači v porovnání s běžnými nasazeními aplikací na počítač. To se týká vyšší hustoty a menšího počtu požadovaných prostředků, zejména při použití orchestrací, jako je Kubernetes.

V ideálních situacích není nutné dělat žádné změny kódu aplikace (C\#). Ve většině scénářů potřebujete jenom soubory metadat nasazení Docker (fázemi a soubory Docker Compose).

### <a name="next-steps"></a>Další postup

Podrobnější zkoumání tohoto obsahu najdete na wikiwebu GitHub:

- [Jak kontejnerizace .NET Framework webové aplikace pomocí kontejnerů Windows a Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [Přidání podpory Docker do služby WCF](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a>Návod 3: Nasazení aplikace založené na kontejnerech Windows do virtuálních počítačů Azure

### <a name="technical-walkthrough-availability"></a>Dostupnost technického návodu

Úplný technický návod je k dispozici na wikiwebu eShopModernizing GitHub:<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

### <a name="overview"></a>Přehled

Nasazení na hostitele Docker na virtuálním počítači s Windows serverem 2016 (VM) v Azure umožňuje rychle nastavit vývojové a testovací a přípravná prostředí. Poskytuje také běžné místo pro testery nebo obchodní uživatele k ověření aplikace. Virtuální počítače můžou být taky platná provozní prostředí infrastruktury jako služby (IaaS).

### <a name="goals"></a>Cíle

Cílem tohoto návodu je ukázat vám několik alternativ, které máte, když nasadíte kontejnery Windows do virtuálních počítačů Azure, které jsou založené na Windows serveru 2016 nebo novějších verzích.

### <a name="scenarios"></a>Scénáře

V tomto návodu se zabývá několik scénářů.

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a>Scénář A: Nasazení na virtuální počítač Azure z vývojového počítače prostřednictvím připojení k Docker Engine

![Nasazení na virtuální počítač Azure z vývojového počítače prostřednictvím připojení k dokovacímu modulu](./media/image5-4.png)

**Obrázek 5-4.** Nasazení na virtuální počítač Azure z vývojového počítače prostřednictvím připojení k dokovacímu modulu

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a>Scénář B: Nasazení na virtuální počítač Azure prostřednictvím registru Docker

![Nasazení na virtuální počítač Azure prostřednictvím registru Docker](./media/image5-5.png)

**Obrázek 5-5.** Nasazení na virtuální počítač Azure prostřednictvím registru Docker

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a>Scénář C: Nasazení na virtuální počítač Azure z kanálů CI/CD v Azure DevOps Services

![Nasazení na virtuální počítač Azure z kanálů CI/CD v Azure DevOps Services](./media/image5-6.png)

**Obrázek 5-6.** Nasazení na virtuální počítač Azure z kanálů CI/CD v Azure DevOps Services

### <a name="azure-vms-for-windows-containers"></a>Virtuální počítače Azure pro kontejnery Windows

Virtuální počítače Azure pro kontejnery Windows jsou virtuální počítače založené na Windows serveru 2016, Windows 10 nebo novějších verzích s nastavením modulu Docker. Ve většině případů se Windows Server 2016 používá ve virtuálních počítačích Azure.

Azure v současné době poskytuje virtuálnímu počítači s názvem **Windows Server 2016 s kontejnery**. Tento virtuální počítač můžete použít k tomu, abyste si vyzkoušeli novou funkci kontejneru Windows serveru, a to buď s Windows serverem Core, nebo Windows nano serverem. Nainstalují se image operačních systémů kontejnerů a pak je virtuální počítač připravený k použití s Docker.

### <a name="benefits"></a>Výhody

I když se kontejnery Windows dají nasadit na místní virtuální počítače s Windows serverem 2016 při nasazení do Azure, získáte snadnější způsob, jak začít s připravenými virtuálními počítači kontejnerů Windows serveru. Získáte také běžné online umístění, které je dostupné pro testery a automatickou škálovatelnost prostřednictvím Azure Virtual Machine Scale Sets.

### <a name="next-steps"></a>Další kroky

Podrobnější zkoumání tohoto obsahu najdete na wikiwebu GitHub:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a>Návod 4: Nasazení aplikací založených na kontejnerech Windows do Azure Container Instances (ACI)

### <a name="technical-walkthrough-availability"></a>Dostupnost technického návodu

Úplný technický návod je k dispozici na wikiwebu eShopModernizing GitHub:

[Nasazení aplikací do ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

### <a name="overview"></a>Přehled

[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) je nejrychlejší způsob, jak mít kontejnery pro vývoj/testování a přípravu, kde můžete nasazovat jednotlivé instance kontejnerů.

### <a name="goals"></a>Cíle

V tomto návodu se dozvíte o hlavních scénářích při nasazování kontejnerů Windows do Azure Container Instances (ACI) a o tom, jak můžete nasadit eShopModernizing aplikace do ACI.

### <a name="scenarios"></a>Scénáře

Existují varianty, jak nasadit aplikace eShopModernizing do ACI, jako je nasazení pouze jedné nebo všech aplikací (aplikace MVC, aplikace WebForm nebo služba WCF). V níže uvedeném scénáři vidíte aplikaci ASP.NET MVC a kontejner SQL Server, jak jsou nasazeny jako kontejnery do ACI (Azure Container Instances).

![Nasazení na ACI z vývojového prostředí](./media/image5-3.5.6.png)

### <a name="benefits"></a>Výhody

Azure Container Instances usnadňuje vytváření a správu kontejnerů Docker v Azure, aniž byste museli zřizovat virtuální počítače nebo přidělovat službu vyšší úrovně. Pomocí ACI můžete přímo nasadit kontejner Windows v Azure a zveřejnit ho na internetu s plně kvalifikovaným názvem domény (FQDN) v řádu sekund (za předpokladu, že máte připravenou image kontejneru Windows v registru Docker, jako je Docker Hub nebo Azure Container. Registr).

### <a name="considerations"></a>Požadavky

Nasazení kontejnerů Windows s úplnými .NET Framework/ASP.NET nebo SQL Server do Azure Container Instances (ACI) není poměrně stejně rychlé jako nasazení na obvyklého hostitele Docker (jako Windows Server 2016 s kontejnery Windows), protože image Docker musí být stažení (z registru Docker) pokaždé a velikosti image kontejneru SQL (15,1 GB) a image kontejneru ASP.NET (13,9 GB) jsou výrazně velké, ale je mnohem levnější než udržování vlastního hostitele Docker (trvale online). Windows Server 2016 s virtuálními počítači kontejnerů Windows v Azure – nezmiňujte si celý Orchestrator jako Kubernetes v Azure (AKS), který je na druhé straně skvělým výběrem pro produkční nasazení.

Hlavním závěrem je použití Azure Container Instances velmi přesvědčivou možností pro scénáře vývoje a testování a pro kanály CI/CD.

## <a name="next-steps"></a>Další postup

Podrobnější zkoumání tohoto obsahu najdete na wikiwebu GitHub:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a>Návod 5: Nasaďte aplikace založené na kontejnerech Windows do Kubernetes v Azure Container Service

### <a name="technical-walkthrough-availability"></a>Dostupnost technického návodu

Úplný technický návod je k dispozici na wikiwebu eShopModernizing GitHub:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a>Přehled

Aplikace, která je založená na kontejnerech Windows, bude rychle potřebovat používání platforem, takže se ještě od virtuálních počítačů s IaaS přesouvá ještě dál. To je nutné, aby bylo možné snadno dosáhnout vysoké škálovatelnosti a lepšího automatizované škálovatelnosti a významně zlepšovat automatizované nasazení a správu verzí. Tyto cíle můžete dosáhnout pomocí nástroje Orchestrator [Kubernetes](https://kubernetes.io/), který je k dispozici ve [službě Azure Container Services](https://azure.microsoft.com/services/container-service/).

### <a name="goals"></a>Cíle

Cílem tohoto návodu je zjistit, jak nasadit aplikaci založenou na kontejnerech Windows do Kubernetes (označované také jako *K8s*) v Azure Container Service. Nasazení na Kubernetes od začátku je proces se dvěma kroky:

1. Nasaďte cluster Kubernetes do Azure Container Service.

2. Nasaďte aplikaci a související prostředky do clusteru Kubernetes.

### <a name="scenarios"></a>Scénáře

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a>Scénář A: Nasazení přímo do clusteru Kubernetes z vývojového prostředí

![Nasazení přímo do clusteru Kubernetes z vývojového prostředí](./media/image5-7.png)

**Obrázek 5-7.** Nasazení přímo do clusteru Kubernetes z vývojového prostředí

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a>Scénář B: Nasazení do clusteru Kubernetes z kanálů CI/CD v Azure DevOps Services

![Nasazení do clusteru Kubernetes z kanálů CI/CD v Azure DevOps Services](./media/image5-8.png)

**Obrázek 5-8.** Nasazení do clusteru Kubernetes z kanálů CI/CD v Azure DevOps Services

### <a name="benefits"></a>Výhody

Nasazení do clusteru v Kubernetes přináší spoustu výhod. Největší výhodou je, že získáte prostředí připravené pro produkční prostředí, ve kterém můžete škálovat aplikaci na základě počtu instancí kontejnerů, které chcete použít (vnitřní škálovatelnost ve stávajících uzlech), a na základě počtu uzlů nebo virtuálních počítačů v clusteru ( globální škálovatelnost clusteru).

Azure Container Service optimalizuje oblíbené open source nástroje a technologie specifické pro Azure. Získáte otevřené řešení, které nabízí přenositelnost, pro vaše kontejnery i pro konfiguraci aplikace. Vyberte velikost, počet hostitelů a služba Orchestrator Tools – Container Service zpracovává všechno ostatní.

Díky Kubernetes můžou vývojáři sledovat fyzické a virtuální počítače a plánovat infrastrukturu zaměřenou na kontejner, která usnadňuje následující možnosti, mimo jiné:

- Aplikace založené na více kontejnerech

- Replikace instancí kontejnerů a horizontálního automatického škálování

- Pojmenování a zjišťování (například interní DNS)

- Vyrovnávání zatížení

- Postupné aktualizace

- Distribuce tajných kódů

- Kontroly stavu aplikace

## <a name="next-steps"></a>Další postup

Podrobnější zkoumání tohoto obsahu najdete na wikiwebu GitHub:<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a>Návod 6: Nasaďte aplikace založené na kontejnerech Windows pro Azure App Service pro kontejnery.

### <a name="technical-walkthrough-availability"></a>Dostupnost technického návodu

Úplný technický návod je k dispozici na wikiwebu eShopModernizing GitHub:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a>Přehled

Jednoduchou kontejnerovou aplikaci pomocí kontejnerů Windows lze snadno nasadit do Azure App Service pro kontejnery. Toto je doporučený postup pro většinu aplikací založených na kontejnerech Windows.

### <a name="goals"></a>Cíle

Cílem tohoto návodu je zjistit, jak nasadit aplikaci založenou na kontejnerech Windows pro Azure App Service pro kontejnery z registru (Docker Hub nebo Azure Container Registry).

### <a name="scenario"></a>Scénář

![Nasazení aplikace založené na kontejnerech Windows pro Azure App Service pro kontejnery](./media/image5-11.png)

### <a name="benefits"></a>Výhody

Nasazení do Azure App Service for Containers nabízí výhody kontejnerů spárovaných s výhodami PaaS Azure App Service. Službu App Service je možné snadno škálovat vertikálně i vodorovně a je možné ji nakonfigurovat na automatické škálování tak, aby splňovala měnící se požadavky. Aktualizace se dají provádět s nulovými výpadky a konfigurace průběžného nasazování z registru se dá snadno nakonfigurovat taky.

## <a name="next-steps"></a>Další kroky

Podrobnější zkoumání tohoto obsahu najdete na wikiwebu GitHub:<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

> [!div class="step-by-step"]
> [Předchozí](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)Další
> [](conclusions.md)
