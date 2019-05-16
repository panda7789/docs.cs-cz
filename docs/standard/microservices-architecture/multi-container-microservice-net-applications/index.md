---
title: Aplikace .NET založené na návrh a vývoj více kontejnerech a Mikroslužbách
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Vysvětlení externí architektury pro návrh a vývoj více kontejnerech a aplikacích .NET na základě Mikroslužeb.
ms.date: 10/02/2018
ms.openlocfilehash: 8c2f828e9913a0efcdf580371124b0f624daeffe
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639457"
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a>Návrh a vývoj aplikací .NET více kontejnerů a založených na Mikroslužbách

*Vývoj aplikací pro kontejnerizované mikroslužby znamená, že vytváříte vícekontejnerových aplikací. Ale může také být jednodušší vícekontejnerová aplikace – například třívrstvé aplikace – a nemusí být sestaveno pomocí architekturu mikroslužeb.*

Dříve jsme vyvolána na otázku "Je Docker nezbytné při vytváření architektury mikroslužeb?" Odpověď je vymazat č. Docker je podpůrnou technologii a může poskytnout významné výhody, ale kontejnerů a Dockeru nejsou o striktní požadavek pro mikroslužby. Například můžete vytvořit aplikace založená na mikroslužbách s nebo bez něj Docker při použití Azure Service Fabric, která podporuje mikroslužeb spouštěných jako jednoduchý proces, nebo jako kontejnery Dockeru.

Ale pokud víte, jak pro návrh a vývoj aplikací založených na mikroslužbách, také založené na kontejnerech Dockeru, vám bude moct navrhovat a vyvíjet jiné aplikační model jednodušší. Například můžete navrhnout třívrstvé aplikace, který taky vyžaduje přístup více kontejnerů. Z důvodu, a protože architektury mikroslužeb jsou důležité trend v rámci světa kontejneru, tato část se zaměřuje na implementaci architektury mikroslužeb pomocí kontejnerů Dockeru.

>[!div class="step-by-step"]
>[Předchozí](../docker-application-development-process/docker-app-development-workflow.md)
>[další](microservice-application-design.md)
