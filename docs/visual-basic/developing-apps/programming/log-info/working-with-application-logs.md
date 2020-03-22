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
# <a name="working-with-application-logs-in-visual-basic"></a><span data-ttu-id="4d387-102">Práce s protokoly aplikací v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4d387-102">Working with Application Logs in Visual Basic</span></span>

<span data-ttu-id="4d387-103">`My.Application.Log` Objekty `My.Log` a usnadňují zápis protokolování a trasování informací do protokolů.</span><span class="sxs-lookup"><span data-stu-id="4d387-103">The `My.Application.Log` and `My.Log` objects make it easy to write logging and tracing information to logs.</span></span>

## <a name="how-messages-are-logged"></a><span data-ttu-id="4d387-104">Jak jsou protokolovány zprávy</span><span class="sxs-lookup"><span data-stu-id="4d387-104">How Messages are Logged</span></span>

<span data-ttu-id="4d387-105">Nejprve závažnost zprávy je kontrolována s <xref:System.Diagnostics.TraceSource.Switch%2A> vlastností protokolu. <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A></span><span class="sxs-lookup"><span data-stu-id="4d387-105">First, the severity of the message is checked with the <xref:System.Diagnostics.TraceSource.Switch%2A> property of the log's <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> property.</span></span> <span data-ttu-id="4d387-106">Ve výchozím nastavení jsou pouze zprávy závažnosti "Informace" a vyšší jsou předány `TraceListener` na posluchače trasování, zadané v kolekci protokolu.</span><span class="sxs-lookup"><span data-stu-id="4d387-106">By default, only messages of severity "Information" and higher are passed on to the trace listeners, specified in the log's `TraceListener` collection.</span></span> <span data-ttu-id="4d387-107">Potom každý naslouchací proces porovnává závažnost <xref:System.Diagnostics.TraceSource.Switch%2A> zprávy na schytavku posluchače.</span><span class="sxs-lookup"><span data-stu-id="4d387-107">Then, each listener compares the severity of the message to the listener's <xref:System.Diagnostics.TraceSource.Switch%2A> property.</span></span> <span data-ttu-id="4d387-108">Pokud závažnost zprávy je dostatečně vysoká, naslouchací proces zapíše zprávu.</span><span class="sxs-lookup"><span data-stu-id="4d387-108">If the message's severity is high enough, the listener writes out the message.</span></span>

<span data-ttu-id="4d387-109">Následující diagram znázorňuje, jak `WriteEntry` zpráva zapsána `WriteLine` do metody získá předány metody posluchačů trasování protokolu:</span><span class="sxs-lookup"><span data-stu-id="4d387-109">The following diagram shows how a message written to the `WriteEntry` method gets passed to the `WriteLine` methods of the log's trace listeners:</span></span>

![Diagram, který zobrazuje můj volání protokolu.](./media/working-with-application-logs/my-log-call-messages.png)

<span data-ttu-id="4d387-111">Můžete změnit chování protokolu a naslouchací procesy trasování změnou konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="4d387-111">You can change the behavior of the log and the trace listeners by changing the application's configuration file.</span></span> <span data-ttu-id="4d387-112">Následující diagram znázorňuje korespondenci mezi částmi protokolu a konfiguračním souborem.</span><span class="sxs-lookup"><span data-stu-id="4d387-112">The following diagram shows the correspondence between the parts of the log and the configuration file.</span></span>

![Diagram, který ukazuje moje konfigurace protokolu.](./media/working-with-application-logs/my-log-configuration.png)

## <a name="where-messages-are-logged"></a><span data-ttu-id="4d387-114">Kde jsou protokolovány zprávy</span><span class="sxs-lookup"><span data-stu-id="4d387-114">Where Messages are Logged</span></span>

<span data-ttu-id="4d387-115">Pokud sestavení nemá žádný konfigurační soubor, `My.Application.Log` a `My.Log` objekty zapisovat do výstupu ladění aplikace (prostřednictvím třídy). <xref:System.Diagnostics.DefaultTraceListener></span><span class="sxs-lookup"><span data-stu-id="4d387-115">If the assembly has no configuration file, the `My.Application.Log` and `My.Log` objects write to the application's debug output (through the <xref:System.Diagnostics.DefaultTraceListener> class).</span></span> <span data-ttu-id="4d387-116">Kromě toho `My.Application.Log` objekt zapíše do souboru protokolu <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> sestavení (prostřednictvím třídy), zatímco `My.Log` objekt zapíše <xref:System.Web.WebPageTraceListener> do výstupu ASP.NET webové stránky (prostřednictvím třídy).</span><span class="sxs-lookup"><span data-stu-id="4d387-116">In addition, the `My.Application.Log` object writes to the assembly's log file (through the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class), while the `My.Log` object writes to the ASP.NET Web page's output (through the <xref:System.Web.WebPageTraceListener> class).</span></span>

<span data-ttu-id="4d387-117">Ladicí výstup lze zobrazit v okně **Výstup** sady Visual Studio při spuštění aplikace v režimu ladění.</span><span class="sxs-lookup"><span data-stu-id="4d387-117">The debug output can be viewed in the Visual Studio **Output** window when running your application in debug mode.</span></span> <span data-ttu-id="4d387-118">Chcete-li otevřít okno **Výstup,** klepněte na položku nabídky **Ladění,** přejděte na **položku Windows**a potom klepněte na **příkaz Výstup**.</span><span class="sxs-lookup"><span data-stu-id="4d387-118">To open the **Output** window, click the **Debug** menu item, point to **Windows**, and then click **Output**.</span></span> <span data-ttu-id="4d387-119">V okně **Výstup** vyberte **ladění** z pole **Zobrazit výstup z.**</span><span class="sxs-lookup"><span data-stu-id="4d387-119">In the **Output** window, select **Debug** from the **Show output from** box.</span></span>

<span data-ttu-id="4d387-120">Ve výchozím `My.Application.Log` nastavení zapisuje soubor protokolu do cesty pro data aplikace uživatele.</span><span class="sxs-lookup"><span data-stu-id="4d387-120">By default, `My.Application.Log` writes the log file in the path for the user's application data.</span></span> <span data-ttu-id="4d387-121">Cestu můžete získat z <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> vlastnosti <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> objektu.</span><span class="sxs-lookup"><span data-stu-id="4d387-121">You can get the path from the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> property of the <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> object.</span></span> <span data-ttu-id="4d387-122">Formát této cesty je následující:</span><span class="sxs-lookup"><span data-stu-id="4d387-122">The format of that path is as follows:</span></span>

`BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`

<span data-ttu-id="4d387-123">Typická hodnota `BasePath` pro je následující.</span><span class="sxs-lookup"><span data-stu-id="4d387-123">A typical value for `BasePath` is as follows.</span></span>

<span data-ttu-id="4d387-124">C:\Dokumenty a\\`username`nastavení \Data aplikace</span><span class="sxs-lookup"><span data-stu-id="4d387-124">C:\Documents and Settings\\`username`\Application Data</span></span>

<span data-ttu-id="4d387-125">Hodnoty `CompanyName`, `ProductName`a `ProductVersion` pocházejí z informací o sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="4d387-125">The values of `CompanyName`, `ProductName`, and `ProductVersion` come from the application's assembly information.</span></span> <span data-ttu-id="4d387-126">Forma názvu souboru protokolu je *AssemblyName*.log, kde *AssemblyName* je název souboru sestavení bez přípony.</span><span class="sxs-lookup"><span data-stu-id="4d387-126">The form of the log file name is *AssemblyName*.log, where *AssemblyName* is the file name of the assembly without the extension.</span></span> <span data-ttu-id="4d387-127">Pokud je potřeba více než jeden soubor protokolu, například když původní protokol není k dispozici, když se aplikace pokusí o `iteration` zápis do `Integer`protokolu, je formulář pro název souboru protokolu *AssemblyName*-*iteration*.log, kde je kladný .</span><span class="sxs-lookup"><span data-stu-id="4d387-127">If more than one log file is needed, such as when the original log is unavailable when the application attempts to write to the log, the form for the log file name is *AssemblyName*-*iteration*.log, where `iteration` is a positive `Integer`.</span></span>

<span data-ttu-id="4d387-128">Výchozí chování můžete přepsat přidáním nebo změnou konfiguračních souborů počítače a aplikace.</span><span class="sxs-lookup"><span data-stu-id="4d387-128">You can override the default behavior by adding or changing the computer's and the application's configuration files.</span></span> <span data-ttu-id="4d387-129">Další informace naleznete [v tématu Návod: Změna místa, kde my.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="4d387-129">For more information, see [Walkthrough: Changing Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).</span></span>

## <a name="configuring-log-settings"></a><span data-ttu-id="4d387-130">Konfigurace nastavení protokolu</span><span class="sxs-lookup"><span data-stu-id="4d387-130">Configuring Log Settings</span></span>

<span data-ttu-id="4d387-131">Objekt `Log` má výchozí implementaci, která funguje bez konfiguračního souboru aplikace app.config. Chcete-li změnit výchozí hodnoty, je nutné přidat konfigurační soubor s novým nastavením.</span><span class="sxs-lookup"><span data-stu-id="4d387-131">The `Log` object has a default implementation that works without an application configuration file, app.config. To change the defaults, you must add a configuration file with the new settings.</span></span> <span data-ttu-id="4d387-132">Další informace naleznete [v tématu Návod: Filtrování výstupu my.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="4d387-132">For more information, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>

<span data-ttu-id="4d387-133">Oddíly konfigurace protokolu jsou `<system.diagnostics>` umístěny v `<configuration>` uzlu v hlavním uzlu souboru app.config.</span><span class="sxs-lookup"><span data-stu-id="4d387-133">The log configuration sections are located in the `<system.diagnostics>` node in the main `<configuration>` node of the app.config file.</span></span> <span data-ttu-id="4d387-134">Informace protokolu jsou definovány v několika uzlech:</span><span class="sxs-lookup"><span data-stu-id="4d387-134">Log information is defined in several nodes:</span></span>

- <span data-ttu-id="4d387-135">Naslouchací procesy `Log` `<sources>` pro objekt jsou definovány v uzlu s názvem DefaultSource.</span><span class="sxs-lookup"><span data-stu-id="4d387-135">The listeners for the `Log` object are defined in the `<sources>` node named DefaultSource.</span></span>

- <span data-ttu-id="4d387-136">Filtr závažnosti objektu `Log` je definován `<switches>` v uzlu s názvem DefaultSwitch.</span><span class="sxs-lookup"><span data-stu-id="4d387-136">The severity filter for the `Log` object is defined in the `<switches>` node named DefaultSwitch.</span></span>

- <span data-ttu-id="4d387-137">Naslouchací procesy protokolu jsou definovány `<sharedListeners>` v uzlu.</span><span class="sxs-lookup"><span data-stu-id="4d387-137">The log listeners are defined in the `<sharedListeners>` node.</span></span>

 <span data-ttu-id="4d387-138">Příklady `<sources>`, `<switches>`a `<sharedListeners>` uzly jsou uvedeny v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="4d387-138">Examples of `<sources>`, `<switches>`, and `<sharedListeners>` nodes are shown in the following code:</span></span>

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

## <a name="changing-log-settings-after-deployment"></a><span data-ttu-id="4d387-139">Změna nastavení protokolu po nasazení</span><span class="sxs-lookup"><span data-stu-id="4d387-139">Changing Log Settings after Deployment</span></span>

<span data-ttu-id="4d387-140">Při vývoji aplikace jsou její nastavení konfigurace uložena v souboru app.config, jak je znázorněno na výše uvedených příkladech.</span><span class="sxs-lookup"><span data-stu-id="4d387-140">When you develop an application, its configuration settings are stored in the app.config file, as shown in the examples above.</span></span> <span data-ttu-id="4d387-141">Po nasazení aplikace můžete protokol nakonfigurovat úpravou konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="4d387-141">After you deploy your application, you can still configure the log by editing the configuration file.</span></span> <span data-ttu-id="4d387-142">V aplikaci založené na systému Windows je název tohoto souboru *applicationName*.exe.config a musí být umístěn ve stejné složce jako spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="4d387-142">In a Windows-based application, this file's name is *applicationName*.exe.config, and it must reside in the same folder as the executable file.</span></span> <span data-ttu-id="4d387-143">Pro webovou aplikaci se jedná o soubor Web.config přidružený k projektu.</span><span class="sxs-lookup"><span data-stu-id="4d387-143">For a Web application, this is the Web.config file associated with the project.</span></span>

<span data-ttu-id="4d387-144">Když aplikace spustí kód, který vytvoří instanci třídy poprvé, zkontroluje konfigurační soubor informace o objektu.</span><span class="sxs-lookup"><span data-stu-id="4d387-144">When your application executes the code that creates an instance of a class for the first time, it checks the configuration file for information about the object.</span></span> <span data-ttu-id="4d387-145">U `Log` objektu k tomu dochází `Log` při prvním přístupu k objektu.</span><span class="sxs-lookup"><span data-stu-id="4d387-145">For the `Log` object, this happens the first time the `Log` object is accessed.</span></span> <span data-ttu-id="4d387-146">Systém zkontroluje konfigurační soubor pouze jednou pro konkrétní objekt – při prvním vytvoření objektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="4d387-146">The system examines the configuration file only once for any particular object—the first time your application creates the object.</span></span> <span data-ttu-id="4d387-147">Proto může být nutné restartovat aplikaci pro změny se projeví.</span><span class="sxs-lookup"><span data-stu-id="4d387-147">Therefore, you may need to restart the application for the changes to take effect.</span></span>

<span data-ttu-id="4d387-148">V nasazené aplikaci povolíte trasovací kód změnou konfigurace objektů přepínače před spuštěním aplikace.</span><span class="sxs-lookup"><span data-stu-id="4d387-148">In a deployed application, you enable trace code by reconfiguring switch objects before your application starts.</span></span> <span data-ttu-id="4d387-149">Obvykle to zahrnuje zapnutí a vypnutí objektů přepínače nebo změnou úrovní trasování a restartování aplikace.</span><span class="sxs-lookup"><span data-stu-id="4d387-149">Typically, this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>

## <a name="security-considerations"></a><span data-ttu-id="4d387-150">Aspekty zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4d387-150">Security Considerations</span></span>

<span data-ttu-id="4d387-151">Při zápisu dat do protokolu zvažte následující:</span><span class="sxs-lookup"><span data-stu-id="4d387-151">Consider the following when writing data to the log:</span></span>

- <span data-ttu-id="4d387-152">**Vyhněte se úniku informací o uživateli.**</span><span class="sxs-lookup"><span data-stu-id="4d387-152">**Avoid leaking user information.**</span></span> <span data-ttu-id="4d387-153">Ujistěte se, že vaše aplikace zapisuje pouze schválené informace do protokolu.</span><span class="sxs-lookup"><span data-stu-id="4d387-153">Ensure that your application writes only approved information to the log.</span></span> <span data-ttu-id="4d387-154">Může být například přijatelné, aby protokol aplikace obsahoval uživatelská jména, ale ne uživatelská hesla.</span><span class="sxs-lookup"><span data-stu-id="4d387-154">For example, it may be acceptable for the application log to contain user names, but not user passwords.</span></span>

- <span data-ttu-id="4d387-155">**Zabezpečte umístění protokolů.**</span><span class="sxs-lookup"><span data-stu-id="4d387-155">**Make log locations secure.**</span></span> <span data-ttu-id="4d387-156">Jakýkoli protokol, který obsahuje potenciálně citlivé informace, by měl být uložen na bezpečném místě.</span><span class="sxs-lookup"><span data-stu-id="4d387-156">Any log that contains potentially sensitive information should be stored in a secure location.</span></span>

- <span data-ttu-id="4d387-157">**Vyhněte se zavádějícím informacím.**</span><span class="sxs-lookup"><span data-stu-id="4d387-157">**Avoid misleading information.**</span></span> <span data-ttu-id="4d387-158">Obecně platí, že aplikace by měla ověřit všechna data zadaná uživatelem před použitím dat.</span><span class="sxs-lookup"><span data-stu-id="4d387-158">In general, your application should validate all data entered by a user before using that data.</span></span> <span data-ttu-id="4d387-159">To zahrnuje zápis dat do protokolu aplikace.</span><span class="sxs-lookup"><span data-stu-id="4d387-159">This includes writing data to the application log.</span></span>

- <span data-ttu-id="4d387-160">**Vyhněte se odmítnutí služby.**</span><span class="sxs-lookup"><span data-stu-id="4d387-160">**Avoid denial of service.**</span></span> <span data-ttu-id="4d387-161">Pokud aplikace zapíše do protokolu příliš mnoho informací, může vyplnit protokol nebo ztížit hledání důležitých informací.</span><span class="sxs-lookup"><span data-stu-id="4d387-161">If your application writes too much information to the log, it could fill the log or make finding important information difficult.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d387-162">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d387-162">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="4d387-163">Protokolování informací z aplikace</span><span class="sxs-lookup"><span data-stu-id="4d387-163">Logging Information from the Application</span></span>](../../../../visual-basic/developing-apps/programming/log-info/index.md)
