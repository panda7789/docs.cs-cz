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
# <a name="working-with-application-logs-in-visual-basic"></a><span data-ttu-id="fba75-102">Práce s protokoly aplikací v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fba75-102">Working with Application Logs in Visual Basic</span></span>
<span data-ttu-id="fba75-103">`My.Applicaton.Log` a `My.Log` objekty usnadňují zapisovat do protokolů informace o trasování a protokolování.</span><span class="sxs-lookup"><span data-stu-id="fba75-103">The `My.Applicaton.Log` and `My.Log` objects make it easy to write logging and tracing information to logs.</span></span>  
  
## <a name="how-messages-are-logged"></a><span data-ttu-id="fba75-104">Jak jsou zprávy protokolovány</span><span class="sxs-lookup"><span data-stu-id="fba75-104">How Messages are Logged</span></span>  
 <span data-ttu-id="fba75-105">Nejprve je zaškrtnuta možnost závažnost zprávy s <xref:System.Diagnostics.TraceSource.Switch%2A> vlastnost v protokolu <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fba75-105">First, the severity of the message is checked with the <xref:System.Diagnostics.TraceSource.Switch%2A> property of the log's <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> property.</span></span> <span data-ttu-id="fba75-106">Ve výchozím pouze zprávy s závažnosti "Informace" a vyšší jsou předány naslouchací procesy trasování, zadaný v protokolu nástroje `TraceListener` kolekce.</span><span class="sxs-lookup"><span data-stu-id="fba75-106">By default, only messages of severity "Information" and higher are passed on to the trace listeners, specified in the log's `TraceListener` collection.</span></span> <span data-ttu-id="fba75-107">Potom každý naslouchací proces porovná závažnost zprávy naslouchacího procesu <xref:System.Diagnostics.TraceSource.Switch%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fba75-107">Then, each listener compares the severity of the message to the listener's <xref:System.Diagnostics.TraceSource.Switch%2A> property.</span></span> <span data-ttu-id="fba75-108">Pokud závažnost zprávy je dostatečně vysoká, naslouchací proces vypíše zprávu.</span><span class="sxs-lookup"><span data-stu-id="fba75-108">If the message's severity is high enough, the listener writes out the message.</span></span>  
  
 <span data-ttu-id="fba75-109">Následující obrázek ukazuje, jak zpráva zapsána do `WriteEntry` metoda předána do `WriteLine` naslouchací procesy trasování metody v protokolu:</span><span class="sxs-lookup"><span data-stu-id="fba75-109">The following diagram shows how a message written to the `WriteEntry` method gets passed to the `WriteLine` methods of the log's trace listeners:</span></span>  
  
 <span data-ttu-id="fba75-110">![Moje volání protokolu](../../../../visual-basic/developing-apps/programming/log-info/media/mylogcall.png "MyLogCall")</span><span class="sxs-lookup"><span data-stu-id="fba75-110">![My Log Call](../../../../visual-basic/developing-apps/programming/log-info/media/mylogcall.png "MyLogCall")</span></span>  
  
 <span data-ttu-id="fba75-111">Chování protokolu a naslouchací procesy trasování můžete změnit změnou souboru konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="fba75-111">You can change the behavior of the log and the trace listeners by changing the application's configuration file.</span></span> <span data-ttu-id="fba75-112">Následující diagram znázorňuje mezi části protokolu a konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="fba75-112">The following diagram shows the correspondence between the parts of the log and the configuration file.</span></span>  
  
 <span data-ttu-id="fba75-113">![Moje konfigurace protokolů](../../../../visual-basic/developing-apps/programming/log-info/media/mylogconfig.png "MyLogConfig")</span><span class="sxs-lookup"><span data-stu-id="fba75-113">![My Log Configuration](../../../../visual-basic/developing-apps/programming/log-info/media/mylogconfig.png "MyLogConfig")</span></span>  
  
## <a name="where-messages-are-logged"></a><span data-ttu-id="fba75-114">Kde se protokolují zprávy</span><span class="sxs-lookup"><span data-stu-id="fba75-114">Where Messages are Logged</span></span>  
 <span data-ttu-id="fba75-115">Pokud sestavení nemá žádný konfigurační soubor `My.Application.Log` a `My.Log` objekty zápis výstupu ladění aplikace (prostřednictvím <xref:System.Diagnostics.DefaultTraceListener> třídy).</span><span class="sxs-lookup"><span data-stu-id="fba75-115">If the assembly has no configuration file, the `My.Application.Log` and `My.Log` objects write to the application's debug output (through the <xref:System.Diagnostics.DefaultTraceListener> class).</span></span> <span data-ttu-id="fba75-116">Kromě toho `My.Application.Log` objekt zapisuje do souboru protokolu sestavení (prostřednictvím <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> – třída), při `My.Log` objekt zapíše do výstupního webová stránka ASP.NET (prostřednictvím <xref:System.Web.WebPageTraceListener> – třída).</span><span class="sxs-lookup"><span data-stu-id="fba75-116">In addition, the `My.Application.Log` object writes to the assembly's log file (through the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class), while the `My.Log` object writes to the ASP.NET Web page's output (through the <xref:System.Web.WebPageTraceListener> class).</span></span>  
  
 <span data-ttu-id="fba75-117">Výstup ladění lze zobrazit v sadě Visual Studio **výstup** okno při spuštění aplikace v režimu ladění.</span><span class="sxs-lookup"><span data-stu-id="fba75-117">The debug output can be viewed in the Visual Studio **Output** window when running your application in debug mode.</span></span> <span data-ttu-id="fba75-118">Otevřete **výstup** okně klikněte na tlačítko **ladění** položky nabídky, přejděte na příkaz **Windows**a potom klikněte na **výstup**.</span><span class="sxs-lookup"><span data-stu-id="fba75-118">To open the **Output** window, click the **Debug** menu item, point to **Windows**, and then click **Output**.</span></span> <span data-ttu-id="fba75-119">V **výstup** vyberte **ladění** z **zobrazit výstup z** pole.</span><span class="sxs-lookup"><span data-stu-id="fba75-119">In the **Output** window, select **Debug** from the **Show output from** box.</span></span>  
  
 <span data-ttu-id="fba75-120">Ve výchozím nastavení `My.Application.Log` soubor protokolu se zapisují cesta k datům uživatele aplikace.</span><span class="sxs-lookup"><span data-stu-id="fba75-120">By default, `My.Application.Log` writes the log file in the path for the user's application data.</span></span> <span data-ttu-id="fba75-121">Můžete získat cestu z <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> vlastnost <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> objektu.</span><span class="sxs-lookup"><span data-stu-id="fba75-121">You can get the path from the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> property of the <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> object.</span></span> <span data-ttu-id="fba75-122">Formát cesty je následující:</span><span class="sxs-lookup"><span data-stu-id="fba75-122">The format of that path is as follows:</span></span>  
  
 `BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`  
  
 <span data-ttu-id="fba75-123">Typické hodnota pro `BasePath` je následující.</span><span class="sxs-lookup"><span data-stu-id="fba75-123">A typical value for `BasePath` is as follows.</span></span>  
  
 <span data-ttu-id="fba75-124">C:\Documents and Settings\\`username`\Application dat</span><span class="sxs-lookup"><span data-stu-id="fba75-124">C:\Documents and Settings\\`username`\Application Data</span></span>  
  
 <span data-ttu-id="fba75-125">Hodnoty `CompanyName`, `ProductName`, a `ProductVersion` pocházejí z informací o sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="fba75-125">The values of `CompanyName`, `ProductName`, and `ProductVersion` come from the application's assembly information.</span></span> <span data-ttu-id="fba75-126">Název souboru protokolu je *AssemblyName*.log, kde *AssemblyName* je název souboru bez přípony sestavení.</span><span class="sxs-lookup"><span data-stu-id="fba75-126">The form of the log file name is *AssemblyName*.log, where *AssemblyName* is the file name of the assembly without the extension.</span></span> <span data-ttu-id="fba75-127">V případě potřeby je více než jeden soubor protokolu, například když není k dispozici v původní protokolu když se aplikace pokusí zapisovat do protokolu, formát názvu souboru protokolu je *AssemblyName*-*iterace* .log, kde `iteration` pozitivní `Integer`.</span><span class="sxs-lookup"><span data-stu-id="fba75-127">If more than one log file is needed, such as when the original log is unavailable when the application attempts to write to the log, the form for the log file name is *AssemblyName*-*iteration*.log, where `iteration` is a positive `Integer`.</span></span>  
  
 <span data-ttu-id="fba75-128">Výchozí chování můžete přepsat pomocí přidání nebo změna konfigurační soubory aplikace a počítače.</span><span class="sxs-lookup"><span data-stu-id="fba75-128">You can override the default behavior by adding or changing the computer's and the application's configuration files.</span></span> <span data-ttu-id="fba75-129">Další informace najdete v tématu [návod: Změna kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="fba75-129">For more information, see [Walkthrough: Changing Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).</span></span>  
  
## <a name="configuring-log-settings"></a><span data-ttu-id="fba75-130">Konfigurace nastavení protokolu</span><span class="sxs-lookup"><span data-stu-id="fba75-130">Configuring Log Settings</span></span>  
 <span data-ttu-id="fba75-131">`Log` Objekt má výchozí implementace, která funguje bez konfigurační soubor aplikace app.config. Chcete-li změnit výchozí hodnoty, musíte přidat konfigurační soubor s novým nastavením.</span><span class="sxs-lookup"><span data-stu-id="fba75-131">The `Log` object has a default implementation that works without an application configuration file, app.config. To change the defaults, you must add a configuration file with the new settings.</span></span> <span data-ttu-id="fba75-132">Další informace najdete v tématu [návod: filtrování výstupu My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="fba75-132">For more information, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>  
  
 <span data-ttu-id="fba75-133">Konfigurační oddíly protokolu jsou umístěné v `<system.diagnostics>` uzlu v hlavní `<configuration>` uzlu souboru app.config.</span><span class="sxs-lookup"><span data-stu-id="fba75-133">The log configuration sections are located in the `<system.diagnostics>` node in the main `<configuration>` node of the app.config file.</span></span> <span data-ttu-id="fba75-134">Informace v protokolu je definována v několika uzly:</span><span class="sxs-lookup"><span data-stu-id="fba75-134">Log information is defined in several nodes:</span></span>  
  
-   <span data-ttu-id="fba75-135">Naslouchací procesy pro `Log` objekt jsou definovány v `<sources>` uzel s názvem DefaultSource.</span><span class="sxs-lookup"><span data-stu-id="fba75-135">The listeners for the `Log` object are defined in the `<sources>` node named DefaultSource.</span></span>  
  
-   <span data-ttu-id="fba75-136">Filtr závažnosti pro `Log` objektu je definována v `<switches>` uzel s názvem DefaultSwitch.</span><span class="sxs-lookup"><span data-stu-id="fba75-136">The severity filter for the `Log` object is defined in the `<switches>` node named DefaultSwitch.</span></span>  
  
-   <span data-ttu-id="fba75-137">Naslouchací procesy pro protokoly jsou definovány v `<sharedListeners>` uzlu.</span><span class="sxs-lookup"><span data-stu-id="fba75-137">The log listeners are defined in the `<sharedListeners>` node.</span></span>  
  
 <span data-ttu-id="fba75-138">Příklady `<sources>`, `<switches>`, a `<sharedListeners>` uzly jsou uvedeny v následující kód:</span><span class="sxs-lookup"><span data-stu-id="fba75-138">Examples of `<sources>`, `<switches>`, and `<sharedListeners>` nodes are shown in the following code:</span></span>  
  
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
  
## <a name="changing-log-settings-after-deployment"></a><span data-ttu-id="fba75-139">Změna nastavení protokolu po nasazení</span><span class="sxs-lookup"><span data-stu-id="fba75-139">Changing Log Settings after Deployment</span></span>  
 <span data-ttu-id="fba75-140">Při vývoji aplikace, nastavení konfigurace se uloží v souboru app.config, jak je vidět ve výše uvedených příkladech.</span><span class="sxs-lookup"><span data-stu-id="fba75-140">When you develop an application, its configuration settings are stored in the app.config file, as shown in the examples above.</span></span> <span data-ttu-id="fba75-141">Poté, co nasadíte aplikaci, můžete přesto nakonfigurovat protokol úpravou konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="fba75-141">After you deploy your application, you can still configure the log by editing the configuration file.</span></span> <span data-ttu-id="fba75-142">V aplikaci systému Windows, je název tohoto souboru *applicationName*. exe.config a se musí nacházet ve stejné složce jako spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="fba75-142">In a Windows-based application, this file's name is *applicationName*.exe.config, and it must reside in the same folder as the executable file.</span></span> <span data-ttu-id="fba75-143">Pro webovou aplikaci Toto je soubor Web.config přidružený k projektu.</span><span class="sxs-lookup"><span data-stu-id="fba75-143">For a Web application, this is the Web.config file associated with the project.</span></span>  
  
 <span data-ttu-id="fba75-144">Když aplikaci spustí kód, který vytvoří instanci třídy poprvé, zkontroluje konfiguračního souboru pro informace o objektu.</span><span class="sxs-lookup"><span data-stu-id="fba75-144">When your application executes the code that creates an instance of a class for the first time, it checks the configuration file for information about the object.</span></span> <span data-ttu-id="fba75-145">Pro `Log` objektu, k tomu dojde při prvním `Log` přístupu k objektu.</span><span class="sxs-lookup"><span data-stu-id="fba75-145">For the `Log` object, this happens the first time the `Log` object is accessed.</span></span> <span data-ttu-id="fba75-146">Systém hodnotu konfiguračního souboru jenom jednou pro každý konkrétní objekt – poprvé vaše aplikace vytvoří objekt.</span><span class="sxs-lookup"><span data-stu-id="fba75-146">The system examines the configuration file only once for any particular object—the first time your application creates the object.</span></span> <span data-ttu-id="fba75-147">Proto musíte restartovat aplikaci, aby změny vstoupily v platnost.</span><span class="sxs-lookup"><span data-stu-id="fba75-147">Therefore, you may need to restart the application for the changes to take effect.</span></span>  
  
 <span data-ttu-id="fba75-148">V nasazení aplikace povolíte kód trasování překonfigurování přepínače objektů, než aplikaci spustí.</span><span class="sxs-lookup"><span data-stu-id="fba75-148">In a deployed application, you enable trace code by reconfiguring switch objects before your application starts.</span></span> <span data-ttu-id="fba75-149">Obvykle to zahrnuje zapnutí přepínače objektů a vypnout nebo změnou úrovně trasování a následné restartování aplikace.</span><span class="sxs-lookup"><span data-stu-id="fba75-149">Typically, this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>  
  
## <a name="security-considerations"></a><span data-ttu-id="fba75-150">Důležité informace o zabezpečení</span><span class="sxs-lookup"><span data-stu-id="fba75-150">Security Considerations</span></span>  
 <span data-ttu-id="fba75-151">Při zápisu dat do protokolu, zvažte následující:</span><span class="sxs-lookup"><span data-stu-id="fba75-151">Consider the following when writing data to the log:</span></span>  
  
-   <span data-ttu-id="fba75-152">**Vyhněte se úniku informace o uživateli.**</span><span class="sxs-lookup"><span data-stu-id="fba75-152">**Avoid leaking user information.**</span></span> <span data-ttu-id="fba75-153">Ujistěte se, že vaše aplikace zapisuje pouze schválené informace do protokolu.</span><span class="sxs-lookup"><span data-stu-id="fba75-153">Ensure that your application writes only approved information to the log.</span></span> <span data-ttu-id="fba75-154">Například může být přijatelné pro protokolu aplikace tak, aby obsahovala uživatelská jména, ale ne uživatelská hesla.</span><span class="sxs-lookup"><span data-stu-id="fba75-154">For example, it may be acceptable for the application log to contain user names, but not user passwords.</span></span>  
  
-   <span data-ttu-id="fba75-155">**Zabezpečte umístění protokolu.**</span><span class="sxs-lookup"><span data-stu-id="fba75-155">**Make log locations secure.**</span></span> <span data-ttu-id="fba75-156">Všechny protokolu, který obsahuje potenciálně citlivé informace by měly být uložené v zabezpečeném umístění.</span><span class="sxs-lookup"><span data-stu-id="fba75-156">Any log that contains potentially sensitive information should be stored in a secure location.</span></span>  
  
-   <span data-ttu-id="fba75-157">**Vyhněte se zavádějící informace.**</span><span class="sxs-lookup"><span data-stu-id="fba75-157">**Avoid misleading information.**</span></span> <span data-ttu-id="fba75-158">Obecně platí vaše aplikace měla ověřit všechna data zadaná uživatelem před použitím tato data.</span><span class="sxs-lookup"><span data-stu-id="fba75-158">In general, your application should validate all data entered by a user before using that data.</span></span> <span data-ttu-id="fba75-159">Jedná se o zápisu dat do protokolu aplikace.</span><span class="sxs-lookup"><span data-stu-id="fba75-159">This includes writing data to the application log.</span></span>  
  
-   <span data-ttu-id="fba75-160">**Vyhněte se odepření služby.**</span><span class="sxs-lookup"><span data-stu-id="fba75-160">**Avoid denial of service.**</span></span> <span data-ttu-id="fba75-161">Pokud vaše aplikace zapisuje příliš velkého množství informací do protokolu, se může zaplnit protokol nebo se přesvědčte, hledání obtížné důležité informace.</span><span class="sxs-lookup"><span data-stu-id="fba75-161">If your application writes too much information to the log, it could fill the log or make finding important information difficult.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fba75-162">Viz také</span><span class="sxs-lookup"><span data-stu-id="fba75-162">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [<span data-ttu-id="fba75-163">Protokolování informací z aplikace</span><span class="sxs-lookup"><span data-stu-id="fba75-163">Logging Information from the Application</span></span>](../../../../visual-basic/developing-apps/programming/log-info/logging-information-from-the-application.md)
