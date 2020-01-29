---
title: Nastavení konfigurace vláken
description: Přečtěte si o nastaveních prostředí runtime, která konfigurují vlákna pro aplikace .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: ed7688d4d8f7178440fe59afc6e2f5e0a11b2a5c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733430"
---
# <a name="run-time-configuration-options-for-threading"></a><span data-ttu-id="b4c8d-103">Možnosti konfigurace běhu pro dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="b4c8d-103">Run-time configuration options for threading</span></span>

## <a name="cpu-groups"></a><span data-ttu-id="b4c8d-104">Skupiny PROCESORů</span><span class="sxs-lookup"><span data-stu-id="b4c8d-104">CPU groups</span></span>

- <span data-ttu-id="b4c8d-105">Konfiguruje, zda jsou vlákna automaticky distribuována napříč skupinami PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="b4c8d-105">Configures whether threads are automatically distributed across CPU groups.</span></span>
- <span data-ttu-id="b4c8d-106">Výchozí: zakázáno (`0`).</span><span class="sxs-lookup"><span data-stu-id="b4c8d-106">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="b4c8d-107">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="b4c8d-107">Setting name</span></span> | <span data-ttu-id="b4c8d-108">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="b4c8d-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="b4c8d-109">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="b4c8d-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="b4c8d-110">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="b4c8d-110">N/A</span></span> | <span data-ttu-id="b4c8d-111">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="b4c8d-111">N/A</span></span> |
| <span data-ttu-id="b4c8d-112">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="b4c8d-112">**Environment variable**</span></span> | `COMPlus_Thread_UseAllCpuGroups` | <span data-ttu-id="b4c8d-113">`0` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="b4c8d-113">`0` - disabled</span></span><br/><span data-ttu-id="b4c8d-114">`1` – povoleno</span><span class="sxs-lookup"><span data-stu-id="b4c8d-114">`1` - enabled</span></span> |

## <a name="minimum-threads"></a><span data-ttu-id="b4c8d-115">Minimální počet vláken</span><span class="sxs-lookup"><span data-stu-id="b4c8d-115">Minimum threads</span></span>

- <span data-ttu-id="b4c8d-116">Určuje minimální počet vláken pro nepracovní podproces pracovního procesu.</span><span class="sxs-lookup"><span data-stu-id="b4c8d-116">Specifies the minimum number of threads for the worker threadpool.</span></span>
- <span data-ttu-id="b4c8d-117">Odpovídá metodě <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b4c8d-117">Corresponds to the <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="b4c8d-118">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="b4c8d-118">Setting name</span></span> | <span data-ttu-id="b4c8d-119">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="b4c8d-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="b4c8d-120">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="b4c8d-120">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MinThreads` | <span data-ttu-id="b4c8d-121">Celé číslo, které představuje minimální počet vláken</span><span class="sxs-lookup"><span data-stu-id="b4c8d-121">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="b4c8d-122">**Vlastnost MSBuild**</span><span class="sxs-lookup"><span data-stu-id="b4c8d-122">**MSBuild property**</span></span> | `ThreadPoolMinThreads` | <span data-ttu-id="b4c8d-123">Celé číslo, které představuje minimální počet vláken</span><span class="sxs-lookup"><span data-stu-id="b4c8d-123">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="b4c8d-124">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="b4c8d-124">**Environment variable**</span></span> | <span data-ttu-id="b4c8d-125">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="b4c8d-125">N/A</span></span> | <span data-ttu-id="b4c8d-126">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="b4c8d-126">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="b4c8d-127">Příklady</span><span class="sxs-lookup"><span data-stu-id="b4c8d-127">Examples</span></span>

<span data-ttu-id="b4c8d-128">soubor *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="b4c8d-128">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MinThreads": 4
      }
   }
}
```

<span data-ttu-id="b4c8d-129">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="b4c8d-129">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>

</Project>
```

## <a name="maximum-threads"></a><span data-ttu-id="b4c8d-130">Maximální počet vláken</span><span class="sxs-lookup"><span data-stu-id="b4c8d-130">Maximum threads</span></span>

- <span data-ttu-id="b4c8d-131">Určuje maximální počet vláken pro vlákno pracovního procesu.</span><span class="sxs-lookup"><span data-stu-id="b4c8d-131">Specifies the maximum number of threads for the worker threadpool.</span></span>
- <span data-ttu-id="b4c8d-132">Odpovídá metodě <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b4c8d-132">Corresponds to the <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="b4c8d-133">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="b4c8d-133">Setting name</span></span> | <span data-ttu-id="b4c8d-134">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="b4c8d-134">Values</span></span> |
| - | - | - |
| <span data-ttu-id="b4c8d-135">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="b4c8d-135">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MaxThreads` | <span data-ttu-id="b4c8d-136">Celé číslo, které představuje maximální počet vláken</span><span class="sxs-lookup"><span data-stu-id="b4c8d-136">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="b4c8d-137">**Vlastnost MSBuild**</span><span class="sxs-lookup"><span data-stu-id="b4c8d-137">**MSBuild property**</span></span> | `ThreadPoolMaxThreads` | <span data-ttu-id="b4c8d-138">Celé číslo, které představuje maximální počet vláken</span><span class="sxs-lookup"><span data-stu-id="b4c8d-138">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="b4c8d-139">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="b4c8d-139">**Environment variable**</span></span> | <span data-ttu-id="b4c8d-140">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="b4c8d-140">N/A</span></span> | <span data-ttu-id="b4c8d-141">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="b4c8d-141">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="b4c8d-142">Příklady</span><span class="sxs-lookup"><span data-stu-id="b4c8d-142">Examples</span></span>

<span data-ttu-id="b4c8d-143">soubor *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="b4c8d-143">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MaxThreads": 20
      }
   }
}
```

<span data-ttu-id="b4c8d-144">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="b4c8d-144">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```
