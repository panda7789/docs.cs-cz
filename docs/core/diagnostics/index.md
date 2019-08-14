---
title: Přehled diagnostických nástrojů – .NET Core
description: Přehled nástrojů a technik, které jsou k dispozici pro diagnostiku aplikací .NET Core.
author: sdmaclea
ms.author: stmaclea
ms.date: 08/05/2019
ms.topic: overview
ms.openlocfilehash: f107d15fa5584bb5a4834b5f11f1096bec7eb749
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68974126"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a>Jaké diagnostické nástroje jsou k dispozici v .NET Core?

Software se vždy chová podle očekávání, ale rozhraní .NET Core obsahuje nástroje a rozhraní API, které vám pomohou rychle a efektivně diagnostikovat tyto problémy.

Tento článek vám pomůže najít různé nástroje, které potřebujete.

## <a name="managed-debuggersmanaged-debuggersmd"></a>[Spravované ladicí programy](managed-debuggers.md)
Spravované ladicí programy umožňují pracovat s programem. Pozastavení, přírůstkové provádění, prozkoumání a obnovení, vám poskytne přehled o chování kódu. Ladicí program je první volbou pro diagnostiku funkčních problémů, které je možné snadno reprodukovat.

## <a name="logging-and-tracinglogging-tracingmd"></a>[Protokolování a trasování](logging-tracing.md)
Protokolování a trasování jsou související techniky. Odkazují na instrumentaci kódu k vytváření souborů protokolu. Soubory zaznamenávají podrobnosti o tom, co program dělá. Pomocí těchto podrobností lze diagnostikovat nejsložitější problémy. V kombinaci s časovými razítky jsou tyto techniky také cenné při vyšetřování výkonu.

## <a name="unit-testingtestingindexmd"></a>[Testování jednotek](../testing/index.md)
Testování částí je klíčovou součástí kontinuální integrace a nasazování vysoce kvalitního softwaru. Testy jednotek jsou navržené tak, aby vám při přerušení nějakého upozornění poskytovala včasné varování.
