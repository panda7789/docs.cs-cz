---
title: Vytvoření aplikace služby Windows v sadě Visual Studio
ms.date: 09/10/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows service applications, walkthroughs
- Windows service applications, creating
ms.assetid: e24d8a3d-edc6-485c-b6e0-5672d91fb607
author: ghogen
manager: douge
ms.openlocfilehash: 27acdac5d34b96dd04fec1bb763edec9077ff928
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46324415"
---
# <a name="walkthrough-create-a-windows-service-app"></a><span data-ttu-id="93962-102">Návod: Vytvoření aplikace služby Windows</span><span class="sxs-lookup"><span data-stu-id="93962-102">Walkthrough: Create a Windows service app</span></span>

<span data-ttu-id="93962-103">Tento článek ukazuje, jak vytvořit jednoduchou aplikaci služby Windows v sadě Visual Studio, která zapisuje zprávy do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="93962-103">This article demonstrates how to create a simple Windows service app in Visual Studio that writes messages to an event log.</span></span>

## <a name="create-a-service"></a><span data-ttu-id="93962-104">Vytvoření služby</span><span class="sxs-lookup"><span data-stu-id="93962-104">Create a service</span></span>

<span data-ttu-id="93962-105">Pokud chcete začít, vytvořte projekt a nastavte hodnoty, které jsou požadovány pro správné fungování služby.</span><span class="sxs-lookup"><span data-stu-id="93962-105">To begin, create the project and set values that are required for the service to function correctly.</span></span>

1. <span data-ttu-id="93962-106">V sadě Visual Studio v panelu nabídek zvolte **souboru** > **nový** > **projektu** (nebo stiskněte klávesu **Ctrl** + **Shift**+**N**) Chcete-li otevřít **nový projekt** dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="93962-106">In Visual Studio, on the menu bar, choose **File** > **New** > **Project** (or press **Ctrl**+**Shift**+**N**) to open the **New Project** dialog.</span></span>

2. <span data-ttu-id="93962-107">Vyhledejte a vyberte **Windows Service** šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="93962-107">Navigate to and select the **Windows Service** project template.</span></span> <span data-ttu-id="93962-108">Rozbalte **nainstalováno** > [**Visual C#** nebo **jazyka Visual Basic**] > **Windows Desktop**, nebo typ **Windows Service** do vyhledávacího pole v pravém horním rohu.</span><span class="sxs-lookup"><span data-stu-id="93962-108">Expand **Installed** > [**Visual C#** or **Visual Basic**] > **Windows Desktop**, or type **Windows Service** in the search box on the upper right.</span></span>

   ![Šablona služby Windows v dialogu Nový projekt v sadě Visual Studio](media/new-project-dialog.png)

   > [!NOTE]
   > <span data-ttu-id="93962-110">Pokud se nezobrazí **Windows Service** šablony, je nutné nainstalovat **vývoj desktopových aplikací .NET** pracovního vytížení.</span><span class="sxs-lookup"><span data-stu-id="93962-110">If you don't see the **Windows Service** template, you may need to install the **.NET desktop development** workload.</span></span> <span data-ttu-id="93962-111">V **nový projekt** dialogového okna, klikněte na odkaz, který říká **otevřít instalační program Visual Studio** v levé dolní části.</span><span class="sxs-lookup"><span data-stu-id="93962-111">In the **New Project** dialog, click the link that says **Open Visual Studio Installer** on the lower left.</span></span> <span data-ttu-id="93962-112">V **instalační program sady Visual Studio**, vyberte **vývoj desktopových aplikací .NET** úloh a klikněte na tlačítko **změnit**.</span><span class="sxs-lookup"><span data-stu-id="93962-112">In **Visual Studio Installer**, select the **.NET desktop development** workload and then choose **Modify**.</span></span>

3. <span data-ttu-id="93962-113">Pojmenujte projekt **MyNewService**a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="93962-113">Name the project **MyNewService**, and then choose **OK**.</span></span>

   <span data-ttu-id="93962-114">Šablona projektu zahrnuje komponentní třídu s názvem `Service1` , která dědí z <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="93962-114">The project template includes a component class named `Service1` that inherits from <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="93962-115">Obsahuje velkou část základního kódu služby, jako je například kód ke spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="93962-115">It includes much of the basic service code, such as the code to start the service.</span></span>

## <a name="rename-the-service"></a><span data-ttu-id="93962-116">Přejmenování služby</span><span class="sxs-lookup"><span data-stu-id="93962-116">Rename the service</span></span>

<span data-ttu-id="93962-117">Přejmenování služby z **Service1** k **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="93962-117">Rename the service from **Service1** to **MyNewService**.</span></span>

1. <span data-ttu-id="93962-118">V **návrhu** zobrazení Service1.cs (nebo Service1.vb), klikněte na odkaz pro **přepněte do zobrazení kódu**.</span><span class="sxs-lookup"><span data-stu-id="93962-118">In the **Design** view for Service1.cs (or Service1.vb), click the link to **switch to code view**.</span></span> <span data-ttu-id="93962-119">Klikněte pravým tlačítkem na **Service1** a vyberte **přejmenovat** v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="93962-119">Right-click on **Service1** and select **Rename** from the context menu.</span></span> <span data-ttu-id="93962-120">Zadejte **MyNewService** a potom stiskněte klávesu **Enter** nebo klikněte na tlačítko **použít**.</span><span class="sxs-lookup"><span data-stu-id="93962-120">Enter **MyNewService** and then press **Enter** or click **Apply**.</span></span>

2. <span data-ttu-id="93962-121">V **vlastnosti** okně **Service1.cs [Design]** nebo **Service1.vb [Design]**, změnit **ServiceName** hodnota, která má **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="93962-121">In the **Properties** window for **Service1.cs [Design]** or **Service1.vb [Design]**, change the **ServiceName** value to **MyNewService**.</span></span>

3. <span data-ttu-id="93962-122">V **Průzkumníka řešení**, přejmenujte **Service1.cs** k **MyNewService.cs**, nebo přejmenujte **Service1.vb** k  **MyNewService.vb**.</span><span class="sxs-lookup"><span data-stu-id="93962-122">In **Solution Explorer**, rename **Service1.cs** to **MyNewService.cs**, or rename **Service1.vb** to **MyNewService.vb**.</span></span>

## <a name="add-features-to-the-service"></a><span data-ttu-id="93962-123">Přidání funkcí do služby</span><span class="sxs-lookup"><span data-stu-id="93962-123">Add features to the service</span></span>

<span data-ttu-id="93962-124">V této části přidáte do služby Windows vlastního protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="93962-124">In this section, you add a custom event log to the Windows service.</span></span> <span data-ttu-id="93962-125">Protokoly událostí nejsou nijak spojené se službami systému Windows.</span><span class="sxs-lookup"><span data-stu-id="93962-125">Event logs are not associated in any way with Windows services.</span></span> <span data-ttu-id="93962-126"><xref:System.Diagnostics.EventLog> Součást slouží jako příklad typ součásti, můžete přidat do služby Windows.</span><span class="sxs-lookup"><span data-stu-id="93962-126">The <xref:System.Diagnostics.EventLog> component is used here as an example of the type of component you can add to a Windows service.</span></span>

### <a name="add-custom-event-log-functionality"></a><span data-ttu-id="93962-127">Přidání funkce vlastního protokolu událostí</span><span class="sxs-lookup"><span data-stu-id="93962-127">Add custom event log functionality</span></span>

1. <span data-ttu-id="93962-128">V **Průzkumníka řešení**, otevřete kontextovou nabídku pro **MyNewService.cs** nebo **MyNewService.vb**a klikněte na tlačítko **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="93962-128">In **Solution Explorer**, open the context menu for **MyNewService.cs** or **MyNewService.vb**, and then choose **View Designer**.</span></span>

2. <span data-ttu-id="93962-129">Z **součásti** část **nástrojů**, přetáhněte <xref:System.Diagnostics.EventLog> komponentu do návrháře.</span><span class="sxs-lookup"><span data-stu-id="93962-129">From the **Components** section of the **Toolbox**, drag an <xref:System.Diagnostics.EventLog> component to the designer.</span></span>

3. <span data-ttu-id="93962-130">V **Průzkumníka řešení**, otevřete kontextovou nabídku pro **MyNewService.cs** nebo **MyNewService.vb**a klikněte na tlačítko **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="93962-130">In **Solution Explorer**, open the context menu for **MyNewService.cs** or **MyNewService.vb**, and then choose **View Code**.</span></span>

4. <span data-ttu-id="93962-131">Upravte konstruktor pro definování vlastního protokolu událostí:</span><span class="sxs-lookup"><span data-stu-id="93962-131">Edit the constructor to define a custom event log:</span></span>

   ```csharp
   public MyNewService()
   {
        InitializeComponent();

        eventLog1 = new System.Diagnostics.EventLog();
        if (!System.Diagnostics.EventLog.SourceExists("MySource"))
        {
            System.Diagnostics.EventLog.CreateEventSource(
                "MySource", "MyNewLog");
        }
        eventLog1.Source = "MySource";
        eventLog1.Log = "MyNewLog";
    }
   ```

   [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]

### <a name="define-what-occurs-when-the-service-starts"></a><span data-ttu-id="93962-132">Definujte, co se stane při spuštění služby</span><span class="sxs-lookup"><span data-stu-id="93962-132">Define what occurs when the service starts</span></span>

<span data-ttu-id="93962-133">V editoru kódu vyhledejte <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodu, která byla automaticky přepsána při vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="93962-133">In the code editor, locate the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method that was automatically overridden when you created the project.</span></span> <span data-ttu-id="93962-134">Přidáte řádek kódu, který zapíše položku do protokolu událostí při spuštění služby:</span><span class="sxs-lookup"><span data-stu-id="93962-134">Add a line of code that writes an entry to the event log when the service starts:</span></span>

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

<span data-ttu-id="93962-135">Aplikace služby byla navržena jako dlouhotrvající, takže obvykle dotazuje nebo něco monitoruje v systému.</span><span class="sxs-lookup"><span data-stu-id="93962-135">A service application is designed to be long-running, so it usually polls or monitors something in the system.</span></span> <span data-ttu-id="93962-136">Monitorování je nastavení <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="93962-136">The monitoring is set up in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span> <span data-ttu-id="93962-137">Ale <xref:System.ServiceProcess.ServiceBase.OnStart%2A> neumí skutečně monitorování.</span><span class="sxs-lookup"><span data-stu-id="93962-137">However, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> doesn’t actually do the monitoring.</span></span> <span data-ttu-id="93962-138"><xref:System.ServiceProcess.ServiceBase.OnStart%2A> Metoda musí vracet v operačním systému po operaci služby.</span><span class="sxs-lookup"><span data-stu-id="93962-138">The <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method must return to the operating system after the service's operation has begun.</span></span> <span data-ttu-id="93962-139">Nesmí spustit nekonečnou smyčku ani blokovat.</span><span class="sxs-lookup"><span data-stu-id="93962-139">It must not loop forever or block.</span></span> <span data-ttu-id="93962-140">Pokud chcete nastavit jednoduchý mechanismus dotazování, můžete použít <xref:System.Timers.Timer?displayProperty=nameWithType> komponenty následujícím způsobem: V <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodu, nastavení parametrů na komponentu a potom nastavte <xref:System.Timers.Timer.Enabled%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="93962-140">To set up a simple polling mechanism, you can use the <xref:System.Timers.Timer?displayProperty=nameWithType> component as follows: In the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, set parameters on the component, and then set the <xref:System.Timers.Timer.Enabled%2A> property to `true`.</span></span> <span data-ttu-id="93962-141">Časovač vyvolává události ve vašem kódu pravidelně, po kterém může služba provádět monitorování.</span><span class="sxs-lookup"><span data-stu-id="93962-141">The timer raises events in your code periodically, at which time your service could do its monitoring.</span></span> <span data-ttu-id="93962-142">K tomu můžete použít následující kód:</span><span class="sxs-lookup"><span data-stu-id="93962-142">You can use the following code to do this:</span></span>

```csharp
// Set up a timer that triggers every minute.
System.Timers.Timer timer = new System.Timers.Timer();
timer.Interval = 60000; // 60 seconds
timer.Elapsed += new System.Timers.ElapsedEventHandler(this.OnTimer);
timer.Start();
```

```vb
' Set up a timer that triggers every minute.
Dim timer As System.Timers.Timer = New System.Timers.Timer()
timer.Interval = 60000 ' 60 seconds
AddHandler timer.Elapsed, AddressOf Me.OnTimer
timer.Start()
```

<span data-ttu-id="93962-143">Přidání členské proměnné třídy.</span><span class="sxs-lookup"><span data-stu-id="93962-143">Add a member variable to the class.</span></span> <span data-ttu-id="93962-144">Obsahuje identifikátor další události pro zápis do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="93962-144">It contains the identifier of the next event to write into the event log.</span></span>

```csharp
private int eventId = 1;
```

```vb
Private eventId As Integer = 1
```

<span data-ttu-id="93962-145">Přidáte nové metody pro zpracování události časovače:</span><span class="sxs-lookup"><span data-stu-id="93962-145">Add a new method to handle the timer event:</span></span>

```csharp
public void OnTimer(object sender, System.Timers.ElapsedEventArgs args)
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

<span data-ttu-id="93962-146">Můžete chtít provádět úlohy pomocí pracovních vláken na pozadí místo spouštění veškerou práci na hlavním vlákně.</span><span class="sxs-lookup"><span data-stu-id="93962-146">You might want to perform tasks by using background worker threads instead of running all your work on the main thread.</span></span> <span data-ttu-id="93962-147">Další informace naleznete v tématu <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="93962-147">For more information, see <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span></span>

### <a name="define-what-occurs-when-the-service-is-stopped"></a><span data-ttu-id="93962-148">Definujte, co se stane při zastavení služby</span><span class="sxs-lookup"><span data-stu-id="93962-148">Define what occurs when the service is stopped</span></span>

<span data-ttu-id="93962-149">Přidat řádek kódu, který <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metodu, která přidá položku do protokolu událostí po zastavení služby:</span><span class="sxs-lookup"><span data-stu-id="93962-149">Add a line of code to the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method that adds an entry to the event log when the service is stopped:</span></span>

```csharp
eventLog1.WriteEntry("In OnStop.");
```

[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a><span data-ttu-id="93962-150">Definování dalších akcí služby</span><span class="sxs-lookup"><span data-stu-id="93962-150">Define other actions for the service</span></span>

<span data-ttu-id="93962-151">Je možné přepsat <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, a <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> metody definovat další zpracování pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="93962-151">You can override the <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, and <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> methods to define additional processing for your component.</span></span> <span data-ttu-id="93962-152">Následující kód ukazuje, jak je možné přepsat <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> metody:</span><span class="sxs-lookup"><span data-stu-id="93962-152">The following code shows how you can override the <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> method:</span></span>

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]

<span data-ttu-id="93962-153">Některé vlastní akce musejí nastat při instalaci služby Windows podle <xref:System.Configuration.Install.Installer> třídy.</span><span class="sxs-lookup"><span data-stu-id="93962-153">Some custom actions have to occur when a Windows service is installed by the <xref:System.Configuration.Install.Installer> class.</span></span> <span data-ttu-id="93962-154">Sada Visual Studio může vytvořit tyto instalační programy speciálně pro službu systému Windows a přidat je do projektu.</span><span class="sxs-lookup"><span data-stu-id="93962-154">Visual Studio can create these installers specifically for a Windows service and add them to your project.</span></span>

## <a name="set-service-status"></a><span data-ttu-id="93962-155">Nastavit stav služby</span><span class="sxs-lookup"><span data-stu-id="93962-155">Set service status</span></span>

<span data-ttu-id="93962-156">Služby oznamují svůj stav tak, aby uživatelé můžete říct, jestli služba správně funguje ke správci řízení služeb.</span><span class="sxs-lookup"><span data-stu-id="93962-156">Services report their status to the Service Control Manager, so that users can tell whether a service is functioning correctly.</span></span> <span data-ttu-id="93962-157">Ve výchozím nastavení, služby, které dědí <xref:System.ServiceProcess.ServiceBase> omezenou sadu nastavení, stav, včetně zastaven, pozastaven a spouštění sestav.</span><span class="sxs-lookup"><span data-stu-id="93962-157">By default, services that inherit from <xref:System.ServiceProcess.ServiceBase> report a limited set of status settings, including Stopped, Paused, and Running.</span></span> <span data-ttu-id="93962-158">Pokud služba trvá o něco se spustí ho může být užitečné oznámit spuštění čeká na stav.</span><span class="sxs-lookup"><span data-stu-id="93962-158">If a service takes a little while to start up, it might be helpful to report a Start Pending status.</span></span> <span data-ttu-id="93962-159">Nastavení stavu čeká na spuštění a zastavení probíhající můžete také implementovat přidáním kódu, která volá Windows [SetServiceStatus funkce](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus).</span><span class="sxs-lookup"><span data-stu-id="93962-159">You can also implement the Start Pending and Stop Pending status settings by adding code that calls into the Windows [SetServiceStatus function](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus).</span></span>

<span data-ttu-id="93962-160">K implementaci služby čekajícím stavu:</span><span class="sxs-lookup"><span data-stu-id="93962-160">To implement service pending status:</span></span>

1. <span data-ttu-id="93962-161">Přidat `using` příkaz nebo `Imports` deklarace <xref:System.Runtime.InteropServices?displayProperty=nameWithType> obor názvů v souboru MyNewService.cs nebo MyNewService.vb:</span><span class="sxs-lookup"><span data-stu-id="93962-161">Add a `using` statement or `Imports` declaration for the <xref:System.Runtime.InteropServices?displayProperty=nameWithType> namespace in the MyNewService.cs or MyNewService.vb file:</span></span>

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. <span data-ttu-id="93962-162">Přidejte následující kód k MyNewService.cs pro deklaraci `ServiceState` hodnoty a přidat strukturu pro stav, který budete používat ve volání funkce invoke:</span><span class="sxs-lookup"><span data-stu-id="93962-162">Add the following code to MyNewService.cs to declare the `ServiceState` values and to add a structure for the status, which you'll use in a platform invoke call:</span></span>

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

3. <span data-ttu-id="93962-163">Teď v `MyNewService` třídy, deklarujte [SetServiceStatus funkce](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) pomocí [vyvolání platformy](../interop/consuming-unmanaged-dll-functions.md):</span><span class="sxs-lookup"><span data-stu-id="93962-163">Now, in the `MyNewService` class, declare the [SetServiceStatus function](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) by using [platform invoke](../interop/consuming-unmanaged-dll-functions.md):</span></span>

    ```csharp
    [DllImport("advapi32.dll", SetLastError = true)]
    private static extern bool SetServiceStatus(System.IntPtr handle, ref ServiceStatus serviceStatus);
    ```

    ```vb
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean
    ```

4. <span data-ttu-id="93962-164">K implementaci spuštění čeká na stav, přidejte následující kód do začátku <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody:</span><span class="sxs-lookup"><span data-stu-id="93962-164">To implement the Start Pending status, add the following code to the beginning of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method:</span></span>

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

5. <span data-ttu-id="93962-165">Přidejte kód pro spuštění na konci nastavit stav <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="93962-165">Add code to set the status to Running at the end of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span>

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

6. <span data-ttu-id="93962-166">(Volitelné) Tento postup zopakujte pro <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="93962-166">(Optional) Repeat this procedure for the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method.</span></span>

> [!NOTE]
> <span data-ttu-id="93962-167">[Správce řízení služeb](/windows/desktop/Services/service-control-manager) používá `dwWaitHint` a `dwCheckpoint` členy [SERVICE_STATUS struktura](/windows/desktop/api/winsvc/ns-winsvc-_service_status) k určení doby čekání na službu Windows ke spuštění nebo vypnutí.</span><span class="sxs-lookup"><span data-stu-id="93962-167">The [Service Control Manager](/windows/desktop/Services/service-control-manager) uses the `dwWaitHint` and `dwCheckpoint` members of the [SERVICE_STATUS structure](/windows/desktop/api/winsvc/ns-winsvc-_service_status) to determine how much time to wait for a Windows service to start or shut down.</span></span> <span data-ttu-id="93962-168">Pokud vaše <xref:System.ServiceProcess.ServiceBase.OnStart%2A> a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody se spustí, long, vaše služba může požádat o víc času voláním [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) znovu se zvýšena `dwCheckPoint` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="93962-168">If your <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods run long, your service can request more time by calling [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) again with an incremented `dwCheckPoint` value.</span></span>

## <a name="add-installers-to-the-service"></a><span data-ttu-id="93962-169">Přidání instalačních programů do služby</span><span class="sxs-lookup"><span data-stu-id="93962-169">Add installers to the service</span></span>

<span data-ttu-id="93962-170">Před spuštěním služby Windows, musíte nainstalovat, které je zaregistruje ho s správce řízení služeb.</span><span class="sxs-lookup"><span data-stu-id="93962-170">Before you can run a Windows service, you need to install it, which registers it with the Service Control Manager.</span></span> <span data-ttu-id="93962-171">Přidání instalačních programů do projektu, který zpracovat podrobnosti registrace.</span><span class="sxs-lookup"><span data-stu-id="93962-171">You can add installers to your project that handle the registration details.</span></span>

1. <span data-ttu-id="93962-172">V **Průzkumníka řešení**, otevřete kontextovou nabídku pro **MyNewService.cs** nebo **MyNewService.vb**a klikněte na tlačítko **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="93962-172">In **Solution Explorer**, open the context menu for **MyNewService.cs** or **MyNewService.vb**, and then choose **View Designer**.</span></span>

2. <span data-ttu-id="93962-173">Kliknutím na pozadí návrháře vyberte samotnou službu namísto některé z jejích komponent.</span><span class="sxs-lookup"><span data-stu-id="93962-173">Click the background of the designer to select the service itself, instead of any of its contents.</span></span>

3. <span data-ttu-id="93962-174">Otevřete místní nabídku pro okna návrháře (Pokud používáte polohovací zařízení, klikněte pravým tlačítkem uvnitř okna) a klikněte na tlačítko **přidat instalační program**.</span><span class="sxs-lookup"><span data-stu-id="93962-174">Open the context menu for the designer window (if you’re using a pointing device, right-click inside the window), and then choose **Add Installer**.</span></span>

   <span data-ttu-id="93962-175">Ve výchozím nastavení bude do projektu přidána komponentní třída, která obsahuje dva instalační programy.</span><span class="sxs-lookup"><span data-stu-id="93962-175">By default, a component class that contains two installers is added to your project.</span></span> <span data-ttu-id="93962-176">Komponenta má název **ProjectInstaller**a obsahuje instalační program pro vaši službu a instalační program služby přidruženého k tomuto procesu.</span><span class="sxs-lookup"><span data-stu-id="93962-176">The component is named **ProjectInstaller**, and the installers it contains are the installer for your service and the installer for the service's associated process.</span></span>

4. <span data-ttu-id="93962-177">V **návrhu** zobrazit **ProjectInstaller**, zvolte **serviceInstaller1** pro projekt jazyka Visual C#, nebo **ServiceInstaller1** vizuálu Základní projekt.</span><span class="sxs-lookup"><span data-stu-id="93962-177">In **Design** view for **ProjectInstaller**, choose **serviceInstaller1** for a Visual C# project, or **ServiceInstaller1** for a Visual Basic project.</span></span>

5. <span data-ttu-id="93962-178">V **vlastnosti** okno, ujistěte se, že <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> je nastavena na **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="93962-178">In the **Properties** window, make sure the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property is set to **MyNewService**.</span></span>

6. <span data-ttu-id="93962-179">Nastavte **popis** vlastnost nějaký text, například "Ukázková služba".</span><span class="sxs-lookup"><span data-stu-id="93962-179">Set the **Description** property to some text, such as "A sample service".</span></span> <span data-ttu-id="93962-180">Tento text se zobrazí v okně služby a pomáhá uživatelům identifikaci služby a pochopit, co se používá.</span><span class="sxs-lookup"><span data-stu-id="93962-180">This text appears in the Services window and helps the user identify the service and understand what it’s used for.</span></span>

7. <span data-ttu-id="93962-181">Nastavte <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> vlastnost text, který se má zobrazit v okně služby **název** sloupec.</span><span class="sxs-lookup"><span data-stu-id="93962-181">Set the <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> property to the text that you want to appear in the Services window in the **Name** column.</span></span> <span data-ttu-id="93962-182">Můžete například zadat "MyNewService zobrazované jméno".</span><span class="sxs-lookup"><span data-stu-id="93962-182">For example, you can enter "MyNewService Display Name".</span></span> <span data-ttu-id="93962-183">Tento název se může lišit od <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> vlastnost, která je název použitý v systému (třeba když použijete `net start` příkaz pro spuštění služby).</span><span class="sxs-lookup"><span data-stu-id="93962-183">This name can be different from the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property, which is the name used by the system (for example, when you use the `net start` command to start your service).</span></span>

8. <span data-ttu-id="93962-184">Nastavte <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnost <xref:System.ServiceProcess.ServiceStartMode.Automatic>.</span><span class="sxs-lookup"><span data-stu-id="93962-184">Set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to <xref:System.ServiceProcess.ServiceStartMode.Automatic>.</span></span>

     <span data-ttu-id="93962-185">![Vlastnosti Instalační služby systému Windows služby](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")</span><span class="sxs-lookup"><span data-stu-id="93962-185">![Installer Properties for a Windows service](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")</span></span>

9. <span data-ttu-id="93962-186">V návrháři, zvolte **serviceProcessInstaller1** pro projekt jazyka Visual C#, nebo **ServiceProcessInstaller1** pro projekt jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="93962-186">In the designer, choose **serviceProcessInstaller1** for a Visual C# project, or **ServiceProcessInstaller1** for a Visual Basic project.</span></span> <span data-ttu-id="93962-187">Nastavte <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> vlastnost <xref:System.ServiceProcess.ServiceAccount.LocalSystem>.</span><span class="sxs-lookup"><span data-stu-id="93962-187">Set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property to <xref:System.ServiceProcess.ServiceAccount.LocalSystem>.</span></span> <span data-ttu-id="93962-188">To způsobí, že služba nainstalována a spuštěna s použitím místního systémového účtu.</span><span class="sxs-lookup"><span data-stu-id="93962-188">This causes the service to be installed and to run using the local system account.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="93962-189"><xref:System.ServiceProcess.ServiceAccount.LocalSystem> Účet má širší oprávnění, včetně možnosti zapisovat do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="93962-189">The <xref:System.ServiceProcess.ServiceAccount.LocalSystem> account has broad permissions, including the ability to write to the event log.</span></span> <span data-ttu-id="93962-190">Používejte tento účet opatrně, protože může zvýšit riziko napadení škodlivým softwarem.</span><span class="sxs-lookup"><span data-stu-id="93962-190">Use this account with caution, because it might increase your risk of attacks from malicious software.</span></span> <span data-ttu-id="93962-191">Pro jiné úlohy zvažte použití <xref:System.ServiceProcess.ServiceAccount.LocalService> účet, který funguje jako neprivilegované uživatele v místním počítači a nabízí pověření anonymního a jakémukoli vzdálenému serveru.</span><span class="sxs-lookup"><span data-stu-id="93962-191">For other tasks, consider using the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, which acts as a non-privileged user on the local computer and presents anonymous credentials to any remote server.</span></span> <span data-ttu-id="93962-192">V tomto příkladu se nezdaří, pokud se pokusíte použít <xref:System.ServiceProcess.ServiceAccount.LocalService> účtu, proto, že potřebuje oprávnění k zápisu do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="93962-192">This example fails if you try to use the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, because it needs permission to write to the event log.</span></span>

<span data-ttu-id="93962-193">Další informace o instalačních programů najdete v tématu [postupy: Přidání instalačních programů do aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="93962-193">For more information about installers, see [How to: Add Installers to Your service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>

## <a name="optional-set-startup-parameters"></a><span data-ttu-id="93962-194">(Volitelné) Nastavit parametry spuštění</span><span class="sxs-lookup"><span data-stu-id="93962-194">(Optional) Set startup parameters</span></span>

<span data-ttu-id="93962-195">Služba Windows, stejně jako jakéhokoliv jiného spustitelného souboru, může přijmout argumenty příkazového řádku, nebo parametry spuštění.</span><span class="sxs-lookup"><span data-stu-id="93962-195">A Windows service, like any other executable, can accept command-line arguments, or startup parameters.</span></span> <span data-ttu-id="93962-196">Když přidáte kód do parametrů spuštění procesu, uživatelé mohou spustit služby s vlastní vlastní spouštěcí parametry pomocí okna služby v Ovládacích panelech Windows.</span><span class="sxs-lookup"><span data-stu-id="93962-196">When you add code to process startup parameters, users can start your service with their own custom startup parameters by using the Services window in the Windows Control Panel.</span></span> <span data-ttu-id="93962-197">Tyto spouštěcí parametry nejsou však zachované při příštím spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="93962-197">However, these startup parameters are not persisted the next time the service starts.</span></span> <span data-ttu-id="93962-198">Pokud chcete nastavit spouštěcí parametry trvale, můžete nastavit je v registru, jak je znázorněno v tomto postupu.</span><span class="sxs-lookup"><span data-stu-id="93962-198">To set startup parameters permanently, you can set them in the registry, as shown in this procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="93962-199">Předtím, než se rozhodnete přidat parametry spuštění, zvažte, jestli, která je nejlepší způsob, jak předávání informací do vaší služby.</span><span class="sxs-lookup"><span data-stu-id="93962-199">Before you decide to add startup parameters, consider whether that is the best way to pass information to your service.</span></span> <span data-ttu-id="93962-200">I když parametry spuštění jsou snadno použitelné a pro analýzy a uživatelé snadno je můžete přepsat, mohou být obtížnější uživatelům objevit a používat bez dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="93962-200">Although startup parameters are easy to use and to parse, and users can easily override them, they might be harder for users to discover and use without documentation.</span></span> <span data-ttu-id="93962-201">Obecně platí Pokud vaše služba vyžaduje více než několik parametrů spuštění, měli byste zvážit použití registru nebo konfiguračního souboru místo toho.</span><span class="sxs-lookup"><span data-stu-id="93962-201">Generally, if your service requires more than just a few startup parameters, you should consider using the registry or a configuration file instead.</span></span> <span data-ttu-id="93962-202">Každá služba Windows má záznam v registru pod **HKLM\System\CurrentControlSet\services**.</span><span class="sxs-lookup"><span data-stu-id="93962-202">Every Windows service has an entry in the registry under **HKLM\System\CurrentControlSet\services**.</span></span> <span data-ttu-id="93962-203">V klíči služby, můžete použít **parametry** podklíč pro ukládání informací, které můžou přistupovat k vaší služby.</span><span class="sxs-lookup"><span data-stu-id="93962-203">Under the service's key, you can use the **Parameters** subkey to store information that your service can access.</span></span> <span data-ttu-id="93962-204">Konfigurační soubory aplikace můžete použít pro službu Windows stejným způsobem jako u jiných typů aplikací.</span><span class="sxs-lookup"><span data-stu-id="93962-204">You can use application configuration files for a Windows service the same way you do for other types of programs.</span></span> <span data-ttu-id="93962-205">Příklad kódu naleznete v tématu <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.</span><span class="sxs-lookup"><span data-stu-id="93962-205">For example code, see <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.</span></span>

<span data-ttu-id="93962-206">Chcete-li přidat parametry spuštění:</span><span class="sxs-lookup"><span data-stu-id="93962-206">To add startup parameters:</span></span>

1. <span data-ttu-id="93962-207">V `Main` metodu v souboru Program.cs nebo MyNewService.Designer.vb, přidejte vstupní parametr předat konstruktoru služby:</span><span class="sxs-lookup"><span data-stu-id="93962-207">In the `Main` method in Program.cs or in MyNewService.Designer.vb, add an input parameter to pass to the service constructor:</span></span>

   ```csharp
   static void Main(string[] args)
   {
       ServiceBase[] ServicesToRun;
       ServicesToRun = new ServiceBase[]
       {
           new MyNewService(args)
       };
       ServiceBase.Run(ServicesToRun);
   }
   ```

   ```vb
   Shared Sub Main(ByVal cmdArgs() As String)
       Dim ServicesToRun() As System.ServiceProcess.ServiceBase = New System.ServiceProcess.ServiceBase() {New MyNewServiceVB(cmdArgs)}
       System.ServiceProcess.ServiceBase.Run(ServicesToRun)
   End Sub
   ```

2. <span data-ttu-id="93962-208">Změnit `MyNewService` konstruktor následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="93962-208">Change the `MyNewService` constructor as follows:</span></span>

   ```csharp
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

        eventLog1 = new System.Diagnostics.EventLog();

        if (!System.Diagnostics.EventLog.SourceExists(eventSourceName))
        {
            System.Diagnostics.EventLog.CreateEventSource(eventSourceName, logName);
        }

        eventLog1.Source = eventSourceName;
        eventLog1.Log = logName;
   }
   ```

   ```vb
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
       eventLog1 = New System.Diagnostics.EventLog()
       If (Not System.Diagnostics.EventLog.SourceExists(eventSourceName)) Then
           System.Diagnostics.EventLog.CreateEventSource(eventSourceName, logName)
       End If
       eventLog1.Source = eventSourceName
       eventLog1.Log = logName
   End Sub
   ```

   <span data-ttu-id="93962-209">Tento kód nastaví název zdroje a protokol událostí podle Zadaný spouštěcí parametry, nebo použije výchozí hodnoty, pokud nejsou dodány žádné argumenty.</span><span class="sxs-lookup"><span data-stu-id="93962-209">This code sets the event source and log name according to the supplied startup parameters, or uses default values if no arguments are supplied.</span></span>

3. <span data-ttu-id="93962-210">Chcete-li zadat argumenty příkazového řádku, přidejte následující kód, který `ProjectInstaller` třídy v ProjectInstaller.cs nebo ProjectInstaller.vb:</span><span class="sxs-lookup"><span data-stu-id="93962-210">To specify the command-line arguments, add the following code to the `ProjectInstaller` class in ProjectInstaller.cs or ProjectInstaller.vb:</span></span>

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

   <span data-ttu-id="93962-211">Tento kód změní **ImagePath** klíč registru, který obvykle obsahuje úplnou cestu ke spustitelnému souboru pro službu Windows tak, že přidáte výchozí hodnoty parametrů.</span><span class="sxs-lookup"><span data-stu-id="93962-211">This code modifies the **ImagePath** registry key, which typically contains the full path to the executable for the Windows service, by adding the default parameter values.</span></span> <span data-ttu-id="93962-212">Uvozovky kolem cestu (a po každé jednotlivé parametr) jsou požadovány pro službu spustit správně.</span><span class="sxs-lookup"><span data-stu-id="93962-212">The quotation marks around the path (and around each individual parameter) are required for the service to start up correctly.</span></span> <span data-ttu-id="93962-213">Chcete-li změnit spouštěcí parametry pro tuto službu Windows, uživatelé mohou změnit parametrech daných **ImagePath** klíč registru, i když lepší je vytvoření a změna programu zpřístupnění funkcí pro uživatele v popisný způsobem (třeba správu nebo konfigurace nástroje).</span><span class="sxs-lookup"><span data-stu-id="93962-213">To change the startup parameters for this Windows service, users can change the parameters given in the **ImagePath** registry key, although the better way is to change it programmatically and expose the functionality to users in a friendly way (for example, in a management or configuration utility).</span></span>

## <a name="build-the-service"></a><span data-ttu-id="93962-214">Vytvoření služby</span><span class="sxs-lookup"><span data-stu-id="93962-214">Build the service</span></span>

1. <span data-ttu-id="93962-215">V **Průzkumníka řešení**, otevřete kontextovou nabídku pro váš projekt a klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="93962-215">In **Solution Explorer**, open the context menu for your project, and then choose **Properties**.</span></span>

   <span data-ttu-id="93962-216">Stránky vlastností pro váš projekt se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="93962-216">The property pages for your project appear.</span></span>

2. <span data-ttu-id="93962-217">Na **aplikace** kartě **spouštěcí objekt** klikněte na položku **MyNewService.Program**.</span><span class="sxs-lookup"><span data-stu-id="93962-217">On the **Application** tab, in the **Startup object** list, choose **MyNewService.Program**.</span></span>

3. <span data-ttu-id="93962-218">V **Průzkumníka řešení**, otevřete kontextovou nabídku pro váš projekt a klikněte na tlačítko **sestavení** k sestavení projektu (nebo stiskněte klávesu **Ctrl**+**Shift**  + **B**).</span><span class="sxs-lookup"><span data-stu-id="93962-218">In **Solution Explorer**, open the context menu for your project, and then choose **Build** to build the project (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="install-the-service"></a><span data-ttu-id="93962-219">Instalace služby</span><span class="sxs-lookup"><span data-stu-id="93962-219">Install the service</span></span>

<span data-ttu-id="93962-220">Teď, když jste vytvořili službu Windows, můžete ho nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="93962-220">Now that you've built the Windows service, you can install it.</span></span> <span data-ttu-id="93962-221">Pro instalaci služby Windows, musíte mít pověření správce na počítači, na kterém instalujete ho.</span><span class="sxs-lookup"><span data-stu-id="93962-221">To install a Windows service, you must have administrator credentials on the computer on which you're installing it.</span></span>

1. <span data-ttu-id="93962-222">Otevřít **Developer Command Prompt pro sadu Visual Studio** s přihlašovacími údaji správce.</span><span class="sxs-lookup"><span data-stu-id="93962-222">Open **Developer Command Prompt for Visual Studio** with administrative credentials.</span></span> <span data-ttu-id="93962-223">Pokud používáte myš, klikněte pravým tlačítkem na **Developer Command Prompt for VS 2017** nabídky Start v Windows a klikněte na tlačítko **Další** > **spustit jako správce** .</span><span class="sxs-lookup"><span data-stu-id="93962-223">If you’re using a mouse, right-click on **Developer Command Prompt for VS 2017** in the Windows Start menu, and then choose **More** > **Run as Administrator**.</span></span>

2. <span data-ttu-id="93962-224">V **Developer Command Prompt** okno, přejděte do složky, který obsahuje výstup projektu (ve výchozím nastavení, je *\bin\Debug* podadresáře projektu).</span><span class="sxs-lookup"><span data-stu-id="93962-224">In the **Developer Command Prompt** window, navigate to the folder that contains your project's output (by default, it's the *\bin\Debug* subdirectory of your project).</span></span>

3. <span data-ttu-id="93962-225">Zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="93962-225">Enter the following command:</span></span>

    ```shell
    installutil.exe MyNewService.exe
    ```

    <span data-ttu-id="93962-226">Pokud je služba nainstalována úspěšně, **installutil.exe** oznámí úspěšné dokončení.</span><span class="sxs-lookup"><span data-stu-id="93962-226">If the service installs successfully, **installutil.exe** reports success.</span></span> <span data-ttu-id="93962-227">Pokud systém nemůže najít **InstallUtil.exe**, ujistěte se, že existuje ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="93962-227">If the system could not find **InstallUtil.exe**, make sure that it exists on your computer.</span></span> <span data-ttu-id="93962-228">Tento nástroj je nainstalován pomocí rozhraní .NET Framework do složky *% windir%\Microsoft.NET\Framework[64]\\[framework verze]*.</span><span class="sxs-lookup"><span data-stu-id="93962-228">This tool is installed with the .NET Framework to the folder *%windir%\Microsoft.NET\Framework[64]\\[framework version]*.</span></span> <span data-ttu-id="93962-229">Například výchozí cesta pro 32bitovou verzi je *%windir%\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="93962-229">For example, the default path for the 32-bit version is *%windir%\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span></span>

    <span data-ttu-id="93962-230">Pokud **installutil.exe** zpracovat selhání zpráv, najdete v protokolu instalace a zjistěte, proč.</span><span class="sxs-lookup"><span data-stu-id="93962-230">If the **installutil.exe** process reports failure, check the install log to find out why.</span></span> <span data-ttu-id="93962-231">Ve výchozím nastavení protokolu je ve stejné složce jako spustitelný soubor služby.</span><span class="sxs-lookup"><span data-stu-id="93962-231">By default the log is in the same folder as the service executable.</span></span> <span data-ttu-id="93962-232">Instalace může selhat, pokud <xref:System.ComponentModel.RunInstallerAttribute> třída není k dispozici na `ProjectInstaller` třídy, pokud atribut není nastavená na **true**, nebo pokud `ProjectInstaller` třída není označena **veřejné**.</span><span class="sxs-lookup"><span data-stu-id="93962-232">The installation can fail if  the <xref:System.ComponentModel.RunInstallerAttribute> Class is not present on the `ProjectInstaller` class, if the attribute is not set to **true**, or if the `ProjectInstaller` class is not marked **public**.</span></span>

<span data-ttu-id="93962-233">Další informace najdete v tématu [postupy: instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="93962-233">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>

## <a name="start-and-run-the-service"></a><span data-ttu-id="93962-234">Spuštění a spuštění služby</span><span class="sxs-lookup"><span data-stu-id="93962-234">Start and run the service</span></span>

1. <span data-ttu-id="93962-235">Ve Windows, otevřete **služby** aplikace klasické pracovní plochy.</span><span class="sxs-lookup"><span data-stu-id="93962-235">In Windows, open the **Services** desktop app.</span></span> <span data-ttu-id="93962-236">Stisknutím klávesy **Windows**+**R** otevřít **spustit** a pak zadejte **services.msc** a stiskněte klávesu **Enter**  nebo klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="93962-236">Press **Windows**+**R** to open the **Run** box, and then enter **services.msc** and press **Enter** or click **OK**.</span></span>

     <span data-ttu-id="93962-237">Měli byste vidět vaše služba uvedená v **služby**, zobrazené abecedně podle zobrazovaného názvu, kterou jste nastavili pro něj.</span><span class="sxs-lookup"><span data-stu-id="93962-237">You should see your service listed in **Services**, displayed alphabetically by the display name that you set for it.</span></span>

     ![MyNewService v okně služby.](../../../docs/framework/windows-services/media/windowsservices-serviceswindow.PNG)

2. <span data-ttu-id="93962-239">V **služby**, otevřete místní nabídku pro vaši službu a pak zvolte **Start**.</span><span class="sxs-lookup"><span data-stu-id="93962-239">In **Services**, open the shortcut menu for your service, and then choose **Start**.</span></span>

3. <span data-ttu-id="93962-240">K zastavení služby, otevřete místní nabídku pro službu a pak zvolte **Zastavit**.</span><span class="sxs-lookup"><span data-stu-id="93962-240">To stop the service, open the shortcut menu for the service, and then choose **Stop**.</span></span>

4. <span data-ttu-id="93962-241">(Volitelné) Z příkazového řádku, můžete použít příkazy `net start ServiceName` a `net stop ServiceName` spuštění a zastavení služby.</span><span class="sxs-lookup"><span data-stu-id="93962-241">(Optional) From the command line, you can use the commands `net start ServiceName` and `net stop ServiceName` to start and stop your service.</span></span>

### <a name="verify-the-event-log-output-of-your-service"></a><span data-ttu-id="93962-242">Ověření výstupu služby v protokolu událostí</span><span class="sxs-lookup"><span data-stu-id="93962-242">Verify the event log output of your service</span></span>

1. <span data-ttu-id="93962-243">Otevřít **Prohlížeč událostí** spuštěním na typ **Prohlížeč událostí** do vyhledávacího pole na hlavním panelu Windows a pak vyberete **Prohlížeč událostí** ve výsledcích hledání.</span><span class="sxs-lookup"><span data-stu-id="93962-243">Open **Event Viewer** by starting to type **Event Viewer** in the search box on the Windows task bar, and then selecting **Event Viewer** from the search results.</span></span>

   > [!TIP]
   > <span data-ttu-id="93962-244">V sadě Visual Studio, dostanete protokoly událostí tak, že otevřete **Průzkumníka serveru** (klávesnice: **Ctrl**+**Alt**+**S**) rozšiřuje i **protokoly událostí** uzel v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="93962-244">In Visual Studio, you can access event logs by opening **Server Explorer** (Keyboard: **Ctrl**+**Alt**+**S**) and expanding the **Event Logs** node for the local computer.</span></span>

2. <span data-ttu-id="93962-245">V **Prohlížeč událostí**, rozbalte **protokoly aplikací a služeb**.</span><span class="sxs-lookup"><span data-stu-id="93962-245">In **Event Viewer**, expand **Applications and Services Logs**.</span></span>

3. <span data-ttu-id="93962-246">Vyhledejte výpis pro **MyNewLog** (nebo **MyLogFile1**, pokud jste postupovali podle volitelný postup pro přidání argumentů příkazového řádku) a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="93962-246">Locate the listing for **MyNewLog** (or **MyLogFile1**, if you followed the optional procedure to add command-line arguments) and expand it.</span></span> <span data-ttu-id="93962-247">Měli byste vidět položky pro dvě akce (spouštění a zastavování), které provádí vaší služby.</span><span class="sxs-lookup"><span data-stu-id="93962-247">You should see entries for the two actions (start and stop) that your service performed.</span></span>

     ![Pomocí prohlížeče událostí zobrazíte položky protokolu událostí](../../../docs/framework/windows-services/media/windows-service-event-viewer.png)

## <a name="uninstall-the-service"></a><span data-ttu-id="93962-249">Odinstalujte službu</span><span class="sxs-lookup"><span data-stu-id="93962-249">Uninstall the service</span></span>

1. <span data-ttu-id="93962-250">Otevřít **Developer Command Prompt pro sadu Visual Studio** s přihlašovacími údaji správce.</span><span class="sxs-lookup"><span data-stu-id="93962-250">Open **Developer Command Prompt for Visual Studio** with administrative credentials.</span></span>

2. <span data-ttu-id="93962-251">V okně příkazového řádku přejděte do složky, který obsahuje výstup projektu.</span><span class="sxs-lookup"><span data-stu-id="93962-251">In the command prompt window, navigate to the folder that contains your project's output.</span></span>

3. <span data-ttu-id="93962-252">Zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="93962-252">Enter the following command:</span></span>

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   <span data-ttu-id="93962-253">Pokud služba úspěšně, odinstalována **installutil.exe** hlásí, že vaše služba byla úspěšně odebrána.</span><span class="sxs-lookup"><span data-stu-id="93962-253">If the service uninstalls successfully, **installutil.exe** reports that your service was successfully removed.</span></span> <span data-ttu-id="93962-254">Další informace najdete v tématu [postupy: instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="93962-254">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="93962-255">Další kroky</span><span class="sxs-lookup"><span data-stu-id="93962-255">Next steps</span></span>

<span data-ttu-id="93962-256">Teď, když jste vytvořili službu, můžete chtít vytvořit samostatný instalační program, který ostatní mohli používat k instalaci služby Windows.</span><span class="sxs-lookup"><span data-stu-id="93962-256">Now that you've created the service, you might want to create a standalone setup program that others can use to install your Windows service.</span></span> <span data-ttu-id="93962-257">Technologie ClickOnce nepodporuje služby Windows, ale můžete použít [sadu nástrojů WiX Toolset](http://wixtoolset.org/) vytvořit instalační službu pro službu Windows.</span><span class="sxs-lookup"><span data-stu-id="93962-257">ClickOnce doesn't support Windows services, but you can use the [WiX Toolset](http://wixtoolset.org/) to create an installer for a Windows service.</span></span> <span data-ttu-id="93962-258">Další příklady naleznete v tématu [vytvoření instalačního balíčku](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).</span><span class="sxs-lookup"><span data-stu-id="93962-258">For other ideas, see [Create an installer package](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).</span></span>

<span data-ttu-id="93962-259">Použití může zkoumat <xref:System.ServiceProcess.ServiceController> komponenta, která vám umožní odesílat příkazy do služby, které jste nainstalovali.</span><span class="sxs-lookup"><span data-stu-id="93962-259">You might explore the use of a <xref:System.ServiceProcess.ServiceController> component, which enables you to send commands to the service you've installed.</span></span>

<span data-ttu-id="93962-260">Pomocí instalačního programu můžete vytvořit protokol událostí při instalaci aplikace namísto vytvoření protokolu událostí po spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="93962-260">You can use an installer to create an event log when the application is installed instead of creating the event log when the application runs.</span></span> <span data-ttu-id="93962-261">Při odinstalaci aplikace navíc instalační program protokol událostí odstraní.</span><span class="sxs-lookup"><span data-stu-id="93962-261">Additionally, the event log will be deleted by the installer when the application is uninstalled.</span></span> <span data-ttu-id="93962-262">Další informace najdete v tématu <xref:System.Diagnostics.EventLogInstaller> referenční stránce.</span><span class="sxs-lookup"><span data-stu-id="93962-262">For more information, see the <xref:System.Diagnostics.EventLogInstaller> reference page.</span></span>

## <a name="see-also"></a><span data-ttu-id="93962-263">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93962-263">See also</span></span>

- [<span data-ttu-id="93962-264">Aplikace služby Windows</span><span class="sxs-lookup"><span data-stu-id="93962-264">Windows service applications</span></span>](../../../docs/framework/windows-services/index.md)
- [<span data-ttu-id="93962-265">Úvod do aplikace služby Windows</span><span class="sxs-lookup"><span data-stu-id="93962-265">Introduction to Windows service applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="93962-266">Postupy: ladění aplikace služby Windows</span><span class="sxs-lookup"><span data-stu-id="93962-266">How to: Debug Windows service applications</span></span>](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="93962-267">Služby (Windows)</span><span class="sxs-lookup"><span data-stu-id="93962-267">Services (Windows)</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms685141.aspx)
