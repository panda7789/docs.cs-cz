---
title: Orchestrace mikroslužeb a vícekontejnerových aplikací pro vysokou škálovatelnost a dostupnost
description: Skutečné produkční aplikace musí být nasazeny a spravovány pomocí orchestrátorů, které zpracovávají zdravotní, pracovní zátěž a životní cykly všech kontejnerů.
ms.date: 02/15/2019
ms.openlocfilehash: 369971455168026d768220dae6e2da5ce92bc698
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988996"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Orchestrace mikroslužeb a vícekontejnerových aplikací pro vysokou škálovatelnost a dostupnost

Použití orchestrators pro produkční aplikace je nezbytné, pokud vaše aplikace je založena na mikroslužeb nebo rozdělit mezi více kontejnerů. Jak bylo zavedeno dříve, v přístupu založeném na mikroslužbách, každá mikroslužba vlastní svůj model a data tak, aby byla autonomní z hlediska vývoje a nasazení. Ale i v případě, že máte více tradiční aplikace, která se skládá z více služeb (jako SOA), budete mít také více kontejnerů nebo služeb, které obsahují jednu obchodní aplikaci, které je třeba nasadit jako distribuovaný systém. Tyto typy systémů jsou složité pro horizontální navýšení kapacity a správu; proto je naprosto nutné orchestrator, pokud chcete mít produkční připravené a škálovatelné vícekontejnerové aplikace.

Obrázek 4-6 znázorňuje nasazení do clusteru aplikace složené z více mikroslužeb (kontejnerů).

![Diagram znázorňující složené aplikace Dockeru v clusteru.](./media/orchestrate-high-scalability-availability/composed-docker-applications-cluster.png)

**Obrázek 4-6**. Shluk kontejnerů

Vypadá to jako logický přístup. Ale jak zvládáte vyrovnávání zatížení, směrování a orchestrace těchto složených aplikací?

Cli Dockeru splňuje potřeby správy jednoho kontejneru na jednom hostiteli, ale nedosahuje, pokud jde o správu více kontejnerů nasazených na více hostitelích pro složitější distribuované aplikace. Ve většině případů potřebujete platformu pro správu, která automaticky spustí kontejnery, horizontální navýšení kapacity kontejnerů s více instancemi na bitovou kopii, pozastaví je nebo je v případě potřeby vypne a v ideálním případě také řídí, jak přistupují k prostředkům, jako je síť a úložiště dat.

Chcete-li jít nad rámec správy jednotlivých kontejnerů nebo jednoduché složené aplikace a přejít k větší podnikové aplikace s mikroslužeb, musíte se obrátit na orchestraci a clustering platformy.

Z hlediska architektury a vývoje, pokud vytváříte velké, podnikové, založené na mikroslužbách, aplikace, je důležité porozumět následujícím platformám a produktům, které podporují pokročilé scénáře:

- **Klastry a orchestrátory.** Když potřebujete škálovat aplikace napříč mnoha hostiteli Dockeru, například s velkou aplikací založenou na mikroslužbách, je důležité, abyste mohli spravovat všechny tyto hostitele jako jeden cluster abstrahováním složitosti základní platformy. To je to, co poskytují clustery kontejnerů a orchestrátory. Příklady orchestrátorů jsou Azure Service Fabric a Kubernetes. Kubernetes je dostupný v Azure prostřednictvím služby Azure Kubernetes Service.

- **Plánovače.** *Plánování* znamená mít možnost správce spouštět kontejnery v clusteru, takže plánovači k tomu také poskytují uživatelské rozhraní. Plánovač clusteru má několik odpovědností: efektivně používat prostředky clusteru, nastavit omezení poskytovaná uživatelem, efektivně načíst kontejnery pro vyrovnávání zatížení mezi uzly nebo hostiteli a být robustní proti chybám při poskytování vysoké dostupnosti.

Koncepty clusteru a plánovače úzce souvisejí, takže produkty poskytované různými dodavateli často poskytují obě sady možností. V následující části jsou uvedeny nejdůležitější možnosti platformy a softwaru, které máte pro clustery a plánovače. Tyto orchestrátory jsou široce nabízeny ve veřejných cloudech, jako je Azure.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Softwarové platformy pro shlukování, orchestraci a plánování kontejnerů

| Platforma | Komentáře |
|:---:|:---|
| **Kubernetes** <br/> ![Obrázek loga Kubernetes.](./media/orchestrate-high-scalability-availability/kubernetes-container-orchestration-system-logo.png) | [*Kubernetes*](https://kubernetes.io/) je open source produkt, který poskytuje funkce, které sahají od infrastruktury clusteru a plánování kontejnerů až po možnosti orchestrace. Umožňuje automatizovat nasazení, škálování a operace kontejnerů aplikací napříč clustery hostitelů. <br/> <br/> *Kubernetes* poskytuje infrastrukturu zaměřenou na kontejnery, která seskupuje kontejnery aplikací do logických jednotek pro snadnou správu a zjišťování. <br/> <br/> *Kubernetes* je zralý v Linuxu, méně zralý ve Windows. |
| **Azure Kubernetes Service (AKS)** <br/> ![Obrázek loga služby Azure Kubernetes.](./media/orchestrate-high-scalability-availability/azure-kubernetes-service-logo.png) | [Azure Kubernetes Service (AKS)](https://azure.microsoft.com/services/kubernetes-service/) je spravovaná služba orchestrace kontejnerů Kubernetes v Azure, která zjednodušuje správu, nasazení a operace clusteru Kubernetes. |
| **Azure Service Fabric** <br/> ![Obrázek loga Azure Service Fabric.](./media/orchestrate-high-scalability-availability/azure-service-fabric-logo.png) | [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) je platforma mikroslužeb společnosti Microsoft pro vytváření aplikací. Je to [orchestrátor](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) služeb a vytváří shluky strojů. Service Fabric můžete nasadit služby jako kontejnery nebo jako prosté procesy. Může dokonce kombinovat služby v procesech se službami v kontejnerech v rámci stejné aplikace a clusteru. <br/> <br/> *Clustery Service Fabric* se můžou nasadit v Azure, místně nebo v jakémkoli cloudu. Nasazení v Azure je však zjednodušené pomocí spravovaného přístupu. <br/> <br/> *Service Fabric* poskytuje další a volitelné normativní [service fabric programovací modely,](https://azure.microsoft.com/documentation/articles/service-fabric-choose-framework/) jako [jsou stavové služby](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-services-introduction/) a [spolehlivé objekty actor](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-actors-introduction/). <br/> <br/> *Service Fabric* je zralý v systému Windows (roky vyvíjející se v systému Windows), méně zralé v Linuxu. <br/> <br/> Oba Linux a Windows kontejnery jsou podporovány v Service Fabric od 2017. |
| **Síť prostředků infrastruktury služby Azure** <br/> ![Obrázek loga Azure Service Fabric Mesh.](./media/orchestrate-high-scalability-availability/azure-service-fabric-mesh-logo.png) | [*Azure Service Fabric Mesh*](https://docs.microsoft.com/azure/service-fabric-mesh/service-fabric-mesh-overview) nabízí stejnou spolehlivost, kritický výkon a škálování jako Service Fabric, ale také nabízí plně spravovanou platformu bez serveru. Nemusíte spravovat konfiguraci clusteru, virtuálních počítačů, úložiště nebo sítě. Stačí se soustředit na vývoj vaší aplikace. <br/> <br/> *Service Fabric Mesh* podporuje kontejnery se systémem Windows i Linux, což vám umožní vyvíjet se s libovolným programovacím jazykem a rámcem podle vašeho výběru.

## <a name="using-container-based-orchestrators-in-azure"></a>Použití orchestrátorů založených na kontejnerech v Azure

Několik dodavatelů cloudu nabízí podporu kontejnerů Dockeru a clustery Dockeru a podporu orchestrace, včetně Azure, Amazon EC2 Container Service a Google Container Engine. Azure poskytuje podporu clusteru dockeru a orchestrátoru prostřednictvím služby Azure Kubernetes Service (AKS), Azure Service Fabric a Azure Service Fabric Mesh.

## <a name="using-azure-kubernetes-service"></a>Používání služby Azure Kubernetes

Cluster Kubernetes sdružuje několik hostitelů Dockeru a zveřejňuje je jako jednoho virtuálního hostitele Dockeru, takže do clusteru můžete nasadit více kontejnerů a škálovat kapacitu s libovolným počtem instancí kontejnerů. Cluster bude zpracovávat všechny komplexní správy instalatérské, jako je škálovatelnost, zdraví a tak dále.

AKS poskytuje způsob, jak zjednodušit vytváření, konfiguraci a správu clusteru virtuálních počítačů v Azure, které jsou předem nakonfigurované pro spouštění kontejnerizovaných aplikací. Pomocí optimalizované konfigurace oblíbených nástrojů pro plánování a orchestraci s otevřeným zdrojovým kódem vám AKS umožňuje využít vaše stávající dovednosti nebo využít velké a rostoucí množství odborných znalostí komunity k nasazení a správě aplikací založených na kontejnerech v Microsoft Azure.

Služba Azure Kubernetes optimalizuje konfiguraci oblíbených nástrojů a technologií s otevřeným zdrojovým kódem Dockeru speciálně pro Azure. Získáte otevřené řešení, které nabízí přenositelnost pro kontejnery i konfiguraci aplikace. Vyberete velikost, počet hostitelů a nástroje orchestrator a AKS zpracovává všechno ostatní.

![Diagram znázorňující strukturu clusteru Kubernetes.](./media/orchestrate-high-scalability-availability/kubernetes-cluster-simplified-structure.png)

**Obrázek 4-7**. Zjednodušená struktura a topologie kubernetes

Obrázek 4-7 znázorňuje strukturu clusteru Kubernetes, kde hlavní uzel (VM) řídí většinu koordinace clusteru a můžete nasadit kontejnery do ostatních uzlů, které jsou spravovány jako jeden fond z hlediska aplikace. To vám umožní škálovat na tisíce nebo dokonce desítky tisíc kontejnerů.

## <a name="development-environment-for-kubernetes"></a>Vývojové prostředí pro Kubernetes

Ve vývojovém prostředí, které [Docker oznámil v červenci 2018](https://blog.docker.com/2018/07/kubernetes-is-now-available-in-docker-desktop-stable-channel/), může Kubernetes také běžet v jednom vývojovém počítači (Windows 10 nebo macOS) pouze instalací [Docker Desktop](https://www.docker.com/community-edition). Později můžete nasadit do cloudu (AKS) pro další testy integrace, jak je znázorněno na obrázku 4-8.

![Diagram znázorňující Kubernetes na vývojovém počítači a poté nasazený do AKS.](./media/orchestrate-high-scalability-availability/kubernetes-development-environment.png)

**Obrázek 4-8**. Běh Kubernetes v dev stroji a cloudu

## <a name="get-started-with-azure-kubernetes-service-aks"></a>Začínáme se službou Azure Kubernetes Service (AKS)

Chcete-li začít používat AKS, nasadit cluster AKS z portálu Azure nebo pomocí příkazového příkazového příkazu. Další informace o nasazení clusteru Kubernetes do Azure najdete v [tématu Nasazení clusteru Služby Azure Kubernetes (AKS).](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal)

Neexistují žádné poplatky za žádný software nainstalovaný ve výchozím nastavení jako součást AKS. Všechny výchozí možnosti jsou implementovány pomocí open-source softwaru. AKS je k dispozici pro více virtuálních počítačů v Azure. Účtují se vám jenom za výpočetní instance, které zvolíte, a také za další spotřebované základní prostředky infrastruktury, jako je úložiště a sítě. Neexistují žádné přírůstkové poplatky za AKS sám.

Další informace o implementaci do Kubernetes `kubectl` `.yaml` na základě a původní soubory, najdete v článku na [nastavení eShopOnContainers se v AKS (Azure Kubernetes Service)](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.-Setting-the-solution-up-in-AKS-(Azure-Kubernetes-Service)).

## <a name="deploy-with-helm-charts-into-kubernetes-clusters"></a>Nasazení pomocí grafů Helm do kubernetesových clusterů

Při nasazování aplikace do clusteru Kubernetes `kubectl.exe` můžete použít původní nástroj příkazového příkazu pomocí souborů nasazení založených na nativním formátu (soubory),`.yaml` jak již bylo uvedeno v předchozí části. Pro složitější aplikace Kubernetes, například při nasazování složitých aplikací založených na mikroslužbách, se však doporučuje používat [Helm](https://helm.sh/).

Helm Charts vám pomůže definovat, verze, nainstalovat, sdílet, upgrade, nebo vrácení zpět i ty složité Aplikace Kubernetes.

Chystáte se dále, helm využití se také doporučuje, protože další Prostředí Kubernetes v Azure, jako je azure [dev spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) jsou také založeny na grafech Helm.

Helm je udržován [nadací Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) ve spolupráci s microsoftem, společností Google, Bitnami a komunitou přispěvatelů Helmu.

Další informace o implementaci na Grafy Helm a Kubernetes, viz příspěvek na [Použití Helm Charts nasadit eShopOnContainers na AKS](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.1-Deploying-to-AKS-using-Helm-Charts).

## <a name="use-azure-dev-spaces-for-you-kubernetes-application-lifecycle"></a>Využití Azure Dev Spaces pro vás Kubernetes životní cyklus aplikace

[Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) poskytuje rychlé a iterativní prostředí pro vývoj Kubernetes pro týmy. S minimálním nastavováním počítačů pro vývoj můžete iterativně spouštět a ladit kontejnery přímo ve službě Azure Kubernetes Service (AKS). Můžete vyvíjet na Windows, Mac nebo Linux pomocí známých nástrojů, jako je Visual Studio, Visual Studio Code nebo příkazového řádku.

Jak již bylo zmíněno, Azure Dev Spaces používá helm grafy při nasazování aplikací založených na kontejnerech.

Azure Dev Spaces pomáhá vývojovým týmům zvýšit produktivitu na Kubernetes, protože umožňuje rychle iterát a ladit kód přímo v globálním clusteru Kubernetes v Azure pomocí visual studia 2017 nebo kódu Visual Studia. Že cluster Kubernetes v Azure je sdílený spravovaný cluster Kubernetes, takže váš tým může spolupracovat. Můžete vyvinout kód izolovaně, pak nasadit do globálního clusteru a provést testování od konce s jinými součástmi bez replikace nebo zesměšňování závislostí.

Jak je znázorněno na obrázku 4-9, nejrozlišující funkcí v Azure Dev Spaces je schopnost vytvářet "prostory", které lze spustit integrované do zbytku globálního nasazení v clusteru:

![Diagram znázorňující použití více prostorů v Azure Dev Spaces.](./media/orchestrate-high-scalability-availability/use-multiple-spaces-azure-dev.png)

**Obrázek 4-9**. Použití více prostorů v Azure Dev Spaces

Azure Dev Spaces můžete transparentně kombinovat produkční mikroslužeb s instancí vývojového kontejneru pro usnadnění testování nových verzí. V podstatě můžete nastavit sdílený dev prostor v Azure. Každý vývojář se může soustředit pouze na svou část aplikace a může iterativně vyvíjet "předem potvrzený" kód v prostoru pro vývoj, který již obsahuje všechny ostatní služby a cloudové prostředky, na kterých závisí jejich scénáře. Závislosti jsou vždycky aktuální a vývojáři pracují způsobem, který odpovídá produkčnímu prostředí.

Azure Dev Spaces poskytuje koncept prostoru, který umožňuje pracovat izolovaně a bez obav z porušení členů týmu. Tato funkce je založena na předponách adres URL; Pokud použijete předponu dev mezery v adrese URL pro požadavek kontejneru, Azure Dev Spaces spustí speciální verzi kontejneru, který nasadil pro tento prostor, pokud existuje. V opačném případě bude spuštěna globální/konsolidovaná verze.

Můžete vidět [eShopOnContainers wiki stránku na Azure Dev Spaces](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.2-Using-Azure-Dev-Spaces-and-AKS) získat praktické zobrazení na konkrétní příklad.

Další informace najdete v článku o [vývoji týmu s Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/team-development-netcore).

## <a name="additional-resources"></a>Další zdroje

- **Začínáme se službou Azure Kubernetes Service (AKS)** \
  <https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal>

- **Azure Dev Spaces** \
  <https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces>

- **Kubernetes.** Oficiální stránky. \
  <https://kubernetes.io/>

## <a name="using-azure-service-fabric"></a>Použití platformy Azure Service Fabric

Azure Service Fabric vznikl z přechodu Microsoftu od doručování "box" produktů, které byly obvykle monolitické ve velkém stylu, k poskytování služeb. Prostředí vytváření a provozu velkých služeb ve velkém měřítku, jako je Azure SQL Database, Azure Cosmos DB, Azure Service Bus nebo AzureEnd, ve tvaru Infrastruktury služeb Cortany. Platforma se vyvíjela v průběhu času, jak ji více a více služeb přijalo. Důležité je, že Service Fabric musel běžet nejen v Azure, ale také v samostatných nasazeních Windows Serveru.

Cílem Service Fabric je vyřešit náročné problémy vytváření a spouštění služeb a efektivně využívat prostředky infrastruktury, aby týmy mohly řešit obchodní problémy pomocí přístupu mikroslužeb.

Service Fabric poskytuje dvě široké oblasti, které vám pomohou vytvářet aplikace, které používají přístup mikroslužeb:

- Platforma, která poskytuje systémové služby pro nasazení, škálování, upgrade, zjišťování a restartování neúspěšných služeb, zjišťování polohy služby, správu stavu a sledování stavu. Tyto systémové služby ve skutečnosti umožňují mnoho vlastností mikroslužeb popsaných výše.

- Programování rozhraní API nebo rozhraní, které vám pomohou vytvářet aplikace jako mikroslužby: [spolehlivé objekty actor a spolehlivé služby](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Můžete si vybrat libovolný kód k vytvoření mikroslužeb, ale tato api usnadňují úlohu a integrují se s platformou na hlubší úrovni. Tímto způsobem můžete získat informace o stavu a diagnostice, nebo můžete využít spolehlivé správy stavu.

Service Fabric je agnostik s ohledem na to, jak budete budovat své služby, a můžete použít libovolnou technologii. Poskytuje však integrované programovací rozhraní API, které usnadňují vytváření mikroslužeb.

Jak je znázorněno na obrázku 4-10, můžete vytvořit a spustit mikroslužeb v Service Fabric buď jako jednoduché procesy nebo jako kontejnery Dockeru. Je také možné kombinovat mikroslužeb založené na kontejnerech s mikroslužbami založenými na procesu v rámci stejného clusteru Service Fabric.

![Diagram znázorňující porovnání clusterů Azure Service Fabric.](./media/orchestrate-high-scalability-availability/azure-service-fabric-cluster-types.png)

**Obrázek 4-10**. Nasazení mikroslužeb jako procesů nebo jako kontejnerů ve službě Azure Service Fabric

V první bitové kopii uvidíte mikroslužeb jako procesy, kde každý uzel spustí jeden proces pro každou mikroslužbu. V druhé bitové kopie uvidíte mikroslužeb jako kontejnery, kde každý uzel běží Docker s několika kontejnery, jeden kontejner na mikroslužbu. Clustery Service Fabric založené na linuxových a hostitelích systému Windows můžou spouštět kontejnery Docker Linux a Kontejnery windows.

Aktuální informace o podpoře kontejnerů v Azure Service Fabric najdete v tématu [Service Fabric a kontejnery](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Service Fabric je dobrým příkladem platformy, kde můžete definovat jinou logickou architekturu (obchodní mikroslužby nebo ohraničené kontexty) než fyzické implementace. Například pokud [implementujete stavové spolehlivé služby](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) v [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), které jsou zavedeny v další části "[Bezstavové versus stavové mikroslužeb](#stateless-versus-stateful-microservices)" máte koncept obchodní mikroslužeb s více fyzických služeb.

Jak je znázorněno na obrázku 4-10 a myšlení z hlediska logické/obchodní mikroslužby při implementaci service fabric stavové spolehlivé služby, obvykle budete muset implementovat dvě úrovně služeb. První je back-end stavové spolehlivé služby, která zpracovává více oddílů (každý oddíl je stavové služby). Druhým je front-endová služba neboli služba Gateway, která má na starosti směrování a agregaci dat napříč více oddíly nebo instancemi stavové služby. Tato služba Gateway také zpracovává komunikaci na straně klienta s opakování smyčky přístup ke službě back-end. Nazývá se služba gateway, pokud implementujete vlastní službu, nebo alternativně můžete také použít out-of-the-box Service Fabric [reverzní proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy).

![Diagram znázorňující několik stavových služeb v kontejnerech.](./media/orchestrate-high-scalability-availability/service-fabric-stateful-business-microservice.png)

**Obrázek 4-11**. Obchodní mikroslužba s několika instancemi stavové služby a vlastní front-end brány

V každém případě při použití Service Fabric stavové spolehlivé služby, máte také logické nebo obchodní mikroslužeb (ohraničený kontext), který se skládá z více fyzických služeb. Každá z nich, služba Gateway a partition služba by mohla být implementována jako ASP.NET služby webového rozhraní API, jak je znázorněno na obrázku 4-11. Service Fabric má předpis pro podporu několika stavových spolehlivých služeb v kontejnerech.

V Service Fabric můžete seskupit a nasadit skupiny služeb jako [service fabric aplikace](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), což je jednotka balení a nasazení pro orchestrator nebo cluster. Aplikace Service Fabric proto může být mapována na tuto autonomní obchodní a logickou hranici mikroslužeb nebo ohraničený kontext, takže můžete tyto služby nasadit samostatně.

### <a name="service-fabric-and-containers"></a>Servisní tkanina a kontejnery

Pokud jde o kontejnery v Service Fabric, můžete také nasadit služby v ikopiíkontejnerů v clusteru Service Fabric. Jak ukazuje obrázek 4-12, většinu času bude existovat pouze jeden kontejner na službu.

![Diagram znázorňující jeden kontejner na službu, který je přiváděn do databáze.](./media/orchestrate-high-scalability-availability/azure-service-fabric-business-microservice.png)

**Obrázek 4-12**. Obchodní mikroslužba s několika službami (kontejnery) v Service Fabric

Aplikace Service Fabric můžete spustit několik kontejnerů přístup k externí databázi a celá sada by logické hranice obchodní mikroslužby. V service fabricu jsou však možné také takzvané "sajdkové" kontejnery (dva kontejnery, které musí být nasazeny společně jako součást logické služby). Důležité je, že obchodní mikroslužeb je logická hranice kolem několika soudržné prvky. V mnoha případech může být jedna služba s jedním datovým modelem, ale v některých jiných případech můžete mít také několik fyzických služeb.

Všimněte si, že můžete kombinovat služby v procesech a služby v kontejnerech ve stejné aplikaci Service Fabric, jak je znázorněno na obrázku 4-13.

![Diagram zobrazující služby v procesech a kontejnerech ve stejné aplikaci.](./media/orchestrate-high-scalability-availability/business-microservice-mapped-to-service-fabric-application.png)

**Obrázek 4-13**. Obchodní mikroslužba mapovaná na aplikaci Service Fabric s kontejnery a stavovými službami

Další informace o podpoře kontejnerů v Azure Service Fabric najdete v [tématu Service Fabric a kontejnery](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Bezstavové versus stavové mikroslužby

Jak již bylo zmíněno dříve, každá mikroslužba (logický ohraničený kontext) musí vlastnit svůj model domény (data a logiku). V případě bezstavové mikroslužeb budou databáze externí a budou využívat relační možnosti, jako je SQL Server nebo Možnosti NoSQL, jako je Azure Cosmos DB nebo MongoDB.

Ale samotné služby mohou být také stavové ve službě Service Fabric, což znamená, že data jsou umístěna v rámci mikroslužby. Tato data mohou existovat nejen na stejném serveru, ale v rámci procesu mikroslužeb, v paměti a trvalé na pevných discích a replikovány do jiných uzlů. Obrázek 4-14 ukazuje různé přístupy.

![Diagram znázorňující porovnání bezstavové a stavové služby.](./media/orchestrate-high-scalability-availability/stateless-vs-stateful-microservices.png)

**Obrázek 4-14**. Bezstavové versus stavové mikroslužby

V bezstavové služby stav (trvalost, databáze) je udržována mimo mikroslužbu. Ve stavových službách je stav udržován uvnitř mikroslužby. Bezstavový přístup je zcela platný a je snadněji implementovat než stavové mikroslužeb, protože přístup je podobný tradiční a známé vzory. Ale bezstavové mikroslužeb uložit latence mezi procesem a zdroje dat. Zahrnují také více přesunutí kusů, když se snažíte zlepšit výkon s další mezipaměti a fronty. Výsledkem je, že můžete skončit s komplexní architektury, které mají příliš mnoho vrstev.

Naproti tomu [stavové mikroslužby](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) mohou vynikat v pokročilých scénářích, protože mezi logikou domény a daty neexistuje žádná latence. Náročné zpracování dat, vrácení her, databáze jako služba a další scénáře s nízkou latencí využívají stavové služby, které umožňují místní stav pro rychlejší přístup.

Bezstátní a stavové služby se doplňují. Například, jak můžete vidět v pravém diagramu na obrázku 4-14, stavové služby lze rozdělit do více oddílů. Chcete-li získat přístup k těmto oddílům, budete pravděpodobně potřebovat bezstavovou službu, která funguje jako služba brány, která ví, jak řešit každý oddíl na základě klíčů oddílů.

Stavové služby mají nevýhody. Vnucují vysokou úroveň složitosti, která má být škálována. Funkce, které by obvykle implementovány externí databázové systémy musí být řešeny pro úkoly, jako je replikace dat napříč stavové mikroslužeb a dělení dat. To je však jedna z oblastí, kde orchestrátor jako [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) s jeho [stavové spolehlivé služby](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) může pomoci nejvíce – zjednodušením vývoje a životního cyklu stavových mikroslužeb pomocí [rozhraní API spolehlivých služeb](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) a spolehlivé [objekty actor](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Další rozhraní mikroslužeb, které umožňují stavové služby, podporují vzorek actor a zlepšují odolnost proti chybám a latenci mezi obchodní logikou a daty, jsou Microsoft [Orleans](https://github.com/dotnet/orleans), od společnosti Microsoft Research a [Akka.NET](https://getakka.net/). Oba rámce v současné době zlepšují svou podporu pro Docker.

Nezapomeňte, že kontejnery Dockeru jsou samy o sobě bezstavové. Pokud chcete implementovat stavové služby, budete potřebovat jeden z dalších normativní a vyšší úrovně rozhraní uvedeno dříve.

## <a name="using-azure-service-fabric-mesh"></a>Použití sítě Azure Service Fabric Mesh

Azure Service Fabric Mesh je plně spravovaná služba, která vývojářům umožňuje vytvářet a nasazovat důležité aplikace bez správy jakékoli infrastruktury. Pomocí služby Service Fabric Mesh můžete sestavovat a spouštět zabezpečené distribuované aplikace mikroslužeb, které se škálují na vyžádání.

Jak je znázorněno na obrázku 4-15, aplikace hostované na Service Fabric Mesh běží a škálují, aniž byste se museli starat o infrastrukturu, která ji pohání.

![Diagram znázorňující nasazení z místního úložiště do sítě Service Fabric.](media/orchestrate-high-scalability-availability/deploy-microservice-containers-apps-service-fabric-mesh.png)

**Obrázek 4-15**. Nasazení aplikace mikroslužeb/kontejnerů do sítě Service Fabric

Pod kryty service fabric mesh se skládá z clusterů tisíců strojů. Veškeré operace správy clusteru jsou před vývojáři skryté. Jednoduše musíte nahrát kontejnery a zadat prostředky, které potřebujete, požadavky na dostupnost a omezení prostředků. Service Fabric Mesh automaticky přidělí infrastrukturu potřebnou pro nasazení vaší aplikace a také se postará o případná selhání infrastruktury, aby vaše aplikace měla trvale vysokou dostupnost. Na vás bude jen starost o stav a rychlost reakce aplikace, nikoli o infrastrukturu.

Další informace naleznete v [dokumentaci service fabric mesh](https://docs.microsoft.com/azure/service-fabric-mesh/).

## <a name="choosing-orchestrators-in-azure"></a>Výběr orchestrátorů v Azure

Následující tabulka obsahuje pokyny k tomu, jaký orchestrátor použít v závislosti na úlohách a fokusu operačního systému.

![Obrázek tabulky, která porovnává Kubernetes a Service Fabric.](media/orchestrate-high-scalability-availability/orchestrator-selection-azure-guidance.png)

**Obrázek 4-16**. Výběr orchestrátoru v navádění k Azure

>[!div class="step-by-step"]
>[Předchozí](soa-applications.md)
>[další](deploy-azure-kubernetes-service.md)
