---
title: 'Postupy: Zápis do protokolu událostí aplikace'
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: 511bb8fb16851872c1a16ae7627ed0fc6594337c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352051"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a><span data-ttu-id="75db6-102">Postupy: Zápis do protokolu událostí aplikace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75db6-102">How to: Write to an Application Event Log (Visual Basic)</span></span>

<span data-ttu-id="75db6-103">Objekty a `My.Application.Log` `My.Log` můžete použít k zápisu informací o událostech, ke kterým dochází ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="75db6-103">You can use the `My.Application.Log` and `My.Log` objects to write information about events that occur in your application.</span></span> <span data-ttu-id="75db6-104">Tento příklad ukazuje, jak nakonfigurovat `My.Application.Log` naslouchací proces protokolu událostí, takže zapíše informace o trasování do protokolu událostí aplikace.</span><span class="sxs-lookup"><span data-stu-id="75db6-104">This example shows how to configure an event log listener so `My.Application.Log` writes tracing information to the Application event log.</span></span>

<span data-ttu-id="75db6-105">Do protokolu zabezpečení nelze zapisovat.</span><span class="sxs-lookup"><span data-stu-id="75db6-105">You cannot write to the Security log.</span></span> <span data-ttu-id="75db6-106">Chcete-li zapisovat do systémového protokolu, musíte být členem účtu LocalSystem nebo Administrator.</span><span class="sxs-lookup"><span data-stu-id="75db6-106">In order to write to the System log, you must be a member of the LocalSystem or Administrator account.</span></span>

<span data-ttu-id="75db6-107">Chcete-li zobrazit protokol událostí, můžete použít **Průzkumníka serveru** nebo **Prohlížeč událostí systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="75db6-107">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="75db6-108">Další informace naleznete [v tématu ETW Události v rozhraní .NET Framework](../../../../framework/performance/etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="75db6-108">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>

## <a name="to-add-and-configure-the-event-log-listener"></a><span data-ttu-id="75db6-109">Přidání a konfigurace posluchače protokolu událostí</span><span class="sxs-lookup"><span data-stu-id="75db6-109">To add and configure the event log listener</span></span>

1. <span data-ttu-id="75db6-110">Klepněte pravým tlačítkem myši na soubor app.config v **Průzkumníku řešení** a zvolte **Otevřít**.</span><span class="sxs-lookup"><span data-stu-id="75db6-110">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

    <span data-ttu-id="75db6-111">\-nebo -</span><span class="sxs-lookup"><span data-stu-id="75db6-111">\- or -</span></span>

    <span data-ttu-id="75db6-112">Pokud není k dispozici žádný soubor app.config,</span><span class="sxs-lookup"><span data-stu-id="75db6-112">If there is no app.config file,</span></span>

    1. <span data-ttu-id="75db6-113">V nabídce **Projekt** zvolte **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="75db6-113">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="75db6-114">V dialogovém okně **Přidat novou položku** zvolte **Konfigurační soubor aplikace**.</span><span class="sxs-lookup"><span data-stu-id="75db6-114">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="75db6-115">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="75db6-115">Click **Add**.</span></span>

2. <span data-ttu-id="75db6-116">Vyhledejte `<listeners>` oddíl v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="75db6-116">Locate the `<listeners>` section in the application configuration file.</span></span>

    <span data-ttu-id="75db6-117">Oddíl najdete `<listeners>` v `<source>` sekci s atributem název "DefaultSource", který `<system.diagnostics>` je vnořen pod oddíl, který je vnořen pod oddíl nejvyšší úrovně. `<configuration>`</span><span class="sxs-lookup"><span data-stu-id="75db6-117">You will find the `<listeners>` section in the `<source>` section with the name attribute "DefaultSource", which is nested under the `<system.diagnostics>` section, which is nested under the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="75db6-118">Přidejte tento `<listeners>` prvek do tohoto oddílu:</span><span class="sxs-lookup"><span data-stu-id="75db6-118">Add this element to that `<listeners>` section:</span></span>

    ```xml
    <add name="EventLog"/>
    ```

4. <span data-ttu-id="75db6-119">Vyhledejte `<sharedListeners>` oddíl v `<system.diagnostics>` části v části `<configuration>` nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="75db6-119">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="75db6-120">Přidejte tento `<sharedListeners>` prvek do tohoto oddílu:</span><span class="sxs-lookup"><span data-stu-id="75db6-120">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    <span data-ttu-id="75db6-121">Nahraďte `APPLICATION_NAME` název aplikace.</span><span class="sxs-lookup"><span data-stu-id="75db6-121">Replace `APPLICATION_NAME` with the name of your application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="75db6-122">Aplikace obvykle zapisuje pouze chyby do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="75db6-122">Typically, an application writes only errors to the event log.</span></span> <span data-ttu-id="75db6-123">Informace o výstupu protokolu filtrování naleznete [v tématu Návod: Filtrování výstupu my.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="75db6-123">For information on filtering log output, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>

## <a name="to-write-event-information-to-the-event-log"></a><span data-ttu-id="75db6-124">Zápis informací o událostech do protokolu událostí</span><span class="sxs-lookup"><span data-stu-id="75db6-124">To write event information to the event log</span></span>

<span data-ttu-id="75db6-125">Pomocí `My.Application.Log.WriteEntry` metody `My.Application.Log.WriteException` or zapište informace do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="75db6-125">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the event log.</span></span> <span data-ttu-id="75db6-126">Další informace naleznete v [tématu How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="75db6-126">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>

<span data-ttu-id="75db6-127">Po konfiguraci posluchače protokolu událostí pro sestavení obdrží `My.Application.Log` všechny zprávy, které zapisuje z tohoto sestavení.</span><span class="sxs-lookup"><span data-stu-id="75db6-127">After you configure the event log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="75db6-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="75db6-128">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="75db6-129">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="75db6-129">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="75db6-130">Postupy: Protokolování výjimek</span><span class="sxs-lookup"><span data-stu-id="75db6-130">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="75db6-131">Návod: Zjištění, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="75db6-131">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
