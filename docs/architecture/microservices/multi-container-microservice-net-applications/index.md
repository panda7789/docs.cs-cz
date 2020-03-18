---
title: Navrhování a vývoj aplikací .NET založených na více kontejnerech a mikroslužbách
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Seznamte se s externí architekturou pro navrhování a vývoj aplikací .NET založených na více kontejnerech a mikroslužbách.
ms.date: 10/02/2018
ms.openlocfilehash: 8c2f828e9913a0efcdf580371124b0f624daeffe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "70296624"
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a>Navrhování a vývoj vícekontejnerových a mikroslužeb založených na aplikacích .NET

*Vývoj kontejnerizovaných aplikací mikroslužeb znamená, že vytváříte aplikace s více kontejnery. Aplikace s více kontejnery však může být také jednodušší – například třívrstvá aplikace – a nemusí být sestavena pomocí architektury mikroslužeb.*

Dříve jsme vznesli otázku "Je Docker nutné při vytváření architektury mikroslužeb?" Odpověď je jasné ne. Docker je enabler a může poskytnout významné výhody, ale kontejnery a Docker nejsou pevný požadavek pro mikroslužeb. Jako příklad můžete vytvořit aplikaci založenou na mikroslužbách s Nebo bez Dockeru při použití Azure Service Fabric, který podporuje mikroslužby spuštěné jako jednoduché procesy nebo jako kontejnery Dockeru.

Pokud však víte, jak navrhnout a vyvinout aplikaci založenou na mikroslužbách, která je také založena na kontejnerech Dockeru, budete moci navrhovat a vyvíjet jakýkoli jiný, jednodušší aplikační model. Můžete například navrhnout třívrstvou aplikaci, která také vyžaduje přístup s více kontejnery. Z tohoto důvodu a protože architektury mikroslužeb jsou důležitým trendem ve světě kontejnerů, tato část se zaměřuje na implementaci architektury mikroslužeb pomocí kontejnerů Dockeru.

>[!div class="step-by-step"]
>[Předchozí](../docker-application-development-process/docker-app-development-workflow.md)
>[další](microservice-application-design.md)
