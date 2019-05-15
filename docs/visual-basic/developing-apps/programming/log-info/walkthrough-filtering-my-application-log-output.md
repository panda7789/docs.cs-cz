---
title: Filtrování výstupu My.Application.Log (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
ms.openlocfilehash: 00e9eeb3227ceef54f899129847bfb74a370c51c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591280"
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a>Návod: Filtrování výstupu My.Application.Log (Visual Basic)
Tento návod ukazuje, jak změnit výchozí filtrování pro protokolování `My.Application.Log` objekt řídit, jaké informace jsou předány z `Log` objektu pro naslouchací procesy a jaké informace jsou zapsány pomocí naslouchací procesy. Protokolování chování můžete změnit i po vytvoření aplikace, protože informace o konfiguraci jsou uložena v konfiguračním souboru aplikace.  
  
## <a name="getting-started"></a>Začínáme  
 Každá zpráva, která `My.Application.Log` zápisy má přidruženou úroveň závažnosti, která filtrování mechanismy používají k řízení výstup protokolu. Tato ukázková aplikace používá `My.Application.Log` metody zapsat několik zprávy protokolu s různou úrovní závažnosti.  
  
#### <a name="to-build-the-sample-application"></a>K vytvoření ukázkové aplikace  
  
1. Otevřete nový projekt aplikace Windows jazyka Visual Basic.  
  
2. Přidejte tlačítko s názvem Button1 Form1.  
  
3. V <xref:System.Windows.Forms.Control.Click> obslužné rutiny události pro Button1, přidejte následující kód:  
  
     [!code-vb[VbVbcnMyApplicationLogFiltering#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyApplicationLogFiltering/VB/Form1.vb#1)]  
  
4. Spusťte aplikaci v ladicím programu.  
  
5. Stisknutím klávesy **Button1**.  
  
     Aplikace tyto informace zapisuje do souboru výstupu a protokolů ladění aplikace.  
  
     `DefaultSource Information: 0 : In Button1_Click`  
  
     `DefaultSource Error: 2 : Error in the application.`  
  
6. Ukončete aplikaci.  
  
     Informace o tom, jak zobrazit okno výstupu ladění vaší aplikace najdete v tématu [okno výstup](/visualstudio/ide/reference/output-window). Informace o umístění souboru protokolu aplikace naleznete v tématu [názorný postup: Určení, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
    > [!NOTE]
    >  Ve výchozím nastavení vyprázdní aplikace výstupní soubor protokolu po zavření aplikace.  
  
     V příkladu výše, druhé volání <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> metoda a volání <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> metoda vytvoří výstup protokolu, při prvním a posledním volání `WriteEntry` metoda tomu tak není. Důvodem je, že úrovně závažnosti `WriteEntry` a `WriteException` jsou "informace o" a "Chyba", které by jsou povolené `My.Application.Log` objektu výchozí filtrování protokolu. Ale události pomocí "Start" a "Stop" úrovně závažnosti bránit vytváření výstupu protokolu.  
  
## <a name="filtering-for-all-myapplicationlog-listeners"></a>Filtrování pro všechny moduly pro naslouchání My.Application.Log  
 `My.Application.Log` Objektu používá <xref:System.Diagnostics.SourceSwitch> s názvem `DefaultSwitch` řídit, která zprávy ji passů z `WriteEntry` a `WriteException` metody pro součásti naslouchající protokolům. Můžete nakonfigurovat `DefaultSwitch` v konfiguračním souboru aplikace tak, že nastavíte její hodnotu na některý <xref:System.Diagnostics.SourceLevels> hodnot výčtu. Ve výchozím nastavení jeho hodnota je "Informace".  
  
 Tato tabulka ukazuje úroveň závažnosti, vyžaduje se pro protokol a zapsat zprávu do naslouchacích procesů, daný konkrétní `DefaultSwitch` nastavení.  
  
|Hodnota DefaultSwitch|Závažnost zprávy vyžaduje pro výstup|  
|---|---| 
|`Critical`|`Critical`|  
|`Error`|`Critical` Nebo `Error`|  
|`Warning`|`Critical`, `Error`, nebo `Warning`|  
|`Information`|`Critical`, `Error`, `Warning`, nebo `Information`|  
|`Verbose`|`Critical`, `Error`, `Warning`, `Information`, nebo `Verbose`|  
|`ActivityTracing`|`Start`, `Stop`, `Suspend`, `Resume`, nebo `Transfer`|  
|`All`|Jsou povoleny všechny zprávy.|  
|`Off`|Všechny zprávy bylo zablokováno.|  
  
> [!NOTE]
>  `WriteEntry` a `WriteException` má každá z metod přetížení, které neurčuje úroveň závažnosti. Implicitní úroveň závažnosti pro `WriteEntry` přetížení je "Informace" a implicitní úroveň závažnosti pro `WriteException` přetížení je "Chyba".  
  
 Tato tabulka popisuje výstupu protokolu v předchozím příkladu: s výchozím `DefaultSwitch` nastavení "Informace", pouze druhé volání `WriteEntry` metoda a volání `WriteException` metoda výstupu protokolu produktu.  
  
#### <a name="to-log-only-activity-tracing-events"></a>Protokolovat události trasování pouze aktivity  
  
1. Klikněte pravým tlačítkem na app.config **Průzkumníka řešení** a vyberte **otevřít**.  
  
     -nebo-  
  
     Pokud není dostupný žádný soubor app.config:  
  
    1. Na **projektu** nabídce zvolte **přidat novou položku**.  
  
    2. Z **přidat novou položku** dialogového okna zvolte **konfiguračního souboru aplikace**.  
  
    3. Klikněte na **Přidat**.  
  
2. Vyhledejte `<switches>` oddíl, což je v `<system.diagnostics>` oddíl, což je na nejvyšší úrovni `<configuration>` oddílu.  
  
3. Najít element, který přidá `DefaultSwitch` do kolekce přepínače. By měla vypadat podobně jako tento element:  
  
     `<add name="DefaultSwitch" value="Information" />`  
  
4. Změňte hodnotu `value` atribut "ActivityTracing".  
  
5. Obsah souboru app.config by měl být podobně jako následující kód XML:  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <!-- This section configures My.Application.Log -->  
          <source name="DefaultSource" switchName="DefaultSwitch">  
            <listeners>  
              <add name="FileLog"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="DefaultSwitch" value="ActivityTracing" />  
        </switches>  
        <sharedListeners>  
          <add name="FileLog"  
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
                     Microsoft.VisualBasic, Version=8.0.0.0,   
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,   
                     processorArchitecture=MSIL"   
               initializeData="FileLogWriter"/>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
6. Spusťte aplikaci v ladicím programu.  
  
7. Stisknutím klávesy **Button1**.  
  
     Aplikace zapíše do souboru výstupu a protokolů ladění aplikace následující informace:  
  
     `DefaultSource Start: 4 : Entering Button1_Click`  
  
     `DefaultSource Stop: 5 : Leaving Button1_Click`  
  
8. Ukončete aplikaci.  
  
9. Změňte hodnotu `value` atribut "Informace".  
  
    > [!NOTE]
    >  `DefaultSwitch` Přepněte nastavení řídí pouze `My.Application.Log`. Nezmění, jak rozhraní .NET Framework <xref:System.Diagnostics.Trace?displayProperty=nameWithType> a <xref:System.Diagnostics.Debug?displayProperty=nameWithType> třídy chovají.  
  
## <a name="individual-filtering-for-myapplicationlog-listeners"></a>Jednotlivé filtrování pro naslouchací procesy My.Application.Log  
 Předchozí příklad ukazuje, jak změnit filtrování pro všechny `My.Application.Log` výstup. Tento příklad ukazuje, jak filtrovat naslouchací proces vlastní protokol. Aplikace má ve výchozím nastavení dva naslouchací procesy tento zápis do výstupu ladění vaší aplikace a souboru protokolu.  
  
 Konfigurační soubor řídí chování součásti naslouchající protokolům tím, že každý z nich mít filtr, který je podobný přepínač pro `My.Application.Log`. Naslouchací proces protokolu bude výstup v podobě zprávy pouze v případě, že povoluje závažnost zprávy obou protokolu `DefaultSwitch` a naslouchacího procesu protokolu filtru.  
  
 Tento příklad ukazuje, jak nakonfigurovat filtrování pro nový naslouchací proces ladění a přidejte ji tak `Log` objektu. Naslouchací proces ladění výchozí by měly odebrat z `Log` objektu, aby bylo zřejmé, že tyto zprávy pocházejí z nový naslouchací proces ladění.  
  
#### <a name="to-log-only-activity-tracing-events"></a>Aby se protokolovaly pouze události trasování činnosti  
  
1. Klikněte pravým tlačítkem na app.config **Průzkumníka řešení** a zvolte **otevřít**.  
  
     -nebo-  
  
     Pokud není dostupný žádný soubor app.config:  
  
    1. Na **projektu** nabídce zvolte **přidat novou položku**.  
  
    2. Z **přidat novou položku** dialogového okna zvolte **konfiguračního souboru aplikace**.  
  
    3. Klikněte na **Přidat**.  
  
2. Klikněte pravým tlačítkem na app.config **Průzkumníka řešení**. Zvolte **otevřít**.  
  
3. Vyhledejte `<listeners>` sekci `<source>` části s `name` atribut "DefaultSource", což je v části `<sources>` oddílu. `<sources>` Oddíl je v části `<system.diagnostics>` části na nejvyšší úrovni `<configuration>` oddílu.  
  
4. Přidání tohoto elementu `<listeners>` části:  
  
    ```xml  
    <!-- Remove the default debug listener. -->  
    <remove name="Default"/>  
    <!-- Add a filterable debug listener. -->  
    <add name="NewDefault"/>  
    ```  
  
5. Vyhledejte `<sharedListeners>` sekci `<system.diagnostics>` části na nejvyšší úrovni `<configuration>` oddílu.  
  
6. Přidejte tento element, který `<sharedListeners>` části:  
  
    ```xml  
    <add name="NewDefault"   
         type="System.Diagnostics.DefaultTraceListener,   
               System, Version=2.0.0.0, Culture=neutral,   
               PublicKeyToken=b77a5c561934e089,   
               processorArchitecture=MSIL">  
        <filter type="System.Diagnostics.EventTypeFilter"   
                initializeData="Error" />  
    </add>  
    ```  
  
     <xref:System.Diagnostics.EventTypeFilter> Filtru má jednu z <xref:System.Diagnostics.SourceLevels> hodnot výčtu jako jeho `initializeData` atribut.  
  
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
              <!-- Remove the default debug listener. -->  
              <remove name="Default"/>  
              <!-- Add a filterable debug listener. -->  
              <add name="NewDefault"/>  
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
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,   
                     processorArchitecture=MSIL"   
               initializeData="FileLogWriter"/>  
          <add name="NewDefault"   
               type="System.Diagnostics.DefaultTraceListener,   
                     System, Version=2.0.0.0, Culture=neutral,   
                     PublicKeyToken=b77a5c561934e089,   
                     processorArchitecture=MSIL">  
            <filter type="System.Diagnostics.EventTypeFilter"   
                    initializeData="Error" />  
          </add>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
8. Spusťte aplikaci v ladicím programu.  
  
9. Stisknutím klávesy **Button1**.  
  
     Aplikace zapíše do souboru protokolu k aplikaci následující informace:  
  
     `Default Information: 0 : In Button1_Click`  
  
     `Default Error: 2 : Error in the application.`  
  
     Aplikace zapíše méně informací do výstupu ladění vaší aplikace z důvodu více omezující filtrování.  
  
     `Default Error   2   Error`  
  
10. Ukončete aplikaci.  
  
 Další informace o změnách nastavení protokolu po nasazení najdete v tématu [práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).  
  
## <a name="see-also"></a>Viz také:

- [Návod: Určení, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [Návod: Změna, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [Návod: Vytváření vlastních součástí naslouchajících protokolům](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)
- [Postupy: Zápis zpráv protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Přepínače trasování](../../../../framework/debug-trace-profile/trace-switches.md)
- [Protokolování informací z aplikace](../../../../visual-basic/developing-apps/programming/log-info/index.md)
