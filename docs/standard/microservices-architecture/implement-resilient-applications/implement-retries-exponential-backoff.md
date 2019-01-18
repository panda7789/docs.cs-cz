---
title: Implementace opakování pomocí exponenciálního omezení rychlosti
description: Zjistěte, jak implementovat opakování pomocí exponenciálního omezení rychlosti.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: 421a4535888f432974c764b238c06b5b323aefb3
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362077"
---
# <a name="implement-retries-with-exponential-backoff"></a><span data-ttu-id="378cb-103">Implementace opakování pomocí exponenciálního omezení rychlosti</span><span class="sxs-lookup"><span data-stu-id="378cb-103">Implement retries with exponential backoff</span></span>

<span data-ttu-id="378cb-104">[*Opakování pomocí exponenciálního omezení rychlosti* ](/azure/architecture/patterns/retry) je technika, která pokusů s exponenciálně rostoucím doba čekání, až maximální počet opakování operace, bylo dosaženo ( [exponenciálního omezení rychlosti](https://en.wikipedia.org/wiki/Exponential_backoff)).</span><span class="sxs-lookup"><span data-stu-id="378cb-104">[*Retries with exponential backoff*](/azure/architecture/patterns/retry) is a technique that retries an operation, with an exponentially increasing wait time, up to a maximum retry count has been reached (the [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff)).</span></span> <span data-ttu-id="378cb-105">Tento postup poskytuje výkonný skutečnost, že cloudové prostředky přerušovaně pravděpodobně není k dispozici po dobu více než několik sekund z jakéhokoli důvodu.</span><span class="sxs-lookup"><span data-stu-id="378cb-105">This technique embraces the fact that cloud resources might intermittently be unavailable for more than a few seconds for any reason.</span></span> <span data-ttu-id="378cb-106">Například orchestrátor může být přechod kontejneru do jiného uzlu v clusteru služby Vyrovnávání zatížení.</span><span class="sxs-lookup"><span data-stu-id="378cb-106">For example, an orchestrator might be moving a container to another node in a cluster for load balancing.</span></span> <span data-ttu-id="378cb-107">Během této doby může selhat některé požadavky.</span><span class="sxs-lookup"><span data-stu-id="378cb-107">During that time, some requests might fail.</span></span> <span data-ttu-id="378cb-108">Dalším příkladem může být databáze jako SQL Azure, ve kterém databáze můžete přesunout na jiný server pro vyrovnávání zatížení, způsobuje, že databáze bude k dispozici pro několik sekund.</span><span class="sxs-lookup"><span data-stu-id="378cb-108">Another example could be a database like SQL Azure, where a database can be moved to another server for load balancing, causing the database to be unavailable for a few seconds.</span></span>

<span data-ttu-id="378cb-109">Existuje celá řada přístupů implementovat logiku opakování pomocí exponenciálního omezení rychlosti.</span><span class="sxs-lookup"><span data-stu-id="378cb-109">There are many approaches to implement retries logic with exponential backoff.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="378cb-110">[Předchozí](partial-failure-strategies.md)
>[další](implement-resilient-entity-framework-core-sql-connections.md)</span><span class="sxs-lookup"><span data-stu-id="378cb-110">[Previous](partial-failure-strategies.md)
[Next](implement-resilient-entity-framework-core-sql-connections.md)</span></span>