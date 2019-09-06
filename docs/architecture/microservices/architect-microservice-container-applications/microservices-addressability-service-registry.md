---
title: Adresovatelnost mikroslužeb a registr služeb
description: Pochopení role registrů imagí kontejneru v architektuře mikroslužeb.
ms.date: 09/20/2018
ms.openlocfilehash: d72ba399f3da730f0e57c44c5ec01c1cc9f5fc05
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295880"
---
# <a name="microservices-addressability-and-the-service-registry"></a>Adresovatelnost mikroslužeb a registr služeb

Každá mikroslužba má jedinečný název (URL), který se používá k překladu jeho umístění. Vaše mikroslužba musí být adresovatelná bez ohledu na to, kde je spuštěná. Pokud si myslíte, na kterém počítači je spuštěná konkrétní mikroslužba, může jít o něco rychle. Stejným způsobem, jakým DNS překládá adresu URL na konkrétní počítač, musí mít vaše mikroslužba jedinečný název, aby bylo možné zjistit jeho aktuální umístění. Mikroslužby potřebují adresovatelné názvy, které je nezávisle na infrastruktuře, na které běží. To znamená, že existuje interakce mezi tím, jak je vaše služba nasazená, a jak je zjištěná, protože je potřeba mít [registr služby](https://microservices.io/patterns/service-registry.html). Ve stejné přízávažnosti, pokud dojde k chybě počítače, musí být služba registru schopná určit, kde je služba nyní spuštěná.

[Vzor registru služby](https://microservices.io/patterns/service-registry.html) je klíčovou součástí zjišťování služeb. Registr je databáze obsahující síťová umístění instancí služby. Registr služeb musí být vysoce dostupný a aktuální. Klienti můžou ukládat do mezipaměti síťová umístění získaná z registru služby. Tyto informace jsou ale nakonec zastaralé a klienti už nebudou moci zjišťovat instance služby. V důsledku toho se registr služeb skládá z clusteru serverů, které používají replikační protokol k zachování konzistence.

V některých prostředích pro nasazení mikroslužeb (označovaných jako clustery, které se mají pokrýt v pozdější části), je zjišťování služeb integrované. Například Azure Container Service s prostředím Kubernetes (AKS) může zpracovávat registraci a zrušení registrace instance služby. Také spouští proxy na každém hostiteli clusteru, který hraje roli směrovače zjišťování na straně serveru.

## <a name="additional-resources"></a>Další zdroje

- **Chris Richardson. Vzorku Registr služby** \
  <https://microservices.io/patterns/service-registry.html>

- **Auth0. Registr služby** \
  <https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/>

- **Gabrielem Schenker. Zjišťování služby** \
  <https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/>

>[!div class="step-by-step"]
>[Předchozí](maintain-microservice-apis.md)Další
>[](microservice-based-composite-ui-shape-layout.md)
