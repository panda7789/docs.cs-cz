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
ms.openlocfilehash: daa2ae4fbbed78bda4648b4b3077fa7d96a9b3f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121561"
---
# <a name="runtime-profiling"></a>Běhová profilace
Profilace je metoda shromažďování údajů o výkonu ve scénáři vývoje nebo nasazení. Tato část je určená pro vývojáře a správce systému, kteří chtějí shromažďovat informace o výkonu aplikace.  
  
## <a name="tracking-performance-using-the-performance-monitor-perfmonexe"></a>Sledování výkonu pomocí nástroje sledování výkonu (Perfmon. exe)  
 Nástroj Sledování výkonu je nejjednodušším nástrojem, který slouží k profilování aplikace .NET Framework. Monitor výkonu graficky reprezentuje data zjištěná v .NET Frameworkch čítačích výkonu, které jsou nainstalovány s modulem CLR (Common Language Runtime) a Windows SDK. Tyto čítače lze použít k monitorování všeho od správy paměti až po výkon kompilátoru JIT (just-in-time). Poskytují informace o prostředcích, které vaše aplikace používá, což je nepřímá míra výkonu vaší aplikace. Pomocí těchto čítačů můžete pochopit, jak vaše aplikace funguje interně.  
  
#### <a name="to-run-perfmonexe-on-windows-vista-and-later-versions"></a>Spuštění programu Perfmon. exe v systému Windows Vista a novějších verzích  
  
1. Do příkazového řádku zadejte **perfmon**. Zobrazí se konzola **nástroje sledování výkonu** .  
  
2. Ve složce **Nástroje pro sledování** klikněte na **sledování výkonu**.  
  
3. Na panelu nástrojů sledování výkonu klikněte na ikonu **Přidat** (znaménko plus), pokud je k dispozici. Pokud není k dispozici, klikněte pravým tlačítkem myši v okně monitorování a vyberte možnost **Přidat čítače** .  
  
     Tím se otevře dialogové okno **Přidat čítače** . Seznam **Dostupné čítače** zobrazuje dostupné objekty výkonu. K dispozici je řada předdefinovaných objektů pro .NET Framework aplikace, včetně funkcí pro správu paměti (**paměť .NET CLR**), interoperability (**zprostředkovatel komunikace .NET CLR**), zpracování výjimek (**výjimky .NET CLR**) a Multithreading ( **.NET CLR LocksAndThreads**). Každý objekt výkonu obsahuje počet jednotlivých čítačů výkonu. Seznam čítačů výkonu dostupných v nástroji Sledování výkonu najdete v tématu [čítače výkonu](performance-counters.md).  
  
4. Zaškrtněte políčko vedle názvu objektu výkonu, chcete-li zobrazit seznam jednotlivých čítačů výkonu, které podporuje.  
  
5. Klikněte na čítač výkonu, který chcete zobrazit.  
  
6. V seznamu **instance vybraného objektu** klikněte na **\<všechny instance >** určete, že chcete monitorovat čítač výkonu pro modul CLR (Common Language Runtime) globálně (to znamená na úrovni systému).  
  
     -nebo-  
  
     V poli se seznamem **instancí vybraného objektu** klikněte na název aplikace a sledujte čítač výkonu této aplikace.  
  
     Chcete-li odlišit více verzí modulu runtime nebo rozlišit více aplikací se stejným názvem, je nutné také upravit klíč registru. Další informace najdete v tématu [čítače výkonu a vnitroprocesové souběžné aplikace](performance-counters-and-in-process-side-by-side-applications.md).  
  
> [!NOTE]
> Když se při spuštění konzoly výkonu nainstalují nové čítače výkonu, zastavte a restartujte konzolu výkonu, aby se nové čítače zobrazily.  
  
 Chcete-li profilovat sestavení, které existuje v zóně nebo na vzdálené sdílené složce, ujistěte se, že má vzdálené sestavení v počítači, který spouští čítače výkonu, úplný vztah důvěryhodnosti. Pokud sestavení nemá dostatečný vztah důvěryhodnosti, čítače výkonu nebudou fungovat. Informace o udělení důvěryhodnosti do různých zón naleznete v tématu [Caspol. exe (Nástroj pro zásady zabezpečení přístupu kódu)](../tools/caspol-exe-code-access-security-policy-tool.md).  
  
> [!NOTE]
> V systémech, na kterých je nainstalován .NET Framework 4, nemusí monitor výkonu zobrazovat data pro čítače výkonu v některých kategoriích, jako jsou **data .NET CLR** a **sítě .NET CLR**, pro aplikace, které byly vyvinuty pomocí rozhraní .NET. Rozhraní 1,1. Pokud se jedná o tento případ, můžete nakonfigurovat nástroj sledování výkonu pro zobrazení těchto dat přidáním prvku [\<forcePerformanceCounterUniqueSharedMemoryReads >](../configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md) do konfiguračního souboru aplikace.  
  
## <a name="reading-and-creating-performance-counters-programmatically"></a>Načítání a vytváření čítačů výkonu prostřednictvím kódu programu  
 .NET Framework poskytuje třídy, které lze použít k programovému přístupu ke stejným informacím o výkonu, které jsou k dispozici v konzole výkon. Tyto třídy můžete použít také k vytvoření vlastních čítačů výkonu. Následující tabulka popisuje některé třídy monitorování výkonu, které jsou k dispozici v .NET Framework.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType>|Představuje součást čítače výkonu systému Windows NT. Tato třída se používá ke čtení existujících předdefinovaných nebo vlastních čítačů a k publikování (zápisu) údajů o výkonu do vlastních čítačů.|  
|<xref:System.Diagnostics.PerformanceCounterCategory?displayProperty=nameWithType>|Poskytuje několik metod pro interakci s čítači a kategoriemi čítačů v počítači.|  
|<xref:System.Diagnostics.PerformanceCounterInstaller?displayProperty=nameWithType>|Určuje instalační program pro součást `PerformanceCounter`.|  
|<xref:System.Diagnostics.PerformanceCounterType?displayProperty=nameWithType>|Určuje vzorec pro výpočet `NextValue` metody pro `PerformanceCounter`.|  
  
## <a name="see-also"></a>Viz také:

- [Čítače výkonu](performance-counters.md)
