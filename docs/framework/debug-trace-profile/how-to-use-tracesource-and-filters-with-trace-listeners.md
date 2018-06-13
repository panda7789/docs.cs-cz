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
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a><span data-ttu-id="cb5a1-102">Postupy: Použití třídy TraceSource a filtrů s naslouchacími procesy trasování</span><span class="sxs-lookup"><span data-stu-id="cb5a1-102">How to: Use TraceSource and Filters with Trace Listeners</span></span>
<span data-ttu-id="cb5a1-103">Jeden z nových funkcí v rozhraní .NET Framework verze 2.0 je systém rozšířené trasování.</span><span class="sxs-lookup"><span data-stu-id="cb5a1-103">One of the new features in the .NET Framework version 2.0 is an enhanced tracing system.</span></span> <span data-ttu-id="cb5a1-104">Základním předpokladem je beze změny: trasování zprávy jsou odesílány prostřednictvím přepínače na naslouchací procesy, které nahlásit střední přidružené výstupní data.</span><span class="sxs-lookup"><span data-stu-id="cb5a1-104">The basic premise is unchanged: tracing messages are sent through switches to listeners, which report the data to an associated output medium.</span></span> <span data-ttu-id="cb5a1-105">Základní rozdíl pro verzi 2.0 je, že trasování lze inicializovat pomocí instance <xref:System.Diagnostics.TraceSource> třídy.</span><span class="sxs-lookup"><span data-stu-id="cb5a1-105">A primary difference for version 2.0 is that traces can be initiated through instances of the <xref:System.Diagnostics.TraceSource> class.</span></span> <span data-ttu-id="cb5a1-106"><xref:System.Diagnostics.TraceSource> je určen k fungovat jako systém rozšířené trasování a jde použít místo statických metod starší <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> třídy trasování.</span><span class="sxs-lookup"><span data-stu-id="cb5a1-106"><xref:System.Diagnostics.TraceSource> is intended to function as an enhanced tracing system and can be used in place of the static methods of the older <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> tracing classes.</span></span> <span data-ttu-id="cb5a1-107">Známé <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> třídy stále existují, ale je doporučený postup použití <xref:System.Diagnostics.TraceSource> třídu pro trasování.</span><span class="sxs-lookup"><span data-stu-id="cb5a1-107">The familiar <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> classes still exist, but the recommended practice is to use the <xref:System.Diagnostics.TraceSource> class for tracing.</span></span>  
  
 <span data-ttu-id="cb5a1-108">Toto téma popisuje použití <xref:System.Diagnostics.TraceSource> kombinaci s konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="cb5a1-108">This topic describes the use of a <xref:System.Diagnostics.TraceSource> coupled with an application configuration file.</span></span>  <span data-ttu-id="cb5a1-109">Je možné, však není doporučena pomocí trasování <xref:System.Diagnostics.TraceSource> bez použití konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="cb5a1-109">It is possible, although not recommended, to trace using a <xref:System.Diagnostics.TraceSource> without the use of a configuration file.</span></span> <span data-ttu-id="cb5a1-110">Informace o trasování bez konfiguračního souboru, najdete v části [postupy: vytváření a inicializace zdrojů trasování](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md).</span><span class="sxs-lookup"><span data-stu-id="cb5a1-110">For information on tracing without a configuration file, see [How to: Create and Initialize Trace Sources](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md).</span></span>  
  
### <a name="to-create-and-initialize-your-trace-source"></a><span data-ttu-id="cb5a1-111">K vytvoření a inicializace váš zdroj trasování</span><span class="sxs-lookup"><span data-stu-id="cb5a1-111">To create and initialize your trace source</span></span>  
  
1.  <span data-ttu-id="cb5a1-112">Prvním krokem k instrumentaci aplikace s trasování je vytvoření zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="cb5a1-112">The first step to instrumenting an application with tracing is to create a trace source.</span></span> <span data-ttu-id="cb5a1-113">V rozsáhlých projektů s různými součástmi můžete vytvořit zdroj samostatné trasování pro každou součást.</span><span class="sxs-lookup"><span data-stu-id="cb5a1-113">In large projects with various components, you can create a separate trace source for each component.</span></span> <span data-ttu-id="cb5a1-114">Doporučený postup je použití název aplikace pro název zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="cb5a1-114">The recommended practice is to use the application name for the trace source name.</span></span> <span data-ttu-id="cb5a1-115">To bude usnadňují oddělit různé trasování.</span><span class="sxs-lookup"><span data-stu-id="cb5a1-115">This will make it easier to keep the different traces separate.</span></span> <span data-ttu-id="cb5a1-116">Následující kód vytvoří nový zdroj trasování (`mySource)` a volá metodu (`Activity1`) který provádí trasování událostí.</span><span class="sxs-lookup"><span data-stu-id="cb5a1-116">The following code creates a new trace source (`mySource)` and calls a method (`Activity1`) that traces events.</span></span>  <span data-ttu-id="cb5a1-117">Trasovací zprávy jsou zapsány pomocí výchozí naslouchací proces trasování.</span><span class="sxs-lookup"><span data-stu-id="cb5a1-117">The trace messages are written by the default trace listener.</span></span>  
  
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
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a><span data-ttu-id="cb5a1-118">K vytvoření a inicializace modulů naslouchání trasování a filtry</span><span class="sxs-lookup"><span data-stu-id="cb5a1-118">To create and initialize trace listeners and filters</span></span>  
  
1.  <span data-ttu-id="cb5a1-119">Kód v prvním postupu neidentifikuje prostřednictvím kódu programu, všechny trasování – moduly naslouchání nebo filtry.</span><span class="sxs-lookup"><span data-stu-id="cb5a1-119">The code in the first procedure does not programmatically identify any trace listeners or filters.</span></span> <span data-ttu-id="cb5a1-120">Kód samostatně výsledkem zapisovaný pro naslouchací proces trasování výchozí trasování zprávy.</span><span class="sxs-lookup"><span data-stu-id="cb5a1-120">The code alone results in the trace messages being written to the default trace listener.</span></span> <span data-ttu-id="cb5a1-121">Pro konfiguraci konkrétní trasování – moduly naslouchání a jejich přidružené filtry, upravte konfigurační soubor, který odpovídá názvu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="cb5a1-121">To configure specific trace listeners and their associated filters, edit the configuration file that corresponds to the name of your application.</span></span> <span data-ttu-id="cb5a1-122">V tomto souboru můžete přidat nebo odebrat naslouchací proces, nastavte vlastnosti a filtru pro naslouchací proces nebo odebrat moduly pro naslouchání.</span><span class="sxs-lookup"><span data-stu-id="cb5a1-122">In this file, you can add or remove a listener, set the properties and filter for a listener, or remove listeners.</span></span> <span data-ttu-id="cb5a1-123">Následující příklad souboru konfigurace ukazuje, jak se inicializovat naslouchací proces trasování konzoly a naslouchací zapisovač textu pro zdroj trasování, který je vytvořen v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="cb5a1-123">The following configuration file example shows how to initialize a console trace listener and a text writer trace listener for the trace source that is created in the preceding procedure.</span></span> <span data-ttu-id="cb5a1-124">Kromě konfigurace naslouchací procesy trasování, konfigurační soubor vytvoří filtry pro obě posluchače a vytvoří přepínač zdroje pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="cb5a1-124">In addition to configuring the trace listeners, the configuration file creates filters for both of the listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="cb5a1-125">Pro přidání trasování – moduly naslouchání se zobrazují dvě techniky: Přidání naslouchací proces přímo na zdroj trasování a přidání naslouchací proces ke kolekci sdílené moduly pro naslouchání a následným přidáním podle názvu zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="cb5a1-125">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="cb5a1-126">Filtry identifikovat pro dva naslouchací procesy jsou inicializovány s jinou zdrojovou úrovněmi.</span><span class="sxs-lookup"><span data-stu-id="cb5a1-126">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="cb5a1-127">Výsledkem některé zprávy zapisovaný jenom jedna z dva naslouchací procesy.</span><span class="sxs-lookup"><span data-stu-id="cb5a1-127">This results in some messages being written by only one of the two listeners.</span></span>  
  
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
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a><span data-ttu-id="cb5a1-128">Chcete-li změnit úroveň, kdy naslouchací proces zapíše zprávu trasování</span><span class="sxs-lookup"><span data-stu-id="cb5a1-128">To change the level at which a listener writes a trace message</span></span>  
  
1.  <span data-ttu-id="cb5a1-129">Konfigurační soubor inicializuje nastavení pro zdroj trasování v době, kdy aplikace je inicializován.</span><span class="sxs-lookup"><span data-stu-id="cb5a1-129">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="cb5a1-130">Chcete-li změnit tato nastavení musíte změnit konfigurační soubor a restartování aplikace nebo prostřednictvím kódu programu aktualizujte aplikace pomocí <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="cb5a1-130">To change those settings you must change the configuration file and restart the application or programmatically refresh the application using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="cb5a1-131">Aplikace můžete dynamicky měnit vlastnosti nastavit pomocí konfiguračního souboru pro přepsání nastavení zadaný uživatelem.</span><span class="sxs-lookup"><span data-stu-id="cb5a1-131">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span>  <span data-ttu-id="cb5a1-132">Například můžete chtít zajistit kritické zprávy vždy odesílání do textového souboru, bez ohledu na aktuální nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="cb5a1-132">For example, you might want to assure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cb5a1-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb5a1-133">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.EventTypeFilter>  
 [<span data-ttu-id="cb5a1-134">Postupy: Vytváření a inicializace zdrojů trasování</span><span class="sxs-lookup"><span data-stu-id="cb5a1-134">How to: Create and Initialize Trace Sources</span></span>](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)  
 [<span data-ttu-id="cb5a1-135">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="cb5a1-135">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)
