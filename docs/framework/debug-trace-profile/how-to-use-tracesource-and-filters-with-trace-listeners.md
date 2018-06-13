---
title: 'Postupy: Použití třídy TraceSource a filtrů s naslouchacími procesy trasování'
ms.date: 03/30/2017
helpviewer_keywords:
- initializing trace listeners
- configuration files [.NET Framework], trace listeners
- app.config files, trace listeners
- levels of writing trace messages
- trace listeners, TraceSource class
- application configuration files, trace listeners
- filters, trace listeners
- TraceSource class, trace listeners
- trace listeners, creating
- trace listeners, filters
- trace listeners, initializing
ms.assetid: 21dc2169-947d-453a-b0e2-3dac3ba0cc9f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c7a912386d93e727a1f4cd2253ad06be76ae3385
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388339"
---
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a>Postupy: Použití třídy TraceSource a filtrů s naslouchacími procesy trasování
Jeden z nových funkcí v rozhraní .NET Framework verze 2.0 je systém rozšířené trasování. Základním předpokladem je beze změny: trasování zprávy jsou odesílány prostřednictvím přepínače na naslouchací procesy, které nahlásit střední přidružené výstupní data. Základní rozdíl pro verzi 2.0 je, že trasování lze inicializovat pomocí instance <xref:System.Diagnostics.TraceSource> třídy. <xref:System.Diagnostics.TraceSource> je určen k fungovat jako systém rozšířené trasování a jde použít místo statických metod starší <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> třídy trasování. Známé <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> třídy stále existují, ale je doporučený postup použití <xref:System.Diagnostics.TraceSource> třídu pro trasování.  
  
 Toto téma popisuje použití <xref:System.Diagnostics.TraceSource> kombinaci s konfiguračním souboru aplikace.  Je možné, však není doporučena pomocí trasování <xref:System.Diagnostics.TraceSource> bez použití konfiguračního souboru. Informace o trasování bez konfiguračního souboru, najdete v části [postupy: vytváření a inicializace zdrojů trasování](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md).  
  
### <a name="to-create-and-initialize-your-trace-source"></a>K vytvoření a inicializace váš zdroj trasování  
  
1.  Prvním krokem k instrumentaci aplikace s trasování je vytvoření zdroje trasování. V rozsáhlých projektů s různými součástmi můžete vytvořit zdroj samostatné trasování pro každou součást. Doporučený postup je použití název aplikace pro název zdroje trasování. To bude usnadňují oddělit různé trasování. Následující kód vytvoří nový zdroj trasování (`mySource)` a volá metodu (`Activity1`) který provádí trasování událostí.  Trasovací zprávy jsou zapsány pomocí výchozí naslouchací proces trasování.  
  
    ```  
    using System;  
    using System.Diagnostics;  
    using System.Threading;  
  
    namespace TraceSourceApp  
    {  
        class Program  
        {  
            private static TraceSource mySource =   
                new TraceSource("TraceSourceApp");  
            static void Main(string[] args)  
            {  
                Activity1();  
                mySource.Close();  
                return;  
            }  
            static void Activity1()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 1,   
                    "Error message.");  
                mySource.TraceEvent(TraceEventType.Warning, 2,   
                    "Warning message.");  
            }  
        }  
    }  
    ```  
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a>K vytvoření a inicializace modulů naslouchání trasování a filtry  
  
1.  Kód v prvním postupu neidentifikuje prostřednictvím kódu programu, všechny trasování – moduly naslouchání nebo filtry. Kód samostatně výsledkem zapisovaný pro naslouchací proces trasování výchozí trasování zprávy. Pro konfiguraci konkrétní trasování – moduly naslouchání a jejich přidružené filtry, upravte konfigurační soubor, který odpovídá názvu vaší aplikace. V tomto souboru můžete přidat nebo odebrat naslouchací proces, nastavte vlastnosti a filtru pro naslouchací proces nebo odebrat moduly pro naslouchání. Následující příklad souboru konfigurace ukazuje, jak se inicializovat naslouchací proces trasování konzoly a naslouchací zapisovač textu pro zdroj trasování, který je vytvořen v předchozím postupu. Kromě konfigurace naslouchací procesy trasování, konfigurační soubor vytvoří filtry pro obě posluchače a vytvoří přepínač zdroje pro zdroj trasování. Pro přidání trasování – moduly naslouchání se zobrazují dvě techniky: Přidání naslouchací proces přímo na zdroj trasování a přidání naslouchací proces ke kolekci sdílené moduly pro naslouchání a následným přidáním podle názvu zdroje trasování. Filtry identifikovat pro dva naslouchací procesy jsou inicializovány s jinou zdrojovou úrovněmi. Výsledkem některé zprávy zapisovaný jenom jedna z dva naslouchací procesy.  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <source name="TraceSourceApp"   
            switchName="sourceSwitch"   
            switchType="System.Diagnostics.SourceSwitch">  
            <listeners>  
              <add name="console"   
                type="System.Diagnostics.ConsoleTraceListener">  
                <filter type="System.Diagnostics.EventTypeFilter"   
                  initializeData="Warning"/>  
              </add>  
              <add name="myListener"/>  
              <remove name="Default"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="sourceSwitch" value="Warning"/>  
        </switches>  
        <sharedListeners>  
          <add name="myListener"   
            type="System.Diagnostics.TextWriterTraceListener"   
            initializeData="myListener.log">  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error"/>  
          </add>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a>Chcete-li změnit úroveň, kdy naslouchací proces zapíše zprávu trasování  
  
1.  Konfigurační soubor inicializuje nastavení pro zdroj trasování v době, kdy aplikace je inicializován. Chcete-li změnit tato nastavení musíte změnit konfigurační soubor a restartování aplikace nebo prostřednictvím kódu programu aktualizujte aplikace pomocí <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> metoda. Aplikace můžete dynamicky měnit vlastnosti nastavit pomocí konfiguračního souboru pro přepsání nastavení zadaný uživatelem.  Například můžete chtít zajistit kritické zprávy vždy odesílání do textového souboru, bez ohledu na aktuální nastavení konfigurace.  
  
    ```  
    using System;  
    using System.Diagnostics;  
    using System.Threading;  
  
    namespace TraceSourceApp  
    {  
        class Program  
        {  
            private static TraceSource mySource =   
                new TraceSource("TraceSourceApp");  
            static void Main(string[] args)  
            {  
                Activity1();  
  
                // Change the event type for which tracing occurs.  
                // The console trace listener must be specified   
                // in the configuration file. First, save the original  
                // settings from the configuration file.  
                EventTypeFilter configFilter =   
                    (EventTypeFilter)mySource.Listeners["console"].Filter;  
  
                // Then create a new event type filter that ensures   
                // critical messages will be written.  
                mySource.Listeners["console"].Filter =  
                    new EventTypeFilter(SourceLevels.Critical);  
                Activity2();  
  
                // Allow the trace source to send messages to listeners   
                // for all event types. This statement will override   
                // any settings in the configuration file.  
                mySource.Switch.Level = SourceLevels.All;  
  
                // Restore the original filter settings.  
                mySource.Listeners["console"].Filter = configFilter;  
                Activity3();  
                mySource.Close();  
                return;  
            }  
            static void Activity1()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 1,   
                    "Error message.");  
                mySource.TraceEvent(TraceEventType.Warning, 2,   
                    "Warning message.");  
            }  
            static void Activity2()  
            {  
                mySource.TraceEvent(TraceEventType.Critical, 3,   
                    "Critical message.");  
                mySource.TraceInformation("Informational message.");  
            }  
            static void Activity3()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 4,   
                    "Error message.");  
                mySource.TraceInformation("Informational message.");  
            }  
        }  
    }  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.EventTypeFilter>  
 [Postupy: Vytváření a inicializace zdrojů trasování](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)  
 [Moduly naslouchání trasování](../../../docs/framework/debug-trace-profile/trace-listeners.md)
