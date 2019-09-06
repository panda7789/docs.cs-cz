---
title: Orchestrace mikroslužeb a vícekontejnerových aplikací pro vysokou škálovatelnost a dostupnost
description: Reálné provozní aplikace musí být nasazeny a spravovány pomocí orchestrace, které zpracovávají stav, zatížení a životní cyklus všech kontejnerů.
ms.date: 02/15/2019
ms.openlocfilehash: 8c1161127eb6b239384444c369de7f11abd3d424
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373696"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Orchestrace mikroslužeb a vícekontejnerových aplikací pro vysokou škálovatelnost a dostupnost

Použití orchestrací pro aplikace připravené pro produkční prostředí je důležité, pokud je vaše aplikace založená na mikroslužbách nebo rozdělená mezi několik kontejnerů. Jak jsme už dřív představili, v rámci přístupu na základě mikroslužeb každá mikroslužba vlastní svůj model a data tak, že bude autonomní z pohledu vývoje a nasazení. I když máte obecnější aplikaci, která se skládá z několika služeb (například SOA), budete mít také více kontejnerů nebo služeb tvořících jednu obchodní aplikaci, která musí být nasazena jako distribuovaný systém. Tyto druhy systémů jsou složité pro horizontální navýšení kapacity a správu. Proto budete potřebovat Orchestrator, pokud chcete mít aplikaci s více kontejnery připravenou pro produkční prostředí a škálovatelnost.

Obrázek 4-6 znázorňuje nasazení do clusteru aplikace tvořené několika mikroslužbami (kontejnery).

![Složené aplikace Docker v clusteru: Pro každou instanci služby použijete jeden kontejner. Kontejnery Docker jsou "jednotky nasazení" a kontejner je instance Docker. hostitel zpracovává spoustu kontejnerů.](./media/image6.png)

**Obrázek 4-6**. Cluster kontejnerů

Vypadá to, že se jedná o logický přístup. Ale jak zpracováváte vyrovnávání zatížení, směrování a orchestraci těchto složených aplikací?

Rozhraní příkazového řádku Docker (CLI) splňuje požadavky na správu jednoho kontejneru na jednom hostiteli, ale v případě, že se jedná o správu více kontejnerů nasazených na více hostitelích pro složitější distribuované aplikace, dojde k jejich krátkému. Ve většině případů potřebujete platformu pro správu, která bude automaticky spouštět kontejnery, škálovat kontejnery s více instancemi na jeden obrázek, pozastavit je nebo je v případě potřeby vypne, a v ideálním případě také řídit, jak přistupují k prostředkům, jako jsou síť a data. pamì.

Aby bylo možné nad rámec správy jednotlivých kontejnerů nebo jednoduchých složených aplikací a přecházet k většímu počtu podnikových aplikací pomocí mikroslužeb, je nutné přepínat na orchestraci a clusteringu platforem.

Pokud vytváříte rozsáhlé, podnikové a vývojové aplikace založené na architektuře a vývojovém bodu, je důležité pochopit následující platformy a produkty, které podporují pokročilé scénáře:

- **Clustery a orchestrace.** Pokud potřebujete škálovat aplikace v mnoha hostitelích Docker, jako je například s rozsáhlou aplikací založenou na mikroslužbách, je důležité, aby bylo možné spravovat všechny tyto hostitele jako jediný cluster abstrakcí složitosti základní platformy. To je to, co poskytují clustery kontejnerů a orchestrace. Příklady orchestrace jsou Azure Service Fabric a Kubernetes. Kubernetes je k dispozici v Azure prostřednictvím služby Azure Kubernetes.

- **Plánovače.** *Plánování* znamená, že má správce možnost spouštět kontejnery v clusteru, takže plánovače také poskytují uživatelské rozhraní pro to. Plánovač clusteru má několik odpovědností: k efektivnímu využití prostředků clusteru, k nastavení omezení poskytovaných uživatelem, k efektivnímu vyrovnávání zatížení kontejnerů napříč uzly nebo hostiteli a k zajištění odolnosti proti chybám při vysokém dosahu dostupnosti.

Koncepty clusteru a plánovače úzce souvisejí, takže produkty poskytované různými dodavateli často poskytují obě sady funkcí. V následující části jsou uvedeny nejdůležitější možnosti platformy a softwaru pro clustery a plánovače. Tyto orchestrace se široce nabízejí ve veřejných cloudech, jako je Azure.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Softwarové platformy pro clusteringu kontejnerů, Orchestrace a plánování

| Platforma | Komentáře |
|:---:|:---|
| **Kubernetes** <br/> ![Logo Kubernetes](./media/kubernetes-logo.png) | [*Kubernetes*](https://kubernetes.io/) je open source produkt, který poskytuje funkce, které jsou v rozsahu od infrastruktury clusteru a plánování kontejneru až po orchestraci možností. Umožňuje automatizovat nasazení, škálování a provoz kontejnerů aplikací napříč clustery hostitelů. <br/> <br/> *Kubernetes* poskytuje infrastrukturu zaměřenou na kontejner, která seskupuje kontejnery aplikací do logických jednotek pro jednoduchou správu a zjišťování. <br/> <br/> *Kubernetes* je vyspělá v systému Linux a méně vyspělá ve Windows. |
| **Azure Kubernetes Service (AKS)** <br/> ![Logo služby Azure Kubernetes](./media/aks-logo.png) | [Služba Azure Kubernetes Service (AKS)](https://azure.microsoft.com/services/kubernetes-service/) je spravovaná služba orchestrace kontejnerů Kubernetes v Azure, která zjednodušuje správu, nasazení a provoz clusteru Kubernetes. |
| **Service Fabric Azure** <br/> ![Logo pro Azure Service Fabric](./media/service-fabric-logo.png) | [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) je platforma mikroslužeb Microsoft pro vytváření aplikací. Jedná se o nástroj [Orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) pro služby a vytváří clustery počítačů. Service Fabric můžou nasazovat služby jako kontejnery nebo jako jednoduché procesy. Může dokonce kombinovat služby v procesech se službami v kontejnerech v rámci stejné aplikace a clusteru. <br/> <br/> Clustery *Service Fabric* můžete nasadit v Azure, v místním prostředí nebo v jakémkoli cloudu. Nasazení v Azure se ale zjednodušuje pomocí spravovaného přístupu. <br/> <br/> *Service Fabric* poskytuje další a volitelné [Service Fabric programovací modely](https://azure.microsoft.com/documentation/articles/service-fabric-choose-framework/) , jako jsou [stavové služby](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-services-introduction/) a [Reliable Actors](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-actors-introduction/). <br/> <br/> *Service Fabric* je vyspělá ve Windows (počet roků, ve kterých se vyvíjí Windows), méně vyspělé v systému Linux. <br/> <br/> V Service Fabric jsou podporovány kontejnery Linux i Windows od 2017. |
| **Síť Azure Service Fabric** <br/> ![Logo sítě Azure Service Fabric](./media/azure-service-fabric-mesh-logo.png) | [*Síť Azure Service Fabric*](https://docs.microsoft.com/azure/service-fabric-mesh/service-fabric-mesh-overview) nabízí stejnou spolehlivost a škálovatelný výkon a škálování jako Service Fabric, ale nabízí také plně spravovanou platformu bez serveru. Nemusíte spravovat cluster, virtuální počítače, úložiště ani konfiguraci sítě. Jenom se zaměřte na vývoj vaší aplikace. <br/> <br/> *Service Fabricová síť* podporuje kontejnery Windows i Linux, což vám umožní vyvíjet s libovolným programovacím jazykem a architekturou, kterou si vyberete.

## <a name="using-container-based-orchestrators-in-azure"></a>Použití orchestrací založených na kontejnerech v Azure

Několik dodavatelů cloudu nabízí podporu kontejnerů Docker a clustery Docker a podporu orchestrace, včetně služeb Azure, Amazon EC2 Container Service a Google Container Engine. Azure poskytuje cluster Docker a podporu nástroje Orchestrator prostřednictvím služby Azure Kubernetes Service (AKS), Azure Service Fabric a Azure Service Fabric sítě.

## <a name="using-azure-kubernetes-service"></a>Pomocí služby Azure Kubernetes

Cluster Kubernetes obsahuje několik hostitelů Docker a zpřístupňuje je jako jeden virtuální hostitel Docker, takže můžete nasadit více kontejnerů do clusteru a škálovat je s libovolným počtem instancí kontejnerů. Cluster bude zpracovávat všechny komplexní instalace správy, jako je škálovatelnost, stav a tak dále.

AKS poskytuje způsob, jak zjednodušit vytváření, konfiguraci a správu clusteru virtuálních počítačů v Azure, které jsou předem nakonfigurované tak, aby se spouštěly aplikace s využitím kontejnerů. Díky optimalizované konfiguraci oblíbených open source nástrojů pro plánování a orchestraci vám AKS umožňuje využívat stávající dovednosti nebo nakládat na velký a rostoucí tělo odborného posudku komunity k nasazení a správě kontejnerových aplikací na Microsoft Azure .

Služba Azure Kubernetes optimalizuje konfiguraci oblíbených nástrojů a technologií open-source pro clustery Docker, konkrétně pro Azure. Získáte otevřené řešení, které nabízí přenositelnost pro vaše kontejnery i konfiguraci vaší aplikace. Vyberte velikost, počet hostitelů a nástroje Orchestrator a AKS zpracuje všechno ostatní.

![Struktura clusteru Kubernetes: Existuje jeden hlavní uzel, který zpracovává služby DNS, Scheduler, proxy atd. a několik pracovních uzlů, které hostují kontejnery.](media/image36.png)

**Obrázek 4-7**. Zjednodušená struktura a topologie clusteru Kubernetes

Obrázek 4-7 ukazuje strukturu clusteru Kubernetes, kde hlavní uzel (VM) ovládá většinu koordinace clusteru, a můžete nasazovat kontejnery do zbývajících uzlů, které jsou spravovány jako jeden fond, z aplikačního bodu zobrazení. To vám umožní škálovat na tisíce nebo dokonce i desítky tisíců kontejnerů.

## <a name="development-environment-for-kubernetes"></a>Vývojové prostředí pro Kubernetes

Ve vývojovém prostředí, které [Docker oznámilo v červenci 2018](https://blog.docker.com/2018/07/kubernetes-is-now-available-in-docker-desktop-stable-channel/), se Kubernetes dá spustit taky na jednom vývojovém počítači (Windows 10 nebo MacOS). stačí jenom nainstalovat [Docker Desktop](https://www.docker.com/community-edition). Později můžete nasadit do cloudu (AKS) pro další testy integrace, jak je znázorněno na obrázku 4-8.

![Docker oznámil podporu vývojových počítačů pro clustery Kubernetes v červenci 2018 s Docker desktopem.](media/kubernetes-development-environment.png)

**Obrázek 4-8**. Spuštění Kubernetes ve vývojovém počítači a v cloudu

## <a name="get-started-with-azure-kubernetes-service-aks"></a>Začínáme se službou Azure Kubernetes (AKS)

Chcete-li začít používat AKS, nasaďte cluster AKS z Azure Portal nebo pomocí rozhraní příkazového řádku. Další informace o nasazení clusteru Kubernetes do Azure najdete v tématu [nasazení clusteru Azure Kubernetes Service (AKS)](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal).

Neexistují žádné poplatky za žádný software nainstalovaný ve výchozím nastavení jako součást AKS. Všechny výchozí možnosti jsou implementované pomocí Open source softwaru. AKS je k dispozici pro více virtuálních počítačů v Azure. Účtují se vám jenom výpočetní instance, které zvolíte, a také ostatní základní prostředky infrastruktury spotřebované jako úložiště a sítě. Za AKS se neúčtují žádné dodatečné poplatky.

Další informace o implementaci nasazení do Kubernetes na základě `kubectl` a originálních `.yaml` souborů najdete v příspěvku k [Nastavení eShopOnContainers v AKS (služba Azure Kubernetes)](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.-Setting-the-solution-up-in-AKS-(Azure-Kubernetes-Service)).

## <a name="deploy-with-helm-charts-into-kubernetes-clusters"></a>Nasazení s Helm grafy do clusterů Kubernetes

Při nasazování aplikace do clusteru Kubernetes můžete použít původní `kubectl.exe` nástroj CLI pomocí souborů nasazení na základě nativního formátu (`.yaml` soubory), jak je uvedeno v předchozí části. U složitějších aplikací Kubernetes, jako je například při nasazení složitých aplikací založených na mikroslužbách, se doporučuje použít [Helm](https://helm.sh/).

Grafy Helm vám pomůžou definovat, verze, nainstalovat, sdílet, upgradovat nebo vrátit zpět i nejsložitější aplikaci Kubernetes.

Dál se doporučuje používat Helm použití, protože další prostředí Kubernetes v Azure, jako je například [Azure dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) , jsou také založená na Helm grafech.

Helm je udržována v [cloudu CNCF (Cloud Native Computing Foundation)](https://www.cncf.io/) ve spolupráci s Microsoftem, Google, Bitnami a komunitou přispěvatelů Helm.

Další informace o implementaci Helm grafů a Kubernetes najdete v příspěvku [použití Helm grafů k nasazení eShopOnContainers na AKS](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.1-Deploying-to-AKS-using-Helm-Charts).

## <a name="use-azure-dev-spaces-for-you-kubernetes-application-lifecycle"></a>Použití Azure Dev Spaces pro Kubernetes životního cyklu aplikace

[Azure dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) poskytuje rychlé a iterativní vývojové prostředí Kubernetes pro týmy. S minimálním nastavením pro vývoj počítačů můžete iterativní spouštění a ladění kontejnerů přímo ve službě Azure Kubernetes Service (AKS). Můžete vyvíjet v systému Windows, Mac nebo Linux pomocí známých nástrojů, jako je Visual Studio, Visual Studio Code nebo příkazového řádku.

Jak bylo zmíněno, Azure Dev Spaces používá při nasazování aplikací založených na kontejnerech Helm grafy.

Azure Dev Spaces pomáhá vývojovým týmům zvýšit produktivitu na Kubernetes, protože umožňuje rychle iterovat a ladit kód přímo v globálním clusteru Kubernetes v Azure jenom pomocí sady Visual Studio 2017 nebo Visual Studio Code. Tento cluster Kubernetes v Azure je sdílený spravovaný cluster Kubernetes, takže váš tým může spolupracovat společně. Můžete vyvíjet kód v izolovaném prostředí a pak ho nasadit do globálního clusteru a provést komplexní testování s ostatními komponentami bez replikace nebo napodobování závislostí.

Jak je znázorněno na obrázku 4-9, nejblížecí funkce v Azure Dev Spaces je schopnost vytvořit "prostory", které mohou být spuštěny integrovány do zbytku globálního nasazení v clusteru.

![Azure Dev Spaces může transparentně kombinovat a párovat provozní mikroslužby s vývojovou instancí kontejneru, aby se usnadnilo testování nových verzí.](media/image38.png)

**Obrázek 4-9**. Použití více mezer v Azure Dev Spaces

V podstatě můžete nastavit sdílený prostor pro vývoj v Azure. Každý vývojář se může zaměřit jenom na jejich část aplikace a může iterativním způsobem vypracovávat "předem potvrzené" kód ve vývojovém prostoru, který už obsahuje všechny ostatní služby a cloudové prostředky, na kterých jsou závislé jejich scénáře. Závislosti jsou vždycky aktuální a vývojáři pracují způsobem, který zrcadlí produkci.

Azure Dev Spaces poskytuje koncept prostoru, který vám umožní pracovat na izolaci a bez obav, že členové týmu mají porušení. Tato funkce je založena na předponách adres URL; Pokud v adrese URL požadavku kontejneru použijete předponu prostoru pro vývoj, Azure Dev Spaces spustí speciální verzi kontejneru, kterou pro toto místo nasadil (pokud existuje). V opačném případě spustí globální/konsolidovanou verzi.

Na [stránce wiki na Azure dev Spaces](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.2-Using-Azure-Dev-Spaces-and-AKS) se můžete podívat, jak získat praktické zobrazení na konkrétní příklad.

Další informace najdete v článku věnovaném [vývoji týmu pomocí Azure dev Spaces](https://docs.microsoft.com/azure/dev-spaces/team-development-netcore).

## <a name="additional-resources"></a>Další zdroje

- **Začínáme se službou Azure Kubernetes (AKS)**  \
  <https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal>

- **Azure Dev Spaces** \
  <https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces>

- **Kubernetes.** Oficiální lokalita. \
  <https://kubernetes.io/>

## <a name="using-azure-service-fabric"></a>Použití platformy Azure Service Fabric

Služba Azure Service Fabric z poskytování "krabicových" produktů od Microsoftu, které se obvykle monolitické ve stylu, pro poskytování služeb. Prostředí, ve kterém se nastavují a provozují velké služby ve velkém měřítku, jako je Azure SQL Database, Azure Cosmos DB, Azure Service Bus nebo Cortana, Service Fabric. Platforma se v průběhu času vyvinula s tím, jak ji přijala víc služeb. Důležité je, Service Fabric museli běžet nejen v Azure, ale také v samostatných nasazeních Windows serveru.

Cílem Service Fabric je vyřešit závažné problémy s vytvářením a provozem služby a efektivně využívat prostředky infrastruktury, aby týmy mohly řešit obchodní problémy pomocí přístupu k mikroslužbám.

Service Fabric poskytují dvě hlavní oblasti, které vám pomůžou při sestavování aplikací využívajících přístup k mikroslužbám:

- Platforma, která poskytuje systémové služby pro nasazení, škálování, upgrade, detekci a restartování neúspěšných služeb, zjištění umístění služby, Správa stavu a monitorování stavu. Tyto systémové služby jsou v platnosti a umožňují řadu výše popsaných mikroslužeb.

- Rozhraní API pro programování nebo architektury, které vám pomůžou sestavovat aplikace jako mikroslužby: [spolehlivé aktéry a spolehlivé služby](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Můžete zvolit libovolný kód pro sestavení mikroslužby, ale tato rozhraní API usnadňují práci a integraci s platformou na hlubší úrovni. Tímto způsobem můžete získat informace o stavu a diagnostice nebo můžete využít spolehlivé správy stavů.

Service Fabric nezávislá s ohledem na způsob sestavování služby a můžete použít libovolnou technologii. Poskytuje ale Vestavěná rozhraní API pro programování, která usnadňují vytváření mikroslužeb.

Jak je znázorněno na obrázku 4-10, můžete vytvořit a spustit mikroslužby v Service Fabric buď jako jednoduché procesy, nebo jako kontejnery Docker. Je také možné kombinovat mikroslužby založené na kontejnerech s mikroslužbami založenými na procesech v rámci stejného Service Fabric clusteru.

![Porovnání clusterů Azure Service Fabric: Mikroslužby jako procesy, ve kterých každý uzel spouští jeden proces pro každou mikroslužbu; Mikroslužby jako kontejnery, ve kterých každý uzel spouští Docker s několika kontejnery, jeden kontejner na mikroslužbu.](./media/azure-service-fabric-cluster-types.png)

**Obrázek 4-10**. Nasazení mikroslužeb jako procesů nebo jako kontejnerů v Azure Service Fabric

Service Fabric clusterů založených na hostitelích se systémy Linux a Windows může spouštět kontejnery Docker Linux a kontejnery Windows v uvedeném pořadí.

Aktuální informace o podpoře kontejnerů v Azure Service Fabric najdete v tématu [Service Fabric a kontejnery](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Service Fabric je dobrým příkladem platformy, kde můžete definovat jinou logickou architekturu (obchodní mikroslužby nebo ohraničené kontexty), než je fyzická implementace. Pokud například implementujete [stavovou Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) ve [službě Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), která je představena v následující části "[bezstavově oproti stavovým mikroslužbám](#stateless-versus-stateful-microservices)", máte koncept obchodních mikroslužeb s více fyzické služby.

Jak je znázorněno na obrázku 4-10 a při implementaci spolehlivé stavové služby Service Fabric, je obvykle potřeba implementovat dvě úrovně služeb. První je back-end spolehlivá stavová služba, která zpracovává více oddílů (každý oddíl je stavová služba). Druhá je front-end služba nebo služba brány, která se účtuje podle směrování a agregace dat napříč více oddíly nebo instancemi stavových služeb. Tato služba brány také zpracovává komunikaci na straně klienta s opakovanými smyčkami, které přistupují k back-endové službě. Je označována jako služba brány, Pokud implementujete vlastní službu, nebo můžete také použít okamžitý Service Fabric [reverzní proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy).

![Service Fabric má předepsáno pro podporu několika stavových spolehlivých služeb v kontejnerech.](./media/service-fabric-stateful-business-microservice.png)

**Obrázek 4-11**. Obchodní mikroslužba s několika instancemi stavových služeb a front-endu vlastní brány

Pokud používáte Service Fabric stavových Reliable Services, budete mít v každém případě také logickou nebo obchodní mikroslužbu (ohraničený kontext), která se skládá z několika fyzických služeb. Každé z nich může být služba brány a služba oddílů implementována jako ASP.NET webové služby API, jak je znázorněno na obrázku 4-11.

V Service Fabric můžete seskupit a nasadit skupiny služeb jako [Service Fabric aplikace](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), což je jednotka balení a nasazení pro produkt Orchestrator nebo cluster. Proto může být aplikace Service Fabric namapována na tuto autonomní firmu i na hranici logické mikroslužeb nebo na ohraničený kontext, takže je možné tyto služby nasadit na autonomní úrovni.

### <a name="service-fabric-and-containers"></a>Service Fabric a kontejnery

S ohledem na kontejnery v Service Fabric můžete také nasadit služby v imagí kontejneru v rámci Service Fabricho clusteru. Jak je znázorněno na obrázku 4-12, bude většina času obsahovat pouze jeden kontejner na službu.

![Service Fabric aplikace může spustit několik kontejnerů, které přistupují k externí databázi, a celá sada bude logickou hranicí obchodní mikroslužby.](./media/azure-service-fabric-business-microservice.png)

**Obrázek 4-12**. Obchodní mikroslužba s několika službami (kontejnery) v Service Fabric

Nicméně označované jako "postranní kontejner" (dva kontejnery, které musí být nasazeny společně jako součást logické služby), jsou také možné v Service Fabric. Důležité je, že obchodní mikroslužba je logické hranice kolem několika soudržných elementů. V mnoha případech se může jednat o jedinou službu s jedním datovým modelem, ale v některých dalších případech můžete mít také několik fyzických služeb.

Všimněte si, že můžete kombinovat služby v procesech a službách v kontejnerech ve stejné Service Fabric aplikaci, jak je znázorněno na obrázku 4-13.

![Aplikace Service Fabric, na které běží jak služby, tak kontejnery ve stejném uzlu.](./media/business-microservice-mapped-to-service-fabric-application.png)

**Obrázek 4-13**. Obchodní mikroslužba mapovaná k Service Fabric aplikaci pomocí kontejnerů a stavových služeb

Další informace o podpoře kontejnerů v Azure Service Fabric najdete v tématu [Service Fabric a kontejnery](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Bezstavové a stavové mikroslužby

Jak bylo zmíněno dříve, každá mikroslužba (logický ohraničený kontext) musí vlastnit svůj doménový model (data a logiku). V případě bezstavových mikroslužeb budou databáze externí, budou využívat relační možnosti, jako je SQL Server, nebo NoSQL možnosti, jako je Azure Cosmos DB nebo MongoDB.

Ale samotné služby můžou být taky Service Fabric stavem, což znamená, že se data nacházejí v rámci mikroslužby. Tato data mohou existovat nejen na stejném serveru, ale v rámci procesu mikroslužeb, v paměti a trvalá na pevných discích a replikovaná do jiných uzlů. Obrázek 4-14 ukazuje různé přístupy.

![V případě bezstavových služeb je stav (trvalost, databáze) z mikroslužby uložený. Stav stavových služeb je v rámci mikroslužeb uchováván.](./media/stateless-vs-stateful-microservices.png)

**Obrázek 4-14**. Bezstavové a stavové mikroslužby

Bezstavový přístup je naprosto platný a je snazší ho implementovat než stavové mikroslužby, protože tento přístup je podobný tradičním a dobře známým vzorům. Bezstavové mikroslužby ale neumožňují latenci mezi procesem a zdroji dat. Zahrnují také další přesuny, když se snažíte zvýšit výkon pomocí další mezipaměti a front. Výsledkem je, že můžete končit komplexními architekturami, které mají příliš mnoho úrovní.

Naproti tomu [stavové mikroslužby](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) můžou Excel v pokročilých scénářích, protože mezi doménovou logikou a daty není latence. Náročné zpracování dat, hraní back-endu, databází jako služby a dalších scénářů s nízkou latencí, se všemi výhodami stavových služeb, které umožňují místní stav pro rychlejší přístup.

Bezstavové a stavové služby se doplňují. Například, jak vidíte v pravém diagramu na obrázku 4-14, může být stavová služba rozdělená na více oddílů. Pro přístup k těmto oddílům budete možná potřebovat bezstavovou službu fungující jako služba brány, která ví, jak každý oddíl řešit na základě klíčů oddílů.

Stavové služby mají nevýhodné. Poskytují vysokou úroveň složitosti pro horizontální navýšení kapacity. Funkce, které by byly obvykle implementovány pomocí externích databázových systémů, musí být řešeny pro úlohy, jako je například replikace dat napříč stavové mikroslužby a dělení dat. Toto je ale jedna z oblastí, kde může nástroj Orchestrator, jako je [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) s jeho [stavovou službou Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) , co nejsnáze usnadnit vývoj a životní cyklus stavových mikroslužeb pomocí [rozhraní API Reliable Services ](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections)a [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Další architektury mikroslužeb, které umožňují stavové služby, které podporují vzor objektu actor a zlepšují odolnost proti chybám a latenci mezi obchodní logikou a daty, jsou Microsoft [Orleans](https://github.com/dotnet/orleans), Microsoft Research a [Akka.NET](https://getakka.net/). Obě architektury aktuálně zlepšují podporu Docker.

Mějte na paměti, že kontejnery Docker jsou bezstavové. Pokud chcete implementovat stavovou službu, budete potřebovat jedno z dalších rozhraní, která jsou popsána v předchozí části a na vyšší úrovni.

## <a name="using-azure-service-fabric-mesh"></a>Používání sítě Azure Service Fabric

Síť Azure Service Fabric je plně spravovaná služba, která vývojářům umožňuje vytvářet a nasazovat klíčové aplikace bez nutnosti spravovat infrastrukturu. Pomocí Service Fabric sítě můžete sestavovat a spouštět zabezpečené distribuované aplikace mikroslužeb, které se škálují na vyžádání.

Jak je znázorněno na obrázku 4-15, aplikace hostované na Service Fabric se spouští a škálovat, aniž byste se museli starat o infrastrukturu.

![Aplikace s více kontejnery běžící v docked desktopu se dá nasadit do Azure Service Fabric sítě, aniž byste se museli starat o infrastrukturu.](media/image39.png)

**Obrázek 4-15**. Nasazení aplikace mikroslužeb/kontejnerů do Service Fabric sítě

V rámci pokrývání Service Fabric sítě se skládají z clusterů tisíc počítačů. Všechny operace clusteru jsou od vývojáře skryté. Stačí nahrát kontejnery a zadat potřebné prostředky, požadavky na dostupnost a omezení prostředků. Service Fabric mřížka automaticky přiděluje infrastrukturu požadovanou nasazením aplikace a také zpracovává selhání infrastruktury a zajišťuje vysokou dostupnost aplikací. Musíte se jenom starat o stav a rychlost odezvy vaší aplikace, ne na infrastrukturu.

Další informace najdete v dokumentaci k síti [Service Fabric](https://docs.microsoft.com/azure/service-fabric-mesh/).

## <a name="choosing-orchestrators-in-azure"></a>Volba orchestrací v Azure

Následující tabulka uvádí informace o tom, co nástroj Orchestrator použije v závislosti na úlohách a zaměření na operační systém.

![Služby Azure Kubernetes jsou vyspělé v systému Linux než ve Windows a většinou se používají pro nasazení mikroslužeb založených na kontejnerech. Azure Service Fabric (cluster i síť) jsou ve Windows vyspělější než v systému Linux, které se běžně používají pro mikroslužby založené na kontejnerech a mikroslužbách na bázi jednoduchých procesů a stavových služeb.](media/image40.png)

**Obrázek 4-16**. Výběr produktu Orchestrator v doprovodnéch materiálech Azure

>[!div class="step-by-step"]
>[Předchozí](soa-applications.md)Další
>[](deploy-azure-kubernetes-service.md)
