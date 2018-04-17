---
title: Návrh aplikace Docker
description: Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 54f6f1ecdd89b85d4f44136da9a5ec9610f170a9
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="design-docker-applications"></a>Návrh aplikace Docker

Kapitola 1 zavedly základní koncepty týkající se kontejnery a Docker. Tyto informace je základní úroveň informace, které potřebujete, abyste mohli začít. Ale podnikové aplikace, které může být složité a skládat z několika služeb místo jednu službu nebo kontejneru. Pro případy nepovinným použitím musíte znát další přístupy k návrhu, jako je architektura Service-Oriented (SOA) a pokročilejší mikroslužeb koncepty a kontejner koncepty orchestration. Rámec tohoto dokumentu se neomezuje na mikroslužeb, ale žádné Docker aplikace životní cyklus, proto ji není prozkoumat mikroslužeb architektura podrobněji, protože také můžete použít kontejnery a Docker pomocí regulárních SAO, úlohy na pozadí nebo úlohy, nebo dokonce i s přístupy k nasazení monolitický aplikace.

Ale předtím, než se nám získat do životního cyklu aplikace a DevOps, je důležité vědět, jak se chystáte návrhu a vytvořit aplikace a jaké jsou vaše volby návrhu.


>[!div class="step-by-step"]
[Předchozí] (index.md) [Další] (běžné kontejneru návrhu principles.md)
