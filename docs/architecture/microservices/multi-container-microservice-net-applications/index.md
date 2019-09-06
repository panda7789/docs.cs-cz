---
title: Navrhování a vývoj aplikací .NET využívajících více kontejnerů a mikroslužeb
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Seznamte se s externí architekturou pro navrhování a vývoj aplikací .NET využívajících více kontejnerů a mikroslužeb.
ms.date: 10/02/2018
ms.openlocfilehash: 8c2f828e9913a0efcdf580371124b0f624daeffe
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296624"
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a>Navrhování a vývoj aplikací .NET založených na více kontejnerech a mikroslužbách

*Vývoj kontejnerových aplikací s využitím kontejnerů znamená, že vytváříte aplikace s více kontejnery. Aplikace s více kontejnery by ale mohla být jednodušší, například aplikace se třemi vrstvami – a nemusí být sestavená pomocí architektury mikroslužeb.*

Dříve jsme při vytváření architektury mikroslužeb vyvolali otázku "Docker". Odpověď není jasné. Docker je aktivátor a může poskytovat významné výhody, ale kontejnery a Docker nejsou pro mikroslužby pevně nutné. Jako příklad můžete vytvořit aplikaci založenou na mikroslužbách s Docker nebo bez něj při použití Azure Service Fabric, která podporuje mikroslužby spuštěné jako jednoduché procesy nebo jako kontejnery Docker.

Pokud ale víte, jak navrhnout a vyvíjet aplikaci založenou na mikroslužbách, která je založená na kontejnerech Docker, budete moct navrhnout a vyvíjet jakýkoliv jiný, jednodušší aplikační model. Můžete například navrhnout trojrozměrnou aplikaci, která také vyžaduje přístup přes více kontejnerů. Vzhledem k tomu, že architektury mikroslužeb jsou důležitým trendem v rámci kontejneru světa, se tato část zaměřuje na implementaci architektury mikroslužeb pomocí kontejnerů Docker.

>[!div class="step-by-step"]
>[Předchozí](../docker-application-development-process/docker-app-development-workflow.md)Další
>[](microservice-application-design.md)
