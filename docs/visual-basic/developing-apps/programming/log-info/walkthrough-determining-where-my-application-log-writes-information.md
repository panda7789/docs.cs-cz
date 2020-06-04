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
ms.openlocfilehash: 00b543dbe96ca99446f6797a13b66ee62c422b93
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398276"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="192f9-102">Návod: Zjištění, kam objekt My.Application.Log zapisuje informace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="192f9-102">Walkthrough: Determining Where My.Application.Log Writes Information (Visual Basic)</span></span>

<span data-ttu-id="192f9-103">`My.Application.Log`Objekt může zapisovat informace do několika posluchačů protokolů.</span><span class="sxs-lookup"><span data-stu-id="192f9-103">The `My.Application.Log` object can write information to several log listeners.</span></span> <span data-ttu-id="192f9-104">Naslouchací procesy protokolu jsou nakonfigurovány pomocí konfiguračního souboru počítače a mohou být přepsány konfiguračním souborem aplikace.</span><span class="sxs-lookup"><span data-stu-id="192f9-104">The log listeners are configured by the computer's configuration file and can be overridden by an application's configuration file.</span></span> <span data-ttu-id="192f9-105">Toto téma popisuje výchozí nastavení a způsob určení nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="192f9-105">This topic describes the default settings and how to determine the settings for your application.</span></span>

<span data-ttu-id="192f9-106">Další informace o výchozích umístěních výstupu najdete v tématu [práce s protokoly aplikací](working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="192f9-106">For more information about the default output locations, see [Working with Application Logs](working-with-application-logs.md).</span></span>

### <a name="to-determine-the-listeners-for-myapplicationlog"></a><span data-ttu-id="192f9-107">Určení naslouchacího procesu pro My. Application. log</span><span class="sxs-lookup"><span data-stu-id="192f9-107">To determine the listeners for My.Application.Log</span></span>

1. <span data-ttu-id="192f9-108">Vyhledejte konfigurační soubor sestavení.</span><span class="sxs-lookup"><span data-stu-id="192f9-108">Locate the assembly's configuration file.</span></span> <span data-ttu-id="192f9-109">Pokud vyvíjíte sestavení, můžete získat přístup k souboru App. config v aplikaci Visual Studio z **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="192f9-109">If you are developing the assembly, you can access the app.config in Visual Studio from the **Solution Explorer**.</span></span> <span data-ttu-id="192f9-110">V opačném případě je název konfiguračního souboru názvem sestavení připojeným pomocí ". config" a je umístěn ve stejném adresáři jako sestavení.</span><span class="sxs-lookup"><span data-stu-id="192f9-110">Otherwise, the configuration file name is the assembly's name appended with ".config", and it is located in the same directory as the assembly.</span></span>

    > [!NOTE]
    > <span data-ttu-id="192f9-111">Ne každé sestavení má konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="192f9-111">Not every assembly has a configuration file.</span></span>

    <span data-ttu-id="192f9-112">Konfigurační soubor je soubor XML.</span><span class="sxs-lookup"><span data-stu-id="192f9-112">The configuration file is an XML file.</span></span>

2. <span data-ttu-id="192f9-113">Vyhledejte `<listeners>` část v části `<source>` s `name` atributem "DefaultSource", který se nachází v `<sources>` části.</span><span class="sxs-lookup"><span data-stu-id="192f9-113">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="192f9-114">`<sources>`Oddíl je umístěný v části `<system.diagnostics>` v části nejvyšší úrovně `<configuration>` .</span><span class="sxs-lookup"><span data-stu-id="192f9-114">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

    <span data-ttu-id="192f9-115">Pokud tyto oddíly neexistují, může konfigurační soubor počítače nakonfigurovat `My.Application.Log` naslouchací procesy protokolu.</span><span class="sxs-lookup"><span data-stu-id="192f9-115">If these sections do not exist, then the computer's configuration file may configure the `My.Application.Log` log listeners.</span></span> <span data-ttu-id="192f9-116">Následující postup popisuje, jak určit, jaký konfigurační soubor počítače definuje:</span><span class="sxs-lookup"><span data-stu-id="192f9-116">The following steps describe how to determine what the computer configuration file defines:</span></span>

    1. <span data-ttu-id="192f9-117">Vyhledejte soubor Machine. config počítače.</span><span class="sxs-lookup"><span data-stu-id="192f9-117">Locate the computer's machine.config file.</span></span> <span data-ttu-id="192f9-118">Obvykle se nachází v adresáři *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* , kde `SystemRoot` je adresář operačního systému, a `frameworkVersion` je verze .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="192f9-118">Typically, it is located in the *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* directory, where `SystemRoot` is the operating system directory, and `frameworkVersion` is the version of the .NET Framework.</span></span>

        <span data-ttu-id="192f9-119">Nastavení v souboru Machine. config může přepsat konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="192f9-119">The settings in machine.config can be overridden by an application's configuration file.</span></span>

        <span data-ttu-id="192f9-120">Pokud volitelné prvky uvedené níže neexistují, můžete je vytvořit.</span><span class="sxs-lookup"><span data-stu-id="192f9-120">If the optional elements listed below do not exist, you can create them.</span></span>

    2. <span data-ttu-id="192f9-121">Vyhledejte část v části `<listeners>` `<source>` s `name` atributem "DefaultSource" v části v části v části v sekci `<sources>` `<system.diagnostics>` nejvyšší úrovně `<configuration>` .</span><span class="sxs-lookup"><span data-stu-id="192f9-121">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

        <span data-ttu-id="192f9-122">Pokud tyto oddíly neexistují, pak `My.Application.Log` má pouze výchozí naslouchací procesy protokolu.</span><span class="sxs-lookup"><span data-stu-id="192f9-122">If these sections do not exist, then the `My.Application.Log` has only the default log listeners.</span></span>

3. <span data-ttu-id="192f9-123">`add>`V části <vyhledejte prvky <`listeners>` .</span><span class="sxs-lookup"><span data-stu-id="192f9-123">Locate the <`add>` elements in the <`listeners>` section.</span></span>

     <span data-ttu-id="192f9-124">Tyto prvky přidávají pojmenované naslouchací procesy protokolu ke `My.Application.Log` zdroji.</span><span class="sxs-lookup"><span data-stu-id="192f9-124">These elements add the named log listeners to `My.Application.Log` source.</span></span>

4. <span data-ttu-id="192f9-125">Vyhledejte `<add>` prvky s názvy naslouchacího procesu protokolu v části v části v oddílu `<sharedListeners>` `<system.diagnostics>` nejvyšší úrovně `<configuration>` .</span><span class="sxs-lookup"><span data-stu-id="192f9-125">Locate the `<add>` elements with the names of the log listeners in the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="192f9-126">Pro mnoho typů sdílených posluchačů obsahuje inicializační data naslouchacího procesu popis, kde naslouchací proces přesměruje data:</span><span class="sxs-lookup"><span data-stu-id="192f9-126">For many types of shared listeners, the listener's initialization data includes a description of where the listener directs the data:</span></span>

    - <span data-ttu-id="192f9-127"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>Naslouchací proces zapisuje do protokolu souborů, jak je popsáno v úvodu.</span><span class="sxs-lookup"><span data-stu-id="192f9-127">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener writes to a file log, as described in the introduction.</span></span>

    - <span data-ttu-id="192f9-128"><xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>Naslouchací proces zapisuje informace do protokolu událostí počítače určeného `initializeData` parametrem.</span><span class="sxs-lookup"><span data-stu-id="192f9-128">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener writes information to the computer event log specified by the `initializeData` parameter.</span></span> <span data-ttu-id="192f9-129">Chcete-li zobrazit protokol událostí, můžete použít **Průzkumník serveru** nebo **Windows Prohlížeč událostí**.</span><span class="sxs-lookup"><span data-stu-id="192f9-129">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="192f9-130">Další informace najdete v tématu [události ETW v .NET Framework](../../../../framework/performance/etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="192f9-130">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>

    - <span data-ttu-id="192f9-131"><xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> Naslouchací procesy a zapisují do souboru zadaného v `initializeData` parametru.</span><span class="sxs-lookup"><span data-stu-id="192f9-131">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners write to the file specified in the `initializeData` parameter.</span></span>

    - <span data-ttu-id="192f9-132"><xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>Naslouchací proces zapisuje do konzoly příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="192f9-132">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener writes to the command-line console.</span></span>

    - <span data-ttu-id="192f9-133">Informace o tom, kde jiné typy protokolových posluchačů zapisují informace, najdete v dokumentaci k tomuto typu.</span><span class="sxs-lookup"><span data-stu-id="192f9-133">For information about where other types of log listeners write information, consult that type's documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="192f9-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="192f9-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DelimitedListTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics>
- [<span data-ttu-id="192f9-135">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="192f9-135">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="192f9-136">Postupy: Protokolování výjimek</span><span class="sxs-lookup"><span data-stu-id="192f9-136">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)
- [<span data-ttu-id="192f9-137">Postupy: Zápis zpráv protokolu</span><span class="sxs-lookup"><span data-stu-id="192f9-137">How to: Write Log Messages</span></span>](how-to-write-log-messages.md)
- [<span data-ttu-id="192f9-138">Návod: Změna místa, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="192f9-138">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="192f9-139">Události Trasování událostí pro Windows v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="192f9-139">ETW Events in the .NET Framework</span></span>](../../../../framework/performance/etw-events.md)
- [<span data-ttu-id="192f9-140">Řešení potíží: Komponenty naslouchající protokolům</span><span class="sxs-lookup"><span data-stu-id="192f9-140">Troubleshooting: Log Listeners</span></span>](troubleshooting-log-listeners.md)
