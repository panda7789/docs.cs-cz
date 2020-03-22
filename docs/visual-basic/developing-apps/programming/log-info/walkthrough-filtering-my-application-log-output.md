---
title: Filtrování výstupu My.Application.Log
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
ms.openlocfilehash: f18556bbe1ca2d77925482319246d403892d31ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74353590"
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a>Návod: Filtrování výstupu My.Application.Log (Visual Basic)

Tento návod ukazuje, jak změnit výchozí filtrování `My.Application.Log` protokolu pro objekt, chcete-li `Log` řídit, jaké informace jsou předávány z objektu naslouchacím procesům a jaké informace jsou napsány posluchači. Chování protokolování můžete změnit i po vytvoření aplikace, protože informace o konfiguraci jsou uloženy v konfiguračním souboru aplikace.

## <a name="getting-started"></a>Začínáme

Každá zpráva, která `My.Application.Log` zapíše má přidruženou úroveň závažnosti, které mechanismy filtrování použít k řízení výstupu protokolu. Tato ukázková `My.Application.Log` aplikace používá metody k zápisu několika zpráv protokolu s různými úrovněmi závažnosti.

#### <a name="to-build-the-sample-application"></a>Vytvoření ukázkové aplikace

1. Otevřete nový projekt aplikace jazyka Visual Basic pro Systém Windows.

2. Přidejte tlačítko s názvem Button1 do formuláře1.

3. V <xref:System.Windows.Forms.Control.Click> obslužné rutině události button1 přidejte následující kód:

     [!code-vb[VbVbcnMyApplicationLogFiltering#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyApplicationLogFiltering/VB/Form1.vb#1)]

4. Spusťte aplikaci v ladicím programu.

5. Stiskněte **tlačítko1**.

     Aplikace zapíše následující informace do ladicího výstupu aplikace a souboru protokolu.

     `DefaultSource Information: 0 : In Button1_Click`

     `DefaultSource Error: 2 : Error in the application.`

6. Zavřete aplikaci.

     Informace o tom, jak zobrazit výstupní okno ladění aplikace, naleznete v [tématu Output Window](/visualstudio/ide/reference/output-window). Informace o umístění souboru protokolu aplikace naleznete v [tématu Návod: Určení, kde my.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).

    > [!NOTE]
    > Ve výchozím nastavení aplikace vyprázdní výstup souboru protokolu při ukončení aplikace.

     Ve výše uvedeném příkladu <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> druhé volání metody <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> a volání metody vytvoří výstup protokolu, zatímco `WriteEntry` první a poslední volání metody není. Důvodem je, že `WriteEntry` úrovně `WriteException` závažnosti a jsou "Informace" a "Chyba", které jsou povoleny výchozí filtrování protokolu objektu. `My.Application.Log` Události s úrovněmi závažnosti "Start" a "Stop" však brání vytváření výstupu protokolu.

## <a name="filtering-for-all-myapplicationlog-listeners"></a>Filtrování pro všechny posluchače my.Application.Log

Objekt `My.Application.Log` používá <xref:System.Diagnostics.SourceSwitch> pojmenovaný `DefaultSwitch` k řízení, které `WriteEntry` zprávy `WriteException` předá z a metody naslouchací procesy protokolu. V konfiguračním souboru aplikace můžete nakonfigurovat `DefaultSwitch` <xref:System.Diagnostics.SourceLevels> nastavením její hodnoty na jednu z hodnot výčtu. Ve výchozím nastavení je jeho hodnota "Informace".

Tato tabulka ukazuje úroveň závažnosti požadovanou pro Protokol napsat zprávu `DefaultSwitch` posluchačům, dané konkrétní nastavení.

|Hodnota DefaultSwitch|Závažnost zprávy požadovaná pro výstup|
|---|---|
|`Critical`|`Critical`|
|`Error`|`Critical` nebo `Error`|
|`Warning`|`Critical`, `Error`, nebo`Warning`|
|`Information`|`Critical`, `Error` `Warning`, , nebo`Information`|
|`Verbose`|`Critical`, `Error` `Warning`, `Information`, , nebo`Verbose`|
|`ActivityTracing`|`Start`, `Stop` `Suspend`, `Resume`, , nebo`Transfer`|
|`All`|Všechny zprávy jsou povoleny.|
|`Off`|Všechny zprávy jsou blokovány.|

> [!NOTE]
> A `WriteEntry` `WriteException` metody mají přetížení, které neurčuje úroveň závažnosti. Implicitní úroveň závažnosti `WriteEntry` pro přetížení je "Informace" a implicitní úroveň závažnosti pro `WriteException` přetížení je "Chyba".

Tato tabulka vysvětluje výstup protokolu zobrazený v předchozím `DefaultSwitch` příkladu: s výchozím nastavením `WriteEntry` "Informace", pouze `WriteException` druhé volání metody a volání metody vytvoří výstup protokolu.

#### <a name="to-log-only-activity-tracing-events"></a>Protokolovat pouze události trasování aktivit

1. Klepněte pravým tlačítkem myši na soubor app.config v **Průzkumníku řešení** a vyberte **příkaz Otevřít**.

     -nebo-

     Pokud není k dispozici žádný soubor app.config:

    1. V nabídce **Projekt** zvolte **Přidat novou položku**.

    2. V dialogovém okně **Přidat novou položku** zvolte **Konfigurační soubor aplikace**.

    3. Klikněte na **Přidat**.

2. Vyhledejte `<switches>` oddíl, který `<system.diagnostics>` je v části, která `<configuration>` je v části nejvyšší úrovně.

3. Najít prvek, `DefaultSwitch` který přidá do kolekce přepínačů. Mělo by vypadat podobně jako tento prvek:

     `<add name="DefaultSwitch" value="Information" />`

4. Změňte hodnotu `value` atributu na "ActivityTracing".

5. Obsah souboru app.config by měl být podobný následujícímu xml:

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

7. Stiskněte **tlačítko1**.

     Aplikace zapíše následující informace do ladicího výstupu aplikace a do souboru protokolu:

     `DefaultSource Start: 4 : Entering Button1_Click`

     `DefaultSource Stop: 5 : Leaving Button1_Click`

8. Zavřete aplikaci.

9. Změňte hodnotu `value` atributu zpět na "Informace".

    > [!NOTE]
    > Nastavení `DefaultSwitch` přepínače `My.Application.Log`ovládá pouze . Nezmění způsob, jakým se <xref:System.Diagnostics.Trace?displayProperty=nameWithType> chová <xref:System.Diagnostics.Debug?displayProperty=nameWithType> rozhraní .NET Framework a třídy.

## <a name="individual-filtering-for-myapplicationlog-listeners"></a>Individuální filtrování pro posluchače my.Application.Log

Předchozí příklad ukazuje, jak změnit filtrování `My.Application.Log` pro všechny výstupy. Tento příklad ukazuje, jak filtrovat naslouchací proces protokolu. Ve výchozím nastavení má aplikace dva naslouchací procesy, které zapisují do ladicího výstupu aplikace a souboru protokolu.

Konfigurační soubor řídí chování posluchačů protokolu tím, že umožňuje každému z nich `My.Application.Log`mít filtr, který je podobný přepínači pro . Naslouchací proces protokolu bude výstup zprávy pouze v případě, `DefaultSwitch` že závažnost zprávy je povoleno protokolu a naslouchací filtr posluchače protokolu.

Tento příklad ukazuje, jak nakonfigurovat filtrování pro nový naslouchací proces ladění a přidat jej do objektu. `Log` Výchozí naslouchací proces `Log` ladění by měl být odebrán z objektu, takže je jasné, že ladicí zprávy pocházejí z nového procesu ladění.

#### <a name="to-log-only-activity-tracing-events"></a>Protokolovat pouze události trasování aktivit

1. Klepněte pravým tlačítkem myši na soubor app.config v **Průzkumníku řešení** a zvolte **Otevřít**.

     \-nebo-

     Pokud není k dispozici žádný soubor app.config:

    1. V nabídce **Projekt** zvolte **Přidat novou položku**.

    2. V dialogovém okně **Přidat novou položku** zvolte **Konfigurační soubor aplikace**.

    3. Klikněte na **Přidat**.

2. Klepněte pravým tlačítkem myši na soubor app.config v **Průzkumníku řešení**. Zvolte **Otevřít**.

3. Vyhledejte `<listeners>` oddíl v `<source>` části `name` s atributem "DefaultSource", `<sources>` který je pod oddílem. Sekce `<sources>` je pod `<system.diagnostics>` částí, v horní `<configuration>` části.

4. Přidejte tento `<listeners>` prvek do oddílu:

    ```xml
    <!-- Remove the default debug listener. -->
    <remove name="Default"/>
    <!-- Add a filterable debug listener. -->
    <add name="NewDefault"/>
    ```

5. Vyhledejte `<sharedListeners>` oddíl v `<system.diagnostics>` části v části `<configuration>` nejvyšší úrovně.

6. Přidejte tento `<sharedListeners>` prvek do tohoto oddílu:

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

     Filtr <xref:System.Diagnostics.EventTypeFilter> přebírá jednu <xref:System.Diagnostics.SourceLevels> z hodnot výčtu jako svůj `initializeData` atribut.

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

9. Stiskněte **tlačítko1**.

     Aplikace zapíše do souboru protokolu aplikace následující informace:

     `Default Information: 0 : In Button1_Click`

     `Default Error: 2 : Error in the application.`

     Aplikace zapíše méně informací do výstupu ladění aplikace z důvodu více omezující filtrování.

     `Default Error   2   Error`

10. Zavřete aplikaci.

Další informace o změně nastavení protokolu po nasazení naleznete v [tématu Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).

## <a name="see-also"></a>Viz také

- [Návod: Zjištění, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [Návod: Změna místa, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [Návod: Vytváření vlastních součástí naslouchajících protokolům](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)
- [Postupy: Zápis zpráv protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Přepínače trasování](../../../../framework/debug-trace-profile/trace-switches.md)
- [Protokolování informací z aplikace](../../../../visual-basic/developing-apps/programming/log-info/index.md)
