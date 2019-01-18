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
# <a name="implement-retries-with-exponential-backoff"></a>Implementace opakování pomocí exponenciálního omezení rychlosti

[*Opakování pomocí exponenciálního omezení rychlosti* ](/azure/architecture/patterns/retry) je technika, která pokusů s exponenciálně rostoucím doba čekání, až maximální počet opakování operace, bylo dosaženo ( [exponenciálního omezení rychlosti](https://en.wikipedia.org/wiki/Exponential_backoff)). Tento postup poskytuje výkonný skutečnost, že cloudové prostředky přerušovaně pravděpodobně není k dispozici po dobu více než několik sekund z jakéhokoli důvodu. Například orchestrátor může být přechod kontejneru do jiného uzlu v clusteru služby Vyrovnávání zatížení. Během této doby může selhat některé požadavky. Dalším příkladem může být databáze jako SQL Azure, ve kterém databáze můžete přesunout na jiný server pro vyrovnávání zatížení, způsobuje, že databáze bude k dispozici pro několik sekund.

Existuje celá řada přístupů implementovat logiku opakování pomocí exponenciálního omezení rychlosti.

>[!div class="step-by-step"]
>[Předchozí](partial-failure-strategies.md)
>[další](implement-resilient-entity-framework-core-sql-connections.md)