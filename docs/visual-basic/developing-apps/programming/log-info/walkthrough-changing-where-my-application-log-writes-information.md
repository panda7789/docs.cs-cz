---
title: Změna, kam objekt My.Application.Log zapisuje informace (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
ms.openlocfilehash: ab46f192f2e9549d0568737236742a366ce7b3a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592207"
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a>Návod: Změna místa, kam objekt My.Application.Log zapisuje informace (Visual Basic)
Můžete použít `My.Application.Log` a `My.Log` objekty k protokolování informací o událostech, ke kterým dochází ve vaší aplikaci. Tento návod ukazuje, jak přepíší výchozí nastavení, a způsobit, že `Log` objektu k zápisu do jiných součástí naslouchajících protokolům.  
  
## <a name="prerequisites"></a>Požadavky  
 `Log` Objekt může zapsat informace do několika naslouchací procesy pro protokoly. Je nutné určit aktuální konfiguraci naslouchacího procesu protokolu před změnou konfigurace. Další informace najdete v tématu [návod: určení kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
 Chcete zkontrolovat [postupy: zápis informací o události do textového souboru](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) nebo [postupy: zápis do protokolu událostí aplikace](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).  
  
### <a name="to-add-listeners"></a>Chcete-li přidat moduly naslouchání  
  
1.  Klikněte pravým tlačítkem na app.config v **Průzkumníku řešení** a zvolte **otevřete**.  
  
     \- nebo –  
  
     Pokud není dostupný žádný soubor app.config:  
  
    1.  Na **projektu** nabídce zvolte **přidat novou položku**.  
  
    2.  Z **přidat novou položku** dialogové okno, vyberte **konfigurační soubor aplikace**.  
  
    3.  Klikněte na tlačítko **přidat**.  
  
2.  Vyhledejte `<listeners>` v oblasti `<source>` část s `name` atribut "DefaultSource", `<sources>` části. `<sources>` Oddíl je ve `<system.diagnostics>` oddílem se v nejvyšší úrovně `<configuration>` části.  
  
3.  Přidat tyto prvky, `<listeners>` části.  
  
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
  
4.  Zrušením komentáře u naslouchací procesy protokolu, které chcete dostávat `Log` zprávy.  
  
5.  Vyhledejte `<sharedListeners>` v části `<system.diagnostics>` oddílem se v nejvyšší úrovně `<configuration>` části.  
  
6.  Přidat tyto prvky, `<sharedListeners>` části.  
  
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
  
7.  Obsah souboru app.config by měl vypadat přibližně následující kód XML:  
  
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
  
1.  Vyhledejte naslouchacího procesu `<add>` element z `<sharedListeners>` oddílu.  
  
2.  `type` Atribut poskytuje název typu naslouchací proces. Tento typ musí dědit z <xref:System.Diagnostics.TraceListener> třídy. Použijte název silně pojmenované typy zajistit, že se používá správný typ. Další informace najdete v části "tak, aby odkazovaly na silně pojmenované typy".  
  
     Některé typy, které můžete použít jsou:  
  
    -   A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> naslouchací proces, který zapisuje do souboru protokolu.  
  
    -   A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> naslouchací proces, který zapisuje informace do protokolu událostí počítače určeného `initializeData` parametr.  
  
    -   <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> a <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> zapisují do zadaného v souboru `initializeData` parametr.  
  
    -   A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> naslouchací proces, který zapisuje do konzoly nástroje příkazového řádku.  
  
     Informace o kde jiné typy naslouchací procesy protokolu zapisují informace najdete v dokumentaci daného typu.  
  
3.  Aplikace vytvoří objekt protokolu naslouchání, předává `initializeData` atribut jako parametr konstruktoru. Význam `initializeData` atribut závisí na naslouchací proces trasování.  
  
4.  Po vytvoření naslouchacího procesu protokolu, aplikace nastaví vlastnosti naslouchacího procesu. Tyto vlastnosti jsou definované atributy v `<add>` elementu. Další informace o vlastnostech pro příslušného naslouchacího procesu naleznete v dokumentaci pro typ této naslouchací proces.  
  
### <a name="to-reference-a-strongly-named-type"></a>Chcete-li typu silně pojmenované  
  
1.  Aby se zajistilo, že správné typ se používá pro vaše naslouchací proces protokolu, nezapomeňte použít název plně kvalifikovaný typ a název silně pojmenované sestavení. Silně pojmenované typy syntaxe vypadá takto:  
  
     \<*Název typu*>, \< *název sestavení*>, \< *číslo verze*>, \< *jazykovou verzi*>, \< *silným názvem*>  
  
2.  Tento příklad kódu ukazuje, jak určit název silně pojmenovaného typu pro plně kvalifikovaný Systen.Diagnostics.FileLogTraceListener"v tomto případě.  
  
     [!code-vb[VbVbalrMyApplicationLog#15](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-changing-where-my-application-log-writes-information_1.vb)]  
  
     Toto je výstup a může sloužit k jednoznačné odkazovat silně pojmenované typy, jako "Chcete-li přidat moduly pro naslouchání" výše uvedený postup.  
  
     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>  
 <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>  
 [Postupy: Zápis informací o události do textového souboru](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)  
 [Postupy: Zápis do protokolu událostí aplikace](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)
