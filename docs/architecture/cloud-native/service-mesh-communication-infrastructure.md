---
title: Komunikační infrastruktura Service Mesh
description: Přečtěte si, jak technologie sítě sítě zefektivňují komunikaci mikroslužeb v cloudu.
author: robvet
ms.date: 03/03/2020
ms.openlocfilehash: 89bc4d307d725e7e31e020ef156c4c5967dd2a1c
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199941"
---
# <a name="service-mesh-communication-infrastructure"></a>Komunikační infrastruktura Service Mesh

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

V rámci této kapitoly jsme prozkoumali problémy s komunikací mikroslužeb. Zjistili jsme, že vývojové týmy musí být citlivé na to, jak vzájemně komunikují služby back-end. V ideálním případě je to lepší komunikace mezi službami. Vyloučení ale není vždycky možné, protože back-endové služby se obvykle vzájemně spoléhá na to, že se operace dokončí.

Prozkoumali jsme různé přístupy k implementaci synchronní komunikace HTTP a asynchronního zasílání zpráv. V každém z těchto případů je vývojář zatížen implementací komunikačního kódu. Kód komunikace je složitý a časově náročný. Nesprávná rozhodnutí mohou vést k významným problémům s výkonem.

Moderní přístup k komunikačním centrům mikroslužeb kolem nové a rychle se vyvíjející technologie s názvem *síť*. [Síť](https://www.nginx.com/blog/what-is-a-service-mesh/) je konfigurovatelná vrstva infrastruktury s integrovanými možnostmi pro zpracování komunikace mezi službami, odolnosti a mnoha různých otázek. Přesune zodpovědnost za tyto otázky z mikroslužeb a do vrstvy sítě. Komunikace je z vašich mikroslužeb abstraktní.

Klíčovou součástí sítě je proxy. V nativní aplikaci pro Cloud je instance proxy obvykle společně umístěná u každé mikroslužby. I když se spouštějí v samostatných procesech, jsou tyto dva úzce propojené a sdílejí stejný životní cyklus. Tento model, známý jako [vzorek postranního vozíku](https://docs.microsoft.com/azure/architecture/patterns/sidecar), je zobrazen na obrázku 4-24.

![Síť s postranním vozíkem](./media/service-mesh-with-side-car.png)

**Obrázek 4-24**. Síť s postranním vozíkem

Všimněte si na předchozím obrázku, jak jsou zprávy zachyceny proxy serverem, který se souběžně používá v rámci každé mikroslužby. Jednotlivé proxy servery je možné nakonfigurovat s pravidly přenosů, které jsou specifické pro mikroslužby. Chápe zprávy a můžou je směrovat mezi vaše služby a vnějším světem.

Spolu se správou komunikace mezi službami zajišťuje služba síť podporu zjišťování služeb a vyrovnávání zatížení.

Po nakonfigurování je síť velmi funkční. Síť načte odpovídající fond instancí z koncového bodu zjišťování služby. Pošle požadavek na konkrétní instanci služby, která zaznamená latenci a typ odpovědi pro výsledek. Zvolí instanci, která pravděpodobně vrátí rychlou odpověď na základě různých faktorů, včetně pozorované latence pro poslední požadavky.

Síť zajišťuje provoz, komunikaci a problémy se sítí na úrovni aplikace. Pochopení zpráv a požadavků. Síť se obvykle integruje s nástrojem Orchestrator kontejneru. Kubernetes podporuje rozšiřitelnou architekturu, ve které lze přidat síť služby.

V kapitole 6 jsme podrobně na technologie sítě, včetně diskuzí o architektuře a dostupných Open Source implementací.

## <a name="summary"></a>Souhrn

V této kapitole jsme probrali vzory komunikace v cloudu Native. Začali jsme zkoumat, jak klienti front-end komunikují s back-end mikroslužbami. Mluvili se na platformě rozhraní API Gateway a na komunikaci v reálném čase. Pak jsme si prohlédli, jak mikroslužby komunikují s jinými back-endové službami. Vyhledali jsme synchronní komunikaci HTTP i asynchronní zasílání zpráv napříč službami. Pokryli jsme gRPC, nadcházející technologii v cloudu Native World. Nakonec jsme zavedli novou a rychle se vyvíjející technologii, která může zjednodušit komunikaci mikroslužeb.

Speciální důraz byl na spravované služby Azure, které můžou přispět k implementaci komunikace v systémech nativních pro Cloud:

- [Azure Application Gateway](https://docs.microsoft.com/azure/application-gateway/overview)
- [Azure API Management](https://azure.microsoft.com/services/api-management/)
- [Služba Azure SignalR](https://azure.microsoft.com/services/signalr-service/)
- [Fronty Azure Storage](https://docs.microsoft.com/azure/storage/queues/storage-queues-introduction)
- [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)
- [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview)
- [Azure Event Hub](https://azure.microsoft.com/services/event-hubs/)

Dál jsme přešli na distribuovaná data v systémech nativních pro Cloud a na výhody a výzvy, které prezentují.

### <a name="references"></a>Odkazy

- [Mikroslužby .NET: architektura pro kontejnerové aplikace .NET](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [Návrh komunikace mezi službami pro mikroslužby](https://docs.microsoft.com/azure/architecture/microservices/design/interservice-communication)

- [Služba signalizace Azure, plně spravovaná služba pro přidání funkcí v reálném čase](https://azure.microsoft.com/blog/azure-signalr-service-a-fully-managed-service-to-add-real-time-functionality/)

- [Kontroler příchozího přenosu brány API Azure](https://azure.github.io/application-gateway-kubernetes-ingress/)

- [Informace o příchozím přenosu ve službě Azure Kubernetes (AKS)](https://vincentlauzon.com/2018/10/10/about-ingress-in-azure-kubernetes-service-aks/)

- [Dokumentace k gRPC](https://grpc.io/docs/guides/)

- [gRPC pro vývojáře WCF](https://docs.microsoft.com/dotnet/architecture/grpc-for-wcf-developers/)

- [Porovnávání služeb gRPC s rozhraními API HTTP](https://docs.microsoft.com/aspnet/core/grpc/comparison?view=aspnetcore-3.0)

- [Vytváření gRPC služeb pomocí videa .NET](https://channel9.msdn.com/Shows/The-Cloud-Native-Show/Building-Microservices-with-gRPC-and-NET)

>[!div class="step-by-step"]
>[Předchozí](grpc.md)
>[Další](distributed-data.md)
