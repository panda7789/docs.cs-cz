---
title: Adresovatelnost mikroslužeb a registr služeb
description: Seznamte se s rolí registrů obrázků kontejnerů v architektuře mikroslužeb.
ms.date: 09/20/2018
ms.openlocfilehash: d72ba399f3da730f0e57c44c5ec01c1cc9f5fc05
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295880"
---
# <a name="microservices-addressability-and-the-service-registry"></a>Adresovatelnost mikroslužeb a registr služeb

Každá mikroslužba má jedinečný název (URL), který se používá k vyřešení jeho umístění. Vaše mikroslužba musí být adresovatelná, ať už běží kdekoli. Pokud máte přemýšlet o tom, který počítač je spuštěn konkrétní mikroslužbu, věci mohou jít špatně rychle. Stejným způsobem, že služba DNS překládá adresu URL pro konkrétní počítač, musí mít mikroslužba jedinečný název, aby bylo možné zjistit její aktuální umístění. Mikroslužby potřebují adresovatelné názvy, které je činí nezávislými na infrastruktuře, na které běží. To znamená, že existuje interakce mezi tím, jak je vaše služba nasazena, a způsobem, jakým je zjištěna, protože musí existovat [registr služeb](https://microservices.io/patterns/service-registry.html). Ve stejném duchu, když počítač selže, musí být služba registru schopna určit, kde je nyní spuštěna služba.

[Vzor registru služby](https://microservices.io/patterns/service-registry.html) je klíčovou součástí zjišťování služby. Registr je databáze obsahující síťová umístění instancí služeb. Registr služeb musí být vysoce dostupný a aktuální. Klienti mohou ukládat do mezipaměti síťová umístění získaná z registru služeb. Tyto informace však nakonec zadá a klienti již nemohou zjišťovat instance služby. V důsledku toho se registr služby skládá z clusteru serverů, které používají replikační protokol k udržení konzistence.

V některých prostředích nasazení mikroslužeb (nazývané clustery, které mají být zahrnuty v pozdější části), zjišťování služby je vestavěný. Například azure kontejnerové služby s Kubernetes (AKS) prostředí může zpracovávat registraci instance služby a zrušení registrace. Také spouští proxy server na každém hostiteli clusteru, který hraje roli směrovače zjišťování na straně serveru.

## <a name="additional-resources"></a>Další zdroje

- **Chrise Richardsona. Vzor: Registr služeb** \
  <https://microservices.io/patterns/service-registry.html>

- **Auth0. Registr služeb** \
  <https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/>

- **Gabriel Schenker. Zjišťování služby** \
  <https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/>

>[!div class="step-by-step"]
>[Předchozí](maintain-microservice-apis.md)
>[další](microservice-based-composite-ui-shape-layout.md)
