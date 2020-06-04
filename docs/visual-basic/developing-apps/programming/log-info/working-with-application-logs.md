---
title: Práce s protokoly aplikací
ms.date: 07/20/2015
helpviewer_keywords:
- logs, application
- application event logs, Visual Basic
- application event logs
ms.assetid: 2581afd1-5791-4bc4-86b2-46244e9fe468
ms.openlocfilehash: e33efac8f65832c87d5c9271eba25c2ca1d1803b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387592"
---
# <a name="working-with-application-logs-in-visual-basic"></a>Práce s protokoly aplikací v jazyce Visual Basic

`My.Application.Log`Objekty a usnadňují `My.Log` zápis informací o protokolování a trasování do protokolů.

## <a name="how-messages-are-logged"></a>Způsob protokolování zpráv

Nejdřív se závažnost zprávy kontroluje pomocí <xref:System.Diagnostics.TraceSource.Switch%2A> vlastnosti <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> Vlastnosti protokolu. Ve výchozím nastavení jsou posluchačům trasování, které jsou zadány v kolekci protokolů, předány pouze zprávy o závažnosti "informace" a vyšší `TraceListener` . Potom každé naslouchací proces porovná závažnost zprávy s vlastností naslouchacího procesu <xref:System.Diagnostics.TraceSource.Switch%2A> . Pokud je závažnost zprávy dostatečně vysoká, posluchač zapíše zprávu.

Následující diagram znázorňuje, jak se zpráva zapsaná do `WriteEntry` metody předává do `WriteLine` metod posluchačů trasování protokolu:

![Diagram, který zobrazuje moje volání protokolu](./media/working-with-application-logs/my-log-call-messages.png)

Můžete změnit chování protokolu a posluchačů trasování změnou konfiguračního souboru aplikace. Následující diagram znázorňuje korespondenci mezi částmi protokolu a konfiguračním souborem.

![Diagram, který zobrazuje konfiguraci protokolu.](./media/working-with-application-logs/my-log-configuration.png)

## <a name="where-messages-are-logged"></a>Kam se zaznamenávají zprávy

Pokud sestavení nemá žádný konfigurační soubor, `My.Application.Log` `My.Log` objekty a zapisují do výstupu ladění aplikace (prostřednictvím <xref:System.Diagnostics.DefaultTraceListener> třídy). Kromě toho `My.Application.Log` objekt zapisuje do souboru protokolu sestavení (prostřednictvím <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> třídy), zatímco se `My.Log` objekt zapisuje do výstupu webové stránky ASP.NET (prostřednictvím <xref:System.Web.WebPageTraceListener> třídy).

Výstup ladění lze zobrazit v okně **výstupu** sady Visual Studio při spuštění aplikace v režimu ladění. Chcete-li otevřít okno **výstup** , klikněte na položku nabídky **ladění** , přejděte na příkaz **Windows**a potom klikněte na možnost **výstup**. V okně **výstup** vyberte **ladit** v poli **Zobrazit výstup z** .

Ve výchozím nastavení `My.Application.Log` zapisuje soubor protokolu do cesty pro data aplikace uživatele. Cestu můžete získat z <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> vlastnosti <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> objektu. Formát této cesty je následující:

`BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`

Typická hodnota pro `BasePath` je následující.

C:\Documents and Settings- \\ `username` \Application data

Hodnoty `CompanyName` , `ProductName` a `ProductVersion` pocházejí z informací o sestavení aplikace. Forma názvu souboru protokolu je *AssemblyName*. log, kde *AssemblyName* je název souboru sestavení bez přípony. Pokud je potřeba více než jeden soubor protokolu, například když je původní protokol nedostupný, když se aplikace pokusí o zápis do protokolu, je formulář pro název souboru protokolu typu *AssemblyName* - *iterace*. log, kde `iteration` je kladné `Integer` .

Výchozí chování můžete přepsat přidáním nebo změnou konfiguračních souborů aplikace a počítače. Další informace naleznete v tématu [Návod: Změna místa, kam aplikace My. Application. Log zapisuje informace](walkthrough-changing-where-my-application-log-writes-information.md).

## <a name="configuring-log-settings"></a>Konfigurace nastavení protokolu

`Log`Objekt má výchozí implementaci, která funguje bez konfiguračního souboru aplikace App. config. Chcete-li změnit výchozí nastavení, je nutné přidat konfigurační soubor s novým nastavením. Další informace najdete v tématu [Návod: filtrování výstupu my. Application. log](walkthrough-filtering-my-application-log-output.md).

Konfigurační oddíly protokolu jsou umístěné v `<system.diagnostics>` uzlu v hlavním `<configuration>` uzlu souboru App. config. Informace protokolu jsou definované v několika uzlech:

- Naslouchací procesy pro `Log` objekt jsou definovány v `<sources>` uzlu s názvem DefaultSource.

- Filtr závažnosti pro `Log` objekt je definován v `<switches>` uzlu s názvem DefaultSwitch.

- Naslouchací procesy protokolu jsou definovány v `<sharedListeners>` uzlu.

 Příklady `<sources>` uzlů, `<switches>` a `<sharedListeners>` jsou uvedeny v následujícím kódu:

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

Když vaše aplikace spustí kód, který vytvoří instanci třídy poprvé, zkontroluje konfigurační soubor o informace o objektu. Pro `Log` objekt k tomu dojde při prvním `Log` otevření objektu. Systém prověřuje konfigurační soubor pouze jednou pro konkrétní objekt – při prvním vytvoření objektu aplikace. Proto může být nutné aplikaci restartovat, aby se změny projevily.

V nasazené aplikaci povolíte trasovací kód tím, že znovu nakonfigurujete objekty přepínače před spuštěním aplikace. Obvykle to zahrnuje zapnutí a vypnutí objektů přepínače nebo změnu úrovní trasování a následné restartování aplikace.

## <a name="security-considerations"></a>Aspekty zabezpečení

Při zápisu dat do protokolu Vezměte v úvahu následující skutečnosti:

- **Vyhněte se nevracení informací o uživateli.** Ujistěte se, že vaše aplikace zapisuje do protokolu pouze schválené informace. Například může být přijatelné, aby protokol aplikace obsahoval uživatelská jména, ale ne hesla uživatelů.

- **Zajistěte zabezpečení umístění protokolu.** Jakýkoli protokol, který obsahuje potenciálně citlivé informace, by měl být uložený v zabezpečeném umístění.

- **Vyhněte se klamavým informacím.** Obecně platí, že aplikace musí před použitím těchto dat ověřit všechna data zadaná uživatelem. To zahrnuje zápis dat do aplikačního protokolu.

- **Vyhněte se odepření služby.** Pokud vaše aplikace zapisuje do protokolu příliš mnoho informací, mohl by protokol vyplnit nebo najít důležité informace, které by byly obtížné.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Protokolování informací z aplikace](index.md)
