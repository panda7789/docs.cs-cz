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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352051"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a><span data-ttu-id="655ed-102">Postupy: Zápis do protokolu událostí aplikace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="655ed-102">How to: Write to an Application Event Log (Visual Basic)</span></span>

<span data-ttu-id="655ed-103">Objekty `My.Application.Log` a `My.Log` lze použít k zápisu informací o událostech, ke kterým dojde v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="655ed-103">You can use the `My.Application.Log` and `My.Log` objects to write information about events that occur in your application.</span></span> <span data-ttu-id="655ed-104">Tento příklad ukazuje, jak nakonfigurovat naslouchací proces protokolu událostí tak, `My.Application.Log` zapisuje trasovací informace do protokolu událostí aplikace.</span><span class="sxs-lookup"><span data-stu-id="655ed-104">This example shows how to configure an event log listener so `My.Application.Log` writes tracing information to the Application event log.</span></span>

<span data-ttu-id="655ed-105">Do protokolu zabezpečení nelze zapisovat.</span><span class="sxs-lookup"><span data-stu-id="655ed-105">You cannot write to the Security log.</span></span> <span data-ttu-id="655ed-106">Aby bylo možné zapisovat do systémového protokolu, musíte být členem účtu LocalSystem nebo správce.</span><span class="sxs-lookup"><span data-stu-id="655ed-106">In order to write to the System log, you must be a member of the LocalSystem or Administrator account.</span></span>

<span data-ttu-id="655ed-107">Chcete-li zobrazit protokol událostí, můžete použít **Průzkumník serveru** nebo **Windows Prohlížeč událostí**.</span><span class="sxs-lookup"><span data-stu-id="655ed-107">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="655ed-108">Další informace najdete v tématu [události ETW v .NET Framework](../../../../framework/performance/etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="655ed-108">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>

## <a name="to-add-and-configure-the-event-log-listener"></a><span data-ttu-id="655ed-109">Přidání a konfigurace naslouchacího procesu protokolu událostí</span><span class="sxs-lookup"><span data-stu-id="655ed-109">To add and configure the event log listener</span></span>

1. <span data-ttu-id="655ed-110">V **Průzkumník řešení** klikněte pravým tlačítkem na soubor App. config a vyberte **otevřít**.</span><span class="sxs-lookup"><span data-stu-id="655ed-110">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

    <span data-ttu-id="655ed-111">\- nebo-</span><span class="sxs-lookup"><span data-stu-id="655ed-111">\- or -</span></span>

    <span data-ttu-id="655ed-112">Pokud soubor App. config neexistuje,</span><span class="sxs-lookup"><span data-stu-id="655ed-112">If there is no app.config file,</span></span>

    1. <span data-ttu-id="655ed-113">V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="655ed-113">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="655ed-114">V dialogovém okně **Přidat novou položku** vyberte možnost **konfigurační soubor aplikace**.</span><span class="sxs-lookup"><span data-stu-id="655ed-114">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="655ed-115">Klikněte na tlačítko **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="655ed-115">Click **Add**.</span></span>

2. <span data-ttu-id="655ed-116">V konfiguračním souboru aplikace vyhledejte část `<listeners>`.</span><span class="sxs-lookup"><span data-stu-id="655ed-116">Locate the `<listeners>` section in the application configuration file.</span></span>

    <span data-ttu-id="655ed-117">Část `<listeners>` najdete v části `<source>` s názvem "DefaultSource", který je vnořen do oddílu `<system.diagnostics>`, který je vnořený pod oddílem `<configuration>` nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="655ed-117">You will find the `<listeners>` section in the `<source>` section with the name attribute "DefaultSource", which is nested under the `<system.diagnostics>` section, which is nested under the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="655ed-118">Přidejte tento prvek do tohoto `<listeners>` části:</span><span class="sxs-lookup"><span data-stu-id="655ed-118">Add this element to that `<listeners>` section:</span></span>

    ```xml
    <add name="EventLog"/>
    ```

4. <span data-ttu-id="655ed-119">Vyhledejte část `<sharedListeners>` v části `<system.diagnostics>` v části `<configuration>` nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="655ed-119">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="655ed-120">Přidejte tento prvek do tohoto `<sharedListeners>` části:</span><span class="sxs-lookup"><span data-stu-id="655ed-120">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    <span data-ttu-id="655ed-121">Nahraďte `APPLICATION_NAME` názvem vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="655ed-121">Replace `APPLICATION_NAME` with the name of your application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="655ed-122">Aplikace obvykle zapisuje pouze chyby do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="655ed-122">Typically, an application writes only errors to the event log.</span></span> <span data-ttu-id="655ed-123">Informace o filtrování výstupu protokolu naleznete v tématu [Návod: filtrování výstupu my. Application. log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="655ed-123">For information on filtering log output, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>

## <a name="to-write-event-information-to-the-event-log"></a><span data-ttu-id="655ed-124">Zápis informací o události do protokolu událostí</span><span class="sxs-lookup"><span data-stu-id="655ed-124">To write event information to the event log</span></span>

<span data-ttu-id="655ed-125">Pomocí metody `My.Application.Log.WriteEntry` nebo `My.Application.Log.WriteException` zapište informace do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="655ed-125">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the event log.</span></span> <span data-ttu-id="655ed-126">Další informace naleznete v tématu [How to: Write log messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [to: log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="655ed-126">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>

<span data-ttu-id="655ed-127">Po nakonfigurování naslouchacího procesu protokolu událostí pro sestavení obdrží všechny zprávy, které `My.Application.Log` zápisy z tohoto sestavení.</span><span class="sxs-lookup"><span data-stu-id="655ed-127">After you configure the event log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="655ed-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="655ed-128">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="655ed-129">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="655ed-129">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="655ed-130">Postupy: Protokolování výjimek</span><span class="sxs-lookup"><span data-stu-id="655ed-130">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="655ed-131">Návod: Zjištění, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="655ed-131">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
