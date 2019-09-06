---
title: Implementace opakovaných pokusů pomocí exponenciálního omezení rychlostiu
description: Naučte se implementovat opakování pomocí exponenciálního omezení rychlostiu.
ms.date: 10/16/2018
ms.openlocfilehash: 1b948e399495eeb12016006442ac08d2b04f2e69
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296063"
---
# <a name="implement-retries-with-exponential-backoff"></a><span data-ttu-id="676dd-103">Implementace opakovaných pokusů pomocí exponenciálního omezení rychlostiu</span><span class="sxs-lookup"><span data-stu-id="676dd-103">Implement retries with exponential backoff</span></span>

<span data-ttu-id="676dd-104">[*Opakování s exponenciálním omezení rychlosti*](/azure/architecture/patterns/retry) je technika, která opakuje operaci s exponenciálním zvýšením doby čekání, až do maximálního počtu opakování ( [exponenciální omezení rychlosti](https://en.wikipedia.org/wiki/Exponential_backoff)).</span><span class="sxs-lookup"><span data-stu-id="676dd-104">[*Retries with exponential backoff*](/azure/architecture/patterns/retry) is a technique that retries an operation, with an exponentially increasing wait time, up to a maximum retry count has been reached (the [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff)).</span></span> <span data-ttu-id="676dd-105">Tato technika zahrnuje skutečnost, že cloudové prostředky můžou být z jakéhokoli důvodu občas nedostupné po dobu delší než pár sekund.</span><span class="sxs-lookup"><span data-stu-id="676dd-105">This technique embraces the fact that cloud resources might intermittently be unavailable for more than a few seconds for any reason.</span></span> <span data-ttu-id="676dd-106">Například produkt Orchestrator může přesunout kontejner do jiného uzlu v clusteru pro vyrovnávání zatížení.</span><span class="sxs-lookup"><span data-stu-id="676dd-106">For example, an orchestrator might be moving a container to another node in a cluster for load balancing.</span></span> <span data-ttu-id="676dd-107">Během této doby může dojít k selhání některých požadavků.</span><span class="sxs-lookup"><span data-stu-id="676dd-107">During that time, some requests might fail.</span></span> <span data-ttu-id="676dd-108">Dalším příkladem může být databáze, jako je například SQL Azure, kde je možné databázi přesunout na jiný server pro vyrovnávání zatížení, což způsobí, že databáze bude během několika sekund nedostupná.</span><span class="sxs-lookup"><span data-stu-id="676dd-108">Another example could be a database like SQL Azure, where a database can be moved to another server for load balancing, causing the database to be unavailable for a few seconds.</span></span>

<span data-ttu-id="676dd-109">Existuje mnoho přístupů k implementaci logiky opakování pomocí exponenciálního omezení rychlostiu.</span><span class="sxs-lookup"><span data-stu-id="676dd-109">There are many approaches to implement retries logic with exponential backoff.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="676dd-110">[Předchozí](partial-failure-strategies.md)Další
>[](implement-resilient-entity-framework-core-sql-connections.md)</span><span class="sxs-lookup"><span data-stu-id="676dd-110">[Previous](partial-failure-strategies.md)
[Next](implement-resilient-entity-framework-core-sql-connections.md)</span></span>
