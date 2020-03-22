---
title: Zjištění, kam objekt My.Application.Log zapisuje informace
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, output location
- output, application log location
- My.Application.Log object, output location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
ms.openlocfilehash: f3fd0ed0388276f1400bf77d0abfb488634a45a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74353610"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="2ef54-102">Návod: Zjištění, kam objekt My.Application.Log zapisuje informace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ef54-102">Walkthrough: Determining Where My.Application.Log Writes Information (Visual Basic)</span></span>

<span data-ttu-id="2ef54-103">Objekt `My.Application.Log` může zapisovat informace do několika naslouchacích procesů protokolu.</span><span class="sxs-lookup"><span data-stu-id="2ef54-103">The `My.Application.Log` object can write information to several log listeners.</span></span> <span data-ttu-id="2ef54-104">Naslouchací procesy protokolu jsou konfigurovány konfiguračním souborem počítače a mohou být přepsány konfiguračním souborem aplikace.</span><span class="sxs-lookup"><span data-stu-id="2ef54-104">The log listeners are configured by the computer's configuration file and can be overridden by an application's configuration file.</span></span> <span data-ttu-id="2ef54-105">Toto téma popisuje výchozí nastavení a způsob určení nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="2ef54-105">This topic describes the default settings and how to determine the settings for your application.</span></span>

<span data-ttu-id="2ef54-106">Další informace o výchozích výstupních umístěních naleznete v [tématu Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="2ef54-106">For more information about the default output locations, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>

### <a name="to-determine-the-listeners-for-myapplicationlog"></a><span data-ttu-id="2ef54-107">Chcete-li určit posluchače pro My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="2ef54-107">To determine the listeners for My.Application.Log</span></span>

1. <span data-ttu-id="2ef54-108">Vyhledejte konfigurační soubor sestavení.</span><span class="sxs-lookup"><span data-stu-id="2ef54-108">Locate the assembly's configuration file.</span></span> <span data-ttu-id="2ef54-109">Pokud vyvíjíte sestavení, můžete získat přístup k app.config v sadě Visual Studio z **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="2ef54-109">If you are developing the assembly, you can access the app.config in Visual Studio from the **Solution Explorer**.</span></span> <span data-ttu-id="2ef54-110">V opačném případě je název konfiguračního souboru název sestavení připojen s ".config" a je umístěn ve stejném adresáři jako sestavení.</span><span class="sxs-lookup"><span data-stu-id="2ef54-110">Otherwise, the configuration file name is the assembly's name appended with ".config", and it is located in the same directory as the assembly.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2ef54-111">Ne každé sestavení má konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="2ef54-111">Not every assembly has a configuration file.</span></span>

    <span data-ttu-id="2ef54-112">Konfigurační soubor je soubor XML.</span><span class="sxs-lookup"><span data-stu-id="2ef54-112">The configuration file is an XML file.</span></span>

2. <span data-ttu-id="2ef54-113">Vyhledejte `<listeners>` oddíl v `<source>` části `name` s atributem "DefaultSource", který se nachází v `<sources>` sekci.</span><span class="sxs-lookup"><span data-stu-id="2ef54-113">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="2ef54-114">Sekce `<sources>` je umístěna `<system.diagnostics>` v sekci, v `<configuration>` sekci nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="2ef54-114">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

    <span data-ttu-id="2ef54-115">Pokud tyto oddíly neexistují, může konfigurační `My.Application.Log` soubor počítače konfigurovat posluchače protokolu.</span><span class="sxs-lookup"><span data-stu-id="2ef54-115">If these sections do not exist, then the computer's configuration file may configure the `My.Application.Log` log listeners.</span></span> <span data-ttu-id="2ef54-116">Následující kroky popisují, jak určit, co definuje konfigurační soubor počítače:</span><span class="sxs-lookup"><span data-stu-id="2ef54-116">The following steps describe how to determine what the computer configuration file defines:</span></span>

    1. <span data-ttu-id="2ef54-117">Vyhledejte soubor machine.config počítače.</span><span class="sxs-lookup"><span data-stu-id="2ef54-117">Locate the computer's machine.config file.</span></span> <span data-ttu-id="2ef54-118">Obvykle je umístěn v adresáři *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG,* kde `SystemRoot` je adresář `frameworkVersion` operačního systému a je verzí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2ef54-118">Typically, it is located in the *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* directory, where `SystemRoot` is the operating system directory, and `frameworkVersion` is the version of the .NET Framework.</span></span>

        <span data-ttu-id="2ef54-119">Nastavení v souboru machine.config lze přepsat konfiguračním souborem aplikace.</span><span class="sxs-lookup"><span data-stu-id="2ef54-119">The settings in machine.config can be overridden by an application's configuration file.</span></span>

        <span data-ttu-id="2ef54-120">Pokud níže uvedené volitelné prvky neexistují, můžete je vytvořit.</span><span class="sxs-lookup"><span data-stu-id="2ef54-120">If the optional elements listed below do not exist, you can create them.</span></span>

    2. <span data-ttu-id="2ef54-121">Vyhledejte `<listeners>` oddíl v `<source>` části `name` s atributem "DefaultSource" v `<sources>` `<system.diagnostics>` části, v sekci, `<configuration>` v části nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="2ef54-121">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

        <span data-ttu-id="2ef54-122">Pokud tyto oddíly neexistují, `My.Application.Log` pak má pouze výchozí naslouchací procesy protokolu.</span><span class="sxs-lookup"><span data-stu-id="2ef54-122">If these sections do not exist, then the `My.Application.Log` has only the default log listeners.</span></span>

3. <span data-ttu-id="2ef54-123">Vyhledejte `add>` <prvky `listeners>` v části <.</span><span class="sxs-lookup"><span data-stu-id="2ef54-123">Locate the <`add>` elements in the <`listeners>` section.</span></span>

     <span data-ttu-id="2ef54-124">Tyto prvky přidat pojmenované `My.Application.Log` posluchače protokolu do zdroje.</span><span class="sxs-lookup"><span data-stu-id="2ef54-124">These elements add the named log listeners to `My.Application.Log` source.</span></span>

4. <span data-ttu-id="2ef54-125">Vyhledejte `<add>` prvky s názvy posluchačů `<sharedListeners>` protokolu v `<system.diagnostics>` části, v části, v části nejvyšší úrovně. `<configuration>`</span><span class="sxs-lookup"><span data-stu-id="2ef54-125">Locate the `<add>` elements with the names of the log listeners in the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="2ef54-126">Pro mnoho typů sdílených naslouchacích procesů inicializační data posluchače obsahuje popis, kde posluchač směruje data:</span><span class="sxs-lookup"><span data-stu-id="2ef54-126">For many types of shared listeners, the listener's initialization data includes a description of where the listener directs the data:</span></span>

    - <span data-ttu-id="2ef54-127">Naslouchací <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> proces zapíše do protokolu souborů, jak je popsáno v úvodu.</span><span class="sxs-lookup"><span data-stu-id="2ef54-127">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener writes to a file log, as described in the introduction.</span></span>

    - <span data-ttu-id="2ef54-128">Naslouchací <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> proces zapisuje informace do protokolu událostí počítače určeného parametrem. `initializeData`</span><span class="sxs-lookup"><span data-stu-id="2ef54-128">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener writes information to the computer event log specified by the `initializeData` parameter.</span></span> <span data-ttu-id="2ef54-129">Chcete-li zobrazit protokol událostí, můžete použít **Průzkumníka serveru** nebo **Prohlížeč událostí systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="2ef54-129">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="2ef54-130">Další informace naleznete [v tématu ETW Události v rozhraní .NET Framework](../../../../framework/performance/etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="2ef54-130">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>

    - <span data-ttu-id="2ef54-131"><xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> Posluchači <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> a zapisovat do `initializeData` souboru určeného v parametru.</span><span class="sxs-lookup"><span data-stu-id="2ef54-131">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners write to the file specified in the `initializeData` parameter.</span></span>

    - <span data-ttu-id="2ef54-132">Naslouchací <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> proces zapisuje do konzoly příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="2ef54-132">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener writes to the command-line console.</span></span>

    - <span data-ttu-id="2ef54-133">Informace o tom, kde jiné typy posluchačů protokolu psát informace, naleznete v dokumentaci tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="2ef54-133">For information about where other types of log listeners write information, consult that type's documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ef54-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ef54-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DelimitedListTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics>
- [<span data-ttu-id="2ef54-135">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="2ef54-135">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="2ef54-136">Postupy: Protokolování výjimek</span><span class="sxs-lookup"><span data-stu-id="2ef54-136">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="2ef54-137">Postupy: Zápis zpráv protokolu</span><span class="sxs-lookup"><span data-stu-id="2ef54-137">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="2ef54-138">Návod: Změna místa, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="2ef54-138">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="2ef54-139">Události Trasování událostí pro Windows v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2ef54-139">ETW Events in the .NET Framework</span></span>](../../../../framework/performance/etw-events.md)
- [<span data-ttu-id="2ef54-140">Řešení potíží: Součásti naslouchající protokolům</span><span class="sxs-lookup"><span data-stu-id="2ef54-140">Troubleshooting: Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
