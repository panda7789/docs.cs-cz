---
title: Trasování a instrumentace aplikací
description: Trasování a instrumentace aplikací v .NET. Trasování umožňuje monitorovat spuštění aplikace, když je spuštěná. Instrumentace umožňuje měřit úroveň výkonu.
ms.date: 03/30/2017
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
ms.openlocfilehash: d5484129ac17ee20aafe305bea5599f85903dfa2
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803544"
---
# <a name="tracing-and-instrumenting-applications"></a>Trasování a instrumentace aplikací
Trasování je způsob, jak můžete monitorovat provádění aplikace, když je spuštěná. Můžete přidat trasování a ladění instrumentace do aplikace .NET Framework při jejím vývoji a můžete použít tuto instrumentaci při vývoji aplikace i po jejím nasazení. <xref:System.Diagnostics.Trace?displayProperty=nameWithType>Třídy, a můžete použít <xref:System.Diagnostics.Debug?displayProperty=nameWithType> <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> k zaznamenání informací o chybách a spouštění aplikací v protokolech, textových souborech nebo jiných zařízeních pro pozdější analýzu.  
  
 Pojem *instrumentace* odkazuje na schopnost sledovat nebo změřit úroveň výkonu produktu a diagnostikovat chyby. V programování to znamená schopnost aplikace začlenit:  
  
- **Trasování kódu** – příjem informativních zpráv o spuštění aplikace za běhu.  
  
- **Ladění** – sledování a opravy chyb programování v aplikaci, která je ve vývoji. Další informace naleznete v tématu [ladění](/visualstudio/debugger/debugger-feature-tour).  
  
- **Čítače výkonu** – součásti, které umožňují sledovat výkon aplikace. Další informace najdete v tématu [čítače výkonu](performance-counters.md).  
  
- **Protokoly událostí** – komponenty, které umožňují přijímat a sledovat hlavní události při provádění aplikace. Další informace naleznete v tématu <xref:System.Diagnostics.EventLog> Třída.  
  
 Při instrumentaci aplikace je vhodné umístit příkazy trasování do strategického umístění ve vašem kódu, zvláště užitečné pro distribuované aplikace. Pomocí příkazů Trace můžete instrumentovat aplikaci tak, aby zobrazovala pouze informace, když se něco nepovede, ale také monitorovat, jak dobře aplikace funguje.  
  
 <xref:System.Diagnostics.TraceSource>Třída poskytuje rozšířené funkce trasování a lze ji použít místo statických metod pro starší <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> trasovací třídy. Známé <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> třídy jsou stále široce používány, ale <xref:System.Diagnostics.TraceSource> Třída je doporučena pro nové příkazy trasování, například <xref:System.Diagnostics.TraceSource.TraceEvent%2A> a <xref:System.Diagnostics.TraceSource.TraceData%2A> .  
  
 <xref:System.Diagnostics.Trace>Třídy a <xref:System.Diagnostics.Debug> jsou identické, s tím rozdílem, že procedury a funkce <xref:System.Diagnostics.Trace> třídy jsou kompilovány ve výchozím nastavení do sestavení vydaných verzí, ale <xref:System.Diagnostics.Debug> třídy nejsou.  
  
 <xref:System.Diagnostics.Trace>Třídy a <xref:System.Diagnostics.Debug> poskytují prostředky pro monitorování a kontrolu výkonu aplikace buď během vývoje, nebo po nasazení. Můžete například použít <xref:System.Diagnostics.Trace> třídu ke sledování určitých typů akcí v nasazené aplikaci, jak se vyskytují (například vytváření nových připojení k databázi), a proto může monitorovat efektivitu aplikace.  
  
## <a name="code-tracing-and-debugging"></a>Trasování a ladění kódu  
 Během vývoje můžete použít výstupní metody <xref:System.Diagnostics.Debug> třídy pro zobrazení zpráv v okně výstup integrovaného vývojového prostředí (IDE) sady Visual Studio. Příklad:  
  
```vb  
Trace.WriteLine("Hello World!")  
Debug.WriteLine("Hello World!")  
```  
  
```csharp  
System.Diagnostics.Trace.WriteLine("Hello World!");  
System.Diagnostics.Debug.WriteLine("Hello World!");  
```  
  
 Každý z těchto příkladů zobrazí "Hello World!" v okně výstup, když je aplikace spuštěna v ladicím programu.  
  
 To vám umožní ladit aplikace a optimalizovat jejich výkon na základě jejich chování v testovacím prostředí. Můžete ladit aplikaci v sestavení ladění pomocí <xref:System.Diagnostics.Debug> podmíněného atributu, který je zapnutý, abyste zobrazili všechny výstupy ladění. Když je vaše aplikace připravená k vydání, můžete zkompilovat sestavení pro vydání, aniž byste museli zapnout <xref:System.Diagnostics.Debug> podmíněný atribut, takže kompilátor nebude zahrnovat váš kód pro ladění do finálního spustitelného souboru. Další informace najdete v tématu [Postupy: podmíněné kompilování pomocí trasování a ladění](how-to-compile-conditionally-with-trace-and-debug.md). Další informace o různých konfiguracích sestavení pro vaši aplikaci naleznete v tématu [kompilace a sestavování](/visualstudio/ide/compiling-and-building-in-visual-studio).  
  
 Můžete také trasovat spuštění kódu v nainstalované aplikaci pomocí metod <xref:System.Diagnostics.Trace> třídy. Vložením [přepínačů trasování](trace-switches.md) do kódu můžete určit, zda trasování probíhá a jak rozsáhlý je. To vám umožní monitorovat stav aplikace v produkčním prostředí. To je obzvláště důležité v obchodní aplikaci, která používá více komponent spuštěných na více počítačích. Můžete řídit, jak se přepínače používají po nasazení prostřednictvím konfiguračního souboru. Další informace najdete v tématu [Postupy: vytváření, inicializace a konfigurace přepínačů trasování](how-to-create-initialize-and-configure-trace-switches.md).  
  
 Při vývoji aplikace, pro kterou chcete použít trasování, obvykle je třeba do kódu aplikace zahrnout trasovací a ladicí zprávy. Až budete připraveni k nasazení aplikace, můžete zkompilovat sestavení pro vydání bez zapnutí podmíněného atributu **ladění** . Můžete však zapnout podmíněný atribut **Trace** tak, aby kompilátor zahrnoval váš kód trasování ve spustitelném souboru. Další informace najdete v tématu [Postupy: podmíněné kompilování pomocí trasování a ladění](how-to-compile-conditionally-with-trace-and-debug.md).  
  
### <a name="phases-of-code-tracing"></a>Fáze trasování kódu  
 Trasování kódu jsou tři fáze:  
  
1. **Instrumentace** – do své aplikace přidáte trasovací kód.  
  
2. **Trasování** – trasovací kód zapisuje informace do zadaného cíle.  
  
3. **Analýza** – vyhodnocujete trasovací informace k identifikaci a pochopení problémů v aplikaci.  
  
 Během vývoje všechny metody ladění a trasování výstupu zapisují informace do okna výstup v aplikaci Visual Studio ve výchozím nastavení. V nasazené aplikaci metody zapisují trasovací informace do cílů, které zadáte. Další informace o určení cíle výstupu pro trasování nebo ladění naleznete v tématu [Trace Listeners](trace-listeners.md).  
  
 Následuje celkový přehled hlavních kroků, které jsou obvykle zahrnuty v použití trasování k analýze a opravě potenciálních problémů v nasazených aplikacích. Další informace o tom, jak provést tyto kroky, najdete v příslušném odkazu.  
  
##### <a name="to-use-tracing-in-an-application"></a>Použití trasování v aplikaci  
  
1. Zvažte, který výstup trasování budete chtít po nasazení aplikace přijmout na pracovišti.  
  
2. Vytvořte sadu přepínačů. Další informace najdete v tématu [Postup: konfigurace přepínačů trasování](how-to-create-initialize-and-configure-trace-switches.md).  
  
3. Přidejte příkazy trasování do kódu aplikace.  
  
4. Určete, kde se má objevit výstup trasování, a přidejte příslušné naslouchací procesy. Další informace najdete v tématu [vytváření a inicializace posluchačů trasování](how-to-create-and-initialize-trace-listeners.md).  
  
5. Testování a ladění aplikace a trasovacího kódu, který obsahuje.  
  
6. Zkompilujte aplikaci do spustitelného kódu pomocí jednoho z následujících postupů:  
  
    - Použijte nabídku **sestavení** spolu se stránkou **ladění** dialogového okna **stránky vlastností** v **Průzkumník řešení**. Toto použijte při kompilaci v aplikaci Visual Studio.  
  
         \-ani  
  
    - Použijte direktivy **Trace** a **Debug** kompilátoru pro metodu kompilování příkazového řádku. Další informace naleznete v tématu [kompilování podmíněně s trasováním a laděním](how-to-compile-conditionally-with-trace-and-debug.md). Toto použijte při kompilaci z příkazového řádku.  
  
7. Pokud během běhu dojde k problému, zapněte příslušný přepínač trasování. Další informace najdete v tématu [konfigurace přepínačů trasování](how-to-create-initialize-and-configure-trace-switches.md).  
  
     Trasovací kód zapisuje trasovací zprávy do zadaného cíle, například obrazovky, textový soubor nebo protokol událostí. Typ naslouchacího procesu, který jste zahrnuli do <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> kolekce, určuje cíl.  
  
8. Analyzujte trasovací zprávy pro identifikaci a pochopení problému v aplikaci.  
  
## <a name="trace-instrumentation-and-distributed-applications"></a>Sledovací instrumentace a distribuované aplikace  
 Když vytvoříte distribuovanou aplikaci, může být obtížné otestovat aplikaci způsobem, ve kterém bude použita. Několik vývojových týmů má možnost testovat všechny možné kombinace operačních systémů nebo webových prohlížečů (včetně všech lokalizovaných jazykových nastavení) nebo simulovat velký počet uživatelů, kteří budou mít přístup k aplikaci ve stejnou dobu. Za těchto okolností nemůžete testovat, jak distribuovaná aplikace reaguje na vysoké objemy, různá nastavení a jedinečné chování koncového uživatele. Mnoho částí distribuované aplikace navíc nemá žádné uživatelské rozhraní, se kterým můžete pracovat přímo nebo zobrazit aktivity těchto částí.  
  
 Můžete to však kompenzovat povolením distribuovaných aplikací, které popisují určité události týkající se správců systému, zejména věcí, které jsou nepřesné, pomocí *instrumentace* aplikace – to znamená tak, že do strategického umístění ve svém kódu umístíte příkazy TRACE. Pokud pak dojde k neočekávanému selhání za běhu (například nadměrné zpomalení doby odezvy), můžete určit pravděpodobnou příčinu.  
  
 Pomocí příkazů Trace se můžete vyhnout obtížnému vyzkoušení původního zdrojového kódu, jeho úprav, opětovnému kompilování a pokusu o vystavení běhové chyby v prostředí ladění. Mějte na paměti, že můžete instrumentovat aplikaci, která není jenom zobrazovat chyby, ale také monitorovat výkon.  
  
## <a name="strategic-placement-of-trace-statements"></a>Strategické umístění příkazů trasování  
 Při umísťování příkazů trasování pro použití za běhu je nutné provést zvláštní péči. Je nutné zvážit, jaké informace o trasování budou pravděpodobně potřeba v nasazené aplikaci, aby všechny pravděpodobná scénáře trasování byly dostatečně pokryté. Vzhledem k tomu, že se aplikace, které používají trasování, značně liší, ale neexistují obecné pokyny pro strategické umístění trasování. Další informace o umístění příkazů trasování naleznete v tématu [How to: Add Trace Statements to Application Code](how-to-add-trace-statements-to-application-code.md).  
  
## <a name="output-from-tracing"></a>Výstup trasování  
 Výstup trasování se shromažďuje pomocí objektů zvaných *naslouchací procesy*. Naslouchací proces je objekt, který přijímá výstup trasování a zapisuje ho do výstupního zařízení (obvykle okno, protokol nebo textový soubor). Když je vytvořen naslouchací proces trasování, je obvykle přidán do <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> kolekce, což umožňuje, aby naslouchací proces přijímal veškerý výstup trasování.  
  
 Trasovací informace jsou vždy zapisovány alespoň do výchozího <xref:System.Diagnostics.Trace> cíle výstupu, a <xref:System.Diagnostics.DefaultTraceListener> . Pokud z nějakého důvodu jste odstranili <xref:System.Diagnostics.DefaultTraceListener> , aniž byste do kolekce přidali žádné jiné naslouchací procesy <xref:System.Diagnostics.Trace.Listeners%2A> , nebudete dostávat žádné zprávy trasování. Další informace naleznete v tématu [Trace Listeners](trace-listeners.md).  
  
 Šest <xref:System.Diagnostics.Debug> členů a <xref:System.Diagnostics.Trace> metod, které zapisují trasovací informace, jsou uvedeny v následující tabulce.  
  
|Metoda|Výstup|  
|------------|------------|  
|`Assert`|Zadaný text; nebo, pokud žádný není zadán, zásobník volání. Výstup je zapsán pouze v případě, že podmínka zadaná jako argument v `Assert` příkazu je **false**.|  
|`Fail`|Zadaný text; nebo, pokud žádný není zadán, zásobník volání.|  
|`Write`|Zadaný text.|  
|`WriteIf`|Zadaný text, pokud je splněna podmínka zadaná jako argument v `WriteIf` příkazu.|  
|`WriteLine`|Zadaný text a znak návratu na začátek řádku.|  
|`WriteLineIf`|Zadaný text a návrat na začátek řádku, pokud je splněna podmínka zadaná jako argument v `WriteLineIf` příkazu.|  
  
 Všechny naslouchací procesy v <xref:System.Diagnostics.Trace.Listeners%2A> kolekci obdrží zprávy popsané v tabulce výše, ale provedené akce se mohou lišit v závislosti na tom, jaký typ naslouchacího procesu obdrží zprávu. Například <xref:System.Diagnostics.DefaultTraceListener> dialogové okno pro zobrazení kontrolního výrazu se zobrazí, když obdrží `Fail` oznámení nebo se nezdařilo `Assert` , ale <xref:System.Diagnostics.TextWriterTraceListener> jednoduše zapíše výstup do jeho streamu.  
  
 Vlastní výsledky můžete vydávat implementací vlastního naslouchacího procesu. Vlastní naslouchací proces trasování může například zobrazit zprávy do okna se zprávou nebo připojit k databázi a přidat zprávy do tabulky. Všechny vlastní naslouchací procesy by měly podporovat šest metod uvedených výše. Další informace o vytváření posluchačů definovaných vývojářům naleznete <xref:System.Diagnostics.TraceListener> v tématu .NET Framework reference.  
  
 `Write`Metody a `WriteLine` vždy zapisují text, který zadáte. `Assert`, `WriteIf` a `WriteLineIf` vyžadují logický argument, který určuje, zda zápis zadaného textu nebo nikoli. zapisuje zadaný text pouze v případě, že má výraz **hodnotu true** (pro `WriteIf` a `WriteLineIf` ) nebo **false** (pro `Assert` ). `Fail`Metoda vždy zapisuje zadaný text. Další informace naleznete v tématu [Postupy: Přidání příkazů trasování do kódu aplikace](how-to-add-trace-statements-to-application-code.md) a odkazu na .NET Framework.  
  
## <a name="security-concerns"></a>Problematika zabezpečení  
 Pokud nezakážete trasování a ladění před nasazením aplikace ASP.NET, může vaše aplikace odhalit informace, které by mohly být zneužity škodlivým programem. Další informace najdete v tématu [Postupy: podmíněné kompilování s trasováním a laděním](how-to-compile-conditionally-with-trace-and-debug.md), [kompilováním a sestavování](/visualstudio/ide/compiling-and-building-in-visual-studio)a [Postupy: vytváření, inicializace a konfigurace přepínačů trasování](how-to-create-initialize-and-configure-trace-switches.md). Ladění je také možné konfigurovat prostřednictvím Internetová informační služba (IIS).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceSource>
- [Kontrakty kódu](code-contracts.md)
- [Typy projektů jazyka C#, F# a Visual Basic](/visualstudio/debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types)
- [Postupy: Přidání příkazů trasování do kódu aplikace](how-to-add-trace-statements-to-application-code.md)
- [Postupy: Podmíněná kompilace pomocí atributu Trace a Debug](how-to-compile-conditionally-with-trace-and-debug.md)
- [Postupy: Vytváření, inicializace a konfigurace přepínačů trasování](how-to-create-initialize-and-configure-trace-switches.md)
- [Postupy: Vytváření a inicializace zdrojů trasování](how-to-create-and-initialize-trace-sources.md)
- [Postupy: Použití třídy TraceSource a filtrů s naslouchacími procesy trasování](how-to-use-tracesource-and-filters-with-trace-listeners.md)
- [Moduly naslouchání trasování](trace-listeners.md)
- [Přepínače trasování](trace-switches.md)
