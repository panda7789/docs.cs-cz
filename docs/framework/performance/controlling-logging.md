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
# <a name="controlling-net-framework-logging"></a>Řízení přihlašování rozhraní .NET Framework

Pro zaznamenání událostí modulu Common Language Runtime (CLR) je možné použít trasování událostí systému Windows (ETW). Můžete vytvořit a zobrazit trasování pomocí následujících nástrojů:

- The [Logman](/windows-server/administration/windows-commands/logman) and [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) command-line tools, which are included with the Windows operating system.

- The [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) tools in the [Windows Performance Toolkit](/windows-hardware/test/wpt/). For more information about Xperf, see the [Windows Performance blog](https://blogs.msdn.microsoft.com/pigscanfly/tag/xperf/).

Pro zaznamenání informací události modulu CLR musí být v počítači nainstalován zprostředkovatel modulu CLR. To confirm that the provider is installed, type `logman query providers` at the command prompt. Zobrazí se seznam zprostředkovatelů. Tento seznam by měl obsahovat následující záznam pro zprostředkovatele modulu CLR.

```output
Provider                                 GUID
-------------------------------------------------------------------------------
.NET Common Language Runtime    {E13C0D23-CCBC-4E12-931B-D9CC2EEE27E4}.
```

If the CLR provider is not listed, you can install it on Windows Vista and later operating systems by using the Windows [Wevtutil](/windows-server/administration/windows-commands/wevtutil) command-line tool. Otevřete okno příkazového řádku jako správce. Change the prompt directory to the .NET Framework 4 folder (%WINDIR%\Microsoft.NET\Framework[64]\v4.\<.NET version>\ ). Tato složka obsahuje soubor CLR-ETW.man. Pro instalaci zprostředkovatele modulu CLR zadejte v příkazovém řádku následující příkaz:

`wevtutil im CLR-ETW.man`

## <a name="capturing-clr-etw-events"></a>Zachycení událostí CLR ETW

You can use the [Logman](/windows-server/administration/windows-commands/logman) and [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) command-line tools to capture ETW events, and the [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) and [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) tools to decode the trace events.

K zapnutí protokolování musí uživatel specifikovat tři věci:

- Zprostředkovatele pro komunikaci.

- 64bitové číslo představující sadu klíčových slov. Každé klíčové slovo představuje sadu událostí, které může zprostředkovatel zapnout. Číslo představuje kombinovanou sadu klíčových slov pro zapnutí.

- Malé číslo představující úroveň (podrobnost) protokolu. Úroveň 1 je nejméně podrobná a úroveň 5 je nejvíce podrobná. Úroveň 0 je výchozí a její význam závisí na konkrétním zprostředkovateli.

### <a name="to-capture-clr-etw-events-using-logman"></a>Zachycení událostí CLR ETW pomocí nástroje Logman

1. V příkazovém řádku zadejte příkaz:

     `logman start clrevents -p {e13c0d23-ccbc-4e12-931b-d9cc2eee27e4} 0x1CCBD 0x5 -ets -ct perf`

     kde:

    - The `-p` parameter identifies the provider GUID.

    - `0x1CCBD` specifies the categories of events that will be raised.

    - `0x5` sets the level of logging (in this case, verbose (5)).

    - The `-ets` parameter instructs Logman to send commands to event tracing sessions.

    - The `-ct perf` parameter specifies that the `QueryPerformanceCounter` function will be used to log the time stamp for each event.

2. K ukončení protokolování událostí zadejte:

     `logman stop clrevents -ets`

     Tento příkaz vytvoří binární soubor trasování s názvem clrevents.etl.

### <a name="to-capture-clr-etw-events-using-xperf"></a>Zachycení událostí CLR ETW pomocí nástroje Xperf

1. V příkazovém řádku zadejte příkaz:

     `xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:5 -f clrevents.etl`

     where the GUID is the CLR ETW provider GUID, and `0x1CCBD:5` traces everything at and below level 5 (verbose).

2. Chcete-li zastavit trasování, zadejte:

     `Xperf -stop clr`

     Tento příkaz vytvoří soubor trasování s názvem clrevents.etl.

## <a name="viewing-clr-etw-events"></a>Zobrazení událostí CLR ETW

Pro zobrazení událostí CLR ETW je možné použít následující příkazy. For a description of the events, see [CLR ETW Events](clr-etw-events.md).

### <a name="to-view-clr-etw-events-using-tracerpt"></a>Zobrazení událostí CLR ETW pomocí nástroje Tracerpt

- V příkazovém řádku zadejte příkaz:

     `tracerpt clrevents.etl`

     Tento příkaz vytvoří dva soubory: dumpfile.xml a summary.txt. Soubor dumpfile.xml obsahuje seznam všech událostí a summary.txt poskytuje souhrn událostí.

### <a name="to-view-clr-etw-events-using-xperf"></a>Zobrazení událostí CLR ETW pomocí nástroje Xperf

- V příkazovém řádku zadejte příkaz:

     `xperf clrevents.etl`

     Tento příkaz otevře prohlížeč souborů ETL nástroje Xperf. In this viewer, the CLR events show up in the **Generic Events** view. To display a data grid of events categorized by type, select a region of time in this view, and then right-click and select **Summary**.

### <a name="to-convert-the-etl-file-to-a-comma-separated-value-file"></a>Převod souboru .etl na soubor .csv

- V příkazovém řádku zadejte příkaz:

     `xperf -i clrevents.etl -f clrevents.csv`

     Tento příkaz způsobí, že nástroj XPerf vypíše paměť událostí do souboru CSV, který je možné zobrazit. Protože různé události mají různá pole, tento soubor CSV obsahuje před daty více než jeden řádek záhlaví. První pole každého řádku je typ události, který určuje záhlaví, které se má použít pro určení zbývajících polí.

## <a name="see-also"></a>Viz také:

- [Windows Performance Toolkit](/windows-hardware/test/wpt/)
- [Události Trasování událostí pro Windows v CLR (Common Language Runtime)](etw-events-in-the-common-language-runtime.md)
