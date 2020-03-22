---
title: Práce s protokoly aplikací
ms.date: 07/20/2015
helpviewer_keywords:
- logs, application
- application event logs, Visual Basic
- application event logs
ms.assetid: 2581afd1-5791-4bc4-86b2-46244e9fe468
ms.openlocfilehash: 617b940d2cf15779ae3c10e4663b63c9771d44b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345902"
---
# <a name="working-with-application-logs-in-visual-basic"></a>Práce s protokoly aplikací v jazyce Visual Basic

`My.Application.Log` Objekty `My.Log` a usnadňují zápis protokolování a trasování informací do protokolů.

## <a name="how-messages-are-logged"></a>Jak jsou protokolovány zprávy

Nejprve závažnost zprávy je kontrolována s <xref:System.Diagnostics.TraceSource.Switch%2A> vlastností protokolu. <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> Ve výchozím nastavení jsou pouze zprávy závažnosti "Informace" a vyšší jsou předány `TraceListener` na posluchače trasování, zadané v kolekci protokolu. Potom každý naslouchací proces porovnává závažnost <xref:System.Diagnostics.TraceSource.Switch%2A> zprávy na schytavku posluchače. Pokud závažnost zprávy je dostatečně vysoká, naslouchací proces zapíše zprávu.

Následující diagram znázorňuje, jak `WriteEntry` zpráva zapsána `WriteLine` do metody získá předány metody posluchačů trasování protokolu:

![Diagram, který zobrazuje můj volání protokolu.](./media/working-with-application-logs/my-log-call-messages.png)

Můžete změnit chování protokolu a naslouchací procesy trasování změnou konfiguračního souboru aplikace. Následující diagram znázorňuje korespondenci mezi částmi protokolu a konfiguračním souborem.

![Diagram, který ukazuje moje konfigurace protokolu.](./media/working-with-application-logs/my-log-configuration.png)

## <a name="where-messages-are-logged"></a>Kde jsou protokolovány zprávy

Pokud sestavení nemá žádný konfigurační soubor, `My.Application.Log` a `My.Log` objekty zapisovat do výstupu ladění aplikace (prostřednictvím třídy). <xref:System.Diagnostics.DefaultTraceListener> Kromě toho `My.Application.Log` objekt zapíše do souboru protokolu <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> sestavení (prostřednictvím třídy), zatímco `My.Log` objekt zapíše <xref:System.Web.WebPageTraceListener> do výstupu ASP.NET webové stránky (prostřednictvím třídy).

Ladicí výstup lze zobrazit v okně **Výstup** sady Visual Studio při spuštění aplikace v režimu ladění. Chcete-li otevřít okno **Výstup,** klepněte na položku nabídky **Ladění,** přejděte na **položku Windows**a potom klepněte na **příkaz Výstup**. V okně **Výstup** vyberte **ladění** z pole **Zobrazit výstup z.**

Ve výchozím `My.Application.Log` nastavení zapisuje soubor protokolu do cesty pro data aplikace uživatele. Cestu můžete získat z <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> vlastnosti <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> objektu. Formát této cesty je následující:

`BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`

Typická hodnota `BasePath` pro je následující.

C:\Dokumenty a\\`username`nastavení \Data aplikace

Hodnoty `CompanyName`, `ProductName`a `ProductVersion` pocházejí z informací o sestavení aplikace. Forma názvu souboru protokolu je *AssemblyName*.log, kde *AssemblyName* je název souboru sestavení bez přípony. Pokud je potřeba více než jeden soubor protokolu, například když původní protokol není k dispozici, když se aplikace pokusí o `iteration` zápis do `Integer`protokolu, je formulář pro název souboru protokolu *AssemblyName*-*iteration*.log, kde je kladný .

Výchozí chování můžete přepsat přidáním nebo změnou konfiguračních souborů počítače a aplikace. Další informace naleznete [v tématu Návod: Změna místa, kde my.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).

## <a name="configuring-log-settings"></a>Konfigurace nastavení protokolu

Objekt `Log` má výchozí implementaci, která funguje bez konfiguračního souboru aplikace app.config. Chcete-li změnit výchozí hodnoty, je nutné přidat konfigurační soubor s novým nastavením. Další informace naleznete [v tématu Návod: Filtrování výstupu my.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).

Oddíly konfigurace protokolu jsou `<system.diagnostics>` umístěny v `<configuration>` uzlu v hlavním uzlu souboru app.config. Informace protokolu jsou definovány v několika uzlech:

- Naslouchací procesy `Log` `<sources>` pro objekt jsou definovány v uzlu s názvem DefaultSource.

- Filtr závažnosti objektu `Log` je definován `<switches>` v uzlu s názvem DefaultSwitch.

- Naslouchací procesy protokolu jsou definovány `<sharedListeners>` v uzlu.

 Příklady `<sources>`, `<switches>`a `<sharedListeners>` uzly jsou uvedeny v následujícím kódu:

```xml
<configuration>
  <system.diagnostics>
    <sources>
      <source name="DefaultSource" switchName="DefaultSwitch">
        <listeners>
          <add name="FileLog"/>
        </listeners>
      </source>
    </sources>
    <switches>
      <add name="DefaultSwitch" value="Information" />
    </switches>
    <sharedListeners>
      <add name="FileLog"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
          Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
          PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL"
        initializeData="FileLogWriter"
      />
    </sharedListeners>
  </system.diagnostics>
</configuration>
```

## <a name="changing-log-settings-after-deployment"></a>Změna nastavení protokolu po nasazení

Při vývoji aplikace jsou její nastavení konfigurace uložena v souboru app.config, jak je znázorněno na výše uvedených příkladech. Po nasazení aplikace můžete protokol nakonfigurovat úpravou konfiguračního souboru. V aplikaci založené na systému Windows je název tohoto souboru *applicationName*.exe.config a musí být umístěn ve stejné složce jako spustitelný soubor. Pro webovou aplikaci se jedná o soubor Web.config přidružený k projektu.

Když aplikace spustí kód, který vytvoří instanci třídy poprvé, zkontroluje konfigurační soubor informace o objektu. U `Log` objektu k tomu dochází `Log` při prvním přístupu k objektu. Systém zkontroluje konfigurační soubor pouze jednou pro konkrétní objekt – při prvním vytvoření objektu aplikace. Proto může být nutné restartovat aplikaci pro změny se projeví.

V nasazené aplikaci povolíte trasovací kód změnou konfigurace objektů přepínače před spuštěním aplikace. Obvykle to zahrnuje zapnutí a vypnutí objektů přepínače nebo změnou úrovní trasování a restartování aplikace.

## <a name="security-considerations"></a>Aspekty zabezpečení

Při zápisu dat do protokolu zvažte následující:

- **Vyhněte se úniku informací o uživateli.** Ujistěte se, že vaše aplikace zapisuje pouze schválené informace do protokolu. Může být například přijatelné, aby protokol aplikace obsahoval uživatelská jména, ale ne uživatelská hesla.

- **Zabezpečte umístění protokolů.** Jakýkoli protokol, který obsahuje potenciálně citlivé informace, by měl být uložen na bezpečném místě.

- **Vyhněte se zavádějícím informacím.** Obecně platí, že aplikace by měla ověřit všechna data zadaná uživatelem před použitím dat. To zahrnuje zápis dat do protokolu aplikace.

- **Vyhněte se odmítnutí služby.** Pokud aplikace zapíše do protokolu příliš mnoho informací, může vyplnit protokol nebo ztížit hledání důležitých informací.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Protokolování informací z aplikace](../../../../visual-basic/developing-apps/programming/log-info/index.md)
