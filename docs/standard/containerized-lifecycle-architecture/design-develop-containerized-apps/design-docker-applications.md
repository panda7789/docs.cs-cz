---
title: Návrh aplikací Dockeru
description: Životní cyklus aplikace kontejnerizovaných Dockeru s platformou a nástroji Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: d02cec0595024eb7bd7c0ac46df093359680da74
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155376"
---
# <a name="design-docker-applications"></a>Návrh aplikací Dockeru

Kapitoly 1 jsme zavedli základní koncepty týkající se kontejnerů a Dockeru. Tyto informace je základní úroveň informací, které potřebujete, abyste mohli začít. Ale podnikových aplikací mohou být složité a skládá z několika služeb namísto jedné služby nebo kontejneru. Pro tyto případy použití volitelné je potřeba vědět další přístupy k návrhu, jako je architektura Service-Oriented (SOA) a pokročilejší koncepty mikroslužeb a kontejnerů koncepty Orchestrace. Rámec tohoto dokumentu se neomezuje na mikroslužby ale do jakékoli Docker aplikace životního cyklu, proto ho není prozkoumat architektury mikroslužeb do hloubky protože také můžete použít kontejnerům a Dockeru s regulární SAO, úlohy na pozadí nebo úlohy, nebo dokonce i s monolitickými aplikacemi způsoby nasazení.

Ale předtím, než se dostaneme k životního cyklu aplikace a DevOps, je důležité vědět, jak chcete navrhnout a sestavit aplikaci a jaké jsou vaše volby při návrhu.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](common-container-design-principles.md)