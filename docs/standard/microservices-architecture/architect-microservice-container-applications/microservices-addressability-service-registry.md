---
title: Adresovatelnost mikroslužeb a registr služeb
description: Seznamte s rolí registry imagí kontejnerů v architektuře mikroslužeb.
ms.date: 09/20/2018
ms.openlocfilehash: d72ba399f3da730f0e57c44c5ec01c1cc9f5fc05
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690458"
---
# <a name="microservices-addressability-and-the-service-registry"></a>Adresovatelnost mikroslužeb a registr služeb

Každá mikroslužba má jedinečný název (URL), který se používá k překladu jeho umístění. Vaše mikroslužeb musí být adresovatelný bez ohledu na to funguje. Pokud máte přemýšlet o počítač, který je spuštěn konkrétní mikroslužeb, může něco chybný rychle. Stejným způsobem, že DNS přeloží adresu URL k určitému počítači musí mít jedinečný název tak, aby jeho aktuálního umístění zjistitelné vaše mikroslužeb. Mikroslužby potřebují adresovatelný názvy, proto je nezávislý na infrastrukturu, která běží na. To znamená, že neexistuje interakci mezi způsob nasazení vaší služby a jak ho najdou, protože musí být [registru služby](https://microservices.io/patterns/service-registry.html). Ve stejném souvislosti když se počítač nepovede, služba registru musí být schopen určit, ve kterém nyní běží služba.

[Služba registru vzor](https://microservices.io/patterns/service-registry.html) je klíčovou součástí zjišťování služby. Registr je databáze obsahující síťová umístění instance služby. Služba registru musí být vysoce dostupná a aktuální. Klienti mezipaměti získal z registru služby umístění v síti. Ale tyto informace nakonec přejde zastaralá a klienti už najdou instance služby. V důsledku toho služba registru se skládá z clusteru serverů, které používají protokol replikace můžete zachovat konzistenci.

V některých prostředích nasazení mikroslužeb (označované jako clustery mají být zahrnuty v další části) jsou integrované zjišťování služby. Azure Container Service pomocí prostředí Kubernetes (AKS) může například zpracování registraci instance služby a zrušení registrace. Proxy server také běží na každého hostitele clusteru, které hrají roli směrovače zjišťování na straně serveru.

## <a name="additional-resources"></a>Další zdroje

- **Chris Richardson. Vzor: Služba registru** \
  <https://microservices.io/patterns/service-registry.html>

- **Auth0. Služba registru** \
  <https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/>

- **Gabrielem Schenker. Zjišťování služby** \
  <https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/>

>[!div class="step-by-step"]
>[Předchozí](maintain-microservice-apis.md)
>[další](microservice-based-composite-ui-shape-layout.md)
