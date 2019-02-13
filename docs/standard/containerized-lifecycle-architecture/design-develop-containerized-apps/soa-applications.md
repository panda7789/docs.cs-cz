---
title: Aplikace SOA
description: Berte v úvahu, že kontejnery můžou být také možnost užitečné nasazení pro aplikace SOA.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 4fd39e075c5730cf7fddb0138cdb5267a914c91f
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221261"
---
# <a name="soa-applications"></a>Aplikace SOA

SOA se Nepromyšlené termín a určená tolik různé věci pro různé osoby. Ale minimálně a jako společným faktorem, SOA, nebo orientaci na služby, střední architekturu aplikace podle rozložení u více služeb (nejčastěji jako služeb HTTP), které mohou být zařazeny do různých typů struktury, jako jsou subsystémů nebo v jiných případech jako úrovní.

V současné době můžete nasadit tyto služby jako kontejnery Dockeru, které řeší problémy týkající se nasazení, protože všechny závislosti jsou zahrnuté do image kontejneru. Ale pokud potřebujete SOAs horizontální navýšení kapacity, může dojít výzvy Pokud provádíte nasazení na základě jedné instance. To je, kde Docker clustering softwaru nebo produktu orchestrator vám pomůže. Podíváme na to podrobněji v další části při prozkoumáme přístupy mikroslužeb.

Na konci dne jsou užitečné pro obě tradiční architektura SOA nebo pro pokročilejší architekturu mikroslužeb, ve kterém je vlastníkem jednotlivých mikroslužeb její datový model clusteringu řešení kontejnerů. A, díky více databází, můžete také můžete škálovat datovou vrstvu, místo abyste pracovali s monolitické databází sdílí služby SOA. Diskuze o rozdělení dat je však čistě o architektuře a designu.

>[!div class="step-by-step"]
>[Předchozí](state-and-data-in-docker-applications.md)
>[další](orchestrate-high-scalability-availability.md)