---
title: Změna místa, kam aplikace My. Application. Log zapisuje informace (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
ms.openlocfilehash: 358638d50e347334487665b950b33a045b6a39f9
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524406"
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a>Návod: Změna místa, kam objekt My.Application.Log zapisuje informace (Visual Basic)

Pomocí objektů `My.Application.Log` a `My.Log` můžete protokolovat informace o událostech, ke kterým dochází ve vaší aplikaci. Tento návod ukazuje, jak přepsat výchozí nastavení a způsobit, `Log` objekt zapisovat do jiných posluchačů protokolů.

## <a name="prerequisites"></a>Požadavky

Objekt `Log` může zapisovat informace do několika posluchačů protokolů. Před změnou konfigurace je třeba určit aktuální konfiguraci naslouchacího procesu protokolu. Další informace naleznete v tématu [Návod: zjištění, kam aplikace My. Application. Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).

Můžete si přečíst [Postupy: zápis informací o události do textového souboru](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) nebo [Postupy: zápis do protokolu událostí aplikace](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).

### <a name="to-add-listeners"></a>Přidání posluchačů

1. V **Průzkumník řešení** klikněte pravým tlačítkem na soubor App. config a vyberte **otevřít**.

     \- nebo-

     Pokud neexistuje žádný soubor App. config:

    1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

    2. V dialogovém okně **Přidat novou položku** vyberte možnost **konfigurační soubor aplikace**.

    3. Klikněte na tlačítko **Přidat**.

2. Vyhledejte část `<listeners>` v části `<source>` s atributem `name` "DefaultSource" v části pro `<sources>`. Část `<sources>` je v části `<system.diagnostics>` v části `<configuration>` nejvyšší úrovně.

3. Přidejte tyto prvky do oddílu `<listeners>`.

    ```xml
    <!-- Uncomment to connect the application file log. -->
    <!-- <add name="FileLog" /> -->
    <!-- Uncomment to connect the event log. -->
    <!-- <add name="EventLog" /> -->
    <!-- Uncomment to connect the event log. -->
    <!-- <add name="Delimited" /> -->
    <!-- Uncomment to connect the XML log. -->
    <!-- <add name="XmlWriter" /> -->
    <!-- Uncomment to connect the console log. -->
    <!-- <add name="Console" /> -->
    ```

4. Odkomentujte naslouchací procesy protokolů, které chcete dostávat `Log` zprávy.

5. Vyhledejte část `<sharedListeners>` v části `<system.diagnostics>` v části `<configuration>` nejvyšší úrovně.

6. Přidejte tyto prvky do oddílu `<sharedListeners>`.

    ```xml
    <add name="FileLog"
         type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
               Microsoft.VisualBasic, Version=8.0.0.0,
               Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
         initializeData="FileLogWriter" />
    <add name="EventLog"
         type="System.Diagnostics.EventLogTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="sample application"/>
    <add name="Delimited"
         type="System.Diagnostics.DelimitedListTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="c:\temp\sampleDelimitedFile.txt"
         traceOutputOptions="DateTime" />
    <add name="XmlWriter"
         type="System.Diagnostics.XmlWriterTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="c:\temp\sampleLogFile.xml" />
    <add name="Console"
         type="System.Diagnostics.ConsoleTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="true" />
    ```

7. Obsah souboru App. config by měl vypadat podobně jako následující kód XML:

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.diagnostics>
        <sources>
          <!-- This section configures My.Application.Log -->
          <source name="DefaultSource" switchName="DefaultSwitch">
            <listeners>
              <add name="FileLog"/>
              <!-- Uncomment to connect the application file log. -->
              <!-- <add name="FileLog" /> -->
              <!-- Uncomment to connect the event log. -->
              <!-- <add name="EventLog" /> -->
              <!-- Uncomment to connect the event log. -->
              <!-- <add name="Delimited" /> -->
              <!-- Uncomment to connect the XML log. -->
              <!-- <add name="XmlWriter" /> -->
              <!-- Uncomment to connect the console log. -->
              <!-- <add name="Console" /> -->
            </listeners>
          </source>
        </sources>
        <switches>
          <add name="DefaultSwitch" value="Information" />
        </switches>
        <sharedListeners>
          <add name="FileLog"
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
                     Microsoft.VisualBasic, Version=8.0.0.0,
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
               initializeData="FileLogWriter" />
          <add name="EventLog"
               type="System.Diagnostics.EventLogTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="sample application"/>
          <add name="Delimited"
               type="System.Diagnostics.DelimitedListTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="c:\temp\sampleDelimitedFile.txt"
               traceOutputOptions="DateTime" />
          <add name="XmlWriter"
               type="System.Diagnostics.XmlWriterTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="c:\temp\sampleLogFile.xml" />
          <add name="Console"
               type="System.Diagnostics.ConsoleTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="true" />
        </sharedListeners>
      </system.diagnostics>
    </configuration>
    ```

### <a name="to-reconfigure-a-listener"></a>Postup překonfigurování naslouchacího procesu

1. V části `<sharedListeners>` vyhledejte `<add>` element naslouchacího procesu.

2. Atribut `type` poskytuje název typu naslouchacího procesu. Tento typ musí dědit z třídy <xref:System.Diagnostics.TraceListener>. Použijte název silně pojmenovaného typu k zajištění toho, aby byl použit správný typ. Další informace naleznete níže v části "odkazování na silně pojmenovaný typ".

     Mezi typy, které můžete použít, patří:

    - Naslouchací proces <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>, který zapisuje do protokolu souborů.

    - @No__t_0 naslouchací proces, který zapisuje informace do protokolu událostí počítače určeného parametrem `initializeData`.

    - Naslouchací procesy <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> a <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>, které zapisují do souboru zadaného v parametru `initializeData`.

    - Naslouchací proces <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>, který zapisuje do konzoly příkazového řádku.

     Informace o tom, kde jiné typy protokolových posluchačů zapisují informace, najdete v dokumentaci k tomuto typu.

3. Když aplikace vytvoří objekt naslouchacího procesu protokolu, předá atribut `initializeData` jako parametr konstruktoru. Význam atributu `initializeData` závisí na naslouchací službě trasování.

4. Po vytvoření naslouchacího procesu protokolu aplikace nastaví vlastnosti naslouchacího procesu. Tyto vlastnosti jsou definovány jinými atributy v prvku `<add>`. Další informace o vlastnostech konkrétního naslouchacího procesu najdete v dokumentaci pro daný typ naslouchacího procesu.

### <a name="to-reference-a-strongly-named-type"></a>Odkazování na silně pojmenovaný typ

1. Chcete-li zajistit, aby byl pro naslouchací proces protokolu použit správný typ, nezapomeňte použít plně kvalifikovaný název typu a silně pojmenovaný název sestavení. Syntaxe silně pojmenovaného typu je následující:

     *název typu*\< >, \<*název sestavení*>, \<*číslo verze*>, \<*jazyková verze*>, \<*silný název* 0

2. Tento příklad kódu ukazuje, jak určit název silně pojmenovaného typu pro plně kvalifikovaný typ – "System. Diagnostics. FileLogTraceListener" v tomto případě.

     [!code-vb[VbVbalrMyApplicationLog#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#15)]

     Toto je výstup a lze jej použít k jedinečnému odkazu silně pojmenovaného typu, jak je uvedeno výše v proceduře "Přidat naslouchací procesy".

     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>
- <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>
- [Postupy: Zápis informací o události do textového souboru](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)
- [Postupy: Zápis do protokolu událostí aplikace](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)
