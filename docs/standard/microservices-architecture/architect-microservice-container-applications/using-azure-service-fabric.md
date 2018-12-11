---
title: Pomocí Azure Service Fabric
description: Zjistěte, jaké modely aplikace Azure Service Fabric můžete kromě identifikace podle představuje pro orchestraci kontejnerů.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: b29be05f5ab353ddfae0d23211efaf57979d0604
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53126962"
---
# <a name="using-azure-service-fabric"></a>Pomocí Azure Service Fabric

Azure Service Fabric nástroji od Microsoftu pro přechod z současném dodávání produktů pole, které byly obvykle monolitické ve stylu, k zajištění služeb. Prostředí pro sestavování a provoz velkých služeb ve velkém měřítku, jako je například Azure SQL Database, Azure Cosmos DB, Azure Service Bus nebo asistentky Cortana back-endu, ve tvaru Service Fabric. Platforma se v čase, jako další a další služby přijal. Co je důležité Service Fabric museli spouštět pouze v Azure, ale také v samostatných nasazeních systému Windows Server.

Cílem Service Fabric je řeší těžké problémy sestavování a provoz služby a efektivně využívá prostředky infrastruktury tak, aby týmy mohou řešení obchodních problémů pomocí přístup založený na mikroslužbách.

Service Fabric poskytuje dva různé oblasti, které vám pomůže vytvářet aplikace, které používají přístup založený na mikroslužbách:

- Platforma, která poskytuje služby systém nasadit, škálovat, upgradovat, zjišťovat a restartujte služby se nezdařilo, zjistit umístění služby, Správa stavu, a monitorovat stav. Tyto systémové služby platit přinášejí mnohé z charakteristiky mikroslužeb je popsáno výše.

- Programování v rozhraní API nebo rozhraní, které vám pomůžou vytvářet aplikace jako mikroslužeb: [reliable actors a modelu reliable services](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Můžete použít libovolný kód pro vytváření mikroslužeb, ale tato rozhraní API provést úlohu jednodušší a integrují s platformou na podrobnější úrovni. Tímto způsobem můžete získat stavu a diagnostické informace nebo je mohou využít výhod správy spolehlivé stavu.

Service Fabric je nezávislá s ohledem na jak vytvářet služby, a můžete použít libovolné technologii. Však nabízí integrovanou programovací rozhraní API, která usnadňují vytváření mikroslužeb.

Jak ukazuje obrázek 4 – 27, můžete vytvořit a spouštět mikroslužby v Service Fabric, buď jako jednoduchý proces, nebo jako kontejnery Dockeru. Je také možné kombinovat mikroslužeb založených na kontejnerech s mikroslužbami založené na procesu ve stejném clusteru Service Fabric.

![Porovnání služby Azure service Fabric clustery: Mikroslužby jako proces, ve kterém každý uzel spuštěná jeden proces u jednotlivých mikroslužeb; Jako kontejnery, ve kterém každý uzel spuštěná Dockeru s několika kontejnery, Mikroslužby jednoho kontejneru na mikroslužbách.](./media/image30.png)

**Obrázek 4 – 27**. Nasazuje mikroslužby jako procesů nebo kontejnerů v Azure Service Fabric

Clustery Service Fabric, které jsou založené na hostitele se systémy Linux a Windows můžete spouštět kontejnery Linuxu Docker a kontejnery Windows.

Aktuální informace o podpoře kontejnery v Azure Service Fabric najdete v tématu [Service Fabric a kontejnery](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Service Fabric je typickým příkladem platformy, ve kterém můžete definovat jinou logickou architekturu (obchodní mikroslužby nebo ohraničených kontextech) než fyzická implementace, které byly zavedeny v [Logická architektura versus fyzická Architektura](logical-versus-physical-architecture.md) oddílu. Například, pokud se rozhodnete implementovat [stavové služby Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction), které jsou popsané v části [Stateless a stavových mikroslužeb](#stateless-versus-stateful-microservices) později, může mít koncept obchodní mikroslužeb s více fyzických služeb.

Jak ukazuje obrázek 4 – 28 a přemýšlení z hlediska obchodní logiky/mikroslužeb, při implementaci služby Reliable Stateful Service Fabric je obvykle potřeba implementovat dvě úrovně služeb. První je back-end spolehlivé stavové služby, která zpracovává více oddílů (každý oddíl se stavovou službou). Druhým je front-endová služba a služba brány starosti agregace směrování a data napříč několika oddíly nebo instance stavové služby. Tuto službu brány také zpracovává komunikace na straně klienta s opakování smyčky přístup k back-end služby. Pokud implementujete vlastní službu, nebo také můžete použít také out-of-the-box Service Fabric se používá označení služba brány [reverzní proxy server](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy).

![](./media/image31.png)

**Obrázek 4 – 28**. Obchodní mikroslužeb s několika instancemi stavové služby a vlastní bránu front-endu

V každém případě použijete Service Fabric stavové služby Reliable Services, máte také logické nebo obchodní mikroslužbě (objektu Context ohraničená), který se obvykle skládá z několika fyzických služeb. Každá je služba brány, oddílu služby může možné implementovat jako rozhraní ASP.NET Web API služby, jak ukazuje obrázek 4 – 28.

V Service Fabric, skupiny a nasazení skupin služeb jako [aplikace Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), což je jednotka balení a nasazení nástroje orchestrator nebo clusteru. Proto aplikace Service Fabric může být mapována na tento autonomní obchodní a logické vyladěných hraniční nebo ohraničená kontext, tak můžete nasadit tyto služby samostatně.

## <a name="service-fabric-and-containers"></a>Service Fabric a kontejnery

Jde o kontejnerů v Service Fabric můžete taky nasadit služby v imagí kontejnerů v clusteru Service Fabric. Jak ukazuje obrázek 4 – 29, ve většině případů bude existovat jenom jeden kontejner na službu.

![Aplikace Service Fabric můžete spustit několik kontejnerů přístup k databázi extern a celé sady by logické hranic Mikroslužby firmy](./media/image32.png)

**Obrázek 4 – 29**. Obchodní mikroslužeb s několika službami (kontejnerů) v Service Fabric

Kontejnery takzvané "sajdkára" (dva kontejnery, které musí být nasazeny společně jako součást logické služby) ale také možné v Service Fabric. Důležité je, že obchodní mikroslužeb je logické hranicí kolem několika získá na ucelenosti prvků. V mnoha případech může být jedinou službou s jediným datovým modelem, ale v některých případech můžete mít i několik fyzických služeb.

Jak ukazuje obrázek 4-30, mějte na paměti, že je možné kombinovat služby v procesech a služby v kontejnerech ve stejné aplikaci Service Fabric.

![Aplikace Service Fabric s služeb a kontejnerů ve stejném uzlu.](./media/image33.png)

**Obrázek 4-30**. Obchodní mikroslužeb mapovány na aplikaci Service Fabric s kontejnery a stavové služby

Další informace o podporu kontejnerů v Azure Service Fabric najdete v tématu [Service Fabric a kontejnery](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Bezstavových a stavových mikroslužeb

Jak bylo zmíněno výše, musíte vlastnit jednotlivých mikroslužeb (logické ohraničená Context) jeho doménový model (data a logiku). V případě bezstavové mikroslužby budou databáze externí, když relační možnosti, jako je SQL Server nebo možností NoSQL, jako jsou služby Azure Cosmos DB nebo MongoDB.

Ale vlastních služeb může být také stavové v Service Fabric, což znamená, že jsou data uložená v rámci mikroslužbách. Tato data mohou existovat nejen na stejném serveru, ale v rámci procesu mikroslužeb v paměti a trvale se uloží na pevné disky a replikují do dalších uzlů. Obrázek 4-30 ukazuje různé přístupy.

![Bezstavové služby stavu (trvalost, databáze), zůstane mimo mikroslužbách. Stavové služby jsou státy průběžně uvnitř mikroslužbách.](./media/image34.png)

**Obrázek 4-31**. Bezstavových a stavových mikroslužeb

Bezstavové přístup dokonale platný a je jednodušší než stavových mikroslužeb, protože tento přístup je podobná tradičním a dobře známé vzory implementace. Ale bezstavové mikroslužby kladou latence mezi zdroji procesy a data. Zahrnují také několik pohyblivých částí, když se snažíte zlepšení výkonu pomocí dalších mezipaměť a fronty. Výsledkem je, že můžete skončit s komplexní architektury, které mají moc úrovní.

Naproti tomu [stavových mikroslužeb](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) může aplikace excel v pokročilých scénářích, protože neexistuje žádný latence mezi domény logiku a data. Silná zpracování dat, hraní her zpět ukončí, databáze jako služba, a další scénáře s nízkou latencí všechny výhody stavové služby, které umožňují rychlejší přístup k místním stavu.

Bezstavové a stavové služby vzájemně doplňují. Například se zobrazí obrázek 4-31 v pravém diagram stavové služby, může rozdělit na několik oddílů. Pro přístup k těmto oddílů, může být nutné bezstavové služby, který funguje jako služba brány, která ví, jak vyřešit každý oddíl podle klíče oddílů.

Stavové služby mají nevýhody. Ukládají zjednodušit postupy, které umožňuje horizontální navýšení kapacity. Funkce, která by obvykle implementována externí databázovými systémy. je potřeba řešit pro úlohy, jako je replikace dat mezi stavových mikroslužeb a dělení dat. Ale to je jedna z oblasti, kde jako orchestrátor [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) s jeho [stavovém modelu reliable services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) může pomoct nejvíce – díky zjednodušení vývoje a životního cyklu stavová mikroslužby pomocí [Reliable Services API](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) a [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Další architektury mikroslužeb, umožňujících stavové služby, které podporují vzor objektu Actor a zlepšují odolnost proti chybám a latencí mezi obchodní logiku a data jsou Microsoft [Orleans](https://github.com/dotnet/orleans), od Microsoft Research a [ Akka.NET](https://getakka.net/). Obě architektury jsou aktuálně zlepšení jejich podpora pro Docker.

Všimněte si, že kontejnery Dockeru jsou bezstavové sami. Pokud chcete implementovat stavové služby, budete potřebovat další doporučené postupy a chcete získat podrobnější popis architektury jste si předtím poznamenali.

## <a name="using-azure-service-fabric-mesh"></a>Pomocí sítě Azure Service Fabric 

Sítě Azure Service Fabric je plně spravovaná služba, která umožňuje vývojářům umožníte sestavovat a nasazovat nejdůležitější aplikace bez nutnosti spravovat žádnou infrastrukturu. Pomocí sítě pro Service Fabric můžete vytvářet a spouštět aplikace zabezpečené a distribuovaných mikroslužeb, které se škálují na vyžádání. 

Jak je znázorněno na obrázku 4-32, aplikacemi hostovanými na služby prostředků infrastruktury sítě spouštění a škálování bez starostí o infrastrukturu ukončit.

![Vícekontejnerových aplikací běžící v desktopu Dockeru je nasadit do Azure Service Fabric sítě bez starostí o infrastrukturu.](media/image39.png)

**Obrázek 4 – 32**. Nasazení aplikace mikroslužeb a kontejnerů do Service Fabric mřížky

Pod pokličkou sítě pro Service Fabric se skládá z clusterů tisíce počítačů. Všechny operace clusteru jsou skryté od vývojáře. Stačí nahrát kontejnery a zadejte prostředky, které potřebujete, požadavky na dostupnost a limity prostředků. Service Fabric sítě automaticky přiděluje infrastruktury požadoval nasazení vaší aplikace a také zpracovává selhání infrastruktury, ujistěte se, že jsou vaše aplikace s vysokou dostupností. Stačí vám jde o stavu a rychlost reakce aplikace, ne na infrastrukturu.

Další informace najdete v článku [dokumentace ke službě Service Fabric mřížky](https://docs.microsoft.com/azure/service-fabric-mesh/).

## <a name="choosing-orchestrators-in-azure"></a>Výběr orchestrátorů v Azure

Následující tabulka obsahuje pokyny k jaké orchestrator, která umožní použít v závislosti na úlohy a operačního systému fokus.

![Služby Azure Kubernetes je vyspělejší v Linuxu než ve Windows a se většinou používá pro nasazení microsevices založené na kontejnerech. Azure Service Fabric (cluster a sítě) je vyspělejší ve Windows než v systému Linux, běžně používá pro mikroslužby podle kontejnery, mikroslužby, na základě jednoduché procesy a stavové služby.](media/image40.png)

**Obrázek 4-33**. Výběr nástroje Orchestrator v doprovodné materiály k Azure

>[!div class="step-by-step"]
>[Předchozí](scalable-available-multi-container-microservice-applications.md)
>[další](../docker-application-development-process/index.md)