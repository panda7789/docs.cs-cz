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
# <a name="trace-listeners"></a>Naslouchací procesy trasování
Při použití **trasování**, **ladění** a <xref:System.Diagnostics.TraceSource>musíte mít mechanismus pro shromažďování a zaznamenávání zpráv, které jsou odesílány. Trasovací zprávy jsou přijímány pomocí *posluchačů*. Účelem tohoto naslouchací proces je shromažďování, ukládání a směrovat trasovací zprávy. Posluchači přímý výstup trasování příslušný cíli, jako je protokol, okno nebo textový soubor.  
  
 Naslouchací procesy jsou k dispozici pro **ladění**, **trasování**a <xref:System.Diagnostics.TraceSource> třídy, z nichž každý může odeslat svůj výstup do nejrůznějších objektů naslouchacího procesu. Níže jsou uvedené běžně používané předdefinované naslouchací procesy:  
  
- Přesměruje výstup do instance <xref:System.IO.TextWriter> třídy nebo cokoli, co je <xref:System.IO.Stream> třída. <xref:System.Diagnostics.TextWriterTraceListener> Může také zapisovat do konzoly nebo do souboru, protože se <xref:System.IO.Stream> jedná o třídy.  
  
- <xref:System.Diagnostics.EventLogTraceListener> Přesměruje výstup do protokolu událostí.  
  
- Vygeneruje zprávy zápisu a WriteLine do OutputDebugString a do metody Debugger. log. <xref:System.Diagnostics.DefaultTraceListener> V aplikaci Visual Studio to způsobí, že se zprávy ladění zobrazí v okně výstup. Zprávy o **chybě** a neúspěšné **kontrolní výrazy** také generují rozhraní API systému Windows **OutputDebugString** a metodu **Debugger. log** a také způsobí, že se zobrazí okno se zprávou. Toto chování je výchozím chováním pro zprávy **ladění** a **trasování** , protože **DefaultTraceListener** je automaticky zahrnuté do `Listeners` každé kolekce a je to jediný naslouchací proces, který je automaticky zahrnutý.  
  
- <xref:System.Diagnostics.ConsoleTraceListener> Přesměruje výstup trasování nebo ladění na standardní výstup nebo standardní chybový proud.  
  
- <xref:System.Diagnostics.DelimitedListTraceListener> Směruje trasování nebo ladění výstupu do zapisovače textu, jako je například zapisovač datového proudu, nebo do datového proudu, jako je například datový proud souboru. Výstup trasování je v odděleném textovém formátu, který používá oddělovač určený <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> vlastností.  
  
- Směruje trasování nebo ladění výstupu jako data kódovaná v jazyce XML <xref:System.IO.TextWriter> do nebo do <xref:System.IO.Stream>, jako je <xref:System.IO.FileStream>například. <xref:System.Diagnostics.XmlWriterTraceListener>  
  
 Pokud chcete, aby nějaký naslouchací proces <xref:System.Diagnostics.DefaultTraceListener> kromě příjmu přijal **ladění**, **trasování** a <xref:System.Diagnostics.TraceSource> výstup, musíte ho přidat do `Listeners` kolekce. Další informace najdete v tématu [jak: Vytváření a inicializace posluchačů](how-to-create-and-initialize-trace-listeners.md) trasování [a postupy: Použijte TraceSource a filtry s naslouchacími](how-to-use-tracesource-and-filters-with-trace-listeners.md)procesy trasování. Jakýkoli naslouchací proces v kolekci **posluchačů** získá stejné zprávy z výstupních metod trasování. Předpokládejme například, že jste nastavili dva naslouchací procesy: **TextWriterTraceListener** a **EventLogTraceListener**. Každý naslouchací proces obdrží stejnou zprávu. **TextWriterTraceListener** by nasměroval svůj výstup do datového proudu a **EventLogTraceListener** by nasměroval svůj výstup do protokolu událostí.  
  
 Následující příklad ukazuje, jak odeslat výstup do kolekce **posluchačů** .  
  
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
  
 Ladění a trasování sdílejí stejnou kolekci **posluchačů** , takže pokud přidáte objekt naslouchacího procesu do kolekce **Debug. Listeners** ve vaší aplikaci, bude přidáno také do kolekce **Trace. Listeners** .  
  
 Následující příklad ukazuje, jak použít naslouchací proces pro odeslání trasovacích informací do konzoly:  
  
```vb  
Trace.Listeners.Clear()  
Trace.Listeners.Add(New TextWriterTraceListener(Console.Out))  
```  
  
```csharp  
System.Diagnostics.Trace.Listeners.Clear();  
System.Diagnostics.Trace.Listeners.Add(  
   new System.Diagnostics.TextWriterTraceListener(Console.Out));  
```  
  
## <a name="developer-defined-listeners"></a>Naslouchací procesy definované vývojářem  
 Můžete definovat vlastní naslouchací procesy děděním ze základní třídy **TraceListener** a přepsáním jejích metod pomocí přizpůsobených metod. Další informace o vytváření posluchačů definovaných vývojářům naleznete v <xref:System.Diagnostics.TraceListener> tématu .NET Framework reference.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TraceListener>
- [Trasování a instrumentace aplikací](tracing-and-instrumenting-applications.md)
- [Přepínače trasování](trace-switches.md)
