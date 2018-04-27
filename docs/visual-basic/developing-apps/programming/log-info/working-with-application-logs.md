---
title: Práce s protokoly aplikací v jazyce Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- logs, application
- application event logs, Visual Basic
- application event logs
ms.assetid: 2581afd1-5791-4bc4-86b2-46244e9fe468
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 40cad53cd9283a99a93cde79616151e77489e7bb
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="working-with-application-logs-in-visual-basic"></a>Práce s protokoly aplikací v jazyce Visual Basic
`My.Applicaton.Log` a `My.Log` objekty usnadňují zapisovat do protokolů informace o trasování a protokolování.  
  
## <a name="how-messages-are-logged"></a>Jak jsou zprávy protokolovány  
 Nejprve je zaškrtnuta možnost závažnost zprávy s <xref:System.Diagnostics.TraceSource.Switch%2A> vlastnost v protokolu <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> vlastnost. Ve výchozím pouze zprávy s závažnosti "Informace" a vyšší jsou předány naslouchací procesy trasování, zadaný v protokolu nástroje `TraceListener` kolekce. Potom každý naslouchací proces porovná závažnost zprávy naslouchacího procesu <xref:System.Diagnostics.TraceSource.Switch%2A> vlastnost. Pokud závažnost zprávy je dostatečně vysoká, naslouchací proces vypíše zprávu.  
  
 Následující obrázek ukazuje, jak zpráva zapsána do `WriteEntry` metoda předána do `WriteLine` naslouchací procesy trasování metody v protokolu:  
  
 ![Moje volání protokolu](../../../../visual-basic/developing-apps/programming/log-info/media/mylogcall.png "MyLogCall")  
  
 Chování protokolu a naslouchací procesy trasování můžete změnit změnou souboru konfigurace aplikace. Následující diagram znázorňuje mezi části protokolu a konfigurační soubor.  
  
 ![Moje konfigurace protokolů](../../../../visual-basic/developing-apps/programming/log-info/media/mylogconfig.png "MyLogConfig")  
  
## <a name="where-messages-are-logged"></a>Kde se protokolují zprávy  
 Pokud sestavení nemá žádný konfigurační soubor `My.Application.Log` a `My.Log` objekty zápis výstupu ladění aplikace (prostřednictvím <xref:System.Diagnostics.DefaultTraceListener> třídy). Kromě toho `My.Application.Log` objekt zapisuje do souboru protokolu sestavení (prostřednictvím <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> – třída), při `My.Log` objekt zapíše do výstupního webová stránka ASP.NET (prostřednictvím <xref:System.Web.WebPageTraceListener> – třída).  
  
 Výstup ladění lze zobrazit v sadě Visual Studio **výstup** okno při spuštění aplikace v režimu ladění. Otevřete **výstup** okně klikněte na tlačítko **ladění** položky nabídky, přejděte na příkaz **Windows**a potom klikněte na **výstup**. V **výstup** vyberte **ladění** z **zobrazit výstup z** pole.  
  
 Ve výchozím nastavení `My.Application.Log` soubor protokolu se zapisují cesta k datům uživatele aplikace. Můžete získat cestu z <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> vlastnost <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> objektu. Formát cesty je následující:  
  
 `BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`  
  
 Typické hodnota pro `BasePath` je následující.  
  
 C:\Documents and Settings\\`username`\Application dat  
  
 Hodnoty `CompanyName`, `ProductName`, a `ProductVersion` pocházejí z informací o sestavení aplikace. Název souboru protokolu je *AssemblyName*.log, kde *AssemblyName* je název souboru bez přípony sestavení. V případě potřeby je více než jeden soubor protokolu, například když není k dispozici v původní protokolu když se aplikace pokusí zapisovat do protokolu, formát názvu souboru protokolu je *AssemblyName*-*iterace* .log, kde `iteration` pozitivní `Integer`.  
  
 Výchozí chování můžete přepsat pomocí přidání nebo změna konfigurační soubory aplikace a počítače. Další informace najdete v tématu [návod: Změna kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).  
  
## <a name="configuring-log-settings"></a>Konfigurace nastavení protokolu  
 `Log` Objekt má výchozí implementace, která funguje bez konfigurační soubor aplikace app.config. Chcete-li změnit výchozí hodnoty, musíte přidat konfigurační soubor s novým nastavením. Další informace najdete v tématu [návod: filtrování výstupu My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
 Konfigurační oddíly protokolu jsou umístěné v `<system.diagnostics>` uzlu v hlavní `<configuration>` uzlu souboru app.config. Informace v protokolu je definována v několika uzly:  
  
-   Naslouchací procesy pro `Log` objekt jsou definovány v `<sources>` uzel s názvem DefaultSource.  
  
-   Filtr závažnosti pro `Log` objektu je definována v `<switches>` uzel s názvem DefaultSwitch.  
  
-   Naslouchací procesy pro protokoly jsou definovány v `<sharedListeners>` uzlu.  
  
 Příklady `<sources>`, `<switches>`, a `<sharedListeners>` uzly jsou uvedeny v následující kód:  
  
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
 Při vývoji aplikace, nastavení konfigurace se uloží v souboru app.config, jak je vidět ve výše uvedených příkladech. Poté, co nasadíte aplikaci, můžete přesto nakonfigurovat protokol úpravou konfiguračního souboru. V aplikaci systému Windows, je název tohoto souboru *applicationName*. exe.config a se musí nacházet ve stejné složce jako spustitelný soubor. Pro webovou aplikaci Toto je soubor Web.config přidružený k projektu.  
  
 Když aplikaci spustí kód, který vytvoří instanci třídy poprvé, zkontroluje konfiguračního souboru pro informace o objektu. Pro `Log` objektu, k tomu dojde při prvním `Log` přístupu k objektu. Systém hodnotu konfiguračního souboru jenom jednou pro každý konkrétní objekt – poprvé vaše aplikace vytvoří objekt. Proto musíte restartovat aplikaci, aby změny vstoupily v platnost.  
  
 V nasazení aplikace povolíte kód trasování překonfigurování přepínače objektů, než aplikaci spustí. Obvykle to zahrnuje zapnutí přepínače objektů a vypnout nebo změnou úrovně trasování a následné restartování aplikace.  
  
## <a name="security-considerations"></a>Důležité informace o zabezpečení  
 Při zápisu dat do protokolu, zvažte následující:  
  
-   **Vyhněte se úniku informace o uživateli.** Ujistěte se, že vaše aplikace zapisuje pouze schválené informace do protokolu. Například může být přijatelné pro protokolu aplikace tak, aby obsahovala uživatelská jména, ale ne uživatelská hesla.  
  
-   **Zabezpečte umístění protokolu.** Všechny protokolu, který obsahuje potenciálně citlivé informace by měly být uložené v zabezpečeném umístění.  
  
-   **Vyhněte se zavádějící informace.** Obecně platí vaše aplikace měla ověřit všechna data zadaná uživatelem před použitím tato data. Jedná se o zápisu dat do protokolu aplikace.  
  
-   **Vyhněte se odepření služby.** Pokud vaše aplikace zapisuje příliš velkého množství informací do protokolu, se může zaplnit protokol nebo se přesvědčte, hledání obtížné důležité informace.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [Protokolování informací z aplikace](../../../../visual-basic/developing-apps/programming/log-info/logging-information-from-the-application.md)
