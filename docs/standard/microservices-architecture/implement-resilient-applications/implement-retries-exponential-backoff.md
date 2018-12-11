---
title: Implementace opakování pomocí exponenciálního omezení rychlosti
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Implementace opakování pomocí exponenciálního omezení rychlosti
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: e0758ee8fe28cb45ecd35ad07ddc738c12614973
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148766"
---
# <a name="implement-retries-with-exponential-backoff"></a>Implementace opakování pomocí exponenciálního omezení rychlosti

[*Opakování pomocí exponenciálního omezení rychlosti* ](https://docs.microsoft.com/azure/architecture/patterns/retry) je technika, která se pokusí o opakování operace, s exponenciálně rostoucím času čekání, dokud nedosáhne maximální počet opakování ( [exponenciálního omezení rychlosti](https://en.wikipedia.org/wiki/Exponential_backoff) ). Tento postup poskytuje výkonný skutečnost, že cloudové prostředky přerušovaně pravděpodobně není k dispozici po dobu více než několik sekund z jakéhokoli důvodu. Například orchestrátor může být přechod kontejneru do jiného uzlu v clusteru služby Vyrovnávání zatížení. Během této doby může selhat některé požadavky. Dalším příkladem může být databáze jako SQL Azure, ve kterém databáze můžete přesunout na jiný server pro vyrovnávání zatížení, způsobuje, že databáze bude k dispozici pro několik sekund.

Existuje celá řada přístupů implementovat logiku opakování pomocí exponenciálního omezení rychlosti.

>[!div class="step-by-step"]
>[Předchozí](partial-failure-strategies.md)
>[další](implement-resilient-entity-framework-core-sql-connections.md)