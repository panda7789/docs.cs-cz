---
title: Filtrování výstupu My.Application.Log
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
ms.openlocfilehash: f18556bbe1ca2d77925482319246d403892d31ef
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353590"
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a>Návod: Filtrování výstupu My.Application.Log (Visual Basic)

Tento návod ukazuje, jak změnit výchozí filtrování protokolu pro objekt `My.Application.Log`, aby bylo možné určit, jaké informace jsou předány z objektu `Log` posluchačům a jaké informace jsou zapsány posluchači. Chování protokolování můžete změnit i po sestavení aplikace, protože informace o konfiguraci jsou uložené v konfiguračním souboru aplikace.

## <a name="getting-started"></a>Začínáme

Každé zprávě, která `My.Application.Log` zápisy, má přidruženou úroveň závažnosti, které mechanismy filtrování používají k řízení výstupu protokolu. Tato ukázková aplikace používá metody `My.Application.Log` k zápisu několika zpráv protokolu s různou úrovní závažnosti.

#### <a name="to-build-the-sample-application"></a>Sestavení ukázkové aplikace

1. Otevřete nový Visual Basic projekt aplikace systému Windows.

2. Přidejte tlačítko s názvem Button1 do formuláře Form1.

3. V obslužné rutině události <xref:System.Windows.Forms.Control.Click> pro Button1 přidejte následující kód:

     [!code-vb[VbVbcnMyApplicationLogFiltering#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyApplicationLogFiltering/VB/Form1.vb#1)]

4. Spusťte aplikaci v ladicím programu.

5. Stiskněte **Button1**.

     Aplikace zapíše do výstupu ladění a souboru protokolu aplikace následující informace.

     `DefaultSource Information: 0 : In Button1_Click`

     `DefaultSource Error: 2 : Error in the application.`

6. Zavřete aplikaci.

     Informace o tom, jak zobrazit okno výstup ladění aplikace, naleznete v tématu [okno výstup](/visualstudio/ide/reference/output-window). Informace o umístění souboru protokolu aplikace naleznete v tématu [Návod: zjištění, kam aplikace My. Application. Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).

    > [!NOTE]
    > Ve výchozím nastavení aplikace při zavření aplikace vyprázdní výstup souboru protokolu.

     Ve výše uvedeném příkladu druhé volání metody <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> a volání metody <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> vytvoří výstup protokolu, zatímco první a poslední volání metody `WriteEntry`. Důvodem je, že úrovně závažnosti `WriteEntry` a `WriteException` jsou "informace" a "Chyba", které jsou povoleny ve výchozím filtrování protokolu `My.Application.Log` objektu. Nicméně události s úrovněmi závažnosti "Start" a "Stop" znemožňují výstup protokolu z výroby.

## <a name="filtering-for-all-myapplicationlog-listeners"></a>Filtrování pro všechny naslouchací procesy my. Application. log

Objekt `My.Application.Log` používá <xref:System.Diagnostics.SourceSwitch> pojmenované `DefaultSwitch` k řízení, které zprávy přecházejí z `WriteEntry` a `WriteException` metod do protokolů naslouchacího procesu. V konfiguračním souboru aplikace můžete nakonfigurovat `DefaultSwitch` nastavením jeho hodnoty na jednu z hodnot výčtu <xref:System.Diagnostics.SourceLevels>. Ve výchozím nastavení je jeho hodnota "informace".

Tato tabulka zobrazuje úroveň závažnosti, která je vyžadována pro protokol k zápisu zprávy do posluchačů s ohledem na konkrétní `DefaultSwitch` nastavení.

|Hodnota DefaultSwitch|Závažnost zprávy požadovaná pro výstup|
|---|---|
|`Critical`|`Critical`|
|`Error`|`Critical` nebo `Error`|
|`Warning`|`Critical`, `Error`nebo `Warning`|
|`Information`|`Critical`, `Error`, `Warning`nebo `Information`|
|`Verbose`|`Critical`, `Error`, `Warning`, `Information`nebo `Verbose`|
|`ActivityTracing`|`Start`, `Stop`, `Suspend`, `Resume`nebo `Transfer`|
|`All`|Všechny zprávy jsou povoleny.|
|`Off`|Všechny zprávy jsou zablokované.|

> [!NOTE]
> Metody `WriteEntry` a `WriteException` mají přetížení, které neurčují úroveň závažnosti. Implicitní úroveň závažnosti pro přetížení `WriteEntry` je "informace" a implicitní úroveň závažnosti pro `WriteException` přetížení je "Error".

Tato tabulka vysvětluje výstup protokolu zobrazený v předchozím příkladu: výchozí `DefaultSwitch` nastavení "informace", pouze druhé volání metody `WriteEntry` a volání metody `WriteException` vyprodukuje výstup protokolu.

#### <a name="to-log-only-activity-tracing-events"></a>Chcete-li protokolovat pouze události trasování aktivit

1. V **Průzkumník řešení** klikněte pravým tlačítkem na soubor App. config a vyberte **otevřít**.

     -nebo-

     Pokud neexistuje žádný soubor App. config:

    1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

    2. V dialogovém okně **Přidat novou položku** vyberte možnost **konfigurační soubor aplikace**.

    3. Klikněte na tlačítko **Přidat**.

2. Vyhledejte část `<switches>`, která je v části `<system.diagnostics>`, která je v části `<configuration>` nejvyšší úrovně.

3. Vyhledejte prvek, který přidá `DefaultSwitch` do kolekce přepínačů. Měl by vypadat podobně jako tento element:

     `<add name="DefaultSwitch" value="Information" />`

4. Změňte hodnotu atributu `value` na "ActivityTracing".

5. Obsah souboru App. config by měl vypadat podobně jako následující kód XML:

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

7. Stiskněte **Button1**.

     Aplikace zapíše do výstupu ladění a souboru protokolu aplikace následující informace:

     `DefaultSource Start: 4 : Entering Button1_Click`

     `DefaultSource Stop: 5 : Leaving Button1_Click`

8. Zavřete aplikaci.

9. Změňte hodnotu atributu `value` zpět na "informace".

    > [!NOTE]
    > Ovládací prvky nastavení `DefaultSwitch` přepínač pouze `My.Application.Log`. Nemění způsob, jakým se chovají .NET Framework <xref:System.Diagnostics.Trace?displayProperty=nameWithType> a třídy <xref:System.Diagnostics.Debug?displayProperty=nameWithType>.

## <a name="individual-filtering-for-myapplicationlog-listeners"></a>Individuální filtrování pro naslouchací procesy my. Application. log

Předchozí příklad ukazuje, jak změnit filtrování pro všechny `My.Application.Log` výstup. Tento příklad ukazuje, jak filtrovat jednotlivé naslouchací procesy protokolů. Ve výchozím nastavení má aplikace dva naslouchací procesy, které zapisují do výstupu ladění aplikace a do souboru protokolu.

Konfigurační soubor řídí chování naslouchacího procesu protokolu tím, že každé z nich může mít filtr, který je podobný přepínači pro `My.Application.Log`. Naslouchací proces protokolu vytvoří zprávu pouze v případě, že je závažnost zprávy povolena pomocí `DefaultSwitch` protokolu i filtru naslouchacího procesu protokolu.

Tento příklad ukazuje, jak nakonfigurovat filtrování pro nový naslouchací proces ladění a přidat ho do objektu `Log`. Výchozí naslouchací proces ladění by měl být odebrán z objektu `Log`, takže je zřejmé, že zprávy ladění pocházejí z nového naslouchacího procesu ladění.

#### <a name="to-log-only-activity-tracing-events"></a>Do protokolu pouze události trasování aktivity

1. V **Průzkumník řešení** klikněte pravým tlačítkem na soubor App. config a vyberte **otevřít**.

     \-nebo-

     Pokud neexistuje žádný soubor App. config:

    1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

    2. V dialogovém okně **Přidat novou položku** vyberte možnost **konfigurační soubor aplikace**.

    3. Klikněte na tlačítko **Přidat**.

2. Klikněte pravým tlačítkem na soubor App. config v **Průzkumník řešení**. Klikněte na tlačítko **otevřít**.

3. Vyhledejte část `<listeners>` v části `<source>` s atributem `name` "DefaultSource", který je v části `<sources>`. Část `<sources>` je pod oddílem `<system.diagnostics>` v části `<configuration>` nejvyšší úrovně.

4. Přidejte tento prvek do oddílu `<listeners>`:

    ```xml
    <!-- Remove the default debug listener. -->
    <remove name="Default"/>
    <!-- Add a filterable debug listener. -->
    <add name="NewDefault"/>
    ```

5. Vyhledejte část `<sharedListeners>` v části `<system.diagnostics>` v části `<configuration>` nejvyšší úrovně.

6. Přidejte tento prvek do tohoto `<sharedListeners>` části:

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

     Filtr <xref:System.Diagnostics.EventTypeFilter> přebírá jednu z <xref:System.Diagnostics.SourceLevels> hodnot výčtu jako atribut `initializeData`.

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

9. Stiskněte **Button1**.

     Aplikace zapíše do souboru protokolu aplikace následující informace:

     `Default Information: 0 : In Button1_Click`

     `Default Error: 2 : Error in the application.`

     Aplikace zapisuje méně informací do výstupu ladění aplikace z důvodu přísnějšího filtrování.

     `Default Error   2   Error`

10. Zavřete aplikaci.

Další informace o změně nastavení protokolu po nasazení najdete v tématu [práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).

## <a name="see-also"></a>Viz také:

- [Návod: Zjištění, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [Návod: Změna místa, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [Návod: Vytváření vlastních součástí naslouchajících protokolům](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)
- [Postupy: Zápis zpráv protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Přepínače trasování](../../../../framework/debug-trace-profile/trace-switches.md)
- [Protokolování informací z aplikace](../../../../visual-basic/developing-apps/programming/log-info/index.md)
