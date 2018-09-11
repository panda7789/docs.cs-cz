---
title: Práce s protokoly aplikací v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- logs, application
- application event logs, Visual Basic
- application event logs
ms.assetid: 2581afd1-5791-4bc4-86b2-46244e9fe468
ms.openlocfilehash: c11e1f0c99b3189c7a353e6778c701667b0a1d12
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44366102"
---
# <a name="working-with-application-logs-in-visual-basic"></a><span data-ttu-id="3dd34-102">Práce s protokoly aplikací v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3dd34-102">Working with Application Logs in Visual Basic</span></span>
<span data-ttu-id="3dd34-103">`My.Applicaton.Log` a `My.Log` objekty usnadňují zapsat informace trasování a protokolování do protokolů.</span><span class="sxs-lookup"><span data-stu-id="3dd34-103">The `My.Applicaton.Log` and `My.Log` objects make it easy to write logging and tracing information to logs.</span></span>  
  
## <a name="how-messages-are-logged"></a><span data-ttu-id="3dd34-104">Jak jsou zprávy zaznamenány</span><span class="sxs-lookup"><span data-stu-id="3dd34-104">How Messages are Logged</span></span>  
 <span data-ttu-id="3dd34-105">Nejprve je zkontrolován závažnost zprávy <xref:System.Diagnostics.TraceSource.Switch%2A> vlastnost v protokolu <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3dd34-105">First, the severity of the message is checked with the <xref:System.Diagnostics.TraceSource.Switch%2A> property of the log's <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> property.</span></span> <span data-ttu-id="3dd34-106">Ve výchozím pouze zprávy závažnosti "Informace" a vyšší jsou předány pro posluchače trasování, zadaný do protokolu `TraceListener` kolekce.</span><span class="sxs-lookup"><span data-stu-id="3dd34-106">By default, only messages of severity "Information" and higher are passed on to the trace listeners, specified in the log's `TraceListener` collection.</span></span> <span data-ttu-id="3dd34-107">Poté porovnává každý naslouchací proces závažnost zpráv pro posluchače <xref:System.Diagnostics.TraceSource.Switch%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3dd34-107">Then, each listener compares the severity of the message to the listener's <xref:System.Diagnostics.TraceSource.Switch%2A> property.</span></span> <span data-ttu-id="3dd34-108">Pokud závažnost zprávy je dostatečně vysoká, naslouchací proces zapíše zprávu.</span><span class="sxs-lookup"><span data-stu-id="3dd34-108">If the message's severity is high enough, the listener writes out the message.</span></span>  
  
 <span data-ttu-id="3dd34-109">Následující obrázek ukazuje, jak se zprávy zapisují do `WriteEntry` metoda bude předána do `WriteLine` naslouchací procesy trasování metody v protokolu:</span><span class="sxs-lookup"><span data-stu-id="3dd34-109">The following diagram shows how a message written to the `WriteEntry` method gets passed to the `WriteLine` methods of the log's trace listeners:</span></span>  
  
 <span data-ttu-id="3dd34-110">![Moje volání protokolu](../../../../visual-basic/developing-apps/programming/log-info/media/mylogcall.png "MyLogCall")</span><span class="sxs-lookup"><span data-stu-id="3dd34-110">![My Log Call](../../../../visual-basic/developing-apps/programming/log-info/media/mylogcall.png "MyLogCall")</span></span>  
  
 <span data-ttu-id="3dd34-111">Chování protokolu a naslouchacími procesy trasování můžete změnit změnou souboru konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="3dd34-111">You can change the behavior of the log and the trace listeners by changing the application's configuration file.</span></span> <span data-ttu-id="3dd34-112">Následující diagram ukazuje souvztažnost mezi částmi v protokolu a konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="3dd34-112">The following diagram shows the correspondence between the parts of the log and the configuration file.</span></span>  
  
 <span data-ttu-id="3dd34-113">![Moje nastavení protokolu](../../../../visual-basic/developing-apps/programming/log-info/media/mylogconfig.png "MyLogConfig")</span><span class="sxs-lookup"><span data-stu-id="3dd34-113">![My Log Configuration](../../../../visual-basic/developing-apps/programming/log-info/media/mylogconfig.png "MyLogConfig")</span></span>  
  
## <a name="where-messages-are-logged"></a><span data-ttu-id="3dd34-114">Kde jsou zprávy zaznamenány</span><span class="sxs-lookup"><span data-stu-id="3dd34-114">Where Messages are Logged</span></span>  
 <span data-ttu-id="3dd34-115">Pokud sestavení nemá žádný konfigurační soubor `My.Application.Log` a `My.Log` objektů zapisovat do výstupu ladění aplikace (prostřednictvím <xref:System.Diagnostics.DefaultTraceListener> třídy).</span><span class="sxs-lookup"><span data-stu-id="3dd34-115">If the assembly has no configuration file, the `My.Application.Log` and `My.Log` objects write to the application's debug output (through the <xref:System.Diagnostics.DefaultTraceListener> class).</span></span> <span data-ttu-id="3dd34-116">Kromě toho `My.Application.Log` zapíše objekt do souboru protokolu sestavení. (prostřednictvím <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> třídy), zatímco `My.Log` zapíše objekt do výstupu webová stránka ASP.NET (prostřednictvím <xref:System.Web.WebPageTraceListener> třídy).</span><span class="sxs-lookup"><span data-stu-id="3dd34-116">In addition, the `My.Application.Log` object writes to the assembly's log file (through the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class), while the `My.Log` object writes to the ASP.NET Web page's output (through the <xref:System.Web.WebPageTraceListener> class).</span></span>  
  
 <span data-ttu-id="3dd34-117">Výstup ladění můžete zobrazit v sadě Visual Studio **výstup** okno při spuštění aplikace v režimu ladění.</span><span class="sxs-lookup"><span data-stu-id="3dd34-117">The debug output can be viewed in the Visual Studio **Output** window when running your application in debug mode.</span></span> <span data-ttu-id="3dd34-118">Otevřete **výstup** okna, klikněte na tlačítko **ladění** položku nabídky, přejděte na **Windows**a potom klikněte na tlačítko **výstup**.</span><span class="sxs-lookup"><span data-stu-id="3dd34-118">To open the **Output** window, click the **Debug** menu item, point to **Windows**, and then click **Output**.</span></span> <span data-ttu-id="3dd34-119">V **výstup** okně **ladění** z **zobrazit výstup z:** pole.</span><span class="sxs-lookup"><span data-stu-id="3dd34-119">In the **Output** window, select **Debug** from the **Show output from** box.</span></span>  
  
 <span data-ttu-id="3dd34-120">Ve výchozím nastavení `My.Application.Log` zapíše soubor protokolu v umístění pro data aplikací uživatele.</span><span class="sxs-lookup"><span data-stu-id="3dd34-120">By default, `My.Application.Log` writes the log file in the path for the user's application data.</span></span> <span data-ttu-id="3dd34-121">Můžete získat cestu z <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> vlastnost <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> objektu.</span><span class="sxs-lookup"><span data-stu-id="3dd34-121">You can get the path from the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> property of the <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> object.</span></span> <span data-ttu-id="3dd34-122">Formát cesty je následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="3dd34-122">The format of that path is as follows:</span></span>  
  
 `BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`  
  
 <span data-ttu-id="3dd34-123">Typická hodnota `BasePath` vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="3dd34-123">A typical value for `BasePath` is as follows.</span></span>  
  
 <span data-ttu-id="3dd34-124">C:\Documents and nastavení\\`username`\Application dat</span><span class="sxs-lookup"><span data-stu-id="3dd34-124">C:\Documents and Settings\\`username`\Application Data</span></span>  
  
 <span data-ttu-id="3dd34-125">Hodnoty `CompanyName`, `ProductName`, a `ProductVersion` pocházejí z informací o sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="3dd34-125">The values of `CompanyName`, `ProductName`, and `ProductVersion` come from the application's assembly information.</span></span> <span data-ttu-id="3dd34-126">Název souboru protokolu má *AssemblyName*.log, kde *AssemblyName* je název souboru sestavení bez přípony.</span><span class="sxs-lookup"><span data-stu-id="3dd34-126">The form of the log file name is *AssemblyName*.log, where *AssemblyName* is the file name of the assembly without the extension.</span></span> <span data-ttu-id="3dd34-127">V případě potřeby je více než jeden soubor protokolu, třeba když původní protokolu není k dispozici aplikace pokusy o zápis do protokolu, je formulář pro název souboru protokolu *AssemblyName*-*iterace* .log, kde `iteration` pozitivní `Integer`.</span><span class="sxs-lookup"><span data-stu-id="3dd34-127">If more than one log file is needed, such as when the original log is unavailable when the application attempts to write to the log, the form for the log file name is *AssemblyName*-*iteration*.log, where `iteration` is a positive `Integer`.</span></span>  
  
 <span data-ttu-id="3dd34-128">Výchozí chování můžete přepsat přidáním nebo změnou konfiguračních souborů aplikace a počítače.</span><span class="sxs-lookup"><span data-stu-id="3dd34-128">You can override the default behavior by adding or changing the computer's and the application's configuration files.</span></span> <span data-ttu-id="3dd34-129">Další informace najdete v tématu [návod: Změna kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="3dd34-129">For more information, see [Walkthrough: Changing Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).</span></span>  
  
## <a name="configuring-log-settings"></a><span data-ttu-id="3dd34-130">Konfigurace nastavení protokolu</span><span class="sxs-lookup"><span data-stu-id="3dd34-130">Configuring Log Settings</span></span>  
 <span data-ttu-id="3dd34-131">`Log` Objekt má výchozí implementaci, která funguje bez konfiguračního souboru aplikace, app.config. Chcete-li změnit výchozí hodnoty, je nutné přidat konfigurační soubor s novým nastavením.</span><span class="sxs-lookup"><span data-stu-id="3dd34-131">The `Log` object has a default implementation that works without an application configuration file, app.config. To change the defaults, you must add a configuration file with the new settings.</span></span> <span data-ttu-id="3dd34-132">Další informace najdete v tématu [návod: filtrování výstupu My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="3dd34-132">For more information, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>  
  
 <span data-ttu-id="3dd34-133">Konfigurační oddíly funkce protokolu jsou umístěné v `<system.diagnostics>` uzlu v hlavním `<configuration>` uzlu ze souboru app.config.</span><span class="sxs-lookup"><span data-stu-id="3dd34-133">The log configuration sections are located in the `<system.diagnostics>` node in the main `<configuration>` node of the app.config file.</span></span> <span data-ttu-id="3dd34-134">Informace o protokolu je definován v několika uzly:</span><span class="sxs-lookup"><span data-stu-id="3dd34-134">Log information is defined in several nodes:</span></span>  
  
-   <span data-ttu-id="3dd34-135">Naslouchací procesy pro `Log` objektu jsou definovány v `<sources>` uzel s názvem DefaultSource.</span><span class="sxs-lookup"><span data-stu-id="3dd34-135">The listeners for the `Log` object are defined in the `<sources>` node named DefaultSource.</span></span>  
  
-   <span data-ttu-id="3dd34-136">Závažnost filtr `Log` objekt je definovaný v `<switches>` uzel s názvem DefaultSwitch.</span><span class="sxs-lookup"><span data-stu-id="3dd34-136">The severity filter for the `Log` object is defined in the `<switches>` node named DefaultSwitch.</span></span>  
  
-   <span data-ttu-id="3dd34-137">Součásti naslouchající protokolům, které jsou definovány v `<sharedListeners>` uzlu.</span><span class="sxs-lookup"><span data-stu-id="3dd34-137">The log listeners are defined in the `<sharedListeners>` node.</span></span>  
  
 <span data-ttu-id="3dd34-138">Příklady `<sources>`, `<switches>`, a `<sharedListeners>` uzly jsou uvedeny v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="3dd34-138">Examples of `<sources>`, `<switches>`, and `<sharedListeners>` nodes are shown in the following code:</span></span>  
  
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
  
## <a name="changing-log-settings-after-deployment"></a><span data-ttu-id="3dd34-139">Změna nastavení protokolu po nasazení</span><span class="sxs-lookup"><span data-stu-id="3dd34-139">Changing Log Settings after Deployment</span></span>  
 <span data-ttu-id="3dd34-140">Když vyvíjíte aplikaci, jeho nastavení konfigurace jsou uloženy v souboru app.config, jak je znázorněno výše uvedených příkladech.</span><span class="sxs-lookup"><span data-stu-id="3dd34-140">When you develop an application, its configuration settings are stored in the app.config file, as shown in the examples above.</span></span> <span data-ttu-id="3dd34-141">Po nasazení aplikace, můžete stále nakonfigurovat protokol úpravou konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="3dd34-141">After you deploy your application, you can still configure the log by editing the configuration file.</span></span> <span data-ttu-id="3dd34-142">V aplikaci založené na Windows, tento název souboru je *applicationName*. exe.config který se musí nacházet ve stejné složce jako spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="3dd34-142">In a Windows-based application, this file's name is *applicationName*.exe.config, and it must reside in the same folder as the executable file.</span></span> <span data-ttu-id="3dd34-143">Pro webovou aplikaci Toto je soubor Web.config, který je přidružený k projektu.</span><span class="sxs-lookup"><span data-stu-id="3dd34-143">For a Web application, this is the Web.config file associated with the project.</span></span>  
  
 <span data-ttu-id="3dd34-144">Pokud vaše aplikace spustí kód, který vytvoří instanci třídy poprvé, ověří konfigurační soubor pro informace o objektu.</span><span class="sxs-lookup"><span data-stu-id="3dd34-144">When your application executes the code that creates an instance of a class for the first time, it checks the configuration file for information about the object.</span></span> <span data-ttu-id="3dd34-145">Pro `Log` objektu, to se stane první `Log` přístupu k objektu.</span><span class="sxs-lookup"><span data-stu-id="3dd34-145">For the `Log` object, this happens the first time the `Log` object is accessed.</span></span> <span data-ttu-id="3dd34-146">Systém zkontroluje konfigurační soubor jen jednou pro každý konkrétní objekt – poprvé vaše aplikace vytvoří objekt.</span><span class="sxs-lookup"><span data-stu-id="3dd34-146">The system examines the configuration file only once for any particular object—the first time your application creates the object.</span></span> <span data-ttu-id="3dd34-147">Proto budete muset restartovat aplikaci, aby se změny projevily.</span><span class="sxs-lookup"><span data-stu-id="3dd34-147">Therefore, you may need to restart the application for the changes to take effect.</span></span>  
  
 <span data-ttu-id="3dd34-148">V nasazené aplikaci povolit trasování kódu překonfigurováním přepínače objektů před spuštěním vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="3dd34-148">In a deployed application, you enable trace code by reconfiguring switch objects before your application starts.</span></span> <span data-ttu-id="3dd34-149">Obvykle to zahrnuje zapnutí přepínače objektů a vypnout nebo změnou úrovně trasování a následného restartování aplikace.</span><span class="sxs-lookup"><span data-stu-id="3dd34-149">Typically, this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>  
  
## <a name="security-considerations"></a><span data-ttu-id="3dd34-150">Důležité informace o zabezpečení</span><span class="sxs-lookup"><span data-stu-id="3dd34-150">Security Considerations</span></span>  
 <span data-ttu-id="3dd34-151">Při zápisu dat do protokolu, zvažte následující:</span><span class="sxs-lookup"><span data-stu-id="3dd34-151">Consider the following when writing data to the log:</span></span>  
  
-   <span data-ttu-id="3dd34-152">**Vyhněte se úniku informací o uživateli.**</span><span class="sxs-lookup"><span data-stu-id="3dd34-152">**Avoid leaking user information.**</span></span> <span data-ttu-id="3dd34-153">Ujistěte se, že vaše aplikace zapisuje pouze schválená informace do protokolu.</span><span class="sxs-lookup"><span data-stu-id="3dd34-153">Ensure that your application writes only approved information to the log.</span></span> <span data-ttu-id="3dd34-154">Například může být přijatelný aplikačního protokolu obsahující uživatelská jména, ale ne hesla uživatele.</span><span class="sxs-lookup"><span data-stu-id="3dd34-154">For example, it may be acceptable for the application log to contain user names, but not user passwords.</span></span>  
  
-   <span data-ttu-id="3dd34-155">**Zabezpečte umístění protokolu.**</span><span class="sxs-lookup"><span data-stu-id="3dd34-155">**Make log locations secure.**</span></span> <span data-ttu-id="3dd34-156">Libovolný protokol, který obsahuje potenciálně citlivé informace ukládat na bezpečném místě.</span><span class="sxs-lookup"><span data-stu-id="3dd34-156">Any log that contains potentially sensitive information should be stored in a secure location.</span></span>  
  
-   <span data-ttu-id="3dd34-157">**Vyhněte se zavádějící informace.**</span><span class="sxs-lookup"><span data-stu-id="3dd34-157">**Avoid misleading information.**</span></span> <span data-ttu-id="3dd34-158">Vaše aplikace měla ověřit obecně platí, všechna data zadaná uživatelem, než začnete používat tato data.</span><span class="sxs-lookup"><span data-stu-id="3dd34-158">In general, your application should validate all data entered by a user before using that data.</span></span> <span data-ttu-id="3dd34-159">Jedná se o zápisu dat do protokolu aplikace.</span><span class="sxs-lookup"><span data-stu-id="3dd34-159">This includes writing data to the application log.</span></span>  
  
-   <span data-ttu-id="3dd34-160">**Vyhněte se útok DoS.**</span><span class="sxs-lookup"><span data-stu-id="3dd34-160">**Avoid denial of service.**</span></span> <span data-ttu-id="3dd34-161">Pokud vaše aplikace zapisuje příliš mnoho informace do protokolu, může zaplnit protokol nebo nalezení obtížné důležité informace.</span><span class="sxs-lookup"><span data-stu-id="3dd34-161">If your application writes too much information to the log, it could fill the log or make finding important information difficult.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dd34-162">Viz také</span><span class="sxs-lookup"><span data-stu-id="3dd34-162">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [<span data-ttu-id="3dd34-163">Protokolování informací z aplikace</span><span class="sxs-lookup"><span data-stu-id="3dd34-163">Logging Information from the Application</span></span>](../../../../visual-basic/developing-apps/programming/log-info/index.md)
