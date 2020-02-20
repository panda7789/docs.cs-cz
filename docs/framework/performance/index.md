---
title: .NET Framework – výkon
ms.date: 03/30/2017
helpviewer_keywords:
- performance [.NET Framework]
- reliability [.NET Framework]
ms.assetid: c1676cca-3f1a-41ec-b469-9029566074fc
ms.openlocfilehash: 47d85ae63f0594b778523425631ff54f9f3ca32f
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77504087"
---
# <a name="net-framework-performance"></a>.NET Framework – výkon
Pokud chcete vytvářet aplikace s skvělým výkonem, měli byste navrhovat a plánovat výkon stejně, jako byste navrhli jakoukoli jinou funkci aplikace. Pomocí nástrojů poskytovaných společností Microsoft můžete měřit výkon vaší aplikace a v případě potřeby provádět vylepšení využití paměti, propustnosti kódu a odezvy. Toto téma obsahuje seznam nástrojů pro analýzu výkonu, které poskytuje společnost Microsoft, a obsahuje odkazy na další témata, která se týkají výkonu pro konkrétní oblasti vývoje aplikací.  
  
## <a name="designing-and-planning-for-performance"></a>Návrh a plánování výkonu  
 Pokud chcete skvělou aplikaci, musíte navrhnout výkon vaší aplikace stejně, jako byste navrhli jakoukoli jinou funkci. Měli byste určit scénáře kritické pro výkon ve vaší aplikaci, nastavit cíle výkonu a měřit výkon těchto scénářů aplikací v předstihu a často. Vzhledem k tomu, že každá aplikace je odlišná a má různé cesty spuštění kritické pro výkon, je třeba tyto cesty včas určit a soustředit se na vaše úsilí, abyste mohli maximalizovat svou produktivitu.  
  
 Abyste mohli vytvořit vysoce výkonné aplikace, nemusíte zcela znát cílovou platformu. Měli byste ale vyvíjet informace o tom, které části vaší cílové platformy jsou nákladné z pohledu výkonu. To můžete udělat tak, že včas vyměříte výkon v procesu vývoje.  
  
 Chcete-li určit oblasti, které jsou zásadní pro výkon a stanovit své cíle výkonu, vždy Vezměte v úvahu činnost koncového uživatele. Čas spuštění a odezva jsou dvě klíčové oblasti, které budou mít vliv na vnímání vaší aplikace uživatelem. Pokud vaše aplikace používá hodně paměti, může se zobrazit pomalá uživateli nebo ovlivnit jiné aplikace spuštěné v systému, nebo může v některých případech dojít k selhání procesu odeslání Windows Storu nebo Windows Phone Storu. Také Pokud určíte, které části kódu budou spouštěny častěji, můžete zajistit, aby byly tyto části kódu dobře optimalizované.  
  
## <a name="analyzing-performance"></a>Analýza výkonu  
 V rámci celkového plánu vývoje nastavte během vývoje body, ve kterých budete měřit výkon aplikace a porovnejte výsledky s cíli, které jste nastavili dříve. Změřte aplikaci v prostředí a hardwaru, které očekáváte od uživatelů. Díky analýze výkonu aplikace v brzkém a často můžete měnit rozhodování o architektuře, která by byla finančně náročná a finančně opravena později v rámci vývojového cyklu. Následující části popisují nástroje pro sledování výkonu, které můžete použít k analýze aplikací a diskuzi o trasování událostí, které tyto nástroje používají.  
  
### <a name="performance-tools"></a>Nástroje pro měření výkonu  
 Zde jsou některé nástroje pro sledování výkonu, které můžete použít spolu s aplikacemi .NET Framework.  
  
|Nástroj|Popis|  
|----------|-----------------|  
|Analýza výkonu sady Visual Studio|Slouží k analýze využití CPU vašich .NET Framework aplikací, které budou nasazeny na počítačích s operačním systémem Windows.<br /><br /> Tento nástroj je k dispozici v nabídce **ladění** v aplikaci Visual Studio po otevření projektu. Další informace najdete v tématu [prohlížeč výkonu](/visualstudio/profiling/performance-explorer). **Poznámka:**  Při Windows Phone cílení na Windows Phone použít analýzu aplikací (viz další řádek).|  
|Windows Phone analýza aplikace|Pomocí nástroje můžete analyzovat kapacitu procesoru a paměti, rychlost přenosu dat v síti, rychlost odezvy aplikace a spotřebu energie ve vašich aplikacích Windows Phone.<br /><br /> Tento nástroj je k dispozici v nabídce **ladění** pro projekt Windows Phone v sadě Visual Studio po instalaci [sady Windows Phone SDK](https://go.microsoft.com/fwlink/?LinkId=265773). Další informace najdete v tématu [profilace aplikace pro Windows Phone 8](https://docs.microsoft.com/previous-versions/windows/apps/jj215908(v=vs.105)).|  
|[PerfView](https://www.microsoft.com/download/details.aspx?id=28567)|Slouží k identifikaci potíží s výkonem souvisejících s PROCESORem a pamětí. Tento nástroj používá trasování událostí pro Windows (ETW) a rozhraní API pro profilaci CLR k zajištění pokročilé paměti a vyšetřování procesoru a také informace o uvolňování paměti a kompilaci JIT. Další informace o tom, jak používat PerfView, najdete v kurzu a souborech s nápovědu, které jsou součástí aplikace, [výukových kurzů 9 pro video](https://channel9.msdn.com/Series/PerfView-Tutorial)a [blogových příspěvků](https://docs.microsoft.com/archive/blogs/vancem/).<br /><br /> Problémy týkající se paměti najdete v tématu [použití PerfView pro vyšetřování paměti](https://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-9-NET-Memory-Investigation-Basics-of-GC-Heap-Snapshots).|  
|[Analyzátor výkonu systému Windows](https://www.microsoft.com/download/details.aspx?id=30652)|Slouží k určení celkového výkonu systému, jako je například paměť a úložiště vaší aplikace, když je na jednom počítači spuštěno více aplikací. Tento nástroj je k dispozici na webu Download Center jako součást sady Windows Assessment and Deployment Kit (ADK) pro systém Windows 8. Další informace najdete v tématu [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer).|
  
### <a name="event-tracing-for-windows-etw"></a>Trasování událostí pro Windows (ETW)  
 ETW je technika, která umožňuje získat diagnostické informace o spuštění kódu a je zásadní pro spoustu výše zmíněných nástrojů pro sledování výkonu. ETW vytváří protokoly, když .NET Framework aplikace a Windows vyvolá konkrétní události. Pomocí trasování událostí pro Windows můžete povolit a zakázat protokolování dynamicky, aby bylo možné v produkčním prostředí provádět podrobné trasování bez nutnosti restartovat aplikaci. .NET Framework nabízí podporu pro události ETW a trasování událostí pro Windows používá mnoho nástrojů pro profilaci a výkon, které generuje data o výkonu. Tyto nástroje často povolují a zakazují události ETW, které jsou proto užitečné. Konkrétní události trasování událostí pro Windows můžete použít ke shromažďování informací o výkonu konkrétních komponent aplikace. Další informace o podpoře ETW v .NET Framework najdete v tématu [události ETW v modulu CLR (Common Language Runtime)](etw-events-in-the-common-language-runtime.md) a v [událostech ETW v Task PARALLEL Library a PLINQ](etw-events-in-task-parallel-library-and-plinq.md).  
  
## <a name="performance-by-app-type"></a>Výkon podle typu aplikace  
 Každý typ aplikace .NET Framework má své osvědčené postupy, požadavky a nástroje pro vyhodnocení výkonu. Následující tabulka obsahuje odkazy na témata týkající se výkonu pro konkrétní .NET Framework typy aplikací.  
  
|Typ aplikace|Přečtěte si:|  
|--------------|---------|  
|.NET Framework aplikací pro všechny platformy|[Kolekce paměti a výkon](../../standard/garbage-collection/performance.md)<br /><br /> [Tipy pro zvýšení výkonu](performance-tips.md)|  
|Aplikace pro Store Windows 8. x C++napsané C#v systémech, a Visual Basic|[Osvědčené postupy výkonu pro aplikace pro Windows C++Store C#využívající systémy, a Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/hh750313%28v=win.10%29)|  
|Windows Presentation Foundation (WPF)|[Sada Performance Suite WPF](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100))|  
|ASP.NET|[Přehled výkonu ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/cc668225(v=vs.100))|  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Ukládání do vyrovnávací paměti v aplikacích .NET Framework](caching-in-net-framework-applications.md)|Popisuje techniky ukládání dat do mezipaměti pro zlepšení výkonu aplikace.|  
|[Opožděná inicializace](lazy-initialization.md)|Popisuje, jak inicializovat objekty podle potřeby pro zlepšení výkonu, zejména při spuštění aplikace.|  
|[Spolehlivost](reliability.md)|Poskytuje informace o předcházení asynchronním výjimkám v prostředí serveru.|  
|[Psaní velkých a pohotově reagujících aplikací .NET Framework](writing-large-responsive-apps.md)|Poskytuje tipy k výkonu shromážděné z přepisu kompilátorů C# a Visual Basic ve spravovaném kódu a obsahuje několik reálných příkladů C# z kompilátoru.|
