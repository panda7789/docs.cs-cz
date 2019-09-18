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
ms.openlocfilehash: a1e214266b66f390fecffe802270a4181a6d7a7f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052682"
---
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a>Postupy: Použití třídy TraceSource a filtrů s naslouchacími procesy trasování
Jednou z nových funkcí v .NET Framework verze 2,0 je vylepšený sledovací systém. Základní místní prostředí není beze změny: trasovací zprávy jsou odesílány pomocí přepínačů posluchačům, kteří nahlásí data na přidružené výstupní médium. Primární rozdíl pro verzi 2,0 je, že trasování lze iniciovat prostřednictvím instancí <xref:System.Diagnostics.TraceSource> třídy. <xref:System.Diagnostics.TraceSource>je určen pro fungování jako vylepšený sledovací systém a lze jej použít místo statických metod pro starší <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> trasovací třídy. Známé <xref:System.Diagnostics.Trace> <xref:System.Diagnostics.TraceSource> a <xref:System.Diagnostics.Debug> třídy stále existují, ale doporučeným postupem je použití třídy pro trasování.  
  
 Toto téma popisuje použití <xref:System.Diagnostics.TraceSource> páru s konfiguračním souborem aplikace.  Je možné, i když nedoporučujeme trasovat pomocí <xref:System.Diagnostics.TraceSource> konfiguračního souboru bez použití konfiguračního souboru. Informace o trasování bez konfiguračního souboru najdete v tématu [How to: Vytvoření a inicializace zdrojů](how-to-create-and-initialize-trace-sources.md)trasování.  
  
### <a name="to-create-and-initialize-your-trace-source"></a>Vytvoření a inicializace zdroje trasování  
  
1. Prvním krokem k instrumentaci aplikace s trasováním je vytvoření zdroje trasování. Ve velkých projektech s různými komponentami můžete pro každou komponentu vytvořit samostatný zdroj trasování. Doporučeným postupem je použití názvu aplikace pro název zdroje trasování. Díky tomu bude snazší uchovávat různá trasování odděleně. Následující kód vytvoří nový zdroj trasování (`mySource)` a zavolá metodu (`Activity1`), která sleduje události.  Zprávy trasování jsou zapisovány pomocí výchozího naslouchacího procesu trasování.  
  
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
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a>Vytvoření a inicializace posluchačů a filtrů trasování  
  
1. Kód v prvním postupu neidentifikuje programově žádné naslouchací procesy nebo filtry trasování. Samotný kód má za následek zprávy trasování, které jsou zapisovány do výchozího naslouchacího procesu trasování. Chcete-li nakonfigurovat konkrétní naslouchací procesy trasování a jejich přidružené filtry, upravte konfigurační soubor, který odpovídá názvu vaší aplikace. V tomto souboru můžete přidat nebo odebrat naslouchací proces, nastavit vlastnosti a filtr pro naslouchací proces nebo odebrat naslouchací procesy. Následující příklad konfiguračního souboru ukazuje, jak inicializovat naslouchací proces trasování konzoly a naslouchací proces zapisovače textu pro zdroj trasování, který je vytvořen v předchozím postupu. Kromě konfigurace posluchačů trasování vytvoří konfigurační soubor filtry pro oba posluchače a vytvoří zdrojový přepínač pro zdroj trasování. Pro přidávání posluchačů trasování jsou zobrazeny dvě metody: Přidání naslouchacího procesu přímo do zdroje trasování a přidání naslouchacího procesu do sdílené kolekce posluchačů a jejich přidání podle názvu do zdroje trasování. Filtry identifikované pro dva naslouchací procesy jsou inicializovány s různými zdrojovými úrovněmi. Výsledkem je, že některé zprávy zapisují pouze jeden ze dvou posluchačů.  
  
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
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a>Změna úrovně, na které naslouchací proces zapisuje trasovací zprávu  
  
1. Konfigurační soubor inicializuje nastavení pro zdroj trasování v době, kdy byla aplikace inicializována. Chcete-li změnit tato nastavení, musíte změnit konfigurační soubor a restartovat aplikaci nebo programově aktualizovat aplikaci pomocí <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> metody. Aplikace může dynamicky měnit vlastnosti nastavené konfiguračním souborem pro přepsání všech nastavení zadaných uživatelem.  Například můžete chtít zajistit, aby se kritické zprávy vždy odesílaly do textového souboru, bez ohledu na aktuální nastavení konfigurace.  
  
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
- [Postupy: Vytvoření a inicializace zdrojů trasování](how-to-create-and-initialize-trace-sources.md)
- [Moduly naslouchání trasování](trace-listeners.md)
