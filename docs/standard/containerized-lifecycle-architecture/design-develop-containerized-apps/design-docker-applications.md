---
title: Návrh aplikací Dockeru
description: Tady najít odkaz na podrobné příručce k architektuře mikroslužeb, protože se na téma, který není podrobně popsané v této příručce.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: f31421cab7d2072441999231adfbe771a3f9a0f5
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220202"
---
# <a name="design-docker-applications"></a>Návrh aplikací Dockeru

Kapitoly 1 jsme zavedli základní koncepty týkající se kontejnerů a Dockeru. Tyto informace je základní úroveň informací, které potřebujete, abyste mohli začít. Ale podnikových aplikací mohou být složité a skládá z několika služeb namísto jedné služby nebo kontejneru. Pro tyto případy použití volitelné je potřeba vědět další přístupy k návrhu, jako je architektura Service-Oriented (SOA) a pokročilejší koncepty mikroslužeb a kontejnerů koncepty Orchestrace. Rámec tohoto dokumentu se neomezuje na mikroslužby ale do jakékoli Docker aplikace životního cyklu, proto ho není prozkoumat architektury mikroslužeb do hloubky protože také můžete použít kontejnerům a Dockeru s regulární SAO, úlohy na pozadí nebo úlohy, nebo dokonce i s monolitickými aplikacemi způsoby nasazení.

Ale předtím, než se dostaneme k životního cyklu aplikace a DevOps, je důležité vědět, jak chcete navrhnout a sestavit aplikaci a jaké jsou vaše volby při návrhu.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](common-container-design-principles.md)