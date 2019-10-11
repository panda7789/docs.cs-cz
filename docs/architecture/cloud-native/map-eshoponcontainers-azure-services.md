---
title: Mapování aplikace eShopOnContainers ke službám Azure
description: Mapování eShopOnContainers na služby Azure, jako je služba Azure Kubernetes, brána API a Azure Service Bus.
ms.date: 06/30/2019
ms.openlocfilehash: 67430da18c0a12c694426214de33e85c2113e454
ms.sourcegitcommit: 992f80328b51b165051c42ff5330788627abe973
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2019
ms.locfileid: "72275814"
---
# <a name="mapping-eshoponcontainers-to-azure-services"></a>Mapování aplikace eShopOnContainers ke službám Azure

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

I když to není nutné, Azure je vhodný pro podporu eShopOnContainers, protože projekt byl sestaven jako cloudová nativní aplikace. Aplikace je sestavená pomocí .NET Core, takže ji můžete spustit na kontejnerech Linux nebo Windows v závislosti na hostiteli Docker. Aplikace se skládá z několika autonomních mikroslužeb, z nichž každá má vlastní data. Různé mikroslužby prezentují různé přístupy od jednoduchých operací CRUD až po složitější a CQRS vzory. Mikroslužby komunikují s klienty přes protokol HTTP a vzájemně komunikují prostřednictvím komunikace založené na zprávách. Aplikace podporuje také více platforem pro klienty, protože přijímá protokol HTTP jako standardní komunikační protokol a zahrnuje ASP.NET Core a Xamarin Mobile Apps, které běží na platformách Android, iOS a Windows.

Architektura aplikace se zobrazuje na obrázku 2-5. Na levé straně jsou klientské aplikace rozdělené na mobilní, tradiční web a charakter SPA (Web Single Page Application). Na pravé straně jsou serverové komponenty, které tvoří systém, z nichž každý je možné hostovat v kontejnerech Docker a clusterech Kubernetes. Tradiční webová aplikace se používá v aplikaci ASP.NET Core MVC zobrazené žlutě. Tato aplikace a mobilní a webové aplikace SPA komunikují s jednotlivými mikroslužbami přes jednu nebo více bran rozhraní API. Brány rozhraní API se řídí vzorem "back-endy pro front-endy" (BFF), což znamená, že každá brána je navržená tak, aby podporovala daného klienta front-endu. Jednotlivé mikroslužby jsou uvedeny napravo od bran rozhraní API a zahrnují obchodní logiku i určitý druh trvalého úložiště. Různé služby využívají SQL Server databáze, instance mezipaměti Redis a úložiště MongoDB/CosmosDB. Úplně vpravo je systémová sběrnice událostí, která se používá ke komunikaci mezi mikroslužbami.

![eShopOnContainers architektura @ no__t-1**obrázek 2-5**. Architektura eShopOnContainers

Komponenty na straně serveru této architektury jsou snadno namapovány na služby Azure.

## <a name="container-orchestration-and-clustering"></a>Orchestrace kontejnerů a clusteringu

Služba Azure Kubernetes Service (AKS) může hostovat a spravovat služby hostované v kontejnerech, od ASP.NET Core aplikací MVC až po jednotlivé katalogy a objednávání mikroslužeb. Aplikace může běžet místně v Docker a Kubernetes a stejné kontejnery pak můžete nasadit do pracovních a produkčních prostředí hostovaných v AKS. Tento proces může být automatizovaný, protože se zobrazí v další části.

AKS poskytuje služby správy pro jednotlivé clustery kontejnerů. Aplikace bude nasazovat samostatné clustery AKS pro jednotlivé mikroslužby zobrazené v diagramu architektury výše. Díky tomuto přístupu se jednotlivé služby můžou nezávisle škálovat podle svých požadavků na prostředky. Jednotlivé mikroslužby je také možné nasadit nezávisle a v ideálním případě taková nasazení by měla způsobit nulové výpadky systému.

## <a name="api-gateway"></a>Brána API

Aplikace eShopOnContainers má několik front-end klientů a několik různých služeb back-end. Mezi klientskými aplikacemi a mikroslužbami, které je podporují, neexistuje žádná korespondence 1:1. V takovém scénáři může být složité složitosti při psaní klientského softwaru do rozhraní s různými back-end službami zabezpečeným způsobem. Každý klient by musel tuto složitost řešit vlastními, výsledkem je duplikace a celá řada míst, kde můžete aktualizovat změny služeb, nebo jsou implementovány nové zásady.

Azure API Management (APIM) pomáhá organizacím publikovat rozhraní API konzistentním, spravovatelným způsobem. APIM se skládá ze tří součástí: brány rozhraní API a portálu pro správu (Azure Portal) a portálu pro vývojáře.

Brána API přijímá volání rozhraní API a směruje je do příslušného back-endu rozhraní API. Může také poskytovat další služby, jako je ověřování klíčů rozhraní API nebo tokenů JWT a transformace rozhraní API, bez úprav kódu (například pro uspokojení klientů, které očekávají starší rozhraní).

Azure Portal je místo, kde definujete schéma rozhraní API a zabalíte různá rozhraní API do produktů. Můžete také nakonfigurovat přístup uživatelů, zobrazit sestavy a nakonfigurovat zásady pro kvóty nebo transformace.

Portál pro vývojáře slouží jako hlavní prostředek pro vývojáře. Poskytuje vývojářům dokumentaci k rozhraní API, interaktivní konzolu testu a sestavy o jejich použití. Vývojáři také portál používají k vytváření a správě vlastních účtů, včetně podpory předplatného a klíčů rozhraní API.

Pomocí APIM můžou aplikace vystavovat několik různých skupin služeb, z nichž každý poskytuje back-end pro konkrétního klienta front-endu. APIM se doporučuje u složitých scénářů. Pro zjednodušení potřeb lze použít zjednodušenou bránu rozhraní API Ocelot. Aplikace eShopOnContainers používá Ocelot z důvodu zjednodušení a protože ji lze nasadit do stejného prostředí aplikace jako samotnou aplikaci. [Přečtěte si další informace o eShopOnContainers, APIM a Ocelot.](https://docs.microsoft.com/dotnet/architecture/microservices/architect-microservice-container-applications/direct-client-to-microservice-communication-versus-the-api-gateway-pattern#azure-api-management)

Další možností, pokud vaše aplikace používá AKS, je nasazení řadiče pro příchozí přenos dat služby Azure Gateway jako pod clusterem AKS. To umožňuje, aby se cluster integroval s Application Gateway Azure, což umožňuje, aby brána vyrovnala zatížení v AKS luskech. [Přečtěte si další informace o řadiči Azure Gateway pro příchozí přenosy pro AKS](https://github.com/Azure/application-gateway-kubernetes-ingress).

## <a name="data"></a>Data

Různé back-endové služby, které používá eShopOnContainers, mají různé požadavky na úložiště. SQL Server databází používá několik mikroslužeb. Mikroslužba košíku využívá pro svůj trvalost mezipaměť Redis Cache. Mikroslužba umístění očekává pro svá data rozhraní MongoDB API. Azure podporuje jednotlivé formáty dat.

V případě podpory databáze SQL Server má Azure produkty pro všechno od samostatných databází až po vysoce škálovatelné SQL Database elastické fondy. Jednotlivé mikroslužby je možné nakonfigurovat tak, aby se rychle a snadno komunikovaly s vlastními SQL Server databázemi. Tyto databáze je možné škálovat podle potřeby, aby podporovaly jednotlivé samostatné mikroslužby podle svých potřeb.

Aplikace eShopOnContainers ukládá aktuální nákupní košík uživatele mezi požadavky. Toto je spravováno mikroslužbou košíku, která ukládá data do mezipaměti Redis Cache. Ve vývoji se tato mezipaměť dá nasadit do kontejneru, zatímco v produkčním prostředí může využít Azure cache pro Redis. Azure cache pro Redis je plně spravovaná služba, která nabízí vysoký výkon a spolehlivost, aniž by bylo potřeba nasazovat a spravovat Redis instance nebo kontejnery sami.

Mikroslužba umístění používá pro svůj trvalost databázi MongoDB NoSQL. Během vývoje se databáze dá nasadit do vlastního kontejneru, zatímco v produkčním prostředí může využít [rozhraní API Azure Cosmos DB pro MongoDB](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction). Jednou z výhod Azure Cosmos DB je schopnost využít více různých komunikačních protokolů, včetně rozhraní SQL API a běžných rozhraní NoSQL API, včetně MongoDB, Cassandra, Gremlin a Azure Table Storage. Azure Cosmos DB nabízí plně spravovanou a globálně distribuovanou databázi jako službu, která se může škálovat tak, aby splňovala potřeby služeb, které ji používají.

Distribuovaná data v nativních aplikacích cloudu jsou podrobněji popsaná v [kapitole 5](distributed-data.md).

## <a name="event-bus"></a>Sběrnice událostí

Aplikace používá události ke komunikaci mezi různými službami. Tato funkce se dá implementovat s různými implementacemi a místně aplikace eShopOnContainers používá [RabbitMQ](https://www.rabbitmq.com/). Při hostování v Azure bude aplikace [Azure Service Bus](https://docs.microsoft.com/azure/service-bus/) pro své zprávy využívat. Azure Service Bus je plně spravovaný zprostředkovatel integračních zpráv, který umožňuje aplikacím a službám vzájemně komunikovat v odděleném a spolehlivém asynchronním způsobu. Azure Service Bus podporuje jednotlivé fronty a také samostatná *témata* pro podporu scénářů pro předplatitele vydavatelů. Aplikace eShopOnContainers by mohla využít témata, která Azure Service Bus k podpoře distribuce zpráv z jedné mikroslužby do jakékoli jiné mikroslužby, která je potřeba k reakci na danou zprávu.

## <a name="resiliency"></a>Odolnost

Po nasazení do produkčního prostředí by aplikace eShopOnContainers mohla využívat několik služeb Azure, které jsou k dispozici pro zlepšení jeho odolnosti. Aplikace zveřejňuje kontroly stavu, které je možné integrovat s Application Insights, aby poskytovala sestavy a výstrahy na základě dostupnosti aplikace. Prostředky Azure také poskytují diagnostické protokoly, které se dají použít k identifikaci a opravě chyb a problémů s výkonem. Protokoly prostředků poskytují podrobné informace o tom, kdy a jak aplikace používá různé prostředky Azure. V [kapitole 6](resiliency.md)se dozvíte víc o funkcích odolnosti nativního cloudu.

## <a name="references"></a>Odkazy

- [Architektura eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Architecture)
- [Orchestrace mikroslužeb a vícekontejnerových aplikací pro vysokou škálovatelnost a dostupnost](https://docs.microsoft.com/dotnet/architecture/microservices/architect-microservice-container-applications/scalable-available-multi-container-microservice-applications)
- [API Management Azure](https://docs.microsoft.com/azure/api-management/api-management-key-concepts)
- [Přehled Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview)
- [Mezipaměť Azure pro Redis](https://azure.microsoft.com/services/cache/)
- [Rozhraní API pro MongoDB Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction)
- [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)
- [Přehled Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview)

>[!div class="step-by-step"]
>[Předchozí](introduce-eshoponcontainers-reference-app.md)
>[Další](deploy-eshoponcontainers-azure.md)
