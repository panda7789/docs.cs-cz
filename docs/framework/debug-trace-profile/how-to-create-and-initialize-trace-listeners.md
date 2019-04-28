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
ms.openlocfilehash: ea5db2ba1060479f55bbd7f67266d36085a2535f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754372"
---
# <a name="how-to-create-and-initialize-trace-listeners"></a>Postupy: Vytváření a inicializace naslouchacích procesů trasování

<xref:System.Diagnostics.Debug?displayProperty=nameWithType> a <xref:System.Diagnostics.Trace?displayProperty=nameWithType> třídy odesílání zpráv do objektů nazývaných naslouchacích procesů, které příjem a zpracování těchto zpráv. Jeden takový naslouchací proces <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, je automaticky vytvořen a inicializován při zapnutém trasování a ladění. Chcete-li <xref:System.Diagnostics.Trace> nebo <xref:System.Diagnostics.Debug> výstup přesměrováni na jakékoli další zdroje, musíte vytvořit a inicializovat naslouchací procesy další trasování.

Naslouchací procesy, které vytvoříte by měly odrážet potřeby vaší aplikace. Například pokud chcete text záznam všech výstupu trasování, vytvořit <xref:System.Diagnostics.TextWriterTraceListener> naslouchací proces, který zapisuje veškerý výstup do nového textového souboru, je-li povolena. Na druhé straně, pokud chcete zobrazit výstup pouze při spuštění aplikace, vytvořte <xref:System.Diagnostics.ConsoleTraceListener> naslouchací proces, který směruje veškerý výstup do okna konzoly. <xref:System.Diagnostics.EventLogTraceListener> Může směrovat výstup trasování do protokolu událostí. Další informace najdete v tématu [naslouchacích procesů trasování](../../../docs/framework/debug-trace-profile/trace-listeners.md).

Můžete vytvořit naslouchací procesy trasování v [konfiguračního souboru aplikace](../../../docs/framework/configure-apps/index.md) nebo ve vašem kódu. Doporučujeme vám používat konfigurační soubory aplikace, protože umožňují přidat, upravit nebo odebrat naslouchacích procesů trasování bez nutnosti měnit kód.

### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a>Vytvoření a použití naslouchací proces trasování pomocí konfiguračního souboru

1. Deklarujte vašemu naslouchacímu procesu trasování v konfiguračním souboru aplikace. Pokud naslouchací proces, který vytváříte vyžaduje další objekty, a je deklarujte. Následující příklad ukazuje, jak vytvořit naslouchací proces nazvaný `myListener` , která zapisuje do textového souboru `TextWriterOutput.log`.

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

2. Použití <xref:System.Diagnostics.Trace> třídy v kódu k zápisu zprávy pro posluchače trasování.

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

### <a name="to-create-and-use-a-trace-listener-in-code"></a>Vytvoření a použití naslouchací proces trasování v kódu

- Přidat naslouchací proces trasování do <xref:System.Diagnostics.Trace.Listeners%2A> kolekce a odeslat informace o pro posluchače trasování.

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

    \- nebo –

- Pokud nechcete, aby vašemu naslouchacímu procesu pro příjem výstup trasování, nepřidávejte tak, <xref:System.Diagnostics.Trace.Listeners%2A> kolekce. Můžete generovat výstup prostřednictvím nezávisle na naslouchací proces <xref:System.Diagnostics.Trace.Listeners%2A> kolekce voláním naslouchacího procesu vlastní výstupu metody. Následující příklad ukazuje, jak napsat řádek na naslouchací proces, který není součástí <xref:System.Diagnostics.Trace.Listeners%2A> kolekce.

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

## <a name="see-also"></a>Viz také:

- [Moduly naslouchání trasování](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [Přepínače trasování](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [Postupy: Přidání příkazů trasování do kódu aplikace](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [Trasování a instrumentace aplikací](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
