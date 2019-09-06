---
title: Návrh aplikací Dockeru
description: Tady najdete odkaz na podrobný Průvodce architekturou mikroslužeb, protože to je téma, které v této příručce není popsané.
ms.date: 02/15/2019
ms.openlocfilehash: b9539ff4edf405ab890d83be59a248ffa2360c99
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295863"
---
# <a name="design-docker-applications"></a>Návrh aplikací Dockeru

Kapitola 1 představila základní koncepty týkající se kontejnerů a Docker. Tyto informace jsou základními informacemi, které potřebujete, abyste mohli začít. Podnikové aplikace ale můžou být složité a skládají se z několika služeb místo jediné služby nebo kontejneru. Pro tyto volitelné případy použití potřebujete znát další postupy pro návrh, jako je například architektura orientované na služby (SOA) a pokročilejší koncepty mikroslužeb a koncepty orchestrace kontejnerů. Rozsah tohoto dokumentu není omezený na mikroslužby, ale i na jakýkoli životní cyklus aplikace Docker, proto nezkoumá architekturu mikroslužeb v hloubkě, protože můžete také použít kontejnery a Docker s pravidelným záznamem SOA, úlohami na pozadí nebo úlohami i s přístupy k nasazení aplikací monolitické.

**Další informace** Pokud chcete získat další informace o architektuře podnikových aplikací a mikroslužeb, přečtěte si [příručku NET mikroslužby: Architektura pro kontejnerové aplikace](../../microservices/index.md) .NET, ze <https://aka.ms/MicroservicesEbook>kterých si můžete stáhnout také.

Před tím, než se dostanete k životnímu cyklu aplikace a DevOps, je důležité znát způsob návrhu a sestavování aplikace a možností vašich návrhů.

>[!div class="step-by-step"]
>[Předchozí](index.md)Další
>[](common-container-design-principles.md)
