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
ms.openlocfilehash: cdccc0d60cb5f4bbee5da9b07072a9aa14a8fde9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54500731"
---
# <a name="trace-listeners"></a>Naslouchací procesy trasování
Při použití **trasování**, **ladění** a <xref:System.Diagnostics.TraceSource>, musí mít mechanismus pro shromažďování a zaznamenávání zpráv, které se odesílají. Trasovací zprávy jsou přijímány *naslouchacích procesů*. Účelem tohoto naslouchací proces je shromažďování, ukládání a směrovat trasovací zprávy. Posluchači přímý výstup trasování příslušný cíli, jako je protokol, okno nebo textový soubor.  
  
 Naslouchací procesy jsou k dispozici na **ladění**, **trasování**, a <xref:System.Diagnostics.TraceSource> tříd, z nichž každý odeslat svůj výstup do různých objektů naslouchací proces. Tady jsou běžně používané předdefinované naslouchacích procesů:  
  
-   A <xref:System.Diagnostics.TextWriterTraceListener> přesměruje výstup do instance <xref:System.IO.TextWriter> třídy nebo cokoli, který je <xref:System.IO.Stream> třídy. To je zapsat také do konzoly nebo do souboru, protože se jedná <xref:System.IO.Stream> třídy.  
  
-   <xref:System.Diagnostics.EventLogTraceListener> Přesměruje výstup do protokolu událostí.  
  
-   A <xref:System.Diagnostics.DefaultTraceListener> vysílá **zápisu** a **WriteLine** zprávy **OutputDebugString** a **Debugger.Log** metoda. V sadě Visual Studio to způsobí, že zprávy ladění se zobrazí v okně výstup. **Selhání** i neúspěšné **Assert** zprávy také posílat do **OutputDebugString** rozhraní Windows API a **Debugger.Log** metoda a zprávu pole bude příčina zobrazí. Toto chování je výchozí chování pro **ladění** a **trasování** zprávy, protože **DefaultTraceListener** je automaticky zahrnut v každé `Listeners` kolekce a je automaticky zahrnuty pouze naslouchací proces.  
  
-   A <xref:System.Diagnostics.ConsoleTraceListener> směruje trasování nebo výstup do standardního výstupu nebo standardní chybový proud ladění.  
  
-   A <xref:System.Diagnostics.DelimitedListTraceListener> přesměruje trasování a ladění výstupu do zapisovače textu, jako je datový proud, nebo do datového proudu, jako je datový proud souboru. Výstup trasování je ve formátu odděleného textu, který používá oddělovač určené <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> vlastnost.  
  
-   <xref:System.Diagnostics.XmlWriterTraceListener> Směruje trasování nebo výstup ladění jako data kódovaná XML do <xref:System.IO.TextWriter> nebo <xref:System.IO.Stream>, například <xref:System.IO.FileStream>.  
  
 Pokud chcete, aby všechny naslouchací proces kromě <xref:System.Diagnostics.DefaultTraceListener> přijímat **ladění**, **trasování** a <xref:System.Diagnostics.TraceSource> výstup, je třeba přidat ji do `Listeners` kolekce. Další informace najdete v tématu [jak: Vytvoření a inicializace naslouchacích procesů trasování](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) a [jak: Použití třídy TraceSource a filtrů s naslouchacími procesy trasování](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md). Žádné naslouchací proces ve **naslouchacích procesů** kolekce získá stejné zprávy z trasování metody výstupu. Předpokládejme například, že nastavíte dva naslouchací procesy: **TextWriterTraceListener** a **EventLogTraceListener**. Každý naslouchací proces obdrží stejné zprávy. **TextWriterTraceListener** by směrovat výstup do datového proudu a **EventLogTraceListener** by směrovat výstup do protokolu událostí.  
  
 Následující příklad ukazuje, jak posílat výstup **naslouchacích procesů** kolekce.  
  
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
  
 Ladění a trasování sdílet stejný **naslouchacích procesů** kolekce, takže když přidáte do objekt naslouchacího procesu **Debug.listeners –** kolekce v aplikaci, získá přidá do **Trace.listeners –** také kolekce.  
  
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
  
## <a name="developer-defined-listeners"></a>Naslouchací procesy definované pro vývojáře  
 Můžete definovat vlastní naslouchací procesy děděním z **TraceListener** základní třídy a metody s vlastní metody přepsání. Další informace o vytvoření naslouchacích procesů definované pro vývojáře najdete v tématu <xref:System.Diagnostics.TraceListener> v referenční dokumentaci rozhraní .NET Framework.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TraceListener>
- [Trasování a instrumentace aplikací](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [Přepínače trasování](../../../docs/framework/debug-trace-profile/trace-switches.md)
