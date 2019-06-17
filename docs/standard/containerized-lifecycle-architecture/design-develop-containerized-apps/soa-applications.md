---
title: Aplikace SOA
description: Berte v úvahu, že kontejnery můžou být také možnost užitečné nasazení pro aplikace SOA.
ms.date: 02/15/2019
ms.openlocfilehash: aa56ada7b14a465fb3dafd02b03b815782ac765b
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/13/2019
ms.locfileid: "65644763"
---
# <a name="service-oriented-applications"></a>Aplikace orientované na služby

Architektura orientovaná na služby (záznam SOA) byl Nepromyšlené termín, který určená mnoho různé věci pro různé osoby. Ale jako společným faktorem SOA znamená, že struktury architekturu aplikace podle rozložení na několik služeb (nejčastěji jako služeb HTTP), které můžou být klasifikované v různých typech, jako je subsystémy nebo v jiných případech, jako úrovně.

Tyto služby ještě dnes, můžete nasadit jako kontejnery Dockeru, které vzhledem k tomu, že všechny závislosti jsou součástí image kontejneru s řešením problémů souvisejících s nasazením. Ale pokud potřebujete horizontálně navýšit kapacitu SOAs, může dojít výzvy Pokud nasazujete na základě jedné instance. Tento problém možné je zpracovávat pomocí Dockeru clustering softwaru nebo produktu orchestrator. Podíváme na orchestrátory podrobněji v další části, když se podíváme na mikroslužby přístupy.

Kontejnery dockeru jsou užitečné (ale nevyžadováno) pro tradiční architektury orientované na služby a pokročilejší architekturu mikroslužeb.

Na konci dne jsou užitečné pro obě tradiční architektura SOA a pro pokročilejší architekturu mikroslužeb, ve kterém je vlastníkem jednotlivých mikroslužeb její datový model clusteringu řešení kontejnerů. A díky více databází, také můžete škálovat datovou vrstvu, místo abyste pracovali s monolitické databází sdílí služby SOA. Diskuze o rozdělení dat je však čistě o architektuře a designu.

>[!div class="step-by-step"]
>[Předchozí](state-and-data-in-docker-applications.md)
>[další](orchestrate-high-scalability-availability.md)
