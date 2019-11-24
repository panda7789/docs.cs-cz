---
title: Řízení přihlašování rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events, logging
ms.assetid: ce13088e-3095-4f0e-9f6b-fad30bbd3d41
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 924d209cd1177ffc1702ebe958c58bfc29c22c38
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447687"
---
# <a name="controlling-net-framework-logging"></a><span data-ttu-id="0d3d5-102">Řízení přihlašování rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0d3d5-102">Controlling .NET Framework Logging</span></span>

<span data-ttu-id="0d3d5-103">Pro zaznamenání událostí modulu Common Language Runtime (CLR) je možné použít trasování událostí systému Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="0d3d5-103">You can use event tracing for Windows (ETW) to record common language runtime (CLR) events.</span></span> <span data-ttu-id="0d3d5-104">Můžete vytvořit a zobrazit trasování pomocí následujících nástrojů:</span><span class="sxs-lookup"><span data-stu-id="0d3d5-104">You can create and view traces by using the following tools:</span></span>

- <span data-ttu-id="0d3d5-105">The [Logman](/windows-server/administration/windows-commands/logman) and [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) command-line tools, which are included with the Windows operating system.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-105">The [Logman](/windows-server/administration/windows-commands/logman) and [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) command-line tools, which are included with the Windows operating system.</span></span>

- <span data-ttu-id="0d3d5-106">The [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) tools in the [Windows Performance Toolkit](/windows-hardware/test/wpt/).</span><span class="sxs-lookup"><span data-stu-id="0d3d5-106">The [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) tools in the [Windows Performance Toolkit](/windows-hardware/test/wpt/).</span></span> <span data-ttu-id="0d3d5-107">For more information about Xperf, see the [Windows Performance blog](https://blogs.msdn.microsoft.com/pigscanfly/tag/xperf/).</span><span class="sxs-lookup"><span data-stu-id="0d3d5-107">For more information about Xperf, see the [Windows Performance blog](https://blogs.msdn.microsoft.com/pigscanfly/tag/xperf/).</span></span>

<span data-ttu-id="0d3d5-108">Pro zaznamenání informací události modulu CLR musí být v počítači nainstalován zprostředkovatel modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-108">To capture CLR event information, the CLR provider must be installed on your computer.</span></span> <span data-ttu-id="0d3d5-109">To confirm that the provider is installed, type `logman query providers` at the command prompt.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-109">To confirm that the provider is installed, type `logman query providers` at the command prompt.</span></span> <span data-ttu-id="0d3d5-110">Zobrazí se seznam zprostředkovatelů.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-110">A list of providers is displayed.</span></span> <span data-ttu-id="0d3d5-111">Tento seznam by měl obsahovat následující záznam pro zprostředkovatele modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-111">This list should contain an entry for the CLR provider, as follows.</span></span>

```output
Provider                                 GUID
-------------------------------------------------------------------------------
.NET Common Language Runtime    {E13C0D23-CCBC-4E12-931B-D9CC2EEE27E4}.
```

<span data-ttu-id="0d3d5-112">If the CLR provider is not listed, you can install it on Windows Vista and later operating systems by using the Windows [Wevtutil](/windows-server/administration/windows-commands/wevtutil) command-line tool.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-112">If the CLR provider is not listed, you can install it on Windows Vista and later operating systems by using the Windows [Wevtutil](/windows-server/administration/windows-commands/wevtutil) command-line tool.</span></span> <span data-ttu-id="0d3d5-113">Otevřete okno příkazového řádku jako správce.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-113">Open the Command Prompt window as an administrator.</span></span> <span data-ttu-id="0d3d5-114">Change the prompt directory to the .NET Framework 4 folder (%WINDIR%\Microsoft.NET\Framework[64]\v4.\<.NET version>\ ).</span><span class="sxs-lookup"><span data-stu-id="0d3d5-114">Change the prompt directory to the .NET Framework 4 folder (%WINDIR%\Microsoft.NET\Framework[64]\v4.\<.NET version>\ ).</span></span> <span data-ttu-id="0d3d5-115">Tato složka obsahuje soubor CLR-ETW.man.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-115">This folder contains the CLR-ETW.man file.</span></span> <span data-ttu-id="0d3d5-116">Pro instalaci zprostředkovatele modulu CLR zadejte v příkazovém řádku následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="0d3d5-116">At the command prompt, type the following command to install the CLR provider:</span></span>

`wevtutil im CLR-ETW.man`

## <a name="capturing-clr-etw-events"></a><span data-ttu-id="0d3d5-117">Zachycení událostí CLR ETW</span><span class="sxs-lookup"><span data-stu-id="0d3d5-117">Capturing CLR ETW Events</span></span>

<span data-ttu-id="0d3d5-118">You can use the [Logman](/windows-server/administration/windows-commands/logman) and [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) command-line tools to capture ETW events, and the [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) and [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) tools to decode the trace events.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-118">You can use the [Logman](/windows-server/administration/windows-commands/logman) and [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) command-line tools to capture ETW events, and the [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) and [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) tools to decode the trace events.</span></span>

<span data-ttu-id="0d3d5-119">K zapnutí protokolování musí uživatel specifikovat tři věci:</span><span class="sxs-lookup"><span data-stu-id="0d3d5-119">To turn on logging, a user must specify three things:</span></span>

- <span data-ttu-id="0d3d5-120">Zprostředkovatele pro komunikaci.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-120">The provider to communicate to.</span></span>

- <span data-ttu-id="0d3d5-121">64bitové číslo představující sadu klíčových slov.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-121">A 64-bit number that represents a set of keywords.</span></span> <span data-ttu-id="0d3d5-122">Každé klíčové slovo představuje sadu událostí, které může zprostředkovatel zapnout.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-122">Each keyword represents a set of events that the provider can turn on.</span></span> <span data-ttu-id="0d3d5-123">Číslo představuje kombinovanou sadu klíčových slov pro zapnutí.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-123">The number represents a combined set of keywords to turn on.</span></span>

- <span data-ttu-id="0d3d5-124">Malé číslo představující úroveň (podrobnost) protokolu.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-124">A small number representing the level (verbosity) to log at.</span></span> <span data-ttu-id="0d3d5-125">Úroveň 1 je nejméně podrobná a úroveň 5 je nejvíce podrobná.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-125">Level 1 is the least verbose, and level 5 is the most verbose.</span></span> <span data-ttu-id="0d3d5-126">Úroveň 0 je výchozí a její význam závisí na konkrétním zprostředkovateli.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-126">Level 0 is a default whose meaning is provider-specific.</span></span>

### <a name="to-capture-clr-etw-events-using-logman"></a><span data-ttu-id="0d3d5-127">Zachycení událostí CLR ETW pomocí nástroje Logman</span><span class="sxs-lookup"><span data-stu-id="0d3d5-127">To capture CLR ETW events using Logman</span></span>

1. <span data-ttu-id="0d3d5-128">V příkazovém řádku zadejte příkaz:</span><span class="sxs-lookup"><span data-stu-id="0d3d5-128">At the command prompt, type:</span></span>

     `logman start clrevents -p {e13c0d23-ccbc-4e12-931b-d9cc2eee27e4} 0x1CCBD 0x5 -ets -ct perf`

     <span data-ttu-id="0d3d5-129">kde:</span><span class="sxs-lookup"><span data-stu-id="0d3d5-129">where:</span></span>

    - <span data-ttu-id="0d3d5-130">The `-p` parameter identifies the provider GUID.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-130">The `-p` parameter identifies the provider GUID.</span></span>

    - <span data-ttu-id="0d3d5-131">`0x1CCBD` specifies the categories of events that will be raised.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-131">`0x1CCBD` specifies the categories of events that will be raised.</span></span>

    - <span data-ttu-id="0d3d5-132">`0x5` sets the level of logging (in this case, verbose (5)).</span><span class="sxs-lookup"><span data-stu-id="0d3d5-132">`0x5` sets the level of logging (in this case, verbose (5)).</span></span>

    - <span data-ttu-id="0d3d5-133">The `-ets` parameter instructs Logman to send commands to event tracing sessions.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-133">The `-ets` parameter instructs Logman to send commands to event tracing sessions.</span></span>

    - <span data-ttu-id="0d3d5-134">The `-ct perf` parameter specifies that the `QueryPerformanceCounter` function will be used to log the time stamp for each event.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-134">The `-ct perf` parameter specifies that the `QueryPerformanceCounter` function will be used to log the time stamp for each event.</span></span>

2. <span data-ttu-id="0d3d5-135">K ukončení protokolování událostí zadejte:</span><span class="sxs-lookup"><span data-stu-id="0d3d5-135">To stop logging the events, type:</span></span>

     `logman stop clrevents -ets`

     <span data-ttu-id="0d3d5-136">Tento příkaz vytvoří binární soubor trasování s názvem clrevents.etl.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-136">This command creates a binary trace file named clrevents.etl.</span></span>

### <a name="to-capture-clr-etw-events-using-xperf"></a><span data-ttu-id="0d3d5-137">Zachycení událostí CLR ETW pomocí nástroje Xperf</span><span class="sxs-lookup"><span data-stu-id="0d3d5-137">To capture CLR ETW events using Xperf</span></span>

1. <span data-ttu-id="0d3d5-138">V příkazovém řádku zadejte příkaz:</span><span class="sxs-lookup"><span data-stu-id="0d3d5-138">At the command prompt, type:</span></span>

     `xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:5 -f clrevents.etl`

     <span data-ttu-id="0d3d5-139">where the GUID is the CLR ETW provider GUID, and `0x1CCBD:5` traces everything at and below level 5 (verbose).</span><span class="sxs-lookup"><span data-stu-id="0d3d5-139">where the GUID is the CLR ETW provider GUID, and `0x1CCBD:5` traces everything at and below level 5 (verbose).</span></span>

2. <span data-ttu-id="0d3d5-140">Chcete-li zastavit trasování, zadejte:</span><span class="sxs-lookup"><span data-stu-id="0d3d5-140">To stop tracing, type:</span></span>

     `Xperf -stop clr`

     <span data-ttu-id="0d3d5-141">Tento příkaz vytvoří soubor trasování s názvem clrevents.etl.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-141">This command creates a trace file named clrevents.etl.</span></span>

## <a name="viewing-clr-etw-events"></a><span data-ttu-id="0d3d5-142">Zobrazení událostí CLR ETW</span><span class="sxs-lookup"><span data-stu-id="0d3d5-142">Viewing CLR ETW Events</span></span>

<span data-ttu-id="0d3d5-143">Pro zobrazení událostí CLR ETW je možné použít následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-143">Use the commands listed below to view the CLR ETW events.</span></span> <span data-ttu-id="0d3d5-144">For a description of the events, see [CLR ETW Events](clr-etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="0d3d5-144">For a description of the events, see [CLR ETW Events](clr-etw-events.md).</span></span>

### <a name="to-view-clr-etw-events-using-tracerpt"></a><span data-ttu-id="0d3d5-145">Zobrazení událostí CLR ETW pomocí nástroje Tracerpt</span><span class="sxs-lookup"><span data-stu-id="0d3d5-145">To view CLR ETW events using Tracerpt</span></span>

- <span data-ttu-id="0d3d5-146">V příkazovém řádku zadejte příkaz:</span><span class="sxs-lookup"><span data-stu-id="0d3d5-146">At the command prompt, type:</span></span>

     `tracerpt clrevents.etl`

     <span data-ttu-id="0d3d5-147">Tento příkaz vytvoří dva soubory: dumpfile.xml a summary.txt.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-147">This command creates two files: dumpfile.xml and summary.txt.</span></span> <span data-ttu-id="0d3d5-148">Soubor dumpfile.xml obsahuje seznam všech událostí a summary.txt poskytuje souhrn událostí.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-148">The dumpfile.xml file lists all the events, and summary.txt provides a summary of the events.</span></span>

### <a name="to-view-clr-etw-events-using-xperf"></a><span data-ttu-id="0d3d5-149">Zobrazení událostí CLR ETW pomocí nástroje Xperf</span><span class="sxs-lookup"><span data-stu-id="0d3d5-149">To view CLR ETW events using Xperf</span></span>

- <span data-ttu-id="0d3d5-150">V příkazovém řádku zadejte příkaz:</span><span class="sxs-lookup"><span data-stu-id="0d3d5-150">At the command prompt, type:</span></span>

     `xperf clrevents.etl`

     <span data-ttu-id="0d3d5-151">Tento příkaz otevře prohlížeč souborů ETL nástroje Xperf.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-151">This command opens the Xperf ETL file viewer.</span></span> <span data-ttu-id="0d3d5-152">In this viewer, the CLR events show up in the **Generic Events** view.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-152">In this viewer, the CLR events show up in the **Generic Events** view.</span></span> <span data-ttu-id="0d3d5-153">To display a data grid of events categorized by type, select a region of time in this view, and then right-click and select **Summary**.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-153">To display a data grid of events categorized by type, select a region of time in this view, and then right-click and select **Summary**.</span></span>

### <a name="to-convert-the-etl-file-to-a-comma-separated-value-file"></a><span data-ttu-id="0d3d5-154">Převod souboru .etl na soubor .csv</span><span class="sxs-lookup"><span data-stu-id="0d3d5-154">To convert the .etl file to a comma-separated value file</span></span>

- <span data-ttu-id="0d3d5-155">V příkazovém řádku zadejte příkaz:</span><span class="sxs-lookup"><span data-stu-id="0d3d5-155">At the command prompt, type:</span></span>

     `xperf -i clrevents.etl -f clrevents.csv`

     <span data-ttu-id="0d3d5-156">Tento příkaz způsobí, že nástroj XPerf vypíše paměť událostí do souboru CSV, který je možné zobrazit.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-156">This command causes XPerf to dump the events as a comma separated value (CSV) file that you can view.</span></span> <span data-ttu-id="0d3d5-157">Protože různé události mají různá pole, tento soubor CSV obsahuje před daty více než jeden řádek záhlaví.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-157">Because different events have different fields, this CSV file is contains more than one header line before the data.</span></span> <span data-ttu-id="0d3d5-158">První pole každého řádku je typ události, který určuje záhlaví, které se má použít pro určení zbývajících polí.</span><span class="sxs-lookup"><span data-stu-id="0d3d5-158">The first field of every line is the event type, which indicates which header should be used to determine the rest of the fields.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d3d5-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0d3d5-159">See also</span></span>

- [<span data-ttu-id="0d3d5-160">Windows Performance Toolkit</span><span class="sxs-lookup"><span data-stu-id="0d3d5-160">Windows Performance Toolkit</span></span>](/windows-hardware/test/wpt/)
- [<span data-ttu-id="0d3d5-161">Události Trasování událostí pro Windows v CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="0d3d5-161">ETW Events in the Common Language Runtime</span></span>](etw-events-in-the-common-language-runtime.md)
