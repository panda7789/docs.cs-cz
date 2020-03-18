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
# <a name="implement-retries-with-exponential-backoff"></a><span data-ttu-id="5207b-103">Implementace opakovaných pokusů s exponenciálním backoffem</span><span class="sxs-lookup"><span data-stu-id="5207b-103">Implement retries with exponential backoff</span></span>

<span data-ttu-id="5207b-104">[*Opakování s exponenciálním podčasovým vypnutím*](/azure/architecture/patterns/retry) je technika, která opakuje operaci s exponenciálně zvyšující čekací dobou, až do maximálního počtu opakování bylo dosaženo [(exponenciální backoff](https://en.wikipedia.org/wiki/Exponential_backoff)).</span><span class="sxs-lookup"><span data-stu-id="5207b-104">[*Retries with exponential backoff*](/azure/architecture/patterns/retry) is a technique that retries an operation, with an exponentially increasing wait time, up to a maximum retry count has been reached (the [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff)).</span></span> <span data-ttu-id="5207b-105">Tato technika zahrnuje skutečnost, že cloudové prostředky může být občas k dispozici pro více než několik sekund z jakéhokoli důvodu.</span><span class="sxs-lookup"><span data-stu-id="5207b-105">This technique embraces the fact that cloud resources might intermittently be unavailable for more than a few seconds for any reason.</span></span> <span data-ttu-id="5207b-106">Například orchestrator může být přesunutí kontejneru do jiného uzlu v clusteru pro vyrovnávání zatížení.</span><span class="sxs-lookup"><span data-stu-id="5207b-106">For example, an orchestrator might be moving a container to another node in a cluster for load balancing.</span></span> <span data-ttu-id="5207b-107">Během této doby může dojít k selhání některých požadavků.</span><span class="sxs-lookup"><span data-stu-id="5207b-107">During that time, some requests might fail.</span></span> <span data-ttu-id="5207b-108">Dalším příkladem může být databáze jako SQL Azure, kde databáze lze přesunout na jiný server pro vyrovnávání zatížení, což způsobí, že databáze nebude k dispozici po dobu několika sekund.</span><span class="sxs-lookup"><span data-stu-id="5207b-108">Another example could be a database like SQL Azure, where a database can be moved to another server for load balancing, causing the database to be unavailable for a few seconds.</span></span>

<span data-ttu-id="5207b-109">Existuje mnoho přístupů k implementaci logiky opakování s exponenciální mantinely.</span><span class="sxs-lookup"><span data-stu-id="5207b-109">There are many approaches to implement retries logic with exponential backoff.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5207b-110">[Předchozí](partial-failure-strategies.md)
>[další](implement-resilient-entity-framework-core-sql-connections.md)</span><span class="sxs-lookup"><span data-stu-id="5207b-110">[Previous](partial-failure-strategies.md)
[Next](implement-resilient-entity-framework-core-sql-connections.md)</span></span>
