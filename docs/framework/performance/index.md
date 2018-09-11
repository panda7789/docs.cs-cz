---
title: .NET Framework – výkon
ms.date: 03/30/2017
helpviewer_keywords:
- performance [.NET Framework]
- reliability [.NET Framework]
ms.assetid: c1676cca-3f1a-41ec-b469-9029566074fc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 59f8ceaf7981aebf3ae64e10d253004780f47e50
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44272875"
---
# <a name="net-framework-performance"></a>.NET Framework – výkon
Pokud chcete vytvářet aplikace s vynikajícím výkonem, měli byste navrhnout a naplánovat výkon stejně jako byste navrhovali libovolnou jinou funkci aplikace. Můžete použít nástroje poskytované společností Microsoft k měření výkonu vaší aplikace a, v případě potřeby zdokonalení využití paměti, propustnosti kódování a rychlost odezvy. Toto téma uvádí analytické nástroje výkonu, poskytuje Microsoft a obsahuje odkazy na další témata, která pokrývají výkon pro konkrétní oblasti vývoje aplikací.  
  
## <a name="designing-and-planning-for-performance"></a>Návrh a plánování pro výkon  
 Pokud chcete aplikaci se skvělým výkonem, je třeba navrhnout výkon do vaší aplikace stejným způsobem, jako byste navrhovali libovolnou jinou funkci. Brzké a časté byste měli určit scénáře důležité pro výkon ve své aplikaci, stanovit cíle výkonu a měřit výkon těchto scénářů aplikace. Protože každé aplikaci, která se liší a má cesty spuštění různých kritickém pro výkon, včasné stanovení těchto cest a zaměření úsilí umožňují maximálně zvýšily vaši produktivitu.  
  
 Nemusíte být zcela obeznámeni s cílovou platformou, k vytvoření vysoce výkonné aplikace. Nicméně byste měli vytvořit porozumění, které části cílové platformy jsou náročné na výkon. Můžete to provést pomocí změření výkonu v rané fázi vývojového procesu.  
  
 Při určování oblastí, které jsou nezbytné k výkonu a stanovení cílů výkonu, vždy zvažte uživatelské prostředí. Čas spuštění a reakce jsou dvě klíčové oblasti, které bude mít vliv na uživatele vnímání vaší aplikace. Pokud vaše aplikace používá velké množství paměti, může se zobrazí uživateli líná nebo ovlivnit jiné aplikace spuštěné v systému, nebo, v některých případech může selhat proces odeslání Windows Store nebo Windows Phone Store. Navíc pokud zjistíte, které části kódu se spouští častěji, zajistíte, že tyto části kódu jsou dobře optimalizované.  
  
## <a name="analyzing-performance"></a>Analýza výkonu  
 Jako součást celkového plánu rozvoje nastavte body během vývoje kde budete měřit výkon vaší aplikace a porovnávat výsledky s cíli, které jste dříve nastavili. Změřte aplikaci v prostředí a hardware, který očekáváte, že uživatelé budou používat. Analýzou výkonu vaší aplikace včas a často můžete změnit rozhodnutí o architektuře, které by byla nákladná a náročná dále v cyklu vývoje opravit. Následující části popisují nástroje výkonu, které můžete použít k analýze aplikací a diskutovat o trasování událostí, které tyto nástroje používají.  
  
### <a name="performance-tools"></a>Nástroje pro měření výkonu  
 Tady jsou některé nástroje pro sledování výkonu, která vám pomůže s vašimi aplikacemi rozhraní .NET Framework.  
  
|Nástroj|Popis|  
|----------|-----------------|  
|Analýza výkonu sady Visual Studio|Slouží k analýze využití procesoru aplikací rozhraní .NET Framework, které se nasadí na počítače, na kterých běží operační systém Windows.<br /><br /> Tento nástroj je k dispozici **ladění** nabídky v aplikaci Visual Studio po otevření projektu. Další informace najdete v tématu [prohlížeč výkonu](/visualstudio/profiling/performance-explorer). **Poznámka:** analýza aplikace použijte Windows Phone (viz další řádek) při cílení na Windows Phone.|  
|Analýza pro aplikace Windows Phone|Slouží k analýze procesoru a paměti, přenosové rychlosti síťových dat, rychlost odezvy aplikace a spotřeby baterie v aplikacích pro Windows Phone.<br /><br /> Tento nástroj je k dispozici **ladění** nabídku pro projekt Windows Phone v sadě Visual Studio po instalaci [Windows Phone SDK](https://go.microsoft.com/fwlink/?LinkId=265773). Další informace najdete v tématu [profilování aplikací pro Windows Phone](https://msdn.microsoft.com/library/windowsphone/develop/jj215908\(v=vs.105\).aspx).|  
|[PerfView](https://www.microsoft.com/download/details.aspx?id=28567)|Slouží k identifikaci procesoru a problémy s výkonem souvisejících s pamětí. Tento nástroj používá trasování událostí pro Windows (ETW) a rozhraní API profilování CLR k poskytování rozšířené paměti a procesoru vyšetřování, jakož i informace o uvolňování paměti a kompilace JIT. Další informace o tom, jak pomocí nástroje PerfView naleznete kurzu a souborech nápovědy, které jsou součástí aplikace, [video kurzy kanál 9](http://channel9.msdn.com/Series/PerfView-Tutorial), a [blogové příspěvky](https://blogs.msdn.com/b/vancem/archive/tags/perfview/).<br /><br /> Problémy specifické pro paměť naleznete v tématu [použití PerfView pro zkoumání paměti](http://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-9-NET-Memory-Investigation-Basics-of-GC-Heap-Snapshots).|  
|[Analyzátor výkonu Windows](https://www.microsoft.com/download/details.aspx?id=30652)|Použijte k určení celkového výkonu systému, jako je využití paměti a úložiště vaší aplikace při spuštění více aplikací ve stejném počítači. Tento nástroj je k dispozici ze služby Stažení softwaru jako součást sady Windows Assessment and Deployment Kit (ADK) pro [!INCLUDE[win8](../../../includes/win8-md.md)]. Další informace najdete v tématu [Analyzátor výkonu Windows](https://msdn.microsoft.com/library/windows/desktop/hh448170.aspx).|  
  
### <a name="event-tracing-for-windows-etw"></a>Trasování událostí pro Windows (ETW)  
 Trasování událostí pro Windows je technika, která umožňuje získat diagnostické informace o spuštěném kódu a je zásadní pro mnoho nástrojů pro sledování výkonu již bylo zmíněno dříve. Trasování událostí pro Windows vytvářejí protokoly, když určité události jsou vyvolány aplikací rozhraní .NET Framework a Windows. S ETW můžete povolit a zakázat protokolování dynamicky, takže je možné provádět podrobné sledování v provozním prostředí bez restartování aplikace. Rozhraní .NET Framework poskytuje podporu pro události ETW a ETW používá mnoho nástrojů pro profilaci a výkonu při generování dat výkonu. Tyto nástroje často povolit nebo zakázat události ETW, seznámení se s nimi je užitečné. Konkrétní události trasování událostí pro Windows můžete použít ke shromažďování informací o konkrétních součástech vaší aplikace. Další informace o podpoře ETW v rozhraní .NET Framework najdete v tématu [události trasování událostí v modulu Common Language Runtime](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md) a [události trasování událostí pro Windows v knihovně Task Parallel Library a PLINQ](../../../docs/framework/performance/etw-events-in-task-parallel-library-and-plinq.md).  
  
## <a name="performance-by-app-type"></a>Výkon podle typu aplikace  
 Každý typ rozhraní .NET Framework aplikace má vlastní doporučené postupy, důležité informace a nástroje pro hodnocení výkonu. Následující tabulka odkazuje na témata o výkonu pro konkrétní typy aplikací rozhraní .NET Framework.  
  
|Typ aplikace|Další informace naleznete v tématu|  
|--------------|---------|  
|Aplikace rozhraní .NET framework pro všechny platformy|[Kolekce paměti a výkon](../../../docs/standard/garbage-collection/performance.md)<br /><br /> [Tipy pro zvýšení výkonu](../../../docs/framework/performance/performance-tips.md)|  
|[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace napsané v jazyce C++, C# a Visual Basic|[Osvědčené postupy z hlediska výkonu pro aplikace Windows Store pomocí jazyka C++, C# a Visual Basic](https://msdn.microsoft.com/library/windows/apps/hh750313.aspx)|  
|Windows Phone|[Důležité informace o výkonu aplikací pro Windows Phone](https://msdn.microsoft.com/library/windowsphone/develop/ff967560\(v=vs.105\).aspx)<br /><br /> [Analýza pro aplikace Windows Phone](https://msdn.microsoft.com/library/windowsphone/develop/hh202934\(v=vs.105\).aspx)<br /><br /> [Zprovozněte své aplikace pro Windows Phone z webu Marketplace rychleji](https://msdn.microsoft.com/magazine/hh781024.aspx)|  
|Windows Presentation Foundation (WPF)|[WPF – výkonnostní sada](https://msdn.microsoft.com/library/67cafaad-57ad-4ecb-9c08-57fac144393e)|  
|Silverlight|[Tipy ke zvýšení výkonu](https://msdn.microsoft.com/library/cc189071\(v=vs.95\).aspx)|  
|ASP.NET|[ASP.NET: přehled výkonu](https://msdn.microsoft.com/library/f882bf1b-a009-4312-ac06-74370ffabc0b)|  
|Windows Forms|[Praktické tipy pro zvýšení výkonu aplikací Windows Forms](https://msdn.microsoft.com/magazine/cc163630.aspx)|  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Ukládání do vyrovnávací paměti v aplikacích .NET Framework](../../../docs/framework/performance/caching-in-net-framework-applications.md)|Popisuje postupy pro ukládání do mezipaměti dat s cílem zlepšit výkon ve vaší aplikaci.|  
|[Opožděná inicializace](../../../docs/framework/performance/lazy-initialization.md)|Popisuje, jak inicializovat objekty podle potřeby pro zvýšení výkonu, zejména při spuštění aplikace.|  
|[Spolehlivost](../../../docs/framework/performance/reliability.md)|Poskytuje informace o předcházení asynchronním výjimkám v prostředí serveru.|  
|[Psaní velkých a pohotově reagujících aplikací .NET Framework](../../../docs/framework/performance/writing-large-responsive-apps.md)|Poskytuje tipy ke zvýšení výkonu shromážděných z přepsání kompilátory C# i Visual Basic ve spravovaném kódu a obsahuje několik skutečné příklady z kompilátoru jazyka C#.|
