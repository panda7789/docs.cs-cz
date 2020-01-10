---
title: Řízení přihlašování rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events, logging
ms.assetid: ce13088e-3095-4f0e-9f6b-fad30bbd3d41
ms.openlocfilehash: 180cce516a1209711430429a46cb5b718b29f1d9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716108"
---
# <a name="controlling-net-framework-logging"></a><span data-ttu-id="5a248-102">Řízení přihlašování rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5a248-102">Controlling .NET Framework Logging</span></span>

<span data-ttu-id="5a248-103">Pro zaznamenání událostí modulu Common Language Runtime (CLR) je možné použít trasování událostí systému Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="5a248-103">You can use event tracing for Windows (ETW) to record common language runtime (CLR) events.</span></span> <span data-ttu-id="5a248-104">Můžete vytvořit a zobrazit trasování pomocí následujících nástrojů:</span><span class="sxs-lookup"><span data-stu-id="5a248-104">You can create and view traces by using the following tools:</span></span>

- <span data-ttu-id="5a248-105">Nástroje příkazového řádku [Logman](/windows-server/administration/windows-commands/logman) a [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) , které jsou součástí operačního systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5a248-105">The [Logman](/windows-server/administration/windows-commands/logman) and [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) command-line tools, which are included with the Windows operating system.</span></span>

- <span data-ttu-id="5a248-106">Nástroje [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) v sadě [nástrojů Windows Performance Toolkit](/windows-hardware/test/wpt/).</span><span class="sxs-lookup"><span data-stu-id="5a248-106">The [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) tools in the [Windows Performance Toolkit](/windows-hardware/test/wpt/).</span></span> <span data-ttu-id="5a248-107">Další informace o Xperf najdete na blogu o [výkonu Windows](https://blogs.msdn.microsoft.com/pigscanfly/tag/xperf/).</span><span class="sxs-lookup"><span data-stu-id="5a248-107">For more information about Xperf, see the [Windows Performance blog](https://blogs.msdn.microsoft.com/pigscanfly/tag/xperf/).</span></span>

<span data-ttu-id="5a248-108">Pro zaznamenání informací události modulu CLR musí být v počítači nainstalován zprostředkovatel modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="5a248-108">To capture CLR event information, the CLR provider must be installed on your computer.</span></span> <span data-ttu-id="5a248-109">Chcete-li ověřit, zda je nainstalován poskytovatel, zadejte `logman query providers` do příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="5a248-109">To confirm that the provider is installed, type `logman query providers` at the command prompt.</span></span> <span data-ttu-id="5a248-110">Zobrazí se seznam zprostředkovatelů.</span><span class="sxs-lookup"><span data-stu-id="5a248-110">A list of providers is displayed.</span></span> <span data-ttu-id="5a248-111">Tento seznam by měl obsahovat následující záznam pro zprostředkovatele modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="5a248-111">This list should contain an entry for the CLR provider, as follows.</span></span>

```output
Provider                                 GUID
-------------------------------------------------------------------------------
.NET Common Language Runtime    {E13C0D23-CCBC-4E12-931B-D9CC2EEE27E4}.
```

<span data-ttu-id="5a248-112">Pokud zprostředkovatel CLR není uveden, můžete jej nainstalovat do systému Windows Vista a novějších operačních systémů pomocí nástroje příkazového řádku Windows [wevtutil](/windows-server/administration/windows-commands/wevtutil) .</span><span class="sxs-lookup"><span data-stu-id="5a248-112">If the CLR provider is not listed, you can install it on Windows Vista and later operating systems by using the Windows [Wevtutil](/windows-server/administration/windows-commands/wevtutil) command-line tool.</span></span> <span data-ttu-id="5a248-113">Otevřete okno příkazového řádku jako správce.</span><span class="sxs-lookup"><span data-stu-id="5a248-113">Open the Command Prompt window as an administrator.</span></span> <span data-ttu-id="5a248-114">Změňte adresář s výzvou na složku .NET Framework 4 (%WINDIR%\Microsoft.NET\Framework [64] \v4.\<.NET verze > \).</span><span class="sxs-lookup"><span data-stu-id="5a248-114">Change the prompt directory to the .NET Framework 4 folder (%WINDIR%\Microsoft.NET\Framework[64]\v4.\<.NET version>\ ).</span></span> <span data-ttu-id="5a248-115">Tato složka obsahuje soubor CLR-ETW.man.</span><span class="sxs-lookup"><span data-stu-id="5a248-115">This folder contains the CLR-ETW.man file.</span></span> <span data-ttu-id="5a248-116">Pro instalaci zprostředkovatele modulu CLR zadejte v příkazovém řádku následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="5a248-116">At the command prompt, type the following command to install the CLR provider:</span></span>

`wevtutil im CLR-ETW.man`

## <a name="capturing-clr-etw-events"></a><span data-ttu-id="5a248-117">Zachycení událostí CLR ETW</span><span class="sxs-lookup"><span data-stu-id="5a248-117">Capturing CLR ETW Events</span></span>

<span data-ttu-id="5a248-118">Pomocí nástrojů příkazového řádku [Logman](/windows-server/administration/windows-commands/logman) a [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) můžete zachytit události ETW a nástroje [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) a [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) k dekódování událostí trasování.</span><span class="sxs-lookup"><span data-stu-id="5a248-118">You can use the [Logman](/windows-server/administration/windows-commands/logman) and [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) command-line tools to capture ETW events, and the [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) and [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) tools to decode the trace events.</span></span>

<span data-ttu-id="5a248-119">K zapnutí protokolování musí uživatel specifikovat tři věci:</span><span class="sxs-lookup"><span data-stu-id="5a248-119">To turn on logging, a user must specify three things:</span></span>

- <span data-ttu-id="5a248-120">Zprostředkovatele pro komunikaci.</span><span class="sxs-lookup"><span data-stu-id="5a248-120">The provider to communicate to.</span></span>

- <span data-ttu-id="5a248-121">64bitové číslo představující sadu klíčových slov.</span><span class="sxs-lookup"><span data-stu-id="5a248-121">A 64-bit number that represents a set of keywords.</span></span> <span data-ttu-id="5a248-122">Každé klíčové slovo představuje sadu událostí, které může zprostředkovatel zapnout.</span><span class="sxs-lookup"><span data-stu-id="5a248-122">Each keyword represents a set of events that the provider can turn on.</span></span> <span data-ttu-id="5a248-123">Číslo představuje kombinovanou sadu klíčových slov pro zapnutí.</span><span class="sxs-lookup"><span data-stu-id="5a248-123">The number represents a combined set of keywords to turn on.</span></span>

- <span data-ttu-id="5a248-124">Malé číslo představující úroveň (podrobnost) protokolu.</span><span class="sxs-lookup"><span data-stu-id="5a248-124">A small number representing the level (verbosity) to log at.</span></span> <span data-ttu-id="5a248-125">Úroveň 1 je nejméně podrobná a úroveň 5 je nejvíce podrobná.</span><span class="sxs-lookup"><span data-stu-id="5a248-125">Level 1 is the least verbose, and level 5 is the most verbose.</span></span> <span data-ttu-id="5a248-126">Úroveň 0 je výchozí a její význam závisí na konkrétním zprostředkovateli.</span><span class="sxs-lookup"><span data-stu-id="5a248-126">Level 0 is a default whose meaning is provider-specific.</span></span>

### <a name="to-capture-clr-etw-events-using-logman"></a><span data-ttu-id="5a248-127">Zachycení událostí CLR ETW pomocí nástroje Logman</span><span class="sxs-lookup"><span data-stu-id="5a248-127">To capture CLR ETW events using Logman</span></span>

1. <span data-ttu-id="5a248-128">Do příkazového řádku zadejte:</span><span class="sxs-lookup"><span data-stu-id="5a248-128">At the command prompt, type:</span></span>

     `logman start clrevents -p {e13c0d23-ccbc-4e12-931b-d9cc2eee27e4} 0x1CCBD 0x5 -ets -ct perf`

     <span data-ttu-id="5a248-129">kde:</span><span class="sxs-lookup"><span data-stu-id="5a248-129">where:</span></span>

    - <span data-ttu-id="5a248-130">Parametr `-p` identifikuje identifikátor GUID zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="5a248-130">The `-p` parameter identifies the provider GUID.</span></span>

    - <span data-ttu-id="5a248-131">`0x1CCBD` určuje kategorie událostí, které budou vyvolány.</span><span class="sxs-lookup"><span data-stu-id="5a248-131">`0x1CCBD` specifies the categories of events that will be raised.</span></span>

    - <span data-ttu-id="5a248-132">`0x5` nastaví úroveň protokolování (v tomto případě verbose (5)).</span><span class="sxs-lookup"><span data-stu-id="5a248-132">`0x5` sets the level of logging (in this case, verbose (5)).</span></span>

    - <span data-ttu-id="5a248-133">Parametr `-ets` instruuje příkaz logman k odeslání příkazů do relací trasování událostí.</span><span class="sxs-lookup"><span data-stu-id="5a248-133">The `-ets` parameter instructs Logman to send commands to event tracing sessions.</span></span>

    - <span data-ttu-id="5a248-134">Parametr `-ct perf` určuje, zda bude funkce `QueryPerformanceCounter` použita k zaznamenání časového razítka pro každou událost.</span><span class="sxs-lookup"><span data-stu-id="5a248-134">The `-ct perf` parameter specifies that the `QueryPerformanceCounter` function will be used to log the time stamp for each event.</span></span>

2. <span data-ttu-id="5a248-135">K ukončení protokolování událostí zadejte:</span><span class="sxs-lookup"><span data-stu-id="5a248-135">To stop logging the events, type:</span></span>

     `logman stop clrevents -ets`

     <span data-ttu-id="5a248-136">Tento příkaz vytvoří binární soubor trasování s názvem clrevents.etl.</span><span class="sxs-lookup"><span data-stu-id="5a248-136">This command creates a binary trace file named clrevents.etl.</span></span>

### <a name="to-capture-clr-etw-events-using-xperf"></a><span data-ttu-id="5a248-137">Zachycení událostí CLR ETW pomocí nástroje Xperf</span><span class="sxs-lookup"><span data-stu-id="5a248-137">To capture CLR ETW events using Xperf</span></span>

1. <span data-ttu-id="5a248-138">Do příkazového řádku zadejte:</span><span class="sxs-lookup"><span data-stu-id="5a248-138">At the command prompt, type:</span></span>

     `xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:5 -f clrevents.etl`

     <span data-ttu-id="5a248-139">kde identifikátor GUID je identifikátor GUID zprostředkovatele modulu CLR ETW a `0x1CCBD:5` sleduje vše na úrovni 5 (verbose).</span><span class="sxs-lookup"><span data-stu-id="5a248-139">where the GUID is the CLR ETW provider GUID, and `0x1CCBD:5` traces everything at and below level 5 (verbose).</span></span>

2. <span data-ttu-id="5a248-140">Chcete-li zastavit trasování, zadejte:</span><span class="sxs-lookup"><span data-stu-id="5a248-140">To stop tracing, type:</span></span>

     `Xperf -stop clr`

     <span data-ttu-id="5a248-141">Tento příkaz vytvoří soubor trasování s názvem clrevents.etl.</span><span class="sxs-lookup"><span data-stu-id="5a248-141">This command creates a trace file named clrevents.etl.</span></span>

## <a name="viewing-clr-etw-events"></a><span data-ttu-id="5a248-142">Zobrazení událostí CLR ETW</span><span class="sxs-lookup"><span data-stu-id="5a248-142">Viewing CLR ETW Events</span></span>

<span data-ttu-id="5a248-143">Pro zobrazení událostí CLR ETW je možné použít následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="5a248-143">Use the commands listed below to view the CLR ETW events.</span></span> <span data-ttu-id="5a248-144">Popis událostí naleznete v tématu [CLR ETW Events](clr-etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="5a248-144">For a description of the events, see [CLR ETW Events](clr-etw-events.md).</span></span>

### <a name="to-view-clr-etw-events-using-tracerpt"></a><span data-ttu-id="5a248-145">Zobrazení událostí CLR ETW pomocí nástroje Tracerpt</span><span class="sxs-lookup"><span data-stu-id="5a248-145">To view CLR ETW events using Tracerpt</span></span>

- <span data-ttu-id="5a248-146">Do příkazového řádku zadejte:</span><span class="sxs-lookup"><span data-stu-id="5a248-146">At the command prompt, type:</span></span>

     `tracerpt clrevents.etl`

     <span data-ttu-id="5a248-147">Tento příkaz vytvoří dva soubory: dumpfile.xml a summary.txt.</span><span class="sxs-lookup"><span data-stu-id="5a248-147">This command creates two files: dumpfile.xml and summary.txt.</span></span> <span data-ttu-id="5a248-148">Soubor dumpfile.xml obsahuje seznam všech událostí a summary.txt poskytuje souhrn událostí.</span><span class="sxs-lookup"><span data-stu-id="5a248-148">The dumpfile.xml file lists all the events, and summary.txt provides a summary of the events.</span></span>

### <a name="to-view-clr-etw-events-using-xperf"></a><span data-ttu-id="5a248-149">Zobrazení událostí CLR ETW pomocí nástroje Xperf</span><span class="sxs-lookup"><span data-stu-id="5a248-149">To view CLR ETW events using Xperf</span></span>

- <span data-ttu-id="5a248-150">Do příkazového řádku zadejte:</span><span class="sxs-lookup"><span data-stu-id="5a248-150">At the command prompt, type:</span></span>

     `xperf clrevents.etl`

     <span data-ttu-id="5a248-151">Tento příkaz otevře prohlížeč souborů ETL nástroje Xperf.</span><span class="sxs-lookup"><span data-stu-id="5a248-151">This command opens the Xperf ETL file viewer.</span></span> <span data-ttu-id="5a248-152">V tomto prohlížeči se události CLR zobrazí v zobrazení **Obecné události** .</span><span class="sxs-lookup"><span data-stu-id="5a248-152">In this viewer, the CLR events show up in the **Generic Events** view.</span></span> <span data-ttu-id="5a248-153">Chcete-li zobrazit datovou mřížku událostí podle typu, vyberte oblast času v tomto zobrazení a potom klikněte pravým tlačítkem myši a vyberte možnost **Souhrn**.</span><span class="sxs-lookup"><span data-stu-id="5a248-153">To display a data grid of events categorized by type, select a region of time in this view, and then right-click and select **Summary**.</span></span>

### <a name="to-convert-the-etl-file-to-a-comma-separated-value-file"></a><span data-ttu-id="5a248-154">Převod souboru .etl na soubor .csv</span><span class="sxs-lookup"><span data-stu-id="5a248-154">To convert the .etl file to a comma-separated value file</span></span>

- <span data-ttu-id="5a248-155">Do příkazového řádku zadejte:</span><span class="sxs-lookup"><span data-stu-id="5a248-155">At the command prompt, type:</span></span>

     `xperf -i clrevents.etl -f clrevents.csv`

     <span data-ttu-id="5a248-156">Tento příkaz způsobí, že nástroj XPerf vypíše paměť událostí do souboru CSV, který je možné zobrazit.</span><span class="sxs-lookup"><span data-stu-id="5a248-156">This command causes XPerf to dump the events as a comma separated value (CSV) file that you can view.</span></span> <span data-ttu-id="5a248-157">Protože různé události mají různá pole, tento soubor CSV obsahuje před daty více než jeden řádek záhlaví.</span><span class="sxs-lookup"><span data-stu-id="5a248-157">Because different events have different fields, this CSV file is contains more than one header line before the data.</span></span> <span data-ttu-id="5a248-158">První pole každého řádku je typ události, který určuje záhlaví, které se má použít pro určení zbývajících polí.</span><span class="sxs-lookup"><span data-stu-id="5a248-158">The first field of every line is the event type, which indicates which header should be used to determine the rest of the fields.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a248-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a248-159">See also</span></span>

- [<span data-ttu-id="5a248-160">Sada Windows Performance Toolkit</span><span class="sxs-lookup"><span data-stu-id="5a248-160">Windows Performance Toolkit</span></span>](/windows-hardware/test/wpt/)
- [<span data-ttu-id="5a248-161">Události Trasování událostí pro Windows v CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="5a248-161">ETW Events in the Common Language Runtime</span></span>](etw-events-in-the-common-language-runtime.md)
