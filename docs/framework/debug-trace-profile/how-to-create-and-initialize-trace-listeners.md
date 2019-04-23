---
title: 'Postupy: Vytváření a inicializace naslouchacích procesů trasování'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- initializing trace listeners
- trace listeners, creating
- trace listeners, initializing
- tracing [.NET Framework], trace listeners
- logs, trace listeners
ms.assetid: 21726de1-61ee-4fdc-9dd0-3be49324d066
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ea5db2ba1060479f55bbd7f67266d36085a2535f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979886"
---
# <a name="how-to-create-and-initialize-trace-listeners"></a><span data-ttu-id="a7ab9-102">Postupy: Vytváření a inicializace naslouchacích procesů trasování</span><span class="sxs-lookup"><span data-stu-id="a7ab9-102">How to: Create and Initialize Trace Listeners</span></span>

<span data-ttu-id="a7ab9-103"><xref:System.Diagnostics.Debug?displayProperty=nameWithType> a <xref:System.Diagnostics.Trace?displayProperty=nameWithType> třídy odesílání zpráv do objektů nazývaných naslouchacích procesů, které příjem a zpracování těchto zpráv.</span><span class="sxs-lookup"><span data-stu-id="a7ab9-103">The <xref:System.Diagnostics.Debug?displayProperty=nameWithType> and <xref:System.Diagnostics.Trace?displayProperty=nameWithType> classes send messages to objects called listeners that receive and process these messages.</span></span> <span data-ttu-id="a7ab9-104">Jeden takový naslouchací proces <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, je automaticky vytvořen a inicializován při zapnutém trasování a ladění.</span><span class="sxs-lookup"><span data-stu-id="a7ab9-104">One such listener, the <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, is automatically created and initialized when tracing or debugging is enabled.</span></span> <span data-ttu-id="a7ab9-105">Chcete-li <xref:System.Diagnostics.Trace> nebo <xref:System.Diagnostics.Debug> výstup přesměrováni na jakékoli další zdroje, musíte vytvořit a inicializovat naslouchací procesy další trasování.</span><span class="sxs-lookup"><span data-stu-id="a7ab9-105">If you want <xref:System.Diagnostics.Trace> or <xref:System.Diagnostics.Debug> output to be directed to any additional sources, you must create and initialize additional trace listeners.</span></span>

<span data-ttu-id="a7ab9-106">Naslouchací procesy, které vytvoříte by měly odrážet potřeby vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="a7ab9-106">The listeners you create should reflect your application's needs.</span></span> <span data-ttu-id="a7ab9-107">Například pokud chcete text záznam všech výstupu trasování, vytvořit <xref:System.Diagnostics.TextWriterTraceListener> naslouchací proces, který zapisuje veškerý výstup do nového textového souboru, je-li povolena.</span><span class="sxs-lookup"><span data-stu-id="a7ab9-107">For example, if you want a text record of all trace output, create a <xref:System.Diagnostics.TextWriterTraceListener> listener, which writes all output to a new text file when it is enabled.</span></span> <span data-ttu-id="a7ab9-108">Na druhé straně, pokud chcete zobrazit výstup pouze při spuštění aplikace, vytvořte <xref:System.Diagnostics.ConsoleTraceListener> naslouchací proces, který směruje veškerý výstup do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="a7ab9-108">On the other hand, if you want to view output only during application execution, create a <xref:System.Diagnostics.ConsoleTraceListener> listener, which directs all output to a console window.</span></span> <span data-ttu-id="a7ab9-109"><xref:System.Diagnostics.EventLogTraceListener> Může směrovat výstup trasování do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="a7ab9-109">The <xref:System.Diagnostics.EventLogTraceListener> can direct trace output to an event log.</span></span> <span data-ttu-id="a7ab9-110">Další informace najdete v tématu [naslouchacích procesů trasování](../../../docs/framework/debug-trace-profile/trace-listeners.md).</span><span class="sxs-lookup"><span data-stu-id="a7ab9-110">For more information, see [Trace Listeners](../../../docs/framework/debug-trace-profile/trace-listeners.md).</span></span>

<span data-ttu-id="a7ab9-111">Můžete vytvořit naslouchací procesy trasování v [konfiguračního souboru aplikace](../../../docs/framework/configure-apps/index.md) nebo ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="a7ab9-111">You can create trace listeners in an [application configuration file](../../../docs/framework/configure-apps/index.md) or in your code.</span></span> <span data-ttu-id="a7ab9-112">Doporučujeme vám používat konfigurační soubory aplikace, protože umožňují přidat, upravit nebo odebrat naslouchacích procesů trasování bez nutnosti měnit kód.</span><span class="sxs-lookup"><span data-stu-id="a7ab9-112">We recommend the use of application configuration files, because they let you add, modify, or remove trace listeners without having to change your code.</span></span>

### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a><span data-ttu-id="a7ab9-113">Vytvoření a použití naslouchací proces trasování pomocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="a7ab9-113">To create and use a trace listener by using a configuration file</span></span>

1. <span data-ttu-id="a7ab9-114">Deklarujte vašemu naslouchacímu procesu trasování v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="a7ab9-114">Declare your trace listener in your application configuration file.</span></span> <span data-ttu-id="a7ab9-115">Pokud naslouchací proces, který vytváříte vyžaduje další objekty, a je deklarujte.</span><span class="sxs-lookup"><span data-stu-id="a7ab9-115">If the listener you are creating requires any other objects, declare them as well.</span></span> <span data-ttu-id="a7ab9-116">Následující příklad ukazuje, jak vytvořit naslouchací proces nazvaný `myListener` , která zapisuje do textového souboru `TextWriterOutput.log`.</span><span class="sxs-lookup"><span data-stu-id="a7ab9-116">The following example shows how to create a listener called `myListener` that writes to the text file `TextWriterOutput.log`.</span></span>

    ```xml
    <configuration>
      <system.diagnostics>
        <trace autoflush="false" indentsize="4">
          <listeners>
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="TextWriterOutput.log" />
            <remove name="Default" />
          </listeners>
        </trace>
      </system.diagnostics>
    </configuration>
    ```

2. <span data-ttu-id="a7ab9-117">Použití <xref:System.Diagnostics.Trace> třídy v kódu k zápisu zprávy pro posluchače trasování.</span><span class="sxs-lookup"><span data-stu-id="a7ab9-117">Use the <xref:System.Diagnostics.Trace> class in your code to write a message to the trace listeners.</span></span>

    ```vb
    Trace.TraceInformation("Test message.")
    ' You must close or flush the trace to empty the output buffer.
    Trace.Flush()
    ```

    ```csharp
    Trace.TraceInformation("Test message.");
    // You must close or flush the trace to empty the output buffer.
    Trace.Flush();
    ```

### <a name="to-create-and-use-a-trace-listener-in-code"></a><span data-ttu-id="a7ab9-118">Vytvoření a použití naslouchací proces trasování v kódu</span><span class="sxs-lookup"><span data-stu-id="a7ab9-118">To create and use a trace listener in code</span></span>

- <span data-ttu-id="a7ab9-119">Přidat naslouchací proces trasování do <xref:System.Diagnostics.Trace.Listeners%2A> kolekce a odeslat informace o pro posluchače trasování.</span><span class="sxs-lookup"><span data-stu-id="a7ab9-119">Add the trace listener to the <xref:System.Diagnostics.Trace.Listeners%2A> collection and send trace information to the listeners.</span></span>

    ```vb
    Trace.Listeners.Add(New TextWriterTraceListener("TextWriterOutput.log", "myListener"))
    Trace.TraceInformation("Test message.")
    ' You must close or flush the trace to empty the output buffer.
    Trace.Flush()
    ```

    ```csharp
    Trace.Listeners.Add(new TextWriterTraceListener("TextWriterOutput.log", "myListener"));
    Trace.TraceInformation("Test message.");
    // You must close or flush the trace to empty the output buffer.
    Trace.Flush();
    ```

    <span data-ttu-id="a7ab9-120">\- nebo –</span><span class="sxs-lookup"><span data-stu-id="a7ab9-120">\- or -</span></span>

- <span data-ttu-id="a7ab9-121">Pokud nechcete, aby vašemu naslouchacímu procesu pro příjem výstup trasování, nepřidávejte tak, <xref:System.Diagnostics.Trace.Listeners%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="a7ab9-121">If you do not want your listener to receive trace output, do not add it to the <xref:System.Diagnostics.Trace.Listeners%2A> collection.</span></span> <span data-ttu-id="a7ab9-122">Můžete generovat výstup prostřednictvím nezávisle na naslouchací proces <xref:System.Diagnostics.Trace.Listeners%2A> kolekce voláním naslouchacího procesu vlastní výstupu metody.</span><span class="sxs-lookup"><span data-stu-id="a7ab9-122">You can emit output through a listener independent of the <xref:System.Diagnostics.Trace.Listeners%2A> collection by calling the listener's own output methods.</span></span> <span data-ttu-id="a7ab9-123">Následující příklad ukazuje, jak napsat řádek na naslouchací proces, který není součástí <xref:System.Diagnostics.Trace.Listeners%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="a7ab9-123">The following example shows how to write a line to a listener that is not in the <xref:System.Diagnostics.Trace.Listeners%2A> collection.</span></span>

    ```vb
    Dim myListener As New TextWriterTraceListener("TextWriterOutput.log", "myListener")
    myListener.WriteLine("Test message.")
    ' You must close or flush the trace listener to empty the output buffer.
    myListener.Flush()
    ```

    ```csharp
    TextWriterTraceListener myListener = new TextWriterTraceListener("TextWriterOutput.log", "myListener");
    myListener.WriteLine("Test message.");
    // You must close or flush the trace listener to empty the output buffer.
    myListener.Flush();
    ```

## <a name="see-also"></a><span data-ttu-id="a7ab9-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a7ab9-124">See also</span></span>

- [<span data-ttu-id="a7ab9-125">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="a7ab9-125">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [<span data-ttu-id="a7ab9-126">Přepínače trasování</span><span class="sxs-lookup"><span data-stu-id="a7ab9-126">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="a7ab9-127">Postupy: Přidání příkazů trasování do kódu aplikace</span><span class="sxs-lookup"><span data-stu-id="a7ab9-127">How to: Add Trace Statements to Application Code</span></span>](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="a7ab9-128">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="a7ab9-128">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
