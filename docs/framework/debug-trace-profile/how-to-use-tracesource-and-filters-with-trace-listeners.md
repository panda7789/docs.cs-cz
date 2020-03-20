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
ms.openlocfilehash: 7d2b9da72ae0b2a5c60eb90da0b56b45634e6e05
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181811"
---
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a>Postupy: Použití třídy TraceSource a filtrů s naslouchacími procesy trasování
Jednou z nových funkcí v rozhraní .NET Framework verze 2.0 je rozšířený systém trasování. Základní předpoklad je beze změny: trasování zprávy jsou odesílány prostřednictvím přepínačů naslouchací procesy, které hlásí data na přidružené výstupní médium. Primární rozdíl pro verzi 2.0 je, že trasování lze <xref:System.Diagnostics.TraceSource> iniciovat prostřednictvím instancí třídy. <xref:System.Diagnostics.TraceSource>je určen k fungování jako rozšířený sledovací systém a může být použit <xref:System.Diagnostics.Trace> namísto statických metod starších a <xref:System.Diagnostics.Debug> trasovacích tříd. Známé <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> třídy stále existují, ale doporučeným postupem je použití třídy <xref:System.Diagnostics.TraceSource> pro trasování.  
  
 Toto téma popisuje použití <xref:System.Diagnostics.TraceSource> spolu s konfiguračním souborem aplikace.  Je možné, i když se nedoporučuje, sledovat pomocí <xref:System.Diagnostics.TraceSource> bez použití konfiguračního souboru. Informace o trasování bez konfiguračního souboru naleznete v [tématu How to: Create and Initialize Trace Sources](how-to-create-and-initialize-trace-sources.md).  
  
### <a name="to-create-and-initialize-your-trace-source"></a>Vytvoření a inicializaci zdroje trasování  
  
1. Prvním krokem k instrumentaci aplikace s trasování je vytvořit zdroj trasování. Ve velkých projektech s různými součástmi můžete vytvořit samostatný zdroj trasování pro každou komponentu. Doporučeným postupem je použití názvu aplikace pro název zdroje trasování. To usnadní oddělené sledování různých tras. Následující kód vytvoří nový zdroj`mySource)` trasování (`Activity1`a volá metodu ( ), která sleduje události.  Trasovací zprávy jsou zapsány výchozí naslouchací proces trasování.  
  
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
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a>Vytvoření a inicializaci posluchačů trasování a filtrů  
  
1. Kód v první proceduře neidentifikuje žádné posluchače trasování nebo filtry. Samotný kód má za následek trasování zpráv zapsaných na výchozí proces trasování. Chcete-li nakonfigurovat konkrétní posluchače trasování a jejich přidružené filtry, upravte konfigurační soubor, který odpovídá názvu aplikace. V tomto souboru můžete přidat nebo odebrat naslouchací proces, nastavit vlastnosti a filtrovat pro naslouchací proces nebo odebrat posluchače. Následující příklad konfiguračního souboru ukazuje, jak inicializovat posluchač trasování konzoly a posluchače trasování zapisovače textu pro zdroj trasování, který je vytvořen v předchozím postupu. Kromě konfigurace posluchačů trasování konfigurační soubor vytvoří filtry pro oba posluchače a vytvoří zdrojový přepínač pro zdroj trasování. Dvě techniky jsou zobrazeny pro přidání naslouchací procesy trasování: přidání posluchače přímo do zdroje trasování a přidání posluchače do sdílené posluchače kolekce a potom jej přidat podle názvu do zdroje trasování. Filtry určené pro dva naslouchací procesy jsou inicializovány s různými zdrojovými úrovněmi. To má za následek některé zprávy zapisovány pouze jeden ze dvou posluchačů.  
  
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
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a>Chcete-li změnit úroveň, na které posluchač zapíše trasovací zprávu  
  
1. Konfigurační soubor inicializuje nastavení zdroje trasování v době, kdy je aplikace inicializována. Chcete-li tato nastavení změnit, je nutné změnit konfigurační soubor <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> a restartovat aplikaci nebo programově aktualizovat aplikaci pomocí metody. Aplikace může dynamicky změnit vlastnosti nastavené konfiguračním souborem tak, aby přepsaly všechna nastavení určená uživatelem.  Můžete například chtít zajistit, že kritické zprávy jsou vždy odesílány do textového souboru, bez ohledu na aktuální nastavení konfigurace.  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [Postupy: Vytváření a inicializace zdrojů trasování](how-to-create-and-initialize-trace-sources.md)
- [Moduly naslouchání trasování](trace-listeners.md)
