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
ms.openlocfilehash: 53cdce767d437c47aab94e883381954f8cf70653
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215924"
---
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a><span data-ttu-id="2e59b-102">Postupy: Použití třídy TraceSource a filtrů s naslouchacími procesy trasování</span><span class="sxs-lookup"><span data-stu-id="2e59b-102">How to: Use TraceSource and Filters with Trace Listeners</span></span>
<span data-ttu-id="2e59b-103">Jednou z nových funkcí v .NET Framework verze 2,0 je vylepšený sledovací systém.</span><span class="sxs-lookup"><span data-stu-id="2e59b-103">One of the new features in the .NET Framework version 2.0 is an enhanced tracing system.</span></span> <span data-ttu-id="2e59b-104">Základní místní prostředí není beze změny: trasovací zprávy jsou odesílány pomocí přepínačů posluchačům, kteří nahlásí data na přidružené výstupní médium.</span><span class="sxs-lookup"><span data-stu-id="2e59b-104">The basic premise is unchanged: tracing messages are sent through switches to listeners, which report the data to an associated output medium.</span></span> <span data-ttu-id="2e59b-105">Primární rozdíl pro verzi 2,0 je, že trasování lze inicializovat prostřednictvím instancí třídy <xref:System.Diagnostics.TraceSource>.</span><span class="sxs-lookup"><span data-stu-id="2e59b-105">A primary difference for version 2.0 is that traces can be initiated through instances of the <xref:System.Diagnostics.TraceSource> class.</span></span> <span data-ttu-id="2e59b-106"><xref:System.Diagnostics.TraceSource> má fungovat jako vylepšený sledovací systém a lze jej použít místo statických metod pro starší <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> trasovacích tříd.</span><span class="sxs-lookup"><span data-stu-id="2e59b-106"><xref:System.Diagnostics.TraceSource> is intended to function as an enhanced tracing system and can be used in place of the static methods of the older <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> tracing classes.</span></span> <span data-ttu-id="2e59b-107">Známé <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> třídy stále existují, ale doporučeným postupem je použití třídy <xref:System.Diagnostics.TraceSource> pro trasování.</span><span class="sxs-lookup"><span data-stu-id="2e59b-107">The familiar <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> classes still exist, but the recommended practice is to use the <xref:System.Diagnostics.TraceSource> class for tracing.</span></span>  
  
 <span data-ttu-id="2e59b-108">Toto téma popisuje použití <xref:System.Diagnostics.TraceSource> společně s konfiguračním souborem aplikace.</span><span class="sxs-lookup"><span data-stu-id="2e59b-108">This topic describes the use of a <xref:System.Diagnostics.TraceSource> coupled with an application configuration file.</span></span>  <span data-ttu-id="2e59b-109">K trasování pomocí <xref:System.Diagnostics.TraceSource> bez použití konfiguračního souboru je to možné, i když to nedoporučujeme.</span><span class="sxs-lookup"><span data-stu-id="2e59b-109">It is possible, although not recommended, to trace using a <xref:System.Diagnostics.TraceSource> without the use of a configuration file.</span></span> <span data-ttu-id="2e59b-110">Informace o trasování bez konfiguračního souboru najdete v tématu [Postupy: vytváření a inicializace zdrojů trasování](how-to-create-and-initialize-trace-sources.md).</span><span class="sxs-lookup"><span data-stu-id="2e59b-110">For information on tracing without a configuration file, see [How to: Create and Initialize Trace Sources](how-to-create-and-initialize-trace-sources.md).</span></span>  
  
### <a name="to-create-and-initialize-your-trace-source"></a><span data-ttu-id="2e59b-111">Vytvoření a inicializace zdroje trasování</span><span class="sxs-lookup"><span data-stu-id="2e59b-111">To create and initialize your trace source</span></span>  
  
1. <span data-ttu-id="2e59b-112">Prvním krokem k instrumentaci aplikace s trasováním je vytvoření zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="2e59b-112">The first step to instrumenting an application with tracing is to create a trace source.</span></span> <span data-ttu-id="2e59b-113">Ve velkých projektech s různými komponentami můžete pro každou komponentu vytvořit samostatný zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="2e59b-113">In large projects with various components, you can create a separate trace source for each component.</span></span> <span data-ttu-id="2e59b-114">Doporučeným postupem je použití názvu aplikace pro název zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="2e59b-114">The recommended practice is to use the application name for the trace source name.</span></span> <span data-ttu-id="2e59b-115">Díky tomu bude snazší uchovávat různá trasování odděleně.</span><span class="sxs-lookup"><span data-stu-id="2e59b-115">This will make it easier to keep the different traces separate.</span></span> <span data-ttu-id="2e59b-116">Následující kód vytvoří nový zdroj trasování (`mySource)` a zavolá metodu (`Activity1`), která sleduje události.</span><span class="sxs-lookup"><span data-stu-id="2e59b-116">The following code creates a new trace source (`mySource)` and calls a method (`Activity1`) that traces events.</span></span>  <span data-ttu-id="2e59b-117">Zprávy trasování jsou zapisovány pomocí výchozího naslouchacího procesu trasování.</span><span class="sxs-lookup"><span data-stu-id="2e59b-117">The trace messages are written by the default trace listener.</span></span>  
  
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
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a><span data-ttu-id="2e59b-118">Vytvoření a inicializace posluchačů a filtrů trasování</span><span class="sxs-lookup"><span data-stu-id="2e59b-118">To create and initialize trace listeners and filters</span></span>  
  
1. <span data-ttu-id="2e59b-119">Kód v prvním postupu neidentifikuje programově žádné naslouchací procesy nebo filtry trasování.</span><span class="sxs-lookup"><span data-stu-id="2e59b-119">The code in the first procedure does not programmatically identify any trace listeners or filters.</span></span> <span data-ttu-id="2e59b-120">Samotný kód má za následek zprávy trasování, které jsou zapisovány do výchozího naslouchacího procesu trasování.</span><span class="sxs-lookup"><span data-stu-id="2e59b-120">The code alone results in the trace messages being written to the default trace listener.</span></span> <span data-ttu-id="2e59b-121">Chcete-li nakonfigurovat konkrétní naslouchací procesy trasování a jejich přidružené filtry, upravte konfigurační soubor, který odpovídá názvu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="2e59b-121">To configure specific trace listeners and their associated filters, edit the configuration file that corresponds to the name of your application.</span></span> <span data-ttu-id="2e59b-122">V tomto souboru můžete přidat nebo odebrat naslouchací proces, nastavit vlastnosti a filtr pro naslouchací proces nebo odebrat naslouchací procesy.</span><span class="sxs-lookup"><span data-stu-id="2e59b-122">In this file, you can add or remove a listener, set the properties and filter for a listener, or remove listeners.</span></span> <span data-ttu-id="2e59b-123">Následující příklad konfiguračního souboru ukazuje, jak inicializovat naslouchací proces trasování konzoly a naslouchací proces zapisovače textu pro zdroj trasování, který je vytvořen v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="2e59b-123">The following configuration file example shows how to initialize a console trace listener and a text writer trace listener for the trace source that is created in the preceding procedure.</span></span> <span data-ttu-id="2e59b-124">Kromě konfigurace posluchačů trasování vytvoří konfigurační soubor filtry pro oba posluchače a vytvoří zdrojový přepínač pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="2e59b-124">In addition to configuring the trace listeners, the configuration file creates filters for both of the listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="2e59b-125">Pro přidávání posluchačů trasování jsou zobrazeny dvě metody: Přidání naslouchacího procesu přímo do zdroje trasování a přidání naslouchacího procesu do sdílené kolekce posluchačů a jejich přidání podle názvu do zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="2e59b-125">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="2e59b-126">Filtry identifikované pro dva naslouchací procesy jsou inicializovány s různými zdrojovými úrovněmi.</span><span class="sxs-lookup"><span data-stu-id="2e59b-126">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="2e59b-127">Výsledkem je, že některé zprávy zapisují pouze jeden ze dvou posluchačů.</span><span class="sxs-lookup"><span data-stu-id="2e59b-127">This results in some messages being written by only one of the two listeners.</span></span>  
  
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
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a><span data-ttu-id="2e59b-128">Změna úrovně, na které naslouchací proces zapisuje trasovací zprávu</span><span class="sxs-lookup"><span data-stu-id="2e59b-128">To change the level at which a listener writes a trace message</span></span>  
  
1. <span data-ttu-id="2e59b-129">Konfigurační soubor inicializuje nastavení pro zdroj trasování v době, kdy byla aplikace inicializována.</span><span class="sxs-lookup"><span data-stu-id="2e59b-129">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="2e59b-130">Chcete-li změnit tato nastavení, musíte změnit konfigurační soubor a restartovat aplikaci nebo programově aktualizovat aplikaci pomocí metody <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2e59b-130">To change those settings you must change the configuration file and restart the application or programmatically refresh the application using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2e59b-131">Aplikace může dynamicky měnit vlastnosti nastavené konfiguračním souborem pro přepsání všech nastavení zadaných uživatelem.</span><span class="sxs-lookup"><span data-stu-id="2e59b-131">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span>  <span data-ttu-id="2e59b-132">Například můžete chtít zajistit, aby se kritické zprávy vždy odesílaly do textového souboru, bez ohledu na aktuální nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="2e59b-132">For example, you might want to assure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2e59b-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e59b-133">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [<span data-ttu-id="2e59b-134">Postupy: Vytváření a inicializace zdrojů trasování</span><span class="sxs-lookup"><span data-stu-id="2e59b-134">How to: Create and Initialize Trace Sources</span></span>](how-to-create-and-initialize-trace-sources.md)
- [<span data-ttu-id="2e59b-135">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="2e59b-135">Trace Listeners</span></span>](trace-listeners.md)
