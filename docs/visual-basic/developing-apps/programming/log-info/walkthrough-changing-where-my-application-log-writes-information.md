---
title: Změna místa, kam objekt My.Application.Log zapisuje informace
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
ms.openlocfilehash: bdee0a91360580b156c1734ef4c82139b18ce2b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74336734"
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a>Návod: Změna místa, kam objekt My.Application.Log zapisuje informace (Visual Basic)

Objekty `My.Application.Log` a `My.Log` můžete použít k protokolování informací o událostech, ke kterým dochází ve vaší aplikaci. Tento návod ukazuje, jak přepsat výchozí nastavení `Log` a způsobit, že objekt zapisovat do jiných posluchačů protokolu.

## <a name="prerequisites"></a>Požadavky

Objekt `Log` může zapisovat informace do několika naslouchacích procesů protokolu. Před změnou konfigurací je třeba určit aktuální konfiguraci posluchačů protokolu. Další informace naleznete [v tématu Návod: Určení, kde my.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).

Můžete si přečíst [postup: Zápis informací o události do textového souboru](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) nebo [Jak: Zápis do protokolu událostí aplikace](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).

### <a name="to-add-listeners"></a>Přidání posluchačů

1. Klepněte pravým tlačítkem myši na soubor app.config v **Průzkumníku řešení** a zvolte **Otevřít**.

     \-nebo -

     Pokud není k dispozici žádný soubor app.config:

    1. V nabídce **Projekt** zvolte **Přidat novou položku**.

    2. V dialogovém okně **Přidat novou položku** vyberte **Konfigurační soubor aplikace**.

    3. Klikněte na **Přidat**.

2. Vyhledejte `<listeners>` oddíl pod `<source>` oddílem `name` s atributem "DefaultSource" v `<sources>` části. Sekce `<sources>` je v `<system.diagnostics>` sekci, v horní `<configuration>` části.

3. Přidejte tyto `<listeners>` prvky do tohoto oddílu.

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

4. Odkomentujte posluchače protokolu, `Log` které chcete přijímat zprávy.

5. Vyhledejte `<sharedListeners>` oddíl v `<system.diagnostics>` části v části `<configuration>` nejvyšší úrovně.

6. Přidejte tyto `<sharedListeners>` prvky do tohoto oddílu.

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

7. Obsah souboru app.config by měl být podobný následujícímu xml:

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

### <a name="to-reconfigure-a-listener"></a>Změna konfigurace naslouchací proces

1. Vyhledejte `<add>` prvek posluchače `<sharedListeners>` z oddílu.

2. Atribut `type` udává název typu naslouchací proces. Tento typ musí <xref:System.Diagnostics.TraceListener> dědit z třídy. Pomocí silně pojmenovaného názvu typu zajistěte, aby byl použit správný typ. Další informace naleznete v části "Chcete-li odkazovat na silně pojmenovaný typ" níže.

     Některé typy, které můžete použít, jsou:

    - Naslouchací <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> proces, který zapisuje do protokolu souborů.

    - Naslouchací <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> proces, který zapisuje informace do protokolu událostí počítače určeného parametrem. `initializeData`

    - A <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> naslouchací procesy, `initializeData` které zapisují do souboru určeného v parametru.

    - Naslouchací <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> proces, který zapisuje do konzoly příkazového řádku.

     Informace o tom, kde jiné typy posluchačů protokolu psát informace, naleznete v dokumentaci tohoto typu.

3. Když aplikace vytvoří objekt posluchače protokolu, `initializeData` předá atribut jako parametr konstruktoru. Význam atributu `initializeData` závisí na naslouchací proces trasování.

4. Po vytvoření naslouchací proces protokolu aplikace nastaví vlastnosti posluchače. Tyto vlastnosti jsou definovány ostatními atributy v elementu. `<add>` Další informace o vlastnostech pro konkrétní naslouchací proces naleznete v dokumentaci k typu tohoto naslouchacího procesu.

### <a name="to-reference-a-strongly-named-type"></a>Odkaz na silně pojmenovaný typ

1. Chcete-li zajistit, že správný typ se používá pro posluchače protokolu, ujistěte se, že používáte plně kvalifikovaný název typu a silně pojmenovaný název sestavení. Syntaxe silně pojmenovaného typu je následující:

     \<*název>,* \< *název* sestavení \<>, \<číslo *verze*>,> jazykové *verze,* \< *silný název*>

2. Tento příklad kódu ukazuje, jak určit silně pojmenovaný název typu pro plně kvalifikovaný typ – "System.Diagnostics.FileLogTraceListener" v tomto případě.

     [!code-vb[VbVbalrMyApplicationLog#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#15)]

     Toto je výstup a lze jej použít k jedinečným odkazem na silně pojmenovaný typ, jako v postupu "Chcete-li přidat posluchače" výše.

     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>
- <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>
- [Postupy: Zápis informací o události do textového souboru](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)
- [Postupy: Zápis do protokolu událostí aplikace](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)
