---
title: Filtrování výstupu My.Application.Log (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
ms.openlocfilehash: 43ac92cefe717b4bfa64969839b289e944980b7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591882"
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a>Návod: Filtrování výstupu My.Application.Log (Visual Basic)
Tento návod ukazuje, jak změnit výchozí filtrování protokolování `My.Application.Log` objektu, k řízení, jaké informace jsou předány z `Log` objektu do posluchače a jaké informace jsou zapsány posluchači. I po vytvoření aplikace, můžete změnit chování protokolování, protože informace o konfiguraci je uložené v konfiguračním souboru aplikace.  
  
## <a name="getting-started"></a>Začínáme  
 Každá zpráva, které `My.Application.Log` zápisy má přidruženou úroveň závažnosti, které filtrování mechanismy používají k řízení výstup protokolu. Tato ukázková aplikace používá `My.Application.Log` metody k zápisu několik protokolování zpráv s různou úrovní závažnosti.  
  
#### <a name="to-build-the-sample-application"></a>K vytvoření ukázkové aplikace  
  
1.  Otevřete nový projekt aplikace Windows Visual Basic.  
  
2.  Přidání tlačítka s názvem Button1 do Form1.  
  
3.  V <xref:System.Windows.Forms.Control.Click> obslužné rutiny události pro Button1, přidejte následující kód:  
  
     [!code-vb[VbVbcnMyApplicationLogFiltering#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-filtering-my-application-log-output_1.vb)]  
  
4.  Spusťte aplikaci v ladicím programu.  
  
5.  Stiskněte klávesu **Button1**.  
  
     Aplikace zapisuje do souboru pro výstup a protokolu ladění aplikace následující informace.  
  
     `DefaultSource Information: 0 : In Button1_Click`  
  
     `DefaultSource Error: 2 : Error in the application.`  
  
6.  Zavřete aplikaci.  
  
     Informace o tom, jak zobrazit okno výstup ladění aplikace najdete v tématu [výstup – okno](/visualstudio/ide/reference/output-window). Informace o umístění souboru protokolu aplikace naleznete v tématu [návod: určení kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
    > [!NOTE]
    >  Ve výchozím nastavení aplikace vyprázdnění výstupní soubor protokolu, po ukončení aplikace.  
  
     V příkladu výše, druhé volání <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> metoda a volání <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> metoda vytvoří protokolový výstup, při prvním a posledním volání `WriteEntry` metoda nepodporují. Důvodem je, že úrovně závažnosti `WriteEntry` a `WriteException` jsou "Informace" a "Chyba" by jsou povolené oba tyto `My.Application.Log` objektu výchozí filtrování protokolu. Události se úrovně závažnosti "Start" a "Stop" však nebudou moci generovala výstup protokolu.  
  
## <a name="filtering-for-all-myapplicationlog-listeners"></a>Filtrování pro všechny naslouchací procesy My.Application.Log  
 `My.Application.Log` Objektu používá <xref:System.Diagnostics.SourceSwitch> s názvem `DefaultSwitch` řídit, která zprávy se předává z `WriteEntry` a `WriteException` metody pro naslouchací procesy protokolu. Můžete nakonfigurovat `DefaultSwitch` v konfiguračním souboru aplikace podle nastavení její hodnoty na jednu z <xref:System.Diagnostics.SourceLevels> hodnot výčtu. Ve výchozím nastavení jeho hodnota je "Informace".  
  
 Tato tabulka ukazuje úrovně závažnosti, pro protokol zapsat zprávu do naslouchací procesy, danou konkrétní `DefaultSwitch` nastavení.  
  
|Hodnota DefaultSwitch|Závažnost zprávy, které jsou potřebné pro výstup|  
|---|---| 
|`Critical`|`Critical`|  
|`Error`|`Critical` Nebo `Error`|  
|`Warning`|`Critical`, `Error`, nebo `Warning`|  
|`Information`|`Critical`, `Error`, `Warning`, nebo `Information`|  
|`Verbose`|`Critical`, `Error`, `Warning`, `Information`, nebo `Verbose`|  
|`ActivityTracing`|`Start`, `Stop`, `Suspend`, `Resume`, nebo `Transfer`|  
|`All`|Jsou povoleny všechny zprávy.|  
|`Off`|Všechny zprávy jsou zablokované.|  
  
> [!NOTE]
>  `WriteEntry` a `WriteException` každá z metod má přetížení, která neurčuje úroveň závažnosti. Implicitní úroveň závažnosti pro `WriteEntry` přetížení je "Informace" a implicitní úroveň závažnosti pro `WriteException` přetížení je "Chyba".  
  
 Tato tabulka vysvětluje protokolový výstup v předchozím příkladu: s výchozím `DefaultSwitch` nastavení "Informace", volat pouze druhý na `WriteEntry` metoda a volání `WriteException` metoda výstup protokolu produktu.  
  
#### <a name="to-log-only-activity-tracing-events"></a>Protokolování událostí trasování pouze aktivity  
  
1.  Klikněte pravým tlačítkem na app.config v **Průzkumníku řešení** a vyberte **otevřete**.  
  
     -nebo-  
  
     Pokud není dostupný žádný soubor app.config:  
  
    1.  Na **projektu** nabídce zvolte **přidat novou položku**.  
  
    2.  Z **přidat novou položku** dialogovém okně vyberte **konfigurační soubor aplikace**.  
  
    3.  Klikněte na tlačítko **přidat**.  
  
2.  Vyhledejte `<switches>` oddíl, což je v `<system.diagnostics>` oddíl, což je v nejvyšší úrovně `<configuration>` části.  
  
3.  Najděte element, který přidá `DefaultSwitch` ke kolekci přepínačů. By měl vypadat podobně jako tento element:  
  
     `<add name="DefaultSwitch" value="Information" />`  
  
4.  Změňte hodnotu `value` atributu na hodnotu "ActivityTracing".  
  
5.  Obsah souboru app.config by měl vypadat přibližně následující kód XML:  
  
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
  
6.  Spusťte aplikaci v ladicím programu.  
  
7.  Stiskněte klávesu **Button1**.  
  
     Aplikace zapisuje do souboru pro výstup a protokolu ladění aplikace následující informace:  
  
     `DefaultSource Start: 4 : Entering Button1_Click`  
  
     `DefaultSource Stop: 5 : Leaving Button1_Click`  
  
8.  Zavřete aplikaci.  
  
9. Změňte hodnotu `value` zpět na "Informace".  
  
    > [!NOTE]
    >  `DefaultSwitch` Přepínač pouze ovládací prvky pro nastavení `My.Application.Log`. Nemění jak [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Diagnostics.Trace?displayProperty=nameWithType> a <xref:System.Diagnostics.Debug?displayProperty=nameWithType> chovat třídy.  
  
## <a name="individual-filtering-for-myapplicationlog-listeners"></a>Jednotlivé filtrování pro naslouchací procesy My.Application.Log  
 Předchozí příklad ukazuje, jak změnit filtrování pro všechny `My.Application.Log` výstup. Tento příklad ukazuje, jak filtrovat naslouchací proces vlastní protokol. Ve výchozím nastavení má aplikace dva naslouchací procesy tento zápis výstupu ladění aplikace a soubor protokolu.  
  
 Konfigurační soubor řídí chování součástí naslouchajících protokolům tím, že každé z nich má filtr, který je podobný přepínač pro `My.Application.Log`. Naslouchací proces protokolu výstup zprávu, pouze pokud je povolena závažnost zprávy pomocí obou protokolové `DefaultSwitch` a naslouchací proces protokolu filtru.  
  
 Tento příklad ukazuje, jak konfigurovat filtrování pro nové naslouchání ladění a přidejte ho do `Log` objektu. Naslouchací proces výchozí ladění, měla by být odebrána z `Log` objektu, aby bylo zřejmé, že zprávy ladění pocházejí z nové naslouchací proces ladění.  
  
#### <a name="to-log-only-activity-tracing-events"></a>Do protokolu pouze události trasování aktivit  
  
1.  Klikněte pravým tlačítkem na app.config v **Průzkumníku řešení** a zvolte **otevřete**.  
  
     -nebo-  
  
     Pokud není dostupný žádný soubor app.config:  
  
    1.  Na **projektu** nabídce zvolte **přidat novou položku**.  
  
    2.  Z **přidat novou položku** dialogovém okně vyberte **konfigurační soubor aplikace**.  
  
    3.  Klikněte na tlačítko **přidat**.  
  
2.  Klikněte pravým tlačítkem na app.config v **Průzkumníku řešení**. Zvolte **otevřete**.  
  
3.  Vyhledejte `<listeners>` v části `<source>` část s `name` atributu "DefaultSource", který je v části `<sources>` části. `<sources>` Část je pod `<system.diagnostics>` oddílem se v nejvyšší úrovně `<configuration>` části.  
  
4.  Přidejte tento element na `<listeners>` části:  
  
    ```xml  
    <!-- Remove the default debug listener. -->  
    <remove name="Default"/>  
    <!-- Add a filterable debug listener. -->  
    <add name="NewDefault"/>  
    ```  
  
5.  Vyhledejte `<sharedListeners>` v části `<system.diagnostics>` oddílem se v nejvyšší úrovně `<configuration>` části.  
  
6.  Přidejte tento element do `<sharedListeners>` části:  
  
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
  
     <xref:System.Diagnostics.EventTypeFilter> Filtru má jednu z <xref:System.Diagnostics.SourceLevels> výčtové hodnoty jako jeho `initializeData` atribut.  
  
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
  
8.  Spusťte aplikaci v ladicím programu.  
  
9. Stiskněte klávesu **Button1**.  
  
     Aplikace zapisuje do souboru protokolu aplikace následující informace:  
  
     `Default Information: 0 : In Button1_Click`  
  
     `Default Error: 2 : Error in the application.`  
  
     Aplikace zapíše méně informací výstupu ladění aplikace z důvodu více omezující filtrování.  
  
     `Default Error   2   Error`  
  
10. Zavřete aplikaci.  
  
 Další informace o změně nastavení protokolování po nasazení najdete v tématu [práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).  
  
## <a name="see-also"></a>Viz také  
 [Návod: Zjištění, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)  
 [Návod: Změna místa, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 [Návod: Vytváření vlastních součástí naslouchajících protokolům](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)  
 [Postupy: Zápis zpráv protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [Přepínače trasování](../../../../framework/debug-trace-profile/trace-switches.md)  
 [Protokolování informací z aplikace](../../../../visual-basic/developing-apps/programming/log-info/logging-information-from-the-application.md)
