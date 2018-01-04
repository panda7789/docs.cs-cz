---
title: ".NET Framework – výkon"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance [.NET Framework]
- reliability [.NET Framework]
ms.assetid: c1676cca-3f1a-41ec-b469-9029566074fc
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aa4db0e3e136eee1d2037ad6041ac6945d313776
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="net-framework-performance"></a>.NET Framework – výkon
Pokud chcete vytvářet aplikace s vysoký výkon, doporučujeme návrhu a plánování výkonu stejně jako jakékoli jiné funkce aplikace by návrhu. Můžete použít nástroje poskytované společností Microsoft k měření výkonu vaší aplikace a, v případě potřeby zlepšení využití paměti, propustnost kódu a odezvy. Toto téma obsahuje seznam nástrojů analýzy výkonu, poskytuje Microsoft a poskytuje odkazy na další témata, které se týkají výkonu pro konkrétní oblasti vývoj aplikací.  
  
## <a name="designing-and-planning-for-performance"></a>Návrh a plánování výkonu  
 Pokud chcete skvělá provádění aplikace, je třeba navrhnout výkonu do vaší aplikace, stejně jako jakékoli jiné funkce by návrhu. Časná a často, měli byste určit výkon kritické scénáře v aplikace, sada výkonnostní cíle a míra výkonu pro tyto scénáře aplikace. Protože každá aplikace se liší a obsahuje jinou důležitá výkonu provádění cesty, již v rané fázi určení těchto cestách a spojením vaše úsilí umožňují zvýšit vaši produktivitu na maximum.  
  
 Nemusíte být zcela obeznámeni s svou cílovou platformu k vytvoření vysoce výkonné aplikace. Nicméně byste měli vytvořit představu, které jsou součástí cílové platformy náročné na výkon. To provedete pomocí měření výkonu časná ve vývojových procesech.  
  
 K určení oblasti, které jsou důležité pro výkon a zřízení výkonnostní cíle, vždycky je třeba činnost koncového uživatele. Čas spuštění a odezvy jsou dvě klíčové oblasti, které ovlivní dojem uživatele vaší aplikace. Pokud vaše aplikace používá velké množství paměti, pravděpodobně se zobrazí uživateli pomalá nebo mít vliv na ostatní aplikace běžící v systému, nebo, v některých případech se pravděpodobně nezdaří proces odesílání Windows Store nebo Windows Phone Store. Pokud zjistíte, jaké části kódu provést častěji, můžete můžete Ujistěte se také, že jsou tyto části kódu dobře optimalizované.  
  
## <a name="analyzing-performance"></a>Analýza výkonu  
 Jako součást plánu celkový vývoj nastavte bodů během vývoje kde budou měřit výkon aplikace a porovnat výsledky s cílů, které nastavíte, dříve. Měření aplikace v prostředí a hardware, který budou vaši uživatelé tak, aby měl. Časná a často analýzou výkon vaší aplikace, můžete změnit architektury rozhodnutí, která by být nákladná a drahý opravte později v cyklu vývoje. Následující části popisují nástroje pro sledování výkonu, které můžete použít k analýze aplikace a diskutovat o trasování událostí, který je používán těchto nástrojů.  
  
### <a name="performance-tools"></a>Nástroje pro měření výkonu  
 Zde jsou některé nástroje pro sledování výkonu, které můžete použít s vaší aplikací rozhraní .NET Framework.  
  
|Nástroj|Popis|  
|----------|-----------------|  
|Analýza výkonu sady Visual Studio|Slouží k analýze využití CPU aplikace rozhraní .NET Framework, které se nasadí do počítačů s operačním systémem Windows.<br /><br /> Tento nástroj najdete na webu **ladění** nabídky v sadě Visual Studio po otevření projektu. Další informace najdete v tématu [prohlížeč výkonu](/visualstudio/profiling/performance-explorer). **Poznámka:** analýza aplikace Windows Phone pomocí (viz další řádek) Pokud je cílem Windows Phone.|  
|Analýza aplikace Windows Phone|Slouží k analýze procesoru a paměť, rychlost přenosu dat sítě, rychlost reakce aplikace a energie baterie v aplikacích Windows Phone.<br /><br /> Tento nástroj najdete na webu **ladění** nabídky pro Windows Phone projekt v sadě Visual Studio po instalaci [Windows Phone SDK](http://go.microsoft.com/fwlink/?LinkId=265773). Další informace najdete v tématu [profilace aplikace pro Windows Phone](http://msdn.microsoft.com/library/windowsphone/develop/jj215908\(v=vs.105\).aspx).|  
|[Nástroje PerfView](http://www.microsoft.com/download/details.aspx?id=28567)|Slouží k identifikaci procesoru a problémy s výkonem souvisejících s pamětí. K poskytování pokročilé paměti a procesoru vyšetřování a také informace o uvolňování paměti a JIT – kompilace používá tento nástroj trasování událostí pro Windows (ETW) a CLR profilace rozhraní API. Další informace o tom, jak pomocí nástroje PerfView, najdete v části kurzu a pomáhá soubory, které jsou součástí aplikace, [video kurzy Channel 9](http://channel9.msdn.com/Series/PerfView-Tutorial), a [příspěvcích na blogu](http://blogs.msdn.com/b/vancem/archive/tags/perfview/).<br /><br /> Problémy specifické pro paměť najdete v tématu [pomocí nástroje PerfView pro vyšetřování paměti](http://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-9-NET-Memory-Investigation-Basics-of-GC-Heap-Snapshots).|  
|[Analyzátor výkonu Windows](http://www.microsoft.com/download/details.aspx?id=30652)|Použijte k určení výkonu celého systému, jako např. paměti vaší aplikace a velikost úložiště použít při více aplikace běží na stejném počítači. Tento nástroj je k dispozici z webu Stažení softwaru jako část sady Windows Assessment and Deployment Kit (ADK) pro [!INCLUDE[win8](../../../includes/win8-md.md)]. Další informace najdete v tématu [Analyzátor výkonu Windows](http://msdn.microsoft.com/library/windows/desktop/hh448170.aspx).|  
  
### <a name="event-tracing-for-windows-etw"></a>Trasování událostí pro Windows (ETW)  
 Trasování událostí pro Windows je technika, který umožňuje získat diagnostické informace o spuštění kódu a je nezbytné pro řadu nástroje pro sledování výkonu, které již bylo zmíněno dříve. Trasování událostí pro Windows vytvoří protokoly při určité události jsou vyvolány aplikací rozhraní .NET Framework a Windows. S trasování událostí pro Windows můžete povolit a zakázat protokolování dynamicky, aby mohli provést podrobného trasování v provozním prostředí bez restartování aplikace. Rozhraní .NET Framework nabízí podporu pro události trasování událostí a trasování událostí pro Windows používá celou řadu nástrojů pro profilaci a výkon pro generování dat výkonu. Tyto nástroje často povolit nebo zakázat události trasování událostí, takže znalost je užitečné. Konkrétní události trasování událostí můžete použít ke shromažďování výkonu informace o konkrétní součásti vaší aplikace. Další informace o podpoře trasování událostí pro Windows v rozhraní .NET Framework najdete v tématu [události trasování událostí v modulu Common Language Runtime](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md) a [události trasování událostí pro Windows v knihovně Task Parallel Library a PLINQ](../../../docs/framework/performance/etw-events-in-task-parallel-library-and-plinq.md).  
  
## <a name="performance-by-app-type"></a>Výkon podle typu aplikace  
 Každý typ rozhraní .NET Framework aplikace má vlastní osvědčených postupů, důležité informace a nástroje pro vyhodnocení výkonu. Následující tabulka odkazy na témata výkonu pro konkrétní typy aplikací rozhraní .NET Framework.  
  
|Typ aplikace|Další informace naleznete v tématu|  
|--------------|---------|  
|Aplikace rozhraní .NET framework pro všechny platformy|[Kolekce paměti a výkon](../../../docs/standard/garbage-collection/performance.md)<br /><br /> [Tipy pro zvýšení výkonu](../../../docs/framework/performance/performance-tips.md)|  
|[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]aplikace napsané v C++, C# a Visual Basic|[Osvědčené postupy z hlediska výkonu pro aplikace Windows Store pomocí C++, C# a Visual Basic](http://msdn.microsoft.com/library/windows/apps/hh750313.aspx)|  
|Windows Phone|[Faktory ovlivňující výkon aplikace pro Windows Phone](http://msdn.microsoft.com/library/windowsphone/develop/ff967560\(v=vs.105\).aspx)<br /><br /> [Analýza aplikace Windows Phone](http://msdn.microsoft.com/library/windowsphone/develop/hh202934\(v=vs.105\).aspx)<br /><br /> [Získat aplikace pro Windows Phone rychlejší na webu Marketplace](http://msdn.microsoft.com/magazine/hh781024.aspx)|  
|Windows Presentation Foundation (WPF)|[WPF – výkonnostní sada](http://msdn.microsoft.com/library/67cafaad-57ad-4ecb-9c08-57fac144393e)|  
|Silverlight|[Tipy pro zvýšení výkonu](http://msdn.microsoft.com/library/cc189071\(v=vs.95\).aspx)|  
|ASP.NET|[Přehled výkonnostní ASP.NET](http://msdn.microsoft.com/library/f882bf1b-a009-4312-ac06-74370ffabc0b)|  
|Windows Forms|[Praktické tipy pro zvýšení výkonu aplikací pro Windows Forms](http://msdn.microsoft.com/magazine/cc163630.aspx)|  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Ukládání do vyrovnávací paměti v aplikacích .NET Framework](../../../docs/framework/performance/caching-in-net-framework-applications.md)|Popisuje techniky pro ukládání do mezipaměti data ke zlepšení výkonu ve vaší aplikaci.|  
|[Opožděná inicializace](../../../docs/framework/performance/lazy-initialization.md)|Popisuje, jak třeba inicializovat objekty podle potřeby ke zlepšení výkonu, zejména při spuštění aplikace.|  
|[Spolehlivost](../../../docs/framework/performance/reliability.md)|Poskytuje informace o brání asynchronní výjimky v prostředí serverů.|  
|[Psaní velkých a pohotově reagujících aplikací .NET Framework](../../../docs/framework/performance/writing-large-responsive-apps.md)|Poskytuje tipy pro zvýšení výkonu získané z přepisování C# a Visual Basic kompilátory ve spravovaném kódu a zahrnuje několik příkladů skutečné z kompilátoru C#.|
