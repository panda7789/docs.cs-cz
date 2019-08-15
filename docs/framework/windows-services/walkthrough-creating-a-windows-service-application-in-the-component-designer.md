---
title: 'Kurz: Vytvoření aplikace služby systému Windows'
ms.date: 03/27/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows service applications, walkthroughs
- Windows service applications, creating
ms.assetid: e24d8a3d-edc6-485c-b6e0-5672d91fb607
author: ghogen
ms.openlocfilehash: fda64cd15e15fb437db415b8a8083829c2d773cb
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039868"
---
# <a name="tutorial-create-a-windows-service-app"></a><span data-ttu-id="5ba90-102">Kurz: Vytvoření aplikace služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="5ba90-102">Tutorial: Create a Windows service app</span></span>

<span data-ttu-id="5ba90-103">Tento článek ukazuje, jak vytvořit aplikaci služby systému Windows v aplikaci Visual Studio, která zapisuje zprávy do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="5ba90-103">This article demonstrates how to create a Windows service app in Visual Studio that writes messages to an event log.</span></span>

## <a name="create-a-service"></a><span data-ttu-id="5ba90-104">Vytvoření služby</span><span class="sxs-lookup"><span data-stu-id="5ba90-104">Create a service</span></span>

<span data-ttu-id="5ba90-105">Začněte tím, že vytvoříte projekt a nastavíte hodnoty požadované pro správné fungování služby.</span><span class="sxs-lookup"><span data-stu-id="5ba90-105">To begin, create the project and set the values that are required for the service to function correctly.</span></span>

1. <span data-ttu-id="5ba90-106">V nabídce **soubor** v aplikaci Visual Studio vyberte **Nový** > **projekt** (nebo stiskněte klávesy **CTRL**+**SHIFT**+**N**) a otevřete tak okno **Nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="5ba90-106">From the Visual Studio **File** menu, select **New** > **Project** (or press **Ctrl**+**Shift**+**N**) to open the **New Project** window.</span></span>

2. <span data-ttu-id="5ba90-107">Přejděte na a vyberte šablonu projektu **služba systému Windows (.NET Framework)** .</span><span class="sxs-lookup"><span data-stu-id="5ba90-107">Navigate to and select the **Windows Service (.NET Framework)** project template.</span></span> <span data-ttu-id="5ba90-108">Pokud ho chcete najít, rozbalte položku **nainstalované** a **vizuál C#**  nebo **Visual Basic**a pak vyberte **Desktop Windows**.</span><span class="sxs-lookup"><span data-stu-id="5ba90-108">To find it, expand **Installed** and **Visual C#** or **Visual Basic**, then select **Windows Desktop**.</span></span> <span data-ttu-id="5ba90-109">Případně zadejte do vyhledávacího pole v pravém horním rohu *službu Windows* a stiskněte klávesu **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="5ba90-109">Or, enter *Windows Service* in the search box on the upper right and press **Enter**.</span></span>

   ![Šablona služby systému Windows v dialogovém okně Nový projekt v aplikaci Visual Studio](media/new-project-dialog.png)

   > [!NOTE]
   > <span data-ttu-id="5ba90-111">Pokud nevidíte šablonu **služby systému Windows** , bude pravděpodobně nutné nainstalovat úlohu **vývoj desktopových** aplikací pro .NET:</span><span class="sxs-lookup"><span data-stu-id="5ba90-111">If you don't see the **Windows Service** template, you may need to install the **.NET desktop development** workload:</span></span>
   >
   > <span data-ttu-id="5ba90-112">V dialogovém okně **Nový projekt** vyberte v levém dolním rohu **otevřít instalační program pro Visual Studio** .</span><span class="sxs-lookup"><span data-stu-id="5ba90-112">In the **New Project** dialog, select **Open Visual Studio Installer** on the lower left.</span></span> <span data-ttu-id="5ba90-113">Vyberte úlohu **vývoj desktopových aplikací .NET** a pak vyberte **Upravit**.</span><span class="sxs-lookup"><span data-stu-id="5ba90-113">Select the **.NET desktop development** workload, and then select **Modify**.</span></span>

3. <span data-ttu-id="5ba90-114">Jako **název**zadejte *MyNewService*a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="5ba90-114">For **Name**, enter *MyNewService*, and then select **OK**.</span></span>

   <span data-ttu-id="5ba90-115">Zobrazí se karta **Návrh** (**Service1.cs [Design]** nebo **Service1. vb [Design]** ).</span><span class="sxs-lookup"><span data-stu-id="5ba90-115">The **Design** tab appears (**Service1.cs [Design]** or **Service1.vb [Design]**).</span></span>

   <span data-ttu-id="5ba90-116">Šablona projektu obsahuje třídu komponenty s názvem `Service1` , která dědí z. <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5ba90-116">The project template includes a component class named `Service1` that inherits from <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5ba90-117">Zahrnuje většinu základního kódu služby, jako je například kód pro spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="5ba90-117">It includes much of the basic service code, such as the code to start the service.</span></span>

## <a name="rename-the-service"></a><span data-ttu-id="5ba90-118">Přejmenování služby</span><span class="sxs-lookup"><span data-stu-id="5ba90-118">Rename the service</span></span>

<span data-ttu-id="5ba90-119">Přejmenujte službu z **Service1** na **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="5ba90-119">Rename the service from **Service1** to **MyNewService**.</span></span>

1. <span data-ttu-id="5ba90-120">V **Průzkumník řešení**vyberte **Service1.cs**nebo **Service1. vb**a zvolte **Přejmenovat** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="5ba90-120">In **Solution Explorer**, select **Service1.cs**, or **Service1.vb**, and choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="5ba90-121">Přejmenujte soubor na **MyNewService.cs**nebo **MyNewService. vb**a potom stiskněte klávesu **ENTER** .</span><span class="sxs-lookup"><span data-stu-id="5ba90-121">Rename the file to **MyNewService.cs**, or **MyNewService.vb**, and then press **Enter**</span></span>

    <span data-ttu-id="5ba90-122">Automaticky otevírané okno se zobrazí dotaz, zda byste chtěli přejmenovat všechny odkazy na prvek kódu *Service1*.</span><span class="sxs-lookup"><span data-stu-id="5ba90-122">A pop-up window appears asking whether you would like to rename all references to the code element *Service1*.</span></span>

2. <span data-ttu-id="5ba90-123">V místním okně vyberte **Ano**.</span><span class="sxs-lookup"><span data-stu-id="5ba90-123">In the pop-up window, select **Yes**.</span></span>

    <span data-ttu-id="5ba90-124">![Přejmenovat výzvu](media/windows-service-rename.png "Výzva k přejmenování služby systému Windows")</span><span class="sxs-lookup"><span data-stu-id="5ba90-124">![Rename prompt](media/windows-service-rename.png "Windows service rename prompt")</span></span>

3. <span data-ttu-id="5ba90-125">Na kartě **Návrh** v místní nabídce vyberte možnost **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="5ba90-125">In the **Design** tab, select **Properties** from the shortcut menu.</span></span> <span data-ttu-id="5ba90-126">V okně **vlastnosti** změňte hodnotu **ServiceName** na *MyNewService*.</span><span class="sxs-lookup"><span data-stu-id="5ba90-126">From the **Properties** window, change the **ServiceName** value to *MyNewService*.</span></span>

    <span data-ttu-id="5ba90-127">![Vlastnosti služby](media/windows-service-properties.png "Vlastnosti služby systému Windows")</span><span class="sxs-lookup"><span data-stu-id="5ba90-127">![Service properties](media/windows-service-properties.png "Windows service properties")</span></span>

4. <span data-ttu-id="5ba90-128">V nabídce **soubor** vyberte **Uložit vše** .</span><span class="sxs-lookup"><span data-stu-id="5ba90-128">Select **Save All** from the **File** menu.</span></span>

## <a name="add-features-to-the-service"></a><span data-ttu-id="5ba90-129">Přidání funkcí do služby</span><span class="sxs-lookup"><span data-stu-id="5ba90-129">Add features to the service</span></span>

<span data-ttu-id="5ba90-130">V této části přidáte do služby systému Windows vlastní protokol událostí.</span><span class="sxs-lookup"><span data-stu-id="5ba90-130">In this section, you add a custom event log to the Windows service.</span></span> <span data-ttu-id="5ba90-131"><xref:System.Diagnostics.EventLog> Komponenta je příkladem typu komponenty, kterou můžete přidat do služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5ba90-131">The <xref:System.Diagnostics.EventLog> component is an example of the type of component you can add to a Windows service.</span></span>

### <a name="add-custom-event-log-functionality"></a><span data-ttu-id="5ba90-132">Přidání funkce vlastního protokolu událostí</span><span class="sxs-lookup"><span data-stu-id="5ba90-132">Add custom event log functionality</span></span>

1. <span data-ttu-id="5ba90-133">V **Průzkumník řešení**v místní nabídce pro **MyNewService.cs**nebo **MyNewService. vb**vyberte možnost **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="5ba90-133">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Designer**.</span></span>

2. <span data-ttu-id="5ba90-134">V **sadě nástrojů**rozbalte položku **součásti**a přetáhněte komponentu **EventLog** na kartu **Service1.cs [Design]** nebo **Service1. vb [Design]** .</span><span class="sxs-lookup"><span data-stu-id="5ba90-134">In **Toolbox**, expand **Components**, and then drag the **EventLog** component to the **Service1.cs [Design]**, or **Service1.vb [Design]** tab.</span></span>

3. <span data-ttu-id="5ba90-135">V **Průzkumník řešení**v místní nabídce pro **MyNewService.cs**nebo **MyNewService. vb**vyberte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="5ba90-135">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Code**.</span></span>

4. <span data-ttu-id="5ba90-136">Definujte vlastní protokol událostí.</span><span class="sxs-lookup"><span data-stu-id="5ba90-136">Define a custom event log.</span></span> <span data-ttu-id="5ba90-137">Pro C#, upravte existující `MyNewService()` konstruktor; pro `New()` Visual Basic přidejte konstruktor:</span><span class="sxs-lookup"><span data-stu-id="5ba90-137">For C#, edit the existing `MyNewService()` constructor; for Visual Basic, add the `New()` constructor:</span></span>

   [!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#2)]
   [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]

5. <span data-ttu-id="5ba90-138">`Imports` <xref:System.Diagnostics?displayProperty=nameWithType>Přidejte příkaz do MyNewService.cs (Pokud ještě neexistuje) nebo příkaz MyNewService. vb pro obor názvů: `using`</span><span class="sxs-lookup"><span data-stu-id="5ba90-138">Add a `using` statement to **MyNewService.cs** (if it doesn't already exist), or an `Imports` statement **MyNewService.vb**, for the <xref:System.Diagnostics?displayProperty=nameWithType> namespace:</span></span>

    ```csharp
    using System.Diagnostics;
    ```

    ```vb
    Imports System.Diagnostics
    ```

6. <span data-ttu-id="5ba90-139">V nabídce **soubor** vyberte **Uložit vše** .</span><span class="sxs-lookup"><span data-stu-id="5ba90-139">Select **Save All** from the **File** menu.</span></span>

### <a name="define-what-occurs-when-the-service-starts"></a><span data-ttu-id="5ba90-140">Definujte, co se stane při spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="5ba90-140">Define what occurs when the service starts</span></span>

<span data-ttu-id="5ba90-141">V editoru kódu pro **MyNewService.cs** nebo **MyNewService. vb**vyhledejte <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodu; Visual Studio automaticky vytvořilo prázdnou definici metody při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="5ba90-141">In the code editor for **MyNewService.cs** or **MyNewService.vb**, locate the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method; Visual Studio automatically created an empty method definition when you created the project.</span></span> <span data-ttu-id="5ba90-142">Přidejte kód, který při spuštění služby zapíše záznam do protokolu událostí:</span><span class="sxs-lookup"><span data-stu-id="5ba90-142">Add code that writes an entry to the event log when the service starts:</span></span>

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

#### <a name="polling"></a><span data-ttu-id="5ba90-143">Dotazování</span><span class="sxs-lookup"><span data-stu-id="5ba90-143">Polling</span></span>

<span data-ttu-id="5ba90-144">Vzhledem k tomu, že je aplikace služby navržena jako dlouhodobá, obvykle se dotazuje nebo monitoruje systém, který jste nastavili v <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodě.</span><span class="sxs-lookup"><span data-stu-id="5ba90-144">Because a service application is designed to be long-running, it usually polls or monitors the system, which you set up in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span> <span data-ttu-id="5ba90-145">`OnStart` Metoda se musí vrátit k operačnímu systému po zahájení operace služby, aby systém nebyl zablokován.</span><span class="sxs-lookup"><span data-stu-id="5ba90-145">The `OnStart` method must return to the operating system after the service's operation has begun so that the system isn't blocked.</span></span>

<span data-ttu-id="5ba90-146">K nastavení jednoduchého mechanismu cyklického dotazování použijte <xref:System.Timers.Timer?displayProperty=nameWithType> komponentu.</span><span class="sxs-lookup"><span data-stu-id="5ba90-146">To set up a simple polling mechanism, use the <xref:System.Timers.Timer?displayProperty=nameWithType> component.</span></span> <span data-ttu-id="5ba90-147">Časovač vyvolá <xref:System.Timers.Timer.Elapsed> událost v pravidelných intervalech, kdy služba může provádět její monitorování.</span><span class="sxs-lookup"><span data-stu-id="5ba90-147">The timer raises an <xref:System.Timers.Timer.Elapsed> event at regular intervals, at which time your service can do its monitoring.</span></span> <span data-ttu-id="5ba90-148"><xref:System.Timers.Timer> Komponentu můžete použít následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="5ba90-148">You use the <xref:System.Timers.Timer> component as follows:</span></span>

- <span data-ttu-id="5ba90-149">Nastavte vlastnosti <xref:System.Timers.Timer> komponenty `MyNewService.OnStart` v metodě.</span><span class="sxs-lookup"><span data-stu-id="5ba90-149">Set the properties of the <xref:System.Timers.Timer> component in the `MyNewService.OnStart` method.</span></span>
- <span data-ttu-id="5ba90-150">Spusťte časovač voláním <xref:System.Timers.Timer.Start%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5ba90-150">Start the timer by calling the <xref:System.Timers.Timer.Start%2A> method.</span></span>

##### <a name="set-up-the-polling-mechanism"></a><span data-ttu-id="5ba90-151">Nastavte mechanismus cyklického dotazování.</span><span class="sxs-lookup"><span data-stu-id="5ba90-151">Set up the polling mechanism.</span></span>

1. <span data-ttu-id="5ba90-152">Přidejte následující kód `MyNewService.OnStart` do události pro nastavení mechanismu cyklického dotazování:</span><span class="sxs-lookup"><span data-stu-id="5ba90-152">Add the following code in the `MyNewService.OnStart` event to set up the polling mechanism:</span></span>

   ```csharp
   // Set up a timer that triggers every minute.
   Timer timer = new Timer();
   timer.Interval = 60000; // 60 seconds
   timer.Elapsed += new ElapsedEventHandler(this.OnTimer);
   timer.Start();
   ```

   ```vb
   ' Set up a timer that triggers every minute.
   Dim timer As Timer = New Timer()
   timer.Interval = 60000 ' 60 seconds
   AddHandler timer.Elapsed, AddressOf Me.OnTimer
   timer.Start()
   ```

2. <span data-ttu-id="5ba90-153">`Imports` Přidejtepříkazdo<xref:System.Timers?displayProperty=nameWithType> MyNewService.cs nebo příkaz do **MyNewService. vb**pro obor názvů: `using`</span><span class="sxs-lookup"><span data-stu-id="5ba90-153">Add a `using` statement to **MyNewService.cs**, or an `Imports` statement to **MyNewService.vb**, for the <xref:System.Timers?displayProperty=nameWithType> namespace:</span></span>

   ```csharp
   using System.Timers;
   ```

   ```vb
   Imports System.Timers
   ```

3. <span data-ttu-id="5ba90-154">Do třídy přidejte metodu pro zpracování <xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType> události: `OnTimer` `MyNewService`</span><span class="sxs-lookup"><span data-stu-id="5ba90-154">In the `MyNewService` class, add the `OnTimer` method to handle the <xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType> event:</span></span>

   ```csharp
   public void OnTimer(object sender, ElapsedEventArgs args)
   {
       // TODO: Insert monitoring activities here.
       eventLog1.WriteEntry("Monitoring the System", EventLogEntryType.Information, eventId++);
   }
   ```

   ```vb
   Private Sub OnTimer(sender As Object, e As Timers.ElapsedEventArgs)
      ' TODO: Insert monitoring activities here.
      eventLog1.WriteEntry("Monitoring the System", EventLogEntryType.Information, eventId)
      eventId = eventId + 1
   End Sub
   ```

4. <span data-ttu-id="5ba90-155">`MyNewService` Ve třídě přidejte členskou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="5ba90-155">In the `MyNewService` class, add a member variable.</span></span> <span data-ttu-id="5ba90-156">Obsahuje identifikátor další události, která má být zapsána do protokolu událostí:</span><span class="sxs-lookup"><span data-stu-id="5ba90-156">It contains the identifier of the next event to write into the event log:</span></span>

   ```csharp
   private int eventId = 1;
   ```

   ```vb
   Private eventId As Integer = 1
   ```

<span data-ttu-id="5ba90-157">Místo spuštění veškeré práce v hlavním vlákně můžete spouštět úlohy pomocí pracovních vláken na pozadí.</span><span class="sxs-lookup"><span data-stu-id="5ba90-157">Instead of running all your work on the main thread, you can run tasks by using background worker threads.</span></span> <span data-ttu-id="5ba90-158">Další informace naleznete v tématu <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="5ba90-158">For more information, see <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span></span>

### <a name="define-what-occurs-when-the-service-is-stopped"></a><span data-ttu-id="5ba90-159">Definujte, co se stane, když se služba zastaví.</span><span class="sxs-lookup"><span data-stu-id="5ba90-159">Define what occurs when the service is stopped</span></span>

<span data-ttu-id="5ba90-160">Vložte řádek kódu do <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody, která po zastavení služby přidá záznam do protokolu událostí:</span><span class="sxs-lookup"><span data-stu-id="5ba90-160">Insert a line of code in the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method that adds an entry to the event log when the service is stopped:</span></span>

[!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#4)]
[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a><span data-ttu-id="5ba90-161">Definování dalších akcí služby</span><span class="sxs-lookup"><span data-stu-id="5ba90-161">Define other actions for the service</span></span>

<span data-ttu-id="5ba90-162">Můžete přepsat <xref:System.ServiceProcess.ServiceBase.OnPause%2A>metody, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>a <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> pro definování dalšího zpracování pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="5ba90-162">You can override the <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, and <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> methods to define additional processing for your component.</span></span>

<span data-ttu-id="5ba90-163">Následující kód ukazuje, jak přepsat <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> metodu `MyNewService` ve třídě:</span><span class="sxs-lookup"><span data-stu-id="5ba90-163">The following code shows how you to override the <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> method in the `MyNewService` class:</span></span>

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]

## <a name="set-service-status"></a><span data-ttu-id="5ba90-164">Nastavit stav služby</span><span class="sxs-lookup"><span data-stu-id="5ba90-164">Set service status</span></span>

<span data-ttu-id="5ba90-165">Služba oznámí jejich stav [Správci řízení služeb](/windows/desktop/Services/service-control-manager) , aby uživatel mohl zjistit, jestli služba funguje správně.</span><span class="sxs-lookup"><span data-stu-id="5ba90-165">Services report their status to the [Service Control Manager](/windows/desktop/Services/service-control-manager) so that a user can tell whether a service is functioning correctly.</span></span> <span data-ttu-id="5ba90-166">Ve výchozím nastavení služba, která dědí z <xref:System.ServiceProcess.ServiceBase> , hlásí omezené sady nastavení stavu, mezi které patří SERVICE_STOPPED, SERVICE_PAUSED a SERVICE_RUNNING.</span><span class="sxs-lookup"><span data-stu-id="5ba90-166">By default, a service that inherits from <xref:System.ServiceProcess.ServiceBase> reports a limited set of status settings, which include SERVICE_STOPPED, SERVICE_PAUSED, and SERVICE_RUNNING.</span></span> <span data-ttu-id="5ba90-167">Pokud se služba začne spouštět, je vhodné ohlásit stav SERVICE_START_PENDING.</span><span class="sxs-lookup"><span data-stu-id="5ba90-167">If a service takes a while to start up, it's useful to report a SERVICE_START_PENDING status.</span></span>

<span data-ttu-id="5ba90-168">Nastavení stavu SERVICE_START_PENDING a SERVICE_STOP_PENDING můžete implementovat přidáním kódu, který volá funkci Windows [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) .</span><span class="sxs-lookup"><span data-stu-id="5ba90-168">You can implement the SERVICE_START_PENDING and SERVICE_STOP_PENDING status settings by adding code that calls the Windows [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) function.</span></span>

### <a name="implement-service-pending-status"></a><span data-ttu-id="5ba90-169">Implementovat stav nedokončené služby</span><span class="sxs-lookup"><span data-stu-id="5ba90-169">Implement service pending status</span></span>

1. <span data-ttu-id="5ba90-170">`Imports` Přidejtepříkazdo<xref:System.Runtime.InteropServices?displayProperty=nameWithType> MyNewService.cs nebo příkaz do **MyNewService. vb**pro obor názvů: `using`</span><span class="sxs-lookup"><span data-stu-id="5ba90-170">Add a `using` statement to **MyNewService.cs**, or an `Imports` statement to **MyNewService.vb**, for the <xref:System.Runtime.InteropServices?displayProperty=nameWithType> namespace:</span></span>

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. <span data-ttu-id="5ba90-171">Přidejte následující kód do **MyNewService.cs**nebo **MyNewService. vb** `ServiceState` pro deklaraci hodnoty a pro přidání struktury pro stav, který použijete v volání vyvolání platformy:</span><span class="sxs-lookup"><span data-stu-id="5ba90-171">Add the following code to **MyNewService.cs**, or **MyNewService.vb**, to declare the `ServiceState` values and to add a structure for the status, which you'll use in a platform invoke call:</span></span>

    ```csharp
    public enum ServiceState
    {
        SERVICE_STOPPED = 0x00000001,
        SERVICE_START_PENDING = 0x00000002,
        SERVICE_STOP_PENDING = 0x00000003,
        SERVICE_RUNNING = 0x00000004,
        SERVICE_CONTINUE_PENDING = 0x00000005,
        SERVICE_PAUSE_PENDING = 0x00000006,
        SERVICE_PAUSED = 0x00000007,
    }

    [StructLayout(LayoutKind.Sequential)]
    public struct ServiceStatus
    {
        public int dwServiceType;
        public ServiceState dwCurrentState;
        public int dwControlsAccepted;
        public int dwWin32ExitCode;
        public int dwServiceSpecificExitCode;
        public int dwCheckPoint;
        public int dwWaitHint;
    };
    ```

    ```vb
    Public Enum ServiceState
        SERVICE_STOPPED = 1
        SERVICE_START_PENDING = 2
        SERVICE_STOP_PENDING = 3
        SERVICE_RUNNING = 4
        SERVICE_CONTINUE_PENDING = 5
        SERVICE_PAUSE_PENDING = 6
        SERVICE_PAUSED = 7
    End Enum

    <StructLayout(LayoutKind.Sequential)>
    Public Structure ServiceStatus
        Public dwServiceType As Long
        Public dwCurrentState As ServiceState
        Public dwControlsAccepted As Long
        Public dwWin32ExitCode As Long
        Public dwServiceSpecificExitCode As Long
        Public dwCheckPoint As Long
        Public dwWaitHint As Long
    End Structure
    ```

    > [!NOTE]
    > <span data-ttu-id="5ba90-172">Správce řízení služeb používá `dwWaitHint` členy a `dwCheckpoint` ke [struktuře SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) k určení, kolik času se má čekat na spuštění nebo vypnutí služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5ba90-172">The Service Control Manager uses the `dwWaitHint` and `dwCheckpoint` members of the [SERVICE_STATUS structure](/windows/win32/api/winsvc/ns-winsvc-service_status) to determine how much time to wait for a Windows service to start or shut down.</span></span> <span data-ttu-id="5ba90-173">Pokud vaše `OnStart` metody `OnStop` a běží dlouho, může vaše služba požádat o další čas tím `SetServiceStatus` , že se znovu zavolá s narůstající `dwCheckPoint` hodnotou.</span><span class="sxs-lookup"><span data-stu-id="5ba90-173">If your `OnStart` and `OnStop` methods run long, your service can request more time by calling `SetServiceStatus` again with an incremented `dwCheckPoint` value.</span></span>

3. <span data-ttu-id="5ba90-174">Ve třídě Deklarujte funkci [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) pomocí [vyvolání platformy:](../interop/consuming-unmanaged-dll-functions.md) `MyNewService`</span><span class="sxs-lookup"><span data-stu-id="5ba90-174">In the `MyNewService` class, declare the [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) function by using [platform invoke](../interop/consuming-unmanaged-dll-functions.md):</span></span>

    ```csharp
    [DllImport("advapi32.dll", SetLastError = true)]
    private static extern bool SetServiceStatus(System.IntPtr handle, ref ServiceStatus serviceStatus);
    ```

    ```vb
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean
    ```

4. <span data-ttu-id="5ba90-175">Chcete-li implementovat stav SERVICE_START_PENDING, přidejte následující kód na začátek <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody:</span><span class="sxs-lookup"><span data-stu-id="5ba90-175">To implement the SERVICE_START_PENDING status, add the following code to the beginning of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method:</span></span>

    ```csharp
    // Update the service state to Start Pending.
    ServiceStatus serviceStatus = new ServiceStatus();
    serviceStatus.dwCurrentState = ServiceState.SERVICE_START_PENDING;
    serviceStatus.dwWaitHint = 100000;
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);
    ```

    ```vb
    ' Update the service state to Start Pending.
    Dim serviceStatus As ServiceStatus = New ServiceStatus()
    serviceStatus.dwCurrentState = ServiceState.SERVICE_START_PENDING
    serviceStatus.dwWaitHint = 100000
    SetServiceStatus(Me.ServiceHandle, serviceStatus)
    ```

5. <span data-ttu-id="5ba90-176">Přidejte kód na konec `OnStart` metody pro nastavení stavu na SERVICE_RUNNING:</span><span class="sxs-lookup"><span data-stu-id="5ba90-176">Add code to the end of the `OnStart` method to set the status to SERVICE_RUNNING:</span></span>

    ```csharp
    // Update the service state to Running.
    serviceStatus.dwCurrentState = ServiceState.SERVICE_RUNNING;
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);
    ```

    ```vb
    ' Update the service state to Running.
    serviceStatus.dwCurrentState = ServiceState.SERVICE_RUNNING
    SetServiceStatus(Me.ServiceHandle, serviceStatus)
    ```

6. <span data-ttu-id="5ba90-177">Volitelné Pokud <xref:System.ServiceProcess.ServiceBase.OnStop%2A> je dlouhodobě spuštěná metoda, opakujte tento postup `OnStop` v metodě.</span><span class="sxs-lookup"><span data-stu-id="5ba90-177">(Optional) If <xref:System.ServiceProcess.ServiceBase.OnStop%2A> is a long-running method, repeat this procedure in the `OnStop` method.</span></span> <span data-ttu-id="5ba90-178">Před ukončením `OnStop` metody implementujte stav SERVICE_STOP_PENDING a vraťte stav SERVICE_STOPPED.</span><span class="sxs-lookup"><span data-stu-id="5ba90-178">Implement the SERVICE_STOP_PENDING status and return the SERVICE_STOPPED status before the `OnStop` method exits.</span></span>

   <span data-ttu-id="5ba90-179">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5ba90-179">For example:</span></span>

    ```csharp
    // Update the service state to Stop Pending.
    ServiceStatus serviceStatus = new ServiceStatus();
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOP_PENDING;
    serviceStatus.dwWaitHint = 100000;
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);

    // Update the service state to Stopped.
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOPPED;
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);
    ```

    ```vb
    ' Update the service state to Stop Pending.
    Dim serviceStatus As ServiceStatus = New ServiceStatus()
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOP_PENDING
    serviceStatus.dwWaitHint = 100000
    SetServiceStatus(Me.ServiceHandle, serviceStatus)

    ' Update the service state to Stopped.
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOPPED
    SetServiceStatus(Me.ServiceHandle, serviceStatus)
    ```

## <a name="add-installers-to-the-service"></a><span data-ttu-id="5ba90-180">Přidat instalační programy do služby</span><span class="sxs-lookup"><span data-stu-id="5ba90-180">Add installers to the service</span></span>

<span data-ttu-id="5ba90-181">Před spuštěním služby systému Windows je nutné ji nainstalovat, která ji zaregistruje ve Správci řízení služeb.</span><span class="sxs-lookup"><span data-stu-id="5ba90-181">Before you run a Windows service, you need to install it, which registers it with the Service Control Manager.</span></span> <span data-ttu-id="5ba90-182">Přidejte instalační programy do projektu pro zpracování podrobností o registraci.</span><span class="sxs-lookup"><span data-stu-id="5ba90-182">Add installers to your project to handle the registration details.</span></span>

1. <span data-ttu-id="5ba90-183">V **Průzkumník řešení**v místní nabídce pro **MyNewService.cs**nebo **MyNewService. vb**vyberte možnost **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="5ba90-183">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Designer**.</span></span>

2. <span data-ttu-id="5ba90-184">V zobrazení **Návrh** vyberte oblast pozadí a pak zvolte **Přidat instalační program** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="5ba90-184">In the **Design** view, select the background area, then choose **Add Installer** from the shortcut menu.</span></span>

     <span data-ttu-id="5ba90-185">Ve výchozím nastavení Visual Studio přidá třídu komponenty s názvem `ProjectInstaller`, která obsahuje dva instalační programy, do vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="5ba90-185">By default, Visual Studio adds a component class named `ProjectInstaller`, which contains two installers, to your project.</span></span> <span data-ttu-id="5ba90-186">Tyto instalační programy jsou pro vaši službu a pro přidružený proces služby.</span><span class="sxs-lookup"><span data-stu-id="5ba90-186">These installers are for your service and for the service's associated process.</span></span>

3. <span data-ttu-id="5ba90-187">V zobrazení **Návrh** pro **ProjectInstaller**vyberte možnost **ServiceInstaller1** pro projekt vizuálu C# , nebo **ServiceInstaller1** pro projekt Visual Basic a pak v místní nabídce zvolte možnost **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="5ba90-187">In the **Design** view for **ProjectInstaller**, select **serviceInstaller1** for a Visual C# project, or **ServiceInstaller1** for a Visual Basic project, then choose **Properties** from the shortcut menu.</span></span>

4. <span data-ttu-id="5ba90-188">V okně **vlastnosti** ověřte, zda <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> je vlastnost nastavena na hodnotu **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="5ba90-188">In the **Properties** window, verify the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property is set to **MyNewService**.</span></span>

5. <span data-ttu-id="5ba90-189">Přidejte text do <xref:System.ServiceProcess.ServiceInstaller.Description%2A> vlastnosti, jako je například *ukázková služba*.</span><span class="sxs-lookup"><span data-stu-id="5ba90-189">Add text to the <xref:System.ServiceProcess.ServiceInstaller.Description%2A> property, such as *A sample service*.</span></span>

     <span data-ttu-id="5ba90-190">Tento text se zobrazí ve sloupci **Popis** v okně **služby** a popisuje službu pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="5ba90-190">This text appears in the **Description** column of the **Services** window and describes the service to the user.</span></span>

    <span data-ttu-id="5ba90-191">![Popis služby v okně služby.](media/windows-service-description.png "Popis služby")</span><span class="sxs-lookup"><span data-stu-id="5ba90-191">![Service description in the Services window.](media/windows-service-description.png "Service description")</span></span>

6. <span data-ttu-id="5ba90-192">Přidejte text do <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5ba90-192">Add text to the <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> property.</span></span> <span data-ttu-id="5ba90-193">Například zobrazované *jméno MyNewService*.</span><span class="sxs-lookup"><span data-stu-id="5ba90-193">For example, *MyNewService Display Name*.</span></span>

     <span data-ttu-id="5ba90-194">Tento text se zobrazí ve sloupci **Zobrazovaný název** v okně **služby** .</span><span class="sxs-lookup"><span data-stu-id="5ba90-194">This text appears in the **Display Name** column of the **Services** window.</span></span> <span data-ttu-id="5ba90-195">Tento název se může lišit od <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> vlastnosti, což je název, který systém používá (například název, který `net start` pro příkaz použijete ke spuštění služby).</span><span class="sxs-lookup"><span data-stu-id="5ba90-195">This name can be different from the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property, which is the name the system uses (for example, the name you use for the `net start` command to start your service).</span></span>

7. <span data-ttu-id="5ba90-196">Nastavte vlastnost na <xref:System.ServiceProcess.ServiceStartMode.Automatic> z rozevíracího seznamu. <xref:System.ServiceProcess.ServiceInstaller.StartType%2A></span><span class="sxs-lookup"><span data-stu-id="5ba90-196">Set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to <xref:System.ServiceProcess.ServiceStartMode.Automatic> from the drop-down list.</span></span>

8. <span data-ttu-id="5ba90-197">Až budete hotovi, okna **vlastností** by měla vypadat jako na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="5ba90-197">When you're finished, the **Properties** windows should look like the following figure:</span></span>

     <span data-ttu-id="5ba90-198">![Vlastnosti instalačního programu pro službu systému Windows](media/windows-service-installer-properties.png "Vlastnosti instalačního programu služby systému Windows")</span><span class="sxs-lookup"><span data-stu-id="5ba90-198">![Installer Properties for a Windows service](media/windows-service-installer-properties.png "Windows service installer properties")</span></span>

9. <span data-ttu-id="5ba90-199">V zobrazení **Návrh** pro **ProjectInstaller**zvolte **položku ServiceProcessInstaller1** pro vizuální C# projekt, nebo **položku ServiceProcessInstaller1** pro projekt Visual Basic a pak v místní nabídce zvolte **vlastnosti** . .</span><span class="sxs-lookup"><span data-stu-id="5ba90-199">In the **Design** view for **ProjectInstaller**, choose **serviceProcessInstaller1** for a Visual C# project, or **ServiceProcessInstaller1** for a Visual Basic project, then choose **Properties** from the shortcut menu.</span></span> <span data-ttu-id="5ba90-200">Nastavte vlastnost na <xref:System.ServiceProcess.ServiceAccount.LocalSystem> z rozevíracího seznamu. <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A></span><span class="sxs-lookup"><span data-stu-id="5ba90-200">Set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property to <xref:System.ServiceProcess.ServiceAccount.LocalSystem> from the drop-down list.</span></span>

     <span data-ttu-id="5ba90-201">Toto nastavení nainstaluje službu a spustí ji pomocí účtu místního systému.</span><span class="sxs-lookup"><span data-stu-id="5ba90-201">This setting installs the service and runs it by using the local system account.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="5ba90-202"><xref:System.ServiceProcess.ServiceAccount.LocalSystem> Účet má široké oprávnění, včetně možnosti zapisovat do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="5ba90-202">The <xref:System.ServiceProcess.ServiceAccount.LocalSystem> account has broad permissions, including the ability to write to the event log.</span></span> <span data-ttu-id="5ba90-203">Používejte tento účet opatrně, protože může zvýšit riziko napadení škodlivým softwarem.</span><span class="sxs-lookup"><span data-stu-id="5ba90-203">Use this account with caution, because it might increase your risk of attacks from malicious software.</span></span> <span data-ttu-id="5ba90-204">Pro jiné úlohy zvažte použití <xref:System.ServiceProcess.ServiceAccount.LocalService> účtu, který v místním počítači funguje jako Neprivilegovaný uživatel a prezentuje anonymní přihlašovací údaje pro všechny vzdálené servery.</span><span class="sxs-lookup"><span data-stu-id="5ba90-204">For other tasks, consider using the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, which acts as a non-privileged user on the local computer and presents anonymous credentials to any remote server.</span></span> <span data-ttu-id="5ba90-205">Tento příklad se nezdařil, pokud se pokusíte použít <xref:System.ServiceProcess.ServiceAccount.LocalService> účet, protože potřebuje oprávnění k zápisu do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="5ba90-205">This example fails if you try to use the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, because it needs permission to write to the event log.</span></span>

<span data-ttu-id="5ba90-206">Další informace o instalačních programů naleznete v [tématu How to: Přidejte instalační programy do aplikace](how-to-add-installers-to-your-service-application.md)služby.</span><span class="sxs-lookup"><span data-stu-id="5ba90-206">For more information about installers, see [How to: Add installers to your service application](how-to-add-installers-to-your-service-application.md).</span></span>

## <a name="optional-set-startup-parameters"></a><span data-ttu-id="5ba90-207">Volitelné Nastavení spouštěcích parametrů</span><span class="sxs-lookup"><span data-stu-id="5ba90-207">(Optional) Set startup parameters</span></span>

> [!NOTE]
> <span data-ttu-id="5ba90-208">Než se rozhodnete přidat parametry spuštění, zvažte, jestli je to nejlepší způsob, jak předat službě informace.</span><span class="sxs-lookup"><span data-stu-id="5ba90-208">Before you decide to add startup parameters, consider whether it's the best way to pass information to your service.</span></span> <span data-ttu-id="5ba90-209">I když je lze snadno použít a analyzovat a uživatel je může snadno přepsat, může být obtížnější ho zjistit a použít bez dokumentace.</span><span class="sxs-lookup"><span data-stu-id="5ba90-209">Although they're easy to use and parse, and a user can easily override them, they might be harder for a user to discover and use without documentation.</span></span> <span data-ttu-id="5ba90-210">Obecně platí, že pokud vaše služba vyžaduje více než jen několik parametrů spuštění, měli byste místo toho použít registr nebo konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="5ba90-210">Generally, if your service requires more than just a few startup parameters, you should use the registry or a configuration file instead.</span></span>

<span data-ttu-id="5ba90-211">Služba systému Windows může přijmout argumenty příkazového řádku nebo parametry spuštění.</span><span class="sxs-lookup"><span data-stu-id="5ba90-211">A Windows service can accept command-line arguments, or startup parameters.</span></span> <span data-ttu-id="5ba90-212">Když přidáte kód pro zpracování parametrů spuštění, může uživatel spustit vaši službu s vlastními parametry spuštění v okně Vlastnosti služby.</span><span class="sxs-lookup"><span data-stu-id="5ba90-212">When you add code to process startup parameters, a user can start your service with their own custom startup parameters in the service properties window.</span></span> <span data-ttu-id="5ba90-213">Tyto parametry spuštění se ale při příštím spuštění služby neuchovávají.</span><span class="sxs-lookup"><span data-stu-id="5ba90-213">However, these startup parameters aren't persisted the next time the service starts.</span></span> <span data-ttu-id="5ba90-214">Chcete-li nastavit parametry spouštění trvale, nastavte je v registru.</span><span class="sxs-lookup"><span data-stu-id="5ba90-214">To set startup parameters permanently, set them in the registry.</span></span>

<span data-ttu-id="5ba90-215">Každá služba systému Windows obsahuje položku registru v podklíči **HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services** .</span><span class="sxs-lookup"><span data-stu-id="5ba90-215">Each Windows service has a registry entry under the **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services** subkey.</span></span> <span data-ttu-id="5ba90-216">V rámci podklíče jednotlivých služeb můžete pomocí podklíče **parametrů** ukládat informace, ke kterým má vaše služba přístup.</span><span class="sxs-lookup"><span data-stu-id="5ba90-216">Under each service's subkey, use the **Parameters** subkey to store information that your service can access.</span></span> <span data-ttu-id="5ba90-217">Konfigurační soubory aplikace pro službu systému Windows můžete použít stejným způsobem jako u jiných typů programů.</span><span class="sxs-lookup"><span data-stu-id="5ba90-217">You can use application configuration files for a Windows service the same way you do for other types of programs.</span></span> <span data-ttu-id="5ba90-218">Vzorový kód naleznete v tématu <xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5ba90-218">For sample code, see <xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType>.</span></span>

### <a name="to-add-startup-parameters"></a><span data-ttu-id="5ba90-219">Přidání parametrů spuštění</span><span class="sxs-lookup"><span data-stu-id="5ba90-219">To add startup parameters</span></span>

1. <span data-ttu-id="5ba90-220">Vyberte **program.cs**nebo **MyNewService. Designer. vb**a pak zvolte **Zobrazit kód** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="5ba90-220">Select **Program.cs**, or **MyNewService.Designer.vb**, then choose **View Code** from the shortcut menu.</span></span> <span data-ttu-id="5ba90-221">`Main` V metodě změňte kód a přidejte vstupní parametr a předejte jej do konstruktoru služby:</span><span class="sxs-lookup"><span data-stu-id="5ba90-221">In the `Main` method, change the code to add an input parameter and pass it to the service constructor:</span></span>

   [!code-csharp[VbRadconService](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/Program-add-parameter.cs?highlight=1,6)]
   [!code-vb[VbRadconService](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.Designer-add-parameter.vb?highlight=1-2)]

2. <span data-ttu-id="5ba90-222">V **MyNewService.cs**nebo **MyNewService. vb**změňte `MyNewService` konstruktor tak, aby zpracoval vstupní parametr následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="5ba90-222">In **MyNewService.cs**, or **MyNewService.vb**, change the `MyNewService` constructor to process the input parameter as follows:</span></span>

   ```csharp
   using System.Diagnostics;

   public MyNewService(string[] args)
   {
       InitializeComponent();

       string eventSourceName = "MySource";
       string logName = "MyNewLog";

       if (args.Length > 0)
       {
          eventSourceName = args[0];
       }

       if (args.Length > 1)
       {
           logName = args[1];
       }

       eventLog1 = new EventLog();

       if (!EventLog.SourceExists(eventSourceName))
       {
           EventLog.CreateEventSource(eventSourceName, logName);
       }

       eventLog1.Source = eventSourceName;
       eventLog1.Log = logName;
   }
   ```

   ```vb
   Imports System.Diagnostics

   Public Sub New(ByVal cmdArgs() As String)
       InitializeComponent()
       Dim eventSourceName As String = "MySource"
       Dim logName As String = "MyNewLog"
       If (cmdArgs.Count() > 0) Then
           eventSourceName = cmdArgs(0)
       End If
       If (cmdArgs.Count() > 1) Then
           logName = cmdArgs(1)
       End If
       eventLog1 = New EventLog()
       If (Not EventLog.SourceExists(eventSourceName)) Then
           EventLog.CreateEventSource(eventSourceName, logName)
       End If
       eventLog1.Source = eventSourceName
       eventLog1.Log = logName
   End Sub
   ```

   <span data-ttu-id="5ba90-223">Tento kód nastaví zdroj a název protokolu události podle parametrů spuštění, které uživatel dodá.</span><span class="sxs-lookup"><span data-stu-id="5ba90-223">This code sets the event source and log name according to the startup parameters that the user supplies.</span></span> <span data-ttu-id="5ba90-224">Pokud nejsou zadány žádné argumenty, budou použity výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5ba90-224">If no arguments are supplied, it uses default values.</span></span>

3. <span data-ttu-id="5ba90-225">Chcete-li zadat argumenty příkazového řádku, přidejte následující kód do `ProjectInstaller` třídy v **ProjectInstaller.cs**nebo **ProjectInstaller. vb**:</span><span class="sxs-lookup"><span data-stu-id="5ba90-225">To specify the command-line arguments, add the following code to the `ProjectInstaller` class in **ProjectInstaller.cs**, or **ProjectInstaller.vb**:</span></span>

   ```csharp
   protected override void OnBeforeInstall(IDictionary savedState)
   {
       string parameter = "MySource1\" \"MyLogFile1";
       Context.Parameters["assemblypath"] = "\"" + Context.Parameters["assemblypath"] + "\" \"" + parameter + "\"";
       base.OnBeforeInstall(savedState);
   }
   ```

   ```vb
   Protected Overrides Sub OnBeforeInstall(ByVal savedState As IDictionary)
       Dim parameter As String = "MySource1"" ""MyLogFile1"
       Context.Parameters("assemblypath") = """" + Context.Parameters("assemblypath") + """ """ + parameter + """"
       MyBase.OnBeforeInstall(savedState)
   End Sub
   ```

   <span data-ttu-id="5ba90-226">Tato hodnota obvykle obsahuje úplnou cestu ke spustitelnému souboru pro službu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5ba90-226">Typically, this value contains the full path to the executable for the Windows service.</span></span> <span data-ttu-id="5ba90-227">Aby se služba spouštěla správně, musí uživatel pro cestu a jednotlivé parametry dodat uvozovky.</span><span class="sxs-lookup"><span data-stu-id="5ba90-227">For the service to start up correctly, the user must supply quotation marks for the path and each individual parameter.</span></span> <span data-ttu-id="5ba90-228">Uživatel může změnit parametry v záznamu registru **ImagePath** pro změnu spouštěcích parametrů pro službu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5ba90-228">A user can change the parameters in the **ImagePath** registry entry to change the startup parameters for the Windows service.</span></span> <span data-ttu-id="5ba90-229">Lepším způsobem je však změnit hodnotu programově a zpřístupnit funkce uživatelsky přívětivým způsobem, například pomocí nástroje pro správu nebo konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="5ba90-229">However, a better way is to change the value programmatically and expose the functionality in a user-friendly way, such as by using a management or configuration utility.</span></span>

## <a name="build-the-service"></a><span data-ttu-id="5ba90-230">Sestavení služby</span><span class="sxs-lookup"><span data-stu-id="5ba90-230">Build the service</span></span>

1. <span data-ttu-id="5ba90-231">V **Průzkumník řešení**v místní nabídce projektu **MyNewService** vyberte možnost **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="5ba90-231">In **Solution Explorer**, choose **Properties** from the shortcut menu for the **MyNewService** project.</span></span>

   <span data-ttu-id="5ba90-232">Zobrazí se stránky vlastností projektu.</span><span class="sxs-lookup"><span data-stu-id="5ba90-232">The property pages for your project appear.</span></span>

2. <span data-ttu-id="5ba90-233">Na kartě **aplikace** v seznamu **spouštěcí objekt** vyberte **MyNewService. Program**nebo **Sub Main** pro Visual Basic projekty.</span><span class="sxs-lookup"><span data-stu-id="5ba90-233">On the **Application** tab, in the **Startup object** list, choose **MyNewService.Program**, or **Sub Main** for Visual Basic projects.</span></span>

3. <span data-ttu-id="5ba90-234">Chcete-li sestavit projekt, v **Průzkumník řešení**zvolte možnost **sestavit** z místní nabídky projektu (nebo stiskněte klávesovou zkratku **CTRL**+**SHIFT**+**B**).</span><span class="sxs-lookup"><span data-stu-id="5ba90-234">To build the project, in **Solution Explorer**, choose **Build** from the shortcut menu for your project (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="install-the-service"></a><span data-ttu-id="5ba90-235">Instalace služby</span><span class="sxs-lookup"><span data-stu-id="5ba90-235">Install the service</span></span>

<span data-ttu-id="5ba90-236">Teď, když jste sestavili službu systému Windows, ji můžete nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="5ba90-236">Now that you've built the Windows service, you can install it.</span></span> <span data-ttu-id="5ba90-237">Chcete-li nainstalovat službu systému Windows, je nutné mít v počítači, kde je nainstalován, pověření správce.</span><span class="sxs-lookup"><span data-stu-id="5ba90-237">To install a Windows service, you must have administrator credentials on the computer where it's installed.</span></span>

1. <span data-ttu-id="5ba90-238">Otevřete [Developer Command Prompt pro Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs) s přihlašovacími údaji správce.</span><span class="sxs-lookup"><span data-stu-id="5ba90-238">Open [Developer Command Prompt for Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs) with administrative credentials.</span></span> <span data-ttu-id="5ba90-239">V nabídce **Start** systému Windows vyberte ve složce Visual Studio možnost **Developer Command Prompt pro vs 2017** a potom v místní nabídce vyberte **Další** > **Spustit jako správce** .</span><span class="sxs-lookup"><span data-stu-id="5ba90-239">From the Windows **Start** menu, select **Developer Command Prompt for VS 2017** in the Visual Studio folder, then select **More** > **Run as Administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="5ba90-240">V okně **Developer Command Prompt pro Visual Studio** přejděte do složky, která obsahuje výstup vašeho projektu (ve výchozím nastavení je to podadresář *\bin\debug* projektu).</span><span class="sxs-lookup"><span data-stu-id="5ba90-240">In the **Developer Command Prompt for Visual Studio** window, navigate to the folder that contains your project's output (by default, the *\bin\Debug* subdirectory of your project).</span></span>

3. <span data-ttu-id="5ba90-241">Zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="5ba90-241">Enter the following command:</span></span>

    ```shell
    installutil MyNewService.exe
    ```

    <span data-ttu-id="5ba90-242">Pokud se služba nainstaluje úspěšně, příkaz ohlásí úspěch.</span><span class="sxs-lookup"><span data-stu-id="5ba90-242">If the service installs successfully, the command reports success.</span></span>

    <span data-ttu-id="5ba90-243">Pokud systém nemůže najít *Installutil. exe*, ujistěte se, že v počítači existuje.</span><span class="sxs-lookup"><span data-stu-id="5ba90-243">If the system can't find *installutil.exe*, make sure that it exists on your computer.</span></span> <span data-ttu-id="5ba90-244">Tento nástroj se instaluje s .NET Framework do složky *verze&gt;architektury%windir%\Microsoft.NET\Framework [64]\\&lt;* .</span><span class="sxs-lookup"><span data-stu-id="5ba90-244">This tool is installed with the .NET Framework to the folder *%windir%\Microsoft.NET\Framework[64]\\&lt;framework version&gt;*.</span></span> <span data-ttu-id="5ba90-245">Například výchozí cesta pro 64-bit verze je *%windir%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="5ba90-245">For example, the default path for the 64-bit version is *%windir%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span></span>

    <span data-ttu-id="5ba90-246">Pokud dojde k chybě procesu **Installutil. exe** , podívejte se do protokolu instalace a zjistěte, proč.</span><span class="sxs-lookup"><span data-stu-id="5ba90-246">If the **installutil.exe** process fails, check the install log to find out why.</span></span> <span data-ttu-id="5ba90-247">Ve výchozím nastavení je protokol ve stejné složce jako spustitelný soubor služby.</span><span class="sxs-lookup"><span data-stu-id="5ba90-247">By default, the log is in the same folder as the service executable.</span></span> <span data-ttu-id="5ba90-248">Instalace může selhat, pokud:</span><span class="sxs-lookup"><span data-stu-id="5ba90-248">The installation can fail if:</span></span>
    - <span data-ttu-id="5ba90-249"><xref:System.ComponentModel.RunInstallerAttribute> Třída není`ProjectInstaller` ve třídě k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5ba90-249">The <xref:System.ComponentModel.RunInstallerAttribute> class isn't present on the `ProjectInstaller` class.</span></span>
    - <span data-ttu-id="5ba90-250">Atribut není nastaven na `true`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5ba90-250">The attribute isn't set to `true`.</span></span>
    - <span data-ttu-id="5ba90-251">Třída není definovaná jako `public`. `ProjectInstaller`</span><span class="sxs-lookup"><span data-stu-id="5ba90-251">The `ProjectInstaller` class isn't defined as `public`.</span></span>

<span data-ttu-id="5ba90-252">Další informace najdete v tématu [jak: Nainstalujte a odinstalujte](how-to-install-and-uninstall-services.md)služby.</span><span class="sxs-lookup"><span data-stu-id="5ba90-252">For more information, see [How to: Install and uninstall services](how-to-install-and-uninstall-services.md).</span></span>

## <a name="start-and-run-the-service"></a><span data-ttu-id="5ba90-253">Spuštění a spuštění služby</span><span class="sxs-lookup"><span data-stu-id="5ba90-253">Start and run the service</span></span>

1. <span data-ttu-id="5ba90-254">V systému Windows otevřete desktopovou aplikaci **služby** .</span><span class="sxs-lookup"><span data-stu-id="5ba90-254">In Windows, open the **Services** desktop app.</span></span> <span data-ttu-id="5ba90-255">Stisknutím **Windows**+**R** otevřete pole **Spustit** , zadejte *Services. msc*a potom stiskněte klávesu **ENTER** nebo klikněte na **tlačítko OK**.</span><span class="sxs-lookup"><span data-stu-id="5ba90-255">Press **Windows**+**R** to open the **Run** box, enter *services.msc*, and then press **Enter** or select **OK**.</span></span>

     <span data-ttu-id="5ba90-256">Vaše služba by se měla zobrazit v seznamu **služby**zobrazená abecedně podle zobrazovaného názvu, který jste pro něj nastavili.</span><span class="sxs-lookup"><span data-stu-id="5ba90-256">You should see your service listed in **Services**, displayed alphabetically by the display name that you set for it.</span></span>

     ![MyNewService v okně služby.](media/windowsservices-serviceswindow.PNG)

2. <span data-ttu-id="5ba90-258">Službu spustíte tak, že v místní nabídce služby zvolíte možnost **Spustit** .</span><span class="sxs-lookup"><span data-stu-id="5ba90-258">To start the service, choose **Start** from the service's shortcut menu.</span></span>

3. <span data-ttu-id="5ba90-259">Pokud chcete službu zastavit, v místní nabídce služby klikněte na **zastavit** .</span><span class="sxs-lookup"><span data-stu-id="5ba90-259">To stop the service, choose **Stop** from the service's shortcut menu.</span></span>

4. <span data-ttu-id="5ba90-260">Volitelné Na příkazovém řádku spusťte a zastavte službu pomocí příkazu  **&lt;NET&gt; Start Service název** a  **&lt;název&gt; služby net stop** .</span><span class="sxs-lookup"><span data-stu-id="5ba90-260">(Optional) From the command line, use the commands **net start &lt;service name&gt;** and **net stop &lt;service name&gt;** to start and stop your service.</span></span>

### <a name="verify-the-event-log-output-of-your-service"></a><span data-ttu-id="5ba90-261">Ověření výstupu protokolu událostí vaší služby</span><span class="sxs-lookup"><span data-stu-id="5ba90-261">Verify the event log output of your service</span></span>

1. <span data-ttu-id="5ba90-262">Ve Windows otevřete **Prohlížeč událostí** desktopovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5ba90-262">In Windows, open the **Event Viewer** desktop app.</span></span> <span data-ttu-id="5ba90-263">Do panelu hledání ve Windows zadejte *Prohlížeč událostí* a pak ve výsledcích hledání vyberte **Prohlížeč událostí** .</span><span class="sxs-lookup"><span data-stu-id="5ba90-263">Enter *Event Viewer* in the Windows search bar, and then select **Event Viewer** from the search results.</span></span>

   > [!TIP]
   > <span data-ttu-id="5ba90-264">V aplikaci Visual Studio můžete získat přístup k protokolům událostí otevřením **Průzkumník serveru** v nabídce **zobrazení** (nebo stisknutím kláves **CTRL**+ **+ ALT**+**S**) a rozbalením uzlu **protokoly událostí** pro místní počítač.</span><span class="sxs-lookup"><span data-stu-id="5ba90-264">In Visual Studio, you can access event logs by opening **Server Explorer** from the **View** menu (or press **Ctrl**+**Alt**+**S**) and expanding the **Event Logs** node for the local computer.</span></span>

2. <span data-ttu-id="5ba90-265">V **Prohlížeč událostí**rozbalte **protokoly aplikací a služeb**.</span><span class="sxs-lookup"><span data-stu-id="5ba90-265">In **Event Viewer**, expand **Applications and Services Logs**.</span></span>

3. <span data-ttu-id="5ba90-266">Vyhledejte výpis pro **myNewLog** (nebo **MyLogFile1** , pokud jste postupovali podle postupu pro přidání argumentů příkazového řádku) a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="5ba90-266">Locate the listing for **MyNewLog** (or **MyLogFile1** if you followed the procedure to add command-line arguments) and expand it.</span></span> <span data-ttu-id="5ba90-267">Měli byste vidět položky dvou akcí (spustit a zastavit), které služba provedla.</span><span class="sxs-lookup"><span data-stu-id="5ba90-267">You should see the entries for the two actions (start and stop) that your service performed.</span></span>

     ![Použití Prohlížeč událostí k zobrazení položek protokolu událostí](media/windows-service-event-viewer.png)

## <a name="clean-up-resources"></a><span data-ttu-id="5ba90-269">Vyčištění prostředků</span><span class="sxs-lookup"><span data-stu-id="5ba90-269">Clean up resources</span></span>

<span data-ttu-id="5ba90-270">Pokud už aplikaci služby systému Windows nepotřebujete, můžete ji odebrat.</span><span class="sxs-lookup"><span data-stu-id="5ba90-270">If you no longer need the Windows service app, you can remove it.</span></span>

1. <span data-ttu-id="5ba90-271">Otevřete **Developer Command Prompt pro Visual Studio** s přihlašovacími údaji správce.</span><span class="sxs-lookup"><span data-stu-id="5ba90-271">Open **Developer Command Prompt for Visual Studio** with administrative credentials.</span></span>

2. <span data-ttu-id="5ba90-272">V okně **Developer Command Prompt pro Visual Studio** přejděte do složky, která obsahuje výstup vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="5ba90-272">In the **Developer Command Prompt for Visual Studio** window, navigate to the folder that contains your project's output.</span></span>

3. <span data-ttu-id="5ba90-273">Zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="5ba90-273">Enter the following command:</span></span>

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   <span data-ttu-id="5ba90-274">Pokud se služba úspěšně odinstaluje, příkaz oznámí, že vaše služba byla úspěšně odebrána.</span><span class="sxs-lookup"><span data-stu-id="5ba90-274">If the service uninstalls successfully, the command reports that your service was successfully removed.</span></span> <span data-ttu-id="5ba90-275">Další informace najdete v tématu [jak: Nainstalujte a odinstalujte](how-to-install-and-uninstall-services.md)služby.</span><span class="sxs-lookup"><span data-stu-id="5ba90-275">For more information, see [How to: Install and uninstall services](how-to-install-and-uninstall-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="5ba90-276">Další postup</span><span class="sxs-lookup"><span data-stu-id="5ba90-276">Next steps</span></span>

<span data-ttu-id="5ba90-277">Teď, když jste vytvořili službu, můžete:</span><span class="sxs-lookup"><span data-stu-id="5ba90-277">Now that you've created the service, you can:</span></span>

- <span data-ttu-id="5ba90-278">Vytvoření samostatného instalačního programu, který bude používat k instalaci služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5ba90-278">Create a standalone setup program for others to use to install your Windows service.</span></span> <span data-ttu-id="5ba90-279">Pomocí sady [nástrojů WIX](http://wixtoolset.org/) můžete vytvořit instalační program pro službu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5ba90-279">Use the [WiX Toolset](http://wixtoolset.org/) to create an installer for a Windows service.</span></span> <span data-ttu-id="5ba90-280">Další nápady najdete v tématu [Vytvoření balíčku instalačního programu](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span><span class="sxs-lookup"><span data-stu-id="5ba90-280">For other ideas, see [Create an installer package](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span></span>

- <span data-ttu-id="5ba90-281">Prozkoumejte <xref:System.ServiceProcess.ServiceController> komponentu, která vám umožní odesílat příkazy do služby, kterou jste nainstalovali.</span><span class="sxs-lookup"><span data-stu-id="5ba90-281">Explore the <xref:System.ServiceProcess.ServiceController> component, which enables you to send commands to the service you've installed.</span></span>

- <span data-ttu-id="5ba90-282">Místo vytvoření protokolu událostí při spuštění aplikace použijte instalační program k vytvoření protokolu událostí při instalaci aplikace.</span><span class="sxs-lookup"><span data-stu-id="5ba90-282">Instead of creating the event log when the application runs, use an installer to create an event log when you install the application.</span></span> <span data-ttu-id="5ba90-283">Protokol událostí je odstraněn instalačním programem při odinstalaci aplikace.</span><span class="sxs-lookup"><span data-stu-id="5ba90-283">The event log is deleted by the installer when you uninstall the application.</span></span> <span data-ttu-id="5ba90-284">Další informace naleznete v tématu <xref:System.Diagnostics.EventLogInstaller>.</span><span class="sxs-lookup"><span data-stu-id="5ba90-284">For more information, see <xref:System.Diagnostics.EventLogInstaller>.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ba90-285">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5ba90-285">See also</span></span>

- [<span data-ttu-id="5ba90-286">Aplikace služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="5ba90-286">Windows service applications</span></span>](index.md)
- [<span data-ttu-id="5ba90-287">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="5ba90-287">Introduction to Windows service applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="5ba90-288">Postupy: Ladění aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="5ba90-288">How to: Debug Windows service applications</span></span>](how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="5ba90-289">Služby (Windows)</span><span class="sxs-lookup"><span data-stu-id="5ba90-289">Services (Windows)</span></span>](/windows/desktop/Services/services)
