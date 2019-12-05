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
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="19fb1-103">Možnosti konfigurace běhu pro kompilaci</span><span class="sxs-lookup"><span data-stu-id="19fb1-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="19fb1-104">Vrstvená kompilace</span><span class="sxs-lookup"><span data-stu-id="19fb1-104">Tiered compilation</span></span>

- <span data-ttu-id="19fb1-105">Konfiguruje, zda kompilátor JIT používá [vrstvenou kompilaci](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="19fb1-105">Configures whether the JIT compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span>
- <span data-ttu-id="19fb1-106">V rozhraní .NET Core 3,0 a novějších je vrstvená kompilace ve výchozím nastavení povolená.</span><span class="sxs-lookup"><span data-stu-id="19fb1-106">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="19fb1-107">V .NET Core 2,1 a 2,2 je vrstvená kompilace ve výchozím nastavení zakázaná.</span><span class="sxs-lookup"><span data-stu-id="19fb1-107">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>

| | <span data-ttu-id="19fb1-108">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="19fb1-108">Setting name</span></span> | <span data-ttu-id="19fb1-109">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="19fb1-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="19fb1-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="19fb1-110">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="19fb1-111">`true` – povoleno</span><span class="sxs-lookup"><span data-stu-id="19fb1-111">`true` - enabled</span></span><br/><span data-ttu-id="19fb1-112">`false` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="19fb1-112">`false` - disabled</span></span> |
| <span data-ttu-id="19fb1-113">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="19fb1-113">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="19fb1-114">`1` – povoleno</span><span class="sxs-lookup"><span data-stu-id="19fb1-114">`1` - enabled</span></span><br/><span data-ttu-id="19fb1-115">`0` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="19fb1-115">`0` - disabled</span></span> |
