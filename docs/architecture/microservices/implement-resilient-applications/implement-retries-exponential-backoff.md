---
title: Implementace opakovaných pokusů s exponenciálním backoffem
description: Zjistěte, jak implementovat opakování s exponenciálním vypnutím.
ms.date: 10/16/2018
ms.openlocfilehash: 1b948e399495eeb12016006442ac08d2b04f2e69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70296063"
---
# <a name="implement-retries-with-exponential-backoff"></a>Implementace opakovaných pokusů s exponenciálním backoffem

[*Opakování s exponenciálním podčasovým vypnutím*](/azure/architecture/patterns/retry) je technika, která opakuje operaci s exponenciálně zvyšující čekací dobou, až do maximálního počtu opakování bylo dosaženo [(exponenciální backoff](https://en.wikipedia.org/wiki/Exponential_backoff)). Tato technika zahrnuje skutečnost, že cloudové prostředky může být občas k dispozici pro více než několik sekund z jakéhokoli důvodu. Například orchestrator může být přesunutí kontejneru do jiného uzlu v clusteru pro vyrovnávání zatížení. Během této doby může dojít k selhání některých požadavků. Dalším příkladem může být databáze jako SQL Azure, kde databáze lze přesunout na jiný server pro vyrovnávání zatížení, což způsobí, že databáze nebude k dispozici po dobu několika sekund.

Existuje mnoho přístupů k implementaci logiky opakování s exponenciální mantinely.

>[!div class="step-by-step"]
>[Předchozí](partial-failure-strategies.md)
>[další](implement-resilient-entity-framework-core-sql-connections.md)
