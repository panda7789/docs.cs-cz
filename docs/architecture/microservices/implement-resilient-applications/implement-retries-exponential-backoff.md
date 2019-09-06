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
# <a name="implement-retries-with-exponential-backoff"></a>Implementace opakovaných pokusů pomocí exponenciálního omezení rychlostiu

[*Opakování s exponenciálním omezení rychlosti*](/azure/architecture/patterns/retry) je technika, která opakuje operaci s exponenciálním zvýšením doby čekání, až do maximálního počtu opakování ( [exponenciální omezení rychlosti](https://en.wikipedia.org/wiki/Exponential_backoff)). Tato technika zahrnuje skutečnost, že cloudové prostředky můžou být z jakéhokoli důvodu občas nedostupné po dobu delší než pár sekund. Například produkt Orchestrator může přesunout kontejner do jiného uzlu v clusteru pro vyrovnávání zatížení. Během této doby může dojít k selhání některých požadavků. Dalším příkladem může být databáze, jako je například SQL Azure, kde je možné databázi přesunout na jiný server pro vyrovnávání zatížení, což způsobí, že databáze bude během několika sekund nedostupná.

Existuje mnoho přístupů k implementaci logiky opakování pomocí exponenciálního omezení rychlostiu.

>[!div class="step-by-step"]
>[Předchozí](partial-failure-strategies.md)Další
>[](implement-resilient-entity-framework-core-sql-connections.md)
