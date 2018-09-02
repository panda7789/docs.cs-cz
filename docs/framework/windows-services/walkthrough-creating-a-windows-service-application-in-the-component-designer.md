---
title: 'Návod: Vytvoření aplikace spouštěné jako služba systému Windows v návrháři součástí'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Service applications, walkthroughs
- Windows Service applications, creating
ms.assetid: e24d8a3d-edc6-485c-b6e0-5672d91fb607
author: ghogen
manager: douge
ms.openlocfilehash: 6d70db7139d82b6e219e2c417282333f950ef402
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43417858"
---
# <a name="walkthrough-creating-a-windows-service-application-in-the-component-designer"></a><span data-ttu-id="3502b-102">Návod: Vytvoření aplikace spouštěné jako služba systému Windows v návrháři součástí</span><span class="sxs-lookup"><span data-stu-id="3502b-102">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>
<span data-ttu-id="3502b-103">Tento článek ukazuje, jak vytvořit jednoduchou aplikaci Windows služby v sadě Visual Studio, která zapisuje zprávy do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="3502b-103">This article demonstrates how to create a simple Windows Service application in Visual Studio that writes messages to an event log.</span></span> <span data-ttu-id="3502b-104">Tady jsou základní kroky, které provádějí vytváření a používání služby:</span><span class="sxs-lookup"><span data-stu-id="3502b-104">Here are the basic steps that you perform to create and use your service:</span></span>  
  
1.  <span data-ttu-id="3502b-105">[Vytvoření služby](#BK_CreateProject) pomocí **Windows Service** šablony projektu a nakonfigurujte ho.</span><span class="sxs-lookup"><span data-stu-id="3502b-105">[Creating a Service](#BK_CreateProject) by using the **Windows Service** project template, and configure it.</span></span> <span data-ttu-id="3502b-106">Tato šablona vytvoří třídu dědící z <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> a velkou část základního kódu služby, jako je například kód ke spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="3502b-106">This template creates a class for you that inherits from <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> and writes much of the basic service code, such as the code to start the service.</span></span>  
  
2.  <span data-ttu-id="3502b-107">[Přidání funkcí do služby](#BK_WriteCode) pro <xref:System.ServiceProcess.ServiceBase.OnStart%2A> a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> postupy a přepište všechny jiné metody, které chcete předefinovat.</span><span class="sxs-lookup"><span data-stu-id="3502b-107">[Adding Features to the Service](#BK_WriteCode) for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures, and override any other methods that you want to redefine.</span></span>  
  
3.  <span data-ttu-id="3502b-108">[Nastavení služby stavu](#BK_SetStatus).</span><span class="sxs-lookup"><span data-stu-id="3502b-108">[Setting Service Status](#BK_SetStatus).</span></span> <span data-ttu-id="3502b-109">Ve výchozím nastavení, služby vytvořené pomocí <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> implementovat pouze podmnožinu příznaků stavu k dispozici.</span><span class="sxs-lookup"><span data-stu-id="3502b-109">By default, services created with <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> implement only a subset of the available status flags.</span></span> <span data-ttu-id="3502b-110">Pokud vaše služba trvá dlouhou dobu spuštění, pozastavení nebo ukončení, můžete implementovat hodnoty stavu, jako je například čeká na spuštění nebo zastavení čeká na vyřízení k označení, že funguje u určité operace.</span><span class="sxs-lookup"><span data-stu-id="3502b-110">If your service takes a long time to start up, pause, or stop, you can implement status values such as Start Pending or Stop Pending to indicate that it's working on an operation.</span></span>  
  
4.  <span data-ttu-id="3502b-111">[Přidávání instalačních programů do služby](#BK_AddInstallers) pro aplikaci služby.</span><span class="sxs-lookup"><span data-stu-id="3502b-111">[Adding Installers to the Service](#BK_AddInstallers) for your service application.</span></span>  
  
5.  <span data-ttu-id="3502b-112">(Volitelné) [Nastavit parametry pro spuštění](#BK_StartupParameters), zadat výchozí argumenty pro spuštění a umožňují uživatelům přepsat výchozí nastavení při spuštění služby ručně.</span><span class="sxs-lookup"><span data-stu-id="3502b-112">(Optional) [Set Startup Parameters](#BK_StartupParameters), specify default startup arguments, and enable users to override default settings when they start your service manually.</span></span>  
  
6.  <span data-ttu-id="3502b-113">[Vytváření služby](#BK_Build).</span><span class="sxs-lookup"><span data-stu-id="3502b-113">[Building the Service](#BK_Build).</span></span>  
  
7.  <span data-ttu-id="3502b-114">[Instalace služby](#BK_Install) v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="3502b-114">[Installing the Service](#BK_Install) on the local machine.</span></span>  
  
8.  <span data-ttu-id="3502b-115">Přístup ke správci řízení služeb Windows a [spuštění a spuštěná služba](#BK_StartService).</span><span class="sxs-lookup"><span data-stu-id="3502b-115">Access the Windows Service Control Manager and [Starting and Running the Service](#BK_StartService).</span></span>  
  
9. <span data-ttu-id="3502b-116">[Odinstalace služby Windows](#BK_Uninstall).</span><span class="sxs-lookup"><span data-stu-id="3502b-116">[Uninstalling a Windows Service](#BK_Uninstall).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="3502b-117">Šablona projektu Služby systému Windows, která je zapotřebí pro tento návod, není k dispozici v edici Express sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3502b-117">The Windows Services project template that is required for this walkthrough is not available in the Express edition of Visual Studio.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]  
  
<a name="BK_CreateProject"></a>   
## <a name="creating-a-service"></a><span data-ttu-id="3502b-118">Vytvoření služby</span><span class="sxs-lookup"><span data-stu-id="3502b-118">Creating a Service</span></span>  
 <span data-ttu-id="3502b-119">Začněte tím, že vytvoříte projekt a nastavíte hodnoty, které jsou požadovány pro správné fungování služby.</span><span class="sxs-lookup"><span data-stu-id="3502b-119">To begin, you create the project and set values that are required for the service to function correctly.</span></span>  
  
#### <a name="to-create-and-configure-your-service"></a><span data-ttu-id="3502b-120">Vytvoření a konfigurace služby</span><span class="sxs-lookup"><span data-stu-id="3502b-120">To create and configure your service</span></span>  
  
1.  <span data-ttu-id="3502b-121">V sadě Visual Studio v panelu nabídek zvolte **souboru**, **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="3502b-121">In Visual Studio, on the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="3502b-122">**Nový projekt** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="3502b-122">The **New Project** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="3502b-123">V seznamu šablon projektů jazyka Visual Basic nebo Visual C#, zvolte **Windows Service**a název projektu **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="3502b-123">In the list of Visual Basic or Visual C# project templates, choose **Windows Service**, and name the project **MyNewService**.</span></span> <span data-ttu-id="3502b-124">Zvolte **OK**.</span><span class="sxs-lookup"><span data-stu-id="3502b-124">Choose **OK**.</span></span>  
  
     <span data-ttu-id="3502b-125">Šablona projektu automaticky přidá komponentní třídu s názvem `Service1` , která dědí z <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3502b-125">The project template automatically adds a component class named `Service1` that inherits from <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span></span>  
  
3.  <span data-ttu-id="3502b-126">Na **upravit** nabídce zvolte **najít a nahradit**, **najít v souborech** (klávesnice: Ctrl + Shift + F).</span><span class="sxs-lookup"><span data-stu-id="3502b-126">On the **Edit** menu, choose **Find and Replace**, **Find in Files** (Keyboard: Ctrl+Shift+F).</span></span> <span data-ttu-id="3502b-127">Změňte všechny výskyty `Service1` k `MyNewService`.</span><span class="sxs-lookup"><span data-stu-id="3502b-127">Change all occurrences of `Service1` to `MyNewService`.</span></span> <span data-ttu-id="3502b-128">Instance najdete v Service1.cs, Program.cs a Service1.Designer.cs (nebo jejich ekvivalenty .vb).</span><span class="sxs-lookup"><span data-stu-id="3502b-128">You’ll find instances in Service1.cs, Program.cs, and Service1.Designer.cs (or their .vb equivalents).</span></span>  
  
4.  <span data-ttu-id="3502b-129">V **vlastnosti** okně **Service1.cs [Design]** nebo **Service1.vb [Design]**, nastavte <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> a **(název)** Vlastnost `Service1` k **MyNewService**, pokud ještě není nastavený.</span><span class="sxs-lookup"><span data-stu-id="3502b-129">In the **Properties** window for **Service1.cs [Design]** or **Service1.vb [Design]**, set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> and the **(Name)** property for `Service1` to **MyNewService**, if it's not already set.</span></span>  
  
5.  <span data-ttu-id="3502b-130">V Průzkumníku řešení, přejmenujte **Service1.cs** k **MyNewService.cs**, nebo **Service1.vb** k **MyNewService.vb**.</span><span class="sxs-lookup"><span data-stu-id="3502b-130">In Solution Explorer, rename **Service1.cs** to **MyNewService.cs**, or **Service1.vb** to **MyNewService.vb**.</span></span>  
  
<a name="BK_WriteCode"></a>   
## <a name="adding-features-to-the-service"></a><span data-ttu-id="3502b-131">Přidání funkcí do služby</span><span class="sxs-lookup"><span data-stu-id="3502b-131">Adding Features to the Service</span></span>  
 <span data-ttu-id="3502b-132">V této části přidáte do služby Windows vlastního protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="3502b-132">In this section, you add a custom event log to the Windows service.</span></span> <span data-ttu-id="3502b-133">Protokoly událostí nejsou nijak spojené se službami systému Windows.</span><span class="sxs-lookup"><span data-stu-id="3502b-133">Event logs are not associated in any way with Windows services.</span></span> <span data-ttu-id="3502b-134">Tady <xref:System.Diagnostics.EventLog> komponenty slouží jako příklad typ součásti, můžete přidat do služby Windows.</span><span class="sxs-lookup"><span data-stu-id="3502b-134">Here the <xref:System.Diagnostics.EventLog> component is used as an example of the type of component you could add to a Windows service.</span></span>  
  
#### <a name="to-add-custom-event-log-functionality-to-your-service"></a><span data-ttu-id="3502b-135">Přidání funkce vlastního protokolu událostí do služby</span><span class="sxs-lookup"><span data-stu-id="3502b-135">To add custom event log functionality to your service</span></span>  
  
1.  <span data-ttu-id="3502b-136">V **Průzkumníka řešení**, otevřete kontextovou nabídku pro **MyNewService.cs** nebo **MyNewService.vb**a klikněte na tlačítko **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="3502b-136">In **Solution Explorer**, open the context menu for **MyNewService.cs** or **MyNewService.vb**, and then choose **View Designer**.</span></span>  
  
2.  <span data-ttu-id="3502b-137">Z **součásti** část **nástrojů**, přetáhněte <xref:System.Diagnostics.EventLog> komponentu do návrháře.</span><span class="sxs-lookup"><span data-stu-id="3502b-137">From the **Components** section of the **Toolbox**, drag an <xref:System.Diagnostics.EventLog> component to the designer.</span></span>  
  
3.  <span data-ttu-id="3502b-138">V **Průzkumníka řešení**, otevřete kontextovou nabídku pro **MyNewService.cs** nebo **MyNewService.vb**a klikněte na tlačítko **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="3502b-138">In **Solution Explorer**, open the context menu for **MyNewService.cs** or **MyNewService.vb**, and then choose **View Code**.</span></span>  
  
4.  <span data-ttu-id="3502b-139">Přidat deklaraci **protokolu událostí** objekt `MyNewService` třídy hned po řádek, který deklaruje `components` proměnné:</span><span class="sxs-lookup"><span data-stu-id="3502b-139">Add a declaration for the **eventLog** object in the `MyNewService` class, right after the line that declares the `components` variable:</span></span>  
  
     [!code-csharp[VbRadconService#16](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#16)]
     [!code-vb[VbRadconService#16](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#16)]  
  
5.  <span data-ttu-id="3502b-140">Přidejte nebo upravte konstruktor pro definování vlastního protokolu událostí:</span><span class="sxs-lookup"><span data-stu-id="3502b-140">Add or edit the constructor to define a custom event log:</span></span>  
  
     [!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#2)]
     [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]  
  
#### <a name="to-define-what-occurs-when-the-service-starts"></a><span data-ttu-id="3502b-141">Definování toho, co se stane při spuštění služby</span><span class="sxs-lookup"><span data-stu-id="3502b-141">To define what occurs when the service starts</span></span>  
  
-   <span data-ttu-id="3502b-142">V editoru kódu vyhledejte <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodu, která byla automaticky přepsána při vytvoření projektu a nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="3502b-142">In the Code Editor, locate the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method that was automatically overridden when you created the project, and replace the code with the following.</span></span> <span data-ttu-id="3502b-143">To přidá položku do protokolu událostí při spuštění služby:</span><span class="sxs-lookup"><span data-stu-id="3502b-143">This adds an entry to the event log when the service starts running:</span></span>  
  
     [!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
     [!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]  
  
     <span data-ttu-id="3502b-144">Aplikace služby byla navržena jako dlouhotrvající, takže obvykle dotazuje nebo něco monitoruje v systému.</span><span class="sxs-lookup"><span data-stu-id="3502b-144">A service application is designed to be long-running, so it usually polls or monitors something in the system.</span></span> <span data-ttu-id="3502b-145">Monitorování je nastavení <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3502b-145">The monitoring is set up in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span> <span data-ttu-id="3502b-146">Ale <xref:System.ServiceProcess.ServiceBase.OnStart%2A> neumí skutečně monitorování.</span><span class="sxs-lookup"><span data-stu-id="3502b-146">However, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> doesn’t actually do the monitoring.</span></span> <span data-ttu-id="3502b-147"><xref:System.ServiceProcess.ServiceBase.OnStart%2A> Metoda musí vracet v operačním systému po operaci služby.</span><span class="sxs-lookup"><span data-stu-id="3502b-147">The <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method must return to the operating system after the service's operation has begun.</span></span> <span data-ttu-id="3502b-148">Nesmí spustit nekonečnou smyčku ani blokovat.</span><span class="sxs-lookup"><span data-stu-id="3502b-148">It must not loop forever or block.</span></span> <span data-ttu-id="3502b-149">Pokud chcete nastavit jednoduchý mechanismus dotazování, můžete použít <xref:System.Timers.Timer?displayProperty=nameWithType> komponenty následujícím způsobem: V <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodu, nastavení parametrů na komponentu a potom nastavte <xref:System.Timers.Timer.Enabled%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="3502b-149">To set up a simple polling mechanism, you can use the <xref:System.Timers.Timer?displayProperty=nameWithType> component as follows: In the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, set parameters on the component, and then set the <xref:System.Timers.Timer.Enabled%2A> property to `true`.</span></span> <span data-ttu-id="3502b-150">Časovač vyvolává události ve vašem kódu pravidelně, po kterém může služba provádět monitorování.</span><span class="sxs-lookup"><span data-stu-id="3502b-150">The timer raises events in your code periodically, at which time your service could do its monitoring.</span></span> <span data-ttu-id="3502b-151">K tomu můžete použít následující kód:</span><span class="sxs-lookup"><span data-stu-id="3502b-151">You can use the following code to do this:</span></span>  
  
    ```csharp  
    // Set up a timer to trigger every minute.  
    System.Timers.Timer timer = new System.Timers.Timer();  
    timer.Interval = 60000; // 60 seconds  
    timer.Elapsed += new System.Timers.ElapsedEventHandler(this.OnTimer);  
    timer.Start();  
    ```  
  
    ```vb  
    ' Set up a timer to trigger every minute.  
    Dim timer As System.Timers.Timer = New System.Timers.Timer()  
    timer.Interval = 60000 ' 60 seconds  
    AddHandler timer.Elapsed, AddressOf Me.OnTimer  
    timer.Start()  
    ```  
     <span data-ttu-id="3502b-152">Přidání členské proměnné třídy.</span><span class="sxs-lookup"><span data-stu-id="3502b-152">Add a member variable to the class.</span></span> <span data-ttu-id="3502b-153">Bude obsahovat identifikátor další události pro zápis do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="3502b-153">It will contain the identifier of the next event to write into the event log.</span></span>

    ```csharp
    private int eventId = 1;
    ```

    ```vb
    Private eventId As Integer = 1
    ```

     <span data-ttu-id="3502b-154">Přidejte kód pro zpracování události časovače:</span><span class="sxs-lookup"><span data-stu-id="3502b-154">Add code to handle the timer event:</span></span>  
  
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
  
     <span data-ttu-id="3502b-155">Můžete chtít provádět úlohy pomocí pracovních vláken na pozadí místo spouštění veškerou práci na hlavním vlákně.</span><span class="sxs-lookup"><span data-stu-id="3502b-155">You might want to perform tasks by using background worker threads instead of running all your work on the main thread.</span></span> <span data-ttu-id="3502b-156">Příkladem, najdete v článku <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> referenční stránce.</span><span class="sxs-lookup"><span data-stu-id="3502b-156">For an example of this, see the <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> reference page.</span></span>  
  
#### <a name="to-define-what-occurs-when-the-service-is-stopped"></a><span data-ttu-id="3502b-157">Definování toho, co se stane při zastavení služby</span><span class="sxs-lookup"><span data-stu-id="3502b-157">To define what occurs when the service is stopped</span></span>  
  
-   <span data-ttu-id="3502b-158">Nahraďte kód <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metoda následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="3502b-158">Replace the code for the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method with the following.</span></span> <span data-ttu-id="3502b-159">To přidá položku do protokolu událostí po zastavení služby:</span><span class="sxs-lookup"><span data-stu-id="3502b-159">This adds an entry to the event log when the service is stopped:</span></span>  
  
     [!code-csharp[VbRadconService#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#4)]
     [!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]  
  
 <span data-ttu-id="3502b-160">V další části, můžete přepsat <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, a <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> metody definovat další zpracování pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="3502b-160">In the next section, you can override the <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, and <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> methods to define additional processing for your component.</span></span>  
  
#### <a name="to-define-other-actions-for-the-service"></a><span data-ttu-id="3502b-161">Definování dalších akcí služby</span><span class="sxs-lookup"><span data-stu-id="3502b-161">To define other actions for the service</span></span>  
  
-   <span data-ttu-id="3502b-162">Vyhledejte metodu, kterou chcete zpracovat a přepsat definovat, co má vykonávat.</span><span class="sxs-lookup"><span data-stu-id="3502b-162">Locate the method that you want to handle, and override it to define what you want to occur.</span></span>  
  
     <span data-ttu-id="3502b-163">Následující kód ukazuje, jak je možné přepsat <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> metody:</span><span class="sxs-lookup"><span data-stu-id="3502b-163">The following code shows how you can override the <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> method:</span></span>  
  
     [!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
     [!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]  
  
 <span data-ttu-id="3502b-164">Některé vlastní akce musejí nastat při instalaci služby Windows podle <xref:System.Configuration.Install.Installer> třídy.</span><span class="sxs-lookup"><span data-stu-id="3502b-164">Some custom actions have to occur when a Windows service is installed by the <xref:System.Configuration.Install.Installer> class.</span></span> <span data-ttu-id="3502b-165">Sada Visual Studio může vytvořit tyto instalační programy speciálně pro službu systému Windows a přidat je do projektu.</span><span class="sxs-lookup"><span data-stu-id="3502b-165">Visual Studio can create these installers specifically for a Windows service and add them to your project.</span></span>  
  
<a name="BK_SetStatus"></a>   
## <a name="setting-service-status"></a><span data-ttu-id="3502b-166">Nastavení služby stavu</span><span class="sxs-lookup"><span data-stu-id="3502b-166">Setting Service Status</span></span>  
 <span data-ttu-id="3502b-167">Služby oznamují svůj stav tak, aby uživatelé můžete říct, jestli služba správně funguje ke správci řízení služeb.</span><span class="sxs-lookup"><span data-stu-id="3502b-167">Services report their status to the Service Control Manager, so that users can tell whether a service is functioning correctly.</span></span> <span data-ttu-id="3502b-168">Ve výchozím nastavení, služby, které dědí <xref:System.ServiceProcess.ServiceBase> omezenou sadu nastavení, stav, včetně zastaven, pozastaven a spouštění sestav.</span><span class="sxs-lookup"><span data-stu-id="3502b-168">By default, services that inherit from <xref:System.ServiceProcess.ServiceBase> report a limited set of status settings, including Stopped, Paused, and Running.</span></span> <span data-ttu-id="3502b-169">Pokud služba trvá o něco se spustí ho může být užitečné oznámit spuštění čeká na stav.</span><span class="sxs-lookup"><span data-stu-id="3502b-169">If a service takes a little while to start up, it might be helpful to report a Start Pending status.</span></span> <span data-ttu-id="3502b-170">Nastavení stavu čeká na spuštění a zastavení probíhající můžete také implementovat přidáním kódu, která volá Windows [SetServiceStatus funkce](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus).</span><span class="sxs-lookup"><span data-stu-id="3502b-170">You can also implement the Start Pending and Stop Pending status settings by adding code that calls into the Windows [SetServiceStatus function](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus).</span></span>  
  
#### <a name="to-implement-service-pending-status"></a><span data-ttu-id="3502b-171">K implementaci služby čekajícím stavu</span><span class="sxs-lookup"><span data-stu-id="3502b-171">To implement service pending status</span></span>  
  
1.  <span data-ttu-id="3502b-172">Přidat `using` příkazu nebo `Imports` prohlášení <xref:System.Runtime.InteropServices?displayProperty=nameWithType> obor názvů v souboru MyNewService.cs nebo MyNewService.vb:</span><span class="sxs-lookup"><span data-stu-id="3502b-172">Add a `using` statement or `Imports` declaration to the <xref:System.Runtime.InteropServices?displayProperty=nameWithType> namespace in the MyNewService.cs or MyNewService.vb file:</span></span>  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    ```  
  
    ```vb  
    Imports System.Runtime.InteropServices  
    ```  
  
2.  <span data-ttu-id="3502b-173">Přidejte následující kód k MyNewService.cs pro deklaraci `ServiceState` hodnoty a přidat strukturu pro stav, který budete používat ve volání funkce invoke:</span><span class="sxs-lookup"><span data-stu-id="3502b-173">Add the following code to MyNewService.cs to declare the `ServiceState` values and to add a structure for the status, which you'll use in a platform invoke call:</span></span>  
  
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
  
3.  <span data-ttu-id="3502b-174">Teď v `MyNewService` třídy, deklarujte [SetServiceStatus funkce](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) pomocí platformy vyvolání:</span><span class="sxs-lookup"><span data-stu-id="3502b-174">Now, in the `MyNewService` class, declare the [SetServiceStatus function](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) by using platform invoke:</span></span>  
  
    ```csharp  
    [DllImport("advapi32.dll", SetLastError=true)]  
            private static extern bool SetServiceStatus(IntPtr handle, ref ServiceStatus serviceStatus);  
    ```  
  
    ```vb  
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean  
    ```  
  
4.  <span data-ttu-id="3502b-175">K implementaci spuštění čeká na stav, přidejte následující kód do začátku <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody:</span><span class="sxs-lookup"><span data-stu-id="3502b-175">To implement the Start Pending status, add the following code to the beginning of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method:</span></span>  
  
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
  
5.  <span data-ttu-id="3502b-176">Přidejte kód pro spuštění na konci nastavit stav <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3502b-176">Add code to set the status to Running at the end of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span>  
  
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
  
6.  <span data-ttu-id="3502b-177">(Volitelné) Tento postup zopakujte pro <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3502b-177">(Optional) Repeat this procedure for the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="3502b-178">[Správce řízení služeb](/windows/desktop/Services/service-control-manager) používá `dwWaitHint` a `dwCheckpoint` členy [SERVICE_STATUS struktura](/windows/desktop/api/winsvc/ns-winsvc-_service_status) k určení doby čekání na službu Windows ke spuštění nebo vypnutí.</span><span class="sxs-lookup"><span data-stu-id="3502b-178">The [Service Control Manager](/windows/desktop/Services/service-control-manager) uses the `dwWaitHint` and `dwCheckpoint` members of the [SERVICE_STATUS structure](/windows/desktop/api/winsvc/ns-winsvc-_service_status) to determine how much time to wait for a Windows Service to start or shut down.</span></span> <span data-ttu-id="3502b-179">Pokud vaše <xref:System.ServiceProcess.ServiceBase.OnStart%2A> a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody se spustí, long, vaše služba může požádat o víc času voláním [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) znovu se zvýšena `dwCheckPoint` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3502b-179">If your <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods run long, your service can request more time by calling [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) again with an incremented `dwCheckPoint` value.</span></span>  
  
<a name="BK_AddInstallers"></a>   
## <a name="adding-installers-to-the-service"></a><span data-ttu-id="3502b-180">Přidávání instalačních programů do služby</span><span class="sxs-lookup"><span data-stu-id="3502b-180">Adding Installers to the Service</span></span>  
 <span data-ttu-id="3502b-181">Před spuštěním služby Windows, musíte nainstalovat, které je zaregistruje ho s správce řízení služeb.</span><span class="sxs-lookup"><span data-stu-id="3502b-181">Before you can run a Windows Service, you need to install it, which registers it with the Service Control Manager.</span></span> <span data-ttu-id="3502b-182">Přidání instalačních programů do projektu, který zpracovat podrobnosti registrace.</span><span class="sxs-lookup"><span data-stu-id="3502b-182">You can add installers to your project that handle the registration details.</span></span>  
  
#### <a name="to-create-the-installers-for-your-service"></a><span data-ttu-id="3502b-183">Vytvoření instalačních programů pro vaši službu</span><span class="sxs-lookup"><span data-stu-id="3502b-183">To create the installers for your service</span></span>  
  
1.  <span data-ttu-id="3502b-184">V **Průzkumníka řešení**, otevřete kontextovou nabídku pro **MyNewService.cs** nebo **MyNewService.vb**a klikněte na tlačítko **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="3502b-184">In **Solution Explorer**, open the context menu for **MyNewService.cs** or **MyNewService.vb**, and then choose **View Designer**.</span></span>  
  
2.  <span data-ttu-id="3502b-185">Kliknutím na pozadí návrháře vyberte samotnou službu namísto některé z jejích komponent.</span><span class="sxs-lookup"><span data-stu-id="3502b-185">Click the background of the designer to select the service itself, instead of any of its contents.</span></span>  
  
3.  <span data-ttu-id="3502b-186">Otevřete místní nabídku pro okna návrháře (Pokud používáte polohovací zařízení, klikněte pravým tlačítkem uvnitř okna) a klikněte na tlačítko **přidat instalační program**.</span><span class="sxs-lookup"><span data-stu-id="3502b-186">Open the context menu for the designer window (if you’re using a pointing device, right-click inside the window), and then choose **Add Installer**.</span></span>  
  
     <span data-ttu-id="3502b-187">Ve výchozím nastavení bude do projektu přidána komponentní třída, která obsahuje dva instalační programy.</span><span class="sxs-lookup"><span data-stu-id="3502b-187">By default, a component class that contains two installers is added to your project.</span></span> <span data-ttu-id="3502b-188">Komponenta má název **ProjectInstaller**a obsahuje instalační program pro vaši službu a instalační program služby přidruženého k tomuto procesu.</span><span class="sxs-lookup"><span data-stu-id="3502b-188">The component is named **ProjectInstaller**, and the installers it contains are the installer for your service and the installer for the service's associated process.</span></span>  
  
4.  <span data-ttu-id="3502b-189">V **návrhu** zobrazit **ProjectInstaller**, zvolte **serviceInstaller1** pro projekt jazyka Visual C#, nebo **ServiceInstaller1** vizuálu Základní projekt.</span><span class="sxs-lookup"><span data-stu-id="3502b-189">In **Design** view for **ProjectInstaller**, choose **serviceInstaller1** for a Visual C# project, or **ServiceInstaller1** for a Visual Basic project.</span></span>  
  
5.  <span data-ttu-id="3502b-190">V **vlastnosti** okno, ujistěte se, že <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> je nastavena na **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="3502b-190">In the **Properties** window, make sure the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property is set to **MyNewService**.</span></span>  
  
6.  <span data-ttu-id="3502b-191">Nastavte **popis** vlastnost nějaký text, například "Ukázková služba".</span><span class="sxs-lookup"><span data-stu-id="3502b-191">Set the **Description** property to some text, such as "A sample service".</span></span> <span data-ttu-id="3502b-192">Tento text se zobrazí v okně služby a pomáhá uživatelům identifikaci služby a pochopit, co se používá.</span><span class="sxs-lookup"><span data-stu-id="3502b-192">This text appears in the Services window and helps the user identify the service and understand what it’s used for.</span></span>  
  
7.  <span data-ttu-id="3502b-193">Nastavte <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> vlastnost text, který se má zobrazit v okně služby **název** sloupec.</span><span class="sxs-lookup"><span data-stu-id="3502b-193">Set the <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> property to the text that you want to appear in the Services window in the **Name** column.</span></span> <span data-ttu-id="3502b-194">Můžete například zadat "MyNewService zobrazované jméno".</span><span class="sxs-lookup"><span data-stu-id="3502b-194">For example, you can enter "MyNewService Display Name".</span></span> <span data-ttu-id="3502b-195">Tento název se může lišit od <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> vlastnost, která je název použitý v systému (třeba když použijete `net start` příkaz pro spuštění služby).</span><span class="sxs-lookup"><span data-stu-id="3502b-195">This name can be different from the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property, which is the name used by the system (for example, when you use the `net start` command to start your service).</span></span>  
  
8.  <span data-ttu-id="3502b-196">Nastavte <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnost <xref:System.ServiceProcess.ServiceStartMode.Automatic>.</span><span class="sxs-lookup"><span data-stu-id="3502b-196">Set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to <xref:System.ServiceProcess.ServiceStartMode.Automatic>.</span></span>  
  
     <span data-ttu-id="3502b-197">![Vlastnosti Instalační služby systému Windows služby](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")</span><span class="sxs-lookup"><span data-stu-id="3502b-197">![Installer Properties for a Windows Service](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")</span></span>  
  
9. <span data-ttu-id="3502b-198">V návrháři, zvolte **serviceProcessInstaller1** pro projekt jazyka Visual C#, nebo **ServiceProcessInstaller1** pro projekt jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3502b-198">In the designer, choose **serviceProcessInstaller1** for a Visual C# project, or **ServiceProcessInstaller1** for a Visual Basic project.</span></span> <span data-ttu-id="3502b-199">Nastavte <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> vlastnost <xref:System.ServiceProcess.ServiceAccount.LocalSystem>.</span><span class="sxs-lookup"><span data-stu-id="3502b-199">Set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property to <xref:System.ServiceProcess.ServiceAccount.LocalSystem>.</span></span> <span data-ttu-id="3502b-200">To způsobí, že bude služba nainstalována a spuštěna s použitím účtu místní služby.</span><span class="sxs-lookup"><span data-stu-id="3502b-200">This will cause the service to be installed and to run on a local service account.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="3502b-201"><xref:System.ServiceProcess.ServiceAccount.LocalSystem> Účet má širší oprávnění, včetně možnosti zapisovat do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="3502b-201">The <xref:System.ServiceProcess.ServiceAccount.LocalSystem> account has broad permissions, including the ability to write to the event log.</span></span> <span data-ttu-id="3502b-202">Používejte tento účet opatrně, protože může zvýšit riziko napadení škodlivým softwarem.</span><span class="sxs-lookup"><span data-stu-id="3502b-202">Use this account with caution, because it might increase your risk of attacks from malicious software.</span></span> <span data-ttu-id="3502b-203">Pro jiné úlohy zvažte použití <xref:System.ServiceProcess.ServiceAccount.LocalService> účet, který funguje jako neprivilegované uživatele v místním počítači a nabízí pověření anonymního a jakémukoli vzdálenému serveru.</span><span class="sxs-lookup"><span data-stu-id="3502b-203">For other tasks, consider using the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, which acts as a non-privileged user on the local computer and presents anonymous credentials to any remote server.</span></span> <span data-ttu-id="3502b-204">V tomto příkladu se nezdaří, pokud se pokusíte použít <xref:System.ServiceProcess.ServiceAccount.LocalService> účtu, proto, že potřebuje oprávnění k zápisu do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="3502b-204">This example fails if you try to use the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, because it needs permission to write to the event log.</span></span>  
  
     <span data-ttu-id="3502b-205">Další informace o instalačních programů najdete v tématu [postupy: Přidání instalačních programů do aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="3502b-205">For more information about installers, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
<a name="BK_StartupParameters"></a>   
## <a name="set-startup-parameters"></a><span data-ttu-id="3502b-206">Nastavit parametry pro spuštění</span><span class="sxs-lookup"><span data-stu-id="3502b-206">Set Startup Parameters</span></span>  
 <span data-ttu-id="3502b-207">Služba Windows, stejně jako jakéhokoliv jiného spustitelného souboru, může přijmout argumenty příkazového řádku, nebo parametry spuštění.</span><span class="sxs-lookup"><span data-stu-id="3502b-207">A Windows Service, like any other executable, can accept command-line arguments, or startup parameters.</span></span> <span data-ttu-id="3502b-208">Když přidáte kód do parametrů spuštění procesu, uživatelé mohou spustit služby s vlastní vlastní spouštěcí parametry pomocí okna služby v Ovládacích panelech Windows.</span><span class="sxs-lookup"><span data-stu-id="3502b-208">When you add code to process startup parameters, users can start your service with their own custom startup parameters by using the Services window in the Windows Control Panel.</span></span> <span data-ttu-id="3502b-209">Tyto spouštěcí parametry nejsou však zachované při příštím spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="3502b-209">However, these startup parameters are not persisted the next time the service starts.</span></span> <span data-ttu-id="3502b-210">Pokud chcete nastavit spouštěcí parametry trvale, můžete nastavit je v registru, jak je znázorněno v tomto postupu.</span><span class="sxs-lookup"><span data-stu-id="3502b-210">To set startup parameters permanently, you can set them in the registry, as shown in this procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3502b-211">Předtím, než se rozhodnete přidat parametry spuštění, zvažte, jestli, která je nejlepší způsob, jak předávání informací do vaší služby.</span><span class="sxs-lookup"><span data-stu-id="3502b-211">Before you decide to add startup parameters, consider whether that is the best way to pass information to your service.</span></span> <span data-ttu-id="3502b-212">I když parametry spuštění jsou snadno použitelné a pro analýzy a uživatelé snadno je můžete přepsat, mohou být obtížnější uživatelům objevit a používat bez dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="3502b-212">Although startup parameters are easy to use and to parse, and users can easily override them, they might be harder for users to discover and use without documentation.</span></span> <span data-ttu-id="3502b-213">Obecně platí Pokud vaše služba vyžaduje více než několik parametrů spuštění, měli byste zvážit použití registru nebo konfiguračního souboru místo toho.</span><span class="sxs-lookup"><span data-stu-id="3502b-213">Generally, if your service requires more than just a few startup parameters, you should consider using the registry or a configuration file instead.</span></span> <span data-ttu-id="3502b-214">Každá služba Windows má záznam v registru pod HKLM\System\CurrentControlSet\services.</span><span class="sxs-lookup"><span data-stu-id="3502b-214">Every Windows Service has an entry in the registry under HKLM\System\CurrentControlSet\services.</span></span> <span data-ttu-id="3502b-215">V klíči služby, můžete použít **parametry** podklíč pro ukládání informací, které můžou přistupovat k vaší služby.</span><span class="sxs-lookup"><span data-stu-id="3502b-215">Under the service's key, you can use the **Parameters** subkey to store information that your service can access.</span></span> <span data-ttu-id="3502b-216">Konfigurační soubory aplikace můžete použít pro službu Windows stejným způsobem jako u jiných typů aplikací.</span><span class="sxs-lookup"><span data-stu-id="3502b-216">You can use application configuration files for a Windows Service the same way you do for other types of programs.</span></span> <span data-ttu-id="3502b-217">Příklad kódu naleznete v tématu <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.</span><span class="sxs-lookup"><span data-stu-id="3502b-217">For example code, see <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.</span></span>  
  
#### <a name="adding-startup-parameters"></a><span data-ttu-id="3502b-218">Přidání parametrů spuštění</span><span class="sxs-lookup"><span data-stu-id="3502b-218">Adding startup parameters</span></span>  
  
1.  <span data-ttu-id="3502b-219">V `Main` metodu v souboru Program.cs nebo MyNewService.Designer.vb, přidejte argument příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="3502b-219">In the `Main` method in Program.cs or in MyNewService.Designer.vb, add an argument for the command line:</span></span>  
  
```csharp  
static void Main(string[] args)
{
    ServiceBase[] ServicesToRun = new ServiceBase[] { new MyNewService(args) };
    ServiceBase.Run(ServicesToRun);
}
```  
  
```vb
Shared Sub Main(ByVal cmdArgs() As String)
    Dim ServicesToRun() As System.ServiceProcess.ServiceBase = New System.ServiceProcess.ServiceBase() {New MyNewServiceVB(cmdArgs)}
    System.ServiceProcess.ServiceBase.Run(ServicesToRun)
End Sub
```  
  
2.  <span data-ttu-id="3502b-220">Změnit `MyNewService` konstruktor následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="3502b-220">Change the `MyNewService` constructor as follows:</span></span>  
  
```csharp  
public MyNewService(string[] args)
{
    InitializeComponent();
    string eventSourceName = "MySource";
    string logName = "MyNewLog";
    if (args.Count() > 0) 
    {
        eventSourceName = args[0];
    }
    if (args.Count() > 1)
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
  
<span data-ttu-id="3502b-221">Tento kód nastaví název zdroje a protokol událostí podle Zadaný spouštěcí parametry, nebo použije výchozí hodnoty, pokud nejsou dodány žádné argumenty.</span><span class="sxs-lookup"><span data-stu-id="3502b-221">This code sets the event source and log name according to the supplied startup parameters, or uses default values if no arguments are supplied.</span></span>  
  
3. <span data-ttu-id="3502b-222">Chcete-li zadat argumenty příkazového řádku, přidejte následující kód, který `ProjectInstaller` třídy v ProjectInstaller.cs nebo ProjectInstaller.vb:</span><span class="sxs-lookup"><span data-stu-id="3502b-222">To specify the command-line arguments, add the following code to the `ProjectInstaller` class in ProjectInstaller.cs or ProjectInstaller.vb:</span></span>  
  
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
  
<span data-ttu-id="3502b-223">Tento kód změní **ImagePath** klíč registru, který obvykle obsahuje úplnou cestu ke spustitelnému souboru pro službu Windows tak, že přidáte výchozí hodnoty parametrů.</span><span class="sxs-lookup"><span data-stu-id="3502b-223">This code modifies the **ImagePath** registry key, which typically contains the full path to the executable for the Windows Service, by adding the default parameter values.</span></span> <span data-ttu-id="3502b-224">Uvozovky kolem cestu (a po každé jednotlivé parametr) jsou požadovány pro službu spustit správně.</span><span class="sxs-lookup"><span data-stu-id="3502b-224">The quotation marks around the path (and around each individual parameter) are required for the service to start up correctly.</span></span> <span data-ttu-id="3502b-225">Chcete-li změnit spouštěcí parametry pro tuto službu Windows, uživatelé mohou změnit parametrech daných **ImagePath** klíč registru, i když lepší je vytvoření a změna programu zpřístupnění funkcí pro uživatele v popisný způsobem (třeba správu nebo konfigurace nástroje).</span><span class="sxs-lookup"><span data-stu-id="3502b-225">To change the startup parameters for this Windows Service, users can change the parameters given in the **ImagePath** registry key, although the better way is to change it programmatically and expose the functionality to users in a friendly way (for example, in a management or configuration utility).</span></span>  
  
<a name="BK_Build"></a>   
## <a name="building-the-service"></a><span data-ttu-id="3502b-226">Vytvoření služby</span><span class="sxs-lookup"><span data-stu-id="3502b-226">Building the Service</span></span>  
  
#### <a name="to-build-your-service-project"></a><span data-ttu-id="3502b-227">Sestavení projektu služby</span><span class="sxs-lookup"><span data-stu-id="3502b-227">To build your service project</span></span>  
  
1.  <span data-ttu-id="3502b-228">V **Průzkumníka řešení**, otevřete kontextovou nabídku pro váš projekt a klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="3502b-228">In **Solution Explorer**, open the context menu for your project, and then choose **Properties**.</span></span> <span data-ttu-id="3502b-229">Stránky vlastností pro váš projekt se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="3502b-229">The property pages for your project  appear.</span></span>  
  
2.  <span data-ttu-id="3502b-230">Na kartě aplikace v **spouštěcí objekt** klikněte na položku **MyNewService.Program**.</span><span class="sxs-lookup"><span data-stu-id="3502b-230">On the Application tab, in the **Startup object** list, choose **MyNewService.Program**.</span></span>  
  
3.  <span data-ttu-id="3502b-231">V **Průzkumníka řešení**, otevřete kontextovou nabídku pro váš projekt a klikněte na tlačítko **sestavení** a sestavte projekt (klávesnice: Ctrl + Shift + B).</span><span class="sxs-lookup"><span data-stu-id="3502b-231">In **Solution Explorer**, open the context menu for your project, and then choose **Build** to build the project (Keyboard: Ctrl+Shift+B).</span></span>  
  
<a name="BK_Install"></a>   
## <a name="installing-the-service"></a><span data-ttu-id="3502b-232">Instalace služby</span><span class="sxs-lookup"><span data-stu-id="3502b-232">Installing the Service</span></span>  
 <span data-ttu-id="3502b-233">Teď, když jste vytvořili službu Windows, můžete ho nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="3502b-233">Now that you've built the Windows service, you can install it.</span></span> <span data-ttu-id="3502b-234">Instalace služby Windows, musí mít pověření správce na počítači, na kterém instalujete ho.</span><span class="sxs-lookup"><span data-stu-id="3502b-234">To install a Windows service, you must have administrative credentials on the computer on which you're installing it.</span></span>  
  
#### <a name="to-install-a-windows-service"></a><span data-ttu-id="3502b-235">Chcete-li nainstalovat službu Windows</span><span class="sxs-lookup"><span data-stu-id="3502b-235">To install a Windows Service</span></span>  
  
1.  <span data-ttu-id="3502b-236">Ve Windows 7 a Windows serveru, otevřete **Developer Command Prompt** pod **Visual Studio Tools** v **Start** nabídky.</span><span class="sxs-lookup"><span data-stu-id="3502b-236">In Windows 7 and Windows Server, open the **Developer Command Prompt** under **Visual Studio Tools** in the **Start** menu.</span></span> <span data-ttu-id="3502b-237">V systému Windows 8 nebo Windows 8.1, zvolte **Visual Studio Tools** na dlaždici **Start** obrazovky a pak spusťte příkazový řádek pro vývojáře s přihlašovacími údaji správce.</span><span class="sxs-lookup"><span data-stu-id="3502b-237">In Windows 8 or Windows 8.1, choose the **Visual Studio Tools** tile on the **Start** screen, and then run Developer Command Prompt with administrative credentials.</span></span> <span data-ttu-id="3502b-238">(Pokud používáte myš, klikněte pravým tlačítkem na **Developer Command Prompt**a klikněte na tlačítko **spustit jako správce**.)</span><span class="sxs-lookup"><span data-stu-id="3502b-238">(If you’re using a mouse, right-click on **Developer Command Prompt**, and then choose **Run as Administrator**.)</span></span>  
  
2.  <span data-ttu-id="3502b-239">V okně příkazového řádku přejděte do složky, který obsahuje výstup projektu.</span><span class="sxs-lookup"><span data-stu-id="3502b-239">In the Command Prompt window, navigate to the folder that contains your project's output.</span></span> <span data-ttu-id="3502b-240">Například v rámci složky Dokumenty přejděte do složky Visual Studio 2013\Projects\MyNewService\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="3502b-240">For example, under your My Documents folder, navigate to Visual Studio 2013\Projects\MyNewService\bin\Debug.</span></span>  
  
3.  <span data-ttu-id="3502b-241">Zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="3502b-241">Enter the following command:</span></span>  
  
    ```  
    installutil.exe MyNewService.exe  
    ```  
  
     <span data-ttu-id="3502b-242">Pokud je služba nainstalována úspěšně, oznámí program installutil.exe úspěch.</span><span class="sxs-lookup"><span data-stu-id="3502b-242">If the service installs successfully, installutil.exe will report success.</span></span> <span data-ttu-id="3502b-243">Pokud systém nemůže najít InstallUtil.exe, ujistěte se, zda existuje ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="3502b-243">If the system could not find InstallUtil.exe, make sure that it exists on your computer.</span></span> <span data-ttu-id="3502b-244">Tento nástroj je nainstalován pomocí rozhraní .NET Framework do složky `%WINDIR%\Microsoft.NET\Framework[64]\` *framework_version*.</span><span class="sxs-lookup"><span data-stu-id="3502b-244">This tool is installed with the .NET Framework to the folder `%WINDIR%\Microsoft.NET\Framework[64]\`*framework_version*.</span></span> <span data-ttu-id="3502b-245">Například výchozí cesta pro 32bitové verze rozhraní .NET Framework 4, 4.5, 4.5.1 a 4.5.2 je `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`.</span><span class="sxs-lookup"><span data-stu-id="3502b-245">For example, the default path for the 32-bit version of the .NET Framework 4, 4.5, 4.5.1, and 4.5.2 is `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`.</span></span>  
  
     <span data-ttu-id="3502b-246">Pokud proces installutil.exe oznámí selhání, naleznete v protokolu instalace a zjistěte, proč.</span><span class="sxs-lookup"><span data-stu-id="3502b-246">If the installutil.exe process reports failure, check the install log to find out why.</span></span> <span data-ttu-id="3502b-247">Ve výchozím nastavení protokolu je ve stejné složce jako spustitelný soubor služby.</span><span class="sxs-lookup"><span data-stu-id="3502b-247">By default the log is in the same folder as the service executable.</span></span> <span data-ttu-id="3502b-248">Instalace může selhat, pokud <xref:System.ComponentModel.RunInstallerAttribute> třída není k dispozici na `ProjectInstaller` třídy, jinak atribut není nastaven na `true`, jinak `ProjectInstaller` třída není `public`.</span><span class="sxs-lookup"><span data-stu-id="3502b-248">The installation can fail if  the <xref:System.ComponentModel.RunInstallerAttribute> Class is not present on the `ProjectInstaller` class, or else the attribute is not set to `true`, or else the `ProjectInstaller` class is not `public`.</span></span>  
  
     <span data-ttu-id="3502b-249">Další informace najdete v tématu [postupy: instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="3502b-249">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
<a name="BK_StartService"></a>   
## <a name="starting-and-running-the-service"></a><span data-ttu-id="3502b-250">Spuštění a spuštěná služba</span><span class="sxs-lookup"><span data-stu-id="3502b-250">Starting and Running the Service</span></span>  
  
#### <a name="to-start-and-stop-your-service"></a><span data-ttu-id="3502b-251">Spuštění a zastavení služby</span><span class="sxs-lookup"><span data-stu-id="3502b-251">To start and stop your service</span></span>  
  
1.  <span data-ttu-id="3502b-252">Ve Windows, otevřete **Start** obrazovky nebo **Start** nabídce a zadejte `services.msc`.</span><span class="sxs-lookup"><span data-stu-id="3502b-252">In Windows, open the **Start** screen or **Start** menu, and type `services.msc`.</span></span>  
  
     <span data-ttu-id="3502b-253">Teď byste měli vidět **MyNewService** uvedené v **služby** okna.</span><span class="sxs-lookup"><span data-stu-id="3502b-253">You should now see **MyNewService** listed in the **Services** window.</span></span>  
  
     <span data-ttu-id="3502b-254">![MyNewService v okně služby. ](../../../docs/framework/windows-services/media/windowsservices-serviceswindow.PNG "WindowsServices_ServicesWindow")</span><span class="sxs-lookup"><span data-stu-id="3502b-254">![MyNewService in the Services window.](../../../docs/framework/windows-services/media/windowsservices-serviceswindow.PNG "WindowsServices_ServicesWindow")</span></span>  
  
2.  <span data-ttu-id="3502b-255">V **služby** okno, otevřete místní nabídku pro vaši službu a pak zvolte **Start**.</span><span class="sxs-lookup"><span data-stu-id="3502b-255">In the **Services** window, open the shortcut menu for your service, and then choose **Start**.</span></span>  
  
3.  <span data-ttu-id="3502b-256">Otevřete místní nabídku pro službu a klikněte na tlačítko **Zastavit**.</span><span class="sxs-lookup"><span data-stu-id="3502b-256">Open the shortcut menu for the service, and then choose **Stop**.</span></span>  
  
4.  <span data-ttu-id="3502b-257">(Volitelné) Z příkazového řádku, můžete použít příkazy `net start``ServiceName` a `net stop``ServiceName` spuštění a zastavení služby.</span><span class="sxs-lookup"><span data-stu-id="3502b-257">(Optional) From the command line, you can use the commands `net start``ServiceName` and `net stop``ServiceName` to start and stop your service.</span></span>  
  
#### <a name="to-verify-the-event-log-output-of-your-service"></a><span data-ttu-id="3502b-258">Ověření výstupu služby v protokolu událostí</span><span class="sxs-lookup"><span data-stu-id="3502b-258">To verify the event log output of your service</span></span>  
  
1.  <span data-ttu-id="3502b-259">V sadě Visual Studio, otevřete **Průzkumníka serveru** (klávesnice: Ctrl + Alt + S) a získat přístup **protokoly událostí** uzel v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="3502b-259">In Visual Studio, open **Server Explorer** (Keyboard: Ctrl+Alt+S), and access the **Event Logs** node for the local computer.</span></span>  
  
2.  <span data-ttu-id="3502b-260">Vyhledejte výpis pro **MyNewLog** (nebo **MyLogFile1**, pokud jste použili volitelný postup k přidání argumentů příkazového řádku) a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="3502b-260">Locate the listing for **MyNewLog** (or **MyLogFile1**, if you used the optional procedure to add command-line arguments) and expand it.</span></span> <span data-ttu-id="3502b-261">Měli byste vidět položky pro dvě akce (spouštění a zastavování) vaše služba provedla.</span><span class="sxs-lookup"><span data-stu-id="3502b-261">You should see entries for the two actions (start and stop) your service has performed.</span></span>  
  
     <span data-ttu-id="3502b-262">![Pomocí prohlížeče událostí zobrazíte položky protokolu událostí. ](../../../docs/framework/windows-services/media/windowsservices-eventviewer.PNG "WindowsServices_EventViewer")</span><span class="sxs-lookup"><span data-stu-id="3502b-262">![Use the Event Viewer to see the event log entries.](../../../docs/framework/windows-services/media/windowsservices-eventviewer.PNG "WindowsServices_EventViewer")</span></span>  
  
<a name="BK_Uninstall"></a>   
## <a name="uninstalling-a-windows-service"></a><span data-ttu-id="3502b-263">Odinstalace služby Windows</span><span class="sxs-lookup"><span data-stu-id="3502b-263">Uninstalling a Windows Service</span></span>  
  
#### <a name="to-uninstall-your-service"></a><span data-ttu-id="3502b-264">Odinstalace služby</span><span class="sxs-lookup"><span data-stu-id="3502b-264">To uninstall your service</span></span>  
  
1.  <span data-ttu-id="3502b-265">Otevřete příkazový řádek pro vývojáře s přihlašovacími údaji správce.</span><span class="sxs-lookup"><span data-stu-id="3502b-265">Open a developer command prompt with administrative credentials.</span></span>  
  
2.  <span data-ttu-id="3502b-266">V okně příkazového řádku přejděte do složky, který obsahuje výstup projektu.</span><span class="sxs-lookup"><span data-stu-id="3502b-266">In the Command Prompt window, navigate to the folder that contains your project's output.</span></span> <span data-ttu-id="3502b-267">Například v rámci složky Dokumenty přejděte do složky Visual Studio 2013\Projects\MyNewService\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="3502b-267">For example, under your My Documents folder, navigate to Visual Studio 2013\Projects\MyNewService\bin\Debug.</span></span>  
  
3.  <span data-ttu-id="3502b-268">Zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="3502b-268">Enter the following command:</span></span>  
  
    ```  
    installutil.exe /u MyNewService.exe  
    ```  
  
     <span data-ttu-id="3502b-269">Pokud je služba úspěšně odinstalována, program installutil.exe oznámí, že byla služba úspěšně odebrána.</span><span class="sxs-lookup"><span data-stu-id="3502b-269">If the service uninstalls successfully, installutil.exe will report that your service was successfully removed.</span></span> <span data-ttu-id="3502b-270">Další informace najdete v tématu [postupy: instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="3502b-270">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="3502b-271">Další kroky</span><span class="sxs-lookup"><span data-stu-id="3502b-271">Next Steps</span></span>  
 <span data-ttu-id="3502b-272">Můžete vytvořit samostatný instalační program, který ostatní mohli používat k instalaci služby Windows, ale vyžaduje další kroky.</span><span class="sxs-lookup"><span data-stu-id="3502b-272">You can create a standalone setup program that others can use to install your Windows service, but it requires additional steps.</span></span> <span data-ttu-id="3502b-273">Technologie ClickOnce nepodporuje služby systému Windows, a proto nelze použít Průvodce publikováním.</span><span class="sxs-lookup"><span data-stu-id="3502b-273">ClickOnce doesn't support Windows services, so you can't use the Publish Wizard.</span></span> <span data-ttu-id="3502b-274">Můžete použít plnou edici nástroje InstallShield, kterou ale společnost Microsoft neposkytuje.</span><span class="sxs-lookup"><span data-stu-id="3502b-274">You can use a full edition of InstallShield, which Microsoft doesn't provide.</span></span> <span data-ttu-id="3502b-275">Další informace o nástroji InstallShield naleznete v tématu [InstallShield Limited Edition](/visualstudio/deployment/installshield-limited-edition).</span><span class="sxs-lookup"><span data-stu-id="3502b-275">For more information about InstallShield, see [InstallShield Limited Edition](/visualstudio/deployment/installshield-limited-edition).</span></span> <span data-ttu-id="3502b-276">Můžete také použít [sady nástrojů XML Instalační služby systému Windows](https://go.microsoft.com/fwlink/?LinkId=249067) vytvořit instalační službu pro službu Windows.</span><span class="sxs-lookup"><span data-stu-id="3502b-276">You can also use the [Windows Installer XML Toolset](https://go.microsoft.com/fwlink/?LinkId=249067) to create an installer for a Windows service.</span></span>  
  
 <span data-ttu-id="3502b-277">Použití může zkoumat <xref:System.ServiceProcess.ServiceController> součásti, která vám umožní odesílat příkazy do služby, které jste nainstalovali.</span><span class="sxs-lookup"><span data-stu-id="3502b-277">You might explore the use of a <xref:System.ServiceProcess.ServiceController> component, which enables you to send commands to the service you have installed.</span></span>  
  
 <span data-ttu-id="3502b-278">Pomocí instalačního programu můžete vytvořit protokol událostí při instalaci aplikace namísto vytvoření protokolu událostí po spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="3502b-278">You can use an installer to create an event log when the application is installed instead of creating the event log when the application runs.</span></span> <span data-ttu-id="3502b-279">Při odinstalaci aplikace navíc instalační program protokol událostí odstraní.</span><span class="sxs-lookup"><span data-stu-id="3502b-279">Additionally, the event log will be deleted by the installer when the application is uninstalled.</span></span> <span data-ttu-id="3502b-280">Další informace najdete v tématu <xref:System.Diagnostics.EventLogInstaller> referenční stránce.</span><span class="sxs-lookup"><span data-stu-id="3502b-280">For more information, see the <xref:System.Diagnostics.EventLogInstaller> reference page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3502b-281">Viz také</span><span class="sxs-lookup"><span data-stu-id="3502b-281">See Also</span></span>  
 [<span data-ttu-id="3502b-282">Aplikace služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="3502b-282">Windows Service Applications</span></span>](../../../docs/framework/windows-services/index.md)  
 [<span data-ttu-id="3502b-283">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="3502b-283">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="3502b-284">Postupy: Ladění aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="3502b-284">How to: Debug Windows Service Applications</span></span>](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [<span data-ttu-id="3502b-285">Služby (Windows)</span><span class="sxs-lookup"><span data-stu-id="3502b-285">Services (Windows)</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms685141.aspx)
