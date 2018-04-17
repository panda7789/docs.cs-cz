---
title: Aplikace SOA
description: Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 48dc0f038cee8ddc9555881f2143b566df223a04
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="soa-applications"></a>Aplikace SOA

SOA byl Nepromyšlené termín a určená mnoho různých věcí na jiné osoby. Ale minimálně a jako běžné jmenovatel, SOA, nebo orientaci na služby, střední architektuře vaší aplikace pomocí decomposing v několika služeb (nejčastěji jako služeb HTTP), které můžou být klasifikované v různých typů struktura jako subsystémy nebo v jiných případech jako úrovně.

Tyto služby můžete v současné době nasadit jako Docker kontejnery, které řeší problémy související s nasazení, protože všechny závislosti jsou zahrnuty do bitové kopie kontejneru. Ale pokud budete potřebovat pro škálované SOAs, můžete setkat výzvy Pokud nasazujete na základě jedné instance. Toto je, kde Docker, clustering softwaru nebo orchestrator vám pomůže. Podíváme to podrobněji v další části když jsme zkontrolujte mikroslužeb přístupy.

Na konci dne jsou užitečné pro obě tradiční architektury SOA nebo pro pokročilejší architektura mikroslužeb, ve kterém každý mikroslužbu vlastní jeho datového modelu řešení clusteringu kontejneru. A díky více databází, můžete také můžete Škálováním na více systémů datové vrstvy místo práce monolitický databáze sdílené službami SOA. Diskuzi o rozdělení dat je však čistě o architektuře a designu.


>[!div class="step-by-step"]
[Předchozí] (state-and-data-in-docker-applications.md) [Další] (orchestraci vysokou škálovatelnost availability.md)
