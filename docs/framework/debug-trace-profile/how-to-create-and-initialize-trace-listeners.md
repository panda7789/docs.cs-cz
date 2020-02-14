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
ms.openlocfilehash: ce0df0af32d6798c89c8db6761d18febc1c398bb
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217445"
---
# <a name="how-to-create-and-initialize-trace-listeners"></a><span data-ttu-id="67cf4-102">Postupy: Vytváření a inicializace naslouchacích procesů trasování</span><span class="sxs-lookup"><span data-stu-id="67cf4-102">How to: Create and Initialize Trace Listeners</span></span>

<span data-ttu-id="67cf4-103">Třídy <xref:System.Diagnostics.Debug?displayProperty=nameWithType> a <xref:System.Diagnostics.Trace?displayProperty=nameWithType> odesílají zprávy do objektů nazývaných naslouchací procesy, které přijímají a zpracovávají tyto zprávy.</span><span class="sxs-lookup"><span data-stu-id="67cf4-103">The <xref:System.Diagnostics.Debug?displayProperty=nameWithType> and <xref:System.Diagnostics.Trace?displayProperty=nameWithType> classes send messages to objects called listeners that receive and process these messages.</span></span> <span data-ttu-id="67cf4-104">Jeden takový naslouchací proces, <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, je automaticky vytvořen a inicializován v případě, že je povoleno trasování nebo ladění.</span><span class="sxs-lookup"><span data-stu-id="67cf4-104">One such listener, the <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, is automatically created and initialized when tracing or debugging is enabled.</span></span> <span data-ttu-id="67cf4-105">Pokud chcete, aby byl výstup <xref:System.Diagnostics.Trace> nebo <xref:System.Diagnostics.Debug> směrován do dalších zdrojů, je nutné vytvořit a inicializovat další naslouchací procesy trasování.</span><span class="sxs-lookup"><span data-stu-id="67cf4-105">If you want <xref:System.Diagnostics.Trace> or <xref:System.Diagnostics.Debug> output to be directed to any additional sources, you must create and initialize additional trace listeners.</span></span>

<span data-ttu-id="67cf4-106">Naslouchací procesy, které vytvoříte, by měly odpovídat potřebám vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="67cf4-106">The listeners you create should reflect your application's needs.</span></span> <span data-ttu-id="67cf4-107">Například pokud chcete textový záznam všech výstupů trasování, vytvořte <xref:System.Diagnostics.TextWriterTraceListener> naslouchací proces, který zapíše veškerý výstup do nového textového souboru, pokud je povolen.</span><span class="sxs-lookup"><span data-stu-id="67cf4-107">For example, if you want a text record of all trace output, create a <xref:System.Diagnostics.TextWriterTraceListener> listener, which writes all output to a new text file when it is enabled.</span></span> <span data-ttu-id="67cf4-108">Na druhé straně, pokud chcete zobrazit výstup pouze během provádění aplikace, vytvořte <xref:System.Diagnostics.ConsoleTraceListener> naslouchací proces, který přesměruje výstup do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="67cf4-108">On the other hand, if you want to view output only during application execution, create a <xref:System.Diagnostics.ConsoleTraceListener> listener, which directs all output to a console window.</span></span> <span data-ttu-id="67cf4-109"><xref:System.Diagnostics.EventLogTraceListener> může směrovat výstup trasování do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="67cf4-109">The <xref:System.Diagnostics.EventLogTraceListener> can direct trace output to an event log.</span></span> <span data-ttu-id="67cf4-110">Další informace naleznete v tématu [Trace Listeners](trace-listeners.md).</span><span class="sxs-lookup"><span data-stu-id="67cf4-110">For more information, see [Trace Listeners](trace-listeners.md).</span></span>

<span data-ttu-id="67cf4-111">Naslouchací procesy trasování lze vytvořit v [konfiguračním souboru aplikace](../configure-apps/index.md) nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="67cf4-111">You can create trace listeners in an [application configuration file](../configure-apps/index.md) or in your code.</span></span> <span data-ttu-id="67cf4-112">Doporučujeme použít konfigurační soubory aplikace, protože umožňují přidat, upravit nebo odebrat naslouchací procesy trasování bez nutnosti měnit kód.</span><span class="sxs-lookup"><span data-stu-id="67cf4-112">We recommend the use of application configuration files, because they let you add, modify, or remove trace listeners without having to change your code.</span></span>

### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a><span data-ttu-id="67cf4-113">Vytvoření a použití naslouchacího procesu trasování pomocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="67cf4-113">To create and use a trace listener by using a configuration file</span></span>

1. <span data-ttu-id="67cf4-114">Deklarujte naslouchací proces trasování v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="67cf4-114">Declare your trace listener in your application configuration file.</span></span> <span data-ttu-id="67cf4-115">Pokud naslouchací proces, který vytváříte, vyžaduje jiné objekty, deklarujte je také.</span><span class="sxs-lookup"><span data-stu-id="67cf4-115">If the listener you are creating requires any other objects, declare them as well.</span></span> <span data-ttu-id="67cf4-116">Následující příklad ukazuje, jak vytvořit naslouchací proces nazvaný `myListener`, který zapisuje do textového souboru `TextWriterOutput.log`.</span><span class="sxs-lookup"><span data-stu-id="67cf4-116">The following example shows how to create a listener called `myListener` that writes to the text file `TextWriterOutput.log`.</span></span>

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

2. <span data-ttu-id="67cf4-117">Použijte třídu <xref:System.Diagnostics.Trace> v kódu k zápisu zprávy do posluchačů trasování.</span><span class="sxs-lookup"><span data-stu-id="67cf4-117">Use the <xref:System.Diagnostics.Trace> class in your code to write a message to the trace listeners.</span></span>

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

### <a name="to-create-and-use-a-trace-listener-in-code"></a><span data-ttu-id="67cf4-118">Vytvoření a použití naslouchacího procesu trasování v kódu</span><span class="sxs-lookup"><span data-stu-id="67cf4-118">To create and use a trace listener in code</span></span>

- <span data-ttu-id="67cf4-119">Přidejte naslouchací proces trasování do kolekce <xref:System.Diagnostics.Trace.Listeners%2A> a odešlete trasovací informace do posluchačů.</span><span class="sxs-lookup"><span data-stu-id="67cf4-119">Add the trace listener to the <xref:System.Diagnostics.Trace.Listeners%2A> collection and send trace information to the listeners.</span></span>

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

    <span data-ttu-id="67cf4-120">\- nebo-</span><span class="sxs-lookup"><span data-stu-id="67cf4-120">\- or -</span></span>

- <span data-ttu-id="67cf4-121">Pokud nechcete, aby naslouchací proces přijímal výstup trasování, nepřidávejte ho do kolekce <xref:System.Diagnostics.Trace.Listeners%2A>.</span><span class="sxs-lookup"><span data-stu-id="67cf4-121">If you do not want your listener to receive trace output, do not add it to the <xref:System.Diagnostics.Trace.Listeners%2A> collection.</span></span> <span data-ttu-id="67cf4-122">Můžete vygenerovat výstup pomocí naslouchacího procesu nezávisle na kolekci <xref:System.Diagnostics.Trace.Listeners%2A> voláním metod vlastního výstupu naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="67cf4-122">You can emit output through a listener independent of the <xref:System.Diagnostics.Trace.Listeners%2A> collection by calling the listener's own output methods.</span></span> <span data-ttu-id="67cf4-123">Následující příklad ukazuje, jak zapsat řádek do naslouchacího procesu, který není v kolekci <xref:System.Diagnostics.Trace.Listeners%2A>.</span><span class="sxs-lookup"><span data-stu-id="67cf4-123">The following example shows how to write a line to a listener that is not in the <xref:System.Diagnostics.Trace.Listeners%2A> collection.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="67cf4-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="67cf4-124">See also</span></span>

- [<span data-ttu-id="67cf4-125">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="67cf4-125">Trace Listeners</span></span>](trace-listeners.md)
- [<span data-ttu-id="67cf4-126">Přepínače trasování</span><span class="sxs-lookup"><span data-stu-id="67cf4-126">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="67cf4-127">Postupy: Přidání příkazů trasování do kódu aplikace</span><span class="sxs-lookup"><span data-stu-id="67cf4-127">How to: Add Trace Statements to Application Code</span></span>](how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="67cf4-128">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="67cf4-128">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
