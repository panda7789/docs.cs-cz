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
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a><span data-ttu-id="57bfa-102">Postupy: Použití třídy TraceSource a filtrů s naslouchacími procesy trasování</span><span class="sxs-lookup"><span data-stu-id="57bfa-102">How to: Use TraceSource and Filters with Trace Listeners</span></span>
<span data-ttu-id="57bfa-103">Mezi nové funkce v rozhraní .NET Framework verze 2.0 je systém rozšířené trasování.</span><span class="sxs-lookup"><span data-stu-id="57bfa-103">One of the new features in the .NET Framework version 2.0 is an enhanced tracing system.</span></span> <span data-ttu-id="57bfa-104">Základní se nezmění: trasování zprávy odesílány prostřednictvím přepínače naslouchacích procesů, které nahlásit střední přidružené výstupní data.</span><span class="sxs-lookup"><span data-stu-id="57bfa-104">The basic premise is unchanged: tracing messages are sent through switches to listeners, which report the data to an associated output medium.</span></span> <span data-ttu-id="57bfa-105">Hlavní rozdíl pro verzi 2.0 je, že můžete zahájit trasování prostřednictvím instancí <xref:System.Diagnostics.TraceSource> třídy.</span><span class="sxs-lookup"><span data-stu-id="57bfa-105">A primary difference for version 2.0 is that traces can be initiated through instances of the <xref:System.Diagnostics.TraceSource> class.</span></span> <span data-ttu-id="57bfa-106"><xref:System.Diagnostics.TraceSource> slouží jako systém rozšířené trasování a dá se použít místo statické metody starší <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> třídy trasování.</span><span class="sxs-lookup"><span data-stu-id="57bfa-106"><xref:System.Diagnostics.TraceSource> is intended to function as an enhanced tracing system and can be used in place of the static methods of the older <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> tracing classes.</span></span> <span data-ttu-id="57bfa-107">Známé <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> třídy stále existují, ale doporučený postup je použít <xref:System.Diagnostics.TraceSource> třídy pro trasování.</span><span class="sxs-lookup"><span data-stu-id="57bfa-107">The familiar <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> classes still exist, but the recommended practice is to use the <xref:System.Diagnostics.TraceSource> class for tracing.</span></span>  
  
 <span data-ttu-id="57bfa-108">Toto téma popisuje použití <xref:System.Diagnostics.TraceSource> pomocí konfiguračního souboru aplikace s velkou provázaností.</span><span class="sxs-lookup"><span data-stu-id="57bfa-108">This topic describes the use of a <xref:System.Diagnostics.TraceSource> coupled with an application configuration file.</span></span>  <span data-ttu-id="57bfa-109">Je to možné, i když není doporučeno použití trasování <xref:System.Diagnostics.TraceSource> bez použití konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="57bfa-109">It is possible, although not recommended, to trace using a <xref:System.Diagnostics.TraceSource> without the use of a configuration file.</span></span> <span data-ttu-id="57bfa-110">Informace o sledování bez konfiguračního souboru najdete v tématu [jak: Vytváření a inicializace zdrojů trasování](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md).</span><span class="sxs-lookup"><span data-stu-id="57bfa-110">For information on tracing without a configuration file, see [How to: Create and Initialize Trace Sources](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md).</span></span>  
  
### <a name="to-create-and-initialize-your-trace-source"></a><span data-ttu-id="57bfa-111">Vytvoření a Inicializace zdroje trasování</span><span class="sxs-lookup"><span data-stu-id="57bfa-111">To create and initialize your trace source</span></span>  
  
1. <span data-ttu-id="57bfa-112">Prvním krokem k instrumentaci aplikace pomocí trasování je vytvoření zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="57bfa-112">The first step to instrumenting an application with tracing is to create a trace source.</span></span> <span data-ttu-id="57bfa-113">Ve velkých projektech s různými součástmi můžete vytvořit samostatné trasování zdroj pro jednotlivé komponenty.</span><span class="sxs-lookup"><span data-stu-id="57bfa-113">In large projects with various components, you can create a separate trace source for each component.</span></span> <span data-ttu-id="57bfa-114">Doporučeným postupem je použít název aplikace pro název zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="57bfa-114">The recommended practice is to use the application name for the trace source name.</span></span> <span data-ttu-id="57bfa-115">To bude usnadňují oddělovat různé trasování.</span><span class="sxs-lookup"><span data-stu-id="57bfa-115">This will make it easier to keep the different traces separate.</span></span> <span data-ttu-id="57bfa-116">Následující kód vytvoří nový zdroj trasování (`mySource)` a volá metodu (`Activity1`), který provádí trasování událostí.</span><span class="sxs-lookup"><span data-stu-id="57bfa-116">The following code creates a new trace source (`mySource)` and calls a method (`Activity1`) that traces events.</span></span>  <span data-ttu-id="57bfa-117">Zprávy trasování jsou zapsány pomocí výchozí naslouchací služby stopy.</span><span class="sxs-lookup"><span data-stu-id="57bfa-117">The trace messages are written by the default trace listener.</span></span>  
  
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
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a><span data-ttu-id="57bfa-118">Vytvoření a inicializace naslouchacích procesů trasování a filtry</span><span class="sxs-lookup"><span data-stu-id="57bfa-118">To create and initialize trace listeners and filters</span></span>  
  
1. <span data-ttu-id="57bfa-119">Filtry ani naslouchacích procesů trasování kódu v prvním postupu neidentifikuje prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="57bfa-119">The code in the first procedure does not programmatically identify any trace listeners or filters.</span></span> <span data-ttu-id="57bfa-120">Samotný kód za následek zprávy trasování do výchozí naslouchací služby stopy.</span><span class="sxs-lookup"><span data-stu-id="57bfa-120">The code alone results in the trace messages being written to the default trace listener.</span></span> <span data-ttu-id="57bfa-121">Pro konfiguraci naslouchacích procesů trasování konkrétní a jejich přidružené filtry, upravte konfigurační soubor, který odpovídá názvu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="57bfa-121">To configure specific trace listeners and their associated filters, edit the configuration file that corresponds to the name of your application.</span></span> <span data-ttu-id="57bfa-122">V tomto souboru můžete přidat nebo odebrat naslouchací proces, nastavte vlastnosti a filtr pro naslouchací proces či odebrat naslouchacích procesů.</span><span class="sxs-lookup"><span data-stu-id="57bfa-122">In this file, you can add or remove a listener, set the properties and filter for a listener, or remove listeners.</span></span> <span data-ttu-id="57bfa-123">Následující příklad konfigurační soubor ukazuje, jak k inicializaci naslouchacího procesu trasování konzoly a naslouchacího procesu text zapisovač trasování pro zdroj trasování, vytvořený v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="57bfa-123">The following configuration file example shows how to initialize a console trace listener and a text writer trace listener for the trace source that is created in the preceding procedure.</span></span> <span data-ttu-id="57bfa-124">Kromě konfigurace posluchačů trasování, konfigurační soubor vytvoří filtry pro oba posluchače a vytvoří zdroj přepínače pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="57bfa-124">In addition to configuring the trace listeners, the configuration file creates filters for both of the listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="57bfa-125">Pro přidávání posluchačů trasování jsou uvedeny dvě metody: Přidání posluchače přímo ke zdroji trasování a přidání posluchače do sdílené kolekce posluchačů a následné přidání podle názvu do zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="57bfa-125">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="57bfa-126">Filtry identifikované pro dva naslouchací procesy jsou inicializovány s jinými zdrojovými úrovněmi.</span><span class="sxs-lookup"><span data-stu-id="57bfa-126">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="57bfa-127">Výsledkem je některé zprávy jsou zapisovány pouze jedním ze dvou posluchačů.</span><span class="sxs-lookup"><span data-stu-id="57bfa-127">This results in some messages being written by only one of the two listeners.</span></span>  
  
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
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a><span data-ttu-id="57bfa-128">Chcete-li změnit úroveň, jakou naslouchací proces zapíše zprávu trasování</span><span class="sxs-lookup"><span data-stu-id="57bfa-128">To change the level at which a listener writes a trace message</span></span>  
  
1. <span data-ttu-id="57bfa-129">Konfigurační soubor inicializuje nastavení pro zdroj trasování v době, kdy je aplikace inicializována.</span><span class="sxs-lookup"><span data-stu-id="57bfa-129">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="57bfa-130">Chcete-li změnit tato nastavení musíte změnit konfigurační soubor a restartovat aplikaci nebo programově aktualizovat aplikace pomocí <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="57bfa-130">To change those settings you must change the configuration file and restart the application or programmatically refresh the application using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="57bfa-131">Aplikace můžete dynamicky měnit vlastnosti nastavením konfiguračního souboru pro přepsání jakéhokoli nastavení zadaného uživatelem.</span><span class="sxs-lookup"><span data-stu-id="57bfa-131">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span>  <span data-ttu-id="57bfa-132">Například můžete chtít zajistit, kritické zprávy byly odesílány vždy do textového souboru, bez ohledu na aktuální nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="57bfa-132">For example, you might want to assure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="57bfa-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57bfa-133">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [<span data-ttu-id="57bfa-134">Postupy: Vytváření a inicializace zdrojů trasování</span><span class="sxs-lookup"><span data-stu-id="57bfa-134">How to: Create and Initialize Trace Sources</span></span>](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)
- [<span data-ttu-id="57bfa-135">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="57bfa-135">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)
