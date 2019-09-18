---
title: Naslouchací procesy trasování
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 752a6a5f9608aa260f192ee3e9e0709b7a10e27e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052290"
---
# <a name="trace-listeners"></a><span data-ttu-id="72d6e-102">Naslouchací procesy trasování</span><span class="sxs-lookup"><span data-stu-id="72d6e-102">Trace Listeners</span></span>
<span data-ttu-id="72d6e-103">Při použití **trasování**, **ladění** a <xref:System.Diagnostics.TraceSource>musíte mít mechanismus pro shromažďování a zaznamenávání zpráv, které jsou odesílány.</span><span class="sxs-lookup"><span data-stu-id="72d6e-103">When using **Trace**, **Debug** and <xref:System.Diagnostics.TraceSource>, you must have a mechanism for collecting and recording the messages that are sent.</span></span> <span data-ttu-id="72d6e-104">Trasovací zprávy jsou přijímány pomocí *posluchačů*.</span><span class="sxs-lookup"><span data-stu-id="72d6e-104">Trace messages are received by *listeners*.</span></span> <span data-ttu-id="72d6e-105">Účelem tohoto naslouchací proces je shromažďování, ukládání a směrovat trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="72d6e-105">The purpose of a listener is to collect, store, and route tracing messages.</span></span> <span data-ttu-id="72d6e-106">Posluchači přímý výstup trasování příslušný cíli, jako je protokol, okno nebo textový soubor.</span><span class="sxs-lookup"><span data-stu-id="72d6e-106">Listeners direct the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="72d6e-107">Naslouchací procesy jsou k dispozici pro **ladění**, **trasování**a <xref:System.Diagnostics.TraceSource> třídy, z nichž každý může odeslat svůj výstup do nejrůznějších objektů naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="72d6e-107">Listeners are available to the **Debug**, **Trace**, and <xref:System.Diagnostics.TraceSource> classes, each of which can send its output to a variety of listener objects.</span></span> <span data-ttu-id="72d6e-108">Níže jsou uvedené běžně používané předdefinované naslouchací procesy:</span><span class="sxs-lookup"><span data-stu-id="72d6e-108">The following are the commonly used predefined listeners:</span></span>  
  
- <span data-ttu-id="72d6e-109">Přesměruje výstup do instance <xref:System.IO.TextWriter> třídy nebo cokoli, co je <xref:System.IO.Stream> třída. <xref:System.Diagnostics.TextWriterTraceListener></span><span class="sxs-lookup"><span data-stu-id="72d6e-109">A <xref:System.Diagnostics.TextWriterTraceListener> redirects output to an instance of the <xref:System.IO.TextWriter> class or to anything that is a <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="72d6e-110">Může také zapisovat do konzoly nebo do souboru, protože se <xref:System.IO.Stream> jedná o třídy.</span><span class="sxs-lookup"><span data-stu-id="72d6e-110">It can also write to the console or to a file, because these are <xref:System.IO.Stream> classes.</span></span>  
  
- <span data-ttu-id="72d6e-111"><xref:System.Diagnostics.EventLogTraceListener> Přesměruje výstup do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="72d6e-111">An <xref:System.Diagnostics.EventLogTraceListener> redirects output to an event log.</span></span>  
  
- <span data-ttu-id="72d6e-112">Vygeneruje zprávy zápisu a WriteLine do OutputDebugString a do metody Debugger. log. <xref:System.Diagnostics.DefaultTraceListener></span><span class="sxs-lookup"><span data-stu-id="72d6e-112">A <xref:System.Diagnostics.DefaultTraceListener> emits **Write** and **WriteLine** messages to the **OutputDebugString** and to the **Debugger.Log** method.</span></span> <span data-ttu-id="72d6e-113">V aplikaci Visual Studio to způsobí, že se zprávy ladění zobrazí v okně výstup.</span><span class="sxs-lookup"><span data-stu-id="72d6e-113">In Visual Studio, this causes the debugging messages to appear in the Output window.</span></span> <span data-ttu-id="72d6e-114">Zprávy o **chybě** a neúspěšné **kontrolní výrazy** také generují rozhraní API systému Windows **OutputDebugString** a metodu **Debugger. log** a také způsobí, že se zobrazí okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="72d6e-114">**Fail** and failed **Assert** messages also emit to the **OutputDebugString** Windows API and the **Debugger.Log** method, and also cause a message box to be displayed.</span></span> <span data-ttu-id="72d6e-115">Toto chování je výchozím chováním pro zprávy **ladění** a **trasování** , protože **DefaultTraceListener** je automaticky zahrnuté do `Listeners` každé kolekce a je to jediný naslouchací proces, který je automaticky zahrnutý.</span><span class="sxs-lookup"><span data-stu-id="72d6e-115">This behavior is the default behavior for **Debug** and **Trace** messages, because **DefaultTraceListener** is automatically included in every `Listeners` collection and is the only listener automatically included.</span></span>  
  
- <span data-ttu-id="72d6e-116"><xref:System.Diagnostics.ConsoleTraceListener> Přesměruje výstup trasování nebo ladění na standardní výstup nebo standardní chybový proud.</span><span class="sxs-lookup"><span data-stu-id="72d6e-116">A <xref:System.Diagnostics.ConsoleTraceListener> directs tracing or debugging output to either the standard output or the standard error stream.</span></span>  
  
- <span data-ttu-id="72d6e-117"><xref:System.Diagnostics.DelimitedListTraceListener> Směruje trasování nebo ladění výstupu do zapisovače textu, jako je například zapisovač datového proudu, nebo do datového proudu, jako je například datový proud souboru.</span><span class="sxs-lookup"><span data-stu-id="72d6e-117">A <xref:System.Diagnostics.DelimitedListTraceListener> directs tracing or debugging output to a text writer, such as a stream writer, or to a stream, such as a file stream.</span></span> <span data-ttu-id="72d6e-118">Výstup trasování je v odděleném textovém formátu, který používá oddělovač určený <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> vlastností.</span><span class="sxs-lookup"><span data-stu-id="72d6e-118">The trace output is in a delimited text format that uses the delimiter specified by the <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> property.</span></span>  
  
- <span data-ttu-id="72d6e-119">Směruje trasování nebo ladění výstupu jako data kódovaná v jazyce XML <xref:System.IO.TextWriter> do nebo do <xref:System.IO.Stream>, jako je <xref:System.IO.FileStream>například. <xref:System.Diagnostics.XmlWriterTraceListener></span><span class="sxs-lookup"><span data-stu-id="72d6e-119">An <xref:System.Diagnostics.XmlWriterTraceListener> directs tracing or debugging output as XML-encoded data to a <xref:System.IO.TextWriter> or to a <xref:System.IO.Stream>, such as a <xref:System.IO.FileStream>.</span></span>  
  
 <span data-ttu-id="72d6e-120">Pokud chcete, aby nějaký naslouchací proces <xref:System.Diagnostics.DefaultTraceListener> kromě příjmu přijal **ladění**, **trasování** a <xref:System.Diagnostics.TraceSource> výstup, musíte ho přidat do `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="72d6e-120">If you want any listener besides the <xref:System.Diagnostics.DefaultTraceListener> to receive **Debug**, **Trace** and <xref:System.Diagnostics.TraceSource> output, you must add it to the `Listeners` collection.</span></span> <span data-ttu-id="72d6e-121">Další informace najdete v tématu [jak: Vytváření a inicializace posluchačů](how-to-create-and-initialize-trace-listeners.md) trasování [a postupy: Použijte TraceSource a filtry s naslouchacími](how-to-use-tracesource-and-filters-with-trace-listeners.md)procesy trasování.</span><span class="sxs-lookup"><span data-stu-id="72d6e-121">For more information, see [How to: Create and Initialize Trace Listeners](how-to-create-and-initialize-trace-listeners.md) and [How to: Use TraceSource and Filters with Trace Listeners](how-to-use-tracesource-and-filters-with-trace-listeners.md).</span></span> <span data-ttu-id="72d6e-122">Jakýkoli naslouchací proces v kolekci **posluchačů** získá stejné zprávy z výstupních metod trasování.</span><span class="sxs-lookup"><span data-stu-id="72d6e-122">Any listener in the **Listeners** collection gets the same messages from the trace output methods.</span></span> <span data-ttu-id="72d6e-123">Předpokládejme například, že jste nastavili dva naslouchací procesy: **TextWriterTraceListener** a **EventLogTraceListener**.</span><span class="sxs-lookup"><span data-stu-id="72d6e-123">For example, suppose you set up two listeners: a **TextWriterTraceListener** and an **EventLogTraceListener**.</span></span> <span data-ttu-id="72d6e-124">Každý naslouchací proces obdrží stejnou zprávu.</span><span class="sxs-lookup"><span data-stu-id="72d6e-124">Each listener receives the same message.</span></span> <span data-ttu-id="72d6e-125">**TextWriterTraceListener** by nasměroval svůj výstup do datového proudu a **EventLogTraceListener** by nasměroval svůj výstup do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="72d6e-125">The **TextWriterTraceListener** would direct its output to a stream, and the **EventLogTraceListener** would direct its output to an event log.</span></span>  
  
 <span data-ttu-id="72d6e-126">Následující příklad ukazuje, jak odeslat výstup do kolekce **posluchačů** .</span><span class="sxs-lookup"><span data-stu-id="72d6e-126">The following example shows how to send output to the **Listeners** collection.</span></span>  
  
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
  
 <span data-ttu-id="72d6e-127">Ladění a trasování sdílejí stejnou kolekci **posluchačů** , takže pokud přidáte objekt naslouchacího procesu do kolekce **Debug. Listeners** ve vaší aplikaci, bude přidáno také do kolekce **Trace. Listeners** .</span><span class="sxs-lookup"><span data-stu-id="72d6e-127">Debug and trace share the same **Listeners** collection, so if you add a listener object to a **Debug.Listeners** collection in your application, it gets added to the **Trace.Listeners** collection as well.</span></span>  
  
 <span data-ttu-id="72d6e-128">Následující příklad ukazuje, jak použít naslouchací proces pro odeslání trasovacích informací do konzoly:</span><span class="sxs-lookup"><span data-stu-id="72d6e-128">The following example shows how to use a listener to send tracing information to a console:</span></span>  
  
```vb  
Trace.Listeners.Clear()  
Trace.Listeners.Add(New TextWriterTraceListener(Console.Out))  
```  
  
```csharp  
System.Diagnostics.Trace.Listeners.Clear();  
System.Diagnostics.Trace.Listeners.Add(  
   new System.Diagnostics.TextWriterTraceListener(Console.Out));  
```  
  
## <a name="developer-defined-listeners"></a><span data-ttu-id="72d6e-129">Naslouchací procesy definované vývojářem</span><span class="sxs-lookup"><span data-stu-id="72d6e-129">Developer-Defined Listeners</span></span>  
 <span data-ttu-id="72d6e-130">Můžete definovat vlastní naslouchací procesy děděním ze základní třídy **TraceListener** a přepsáním jejích metod pomocí přizpůsobených metod.</span><span class="sxs-lookup"><span data-stu-id="72d6e-130">You can define your own listeners by inheriting from the **TraceListener** base class and overriding its methods with your customized methods.</span></span> <span data-ttu-id="72d6e-131">Další informace o vytváření posluchačů definovaných vývojářům naleznete v <xref:System.Diagnostics.TraceListener> tématu .NET Framework reference.</span><span class="sxs-lookup"><span data-stu-id="72d6e-131">For more information on creating developer-defined listeners, see <xref:System.Diagnostics.TraceListener> in the .NET Framework reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72d6e-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="72d6e-132">See also</span></span>

- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="72d6e-133">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="72d6e-133">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="72d6e-134">Přepínače trasování</span><span class="sxs-lookup"><span data-stu-id="72d6e-134">Trace Switches</span></span>](trace-switches.md)
