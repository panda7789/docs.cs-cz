---
title: Nastavení konfigurace zřetězení
description: Přečtěte si o nastavení za běhu, které konfigurují zřetězení pro aplikace .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 68b8e93ca6ec3f708a7a627307655ada1955500a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789853"
---
# <a name="run-time-configuration-options-for-threading"></a><span data-ttu-id="975bf-103">Možnosti konfigurace za běhu pro zřetězení</span><span class="sxs-lookup"><span data-stu-id="975bf-103">Run-time configuration options for threading</span></span>

## <a name="cpu-groups"></a><span data-ttu-id="975bf-104">Skupiny procesorů</span><span class="sxs-lookup"><span data-stu-id="975bf-104">CPU groups</span></span>

- <span data-ttu-id="975bf-105">Konfiguruje, zda jsou vlákna automaticky distribuována mezi skupinami procesorů.</span><span class="sxs-lookup"><span data-stu-id="975bf-105">Configures whether threads are automatically distributed across CPU groups.</span></span>
- <span data-ttu-id="975bf-106">Výchozí: Zakázáno (`0`).</span><span class="sxs-lookup"><span data-stu-id="975bf-106">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="975bf-107">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="975bf-107">Setting name</span></span> | <span data-ttu-id="975bf-108">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="975bf-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="975bf-109">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="975bf-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="975bf-110">Není dostupné.</span><span class="sxs-lookup"><span data-stu-id="975bf-110">N/A</span></span> | <span data-ttu-id="975bf-111">Není dostupné.</span><span class="sxs-lookup"><span data-stu-id="975bf-111">N/A</span></span> |
| <span data-ttu-id="975bf-112">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="975bf-112">**Environment variable**</span></span> | `COMPlus_Thread_UseAllCpuGroups` | <span data-ttu-id="975bf-113">`0`- zakázáno</span><span class="sxs-lookup"><span data-stu-id="975bf-113">`0` - disabled</span></span><br/><span data-ttu-id="975bf-114">`1`- povoleno</span><span class="sxs-lookup"><span data-stu-id="975bf-114">`1` - enabled</span></span> |

## <a name="minimum-threads"></a><span data-ttu-id="975bf-115">Minimální závity</span><span class="sxs-lookup"><span data-stu-id="975bf-115">Minimum threads</span></span>

- <span data-ttu-id="975bf-116">Určuje minimální počet podprocesů pro fond pracovních vláken.</span><span class="sxs-lookup"><span data-stu-id="975bf-116">Specifies the minimum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="975bf-117">Odpovídá metodě. <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="975bf-117">Corresponds to the <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="975bf-118">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="975bf-118">Setting name</span></span> | <span data-ttu-id="975bf-119">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="975bf-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="975bf-120">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="975bf-120">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MinThreads` | <span data-ttu-id="975bf-121">Celé číslo představující minimální počet podprocesů</span><span class="sxs-lookup"><span data-stu-id="975bf-121">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="975bf-122">**MSBuild, vlastnost**</span><span class="sxs-lookup"><span data-stu-id="975bf-122">**MSBuild property**</span></span> | `ThreadPoolMinThreads` | <span data-ttu-id="975bf-123">Celé číslo představující minimální počet podprocesů</span><span class="sxs-lookup"><span data-stu-id="975bf-123">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="975bf-124">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="975bf-124">**Environment variable**</span></span> | <span data-ttu-id="975bf-125">Není dostupné.</span><span class="sxs-lookup"><span data-stu-id="975bf-125">N/A</span></span> | <span data-ttu-id="975bf-126">Není dostupné.</span><span class="sxs-lookup"><span data-stu-id="975bf-126">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="975bf-127">Příklady</span><span class="sxs-lookup"><span data-stu-id="975bf-127">Examples</span></span>

<span data-ttu-id="975bf-128">*soubor runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="975bf-128">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MinThreads": 4
      }
   }
}
```

<span data-ttu-id="975bf-129">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="975bf-129">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>

</Project>
```

## <a name="maximum-threads"></a><span data-ttu-id="975bf-130">Maximální počet vláken</span><span class="sxs-lookup"><span data-stu-id="975bf-130">Maximum threads</span></span>

- <span data-ttu-id="975bf-131">Určuje maximální počet podprocesů pro fond pracovních vláken.</span><span class="sxs-lookup"><span data-stu-id="975bf-131">Specifies the maximum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="975bf-132">Odpovídá metodě. <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="975bf-132">Corresponds to the <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="975bf-133">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="975bf-133">Setting name</span></span> | <span data-ttu-id="975bf-134">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="975bf-134">Values</span></span> |
| - | - | - |
| <span data-ttu-id="975bf-135">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="975bf-135">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MaxThreads` | <span data-ttu-id="975bf-136">Celé číslo představující maximální počet podprocesů</span><span class="sxs-lookup"><span data-stu-id="975bf-136">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="975bf-137">**MSBuild, vlastnost**</span><span class="sxs-lookup"><span data-stu-id="975bf-137">**MSBuild property**</span></span> | `ThreadPoolMaxThreads` | <span data-ttu-id="975bf-138">Celé číslo představující maximální počet podprocesů</span><span class="sxs-lookup"><span data-stu-id="975bf-138">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="975bf-139">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="975bf-139">**Environment variable**</span></span> | <span data-ttu-id="975bf-140">Není dostupné.</span><span class="sxs-lookup"><span data-stu-id="975bf-140">N/A</span></span> | <span data-ttu-id="975bf-141">Není dostupné.</span><span class="sxs-lookup"><span data-stu-id="975bf-141">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="975bf-142">Příklady</span><span class="sxs-lookup"><span data-stu-id="975bf-142">Examples</span></span>

<span data-ttu-id="975bf-143">*soubor runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="975bf-143">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MaxThreads": 20
      }
   }
}
```

<span data-ttu-id="975bf-144">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="975bf-144">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```
