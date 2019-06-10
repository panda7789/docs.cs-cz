---
title: Běhová profilace
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0c56018c61e5566043fb2b9ba8bbee042093f12
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758149"
---
# <a name="runtime-profiling"></a>Běhová profilace
Profilace je metoda shromažďování dat výkonu ve všech scénářích vývoj nebo nasazení. Tato část se týká vývojáři a správci systému, kteří chtějí získat informace o výkonu aplikace.  
  
## <a name="tracking-performance-using-the-performance-monitor-perfmonexe"></a>Sledování výkonu pomocí sledování výkonu (Perfmon.exe)  
 Sledování výkonu je nejjednodušší nástroje pro použití Chcete-li Profilovat aplikaci rozhraní .NET Framework. Sledování výkonu graficky představuje data v rozhraní .NET Framework čítačů výkonu, které jsou součástí common language runtime a [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]. Tyto čítače umožňuje monitorovat vše od správy paměti na výkon kompilátor just-in-time (JIT). Upozorní vás, o prostředcích vaše aplikace využívá, což je nepřímé zlomek výkonu vaší aplikace. Tyto čítače slouží k pochopení, jak vaše aplikace funguje interně.  
  
#### <a name="to-run-perfmonexe-on-windows-vista-and-later-versions"></a>Ke spuštění Perfmon.exe ve Windows Vista a novějších verzích  
  
1. Na příkazovém řádku zadejte **perfmon**. **Sledování výkonu** konzoly se zobrazí.  
  
2. V **nástroje pro sledování** složky, klikněte na tlačítko **sledování výkonu**.  
  
3. Na panelu nástrojů nástroje Sledování výkonu, klepněte **přidat** ikonu (znaménko plus), pokud je k dispozici. Pokud tam není, klikněte pravým tlačítkem v okně Sledování a vyberte **přidat čítače** možnost.  
  
     Tím se otevře **přidat čítače** dialogové okno. **Dostupné čítače** seznamu se zobrazí objekty výkonu k dispozici. Existuje mnoho předdefinovaných objektů pro aplikace .NET Framework, včetně těch, které pro správu paměti (**paměť .NET CLR**), vzájemná funkční spolupráce (**spolupráce .NET CLR**), zpracování výjimek (**Výjimky .NET CLR**) a multithreading (**uzamčení a vlákna .NET CLR**). Každý objekt sledování výkonu zahrnuje celou řadou jednotlivé čítače. Seznam dostupných v nástroji Sledování výkonu čítačů výkonu najdete v tématu [čítače výkonu](../../../docs/framework/debug-trace-profile/performance-counters.md).  
  
4. Zaškrtněte políčko vedle názvu objekt sledování výkonu a zobrazit seznam jednotlivé čítače, které podporuje.  
  
5. Klikněte na čítač výkonu, které chcete zobrazit.  
  
6. V **výskyty vybraný objekt** seznamu, klikněte na tlačítko  **\<všechny instance >** k určení, že chcete globálně monitorování čítače výkonu pro modul common language runtime (to znamená na celého systému).  
  
     -nebo-  
  
     V **výskyty vybraný objekt** seznamu, klikněte na název aplikace pro monitorování čítače výkonu pro tuto aplikaci.  
  
     K rozlišení více verzí modulu runtime, nebo k rozlišení více aplikací se stejným názvem, je třeba také upravit klíč registru. Další informace najdete v tématu [čítače výkonu a Vnitroprocesorové aplikace vedle sebe](../../../docs/framework/debug-trace-profile/performance-counters-and-in-process-side-by-side-applications.md).  
  
> [!NOTE]
>  Při instalaci nové čítače výkonu je spuštěna konzola výkonu, zastavit a restartovat konzolu výkonu chcete zviditelnit nové čítače.  
  
 Pokud chcete Profilovat sestavení, která existuje v zóně nebo ve vzdálené sdílené složce, ujistěte se, že vzdálené sestavení má úplný vztah důvěryhodnosti na počítač, na kterém běží čítače výkonu. Pokud sestavení nemá dostatek vztah důvěryhodnosti, nebude fungovat čítače výkonu. Informace o udělení důvěry různým zónám najdete v tématu [Caspol.exe (nástroj zásad zabezpečení přístupu kódu)](../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md).  
  
> [!NOTE]
>  V systémech, na kterých je nainstalované rozhraní .NET Framework 4, sledování výkonu nemusí zobrazit data pro čítače výkonu v některé kategorie, jako **.NET CLR Data** a **.NET CLR sítě**, pro aplikace, které byly vytvořeny pomocí rozhraní .NET Framework 1.1. Pokud je to tento případ, můžete nakonfigurovat monitorování výkonu pro zobrazení těchto dat tak, že přidáte [ \<forceperformancecounteruniquesharedmemoryreads – >](../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md) prvku do konfiguračního souboru aplikace.  
  
## <a name="reading-and-creating-performance-counters-programmatically"></a>Čtení a vytvoření čítače výkonu prostřednictvím kódu programu  
 Rozhraní .NET Framework poskytuje třídy, které můžete použít k programovému přístupu ke stejné informace výkonu, která je dostupná v konzole výkonu. Tyto třídy můžete také vytvořit vlastní čítače výkonu. Následující tabulka popisuje některé třídy, které jsou k dispozici v rozhraní .NET Framework pro sledování výkonu.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType>|Představuje součást čítače výkonu systému Windows NT. Tato třída slouží ke čtení existující předdefinovaných nebo vlastních čítačů a vydávání dat výkonu (zápis) do vlastních čítačů.|  
|<xref:System.Diagnostics.PerformanceCounterCategory?displayProperty=nameWithType>|Nabízí několik metod pro interakci s čítače a kategorie čítačů v počítači.|  
|<xref:System.Diagnostics.PerformanceCounterInstaller?displayProperty=nameWithType>|Určuje instalační program pro `PerformanceCounter` komponenty.|  
|<xref:System.Diagnostics.PerformanceCounterType?displayProperty=nameWithType>|Určuje vzorce pro výpočet `NextValue` metodu `PerformanceCounter`.|  
  
## <a name="see-also"></a>Viz také:

- [Čítače výkonu](../../../docs/framework/debug-trace-profile/performance-counters.md)
