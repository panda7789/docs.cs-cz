---
title: .NET Framework – výkon
ms.date: 03/30/2017
helpviewer_keywords:
- performance [.NET Framework]
- reliability [.NET Framework]
ms.assetid: c1676cca-3f1a-41ec-b469-9029566074fc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b3f3d035ebf6472788e2c7d6e11cb1a39708367b
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800324"
---
# <a name="net-framework-performance"></a>.NET Framework – výkon
Pokud chcete vytvořit aplikace s vynikajícím výkonem, měli byste navrhnout a naplánovat výkon stejně jako byste navrhovali libovolnou jinou funkci aplikace. Můžete použít nástroje poskytované společností Microsoft k měření výkonu vaší aplikace a, v případě potřeby zdokonalení využití paměti, propustnosti kódování a doby odezvy. Toto téma uvádí analytické nástroje výkonu poskytované společností Microsoft a poskytuje odkazy na další témata, která pokrývají výkon pro konkrétní oblasti vývoje aplikací.  
  
## <a name="designing-and-planning-for-performance"></a>Návrh a plánování pro výkon  
 Pokud chcete aplikaci se skvělým výkonem, je třeba navrhnout výkon do vaší aplikace stejným způsobem, jako byste navrhli kteroukoli jinou funkci. Ve své aplikaci byste měli určit scénáře důležité pro výkon, stanovit cíle výkonu a včas a často měřit výkon těchto scénářů aplikace. Protože každá aplikace se liší a má různé cesty spuštění nutné pro výkon, včasné stanovení těchto cest a zaměření úsilí zvýší vaši produktivitu.  
  
 Nemusíte být zcela obeznámeni s cílovou platformou, abyste vytvořili vysoce výkonnou aplikaci. Nicméně byste měli vytvořit porozumění, které části cílové platformy jsou náročné na výkon. To lze provést pomocí změření výkonu v rané fázi vývojového procesu.  
  
 Při určování oblastí, které jsou nezbytné k výkonu a ke stanovení cílů výkonu, vždy zvažte uživatelské prostředí. Čas spuštění a reakce jsou dvě klíčové oblasti, které budou mít vliv na uživatele a jeho vnímání vaší aplikace. Pokud vaše aplikace používá velké množství paměti, může se zdát uživateli líná nebo ovlivnit jiné aplikace v systému, nebo v některých případech může selhat proces odeslání webů Windows Store nebo Windows Phone Store. Pokud zjistíte, které části kódu se spouští častěji, můžete se také ujistit, že tyto části kódu jsou dobře optimalizované.  
  
## <a name="analyzing-performance"></a>Analýza výkonu  
 Jako součást celkového plánu rozvoje nastavte body během vývoje, kde budete měřit výkon vaší aplikace a porovnávat výsledky s cíli, které jste dříve nastavili. Změřte aplikaci v prostředí a hardware, který očekáváte, že uživatelé budou používat. Analýzou výkonu vaší aplikace včas a často můžete změnit rozhodnutí o architektuře, jejichž oprava by byla nákladná a náročná dále v cyklu vývoje. V následujících částech naleznete nástroje pro sledování výkonu, které lze použít k analýze aplikací a diskutovat o trasování událostí, které tyto nástroje používají.  
  
### <a name="performance-tools"></a>Nástroje pro měření výkonu  
 Zde jsou některé nástroje pro sledování výkonu, které lze použít s aplikacemi rozhraní .NET Framework.  
  
|Nástroj|Popis|  
|----------|-----------------|  
|Analýza výkonu aplikace Visual Studio|Slouží k analýze využití procesoru aplikací rozhraní .NET Framework, které budou nasazeny do počítačů s operačním systémem Windows.<br /><br /> Tento nástroj je k dispozici v nabídce **ladění** v aplikaci Visual Studio po otevření projektu. Další informace najdete v tématu [prohlížeč výkonu](/visualstudio/profiling/performance-explorer). **Poznámka:**  Při Windows Phone cílení na Windows Phone použít analýzu aplikací (viz další řádek).|  
|Analýza aplikací pro Windows Phone|Slouží k analýze procesoru a paměti, přenosové rychlosti síťových dat, reakce aplikace a spotřeby baterie v aplikacích pro Windows Phone.<br /><br /> Tento nástroj je k dispozici v nabídce **ladění** pro projekt Windows Phone v sadě Visual Studio po instalaci [sady Windows Phone SDK](https://go.microsoft.com/fwlink/?LinkId=265773). Další informace najdete v tématu [profilace aplikace pro Windows Phone 8](https://docs.microsoft.com/previous-versions/windows/apps/jj215908(v=vs.105)).|  
|[PerfView](https://www.microsoft.com/download/details.aspx?id=28567)|Slouží k identifikaci problémů souvisejících s využitím procesoru a paměti. Tento nástroj používá událost trasování pro Windows (ETW) a rozhraní API pro profilování CLR k poskytnutí rozšířené paměti a procesoru vyšetřování, jakož i informace o uvolnění paměti a kompilace JIT. Další informace o tom, jak používat PerfView, najdete v kurzu a souborech s nápovědu, které jsou součástí aplikace, [výukových kurzů 9 pro video](https://channel9.msdn.com/Series/PerfView-Tutorial)a [blogových příspěvků](https://blogs.msdn.microsoft.com/vancem/tag/perfview/).<br /><br /> Problémy týkající se paměti najdete v tématu [použití PerfView pro vyšetřování paměti](https://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-9-NET-Memory-Investigation-Basics-of-GC-Heap-Snapshots).|  
|[Analyzátor výkonu systému Windows](https://www.microsoft.com/download/details.aspx?id=30652)|Slouží k určení celkového výkonu systému, jako je využití paměti a ukládání aplikace při spuštění více aplikací ve stejném počítači. Tento nástroj je k dispozici na webu Download Center jako součást sady Windows Assessment and Deployment Kit (ADK) pro systém Windows 8. Další informace najdete v tématu [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer).|  
  
### <a name="event-tracing-for-windows-etw"></a>Trasování událostí pro Windows (ETW)  
 Trasování událostí pro Windows je technika, která umožňuje získat diagnostické informace o spuštěném kódu a je zásadní pro mnoho nástrojů pro sledování výkonu, které byly zmíněny dříve. Trasování událostí pro Windows vytvářejí protokoly, když určité události jsou vyvolány aplikací rozhraní .NET Framework a systému Windows. S ETW můžete povolit a zakázat protokolování dynamicky, tak, aby bylo možné provádět podrobné sledování v provozním prostředí bez restartování aplikací. Rozhraní .NET Framework poskytuje podporu pro události ETW a ETW používá mnoho nástrojů pro vytváření profilů a řízení výkonu při generování dat výkonu. Tyto nástroje často povolují a zakazují události ETW, seznámení se s nimi je užitečné. Konkrétní události trasování událostí pro Windows můžete používat ke shromažďování informací o konkrétních součástech vaší aplikace. Další informace o podpoře ETW v .NET Framework najdete v tématu [události ETW v modulu CLR (Common Language Runtime)](etw-events-in-the-common-language-runtime.md) a v [událostech ETW v Task PARALLEL Library a PLINQ](etw-events-in-task-parallel-library-and-plinq.md).  
  
## <a name="performance-by-app-type"></a>Výkon podle typu aplikace  
 Každý typ rozhraní .NET Framework aplikace má vlastní doporučené postupy, důležité informace a nástroje pro hodnocení výkonu. Následující tabulka odkazuje na témata o výkonu pro konkrétní typy aplikací .NET Framework.  
  
|Typ aplikace|Viz .|  
|--------------|---------|  
|.NET Framework aplikací pro všechny platformy|[Kolekce paměti a výkon](../../standard/garbage-collection/performance.md)<br /><br /> [Tipy pro zvýšení výkonu](performance-tips.md)|  
|Aplikace pro Store Windows 8. x C++napsané C#v systémech, a Visual Basic|[Osvědčené postupy výkonu pro aplikace pro Windows C++Store C#využívající systémy, a Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/hh750313%28v=win.10%29)|  
|Windows Presentation Foundation (WPF)|[Sada Performance Suite WPF](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100))|  
|ASP.NET|[Přehled výkonu ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/cc668225(v=vs.100))|  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Ukládání do vyrovnávací paměti v aplikacích .NET Framework](caching-in-net-framework-applications.md)|Popisuje postupy pro ukládání dat do mezipaměti ke zlepšení výkonu aplikací.|  
|[Opožděná inicializace](lazy-initialization.md)|Popisuje, jak inicializovat objekty podle potřeby pro zvýšení výkon, zejména při spuštění aplikace.|  
|[Spolehlivost](reliability.md)|Obsahuje informace o předcházení asynchronním výjimkám v prostředí serveru.|  
|[Psaní velkých a pohotově reagujících aplikací .NET Framework](writing-large-responsive-apps.md)|Poskytuje tipy k výkonu shromážděné z přepisu kompilátorů C# a Visual Basic ve spravovaném kódu a obsahuje několik reálných příkladů C# z kompilátoru.|
