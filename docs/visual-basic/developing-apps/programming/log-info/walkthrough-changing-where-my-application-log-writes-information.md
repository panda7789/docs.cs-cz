---
title: Změna, kam objekt My.Application.Log zapisuje informace (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
ms.openlocfilehash: 56fef77448f3523732e755f57e8cdabe6ad71379
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59327643"
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a>Návod: Změna, kam objekt My.Application.Log zapisuje informace (Visual Basic)
Můžete použít `My.Application.Log` a `My.Log` objekty k protokolování informací o události, ke kterým dochází ve vaší aplikaci. Tento návod ukazuje, jak přepsat výchozí nastavení a způsobit, `Log` objekt k zápisu do jiných naslouchacích procesů protokolu.  
  
## <a name="prerequisites"></a>Požadavky  
 `Log` Objektu lze zapsat informace na několik součástí naslouchajících protokolům. Je nutné určit aktuální konfiguraci součásti naslouchající protokolům před změnou konfigurace. Další informace najdete v tématu [názorný postup: Určení, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
 Můžete chtít zkontrolovat [jak: Zápis informací o události do textového souboru](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) nebo [jak: Zápis do protokolu událostí aplikace](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).  
  
### <a name="to-add-listeners"></a>Chcete-li přidat naslouchací procesy  
  
1. Klikněte pravým tlačítkem na app.config **Průzkumníka řešení** a zvolte **otevřít**.  
  
     \- nebo –  
  
     Pokud není dostupný žádný soubor app.config:  
  
    1.  Na **projektu** nabídce zvolte **přidat novou položku**.  
  
    2.  Z **přidat novou položku** dialogu **konfiguračního souboru aplikace**.  
  
    3.  Klikněte na **Přidat**.  
  
2. Vyhledejte `<listeners>` pod `<source>` části s `name` atribut "DefaultSource" `<sources>` oddílu. `<sources>` Oddíl je ve `<system.diagnostics>` části na nejvyšší úrovni `<configuration>` oddílu.  
  
3. Přidejte tyto prvky do `<listeners>` oddílu.  
  
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
  
4. Zrušením komentáře u součásti naslouchající protokolům, které chcete dostávat `Log` zprávy.  
  
5. Vyhledejte `<sharedListeners>` sekci `<system.diagnostics>` části na nejvyšší úrovni `<configuration>` oddílu.  
  
6. Přidejte tyto prvky do `<sharedListeners>` oddílu.  
  
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
  
7. Obsah souboru app.config by měl být podobně jako následující kód XML:  
  
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
  
### <a name="to-reconfigure-a-listener"></a>Chcete-li překonfigurovat naslouchací proces  
  
1. Vyhledejte naslouchacího procesu `<add>` element z `<sharedListeners>` oddílu.  
  
2. `type` Atribut poskytuje název typu naslouchacího procesu. Tento typ musí dědit z <xref:System.Diagnostics.TraceListener> třídy. Chcete-li zajistit, aby používal správný typ použijte název silným názvem typu. Další informace najdete v části "k odkazování silným názvem typu".  
  
     Jsou některé typy, které můžete použít:  
  
    -   A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> naslouchací proces, který zapisuje do souboru protokolu.  
  
    -   A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> naslouchací proces, který zapisuje informace do protokolu událostí počítače určené `initializeData` parametru.  
  
    -   <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> a <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> naslouchacích procesů, které zapisovat do souboru zadaného v `initializeData` parametru.  
  
    -   A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> naslouchací proces, který zapisuje do konzoly příkazového řádku.  
  
     Informace o tom, kde psát jiných typů součástí naslouchajících protokolům informace najdete v dokumentaci tohoto typu.  
  
3. Když se aplikace vytvoří objekt protokolu naslouchací proces, předá `initializeData` atribut jako parametr konstruktoru. Význam `initializeData` atributu závisí na naslouchací služby stopy.  
  
4. Po vytvoření naslouchacího procesu protokolu aplikace nastaví vlastnosti naslouchacího procesu. Tyto vlastnosti jsou definovány další atributy `<add>` elementu. Další informace o vlastnostech pro příslušného naslouchacího procesu naleznete v dokumentaci pro typ tohoto naslouchacího procesu.  
  
### <a name="to-reference-a-strongly-named-type"></a>Chcete-li odkazovat na typ silným názvem  
  
1. Chcete-li zajistit, aby používal správný typ pro vaše naslouchací proces protokolu, nezapomeňte použít plně kvalifikovaného názvu a názvu sestavení se silným názvem. Syntaxe typu silným názvem je následujícím způsobem:  
  
     \<*Název typu*>, \< *název sestavení*>, \< *číslo verze*>, \< *jazykovou verzi*>, \< *silným názvem*>  
  
2. Tento příklad kódu ukazuje, jak určit název silně pojmenované typy pro plně kvalifikovaný Systen.Diagnostics.FileLogTraceListener"v tomto případě.  
  
     [!code-vb[VbVbalrMyApplicationLog#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#15)]  
  
     Toto je výstup, a to je možné jednoznačně odkazovat na typ silným názvem, stejně jako v "pro přidání posluchače" výše uvedeného postupu.  
  
     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>
- <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>
- [Postupy: Zápis informací o události do textového souboru](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)
- [Postupy: Zápis do protokolu událostí aplikace](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)
