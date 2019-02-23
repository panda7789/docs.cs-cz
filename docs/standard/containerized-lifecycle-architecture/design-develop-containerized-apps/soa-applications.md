---
title: Aplikace SOA
description: Berte v úvahu, že kontejnery můžou být také možnost užitečné nasazení pro aplikace SOA.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 353ba738143b7dcd92c7c75ac27ea6a7370f9da6
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745830"
---
# <a name="service-oriented-applications"></a>Aplikace orientované na služby

Architektura orientovaná na služby (záznam SOA) byl Nepromyšlené termín, který určená mnoho různé věci pro různé osoby. Ale jako společným faktorem SOA znamená, že struktury architekturu aplikace podle rozložení na několik služeb (nejčastěji jako služeb HTTP), které můžou být klasifikované v různých typech, jako je subsystémy nebo v jiných případech, jako úrovně.

Tyto služby ještě dnes, můžete nasadit jako kontejnery Dockeru, které vzhledem k tomu, že všechny závislosti jsou součástí image kontejneru s řešením problémů souvisejících s nasazením. Ale pokud potřebujete horizontálně navýšit kapacitu SOAs, může dojít výzvy Pokud provádíte nasazení na základě jedné instance. Tento problém možné je zpracovávat pomocí Dockeru clustering softwaru nebo produktu orchestrator. Podíváme na orchestrátory podrobněji v další části, když se podíváme na mikroslužby přístupy.

Kontejnery dockeru jsou užitečné (ale nevyžadováno) pro tradiční architektury orientované na služby a pokročilejší architekturu mikroslužeb.

Na konci dne jsou užitečné pro obě tradiční architektura SOA a pro pokročilejší architekturu mikroslužeb, ve kterém je vlastníkem jednotlivých mikroslužeb její datový model clusteringu řešení kontejnerů. A díky více databází, také můžete škálovat datovou vrstvu, místo abyste pracovali s monolitické databází sdílí služby SOA. Diskuze o rozdělení dat je však čistě o architektuře a designu.

>[!div class="step-by-step"]
>[Předchozí](state-and-data-in-docker-applications.md)
>[další](orchestrate-high-scalability-availability.md)
