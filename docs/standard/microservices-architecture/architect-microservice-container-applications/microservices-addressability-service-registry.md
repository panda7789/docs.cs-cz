---
title: Mikroslužeb adresovatelnosti a registru služby
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Mikroslužeb adresovatelnosti a registru služby
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: cce0b11ca8cb4fe4d97e2f575888254f92543fc3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="microservices-addressability-and-the-service-registry"></a>Mikroslužeb adresovatelnosti a registru služby

Každý mikroslužbu má jedinečný název (URL), který se používá k překladu jeho umístění. Vaše mikroslužbu musí být adresovatelné vždy, když je spuštěná. Pokud máte myslíte o počítač, který je spuštěn konkrétní mikroslužbu, co můžete přejít chybný rychle. Stejným způsobem, že DNS přeloží adresu URL k určitému počítači musí mít jedinečný název, tak, aby jeho aktuálního umístění zjistitelný vaší mikroslužby. Mikroslužeb potřebovat adresovatelné názvy, které je nezávislé na infrastrukturu, která běží na. Z toho vyplývá, že existuje interakci mezi nasazení služby a jak se zjistí, protože je potřeba [registru služby](https://microservices.io/patterns/service-registry.html). Ve stejné souvislosti nepodaří-li počítač, služba registru musí umět označuje, kde služba je nyní spuštěna.

[Vzor registru služby](https://microservices.io/patterns/service-registry.html) je klíčovou součástí zjišťování služby. Registr je databáze obsahující síťová umístění instancí služby. Registru služby musí být vysoce dostupné a aktuální. Klienti mohou ukládat do mezipaměti získaný z registru služby umístění v síti. Ale tyto informace nakonec přejde zastaralý a klienti mohou už zjistit instance služby. V důsledku toho služba registru se skládá z clusteru serverů, které používají protokol replikace můžete zachovat konzistenci.

V některých prostředích nasazení mikroslužbu (označovaný jako clustery, na které se vztahují v další části) je integrovaný zjišťování služby. Například v prostředí Azure Container Service Kubernetes a DC/OS s Marathon můžete zpracovat registraci instance služby a zrušení registrace. Proxy server také běží na každého hostitele clusteru, kterou hraje roli směrovače zjišťování na straně serveru. Dalším příkladem je Azure Service Fabric, která také poskytuje registru služby prostřednictvím jeho služby DNS na více systémů v poli.

Všimněte si, že určité překrytí registru služby a vzoru Brána rozhraní API, která pomáhá také tento problém vyřešit. Například [Service Fabric Reverse Proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy) typu implementace bránu rozhraní API, který je založen na službu Naming Service Fabrici a který pomáhá vyřešit překladu adresy pro interní služby.

## <a name="additional-resources"></a>Další zdroje

-   **Jan Ryšánková. Vzoru: Registru služby**
    *https://microservices.io/patterns/service-registry.html*

-   **Auth0. Služba registru**
    [*https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/*](https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/)

-   **Gabriel Schenker. Zjišťování služby**
    [*https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/*](https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/)


>[!div class="step-by-step"]
[Předchozí] (maintain-microservice-apis.md) [Další] (microservice-based-composite-ui-shape-layout.md)
