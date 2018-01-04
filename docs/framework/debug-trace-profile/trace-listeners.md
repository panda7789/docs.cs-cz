---
title: "Naslouchací procesy trasování"
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
- Listener object types
- listeners
- Trace class, listeners
- trace listeners, about trace listeners
- Listeners collection
- trace listeners
- tracing [.NET Framework], trace listeners
- logs, trace listeners
ms.assetid: 444b0d33-67ea-4c36-9e94-79c50f839025
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 042b8a6f7c25c34fc06d5d0bfd4ebce6417b920f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="trace-listeners"></a><span data-ttu-id="d0fbc-102">Naslouchací procesy trasování</span><span class="sxs-lookup"><span data-stu-id="d0fbc-102">Trace Listeners</span></span>
<span data-ttu-id="d0fbc-103">Při použití **trasování**, **ladění** a <xref:System.Diagnostics.TraceSource>, musí mít mechanismus pro shromažďování a záznamem zpráv, které se odesílají.</span><span class="sxs-lookup"><span data-stu-id="d0fbc-103">When using **Trace**, **Debug** and <xref:System.Diagnostics.TraceSource>, you must have a mechanism for collecting and recording the messages that are sent.</span></span> <span data-ttu-id="d0fbc-104">Trasovací zprávy jsou přijímány *naslouchací procesy*.</span><span class="sxs-lookup"><span data-stu-id="d0fbc-104">Trace messages are received by *listeners*.</span></span> <span data-ttu-id="d0fbc-105">Účelem tohoto naslouchací proces je shromažďování, ukládání a směrovat trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="d0fbc-105">The purpose of a listener is to collect, store, and route tracing messages.</span></span> <span data-ttu-id="d0fbc-106">Posluchači přímý výstup trasování příslušný cíli, jako je protokol, okno nebo textový soubor.</span><span class="sxs-lookup"><span data-stu-id="d0fbc-106">Listeners direct the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="d0fbc-107">Moduly pro naslouchání jsou k dispozici **ladění**, **trasování**, a <xref:System.Diagnostics.TraceSource> tříd, z nichž každá může odesílat její výstup do různých objektů naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="d0fbc-107">Listeners are available to the **Debug**, **Trace**, and <xref:System.Diagnostics.TraceSource> classes, each of which can send its output to a variety of listener objects.</span></span> <span data-ttu-id="d0fbc-108">Tady jsou běžně používané předdefinované naslouchací procesy:</span><span class="sxs-lookup"><span data-stu-id="d0fbc-108">The following are the commonly used predefined listeners:</span></span>  
  
-   <span data-ttu-id="d0fbc-109">A <xref:System.Diagnostics.TextWriterTraceListener> přesměruje výstup do instance <xref:System.IO.TextWriter> třídy nebo nic, který je <xref:System.IO.Stream> třídy.</span><span class="sxs-lookup"><span data-stu-id="d0fbc-109">A <xref:System.Diagnostics.TextWriterTraceListener> redirects output to an instance of the <xref:System.IO.TextWriter> class or to anything that is a <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="d0fbc-110">Je také možné zapsat na konzole nebo do souboru, protože se jedná <xref:System.IO.Stream> třídy.</span><span class="sxs-lookup"><span data-stu-id="d0fbc-110">It can also write to the console or to a file, because these are <xref:System.IO.Stream> classes.</span></span>  
  
-   <span data-ttu-id="d0fbc-111"><xref:System.Diagnostics.EventLogTraceListener> Přesměruje výstup do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="d0fbc-111">An <xref:System.Diagnostics.EventLogTraceListener> redirects output to an event log.</span></span>  
  
-   <span data-ttu-id="d0fbc-112">A <xref:System.Diagnostics.DefaultTraceListener> vysílá **zápisu** a **WriteLine** zprávy pro **OutputDebugString** a **Debugger.Log** metoda.</span><span class="sxs-lookup"><span data-stu-id="d0fbc-112">A <xref:System.Diagnostics.DefaultTraceListener> emits **Write** and **WriteLine** messages to the **OutputDebugString** and to the **Debugger.Log** method.</span></span> <span data-ttu-id="d0fbc-113">V sadě Visual Studio to způsobí, že zprávy ladění zobrazí v okně výstupu.</span><span class="sxs-lookup"><span data-stu-id="d0fbc-113">In Visual Studio, this causes the debugging messages to appear in the Output window.</span></span> <span data-ttu-id="d0fbc-114">**Selhání** a k selhání **Assert** zprávy emitování také k **OutputDebugString** rozhraní API systému Windows a **Debugger.Log** metoda a příčina zprávu pole do Zobrazit.</span><span class="sxs-lookup"><span data-stu-id="d0fbc-114">**Fail** and failed **Assert** messages also emit to the **OutputDebugString** Windows API and the **Debugger.Log** method, and also cause a message box to be displayed.</span></span> <span data-ttu-id="d0fbc-115">Toto chování je výchozí chování pro **ladění** a **trasování** zprávy, protože **DefaultTraceListener** je automaticky zahrnuta v každé `Listeners` kolekce a je automaticky zahrnuty pouze naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="d0fbc-115">This behavior is the default behavior for **Debug** and **Trace** messages, because **DefaultTraceListener** is automatically included in every `Listeners` collection and is the only listener automatically included.</span></span>  
  
-   <span data-ttu-id="d0fbc-116">A <xref:System.Diagnostics.ConsoleTraceListener> směruje trasování nebo výstup do standardního výstupního nebo standardní chybový proud ladění.</span><span class="sxs-lookup"><span data-stu-id="d0fbc-116">A <xref:System.Diagnostics.ConsoleTraceListener> directs tracing or debugging output to either the standard output or the standard error stream.</span></span>  
  
-   <span data-ttu-id="d0fbc-117">A <xref:System.Diagnostics.DelimitedListTraceListener> směruje trasování nebo výstup ladění do zapisovače textu, jako je datový proud, nebo do datového proudu, jako je datový proud souboru.</span><span class="sxs-lookup"><span data-stu-id="d0fbc-117">A <xref:System.Diagnostics.DelimitedListTraceListener> directs tracing or debugging output to a text writer, such as a stream writer, or to a stream, such as a file stream.</span></span> <span data-ttu-id="d0fbc-118">Výstup trasování je ve formátu odděleného textu, který používá jako oddělovač určeného <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d0fbc-118">The trace output is in a delimited text format that uses the delimiter specified by the <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> property.</span></span>  
  
-   <span data-ttu-id="d0fbc-119"><xref:System.Diagnostics.XmlWriterTraceListener> Směruje trasování nebo výstup ladění jako data kódovaná XML do <xref:System.IO.TextWriter> nebo <xref:System.IO.Stream>, například <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="d0fbc-119">An <xref:System.Diagnostics.XmlWriterTraceListener> directs tracing or debugging output as XML-encoded data to a <xref:System.IO.TextWriter> or to a <xref:System.IO.Stream>, such as a <xref:System.IO.FileStream>.</span></span>  
  
 <span data-ttu-id="d0fbc-120">Pokud chcete, aby všechny naslouchací proces kromě <xref:System.Diagnostics.DefaultTraceListener> přijímat **ladění**, **trasování** a <xref:System.Diagnostics.TraceSource> výstup, je třeba přidat ji do `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="d0fbc-120">If you want any listener besides the <xref:System.Diagnostics.DefaultTraceListener> to receive **Debug**, **Trace** and <xref:System.Diagnostics.TraceSource> output, you must add it to the `Listeners` collection.</span></span> <span data-ttu-id="d0fbc-121">Další informace najdete v tématu [postupy: vytvoření a inicializace naslouchacích procesů trasování](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) a [postupy: použití třídy TraceSource a filtrů s naslouchacími procesy trasování](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md).</span><span class="sxs-lookup"><span data-stu-id="d0fbc-121">For more information, see [How to: Create and Initialize Trace Listeners](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) and [How to: Use TraceSource and Filters with Trace Listeners](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md).</span></span> <span data-ttu-id="d0fbc-122">Všechny naslouchací proces ve **naslouchací procesy** kolekce získá stejné zprávy z trasování výstupu metody.</span><span class="sxs-lookup"><span data-stu-id="d0fbc-122">Any listener in the **Listeners** collection gets the same messages from the trace output methods.</span></span> <span data-ttu-id="d0fbc-123">Předpokládejme například, můžete nastavit dva naslouchací procesy: **TextWriterTraceListener** a **EventLogTraceListener**.</span><span class="sxs-lookup"><span data-stu-id="d0fbc-123">For example, suppose you set up two listeners: a **TextWriterTraceListener** and an **EventLogTraceListener**.</span></span> <span data-ttu-id="d0fbc-124">Každý naslouchací proces obdrží stejnou zprávu.</span><span class="sxs-lookup"><span data-stu-id="d0fbc-124">Each listener receives the same message.</span></span> <span data-ttu-id="d0fbc-125">**TextWriterTraceListener** by přímé její výstup do datového proudu a **EventLogTraceListener** by přímé její výstup do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="d0fbc-125">The **TextWriterTraceListener** would direct its output to a stream, and the **EventLogTraceListener** would direct its output to an event log.</span></span>  
  
 <span data-ttu-id="d0fbc-126">Následující příklad ukazuje, jak odeslat výstup do **naslouchací procesy** kolekce.</span><span class="sxs-lookup"><span data-stu-id="d0fbc-126">The following example shows how to send output to the **Listeners** collection.</span></span>  
  
```vb  
' Use this example when debugging.  
Debug.WriteLine("Error in Widget 42")  
' Use this example when tracing.  
Trace.WriteLine("Error in Widget 42")  
```  
  
```csharp  
// Use this example when debugging.  
System.Diagnostics.Debug.WriteLine("Error in Widget 42");  
// Use this example when tracing.  
System.Diagnostics.Trace.WriteLine("Error in Widget 42");  
```  
  
 <span data-ttu-id="d0fbc-127">Ladění a trasování sdílet stejný **naslouchací procesy** kolekce, takže když přidáte do objekt naslouchací proces **Debug.listeners –** kolekce v aplikaci, bude přidána k **Trace.Listeners** také kolekce.</span><span class="sxs-lookup"><span data-stu-id="d0fbc-127">Debug and trace share the same **Listeners** collection, so if you add a listener object to a **Debug.Listeners** collection in your application, it gets added to the **Trace.Listeners** collection as well.</span></span>  
  
 <span data-ttu-id="d0fbc-128">Následující příklad ukazuje, jak používat naslouchací proces k odesílání informací o trasování do konzoly:</span><span class="sxs-lookup"><span data-stu-id="d0fbc-128">The following example shows how to use a listener to send tracing information to a console:</span></span>  
  
```vb  
Trace.Listeners.Clear()  
Trace.Listeners.Add(New TextWriterTraceListener(Console.Out))  
```  
  
```csharp  
System.Diagnostics.Trace.Listeners.Clear();  
System.Diagnostics.Trace.Listeners.Add(  
   new System.Diagnostics.TextWriterTraceListener(Console.Out));  
```  
  
## <a name="developer-defined-listeners"></a><span data-ttu-id="d0fbc-129">Definované vývojáře – moduly naslouchání</span><span class="sxs-lookup"><span data-stu-id="d0fbc-129">Developer-Defined Listeners</span></span>  
 <span data-ttu-id="d0fbc-130">Vlastní naslouchací procesy můžete definovat dědění ze **TraceListener** základní třídy a přepsání její metody se vaše vlastní metody.</span><span class="sxs-lookup"><span data-stu-id="d0fbc-130">You can define your own listeners by inheriting from the **TraceListener** base class and overriding its methods with your customized methods.</span></span> <span data-ttu-id="d0fbc-131">Další informace o vytváření definované vývojáře naslouchací procesy najdete v tématu <xref:System.Diagnostics.TraceListener> v referenci rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d0fbc-131">For more information on creating developer-defined listeners, see <xref:System.Diagnostics.TraceListener> in the .NET Framework reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0fbc-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0fbc-132">See Also</span></span>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="d0fbc-133">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="d0fbc-133">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [<span data-ttu-id="d0fbc-134">Přepínače trasování</span><span class="sxs-lookup"><span data-stu-id="d0fbc-134">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)
