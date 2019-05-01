---
title: 'Kurz: Vytvoření aplikace služby Windows'
ms.date: 03/27/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows service applications, walkthroughs
- Windows service applications, creating
ms.assetid: e24d8a3d-edc6-485c-b6e0-5672d91fb607
author: ghogen
ms.openlocfilehash: 8d30b7b98648e36a3008ac015f9560620f77b363
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "63809501"
---
# <a name="tutorial-create-a-windows-service-app"></a><span data-ttu-id="da3af-102">Kurz: Vytvoření aplikace služby Windows</span><span class="sxs-lookup"><span data-stu-id="da3af-102">Tutorial: Create a Windows service app</span></span>

<span data-ttu-id="da3af-103">Tento článek ukazuje, jak vytvořit aplikaci služby Windows v sadě Visual Studio, která zapisuje zprávy do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="da3af-103">This article demonstrates how to create a Windows service app in Visual Studio that writes messages to an event log.</span></span>

## <a name="create-a-service"></a><span data-ttu-id="da3af-104">Vytvoření služby</span><span class="sxs-lookup"><span data-stu-id="da3af-104">Create a service</span></span>

<span data-ttu-id="da3af-105">Pokud chcete začít, vytvořte projekt a nastavte hodnoty, které jsou požadovány pro správné fungování služby.</span><span class="sxs-lookup"><span data-stu-id="da3af-105">To begin, create the project and set the values that are required for the service to function correctly.</span></span>

1. <span data-ttu-id="da3af-106">Ze sady Visual Studio **souboru** nabídce vyberte možnost **nový** > **projektu** (nebo stiskněte klávesu **Ctrl** + **Shift**+**N**) Chcete-li otevřít **nový projekt** okna.</span><span class="sxs-lookup"><span data-stu-id="da3af-106">From the Visual Studio **File** menu, select **New** > **Project** (or press **Ctrl**+**Shift**+**N**) to open the **New Project** window.</span></span>

2. <span data-ttu-id="da3af-107">Vyhledejte a vyberte **služba Windows (.NET Framework)** šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="da3af-107">Navigate to and select the **Windows Service (.NET Framework)** project template.</span></span> <span data-ttu-id="da3af-108">Pokud chcete ji najít, rozbalte **nainstalováno** a **Visual C#**  nebo **jazyka Visual Basic**a pak vyberte **Windows Desktop**.</span><span class="sxs-lookup"><span data-stu-id="da3af-108">To find it, expand **Installed** and **Visual C#** or **Visual Basic**, then select **Windows Desktop**.</span></span> <span data-ttu-id="da3af-109">Nebo zadejte *Windows Service* do vyhledávacího pole na vpravo nahoře a stiskněte klávesu **Enter**.</span><span class="sxs-lookup"><span data-stu-id="da3af-109">Or, enter *Windows Service* in the search box on the upper right and press **Enter**.</span></span>

   ![Šablona služby Windows v dialogu Nový projekt v sadě Visual Studio](media/new-project-dialog.png)

   > [!NOTE]
   > <span data-ttu-id="da3af-111">Pokud se nezobrazí **Windows Service** šablony, je nutné nainstalovat **vývoj desktopových aplikací .NET** úlohy:</span><span class="sxs-lookup"><span data-stu-id="da3af-111">If you don't see the **Windows Service** template, you may need to install the **.NET desktop development** workload:</span></span>
   >
   > <span data-ttu-id="da3af-112">V **nový projekt** dialogového okna, vyberte **otevřít instalační program Visual Studio** v levé dolní části.</span><span class="sxs-lookup"><span data-stu-id="da3af-112">In the **New Project** dialog, select **Open Visual Studio Installer** on the lower left.</span></span> <span data-ttu-id="da3af-113">Vyberte **vývoj desktopových aplikací .NET** úlohy a pak vyberte **změnit**.</span><span class="sxs-lookup"><span data-stu-id="da3af-113">Select the **.NET desktop development** workload, and then select **Modify**.</span></span>

3. <span data-ttu-id="da3af-114">Pro **název**, zadejte *MyNewService*a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="da3af-114">For **Name**, enter *MyNewService*, and then select **OK**.</span></span>

   <span data-ttu-id="da3af-115">**Návrhu** se zobrazí karta (**Service1.cs [Design]** nebo **Service1.vb [Design]**).</span><span class="sxs-lookup"><span data-stu-id="da3af-115">The **Design** tab appears (**Service1.cs [Design]** or **Service1.vb [Design]**).</span></span>

   <span data-ttu-id="da3af-116">Šablona projektu zahrnuje komponentní třídu s názvem `Service1` , která dědí z <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="da3af-116">The project template includes a component class named `Service1` that inherits from <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="da3af-117">Obsahuje velkou část základního kódu služby, jako je například kód ke spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="da3af-117">It includes much of the basic service code, such as the code to start the service.</span></span>

## <a name="rename-the-service"></a><span data-ttu-id="da3af-118">Přejmenování služby</span><span class="sxs-lookup"><span data-stu-id="da3af-118">Rename the service</span></span>

<span data-ttu-id="da3af-119">Přejmenování služby z **Service1** k **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="da3af-119">Rename the service from **Service1** to **MyNewService**.</span></span>

1. <span data-ttu-id="da3af-120">V **Průzkumníka řešení**vyberte **Service1.cs**, nebo **Service1.vb**a zvolte **přejmenovat** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="da3af-120">In **Solution Explorer**, select **Service1.cs**, or **Service1.vb**, and choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="da3af-121">Přejmenujte soubor na **MyNewService.cs**, nebo **MyNewService.vb**a potom stiskněte klávesu **Enter**</span><span class="sxs-lookup"><span data-stu-id="da3af-121">Rename the file to **MyNewService.cs**, or **MyNewService.vb**, and then press **Enter**</span></span>

    <span data-ttu-id="da3af-122">Zobrazí se automaticky otevírané okno s dotazem, zda chcete přejmenovat všechny odkazy na prvek kódu *Service1*.</span><span class="sxs-lookup"><span data-stu-id="da3af-122">A pop-up window appears asking whether you would like to rename all references to the code element *Service1*.</span></span>

2. <span data-ttu-id="da3af-123">V místním okně vyberte **Ano**.</span><span class="sxs-lookup"><span data-stu-id="da3af-123">In the pop-up window, select **Yes**.</span></span>

    <span data-ttu-id="da3af-124">![Přejmenovat řádku](media/windows-service-rename.png "Windows service přejmenovat řádku")</span><span class="sxs-lookup"><span data-stu-id="da3af-124">![Rename prompt](media/windows-service-rename.png "Windows service rename prompt")</span></span>

3. <span data-ttu-id="da3af-125">V **návrhu** kartu, vyberte možnost **vlastnosti** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="da3af-125">In the **Design** tab, select **Properties** from the shortcut menu.</span></span> <span data-ttu-id="da3af-126">Z **vlastnosti** okno Změnit **ServiceName** hodnota, která se *MyNewService*.</span><span class="sxs-lookup"><span data-stu-id="da3af-126">From the **Properties** window, change the **ServiceName** value to *MyNewService*.</span></span>

    <span data-ttu-id="da3af-127">![Vlastnosti služby](media/windows-service-properties.png "vlastností služby Windows")</span><span class="sxs-lookup"><span data-stu-id="da3af-127">![Service properties](media/windows-service-properties.png "Windows service properties")</span></span>

4. <span data-ttu-id="da3af-128">Vyberte **Uložit vše** z **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="da3af-128">Select **Save All** from the **File** menu.</span></span>

## <a name="add-features-to-the-service"></a><span data-ttu-id="da3af-129">Přidání funkcí do služby</span><span class="sxs-lookup"><span data-stu-id="da3af-129">Add features to the service</span></span>

<span data-ttu-id="da3af-130">V této části přidáte do služby Windows vlastního protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="da3af-130">In this section, you add a custom event log to the Windows service.</span></span> <span data-ttu-id="da3af-131"><xref:System.Diagnostics.EventLog> Komponenta je příkladem typ součásti, můžete přidat do služby Windows.</span><span class="sxs-lookup"><span data-stu-id="da3af-131">The <xref:System.Diagnostics.EventLog> component is an example of the type of component you can add to a Windows service.</span></span>

### <a name="add-custom-event-log-functionality"></a><span data-ttu-id="da3af-132">Přidání funkce vlastního protokolu událostí</span><span class="sxs-lookup"><span data-stu-id="da3af-132">Add custom event log functionality</span></span>

1. <span data-ttu-id="da3af-133">V **Průzkumníka řešení**, v místní nabídce pro **MyNewService.cs**, nebo **MyNewService.vb**, zvolte **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="da3af-133">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Designer**.</span></span>

2. <span data-ttu-id="da3af-134">V **nástrojů**, rozbalte **součásti**a pak přetáhněte **EventLog** komponentu do **Service1.cs [Design]**, nebo  **Service1.VB [Design]** kartu.</span><span class="sxs-lookup"><span data-stu-id="da3af-134">In **Toolbox**, expand **Components**, and then drag the **EventLog** component to the **Service1.cs [Design]**, or **Service1.vb [Design]** tab.</span></span>

3. <span data-ttu-id="da3af-135">V **Průzkumníka řešení**, v místní nabídce pro **MyNewService.cs**, nebo **MyNewService.vb**, zvolte **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="da3af-135">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Code**.</span></span>

4. <span data-ttu-id="da3af-136">Definování vlastního protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="da3af-136">Define a custom event log.</span></span> <span data-ttu-id="da3af-137">Pro C#, upravte existující `MyNewService()` konstruktor; v jazyce Visual Basic přidejte `New()` konstruktor:</span><span class="sxs-lookup"><span data-stu-id="da3af-137">For C#, edit the existing `MyNewService()` constructor; for Visual Basic, add the `New()` constructor:</span></span>

   [!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#2)]
   [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]

5. <span data-ttu-id="da3af-138">Přidat `using` příkazu **MyNewService.cs** (pokud ještě neexistuje), nebo `Imports` příkaz **MyNewService.vb**, pro <xref:System.Diagnostics?displayProperty=nameWithType> obor názvů:</span><span class="sxs-lookup"><span data-stu-id="da3af-138">Add a `using` statement to **MyNewService.cs** (if it doesn't already exist), or an `Imports` statement **MyNewService.vb**, for the <xref:System.Diagnostics?displayProperty=nameWithType> namespace:</span></span>

    ```csharp
    using System.Diagnostics;
    ```

    ```vb
    Imports System.Diagnostics
    ```

6. <span data-ttu-id="da3af-139">Vyberte **Uložit vše** z **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="da3af-139">Select **Save All** from the **File** menu.</span></span>

### <a name="define-what-occurs-when-the-service-starts"></a><span data-ttu-id="da3af-140">Definujte, co se stane při spuštění služby</span><span class="sxs-lookup"><span data-stu-id="da3af-140">Define what occurs when the service starts</span></span>

<span data-ttu-id="da3af-141">V editoru kódu pro **MyNewService.cs** nebo **MyNewService.vb**, vyhledejte <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody. Visual Studio automaticky vytvoří definici prázdnou metodu při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="da3af-141">In the code editor for **MyNewService.cs** or **MyNewService.vb**, locate the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method; Visual Studio automatically created an empty method definition when you created the project.</span></span> <span data-ttu-id="da3af-142">Přidejte kód, který zapíše položku do protokolu událostí při spuštění služby:</span><span class="sxs-lookup"><span data-stu-id="da3af-142">Add code that writes an entry to the event log when the service starts:</span></span>

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

#### <a name="polling"></a><span data-ttu-id="da3af-143">Dotazování</span><span class="sxs-lookup"><span data-stu-id="da3af-143">Polling</span></span>

<span data-ttu-id="da3af-144">Protože aplikace služby byla navržena jako dlouhotrvající, obvykle dotazuje nebo sleduje systém, který jste vytvořili v <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="da3af-144">Because a service application is designed to be long-running, it usually polls or monitors the system, which you set up in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span> <span data-ttu-id="da3af-145">`OnStart` Metoda musí vracet v operačním systému po operaci služby tak, aby systém není blokován.</span><span class="sxs-lookup"><span data-stu-id="da3af-145">The `OnStart` method must return to the operating system after the service's operation has begun so that the system isn't blocked.</span></span>

<span data-ttu-id="da3af-146">Pokud chcete nastavit jednoduchý mechanismus dotazování, použijte <xref:System.Timers.Timer?displayProperty=nameWithType> komponenty.</span><span class="sxs-lookup"><span data-stu-id="da3af-146">To set up a simple polling mechanism, use the <xref:System.Timers.Timer?displayProperty=nameWithType> component.</span></span> <span data-ttu-id="da3af-147">Časovač vyvolá <xref:System.Timers.Timer.Elapsed> události v pravidelných intervalech, po kterém můžete provádět monitorování vaší služby.</span><span class="sxs-lookup"><span data-stu-id="da3af-147">The timer raises an <xref:System.Timers.Timer.Elapsed> event at regular intervals, at which time your service can do its monitoring.</span></span> <span data-ttu-id="da3af-148">Můžete použít <xref:System.Timers.Timer> komponenty následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="da3af-148">You use the <xref:System.Timers.Timer> component as follows:</span></span>

- <span data-ttu-id="da3af-149">Nastavte vlastnosti <xref:System.Timers.Timer> v komponentu `MyNewService.OnStart` metody.</span><span class="sxs-lookup"><span data-stu-id="da3af-149">Set the properties of the <xref:System.Timers.Timer> component in the `MyNewService.OnStart` method.</span></span>
- <span data-ttu-id="da3af-150">Spuštění časovače voláním <xref:System.Timers.Timer.Start%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="da3af-150">Start the timer by calling the <xref:System.Timers.Timer.Start%2A> method.</span></span>

##### <a name="set-up-the-polling-mechanism"></a><span data-ttu-id="da3af-151">Nastavte dotazovací mechanismus.</span><span class="sxs-lookup"><span data-stu-id="da3af-151">Set up the polling mechanism.</span></span>

1. <span data-ttu-id="da3af-152">Přidejte následující kód `MyNewService.OnStart` událost nastavit dotazovací mechanismus:</span><span class="sxs-lookup"><span data-stu-id="da3af-152">Add the following code in the `MyNewService.OnStart` event to set up the polling mechanism:</span></span>

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

2. <span data-ttu-id="da3af-153">Přidat `using` příkazu **MyNewService.cs**, nebo `Imports` příkazu **MyNewService.vb**, pro <xref:System.Timers?displayProperty=nameWithType> obor názvů:</span><span class="sxs-lookup"><span data-stu-id="da3af-153">Add a `using` statement to **MyNewService.cs**, or an `Imports` statement to **MyNewService.vb**, for the <xref:System.Timers?displayProperty=nameWithType> namespace:</span></span>

   ```csharp
   using System.Timers;
   ```

   ```vb
   Imports System.Timers
   ```

3. <span data-ttu-id="da3af-154">V `MyNewService` třídy, přidejte `OnTimer` metodu ke zpracování <xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType> události:</span><span class="sxs-lookup"><span data-stu-id="da3af-154">In the `MyNewService` class, add the `OnTimer` method to handle the <xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType> event:</span></span>

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

4. <span data-ttu-id="da3af-155">V `MyNewService` třídy, přidat členskou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="da3af-155">In the `MyNewService` class, add a member variable.</span></span> <span data-ttu-id="da3af-156">Obsahuje identifikátor další události pro zápis do protokolu událostí:</span><span class="sxs-lookup"><span data-stu-id="da3af-156">It contains the identifier of the next event to write into the event log:</span></span>

   ```csharp
   private int eventId = 1;
   ```

   ```vb
   Private eventId As Integer = 1
   ```

<span data-ttu-id="da3af-157">Místo spouštění veškerou práci na hlavním vlákně, můžete spouštět úlohy s použitím pracovních vláken na pozadí.</span><span class="sxs-lookup"><span data-stu-id="da3af-157">Instead of running all your work on the main thread, you can run tasks by using background worker threads.</span></span> <span data-ttu-id="da3af-158">Další informace naleznete v tématu <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="da3af-158">For more information, see <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span></span>

### <a name="define-what-occurs-when-the-service-is-stopped"></a><span data-ttu-id="da3af-159">Definujte, co se stane při zastavení služby</span><span class="sxs-lookup"><span data-stu-id="da3af-159">Define what occurs when the service is stopped</span></span>

<span data-ttu-id="da3af-160">Vložit řádek kódu <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metodu, která přidá položku do protokolu událostí po zastavení služby:</span><span class="sxs-lookup"><span data-stu-id="da3af-160">Insert a line of code in the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method that adds an entry to the event log when the service is stopped:</span></span>

[!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#4)]
[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a><span data-ttu-id="da3af-161">Definování dalších akcí služby</span><span class="sxs-lookup"><span data-stu-id="da3af-161">Define other actions for the service</span></span>

<span data-ttu-id="da3af-162">Je možné přepsat <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, a <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> metody definovat další zpracování pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="da3af-162">You can override the <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, and <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> methods to define additional processing for your component.</span></span>

<span data-ttu-id="da3af-163">Následující kód ukazuje, jak přepsat <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> metodu `MyNewService` třídy:</span><span class="sxs-lookup"><span data-stu-id="da3af-163">The following code shows how you to override the <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> method in the `MyNewService` class:</span></span>

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]

## <a name="set-service-status"></a><span data-ttu-id="da3af-164">Nastavit stav služby</span><span class="sxs-lookup"><span data-stu-id="da3af-164">Set service status</span></span>

<span data-ttu-id="da3af-165">Služby oznamují svůj stav na [správce řízení služeb](/windows/desktop/Services/service-control-manager) tak, aby uživatel můžete zjistit, jestli služba správně funguje.</span><span class="sxs-lookup"><span data-stu-id="da3af-165">Services report their status to the [Service Control Manager](/windows/desktop/Services/service-control-manager) so that a user can tell whether a service is functioning correctly.</span></span> <span data-ttu-id="da3af-166">Ve výchozím nastavení, služby, která dědí z <xref:System.ServiceProcess.ServiceBase> omezenou sadu nastavení stavu, které zahrnují SERVICE_STOPPED SERVICE_PAUSED a SERVICE_RUNNING sestavy.</span><span class="sxs-lookup"><span data-stu-id="da3af-166">By default, a service that inherits from <xref:System.ServiceProcess.ServiceBase> reports a limited set of status settings, which include SERVICE_STOPPED, SERVICE_PAUSED, and SERVICE_RUNNING.</span></span> <span data-ttu-id="da3af-167">Pokud služba chvíli trvat, než se spustí, je vhodné informuje o stavu SERVICE_START_PENDING.</span><span class="sxs-lookup"><span data-stu-id="da3af-167">If a service takes a while to start up, it's useful to report a SERVICE_START_PENDING status.</span></span>

<span data-ttu-id="da3af-168">Nastavení stavu SERVICE_START_PENDING a SERVICE_STOP_PENDING můžete implementovat přidáním kódu, který volá Windows [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) funkce.</span><span class="sxs-lookup"><span data-stu-id="da3af-168">You can implement the SERVICE_START_PENDING and SERVICE_STOP_PENDING status settings by adding code that calls the Windows [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) function.</span></span>

### <a name="implement-service-pending-status"></a><span data-ttu-id="da3af-169">Implementace služby čekajícím stavu</span><span class="sxs-lookup"><span data-stu-id="da3af-169">Implement service pending status</span></span>

1. <span data-ttu-id="da3af-170">Přidat `using` příkazu **MyNewService.cs**, nebo `Imports` příkazu **MyNewService.vb**, pro <xref:System.Runtime.InteropServices?displayProperty=nameWithType> obor názvů:</span><span class="sxs-lookup"><span data-stu-id="da3af-170">Add a `using` statement to **MyNewService.cs**, or an `Imports` statement to **MyNewService.vb**, for the <xref:System.Runtime.InteropServices?displayProperty=nameWithType> namespace:</span></span>

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. <span data-ttu-id="da3af-171">Přidejte následující kód, který **MyNewService.cs**, nebo **MyNewService.vb**, chcete-li deklarovat `ServiceState` hodnoty a přidat strukturu pro stav, který budete používat ve volání funkce invoke:</span><span class="sxs-lookup"><span data-stu-id="da3af-171">Add the following code to **MyNewService.cs**, or **MyNewService.vb**, to declare the `ServiceState` values and to add a structure for the status, which you'll use in a platform invoke call:</span></span>

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
    > <span data-ttu-id="da3af-172">Správce řízení služeb používá `dwWaitHint` a `dwCheckpoint` členy [SERVICE_STATUS struktura](/windows/desktop/api/winsvc/ns-winsvc-_service_status) k určení doby čekání na službu Windows ke spuštění nebo vypnutí.</span><span class="sxs-lookup"><span data-stu-id="da3af-172">The Service Control Manager uses the `dwWaitHint` and `dwCheckpoint` members of the [SERVICE_STATUS structure](/windows/desktop/api/winsvc/ns-winsvc-_service_status) to determine how much time to wait for a Windows service to start or shut down.</span></span> <span data-ttu-id="da3af-173">Pokud vaše `OnStart` a `OnStop` metody se spustí, long, vaše služba může požádat o víc času voláním `SetServiceStatus` znovu se zvýšena `dwCheckPoint` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="da3af-173">If your `OnStart` and `OnStop` methods run long, your service can request more time by calling `SetServiceStatus` again with an incremented `dwCheckPoint` value.</span></span>

3. <span data-ttu-id="da3af-174">V `MyNewService` třídy, deklarujte [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) funkce s použitím [vyvolání platformy](../interop/consuming-unmanaged-dll-functions.md):</span><span class="sxs-lookup"><span data-stu-id="da3af-174">In the `MyNewService` class, declare the [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) function by using [platform invoke](../interop/consuming-unmanaged-dll-functions.md):</span></span>

    ```csharp
    [DllImport("advapi32.dll", SetLastError = true)]
    private static extern bool SetServiceStatus(System.IntPtr handle, ref ServiceStatus serviceStatus);
    ```

    ```vb
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean
    ```

4. <span data-ttu-id="da3af-175">K implementaci SERVICE_START_PENDING stavu, přidejte následující kód do začátku <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody:</span><span class="sxs-lookup"><span data-stu-id="da3af-175">To implement the SERVICE_START_PENDING status, add the following code to the beginning of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method:</span></span>

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

5. <span data-ttu-id="da3af-176">Přidejte kód do konce `OnStart` metody nastavte stav SERVICE_RUNNING:</span><span class="sxs-lookup"><span data-stu-id="da3af-176">Add code to the end of the `OnStart` method to set the status to SERVICE_RUNNING:</span></span>

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

6. <span data-ttu-id="da3af-177">(Volitelné) Pokud <xref:System.ServiceProcess.ServiceBase.OnStop%2A> je metoda dlouhotrvající, opakujte tento postup `OnStop` metoda.</span><span class="sxs-lookup"><span data-stu-id="da3af-177">(Optional) If <xref:System.ServiceProcess.ServiceBase.OnStop%2A> is a long-running method, repeat this procedure in the `OnStop` method.</span></span> <span data-ttu-id="da3af-178">Implementace SERVICE_STOP_PENDING stav a stav SERVICE_STOPPED před vrácení `OnStop` metoda ukončení.</span><span class="sxs-lookup"><span data-stu-id="da3af-178">Implement the SERVICE_STOP_PENDING status and return the SERVICE_STOPPED status before the `OnStop` method exits.</span></span>

   <span data-ttu-id="da3af-179">Příklad:</span><span class="sxs-lookup"><span data-stu-id="da3af-179">For example:</span></span>

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

## <a name="add-installers-to-the-service"></a><span data-ttu-id="da3af-180">Přidání instalačních programů do služby</span><span class="sxs-lookup"><span data-stu-id="da3af-180">Add installers to the service</span></span>

<span data-ttu-id="da3af-181">Před spuštěním služby Windows musíte nainstalovat, které je zaregistruje ho s správce řízení služeb.</span><span class="sxs-lookup"><span data-stu-id="da3af-181">Before you run a Windows service, you need to install it, which registers it with the Service Control Manager.</span></span> <span data-ttu-id="da3af-182">Přidání instalačních programů do projektu pro zpracování podrobnosti registrace.</span><span class="sxs-lookup"><span data-stu-id="da3af-182">Add installers to your project to handle the registration details.</span></span>

1. <span data-ttu-id="da3af-183">V **Průzkumníka řešení**, v místní nabídce pro **MyNewService.cs**, nebo **MyNewService.vb**, zvolte **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="da3af-183">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Designer**.</span></span>

2. <span data-ttu-id="da3af-184">V **návrhu** zobrazení, vyberte oblast, pozadí a pak zvolte **přidat instalační program** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="da3af-184">In the **Design** view, select the background area, then choose **Add Installer** from the shortcut menu.</span></span>

     <span data-ttu-id="da3af-185">Ve výchozím nastavení, sada Visual Studio přidá komponentní třídu s názvem `ProjectInstaller`, který obsahuje dva instalační programy, do projektu.</span><span class="sxs-lookup"><span data-stu-id="da3af-185">By default, Visual Studio adds a component class named `ProjectInstaller`, which contains two installers, to your project.</span></span> <span data-ttu-id="da3af-186">Tyto instalační programy jsou pro vaši službu a pro služby přidruženého procesu.</span><span class="sxs-lookup"><span data-stu-id="da3af-186">These installers are for your service and for the service's associated process.</span></span>

3. <span data-ttu-id="da3af-187">V **návrhu** zobrazit **ProjectInstaller**vyberte **serviceInstaller1** vizuálu C# projektu, nebo **ServiceInstaller1**projektu jazyka Visual Basic, zvolte **vlastnosti** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="da3af-187">In the **Design** view for **ProjectInstaller**, select **serviceInstaller1** for a Visual C# project, or **ServiceInstaller1** for a Visual Basic project, then choose **Properties** from the shortcut menu.</span></span>

4. <span data-ttu-id="da3af-188">V **vlastnosti** okna, ověřte <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> je nastavena na **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="da3af-188">In the **Properties** window, verify the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property is set to **MyNewService**.</span></span>

5. <span data-ttu-id="da3af-189">Přidejte text, který se <xref:System.ServiceProcess.ServiceInstaller.Description%2A> vlastnost, jako například *Ukázka služby*.</span><span class="sxs-lookup"><span data-stu-id="da3af-189">Add text to the <xref:System.ServiceProcess.ServiceInstaller.Description%2A> property, such as *A sample service*.</span></span>

     <span data-ttu-id="da3af-190">Tento text se zobrazí **popis** sloupec **služby** okno a popisuje službu pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="da3af-190">This text appears in the **Description** column of the **Services** window and describes the service to the user.</span></span>

    <span data-ttu-id="da3af-191">![Popis služby v okně služby. ](media/windows-service-description.png "Popis služby")</span><span class="sxs-lookup"><span data-stu-id="da3af-191">![Service description in the Services window.](media/windows-service-description.png "Service description")</span></span>

6. <span data-ttu-id="da3af-192">Přidejte text, který má <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="da3af-192">Add text to the <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> property.</span></span> <span data-ttu-id="da3af-193">Například *MyNewService zobrazovaný název*.</span><span class="sxs-lookup"><span data-stu-id="da3af-193">For example, *MyNewService Display Name*.</span></span>

     <span data-ttu-id="da3af-194">Tento text se zobrazí **zobrazovaný název** sloupec **služby** okna.</span><span class="sxs-lookup"><span data-stu-id="da3af-194">This text appears in the **Display Name** column of the **Services** window.</span></span> <span data-ttu-id="da3af-195">Tento název se může lišit od <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> vlastnost, která je název, použije systém (třeba název, který slouží pro `net start` příkaz pro spuštění služby).</span><span class="sxs-lookup"><span data-stu-id="da3af-195">This name can be different from the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property, which is the name the system uses (for example, the name you use for the `net start` command to start your service).</span></span>

7. <span data-ttu-id="da3af-196">Nastavte <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnost <xref:System.ServiceProcess.ServiceStartMode.Automatic> z rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="da3af-196">Set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to <xref:System.ServiceProcess.ServiceStartMode.Automatic> from the drop-down list.</span></span>

8. <span data-ttu-id="da3af-197">Jakmile budete hotovi, **vlastnosti** windows by měl vypadat jako na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="da3af-197">When you're finished, the **Properties** windows should look like the following figure:</span></span>

     <span data-ttu-id="da3af-198">![Vlastnosti Instalační služby systému Windows služby](media/windows-service-installer-properties.png "služby vlastnosti Instalační služby systému Windows")</span><span class="sxs-lookup"><span data-stu-id="da3af-198">![Installer Properties for a Windows service](media/windows-service-installer-properties.png "Windows service installer properties")</span></span>

9. <span data-ttu-id="da3af-199">V **návrhu** zobrazit **ProjectInstaller**, zvolte **serviceProcessInstaller1** vizuálu C# projektu, nebo **ServiceProcessInstaller1**  projektu jazyka Visual Basic, zvolte **vlastnosti** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="da3af-199">In the **Design** view for **ProjectInstaller**, choose **serviceProcessInstaller1** for a Visual C# project, or **ServiceProcessInstaller1** for a Visual Basic project, then choose **Properties** from the shortcut menu.</span></span> <span data-ttu-id="da3af-200">Nastavte <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> vlastnost <xref:System.ServiceProcess.ServiceAccount.LocalSystem> z rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="da3af-200">Set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property to <xref:System.ServiceProcess.ServiceAccount.LocalSystem> from the drop-down list.</span></span>

     <span data-ttu-id="da3af-201">Toto nastavení se nainstaluje službu a běží za použití místního systémového účtu.</span><span class="sxs-lookup"><span data-stu-id="da3af-201">This setting installs the service and runs it by using the local system account.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="da3af-202"><xref:System.ServiceProcess.ServiceAccount.LocalSystem> Účet má širší oprávnění, včetně možnosti zapisovat do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="da3af-202">The <xref:System.ServiceProcess.ServiceAccount.LocalSystem> account has broad permissions, including the ability to write to the event log.</span></span> <span data-ttu-id="da3af-203">Používejte tento účet opatrně, protože může zvýšit riziko napadení škodlivým softwarem.</span><span class="sxs-lookup"><span data-stu-id="da3af-203">Use this account with caution, because it might increase your risk of attacks from malicious software.</span></span> <span data-ttu-id="da3af-204">Pro jiné úlohy zvažte použití <xref:System.ServiceProcess.ServiceAccount.LocalService> účet, který funguje jako neprivilegované uživatele v místním počítači a nabízí pověření anonymního a jakémukoli vzdálenému serveru.</span><span class="sxs-lookup"><span data-stu-id="da3af-204">For other tasks, consider using the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, which acts as a non-privileged user on the local computer and presents anonymous credentials to any remote server.</span></span> <span data-ttu-id="da3af-205">V tomto příkladu se nezdaří, pokud se pokusíte použít <xref:System.ServiceProcess.ServiceAccount.LocalService> účtu, proto, že potřebuje oprávnění k zápisu do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="da3af-205">This example fails if you try to use the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, because it needs permission to write to the event log.</span></span>

<span data-ttu-id="da3af-206">Další informace o instalačních programů najdete v tématu [jak: Přidání instalačních programů do aplikace služby](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="da3af-206">For more information about installers, see [How to: Add installers to your service application](how-to-add-installers-to-your-service-application.md).</span></span>

## <a name="optional-set-startup-parameters"></a><span data-ttu-id="da3af-207">(Volitelné) Nastavit parametry spuštění</span><span class="sxs-lookup"><span data-stu-id="da3af-207">(Optional) Set startup parameters</span></span>

> [!NOTE]
> <span data-ttu-id="da3af-208">Předtím, než se rozhodnete přidat parametry spuštění, zvažte, zda je nejlepší způsob, jak předávání informací do vaší služby.</span><span class="sxs-lookup"><span data-stu-id="da3af-208">Before you decide to add startup parameters, consider whether it's the best way to pass information to your service.</span></span> <span data-ttu-id="da3af-209">I když jsou snadno použitelné a analýzy a uživatel snadno je můžete přepsat, mohou být obtížnější uživatelům objevit a používat bez dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="da3af-209">Although they're easy to use and parse, and a user can easily override them, they might be harder for a user to discover and use without documentation.</span></span> <span data-ttu-id="da3af-210">Obecně platí Pokud vaše služba vyžaduje více než několik parametrů spuštění, měli byste použít registru nebo konfiguračního souboru místo toho.</span><span class="sxs-lookup"><span data-stu-id="da3af-210">Generally, if your service requires more than just a few startup parameters, you should use the registry or a configuration file instead.</span></span>

<span data-ttu-id="da3af-211">Služba Windows může přijmout argumenty příkazového řádku, nebo parametry spuštění.</span><span class="sxs-lookup"><span data-stu-id="da3af-211">A Windows service can accept command-line arguments, or startup parameters.</span></span> <span data-ttu-id="da3af-212">Když přidáte kód do parametrů spuštění procesu, uživatele můžete začít vaši službu s vlastní vlastní spouštěcí parametry v okně Vlastnosti služby.</span><span class="sxs-lookup"><span data-stu-id="da3af-212">When you add code to process startup parameters, a user can start your service with their own custom startup parameters in the service properties window.</span></span> <span data-ttu-id="da3af-213">Tyto spouštěcí parametry nejsou však zachované při příštím spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="da3af-213">However, these startup parameters aren't persisted the next time the service starts.</span></span> <span data-ttu-id="da3af-214">Pokud chcete nastavit spouštěcí parametry trvale, jejich nastavení v registru.</span><span class="sxs-lookup"><span data-stu-id="da3af-214">To set startup parameters permanently, set them in the registry.</span></span>

<span data-ttu-id="da3af-215">Každá služba Windows má záznam v registru pod **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services** podklíči.</span><span class="sxs-lookup"><span data-stu-id="da3af-215">Each Windows service has a registry entry under the **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services** subkey.</span></span> <span data-ttu-id="da3af-216">V podklíči každou službu, použijte **parametry** podklíč pro ukládání informací, které můžou přistupovat k vaší služby.</span><span class="sxs-lookup"><span data-stu-id="da3af-216">Under each service's subkey, use the **Parameters** subkey to store information that your service can access.</span></span> <span data-ttu-id="da3af-217">Konfigurační soubory aplikace můžete použít pro službu Windows stejným způsobem jako u jiných typů aplikací.</span><span class="sxs-lookup"><span data-stu-id="da3af-217">You can use application configuration files for a Windows service the same way you do for other types of programs.</span></span> <span data-ttu-id="da3af-218">Ukázkový kód, naleznete v tématu <xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="da3af-218">For sample code, see <xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType>.</span></span>

### <a name="to-add-startup-parameters"></a><span data-ttu-id="da3af-219">Chcete-li přidat parametry spuštění</span><span class="sxs-lookup"><span data-stu-id="da3af-219">To add startup parameters</span></span>

1. <span data-ttu-id="da3af-220">Vyberte **Program.cs**, nebo **MyNewService.Designer.vb**, klikněte na tlačítko **zobrazit kód** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="da3af-220">Select **Program.cs**, or **MyNewService.Designer.vb**, then choose **View Code** from the shortcut menu.</span></span> <span data-ttu-id="da3af-221">V `Main` metodu, změňte kód pro přidání vstupního parametru a předejte jej do konstruktoru služby:</span><span class="sxs-lookup"><span data-stu-id="da3af-221">In the `Main` method, change the code to add an input parameter and pass it to the service constructor:</span></span>

   [!code-csharp[VbRadconService](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/Program-add-parameter.cs?highlight=1,6)]
   [!code-vb[VbRadconService](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.Designer-add-parameter.vb?highlight=1-2)]

2. <span data-ttu-id="da3af-222">V **MyNewService.cs**, nebo **MyNewService.vb**, změnit `MyNewService` konstruktor zpracovat vstupní parametr následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="da3af-222">In **MyNewService.cs**, or **MyNewService.vb**, change the `MyNewService` constructor to process the input parameter as follows:</span></span>

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

   <span data-ttu-id="da3af-223">Tento kód nastaví název zdroje a protokol událostí podle spouštěcí parametry, které uživatel zadává.</span><span class="sxs-lookup"><span data-stu-id="da3af-223">This code sets the event source and log name according to the startup parameters that the user supplies.</span></span> <span data-ttu-id="da3af-224">Pokud nejsou dodány žádné argumenty, použije výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="da3af-224">If no arguments are supplied, it uses default values.</span></span>

3. <span data-ttu-id="da3af-225">Chcete-li zadat argumenty příkazového řádku, přidejte následující kód, který `ProjectInstaller` třídy v **ProjectInstaller.cs**, nebo **ProjectInstaller.vb**:</span><span class="sxs-lookup"><span data-stu-id="da3af-225">To specify the command-line arguments, add the following code to the `ProjectInstaller` class in **ProjectInstaller.cs**, or **ProjectInstaller.vb**:</span></span>

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

   <span data-ttu-id="da3af-226">Tato hodnota se obvykle obsahuje úplnou cestu ke spustitelnému souboru pro službu Windows.</span><span class="sxs-lookup"><span data-stu-id="da3af-226">Typically, this value contains the full path to the executable for the Windows service.</span></span> <span data-ttu-id="da3af-227">Služba správně je nutné zadat znaky uvozovek pro cestu a jednotlivé jednotlivé parametry.</span><span class="sxs-lookup"><span data-stu-id="da3af-227">For the service to start up correctly, the user must supply quotation marks for the path and each individual parameter.</span></span> <span data-ttu-id="da3af-228">Uživatel může změnit na parametry **ImagePath** záznam v registru můžete změnit parametry spuštění pro službu Windows.</span><span class="sxs-lookup"><span data-stu-id="da3af-228">A user can change the parameters in the **ImagePath** registry entry to change the startup parameters for the Windows service.</span></span> <span data-ttu-id="da3af-229">Je však lepší způsob, a změňte hodnotu prostřednictvím kódu programu zpřístupnění funkce a uživatelsky přívětivé, například pomocí nástroje pro správu nebo konfigurace.</span><span class="sxs-lookup"><span data-stu-id="da3af-229">However, a better way is to change the value programmatically and expose the functionality in a user-friendly way, such as by using a management or configuration utility.</span></span>

## <a name="build-the-service"></a><span data-ttu-id="da3af-230">Vytvoření služby</span><span class="sxs-lookup"><span data-stu-id="da3af-230">Build the service</span></span>

1. <span data-ttu-id="da3af-231">V **Průzkumníka řešení**, zvolte **vlastnosti** z místní nabídky pro **MyNewService** projektu.</span><span class="sxs-lookup"><span data-stu-id="da3af-231">In **Solution Explorer**, choose **Properties** from the shortcut menu for the **MyNewService** project.</span></span>

   <span data-ttu-id="da3af-232">Stránky vlastností pro váš projekt se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="da3af-232">The property pages for your project appear.</span></span>

2. <span data-ttu-id="da3af-233">Na **aplikace** kartě **spouštěcí objekt** klikněte na položku **MyNewService.Program**, nebo **Sub Main** pro projekty jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="da3af-233">On the **Application** tab, in the **Startup object** list, choose **MyNewService.Program**, or **Sub Main** for Visual Basic projects.</span></span>

3. <span data-ttu-id="da3af-234">Sestavte projekt, v **Průzkumníka řešení**, zvolte **sestavení** z místní nabídky projektu (nebo stiskněte klávesu **Ctrl**+**Shift** + **B**).</span><span class="sxs-lookup"><span data-stu-id="da3af-234">To build the project, in **Solution Explorer**, choose **Build** from the shortcut menu for your project (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="install-the-service"></a><span data-ttu-id="da3af-235">Instalace služby</span><span class="sxs-lookup"><span data-stu-id="da3af-235">Install the service</span></span>

<span data-ttu-id="da3af-236">Teď, když jste vytvořili službu Windows, můžete ho nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="da3af-236">Now that you've built the Windows service, you can install it.</span></span> <span data-ttu-id="da3af-237">Pro instalaci služby Windows, musíte mít pověření správce na počítači, kde je nainstalován.</span><span class="sxs-lookup"><span data-stu-id="da3af-237">To install a Windows service, you must have administrator credentials on the computer where it's installed.</span></span>

1. <span data-ttu-id="da3af-238">Otevřít [Developer Command Prompt pro sadu Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs) s přihlašovacími údaji správce.</span><span class="sxs-lookup"><span data-stu-id="da3af-238">Open [Developer Command Prompt for Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs) with administrative credentials.</span></span> <span data-ttu-id="da3af-239">Z Windows **Start** nabídce vyberte možnost **Developer Command Prompt for VS 2017** ve složce aplikace Visual Studio vyberte **Další** > **spustit jako Správce** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="da3af-239">From the Windows **Start** menu, select **Developer Command Prompt for VS 2017** in the Visual Studio folder, then select **More** > **Run as Administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="da3af-240">V **Developer Command Prompt pro sadu Visual Studio** okno, přejděte do složky, který obsahuje výstup projektu (ve výchozím nastavení, *\bin\Debug* podadresáře projektu).</span><span class="sxs-lookup"><span data-stu-id="da3af-240">In the **Developer Command Prompt for Visual Studio** window, navigate to the folder that contains your project's output (by default, the *\bin\Debug* subdirectory of your project).</span></span>

3. <span data-ttu-id="da3af-241">Zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="da3af-241">Enter the following command:</span></span>

    ```shell
    installutil MyNewService.exe
    ```

    <span data-ttu-id="da3af-242">Pokud je služba nainstalována úspěšně, příkaz oznámí úspěšné dokončení.</span><span class="sxs-lookup"><span data-stu-id="da3af-242">If the service installs successfully, the command reports success.</span></span>

    <span data-ttu-id="da3af-243">Pokud systém nemůže najít *installutil.exe*, ujistěte se, že existuje ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="da3af-243">If the system can't find *installutil.exe*, make sure that it exists on your computer.</span></span> <span data-ttu-id="da3af-244">Tento nástroj je nainstalován pomocí rozhraní .NET Framework do složky *% windir%\Microsoft.NET\Framework[64]\\&lt;verzi rozhraní framework&gt;*.</span><span class="sxs-lookup"><span data-stu-id="da3af-244">This tool is installed with the .NET Framework to the folder *%windir%\Microsoft.NET\Framework[64]\\&lt;framework version&gt;*.</span></span> <span data-ttu-id="da3af-245">Například výchozí cesta pro 64bitovou verzi je *%windir%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="da3af-245">For example, the default path for the 64-bit version is *%windir%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span></span>

    <span data-ttu-id="da3af-246">Pokud **installutil.exe** proces selže, najdete v protokolu instalace a zjistěte, proč.</span><span class="sxs-lookup"><span data-stu-id="da3af-246">If the **installutil.exe** process fails, check the install log to find out why.</span></span> <span data-ttu-id="da3af-247">Ve výchozím nastavení v protokolu je ve stejné složce jako spustitelný soubor služby.</span><span class="sxs-lookup"><span data-stu-id="da3af-247">By default, the log is in the same folder as the service executable.</span></span> <span data-ttu-id="da3af-248">Instalace může selhat, pokud:</span><span class="sxs-lookup"><span data-stu-id="da3af-248">The installation can fail if:</span></span>
    - <span data-ttu-id="da3af-249"><xref:System.ComponentModel.RunInstallerAttribute> Třída není k dispozici na `ProjectInstaller` třídy.</span><span class="sxs-lookup"><span data-stu-id="da3af-249">The <xref:System.ComponentModel.RunInstallerAttribute> class isn't present on the `ProjectInstaller` class.</span></span>
    - <span data-ttu-id="da3af-250">Atribut není nastavená na `true`.</span><span class="sxs-lookup"><span data-stu-id="da3af-250">The attribute isn't set to `true`.</span></span>
    - <span data-ttu-id="da3af-251">`ProjectInstaller` Třída není definován jako `public`.</span><span class="sxs-lookup"><span data-stu-id="da3af-251">The `ProjectInstaller` class isn't defined as `public`.</span></span>

<span data-ttu-id="da3af-252">Další informace najdete v tématu [jak: Instalace a odinstalace služeb](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="da3af-252">For more information, see [How to: Install and uninstall services](how-to-install-and-uninstall-services.md).</span></span>

## <a name="start-and-run-the-service"></a><span data-ttu-id="da3af-253">Spuštění a spuštění služby</span><span class="sxs-lookup"><span data-stu-id="da3af-253">Start and run the service</span></span>

1. <span data-ttu-id="da3af-254">Ve Windows, otevřete **služby** aplikace klasické pracovní plochy.</span><span class="sxs-lookup"><span data-stu-id="da3af-254">In Windows, open the **Services** desktop app.</span></span> <span data-ttu-id="da3af-255">Stisknutím klávesy **Windows**+**R** otevřít **spustit** zadejte *services.msc*a potom stiskněte klávesu **Enter** nebo vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="da3af-255">Press **Windows**+**R** to open the **Run** box, enter *services.msc*, and then press **Enter** or select **OK**.</span></span>

     <span data-ttu-id="da3af-256">Měli byste vidět vaše služba uvedená v **služby**, zobrazené abecedně podle zobrazovaného názvu, kterou jste nastavili pro něj.</span><span class="sxs-lookup"><span data-stu-id="da3af-256">You should see your service listed in **Services**, displayed alphabetically by the display name that you set for it.</span></span>

     ![MyNewService v okně služby.](media/windowsservices-serviceswindow.PNG)

2. <span data-ttu-id="da3af-258">Chcete-li spustit službu, zvolte **Start** z místní nabídky služby.</span><span class="sxs-lookup"><span data-stu-id="da3af-258">To start the service, choose **Start** from the service's shortcut menu.</span></span>

3. <span data-ttu-id="da3af-259">Chcete-li zastavit službu, zvolte **Zastavit** z místní nabídky služby.</span><span class="sxs-lookup"><span data-stu-id="da3af-259">To stop the service, choose **Stop** from the service's shortcut menu.</span></span>

4. <span data-ttu-id="da3af-260">(Volitelné) Z příkazového řádku, použijte příkazy **net start &lt;název služby&gt;**  a **net stop &lt;název služby&gt;**  spuštění a zastavení služby.</span><span class="sxs-lookup"><span data-stu-id="da3af-260">(Optional) From the command line, use the commands **net start &lt;service name&gt;** and **net stop &lt;service name&gt;** to start and stop your service.</span></span>

### <a name="verify-the-event-log-output-of-your-service"></a><span data-ttu-id="da3af-261">Ověření výstupu služby v protokolu událostí</span><span class="sxs-lookup"><span data-stu-id="da3af-261">Verify the event log output of your service</span></span>

1. <span data-ttu-id="da3af-262">Ve Windows, otevřete **Prohlížeč událostí** aplikace klasické pracovní plochy.</span><span class="sxs-lookup"><span data-stu-id="da3af-262">In Windows, open the **Event Viewer** desktop app.</span></span> <span data-ttu-id="da3af-263">Zadejte *Prohlížeč událostí* ve službě Windows search panelu a pak vyberte **Prohlížeč událostí** ve výsledcích hledání.</span><span class="sxs-lookup"><span data-stu-id="da3af-263">Enter *Event Viewer* in the Windows search bar, and then select **Event Viewer** from the search results.</span></span>

   > [!TIP]
   > <span data-ttu-id="da3af-264">V sadě Visual Studio, dostanete protokoly událostí tak, že otevřete **Průzkumníka serveru** z **zobrazení** nabídce (nebo stiskněte klávesu **Ctrl**+**Alt** + **S**) rozšiřuje i **protokoly událostí** uzel v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="da3af-264">In Visual Studio, you can access event logs by opening **Server Explorer** from the **View** menu (or press **Ctrl**+**Alt**+**S**) and expanding the **Event Logs** node for the local computer.</span></span>

2. <span data-ttu-id="da3af-265">V **Prohlížeč událostí**, rozbalte **protokoly aplikací a služeb**.</span><span class="sxs-lookup"><span data-stu-id="da3af-265">In **Event Viewer**, expand **Applications and Services Logs**.</span></span>

3. <span data-ttu-id="da3af-266">Vyhledejte výpis pro **MyNewLog** (nebo **MyLogFile1** Pokud jste postupovali podle postupu pro přidání argumentů příkazového řádku) a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="da3af-266">Locate the listing for **MyNewLog** (or **MyLogFile1** if you followed the procedure to add command-line arguments) and expand it.</span></span> <span data-ttu-id="da3af-267">Měli byste vidět položky pro dvě akce (spouštění a zastavování), které provádí vaší služby.</span><span class="sxs-lookup"><span data-stu-id="da3af-267">You should see the entries for the two actions (start and stop) that your service performed.</span></span>

     ![Pomocí prohlížeče událostí zobrazíte položky protokolu událostí](media/windows-service-event-viewer.png)

## <a name="clean-up-resources"></a><span data-ttu-id="da3af-269">Vyčištění prostředků</span><span class="sxs-lookup"><span data-stu-id="da3af-269">Clean up resources</span></span>

<span data-ttu-id="da3af-270">Pokud už nepotřebujete Windows service app, můžete ho odebrat.</span><span class="sxs-lookup"><span data-stu-id="da3af-270">If you no longer need the Windows service app, you can remove it.</span></span>

1. <span data-ttu-id="da3af-271">Otevřít **Developer Command Prompt pro sadu Visual Studio** s přihlašovacími údaji správce.</span><span class="sxs-lookup"><span data-stu-id="da3af-271">Open **Developer Command Prompt for Visual Studio** with administrative credentials.</span></span>

2. <span data-ttu-id="da3af-272">V **Developer Command Prompt pro sadu Visual Studio** okno, přejděte do složky, který obsahuje výstup projektu.</span><span class="sxs-lookup"><span data-stu-id="da3af-272">In the **Developer Command Prompt for Visual Studio** window, navigate to the folder that contains your project's output.</span></span>

3. <span data-ttu-id="da3af-273">Zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="da3af-273">Enter the following command:</span></span>

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   <span data-ttu-id="da3af-274">Pokud služba úspěšně odinstalována, příkaz hlásí, že vaše služba byla úspěšně odebrána.</span><span class="sxs-lookup"><span data-stu-id="da3af-274">If the service uninstalls successfully, the command reports that your service was successfully removed.</span></span> <span data-ttu-id="da3af-275">Další informace najdete v tématu [jak: Instalace a odinstalace služeb](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="da3af-275">For more information, see [How to: Install and uninstall services](how-to-install-and-uninstall-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="da3af-276">Další kroky</span><span class="sxs-lookup"><span data-stu-id="da3af-276">Next steps</span></span>

<span data-ttu-id="da3af-277">Teď, když jste vytvořili službu, můžete:</span><span class="sxs-lookup"><span data-stu-id="da3af-277">Now that you've created the service, you can:</span></span>

- <span data-ttu-id="da3af-278">Vytvořte samostatný instalační program ostatním uživatelům pro instalaci služby Windows.</span><span class="sxs-lookup"><span data-stu-id="da3af-278">Create a standalone setup program for others to use to install your Windows service.</span></span> <span data-ttu-id="da3af-279">Použití [sadu nástrojů WiX Toolset](http://wixtoolset.org/) vytvořit instalační službu pro službu Windows.</span><span class="sxs-lookup"><span data-stu-id="da3af-279">Use the [WiX Toolset](http://wixtoolset.org/) to create an installer for a Windows service.</span></span> <span data-ttu-id="da3af-280">Další příklady naleznete v tématu [vytvoření instalačního balíčku](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span><span class="sxs-lookup"><span data-stu-id="da3af-280">For other ideas, see [Create an installer package](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span></span>

- <span data-ttu-id="da3af-281">Prozkoumejte <xref:System.ServiceProcess.ServiceController> komponenta, která vám umožní odesílat příkazy do služby, které jste nainstalovali.</span><span class="sxs-lookup"><span data-stu-id="da3af-281">Explore the <xref:System.ServiceProcess.ServiceController> component, which enables you to send commands to the service you've installed.</span></span>

- <span data-ttu-id="da3af-282">Namísto vytvoření protokolu událostí při spuštění aplikace, použijte instalační program k vytvoření protokolu událostí při instalaci aplikace.</span><span class="sxs-lookup"><span data-stu-id="da3af-282">Instead of creating the event log when the application runs, use an installer to create an event log when you install the application.</span></span> <span data-ttu-id="da3af-283">Když odinstalujete aplikaci je protokol událostí odstraní instalační služby.</span><span class="sxs-lookup"><span data-stu-id="da3af-283">The event log is deleted by the installer when you uninstall the application.</span></span> <span data-ttu-id="da3af-284">Další informace naleznete v tématu <xref:System.Diagnostics.EventLogInstaller>.</span><span class="sxs-lookup"><span data-stu-id="da3af-284">For more information, see <xref:System.Diagnostics.EventLogInstaller>.</span></span>

## <a name="see-also"></a><span data-ttu-id="da3af-285">Viz také:</span><span class="sxs-lookup"><span data-stu-id="da3af-285">See also</span></span>

- [<span data-ttu-id="da3af-286">Aplikace služby Windows</span><span class="sxs-lookup"><span data-stu-id="da3af-286">Windows service applications</span></span>](index.md)
- [<span data-ttu-id="da3af-287">Úvod do aplikace služby Windows</span><span class="sxs-lookup"><span data-stu-id="da3af-287">Introduction to Windows service applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="da3af-288">Postupy: Ladění aplikace služby Windows</span><span class="sxs-lookup"><span data-stu-id="da3af-288">How to: Debug Windows service applications</span></span>](how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="da3af-289">Služby (Windows)</span><span class="sxs-lookup"><span data-stu-id="da3af-289">Services (Windows)</span></span>](/windows/desktop/Services/services)
