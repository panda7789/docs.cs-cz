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
ms.openlocfilehash: 56cbde16eff89d25960e510e7eec2424f15e51b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="trace-listeners"></a>Naslouchací procesy trasování
Při použití **trasování**, **ladění** a <xref:System.Diagnostics.TraceSource>, musí mít mechanismus pro shromažďování a záznamem zpráv, které se odesílají. Trasovací zprávy jsou přijímány *naslouchací procesy*. Účelem tohoto naslouchací proces je shromažďování, ukládání a směrovat trasovací zprávy. Posluchači přímý výstup trasování příslušný cíli, jako je protokol, okno nebo textový soubor.  
  
 Moduly pro naslouchání jsou k dispozici **ladění**, **trasování**, a <xref:System.Diagnostics.TraceSource> tříd, z nichž každá může odesílat její výstup do různých objektů naslouchací proces. Tady jsou běžně používané předdefinované naslouchací procesy:  
  
-   A <xref:System.Diagnostics.TextWriterTraceListener> přesměruje výstup do instance <xref:System.IO.TextWriter> třídy nebo nic, který je <xref:System.IO.Stream> třídy. Je také možné zapsat na konzole nebo do souboru, protože se jedná <xref:System.IO.Stream> třídy.  
  
-   <xref:System.Diagnostics.EventLogTraceListener> Přesměruje výstup do protokolu událostí.  
  
-   A <xref:System.Diagnostics.DefaultTraceListener> vysílá **zápisu** a **WriteLine** zprávy pro **OutputDebugString** a **Debugger.Log** metoda. V sadě Visual Studio to způsobí, že zprávy ladění zobrazí v okně výstupu. **Selhání** a k selhání **Assert** zprávy emitování také k **OutputDebugString** rozhraní API systému Windows a **Debugger.Log** metoda a příčina zprávu pole do Zobrazit. Toto chování je výchozí chování pro **ladění** a **trasování** zprávy, protože **DefaultTraceListener** je automaticky zahrnuta v každé `Listeners` kolekce a je automaticky zahrnuty pouze naslouchací proces.  
  
-   A <xref:System.Diagnostics.ConsoleTraceListener> směruje trasování nebo výstup do standardního výstupního nebo standardní chybový proud ladění.  
  
-   A <xref:System.Diagnostics.DelimitedListTraceListener> směruje trasování nebo výstup ladění do zapisovače textu, jako je datový proud, nebo do datového proudu, jako je datový proud souboru. Výstup trasování je ve formátu odděleného textu, který používá jako oddělovač určeného <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> vlastnost.  
  
-   <xref:System.Diagnostics.XmlWriterTraceListener> Směruje trasování nebo výstup ladění jako data kódovaná XML do <xref:System.IO.TextWriter> nebo <xref:System.IO.Stream>, například <xref:System.IO.FileStream>.  
  
 Pokud chcete, aby všechny naslouchací proces kromě <xref:System.Diagnostics.DefaultTraceListener> přijímat **ladění**, **trasování** a <xref:System.Diagnostics.TraceSource> výstup, je třeba přidat ji do `Listeners` kolekce. Další informace najdete v tématu [postupy: vytvoření a inicializace naslouchacích procesů trasování](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) a [postupy: použití třídy TraceSource a filtrů s naslouchacími procesy trasování](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md). Všechny naslouchací proces ve **naslouchací procesy** kolekce získá stejné zprávy z trasování výstupu metody. Předpokládejme například, můžete nastavit dva naslouchací procesy: **TextWriterTraceListener** a **EventLogTraceListener**. Každý naslouchací proces obdrží stejnou zprávu. **TextWriterTraceListener** by přímé její výstup do datového proudu a **EventLogTraceListener** by přímé její výstup do protokolu událostí.  
  
 Následující příklad ukazuje, jak odeslat výstup do **naslouchací procesy** kolekce.  
  
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
  
 Ladění a trasování sdílet stejný **naslouchací procesy** kolekce, takže když přidáte do objekt naslouchací proces **Debug.listeners –** kolekce v aplikaci, bude přidána k **Trace.Listeners** také kolekce.  
  
 Následující příklad ukazuje, jak používat naslouchací proces k odesílání informací o trasování do konzoly:  
  
```vb  
Trace.Listeners.Clear()  
Trace.Listeners.Add(New TextWriterTraceListener(Console.Out))  
```  
  
```csharp  
System.Diagnostics.Trace.Listeners.Clear();  
System.Diagnostics.Trace.Listeners.Add(  
   new System.Diagnostics.TextWriterTraceListener(Console.Out));  
```  
  
## <a name="developer-defined-listeners"></a>Definované vývojáře – moduly naslouchání  
 Vlastní naslouchací procesy můžete definovat dědění ze **TraceListener** základní třídy a přepsání její metody se vaše vlastní metody. Další informace o vytváření definované vývojáře naslouchací procesy najdete v tématu <xref:System.Diagnostics.TraceListener> v referenci rozhraní .NET Framework.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TraceListener>  
 [Trasování a instrumentace aplikací](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [Trasování – přepínače](../../../docs/framework/debug-trace-profile/trace-switches.md)
