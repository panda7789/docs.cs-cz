---
title: Implementace opakování pomocí exponenciálního omezení rychlosti
description: Zjistěte, jak implementovat opakování pomocí exponenciálního omezení rychlosti.
ms.date: 10/16/2018
ms.openlocfilehash: 1b948e399495eeb12016006442ac08d2b04f2e69
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644237"
---
# <a name="implement-retries-with-exponential-backoff"></a>Implementace opakování pomocí exponenciálního omezení rychlosti

[*Opakování pomocí exponenciálního omezení rychlosti* ](/azure/architecture/patterns/retry) je technika, která pokusů s exponenciálně rostoucím doba čekání, až maximální počet opakování operace, bylo dosaženo ( [exponenciálního omezení rychlosti](https://en.wikipedia.org/wiki/Exponential_backoff)). Tento postup poskytuje výkonný skutečnost, že cloudové prostředky přerušovaně pravděpodobně není k dispozici po dobu více než několik sekund z jakéhokoli důvodu. Například orchestrátor může být přechod kontejneru do jiného uzlu v clusteru služby Vyrovnávání zatížení. Během této doby může selhat některé požadavky. Dalším příkladem může být databáze jako SQL Azure, ve kterém databáze můžete přesunout na jiný server pro vyrovnávání zatížení, způsobuje, že databáze bude k dispozici pro několik sekund.

Existuje celá řada přístupů implementovat logiku opakování pomocí exponenciálního omezení rychlosti.

>[!div class="step-by-step"]
>[Předchozí](partial-failure-strategies.md)
>[další](implement-resilient-entity-framework-core-sql-connections.md)
