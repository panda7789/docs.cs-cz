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
ms.openlocfilehash: ad2c41cc99422217b9f85acbd32f91ac78a9a7c2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614231"
---
# <a name="tracing-and-instrumenting-applications"></a>Trasování a instrumentace aplikací
Trasování je způsob, jak můžete monitorovat provádění aplikace během jejího běhu. Instrumentace trasování a ladění můžete přidat do vaší aplikace rozhraní .NET Framework při při vývoji a instrumentaci můžete použít při vývoji aplikace i po jeho nasazení. Můžete použít <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug?displayProperty=nameWithType>, a <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> třídy k zaznamenání informací o chybách a spuštění aplikace v protokolech, textové soubory nebo jiná pro pozdější analýzu.  
  
 Termín *instrumentace* odkazuje na schopnost, monitorovat nebo úroveň výkonu produktu měření a diagnostikovat chyby. Při programování, to znamená možnost aplikace začlenit:  
  
- **Trasování kódu** -příjem informativní zprávy o spuštění aplikace v době běhu.  
  
- **Ladění** – sledováním a oprava programovacích chyb v aplikaci ve vývoji. Další informace najdete v tématu [ladění](/visualstudio/debugger/debugging-in-visual-studio).  
  
- **Čítače výkonu** – komponenty, které umožňují sledovat výkon aplikace. Další informace najdete v tématu [čítače výkonu](../../../docs/framework/debug-trace-profile/performance-counters.md).  
  
- **Protokoly událostí** – komponenty, které vám umožní získáte a můžete sledovat důležité události v provádění aplikace. Další informace najdete v tématu <xref:System.Diagnostics.EventLog> třídy.  
  
 Instrumentace vaší aplikace tak, že příkazy trasování na strategická místa v kódu je užitečné zejména pro distribuované aplikace. Pomocí příkazů trasování vám umožňuje instrumentovat aplikaci pouze pro zobrazení informací, když něco selže, ale také k monitorování, jak dobře fungují aplikace.  
  
 <xref:System.Diagnostics.TraceSource> Třída poskytuje vylepšené funkce trasování a dá se použít místo statické metody starší <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> třídy trasování. Známé <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> třídy jsou stále používá, ale <xref:System.Diagnostics.TraceSource> třídu se doporučuje pro nové příkazy trasování, například <xref:System.Diagnostics.TraceSource.TraceEvent%2A> a <xref:System.Diagnostics.TraceSource.TraceData%2A>.  
  
 <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> třídy jsou identické, s výjimkou této procedury a funkce <xref:System.Diagnostics.Trace> třídy jsou kompilovány ve výchozím nastavení do sestavení pro vydání, ale u <xref:System.Diagnostics.Debug> třídy nejsou.  
  
 <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> třídy poskytují způsob, jak monitorovat a zjištění výkonu aplikace při vývoji nebo po nasazení. Například můžete použít <xref:System.Diagnostics.Trace> třídy můžete sledovat konkrétní typy akcí v nasazené aplikaci tak, jak dojde k (třeba vytvoření nového připojení k databázi) a proto můžete sledovat efektivitu vaší aplikace.  
  
## <a name="code-tracing-and-debugging"></a>Ladění a trasování kódu  
 Během vývoje, můžete použít metod výstupu <xref:System.Diagnostics.Debug> třídy mají zobrazovat zprávy v okně výstupu sady Visual Studio integrované vývojové prostředí (IDE). Příklad:  
  
```vb  
Trace.WriteLine("Hello World!")  
Debug.WriteLine("Hello World!")  
```  
  
```csharp  
System.Diagnostics.Trace.WriteLine("Hello World!");  
System.Diagnostics.Debug.WriteLine("Hello World!");  
```  
  
 Každá z těchto příkladech se zobrazí "Hello World!" v okně výstup při spuštění aplikace v ladicím programu.  
  
 To umožňuje ladit aplikace a optimalizaci výkonu na základě jejich chování ve vašem testovacím prostředí. Můžete ladit svoji aplikaci v sestavení ladění s <xref:System.Diagnostics.Debug> atribut conditional zapnuté, abyste dostávali veškerý výstup ladění. Pokud vaše aplikace je připraven k vydání, můžete vaše sestavení pro vydání kompilovat bez zapnete <xref:System.Diagnostics.Debug> podmíněný atribut, tak, aby kompilátor nebude zahrnut do konečného spustitelného souboru ladění kódu. Další informace najdete v tématu [jak: Podmíněná kompilace pomocí trasování a ladění](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md). Další informace o různé konfigurace sestavení pro vaši aplikaci najdete v tématu [kompilování a sestavování](/visualstudio/ide/compiling-and-building-in-visual-studio).  
  
 Můžete také sledovat spuštění kódu v nainstalovaná aplikace, pomocí metody <xref:System.Diagnostics.Trace> třídy. Tím, že umístíte [přepínačů trasování](../../../docs/framework/debug-trace-profile/trace-switches.md) ve vašem kódu, můžete řídit, jestli dojde k trasování a jak rozsáhlé je. To vám umožňuje monitorovat stav vaší aplikace v produkčním prostředí. To je obzvláště důležité v obchodních aplikací, které používá více součástí, které běží na několika počítačích. Můžete řídit, jak se používají přepínače po nasazení prostřednictvím konfiguračního souboru. Další informace najdete v tématu [jak: Vytváření, inicializace a konfigurace přepínačů trasování](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
 Když vyvíjíte aplikaci, pro který máte v úmyslu použít trasování, je obvykle zahrnout trasování a ladění zprávy v kódu aplikace. Jakmile budete připraveni k nasazení aplikace, můžete vaše sestavení pro vydání kompilovat bez zapnete **ladění** atribut conditional. Ale můžete zapnout **trasování** podmíněný atribut tak, aby kompilátor obsahuje trasování kódu ve spustitelném souboru. Další informace najdete v tématu [jak: Podmíněná kompilace pomocí trasování a ladění](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md).  
  
### <a name="phases-of-code-tracing"></a>Fáze trasování kódu  
 Existují tři fáze kód trasování:  
  
1. **Instrumentace** – přidání kódu trasování pro aplikaci.  
  
2. **Trasování** – trasování kódu zapisuje informace do zadaného cíle.  
  
3. **Analýza** – vyhodnocení trasovací informace k identifikaci a informace o problémech v aplikaci.  
  
 Během vývoje výstup všech ladění a trasování, že metody zapsat informace do okna výstup v sadě Visual Studio ve výchozím nastavení. V nasazené aplikaci metody zapsat informace trasování do cíle, které zadáte. Další informace o zadání cíl výstupu pro trasování a ladění, naleznete v tématu [naslouchacích procesů trasování](../../../docs/framework/debug-trace-profile/trace-listeners.md).  
  
 Následuje celkový přehled hlavních kroků, které jsou obvykle součástí pomocí trasování k analýze a opravte potenciální problémy v nasazené aplikace. Další informace o tom, jak tyto kroky provést najdete v článku na příslušný odkaz.  
  
##### <a name="to-use-tracing-in-an-application"></a>Chcete-li použít trasování v aplikaci  
  
1. Zvažte, které trasování výstupu, že který chcete přijímat získáte po nasazení aplikace.  
  
2. Vytvoření sady přepínačů. Další informace najdete v tématu [jak: Konfigurace přepínačů trasování](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
3. Přidání příkazů trasování do kódu aplikace.  
  
4. Určete, kam chcete výstup trasování objevit a přidejte odpovídající naslouchacích procesů. Další informace najdete v tématu [vytváření a inicializace naslouchacích procesů trasování](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md).  
  
5. Testování a ladění vaší aplikace a trasování kódu, které obsahuje.  
  
6. Zkompilujte aplikaci do spustitelného kódu pomocí jedné z následujících postupů:  
  
    - Použití **sestavení** nabídky spolu s **ladění** stránku **stránky vlastností** dialogové okno v **Průzkumníka řešení**. Použijte při kompilaci v sadě Visual Studio.  
  
         \- nebo –  
  
    - Použití **trasování** a **ladění** direktivy kompilátoru pro kompilaci metodu příkazového řádku. Další informace najdete v tématu [Podmíněná kompilace pomocí trasování a ladění](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md). Použijte při kompilaci z příkazového řádku.  
  
7. Pokud dojde k potížím při běhu, zapněte trasování odpovídající přepínač. Další informace najdete v tématu [konfigurace přepínačů trasování](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
     Trasování kódu zapisuje zprávy trasování do zadaného cíle, například obrazovku, do textového souboru nebo protokolu událostí. Typ naslouchací proces jste zahrnuli **Trace.listeners –** kolekce Určuje cíl.  
  
8. Analyzujte trasování zprávy k identifikaci a porozumět danému problému v aplikaci.  
  
## <a name="trace-instrumentation-and-distributed-applications"></a>Pro trasovacího instrumentaci a distribuovaných aplikací  
 Při vytváření distribuované aplikace, možná pro vás bude obtížné otestovat aplikaci způsobem, který se použije. Několik vývojové týmy mají možnost vyzkoušet všechny možné kombinace operačních systémů nebo webových prohlížečů (včetně všech možností lokalizovaném jazyce) nebo simulace velkého počtu uživatelů, kteří se k aplikaci ve stejnou dobu. Za těchto okolností nemůže testovat, jak distribuované aplikace bude reagovat na velké objemy, jiné nastavení a chování koncových uživatelů jedinečný. Také mnoho částí distribuované aplikace mít žádné uživatelské rozhraní pracovat přímo nebo zobrazit aktivitu z těchto částí.  
  
 Však můžete kompenzovat to tím, že distribuované aplikace při určitých událostí, abyste správci systému, zejména věcí, které se pokazí, podle popisu *instrumentace* aplikace – to znamená podle umístění příkazy trasování strategická místa v kódu. A pokud se něco neočekávaného dojde za běhu (například nadměrně dlouhá doba odezvy), můžete určit pravděpodobnou příčinou.  
  
 Pomocí příkazů trasování se můžete vyhnout těžký úkol zkoumání původní zdrojový kód, úpravách, rekompilace a pokus o této chybě za běhu v prostředí ladění. Mějte na paměti, že instrumentovat můžete nejenom k zobrazení chyb, ale také k monitorování výkonu aplikace.  
  
## <a name="strategic-placement-of-trace-statements"></a>Strategické umístění příkazů trasování  
 Zvláštní pozornost musí uplatňovat při umísťování výpisy trasování pro použití za běhu. Musíte zvážit, jaké informace vektorizace by mohla být potřeba v nasazené aplikaci tak, aby všechny pravděpodobně trasování scénáře jsou popsané odpovídajícím způsobem. Protože aplikace, které používají trasování se liší běžně, ale nejsou žádné obecné pokyny pro strategické umístění trasování. Další informace o umístění příkazů trasování najdete v tématu [jak: Přidání příkazů trasování do kódu aplikace](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md).  
  
## <a name="output-from-tracing"></a>Výstup trasování  
 Trasování shromáždí výstup podřízeného runbooku objekty volá *naslouchacích procesů*. Naslouchací proces je objekt, který přijímá výstup trasování a zapisuje je do výstupní zařízení (obvykle okna, protokolu nebo textový soubor). Když se vytvoří naslouchací proces trasování, je obvykle přidá do <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> kolekce, což naslouchací proces pro příjem všech výstupu trasování.  
  
 Trasovací informace je vždy napsané alespoň na výchozí hodnotu <xref:System.Diagnostics.Trace> cíl výstupu <xref:System.Diagnostics.DefaultTraceListener>. Pokud z nějakého důvodu jste odstranili <xref:System.Diagnostics.DefaultTraceListener> bez nutnosti přidávat další naslouchacích procesů k <xref:System.Diagnostics.Trace.Listeners%2A> kolekce, neobdržíte žádné zprávy trasování. Další informace najdete v tématu [naslouchacích procesů trasování](../../../docs/framework/debug-trace-profile/trace-listeners.md).  
  
 Všech šest <xref:System.Diagnostics.Debug> členy a <xref:System.Diagnostics.Trace> metody, které zapsat informace trasování jsou uvedeny v následující tabulce.  
  
|Metoda|Výstup|  
|------------|------------|  
|**Kontrolní výraz**|Zadaný text; nebo, pokud není zadaný žádný zásobník volání. Výstup bude zapsán pouze pokud je podmínka zadaný jako argument v **Assert** příkaz je **false**.|  
|**Selhání**|Zadaný text; nebo, pokud není zadaný žádný zásobník volání.|  
|**Zápis**|Zadaný text.|  
|**Writeif –**|Zadaný text, pokud podmínka zadaný jako argument v **writeif –** příkazu není splněna.|  
|**WriteLine**|Zadaný text a zalomení řádku.|  
|**WriteLineIf**|Zadaný text a zalomení řádku vrátit, pokud podmínka zadaný jako argument v **writelineif –** příkazu není splněna.|  
  
 Všechny moduly pro naslouchání v <xref:System.Diagnostics.Trace.Listeners%2A> kolekce přijímat zprávy popsané v tabulce výše, ale akce prováděné se mohou lišit v závislosti na tom, jaký druh naslouchací proces obdrží zprávu. Například <xref:System.Diagnostics.DefaultTraceListener> zobrazí dialogové okno výraz, když přijme **selhání** nebo se nezdařilo **Assert** oznámení, ale <xref:System.Diagnostics.TextWriterTraceListener> jednoduše zapíše výstup do jeho datového proudu.  
  
 Můžete vytvářet vlastní výsledky implementací vlastní naslouchací proces. Vlastní naslouchací může například zobrazit zprávy do okna se zprávou a připojení k databázi a přidává zprávy do tabulky. Všechny vlastní naslouchací procesy by měly podporovat šest metod uvedených výše. Další informace o vytvoření naslouchacích procesů definované pro vývojáře najdete v tématu <xref:System.Diagnostics.TraceListener> v referenční dokumentaci rozhraní .NET Framework.  
  
> [!NOTE]
>  V [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], **Debug.Write –**, **Debug.WriteIf**, **Debug.WriteLine**, a **Debug.WriteLineIf** nahradil metody **Debug.Print** metodu, která byla k dispozici v dřívějších verzích sady Visual Basic.  
  
 **Zápisu** a **WriteLine** metody vždy vypsání textu, že zadáte. **Assert –**, **writeif –**, a **writelineif –** vyžadují logický argument, který určuje, zda zapisovaly zadaný text; zapisovaly zadaný text pouze pokud má výraz hodnotu **true** (pro **writeif –** a **writelineif –**), nebo **false** (pro **Assert**). **Selhání** metoda vždy zapíše zadaný text. Další informace najdete v tématu [jak: Přidání příkazů trasování do kódu aplikace](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md) a odkaz na rozhraní .NET Framework.  
  
## <a name="security-concerns"></a>Zajištění zabezpečení  
 Pokud zakážete nikoli trasování a ladění před nasazením aplikace technologie ASP.NET, aplikace může zobrazit informace o sobě, který by mohl zneužít škodlivý program. Další informace najdete v tématu [jak: Kompilace podmíněně s Trace a Debug](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md), [kompilování a sestavování](/visualstudio/ide/compiling-and-building-in-visual-studio), a [jak: Vytváření, inicializace a konfigurace přepínačů trasování](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md). Ladění je také možné konfigurovat pomocí Internetové informační služby (IIS).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceSource>
- [Kontrakty kódu](../../../docs/framework/debug-trace-profile/code-contracts.md)
- [Typy projektů jazyka C#, F# a Visual Basic](/visualstudio/debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types)
- [Postupy: Přidání příkazů trasování do kódu aplikace](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [Postupy: Podmíněná kompilace pomocí trasování a ladění](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
- [Postupy: Vytváření, inicializace a konfigurace přepínačů trasování](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)
- [Postupy: Vytváření a inicializace zdrojů trasování](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)
- [Postupy: Použití třídy TraceSource a filtrů s naslouchacími procesy trasování](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md)
- [Moduly naslouchání trasování](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [Přepínače trasování](../../../docs/framework/debug-trace-profile/trace-switches.md)
