---
title: 'Postupy: Vytváření a inicializace zdrojů trasování'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace sources
- initializing trace sources
- configuration files [.NET Framework], trace sources
ms.assetid: f88dda6f-5fda-45be-9b3c-745a9b708c4d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2d96de43d258e4a7ff925e0c5b1702727e67d737
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59339434"
---
# <a name="how-to-create-and-initialize-trace-sources"></a><span data-ttu-id="80057-102">Postupy: Vytváření a inicializace zdrojů trasování</span><span class="sxs-lookup"><span data-stu-id="80057-102">How to: Create and Initialize Trace Sources</span></span>
<span data-ttu-id="80057-103"><xref:System.Diagnostics.TraceSource> Třídu aplikace používá k vytvoření trasování, které lze asociovat s aplikací.</span><span class="sxs-lookup"><span data-stu-id="80057-103">The <xref:System.Diagnostics.TraceSource> class is used by applications to produce traces that can be associated with the application.</span></span> <span data-ttu-id="80057-104"><xref:System.Diagnostics.TraceSource> poskytuje metody trasování, které vám umožní snadno trasovat události, trasovat data a vydávat informační trasování.</span><span class="sxs-lookup"><span data-stu-id="80057-104"><xref:System.Diagnostics.TraceSource> provides tracing methods that allow you to easily trace events, trace data, and issue informational traces.</span></span> <span data-ttu-id="80057-105">Trasování výstupu z <xref:System.Diagnostics.TraceSource> může být vytvořeno a inicializováno s nebo bez použití konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="80057-105">Trace output from <xref:System.Diagnostics.TraceSource> can be created and initialized with or without the use of configuration files.</span></span> <span data-ttu-id="80057-106">Toto téma obsahuje pokyny pro obě možnosti.</span><span class="sxs-lookup"><span data-stu-id="80057-106">This topic provides instructions for both options.</span></span> <span data-ttu-id="80057-107">Doporučujeme však použít konfigurační soubory pro usnadnění opětovné konfigurace trasování vyprodukované zdroji trasování za běhu.</span><span class="sxs-lookup"><span data-stu-id="80057-107">However, we recommend that you use configuration files to facilitate the reconfiguration of the traces produced by trace sources at run time.</span></span>  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a><span data-ttu-id="80057-108">Vytvoření a Inicializace zdroje trasování pomocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="80057-108">To create and initialize a trace source using a configuration file</span></span>  
  
1. <span data-ttu-id="80057-109">Vytvořte projekt konzolové aplikace Visual Studio a nahraďte zadaný kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="80057-109">Create a Visual Studio console application project and replace the supplied code with the following code.</span></span> <span data-ttu-id="80057-110">Tento kód protokoluje chyby a upozornění a vypíše některé z nich do konzoly a některé z nich do souboru myListener, který je vytvořen pomocí položek v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="80057-110">This code logs errors and warnings and outputs some of them to the console, and some of them to the myListener file that is created by the entries in the configuration file.</span></span>  
  
     [!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]
     [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]  
  
2. <span data-ttu-id="80057-111">Přidání konfiguračního souboru aplikace, pokud jeden není uveden do projektu pro inicializaci zdroje trasování s názvem `TraceSourceApp` v příkladu kódu v kroku 1.</span><span class="sxs-lookup"><span data-stu-id="80057-111">Add an application configuration file, if one is not present, to the project to initialize the trace source named `TraceSourceApp` in the code example in step 1.</span></span>  
  
3. <span data-ttu-id="80057-112">Nahraďte výchozí obsah souboru konfigurace následujícím nastavením pro inicializaci naslouchacího procesu trasování konzoly a naslouchacího procesu text zapisovač trasování pro zdroj trasování, který byl vytvořen v kroku 1.</span><span class="sxs-lookup"><span data-stu-id="80057-112">Replace the default configuration file content with the following settings to initialize a console trace listener and a text writer trace listener for the trace source that was created in step 1.</span></span>  
  
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
                  initializeData="Error"/>  
              </add>  
              <add name="myListener"/>  
              <remove name="Default"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="sourceSwitch" value="Error"/>  
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
  
     <span data-ttu-id="80057-113">Kromě konfigurace posluchačů trasování, konfigurační soubor vytvoří filtry pro oba posluchače a vytvoří zdroj přepínače pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="80057-113">In addition to configuring the trace listeners, the configuration file creates filters for both listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="80057-114">Pro přidávání posluchačů trasování jsou uvedeny dvě metody: Přidání posluchače přímo ke zdroji trasování a přidání posluchače do sdílené kolekce posluchačů a následné přidání podle názvu do zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="80057-114">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="80057-115">Filtry identifikované pro dva naslouchací procesy jsou inicializovány s jinými zdrojovými úrovněmi.</span><span class="sxs-lookup"><span data-stu-id="80057-115">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="80057-116">Výsledkem je některé zprávy jsou zapisovány pouze jedním ze dvou posluchačů.</span><span class="sxs-lookup"><span data-stu-id="80057-116">This results in some messages being written by only one of the two listeners.</span></span>  
  
     <span data-ttu-id="80057-117">Konfigurační soubor inicializuje nastavení pro zdroj trasování v době, kdy je aplikace inicializována.</span><span class="sxs-lookup"><span data-stu-id="80057-117">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="80057-118">Aplikace můžete dynamicky měnit vlastnosti nastavením konfiguračního souboru pro přepsání jakéhokoli nastavení zadaného uživatelem.</span><span class="sxs-lookup"><span data-stu-id="80057-118">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span> <span data-ttu-id="80057-119">Můžete například chtít zajistit, aby kritické zprávy byly odesílány vždy do textového souboru, bez ohledu na aktuální nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="80057-119">For example, you might want to ensure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span> <span data-ttu-id="80057-120">Příklad kódu ukazuje, jak přepsat nastavení konfiguračního souboru k zajištění, aby kritické zprávy se zobrazují pro posluchače trasování.</span><span class="sxs-lookup"><span data-stu-id="80057-120">The example code demonstrates how to override configuration file settings to ensure that critical messages are output to the trace listeners.</span></span>  
  
     <span data-ttu-id="80057-121">Změna nastavení konfiguračních souborů při provádění aplikace nezmění výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="80057-121">Changing the configuration file settings while the application is executing does not change the initial settings.</span></span> <span data-ttu-id="80057-122">Chcete-li změnit nastavení, musíte restartovat aplikaci nebo programově aktualizovat aplikace pomocí <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="80057-122">To change the settings, you must either restart the application or programmatically refresh the application by using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span>  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a><span data-ttu-id="80057-123">Inicializace zdrojů trasování, posluchačů a filtrů bez konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="80057-123">To initialize trace sources, listeners, and filters without a configuration file</span></span>  
  
-   <span data-ttu-id="80057-124">Použijte následující příklad kódu povolíte trasování prostřednictvím zdroje trasování bez použití konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="80057-124">Use the following example code to enable tracing through a trace source without using a configuration file.</span></span> <span data-ttu-id="80057-125">Toto není doporučený postup, ale mohou nastat okolnosti, ve kterých nechcete záviset na konfiguračních souborech k zajištění sledování.</span><span class="sxs-lookup"><span data-stu-id="80057-125">This is not a recommended practice, but there may be circumstances in which you do not want to depend on configuration files to ensure tracing.</span></span>  
  
     [!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]
     [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="80057-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="80057-126">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [<span data-ttu-id="80057-127">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="80057-127">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
