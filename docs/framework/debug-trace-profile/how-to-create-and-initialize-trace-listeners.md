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
ms.openlocfilehash: 943621b953fbe158b3be6ae0695ba7692b7c517f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-and-initialize-trace-listeners"></a>Postupy: Vytváření a inicializace naslouchacích procesů trasování
<xref:System.Diagnostics.Debug?displayProperty=nameWithType> a <xref:System.Diagnostics.Trace?displayProperty=nameWithType> třídy odesílat zprávy objektů názvem naslouchací procesy, které přijímat a zpracovávat tyto zprávy. Jeden takový naslouchací proces, <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, je automaticky vytvořen a inicializován při zapnutém trasování nebo ladění. Chcete-li <xref:System.Diagnostics.Trace> nebo <xref:System.Diagnostics.Debug> výstup přesměrováni na žádné další zdroje, musíte vytvořit a inicializace naslouchacích procesů trasování Další.  
  
 Naslouchací procesy, které vytvoříte by měla odpovídat potřebám vaší aplikace. Například pokud chcete text záznam všech výstup trasování, vytvořit <xref:System.Diagnostics.TextWriterTraceListener> naslouchací proces, který zapisuje veškerý výstup do nového textového souboru, pokud je povolený. Na druhé straně, pokud chcete zobrazit výstup pouze během provádění aplikací, vytvořte <xref:System.Diagnostics.ConsoleTraceListener> naslouchací proces, který přesměruje veškerý výstup do okna konzoly. <xref:System.Diagnostics.EventLogTraceListener> Můžete přesměrujte výstup trasování do protokolu událostí. Další informace najdete v tématu [trasování – moduly naslouchání](../../../docs/framework/debug-trace-profile/trace-listeners.md).  
  
 Můžete vytvořit naslouchací procesy trasování v [konfigurační soubor aplikace](../../../docs/framework/configure-apps/index.md) nebo v kódu. Doporučujeme použití konfigurační soubory aplikace, protože umožňují přidávat, upravovat nebo odebírat trasování – moduly naslouchání bez nutnosti měnit kód.  
  
### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a>Vytváření a používání naslouchací pomocí konfiguračního souboru  
  
1.  Deklarujte vaší naslouchací proces trasování v konfiguračním souboru aplikace. Pokud naslouchací proces, který vytváříte vyžaduje, aby všechny další objekty, deklarujte je také. Následující příklad ukazuje, jak vytvořit naslouchací proces nazvaný `myListener` který zapisuje do textového souboru `TextWriterOutput.log`.  
  
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
  
2.  Použití <xref:System.Diagnostics.Trace> třídy ve vašem kódu zapsat zprávu do naslouchací procesy trasování.  
  
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
  
### <a name="to-create-and-use-a-trace-listener-in-code"></a>Vytváření a používání naslouchací proces trasování v kódu  
  
-   Přidejte naslouchací proces trasování do <xref:System.Diagnostics.Trace.Listeners%2A> shromažďování a odesílání informací naslouchací procesy trasování.  
  
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
  
     - nebo –  
  
-   Pokud nechcete, aby vaše naslouchací proces pro příjem výstup trasování, nepřidávejte jej do <xref:System.Diagnostics.Trace.Listeners%2A> kolekce. Můžete emitování výstup prostřednictvím naslouchací proces nezávisle <xref:System.Diagnostics.Trace.Listeners%2A> kolekce voláním naslouchací proces pro vlastní výstup metody. Následující příklad ukazuje, jak napsat řádek pro naslouchací proces, který není součástí <xref:System.Diagnostics.Trace.Listeners%2A> kolekce.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Moduly naslouchání trasování](../../../docs/framework/debug-trace-profile/trace-listeners.md)  
 [Přepínače trasování](../../../docs/framework/debug-trace-profile/trace-switches.md)  
 [Postupy: Přidání příkazů trasování do kódu aplikace](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)  
 [Trasování a instrumentace aplikací](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
