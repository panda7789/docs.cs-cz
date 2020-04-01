---
title: Komunikační infrastruktura Service Mesh
description: Informace o tom, jak technologie sítě služeb zjednodušují komunikaci mikroslužeb nativní pro cloud
author: robvet
ms.date: 03/03/2020
ms.openlocfilehash: 6b177ef33b804ec35f3acb919539a97683e5a487
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523524"
---
# <a name="service-mesh-communication-infrastructure"></a>Komunikační infrastruktura Service Mesh

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

V této kapitole jsme prozkoumali výzvy mikroslužeb komunikace. Řekli jsme, že vývojové týmy musí být citlivé na to, jak back-end služby vzájemně komunikují. V ideálním případě, čím méně meziútvarové komunikace, tím lépe. Vyhýbání se však není vždy možné, protože back-endové služby se často spoléhají na sebe navzájem k dokončení operací.

Prozkoumali jsme různé přístupy pro implementaci synchronní HTTP komunikace a asynchronní zasílání zpráv. V každém z případů je vývojář zatížen implementačním komunikačním kódem. Komunikační kód je složitý a časově náročný. Nesprávná rozhodnutí mohou vést k významným problémům s výkonem.

Modernější přístup ke komunikaci mikroslužeb se točí kolem nové a rychle se vyvíjející technologie s názvem *Service Mesh*. [Síť služeb](https://www.nginx.com/blog/what-is-a-service-mesh/) je konfigurovatelná vrstva infrastruktury s integrovanými funkcemi pro zpracování komunikace mezi službami, odolnosti proti chybám a mnoha průřezovým problémům. Přesune odpovědnost za tyto obavy z mikroslužeb a do vrstvy sítě služby. Komunikace je abstrahována od mikroslužeb.

Klíčovou součástí sítě služby je proxy server. V aplikaci nativní pro cloud je instance proxy obvykle umístěna společně s každou mikroslužbou. Zatímco oni provádějí v samostatných procesech, dva jsou úzce propojeny a sdílejí stejný životní cyklus. Tento vzor, známý jako [vzor postranního vah](https://docs.microsoft.com/azure/architecture/patterns/sidecar), a je znázorněn na obrázku 4-24.

![Servisní síť s postranním vozem](./media/service-mesh-with-side-car.png)

**Obrázek 4-24**. Servisní síť s postranním vozem

Všimněte si na předchozím obrázku, jak jsou zprávy zachyceny proxy serverem, který běží vedle každé mikroslužby. Každý proxy server lze nakonfigurovat s pravidly provozu specifickými pro mikroslužbu. Rozumí zprávám a může je směrovat napříč vašimi službami a okolním světem.

Spolu se správou komunikace mezi službami poskytuje síť service mesh podporu pro zjišťování služeb a vyrovnávání zatížení.

Po konfiguraci je síť služby vysoce funkční. Síť načte odpovídající fond instancí z koncového bodu zjišťování služby. Odešle požadavek na konkrétní instanci služby a zaznapí na latenci a typ odpovědi výsledku. Vybere instanci s největší pravděpodobností vrátí rychlou odpověď na základě různých faktorů, včetně pozorované latence pro poslední požadavky.

Síť služeb spravuje problémy s provozem, komunikací a sítí na úrovni aplikace. Rozumí zprávám a požadavkům. Síť služeb se obvykle integruje s orchestrátorem kontejneru. Kubernetes podporuje rozšiřitelnou architekturu, ve které lze přidat síť služeb.

V kapitole 6 se podrobně zabýváme technologiemi Service Mesh, včetně diskuse o její architektuře a dostupných implementacích s otevřeným zdrojovým kódem.

## <a name="summary"></a>Souhrn

V této kapitole jsme diskutovali o vzorcích komunikace nativní pro cloud. Začali jsme zkoumáním toho, jak klienti front-endu komunikují s back-endovými mikroslužbami. Cestou jsme mluvili o platformách API Gateway a komunikaci v reálném čase. Pak jsme se podívali na to, jak mikroslužby komunikují s jinými back-endovými službami. Podívali jsme se na synchronní http komunikaci a asynchronní zasílání zpráv napříč službami. Pokryli jsme gRPC, nadcházející technologii v cloudově rodném světě. Nakonec jsme zavedli novou a rychle se vyvíjející technologii s názvem Service Mesh, která může zefektivnit komunikaci mikroslužeb.

Zvláštní důraz byl kladen na spravované služby Azure, které můžou pomoct implementovat komunikaci v cloudových nativních systémech:

- [Azure Application Gateway](https://docs.microsoft.com/azure/application-gateway/overview)
- [Azure API Management](https://azure.microsoft.com/services/api-management/)
- [Služba Azure SignalR](https://azure.microsoft.com/services/signalr-service/)
- [Fronty Azure Storage](https://docs.microsoft.com/azure/storage/queues/storage-queues-introduction)
- [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)
- [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview)
- [Azure Event Hub](https://azure.microsoft.com/services/event-hubs/)

Dále se přesuneme k distribuovaným datům v systémech nativních na cloud a k výhodám a výzvám, které představuje.

### <a name="references"></a>Odkazy

- [.NET Microservices: Architektura pro kontejnerizované aplikace .NET](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [Návrh meziútvarové komunikace pro mikroslužby](https://docs.microsoft.com/azure/architecture/microservices/design/interservice-communication)

- [Azure SignalR Service, plně spravovaná služba pro přidání funkcí v reálném čase](https://azure.microsoft.com/blog/azure-signalr-service-a-fully-managed-service-to-add-real-time-functionality/)

- [Řadič příchozího přenosu brány rozhraní Azure API](https://azure.github.io/application-gateway-kubernetes-ingress/)

- [O příchozím přenosu dat ve službě Azure Kubernetes Service (AKS)](https://vincentlauzon.com/2018/10/10/about-ingress-in-azure-kubernetes-service-aks/)

- [gRPC Dokumentace](https://grpc.io/docs/guides/)

- [gRPC pro vývojáře WCF](https://docs.microsoft.com/dotnet/architecture/grpc-for-wcf-developers/)

- [Porovnání služeb gRPC s http api](https://docs.microsoft.com/aspnet/core/grpc/comparison?view=aspnetcore-3.0)

- [Vytváření služeb gRPC pomocí videa .NET](https://channel9.msdn.com/Shows/The-Cloud-Native-Show/Building-Microservices-with-gRPC-and-NET)

>[!div class="step-by-step"]
>[Předchozí](grpc.md)
>[další](Database-per-microservice.md)
