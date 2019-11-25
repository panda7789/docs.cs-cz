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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353610"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="89734-102">Návod: Zjištění, kam objekt My.Application.Log zapisuje informace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89734-102">Walkthrough: Determining Where My.Application.Log Writes Information (Visual Basic)</span></span>

<span data-ttu-id="89734-103">The `My.Application.Log` object can write information to several log listeners.</span><span class="sxs-lookup"><span data-stu-id="89734-103">The `My.Application.Log` object can write information to several log listeners.</span></span> <span data-ttu-id="89734-104">The log listeners are configured by the computer's configuration file and can be overridden by an application's configuration file.</span><span class="sxs-lookup"><span data-stu-id="89734-104">The log listeners are configured by the computer's configuration file and can be overridden by an application's configuration file.</span></span> <span data-ttu-id="89734-105">This topic describes the default settings and how to determine the settings for your application.</span><span class="sxs-lookup"><span data-stu-id="89734-105">This topic describes the default settings and how to determine the settings for your application.</span></span>

<span data-ttu-id="89734-106">For more information about the default output locations, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="89734-106">For more information about the default output locations, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>

### <a name="to-determine-the-listeners-for-myapplicationlog"></a><span data-ttu-id="89734-107">To determine the listeners for My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="89734-107">To determine the listeners for My.Application.Log</span></span>

1. <span data-ttu-id="89734-108">Locate the assembly's configuration file.</span><span class="sxs-lookup"><span data-stu-id="89734-108">Locate the assembly's configuration file.</span></span> <span data-ttu-id="89734-109">If you are developing the assembly, you can access the app.config in Visual Studio from the **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="89734-109">If you are developing the assembly, you can access the app.config in Visual Studio from the **Solution Explorer**.</span></span> <span data-ttu-id="89734-110">Otherwise, the configuration file name is the assembly's name appended with ".config", and it is located in the same directory as the assembly.</span><span class="sxs-lookup"><span data-stu-id="89734-110">Otherwise, the configuration file name is the assembly's name appended with ".config", and it is located in the same directory as the assembly.</span></span>

    > [!NOTE]
    > <span data-ttu-id="89734-111">Not every assembly has a configuration file.</span><span class="sxs-lookup"><span data-stu-id="89734-111">Not every assembly has a configuration file.</span></span>

    <span data-ttu-id="89734-112">The configuration file is an XML file.</span><span class="sxs-lookup"><span data-stu-id="89734-112">The configuration file is an XML file.</span></span>

2. <span data-ttu-id="89734-113">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span><span class="sxs-lookup"><span data-stu-id="89734-113">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="89734-114">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span><span class="sxs-lookup"><span data-stu-id="89734-114">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

    <span data-ttu-id="89734-115">If these sections do not exist, then the computer's configuration file may configure the `My.Application.Log` log listeners.</span><span class="sxs-lookup"><span data-stu-id="89734-115">If these sections do not exist, then the computer's configuration file may configure the `My.Application.Log` log listeners.</span></span> <span data-ttu-id="89734-116">The following steps describe how to determine what the computer configuration file defines:</span><span class="sxs-lookup"><span data-stu-id="89734-116">The following steps describe how to determine what the computer configuration file defines:</span></span>

    1. <span data-ttu-id="89734-117">Locate the computer's machine.config file.</span><span class="sxs-lookup"><span data-stu-id="89734-117">Locate the computer's machine.config file.</span></span> <span data-ttu-id="89734-118">Typically, it is located in the *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* directory, where `SystemRoot` is the operating system directory, and `frameworkVersion` is the version of the .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="89734-118">Typically, it is located in the *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* directory, where `SystemRoot` is the operating system directory, and `frameworkVersion` is the version of the .NET Framework.</span></span>

        <span data-ttu-id="89734-119">The settings in machine.config can be overridden by an application's configuration file.</span><span class="sxs-lookup"><span data-stu-id="89734-119">The settings in machine.config can be overridden by an application's configuration file.</span></span>

        <span data-ttu-id="89734-120">If the optional elements listed below do not exist, you can create them.</span><span class="sxs-lookup"><span data-stu-id="89734-120">If the optional elements listed below do not exist, you can create them.</span></span>

    2. <span data-ttu-id="89734-121">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span><span class="sxs-lookup"><span data-stu-id="89734-121">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

        <span data-ttu-id="89734-122">If these sections do not exist, then the `My.Application.Log` has only the default log listeners.</span><span class="sxs-lookup"><span data-stu-id="89734-122">If these sections do not exist, then the `My.Application.Log` has only the default log listeners.</span></span>

3. <span data-ttu-id="89734-123">Locate the <`add>` elements in the <`listeners>` section.</span><span class="sxs-lookup"><span data-stu-id="89734-123">Locate the <`add>` elements in the <`listeners>` section.</span></span>

     <span data-ttu-id="89734-124">These elements add the named log listeners to `My.Application.Log` source.</span><span class="sxs-lookup"><span data-stu-id="89734-124">These elements add the named log listeners to `My.Application.Log` source.</span></span>

4. <span data-ttu-id="89734-125">Locate the `<add>` elements with the names of the log listeners in the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span><span class="sxs-lookup"><span data-stu-id="89734-125">Locate the `<add>` elements with the names of the log listeners in the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="89734-126">For many types of shared listeners, the listener's initialization data includes a description of where the listener directs the data:</span><span class="sxs-lookup"><span data-stu-id="89734-126">For many types of shared listeners, the listener's initialization data includes a description of where the listener directs the data:</span></span>

    - <span data-ttu-id="89734-127">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener writes to a file log, as described in the introduction.</span><span class="sxs-lookup"><span data-stu-id="89734-127">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener writes to a file log, as described in the introduction.</span></span>

    - <span data-ttu-id="89734-128">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener writes information to the computer event log specified by the `initializeData` parameter.</span><span class="sxs-lookup"><span data-stu-id="89734-128">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener writes information to the computer event log specified by the `initializeData` parameter.</span></span> <span data-ttu-id="89734-129">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span><span class="sxs-lookup"><span data-stu-id="89734-129">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="89734-130">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="89734-130">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>

    - <span data-ttu-id="89734-131">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners write to the file specified in the `initializeData` parameter.</span><span class="sxs-lookup"><span data-stu-id="89734-131">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners write to the file specified in the `initializeData` parameter.</span></span>

    - <span data-ttu-id="89734-132">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener writes to the command-line console.</span><span class="sxs-lookup"><span data-stu-id="89734-132">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener writes to the command-line console.</span></span>

    - <span data-ttu-id="89734-133">For information about where other types of log listeners write information, consult that type's documentation.</span><span class="sxs-lookup"><span data-stu-id="89734-133">For information about where other types of log listeners write information, consult that type's documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="89734-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89734-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DelimitedListTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics>
- [<span data-ttu-id="89734-135">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="89734-135">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="89734-136">Postupy: Protokolování výjimek</span><span class="sxs-lookup"><span data-stu-id="89734-136">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="89734-137">Postupy: Zápis zpráv protokolu</span><span class="sxs-lookup"><span data-stu-id="89734-137">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="89734-138">Návod: Změna místa, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="89734-138">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="89734-139">Trasování událostí pro Windows – události v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="89734-139">ETW Events in the .NET Framework</span></span>](../../../../framework/performance/etw-events.md)
- [<span data-ttu-id="89734-140">Řešení potíží: Součásti naslouchající protokolům</span><span class="sxs-lookup"><span data-stu-id="89734-140">Troubleshooting: Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
