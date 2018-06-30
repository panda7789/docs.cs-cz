---
title: Implementace opakování s exponenciálního omezení rychlosti
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace opakování s exponenciálního omezení rychlosti
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: ee5dd711484ba7861eedbd9613fda1209736d5b6
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106915"
---
# <a name="implementing-retries-with-exponential-backoff"></a><span data-ttu-id="b58e3-103">Implementace opakování s exponenciálního omezení rychlosti</span><span class="sxs-lookup"><span data-stu-id="b58e3-103">Implementing retries with exponential backoff</span></span>

<span data-ttu-id="b58e3-104">[*Opakuje se exponenciálního omezení rychlosti* ](https://docs.microsoft.com/azure/architecture/patterns/retry) je technika, který se pokouší opakovat operace, exponenciálně roste doba čekání, dokud nedosáhne maximální počet opakování ( [exponenciálního omezení rychlosti](https://en.wikipedia.org/wiki/Exponential_backoff) ).</span><span class="sxs-lookup"><span data-stu-id="b58e3-104">[*Retries with exponential backoff*](https://docs.microsoft.com/azure/architecture/patterns/retry) is a technique that attempts to retry an operation, with an exponentially increasing wait time, until a maximum retry count has been reached (the [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff)).</span></span> <span data-ttu-id="b58e3-105">Tento postup zahrnuje fakt, že cloudové prostředky občas je pravděpodobně není k dispozici více než několik sekund z jakéhokoli důvodu.</span><span class="sxs-lookup"><span data-stu-id="b58e3-105">This technique embraces the fact that cloud resources might intermittently be unavailable for more than a few seconds for any reason.</span></span> <span data-ttu-id="b58e3-106">Například orchestrator může být přesunutí kontejner do jiného uzlu v clusteru s podporou pro vyrovnávání zatížení.</span><span class="sxs-lookup"><span data-stu-id="b58e3-106">For example, an orchestrator might be moving a container to another node in a cluster for load balancing.</span></span> <span data-ttu-id="b58e3-107">Během této doby může selhat některé požadavky.</span><span class="sxs-lookup"><span data-stu-id="b58e3-107">During that time, some requests might fail.</span></span> <span data-ttu-id="b58e3-108">Dalším příkladem může být databáze jako SQL Azure, kde databáze můžete přesunout na jiný server pro zatížení vyrovnávání, což databáze má k dispozici pro několik sekund.</span><span class="sxs-lookup"><span data-stu-id="b58e3-108">Another example could be a database like SQL Azure, where a database can be moved to another server for load balancing, causing the database to be unavailable for a few seconds.</span></span>

<span data-ttu-id="b58e3-109">Existuje mnoho přístupů implementovat logiku opakovaných pokusů s exponenciálního omezení rychlosti.</span><span class="sxs-lookup"><span data-stu-id="b58e3-109">There are many approaches to implement retries logic with exponential backoff.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="b58e3-110">[Předchozí](partial-failure-strategies.md)
[další](implement-resilient-entity-framework-core-sql-connections.md)</span><span class="sxs-lookup"><span data-stu-id="b58e3-110">[Previous](partial-failure-strategies.md)
[Next](implement-resilient-entity-framework-core-sql-connections.md)</span></span>
