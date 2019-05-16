---
title: Orchestrace mikroslužeb a vícekontejnerových aplikací pro vysokou škálovatelnost a dostupnost
description: Skutečné produkční aplikace muset nasazují a spravují s orchestrátory, které zpracovávají stavu, úlohy a životní cykly všechny kontejnery.
ms.date: 02/15/2019
ms.openlocfilehash: 6cb41e632db7c7c6b9412bf54d2efeb44deee80f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644712"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Orchestrace mikroslužeb a vícekontejnerových aplikací pro vysokou škálovatelnost a dostupnost

Využitím orchestrátorů, pro aplikace připravené pro produkční prostředí je nezbytné, pokud je vaše aplikace založené na mikroslužbách nebo rozdělit mezi několik kontejnerů. Zavedeném dříve, v rámci přístupu založených na mikroslužbách vlastní jednotlivých mikroslužeb jeho modelu a datům tak, aby ho autonomní od vývoje a nasazení pohledu. Ale i v případě, že máte více tradiční aplikace, který se skládá z několika služeb (např. SOA), budete mít také více kontejnerů nebo služby vytvářející jednu obchodní aplikaci, která je nutné nasadit jako distribuovaný systém. Tyto druhy systémy jsou komplexní horizontální navýšení kapacity a Správa; Proto pokud chcete mít vícekontejnerová aplikace připravené pro produkční prostředí a škálovatelné se naprosto je nutné orchestrátor.

Obrázek 4 až 6 ukazuje nasazení do clusteru aplikace skládá z několika mikroslužeb (kontejnery).

![Složené aplikací Dockeru v clusteru: Použijete jeden kontejner pro každou repliku služby. Kontejnery dockeru jsou "jednotkách nasazení" a kontejner je, že instance hostitele Docker.A zpracovává mnoho kontejnerů](./media/image6.png)

**Obrázek 4 až 6**. Cluster kontejnerů

Vypadá jako logický přístup. Ale jak můžete zvládají Vyrovnávání zatížení, směrování a orchestraci těchto aplikací skládá?

Rozhraní příkazového řádku Docker (CLI) splňuje potřeby správy jednoho kontejneru na jednom hostiteli, ale vrátí krátký se při rozhodování o Správa více kontejnerů, které jsou nasazeny na více hostitelích pro složitější distribuované aplikace. Ve většině případů je třeba platforma pro správu, který bude automaticky spustit kontejnery, horizontální navýšení kapacity s více instancemi jednotlivé image kontejnerů, pozastavit je nebo je vypnout, když potřeba a v ideálním případě také určují, jak bude přístup k prostředkům, jako je síť a data úložiště.

Se dostat nad rámec správu jednotlivých kontejnerů nebo jednoduché složené aplikace a přesun směrem k větší podnikové aplikace s využitím mikroslužeb, musíte povolit orchestraci a clustering platformy.

Z pro architekturu a vývoj pohledu Pokud jste sestavení velké, enterprise, založených na mikroslužbách, aplikace, je důležité pochopit následující platformy a produkty, které podporují pokročilé scénáře:

- **Clustery a orchestrátorů.** Když budete potřebovat pro horizontální navýšení kapacity aplikace v mnoha hostitelích Dockeru, jako s velkých aplikací založených na mikroslužbách, je důležité mít možnost spravovat všechny tyto hostitele jako jeden cluster podle abstrahovat složitost základní platformy. Je to, co nabízejí clustery kontejnerů a orchestrátorů. Příklady orchestrátorů: Azure Service Fabric a Kubernetes. Kubernetes je k dispozici v Azure pomocí služby Azure Kubernetes Service.

- **Plánovači.** *Plánování* znamená, že chcete mít možnost pro správce ke spuštění kontejnerů v clusteru, takže plánovači také nabízí uživatelské rozhraní, to udělat. Plánovač clusteru má několik odpovědnosti: efektivně využívat prostředky clusteru, omezení zadaná uživatelem pro efektivní kontejnery pro vyrovnávání zatížení napříč uzly nebo hostitele a být odolnější proti chybám při zajištění vysoké dostupnost.

Koncepty cluster a Plánovač jsou úzce souvisí, takže produkty k dispozici od různých dodavatelů často zadat obě sady funkcí. Následující sekci je uvedena nejdůležitější platformy a software volby, které máte pro clustery a plánovače. Tyto orchestrátorů se běžně nabízejí ve veřejných cloudech, jako je Azure.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Softwarové platformy pro kontejner clustering, orchestraci a plánování

| Platforma | Komentáře |
|:---:|:---|
| **Kubernetes** <br/> ![Kubernetes Logo](./media/kubernetes-logo.png) | [*Kubernetes* ](https://kubernetes.io/) je opensourcový produkt, který poskytuje funkce, které od infrastruktura clusteru a kontejnerů plánování a orchestraci možnosti. Umožňuje vám automatizovat nasazování, škálování a provoz kontejnerů aplikací napříč clustery hostitelů. <br/> <br/> *Kubernetes* poskytuje infrastrukturu zaměřené na kontejner, který seskupuje kontejnerů aplikací do logické jednotky pro snadnou správu a zjišťování. <br/> <br/> *Kubernetes* je zavedený v systému Linux, méně až po zralé ve Windows. |
| **Azure Kubernetes Service (AKS)** <br/> ![Logo Azure Kubernetes Service](./media/aks-logo.png) | [Azure Kubernetes Service (AKS)](https://azure.microsoft.com/services/kubernetes-service/) je spravovaná služba Orchestrace kontejnerů Kubernetes v Azure, která zjednodušuje správu clusteru Kubernetes, nasazení a provoz. |
| **Azure Service Fabric** <br/> ![Logo Azure Service Fabric](./media/service-fabric-logo.png) | [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) je platforma mikroslužeb Microsoftu pro sestavování aplikací. Je [orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) ze služeb a vytváří clustery počítačů. Service Fabric dokáže nasadit služby, kontejnery nebo jako obyčejný procesy. Může dokonce kombinaci služby v procesech se službami v kontejnerech v rámci stejné aplikace a clusteru. <br/> <br/> *Service Fabric* clustery je možné nasadit v Azure, místně nebo v libovolném cloudu. Nasazení v Azure je však zjednodušen spravovaný přístup. <br/> <br/> *Service Fabric* poskytuje další a volitelné doporučené [programovacích modelů Service Fabric](https://azure.microsoft.com/documentation/articles/service-fabric-choose-framework/) jako [stavové služby](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-services-introduction/) a [Reliable Actors](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-actors-introduction/) . <br/> <br/> *Service Fabric* je zavedený ve Windows (roky vyvíjejí Windows), méně až po zralé v systému Linux. <br/> <br/> Od verze 2017 jsou podporovány kontejnery Linux i Windows v Service Fabric. |
| **Síť Azure Service Fabric** <br/> ![Azure Service Fabric sítě Logo](./media/azure-service-fabric-mesh-logo.png) | [*Azure Service Fabric mřížky* ](https://docs.microsoft.com/azure/service-fabric-mesh/service-fabric-mesh-overview) nabízí stejnou spolehlivost, kritických pro chod výkonu a škálování jako Service Fabric, ale také nabízí plně spravované a bez serveru platformy. Není nutné ke správě clusteru, virtuální počítače, úložiště nebo síťové konfigurace. Můžete soustředit jen na vývoj vaší aplikace. <br/> <br/> *Service Fabric mřížky* podporuje kontejnery Windows i Linuxem, abyste mohli vyvíjet s libovolný programovací jazyk a rozhraní dle vlastního výběru.

## <a name="using-container-based-orchestrators-in-azure"></a>Pomocí orchestrátorů založených na kontejnerech v Azure

Několik dodavatelů cloud nabízí podporu kontejnerů Dockeru a Docker clusterů a podporu Orchestrace, včetně Azure, Amazon EC2 Container Service a modul kontejnerů Google. Azure podporuje Docker clusteru a orchestrator prostřednictvím Azure Kubernetes Service (AKS), Azure Service Fabric a Azure Service Fabric mřížky.

## <a name="using-azure-kubernetes-service"></a>Používání služby Azure Kubernetes

Kubernetes cluster fondy několik hostitelů Docker a zpřístupňuje jako jednoho virtuálního hostitele Docker, abyste mohli nasadit několik kontejnerů do clusteru a horizontální navýšení kapacity s libovolným počtem instancí kontejneru. Cluster bude zpracovávat složité správy základní, jako je škálovatelnost, stavu a tak dále.

AKS zajišťuje zjednodušení vytváření, konfiguraci a správu clusterů virtuálních počítačů v Azure, které je předem nakonfigurované spouštění kontejnerizovaných aplikací. Použití optimalizovanou konfiguraci oblíbených nástrojů open source plánování a orchestraci, AKS vám umožní využívat své stávající dovednosti nebo nakreslit velké a stále se rozšiřujících odborných znalostech komunity k nasazení a správě kontejnerových aplikací v Microsoft Azure .

Azure Kubernetes Service optimalizuje konfiguraci oblíbených Docker clusteringu open source nástrojů a technologií konkrétně pro Azure. Získáte otevřené řešení, které nabízí přenositelnost pro vaše kontejnery i Konfigurace aplikací. Vyberete velikost, počet hostitelů a orchestrační nástroje a AKS postará o všechno ostatní.

![Struktura clusteru Kubernetes: Existuje jeden hlavní uzel, který zpracovává DNS, Plánovač, proxy server a podobně a několik pracovních uzlů, které jsou hostiteli kontejnerů.](media/image36.png)

**Obrázek 4 – 7**. Zjednodušenou strukturu a topologii clusteru Kubernetes

Obrázek 4 – 7 znázorňuje strukturu cluster Kubernetes hlavní uzel (VM) řídí většina koordinace clusteru, kde můžete nasadit kontejnery na zbývající uzly, které se spravují jako jeden fond z hlediska aplikací. Máte možnost škálovat do tisíců nebo dokonce desítek tisíců kontejnerů.

## <a name="development-environment-for-kubernetes"></a>Vývojové prostředí pro Kubernetes

Ve vývojovém prostředí, která [Dockeru v červenci 2018 jsme oznámili](https://blog.docker.com/2018/07/kubernetes-is-now-available-in-docker-desktop-stable-channel/), Kubernetes můžete také spustit v rámci jediného vývojového počítače (Windows 10 nebo macOS) právě nainstalováním [Docker Desktop](https://www.docker.com/community-edition). Můžete ji později nasadit do cloudu (AKS) pro další testů integrace, jak je znázorněno na obrázku 4. – 8.

![Docker oznámilo podporu počítač dev pro clustery Kubernetes na dne. 2018 v Desktopu Dockeru.](media/kubernetes-development-environment.png)

**Obrázek 4. – 8**. Ve vývojovém počítači i v cloudu s Kubernetes

## <a name="get-started-with-azure-kubernetes-service-aks"></a>Začínáme s Azure Kubernetes Service (AKS)

Pokud chcete začít používat AKS, nasaďte cluster AKS z webu Azure portal nebo pomocí rozhraní příkazového řádku. Další informace o nasazení clusteru Azure Container Service najdete v tématu [Nasaďte cluster Azure Kubernetes Service (AKS)](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal).

Neexistují žádné poplatky za software ve výchozím nastavení nainstalované jako součást AKS. Všechny výchozí možnosti jsou implementovány pomocí open source softwaru. AKS je k dispozici pro několik virtuálních počítačů v Azure. Platíte jenom za výpočetní instance, kterou zvolíte, jakož i jiné infrastruktury spotřebované základní prostředky, jako je například úložiště a sítě. Neúčtují žádné dodatečné poplatky pro AKS, samotného.

Pro implementaci Další informace o nasazování do Kubernetes na základě `kubectl` a původní `.yaml` soubory, najdete v příspěvku [aplikaci eShopOnContainers nastavení ve službě AKS (služby Azure Kubernetes Service)](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.-Setting-the-solution-up-in-AKS-(Azure-Kubernetes-Service)).

## <a name="deploy-with-helm-charts-into-kubernetes-clusters"></a>Nasazení pomocí helmu do clusterů Kubernetes

Při nasazení aplikace do clusteru Kubernetes, můžete použít původní `kubectl.exe` nástroj rozhraní příkazového řádku pomocí souborů nasazení založen na nativním formátu (`.yaml` soubory), co již bylo uvedeno v předchozí části. Nicméně u složitějších aplikací Kubernetes, jako při nasazení složitých aplikací založených na mikroslužbách, doporučuje se použít [Helm](https://helm.sh/).

Grafy Helm umožňuje definovat, verzi, instalace, sdílené složky, upgrade nebo vrácení zpět i nejsložitější aplikaci Kubernetes.

Když budete pokračovat, Helm využití se také doporučuje, protože další prostředí Kubernetes v Azure, jako například [prostory Azure Dev](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) jsou také založeny na helmu.

Helm je spravován [Foundation nativní computingu na Cloud (CNCF)](https://www.cncf.io/) ve spolupráci s Microsoftem, Google, Bitnami a Přispěvatel komunity Helm.

Další informace o implementaci na grafy Helm a Kubernetes, najdete v příspěvku [pomocí helmu k nasazení do AKS aplikaci eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.1-Deploying-to-AKS-using-Helm-Charts).

## <a name="use-azure-dev-spaces-for-you-kubernetes-application-lifecycle"></a>Použijte Azure Dev mezery za vás Kubernetes životního cyklu aplikací

[Azure Dev prostory](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) poskytuje rychlý a iterativní Kubernetes vývojové prostředí pro týmy. S nastavením minimální dev počítače můžete interaktivně spustit a ladit kontejnery přímo ve službě Azure Kubernetes Service (AKS). Můžete vyvíjet pro Windows, Mac nebo Linux pomocí známých nástrojů, jako je Visual Studio, Visual Studio Code nebo příkazového řádku.

Jak už bylo zmíněno, používá Azure Dev prostory helmu při nasazování aplikací založených na kontejnerech.

Azure Dev prostorech vývojové týmy být produktivnější s Kubernetes, protože umožňuje rychle iterovat a ladění kódu přímo v globální clusteru Kubernetes v Azure jenom pomocí sady Visual Studio 2017 nebo Visual Studio Code. Že cluster Kubernetes v Azure sdílené spravuje clusteru Kubernetes, takže váš tým může spolupracovat spolupracují. Vývoj kódu v izolaci, pak můžete nasadit do clusteru globální a provést začátku do konce testování s ostatními součástmi bez replikace nebo napodobování nahoru závislosti.

Jak je znázorněno na obrázku 4 – 9, většina odlišující funkce v Azure Dev prostory je možnost vytváření mezery' ", které můžou běžet integrované do zbytku globálního nasazení v clusteru.

![Azure Dev prostory můžete transparentně kombinovat a párovat produkční mikroslužeb s vývoj instance kontejneru, do testování nových verzí.](media/image38.png)

**Obrázek 4 – 9**. Použití více mezer v Azure Dev mezery

V podstatě můžete nastavit prostor sdíleném vývojovém v Azure. Každý Vývojář můžete zaměřit na právě jejich součástí aplikace a můžete využít iterativní vývoj "předem potvrzené" kódu v prostoru dev, která už obsahuje všechny ostatní služby a cloudové prostředky, které jejich scénářů závisí na. Závislosti jsou vždy aktuální a vývojáři už pracují tak, aby zrcadlí produkčního prostředí.

Azure Dev prostory nabízí koncepci místa, což umožňuje pracovat v izolaci a bez obav z přerušení členy týmu. Tato funkce je založena na předpony adres URL; Pokud používáte předponu prostoru vývoj v adrese URL pro požadavek kontejneru, spustí prostory Azure Dev speciální verzi kontejneru, který se nasazuje pro toto místo, pokud existuje. V opačném případě poběží verze globální nebo konsolidované.

Zobrazí se [aplikaci eShopOnContainers wiki stránky v Azure Dev prostorech](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.2-Using-Azure-Dev-Spaces-and-AKS) získat praktické zobrazení na konkrétní příklad.

Další informace najdete v článku na [týmový vývoj pomocí Azure Dev prostory](https://docs.microsoft.com/azure/dev-spaces/team-development-netcore).

## <a name="additional-resources"></a>Další zdroje

- **Začínáme s Azure Kubernetes Service (AKS)** \
  <https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal>

- **Azure Dev mezery** \
  <https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces>

- **Kubernetes.** Oficiální web. \
  <https://kubernetes.io/>

## <a name="using-azure-service-fabric"></a>Použití platformy Azure Service Fabric

Azure Service Fabric nástroji od Microsoftu pro přechod z současném dodávání produktů "pole", které byly obvykle monolitické ve stylu, k zajištění služeb. Prostředí pro sestavování a provoz velkých služeb ve velkém měřítku, jako je například Azure SQL Database, Azure Cosmos DB, Azure Service Bus nebo back-endu asistentky Cortana ve tvaru Service Fabric. Platforma se v čase, jako další a další služby přijal. Co je důležité Service Fabric museli spouštět pouze v Azure, ale také v samostatných nasazeních systému Windows Server.

Cílem Service Fabric je řeší těžké problémy sestavování a provoz služby a efektivně využívá prostředky infrastruktury tak, aby týmy mohou řešení obchodních problémů pomocí přístup založený na mikroslužbách.

Service Fabric poskytuje dva různé oblasti, které vám pomůže vytvářet aplikace, které používají přístup založený na mikroslužbách:

- Platforma, která poskytuje služby systém nasadit, škálovat, upgradovat, zjišťovat a restartujte služby se nezdařilo, zjistit umístění služby, Správa stavu, a monitorovat stav. Tyto systémové služby platit přinášejí mnohé z charakteristiky mikroslužeb je popsáno výše.

- Programování v rozhraní API nebo rozhraní, které vám pomůžou vytvářet aplikace jako mikroslužeb: [reliable actors a modelu reliable services](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Můžete použít libovolný kód pro vytváření mikroslužeb, ale tato rozhraní API provést úlohu jednodušší a integrují s platformou na podrobnější úrovni. Tímto způsobem můžete získat stavu a diagnostické informace nebo je mohou využít výhod správy spolehlivé stavu.

Service Fabric je nezávislá s ohledem na jak vytvářet služby, a můžete použít libovolné technologii. Však nabízí integrovanou programovací rozhraní API, která usnadňují vytváření mikroslužeb.

Jak ukazuje obrázek 4 – 10, můžete vytvořit a spouštět mikroslužby v Service Fabric, buď jako jednoduchý proces, nebo jako kontejnery Dockeru. Je také možné kombinovat mikroslužeb založených na kontejnerech s mikroslužbami založené na procesu ve stejném clusteru Service Fabric.

![Porovnání služby Azure service Fabric clustery: Mikroslužby jako proces, ve kterém každý uzel spuštěná jeden proces u jednotlivých mikroslužeb; Jako kontejnery, ve kterém každý uzel spuštěná Dockeru s několika kontejnery, Mikroslužby jednoho kontejneru na mikroslužbách.](./media/azure-service-fabric-cluster-types.png)

**Obrázek 4 – 10**. Nasazuje mikroslužby jako procesů nebo kontejnerů v Azure Service Fabric

Clustery Service Fabric, které jsou založené na hostitele se systémy Linux a Windows můžete spouštět kontejnery Linuxu Docker a kontejnery Windows.

Aktuální informace o podpoře kontejnery v Azure Service Fabric najdete v tématu [Service Fabric a kontejnery](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Service Fabric je typickým příkladem platformy, ve kterém můžete definovat jinou logickou architekturu (obchodní mikroslužby nebo ohraničených kontextech) než fyzická implementace. Například, pokud se rozhodnete implementovat [stavové služby Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) v [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), které jsou popsané v další části "[Stateless a stavových mikroslužeb](#stateless-versus-stateful-microservices), "máte koncept obchodní mikroslužeb s více službami fyzické.

Jak ukazuje obrázek 4 – 10 a přemýšlení z hlediska obchodní logiky/mikroslužeb, při implementaci služby Reliable Stateful Service Fabric je obvykle potřeba implementovat dvě úrovně služeb. První je back-end spolehlivé stavové služby, která zpracovává více oddílů (každý oddíl se stavovou službou). Druhým je front-endová služba a služba brány starosti agregace směrování a data napříč několika oddíly nebo instance stavové služby. Tuto službu brány také zpracovává komunikace na straně klienta s opakování smyčky přístup k back-end služby. Pokud implementujete vlastní službu, nebo také můžete použít také out-of-the-box Service Fabric se používá označení služba brány [reverzní proxy server](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy).

![Service Fabric je předpis pro podporu několika stavovém modelu reliable services v kontejnerech.](./media/service-fabric-stateful-business-microservice.png)

**Obrázek 4 – 11**. Obchodní mikroslužeb s několika instancemi stavové služby a vlastní bránu front-endu

V každém případě použijete Service Fabric stavové služby Reliable Services, máte také logické nebo obchodní mikroslužbě (objektu Context ohraničená), který se skládá z několika fyzických služeb. Každá z jejich, služba brány a oddílu služby může možné implementovat jako rozhraní ASP.NET Web API služby, jak ukazuje obrázek 4 – 11.

V Service Fabric, skupiny a nasazení skupin služeb jako [aplikace Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), což je jednotka balení a nasazení nástroje orchestrator nebo clusteru. Proto aplikace Service Fabric může být mapována na tento autonomní obchodní a logické vyladěných hraniční nebo ohraničená kontext, tak můžete nasadit tyto služby samostatně.

### <a name="service-fabric-and-containers"></a>Service Fabric a kontejnery

Jde o kontejnerů v Service Fabric můžete taky nasadit služby v imagí kontejnerů v clusteru Service Fabric. Jak ukazuje obrázek 4-12, ve většině případů bude existovat jenom jeden kontejner na službu.

![Aplikace Service Fabric můžete spustit několik kontejnerů přístup k externí databázi a celé sady by logické hranic Mikroslužby firmy](./media/azure-service-fabric-business-microservice.png)

**Obrázek 4-12**. Obchodní mikroslužeb s několika službami (kontejnerů) v Service Fabric

Kontejnery takzvané "sajdkára" (dva kontejnery, které musí být nasazeny společně jako součást logické služby) ale také možné v Service Fabric. Důležité je, že obchodní mikroslužeb je logické hranicí kolem několika získá na ucelenosti prvků. V mnoha případech může být jedinou službou s jediným datovým modelem, ale v některých případech můžete mít i několik fyzických služeb.

Jak ukazuje obrázek 4-13, mějte na paměti, že je možné kombinovat služby v procesech a služby v kontejnerech, ve stejné aplikaci Service Fabric.

![Aplikace service fabric s služeb a kontejnerů ve stejném uzlu.](./media/business-microservice-mapped-to-service-fabric-application.png)

**Obrázek 4 – 13**. Obchodní mikroslužeb mapovány na aplikaci Service Fabric s kontejnery a stavové služby

Další informace o podporu kontejnerů v Azure Service Fabric najdete v tématu [Service Fabric a kontejnery](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Bezstavových a stavových mikroslužeb

Jak bylo zmíněno výše, musíte vlastnit jednotlivých mikroslužeb (logické ohraničená Context) jeho doménový model (data a logiku). V případě bezstavové mikroslužby budou databáze externí, když relační možnosti, jako je SQL Server nebo možností NoSQL, jako jsou služby Azure Cosmos DB nebo MongoDB.

Ale vlastních služeb může být také stavové v Service Fabric, což znamená, že jsou data uložená v rámci mikroslužbách. Tato data mohou existovat nejen na stejném serveru, ale v rámci procesu mikroslužeb v paměti a trvale se uloží na pevné disky a replikují do dalších uzlů. Obrázek 4-30 ukazuje různé přístupy.

![V bezstavové služby stavu (trvalost, databáze), zůstane mimo mikroslužbách. Stavové služby stavu, zůstane uvnitř mikroslužbách.](./media/stateless-vs-stateful-microservices.png)

**Obrázek 4 – 14**. Bezstavových a stavových mikroslužeb

Bezstavové přístup dokonale platný a je jednodušší než stavových mikroslužeb, protože tento přístup je podobná tradičním a dobře známé vzory implementace. Ale bezstavové mikroslužby kladou latence mezi zdroji procesy a data. Zahrnují také několik pohyblivých částí, když se snažíte zlepšení výkonu pomocí dalších mezipaměť a fronty. Výsledkem je, že můžete skončit s komplexní architektury, které mají moc úrovní.

Naproti tomu [stavových mikroslužeb](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) může aplikace excel v pokročilých scénářích, protože neexistuje žádný latence mezi domény logiku a data. Silná zpracování dat, hraní her zpět ukončí, databáze jako služba, a další scénáře s nízkou latencí všechny výhody stavové služby, které umožňují rychlejší přístup k místním stavu.

Bezstavové a stavové služby vzájemně doplňují. Pro instanci jak je vidět v diagramu pravý obrázek 4 – 31, stavové služby je možné rozdělit do několika oddílů. Pro přístup k těmto oddílů, může být nutné bezstavové služby, který funguje jako služba brány, která ví, jak vyřešit každý oddíl podle klíče oddílů.

Stavové služby mají nevýhody. Ukládají na úroveň vysokou složitost škálovat. Funkce, která by obvykle implementována externí databázovými systémy. je potřeba řešit pro úlohy, jako je replikace dat mezi stavových mikroslužeb a dělení dat. Ale to je jedna z oblasti, kde jako orchestrátor [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) s jeho [stavovém modelu reliable services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) může pomoct nejvíce – díky zjednodušení vývoje a životního cyklu stavová mikroslužby pomocí [Reliable Services API](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) a [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Další architektury mikroslužeb, umožňujících stavové služby, které podporují vzor objektu Actor a zlepšují odolnost proti chybám a latencí mezi obchodní logiku a data jsou Microsoft [Orleans](https://github.com/dotnet/orleans), od Microsoft Research a [ Akka.NET](https://getakka.net/). Obě architektury jsou aktuálně zlepšení jejich podpora pro Docker.

Mějte na paměti, že kontejnery Dockeru jsou bezstavové sami. Pokud chcete implementovat stavové služby, budete potřebovat další doporučené postupy a chcete získat podrobnější popis architektury jste si předtím poznamenali.

## <a name="using-azure-service-fabric-mesh"></a>Pomocí sítě Azure Service Fabric

Sítě Azure Service Fabric je plně spravovaná služba, která umožňuje vývojářům umožníte sestavovat a nasazovat nejdůležitější aplikace bez nutnosti spravovat žádnou infrastrukturu. Pomocí sítě pro Service Fabric můžete vytvářet a spouštět aplikace zabezpečené a distribuovaných mikroslužeb, které se škálují na vyžádání.

Jak je znázorněno na obrázku 4-15, aplikacemi hostovanými na služby prostředků infrastruktury sítě spouštění a škálování bez starostí o infrastrukturu ukončit.

![Vícekontejnerová aplikace spuštěná v desktopu Dockeru je nasadit do Azure Service Fabric sítě bez starostí o infrastrukturu.](media/image39.png)

**Obrázek 4 – 15**. Nasazení aplikace mikroslužeb a kontejnerů do Service Fabric mřížky

Pod pokličkou sítě pro Service Fabric se skládá z clusterů tisíce počítačů. Všechny operace clusteru jsou skryté od vývojáře. Stačí nahrát kontejnery a zadejte prostředky, které potřebujete, požadavky na dostupnost a limity prostředků. Service Fabric sítě automaticky přiděluje infrastruktury požadoval nasazení vaší aplikace a také zpracovává selhání infrastruktury, ujistěte se, že jsou vaše aplikace s vysokou dostupností. Stačí vám jde o stavu a rychlost reakce aplikace, ne na infrastrukturu.

Další informace najdete v tématu [dokumentace ke službě Service Fabric mřížky](https://docs.microsoft.com/azure/service-fabric-mesh/).

## <a name="choosing-orchestrators-in-azure"></a>Výběr orchestrátorů v Azure

Následující tabulka obsahuje pokyny k jaké orchestrator, která umožní použít v závislosti na úlohy a operačního systému fokus.

![Služby Azure Kubernetes je vyspělejší v Linuxu než ve Windows a se nejčastěji používá pro nasazování mikroslužeb založené na kontejnerech. Azure Service Fabric (cluster a sítě) je vyspělejší ve Windows než v systému Linux, běžně používá pro mikroslužby podle kontejnery, mikroslužby, na základě jednoduché procesy a stavové služby.](media/image40.png)

**Obrázek 4 – 16**. Výběr nástroje Orchestrator v doprovodné materiály k Azure

>[!div class="step-by-step"]
>[Předchozí](soa-applications.md)
>[další](deploy-azure-kubernetes-service.md)
