---
title: Návrh aplikací Dockeru
description: Zde naleznete odkaz na podrobný průvodce architekturou mikroslužeb, protože to je téma, které není podrobně popsáno v této příručce.
ms.date: 02/15/2019
ms.openlocfilehash: b9539ff4edf405ab890d83be59a248ffa2360c99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295863"
---
# <a name="design-docker-applications"></a>Návrh aplikací Dockeru

Kapitola 1 představila základní koncepty týkající se kontejnerů a Dockeru. Tyto informace jsou základní úrovní informací, které potřebujete k zahájení. Podnikové aplikace však mohou být složité a složené z více služeb namísto jedné služby nebo kontejneru. Pro tyto volitelné případy použití, musíte znát další přístupy k návrhu, jako je například architektura orientovaná na služby (SOA) a pokročilejší koncepty mikroslužeb a koncepty orchestrace kontejnerů. Rozsah tohoto dokumentu není omezena na mikroslužeb, ale na všechny dockerové aplikace životního cyklu, proto není prozkoumat architekturu mikroslužeb do hloubky, protože můžete také použít kontejnery a Docker s pravidelným SOA, úlohy na pozadí nebo úlohy, nebo dokonce s monolitickými přístupy k nasazení aplikací.

**Více informací** Další informace o podnikových aplikacích a architektuře mikroslužeb do hloubky naleznete v průvodci NET <https://aka.ms/MicroservicesEbook> [Microservices: Architecture for Containerized .NET Applications,](../../microservices/index.md) které můžete také stáhnout z aplikace .

Než se však dostaneme do životního cyklu aplikace a devops, je důležité vědět, jak budete navrhovat a konstruovat aplikaci a jaké jsou vaše možnosti návrhu.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](common-container-design-principles.md)
