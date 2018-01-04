---
title: "Trasování a instrumentace aplikací"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tracing [.NET Framework]
- debugging [.NET Framework], instrumentation
- performance monitoring, instrumentation
- instrumentation, about instrumentation
- tracing [.NET Framework], about tracing
- performance monitoring, tracing code
- Trace class, instrumentation for .NET applications
ms.assetid: 773b6fc4-9013-4322-b728-5dec7a72e743
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 20eea5ed6f69c17466aeb33617f418ac71a3e1b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="tracing-and-instrumenting-applications"></a>Trasování a instrumentace aplikací
Trasování je způsob, jak můžete monitorovat aplikace, když je spuštěná. Trasování a ladění instrumentace můžete přidat do vaší aplikace rozhraní .NET Framework při jeho vývoji a že instrumentace můžete použít při vývoji aplikace i po jeho nasazení. Můžete použít <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug?displayProperty=nameWithType>, a <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> třídy k zaznamenání informací o chybách a spuštění aplikace v protokolech, textové soubory nebo jiné zařízení pro pozdější analýzu.  
  
 Termín *instrumentace* odkazuje na funkce pro monitorování a měření úroveň výkonu produktu a diagnostikovat chyby. Při programování, to znamená možnost aplikace, abyste zapracovali:  
  
-   **Trasování kódu** -přijetí informativní zprávy o spuštění aplikace v době běhu.  
  
-   **Ladění** – sledování a opravy chyb programování v aplikaci ve vývoji. Další informace najdete v tématu [ladění](/visualstudio/debugger/debugging-in-visual-studio).  
  
-   **Čítače výkonu** -součásti, které umožňují sledovat výkon aplikace. Další informace najdete v tématu [čítače výkonu](../../../docs/framework/debug-trace-profile/performance-counters.md).  
  
-   **Protokoly událostí** -součásti, které umožní přijímat a sledovat hlavní události při spuštění aplikace. Další informace najdete v tématu <xref:System.Diagnostics.EventLog> třídy.  
  
 Instrumentace umístěním trasovacích příkazů na strategická místa v kódu aplikace je užitečné zejména pro distribuované aplikace. Pomocí příkazů trasování můžete instrumentace aplikace jenom pro zobrazení informací v případě problémů, ale taky k monitorování, jak dobře fungují aplikace.  
  
 <xref:System.Diagnostics.TraceSource> Třída poskytuje pokročilé funkce, trasování a jde použít místo statických metod starší <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> třídy trasování. Známé <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> třídy jsou stále používají, ale <xref:System.Diagnostics.TraceSource> třídy se doporučuje pro nové příkazy trasování, například <xref:System.Diagnostics.TraceSource.TraceEvent%2A> a <xref:System.Diagnostics.TraceSource.TraceData%2A>.  
  
 <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> třídy jsou stejné, s výjimkou této procedury a funkce <xref:System.Diagnostics.Trace> třída kompilovány ve výchozím nastavení do sestavení pro vydání, ale těch, které <xref:System.Diagnostics.Debug> třídy nejsou.  
  
 <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> třídy poskytují způsob, jak sledovat a analýze výkonu aplikace během vývoje nebo po nasazení. Například můžete použít <xref:System.Diagnostics.Trace> třídy ke sledování konkrétní typy akcí v nasazení aplikace v jejich výskytu (například vytvoření nového připojení databáze) a proto můžete monitorovat aplikace efektivitu.  
  
## <a name="code-tracing-and-debugging"></a>Kód trasování a ladění  
 Během vývoje, můžete použít výstup metody <xref:System.Diagnostics.Debug> třída pro zobrazení zpráv v okně výstupu sady Visual Studio integrované vývojové prostředí (IDE). Příklad:  
  
```vb  
Trace.WriteLine("Hello World!")  
Debug.WriteLine("Hello World!")  
```  
  
```csharp  
System.Diagnostics.Trace.WriteLine("Hello World!");  
System.Diagnostics.Debug.WriteLine("Hello World!");  
```  
  
 Každý z těchto příkladech se zobrazí "Hello, World!" v okně výstupu, když je aplikace spuštěna v ladicím programu.  
  
 To umožňuje ladit aplikace a optimalizaci výkonu na základě jejich chování v testovacím prostředí. Můžete ladit aplikaci v buildu ladění pomocí <xref:System.Diagnostics.Debug> podmíněný atribut zapnutý, aby se zobrazí všechny ladění výstupu. Když je aplikace připravená pro vydání, můžete zkompilovat sestavení pro vydání bez zapnutí <xref:System.Diagnostics.Debug> podmíněného atributů tak, aby kompilátor nebude obsahovat ladění kódu v posledním spustitelný soubor. Další informace najdete v tématu [postupy: Podmíněná kompilace pomocí trasování a ladění](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md). Další informace o konfiguracích různých sestavení pro aplikaci najdete v tématu [kompilaci a sestavování](/visualstudio/ide/compiling-and-building-in-visual-studio).  
  
 Můžete také sledovat spuštění kódu v aplikaci nainstalované pomocí metody <xref:System.Diagnostics.Trace> třídy. Tím, že umístíte [trasování – přepínače](../../../docs/framework/debug-trace-profile/trace-switches.md) ve vašem kódu můžete ovládat, zda dojde k trasování a jak rozsáhlé je. To vám umožňuje monitorovat stav aplikace v provozním prostředí. To je obzvláště důležité v obchodní aplikace, která používá několik součástí běžící na více počítačích. Můžete řídit, jak se používají přepínače po nasazení prostřednictvím konfiguračního souboru. Další informace najdete v tématu [postupy: vytváření, inicializace a konfigurace přepínačů trasování](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
 Pokud vyvíjíte aplikaci, pro který chcete používat trasování, je obvykle zahrnout trasování a ladění zprávy v kódu aplikace. Jakmile budete připraveni k nasazení aplikace, můžete zkompilovat sestavení pro vydání bez zapnutí **ladění** podmíněný atribut. Však můžete zapnout **trasování** podmíněného atributů tak, že kompilátor obsahují kódu trasování ve spustitelném souboru. Další informace najdete v tématu [postupy: Podmíněná kompilace pomocí trasování a ladění](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md).  
  
### <a name="phases-of-code-tracing"></a>Fáze trasování kódu  
 Existují tři fáze kód trasování:  
  
1.  **Instrumentace** – přidání kódu trasování do aplikace.  
  
2.  **Trasování** – kód trasování do zadaného cíle zapisuje informace.  
  
3.  **Analýza** – vyhodnotit trasování informace k identifikaci a pochopit problémy v aplikaci.  
  
 Během vývoje všechny trasování a ladění výstupu metody zápisu informací do okna výstupu v sadě Visual Studio ve výchozím nastavení. V nasazení aplikace metody zapsat informace trasování do cíle, které zadáte. Další informace o zadání cíl výstupu trasování nebo ladění, najdete v části [trasování – moduly naslouchání](../../../docs/framework/debug-trace-profile/trace-listeners.md).  
  
 Toto je celkový přehled o hlavní kroky obvykle pomocí trasování k analýze a opravte potenciální problémy v nasazené aplikace. Další informace o tom, jak provést tyto kroky v tématu na příslušný odkaz.  
  
##### <a name="to-use-tracing-in-an-application"></a>Chcete-li použít trasování v aplikaci  
  
1.  Zvažte, které trasování výstup, že budete chtít přijímat dohlížející na bezpečný po nasazení aplikace.  
  
2.  Vytvořte sadu přepínače. Další informace najdete v tématu [postupy: Konfigurace trasování – přepínače](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
3.  Přidání příkazů trasování do kódu aplikace.  
  
4.  Určete, kam chcete zobrazit, a přidejte příslušné posluchače výstup trasování. Další informace najdete v tématu [vytváření a inicializace modulů naslouchání trasování](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md).  
  
5.  Testování a ladění aplikace a kód trasování, které obsahuje.  
  
6.  Kompilace aplikace do spustitelného kódu pomocí jedné z následujících postupů:  
  
    -   Použití **sestavení** nabídky spolu s **ladění** stránky **stránky vlastností** dialogovém okně **Průzkumníku řešení**. Používejte při kompilaci v sadě Visual Studio.  
  
         \-nebo –  
  
    -   Použití **trasování** a **ladění** direktivy kompilátoru příkazového řádku metody kompilace. Další informace najdete v tématu [Podmíněná kompilace pomocí trasování a ladění](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md). Používejte při kompilaci z příkazového řádku.  
  
7.  Pokud dojde k potížím při běhu, zapněte přepínač odpovídající trasování. Další informace najdete v tématu [Konfigurace trasování – přepínače](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
     Trasování kódu zapíše zprávy trasování do zadaného cíle, například na obrazovce, do textového souboru nebo protokolu událostí. Typ naslouchací proces je součástí **Trace.Listeners** kolekce Určuje cíl.  
  
8.  Analýza trasování zprávy k identifikaci a pochopit problém v aplikaci.  
  
## <a name="trace-instrumentation-and-distributed-applications"></a>Trasování instrumentace a distribuovaných aplikací  
 Při vytváření distribuované aplikace, může být obtížné testování aplikace způsobem, který se použije. Několik vývojové týmy mít možnost otestovat všechny možné kombinace operačních systémů nebo webových prohlížečů (včetně všech možností lokalizovaném jazyce) nebo k simulaci vysoký počet uživatelů, kteří budou přistupovat k aplikaci ve stejnou dobu. Za těchto okolností nelze testovat, jak bude odpovídat distribuované aplikace k velkému vytížení, jiné nastavení a chování jedinečný koncového uživatele. Mnoho částí distribuované aplikace také mít žádné uživatelské rozhraní pracovat přímo nebo zobrazit aktivitu z těchto částí.  
  
 Však můžete kompenzovat to povolením distribuované aplikace k popisu určité události důležité pro správce systému, zejména věcí, které dojít k chybě, ve *instrumentace* aplikace – tj pomocí umístění příkazy trasování na strategická místa v kódu. Poté neočekávané případě za běhu (například nadměrně dlouhá doba odezvy), můžete určit pravděpodobnou příčinou.  
  
 Pomocí příkazů trasování se můžete vyhnout snadné zkoumání původní zdrojový kód, provádění úprav, nutnosti rekompilace a pokus o vytvoření Chyba spuštění v prostředí ladění. Mějte na paměti, že můžete instrumentace aplikace nejen pro zobrazení chyb, ale také kvůli sledování výkonu.  
  
## <a name="strategic-placement-of-trace-statements"></a>Strategické umístění příkazy trasování  
 Zvláštní pozornost musí výkonu při umísťování vaše příkazy trasování pro použití při běhu. Musíte zvážit, jaké informace trasování bude pravděpodobně potřeba v nasazení aplikace, tak, aby všechny scénáře pravděpodobně trasování jsou adekvátní popsané. Vzhledem k tomu, že aplikace, které používají trasování lišit, často, ale neexistují žádné obecné pokyny pro strategické umístění trasování. Další informace o umístění trasovacích příkazů najdete v tématu [postupy: Přidání příkazů trasování do kódu aplikace](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md).  
  
## <a name="output-from-tracing"></a>Výstup trasování  
 Výstup trasování se shromažďují objekty názvem *naslouchací procesy*. Naslouchací proces je objekt, který přijímá výstup trasování a zapíše ho do zařízení se systémem výstup (obvykle soubor okno, protokolu nebo text). Když je vytvořen naslouchací proces trasování, je obvykle přidán do <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> kolekce, což naslouchací proces pro příjem všech výstup trasování.  
  
 Informace o trasování je vždy zapisovány alespoň na výchozí <xref:System.Diagnostics.Trace> cíl výstupu, <xref:System.Diagnostics.DefaultTraceListener>. Pokud z nějakého důvodu jste odstranili <xref:System.Diagnostics.DefaultTraceListener> bez přidání jakékoli naslouchací procesy na <xref:System.Diagnostics.Trace.Listeners%2A> kolekce, všechny zprávy trasování se nezobrazí. Další informace najdete v tématu [trasování – moduly naslouchání](../../../docs/framework/debug-trace-profile/trace-listeners.md).  
  
 Šesti <xref:System.Diagnostics.Debug> členy a <xref:System.Diagnostics.Trace> metody, které zapsat informace trasování jsou uvedeny v následující tabulce.  
  
|Metoda|Výstup|  
|------------|------------|  
|**Assert**|Zadaný text; nebo, pokud není zadaný žádný zásobníku volání. Výstup se zapíše pouze pokud podmínka zadaný jako argument **Assert** příkaz **false**.|  
|**Selhání**|Zadaný text; nebo, pokud není zadaný žádný zásobníku volání.|  
|**Zápis**|Zadaný text.|  
|**Writeif –**|Zadaný text, pokud podmínky zadané jako argument **writeif –** příkaz je splněné.|  
|**WriteLine**|Zadaný text a návrat.|  
|**Writelineif –**|Zadaný text a znak konce řádku vrátit, pokud podmínky zadané jako argument **writelineif –** příkaz je splněné.|  
  
 Všechny moduly pro naslouchání v <xref:System.Diagnostics.Trace.Listeners%2A> kolekce přijímat zprávy popsané v předchozí tabulce, ale akce prováděné se mohou lišit v závislosti na tom, jaký druh naslouchací proces obdrží zprávu. Například <xref:System.Diagnostics.DefaultTraceListener> zobrazí dialogové okno kontrolní výraz při přijetí **nezdaří** nebo se nezdařilo **Assert** oznámení, ale <xref:System.Diagnostics.TextWriterTraceListener> jednoduše výstup zapíše do jeho datového proudu.  
  
 Můžete vytvořit vlastní výsledky implementací vlastní naslouchací proces. Vlastní naslouchací může, například zobrazit okno se zprávou zprávy nebo připojení k databázi, chcete-li přidat zprávy do tabulky. Všechny vlastní naslouchací procesy by měly podporovat šesti metody uvedené výše. Další informace o vytváření definované vývojáře naslouchací procesy najdete v tématu <xref:System.Diagnostics.TraceListener> v referenci rozhraní .NET Framework.  
  
> [!NOTE]
>  V [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], **Debug.Write –**, **Debug.WriteIf**, **Debug.WriteLine**, a **Debug.WriteLineIf** nahradit metody **Debug.Print –** metoda, která byla k dispozici v dřívějších verzích jazyka Visual Basic.  
  
 **Zápisu** a **WriteLine** zápisu vždy metody text, zda jste zadali. **Assert –**, **writeif –**, a **writelineif –** vyžadují Boolean argument, který určuje, zda budou zapisovat zadaný text; zapíší zadaný text pouze pokud je výraz **true** (pro **writeif –** a **writelineif –**), nebo **false** (pro **Assert**). **Nezdaří** metoda vždy zapíše zadaný text. Další informace najdete v tématu [postupy: Přidání příkazů trasování do kódu aplikace](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md) a odkaz na rozhraní .NET Framework.  
  
## <a name="security-concerns"></a>Aspekty zabezpečení  
 Pokud nezakážete trasování a ladění před nasazením aplikace ASP.NET, vaše aplikace může odhalit informace o sobě, který může zneužít škodlivý program. Další informace najdete v tématu [postupy: Podmíněná kompilace pomocí trasování a ladění](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md), [kompilaci a sestavování](/visualstudio/ide/compiling-and-building-in-visual-studio), a [postupy: vytváření, inicializace a konfigurace přepínačů trasování](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md) . Ladění je také možné konfigurovat pomocí Internetové informační služby (IIS).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.TraceSource>  
 [Kontrakty kódu](../../../docs/framework/debug-trace-profile/code-contracts.md)  
 [C#, F # a typy projektů jazyka Visual Basic](/visualstudio/debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types)  
 [Postupy: Přidání příkazů trasování do kódu aplikace](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)  
 [Postupy: Podmíněná kompilace pomocí atributu Trace a Debug](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)  
 [Postupy: Vytváření, inicializace a konfigurace přepínačů trasování](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)  
 [Postupy: Vytváření a inicializace zdrojů trasování](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)  
 [Postupy: Použití třídy TraceSource a filtrů s naslouchacími procesy trasování](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md)  
 [Moduly naslouchání trasování](../../../docs/framework/debug-trace-profile/trace-listeners.md)  
 [Přepínače trasování](../../../docs/framework/debug-trace-profile/trace-switches.md)
