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
ms.openlocfilehash: 6805385ec21deb8748354647ab0f09b3a51353fa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754411"
---
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a>Postupy: Použití třídy TraceSource a filtrů s naslouchacími procesy trasování
Mezi nové funkce v rozhraní .NET Framework verze 2.0 je systém rozšířené trasování. Základní se nezmění: trasování zprávy odesílány prostřednictvím přepínače naslouchacích procesů, které nahlásit střední přidružené výstupní data. Hlavní rozdíl pro verzi 2.0 je, že můžete zahájit trasování prostřednictvím instancí <xref:System.Diagnostics.TraceSource> třídy. <xref:System.Diagnostics.TraceSource> slouží jako systém rozšířené trasování a dá se použít místo statické metody starší <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> třídy trasování. Známé <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> třídy stále existují, ale doporučený postup je použít <xref:System.Diagnostics.TraceSource> třídy pro trasování.  
  
 Toto téma popisuje použití <xref:System.Diagnostics.TraceSource> pomocí konfiguračního souboru aplikace s velkou provázaností.  Je to možné, i když není doporučeno použití trasování <xref:System.Diagnostics.TraceSource> bez použití konfiguračního souboru. Informace o sledování bez konfiguračního souboru najdete v tématu [jak: Vytváření a inicializace zdrojů trasování](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md).  
  
### <a name="to-create-and-initialize-your-trace-source"></a>Vytvoření a Inicializace zdroje trasování  
  
1. Prvním krokem k instrumentaci aplikace pomocí trasování je vytvoření zdroje trasování. Ve velkých projektech s různými součástmi můžete vytvořit samostatné trasování zdroj pro jednotlivé komponenty. Doporučeným postupem je použít název aplikace pro název zdroje trasování. To bude usnadňují oddělovat různé trasování. Následující kód vytvoří nový zdroj trasování (`mySource)` a volá metodu (`Activity1`), který provádí trasování událostí.  Zprávy trasování jsou zapsány pomocí výchozí naslouchací služby stopy.  
  
    ```csharp
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
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a>Vytvoření a inicializace naslouchacích procesů trasování a filtry  
  
1. Filtry ani naslouchacích procesů trasování kódu v prvním postupu neidentifikuje prostřednictvím kódu programu. Samotný kód za následek zprávy trasování do výchozí naslouchací služby stopy. Pro konfiguraci naslouchacích procesů trasování konkrétní a jejich přidružené filtry, upravte konfigurační soubor, který odpovídá názvu vaší aplikace. V tomto souboru můžete přidat nebo odebrat naslouchací proces, nastavte vlastnosti a filtr pro naslouchací proces či odebrat naslouchacích procesů. Následující příklad konfigurační soubor ukazuje, jak k inicializaci naslouchacího procesu trasování konzoly a naslouchacího procesu text zapisovač trasování pro zdroj trasování, vytvořený v předchozím postupu. Kromě konfigurace posluchačů trasování, konfigurační soubor vytvoří filtry pro oba posluchače a vytvoří zdroj přepínače pro zdroj trasování. Pro přidávání posluchačů trasování jsou uvedeny dvě metody: Přidání posluchače přímo ke zdroji trasování a přidání posluchače do sdílené kolekce posluchačů a následné přidání podle názvu do zdroje trasování. Filtry identifikované pro dva naslouchací procesy jsou inicializovány s jinými zdrojovými úrovněmi. Výsledkem je některé zprávy jsou zapisovány pouze jedním ze dvou posluchačů.  
  
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
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a>Chcete-li změnit úroveň, jakou naslouchací proces zapíše zprávu trasování  
  
1. Konfigurační soubor inicializuje nastavení pro zdroj trasování v době, kdy je aplikace inicializována. Chcete-li změnit tato nastavení musíte změnit konfigurační soubor a restartovat aplikaci nebo programově aktualizovat aplikace pomocí <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> metody. Aplikace můžete dynamicky měnit vlastnosti nastavením konfiguračního souboru pro přepsání jakéhokoli nastavení zadaného uživatelem.  Například můžete chtít zajistit, kritické zprávy byly odesílány vždy do textového souboru, bez ohledu na aktuální nastavení konfigurace.  
  
    ```csharp
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [Postupy: Vytváření a inicializace zdrojů trasování](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)
- [Moduly naslouchání trasování](../../../docs/framework/debug-trace-profile/trace-listeners.md)
