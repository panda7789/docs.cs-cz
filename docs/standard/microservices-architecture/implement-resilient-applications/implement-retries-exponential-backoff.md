---
title: Implementace opakování pomocí exponenciálního omezení rychlosti
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Implementace opakování pomocí exponenciálního omezení rychlosti
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: a5ab15299ecb501691c26bbc6d377e22a38ee51e
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874361"
---
# <a name="implement-retries-with-exponential-backoff"></a><span data-ttu-id="124a0-103">Implementace opakování pomocí exponenciálního omezení rychlosti</span><span class="sxs-lookup"><span data-stu-id="124a0-103">Implement retries with exponential backoff</span></span>

<span data-ttu-id="124a0-104">[*Opakování pomocí exponenciálního omezení rychlosti* ](https://docs.microsoft.com/azure/architecture/patterns/retry) je technika, která se pokusí o opakování operace, s exponenciálně rostoucím času čekání, dokud nedosáhne maximální počet opakování ( [exponenciálního omezení rychlosti](https://en.wikipedia.org/wiki/Exponential_backoff) ).</span><span class="sxs-lookup"><span data-stu-id="124a0-104">[*Retries with exponential backoff*](https://docs.microsoft.com/azure/architecture/patterns/retry) is a technique that attempts to retry an operation, with an exponentially increasing wait time, until a maximum retry count has been reached (the [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff)).</span></span> <span data-ttu-id="124a0-105">Tento postup poskytuje výkonný skutečnost, že cloudové prostředky přerušovaně pravděpodobně není k dispozici po dobu více než několik sekund z jakéhokoli důvodu.</span><span class="sxs-lookup"><span data-stu-id="124a0-105">This technique embraces the fact that cloud resources might intermittently be unavailable for more than a few seconds for any reason.</span></span> <span data-ttu-id="124a0-106">Například orchestrátor může být přechod kontejneru do jiného uzlu v clusteru služby Vyrovnávání zatížení.</span><span class="sxs-lookup"><span data-stu-id="124a0-106">For example, an orchestrator might be moving a container to another node in a cluster for load balancing.</span></span> <span data-ttu-id="124a0-107">Během této doby může selhat některé požadavky.</span><span class="sxs-lookup"><span data-stu-id="124a0-107">During that time, some requests might fail.</span></span> <span data-ttu-id="124a0-108">Dalším příkladem může být databáze jako SQL Azure, ve kterém databáze můžete přesunout na jiný server pro vyrovnávání zatížení, způsobuje, že databáze bude k dispozici pro několik sekund.</span><span class="sxs-lookup"><span data-stu-id="124a0-108">Another example could be a database like SQL Azure, where a database can be moved to another server for load balancing, causing the database to be unavailable for a few seconds.</span></span>

<span data-ttu-id="124a0-109">Existuje celá řada přístupů implementovat logiku opakování pomocí exponenciálního omezení rychlosti.</span><span class="sxs-lookup"><span data-stu-id="124a0-109">There are many approaches to implement retries logic with exponential backoff.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="124a0-110">[Předchozí](partial-failure-strategies.md)
[další](implement-resilient-entity-framework-core-sql-connections.md)</span><span class="sxs-lookup"><span data-stu-id="124a0-110">[Previous](partial-failure-strategies.md)
[Next](implement-resilient-entity-framework-core-sql-connections.md)</span></span>
