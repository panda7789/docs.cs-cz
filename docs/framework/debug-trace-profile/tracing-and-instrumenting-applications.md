---
title: Trasování a instrumentace aplikací
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9e1b8d5cb25445ffc3ce08e8c73e1d3742067e21
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73196718"
---
# <a name="tracing-and-instrumenting-applications"></a>Trasování a instrumentace aplikací
Trasování je způsob, jak můžete monitorovat provádění aplikace, když je spuštěná. Můžete přidat trasování a ladění instrumentace do aplikace .NET Framework při jejím vývoji a můžete použít tuto instrumentaci při vývoji aplikace i po jejím nasazení. Třídy <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug?displayProperty=nameWithType>a <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> můžete použít k zaznamenání informací o chybách a spouštění aplikací v protokolech, textových souborech nebo jiných zařízeních pro pozdější analýzu.  
  
 Pojem *instrumentace* odkazuje na schopnost sledovat nebo změřit úroveň výkonu produktu a diagnostikovat chyby. V programování to znamená schopnost aplikace začlenit:  
  
- **Trasování kódu** – příjem informativních zpráv o spuštění aplikace za běhu.  
  
- **Ladění** – sledování a opravy chyb programování v aplikaci, která je ve vývoji. Další informace naleznete v tématu [ladění](/visualstudio/debugger/debugger-feature-tour).  
  
- **Čítače výkonu** – součásti, které umožňují sledovat výkon aplikace. Další informace najdete v tématu [čítače výkonu](performance-counters.md).  
  
- **Protokoly událostí** – komponenty, které umožňují přijímat a sledovat hlavní události při provádění aplikace. Další informace naleznete v tématu Třída <xref:System.Diagnostics.EventLog>.  
  
 Při instrumentaci aplikace je vhodné umístit příkazy trasování do strategického umístění ve vašem kódu, zvláště užitečné pro distribuované aplikace. Pomocí příkazů Trace můžete instrumentovat aplikaci tak, aby zobrazovala pouze informace, když se něco nepovede, ale také monitorovat, jak dobře aplikace funguje.  
  
 Třída <xref:System.Diagnostics.TraceSource> poskytuje rozšířené funkce trasování a lze ji použít místo statických metod pro starší <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> trasovacích tříd. Známé <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> třídy jsou stále běžně používány, ale pro nové trasovací příkazy, jako jsou například <xref:System.Diagnostics.TraceSource.TraceEvent%2A> a <xref:System.Diagnostics.TraceSource.TraceData%2A>, se doporučuje třída <xref:System.Diagnostics.TraceSource>.  
  
 Třídy <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> jsou identické, s tím rozdílem, že postupy a funkce třídy <xref:System.Diagnostics.Trace> jsou kompilovány ve výchozím nastavení do sestavení vydaných verzí, ale třídy <xref:System.Diagnostics.Debug> nejsou.  
  
 Třídy <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> poskytují prostředky pro monitorování a kontrolu výkonu aplikace buď během vývoje, nebo po nasazení. Můžete například použít třídu <xref:System.Diagnostics.Trace> ke sledování určitých typů akcí v nasazené aplikaci, jak se vyskytují (například vytváření nových připojení k databázi), a proto může monitorovat efektivitu aplikace.  
  
## <a name="code-tracing-and-debugging"></a>Trasování a ladění kódu  
 Během vývoje můžete použít metody výstupu třídy <xref:System.Diagnostics.Debug> k zobrazení zpráv v okně výstup integrovaného vývojového prostředí (IDE) sady Visual Studio. Příklad:  
  
```vb  
Trace.WriteLine("Hello World!")  
Debug.WriteLine("Hello World!")  
```  
  
```csharp  
System.Diagnostics.Trace.WriteLine("Hello World!");  
System.Diagnostics.Debug.WriteLine("Hello World!");  
```  
  
 Každý z těchto příkladů zobrazí "Hello World!" v okně výstup, když je aplikace spuštěna v ladicím programu.  
  
 To vám umožní ladit aplikace a optimalizovat jejich výkon na základě jejich chování v testovacím prostředí. Můžete ladit aplikaci v sestavení ladění pomocí atributu <xref:System.Diagnostics.Debug> podmíněný atribut zapnuto, abyste zobrazili všechny výstupy ladění. Když je vaše aplikace připravená k vydání, můžete zkompilovat sestavení pro vydání bez zapnutí <xref:System.Diagnostics.Debug> podmíněného atributu, takže kompilátor nebude zahrnovat váš kód pro ladění do finálního spustitelného souboru. Další informace najdete v tématu [jak: Podmíněně Zkompilujte pomocí](how-to-compile-conditionally-with-trace-and-debug.md)trasování a ladění. Další informace o různých konfiguracích sestavení pro vaši aplikaci naleznete v tématu [kompilace a sestavování](/visualstudio/ide/compiling-and-building-in-visual-studio).  
  
 Můžete také trasovat spuštění kódu v nainstalované aplikaci pomocí metod <xref:System.Diagnostics.Trace> třídy. Vložením [přepínačů trasování](trace-switches.md) do kódu můžete určit, zda trasování probíhá a jak rozsáhlý je. To vám umožní monitorovat stav aplikace v produkčním prostředí. To je obzvláště důležité v obchodní aplikaci, která používá více komponent spuštěných na více počítačích. Můžete řídit, jak se přepínače používají po nasazení prostřednictvím konfiguračního souboru. Další informace najdete v tématu [jak: Vytvoření, inicializace a konfigurace přepínačů trasování](how-to-create-initialize-and-configure-trace-switches.md).  
  
 Při vývoji aplikace, pro kterou chcete použít trasování, obvykle je třeba do kódu aplikace zahrnout trasovací a ladicí zprávy. Až budete připraveni k nasazení aplikace, můžete zkompilovat sestavení pro vydání bez zapnutí podmíněného atributu **ladění** . Můžete však zapnout podmíněný atribut **Trace** tak, aby kompilátor zahrnoval váš kód trasování ve spustitelném souboru. Další informace najdete v tématu [jak: Podmíněně Zkompilujte pomocí](how-to-compile-conditionally-with-trace-and-debug.md)trasování a ladění.  
  
### <a name="phases-of-code-tracing"></a>Fáze trasování kódu  
 Trasování kódu jsou tři fáze:  
  
1. **Instrumentace** – do své aplikace přidáte trasovací kód.  
  
2. **Trasování** – trasovací kód zapisuje informace do zadaného cíle.  
  
3. **Analýza** – vyhodnocujete trasovací informace k identifikaci a pochopení problémů v aplikaci.  
  
 Během vývoje všechny metody ladění a trasování výstupu zapisují informace do okna výstup v aplikaci Visual Studio ve výchozím nastavení. V nasazené aplikaci metody zapisují trasovací informace do cílů, které zadáte. Další informace o určení cíle výstupu pro trasování nebo ladění naleznete v tématu [Trace Listeners](trace-listeners.md).  
  
 Následuje celkový přehled hlavních kroků, které jsou obvykle zahrnuty v použití trasování k analýze a opravě potenciálních problémů v nasazených aplikacích. Další informace o tom, jak provést tyto kroky, najdete v příslušném odkazu.  
  
##### <a name="to-use-tracing-in-an-application"></a>Použití trasování v aplikaci  
  
1. Zvažte, který výstup trasování budete chtít po nasazení aplikace přijmout na pracovišti.  
  
2. Vytvořte sadu přepínačů. Další informace najdete v tématu [jak: Konfigurace přepínačů trasování](how-to-create-initialize-and-configure-trace-switches.md).  
  
3. Přidejte příkazy trasování do kódu aplikace.  
  
4. Určete, kde se má objevit výstup trasování, a přidejte příslušné naslouchací procesy. Další informace najdete v tématu [vytváření a inicializace posluchačů trasování](how-to-create-and-initialize-trace-listeners.md).  
  
5. Testování a ladění aplikace a trasovacího kódu, který obsahuje.  
  
6. Zkompilujte aplikaci do spustitelného kódu pomocí jednoho z následujících postupů:  
  
    - Použijte nabídku **sestavení** spolu se stránkou **ladění** dialogového okna **stránky vlastností** v **Průzkumník řešení**. Toto použijte při kompilaci v aplikaci Visual Studio.  
  
         \- nebo –  
  
    - Použijte direktivy **Trace** a **Debug** kompilátoru pro metodu kompilování příkazového řádku. Další informace naleznete v tématu [kompilování podmíněně s trasováním a laděním](how-to-compile-conditionally-with-trace-and-debug.md). Toto použijte při kompilaci z příkazového řádku.  
  
7. Pokud během běhu dojde k problému, zapněte příslušný přepínač trasování. Další informace najdete v tématu [konfigurace přepínačů trasování](how-to-create-initialize-and-configure-trace-switches.md).  
  
     Trasovací kód zapisuje trasovací zprávy do zadaného cíle, například obrazovky, textový soubor nebo protokol událostí. Typ naslouchacího procesu, který jste zahrnuli do kolekce **Trace. Listeners** , určuje cíl.  
  
8. Analyzujte trasovací zprávy pro identifikaci a pochopení problému v aplikaci.  
  
## <a name="trace-instrumentation-and-distributed-applications"></a>Sledovací instrumentace a distribuované aplikace  
 Když vytvoříte distribuovanou aplikaci, může být obtížné otestovat aplikaci způsobem, ve kterém bude použita. Několik vývojových týmů má možnost testovat všechny možné kombinace operačních systémů nebo webových prohlížečů (včetně všech lokalizovaných jazykových nastavení) nebo simulovat velký počet uživatelů, kteří budou mít přístup k aplikaci ve stejnou dobu. Za těchto okolností nemůžete testovat, jak distribuovaná aplikace reaguje na vysoké objemy, různá nastavení a jedinečné chování koncového uživatele. Mnoho částí distribuované aplikace navíc nemá žádné uživatelské rozhraní, se kterým můžete pracovat přímo nebo zobrazit aktivity těchto částí.  
  
 Můžete to však kompenzovat povolením distribuovaných aplikací, které popisují určité události týkající se správců systému, zejména věcí, které jsou nepřesné, pomocí *instrumentace* aplikace – to znamená tak, že do strategického umístění ve svém kódu umístíte příkazy TRACE. Pokud pak dojde k neočekávanému selhání za běhu (například nadměrné zpomalení doby odezvy), můžete určit pravděpodobnou příčinu.  
  
 Pomocí příkazů Trace se můžete vyhnout obtížnému vyzkoušení původního zdrojového kódu, jeho úprav, opětovnému kompilování a pokusu o vystavení běhové chyby v prostředí ladění. Mějte na paměti, že můžete instrumentovat aplikaci, která není jenom zobrazovat chyby, ale také monitorovat výkon.  
  
## <a name="strategic-placement-of-trace-statements"></a>Strategické umístění příkazů trasování  
 Při umísťování příkazů trasování pro použití za běhu je nutné provést zvláštní péči. Je nutné zvážit, jaké informace o trasování budou pravděpodobně potřeba v nasazené aplikaci, aby všechny pravděpodobná scénáře trasování byly dostatečně pokryté. Vzhledem k tomu, že se aplikace, které používají trasování, značně liší, ale neexistují obecné pokyny pro strategické umístění trasování. Další informace o umístění příkazů trasování naleznete v tématu [How to: Přidejte příkazy trasování do kódu aplikace](how-to-add-trace-statements-to-application-code.md).  
  
## <a name="output-from-tracing"></a>Výstup trasování  
 Výstup trasování se shromažďuje pomocí objektů zvaných *naslouchací procesy*. Naslouchací proces je objekt, který přijímá výstup trasování a zapisuje ho do výstupního zařízení (obvykle okno, protokol nebo textový soubor). Když je vytvořen naslouchací proces trasování, je obvykle přidán do kolekce <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType>, což umožňuje, aby naslouchací proces přijímal veškerý výstup trasování.  
  
 Trasovací informace jsou vždy zapisovány alespoň do výchozího cíle <xref:System.Diagnostics.Trace>ho výstupu, <xref:System.Diagnostics.DefaultTraceListener>. Pokud z nějakého důvodu odstraníte <xref:System.Diagnostics.DefaultTraceListener>, aniž byste do kolekce <xref:System.Diagnostics.Trace.Listeners%2A> přidali žádné jiné naslouchací procesy, nebudete dostávat žádné zprávy trasování. Další informace naleznete v tématu [Trace Listeners](trace-listeners.md).  
  
 Šest <xref:System.Diagnostics.Debug> členů a <xref:System.Diagnostics.Trace> metody, které zapisují trasovací informace, jsou uvedeny v následující tabulce.  
  
|Metoda|Výstup|  
|------------|------------|  
|**Uplatňuje**|Zadaný text; nebo, pokud žádný není zadán, zásobník volání. Výstup je zapsán pouze v případě, že podmínka zadaná jako argument v příkazu **Assert** je **false**.|  
|**Proběhne**|Zadaný text; nebo, pokud žádný není zadán, zásobník volání.|  
|**Psal**|Zadaný text.|  
|**WriteIf**|Zadaný text, pokud je splněna podmínka zadaná jako argument v příkazu **WriteIf** .|  
|**WriteLine**|Zadaný text a znak návratu na začátek řádku.|  
|**WriteLineIf**|Zadaný text a návrat na začátek řádku, pokud je splněna podmínka zadaná jako argument v příkazu **WriteLineIf** .|  
  
 Všechny naslouchací procesy v kolekci <xref:System.Diagnostics.Trace.Listeners%2A> obdrží zprávy popsané v tabulce výše, ale provedené akce se mohou lišit v závislosti na tom, jaký typ naslouchacího procesu zprávu obdrží. Například <xref:System.Diagnostics.DefaultTraceListener> zobrazí dialogové okno kontrolní výraz při přijetí oznámení o **chybě** nebo neúspěšném **vyhodnocení kontrolního** výrazu, ale <xref:System.Diagnostics.TextWriterTraceListener> jednoduše zapíše výstup do svého proudu.  
  
 Vlastní výsledky můžete vydávat implementací vlastního naslouchacího procesu. Vlastní naslouchací proces trasování může například zobrazit zprávy do okna se zprávou nebo připojit k databázi a přidat zprávy do tabulky. Všechny vlastní naslouchací procesy by měly podporovat šest metod uvedených výše. Další informace o vytváření posluchačů definovaných vývojářům naleznete v tématu <xref:System.Diagnostics.TraceListener> v referenční příručce .NET Framework.  
  
 Metody **Write** a **WriteLine** vždy zapisují zadaný text. **Assert**, **WriteIf**a **WriteLineIf** vyžadují logický argument, který určuje, zda zapisují zadaný text, nebo ne. zapisují zadaný text pouze v případě, že má výraz **hodnotu true** (pro **WriteIf** a **WriteLineIf**) nebo **false** (pro **Assert**). Metoda **neúspěšného** zápisu vždy zapisuje zadaný text. Další informace najdete v tématu [jak: Přidejte příkazy trasování do kódu aplikace](how-to-add-trace-statements-to-application-code.md) a odkaz na .NET Framework.  
  
## <a name="security-concerns"></a>Problematika zabezpečení  
 Pokud nezakážete trasování a ladění před nasazením aplikace ASP.NET, může vaše aplikace odhalit informace, které by mohly být zneužity škodlivým programem. Další informace najdete v tématu [jak: Podmíněně Zkompilujte pomocí trasování a ladění](how-to-compile-conditionally-with-trace-and-debug.md), [kompilování a sestavování](/visualstudio/ide/compiling-and-building-in-visual-studio)a [postupy: Vytvoření, inicializace a konfigurace přepínačů trasování](how-to-create-initialize-and-configure-trace-switches.md). Ladění je také možné konfigurovat prostřednictvím Internetová informační služba (IIS).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceSource>
- [Kontrakty kódu](code-contracts.md)
- [Typy projektů jazyka C#, F# a Visual Basic](/visualstudio/debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types)
- [Postupy: Přidání příkazů trasování do kódu aplikace](how-to-add-trace-statements-to-application-code.md)
- [Postupy: Podmíněně kompilovat pomocí](how-to-compile-conditionally-with-trace-and-debug.md) trasování a ladění
- [Postupy: Vytvoření, inicializace a konfigurace přepínačů trasování](how-to-create-initialize-and-configure-trace-switches.md)
- [Postupy: Vytvoření a inicializace zdrojů trasování](how-to-create-and-initialize-trace-sources.md)
- [Postupy: Použití TraceSource a filtrů s naslouchacími procesy trasování](how-to-use-tracesource-and-filters-with-trace-listeners.md)
- [Moduly naslouchání trasování](trace-listeners.md)
- [Přepínače trasování](trace-switches.md)
