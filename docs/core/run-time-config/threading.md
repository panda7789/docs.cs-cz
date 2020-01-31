---
title: Nastavení konfigurace vláken
description: Přečtěte si o nastaveních prostředí runtime, která konfigurují vlákna pro aplikace .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 68b8e93ca6ec3f708a7a627307655ada1955500a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789853"
---
# <a name="run-time-configuration-options-for-threading"></a><span data-ttu-id="fa06c-103">Možnosti konfigurace běhu pro dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="fa06c-103">Run-time configuration options for threading</span></span>

## <a name="cpu-groups"></a><span data-ttu-id="fa06c-104">Skupiny PROCESORů</span><span class="sxs-lookup"><span data-stu-id="fa06c-104">CPU groups</span></span>

- <span data-ttu-id="fa06c-105">Konfiguruje, zda jsou vlákna automaticky distribuována napříč skupinami PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="fa06c-105">Configures whether threads are automatically distributed across CPU groups.</span></span>
- <span data-ttu-id="fa06c-106">Výchozí: zakázáno (`0`).</span><span class="sxs-lookup"><span data-stu-id="fa06c-106">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="fa06c-107">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="fa06c-107">Setting name</span></span> | <span data-ttu-id="fa06c-108">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="fa06c-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="fa06c-109">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="fa06c-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="fa06c-110">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="fa06c-110">N/A</span></span> | <span data-ttu-id="fa06c-111">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="fa06c-111">N/A</span></span> |
| <span data-ttu-id="fa06c-112">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="fa06c-112">**Environment variable**</span></span> | `COMPlus_Thread_UseAllCpuGroups` | <span data-ttu-id="fa06c-113">`0` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="fa06c-113">`0` - disabled</span></span><br/><span data-ttu-id="fa06c-114">`1` – povoleno</span><span class="sxs-lookup"><span data-stu-id="fa06c-114">`1` - enabled</span></span> |

## <a name="minimum-threads"></a><span data-ttu-id="fa06c-115">Minimální počet vláken</span><span class="sxs-lookup"><span data-stu-id="fa06c-115">Minimum threads</span></span>

- <span data-ttu-id="fa06c-116">Určuje minimální počet vláken pro fond pracovních vláken.</span><span class="sxs-lookup"><span data-stu-id="fa06c-116">Specifies the minimum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="fa06c-117">Odpovídá metodě <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fa06c-117">Corresponds to the <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="fa06c-118">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="fa06c-118">Setting name</span></span> | <span data-ttu-id="fa06c-119">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="fa06c-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="fa06c-120">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="fa06c-120">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MinThreads` | <span data-ttu-id="fa06c-121">Celé číslo, které představuje minimální počet vláken</span><span class="sxs-lookup"><span data-stu-id="fa06c-121">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="fa06c-122">**Vlastnost MSBuild**</span><span class="sxs-lookup"><span data-stu-id="fa06c-122">**MSBuild property**</span></span> | `ThreadPoolMinThreads` | <span data-ttu-id="fa06c-123">Celé číslo, které představuje minimální počet vláken</span><span class="sxs-lookup"><span data-stu-id="fa06c-123">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="fa06c-124">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="fa06c-124">**Environment variable**</span></span> | <span data-ttu-id="fa06c-125">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="fa06c-125">N/A</span></span> | <span data-ttu-id="fa06c-126">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="fa06c-126">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="fa06c-127">Příklady</span><span class="sxs-lookup"><span data-stu-id="fa06c-127">Examples</span></span>

<span data-ttu-id="fa06c-128">soubor *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="fa06c-128">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MinThreads": 4
      }
   }
}
```

<span data-ttu-id="fa06c-129">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="fa06c-129">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>

</Project>
```

## <a name="maximum-threads"></a><span data-ttu-id="fa06c-130">Maximální počet vláken</span><span class="sxs-lookup"><span data-stu-id="fa06c-130">Maximum threads</span></span>

- <span data-ttu-id="fa06c-131">Určuje maximální počet vláken pro fond pracovních vláken.</span><span class="sxs-lookup"><span data-stu-id="fa06c-131">Specifies the maximum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="fa06c-132">Odpovídá metodě <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fa06c-132">Corresponds to the <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="fa06c-133">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="fa06c-133">Setting name</span></span> | <span data-ttu-id="fa06c-134">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="fa06c-134">Values</span></span> |
| - | - | - |
| <span data-ttu-id="fa06c-135">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="fa06c-135">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MaxThreads` | <span data-ttu-id="fa06c-136">Celé číslo, které představuje maximální počet vláken</span><span class="sxs-lookup"><span data-stu-id="fa06c-136">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="fa06c-137">**Vlastnost MSBuild**</span><span class="sxs-lookup"><span data-stu-id="fa06c-137">**MSBuild property**</span></span> | `ThreadPoolMaxThreads` | <span data-ttu-id="fa06c-138">Celé číslo, které představuje maximální počet vláken</span><span class="sxs-lookup"><span data-stu-id="fa06c-138">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="fa06c-139">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="fa06c-139">**Environment variable**</span></span> | <span data-ttu-id="fa06c-140">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="fa06c-140">N/A</span></span> | <span data-ttu-id="fa06c-141">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="fa06c-141">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="fa06c-142">Příklady</span><span class="sxs-lookup"><span data-stu-id="fa06c-142">Examples</span></span>

<span data-ttu-id="fa06c-143">soubor *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="fa06c-143">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MaxThreads": 20
      }
   }
}
```

<span data-ttu-id="fa06c-144">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="fa06c-144">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```
