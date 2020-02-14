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
ms.openlocfilehash: ce0df0af32d6798c89c8db6761d18febc1c398bb
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217445"
---
# <a name="how-to-create-and-initialize-trace-listeners"></a>Postupy: Vytváření a inicializace naslouchacích procesů trasování

Třídy <xref:System.Diagnostics.Debug?displayProperty=nameWithType> a <xref:System.Diagnostics.Trace?displayProperty=nameWithType> odesílají zprávy do objektů nazývaných naslouchací procesy, které přijímají a zpracovávají tyto zprávy. Jeden takový naslouchací proces, <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, je automaticky vytvořen a inicializován v případě, že je povoleno trasování nebo ladění. Pokud chcete, aby byl výstup <xref:System.Diagnostics.Trace> nebo <xref:System.Diagnostics.Debug> směrován do dalších zdrojů, je nutné vytvořit a inicializovat další naslouchací procesy trasování.

Naslouchací procesy, které vytvoříte, by měly odpovídat potřebám vaší aplikace. Například pokud chcete textový záznam všech výstupů trasování, vytvořte <xref:System.Diagnostics.TextWriterTraceListener> naslouchací proces, který zapíše veškerý výstup do nového textového souboru, pokud je povolen. Na druhé straně, pokud chcete zobrazit výstup pouze během provádění aplikace, vytvořte <xref:System.Diagnostics.ConsoleTraceListener> naslouchací proces, který přesměruje výstup do okna konzoly. <xref:System.Diagnostics.EventLogTraceListener> může směrovat výstup trasování do protokolu událostí. Další informace naleznete v tématu [Trace Listeners](trace-listeners.md).

Naslouchací procesy trasování lze vytvořit v [konfiguračním souboru aplikace](../configure-apps/index.md) nebo v kódu. Doporučujeme použít konfigurační soubory aplikace, protože umožňují přidat, upravit nebo odebrat naslouchací procesy trasování bez nutnosti měnit kód.

### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a>Vytvoření a použití naslouchacího procesu trasování pomocí konfiguračního souboru

1. Deklarujte naslouchací proces trasování v konfiguračním souboru aplikace. Pokud naslouchací proces, který vytváříte, vyžaduje jiné objekty, deklarujte je také. Následující příklad ukazuje, jak vytvořit naslouchací proces nazvaný `myListener`, který zapisuje do textového souboru `TextWriterOutput.log`.

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

2. Použijte třídu <xref:System.Diagnostics.Trace> v kódu k zápisu zprávy do posluchačů trasování.

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

### <a name="to-create-and-use-a-trace-listener-in-code"></a>Vytvoření a použití naslouchacího procesu trasování v kódu

- Přidejte naslouchací proces trasování do kolekce <xref:System.Diagnostics.Trace.Listeners%2A> a odešlete trasovací informace do posluchačů.

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

    \- nebo-

- Pokud nechcete, aby naslouchací proces přijímal výstup trasování, nepřidávejte ho do kolekce <xref:System.Diagnostics.Trace.Listeners%2A>. Můžete vygenerovat výstup pomocí naslouchacího procesu nezávisle na kolekci <xref:System.Diagnostics.Trace.Listeners%2A> voláním metod vlastního výstupu naslouchacího procesu. Následující příklad ukazuje, jak zapsat řádek do naslouchacího procesu, který není v kolekci <xref:System.Diagnostics.Trace.Listeners%2A>.

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

- [Moduly naslouchání trasování](trace-listeners.md)
- [Přepínače trasování](trace-switches.md)
- [Postupy: Přidání příkazů trasování do kódu aplikace](how-to-add-trace-statements-to-application-code.md)
- [Trasování a instrumentace aplikací](tracing-and-instrumenting-applications.md)
