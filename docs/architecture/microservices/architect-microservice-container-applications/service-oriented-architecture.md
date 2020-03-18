---
title: Architektura orientovaná na služby
description: Naučte se základní rozdíly mezi mikroslužeb a architektura orientovaná na služby (SOA).
ms.date: 09/20/2018
ms.openlocfilehash: 84786539fbac0e8b38a81a2580232474774cd355
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70296215"
---
# <a name="service-oriented-architecture"></a>Architektura orientovaná na služby

Architektura orientovaná na služby (SOA) byla nadměrně používaná a znamenala pro různé lidi různé věci. Ale jako společný jmenovatel SOA znamená, že strukturu aplikace rozkladem do více služeb (nejčastěji jako služby HTTP), které lze klasifikovat jako různé typy, jako jsou subsystémy nebo vrstvy.

Tyto služby lze nyní nasadit jako kontejnery Dockeru, což řeší problémy s nasazením, protože všechny závislosti jsou zahrnuty v image kontejneru. Když však potřebujete vertikálně navýšit kapacitu aplikací SOA, můžete mít problémy s škálovatelností a dostupností, pokud nasazujete na základě jednotlivých hostitelů Dockeru. Toto je místo, kde Docker clustering software nebo orchestrator vám může pomoci, jak je vysvětleno v dalších částech, kde jsou popsány přístupy nasazení pro mikroslužby.

Kontejnery Dockeru jsou užitečné (ale není vyžadováno) pro tradiční architektury orientované na služby a pokročilejší architektury mikroslužeb.

Mikroslužby jsou odvozeny od SOA, ale SOA se liší od architektury mikroslužeb. Funkce, jako jsou velké centrální makléři, centrální orchestrátory na úrovni organizace a [Enterprise Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) jsou typické pro SOA. Ale ve většině případů se jedná o anti-vzory v komunitě mikroslužeb. Ve skutečnosti, někteří lidé tvrdí, že "architektura mikroslužeb je SOA udělat správně."

Tato příručka se zaměřuje na mikroslužeb, protože přístup SOA je méně normativní než požadavky a techniky používané v architektuře mikroslužeb. Pokud víte, jak vytvořit aplikaci založenou na mikroslužbách, víte také, jak vytvořit jednodušší aplikaci orientovanou na služby.

>[!div class="step-by-step"]
>[Předchozí](docker-application-state-data.md)
>[další](microservices-architecture.md)
