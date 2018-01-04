---
title: "Postupy: Vytváření a inicializace naslouchacích procesů trasování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ebc50e4075a5793c344cbc017eb60247c1c8774
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-and-initialize-trace-listeners"></a><span data-ttu-id="4be6a-102">Postupy: Vytváření a inicializace naslouchacích procesů trasování</span><span class="sxs-lookup"><span data-stu-id="4be6a-102">How to: Create and Initialize Trace Listeners</span></span>
<span data-ttu-id="4be6a-103"><xref:System.Diagnostics.Debug?displayProperty=nameWithType> a <xref:System.Diagnostics.Trace?displayProperty=nameWithType> třídy odesílat zprávy objektů názvem naslouchací procesy, které přijímat a zpracovávat tyto zprávy.</span><span class="sxs-lookup"><span data-stu-id="4be6a-103">The <xref:System.Diagnostics.Debug?displayProperty=nameWithType> and <xref:System.Diagnostics.Trace?displayProperty=nameWithType> classes send messages to objects called listeners that receive and process these messages.</span></span> <span data-ttu-id="4be6a-104">Jeden takový naslouchací proces, <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, je automaticky vytvořen a inicializován při zapnutém trasování nebo ladění.</span><span class="sxs-lookup"><span data-stu-id="4be6a-104">One such listener, the <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, is automatically created and initialized when tracing or debugging is enabled.</span></span> <span data-ttu-id="4be6a-105">Chcete-li <xref:System.Diagnostics.Trace> nebo <xref:System.Diagnostics.Debug> výstup přesměrováni na žádné další zdroje, musíte vytvořit a inicializace naslouchacích procesů trasování Další.</span><span class="sxs-lookup"><span data-stu-id="4be6a-105">If you want <xref:System.Diagnostics.Trace> or <xref:System.Diagnostics.Debug> output to be directed to any additional sources, you must create and initialize additional trace listeners.</span></span>  
  
 <span data-ttu-id="4be6a-106">Naslouchací procesy, které vytvoříte by měla odpovídat potřebám vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="4be6a-106">The listeners you create should reflect your application's needs.</span></span> <span data-ttu-id="4be6a-107">Například pokud chcete text záznam všech výstup trasování, vytvořit <xref:System.Diagnostics.TextWriterTraceListener> naslouchací proces, který zapisuje veškerý výstup do nového textového souboru, pokud je povolený.</span><span class="sxs-lookup"><span data-stu-id="4be6a-107">For example, if you want a text record of all trace output, create a <xref:System.Diagnostics.TextWriterTraceListener> listener, which writes all output to a new text file when it is enabled.</span></span> <span data-ttu-id="4be6a-108">Na druhé straně, pokud chcete zobrazit výstup pouze během provádění aplikací, vytvořte <xref:System.Diagnostics.ConsoleTraceListener> naslouchací proces, který přesměruje veškerý výstup do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="4be6a-108">On the other hand, if you want to view output only during application execution, create a <xref:System.Diagnostics.ConsoleTraceListener> listener, which directs all output to a console window.</span></span> <span data-ttu-id="4be6a-109"><xref:System.Diagnostics.EventLogTraceListener> Můžete přesměrujte výstup trasování do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="4be6a-109">The <xref:System.Diagnostics.EventLogTraceListener> can direct trace output to an event log.</span></span> <span data-ttu-id="4be6a-110">Další informace najdete v tématu [trasování – moduly naslouchání](../../../docs/framework/debug-trace-profile/trace-listeners.md).</span><span class="sxs-lookup"><span data-stu-id="4be6a-110">For more information, see [Trace Listeners](../../../docs/framework/debug-trace-profile/trace-listeners.md).</span></span>  
  
 <span data-ttu-id="4be6a-111">Můžete vytvořit naslouchací procesy trasování v [konfigurační soubor aplikace](../../../docs/framework/configure-apps/index.md) nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="4be6a-111">You can create trace listeners in an [application configuration file](../../../docs/framework/configure-apps/index.md) or in your code.</span></span> <span data-ttu-id="4be6a-112">Doporučujeme použití konfigurační soubory aplikace, protože umožňují přidávat, upravovat nebo odebírat trasování – moduly naslouchání bez nutnosti měnit kód.</span><span class="sxs-lookup"><span data-stu-id="4be6a-112">We recommend the use of application configuration files, because they let you add, modify, or remove trace listeners without having to change your code.</span></span>  
  
### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a><span data-ttu-id="4be6a-113">Vytváření a používání naslouchací pomocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="4be6a-113">To create and use a trace listener by using a configuration file</span></span>  
  
1.  <span data-ttu-id="4be6a-114">Deklarujte vaší naslouchací proces trasování v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="4be6a-114">Declare your trace listener in your application configuration file.</span></span> <span data-ttu-id="4be6a-115">Pokud naslouchací proces, který vytváříte vyžaduje, aby všechny další objekty, deklarujte je také.</span><span class="sxs-lookup"><span data-stu-id="4be6a-115">If the listener you are creating requires any other objects, declare them as well.</span></span> <span data-ttu-id="4be6a-116">Následující příklad ukazuje, jak vytvořit naslouchací proces nazvaný `myListener` který zapisuje do textového souboru `TextWriterOutput.log`.</span><span class="sxs-lookup"><span data-stu-id="4be6a-116">The following example shows how to create a listener called `myListener` that writes to the text file `TextWriterOutput.log`.</span></span>  
  
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
  
2.  <span data-ttu-id="4be6a-117">Použití <xref:System.Diagnostics.Trace> třídy ve vašem kódu zapsat zprávu do naslouchací procesy trasování.</span><span class="sxs-lookup"><span data-stu-id="4be6a-117">Use the <xref:System.Diagnostics.Trace> class in your code to write a message to the trace listeners.</span></span>  
  
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
  
### <a name="to-create-and-use-a-trace-listener-in-code"></a><span data-ttu-id="4be6a-118">Vytváření a používání naslouchací proces trasování v kódu</span><span class="sxs-lookup"><span data-stu-id="4be6a-118">To create and use a trace listener in code</span></span>  
  
-   <span data-ttu-id="4be6a-119">Přidejte naslouchací proces trasování do <xref:System.Diagnostics.Trace.Listeners%2A> shromažďování a odesílání informací naslouchací procesy trasování.</span><span class="sxs-lookup"><span data-stu-id="4be6a-119">Add the trace listener to the <xref:System.Diagnostics.Trace.Listeners%2A> collection and send trace information to the listeners.</span></span>  
  
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
  
     - <span data-ttu-id="4be6a-120">nebo –</span><span class="sxs-lookup"><span data-stu-id="4be6a-120">or -</span></span>  
  
-   <span data-ttu-id="4be6a-121">Pokud nechcete, aby vaše naslouchací proces pro příjem výstup trasování, nepřidávejte jej do <xref:System.Diagnostics.Trace.Listeners%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="4be6a-121">If you do not want your listener to receive trace output, do not add it to the <xref:System.Diagnostics.Trace.Listeners%2A> collection.</span></span> <span data-ttu-id="4be6a-122">Můžete emitování výstup prostřednictvím naslouchací proces nezávisle <xref:System.Diagnostics.Trace.Listeners%2A> kolekce voláním naslouchací proces pro vlastní výstup metody.</span><span class="sxs-lookup"><span data-stu-id="4be6a-122">You can emit output through a listener independent of the <xref:System.Diagnostics.Trace.Listeners%2A> collection by calling the listener's own output methods.</span></span> <span data-ttu-id="4be6a-123">Následující příklad ukazuje, jak napsat řádek pro naslouchací proces, který není součástí <xref:System.Diagnostics.Trace.Listeners%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="4be6a-123">The following example shows how to write a line to a listener that is not in the <xref:System.Diagnostics.Trace.Listeners%2A> collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4be6a-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="4be6a-124">See Also</span></span>  
 [<span data-ttu-id="4be6a-125">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="4be6a-125">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)  
 [<span data-ttu-id="4be6a-126">Přepínače trasování</span><span class="sxs-lookup"><span data-stu-id="4be6a-126">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)  
 [<span data-ttu-id="4be6a-127">Postupy: Přidání příkazů trasování do kódu aplikace</span><span class="sxs-lookup"><span data-stu-id="4be6a-127">How to: Add Trace Statements to Application Code</span></span>](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)  
 [<span data-ttu-id="4be6a-128">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="4be6a-128">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
