---
title: "Běhová profilace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance counters
- common language runtime, profiling
- Perfmon.exe
- System Monitor
- profiling
- runtime, profiling
- profiling applications
- Performance Console
ms.assetid: ccd68284-f3a8-47b8-bc3f-92e5fe3a1640
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4a8f3af4878e0f6911fcc55ec76b26649d517b3b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="runtime-profiling"></a>Běhová profilace
Profilace je metoda shromažďování dat výkonu v žádném scénáři vývoj nebo nasazení. Tato část je určena pro vývojáře a správce systému, kteří chtějí shromažďovat informace o výkonu aplikací.  
  
## <a name="tracking-performance-using-the-performance-monitor-perfmonexe"></a>Sledování výkonu pomocí sledování výkonu (Perfmon.exe)  
 Sledování výkonu je nejjednodušší nástroj sloužící k profilu vaší [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] aplikace. Sledování výkonu graficky představuje data nalezen v rozhraní .NET Framework čítače výkonu, které jsou nainstalované s modul common language runtime a [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]. Tyto čítače lze monitorovat všechno, co je ze správy paměti na výkon kompilátoru za běhu (JIT). Jejich vás informovat o prostředky vaše aplikace používá, což je nepřímým měřítkem výkon aplikace. Pomocí těchto čítačů pochopit, jak vaše aplikace funguje interně.  
  
#### <a name="to-run-perfmonexe-on-windows-vista-and-later-versions"></a>Ke spuštění Perfmon.exe ve Windows Vista a novějších verzích  
  
1.  Na příkazovém řádku zadejte **perfmon**. **Sledování výkonu** konzoly se zobrazí.  
  
2.  V **nástroje pro sledování** složku, klikněte na tlačítko **sledování výkonu**.  
  
3.  Na panelu nástrojů nástroje Sledování výkonu, klikněte **přidat** ikona (znaménko plus), jestliže je nachází. Pokud není přítomen, klikněte pravým tlačítkem myši do okna sledování a vyberte **přidat čítače** možnost.  
  
     Tím se otevře **přidat čítače** dialogové okno. **Dostupné čítače** seznamu se zobrazí objekty výkonu k dispozici. Existuje několik předdefinovaných objektů pro aplikace .NET Framework, včetně těch, které pro správu paměti (**využívání paměti rozhraním .NET CLR**), interoperability (**zprostředkovatel komunikace s objekty .NET CLR**), zpracování výjimek (**.NET CLR – výjimky na**) a více vláken (**.NET CLR LocksAndThreads**). Každý objekt výkonu zahrnuje několik jednotlivé čítače. Seznam dostupných v nástroji Sledování výkonu čítačů výkonu najdete v tématu [čítače výkonu](../../../docs/framework/debug-trace-profile/performance-counters.md).  
  
4.  Zaškrtněte políčko vedle názvu objektu výkonu pro zobrazení seznamu jednotlivé čítače, které podporuje.  
  
5.  Klikněte na tlačítko čítač výkonu, které chcete zobrazit.  
  
6.  V **instance zvoleného objektu** seznam pole, klikněte na tlačítko  **\<všechny instance >** k určení, že chcete do monitorování čítače výkonu pro modul common language runtime globálně (který je na základ celého systému).  
  
     -nebo-  
  
     V **instance zvoleného objektu** seznam pole, klikněte na název aplikace pro monitorování čítače výkonu pro tuto aplikaci.  
  
     Chcete-li rozlišit několik verzí modulu runtime nebo k rozlišení více aplikací se stejným názvem, je třeba upravit klíč registru. Další informace najdete v tématu [čítače výkonu a aplikace vedle sebe v procesu](../../../docs/framework/debug-trace-profile/performance-counters-and-in-process-side-by-side-applications.md).  
  
> [!NOTE]
>  Při instalaci nové čítače výkonu je spuštěna konzola výkonu zastavit a restartovat konzolu výkonu chcete zviditelnit nové čítače.  
  
 Pokud chcete profil sestavení, které existuje v zóně, nebo na vzdálené sdílené složky, ujistěte se, že vzdálený sestavení má úplný vztah důvěryhodnosti na počítač, který spouští čítače výkonu. Pokud sestavení nemá dostatečná vztah důvěryhodnosti, čítače výkonu nebudou fungovat. Informace o udělení důvěry různým zónám najdete v tématu [Caspol.exe (nástroj zásad zabezpečení přístupu kódu)](../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md).  
  
> [!NOTE]
>  V systémech, na kterém [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] je nainstalovaná, sledování výkonu nemusí být zobrazeny dat pro čítače výkonu v některých kategorií, například **.NET CLR Data** a **.NET CLR sítě**, pro aplikace vyvinuté pomocí [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)]. Pokud je to tento případ, můžete nakonfigurovat sledování výkonu, které chcete zobrazit tato data tak, že přidáte [ \<forceperformancecounteruniquesharedmemoryreads – >](../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md) element konfiguračního souboru aplikace.  
  
## <a name="reading-and-creating-performance-counters-programmatically"></a>Čtení a vytvoření čítače výkonu prostřednictvím kódu programu  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Poskytuje třídy, které můžete použít k programovému přístupu ke stejné informace o výkonu, která je k dispozici v konzole výkonu. Tyto třídy můžete také vytvořit vlastní čítače výkonu. Následující tabulka popisuje některé třídy, které jsou součástí pro monitorování výkonu [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType>|Představuje součást čítače výkonu systému Windows NT. Tato třída slouží ke čtení existující předdefinované nebo vlastní čítače a vydávání dat výkonu (zápis) pro vlastní čítače.|  
|<xref:System.Diagnostics.PerformanceCounterCategory?displayProperty=nameWithType>|Poskytuje několik metod pro interakci s kategorií čítačů v počítači a čítače.|  
|<xref:System.Diagnostics.PerformanceCounterInstaller?displayProperty=nameWithType>|Určuje instalační program pro `PerformanceCounter` součásti.|  
|<xref:System.Diagnostics.PerformanceCounterType?displayProperty=nameWithType>|Určuje vzorce pro výpočet `NextValue` metodu `PerformanceCounter`.|  
  
## <a name="see-also"></a>Viz také  
 [Čítače výkonu](../../../docs/framework/debug-trace-profile/performance-counters.md)
