---
title: Práce s protokoly aplikací
ms.date: 07/20/2015
helpviewer_keywords:
- logs, application
- application event logs, Visual Basic
- application event logs
ms.assetid: 2581afd1-5791-4bc4-86b2-46244e9fe468
ms.openlocfilehash: 617b940d2cf15779ae3c10e4663b63c9771d44b6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345902"
---
# <a name="working-with-application-logs-in-visual-basic"></a>Práce s protokoly aplikací v jazyce Visual Basic

Objekty `My.Application.Log` a `My.Log` usnadňují zápis informací o protokolování a trasování do protokolů.

## <a name="how-messages-are-logged"></a>Způsob protokolování zpráv

Nejdřív se u zprávy kontroluje závažnost pomocí vlastnosti <xref:System.Diagnostics.TraceSource.Switch%2A> vlastnosti <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> protokolu. Ve výchozím nastavení jsou posluchačům trasování, které jsou zadány v kolekci `TraceListener` protokolu, pouze zprávy "informace o závažnosti" a vyšší. Potom každé naslouchací proces porovná závažnost zprávy s vlastností <xref:System.Diagnostics.TraceSource.Switch%2A> naslouchacího procesu. Pokud je závažnost zprávy dostatečně vysoká, posluchač zapíše zprávu.

Následující diagram znázorňuje, jak se zpráva zapsaná do metody `WriteEntry` předává do `WriteLine` metod posluchačů trasování protokolu:

![Diagram, který zobrazuje moje volání protokolu](./media/working-with-application-logs/my-log-call-messages.png)

Můžete změnit chování protokolu a posluchačů trasování změnou konfiguračního souboru aplikace. Následující diagram znázorňuje korespondenci mezi částmi protokolu a konfiguračním souborem.

![Diagram, který zobrazuje konfiguraci protokolu.](./media/working-with-application-logs/my-log-configuration.png)

## <a name="where-messages-are-logged"></a>Kam se zaznamenávají zprávy

Pokud sestavení nemá žádný konfigurační soubor, objekty `My.Application.Log` a `My.Log` zapisují do výstupu ladění aplikace (prostřednictvím třídy <xref:System.Diagnostics.DefaultTraceListener>). Kromě toho `My.Application.Log` objekt zapisuje do souboru protokolu sestavení (prostřednictvím <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> třídy), zatímco objekt `My.Log` zapisuje do výstupu webové stránky ASP.NET (prostřednictvím třídy <xref:System.Web.WebPageTraceListener>).

Výstup ladění lze zobrazit v okně **výstupu** sady Visual Studio při spuštění aplikace v režimu ladění. Chcete-li otevřít okno **výstup** , klikněte na položku nabídky **ladění** , přejděte na příkaz **Windows**a potom klikněte na možnost **výstup**. V okně **výstup** vyberte **ladit** v poli **Zobrazit výstup z** .

Ve výchozím nastavení `My.Application.Log` zapisuje soubor protokolu do cesty pro data aplikace uživatele. Cestu můžete získat z vlastnosti <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> objektu <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A>. Formát této cesty je následující:

`BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`

Typická hodnota pro `BasePath` je následující.

C:\Documents and Settings\\`username`\Application data

Hodnoty `CompanyName`, `ProductName`a `ProductVersion` pocházejí z informací o sestavení aplikace. Forma názvu souboru protokolu je *AssemblyName*. log, kde *AssemblyName* je název souboru sestavení bez přípony. Pokud je potřeba více než jeden soubor protokolu, například když je původní protokol nedostupný, když se aplikace pokusí zapisovat do protokolu, je formulář pro název souboru protokolu *AssemblyName*-*iterace*. log, kde `iteration` je kladné `Integer`.

Výchozí chování můžete přepsat přidáním nebo změnou konfiguračních souborů aplikace a počítače. Další informace naleznete v tématu [Návod: Změna místa, kam aplikace My. Application. Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).

## <a name="configuring-log-settings"></a>Konfigurace nastavení protokolu

Objekt `Log` má výchozí implementaci, která funguje bez konfiguračního souboru aplikace App. config. Chcete-li změnit výchozí nastavení, je nutné přidat konfigurační soubor s novým nastavením. Další informace najdete v tématu [Návod: filtrování výstupu my. Application. log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).

Konfigurační oddíly protokolu jsou umístěné v uzlu `<system.diagnostics>` v hlavním uzlu `<configuration>` souboru App. config. Informace protokolu jsou definované v několika uzlech:

- Naslouchací procesy pro objekt `Log` jsou definovány v uzlu `<sources>` s názvem DefaultSource.

- Filtr závažnosti pro objekt `Log` je definován v uzlu `<switches>` s názvem DefaultSwitch.

- Naslouchací procesy protokolu jsou definovány v uzlu `<sharedListeners>`.

 Příklady `<sources>`, `<switches>`a `<sharedListeners>` uzlů jsou uvedeny v následujícím kódu:

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

Při vývoji aplikace se její nastavení konfigurace ukládají do souboru App. config, jak je znázorněno v předchozích příkladech. Po nasazení aplikace můžete protokol i nadále konfigurovat úpravou konfiguračního souboru. V aplikaci pro systém Windows je název tohoto souboru *ApplicationName*. exe. config a musí být umístěn ve stejné složce jako spustitelný soubor. Pro webovou aplikaci je to soubor Web. config přidružený k projektu.

Když vaše aplikace spustí kód, který vytvoří instanci třídy poprvé, zkontroluje konfigurační soubor o informace o objektu. Pro objekt `Log` k tomu dojde při prvním otevření objektu `Log`. Systém prověřuje konfigurační soubor pouze jednou pro konkrétní objekt – při prvním vytvoření objektu aplikace. Proto může být nutné aplikaci restartovat, aby se změny projevily.

V nasazené aplikaci povolíte trasovací kód tím, že znovu nakonfigurujete objekty přepínače před spuštěním aplikace. Obvykle to zahrnuje zapnutí a vypnutí objektů přepínače nebo změnu úrovní trasování a následné restartování aplikace.

## <a name="security-considerations"></a>Důležité informace o zabezpečení

Při zápisu dat do protokolu Vezměte v úvahu následující skutečnosti:

- **Vyhněte se nevracení informací o uživateli.** Ujistěte se, že vaše aplikace zapisuje do protokolu pouze schválené informace. Například může být přijatelné, aby protokol aplikace obsahoval uživatelská jména, ale ne hesla uživatelů.

- **Zajistěte zabezpečení umístění protokolu.** Jakýkoli protokol, který obsahuje potenciálně citlivé informace, by měl být uložený v zabezpečeném umístění.

- **Vyhněte se klamavým informacím.** Obecně platí, že aplikace musí před použitím těchto dat ověřit všechna data zadaná uživatelem. To zahrnuje zápis dat do aplikačního protokolu.

- **Vyhněte se odepření služby.** Pokud vaše aplikace zapisuje do protokolu příliš mnoho informací, mohl by protokol vyplnit nebo najít důležité informace, které by byly obtížné.

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Protokolování informací z aplikace](../../../../visual-basic/developing-apps/programming/log-info/index.md)
