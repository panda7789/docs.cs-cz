---
title: Filtrování výstupu My.Application.Log
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
ms.openlocfilehash: f18556bbe1ca2d77925482319246d403892d31ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74353590"
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a><span data-ttu-id="c74c2-102">Návod: Filtrování výstupu My.Application.Log (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c74c2-102">Walkthrough: Filtering My.Application.Log Output (Visual Basic)</span></span>

<span data-ttu-id="c74c2-103">Tento návod ukazuje, jak změnit výchozí filtrování `My.Application.Log` protokolu pro objekt, chcete-li `Log` řídit, jaké informace jsou předávány z objektu naslouchacím procesům a jaké informace jsou napsány posluchači.</span><span class="sxs-lookup"><span data-stu-id="c74c2-103">This walkthrough demonstrates how to change the default log filtering for the `My.Application.Log` object, to control what information is passed from the `Log` object to the listeners and what information is written by the listeners.</span></span> <span data-ttu-id="c74c2-104">Chování protokolování můžete změnit i po vytvoření aplikace, protože informace o konfiguraci jsou uloženy v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="c74c2-104">You can change the logging behavior even after building the application, because the configuration information is stored in the application's configuration file.</span></span>

## <a name="getting-started"></a><span data-ttu-id="c74c2-105">Začínáme</span><span class="sxs-lookup"><span data-stu-id="c74c2-105">Getting Started</span></span>

<span data-ttu-id="c74c2-106">Každá zpráva, která `My.Application.Log` zapíše má přidruženou úroveň závažnosti, které mechanismy filtrování použít k řízení výstupu protokolu.</span><span class="sxs-lookup"><span data-stu-id="c74c2-106">Each message that `My.Application.Log` writes has an associated severity level, which filtering mechanisms use to control the log output.</span></span> <span data-ttu-id="c74c2-107">Tato ukázková `My.Application.Log` aplikace používá metody k zápisu několika zpráv protokolu s různými úrovněmi závažnosti.</span><span class="sxs-lookup"><span data-stu-id="c74c2-107">This sample application uses `My.Application.Log` methods to write several log messages with different severity levels.</span></span>

#### <a name="to-build-the-sample-application"></a><span data-ttu-id="c74c2-108">Vytvoření ukázkové aplikace</span><span class="sxs-lookup"><span data-stu-id="c74c2-108">To build the sample application</span></span>

1. <span data-ttu-id="c74c2-109">Otevřete nový projekt aplikace jazyka Visual Basic pro Systém Windows.</span><span class="sxs-lookup"><span data-stu-id="c74c2-109">Open a new Visual Basic Windows Application project.</span></span>

2. <span data-ttu-id="c74c2-110">Přidejte tlačítko s názvem Button1 do formuláře1.</span><span class="sxs-lookup"><span data-stu-id="c74c2-110">Add a button named Button1 to Form1.</span></span>

3. <span data-ttu-id="c74c2-111">V <xref:System.Windows.Forms.Control.Click> obslužné rutině události button1 přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="c74c2-111">In the <xref:System.Windows.Forms.Control.Click> event handler for Button1, add the following code:</span></span>

     [!code-vb[VbVbcnMyApplicationLogFiltering#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyApplicationLogFiltering/VB/Form1.vb#1)]

4. <span data-ttu-id="c74c2-112">Spusťte aplikaci v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="c74c2-112">Run the application in the debugger.</span></span>

5. <span data-ttu-id="c74c2-113">Stiskněte **tlačítko1**.</span><span class="sxs-lookup"><span data-stu-id="c74c2-113">Press **Button1**.</span></span>

     <span data-ttu-id="c74c2-114">Aplikace zapíše následující informace do ladicího výstupu aplikace a souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="c74c2-114">The application writes the following information to the application's debug output and log file.</span></span>

     `DefaultSource Information: 0 : In Button1_Click`

     `DefaultSource Error: 2 : Error in the application.`

6. <span data-ttu-id="c74c2-115">Zavřete aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c74c2-115">Close the application.</span></span>

     <span data-ttu-id="c74c2-116">Informace o tom, jak zobrazit výstupní okno ladění aplikace, naleznete v [tématu Output Window](/visualstudio/ide/reference/output-window).</span><span class="sxs-lookup"><span data-stu-id="c74c2-116">For information on how to view the application's debug output window, see [Output Window](/visualstudio/ide/reference/output-window).</span></span> <span data-ttu-id="c74c2-117">Informace o umístění souboru protokolu aplikace naleznete v [tématu Návod: Určení, kde my.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="c74c2-117">For information on the location of the application's log file, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="c74c2-118">Ve výchozím nastavení aplikace vyprázdní výstup souboru protokolu při ukončení aplikace.</span><span class="sxs-lookup"><span data-stu-id="c74c2-118">By default, the application flushes the log-file output when the application closes.</span></span>

     <span data-ttu-id="c74c2-119">Ve výše uvedeném příkladu <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> druhé volání metody <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> a volání metody vytvoří výstup protokolu, zatímco `WriteEntry` první a poslední volání metody není.</span><span class="sxs-lookup"><span data-stu-id="c74c2-119">In the example above, the second call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> method and the call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> method produces log output, while the first and last calls to the `WriteEntry` method do not.</span></span> <span data-ttu-id="c74c2-120">Důvodem je, že `WriteEntry` úrovně `WriteException` závažnosti a jsou "Informace" a "Chyba", které jsou povoleny výchozí filtrování protokolu objektu. `My.Application.Log`</span><span class="sxs-lookup"><span data-stu-id="c74c2-120">This is because the severity levels of `WriteEntry` and `WriteException` are "Information" and "Error", both of which are allowed by the `My.Application.Log` object's default log filtering.</span></span> <span data-ttu-id="c74c2-121">Události s úrovněmi závažnosti "Start" a "Stop" však brání vytváření výstupu protokolu.</span><span class="sxs-lookup"><span data-stu-id="c74c2-121">However, events with "Start" and "Stop" severity levels are prevented from producing log output.</span></span>

## <a name="filtering-for-all-myapplicationlog-listeners"></a><span data-ttu-id="c74c2-122">Filtrování pro všechny posluchače my.Application.Log</span><span class="sxs-lookup"><span data-stu-id="c74c2-122">Filtering for All My.Application.Log Listeners</span></span>

<span data-ttu-id="c74c2-123">Objekt `My.Application.Log` používá <xref:System.Diagnostics.SourceSwitch> pojmenovaný `DefaultSwitch` k řízení, které `WriteEntry` zprávy `WriteException` předá z a metody naslouchací procesy protokolu.</span><span class="sxs-lookup"><span data-stu-id="c74c2-123">The `My.Application.Log` object uses a <xref:System.Diagnostics.SourceSwitch> named `DefaultSwitch` to control which messages it passes from the `WriteEntry` and `WriteException` methods to the log listeners.</span></span> <span data-ttu-id="c74c2-124">V konfiguračním souboru aplikace můžete nakonfigurovat `DefaultSwitch` <xref:System.Diagnostics.SourceLevels> nastavením její hodnoty na jednu z hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="c74c2-124">You can configure `DefaultSwitch` in the application's configuration file by setting its value to one of the <xref:System.Diagnostics.SourceLevels> enumeration values.</span></span> <span data-ttu-id="c74c2-125">Ve výchozím nastavení je jeho hodnota "Informace".</span><span class="sxs-lookup"><span data-stu-id="c74c2-125">By default, its value is "Information".</span></span>

<span data-ttu-id="c74c2-126">Tato tabulka ukazuje úroveň závažnosti požadovanou pro Protokol napsat zprávu `DefaultSwitch` posluchačům, dané konkrétní nastavení.</span><span class="sxs-lookup"><span data-stu-id="c74c2-126">This table shows the severity level required for Log to write a message to the listeners, given a particular `DefaultSwitch` setting.</span></span>

|<span data-ttu-id="c74c2-127">Hodnota DefaultSwitch</span><span class="sxs-lookup"><span data-stu-id="c74c2-127">DefaultSwitch Value</span></span>|<span data-ttu-id="c74c2-128">Závažnost zprávy požadovaná pro výstup</span><span class="sxs-lookup"><span data-stu-id="c74c2-128">Message severity required for output</span></span>|
|---|---|
|`Critical`|`Critical`|
|`Error`|<span data-ttu-id="c74c2-129">`Critical` nebo `Error`</span><span class="sxs-lookup"><span data-stu-id="c74c2-129">`Critical` or `Error`</span></span>|
|`Warning`|<span data-ttu-id="c74c2-130">`Critical`, `Error`, nebo`Warning`</span><span class="sxs-lookup"><span data-stu-id="c74c2-130">`Critical`, `Error`, or `Warning`</span></span>|
|`Information`|<span data-ttu-id="c74c2-131">`Critical`, `Error` `Warning`, , nebo`Information`</span><span class="sxs-lookup"><span data-stu-id="c74c2-131">`Critical`, `Error`, `Warning`, or `Information`</span></span>|
|`Verbose`|<span data-ttu-id="c74c2-132">`Critical`, `Error` `Warning`, `Information`, , nebo`Verbose`</span><span class="sxs-lookup"><span data-stu-id="c74c2-132">`Critical`, `Error`, `Warning`, `Information`, or `Verbose`</span></span>|
|`ActivityTracing`|<span data-ttu-id="c74c2-133">`Start`, `Stop` `Suspend`, `Resume`, , nebo`Transfer`</span><span class="sxs-lookup"><span data-stu-id="c74c2-133">`Start`, `Stop`, `Suspend`, `Resume`, or `Transfer`</span></span>|
|`All`|<span data-ttu-id="c74c2-134">Všechny zprávy jsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="c74c2-134">All messages are allowed.</span></span>|
|`Off`|<span data-ttu-id="c74c2-135">Všechny zprávy jsou blokovány.</span><span class="sxs-lookup"><span data-stu-id="c74c2-135">All messages are blocked.</span></span>|

> [!NOTE]
> <span data-ttu-id="c74c2-136">A `WriteEntry` `WriteException` metody mají přetížení, které neurčuje úroveň závažnosti.</span><span class="sxs-lookup"><span data-stu-id="c74c2-136">The `WriteEntry` and `WriteException` methods each have an overload that does not specify a severity level.</span></span> <span data-ttu-id="c74c2-137">Implicitní úroveň závažnosti `WriteEntry` pro přetížení je "Informace" a implicitní úroveň závažnosti pro `WriteException` přetížení je "Chyba".</span><span class="sxs-lookup"><span data-stu-id="c74c2-137">The implicit severity level for the `WriteEntry` overload is "Information", and the implicit severity level for the `WriteException` overload is "Error".</span></span>

<span data-ttu-id="c74c2-138">Tato tabulka vysvětluje výstup protokolu zobrazený v předchozím `DefaultSwitch` příkladu: s výchozím nastavením `WriteEntry` "Informace", pouze `WriteException` druhé volání metody a volání metody vytvoří výstup protokolu.</span><span class="sxs-lookup"><span data-stu-id="c74c2-138">This table explains the log output shown in the previous example: with the default `DefaultSwitch` setting of "Information", only the second call to the `WriteEntry` method and the call to the `WriteException` method produce log output.</span></span>

#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="c74c2-139">Protokolovat pouze události trasování aktivit</span><span class="sxs-lookup"><span data-stu-id="c74c2-139">To log only activity tracing events</span></span>

1. <span data-ttu-id="c74c2-140">Klepněte pravým tlačítkem myši na soubor app.config v **Průzkumníku řešení** a vyberte **příkaz Otevřít**.</span><span class="sxs-lookup"><span data-stu-id="c74c2-140">Right-click app.config in the **Solution Explorer** and select **Open**.</span></span>

     <span data-ttu-id="c74c2-141">-nebo-</span><span class="sxs-lookup"><span data-stu-id="c74c2-141">-or-</span></span>

     <span data-ttu-id="c74c2-142">Pokud není k dispozici žádný soubor app.config:</span><span class="sxs-lookup"><span data-stu-id="c74c2-142">If there is no app.config file:</span></span>

    1. <span data-ttu-id="c74c2-143">V nabídce **Projekt** zvolte **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="c74c2-143">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="c74c2-144">V dialogovém okně **Přidat novou položku** zvolte **Konfigurační soubor aplikace**.</span><span class="sxs-lookup"><span data-stu-id="c74c2-144">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="c74c2-145">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="c74c2-145">Click **Add**.</span></span>

2. <span data-ttu-id="c74c2-146">Vyhledejte `<switches>` oddíl, který `<system.diagnostics>` je v části, která `<configuration>` je v části nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="c74c2-146">Locate the `<switches>` section, which is in the `<system.diagnostics>` section, which is in the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="c74c2-147">Najít prvek, `DefaultSwitch` který přidá do kolekce přepínačů.</span><span class="sxs-lookup"><span data-stu-id="c74c2-147">Find the element that adds `DefaultSwitch` to the collection of switches.</span></span> <span data-ttu-id="c74c2-148">Mělo by vypadat podobně jako tento prvek:</span><span class="sxs-lookup"><span data-stu-id="c74c2-148">It should look similar to this element:</span></span>

     `<add name="DefaultSwitch" value="Information" />`

4. <span data-ttu-id="c74c2-149">Změňte hodnotu `value` atributu na "ActivityTracing".</span><span class="sxs-lookup"><span data-stu-id="c74c2-149">Change the value of the `value` attribute to "ActivityTracing".</span></span>

5. <span data-ttu-id="c74c2-150">Obsah souboru app.config by měl být podobný následujícímu xml:</span><span class="sxs-lookup"><span data-stu-id="c74c2-150">The content of the app.config file should be similar to the following XML:</span></span>

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

6. <span data-ttu-id="c74c2-151">Spusťte aplikaci v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="c74c2-151">Run the application in the debugger.</span></span>

7. <span data-ttu-id="c74c2-152">Stiskněte **tlačítko1**.</span><span class="sxs-lookup"><span data-stu-id="c74c2-152">Press **Button1**.</span></span>

     <span data-ttu-id="c74c2-153">Aplikace zapíše následující informace do ladicího výstupu aplikace a do souboru protokolu:</span><span class="sxs-lookup"><span data-stu-id="c74c2-153">The application writes the following information to the application's debug output and log file:</span></span>

     `DefaultSource Start: 4 : Entering Button1_Click`

     `DefaultSource Stop: 5 : Leaving Button1_Click`

8. <span data-ttu-id="c74c2-154">Zavřete aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c74c2-154">Close the application.</span></span>

9. <span data-ttu-id="c74c2-155">Změňte hodnotu `value` atributu zpět na "Informace".</span><span class="sxs-lookup"><span data-stu-id="c74c2-155">Change the value of the `value` attribute back to "Information".</span></span>

    > [!NOTE]
    > <span data-ttu-id="c74c2-156">Nastavení `DefaultSwitch` přepínače `My.Application.Log`ovládá pouze .</span><span class="sxs-lookup"><span data-stu-id="c74c2-156">The `DefaultSwitch` switch setting controls only `My.Application.Log`.</span></span> <span data-ttu-id="c74c2-157">Nezmění způsob, jakým se <xref:System.Diagnostics.Trace?displayProperty=nameWithType> chová <xref:System.Diagnostics.Debug?displayProperty=nameWithType> rozhraní .NET Framework a třídy.</span><span class="sxs-lookup"><span data-stu-id="c74c2-157">It does not change how the .NET Framework <xref:System.Diagnostics.Trace?displayProperty=nameWithType> and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes behave.</span></span>

## <a name="individual-filtering-for-myapplicationlog-listeners"></a><span data-ttu-id="c74c2-158">Individuální filtrování pro posluchače my.Application.Log</span><span class="sxs-lookup"><span data-stu-id="c74c2-158">Individual Filtering For My.Application.Log Listeners</span></span>

<span data-ttu-id="c74c2-159">Předchozí příklad ukazuje, jak změnit filtrování `My.Application.Log` pro všechny výstupy.</span><span class="sxs-lookup"><span data-stu-id="c74c2-159">The previous example shows how to change the filtering for all `My.Application.Log` output.</span></span> <span data-ttu-id="c74c2-160">Tento příklad ukazuje, jak filtrovat naslouchací proces protokolu.</span><span class="sxs-lookup"><span data-stu-id="c74c2-160">This example demonstrates how to filter an individual log listener.</span></span> <span data-ttu-id="c74c2-161">Ve výchozím nastavení má aplikace dva naslouchací procesy, které zapisují do ladicího výstupu aplikace a souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="c74c2-161">By default, an application has two listeners that write to the application's debug output and the log file.</span></span>

<span data-ttu-id="c74c2-162">Konfigurační soubor řídí chování posluchačů protokolu tím, že umožňuje každému z nich `My.Application.Log`mít filtr, který je podobný přepínači pro .</span><span class="sxs-lookup"><span data-stu-id="c74c2-162">The configuration file controls the behavior of the log listeners by allowing each one to have a filter, which is similar to a switch for `My.Application.Log`.</span></span> <span data-ttu-id="c74c2-163">Naslouchací proces protokolu bude výstup zprávy pouze v případě, `DefaultSwitch` že závažnost zprávy je povoleno protokolu a naslouchací filtr posluchače protokolu.</span><span class="sxs-lookup"><span data-stu-id="c74c2-163">A log listener will output a message only if the message's severity is allowed by both the log's `DefaultSwitch` and the log listener's filter.</span></span>

<span data-ttu-id="c74c2-164">Tento příklad ukazuje, jak nakonfigurovat filtrování pro nový naslouchací proces ladění a přidat jej do objektu. `Log`</span><span class="sxs-lookup"><span data-stu-id="c74c2-164">This example demonstrates how to configure filtering for a new debug listener and add it to the `Log` object.</span></span> <span data-ttu-id="c74c2-165">Výchozí naslouchací proces `Log` ladění by měl být odebrán z objektu, takže je jasné, že ladicí zprávy pocházejí z nového procesu ladění.</span><span class="sxs-lookup"><span data-stu-id="c74c2-165">The default debug listener should be removed from the `Log` object, so it is clear that the debug messages come from the new debug listener.</span></span>

#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="c74c2-166">Protokolovat pouze události trasování aktivit</span><span class="sxs-lookup"><span data-stu-id="c74c2-166">To log only activity-tracing events</span></span>

1. <span data-ttu-id="c74c2-167">Klepněte pravým tlačítkem myši na soubor app.config v **Průzkumníku řešení** a zvolte **Otevřít**.</span><span class="sxs-lookup"><span data-stu-id="c74c2-167">Right-click app.config in the **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="c74c2-168">\-nebo-</span><span class="sxs-lookup"><span data-stu-id="c74c2-168">\-or-</span></span>

     <span data-ttu-id="c74c2-169">Pokud není k dispozici žádný soubor app.config:</span><span class="sxs-lookup"><span data-stu-id="c74c2-169">If there is no app.config file:</span></span>

    1. <span data-ttu-id="c74c2-170">V nabídce **Projekt** zvolte **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="c74c2-170">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="c74c2-171">V dialogovém okně **Přidat novou položku** zvolte **Konfigurační soubor aplikace**.</span><span class="sxs-lookup"><span data-stu-id="c74c2-171">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="c74c2-172">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="c74c2-172">Click **Add**.</span></span>

2. <span data-ttu-id="c74c2-173">Klepněte pravým tlačítkem myši na soubor app.config v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="c74c2-173">Right-click app.config in **Solution Explorer**.</span></span> <span data-ttu-id="c74c2-174">Zvolte **Otevřít**.</span><span class="sxs-lookup"><span data-stu-id="c74c2-174">Choose **Open**.</span></span>

3. <span data-ttu-id="c74c2-175">Vyhledejte `<listeners>` oddíl v `<source>` části `name` s atributem "DefaultSource", `<sources>` který je pod oddílem.</span><span class="sxs-lookup"><span data-stu-id="c74c2-175">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", which is under the `<sources>` section.</span></span> <span data-ttu-id="c74c2-176">Sekce `<sources>` je pod `<system.diagnostics>` částí, v horní `<configuration>` části.</span><span class="sxs-lookup"><span data-stu-id="c74c2-176">The `<sources>` section is under the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

4. <span data-ttu-id="c74c2-177">Přidejte tento `<listeners>` prvek do oddílu:</span><span class="sxs-lookup"><span data-stu-id="c74c2-177">Add this element to the `<listeners>` section:</span></span>

    ```xml
    <!-- Remove the default debug listener. -->
    <remove name="Default"/>
    <!-- Add a filterable debug listener. -->
    <add name="NewDefault"/>
    ```

5. <span data-ttu-id="c74c2-178">Vyhledejte `<sharedListeners>` oddíl v `<system.diagnostics>` části v části `<configuration>` nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="c74c2-178">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

6. <span data-ttu-id="c74c2-179">Přidejte tento `<sharedListeners>` prvek do tohoto oddílu:</span><span class="sxs-lookup"><span data-stu-id="c74c2-179">Add this element to that `<sharedListeners>` section:</span></span>

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

     <span data-ttu-id="c74c2-180">Filtr <xref:System.Diagnostics.EventTypeFilter> přebírá jednu <xref:System.Diagnostics.SourceLevels> z hodnot výčtu jako svůj `initializeData` atribut.</span><span class="sxs-lookup"><span data-stu-id="c74c2-180">The <xref:System.Diagnostics.EventTypeFilter> filter takes one of the <xref:System.Diagnostics.SourceLevels> enumeration values as its `initializeData` attribute.</span></span>

7. <span data-ttu-id="c74c2-181">Obsah souboru app.config by měl být podobný následujícímu xml:</span><span class="sxs-lookup"><span data-stu-id="c74c2-181">The content of the app.config file should be similar to the following XML:</span></span>

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

8. <span data-ttu-id="c74c2-182">Spusťte aplikaci v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="c74c2-182">Run the application in the debugger.</span></span>

9. <span data-ttu-id="c74c2-183">Stiskněte **tlačítko1**.</span><span class="sxs-lookup"><span data-stu-id="c74c2-183">Press **Button1**.</span></span>

     <span data-ttu-id="c74c2-184">Aplikace zapíše do souboru protokolu aplikace následující informace:</span><span class="sxs-lookup"><span data-stu-id="c74c2-184">The application writes the following information to the application's log file:</span></span>

     `Default Information: 0 : In Button1_Click`

     `Default Error: 2 : Error in the application.`

     <span data-ttu-id="c74c2-185">Aplikace zapíše méně informací do výstupu ladění aplikace z důvodu více omezující filtrování.</span><span class="sxs-lookup"><span data-stu-id="c74c2-185">The application writes less information to the application's debug output because of the more restrictive filtering.</span></span>

     `Default Error   2   Error`

10. <span data-ttu-id="c74c2-186">Zavřete aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c74c2-186">Close the application.</span></span>

<span data-ttu-id="c74c2-187">Další informace o změně nastavení protokolu po nasazení naleznete v [tématu Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="c74c2-187">For more information about changing log settings after deployment, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c74c2-188">Viz také</span><span class="sxs-lookup"><span data-stu-id="c74c2-188">See also</span></span>

- [<span data-ttu-id="c74c2-189">Návod: Zjištění, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="c74c2-189">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="c74c2-190">Návod: Změna místa, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="c74c2-190">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="c74c2-191">Návod: Vytváření vlastních součástí naslouchajících protokolům</span><span class="sxs-lookup"><span data-stu-id="c74c2-191">Walkthrough: Creating Custom Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)
- [<span data-ttu-id="c74c2-192">Postupy: Zápis zpráv protokolu</span><span class="sxs-lookup"><span data-stu-id="c74c2-192">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="c74c2-193">Přepínače trasování</span><span class="sxs-lookup"><span data-stu-id="c74c2-193">Trace Switches</span></span>](../../../../framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="c74c2-194">Protokolování informací z aplikace</span><span class="sxs-lookup"><span data-stu-id="c74c2-194">Logging Information from the Application</span></span>](../../../../visual-basic/developing-apps/programming/log-info/index.md)
