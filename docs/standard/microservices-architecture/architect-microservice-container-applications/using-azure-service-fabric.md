---
title: "Pomocí Azure Service Fabric"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Pomocí Azure Service Fabric"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9480a3f67e9d0a61d0669bf34be4b66208f5e9ce
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="using-azure-service-fabric"></a>Pomocí Azure Service Fabric

Azure Service Fabric vznikly z Microsoftu pro přechod z doručování pole produkty, které byly obvykle monolitický ve stylu, k poskytování služeb. Prostředí sestavování a provoz velké služby ve velkém měřítku, jako je například Azure SQL Database, Azure Cosmos DB, Azure Service Bus nebo na webu Cortana back-end, ve tvaru Service Fabric. Platforma vyvinuly časem více služeb přijatá ho. Je důležité Service Fabric museli spustit pouze v Azure, ale také v samostatných nasazeních systému Windows Server.

Cílem Service Fabric je k vyřešení pevný problémů, sestavování a spuštěna služba a efektivně využívá prostředky infrastruktury tak, aby týmy můžete řešení obchodních problémů mikroslužeb přístup.

Service Fabric nabízí dvě obecné oblasti můžete vytvářet aplikace, které používají mikroslužeb přístup:

-   Platforma, která poskytuje systémové služby pro nasazení, škálování, upgradu, zjišťovat a restartujte služby se nezdařilo, zjistit umístění služby, Správa stavu a sledování stavu. Tyto systémové služby platí povolit mnoho společných vlastností mikroslužeb popsané.

-   Rozhraní API pro programování nebo rozhraní, můžete vytvářet aplikace, jako mikroslužeb: [spolehlivé aktéři a spolehlivé služby](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Samozřejmě můžete žádný kód k vytvoření mikroslužbu, ale tato rozhraní API proveďte úlohy více přehledné a jejich integraci s platformou na podrobnější úrovni. Tímto způsobem můžete získat stavu a diagnostické informace nebo můžete využít výhod správy spolehlivé stavu.

Service Fabric nerozlišuje s ohledem na tom, jak sestavit služby a všechny technologii můžete použít. Však poskytuje integrované programovací rozhraní API, která usnadňují sestavení mikroslužeb.

Jak ukazuje obrázek 4-26, můžete vytvořit a spustit mikroslužeb v Service Fabric jako jednoduchý procesy, nebo jako Docker kontejnery. Je také možné kombinovat na základě kontejneru mikroslužeb s na základě proces mikroslužeb ve stejném clusteru Service Fabric.

![](./media/image30.png)

**Obrázek 4-26**. Nasazení mikroslužeb jako procesy, nebo jako kontejnery v Azure Service Fabric

Service Fabric clustery založené na hostitelích se systémem Linux a Windows můžete spustit kontejnery Docker Linux a Windows kontejnery.

Aktuální informace o podpoře kontejnerů v Azure Service Fabric najdete v tématu [Service Fabric a kontejnery](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Service Fabric je dobrým příkladem platformy, kde můžete definovat různých Logická architektura (business mikroslužeb nebo ohraničenou kontexty) než fyzické implementace, které byly zavedeny v [Logická architektura versus fyzického Architektura](#logical-architecture-versus-physical-architecture) části. Například, pokud budete implementovat [stavové služby Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) v [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), které jsou popsané v části [Stateless versus stavová mikroslužeb](#stateless-versus-stateful-microservices) později může mít koncept mikroslužbu obchodní s více fyzických službami.

Jak ukazuje obrázek 4-27 a přemýšlení z hlediska logické nebo obchodní mikroslužbu při implementaci služby Fabric Stateful spolehlivě obvykle musíte implementovat dvě úrovně služeb. První je back-end stavová spolehlivá služba, která zpracovává více oddílů (každý oddíl je stavové služby). Druhá je front-endová služba, nebo služba brány starosti agregace směrování a data mezi více oddílů nebo instancí stavové služby. Tuto službu brány také obstará komunikace klienta s opakování smyčky přístupu ke službě back-end.
Pokud implementujete vlastní služby nebo alternatevely můžete také použít Service Fabric se na pole se označuje jako služba brány [Reverse Proxy služby](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy).

![](./media/image31.png)

**Obrázek 4-27**. Mikroslužbu obchodní s několika instancemi stavové služby a vlastní bránu front-endu

V každém případě při použití služby Fabric stavové služby Reliable Services, máte také logickou nebo obchodní mikroslužbu (ohraničenou kontextu), se obvykle skládá z několika fyzických služeb. Každý z jejich, služba brány a oddílu služby by se mohlo provádět jako rozhraní ASP.NET Web API služby, jak ukazuje obrázek 4-26.

V Service Fabric, skupiny a nasazení skupin služby jako [aplikace Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), což je jednotky balení a nasazení pro orchestrator nebo cluster. Proto aplikace Service Fabric mapovat tento autonomní obchodní a logické mikroslužbu hranic nebo ohraničenou kontextu, je také možné, tak může tyto služby nasadit samostatně.

## <a name="service-fabric-and-containers"></a>Service Fabric a kontejnery

S ohledem na kontejnery v Service Fabric můžete také nasadit services v kontejneru bitové kopie v rámci clusteru Service Fabric. Jak ukazuje obrázek 4-28, ve většině případů budou existovat jenom jeden kontejner pro službu.

![](./media/image32.png)

**Obrázek 4-28**. Mikroslužbu obchodní s několika služeb (kontejnerů) v Service Fabric

Kontejnery takzvané "něho" (dva kontejnery, které musí být nasazeny společně v rámci logické service) je však také možné v Service Fabric. Důležité je, že obchodní mikroslužbu není logické okolí několik získá na ucelenosti elementy. V mnoha případech může být jednu službu s jeden datový model, ale v některých jiných případech může mít také fyzické několik služeb.

Od verze mid 2017, v Service Fabric nemůžete nasadit SF spolehlivé stavové služby kontejnerům – lze nasadit pouze bezstavové služby a služby objektu actor v kontejnerech. Ale Všimněte si, že je možné kombinovat služby v procesy a služby v kontejnerech ve stejné aplikaci, Service Fabric, jak ukazuje obrázek 4-29.

![](./media/image33.png)

**Obrázek 4-29**. Mikroslužbu obchodní namapované na aplikace Service Fabric s kontejnery a stavové služby

Další informace o podpoře kontejneru v Azure Service Fabric najdete v tématu [Service Fabric a kontejnery](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Bezstavové a stavové mikroslužeb

Jak už bylo zmíněno dříve, musí každý mikroslužbu (logické ohraničenou kontextu) vlastní svůj model domény (dat a logiku). V případě bezstavové mikroslužeb bude externí zaměstnávající relační možnosti, jako je SQL Server nebo NoSQL možnosti jako MongoDB nebo Azure Cosmos DB databáze.

Ale sami služby může být také stavová v Service Fabric, což znamená, že data jsou umístěna v rámci mikroslužby. Tato data mohou existovat nejen na stejném serveru, ale v rámci procesu mikroslužbu v paměti a trvalé na pevné disky a replikované do dalších uzlů. Obrázek 4 – 30 ukazuje různý přístup.

![](./media/image34.png)

**Obrázek 4 – 30**. Bezstavové a stavové mikroslužeb

Bezstavové přístup perfektně platný a je jednodušší než stavová mikroslužeb implementace vzhledem k tomu, že je podobná tradičním a dobře známé vzorů přístupu. Ale bezstavové mikroslužeb použít latenci mezi zdroji proces a data. Taky při nich probíhá více přesunutí částí Pokud chcete zlepšit výkon s další mezipaměti a fronty. Výsledkem je, že můžou skončit s komplexní architektury, které mají příliš mnoho úrovní.

Naproti tomu [stavová mikroslužeb](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) můžete v aplikaci excel v pokročilých scénářích, protože neexistuje žádný latenci mezi domény logiku a data. Velkou zpracování dat, hry zpět skončí, databáze jako služba, a všechny scénáře s nízkou latencí využívat stavové služby, které Povolit místní stav pro rychlejší přístup.

Bezstavové a stavové služby jsou vzájemně doplňují. Například se zobrazí obrázek 4 – 30 v pravém diagramu, že stavové služby může rozdělit do několika oddílů. Přístup k tyto oddíly, budete pravděpodobně potřebovat bezstavové služby, který funguje jako brána službu, která umí adres každý oddíl podle klíče oddílů.

Stavové služby mají nevýhody. Úroveň složitosti, která umožňuje škálování, jež ukládají. Funkce, které by obvykle implementována systémy externí databáze je potřeba řešit pro úlohy, jako je například replikace dat mezi stavová mikroslužeb a data rozdělení do oddílů. To je však jeden z oblastí, kde orchestrator jako [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) s jeho [stavová spolehlivé služby](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) může pomoci nejvíce – tím, že zjednodušuje vývoj a životního cyklu stateful pomocí mikroslužeb [spolehlivé rozhraní API služby](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) a [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Ostatní mikroslužbu platformy, které umožňují stavové služby, které podporují vzor objektu Actor a zlepšují odolnost proti chybám a latence mezi obchodní logiku a data jsou Microsoft [Orléans](https://github.com/dotnet/orleans), z Microsoft Research a [ Akka.NET](http://getakka.net/). Obě architektury jsou aktuálně zlepšení jejich podpora pro Docker.

Upozorňujeme, že jsou kontejnery Docker bezstavové sami. Pokud chcete implementovat stavové služby, musíte další doporučený a vyšší úrovně rozhraní si předtím poznamenali. 

>[!div class="step-by-step"]
[Předchozí] (scalable-available-multi-container-microservice-applications.md) [Další] (.. /docker-Application-Development-Process/index.MD)
