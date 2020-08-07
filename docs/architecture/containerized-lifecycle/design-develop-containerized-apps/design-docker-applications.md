---
title: Návrh aplikací Dockeru
description: Tady najdete odkaz na podrobný Průvodce architekturou mikroslužeb, protože to je téma, které v této příručce není popsané.
ms.date: 08/06/2020
ms.openlocfilehash: b63d4344abb358a393587bdacf91f6091b531af0
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915972"
---
# <a name="design-docker-applications"></a>Návrh aplikací Dockeru

Kapitola 1 představila základní koncepty týkající se kontejnerů a Docker. Tyto informace jsou základními informacemi, které potřebujete, abyste mohli začít. Podnikové aplikace ale můžou být složité a skládají se z několika služeb místo jediné služby nebo kontejneru. Pro tyto volitelné případy použití potřebujete znát další postupy pro návrh, jako je například architektura orientované na služby (SOA) a pokročilejší koncepty mikroslužeb a koncepty orchestrace kontejnerů. Rozsah tohoto dokumentu není omezený na mikroslužby, ale i na jakýkoli životní cyklus aplikace Docker, proto nezkoumá architekturu mikroslužeb v hloubkě, protože můžete také použít kontejnery a Docker s pravidelným záznamem SOA, úlohami na pozadí nebo úlohami nebo dokonce s přístupy k nasazení aplikací monolitické.

**Další informace** Pokud chcete získat další informace o architektuře podnikových aplikací a mikroslužeb, přečtěte si příručku [net mikroslužby: architektura pro kontejnerové aplikace .NET](../../microservices/index.md) , ze kterých si můžete také stáhnout <https://aka.ms/MicroservicesEbook> .

Před tím, než se dostanete k životnímu cyklu aplikace a DevOps, je důležité, abyste věděli, jak navrhnout a sestavit aplikaci a jaké jsou vaše možnosti návrhu.

>[!div class="step-by-step"]
>[Předchozí](index.md) 
> [Další](common-container-design-principles.md)
