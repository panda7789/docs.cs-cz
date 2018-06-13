---
title: Určení, kam objekt My.Application.Log zapisuje informace (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, output location
- output, application log location
- My.Application.Log object, outpout location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
ms.openlocfilehash: fa177fa1f07c52d900f57e5bf61c967f06203c4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590930"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="234cf-102">Návod: Zjištění, kam objekt My.Application.Log zapisuje informace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="234cf-102">Walkthrough: Determining Where My.Application.Log Writes Information (Visual Basic)</span></span>
<span data-ttu-id="234cf-103">`My.Application.Log` Objekt může zapsat informace do několika naslouchací procesy pro protokoly.</span><span class="sxs-lookup"><span data-stu-id="234cf-103">The `My.Application.Log` object can write information to several log listeners.</span></span> <span data-ttu-id="234cf-104">Naslouchací procesy pro protokoly jsou nakonfigurovány pomocí souboru konfigurace počítače a mohou být přepsány konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="234cf-104">The log listeners are configured by the computer's configuration file and can be overridden by an application's configuration file.</span></span> <span data-ttu-id="234cf-105">Toto téma popisuje výchozí nastavení a jak určit nastavení pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="234cf-105">This topic describes the default settings and how to determine the settings for your application.</span></span>  
  
 <span data-ttu-id="234cf-106">Další informace o výchozích umístění výstupu najdete v tématu [práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="234cf-106">For more information about the default output locations, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>  
  
### <a name="to-determine-the-listeners-for-myapplicationlog"></a><span data-ttu-id="234cf-107">Chcete-li zjistit naslouchací procesy pro My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="234cf-107">To determine the listeners for My.Application.Log</span></span>  
  
1.  <span data-ttu-id="234cf-108">Vyhledejte soubor konfigurace je sestavení.</span><span class="sxs-lookup"><span data-stu-id="234cf-108">Locate the assembly's configuration file.</span></span> <span data-ttu-id="234cf-109">Pokud vyvíjíte sestavení, můžete přístup k souboru app.config v sadě Visual Studio z **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="234cf-109">If you are developing the assembly, you can access the app.config in Visual Studio from the **Solution Explorer**.</span></span> <span data-ttu-id="234cf-110">Jinak název konfiguračního souboru je spolu s ".config" název sestavení a nachází se ve stejném adresáři jako sestavení.</span><span class="sxs-lookup"><span data-stu-id="234cf-110">Otherwise, the configuration file name is the assembly's name appended with ".config", and it is located in the same directory as the assembly.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="234cf-111">Konfigurační soubor obsahuje Ne každé sestavení.</span><span class="sxs-lookup"><span data-stu-id="234cf-111">Not every assembly has a configuration file.</span></span>  
  
     <span data-ttu-id="234cf-112">Konfigurační soubor je soubor XML.</span><span class="sxs-lookup"><span data-stu-id="234cf-112">The configuration file is an XML file.</span></span>  
  
2.  <span data-ttu-id="234cf-113">Vyhledejte `<listeners>` v části `<source>` část s `name` atributu "DefaultSource", umístěný ve `<sources>` části.</span><span class="sxs-lookup"><span data-stu-id="234cf-113">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="234cf-114">`<sources>` Je umístěna v `<system.diagnostics>` oddílem se v nejvyšší úrovně `<configuration>` části.</span><span class="sxs-lookup"><span data-stu-id="234cf-114">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
     <span data-ttu-id="234cf-115">Pokud tyto části nejsou k dispozici, pak může konfigurovat počítače konfigurační soubor `My.Application.Log` protokolu naslouchací procesy.</span><span class="sxs-lookup"><span data-stu-id="234cf-115">If these sections do not exist, then the computer's configuration file may configure the `My.Application.Log` log listeners.</span></span> <span data-ttu-id="234cf-116">Následující kroky popisují, jak zjistit, co definuje konfigurační soubor na počítači:</span><span class="sxs-lookup"><span data-stu-id="234cf-116">The following steps describe how to determine what the computer configuration file defines:</span></span>  
  
    1.  <span data-ttu-id="234cf-117">Vyhledejte souboru machine.config.</span><span class="sxs-lookup"><span data-stu-id="234cf-117">Locate the computer's machine.config file.</span></span> <span data-ttu-id="234cf-118">Obvykle se nachází v *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* adresáře, kde `SystemRoot` je adresář operačního systému a `frameworkVersion` je verze [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="234cf-118">Typically, it is located in the *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* directory, where `SystemRoot` is the operating system directory, and `frameworkVersion` is the version of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
         <span data-ttu-id="234cf-119">Konfigurační soubor aplikace je možné přepsat nastavení v souboru machine.config.</span><span class="sxs-lookup"><span data-stu-id="234cf-119">The settings in machine.config can be overridden by an application's configuration file.</span></span>  
  
         <span data-ttu-id="234cf-120">Pokud nejsou k dispozici níže uvedené volitelné prvky, můžete je vytvořit.</span><span class="sxs-lookup"><span data-stu-id="234cf-120">If the optional elements listed below do not exist, you can create them.</span></span>  
  
    2.  <span data-ttu-id="234cf-121">Vyhledejte `<listeners>` v části `<source>` část s `name` atribut "DefaultSource", `<sources>` v části `<system.diagnostics>` oddílem se v nejvyšší úrovně `<configuration>` části.</span><span class="sxs-lookup"><span data-stu-id="234cf-121">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
         <span data-ttu-id="234cf-122">Pokud tyto části nejsou k dispozici, pak se `My.Application.Log` má pouze výchozí posluchače protokolu.</span><span class="sxs-lookup"><span data-stu-id="234cf-122">If these sections do not exist, then the `My.Application.Log` has only the default log listeners.</span></span>  
  
3.  <span data-ttu-id="234cf-123">Vyhledejte <`add>` elementů v <`listeners>` části.</span><span class="sxs-lookup"><span data-stu-id="234cf-123">Locate the <`add>` elements in the <`listeners>` section.</span></span>  
  
     <span data-ttu-id="234cf-124">Tyto prvky přidejte naslouchací procesy protokolu s názvem na `My.Application.Log` zdroje.</span><span class="sxs-lookup"><span data-stu-id="234cf-124">These elements add the named log listeners to `My.Application.Log` source.</span></span>  
  
4.  <span data-ttu-id="234cf-125">Vyhledejte `<add>` prvků s názvy součástí naslouchajících protokolům v `<sharedListeners>` v části `<system.diagnostics>` oddílem se v nejvyšší úrovně `<configuration>` části.</span><span class="sxs-lookup"><span data-stu-id="234cf-125">Locate the `<add>` elements with the names of the log listeners in the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="234cf-126">Pro mnoho typů sdílené moduly pro naslouchání inicializační data obsahuje popis kde naslouchací proces nasměruje data:</span><span class="sxs-lookup"><span data-stu-id="234cf-126">For many types of shared listeners, the listener's initialization data includes a description of where the listener directs the data:</span></span>  
  
    -   <span data-ttu-id="234cf-127">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> naslouchací proces zapisuje do protokolového souboru, jak je popsáno v zavedení.</span><span class="sxs-lookup"><span data-stu-id="234cf-127">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener writes to a file log, as described in the introduction.</span></span>  
  
    -   <span data-ttu-id="234cf-128">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> naslouchací proces zapisuje informace do protokolu událostí počítače určeného `initializeData` parametr.</span><span class="sxs-lookup"><span data-stu-id="234cf-128">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener writes information to the computer event log specified by the `initializeData` parameter.</span></span> <span data-ttu-id="234cf-129">Chcete-li zobrazit protokol událostí, můžete použít **Průzkumníka serveru** nebo **Prohlížeč událostí systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="234cf-129">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="234cf-130">Další informace najdete v tématu [události trasování událostí pro Windows v rozhraní .NET Framework](../../../../framework/performance/etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="234cf-130">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>  
  
    -   <span data-ttu-id="234cf-131"><xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> a <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> zapisují do souboru určeném v `initializeData` parametr.</span><span class="sxs-lookup"><span data-stu-id="234cf-131">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners write to the file specified in the `initializeData` parameter.</span></span>  
  
    -   <span data-ttu-id="234cf-132">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> naslouchací proces zapisuje do konzoly nástroje příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="234cf-132">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener writes to the command-line console.</span></span>  
  
    -   <span data-ttu-id="234cf-133">Informace o kde jiné typy naslouchací procesy protokolu zapisují informace najdete v dokumentaci daného typu.</span><span class="sxs-lookup"><span data-stu-id="234cf-133">For information about where other types of log listeners write information, consult that type's documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="234cf-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="234cf-134">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.DelimitedListTraceListener>  
 <xref:System.Diagnostics.XmlWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics>  
 [<span data-ttu-id="234cf-135">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="234cf-135">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="234cf-136">Postupy: Protokolování výjimek</span><span class="sxs-lookup"><span data-stu-id="234cf-136">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [<span data-ttu-id="234cf-137">Postupy: Zápis zpráv protokolu</span><span class="sxs-lookup"><span data-stu-id="234cf-137">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [<span data-ttu-id="234cf-138">Návod: Změna místa, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="234cf-138">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 [<span data-ttu-id="234cf-139">Trasování událostí pro Windows – události v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="234cf-139">ETW Events in the .NET Framework</span></span>](../../../../framework/performance/etw-events.md)  
 [<span data-ttu-id="234cf-140">Řešení potíží: Součásti naslouchající protokolům</span><span class="sxs-lookup"><span data-stu-id="234cf-140">Troubleshooting: Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
