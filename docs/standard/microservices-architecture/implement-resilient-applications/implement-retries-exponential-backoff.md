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
# <a name="implementing-retries-with-exponential-backoff"></a>Implementace opakování s exponenciálního omezení rychlosti

[*Opakuje se exponenciálního omezení rychlosti* ](https://docs.microsoft.com/azure/architecture/patterns/retry) je technika, který se pokouší opakovat operace, exponenciálně roste doba čekání, dokud nedosáhne maximální počet opakování ( [exponenciálního omezení rychlosti](https://en.wikipedia.org/wiki/Exponential_backoff) ). Tento postup zahrnuje fakt, že cloudové prostředky občas je pravděpodobně není k dispozici více než několik sekund z jakéhokoli důvodu. Například orchestrator může být přesunutí kontejner do jiného uzlu v clusteru s podporou pro vyrovnávání zatížení. Během této doby může selhat některé požadavky. Dalším příkladem může být databáze jako SQL Azure, kde databáze můžete přesunout na jiný server pro zatížení vyrovnávání, což databáze má k dispozici pro několik sekund.

Existuje mnoho přístupů implementovat logiku opakovaných pokusů s exponenciálního omezení rychlosti.


>[!div class="step-by-step"]
[Předchozí](partial-failure-strategies.md)
[další](implement-resilient-entity-framework-core-sql-connections.md)
