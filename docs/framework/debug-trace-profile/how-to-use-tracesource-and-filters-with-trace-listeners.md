---
title: 'Postupy: Použití třídy TraceSource a filtrů s naslouchacími procesy trasování'
description: Použijte třídu TraceSource a filtry s naslouchacími procesy trasování v rozhraní .NET. TraceSource nahrazuje statické metody pro starší třídy Trace a Debug.
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
ms.openlocfilehash: 432c866f7c3ca1fd59f8f3d36acd61740b6584c0
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051256"
---
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a><span data-ttu-id="c83e2-104">Postupy: Použití třídy TraceSource a filtrů s naslouchacími procesy trasování</span><span class="sxs-lookup"><span data-stu-id="c83e2-104">How to: Use TraceSource and Filters with Trace Listeners</span></span>
<span data-ttu-id="c83e2-105">Jednou z nových funkcí v .NET Framework verze 2,0 je vylepšený sledovací systém.</span><span class="sxs-lookup"><span data-stu-id="c83e2-105">One of the new features in the .NET Framework version 2.0 is an enhanced tracing system.</span></span> <span data-ttu-id="c83e2-106">Základní místní prostředí není beze změny: trasovací zprávy jsou odesílány pomocí přepínačů posluchačům, kteří nahlásí data na přidružené výstupní médium.</span><span class="sxs-lookup"><span data-stu-id="c83e2-106">The basic premise is unchanged: tracing messages are sent through switches to listeners, which report the data to an associated output medium.</span></span> <span data-ttu-id="c83e2-107">Primární rozdíl pro verzi 2,0 je, že trasování lze iniciovat prostřednictvím instancí <xref:System.Diagnostics.TraceSource> třídy.</span><span class="sxs-lookup"><span data-stu-id="c83e2-107">A primary difference for version 2.0 is that traces can be initiated through instances of the <xref:System.Diagnostics.TraceSource> class.</span></span> <span data-ttu-id="c83e2-108"><xref:System.Diagnostics.TraceSource>je určen pro fungování jako vylepšený sledovací systém a lze jej použít místo statických metod pro starší <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> trasovací třídy.</span><span class="sxs-lookup"><span data-stu-id="c83e2-108"><xref:System.Diagnostics.TraceSource> is intended to function as an enhanced tracing system and can be used in place of the static methods of the older <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> tracing classes.</span></span> <span data-ttu-id="c83e2-109">Známé <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> třídy stále existují, ale doporučeným postupem je použití <xref:System.Diagnostics.TraceSource> třídy pro trasování.</span><span class="sxs-lookup"><span data-stu-id="c83e2-109">The familiar <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> classes still exist, but the recommended practice is to use the <xref:System.Diagnostics.TraceSource> class for tracing.</span></span>  
  
 <span data-ttu-id="c83e2-110">Toto téma popisuje použití <xref:System.Diagnostics.TraceSource> páru s konfiguračním souborem aplikace.</span><span class="sxs-lookup"><span data-stu-id="c83e2-110">This topic describes the use of a <xref:System.Diagnostics.TraceSource> coupled with an application configuration file.</span></span>  <span data-ttu-id="c83e2-111">Je možné, i když nedoporučujeme trasovat pomocí <xref:System.Diagnostics.TraceSource> konfiguračního souboru bez použití konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="c83e2-111">It is possible, although not recommended, to trace using a <xref:System.Diagnostics.TraceSource> without the use of a configuration file.</span></span> <span data-ttu-id="c83e2-112">Informace o trasování bez konfiguračního souboru najdete v tématu [Postupy: vytváření a inicializace zdrojů trasování](how-to-create-and-initialize-trace-sources.md).</span><span class="sxs-lookup"><span data-stu-id="c83e2-112">For information on tracing without a configuration file, see [How to: Create and Initialize Trace Sources](how-to-create-and-initialize-trace-sources.md).</span></span>  
  
### <a name="to-create-and-initialize-your-trace-source"></a><span data-ttu-id="c83e2-113">Vytvoření a inicializace zdroje trasování</span><span class="sxs-lookup"><span data-stu-id="c83e2-113">To create and initialize your trace source</span></span>  
  
1. <span data-ttu-id="c83e2-114">Prvním krokem k instrumentaci aplikace s trasováním je vytvoření zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="c83e2-114">The first step to instrumenting an application with tracing is to create a trace source.</span></span> <span data-ttu-id="c83e2-115">Ve velkých projektech s různými komponentami můžete pro každou komponentu vytvořit samostatný zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="c83e2-115">In large projects with various components, you can create a separate trace source for each component.</span></span> <span data-ttu-id="c83e2-116">Doporučeným postupem je použití názvu aplikace pro název zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="c83e2-116">The recommended practice is to use the application name for the trace source name.</span></span> <span data-ttu-id="c83e2-117">Díky tomu bude snazší uchovávat různá trasování odděleně.</span><span class="sxs-lookup"><span data-stu-id="c83e2-117">This will make it easier to keep the different traces separate.</span></span> <span data-ttu-id="c83e2-118">Následující kód vytvoří nový zdroj trasování ( `mySource)` a zavolá metodu ( `Activity1` ), která sleduje události.</span><span class="sxs-lookup"><span data-stu-id="c83e2-118">The following code creates a new trace source (`mySource)` and calls a method (`Activity1`) that traces events.</span></span>  <span data-ttu-id="c83e2-119">Zprávy trasování jsou zapisovány pomocí výchozího naslouchacího procesu trasování.</span><span class="sxs-lookup"><span data-stu-id="c83e2-119">The trace messages are written by the default trace listener.</span></span>  
  
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
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a><span data-ttu-id="c83e2-120">Vytvoření a inicializace posluchačů a filtrů trasování</span><span class="sxs-lookup"><span data-stu-id="c83e2-120">To create and initialize trace listeners and filters</span></span>  
  
1. <span data-ttu-id="c83e2-121">Kód v prvním postupu neidentifikuje programově žádné naslouchací procesy nebo filtry trasování.</span><span class="sxs-lookup"><span data-stu-id="c83e2-121">The code in the first procedure does not programmatically identify any trace listeners or filters.</span></span> <span data-ttu-id="c83e2-122">Samotný kód má za následek zprávy trasování, které jsou zapisovány do výchozího naslouchacího procesu trasování.</span><span class="sxs-lookup"><span data-stu-id="c83e2-122">The code alone results in the trace messages being written to the default trace listener.</span></span> <span data-ttu-id="c83e2-123">Chcete-li nakonfigurovat konkrétní naslouchací procesy trasování a jejich přidružené filtry, upravte konfigurační soubor, který odpovídá názvu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="c83e2-123">To configure specific trace listeners and their associated filters, edit the configuration file that corresponds to the name of your application.</span></span> <span data-ttu-id="c83e2-124">V tomto souboru můžete přidat nebo odebrat naslouchací proces, nastavit vlastnosti a filtr pro naslouchací proces nebo odebrat naslouchací procesy.</span><span class="sxs-lookup"><span data-stu-id="c83e2-124">In this file, you can add or remove a listener, set the properties and filter for a listener, or remove listeners.</span></span> <span data-ttu-id="c83e2-125">Následující příklad konfiguračního souboru ukazuje, jak inicializovat naslouchací proces trasování konzoly a naslouchací proces zapisovače textu pro zdroj trasování, který je vytvořen v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="c83e2-125">The following configuration file example shows how to initialize a console trace listener and a text writer trace listener for the trace source that is created in the preceding procedure.</span></span> <span data-ttu-id="c83e2-126">Kromě konfigurace posluchačů trasování vytvoří konfigurační soubor filtry pro oba posluchače a vytvoří zdrojový přepínač pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="c83e2-126">In addition to configuring the trace listeners, the configuration file creates filters for both of the listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="c83e2-127">Pro přidávání posluchačů trasování jsou zobrazeny dvě metody: Přidání naslouchacího procesu přímo do zdroje trasování a přidání naslouchacího procesu do sdílené kolekce posluchačů a jejich přidání podle názvu do zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="c83e2-127">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="c83e2-128">Filtry identifikované pro dva naslouchací procesy jsou inicializovány s různými zdrojovými úrovněmi.</span><span class="sxs-lookup"><span data-stu-id="c83e2-128">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="c83e2-129">Výsledkem je, že některé zprávy zapisují pouze jeden ze dvou posluchačů.</span><span class="sxs-lookup"><span data-stu-id="c83e2-129">This results in some messages being written by only one of the two listeners.</span></span>  
  
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
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a><span data-ttu-id="c83e2-130">Změna úrovně, na které naslouchací proces zapisuje trasovací zprávu</span><span class="sxs-lookup"><span data-stu-id="c83e2-130">To change the level at which a listener writes a trace message</span></span>  
  
1. <span data-ttu-id="c83e2-131">Konfigurační soubor inicializuje nastavení pro zdroj trasování v době, kdy byla aplikace inicializována.</span><span class="sxs-lookup"><span data-stu-id="c83e2-131">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="c83e2-132">Chcete-li změnit tato nastavení, musíte změnit konfigurační soubor a restartovat aplikaci nebo programově aktualizovat aplikaci pomocí <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="c83e2-132">To change those settings you must change the configuration file and restart the application or programmatically refresh the application using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c83e2-133">Aplikace může dynamicky měnit vlastnosti nastavené konfiguračním souborem pro přepsání všech nastavení zadaných uživatelem.</span><span class="sxs-lookup"><span data-stu-id="c83e2-133">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span>  <span data-ttu-id="c83e2-134">Například můžete chtít zajistit, aby se kritické zprávy vždy odesílaly do textového souboru, bez ohledu na aktuální nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="c83e2-134">For example, you might want to assure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c83e2-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="c83e2-135">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [<span data-ttu-id="c83e2-136">Postupy: Vytváření a inicializace zdrojů trasování</span><span class="sxs-lookup"><span data-stu-id="c83e2-136">How to: Create and Initialize Trace Sources</span></span>](how-to-create-and-initialize-trace-sources.md)
- [<span data-ttu-id="c83e2-137">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="c83e2-137">Trace Listeners</span></span>](trace-listeners.md)
