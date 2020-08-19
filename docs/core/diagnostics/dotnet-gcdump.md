---
title: dotnet – gcdump – .NET Core
description: Instalace a použití nástroje příkazového řádku dotnet-gcdump.
ms.date: 07/26/2020
ms.openlocfilehash: 10e4c7e9e3a1df5d0eb58e68d38c0af091aeedc1
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88575679"
---
# <a name="heap-analysis-tool-dotnet-gcdump"></a><span data-ttu-id="7b53d-103">Nástroj pro analýzu haldy (dotnet – gcdump)</span><span class="sxs-lookup"><span data-stu-id="7b53d-103">Heap analysis tool (dotnet-gcdump)</span></span>

<span data-ttu-id="7b53d-104">**Tento článek se týká:** ✔️ .net Core 3,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="7b53d-104">**This article applies to:** ✔️ .NET Core 3.1 SDK and later versions</span></span>

## <a name="install-dotnet-gcdump"></a><span data-ttu-id="7b53d-105">Instalace dotnet – gcdump</span><span class="sxs-lookup"><span data-stu-id="7b53d-105">Install dotnet-gcdump</span></span>

<span data-ttu-id="7b53d-106">Chcete-li nainstalovat nejnovější verzi `dotnet-gcdump` [balíčku NuGet](https://www.nuget.org/packages/dotnet-gcdump), použijte příkaz pro [instalaci nástroje dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="7b53d-106">To install the latest release version of the `dotnet-gcdump` [NuGet package](https://www.nuget.org/packages/dotnet-gcdump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install -g dotnet-gcdump
```

## <a name="synopsis"></a><span data-ttu-id="7b53d-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="7b53d-107">Synopsis</span></span>

```console
dotnet-gcdump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="7b53d-108">Popis</span><span class="sxs-lookup"><span data-stu-id="7b53d-108">Description</span></span>

<span data-ttu-id="7b53d-109">`dotnet-gcdump`Globální nástroj je způsob, jak shromažďovat výpisy GC (uvolňování paměti) pro živé procesy .NET.</span><span class="sxs-lookup"><span data-stu-id="7b53d-109">The `dotnet-gcdump` global tool is a way to collect GC (Garbage Collector) dumps of live .NET processes.</span></span> <span data-ttu-id="7b53d-110">Používá technologii EventPipe, což je alternativa k ETW v systému Windows, která je jiná pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="7b53d-110">It uses the EventPipe technology, which is a cross-platform alternative to ETW on Windows.</span></span> <span data-ttu-id="7b53d-111">Výpisy paměti GC se vytvářejí aktivací GC v cílovém procesu, zapnutím zvláštních událostí a obnovením grafu kořenových adresářů objektů z datového proudu událostí.</span><span class="sxs-lookup"><span data-stu-id="7b53d-111">GC dumps are created by triggering a GC in the target process, turning on special events, and regenerating the graph of object roots from the event stream.</span></span> <span data-ttu-id="7b53d-112">Díky tomu můžou být výpisy paměti GC shromažďovány, když je proces spuštěný, s minimální režií.</span><span class="sxs-lookup"><span data-stu-id="7b53d-112">This allows for GC dumps to be collected while the process is running, with minimal overhead.</span></span> <span data-ttu-id="7b53d-113">Tyto výpisy jsou užitečné pro několik scénářů:</span><span class="sxs-lookup"><span data-stu-id="7b53d-113">These dumps are useful for several scenarios:</span></span>

- <span data-ttu-id="7b53d-114">Porovnání počtu objektů v haldě v několika okamžicích v čase.</span><span class="sxs-lookup"><span data-stu-id="7b53d-114">Comparing the number of objects on the heap at several points in time.</span></span>
- <span data-ttu-id="7b53d-115">Analyzují se kořeny objektů (zodpovězené otázky, jako je například "co stále obsahuje odkaz na tento typ?").</span><span class="sxs-lookup"><span data-stu-id="7b53d-115">Analyzing roots of objects (answering questions like, "what still has a reference to this type?").</span></span>
- <span data-ttu-id="7b53d-116">Shromažďování obecných statistik o počtu objektů v haldě.</span><span class="sxs-lookup"><span data-stu-id="7b53d-116">Collecting general statistics about the counts of objects on the heap.</span></span>

### <a name="view-the-gc-dump-captured-from-dotnet-gcdump"></a><span data-ttu-id="7b53d-117">Zobrazit výpis GC zachycený z dotnet-gcdump</span><span class="sxs-lookup"><span data-stu-id="7b53d-117">View the GC dump captured from dotnet-gcdump</span></span>

<span data-ttu-id="7b53d-118">V systému Windows `.gcdump` lze soubory zobrazit v [PerfView](https://github.com/microsoft/perfview) pro účely analýzy nebo v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7b53d-118">On Windows, `.gcdump` files can be viewed in [PerfView](https://github.com/microsoft/perfview) for analysis or in Visual Studio.</span></span> <span data-ttu-id="7b53d-119">V současné době neexistuje žádný způsob, jak otevřít `.gcdump` na platformách jiných než Windows.</span><span class="sxs-lookup"><span data-stu-id="7b53d-119">Currently, There is no way of opening a `.gcdump` on non-Windows platforms.</span></span>

<span data-ttu-id="7b53d-120">Můžete shromáždit vícenásobné `.gcdump` a otevřít je současně v aplikaci Visual Studio a získat tak prostředí pro porovnání.</span><span class="sxs-lookup"><span data-stu-id="7b53d-120">You can collect multiple `.gcdump`s and open them simultaneously in Visual Studio to get a comparison experience.</span></span>

## <a name="options"></a><span data-ttu-id="7b53d-121">Možnosti</span><span class="sxs-lookup"><span data-stu-id="7b53d-121">Options</span></span>

- **`--version`**

  <span data-ttu-id="7b53d-122">Zobrazuje verzi `dotnet-gcdump` nástroje.</span><span class="sxs-lookup"><span data-stu-id="7b53d-122">Displays the version of the `dotnet-gcdump` utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="7b53d-123">Zobrazí pomocníka s příkazovým řádkem.</span><span class="sxs-lookup"><span data-stu-id="7b53d-123">Shows command-line help.</span></span>

## `dotnet-gcdump collect`

<span data-ttu-id="7b53d-124">Shromažďuje výpis GC z aktuálně spuštěného procesu.</span><span class="sxs-lookup"><span data-stu-id="7b53d-124">Collects a GC dump from a currently running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="7b53d-125">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="7b53d-125">Synopsis</span></span>

```console
dotnet-gcdump collect [-h|--help] [-p|--process-id <pid>] [-o|--output <gcdump-file-path>] [-v|--verbose] [-t|--timeout <timeout>] [-n|--name <name>]
```

### <a name="options"></a><span data-ttu-id="7b53d-126">Možnosti</span><span class="sxs-lookup"><span data-stu-id="7b53d-126">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="7b53d-127">Zobrazí pomocníka s příkazovým řádkem.</span><span class="sxs-lookup"><span data-stu-id="7b53d-127">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="7b53d-128">ID procesu, ze kterého se má shromáždit výpis paměti.</span><span class="sxs-lookup"><span data-stu-id="7b53d-128">The process id to collect the GC dump from.</span></span>

- **`-o|--output <gcdump-file-path>`**

  <span data-ttu-id="7b53d-129">Cesta, kam se mají zapisovat výpisy paměti GC</span><span class="sxs-lookup"><span data-stu-id="7b53d-129">The path where collected GC dumps should be written.</span></span> <span data-ttu-id="7b53d-130">Výchozí hodnota je *. \\ RRRRMMDD \_ HHMMSS \_ \<pid> . gcdump*.</span><span class="sxs-lookup"><span data-stu-id="7b53d-130">Defaults to *.\\YYYYMMDD\_HHMMSS\_\<pid>.gcdump*.</span></span>

- **`-v|--verbose`**

  <span data-ttu-id="7b53d-131">Výstup protokolu při shromažďování výpisu paměti GC.</span><span class="sxs-lookup"><span data-stu-id="7b53d-131">Output the log while collecting the GC dump.</span></span>

- **`-t|--timeout <timeout>`**

  <span data-ttu-id="7b53d-132">Zastavte shromažďování výpisu paměti, pokud trvá déle než tento počet sekund.</span><span class="sxs-lookup"><span data-stu-id="7b53d-132">Give up on collecting the GC dump if it takes longer than this many seconds.</span></span> <span data-ttu-id="7b53d-133">Výchozí hodnota je 30.</span><span class="sxs-lookup"><span data-stu-id="7b53d-133">The default value is 30.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="7b53d-134">Název procesu, ze kterého se má shromáždit výpis paměti.</span><span class="sxs-lookup"><span data-stu-id="7b53d-134">The name of the process to collect the GC dump from.</span></span>

## `dotnet-gcdump ps`

<span data-ttu-id="7b53d-135">Zobrazuje seznam procesů dotnet, pro které lze shromáždit výpisy paměti GC.</span><span class="sxs-lookup"><span data-stu-id="7b53d-135">Lists the dotnet processes that GC dumps can be collected for.</span></span>

### <a name="synopsis"></a><span data-ttu-id="7b53d-136">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="7b53d-136">Synopsis</span></span>

```console
dotnet-gcdump ps
```

## `dotnet-gcdump report <gcdump_filename>`

<span data-ttu-id="7b53d-137">Vygenerujte sestavu z dříve generovaného výpisu GC nebo ze spuštěného procesu a zapište do `stdout` .</span><span class="sxs-lookup"><span data-stu-id="7b53d-137">Generate a report from a previously generated GC dump or from a running process, and write to `stdout`.</span></span>

### <a name="synopsis"></a><span data-ttu-id="7b53d-138">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="7b53d-138">Synopsis</span></span>

```console
dotnet-gcdump report [-h|--help] [-p|--process-id <pid>] [-t|--report-type <HeapStat>]
```

### <a name="options"></a><span data-ttu-id="7b53d-139">Možnosti</span><span class="sxs-lookup"><span data-stu-id="7b53d-139">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="7b53d-140">Zobrazí pomocníka s příkazovým řádkem.</span><span class="sxs-lookup"><span data-stu-id="7b53d-140">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="7b53d-141">ID procesu, ze kterého se má shromáždit výpis paměti.</span><span class="sxs-lookup"><span data-stu-id="7b53d-141">The process id to collect the GC dump from.</span></span>

- **`-t|--report-type <HeapStat>`**

  <span data-ttu-id="7b53d-142">Typ sestavy, která má být vygenerována.</span><span class="sxs-lookup"><span data-stu-id="7b53d-142">The type of report to generate.</span></span> <span data-ttu-id="7b53d-143">Dostupné možnosti: heapstat (výchozí).</span><span class="sxs-lookup"><span data-stu-id="7b53d-143">Available options: heapstat (default).</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="7b53d-144">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="7b53d-144">Troubleshoot</span></span>

- <span data-ttu-id="7b53d-145">V gcdump nejsou žádné informace o typu.</span><span class="sxs-lookup"><span data-stu-id="7b53d-145">There is no type information in the gcdump.</span></span>

   <span data-ttu-id="7b53d-146">Před rozhraním .NET Core 3,1 došlo k potížím s nesmazáním mezipaměti typů mezi gcdumps, pokud byly vyvolány pomocí EventPipe.</span><span class="sxs-lookup"><span data-stu-id="7b53d-146">Prior to .NET Core 3.1, there was an issue where a type cache was not cleared between gcdumps when they were invoked with EventPipe.</span></span> <span data-ttu-id="7b53d-147">Výsledkem jsou události potřebné k určení typu informací, které nejsou odesílány pro druhý a další gcdumps.</span><span class="sxs-lookup"><span data-stu-id="7b53d-147">This resulted in the events needed for determining type information not being sent for the second and subsequent gcdumps.</span></span> <span data-ttu-id="7b53d-148">Tento problém byl opravený v .NET Core 3,1-preview2.</span><span class="sxs-lookup"><span data-stu-id="7b53d-148">This was fixed in .NET Core 3.1-preview2.</span></span>

- <span data-ttu-id="7b53d-149">COM a statické typy nejsou ve výpisu GC.</span><span class="sxs-lookup"><span data-stu-id="7b53d-149">COM and static types aren't in the GC dump.</span></span>

   <span data-ttu-id="7b53d-150">Před rozhraním .NET Core 3,1-preview2 došlo k problému, kdy se při vyvolání výpisu paměti GC prostřednictvím EventPipe neodeslaly statické a COM typy.</span><span class="sxs-lookup"><span data-stu-id="7b53d-150">Prior to .NET Core 3.1-preview2, there was an issue where static and COM types weren't sent when the GC dump was invoked via EventPipe.</span></span> <span data-ttu-id="7b53d-151">Tento problém byl opraven v rozhraní .NET Core 3,1-preview2.</span><span class="sxs-lookup"><span data-stu-id="7b53d-151">This has been fixed in .NET Core 3.1-preview2.</span></span>
