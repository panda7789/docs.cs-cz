---
title: "Postupy: Zápis do protokolu událostí aplikace (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8225deaac92b4f375f57501875e13216b35a120d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a><span data-ttu-id="f2b70-102">Postupy: Zápis do protokolu událostí aplikace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2b70-102">How to: Write to an Application Event Log (Visual Basic)</span></span>
<span data-ttu-id="f2b70-103">Můžete použít `My.Application.Log` a `My.Log` objekty při zápisu informací o událostech, ke kterým dochází ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f2b70-103">You can use the `My.Application.Log` and `My.Log` objects to write information about events that occur in your application.</span></span> <span data-ttu-id="f2b70-104">Tento příklad ukazuje postup konfigurace naslouchací proces protokolu událostí, takže `My.Application.Log` informace trasování zapíše do protokolu událostí aplikace.</span><span class="sxs-lookup"><span data-stu-id="f2b70-104">This example shows how to configure an event log listener so `My.Application.Log` writes tracing information to the Application event log.</span></span>  
  
 <span data-ttu-id="f2b70-105">Nelze zapisovat do protokolu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f2b70-105">You cannot write to the Security log.</span></span> <span data-ttu-id="f2b70-106">Aby bylo možné zapsat do systémového protokolu, musí být členem skupiny účet LocalSystem nebo správce.</span><span class="sxs-lookup"><span data-stu-id="f2b70-106">In order to write to the System log, you must be a member of the LocalSystem or Administrator account.</span></span>  
  
 <span data-ttu-id="f2b70-107">Chcete-li zobrazit protokol událostí, můžete použít **Průzkumníka serveru** nebo **Prohlížeč událostí systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="f2b70-107">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="f2b70-108">Další informace najdete v tématu [události trasování událostí pro Windows v rozhraní .NET Framework](../../../../framework/performance/etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="f2b70-108">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2b70-109">Protokoly událostí nejsou podporovány v systému Windows 95, Windows 98 nebo Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="f2b70-109">Event logs are not supported on Windows 95, Windows 98, or Windows Millennium Edition.</span></span>  
  
### <a name="to-add-and-configure-the-event-log-listener"></a><span data-ttu-id="f2b70-110">Přidání a konfigurace naslouchací proces protokolu událostí</span><span class="sxs-lookup"><span data-stu-id="f2b70-110">To add and configure the event log listener</span></span>  
  
1.  <span data-ttu-id="f2b70-111">Klikněte pravým tlačítkem na app.config v **Průzkumníku řešení** a zvolte **otevřete**.</span><span class="sxs-lookup"><span data-stu-id="f2b70-111">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="f2b70-112">\-nebo –</span><span class="sxs-lookup"><span data-stu-id="f2b70-112">\- or -</span></span>  
  
     <span data-ttu-id="f2b70-113">Pokud není dostupný žádný soubor app.config,</span><span class="sxs-lookup"><span data-stu-id="f2b70-113">If there is no app.config file,</span></span>  
  
    1.  <span data-ttu-id="f2b70-114">Na **projektu** nabídce zvolte **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="f2b70-114">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="f2b70-115">Z **přidat novou položku** dialogovém okně vyberte **konfigurační soubor aplikace**.</span><span class="sxs-lookup"><span data-stu-id="f2b70-115">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="f2b70-116">Klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="f2b70-116">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="f2b70-117">Vyhledejte `<listeners>` oddílu v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="f2b70-117">Locate the `<listeners>` section in the application configuration file.</span></span>  
  
     <span data-ttu-id="f2b70-118">Zjistíte, `<listeners>` kapitoly `<source>` části s názvem atributu "DefaultSource", která je vnořená `<system.diagnostics>` oddíl, což je vnořená do nejvyšší úrovně `<configuration>` části.</span><span class="sxs-lookup"><span data-stu-id="f2b70-118">You will find the `<listeners>` section in the `<source>` section with the name attribute "DefaultSource", which is nested under the `<system.diagnostics>` section, which is nested under the top-level `<configuration>` section.</span></span>  
  
3.  <span data-ttu-id="f2b70-119">Přidejte tento element do `<listeners>` části:</span><span class="sxs-lookup"><span data-stu-id="f2b70-119">Add this element to that `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="EventLog"/>  
    ```  
  
4.  <span data-ttu-id="f2b70-120">Vyhledejte `<sharedListeners>` v části `<system.diagnostics>` oddílem se v nejvyšší úrovně `<configuration>` části.</span><span class="sxs-lookup"><span data-stu-id="f2b70-120">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="f2b70-121">Přidejte tento element do `<sharedListeners>` části:</span><span class="sxs-lookup"><span data-stu-id="f2b70-121">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="EventLog"  
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="APPLICATION_NAME"/>  
    ```  
  
     <span data-ttu-id="f2b70-122">Nahraďte `APPLICATION_NAME` s názvem vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="f2b70-122">Replace `APPLICATION_NAME` with the name of your application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f2b70-123">Aplikace obvykle zaznamená pouze chyby do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="f2b70-123">Typically, an application writes only errors to the event log.</span></span> <span data-ttu-id="f2b70-124">Informace o filtrování výstupu protokolu najdete v tématu [návod: filtrování výstupu My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="f2b70-124">For information on filtering log output, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>  
  
### <a name="to-write-event-information-to-the-event-log"></a><span data-ttu-id="f2b70-125">Zápis informací o události do protokolu událostí</span><span class="sxs-lookup"><span data-stu-id="f2b70-125">To write event information to the event log</span></span>  
  
-   <span data-ttu-id="f2b70-126">Použití `My.Application.Log.WriteEntry` nebo `My.Application.Log.WriteException` metoda při zápisu informací do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="f2b70-126">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the event log.</span></span> <span data-ttu-id="f2b70-127">Další informace najdete v tématu [postupy: zápis zpráv protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) a [postup: výjimky protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="f2b70-127">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>  
  
     <span data-ttu-id="f2b70-128">Po dokončení konfigurace naslouchací proces protokolu událostí pro sestavení, obdrží všechny zprávy, která `My.Applcation.Log` zapíše z tohoto sestavení.</span><span class="sxs-lookup"><span data-stu-id="f2b70-128">After you configure the event log listener for an assembly, it receives all messages that `My.Applcation.Log` writes from that assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2b70-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2b70-129">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [<span data-ttu-id="f2b70-130">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="f2b70-130">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="f2b70-131">Postupy: Protokolování výjimek</span><span class="sxs-lookup"><span data-stu-id="f2b70-131">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [<span data-ttu-id="f2b70-132">Návod: Zjištění, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="f2b70-132">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
