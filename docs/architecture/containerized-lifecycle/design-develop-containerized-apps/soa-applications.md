---
title: Aplikace SOA
description: Mějte na paměti, že kontejnery mohou být také užitečnou možností nasazení pro aplikace SOA.
ms.date: 02/15/2019
ms.openlocfilehash: f8619cb50a7d90b911db9ff2c8ef37c3c5fde210
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738389"
---
# <a name="service-oriented-applications"></a>Aplikace orientované na služby

Architektura orientovaná na služby (SOA) byla nadměrně používaný termín, který znamenal pro různé lidi mnoho různých věcí. Ale jako společný jmenovatel SOA znamená, že strukturu architektury aplikace rozkladu do několika služeb (nejčastěji jako služby HTTP), které mohou být klasifikovány v různých typech, jako jsou subsystémy nebo v jiných případech jako vrstvy.

Dnes můžete nasadit tyto služby jako kontejnery Dockeru, které řeší problémy související s nasazením, protože všechny závislosti jsou zahrnuty v image kontejneru. Však když potřebujete horizontální navýšení kapacity SOA, můžete se setkat s problémy, pokud nasazujete na základě jednotlivých instancí. Tuto výzvu lze zpracovat pomocí softwaru clusteringdockeru nebo orchestrátoru. Podíváme se na orchestrátory podrobněji v další části, když prozkoumáme přístupy mikroslužeb.

Kontejnery Dockeru jsou užitečné (ale není vyžadováno) pro tradiční architektury orientované na služby a pokročilejší architektury mikroslužeb.

Na konci dne řešení clustering kontejnerů jsou užitečné pro tradiční soa architektury a pro pokročilejší architekturu mikroslužeb, ve kterém každý mikroslužby vlastní svůj datový model. A díky více databázím můžete také škálovat datovou vrstvu namísto práce s monolitickými databázemi sdílenými službami SOA. Diskuse o rozdělení dat je však čistě o architektuře a designu.

>[!div class="step-by-step"]
>[Předchozí](state-and-data-in-docker-applications.md)
>[další](orchestrate-high-scalability-availability.md)
