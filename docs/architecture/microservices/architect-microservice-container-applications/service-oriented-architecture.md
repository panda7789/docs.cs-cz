---
title: Architektura orientovaná na služby
description: Seznamte se se základními rozdíly mezi mikroslužbami a architekturou orientované na služby (SOA).
ms.date: 09/20/2018
ms.openlocfilehash: 84786539fbac0e8b38a81a2580232474774cd355
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296215"
---
# <a name="service-oriented-architecture"></a>Architektura orientovaná na služby

Architektura založená na službách (SOA) byla přejmenována za nepoužitou a má různé věci pro různé lidi. Ale jako společný jmenovatel, záznam SOA znamená, že svou aplikaci můžete strukturovat tím, že ji vyměníte do více služeb (nejčastěji jako služby HTTP), které je možné klasifikovat jako různé typy, jako jsou například subsystémy nebo vrstvy.

Tyto služby se teď dají nasadit jako kontejnery Docker, které řeší problémy s nasazením, protože všechny závislosti jsou obsažené v imagi kontejneru. Pokud ale potřebujete škálovat aplikace typu SOA, můžete mít problémy se škálovatelností a dostupností, pokud nasazujete na základě jednoho hostitele Docker. Tady se dozvíte, že software pro clusteringu Docker nebo produkt Orchestrator vám může pomáhat, jak je vysvětleno v dalších částech, kde jsou popsány přístupy k nasazení pro mikroslužby.

Kontejnery Docker jsou užitečné (ale nevyžadují se) pro tradiční architektury zaměřené na služby a pokročilejší architektury mikroslužeb.

Mikroslužby jsou odvozeny od SOA, ale záznam SOA se liší od architektury mikroslužeb. Funkce, jako jsou velká centrální zprostředkovatelé, centrální orchestrace na úrovni organizace a [Enterprise Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) , jsou typické v záznamu SOA. Ve většině případů se ale jedná o antipatterny v komunitě mikroslužeb. Ve skutečnosti někteří lidé tvrdíi, že architektura mikroslužeb se dokončí přímo. "

Tato příručka se zaměřuje na mikroslužby, protože přístup k SOA je méně podrobný než požadavky a techniky používané v architektuře mikroslužeb. Pokud víte, jak vytvořit aplikaci založenou na mikroslužbách, dozvíte se také, jak vytvořit jednodušší aplikaci orientované na služby.

>[!div class="step-by-step"]
>[Předchozí](docker-application-state-data.md)Další
>[](microservices-architecture.md)
