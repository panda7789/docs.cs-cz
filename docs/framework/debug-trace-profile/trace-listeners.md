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
ms.openlocfilehash: a51c046a296fbb62d21c7784cf7c1e78b700f3e9
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216145"
---
# <a name="trace-listeners"></a>Naslouchací procesy trasování
Při použití **trasování**, **ladění** a <xref:System.Diagnostics.TraceSource>musíte mít mechanismus pro shromažďování a zaznamenávání zpráv, které jsou odesílány. Trasovací zprávy jsou přijímány pomocí *posluchačů*. Účelem tohoto naslouchací proces je shromažďování, ukládání a směrovat trasovací zprávy. Posluchači přímý výstup trasování příslušný cíli, jako je protokol, okno nebo textový soubor.  
  
 Naslouchací procesy jsou k dispozici pro třídy **ladění**, **trasování**a <xref:System.Diagnostics.TraceSource>, z nichž každá může odeslat svůj výstup do nejrůznějších objektů naslouchacího procesu. Níže jsou uvedené běžně používané předdefinované naslouchací procesy:  
  
- <xref:System.Diagnostics.TextWriterTraceListener> přesměruje výstup do instance <xref:System.IO.TextWriter> třídy nebo cokoli, co je třída <xref:System.IO.Stream>. Může také zapisovat do konzoly nebo do souboru, protože se jedná o <xref:System.IO.Stream> třídy.  
  
- <xref:System.Diagnostics.EventLogTraceListener> přesměruje výstup do protokolu událostí.  
  
- <xref:System.Diagnostics.DefaultTraceListener> emituje zprávy **zápisu** a **WriteLine** do **OutputDebugString** a do metody **Debugger. log** . V aplikaci Visual Studio to způsobí, že se zprávy ladění zobrazí v okně výstup. Zprávy o **chybě** a neúspěšné **kontrolní výrazy** také generují rozhraní API systému Windows **OutputDebugString** a metodu **Debugger. log** a také způsobí, že se zobrazí okno se zprávou. Toto chování je výchozím chováním pro zprávy **ladění** a **trasování** , protože **DefaultTraceListener** je automaticky zahrnuté v každé kolekci `Listeners` a je to jediný naslouchací proces, který je automaticky zahrnutý.  
  
- <xref:System.Diagnostics.ConsoleTraceListener> směruje výstup trasování nebo ladění na standardní výstup nebo standardní chybový proud.  
  
- <xref:System.Diagnostics.DelimitedListTraceListener> směruje výstup trasování nebo ladění do zapisovače textu, jako je například zapisovač datového proudu, nebo do datového proudu, jako je například datový proud souboru. Výstup trasování je v odděleném textovém formátu, který používá oddělovač určený vlastností <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>.  
  
- <xref:System.Diagnostics.XmlWriterTraceListener> směruje trasování nebo ladění výstupu jako data zakódovaná XML do <xref:System.IO.TextWriter> nebo do <xref:System.IO.Stream>, jako je například <xref:System.IO.FileStream>.  
  
 Pokud chcete, aby jakýkoliv naslouchací proces kromě <xref:System.Diagnostics.DefaultTraceListener> přijímal **ladění**, **trasování** a <xref:System.Diagnostics.TraceSource> výstup, musíte ho přidat do kolekce `Listeners`. Další informace naleznete v tématu [How to: Create and Initialize Listeners Traces](how-to-create-and-initialize-trace-listeners.md) and [How to: use TraceSource and Filters with Trace Listeners](how-to-use-tracesource-and-filters-with-trace-listeners.md). Jakýkoli naslouchací proces v kolekci **posluchačů** získá stejné zprávy z výstupních metod trasování. Předpokládejme například, že jste nastavili dva naslouchací procesy: **TextWriterTraceListener** a **EventLogTraceListener**. Každý naslouchací proces obdrží stejnou zprávu. **TextWriterTraceListener** by nasměroval svůj výstup do datového proudu a **EventLogTraceListener** by nasměroval svůj výstup do protokolu událostí.  
  
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
 Můžete definovat vlastní naslouchací procesy děděním ze základní třídy **TraceListener** a přepsáním jejích metod pomocí přizpůsobených metod. Další informace o vytváření posluchačů definovaných vývojářům naleznete v tématu <xref:System.Diagnostics.TraceListener> v referenční příručce .NET Framework.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TraceListener>
- [Trasování a instrumentace aplikací](tracing-and-instrumenting-applications.md)
- [Přepínače trasování](trace-switches.md)
