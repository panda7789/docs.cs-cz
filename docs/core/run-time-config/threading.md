---
title: Nastavení konfigurace vláken
description: Přečtěte si o nastaveních prostředí runtime, která konfigurují vlákna pro aplikace .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 6a920dbc301830e3f4c95bf637ff3de6d4f464ff
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802762"
---
# <a name="run-time-configuration-options-for-threading"></a><span data-ttu-id="f34ee-103">Možnosti konfigurace běhu pro dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="f34ee-103">Run-time configuration options for threading</span></span>

## <a name="cpu-groups"></a><span data-ttu-id="f34ee-104">Skupiny PROCESORů</span><span class="sxs-lookup"><span data-stu-id="f34ee-104">CPU groups</span></span>

- <span data-ttu-id="f34ee-105">Konfiguruje, zda jsou vlákna automaticky distribuována napříč skupinami PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="f34ee-105">Configures whether threads are automatically distributed across CPU groups.</span></span>
- <span data-ttu-id="f34ee-106">Výchozí: zakázáno (`0`).</span><span class="sxs-lookup"><span data-stu-id="f34ee-106">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="f34ee-107">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="f34ee-107">Setting name</span></span> | <span data-ttu-id="f34ee-108">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="f34ee-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="f34ee-109">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="f34ee-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="f34ee-110">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="f34ee-110">N/A</span></span> | <span data-ttu-id="f34ee-111">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="f34ee-111">N/A</span></span> |
| <span data-ttu-id="f34ee-112">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="f34ee-112">**Environment variable**</span></span> | `COMPlus_Thread_UseAllCpuGroups` | <span data-ttu-id="f34ee-113">`0` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="f34ee-113">`0` - disabled</span></span><br/><span data-ttu-id="f34ee-114">`1` – povoleno</span><span class="sxs-lookup"><span data-stu-id="f34ee-114">`1` - enabled</span></span> |

## <a name="minimum-threads"></a><span data-ttu-id="f34ee-115">Minimální počet vláken</span><span class="sxs-lookup"><span data-stu-id="f34ee-115">Minimum threads</span></span>

- <span data-ttu-id="f34ee-116">Určuje minimální počet vláken pro nepracovní podproces pracovního procesu.</span><span class="sxs-lookup"><span data-stu-id="f34ee-116">Specifies the minimum number of threads for the worker threadpool.</span></span>
- <span data-ttu-id="f34ee-117">Odpovídá metodě <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f34ee-117">Corresponds to the <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="f34ee-118">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="f34ee-118">Setting name</span></span> | <span data-ttu-id="f34ee-119">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="f34ee-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="f34ee-120">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="f34ee-120">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MinThreads` | <span data-ttu-id="f34ee-121">Celé číslo, které představuje minimální počet vláken</span><span class="sxs-lookup"><span data-stu-id="f34ee-121">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="f34ee-122">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="f34ee-122">**Environment variable**</span></span> | <span data-ttu-id="f34ee-123">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="f34ee-123">N/A</span></span> | <span data-ttu-id="f34ee-124">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="f34ee-124">N/A</span></span> |

## <a name="maximum-threads"></a><span data-ttu-id="f34ee-125">Maximální počet vláken</span><span class="sxs-lookup"><span data-stu-id="f34ee-125">Maximum threads</span></span>

- <span data-ttu-id="f34ee-126">Určuje maximální počet vláken pro vlákno pracovního procesu.</span><span class="sxs-lookup"><span data-stu-id="f34ee-126">Specifies the maximum number of threads for the worker threadpool.</span></span>
- <span data-ttu-id="f34ee-127">Odpovídá metodě <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f34ee-127">Corresponds to the <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="f34ee-128">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="f34ee-128">Setting name</span></span> | <span data-ttu-id="f34ee-129">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="f34ee-129">Values</span></span> |
| - | - | - |
| <span data-ttu-id="f34ee-130">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="f34ee-130">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MaxThreads` | <span data-ttu-id="f34ee-131">Celé číslo, které představuje maximální počet vláken</span><span class="sxs-lookup"><span data-stu-id="f34ee-131">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="f34ee-132">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="f34ee-132">**Environment variable**</span></span> | <span data-ttu-id="f34ee-133">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="f34ee-133">N/A</span></span> | <span data-ttu-id="f34ee-134">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="f34ee-134">N/A</span></span> |
