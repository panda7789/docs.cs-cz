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
ms.openlocfilehash: 07c4d65e3fb6d61ae5d1b766c70cbb25d54bdc7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386519"
---
# <a name="how-to-create-and-initialize-trace-sources"></a><span data-ttu-id="b61a8-102">Postupy: Vytváření a inicializace zdrojů trasování</span><span class="sxs-lookup"><span data-stu-id="b61a8-102">How to: Create and Initialize Trace Sources</span></span>
<span data-ttu-id="b61a8-103"><xref:System.Diagnostics.TraceSource> Třída se používá aplikace k vytvoření trasování, které může být spojeno s aplikací.</span><span class="sxs-lookup"><span data-stu-id="b61a8-103">The <xref:System.Diagnostics.TraceSource> class is used by applications to produce traces that can be associated with the application.</span></span> <span data-ttu-id="b61a8-104"><xref:System.Diagnostics.TraceSource> poskytuje metody trasování, které vám umožňují snadno události trasování, data trasování a problém informativní trasování.</span><span class="sxs-lookup"><span data-stu-id="b61a8-104"><xref:System.Diagnostics.TraceSource> provides tracing methods that allow you to easily trace events, trace data, and issue informational traces.</span></span> <span data-ttu-id="b61a8-105">Výstup trasování <xref:System.Diagnostics.TraceSource> můžete vytvořit a inicializován s nebo bez použití konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="b61a8-105">Trace output from <xref:System.Diagnostics.TraceSource> can be created and initialized with or without the use of configuration files.</span></span> <span data-ttu-id="b61a8-106">Toto téma obsahuje pokyny pro obě možnosti.</span><span class="sxs-lookup"><span data-stu-id="b61a8-106">This topic provides instructions for both options.</span></span> <span data-ttu-id="b61a8-107">Doporučujeme však používají konfigurační soubory pro usnadnění Rekonfigurace trasování vyprodukované trasování zdrojů za běhu.</span><span class="sxs-lookup"><span data-stu-id="b61a8-107">However, we recommend that you use configuration files to facilitate the reconfiguration of the traces produced by trace sources at run time.</span></span>  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a><span data-ttu-id="b61a8-108">K vytvoření a inicializace zdroj trasování pomocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="b61a8-108">To create and initialize a trace source using a configuration file</span></span>  
  
1.  <span data-ttu-id="b61a8-109">Vytvoření projektu konzolové aplikace Visual Studio a zadaný kód nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="b61a8-109">Create a Visual Studio console application project and replace the supplied code with the following code.</span></span> <span data-ttu-id="b61a8-110">Tento kód protokoly chyb a varování a výstupy některé z nich ke konzole a některá z nich myListener soubor, který byl vytvořený položky v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="b61a8-110">This code logs errors and warnings and outputs some of them to the console, and some of them to the myListener file that is created by the entries in the configuration file.</span></span>  
  
     [!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]
     [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]  
  
2.  <span data-ttu-id="b61a8-111">Přidání konfiguračního souboru aplikace, pokud není přítomný, do projektu se inicializovat zdroj trasování s názvem `TraceSourceApp` v příkladu v kroku 1.</span><span class="sxs-lookup"><span data-stu-id="b61a8-111">Add an application configuration file, if one is not present, to the project to initialize the trace source named `TraceSourceApp` in the code example in step 1.</span></span>  
  
3.  <span data-ttu-id="b61a8-112">Nahraďte obsah souboru výchozí konfiguraci následujících nastavení můžete inicializovat naslouchací proces trasování konzoly a naslouchací zapisovač textu pro trasování zdroj, který byl vytvořen v kroku 1.</span><span class="sxs-lookup"><span data-stu-id="b61a8-112">Replace the default configuration file content with the following settings to initialize a console trace listener and a text writer trace listener for the trace source that was created in step 1.</span></span>  
  
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
  
     <span data-ttu-id="b61a8-113">Kromě konfigurace naslouchací procesy trasování, konfigurační soubor vytvoří filtry pro obě naslouchací procesy a vytvoří přepínač zdroje pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="b61a8-113">In addition to configuring the trace listeners, the configuration file creates filters for both listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="b61a8-114">Pro přidání trasování – moduly naslouchání se zobrazují dvě techniky: Přidání naslouchací proces přímo na zdroj trasování a přidání naslouchací proces ke kolekci sdílené moduly pro naslouchání a následným přidáním podle názvu zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="b61a8-114">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="b61a8-115">Filtry identifikovat pro dva naslouchací procesy jsou inicializovány s jinou zdrojovou úrovněmi.</span><span class="sxs-lookup"><span data-stu-id="b61a8-115">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="b61a8-116">Výsledkem některé zprávy zapisovaný jenom jedna z dva naslouchací procesy.</span><span class="sxs-lookup"><span data-stu-id="b61a8-116">This results in some messages being written by only one of the two listeners.</span></span>  
  
     <span data-ttu-id="b61a8-117">Konfigurační soubor inicializuje nastavení pro zdroj trasování v době, kdy aplikace je inicializován.</span><span class="sxs-lookup"><span data-stu-id="b61a8-117">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="b61a8-118">Aplikace můžete dynamicky měnit vlastnosti nastavit pomocí konfiguračního souboru pro přepsání nastavení zadaný uživatelem.</span><span class="sxs-lookup"><span data-stu-id="b61a8-118">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span> <span data-ttu-id="b61a8-119">Například můžete chtít zajistit kritické jsou vždy odesílání zpráv do textového souboru, bez ohledu na aktuální nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="b61a8-119">For example, you might want to ensure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span> <span data-ttu-id="b61a8-120">Příklad kódu ukazuje, jak k přepsání souboru nastavení konfigurace zajistit, že kritické zprávy se zobrazují naslouchací procesy trasování.</span><span class="sxs-lookup"><span data-stu-id="b61a8-120">The example code demonstrates how to override configuration file settings to ensure that critical messages are output to the trace listeners.</span></span>  
  
     <span data-ttu-id="b61a8-121">Změna souboru nastavení konfigurace, když spouští aplikaci počáteční nastavení nezmění.</span><span class="sxs-lookup"><span data-stu-id="b61a8-121">Changing the configuration file settings while the application is executing does not change the initial settings.</span></span> <span data-ttu-id="b61a8-122">Chcete-li změnit nastavení, musíte aplikaci restartovat nebo prostřednictvím kódu programu obnovit aplikace pomocí <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="b61a8-122">To change the settings, you must either restart the application or programmatically refresh the application by using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span>  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a><span data-ttu-id="b61a8-123">Inicializace zdrojů trasování, naslouchací procesy a filtry bez konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="b61a8-123">To initialize trace sources, listeners, and filters without a configuration file</span></span>  
  
-   <span data-ttu-id="b61a8-124">Použijte následující příklad kódu povolení trasování prostřednictvím zdroj trasování bez použití konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="b61a8-124">Use the following example code to enable tracing through a trace source without using a configuration file.</span></span> <span data-ttu-id="b61a8-125">Toto není doporučený postup, ale může být případech, ve kterých nechcete závisí na konfigurační soubory, aby trasování.</span><span class="sxs-lookup"><span data-stu-id="b61a8-125">This is not a recommended practice, but there may be circumstances in which you do not want to depend on configuration files to ensure tracing.</span></span>  
  
     [!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]
     [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b61a8-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="b61a8-126">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.EventTypeFilter>  
 [<span data-ttu-id="b61a8-127">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="b61a8-127">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
