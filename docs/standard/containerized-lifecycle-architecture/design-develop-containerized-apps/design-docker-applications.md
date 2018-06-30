---
title: Návrh aplikace Docker
description: Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: 2f4a3b7675365aa4d1e33328f756439398f3a4de
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105234"
---
# <a name="design-docker-applications"></a>Návrh aplikace Docker

Kapitola 1 zavedly základní koncepty týkající se kontejnery a Docker. Tyto informace je základní úroveň informace, které potřebujete, abyste mohli začít. Ale podnikové aplikace, které může být složité a skládat z několika služeb místo jednu službu nebo kontejneru. Pro případy nepovinným použitím musíte znát další přístupy k návrhu, jako je architektura Service-Oriented (SOA) a pokročilejší mikroslužeb koncepty a kontejner koncepty orchestration. Rámec tohoto dokumentu se neomezuje na mikroslužeb, ale žádné Docker aplikace životní cyklus, proto ji není prozkoumat mikroslužeb architektura podrobněji, protože také můžete použít kontejnery a Docker pomocí regulárních SAO, úlohy na pozadí nebo úlohy, nebo dokonce i s přístupy k nasazení monolitický aplikace.

Ale předtím, než se nám získat do životního cyklu aplikace a DevOps, je důležité vědět, jak se chystáte návrhu a vytvořit aplikace a jaké jsou vaše volby návrhu.


>[!div class="step-by-step"]
[Předchozí](index.md)
[další](common-container-design-principles.md)
