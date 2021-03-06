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
# <a name="controlling-net-framework-logging"></a>Řízení přihlašování rozhraní .NET Framework

Pro zaznamenání událostí modulu Common Language Runtime (CLR) je možné použít trasování událostí systému Windows (ETW). Můžete vytvořit a zobrazit trasování pomocí následujících nástrojů:

- Nástroje příkazového řádku [Logman](/windows-server/administration/windows-commands/logman) a [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) , které jsou součástí operačního systému Windows.

- Nástroje [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) v sadě [nástrojů Windows Performance Toolkit](/windows-hardware/test/wpt/). Další informace o Xperf najdete na blogu o [výkonu Windows](https://docs.microsoft.com/archive/blogs/pigscanfly/).

Pro zaznamenání informací události modulu CLR musí být v počítači nainstalován zprostředkovatel modulu CLR. Chcete-li ověřit, zda je poskytovatel nainstalován, zadejte do `logman query providers` příkazového řádku příkaz. Zobrazí se seznam zprostředkovatelů. Tento seznam by měl obsahovat následující záznam pro zprostředkovatele modulu CLR.

```output
Provider                                 GUID
-------------------------------------------------------------------------------
.NET Common Language Runtime    {E13C0D23-CCBC-4E12-931B-D9CC2EEE27E4}.
```

Pokud zprostředkovatel CLR není uveden, můžete jej nainstalovat do systému Windows Vista a novějších operačních systémů pomocí nástroje příkazového řádku Windows [wevtutil](/windows-server/administration/windows-commands/wevtutil) . Otevřete okno příkazového řádku jako správce. Změna adresáře s výzvou na složku .NET Framework 4 (%WINDIR%\Microsoft.NET\Framework [64] \v4. \<.NET version> \ ). Tato složka obsahuje soubor CLR-ETW.man. Pro instalaci zprostředkovatele modulu CLR zadejte v příkazovém řádku následující příkaz:

`wevtutil im CLR-ETW.man`

## <a name="capturing-clr-etw-events"></a>Zachycení událostí CLR ETW

Pomocí nástrojů příkazového řádku [Logman](/windows-server/administration/windows-commands/logman) a [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) můžete zachytit události ETW a nástroje [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) a [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) k dekódování událostí trasování.

K zapnutí protokolování musí uživatel specifikovat tři věci:

- Zprostředkovatele pro komunikaci.

- 64bitové číslo představující sadu klíčových slov. Každé klíčové slovo představuje sadu událostí, které může zprostředkovatel zapnout. Číslo představuje kombinovanou sadu klíčových slov pro zapnutí.

- Malé číslo představující úroveň (podrobnost) protokolu. Úroveň 1 je nejméně podrobná a úroveň 5 je nejvíce podrobná. Úroveň 0 je výchozí a její význam závisí na konkrétním zprostředkovateli.

### <a name="to-capture-clr-etw-events-using-logman"></a>Zachycení událostí CLR ETW pomocí nástroje Logman

1. Na příkazovém řádku zadejte:

     `logman start clrevents -p {e13c0d23-ccbc-4e12-931b-d9cc2eee27e4} 0x1CCBD 0x5 -ets -ct perf`

     kde:

    - `-p`Parametr identifikuje identifikátor GUID zprostředkovatele.

    - `0x1CCBD`Určuje kategorie událostí, které budou vyvolány.

    - `0x5`Nastaví úroveň protokolování (v tomto případě verbose (5)).

    - `-ets`Parametr nastaví příkaz logman k odeslání příkazů do relací trasování událostí.

    - `-ct perf`Parametr určuje, že `QueryPerformanceCounter` funkce bude použita k zaznamenání časového razítka pro každou událost.

2. K ukončení protokolování událostí zadejte:

     `logman stop clrevents -ets`

     Tento příkaz vytvoří binární soubor trasování s názvem clrevents.etl.

### <a name="to-capture-clr-etw-events-using-xperf"></a>Zachycení událostí CLR ETW pomocí nástroje Xperf

1. Na příkazovém řádku zadejte:

     `xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:5 -f clrevents.etl`

     kde identifikátor GUID je identifikátor GUID zprostředkovatele modulu CLR ETW a `0x1CCBD:5` sleduje vše na úrovni 5 (verbose).

2. Chcete-li zastavit trasování, zadejte:

     `Xperf -stop clr`

     Tento příkaz vytvoří soubor trasování s názvem clrevents.etl.

## <a name="viewing-clr-etw-events"></a>Zobrazení událostí CLR ETW

Pro zobrazení událostí CLR ETW je možné použít následující příkazy. Popis událostí naleznete v tématu [CLR ETW Events](clr-etw-events.md).

### <a name="to-view-clr-etw-events-using-tracerpt"></a>Zobrazení událostí CLR ETW pomocí nástroje Tracerpt

- Na příkazovém řádku zadejte:

     `tracerpt clrevents.etl`

     Tento příkaz vytvoří dva soubory: dumpfile.xml a summary.txt. Soubor dumpfile.xml obsahuje seznam všech událostí a summary.txt poskytuje souhrn událostí.

### <a name="to-view-clr-etw-events-using-xperf"></a>Zobrazení událostí CLR ETW pomocí nástroje Xperf

- Na příkazovém řádku zadejte:

     `xperf clrevents.etl`

     Tento příkaz otevře prohlížeč souborů ETL nástroje Xperf. V tomto prohlížeči se události CLR zobrazí v zobrazení **Obecné události** . Chcete-li zobrazit datovou mřížku událostí podle typu, vyberte oblast času v tomto zobrazení a potom klikněte pravým tlačítkem myši a vyberte možnost **Souhrn**.

### <a name="to-convert-the-etl-file-to-a-comma-separated-value-file"></a>Převod souboru .etl na soubor .csv

- Na příkazovém řádku zadejte:

     `xperf -i clrevents.etl -f clrevents.csv`

     Tento příkaz způsobí, že nástroj XPerf vypíše paměť událostí do souboru CSV, který je možné zobrazit. Protože různé události mají různá pole, tento soubor CSV obsahuje před daty více než jeden řádek záhlaví. První pole každého řádku je typ události, který určuje záhlaví, které se má použít pro určení zbývajících polí.

## <a name="see-also"></a>Viz také

- [Sada Windows Performance Toolkit](/windows-hardware/test/wpt/)
- [Události Trasování událostí pro Windows v CLR (Common Language Runtime)](etw-events-in-the-common-language-runtime.md)
