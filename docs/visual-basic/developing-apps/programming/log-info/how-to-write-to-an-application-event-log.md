---
title: 'Postupy: Zápis do protokolu událostí aplikace (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: c3c7d350132ee6c891633141fc5c4b280989e77f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366501"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a><span data-ttu-id="abf2d-102">Postupy: Zápis do protokolu událostí aplikace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="abf2d-102">How to: Write to an Application Event Log (Visual Basic)</span></span>

<span data-ttu-id="abf2d-103">Můžete použít `My.Application.Log` a `My.Log` objekty při zápisu informací o událostech, ke kterým dochází ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="abf2d-103">You can use the `My.Application.Log` and `My.Log` objects to write information about events that occur in your application.</span></span> <span data-ttu-id="abf2d-104">Tento příklad ukazuje, jak konfigurace naslouchacího procesu protokolu událostí tak `My.Application.Log` informace trasování zapíše do protokolu událostí aplikace.</span><span class="sxs-lookup"><span data-stu-id="abf2d-104">This example shows how to configure an event log listener so `My.Application.Log` writes tracing information to the Application event log.</span></span>

<span data-ttu-id="abf2d-105">Nelze zapisovat do protokolu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="abf2d-105">You cannot write to the Security log.</span></span> <span data-ttu-id="abf2d-106">Aby bylo možné zapsat do systémového protokolu, musí být členem účtu LocalSystem nebo správce.</span><span class="sxs-lookup"><span data-stu-id="abf2d-106">In order to write to the System log, you must be a member of the LocalSystem or Administrator account.</span></span>

<span data-ttu-id="abf2d-107">Chcete-li zobrazit protokol událostí, můžete použít **Průzkumníka serveru** nebo **Prohlížeč událostí Windows**.</span><span class="sxs-lookup"><span data-stu-id="abf2d-107">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="abf2d-108">Další informace najdete v tématu [události trasování událostí pro Windows v rozhraní .NET Framework](../../../../framework/performance/etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="abf2d-108">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>

### <a name="to-add-and-configure-the-event-log-listener"></a><span data-ttu-id="abf2d-109">Přidání a konfigurace naslouchacího procesu protokolu událostí</span><span class="sxs-lookup"><span data-stu-id="abf2d-109">To add and configure the event log listener</span></span>

1. <span data-ttu-id="abf2d-110">Klikněte pravým tlačítkem na app.config **Průzkumníka řešení** a zvolte **otevřít**.</span><span class="sxs-lookup"><span data-stu-id="abf2d-110">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

    <span data-ttu-id="abf2d-111">\- nebo –</span><span class="sxs-lookup"><span data-stu-id="abf2d-111">\- or -</span></span>

    <span data-ttu-id="abf2d-112">Pokud neexistuje žádný soubor app.config</span><span class="sxs-lookup"><span data-stu-id="abf2d-112">If there is no app.config file,</span></span>

    1. <span data-ttu-id="abf2d-113">Na **projektu** nabídce zvolte **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="abf2d-113">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="abf2d-114">Z **přidat novou položku** dialogového okna zvolte **konfiguračního souboru aplikace**.</span><span class="sxs-lookup"><span data-stu-id="abf2d-114">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="abf2d-115">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="abf2d-115">Click **Add**.</span></span>

2. <span data-ttu-id="abf2d-116">Vyhledejte `<listeners>` oddílu v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="abf2d-116">Locate the `<listeners>` section in the application configuration file.</span></span>

    <span data-ttu-id="abf2d-117">Vás bude `<listeners>` tématu `<source>` část s atributem name "DefaultSource", která je vnořená v rámci `<system.diagnostics>` oddíl, což je vnořený na nejvyšší úrovni `<configuration>` části.</span><span class="sxs-lookup"><span data-stu-id="abf2d-117">You will find the `<listeners>` section in the `<source>` section with the name attribute "DefaultSource", which is nested under the `<system.diagnostics>` section, which is nested under the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="abf2d-118">Přidejte tento element, který `<listeners>` části:</span><span class="sxs-lookup"><span data-stu-id="abf2d-118">Add this element to that `<listeners>` section:</span></span>

    ```xml
    <add name="EventLog"/>
    ```

4. <span data-ttu-id="abf2d-119">Vyhledejte `<sharedListeners>` sekci `<system.diagnostics>` části na nejvyšší úrovni `<configuration>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="abf2d-119">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="abf2d-120">Přidejte tento element, který `<sharedListeners>` části:</span><span class="sxs-lookup"><span data-stu-id="abf2d-120">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    <span data-ttu-id="abf2d-121">Nahraďte `APPLICATION_NAME` s názvem vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="abf2d-121">Replace `APPLICATION_NAME` with the name of your application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="abf2d-122">Aplikace obvykle zapisuje pouze chyby do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="abf2d-122">Typically, an application writes only errors to the event log.</span></span> <span data-ttu-id="abf2d-123">Informace o filtrování výstupu protokolu najdete v tématu [názorný postup: Filtrování výstupu My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="abf2d-123">For information on filtering log output, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>

### <a name="to-write-event-information-to-the-event-log"></a><span data-ttu-id="abf2d-124">Zápis informací o události do protokolu událostí</span><span class="sxs-lookup"><span data-stu-id="abf2d-124">To write event information to the event log</span></span>

- <span data-ttu-id="abf2d-125">Použití `My.Application.Log.WriteEntry` nebo `My.Application.Log.WriteException` metoda při zápisu informací do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="abf2d-125">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the event log.</span></span> <span data-ttu-id="abf2d-126">Další informace najdete v tématu [jak: Zápis zpráv protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) a [jak: Protokolování výjimek](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="abf2d-126">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>

    <span data-ttu-id="abf2d-127">Po dokončení konfigurace naslouchacího procesu protokolu událostí pro sestavení přijímá všechny zprávy, které `My.Application.Log` zapíše z tohoto sestavení.</span><span class="sxs-lookup"><span data-stu-id="abf2d-127">After you configure the event log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="abf2d-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="abf2d-128">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="abf2d-129">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="abf2d-129">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="abf2d-130">Postupy: Výjimky protokolu</span><span class="sxs-lookup"><span data-stu-id="abf2d-130">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="abf2d-131">Návod: Určení, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="abf2d-131">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
