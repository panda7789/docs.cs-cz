---
title: Orchestrace mikroslužeb a multicontainer aplikace pro vysokou škálovatelnost a dostupnost
description: Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/19/2017
ms.openlocfilehash: 3a505e10b2a37032a7ccfefdf4a6f4bb64d65486
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579545"
---
# <a name="orchestrating-microservices-and-multicontainer-applications-for-high-scalability-and-availability"></a>Orchestrace mikroslužeb a multicontainer aplikace pro vysokou škálovatelnost a dostupnost

Použití orchestrators pro produkční prostředí aplikací je nezbytné, pokud vaše aplikace je založena na mikroslužeb nebo jednoduše rozdělit do několika kontejnerů. Zavedeném dříve, v rámci přístupu na základě mikroslužbu každý mikroslužbu vlastní jeho modelu a data tak, že bude autonomního z hlediska vývoje a nasazení hlediska. Ale i v případě, že máte více tradiční aplikace, která se skládá z několika služeb (například SOA), bude mít také více kontejnerů nebo služby vytvářející jeden obchodní aplikace, které je potřeba nasadit jako distribuovaného systému. Tyto typy systémů jsou složité škálovat a spravovat; Proto pokud chcete, aby produkční prostředí a škálovatelné aplikace multicontainer se absolutně je nutné produktu orchestrator.

Obrázek 4 až 6 znázorňuje nasazení do clusteru s podporou aplikace skládá z několika mikroslužeb (kontejnerů).

![](./media/image6.png)

Obrázek 4 – 6: cluster kontejnery

To vypadá logického přístupu. Ale jak se vám zpracovává Vyrovnávání zatížení, směrování a Orchestrace tyto složený aplikace?

Rozhraní příkazového řádku (CLI) Docker splňuje potřeby správy jednoho kontejneru na jednoho hostitele, ale spadá krátký, pokud jde o správě několika kontejnerů, které jsou nasazené na několika hostitelích pro složitější distribuované aplikace. Ve většině případů potřebujete platforma pro správu, který bude automaticky spustit kontejnery, pozastavení, nebo vypnete v případě potřeby a v ideálním případě taky řídit, jak přistupují k prostředkům, jako jsou úložiště síť a data.

Chcete-li překročila správu jednotlivých kontejnery nebo velmi jednoduché složený aplikace a přesuňte směrem k větší podnikové aplikace s mikroslužeb, musíte povolit orchestration a clustering platformy.

Z architektury a vývoj hlediska Pokud jsou velké enterprise sestavení, na základě mikroslužeb, aplikace, je důležité si uvědomit následující platformy a produkty, které podporují pokročilé scénáře:

-   **Clustery a orchestrators** když potřebujete škálování-out aplikacemi v rámci řadu hostitelů Docker, například s rozsáhlé aplikace na základě mikroslužeb je velmi důležité mít možnost spravovat všechny tyto hostitele jako jeden cluster pomocí poskytuje abstrakci složitost základní platformy. To je, co kontejneru clustery a orchestrators poskytují. Příkladem orchestrators jsou Docker Swarm, Mesosphere DC/OS, Kubernetes (první tři k dispozici prostřednictvím Azure Container Service) a Azure Service Fabric.

-   **Plánovače** *plánování* znamená schopnost pro správce ke spuštění kontejnery v clusteru, aby poskytovaly uživatelské rozhraní. Scheduler clusteru má několik odpovědnosti: efektivně využívat prostředky do clusteru, nastavit omezení zadané uživatelem, efektivně kontejnery Vyrovnávání zatížení mezi uzly nebo hostitele a být odolnosti proti chybám při současném poskytování základní dostupnost.

Koncepty cluster a plánovače jsou úzce související, takže produkty od různých výrobců často poskytují obě sady funkcí. Tabulka 4-1 obsahuje nejdůležitější platformy a softwaru možnosti dostupné pro clustery a plánovače. Tyto clustery jsou obecně nabízena v veřejných cloudů, jako je například Azure.

Tabulka 4-1: softwarovými platformami pro kontejner clustering, orchestration a plánování

| Platforma | Popis |
|---|---|
| Docker Swarm<br/> ![http://rancher.com/wp-content/themes/rancher-2016/assets/images/swarm.png?v=2016-07-10-am](./media/image7.png) | Docker Swarm vám dává možnost clusteru a plán Docker kontejnery. Pomocí Swarm, můžete upravit fond hostitelů Docker na jednu virtuální hostitel Docker. Klienty můžete provést žádostí o rozhraní API Swarm stejným způsobem, který dělají na hostitele, což znamená, že Swarm usnadňuje aplikace škálovat na více hostitelů. <br /><br /> Docker Swarm je produkt z Docker společnosti. <br /><br /> Docker v1.12 nebo můžete později spustit nativní a integrované Swarm režimu. |
| Mesosphere DC/OS<br/>![https://mesosphere.com/wp-content/uploads/2016/04/logo-horizontal-styled.png](./media/image8.png) |  Mesosphere Enterprise DC/OS (podle Apache Mesos) je platforma pro produkční prostředí pro spouštění kontejnery a distribuovaných aplikací. <br /><br /> DC/OS funguje tak, že poskytuje abstrakci kolekce prostředků, které jsou k dispozici v clusteru a zpřístupnění těchto prostředků postavená na jeho součástí. Marathon se obvykle používá jako plánovače integrovat DC/OS. |
| Google Kubernetes<br />![https://pbs.twimg.com/media/Bt\_pEfqCAAAiVyz.png](./media/image9.png) | Kubernetes je produkt open source, který poskytuje funkce, které rozsahy z infrastruktura clusteru a kontejner plánování k funkcím Orchestrace. Pomocí něho můžete automatizovat nasazení, škálování a operace kontejnery aplikací napříč clustery hostitelů. <br /><br /> Kubernetes poskytuje infrastrukturu zaměřené na kontejneru, která skupiny kontejnery aplikací do logické jednotky pro snadnou správu a zjišťování. |
| Azure Service Fabric<br />![https://azure.microsoft.com/svghandler/service-fabric?width=600&height=315](./media/image10.png) | [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) je platforma Microsoft mikroslužeb pro vytváření aplikací. Je [orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) z služby a vytvoří clustery počítačů. Ve výchozím nastavení Service Fabric nasadí a aktivuje služby jako procesy, ale Service Fabric můžete nasadit services v kontejneru imagí Dockeru. Důležitější, je možné kombinovat služby v procesech se službami v kontejnery ve stejné aplikaci. <br /><br /> Od verze může 2017 funkci Service Fabric, který podporuje nasazení služby jako kontejnery Docker je ve stavu preview. <br /><br /> Můžete vyvíjet služby Service Fabric v mnoha směrech pomocí [Service Fabric programovací modely](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) nasazení [hosta spustitelné soubory](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-existing-app) a také kontejnery. Service Fabric podporuje doporučený aplikace modely jako [stavové služby](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) a [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

## <a name="using-container-based-orchestrators-in-azure"></a>Použití na základě kontejneru orchestrators v Azure

Několik cloudu dodavatelé nabízejí podporu kontejnery Docker plus Docker clustery a podporu orchestration, včetně Azure, Amazon EC2 Container Service a modul kontejneru Google. Azure poskytuje Docker podpora clusteru a orchestrator prostřednictvím Azure Container Service, jak je popsáno v následující části.

Další možnost je použít Azure Service Fabric, který podporuje i Docker založené na Linuxu a Windows kontejnery. Service Fabric běží v Azure nebo jiné cloudové a také [místní](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere).

## <a name="using-azure-container-service"></a>Pomocí Azure Container Service

Cluster s podporou Docker fondy více hostitelů Docker a zpřístupní jako jediného virtuálního Docker hostitele, abyste mohli nasadit víc kontejnerů do clusteru. Cluster bude zpracovávat všechny záležitosti komplexní správu třeba škálovatelnost a stavu. Obrázek 4-7 představuje, jak mapuje clusteru Docker pro složený aplikace na službu kontejneru.

Container Service poskytuje způsob, jak zjednodušení vytváření, konfiguraci a správu clusteru virtuálních počítačů, které jsou předem nakonfigurován ke spuštění kontejnerizované aplikací. Pomocí nástroje oblíbených open-source plánování a orchestraci konfigurace aplikace optimalizované, Container Service vám dává možnost k použití existujících dovedností a kreslení na text velké a stále se rozrůstající komunita odborných znalostí k nasazení a správě na základě kontejneru aplikace v Azure.

Container Service optimalizuje konfigurace oblíbených Docker clustering open source nástrojů a technologií speciálně pro Azure. Získáte otevřete řešení, která nabízí přenositelnost kontejnerů a konfigurace aplikace. Vyberte velikost, počtu hostitelů a nástroje orchestrator a kontejneru služba zpracovává nic jiného.

Kontejner službou imagí Dockeru pro zajistěte, aby vaše kontejnery aplikace plně přenositelné. Podporuje vaši volbu open-source orchestration platformách, jako je DC/OS, Kubernetes a Docker Swarm zajistit, aby tyto aplikace lze škálovat pro tisíce nebo i desetitisíce kontejnery.

S Azure Container Service můžete využít výhod funkce podnikové úrovni Azure současně se zachovává přenositelnost aplikace, včetně na vrstvy orchestration.

![](./media/image11.png)

Obrázek 4-7: Clustering volbám v Azure Container Service

Jak ukazuje obrázek 4-8, Container Service je jednoduše infrastruktury služby Azure za účelem nasazení DC/OS, Kubernetes nebo Docker Swarm, ale neimplementuje žádné další orchestrator. Proto je Container Service není orchestrator, jako například; je jenom infrastruktura, která využívá existující orchestrators open source pro kontejnery.

![](./media/image12.png)

Obrázek 4 – 8: Orchestrators v Container Service

Z hlediska využití je cílem Container Service poskytuje hostitelské prostředí kontejneru pomocí Oblíbené open source nástroje a technologie. Za tímto účelem zpřístupní standardní koncové body rozhraní API pro vaši zvolenou orchestrator. Pomocí těchto koncových bodů můžete veškerý software, který může komunikovat se do těchto koncových bodů. V případě koncového bodu Docker Swarm, můžete například použít rozhraní příkazového řádku Dockeru. Pro DC/OS je možné pomocí rozhraní příkazového řádku DC/OS.

### <a name="getting-started-with-container-service"></a>Začínáme s službu kontejneru.

Pokud chcete začít používat službu kontejneru, můžete nasadit cluster Container Service z portálu Azure pomocí šablony Azure Resource Manager nebo [rozhraní příkazového řádku](https://docs.microsoft.com/cli/azure/install-azure-cli). K dispozici šablony zahrnují [Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm), [Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes), a [DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos). Můžete upravit šablony rychlý start zahrnout další nebo pokročilá konfigurace Azure.

**Další informace o** Další informace o nasazení cluster Container Service na webu Azure, přečtěte si [nasazení clusteru Azure Container Service](https://docs.microsoft.com/azure/container-service/dcos-swarm/container-service-deployment).

Neexistují žádné poplatky za software nainstalovaný ve výchozím nastavení jako součást služby ACS. Všechny výchozí možnosti jsou implementovány pomocí open-source softwaru.

Je aktuálně dostupné pro standardní A, D, DS, G a GS řady Linux virtuálních počítačů v Azure Container Service. Budou se účtovat pouze pro výpočetní instance, který zvolíte, a také další základní prostředky infrastruktury využívat, jako je například úložiště a sítě. Neexistují žádné poplatky přírůstkové pro službu kontejneru sám sebe.

### <a name="additional-resources"></a>Další zdroje

Toto jsou umístění, kde můžete najít další informace:

-   Úvod do kontejner Docker hostování řešení s Container Service:  
    https://docs.microsoft.com/azure/container-service/kubernetes/container-service-intro-kubernetes>

-   Přehled docker Swarm:  
    <https://docs.docker.com/swarm/overview/>

-   Přehled režimu swarm:  
    <https://docs.docker.com/engine/swarm/>

-   Přehled mesosphere DC/OS:    
    <https://docs.mesosphere.com/1.7/overview/>

-   Kubernetes (oficiální web):  
    <https://kubernetes.io/>

## <a name="using-service-fabric"></a>Pomocí Service Fabric

Service Fabric vznikly z Microsoftu pro přechod z doručování "pole" produkty, které byly obvykle monolitický ve stylu, k poskytování služeb. Prostředí sestavování a provoz velké služby ve velkém měřítku, jako je například Azure SQL Database, databázi dokumentů Azure, Azure Service Bus nebo na webu Cortana back-end, ve tvaru Service Fabric. Platforma vyvinuly časem více služeb přijatá ho. Je důležité Service Fabric museli spustit pouze v Azure, ale také v samostatných nasazeních systému Windows Server.

Cílem Service Fabric je řešit složité problémy sestavení a spuštění služby a efektivně využívá prostředky infrastruktury tak, aby týmy můžete řešení obchodních problémů mikroslužeb přístup.

Service Fabric nabízí dvě obecné oblasti můžete vytvářet aplikace, které používají mikroslužeb přístup:

-   Platforma, která poskytuje systémové služby pro nasazení, škálování, upgradu, zjišťovat a restartujte služby se nezdařilo, zjistit umístění služby, Správa stavu a sledování stavu. Tyto systémové služby platí poskytují mnoho společných vlastností mikroslužeb popsané.

-   Rozhraní API pro programování nebo rozhraní, můžete vytvářet aplikace, jako mikroslužeb: [spolehlivé aktéři a spolehlivé služby](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Samozřejmě můžete žádný kód k vytvoření mikroslužbu, ale tato rozhraní API proveďte úlohy více přehledné a jejich integraci s platformou na podrobnější úrovni. Tímto způsobem můžete získat stavu a diagnostické informace nebo můžete využít výhod správy spolehlivé stavu.

Service Fabric nerozlišuje s ohledem na tom, jak sestavit služby a všechny technologii můžete použít. Však poskytuje integrované programovací rozhraní API, která usnadňují sestavení mikroslužeb.

Obrázek 4 – 9 ukazuje, jak můžete vytvořit a spustit mikroslužeb v Service Fabric jako jednoduchý procesy, nebo jako Docker kontejnery. Je také možné kombinovat na základě kontejneru mikroslužeb s na základě proces mikroslužeb ve stejném clusteru Service Fabric.

![](./media/image13.png)

Obrázek 4 – 9: nasazení mikroslužeb jako procesy, nebo jako kontejnery v Azure Service Fabric

Kontejnery Docker Linux a Windows kontejnery můžete spouštět clusterů Service Fabric na základě na hostitelích se systémem Linux a Windows.

**Další informace o** aktuální informace o podpoře kontejnery v Service Fabric na webu Azure, najdete v tématu [Service Fabric a kontejnery](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Service Fabric je dobrým příkladem platformy, pomocí kterého můžete definovat různých Logická architektura (business mikroslužeb nebo ohraničenou kontexty) než fyzické implementace. Například, pokud budete implementovat [stavové služby Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) v [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), které jsou popsané v další části "[Stateless versus stavová mikroslužeb](#stateless-versus-stateful-microservices), "máte koncept mikroslužbu obchodní s více fyzických službami.

Jak ukazuje obrázek 4 – 10 a přemýšlení z hlediska logické nebo obchodní mikroslužbu při implementaci služby Fabric Stateful spolehlivě obvykle musíte implementovat dvě úrovně služeb. První je back-end stavová spolehlivá služba, která zpracovává více oddílů. Druhá je front-endová služba, nebo služba brány starosti agregace směrování a data mezi více oddílů nebo instancí stavové služby. Tuto službu brány také obstará komunikace klienta s opakování smyčky přístupu ke službě back-end používá ve spojení s Service Fabric [reverse proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy).

![](./media/image14.png)

Obrázek 4 – 10: obchodní mikroslužbu s několika stavová a Bezstavová služby v Service Fabric

V každém případě při použití služby Fabric stavové služby Reliable Services, máte také logickou nebo obchodní mikroslužbu (ohraničenou kontextu), se obvykle skládá z několika fyzických služeb. Každý z nich, služba brány a oddílu služby by se mohlo provádět jako rozhraní ASP.NET Web API služby, jak ukazuje obrázek 4-10.

V Service Fabric, skupiny a nasazení skupin služby jako [aplikace Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), což je jednotky balení a nasazení pro orchestrator nebo cluster. Proto aplikace Service Fabric mapovat tuto autonomní obchodní a logické mikroslužbu hranic nebo ohraničenou kontextu také.

### <a name="service-fabric-and-containers"></a>Service Fabric a kontejnery

S ohledem na kontejnery v Service Fabric můžete také nasadit services v kontejneru bitové kopie v rámci clusteru Service Fabric. Obrázek 4 – 11 ukazuje, že ve většině případů, které budou existovat jenom jeden kontejner pro službu.

![](./media/image15.png)

Obrázek 4 – 11: obchodní mikroslužbu s několika služeb (kontejnerů) v Service Fabric

Kontejnery takzvané "něho" (dva kontejnery, které musí být nasazeny společně v rámci logické service) je však také možné v Service Fabric. Důležité je, že obchodní mikroslužbu není logické okolí několik získá na ucelenosti elementy. V mnoha případech může být jednu službu s jeden datový model, ale v některých jiných případech může mít fyzické několik služeb, také.

Od této zápis (dubna 2017), v Service Fabric nemůžete nasadit SF spolehlivé stavové služby kontejnerům – můžete nasadit pouze hosta kontejnery, bezstavové služby nebo služby objektu actor v kontejnerech. Ale Všimněte si, že je možné kombinovat služby v procesy a služby v kontejnerech ve stejné aplikaci, Service Fabric, jak ukazuje obrázek 4 – 12.

![](./media/image16.png)

Obrázek 4 – 12: obchodní mikroslužbu namapované na aplikace Service Fabric s kontejnery a stavové služby

Podpora je také liší v závislosti na tom, jestli používáte Docker kontejnery v Linux nebo Windows kontejnerů. Podpora pro kontejnery v Service Fabric se rozšířit v budoucích verzích. Aktuální informace o podpoře kontejneru v Service Fabric na webu Azure číst [Service Fabric a kontejnery](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Bezstavové a stavové mikroslužeb

Jak už bylo zmíněno dříve, musí každý mikroslužbu (logické ohraničenou kontextu) vlastní svůj model domény (dat a logiku). V případě bezstavové mikroslužeb bude databáze externí, využívání možností relační jako SQL Server nebo NoSQL možnosti jako MongoDB nebo Azure DocumentDB.

Služby sami také může být ale stavová, což znamená, že data jsou umístěna v rámci mikroslužby. Tato data mohou existovat nejen na stejném serveru, ale v rámci procesu mikroslužbu v paměti a trvalé na jednotkách a replikované do dalších uzlů. Obrázek 4 – 13 ukazuje různý přístup.

![](./media/image17.png)

Obrázek 4 – 13: bezstavové a stavové mikroslužeb

Bezstavové přístup perfektně platný a je jednodušší než stavová mikroslužeb implementace, protože je podobná tradičním a dobře známé vzorů přístupu. Ale bezstavové mikroslužeb použít latenci mezi zdroji proces a data. Taky při nich probíhá více přesunutí částí Pokud chcete zlepšit výkon s další mezipaměti a fronty. Výsledkem je, že můžou skončit s komplexní architektury, které mají příliš mnoho úrovní.

Naproti tomu [stavová mikroslužeb](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) můžete v aplikaci excel v pokročilých scénářích protože latence mezi domény logiku a data neexistuje. Velkou zpracování dat, herní back EndY, databáze jako služba a v dalších scénářích s nízkou latencí všechny těžit z stavové služby, které místní poskytnutí rychlejší přístup.

Bezstavové a stavové služby jsou vzájemně doplňují. Stavové služby může například rozdělit do několika oddílů. Přístup k tyto oddíly, budete pravděpodobně potřebovat bezstavové služby, který funguje jako brána službu, která umí adres každý oddíl podle klíče oddílů.

Stavové služby mají nevýhody. Ukládají zjednodušit postupy, které umožňuje, aby horizontální navýšení kapacity. Funkce, které by obvykle implementována systémy externí databáze je potřeba řešit pro úlohy, jako je například replikace dat mezi stavová mikroslužeb a data rozdělení do oddílů. To je však jeden z oblastí, kde orchestrator jako [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) s jeho [stavová spolehlivé služby](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) může pomoci nejvíce – tím, že zjednodušuje vývoj a životního cyklu stateful pomocí mikroslužeb [spolehlivé rozhraní API služby](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) a [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Ostatní mikroslužbu platformy, které umožňují stavové služby, které podporují vzor objektu Actor a zlepšují odolnost proti chybám a latence mezi obchodní logiku a data jsou Microsoft [Orléans](https://github.com/dotnet/orleans), z Microsoft Research a [ Akka.NET](https://getakka.net/). Obě architektury jsou aktuálně zlepšení jejich podpora pro Docker.

Upozorňujeme, že jsou kontejnery Docker bezstavové sami. Pokud chcete implementovat stavové služby, musíte další doporučený a vyšší úrovně rozhraní si předtím poznamenali. Době psaní tohoto textu, ale stavové služby v Service Fabric nejsou podporovány jako kontejnery pouze jako prostý mikroslužeb. Spolehlivé služby podpory v kontejnerech bude k dispozici v budoucích verzích Service Fabric.


>[!div class="step-by-step"]
[Předchozí] (applications.md soa) [Další] (docker aplikace development-environment.md)
