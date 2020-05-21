---
title: Nastavení konfigurace vláken
description: Přečtěte si o nastaveních prostředí runtime, která konfigurují vlákna pro aplikace .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 1c7c16993a07ef95223481791153b75ab2f61533
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761925"
---
# <a name="run-time-configuration-options-for-threading"></a><span data-ttu-id="59049-103">Možnosti konfigurace běhu pro dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="59049-103">Run-time configuration options for threading</span></span>

## <a name="cpu-groups"></a><span data-ttu-id="59049-104">Skupiny PROCESORů</span><span class="sxs-lookup"><span data-stu-id="59049-104">CPU groups</span></span>

- <span data-ttu-id="59049-105">Konfiguruje, zda jsou vlákna automaticky distribuována napříč skupinami PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="59049-105">Configures whether threads are automatically distributed across CPU groups.</span></span>
- <span data-ttu-id="59049-106">Pokud toto nastavení vynecháte, nebudou vlákna distribuována mezi skupiny PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="59049-106">If you omit this setting, threads are not distributed across CPU groups.</span></span> <span data-ttu-id="59049-107">To je ekvivalentní nastavení hodnoty na `0` .</span><span class="sxs-lookup"><span data-stu-id="59049-107">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="59049-108">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="59049-108">Setting name</span></span> | <span data-ttu-id="59049-109">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="59049-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="59049-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="59049-110">**runtimeconfig.json**</span></span> | <span data-ttu-id="59049-111">–</span><span class="sxs-lookup"><span data-stu-id="59049-111">N/A</span></span> | <span data-ttu-id="59049-112">–</span><span class="sxs-lookup"><span data-stu-id="59049-112">N/A</span></span> |
| <span data-ttu-id="59049-113">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="59049-113">**Environment variable**</span></span> | `COMPlus_Thread_UseAllCpuGroups` | <span data-ttu-id="59049-114">`0`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="59049-114">`0` - disabled</span></span><br/><span data-ttu-id="59049-115">`1`– povoleno</span><span class="sxs-lookup"><span data-stu-id="59049-115">`1` - enabled</span></span> |

## <a name="minimum-threads"></a><span data-ttu-id="59049-116">Minimální počet vláken</span><span class="sxs-lookup"><span data-stu-id="59049-116">Minimum threads</span></span>

- <span data-ttu-id="59049-117">Určuje minimální počet vláken pro fond pracovních vláken.</span><span class="sxs-lookup"><span data-stu-id="59049-117">Specifies the minimum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="59049-118">Odpovídá <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> metodě.</span><span class="sxs-lookup"><span data-stu-id="59049-118">Corresponds to the <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="59049-119">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="59049-119">Setting name</span></span> | <span data-ttu-id="59049-120">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="59049-120">Values</span></span> |
| - | - | - |
| <span data-ttu-id="59049-121">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="59049-121">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MinThreads` | <span data-ttu-id="59049-122">Celé číslo, které představuje minimální počet vláken</span><span class="sxs-lookup"><span data-stu-id="59049-122">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="59049-123">**Vlastnost MSBuild**</span><span class="sxs-lookup"><span data-stu-id="59049-123">**MSBuild property**</span></span> | `ThreadPoolMinThreads` | <span data-ttu-id="59049-124">Celé číslo, které představuje minimální počet vláken</span><span class="sxs-lookup"><span data-stu-id="59049-124">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="59049-125">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="59049-125">**Environment variable**</span></span> | <span data-ttu-id="59049-126">–</span><span class="sxs-lookup"><span data-stu-id="59049-126">N/A</span></span> | <span data-ttu-id="59049-127">–</span><span class="sxs-lookup"><span data-stu-id="59049-127">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="59049-128">Příklady</span><span class="sxs-lookup"><span data-stu-id="59049-128">Examples</span></span>

<span data-ttu-id="59049-129">soubor *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="59049-129">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MinThreads": 4
      }
   }
}
```

<span data-ttu-id="59049-130">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="59049-130">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>

</Project>
```

## <a name="maximum-threads"></a><span data-ttu-id="59049-131">Maximální počet vláken</span><span class="sxs-lookup"><span data-stu-id="59049-131">Maximum threads</span></span>

- <span data-ttu-id="59049-132">Určuje maximální počet vláken pro fond pracovních vláken.</span><span class="sxs-lookup"><span data-stu-id="59049-132">Specifies the maximum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="59049-133">Odpovídá <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> metodě.</span><span class="sxs-lookup"><span data-stu-id="59049-133">Corresponds to the <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="59049-134">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="59049-134">Setting name</span></span> | <span data-ttu-id="59049-135">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="59049-135">Values</span></span> |
| - | - | - |
| <span data-ttu-id="59049-136">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="59049-136">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MaxThreads` | <span data-ttu-id="59049-137">Celé číslo, které představuje maximální počet vláken</span><span class="sxs-lookup"><span data-stu-id="59049-137">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="59049-138">**Vlastnost MSBuild**</span><span class="sxs-lookup"><span data-stu-id="59049-138">**MSBuild property**</span></span> | `ThreadPoolMaxThreads` | <span data-ttu-id="59049-139">Celé číslo, které představuje maximální počet vláken</span><span class="sxs-lookup"><span data-stu-id="59049-139">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="59049-140">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="59049-140">**Environment variable**</span></span> | <span data-ttu-id="59049-141">–</span><span class="sxs-lookup"><span data-stu-id="59049-141">N/A</span></span> | <span data-ttu-id="59049-142">–</span><span class="sxs-lookup"><span data-stu-id="59049-142">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="59049-143">Příklady</span><span class="sxs-lookup"><span data-stu-id="59049-143">Examples</span></span>

<span data-ttu-id="59049-144">soubor *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="59049-144">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MaxThreads": 20
      }
   }
}
```

<span data-ttu-id="59049-145">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="59049-145">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```
