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
ms.openlocfilehash: eeccad44bd2719a3cb2a721ba4e32a7bf477636f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174729"
---
# <a name="how-to-create-and-initialize-trace-sources"></a><span data-ttu-id="0e7d1-102">Postupy: Vytváření a inicializace zdrojů trasování</span><span class="sxs-lookup"><span data-stu-id="0e7d1-102">How to: Create and Initialize Trace Sources</span></span>
<span data-ttu-id="0e7d1-103">Třída <xref:System.Diagnostics.TraceSource> se používá aplikace k výrobě trasování, které mohou být přidruženy k aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0e7d1-103">The <xref:System.Diagnostics.TraceSource> class is used by applications to produce traces that can be associated with the application.</span></span> <span data-ttu-id="0e7d1-104"><xref:System.Diagnostics.TraceSource>Poskytuje metody trasování, které umožňují snadno sledovat události, trasování dat a vydávat informační trasování.</span><span class="sxs-lookup"><span data-stu-id="0e7d1-104"><xref:System.Diagnostics.TraceSource> provides tracing methods that allow you to easily trace events, trace data, and issue informational traces.</span></span> <span data-ttu-id="0e7d1-105">Výstup trasování z <xref:System.Diagnostics.TraceSource> lze vytvořit a inicializovat s nebo bez použití konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="0e7d1-105">Trace output from <xref:System.Diagnostics.TraceSource> can be created and initialized with or without the use of configuration files.</span></span> <span data-ttu-id="0e7d1-106">Toto téma obsahuje pokyny pro obě možnosti.</span><span class="sxs-lookup"><span data-stu-id="0e7d1-106">This topic provides instructions for both options.</span></span> <span data-ttu-id="0e7d1-107">Doporučujeme však použít konfigurační soubory k usnadnění rekonfigurace trasování produkovaných zdroji trasování za běhu.</span><span class="sxs-lookup"><span data-stu-id="0e7d1-107">However, we recommend that you use configuration files to facilitate the reconfiguration of the traces produced by trace sources at run time.</span></span>  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a><span data-ttu-id="0e7d1-108">Vytvoření a inicializaci zdroje trasování pomocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="0e7d1-108">To create and initialize a trace source using a configuration file</span></span>  
  
1. <span data-ttu-id="0e7d1-109">Vytvořte projekt aplikace konzoly Visual Studio (.NET Framework) a nahraďte dodaný kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="0e7d1-109">Create a Visual Studio console application project (.NET Framework) and replace the supplied code with the following code.</span></span> <span data-ttu-id="0e7d1-110">Tento kód protokoluje chyby a upozornění a výstupy některé z nich do konzoly a některé z nich do souboru myListener, který je vytvořen položky v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="0e7d1-110">This code logs errors and warnings and outputs some of them to the console, and some of them to the myListener file that is created by the entries in the configuration file.</span></span>  
  
     [!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]
     [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]  
  
2. <span data-ttu-id="0e7d1-111">Přidejte konfigurační soubor aplikace, pokud není k dispozici, do `TraceSourceApp` projektu inicializovat zdroj trasování pojmenovaný v příkladu kódu v kroku 1.</span><span class="sxs-lookup"><span data-stu-id="0e7d1-111">Add an application configuration file, if one is not present, to the project to initialize the trace source named `TraceSourceApp` in the code example in step 1.</span></span>  
  
3. <span data-ttu-id="0e7d1-112">Nahraďte výchozí obsah konfiguračního souboru následujícími nastaveními pro inicializaci posluchače trasování konzoly a posluchače trasování zapisovače textu pro zdroj trasování, který byl vytvořen v kroku 1.</span><span class="sxs-lookup"><span data-stu-id="0e7d1-112">Replace the default configuration file content with the following settings to initialize a console trace listener and a text writer trace listener for the trace source that was created in step 1.</span></span>  
  
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
  
     <span data-ttu-id="0e7d1-113">Kromě konfigurace posluchačů trasování konfigurační soubor vytvoří filtry pro oba posluchače a vytvoří zdrojový přepínač pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="0e7d1-113">In addition to configuring the trace listeners, the configuration file creates filters for both listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="0e7d1-114">Dvě techniky jsou zobrazeny pro přidání naslouchací procesy trasování: přidání posluchače přímo do zdroje trasování a přidání posluchače do sdílené posluchače kolekce a potom jej přidat podle názvu do zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="0e7d1-114">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="0e7d1-115">Filtry určené pro dva naslouchací procesy jsou inicializovány s různými zdrojovými úrovněmi.</span><span class="sxs-lookup"><span data-stu-id="0e7d1-115">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="0e7d1-116">To má za následek některé zprávy zapisovány pouze jeden ze dvou posluchačů.</span><span class="sxs-lookup"><span data-stu-id="0e7d1-116">This results in some messages being written by only one of the two listeners.</span></span>  
  
     <span data-ttu-id="0e7d1-117">Konfigurační soubor inicializuje nastavení zdroje trasování v době, kdy je aplikace inicializována.</span><span class="sxs-lookup"><span data-stu-id="0e7d1-117">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="0e7d1-118">Aplikace může dynamicky změnit vlastnosti nastavené konfiguračním souborem tak, aby přepsaly všechna nastavení určená uživatelem.</span><span class="sxs-lookup"><span data-stu-id="0e7d1-118">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span> <span data-ttu-id="0e7d1-119">Můžete například chtít zajistit, aby kritické zprávy byly vždy odesílány do textového souboru bez ohledu na aktuální nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="0e7d1-119">For example, you might want to ensure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span> <span data-ttu-id="0e7d1-120">Ukázkový kód ukazuje, jak přepsat nastavení konfiguračního souboru, aby bylo zajištěno, že kritické zprávy jsou výstupem na posluchače trasování.</span><span class="sxs-lookup"><span data-stu-id="0e7d1-120">The example code demonstrates how to override configuration file settings to ensure that critical messages are output to the trace listeners.</span></span>  
  
     <span data-ttu-id="0e7d1-121">Změna nastavení konfiguračního souboru při provádění aplikace nezmění počáteční nastavení.</span><span class="sxs-lookup"><span data-stu-id="0e7d1-121">Changing the configuration file settings while the application is executing does not change the initial settings.</span></span> <span data-ttu-id="0e7d1-122">Chcete-li změnit nastavení, musíte aplikaci restartovat nebo programově <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> aktualizovat aplikaci pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="0e7d1-122">To change the settings, you must either restart the application or programmatically refresh the application by using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span>  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a><span data-ttu-id="0e7d1-123">Inicializaci zdrojů trasování, naslouchacích procesů a filtrů bez konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="0e7d1-123">To initialize trace sources, listeners, and filters without a configuration file</span></span>  
  
- <span data-ttu-id="0e7d1-124">Pomocí následujícího ukázkového kódu povolte trasování přes zdroj trasování bez použití konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="0e7d1-124">Use the following example code to enable tracing through a trace source without using a configuration file.</span></span> <span data-ttu-id="0e7d1-125">Toto není doporučený postup, ale mohou nastaly okolnosti, za kterých nechcete být závislí na konfiguračních souborech, abyste zajistili trasování.</span><span class="sxs-lookup"><span data-stu-id="0e7d1-125">This is not a recommended practice, but there may be circumstances in which you do not want to depend on configuration files to ensure tracing.</span></span>  
  
     [!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]
     [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0e7d1-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e7d1-126">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [<span data-ttu-id="0e7d1-127">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="0e7d1-127">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
