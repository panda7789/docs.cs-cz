---
title: Práce s protokoly aplikací v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- logs, application
- application event logs, Visual Basic
- application event logs
ms.assetid: 2581afd1-5791-4bc4-86b2-46244e9fe468
ms.openlocfilehash: c11e1f0c99b3189c7a353e6778c701667b0a1d12
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43725082"
---
# <a name="working-with-application-logs-in-visual-basic"></a>Práce s protokoly aplikací v jazyce Visual Basic
`My.Applicaton.Log` a `My.Log` objekty usnadňují zapsat informace trasování a protokolování do protokolů.  
  
## <a name="how-messages-are-logged"></a>Jak jsou zprávy zaznamenány  
 Nejprve je zkontrolován závažnost zprávy <xref:System.Diagnostics.TraceSource.Switch%2A> vlastnost v protokolu <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> vlastnost. Ve výchozím pouze zprávy závažnosti "Informace" a vyšší jsou předány pro posluchače trasování, zadaný do protokolu `TraceListener` kolekce. Poté porovnává každý naslouchací proces závažnost zpráv pro posluchače <xref:System.Diagnostics.TraceSource.Switch%2A> vlastnost. Pokud závažnost zprávy je dostatečně vysoká, naslouchací proces zapíše zprávu.  
  
 Následující obrázek ukazuje, jak se zprávy zapisují do `WriteEntry` metoda bude předána do `WriteLine` naslouchací procesy trasování metody v protokolu:  
  
 ![Moje volání protokolu](../../../../visual-basic/developing-apps/programming/log-info/media/mylogcall.png "MyLogCall")  
  
 Chování protokolu a naslouchacími procesy trasování můžete změnit změnou souboru konfigurace aplikace. Následující diagram ukazuje souvztažnost mezi částmi v protokolu a konfigurační soubor.  
  
 ![Moje nastavení protokolu](../../../../visual-basic/developing-apps/programming/log-info/media/mylogconfig.png "MyLogConfig")  
  
## <a name="where-messages-are-logged"></a>Kde jsou zprávy zaznamenány  
 Pokud sestavení nemá žádný konfigurační soubor `My.Application.Log` a `My.Log` objektů zapisovat do výstupu ladění aplikace (prostřednictvím <xref:System.Diagnostics.DefaultTraceListener> třídy). Kromě toho `My.Application.Log` zapíše objekt do souboru protokolu sestavení. (prostřednictvím <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> třídy), zatímco `My.Log` zapíše objekt do výstupu webová stránka ASP.NET (prostřednictvím <xref:System.Web.WebPageTraceListener> třídy).  
  
 Výstup ladění můžete zobrazit v sadě Visual Studio **výstup** okno při spuštění aplikace v režimu ladění. Otevřete **výstup** okna, klikněte na tlačítko **ladění** položku nabídky, přejděte na **Windows**a potom klikněte na tlačítko **výstup**. V **výstup** okně **ladění** z **zobrazit výstup z:** pole.  
  
 Ve výchozím nastavení `My.Application.Log` zapíše soubor protokolu v umístění pro data aplikací uživatele. Můžete získat cestu z <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> vlastnost <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> objektu. Formát cesty je následujícím způsobem:  
  
 `BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`  
  
 Typická hodnota `BasePath` vypadá takto.  
  
 C:\Documents and nastavení\\`username`\Application dat  
  
 Hodnoty `CompanyName`, `ProductName`, a `ProductVersion` pocházejí z informací o sestavení aplikace. Název souboru protokolu má *AssemblyName*.log, kde *AssemblyName* je název souboru sestavení bez přípony. V případě potřeby je více než jeden soubor protokolu, třeba když původní protokolu není k dispozici aplikace pokusy o zápis do protokolu, je formulář pro název souboru protokolu *AssemblyName*-*iterace* .log, kde `iteration` pozitivní `Integer`.  
  
 Výchozí chování můžete přepsat přidáním nebo změnou konfiguračních souborů aplikace a počítače. Další informace najdete v tématu [návod: Změna kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).  
  
## <a name="configuring-log-settings"></a>Konfigurace nastavení protokolu  
 `Log` Objekt má výchozí implementaci, která funguje bez konfiguračního souboru aplikace, app.config. Chcete-li změnit výchozí hodnoty, je nutné přidat konfigurační soubor s novým nastavením. Další informace najdete v tématu [návod: filtrování výstupu My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
 Konfigurační oddíly funkce protokolu jsou umístěné v `<system.diagnostics>` uzlu v hlavním `<configuration>` uzlu ze souboru app.config. Informace o protokolu je definován v několika uzly:  
  
-   Naslouchací procesy pro `Log` objektu jsou definovány v `<sources>` uzel s názvem DefaultSource.  
  
-   Závažnost filtr `Log` objekt je definovaný v `<switches>` uzel s názvem DefaultSwitch.  
  
-   Součásti naslouchající protokolům, které jsou definovány v `<sharedListeners>` uzlu.  
  
 Příklady `<sources>`, `<switches>`, a `<sharedListeners>` uzly jsou uvedeny v následujícím kódu:  
  
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
 Když vyvíjíte aplikaci, jeho nastavení konfigurace jsou uloženy v souboru app.config, jak je znázorněno výše uvedených příkladech. Po nasazení aplikace, můžete stále nakonfigurovat protokol úpravou konfiguračního souboru. V aplikaci založené na Windows, tento název souboru je *applicationName*. exe.config který se musí nacházet ve stejné složce jako spustitelný soubor. Pro webovou aplikaci Toto je soubor Web.config, který je přidružený k projektu.  
  
 Pokud vaše aplikace spustí kód, který vytvoří instanci třídy poprvé, ověří konfigurační soubor pro informace o objektu. Pro `Log` objektu, to se stane první `Log` přístupu k objektu. Systém zkontroluje konfigurační soubor jen jednou pro každý konkrétní objekt – poprvé vaše aplikace vytvoří objekt. Proto budete muset restartovat aplikaci, aby se změny projevily.  
  
 V nasazené aplikaci povolit trasování kódu překonfigurováním přepínače objektů před spuštěním vaší aplikace. Obvykle to zahrnuje zapnutí přepínače objektů a vypnout nebo změnou úrovně trasování a následného restartování aplikace.  
  
## <a name="security-considerations"></a>Důležité informace o zabezpečení  
 Při zápisu dat do protokolu, zvažte následující:  
  
-   **Vyhněte se úniku informací o uživateli.** Ujistěte se, že vaše aplikace zapisuje pouze schválená informace do protokolu. Například může být přijatelný aplikačního protokolu obsahující uživatelská jména, ale ne hesla uživatele.  
  
-   **Zabezpečte umístění protokolu.** Libovolný protokol, který obsahuje potenciálně citlivé informace ukládat na bezpečném místě.  
  
-   **Vyhněte se zavádějící informace.** Vaše aplikace měla ověřit obecně platí, všechna data zadaná uživatelem, než začnete používat tato data. Jedná se o zápisu dat do protokolu aplikace.  
  
-   **Vyhněte se útok DoS.** Pokud vaše aplikace zapisuje příliš mnoho informace do protokolu, může zaplnit protokol nebo nalezení obtížné důležité informace.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [Protokolování informací z aplikace](../../../../visual-basic/developing-apps/programming/log-info/index.md)
