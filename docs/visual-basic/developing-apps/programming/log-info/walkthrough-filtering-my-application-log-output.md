---
title: Filtrování výstupu my. Application. log (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
ms.openlocfilehash: af1dc3e1ce22112d76ad566873f40c1c2ac05c9d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968689"
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a><span data-ttu-id="1b105-102">Návod: Filtrování výstupu my. Application. log (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b105-102">Walkthrough: Filtering My.Application.Log Output (Visual Basic)</span></span>
<span data-ttu-id="1b105-103">Tento návod ukazuje, jak změnit výchozí filtrování protokolu pro `My.Application.Log` objekt, aby bylo možné určit, jaké informace jsou předány `Log` z objektu posluchačům a jaké informace jsou zapsány posluchači.</span><span class="sxs-lookup"><span data-stu-id="1b105-103">This walkthrough demonstrates how to change the default log filtering for the `My.Application.Log` object, to control what information is passed from the `Log` object to the listeners and what information is written by the listeners.</span></span> <span data-ttu-id="1b105-104">Chování protokolování můžete změnit i po sestavení aplikace, protože informace o konfiguraci jsou uložené v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="1b105-104">You can change the logging behavior even after building the application, because the configuration information is stored in the application's configuration file.</span></span>  
  
## <a name="getting-started"></a><span data-ttu-id="1b105-105">Začínáme</span><span class="sxs-lookup"><span data-stu-id="1b105-105">Getting Started</span></span>  
 <span data-ttu-id="1b105-106">Každá zpráva, `My.Application.Log` kterou zápis má přidruženou úroveň závažnosti, která mechanismy filtrování používá k řízení výstupu protokolu.</span><span class="sxs-lookup"><span data-stu-id="1b105-106">Each message that `My.Application.Log` writes has an associated severity level, which filtering mechanisms use to control the log output.</span></span> <span data-ttu-id="1b105-107">Tato ukázková aplikace `My.Application.Log` používá metody pro zápis několika zpráv protokolu s různou úrovní závažnosti.</span><span class="sxs-lookup"><span data-stu-id="1b105-107">This sample application uses `My.Application.Log` methods to write several log messages with different severity levels.</span></span>  
  
#### <a name="to-build-the-sample-application"></a><span data-ttu-id="1b105-108">Sestavení ukázkové aplikace</span><span class="sxs-lookup"><span data-stu-id="1b105-108">To build the sample application</span></span>  
  
1. <span data-ttu-id="1b105-109">Otevřete nový Visual Basic projekt aplikace systému Windows.</span><span class="sxs-lookup"><span data-stu-id="1b105-109">Open a new Visual Basic Windows Application project.</span></span>  
  
2. <span data-ttu-id="1b105-110">Přidejte tlačítko s názvem Button1 do formuláře Form1.</span><span class="sxs-lookup"><span data-stu-id="1b105-110">Add a button named Button1 to Form1.</span></span>  
  
3. <span data-ttu-id="1b105-111">V obslužné rutině události pro Button1 přidejte následující kód: <xref:System.Windows.Forms.Control.Click></span><span class="sxs-lookup"><span data-stu-id="1b105-111">In the <xref:System.Windows.Forms.Control.Click> event handler for Button1, add the following code:</span></span>  
  
     [!code-vb[VbVbcnMyApplicationLogFiltering#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyApplicationLogFiltering/VB/Form1.vb#1)]  
  
4. <span data-ttu-id="1b105-112">Spusťte aplikaci v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="1b105-112">Run the application in the debugger.</span></span>  
  
5. <span data-ttu-id="1b105-113">Stiskněte **Button1**.</span><span class="sxs-lookup"><span data-stu-id="1b105-113">Press **Button1**.</span></span>  
  
     <span data-ttu-id="1b105-114">Aplikace zapíše do výstupu ladění a souboru protokolu aplikace následující informace.</span><span class="sxs-lookup"><span data-stu-id="1b105-114">The application writes the following information to the application's debug output and log file.</span></span>  
  
     `DefaultSource Information: 0 : In Button1_Click`  
  
     `DefaultSource Error: 2 : Error in the application.`  
  
6. <span data-ttu-id="1b105-115">Zavřete aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1b105-115">Close the application.</span></span>  
  
     <span data-ttu-id="1b105-116">Informace o tom, jak zobrazit okno výstup ladění aplikace, naleznete v tématu [okno výstup](/visualstudio/ide/reference/output-window).</span><span class="sxs-lookup"><span data-stu-id="1b105-116">For information on how to view the application's debug output window, see [Output Window](/visualstudio/ide/reference/output-window).</span></span> <span data-ttu-id="1b105-117">Informace o umístění souboru protokolu aplikace najdete v tématu [Návod: Určení místa, kde aplikace My. Application.](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)Log zapisuje informace.</span><span class="sxs-lookup"><span data-stu-id="1b105-117">For information on the location of the application's log file, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="1b105-118">Ve výchozím nastavení aplikace při zavření aplikace vyprázdní výstup souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="1b105-118">By default, the application flushes the log-file output when the application closes.</span></span>  
  
     <span data-ttu-id="1b105-119">V předchozím příkladu druhá volání <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> metody a volání <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> metody vytvoří výstup protokolu, zatímco první `WriteEntry` a poslední volání metody nezpůsobí.</span><span class="sxs-lookup"><span data-stu-id="1b105-119">In the example above, the second call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> method and the call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> method produces log output, while the first and last calls to the `WriteEntry` method do not.</span></span> <span data-ttu-id="1b105-120">Důvodem je to, že úrovně `WriteEntry` závažnosti a `WriteException` jsou "informace" a "Chyba", `My.Application.Log` které jsou povoleny ve výchozím filtrování protokolu objektu.</span><span class="sxs-lookup"><span data-stu-id="1b105-120">This is because the severity levels of `WriteEntry` and `WriteException` are "Information" and "Error", both of which are allowed by the `My.Application.Log` object's default log filtering.</span></span> <span data-ttu-id="1b105-121">Nicméně události s úrovněmi závažnosti "Start" a "Stop" znemožňují výstup protokolu z výroby.</span><span class="sxs-lookup"><span data-stu-id="1b105-121">However, events with "Start" and "Stop" severity levels are prevented from producing log output.</span></span>  
  
## <a name="filtering-for-all-myapplicationlog-listeners"></a><span data-ttu-id="1b105-122">Filtrování pro všechny naslouchací procesy my. Application. log</span><span class="sxs-lookup"><span data-stu-id="1b105-122">Filtering for All My.Application.Log Listeners</span></span>  
 <span data-ttu-id="1b105-123">`My.Application.Log` Objekt `WriteException` používá pojmenovaný k`DefaultSwitch`řízení , které zprávy přecházejí z metod adoprotokolůnaslouchacíhoprocesu.`WriteEntry` <xref:System.Diagnostics.SourceSwitch></span><span class="sxs-lookup"><span data-stu-id="1b105-123">The `My.Application.Log` object uses a <xref:System.Diagnostics.SourceSwitch> named `DefaultSwitch` to control which messages it passes from the `WriteEntry` and `WriteException` methods to the log listeners.</span></span> <span data-ttu-id="1b105-124">V konfiguračním souboru `DefaultSwitch` aplikace můžete konfigurovat nastavením jeho hodnoty na jednu <xref:System.Diagnostics.SourceLevels> z hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="1b105-124">You can configure `DefaultSwitch` in the application's configuration file by setting its value to one of the <xref:System.Diagnostics.SourceLevels> enumeration values.</span></span> <span data-ttu-id="1b105-125">Ve výchozím nastavení je jeho hodnota "informace".</span><span class="sxs-lookup"><span data-stu-id="1b105-125">By default, its value is "Information".</span></span>  
  
 <span data-ttu-id="1b105-126">Tato tabulka zobrazuje úroveň závažnosti, která je vyžadována pro protokol k zápisu zprávy do posluchačů, s ohledem `DefaultSwitch` na konkrétní nastavení.</span><span class="sxs-lookup"><span data-stu-id="1b105-126">This table shows the severity level required for Log to write a message to the listeners, given a particular `DefaultSwitch` setting.</span></span>  
  
|<span data-ttu-id="1b105-127">Hodnota DefaultSwitch</span><span class="sxs-lookup"><span data-stu-id="1b105-127">DefaultSwitch Value</span></span>|<span data-ttu-id="1b105-128">Závažnost zprávy požadovaná pro výstup</span><span class="sxs-lookup"><span data-stu-id="1b105-128">Message severity required for output</span></span>|  
|---|---| 
|`Critical`|`Critical`|  
|`Error`|<span data-ttu-id="1b105-129">`Critical` Nebo `Error`</span><span class="sxs-lookup"><span data-stu-id="1b105-129">`Critical` or `Error`</span></span>|  
|`Warning`|<span data-ttu-id="1b105-130">`Critical`, `Error`nebo`Warning`</span><span class="sxs-lookup"><span data-stu-id="1b105-130">`Critical`, `Error`, or `Warning`</span></span>|  
|`Information`|<span data-ttu-id="1b105-131">`Critical`, `Error`, `Warning`nebo`Information`</span><span class="sxs-lookup"><span data-stu-id="1b105-131">`Critical`, `Error`, `Warning`, or `Information`</span></span>|  
|`Verbose`|<span data-ttu-id="1b105-132">`Critical`, `Error` ,`Warning`,nebo `Information``Verbose`</span><span class="sxs-lookup"><span data-stu-id="1b105-132">`Critical`, `Error`, `Warning`, `Information`, or `Verbose`</span></span>|  
|`ActivityTracing`|<span data-ttu-id="1b105-133">`Start`, `Stop` ,`Suspend`,nebo `Resume``Transfer`</span><span class="sxs-lookup"><span data-stu-id="1b105-133">`Start`, `Stop`, `Suspend`, `Resume`, or `Transfer`</span></span>|  
|`All`|<span data-ttu-id="1b105-134">Všechny zprávy jsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="1b105-134">All messages are allowed.</span></span>|  
|`Off`|<span data-ttu-id="1b105-135">Všechny zprávy jsou zablokované.</span><span class="sxs-lookup"><span data-stu-id="1b105-135">All messages are blocked.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="1b105-136">Jednotlivé metody `WriteException` a mají přetížení, které neurčuje úroveň závažnosti. `WriteEntry`</span><span class="sxs-lookup"><span data-stu-id="1b105-136">The `WriteEntry` and `WriteException` methods each have an overload that does not specify a severity level.</span></span> <span data-ttu-id="1b105-137">Implicitní úroveň závažnosti pro `WriteEntry` přetížení je "informace" a implicitní úroveň závažnosti `WriteException` pro přetížení je "Chyba".</span><span class="sxs-lookup"><span data-stu-id="1b105-137">The implicit severity level for the `WriteEntry` overload is "Information", and the implicit severity level for the `WriteException` overload is "Error".</span></span>  
  
 <span data-ttu-id="1b105-138">Tato tabulka vysvětluje výstup protokolu zobrazený v předchozím příkladu: s výchozím `DefaultSwitch` nastavením "Information", pouze druhým voláním `WriteEntry` metody `WriteException` a voláním metody, která vytváří výstup protokolu.</span><span class="sxs-lookup"><span data-stu-id="1b105-138">This table explains the log output shown in the previous example: with the default `DefaultSwitch` setting of "Information", only the second call to the `WriteEntry` method and the call to the `WriteException` method produce log output.</span></span>  
  
#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="1b105-139">Chcete-li protokolovat pouze události trasování aktivit</span><span class="sxs-lookup"><span data-stu-id="1b105-139">To log only activity tracing events</span></span>  
  
1. <span data-ttu-id="1b105-140">V **Průzkumník řešení** klikněte pravým tlačítkem na soubor App. config a vyberte **otevřít**.</span><span class="sxs-lookup"><span data-stu-id="1b105-140">Right-click app.config in the **Solution Explorer** and select **Open**.</span></span>  
  
     <span data-ttu-id="1b105-141">-nebo-</span><span class="sxs-lookup"><span data-stu-id="1b105-141">-or-</span></span>  
  
     <span data-ttu-id="1b105-142">Pokud neexistuje žádný soubor App. config:</span><span class="sxs-lookup"><span data-stu-id="1b105-142">If there is no app.config file:</span></span>  
  
    1. <span data-ttu-id="1b105-143">V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="1b105-143">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2. <span data-ttu-id="1b105-144">V dialogovém okně **Přidat novou položku** vyberte možnost **konfigurační soubor aplikace**.</span><span class="sxs-lookup"><span data-stu-id="1b105-144">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3. <span data-ttu-id="1b105-145">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="1b105-145">Click **Add**.</span></span>  
  
2. <span data-ttu-id="1b105-146">Vyhledejte část, která je `<system.diagnostics>` v části, která je v části nejvyšší úrovně `<configuration>`. `<switches>`</span><span class="sxs-lookup"><span data-stu-id="1b105-146">Locate the `<switches>` section, which is in the `<system.diagnostics>` section, which is in the top-level `<configuration>` section.</span></span>  
  
3. <span data-ttu-id="1b105-147">Vyhledejte prvek, který je `DefaultSwitch` přidán do kolekce přepínačů.</span><span class="sxs-lookup"><span data-stu-id="1b105-147">Find the element that adds `DefaultSwitch` to the collection of switches.</span></span> <span data-ttu-id="1b105-148">Měl by vypadat podobně jako tento element:</span><span class="sxs-lookup"><span data-stu-id="1b105-148">It should look similar to this element:</span></span>  
  
     `<add name="DefaultSwitch" value="Information" />`  
  
4. <span data-ttu-id="1b105-149">Změňte hodnotu `value` atributu na "ActivityTracing".</span><span class="sxs-lookup"><span data-stu-id="1b105-149">Change the value of the `value` attribute to "ActivityTracing".</span></span>  
  
5. <span data-ttu-id="1b105-150">Obsah souboru App. config by měl vypadat podobně jako následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="1b105-150">The content of the app.config file should be similar to the following XML:</span></span>  
  
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
  
6. <span data-ttu-id="1b105-151">Spusťte aplikaci v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="1b105-151">Run the application in the debugger.</span></span>  
  
7. <span data-ttu-id="1b105-152">Stiskněte **Button1**.</span><span class="sxs-lookup"><span data-stu-id="1b105-152">Press **Button1**.</span></span>  
  
     <span data-ttu-id="1b105-153">Aplikace zapíše do výstupu ladění a souboru protokolu aplikace následující informace:</span><span class="sxs-lookup"><span data-stu-id="1b105-153">The application writes the following information to the application's debug output and log file:</span></span>  
  
     `DefaultSource Start: 4 : Entering Button1_Click`  
  
     `DefaultSource Stop: 5 : Leaving Button1_Click`  
  
8. <span data-ttu-id="1b105-154">Zavřete aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1b105-154">Close the application.</span></span>  
  
9. <span data-ttu-id="1b105-155">Změňte hodnotu `value` atributu zpět na "informace".</span><span class="sxs-lookup"><span data-stu-id="1b105-155">Change the value of the `value` attribute back to "Information".</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="1b105-156">Nastavení přepínače pouze `My.Application.Log`ovládacíprvky. `DefaultSwitch`</span><span class="sxs-lookup"><span data-stu-id="1b105-156">The `DefaultSwitch` switch setting controls only `My.Application.Log`.</span></span> <span data-ttu-id="1b105-157">Nemění způsob, jakým se <xref:System.Diagnostics.Trace?displayProperty=nameWithType> chovají <xref:System.Diagnostics.Debug?displayProperty=nameWithType> .NET Framework a třídy.</span><span class="sxs-lookup"><span data-stu-id="1b105-157">It does not change how the .NET Framework <xref:System.Diagnostics.Trace?displayProperty=nameWithType> and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes behave.</span></span>  
  
## <a name="individual-filtering-for-myapplicationlog-listeners"></a><span data-ttu-id="1b105-158">Individuální filtrování pro naslouchací procesy my. Application. log</span><span class="sxs-lookup"><span data-stu-id="1b105-158">Individual Filtering For My.Application.Log Listeners</span></span>  
 <span data-ttu-id="1b105-159">Předchozí příklad ukazuje, jak změnit filtrování pro všechny `My.Application.Log` výstupy.</span><span class="sxs-lookup"><span data-stu-id="1b105-159">The previous example shows how to change the filtering for all `My.Application.Log` output.</span></span> <span data-ttu-id="1b105-160">Tento příklad ukazuje, jak filtrovat jednotlivé naslouchací procesy protokolů.</span><span class="sxs-lookup"><span data-stu-id="1b105-160">This example demonstrates how to filter an individual log listener.</span></span> <span data-ttu-id="1b105-161">Ve výchozím nastavení má aplikace dva naslouchací procesy, které zapisují do výstupu ladění aplikace a do souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="1b105-161">By default, an application has two listeners that write to the application's debug output and the log file.</span></span>  
  
 <span data-ttu-id="1b105-162">Konfigurační soubor řídí chování naslouchacího procesu protokolu tím, že každé z nich může mít filtr, který je podobný přepínači pro `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="1b105-162">The configuration file controls the behavior of the log listeners by allowing each one to have a filter, which is similar to a switch for `My.Application.Log`.</span></span> <span data-ttu-id="1b105-163">Naslouchací proces protokolu vypíše zprávu pouze v případě, že je závažnost zprávy povolena filtrem protokolu `DefaultSwitch` i naslouchacího procesu protokolu.</span><span class="sxs-lookup"><span data-stu-id="1b105-163">A log listener will output a message only if the message's severity is allowed by both the log's `DefaultSwitch` and the log listener's filter.</span></span>  
  
 <span data-ttu-id="1b105-164">Tento příklad ukazuje, jak nakonfigurovat filtrování pro nový naslouchací proces ladění a přidat ho do `Log` objektu.</span><span class="sxs-lookup"><span data-stu-id="1b105-164">This example demonstrates how to configure filtering for a new debug listener and add it to the `Log` object.</span></span> <span data-ttu-id="1b105-165">Výchozí naslouchací proces ladění by měl být odebrán z `Log` objektu, takže je zřejmé, že zprávy ladění pocházejí z nového naslouchacího procesu ladění.</span><span class="sxs-lookup"><span data-stu-id="1b105-165">The default debug listener should be removed from the `Log` object, so it is clear that the debug messages come from the new debug listener.</span></span>  
  
#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="1b105-166">Do protokolu pouze události trasování aktivity</span><span class="sxs-lookup"><span data-stu-id="1b105-166">To log only activity-tracing events</span></span>  
  
1. <span data-ttu-id="1b105-167">V **Průzkumník řešení** klikněte pravým tlačítkem na soubor App. config a vyberte **otevřít**.</span><span class="sxs-lookup"><span data-stu-id="1b105-167">Right-click app.config in the **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="1b105-168">-nebo-</span><span class="sxs-lookup"><span data-stu-id="1b105-168">-or-</span></span>  
  
     <span data-ttu-id="1b105-169">Pokud neexistuje žádný soubor App. config:</span><span class="sxs-lookup"><span data-stu-id="1b105-169">If there is no app.config file:</span></span>  
  
    1. <span data-ttu-id="1b105-170">V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="1b105-170">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2. <span data-ttu-id="1b105-171">V dialogovém okně **Přidat novou položku** vyberte možnost **konfigurační soubor aplikace**.</span><span class="sxs-lookup"><span data-stu-id="1b105-171">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3. <span data-ttu-id="1b105-172">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="1b105-172">Click **Add**.</span></span>  
  
2. <span data-ttu-id="1b105-173">Klikněte pravým tlačítkem na soubor App. config v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="1b105-173">Right-click app.config in **Solution Explorer**.</span></span> <span data-ttu-id="1b105-174">Klikněte na tlačítko **otevřít**.</span><span class="sxs-lookup"><span data-stu-id="1b105-174">Choose **Open**.</span></span>  
  
3. <span data-ttu-id="1b105-175">Vyhledejte část v části s `name` atributem `<sources>` "DefaultSource", který je v části. `<source>` `<listeners>`</span><span class="sxs-lookup"><span data-stu-id="1b105-175">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", which is under the `<sources>` section.</span></span> <span data-ttu-id="1b105-176">Oddíl je pod oddílem v části nejvyšší úrovně `<configuration>`. `<system.diagnostics>` `<sources>`</span><span class="sxs-lookup"><span data-stu-id="1b105-176">The `<sources>` section is under the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
4. <span data-ttu-id="1b105-177">Přidejte tento element do `<listeners>` oddílu:</span><span class="sxs-lookup"><span data-stu-id="1b105-177">Add this element to the `<listeners>` section:</span></span>  
  
    ```xml  
    <!-- Remove the default debug listener. -->  
    <remove name="Default"/>  
    <!-- Add a filterable debug listener. -->  
    <add name="NewDefault"/>  
    ```  
  
5. <span data-ttu-id="1b105-178">`<sharedListeners>` Vyhledejte část `<system.diagnostics>` v části v sekci nejvyšší úrovně `<configuration>` .</span><span class="sxs-lookup"><span data-stu-id="1b105-178">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
6. <span data-ttu-id="1b105-179">Přidejte tento element do této `<sharedListeners>` části:</span><span class="sxs-lookup"><span data-stu-id="1b105-179">Add this element to that `<sharedListeners>` section:</span></span>  
  
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
  
     <span data-ttu-id="1b105-180">Filtr převezme jednu <xref:System.Diagnostics.SourceLevels> z hodnot výčtu jako svůj `initializeData` atribut. <xref:System.Diagnostics.EventTypeFilter></span><span class="sxs-lookup"><span data-stu-id="1b105-180">The <xref:System.Diagnostics.EventTypeFilter> filter takes one of the <xref:System.Diagnostics.SourceLevels> enumeration values as its `initializeData` attribute.</span></span>  
  
7. <span data-ttu-id="1b105-181">Obsah souboru App. config by měl vypadat podobně jako následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="1b105-181">The content of the app.config file should be similar to the following XML:</span></span>  
  
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
  
8. <span data-ttu-id="1b105-182">Spusťte aplikaci v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="1b105-182">Run the application in the debugger.</span></span>  
  
9. <span data-ttu-id="1b105-183">Stiskněte **Button1**.</span><span class="sxs-lookup"><span data-stu-id="1b105-183">Press **Button1**.</span></span>  
  
     <span data-ttu-id="1b105-184">Aplikace zapíše do souboru protokolu aplikace následující informace:</span><span class="sxs-lookup"><span data-stu-id="1b105-184">The application writes the following information to the application's log file:</span></span>  
  
     `Default Information: 0 : In Button1_Click`  
  
     `Default Error: 2 : Error in the application.`  
  
     <span data-ttu-id="1b105-185">Aplikace zapisuje méně informací do výstupu ladění aplikace z důvodu přísnějšího filtrování.</span><span class="sxs-lookup"><span data-stu-id="1b105-185">The application writes less information to the application's debug output because of the more restrictive filtering.</span></span>  
  
     `Default Error   2   Error`  
  
10. <span data-ttu-id="1b105-186">Zavřete aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1b105-186">Close the application.</span></span>  
  
 <span data-ttu-id="1b105-187">Další informace o změně nastavení protokolu po nasazení najdete v tématu [práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="1b105-187">For more information about changing log settings after deployment, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b105-188">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1b105-188">See also</span></span>

- [<span data-ttu-id="1b105-189">Návod: Určení místa, kde aplikace My. Application. Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="1b105-189">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="1b105-190">Návod: Změna místa, kam aplikace My. Application. Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="1b105-190">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="1b105-191">Návod: Vytváření vlastních posluchačů protokolů</span><span class="sxs-lookup"><span data-stu-id="1b105-191">Walkthrough: Creating Custom Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)
- [<span data-ttu-id="1b105-192">Postupy: Zápis zpráv protokolu</span><span class="sxs-lookup"><span data-stu-id="1b105-192">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="1b105-193">Přepínače trasování</span><span class="sxs-lookup"><span data-stu-id="1b105-193">Trace Switches</span></span>](../../../../framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="1b105-194">Protokolování informací z aplikace</span><span class="sxs-lookup"><span data-stu-id="1b105-194">Logging Information from the Application</span></span>](../../../../visual-basic/developing-apps/programming/log-info/index.md)
