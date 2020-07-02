---
title: Naslouchací procesy trasování
description: Prozkoumejte naslouchací procesy trasování, které jsou mechanismem pro shromažďování a zaznamenávání trasovacích zpráv odeslaných v rozhraní .NET. Naslouchací proces shromažďuje, ukládá a směruje zprávy.
ms.date: 03/30/2017
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
ms.openlocfilehash: d08f86c782284a296090cf63e4b03c8d446a95fc
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803520"
---
# <a name="trace-listeners"></a><span data-ttu-id="ff0e5-104">Naslouchací procesy trasování</span><span class="sxs-lookup"><span data-stu-id="ff0e5-104">Trace Listeners</span></span>
<span data-ttu-id="ff0e5-105">Při použití **trasování**, **ladění** a <xref:System.Diagnostics.TraceSource> musíte mít mechanismus pro shromažďování a zaznamenávání zpráv, které jsou odesílány.</span><span class="sxs-lookup"><span data-stu-id="ff0e5-105">When using **Trace**, **Debug** and <xref:System.Diagnostics.TraceSource>, you must have a mechanism for collecting and recording the messages that are sent.</span></span> <span data-ttu-id="ff0e5-106">Trasovací zprávy jsou přijímány pomocí *posluchačů*.</span><span class="sxs-lookup"><span data-stu-id="ff0e5-106">Trace messages are received by *listeners*.</span></span> <span data-ttu-id="ff0e5-107">Účelem tohoto naslouchací proces je shromažďování, ukládání a směrovat trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="ff0e5-107">The purpose of a listener is to collect, store, and route tracing messages.</span></span> <span data-ttu-id="ff0e5-108">Posluchači přímý výstup trasování příslušný cíli, jako je protokol, okno nebo textový soubor.</span><span class="sxs-lookup"><span data-stu-id="ff0e5-108">Listeners direct the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="ff0e5-109">Naslouchací procesy jsou k dispozici pro **ladění**, **trasování**a <xref:System.Diagnostics.TraceSource> třídy, z nichž každý může odeslat svůj výstup do nejrůznějších objektů naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="ff0e5-109">Listeners are available to the **Debug**, **Trace**, and <xref:System.Diagnostics.TraceSource> classes, each of which can send its output to a variety of listener objects.</span></span> <span data-ttu-id="ff0e5-110">Níže jsou uvedené běžně používané předdefinované naslouchací procesy:</span><span class="sxs-lookup"><span data-stu-id="ff0e5-110">The following are the commonly used predefined listeners:</span></span>  
  
- <span data-ttu-id="ff0e5-111"><xref:System.Diagnostics.TextWriterTraceListener>Přesměruje výstup do instance <xref:System.IO.TextWriter> třídy nebo cokoli, co je <xref:System.IO.Stream> Třída.</span><span class="sxs-lookup"><span data-stu-id="ff0e5-111">A <xref:System.Diagnostics.TextWriterTraceListener> redirects output to an instance of the <xref:System.IO.TextWriter> class or to anything that is a <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="ff0e5-112">Může také zapisovat do konzoly nebo do souboru, protože se jedná o <xref:System.IO.Stream> třídy.</span><span class="sxs-lookup"><span data-stu-id="ff0e5-112">It can also write to the console or to a file, because these are <xref:System.IO.Stream> classes.</span></span>  
  
- <span data-ttu-id="ff0e5-113"><xref:System.Diagnostics.EventLogTraceListener>Přesměruje výstup do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="ff0e5-113">An <xref:System.Diagnostics.EventLogTraceListener> redirects output to an event log.</span></span>  
  
- <span data-ttu-id="ff0e5-114"><xref:System.Diagnostics.DefaultTraceListener>Vygeneruje zprávy **zápisu** a **WriteLine** do **OutputDebugString** a do metody **Debugger. log** .</span><span class="sxs-lookup"><span data-stu-id="ff0e5-114">A <xref:System.Diagnostics.DefaultTraceListener> emits **Write** and **WriteLine** messages to the **OutputDebugString** and to the **Debugger.Log** method.</span></span> <span data-ttu-id="ff0e5-115">V aplikaci Visual Studio to způsobí, že se zprávy ladění zobrazí v okně výstup.</span><span class="sxs-lookup"><span data-stu-id="ff0e5-115">In Visual Studio, this causes the debugging messages to appear in the Output window.</span></span> <span data-ttu-id="ff0e5-116">Zprávy o **chybě** a neúspěšné **kontrolní výrazy** také generují rozhraní API systému Windows **OutputDebugString** a metodu **Debugger. log** a také způsobí, že se zobrazí okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="ff0e5-116">**Fail** and failed **Assert** messages also emit to the **OutputDebugString** Windows API and the **Debugger.Log** method, and also cause a message box to be displayed.</span></span> <span data-ttu-id="ff0e5-117">Toto chování je výchozím chováním pro zprávy **ladění** a **trasování** , protože **DefaultTraceListener** je automaticky zahrnuté do každé `Listeners` kolekce a je to jediný naslouchací proces, který je automaticky zahrnutý.</span><span class="sxs-lookup"><span data-stu-id="ff0e5-117">This behavior is the default behavior for **Debug** and **Trace** messages, because **DefaultTraceListener** is automatically included in every `Listeners` collection and is the only listener automatically included.</span></span>  
  
- <span data-ttu-id="ff0e5-118"><xref:System.Diagnostics.ConsoleTraceListener>Přesměruje výstup trasování nebo ladění na standardní výstup nebo standardní chybový proud.</span><span class="sxs-lookup"><span data-stu-id="ff0e5-118">A <xref:System.Diagnostics.ConsoleTraceListener> directs tracing or debugging output to either the standard output or the standard error stream.</span></span>  
  
- <span data-ttu-id="ff0e5-119"><xref:System.Diagnostics.DelimitedListTraceListener>Směruje trasování nebo ladění výstupu do zapisovače textu, jako je například zapisovač datového proudu, nebo do datového proudu, jako je například datový proud souboru.</span><span class="sxs-lookup"><span data-stu-id="ff0e5-119">A <xref:System.Diagnostics.DelimitedListTraceListener> directs tracing or debugging output to a text writer, such as a stream writer, or to a stream, such as a file stream.</span></span> <span data-ttu-id="ff0e5-120">Výstup trasování je v odděleném textovém formátu, který používá oddělovač určený <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> vlastností.</span><span class="sxs-lookup"><span data-stu-id="ff0e5-120">The trace output is in a delimited text format that uses the delimiter specified by the <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> property.</span></span>  
  
- <span data-ttu-id="ff0e5-121"><xref:System.Diagnostics.XmlWriterTraceListener>Směruje trasování nebo ladění výstupu jako data kódovaná v jazyce XML do <xref:System.IO.TextWriter> nebo do <xref:System.IO.Stream> , jako je například <xref:System.IO.FileStream> .</span><span class="sxs-lookup"><span data-stu-id="ff0e5-121">An <xref:System.Diagnostics.XmlWriterTraceListener> directs tracing or debugging output as XML-encoded data to a <xref:System.IO.TextWriter> or to a <xref:System.IO.Stream>, such as a <xref:System.IO.FileStream>.</span></span>  
  
 <span data-ttu-id="ff0e5-122">Pokud chcete, aby nějaký naslouchací proces kromě <xref:System.Diagnostics.DefaultTraceListener> příjmu přijal **ladění**, **trasování** a <xref:System.Diagnostics.TraceSource> výstup, musíte ho přidat do `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="ff0e5-122">If you want any listener besides the <xref:System.Diagnostics.DefaultTraceListener> to receive **Debug**, **Trace** and <xref:System.Diagnostics.TraceSource> output, you must add it to the `Listeners` collection.</span></span> <span data-ttu-id="ff0e5-123">Další informace naleznete v tématu [How to: Create and Initialize Listeners Traces](how-to-create-and-initialize-trace-listeners.md) and [How to: use TraceSource and Filters with Trace Listeners](how-to-use-tracesource-and-filters-with-trace-listeners.md).</span><span class="sxs-lookup"><span data-stu-id="ff0e5-123">For more information, see [How to: Create and Initialize Trace Listeners](how-to-create-and-initialize-trace-listeners.md) and [How to: Use TraceSource and Filters with Trace Listeners](how-to-use-tracesource-and-filters-with-trace-listeners.md).</span></span> <span data-ttu-id="ff0e5-124">Jakýkoli naslouchací proces v kolekci **posluchačů** získá stejné zprávy z výstupních metod trasování.</span><span class="sxs-lookup"><span data-stu-id="ff0e5-124">Any listener in the **Listeners** collection gets the same messages from the trace output methods.</span></span> <span data-ttu-id="ff0e5-125">Předpokládejme například, že jste nastavili dva naslouchací procesy: **TextWriterTraceListener** a **EventLogTraceListener**.</span><span class="sxs-lookup"><span data-stu-id="ff0e5-125">For example, suppose you set up two listeners: a **TextWriterTraceListener** and an **EventLogTraceListener**.</span></span> <span data-ttu-id="ff0e5-126">Každý naslouchací proces obdrží stejnou zprávu.</span><span class="sxs-lookup"><span data-stu-id="ff0e5-126">Each listener receives the same message.</span></span> <span data-ttu-id="ff0e5-127">**TextWriterTraceListener** by nasměroval svůj výstup do datového proudu a **EventLogTraceListener** by nasměroval svůj výstup do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="ff0e5-127">The **TextWriterTraceListener** would direct its output to a stream, and the **EventLogTraceListener** would direct its output to an event log.</span></span>  
  
 <span data-ttu-id="ff0e5-128">Následující příklad ukazuje, jak odeslat výstup do kolekce **posluchačů** .</span><span class="sxs-lookup"><span data-stu-id="ff0e5-128">The following example shows how to send output to the **Listeners** collection.</span></span>  
  
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
  
 <span data-ttu-id="ff0e5-129">Ladění a trasování sdílejí stejnou kolekci **posluchačů** , takže pokud přidáte objekt naslouchacího procesu do kolekce **Debug. Listeners** ve vaší aplikaci, bude přidáno také do kolekce **Trace. Listeners** .</span><span class="sxs-lookup"><span data-stu-id="ff0e5-129">Debug and trace share the same **Listeners** collection, so if you add a listener object to a **Debug.Listeners** collection in your application, it gets added to the **Trace.Listeners** collection as well.</span></span>  
  
 <span data-ttu-id="ff0e5-130">Následující příklad ukazuje, jak použít naslouchací proces pro odeslání trasovacích informací do konzoly:</span><span class="sxs-lookup"><span data-stu-id="ff0e5-130">The following example shows how to use a listener to send tracing information to a console:</span></span>  
  
```vb  
Trace.Listeners.Clear()  
Trace.Listeners.Add(New TextWriterTraceListener(Console.Out))  
```  
  
```csharp  
System.Diagnostics.Trace.Listeners.Clear();  
System.Diagnostics.Trace.Listeners.Add(  
   new System.Diagnostics.TextWriterTraceListener(Console.Out));  
```  
  
## <a name="developer-defined-listeners"></a><span data-ttu-id="ff0e5-131">Naslouchací procesy definované vývojářem</span><span class="sxs-lookup"><span data-stu-id="ff0e5-131">Developer-Defined Listeners</span></span>  
 <span data-ttu-id="ff0e5-132">Můžete definovat vlastní naslouchací procesy děděním ze základní třídy **TraceListener** a přepsáním jejích metod pomocí přizpůsobených metod.</span><span class="sxs-lookup"><span data-stu-id="ff0e5-132">You can define your own listeners by inheriting from the **TraceListener** base class and overriding its methods with your customized methods.</span></span> <span data-ttu-id="ff0e5-133">Další informace o vytváření posluchačů definovaných vývojářům naleznete <xref:System.Diagnostics.TraceListener> v tématu .NET Framework reference.</span><span class="sxs-lookup"><span data-stu-id="ff0e5-133">For more information on creating developer-defined listeners, see <xref:System.Diagnostics.TraceListener> in the .NET Framework reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff0e5-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ff0e5-134">See also</span></span>

- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="ff0e5-135">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="ff0e5-135">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="ff0e5-136">Přepínače trasování</span><span class="sxs-lookup"><span data-stu-id="ff0e5-136">Trace Switches</span></span>](trace-switches.md)
