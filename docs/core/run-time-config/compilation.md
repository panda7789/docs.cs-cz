---
title: Konfigurační nastavení kompilace
description: Přečtěte si o nastaveních modulu runtime, která konfigurují, jak kompilátor JIT funguje pro aplikace .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: bcc445b6edc48d9432ee614b0b19c9c25621f4a0
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802818"
---
# <a name="run-time-configuration-options-for-compilation"></a>Možnosti konfigurace běhu pro kompilaci

## <a name="tiered-compilation"></a>Vrstvená kompilace

- Konfiguruje, zda kompilátor JIT používá [vrstvenou kompilaci](../whats-new/dotnet-core-3-0.md#tiered-compilation).
- V rozhraní .NET Core 3,0 a novějších je vrstvená kompilace ve výchozím nastavení povolená.
- V .NET Core 2,1 a 2,2 je vrstvená kompilace ve výchozím nastavení zakázaná.

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | `System.Runtime.TieredCompilation` | `true` – povoleno<br/>`false` – zakázáno |
| **Proměnná prostředí** | `COMPlus_TieredCompilation` | `1` – povoleno<br/>`0` – zakázáno |
