---
title: 'Postupy: Vytváření a inicializace naslouchacích procesů trasování'
description: Naučte se vytvářet a inicializovat naslouchací procesy trasování pomocí tříd, jako je System. Diagnostics. DefaultTraceListener v rozhraní .NET.
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
ms.openlocfilehash: 752306124e41a7fb7458daccc8c2891631eb9616
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051204"
---
# <a name="how-to-create-and-initialize-trace-listeners"></a>Postupy: Vytváření a inicializace naslouchacích procesů trasování

<xref:System.Diagnostics.Debug?displayProperty=nameWithType>Třídy a <xref:System.Diagnostics.Trace?displayProperty=nameWithType> odesílají zprávy do objektů nazývaných naslouchací procesy, které přijímají a zpracovávají tyto zprávy. Jeden takový naslouchací proces, <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType> je automaticky vytvořen a inicializován v případě, že je povoleno trasování nebo ladění. Chcete-li <xref:System.Diagnostics.Trace> <xref:System.Diagnostics.Debug> , aby byl výstup směrován do dalších zdrojů, je nutné vytvořit a inicializovat další naslouchací procesy trasování.

Naslouchací procesy, které vytvoříte, by měly odpovídat potřebám vaší aplikace. Například pokud chcete textový záznam všech výstupů trasování, vytvořte <xref:System.Diagnostics.TextWriterTraceListener> naslouchací proces, který zapíše veškerý výstup do nového textového souboru, pokud je povolen. Na druhé straně, pokud chcete zobrazit výstup pouze během provádění aplikace, vytvořte <xref:System.Diagnostics.ConsoleTraceListener> naslouchací proces, který směruje veškerý výstup do okna konzoly. <xref:System.Diagnostics.EventLogTraceListener>Může směrovat výstup trasování do protokolu událostí. Další informace naleznete v tématu [Trace Listeners](trace-listeners.md).

Naslouchací procesy trasování lze vytvořit v [konfiguračním souboru aplikace](../configure-apps/index.md) nebo v kódu. Doporučujeme použít konfigurační soubory aplikace, protože umožňují přidat, upravit nebo odebrat naslouchací procesy trasování bez nutnosti měnit kód.

### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a>Vytvoření a použití naslouchacího procesu trasování pomocí konfiguračního souboru

1. Deklarujte naslouchací proces trasování v konfiguračním souboru aplikace. Pokud naslouchací proces, který vytváříte, vyžaduje jiné objekty, deklarujte je také. Následující příklad ukazuje, jak vytvořit naslouchací proces s názvem `myListener` , který zapisuje do textového souboru `TextWriterOutput.log` .

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

2. Použijte <xref:System.Diagnostics.Trace> třídu v kódu k zápisu zprávy do posluchačů trasování.

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

- Přidejte naslouchací proces trasování do <xref:System.Diagnostics.Trace.Listeners%2A> kolekce a odešlete trasovací informace do posluchačů.

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

    \-ani

- Pokud nechcete, aby naslouchací proces přijímal výstup trasování, nepřidávejte ho do <xref:System.Diagnostics.Trace.Listeners%2A> kolekce. Můžete vygenerovat výstup pomocí naslouchacího procesu nezávisle na <xref:System.Diagnostics.Trace.Listeners%2A> kolekci voláním metod vlastního výstupu naslouchacího procesu. Následující příklad ukazuje, jak zapsat řádek do naslouchacího procesu, který není v <xref:System.Diagnostics.Trace.Listeners%2A> kolekci.

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
