---
title: Řízení přihlašování rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events, logging
ms.assetid: ce13088e-3095-4f0e-9f6b-fad30bbd3d41
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1bee42db7b9a92723b0640d0b3747a7921b8617c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43418982"
---
# <a name="controlling-net-framework-logging"></a>Řízení přihlašování rozhraní .NET Framework
Pro zaznamenání událostí modulu Common Language Runtime (CLR) je možné použít trasování událostí systému Windows (ETW). Můžete vytvořit a zobrazit trasování pomocí následujících nástrojů:  
  
-   [Logman](https://go.microsoft.com/fwlink/?LinkId=150916) a [Tracerpt](https://go.microsoft.com/fwlink/?LinkId=150919) nástroje příkazového řádku, které jsou součástí operačního systému Windows.  
  
-   [Xperf](https://msdn.microsoft.com/library/windows/hardware/hh162920.aspx) nástroje v [Windows Performance Toolkit](https://msdn.microsoft.com/library/windows/hardware/hh162945.aspx). Další informace o nástroji Xperf naleznete v tématu [blogu Windows Performance](https://go.microsoft.com/fwlink/?LinkId=179509).  
  
 Pro zaznamenání informací události modulu CLR musí být v počítači nainstalován zprostředkovatel modulu CLR. Pokud chcete potvrdit, že je daný poskytovatel nainstalován, zadejte `logman query providers` příkazového řádku. Zobrazí se seznam zprostředkovatelů. Tento seznam by měl obsahovat následující záznam pro zprostředkovatele modulu CLR.  
  
```  
Provider                                 GUID  
-------------------------------------------------------------------------------  
.NET Common Language Runtime    {E13C0D23-CCBC-4E12-931B-D9CC2EEE27E4}.  
```  
  
 Pokud není zprostředkovatel modulu CLR uveden, můžete instalaci na Windows Vista a novějších operačních systémů s použitím Windows [Wevtutil](https://go.microsoft.com/fwlink/?LinkID=150915) nástroj příkazového řádku. Otevřete okno příkazového řádku jako správce. Změňte adresář na výzvy [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] složky (% WINDIR%\Microsoft.NET\Framework[64]\v4.\<.NET verze >\ ). Tato složka obsahuje soubor CLR-ETW.man. Pro instalaci zprostředkovatele modulu CLR zadejte v příkazovém řádku následující příkaz:  
  
 `wevtutil im CLR-ETW.man`  
  
## <a name="capturing-clr-etw-events"></a>Zachycení událostí CLR ETW  
 Můžete použít [Logman](https://go.microsoft.com/fwlink/?LinkId=150916) a [Xperf](https://msdn.microsoft.com/library/windows/hardware/hh162920.aspx) nástroje příkazového řádku k zachycení událostí trasování událostí pro Windows a [Tracerpt](https://go.microsoft.com/fwlink/?LinkId=150919) a [Xperf](https://msdn.microsoft.com/library/windows/hardware/hh162920.aspx) k dekódování události trasování.  
  
 K zapnutí protokolování musí uživatel specifikovat tři věci:  
  
-   Zprostředkovatele pro komunikaci.  
  
-   64bitové číslo představující sadu klíčových slov. Každé klíčové slovo představuje sadu událostí, které může zprostředkovatel zapnout. Číslo představuje kombinovanou sadu klíčových slov pro zapnutí.  
  
-   Malé číslo představující úroveň (podrobnost) protokolu. Úroveň 1 je nejméně podrobná a úroveň 5 je nejvíce podrobná. Úroveň 0 je výchozí a její význam závisí na konkrétním zprostředkovateli.  
  
#### <a name="to-capture-clr-etw-events-using-logman"></a>Zachycení událostí CLR ETW pomocí nástroje Logman  
  
1.  V příkazovém řádku zadejte příkaz:  
  
     `logman start clrevents -p {e13c0d23-ccbc-4e12-931b-d9cc2eee27e4} 0x1CCBD 0x5 -ets -ct perf`  
  
     kde:  
  
    -   `-p` Parametr identifikuje GUID zprostředkovatele.  
  
    -   `0x1CCBD` Určuje kategorie událostí, které budou aktivovány.  
  
    -   `0x5` Nastaví úroveň protokolování (v tomto případě verbose [5]).  
  
    -   `-ets` Parametr dává pokyn nástroji Logman odesílat příkazy do relace trasování událostí.  
  
    -   `-ct perf` Parametr určuje, že `QueryPerformanceCounter` funkce se použije k zaznamenání časového razítka pro každou jednotlivou událost.  
  
2.  K ukončení protokolování událostí zadejte:  
  
     `logman stop clrevents -ets`  
  
     Tento příkaz vytvoří binární soubor trasování s názvem clrevents.etl.  
  
#### <a name="to-capture-clr-etw-events-using-xperf"></a>Zachycení událostí CLR ETW pomocí nástroje Xperf  
  
1.  V příkazovém řádku zadejte příkaz:  
  
     `xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:5 -f clrevents.etl`  
  
     kde GUID je GUID zprostředkovatele CLR ETW a `0x1CCBD:5` trasuje vše na a nižší než úroveň 5 (podrobné).  
  
2.  Chcete-li zastavit trasování, zadejte:  
  
     `Xperf -stop clr`  
  
     Tento příkaz vytvoří soubor trasování s názvem clrevents.etl.  
  
## <a name="viewing-clr-etw-events"></a>Zobrazení událostí CLR ETW  
 Pro zobrazení událostí CLR ETW je možné použít následující příkazy. Popis událostí naleznete v tématu [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md).  
  
#### <a name="to-view-clr-etw-events-using-tracerpt"></a>Zobrazení událostí CLR ETW pomocí nástroje Tracerpt  
  
-   V příkazovém řádku zadejte příkaz:  
  
     `tracerpt clrevents.etl`  
  
     Tento příkaz vytvoří dva soubory: dumpfile.xml a summary.txt. Soubor dumpfile.xml obsahuje seznam všech událostí a summary.txt poskytuje souhrn událostí.  
  
#### <a name="to-view-clr-etw-events-using-xperf"></a>Zobrazení událostí CLR ETW pomocí nástroje Xperf  
  
-   V příkazovém řádku zadejte příkaz:  
  
     `xperf clrevents.etl`  
  
     Tento příkaz otevře prohlížeč souborů ETL nástroje Xperf. V tomto prohlížeči se události CLR zobrazují v **obecné události** zobrazení. Pro zobrazení mřížky dat událostí zařazených do kategorií podle typu, vyberte oblast času v tomto zobrazení a pak klikněte pravým tlačítkem a vyberte **Souhrn**.  
  
#### <a name="to-convert-the-etl-file-to-a-comma-separated-value-file"></a>Převod souboru .etl na soubor .csv  
  
-   V příkazovém řádku zadejte příkaz:  
  
     `xperf -i clrevents.etl -f clrevents.csv`  
  
     Tento příkaz způsobí, že nástroj XPerf vypíše paměť událostí do souboru CSV, který je možné zobrazit. Protože různé události mají různá pole, tento soubor CSV obsahuje před daty více než jeden řádek záhlaví. První pole každého řádku je typ události, který určuje záhlaví, které se má použít pro určení zbývajících polí.  
  
## <a name="see-also"></a>Viz také  
 [Sada Windows Performance Toolkit](https://go.microsoft.com/fwlink/?LinkID=161141)  
 [Události Trasování událostí pro Windows v CLR (Common Language Runtime)](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
