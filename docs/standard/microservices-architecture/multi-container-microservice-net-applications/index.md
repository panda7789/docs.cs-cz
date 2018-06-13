---
title: Návrh a vývoj Mikroslužbu a více kontejneru na základě aplikací .NET
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Návrh a vývoj Mikroslužbu a více kontejneru na základě aplikací .NET
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 297a53d6d6d37b1fa4a0e021919c9df86edeca03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571953"
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a>Návrh a vývoj aplikace s více kontejneru a na základě Mikroslužbu .NET

*Vývoj aplikací kontejnerizované mikroslužbu znamená, že vytváříte více kontejneru aplikace. Ale aplikace s více kontejnerů mohou být také jednodušší – například třívrstvá aplikace – a nemusí být vytvořená s využitím architektury mikroslužby.*

Dříve jsme vyvolá na otázku "Je Docker potřebné při sestavování architektury mikroslužby?" Odpověď je zrušte ne. Docker je podpůrnou technologii a může poskytnout významné výhody, ale kontejnery a Docker nejsou pevný požadavek pro mikroslužeb. Jako příklad může vytvořte aplikaci na základě mikroslužeb s nebo bez Docker při použití Azure Service Fabric, která podporuje běží jako jednoduchý procesy nebo jako kontejnery Docker mikroslužeb.

Ale pokud víte, jak pro návrh a vývoj aplikace na základě mikroslužeb také založené na Docker kontejnery, bude moct návrh a vývoj jiných, aplikační model jednodušší. Například můžete navrhnout třívrstvá aplikace, který taky vyžaduje přístup více kontejneru. Z tohoto důvodu a protože architektury mikroslužby jsou důležité trend v rámci světa kontejneru, tato část se zaměřuje na na implementace architektury mikroslužby pomocí Docker kontejnery.


>[!div class="step-by-step"]
[Předchozí] (.. /containerize-NET-Framework-Applications/index.MD) [Další] (mikroslužbu design.md aplikace)
