---
title: "Implementace odolná aplikace"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace odolná aplikace"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: a6fc2f4c963d857be06e194468e2f8514437dd1d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-resilient-applications"></a>Implementace odolná aplikace

*Vaše mikroslužbu a cloudové aplikace musí použít částečný chyby, ke kterým určitě dojde nakonec. Je třeba navrhnout vaše aplikace, bude odolné vůči selhání těchto částečné.*

Odolnost proti chybám je možnost obnovení v případě selhání a i nadále fungovat. Nejedná se o zamezení selhání, ale přijímá fakt, že dojde k selhání a reagovat na ně způsobem, který zabraňuje výpadku nebo ztráty dat. Cílem odolnosti je pro návrat aplikace plně funkčního stavu po selhání.

Je náročné dost pro návrh a nasazení aplikace na základě mikroslužeb. Ale musíte také zachovat spuštěn v prostředí, kde některé řazení selhání je určitá aplikace. Aplikace musí být proto odolný. Ho by se měly navrhovat zvládnout s částečné chybami, jako jsou výpadky sítě nebo uzly nebo chybám v cloudu virtuálních počítačů. Přesouvá na jiný uzel v clusteru i mikroslužeb (kontejnerů) může způsobit občasné krátké chyby v aplikaci.

Mnoho jednotlivých součástí aplikace by měla obsahovat také funkce sledování stavu. Podle pokynů v této kapitole můžete vytvořit aplikaci, která může bezproblémově pracovat s Přestože přechodný výpadku nebo normální hiccups, ke kterým došlo v nasazení komplexní a založené na cloudu.


>[!div class="step-by-step"]
[Předchozí] (.. / microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md) [Další] (popisovač failure.md partial)
