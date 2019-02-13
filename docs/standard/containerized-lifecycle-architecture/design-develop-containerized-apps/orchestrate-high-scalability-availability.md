---
title: Orchestrace mikroslužeb a vícekontejnerových aplikací pro vysokou škálovatelnost a dostupnost
description: Skutečné produkční aplikace muset nasazují a spravují s orchestrátory, které zpracovávají stavu, úlohy a životní cykly všechny kontejnery.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 749b613ac847c57eb993bff90b36f02a0b39477f
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221157"
---
# <a name="orchestrating-microservices-and-multicontainer-applications-for-high-scalability-and-availability"></a>Orchestrace mikroslužeb a vícekontejnerových aplikací pro vysokou škálovatelnost a dostupnost

Využitím orchestrátorů, pro aplikace připravené pro produkční prostředí je nezbytné, pokud je vaše aplikace založené na mikroslužbách nebo jednoduše rozdělit mezi několik kontejnerů. Zavedeném dříve, v rámci přístupu založených na mikroslužbách vlastní jednotlivých mikroslužeb jeho modelu a datům tak, aby ho autonomní od vývoje a nasazení pohledu. Ale i v případě, že máte více tradiční aplikace, který se skládá z několika služeb (např. SOA), budou mít také více kontejnerů nebo služby vytvářející jednu obchodní aplikaci, která je nutné nasadit jako distribuovaný systém. Tyto druhy systémy jsou komplexní horizontální navýšení kapacity a Správa; proto naprosto nutné orchestrátor Pokud budete chtít mít připravené pro produkční prostředí a škálovatelné vícekontejnerových aplikací.

Obrázek 4 až 6 ukazuje nasazení do clusteru aplikace skládá z několika mikroslužeb (kontejnery).

![](./media/image6.png)

Obrázek 4 – 6: Cluster kontejnerů

Vypadá jako logický přístup. Ale jak můžete zvládají Vyrovnávání zatížení, směrování a orchestraci těchto aplikací skládá?

Rozhraní příkazového řádku Docker (CLI) splňuje potřeby správy jednoho kontejneru na jednom hostiteli, ale vrátí krátký se při rozhodování o Správa více kontejnerů, které jsou nasazeny na více hostitelích pro složitější distribuované aplikace. Ve většině případů je třeba platforma pro správu, který bude automaticky spustit kontejnery, pozastavení, nebo je vypnout, pokud je nepotřebujete a v ideálním případě také určují, jak bude přístup k prostředkům, jako je úložiště síť a data.

Se dostat nad rámec správu jednotlivých kontejnerů nebo velmi jednoduché složené aplikace a přesun směrem k větší podnikové aplikace s využitím mikroslužeb, musíte povolit orchestraci a clustering platformy.

Z pro architekturu a vývoj pohledu Pokud je sestavení velké, enterprise, založených na mikroslužbách, aplikace, je důležité pochopit následující platformy a produkty, které podporují pokročilé scénáře:

-   **Clustery a orchestrátorů** potřeba škálovat-navýšení kapacity aplikace napříč mnoha hostitelů Docker, jako s velkých aplikací založených na mikroslužbách je důležité mít možnost spravovat všechny tyto hostitele jako jeden cluster pomocí poskytuje abstrakci složitost základní platformy. Je to, co nabízejí clustery kontejnerů a orchestrátorů. Příklady orchestrátorů: Docker Swarm, Mesosphere DC/OS, Kubernetes (první tři dostupné prostřednictvím služby Azure Container Service) a Azure Service Fabric.

-   **Plánovači** *plánování* znamená, že chcete mít možnost pro správce ke spuštění kontejnerů v clusteru tak, aby také poskytují uživatelské rozhraní. Plánovač clusteru má několik odpovědnosti: efektivně využívat prostředky clusteru, omezení zadaná uživatelem pro efektivní kontejnery pro vyrovnávání zatížení napříč uzly nebo hostitele a být odolnější proti chybám při zajištění vysoké dostupnost.

Koncepty cluster a Plánovač jsou úzce souvisí, takže produkty k dispozici od různých dodavatelů často zadat obě sady funkcí. Tabulka 4-1 obsahuje nejdůležitější platformy a software volby, které máte pro clustery a plánovače. Tyto clustery se obvykle nabízejí ve veřejných cloudech, jako je Azure.

Tabulka 4-1: Softwarové platformy pro kontejner clustering, orchestraci a plánování

| Platforma | Popis |
|---|---|
| Docker Swarm<br/> ![Docker Swarm logo](./media/image7.png) | Docker Swarm poskytuje možnost seskupit do clusteru a plánovat kontejnery Dockeru. Pomocí Swarm můžete zapnout fondu hostitelů Docker do jednoho, virtuálního hostitele Dockeru. Klienti mohou provádět požadavky rozhraní API Swarm stejným způsobem, který se dělají na hostitele, což znamená, že Swarm usnadňuje aplikacím škálování na více hostitelích. <br /><br /> Docker Swarm je produkt z Dockeru, společnost. <br /><br /> Docker v1.12 nebo novější můžete spouštět nativní a integrované režimu Swarm. |
| Mesosphere DC/OS<br/>![Logo mesosphere DC/OS](./media/image8.png) |  Mesosphere Enterprise DC/OS (založená na Apache Mesos) je platforma pro produkční prostředí pro spouštění kontejnerů a distribuovaných aplikací. <br /><br /> DC/OS, funguje tak, že poskytuje abstrakci kolekci prostředků, které jsou k dispozici v clusteru a zpřístupnění těchto prostředků komponenty sestavené dojde k jeho zvýraznění. Marathon se obvykle používá jako Plánovač integrovaná s DC/OS. |
| Google Kubernetes<br />![Logo Google Kubernetes](./media/image9.png) | Kubernetes je opensourcový produkt, který poskytuje funkce, které od infrastruktura clusteru a plánování k funkcím orchestrací kontejnerů. Pomocí něho můžete automatizovat nasazení, škálování a provoz kontejnerů aplikací napříč clustery hostitelů. <br /><br /> Kubernetes poskytuje infrastrukturu zaměřené na kontejner, který seskupuje kontejnerů aplikací do logické jednotky pro snadnou správu a zjišťování. |
| Azure Service Fabric<br />![Logo Azure Service Fabric](./media/image10.png) | [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) je platforma mikroslužeb Microsoftu pro sestavování aplikací. Je [orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) ze služeb a vytváří clustery počítačů. Ve výchozím nastavení Service Fabric nasadí a aktivuje služby jako proces, ale Service Fabric dokáže nasadit služby v imagí kontejnerů Dockeru. Důležitější, je možné kombinovat služby v procesech se službami v kontejnerech ve stejné aplikaci. <br /><br /> Od května 2017 je funkce produktu Service Fabric, který podporuje nasazení služby jako kontejnery Dockeru je ve verzi preview. <br /><br /> Při vývoji služeb Service Fabric mnoha způsoby používání [programovacích modelů Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) až po nasazení [spustitelné soubory hosta](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-existing-app) stejně jako kontejnery. Service Fabric podporuje doporučené aplikace modely jako [stavové služby](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) a [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

## <a name="using-container-based-orchestrators-in-azure"></a>Pomocí orchestrátorů založených na kontejnerech v Azure

Několik dodavatelů cloud nabízí podporu kontejnerů Dockeru a Docker clusterů a podporu Orchestrace, včetně Azure, Amazon EC2 Container Service a modul kontejnerů Google. Azure podporuje Docker clusteru a orchestrator prostřednictvím služby Azure Container Service, jak je vysvětleno v další části.

Další volbou je použití Azure Service Fabric, která podporuje také založené na Linuxu a Windows kontejnery Dockeru. Spustí Service Fabric v Azure nebo na jiný cloud a jednak [místní](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere).

## <a name="using-azure-container-service"></a>Pomocí služby Azure Container Service

Docker cluster fondy více hostitelů Docker a zpřístupňuje jako jednoho virtuálního hostitele Docker, abyste mohli nasadit několik kontejnerů do clusteru. Cluster bude zpracovávat složité správy základní například škálovatelnost a stav. Obrázek 4 – 7 znázorňuje, jak mapuje clusteru Docker pro složené aplikace do služby Container Service.

Container Service umožňuje zjednodušení vytváření, konfiguraci a správu clusterů virtuálních počítačů, které je předem nakonfigurované spouštění kontejnerizovaných aplikací. Pomocí optimalizovanou konfiguraci oblíbených nástrojů open source plánování a orchestraci, služba Container Service poskytuje možnost používat svoje stávající dovednosti nebo nakreslit velké a stále se rozšiřujících odborných znalostech komunity k nasazení a správě kontejnerových aplikace v Azure.

Container Service optimalizuje konfiguraci oblíbených Docker clusteringu open source nástrojů a technologií konkrétně pro Azure. Získáte otevřené řešení, které nabízí přenositelnost pro vaše kontejnery i Konfigurace aplikací. Vyberete velikost, počet hostitelů a orchestrační nástroje a služby Container Service se postará o všechno ostatní.

Container Service používá Image Dockeru k zajištění, že plné přenositelnosti kontejnerů vaší aplikace. Podporuje zvoleného Orchestrace open source platforem, jako jsou DC/OS, Kubernetes a Docker Swarm k zajištění, že můžete tyto aplikace škálovat do tisíců nebo dokonce desítek tisíců kontejnerů.

Se službou Azure Container Service můžete využít výhod funkcí Azure na podnikové úrovni a přitom zachovávat přenositelnost aplikací, včetně v orchestračních vrstvách.

![](./media/image11.png)

Obrázek 4 – 7: Clustering s možností ve službě Azure Container Service

Jak je znázorněno v obrázek 4. – 8, Container Service je jednoduše infrastruktury poskytovaný platformou Azure, abyste mohli nasadit DC/OS, Kubernetes a Docker Swarm, ale neimplementuje žádné další nástroje orchestrator. Container Service je proto není orchestrátor, jako například; je jenom infrastruktura, která využívá existující open source orchestrátorů kontejnerů.

![](./media/image12.png)

Obrázek 4. – 8: Orchestrátorů ve službě Container Service

Z hlediska využití cílem služby Container Service je poskytnout hostitelské prostředí kontejneru pomocí oblíbených opensourcových nástrojů a technologií. Za tímto účelem zpřístupňuje standardní koncové body rozhraní API pro zvolený orchestrátor. Pomocí těchto koncových bodů můžete použít jakýkoli software, který může komunikovat s těmito koncovými body. V případě koncového bodu Docker Swarm můžete například použít rozhraní příkazového řádku Dockeru. Pro DC/OS můžete zvolit použití rozhraní příkazového řádku DC/OS.

### <a name="getting-started-with-container-service"></a>Začínáme se službou Container Service

Pokud chcete začít používat službu Container Service, nasaďte cluster Container Service z webu Azure portal s použitím šablony Azure Resource Manageru nebo [CLI](https://docs.microsoft.com/cli/azure/install-azure-cli). Dostupné šablony zahrnují [Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm), [Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes), a [DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos). Můžete upravit šablony pro rychlý start zahrnout další nebo rozšířenou konfiguraci Azure.

**Další informace o** Další informace o nasazování clusteru služby Container Service, na webu Azure [nasazení clusteru Azure Container Service](https://docs.microsoft.com/azure/container-service/dcos-swarm/container-service-deployment).

Neexistují žádné poplatky za software ve výchozím nastavení nainstalované jako součást služby ACS. Všechny výchozí možnosti jsou implementovány pomocí open source softwaru.

Container Service je nyní dostupná pro standardní A, D, DS, G a GS series s Linuxem v Azure. Se vám účtovat jenom výpočetní instance, kterou zvolíte, a také další infrastrukturu spotřebované základní prostředky, jako je například úložiště a sítě. Neúčtují žádné dodatečné poplatky pro službu Container Service samotný.

### <a name="additional-resources"></a>Další zdroje

Umístění, kde najdete další informace jsou následující:

-   Úvod do řešení pomocí služby Container Service pro hostování kontejnerů Docker:  
    https://docs.microsoft.com/azure/container-service/kubernetes/container-service-intro-kubernetes>

-   Přehled dockeru Swarm:  
    <https://docs.docker.com/swarm/overview/>

-   Přehled režimu swarm:  
    <https://docs.docker.com/engine/swarm/>

-   Přehled mesosphere DC/OS:    
    <https://docs.mesosphere.com/1.7/overview/>

-   Kubernetes (oficiální web):  
    <https://kubernetes.io/>

## <a name="using-service-fabric"></a>Pomocí Service Fabric

Service Fabric nástroji od Microsoftu pro přechod z současném dodávání produktů "pole", které byly obvykle monolitické ve stylu, k zajištění služeb. Prostředí pro sestavování a provoz velkých služeb ve velkém měřítku, jako je například Azure SQL Database, Azure Document DB, Azure Service Bus nebo back-endu asistentky Cortana ve tvaru Service Fabric. Platforma se v čase, jako další a další služby přijal. Co je důležité Service Fabric museli spouštět pouze v Azure, ale také v samostatných nasazeních systému Windows Server.

Cílem Service Fabric je řešit složité problémy sestavování a provoz služby a efektivně využívá prostředky infrastruktury tak, aby týmy mohou řešení obchodních problémů pomocí přístup založený na mikroslužbách.

Service Fabric poskytuje dva různé oblasti, které vám pomůže vytvářet aplikace, které používají přístup založený na mikroslužbách:

-   Platforma, která poskytuje služby systém nasadit, škálovat, upgradovat, zjišťovat a restartujte služby se nezdařilo, zjistit umístění služby, Správa stavu, a monitorovat stav. Tyto systémové služby platit poskytují řadu charakteristiky mikroslužeb je popsáno výše.

-   Programování v rozhraní API nebo rozhraní, které vám pomůžou vytvářet aplikace jako mikroslužeb: [reliable actors a modelu reliable services](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Samozřejmě můžete použít libovolný kód pro vytváření mikroslužeb, ale tato rozhraní API provést úlohu jednodušší a integrují s platformou na podrobnější úrovni. Tímto způsobem můžete získat stavu a diagnostické informace nebo je mohou využít výhod správy spolehlivé stavu.

Service Fabric je nezávislá s ohledem na jak vytvářet služby, a můžete použít libovolné technologii. Však nabízí integrovanou programovací rozhraní API, která usnadňují vytváření mikroslužeb.

Obrázek 4 – 9 ukazuje, jak můžete vytvořit a spouštět mikroslužby v Service Fabric, buď jako jednoduchý proces, nebo jako kontejnery Dockeru. Je také možné kombinovat mikroslužeb založených na kontejnerech s mikroslužbami založené na procesu ve stejném clusteru Service Fabric.

![](./media/image13.png)

Obrázek 4 – 9: Nasazuje mikroslužby jako procesů nebo kontejnerů v Azure Service Fabric

Clustery Service Fabric, které jsou založené na hostitele se systémy Linux a Windows můžete spouštět kontejnery Linuxu Docker a kontejnery Windows.

**Další informace o** aktuální informace o podporu kontejnerů v Service Fabric na webu Azure, přečtěte si [Service Fabric a kontejnery](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Service Fabric je typickým příkladem platformy, pomocí kterého můžete definovat jinou logickou architekturu (obchodní mikroslužby nebo ohraničených kontextech) než fyzická implementace. Například, pokud se rozhodnete implementovat [stavové služby Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) v [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), které jsou popsané v další části "[Stateless a stavových mikroslužeb](#stateless-versus-stateful-microservices), "máte koncept obchodní mikroslužeb s více službami fyzické.

Jak ukazuje obrázek 4 – 10 a přemýšlení z hlediska obchodní logiky/mikroslužeb, při implementaci služby Reliable Stateful Service Fabric je obvykle potřeba implementovat dvě úrovně služeb. První je back-end spolehlivé stavové služby, která zpracovává několik oddílů. Druhým je front-endová služba a služba brány starosti agregace směrování a data napříč několika oddíly nebo instance stavové služby. Tuto službu brány také zpracovává komunikace na straně klienta s opakování smyčky přístup k back-end služba používá ve spojení s využitím Service Fabric [reverzní proxy server](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy).

![](./media/image14.png)

Obrázek 4 – 10: Obchodní mikroslužeb s několika stavové a bezstavové služby v Service Fabric

V každém případě použijete Service Fabric stavové služby Reliable Services, máte také logické nebo obchodní mikroslužbě (objektu Context ohraničená), který se obvykle skládá z několika fyzických služeb. Každá z jejich, služba brány a oddílu služby může možné implementovat jako rozhraní ASP.NET Web API služby, jak ukazuje obrázek 4 – 10.

V Service Fabric, skupiny a nasazení skupin služeb jako [aplikace Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), což je jednotka balení a nasazení nástroje orchestrator nebo clusteru. Proto aplikace Service Fabric mapovat tento autonomní firmy a logické vyladěných hraniční nebo ohraničená kontext také.

### <a name="service-fabric-and-containers"></a>Service Fabric a kontejnery

Jde o kontejnerů v Service Fabric také můžete nasadit služby v imagí kontejnerů v clusteru Service Fabric. Obrázek 4 – 11 znázorňuje, že většina čas, kdy bude existovat pouze jeden kontejner na službu.

![](./media/image15.png)

Obrázek 4 – 11: Obchodní mikroslužeb s několika službami (kontejnerů) v Service Fabric

Kontejnery takzvané "sajdkára" (dva kontejnery, které musí být nasazeny společně jako součást logické služby) ale také možné v Service Fabric. Důležité je, že obchodní mikroslužeb je logické hranicí kolem několika získá na ucelenosti prvků. V mnoha případech může být jedinou službou s jediným datovým modelem, ale v některých případech můžete mít fyzické několik služeb a také.

V době vytváření tohoto dokumentu (duben 2017), v Service Fabric nelze nasadit SF Reliable Stateful Services v kontejnerech, můžete nasadit pouze hostované kontejnery, bezstavové služby nebo služby objektu actor v kontejnerech. Ale mějte na paměti, že je možné kombinovat služby v procesech a služby v kontejnerech ve stejné aplikaci Service Fabric, jak ukazuje obrázek 4 – 12.

![](./media/image16.png)

Obrázek 4-12: Obchodní mikroslužeb mapovány na aplikaci Service Fabric s kontejnery a stavové služby

Podpora je taky liší v závislosti na tom, zda používáte kontejnery Dockeru v Linuxu nebo kontejnery Windows. Podpora kontejnerů v Service Fabric se rozšíření v budoucích verzích. Aktuální novinky o podporu kontejnerů v Service Fabric na webu Azure, přečtěte si [Service Fabric a kontejnery](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Bezstavových a stavových mikroslužeb

Jak bylo zmíněno výše, musíte vlastnit jednotlivých mikroslužeb (logické ohraničená Context) jeho doménový model (data a logiku). V případě bezstavové mikroslužby budou databáze externí, když relační možnosti, jako je SQL Server nebo možností NoSQL, jako jsou MongoDB nebo Azure DocumentDB.

Ale vlastních služeb také může být stavový, což znamená, že jsou data uložená v rámci mikroslužbách. Tato data mohou existovat nejen na stejném serveru, ale v rámci procesu mikroslužeb v paměti, trvale se uloží na disky a replikují do dalších uzlů. Obrázek 4 – 13 ukazuje různé přístupy.

![](./media/image17.png)

Obrázek 4 – 13: Bezstavových a stavových mikroslužeb

Bezstavové přístup dokonale platný a je jednodušší než stavových mikroslužeb implementace, protože tento přístup je podobný tradiční a dobře známé vzory. Ale bezstavové mikroslužby kladou latence mezi zdroji procesy a data. Zahrnují také několik pohyblivých částí, pokud se pokoušíte zlepšení výkonu pomocí dalších mezipaměť a fronty. Výsledkem je, že můžete skončit s komplexní architektury, které mají moc úrovní.

Naproti tomu [stavových mikroslužeb](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) můžete excel v pokročilých scénářích, protože neexistuje žádný latence mezi domény logiku a data. Silná zpracování dat, herních back EndY, databáze jako služby a další scénáře s nízkou latencí všechny výhody stavové služby, které poskytují místní stavu pro rychlejší přístup.

Bezstavové a stavové služby vzájemně doplňují. Stavové služby, může rozdělit do několika oddílů. Pro přístup k těmto oddílů, může být nutné bezstavové služby, který funguje jako služba brány, která ví, jak vyřešit každý oddíl podle klíče oddílů.

Stavové služby mají nevýhody. Ukládají zjednodušit postupy, které umožňuje horizontální navýšení kapacity. Funkce, která by obvykle implementována externí databázovými systémy. je potřeba řešit pro úlohy, jako je replikace dat mezi stavových mikroslužeb a dělení dat. Ale to je jedna z oblasti, kde jako orchestrátor [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) s jeho [stavovém modelu reliable services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) může pomoct nejvíce – díky zjednodušení vývoje a životního cyklu stavová mikroslužby pomocí [Reliable Services API](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) a [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Další architektury mikroslužeb, umožňujících stavové služby, které podporují vzor objektu Actor a zlepšují odolnost proti chybám a latencí mezi obchodní logiku a data jsou Microsoft [Orleans](https://github.com/dotnet/orleans), od Microsoft Research a [ Akka.NET](https://getakka.net/). Obě architektury jsou aktuálně zlepšení jejich podpora pro Docker.

Všimněte si, že kontejnery Dockeru jsou bezstavové sami. Pokud chcete implementovat stavové služby, budete potřebovat další doporučené postupy a chcete získat podrobnější popis architektury jste si předtím poznamenali. V době psaní tohoto návodu, ale stavové služby v Service Fabric nejsou podporovány jako kontejnery, pouze jako obyčejný mikroslužeb. Služby Reliable Service podporují v kontejnerech, bude k dispozici v budoucích verzích Service Fabric.

>[!div class="step-by-step"]
>[Předchozí](soa-applications.md)
>[další](deploy-azure-kubernetes-service.md)
