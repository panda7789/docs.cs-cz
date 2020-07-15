---
title: Řízení přihlašování rozhraní .NET Framework
description: Použijte trasování událostí pro Windows (ETW) k řízení protokolování rozhraní .NET a zaznamenání událostí modulu CLR (Common Language Runtime). Používejte nástroje, jako je například logman, Tracerpt a Xperf.
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events, logging
ms.assetid: ce13088e-3095-4f0e-9f6b-fad30bbd3d41
ms.openlocfilehash: 45d9244eb11b914fd203f24057e1b65c6bef18c2
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309583"
---
# <a name="controlling-net-framework-logging"></a><span data-ttu-id="78ed1-104">Řízení přihlašování rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="78ed1-104">Controlling .NET Framework Logging</span></span>

<span data-ttu-id="78ed1-105">Pro zaznamenání událostí modulu Common Language Runtime (CLR) je možné použít trasování událostí systému Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="78ed1-105">You can use event tracing for Windows (ETW) to record common language runtime (CLR) events.</span></span> <span data-ttu-id="78ed1-106">Můžete vytvořit a zobrazit trasování pomocí následujících nástrojů:</span><span class="sxs-lookup"><span data-stu-id="78ed1-106">You can create and view traces by using the following tools:</span></span>

- <span data-ttu-id="78ed1-107">Nástroje příkazového řádku [Logman](/windows-server/administration/windows-commands/logman) a [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) , které jsou součástí operačního systému Windows.</span><span class="sxs-lookup"><span data-stu-id="78ed1-107">The [Logman](/windows-server/administration/windows-commands/logman) and [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) command-line tools, which are included with the Windows operating system.</span></span>

- <span data-ttu-id="78ed1-108">Nástroje [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) v sadě [nástrojů Windows Performance Toolkit](/windows-hardware/test/wpt/).</span><span class="sxs-lookup"><span data-stu-id="78ed1-108">The [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) tools in the [Windows Performance Toolkit](/windows-hardware/test/wpt/).</span></span> <span data-ttu-id="78ed1-109">Další informace o Xperf najdete na blogu o [výkonu Windows](https://docs.microsoft.com/archive/blogs/pigscanfly/).</span><span class="sxs-lookup"><span data-stu-id="78ed1-109">For more information about Xperf, see the [Windows Performance blog](https://docs.microsoft.com/archive/blogs/pigscanfly/).</span></span>

<span data-ttu-id="78ed1-110">Pro zaznamenání informací události modulu CLR musí být v počítači nainstalován zprostředkovatel modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="78ed1-110">To capture CLR event information, the CLR provider must be installed on your computer.</span></span> <span data-ttu-id="78ed1-111">Chcete-li ověřit, zda je poskytovatel nainstalován, zadejte do `logman query providers` příkazového řádku příkaz.</span><span class="sxs-lookup"><span data-stu-id="78ed1-111">To confirm that the provider is installed, type `logman query providers` at the command prompt.</span></span> <span data-ttu-id="78ed1-112">Zobrazí se seznam zprostředkovatelů.</span><span class="sxs-lookup"><span data-stu-id="78ed1-112">A list of providers is displayed.</span></span> <span data-ttu-id="78ed1-113">Tento seznam by měl obsahovat následující záznam pro zprostředkovatele modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="78ed1-113">This list should contain an entry for the CLR provider, as follows.</span></span>

```output
Provider                                 GUID
-------------------------------------------------------------------------------
.NET Common Language Runtime    {E13C0D23-CCBC-4E12-931B-D9CC2EEE27E4}.
```

<span data-ttu-id="78ed1-114">Pokud zprostředkovatel CLR není uveden, můžete jej nainstalovat do systému Windows Vista a novějších operačních systémů pomocí nástroje příkazového řádku Windows [wevtutil](/windows-server/administration/windows-commands/wevtutil) .</span><span class="sxs-lookup"><span data-stu-id="78ed1-114">If the CLR provider is not listed, you can install it on Windows Vista and later operating systems by using the Windows [Wevtutil](/windows-server/administration/windows-commands/wevtutil) command-line tool.</span></span> <span data-ttu-id="78ed1-115">Otevřete okno příkazového řádku jako správce.</span><span class="sxs-lookup"><span data-stu-id="78ed1-115">Open the Command Prompt window as an administrator.</span></span> <span data-ttu-id="78ed1-116">Změna adresáře s výzvou na složku .NET Framework 4 (%WINDIR%\Microsoft.NET\Framework [64] \v4. \<.NET version> \ ).</span><span class="sxs-lookup"><span data-stu-id="78ed1-116">Change the prompt directory to the .NET Framework 4 folder (%WINDIR%\Microsoft.NET\Framework[64]\v4.\<.NET version>\ ).</span></span> <span data-ttu-id="78ed1-117">Tato složka obsahuje soubor CLR-ETW.man.</span><span class="sxs-lookup"><span data-stu-id="78ed1-117">This folder contains the CLR-ETW.man file.</span></span> <span data-ttu-id="78ed1-118">Pro instalaci zprostředkovatele modulu CLR zadejte v příkazovém řádku následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="78ed1-118">At the command prompt, type the following command to install the CLR provider:</span></span>

`wevtutil im CLR-ETW.man`

## <a name="capturing-clr-etw-events"></a><span data-ttu-id="78ed1-119">Zachycení událostí CLR ETW</span><span class="sxs-lookup"><span data-stu-id="78ed1-119">Capturing CLR ETW Events</span></span>

<span data-ttu-id="78ed1-120">Pomocí nástrojů příkazového řádku [Logman](/windows-server/administration/windows-commands/logman) a [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) můžete zachytit události ETW a nástroje [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) a [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) k dekódování událostí trasování.</span><span class="sxs-lookup"><span data-stu-id="78ed1-120">You can use the [Logman](/windows-server/administration/windows-commands/logman) and [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) command-line tools to capture ETW events, and the [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) and [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) tools to decode the trace events.</span></span>

<span data-ttu-id="78ed1-121">K zapnutí protokolování musí uživatel specifikovat tři věci:</span><span class="sxs-lookup"><span data-stu-id="78ed1-121">To turn on logging, a user must specify three things:</span></span>

- <span data-ttu-id="78ed1-122">Zprostředkovatele pro komunikaci.</span><span class="sxs-lookup"><span data-stu-id="78ed1-122">The provider to communicate to.</span></span>

- <span data-ttu-id="78ed1-123">64bitové číslo představující sadu klíčových slov.</span><span class="sxs-lookup"><span data-stu-id="78ed1-123">A 64-bit number that represents a set of keywords.</span></span> <span data-ttu-id="78ed1-124">Každé klíčové slovo představuje sadu událostí, které může zprostředkovatel zapnout.</span><span class="sxs-lookup"><span data-stu-id="78ed1-124">Each keyword represents a set of events that the provider can turn on.</span></span> <span data-ttu-id="78ed1-125">Číslo představuje kombinovanou sadu klíčových slov pro zapnutí.</span><span class="sxs-lookup"><span data-stu-id="78ed1-125">The number represents a combined set of keywords to turn on.</span></span>

- <span data-ttu-id="78ed1-126">Malé číslo představující úroveň (podrobnost) protokolu.</span><span class="sxs-lookup"><span data-stu-id="78ed1-126">A small number representing the level (verbosity) to log at.</span></span> <span data-ttu-id="78ed1-127">Úroveň 1 je nejméně podrobná a úroveň 5 je nejvíce podrobná.</span><span class="sxs-lookup"><span data-stu-id="78ed1-127">Level 1 is the least verbose, and level 5 is the most verbose.</span></span> <span data-ttu-id="78ed1-128">Úroveň 0 je výchozí a její význam závisí na konkrétním zprostředkovateli.</span><span class="sxs-lookup"><span data-stu-id="78ed1-128">Level 0 is a default whose meaning is provider-specific.</span></span>

### <a name="to-capture-clr-etw-events-using-logman"></a><span data-ttu-id="78ed1-129">Zachycení událostí CLR ETW pomocí nástroje Logman</span><span class="sxs-lookup"><span data-stu-id="78ed1-129">To capture CLR ETW events using Logman</span></span>

1. <span data-ttu-id="78ed1-130">Na příkazovém řádku zadejte:</span><span class="sxs-lookup"><span data-stu-id="78ed1-130">At the command prompt, type:</span></span>

     `logman start clrevents -p {e13c0d23-ccbc-4e12-931b-d9cc2eee27e4} 0x1CCBD 0x5 -ets -ct perf`

     <span data-ttu-id="78ed1-131">kde:</span><span class="sxs-lookup"><span data-stu-id="78ed1-131">where:</span></span>

    - <span data-ttu-id="78ed1-132">`-p`Parametr identifikuje identifikátor GUID zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="78ed1-132">The `-p` parameter identifies the provider GUID.</span></span>

    - <span data-ttu-id="78ed1-133">`0x1CCBD`Určuje kategorie událostí, které budou vyvolány.</span><span class="sxs-lookup"><span data-stu-id="78ed1-133">`0x1CCBD` specifies the categories of events that will be raised.</span></span>

    - <span data-ttu-id="78ed1-134">`0x5`Nastaví úroveň protokolování (v tomto případě verbose (5)).</span><span class="sxs-lookup"><span data-stu-id="78ed1-134">`0x5` sets the level of logging (in this case, verbose (5)).</span></span>

    - <span data-ttu-id="78ed1-135">`-ets`Parametr nastaví příkaz logman k odeslání příkazů do relací trasování událostí.</span><span class="sxs-lookup"><span data-stu-id="78ed1-135">The `-ets` parameter instructs Logman to send commands to event tracing sessions.</span></span>

    - <span data-ttu-id="78ed1-136">`-ct perf`Parametr určuje, že `QueryPerformanceCounter` funkce bude použita k zaznamenání časového razítka pro každou událost.</span><span class="sxs-lookup"><span data-stu-id="78ed1-136">The `-ct perf` parameter specifies that the `QueryPerformanceCounter` function will be used to log the time stamp for each event.</span></span>

2. <span data-ttu-id="78ed1-137">K ukončení protokolování událostí zadejte:</span><span class="sxs-lookup"><span data-stu-id="78ed1-137">To stop logging the events, type:</span></span>

     `logman stop clrevents -ets`

     <span data-ttu-id="78ed1-138">Tento příkaz vytvoří binární soubor trasování s názvem clrevents.etl.</span><span class="sxs-lookup"><span data-stu-id="78ed1-138">This command creates a binary trace file named clrevents.etl.</span></span>

### <a name="to-capture-clr-etw-events-using-xperf"></a><span data-ttu-id="78ed1-139">Zachycení událostí CLR ETW pomocí nástroje Xperf</span><span class="sxs-lookup"><span data-stu-id="78ed1-139">To capture CLR ETW events using Xperf</span></span>

1. <span data-ttu-id="78ed1-140">Na příkazovém řádku zadejte:</span><span class="sxs-lookup"><span data-stu-id="78ed1-140">At the command prompt, type:</span></span>

     `xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:5 -f clrevents.etl`

     <span data-ttu-id="78ed1-141">kde identifikátor GUID je identifikátor GUID zprostředkovatele modulu CLR ETW a `0x1CCBD:5` sleduje vše na úrovni 5 (verbose).</span><span class="sxs-lookup"><span data-stu-id="78ed1-141">where the GUID is the CLR ETW provider GUID, and `0x1CCBD:5` traces everything at and below level 5 (verbose).</span></span>

2. <span data-ttu-id="78ed1-142">Chcete-li zastavit trasování, zadejte:</span><span class="sxs-lookup"><span data-stu-id="78ed1-142">To stop tracing, type:</span></span>

     `Xperf -stop clr`

     <span data-ttu-id="78ed1-143">Tento příkaz vytvoří soubor trasování s názvem clrevents.etl.</span><span class="sxs-lookup"><span data-stu-id="78ed1-143">This command creates a trace file named clrevents.etl.</span></span>

## <a name="viewing-clr-etw-events"></a><span data-ttu-id="78ed1-144">Zobrazení událostí CLR ETW</span><span class="sxs-lookup"><span data-stu-id="78ed1-144">Viewing CLR ETW Events</span></span>

<span data-ttu-id="78ed1-145">Pro zobrazení událostí CLR ETW je možné použít následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="78ed1-145">Use the commands listed below to view the CLR ETW events.</span></span> <span data-ttu-id="78ed1-146">Popis událostí naleznete v tématu [CLR ETW Events](clr-etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="78ed1-146">For a description of the events, see [CLR ETW Events](clr-etw-events.md).</span></span>

### <a name="to-view-clr-etw-events-using-tracerpt"></a><span data-ttu-id="78ed1-147">Zobrazení událostí CLR ETW pomocí nástroje Tracerpt</span><span class="sxs-lookup"><span data-stu-id="78ed1-147">To view CLR ETW events using Tracerpt</span></span>

- <span data-ttu-id="78ed1-148">Na příkazovém řádku zadejte:</span><span class="sxs-lookup"><span data-stu-id="78ed1-148">At the command prompt, type:</span></span>

     `tracerpt clrevents.etl`

     <span data-ttu-id="78ed1-149">Tento příkaz vytvoří dva soubory: dumpfile.xml a summary.txt.</span><span class="sxs-lookup"><span data-stu-id="78ed1-149">This command creates two files: dumpfile.xml and summary.txt.</span></span> <span data-ttu-id="78ed1-150">Soubor dumpfile.xml obsahuje seznam všech událostí a summary.txt poskytuje souhrn událostí.</span><span class="sxs-lookup"><span data-stu-id="78ed1-150">The dumpfile.xml file lists all the events, and summary.txt provides a summary of the events.</span></span>

### <a name="to-view-clr-etw-events-using-xperf"></a><span data-ttu-id="78ed1-151">Zobrazení událostí CLR ETW pomocí nástroje Xperf</span><span class="sxs-lookup"><span data-stu-id="78ed1-151">To view CLR ETW events using Xperf</span></span>

- <span data-ttu-id="78ed1-152">Na příkazovém řádku zadejte:</span><span class="sxs-lookup"><span data-stu-id="78ed1-152">At the command prompt, type:</span></span>

     `xperf clrevents.etl`

     <span data-ttu-id="78ed1-153">Tento příkaz otevře prohlížeč souborů ETL nástroje Xperf.</span><span class="sxs-lookup"><span data-stu-id="78ed1-153">This command opens the Xperf ETL file viewer.</span></span> <span data-ttu-id="78ed1-154">V tomto prohlížeči se události CLR zobrazí v zobrazení **Obecné události** .</span><span class="sxs-lookup"><span data-stu-id="78ed1-154">In this viewer, the CLR events show up in the **Generic Events** view.</span></span> <span data-ttu-id="78ed1-155">Chcete-li zobrazit datovou mřížku událostí podle typu, vyberte oblast času v tomto zobrazení a potom klikněte pravým tlačítkem myši a vyberte možnost **Souhrn**.</span><span class="sxs-lookup"><span data-stu-id="78ed1-155">To display a data grid of events categorized by type, select a region of time in this view, and then right-click and select **Summary**.</span></span>

### <a name="to-convert-the-etl-file-to-a-comma-separated-value-file"></a><span data-ttu-id="78ed1-156">Převod souboru .etl na soubor .csv</span><span class="sxs-lookup"><span data-stu-id="78ed1-156">To convert the .etl file to a comma-separated value file</span></span>

- <span data-ttu-id="78ed1-157">Na příkazovém řádku zadejte:</span><span class="sxs-lookup"><span data-stu-id="78ed1-157">At the command prompt, type:</span></span>

     `xperf -i clrevents.etl -f clrevents.csv`

     <span data-ttu-id="78ed1-158">Tento příkaz způsobí, že nástroj XPerf vypíše paměť událostí do souboru CSV, který je možné zobrazit.</span><span class="sxs-lookup"><span data-stu-id="78ed1-158">This command causes XPerf to dump the events as a comma separated value (CSV) file that you can view.</span></span> <span data-ttu-id="78ed1-159">Protože různé události mají různá pole, tento soubor CSV obsahuje před daty více než jeden řádek záhlaví.</span><span class="sxs-lookup"><span data-stu-id="78ed1-159">Because different events have different fields, this CSV file is contains more than one header line before the data.</span></span> <span data-ttu-id="78ed1-160">První pole každého řádku je typ události, který určuje záhlaví, které se má použít pro určení zbývajících polí.</span><span class="sxs-lookup"><span data-stu-id="78ed1-160">The first field of every line is the event type, which indicates which header should be used to determine the rest of the fields.</span></span>

## <a name="see-also"></a><span data-ttu-id="78ed1-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="78ed1-161">See also</span></span>

- [<span data-ttu-id="78ed1-162">Sada Windows Performance Toolkit</span><span class="sxs-lookup"><span data-stu-id="78ed1-162">Windows Performance Toolkit</span></span>](/windows-hardware/test/wpt/)
- [<span data-ttu-id="78ed1-163">Události Trasování událostí pro Windows v CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="78ed1-163">ETW Events in the Common Language Runtime</span></span>](etw-events-in-the-common-language-runtime.md)
