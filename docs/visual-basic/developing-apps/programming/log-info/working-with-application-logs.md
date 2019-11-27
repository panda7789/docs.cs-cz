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
# <a name="working-with-application-logs-in-visual-basic"></a><span data-ttu-id="e6d4a-102">Práce s protokoly aplikací v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e6d4a-102">Working with Application Logs in Visual Basic</span></span>

<span data-ttu-id="e6d4a-103">Objekty `My.Application.Log` a `My.Log` usnadňují zápis informací o protokolování a trasování do protokolů.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-103">The `My.Application.Log` and `My.Log` objects make it easy to write logging and tracing information to logs.</span></span>

## <a name="how-messages-are-logged"></a><span data-ttu-id="e6d4a-104">Způsob protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="e6d4a-104">How Messages are Logged</span></span>

<span data-ttu-id="e6d4a-105">Nejdřív se u zprávy kontroluje závažnost pomocí vlastnosti <xref:System.Diagnostics.TraceSource.Switch%2A> vlastnosti <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> protokolu.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-105">First, the severity of the message is checked with the <xref:System.Diagnostics.TraceSource.Switch%2A> property of the log's <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> property.</span></span> <span data-ttu-id="e6d4a-106">Ve výchozím nastavení jsou posluchačům trasování, které jsou zadány v kolekci `TraceListener` protokolu, pouze zprávy "informace o závažnosti" a vyšší.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-106">By default, only messages of severity "Information" and higher are passed on to the trace listeners, specified in the log's `TraceListener` collection.</span></span> <span data-ttu-id="e6d4a-107">Potom každé naslouchací proces porovná závažnost zprávy s vlastností <xref:System.Diagnostics.TraceSource.Switch%2A> naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-107">Then, each listener compares the severity of the message to the listener's <xref:System.Diagnostics.TraceSource.Switch%2A> property.</span></span> <span data-ttu-id="e6d4a-108">Pokud je závažnost zprávy dostatečně vysoká, posluchač zapíše zprávu.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-108">If the message's severity is high enough, the listener writes out the message.</span></span>

<span data-ttu-id="e6d4a-109">Následující diagram znázorňuje, jak se zpráva zapsaná do metody `WriteEntry` předává do `WriteLine` metod posluchačů trasování protokolu:</span><span class="sxs-lookup"><span data-stu-id="e6d4a-109">The following diagram shows how a message written to the `WriteEntry` method gets passed to the `WriteLine` methods of the log's trace listeners:</span></span>

![Diagram, který zobrazuje moje volání protokolu](./media/working-with-application-logs/my-log-call-messages.png)

<span data-ttu-id="e6d4a-111">Můžete změnit chování protokolu a posluchačů trasování změnou konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-111">You can change the behavior of the log and the trace listeners by changing the application's configuration file.</span></span> <span data-ttu-id="e6d4a-112">Následující diagram znázorňuje korespondenci mezi částmi protokolu a konfiguračním souborem.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-112">The following diagram shows the correspondence between the parts of the log and the configuration file.</span></span>

![Diagram, který zobrazuje konfiguraci protokolu.](./media/working-with-application-logs/my-log-configuration.png)

## <a name="where-messages-are-logged"></a><span data-ttu-id="e6d4a-114">Kam se zaznamenávají zprávy</span><span class="sxs-lookup"><span data-stu-id="e6d4a-114">Where Messages are Logged</span></span>

<span data-ttu-id="e6d4a-115">Pokud sestavení nemá žádný konfigurační soubor, objekty `My.Application.Log` a `My.Log` zapisují do výstupu ladění aplikace (prostřednictvím třídy <xref:System.Diagnostics.DefaultTraceListener>).</span><span class="sxs-lookup"><span data-stu-id="e6d4a-115">If the assembly has no configuration file, the `My.Application.Log` and `My.Log` objects write to the application's debug output (through the <xref:System.Diagnostics.DefaultTraceListener> class).</span></span> <span data-ttu-id="e6d4a-116">Kromě toho `My.Application.Log` objekt zapisuje do souboru protokolu sestavení (prostřednictvím <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> třídy), zatímco objekt `My.Log` zapisuje do výstupu webové stránky ASP.NET (prostřednictvím třídy <xref:System.Web.WebPageTraceListener>).</span><span class="sxs-lookup"><span data-stu-id="e6d4a-116">In addition, the `My.Application.Log` object writes to the assembly's log file (through the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class), while the `My.Log` object writes to the ASP.NET Web page's output (through the <xref:System.Web.WebPageTraceListener> class).</span></span>

<span data-ttu-id="e6d4a-117">Výstup ladění lze zobrazit v okně **výstupu** sady Visual Studio při spuštění aplikace v režimu ladění.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-117">The debug output can be viewed in the Visual Studio **Output** window when running your application in debug mode.</span></span> <span data-ttu-id="e6d4a-118">Chcete-li otevřít okno **výstup** , klikněte na položku nabídky **ladění** , přejděte na příkaz **Windows**a potom klikněte na možnost **výstup**.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-118">To open the **Output** window, click the **Debug** menu item, point to **Windows**, and then click **Output**.</span></span> <span data-ttu-id="e6d4a-119">V okně **výstup** vyberte **ladit** v poli **Zobrazit výstup z** .</span><span class="sxs-lookup"><span data-stu-id="e6d4a-119">In the **Output** window, select **Debug** from the **Show output from** box.</span></span>

<span data-ttu-id="e6d4a-120">Ve výchozím nastavení `My.Application.Log` zapisuje soubor protokolu do cesty pro data aplikace uživatele.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-120">By default, `My.Application.Log` writes the log file in the path for the user's application data.</span></span> <span data-ttu-id="e6d4a-121">Cestu můžete získat z vlastnosti <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> objektu <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A>.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-121">You can get the path from the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> property of the <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> object.</span></span> <span data-ttu-id="e6d4a-122">Formát této cesty je následující:</span><span class="sxs-lookup"><span data-stu-id="e6d4a-122">The format of that path is as follows:</span></span>

`BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`

<span data-ttu-id="e6d4a-123">Typická hodnota pro `BasePath` je následující.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-123">A typical value for `BasePath` is as follows.</span></span>

<span data-ttu-id="e6d4a-124">C:\Documents and Settings\\`username`\Application data</span><span class="sxs-lookup"><span data-stu-id="e6d4a-124">C:\Documents and Settings\\`username`\Application Data</span></span>

<span data-ttu-id="e6d4a-125">Hodnoty `CompanyName`, `ProductName`a `ProductVersion` pocházejí z informací o sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-125">The values of `CompanyName`, `ProductName`, and `ProductVersion` come from the application's assembly information.</span></span> <span data-ttu-id="e6d4a-126">Forma názvu souboru protokolu je *AssemblyName*. log, kde *AssemblyName* je název souboru sestavení bez přípony.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-126">The form of the log file name is *AssemblyName*.log, where *AssemblyName* is the file name of the assembly without the extension.</span></span> <span data-ttu-id="e6d4a-127">Pokud je potřeba více než jeden soubor protokolu, například když je původní protokol nedostupný, když se aplikace pokusí zapisovat do protokolu, je formulář pro název souboru protokolu *AssemblyName*-*iterace*. log, kde `iteration` je kladné `Integer`.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-127">If more than one log file is needed, such as when the original log is unavailable when the application attempts to write to the log, the form for the log file name is *AssemblyName*-*iteration*.log, where `iteration` is a positive `Integer`.</span></span>

<span data-ttu-id="e6d4a-128">Výchozí chování můžete přepsat přidáním nebo změnou konfiguračních souborů aplikace a počítače.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-128">You can override the default behavior by adding or changing the computer's and the application's configuration files.</span></span> <span data-ttu-id="e6d4a-129">Další informace naleznete v tématu [Návod: Změna místa, kam aplikace My. Application. Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="e6d4a-129">For more information, see [Walkthrough: Changing Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).</span></span>

## <a name="configuring-log-settings"></a><span data-ttu-id="e6d4a-130">Konfigurace nastavení protokolu</span><span class="sxs-lookup"><span data-stu-id="e6d4a-130">Configuring Log Settings</span></span>

<span data-ttu-id="e6d4a-131">Objekt `Log` má výchozí implementaci, která funguje bez konfiguračního souboru aplikace App. config. Chcete-li změnit výchozí nastavení, je nutné přidat konfigurační soubor s novým nastavením.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-131">The `Log` object has a default implementation that works without an application configuration file, app.config. To change the defaults, you must add a configuration file with the new settings.</span></span> <span data-ttu-id="e6d4a-132">Další informace najdete v tématu [Návod: filtrování výstupu my. Application. log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="e6d4a-132">For more information, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>

<span data-ttu-id="e6d4a-133">Konfigurační oddíly protokolu jsou umístěné v uzlu `<system.diagnostics>` v hlavním uzlu `<configuration>` souboru App. config.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-133">The log configuration sections are located in the `<system.diagnostics>` node in the main `<configuration>` node of the app.config file.</span></span> <span data-ttu-id="e6d4a-134">Informace protokolu jsou definované v několika uzlech:</span><span class="sxs-lookup"><span data-stu-id="e6d4a-134">Log information is defined in several nodes:</span></span>

- <span data-ttu-id="e6d4a-135">Naslouchací procesy pro objekt `Log` jsou definovány v uzlu `<sources>` s názvem DefaultSource.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-135">The listeners for the `Log` object are defined in the `<sources>` node named DefaultSource.</span></span>

- <span data-ttu-id="e6d4a-136">Filtr závažnosti pro objekt `Log` je definován v uzlu `<switches>` s názvem DefaultSwitch.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-136">The severity filter for the `Log` object is defined in the `<switches>` node named DefaultSwitch.</span></span>

- <span data-ttu-id="e6d4a-137">Naslouchací procesy protokolu jsou definovány v uzlu `<sharedListeners>`.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-137">The log listeners are defined in the `<sharedListeners>` node.</span></span>

 <span data-ttu-id="e6d4a-138">Příklady `<sources>`, `<switches>`a `<sharedListeners>` uzlů jsou uvedeny v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="e6d4a-138">Examples of `<sources>`, `<switches>`, and `<sharedListeners>` nodes are shown in the following code:</span></span>

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

## <a name="changing-log-settings-after-deployment"></a><span data-ttu-id="e6d4a-139">Změna nastavení protokolu po nasazení</span><span class="sxs-lookup"><span data-stu-id="e6d4a-139">Changing Log Settings after Deployment</span></span>

<span data-ttu-id="e6d4a-140">Při vývoji aplikace se její nastavení konfigurace ukládají do souboru App. config, jak je znázorněno v předchozích příkladech.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-140">When you develop an application, its configuration settings are stored in the app.config file, as shown in the examples above.</span></span> <span data-ttu-id="e6d4a-141">Po nasazení aplikace můžete protokol i nadále konfigurovat úpravou konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-141">After you deploy your application, you can still configure the log by editing the configuration file.</span></span> <span data-ttu-id="e6d4a-142">V aplikaci pro systém Windows je název tohoto souboru *ApplicationName*. exe. config a musí být umístěn ve stejné složce jako spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-142">In a Windows-based application, this file's name is *applicationName*.exe.config, and it must reside in the same folder as the executable file.</span></span> <span data-ttu-id="e6d4a-143">Pro webovou aplikaci je to soubor Web. config přidružený k projektu.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-143">For a Web application, this is the Web.config file associated with the project.</span></span>

<span data-ttu-id="e6d4a-144">Když vaše aplikace spustí kód, který vytvoří instanci třídy poprvé, zkontroluje konfigurační soubor o informace o objektu.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-144">When your application executes the code that creates an instance of a class for the first time, it checks the configuration file for information about the object.</span></span> <span data-ttu-id="e6d4a-145">Pro objekt `Log` k tomu dojde při prvním otevření objektu `Log`.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-145">For the `Log` object, this happens the first time the `Log` object is accessed.</span></span> <span data-ttu-id="e6d4a-146">Systém prověřuje konfigurační soubor pouze jednou pro konkrétní objekt – při prvním vytvoření objektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-146">The system examines the configuration file only once for any particular object—the first time your application creates the object.</span></span> <span data-ttu-id="e6d4a-147">Proto může být nutné aplikaci restartovat, aby se změny projevily.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-147">Therefore, you may need to restart the application for the changes to take effect.</span></span>

<span data-ttu-id="e6d4a-148">V nasazené aplikaci povolíte trasovací kód tím, že znovu nakonfigurujete objekty přepínače před spuštěním aplikace.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-148">In a deployed application, you enable trace code by reconfiguring switch objects before your application starts.</span></span> <span data-ttu-id="e6d4a-149">Obvykle to zahrnuje zapnutí a vypnutí objektů přepínače nebo změnu úrovní trasování a následné restartování aplikace.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-149">Typically, this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>

## <a name="security-considerations"></a><span data-ttu-id="e6d4a-150">Důležité informace o zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e6d4a-150">Security Considerations</span></span>

<span data-ttu-id="e6d4a-151">Při zápisu dat do protokolu Vezměte v úvahu následující skutečnosti:</span><span class="sxs-lookup"><span data-stu-id="e6d4a-151">Consider the following when writing data to the log:</span></span>

- <span data-ttu-id="e6d4a-152">**Vyhněte se nevracení informací o uživateli.**</span><span class="sxs-lookup"><span data-stu-id="e6d4a-152">**Avoid leaking user information.**</span></span> <span data-ttu-id="e6d4a-153">Ujistěte se, že vaše aplikace zapisuje do protokolu pouze schválené informace.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-153">Ensure that your application writes only approved information to the log.</span></span> <span data-ttu-id="e6d4a-154">Například může být přijatelné, aby protokol aplikace obsahoval uživatelská jména, ale ne hesla uživatelů.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-154">For example, it may be acceptable for the application log to contain user names, but not user passwords.</span></span>

- <span data-ttu-id="e6d4a-155">**Zajistěte zabezpečení umístění protokolu.**</span><span class="sxs-lookup"><span data-stu-id="e6d4a-155">**Make log locations secure.**</span></span> <span data-ttu-id="e6d4a-156">Jakýkoli protokol, který obsahuje potenciálně citlivé informace, by měl být uložený v zabezpečeném umístění.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-156">Any log that contains potentially sensitive information should be stored in a secure location.</span></span>

- <span data-ttu-id="e6d4a-157">**Vyhněte se klamavým informacím.**</span><span class="sxs-lookup"><span data-stu-id="e6d4a-157">**Avoid misleading information.**</span></span> <span data-ttu-id="e6d4a-158">Obecně platí, že aplikace musí před použitím těchto dat ověřit všechna data zadaná uživatelem.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-158">In general, your application should validate all data entered by a user before using that data.</span></span> <span data-ttu-id="e6d4a-159">To zahrnuje zápis dat do aplikačního protokolu.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-159">This includes writing data to the application log.</span></span>

- <span data-ttu-id="e6d4a-160">**Vyhněte se odepření služby.**</span><span class="sxs-lookup"><span data-stu-id="e6d4a-160">**Avoid denial of service.**</span></span> <span data-ttu-id="e6d4a-161">Pokud vaše aplikace zapisuje do protokolu příliš mnoho informací, mohl by protokol vyplnit nebo najít důležité informace, které by byly obtížné.</span><span class="sxs-lookup"><span data-stu-id="e6d4a-161">If your application writes too much information to the log, it could fill the log or make finding important information difficult.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6d4a-162">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6d4a-162">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="e6d4a-163">Protokolování informací z aplikace</span><span class="sxs-lookup"><span data-stu-id="e6d4a-163">Logging Information from the Application</span></span>](../../../../visual-basic/developing-apps/programming/log-info/index.md)
