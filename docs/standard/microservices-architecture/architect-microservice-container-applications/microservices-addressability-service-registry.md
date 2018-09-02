---
title: Adresovatelnost Mikroslužeb a registr služeb
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Adresovatelnost Mikroslužeb a registr služeb
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: ec0617c5a5c1861f3596e12f3d7a7017a448239e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43388902"
---
# <a name="microservices-addressability-and-the-service-registry"></a>Adresovatelnost Mikroslužeb a registr služeb

Každá mikroslužba má jedinečný název (URL), který se používá k překladu jeho umístění. Vaše mikroslužeb musí být adresovatelný bez ohledu na to funguje. Pokud máte přemýšlet o počítač, který je spuštěn konkrétní mikroslužeb, může něco chybný rychle. Stejným způsobem, že DNS přeloží adresu URL k určitému počítači musí mít jedinečný název tak, aby jeho aktuálního umístění zjistitelné vaše mikroslužeb. Mikroslužby potřebují adresovatelný názvy, proto je nezávislý na infrastrukturu, která, na kterém běží. To znamená, že neexistuje interakci mezi způsob nasazení vaší služby a jak ho najdou, protože musí být [registru služby](https://microservices.io/patterns/service-registry.html). Ve stejném souvislosti když se počítač nepovede, služba registru musí být schopen určit, ve kterém nyní běží služba.

[Služba registru vzor](https://microservices.io/patterns/service-registry.html) je klíčovou součástí zjišťování služby. Registr je databáze obsahující síťová umístění instance služby. Služba registru musí být vysoce dostupná a aktuální. Klienti mezipaměti získal z registru služby umístění v síti. Ale tyto informace nakonec přejde zastaralá a klienti už najdou instance služby. V důsledku toho služba registru se skládá z clusteru serverů, které používají protokol replikace můžete zachovat konzistenci.

V některých prostředích nasazení mikroslužeb (označované jako clustery mají být zahrnuty v další části) jsou integrované zjišťování služby. Například v rámci prostředí Azure Container Service Kubernetes a DC/OS pomocí Marathonu může zpracování registrace instance služby a zrušení registrace. Také použijí proxy hostitele clusteru, do kterého hraje roli směrovače zjišťování na straně serveru. Dalším příkladem je Azure Service Fabric, které také poskytuje služba registru prostřednictvím jeho out-of-the-box pojmenování Service.

Všimněte si, že některé překrytí registru služby a model brány rozhraní API, která pomáhá také tento problém vyřešit. Například [reverzní Proxy Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy) k typu implementace bránu rozhraní API, který je založen na služba pojmenování Service Fabric a, která pomáhá řešit rozpoznání adresy pro interní služby.

## <a name="additional-resources"></a>Další zdroje

-   **Chris Richardson. Vzoru: Služba registru**
    *https://microservices.io/patterns/service-registry.html*

-   **Auth0. Služba registru**
    [*https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/*](https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/)

-   **Gabrielem Schenker. Zjišťování služby**
    [*https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/*](https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/)


>[!div class="step-by-step"]
[Předchozí](maintain-microservice-apis.md)
[další](microservice-based-composite-ui-shape-layout.md)
