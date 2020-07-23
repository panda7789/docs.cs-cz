---
title: 'Kurz: Vytvoření aplikace služby systému Windows'
description: V tomto kurzu vytvoříte v aplikaci Visual Studio aplikaci služby systému Windows, která zapisuje zprávy do protokolu událostí. Přidejte funkce, nastavte stav, přidejte instalační programy a další.
ms.date: 03/27/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows service applications, walkthroughs
- Windows service applications, creating
ms.assetid: e24d8a3d-edc6-485c-b6e0-5672d91fb607
author: ghogen
ms.openlocfilehash: 487a974af2280a02b83fe685324c9464df705585
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925628"
---
# <a name="tutorial-create-a-windows-service-app"></a>Kurz: Vytvoření aplikace služby systému Windows

Tento článek ukazuje, jak vytvořit aplikaci služby systému Windows v aplikaci Visual Studio, která zapisuje zprávy do protokolu událostí.

## <a name="create-a-service"></a>Vytvoření služby

Začněte tím, že vytvoříte projekt a nastavíte hodnoty požadované pro správné fungování služby.

1. V nabídce **soubor** v aplikaci Visual Studio vyberte **Nový**  >  **projekt** (nebo stiskněte klávesy **CTRL** + **SHIFT** + **N**) a otevřete tak okno **Nový projekt** .

2. Přejděte na a vyberte šablonu projektu **služba systému Windows (.NET Framework)** . Pokud ho chcete najít, rozbalte položku **nainstalované** a **Visual C#** nebo **Visual Basic**a pak vyberte **Desktop Windows**. Případně zadejte do vyhledávacího pole v pravém horním rohu *službu Windows* a stiskněte klávesu **ENTER**.

   ![Šablona služby systému Windows v dialogovém okně Nový projekt v aplikaci Visual Studio](./media/new-project-dialog.png)

   > [!NOTE]
   > Pokud nevidíte šablonu **služby systému Windows** , bude pravděpodobně nutné nainstalovat úlohu **vývoj desktopových** aplikací pro .NET:
   >
   > V dialogovém okně **Nový projekt** vyberte v levém dolním rohu **otevřít instalační program pro Visual Studio** . Vyberte úlohu **vývoj desktopových aplikací .NET** a pak vyberte **Upravit**.

3. Jako **název**zadejte *MyNewService*a pak vyberte **OK**.

   Zobrazí se karta **Návrh** (**Service1.cs [Design]** nebo **Service1. vb [Design]**).

   Šablona projektu obsahuje třídu komponenty s názvem `Service1` , která dědí z <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> . Zahrnuje většinu základního kódu služby, jako je například kód pro spuštění služby.

## <a name="rename-the-service"></a>Přejmenování služby

Přejmenujte službu z **Service1** na **MyNewService**.

1. V **Průzkumník řešení**vyberte **Service1.cs**nebo **Service1. vb**a zvolte **Přejmenovat** z místní nabídky. Přejmenujte soubor na **MyNewService.cs**nebo **MyNewService. vb**a potom stiskněte klávesu **ENTER** .

    Automaticky otevírané okno se zobrazí dotaz, zda byste chtěli přejmenovat všechny odkazy na prvek kódu *Service1*.

2. V místním okně vyberte **Ano**.

    ![Přejmenovat výzvu](./media/windows-service-rename.png "Výzva k přejmenování služby systému Windows")

3. Na kartě **Návrh** v místní nabídce vyberte možnost **vlastnosti** . V okně **vlastnosti** změňte hodnotu **ServiceName** na *MyNewService*.

    ![Vlastnosti služby](./media/windows-service-properties.png "Vlastnosti služby systému Windows")

4. V nabídce **soubor** vyberte **Uložit vše** .

## <a name="add-features-to-the-service"></a>Přidání funkcí do služby

V této části přidáte do služby systému Windows vlastní protokol událostí. <xref:System.Diagnostics.EventLog>Komponenta je příkladem typu komponenty, kterou můžete přidat do služby systému Windows.

### <a name="add-custom-event-log-functionality"></a>Přidání funkce vlastního protokolu událostí

1. V **Průzkumník řešení**v místní nabídce pro **MyNewService.cs**nebo **MyNewService. vb**vyberte možnost **Návrhář zobrazení**.

2. V **sadě nástrojů**rozbalte položku **součásti**a přetáhněte komponentu **EventLog** na kartu **Service1.cs [Design]** nebo **Service1. vb [Design]** .

3. V **Průzkumník řešení**v místní nabídce pro **MyNewService.cs**nebo **MyNewService. vb**vyberte **Zobrazit kód**.

4. Definujte vlastní protokol událostí. V jazyce C# upravte existující `MyNewService()` konstruktor; pro Visual Basic přidejte `New()` konstruktor:

   [!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#2)]
   [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]

5. Přidejte `using` příkaz do **MyNewService.cs** (Pokud ještě neexistuje) nebo `Imports` příkaz **MyNewService. vb**pro <xref:System.Diagnostics?displayProperty=nameWithType> obor názvů:

    ```csharp
    using System.Diagnostics;
    ```

    ```vb
    Imports System.Diagnostics
    ```

6. V nabídce **soubor** vyberte **Uložit vše** .

### <a name="define-what-occurs-when-the-service-starts"></a>Definujte, co se stane při spuštění služby.

V editoru kódu pro **MyNewService.cs** nebo **MyNewService. vb**vyhledejte <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodu; Visual Studio automaticky vytvořilo prázdnou definici metody při vytváření projektu. Přidejte kód, který při spuštění služby zapíše záznam do protokolu událostí:

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

#### <a name="polling"></a>Cyklické dotazování

Vzhledem k tomu, že je aplikace služby navržena jako dlouhodobá, obvykle se dotazuje nebo monitoruje systém, který jste nastavili v <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodě. `OnStart`Metoda se musí vrátit k operačnímu systému po zahájení operace služby, aby systém nebyl zablokován.

K nastavení jednoduchého mechanismu cyklického dotazování použijte <xref:System.Timers.Timer?displayProperty=nameWithType> komponentu. Časovač vyvolá <xref:System.Timers.Timer.Elapsed> událost v pravidelných intervalech, kdy služba může provádět její monitorování. Komponentu můžete použít následujícím <xref:System.Timers.Timer> způsobem:

- Nastavte vlastnosti <xref:System.Timers.Timer> komponenty v `MyNewService.OnStart` metodě.
- Spusťte časovač voláním <xref:System.Timers.Timer.Start%2A> metody.

##### <a name="set-up-the-polling-mechanism"></a>Nastavte mechanismus cyklického dotazování.

1. Přidejte následující kód do `MyNewService.OnStart` události pro nastavení mechanismu cyklického dotazování:

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

2. Přidejte `using` příkaz do **MyNewService.cs**nebo `Imports` příkaz do **MyNewService. vb**pro <xref:System.Timers?displayProperty=nameWithType> obor názvů:

   ```csharp
   using System.Timers;
   ```

   ```vb
   Imports System.Timers
   ```

3. Do `MyNewService` třídy přidejte `OnTimer` metodu pro zpracování <xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType> události:

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

4. Ve `MyNewService` třídě přidejte členskou proměnnou. Obsahuje identifikátor další události, která má být zapsána do protokolu událostí:

   ```csharp
   private int eventId = 1;
   ```

   ```vb
   Private eventId As Integer = 1
   ```

Místo spuštění veškeré práce v hlavním vlákně můžete spouštět úlohy pomocí pracovních vláken na pozadí. Další informace naleznete v tématu <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.

### <a name="define-what-occurs-when-the-service-is-stopped"></a>Definujte, co se stane, když se služba zastaví.

Vložte řádek kódu do <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody, která po zastavení služby přidá záznam do protokolu událostí:

[!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#4)]
[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a>Definování dalších akcí služby

Můžete přepsat <xref:System.ServiceProcess.ServiceBase.OnPause%2A> <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> metody, a <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> pro definování dalšího zpracování pro komponentu.

Následující kód ukazuje, jak přepsat <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> metodu ve `MyNewService` třídě:

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]

## <a name="set-service-status"></a>Nastavit stav služby

Služba oznámí jejich stav [Správci řízení služeb](/windows/desktop/Services/service-control-manager) , aby uživatel mohl zjistit, jestli služba funguje správně. Ve výchozím nastavení služba, která dědí z, <xref:System.ServiceProcess.ServiceBase> hlásí omezené sady nastavení stavu, mezi které patří SERVICE_STOPPED, SERVICE_PAUSED a SERVICE_RUNNING. Pokud se služba začne spouštět, je vhodné ohlásit stav SERVICE_START_PENDING.

Můžete implementovat nastavení stavu SERVICE_START_PENDING a SERVICE_STOP_PENDING přidáním kódu, který volá funkci Windows [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) .

### <a name="implement-service-pending-status"></a>Implementovat stav nedokončené služby

1. Přidejte `using` příkaz do **MyNewService.cs**nebo `Imports` příkaz do **MyNewService. vb**pro <xref:System.Runtime.InteropServices?displayProperty=nameWithType> obor názvů:

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. Přidejte následující kód do **MyNewService.cs**nebo **MyNewService. vb**pro deklaraci `ServiceState` hodnoty a pro přidání struktury pro stav, který použijete v volání vyvolání platformy:

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
    > Správce řízení služeb používá `dwWaitHint` členy a ke `dwCheckpoint` [struktuře SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) k určení, kolik času se má čekat na spuštění nebo vypnutí služby systému Windows. Pokud vaše `OnStart` `OnStop` metody a běží dlouho, může vaše služba požádat o další čas tím, že `SetServiceStatus` se znovu zavolá s narůstající `dwCheckPoint` hodnotou.

3. Ve `MyNewService` třídě Deklarujte funkci [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) pomocí [vyvolání platformy](../interop/consuming-unmanaged-dll-functions.md):

    ```csharp
    [DllImport("advapi32.dll", SetLastError = true)]
    private static extern bool SetServiceStatus(System.IntPtr handle, ref ServiceStatus serviceStatus);
    ```

    ```vb
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean
    ```

4. Chcete-li implementovat stav SERVICE_START_PENDING, přidejte následující kód na začátek <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody:

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

5. Přidejte kód na konec `OnStart` metody pro nastavení stavu na SERVICE_RUNNING:

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

6. Volitelné Pokud <xref:System.ServiceProcess.ServiceBase.OnStop%2A> je dlouhodobě spuštěná metoda, opakujte tento postup v `OnStop` metodě. Před ukončením metody implementujte stav SERVICE_STOP_PENDING a vraťte stav SERVICE_STOPPED `OnStop` .

   Příklad:

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

## <a name="add-installers-to-the-service"></a>Přidat instalační programy do služby

Před spuštěním služby systému Windows je nutné ji nainstalovat, která ji zaregistruje ve Správci řízení služeb. Přidejte instalační programy do projektu pro zpracování podrobností o registraci.

1. V **Průzkumník řešení**v místní nabídce pro **MyNewService.cs**nebo **MyNewService. vb**vyberte možnost **Návrhář zobrazení**.

2. V zobrazení **Návrh** vyberte oblast pozadí a pak zvolte **Přidat instalační program** z místní nabídky.

     Ve výchozím nastavení Visual Studio přidá třídu komponenty s názvem `ProjectInstaller` , která obsahuje dva instalační programy, do vašeho projektu. Tyto instalační programy jsou pro vaši službu a pro přidružený proces služby.

3. V zobrazení **Návrh** pro **ProjectInstaller**vyberte možnost **ServiceInstaller1** pro projekt jazyka Visual C# nebo **ServiceInstaller1** pro projekt Visual Basic a pak v místní nabídce zvolte možnost **vlastnosti** .

4. V okně **vlastnosti** ověřte, zda <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> je vlastnost nastavena na hodnotu **MyNewService**.

5. Přidejte text do <xref:System.ServiceProcess.ServiceInstaller.Description%2A> vlastnosti, jako je například *ukázková služba*.

     Tento text se zobrazí ve sloupci **Popis** v okně **služby** a popisuje službu pro uživatele.

    ![Popis služby v okně služby.](./media/windows-service-description.png "Popis služby")

6. Přidejte text do <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> Vlastnosti. Například *zobrazované jméno MyNewService*.

     Tento text se zobrazí ve sloupci **Zobrazovaný název** v okně **služby** . Tento název se může lišit od <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> vlastnosti, což je název, který systém používá (například název, který pro příkaz použijete `net start` ke spuštění služby).

7. Nastavte <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnost na <xref:System.ServiceProcess.ServiceStartMode.Automatic> z rozevíracího seznamu.

8. Až budete hotovi, okna **vlastností** by měla vypadat jako na následujícím obrázku:

     ![Vlastnosti instalačního programu pro službu systému Windows](./media/windows-service-installer-properties.png "Vlastnosti instalačního programu služby systému Windows")

9. V zobrazení **Návrh** pro **ProjectInstaller**zvolte **položku ServiceProcessInstaller1** pro projekt jazyka Visual C#, nebo **položku ServiceProcessInstaller1** pro projekt Visual Basic a potom v místní nabídce zvolte možnost **vlastnosti** . Nastavte <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> vlastnost na <xref:System.ServiceProcess.ServiceAccount.LocalSystem> z rozevíracího seznamu.

     Toto nastavení nainstaluje službu a spustí ji pomocí účtu místního systému.

    > [!IMPORTANT]
    > <xref:System.ServiceProcess.ServiceAccount.LocalSystem>Účet má široké oprávnění, včetně možnosti zapisovat do protokolu událostí. Používejte tento účet opatrně, protože může zvýšit riziko napadení škodlivým softwarem. Pro jiné úlohy zvažte použití <xref:System.ServiceProcess.ServiceAccount.LocalService> účtu, který v místním počítači funguje jako Neprivilegovaný uživatel a prezentuje anonymní přihlašovací údaje pro všechny vzdálené servery. Tento příklad se nezdařil, pokud se pokusíte použít <xref:System.ServiceProcess.ServiceAccount.LocalService> účet, protože potřebuje oprávnění k zápisu do protokolu událostí.

Další informace o instalačních programech najdete v tématu [Postup: Přidání instalačních programů do aplikace služby](how-to-add-installers-to-your-service-application.md).

## <a name="optional-set-startup-parameters"></a>Volitelné Nastavení spouštěcích parametrů

> [!NOTE]
> Než se rozhodnete přidat parametry spuštění, zvažte, jestli je to nejlepší způsob, jak předat službě informace. I když je lze snadno použít a analyzovat a uživatel je může snadno přepsat, může být obtížnější ho zjistit a použít bez dokumentace. Obecně platí, že pokud vaše služba vyžaduje více než jen několik parametrů spuštění, měli byste místo toho použít registr nebo konfigurační soubor.

Služba systému Windows může přijmout argumenty příkazového řádku nebo parametry spuštění. Když přidáte kód pro zpracování parametrů spuštění, může uživatel spustit vaši službu s vlastními parametry spuštění v okně Vlastnosti služby. Tyto parametry spuštění se ale při příštím spuštění služby neuchovávají. Chcete-li nastavit parametry spouštění trvale, nastavte je v registru.

Každá služba systému Windows obsahuje položku registru pod podklíčem **HKEY_LOCAL_MACHINE \system\currentcontrolset\services** . V rámci podklíče jednotlivých služeb můžete pomocí podklíče **parametrů** ukládat informace, ke kterým má vaše služba přístup. Konfigurační soubory aplikace pro službu systému Windows můžete použít stejným způsobem jako u jiných typů programů. Vzorový kód naleznete v tématu <xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType> .

### <a name="to-add-startup-parameters"></a>Přidání parametrů spuštění

1. Vyberte **program.cs**nebo **MyNewService. Designer. vb**a pak zvolte **Zobrazit kód** z místní nabídky. V `Main` metodě změňte kód a přidejte vstupní parametr a předejte jej do konstruktoru služby:

   [!code-csharp[VbRadconService](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/Program-add-parameter.cs?highlight=1,6)]
   [!code-vb[VbRadconService](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.Designer-add-parameter.vb?highlight=1-2)]

2. V **MyNewService.cs**nebo **MyNewService. vb**změňte `MyNewService` konstruktor tak, aby zpracoval vstupní parametr následujícím způsobem:

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

   Tento kód nastaví zdroj a název protokolu události podle parametrů spuštění, které uživatel dodá. Pokud nejsou zadány žádné argumenty, budou použity výchozí hodnoty.

3. Chcete-li zadat argumenty příkazového řádku, přidejte následující kód do `ProjectInstaller` třídy v **ProjectInstaller.cs**nebo **ProjectInstaller. vb**:

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

   Tato hodnota obvykle obsahuje úplnou cestu ke spustitelnému souboru pro službu systému Windows. Aby se služba spouštěla správně, musí uživatel pro cestu a jednotlivé parametry dodat uvozovky. Uživatel může změnit parametry v záznamu registru **ImagePath** pro změnu spouštěcích parametrů pro službu systému Windows. Lepším způsobem je však změnit hodnotu programově a zpřístupnit funkce uživatelsky přívětivým způsobem, například pomocí nástroje pro správu nebo konfiguraci.

## <a name="build-the-service"></a>Sestavení služby

1. V **Průzkumník řešení**v místní nabídce projektu **MyNewService** vyberte možnost **vlastnosti** .

   Zobrazí se stránky vlastností projektu.

2. Na kartě **aplikace** v seznamu **spouštěcí objekt** vyberte **MyNewService. Program**nebo **Sub Main** pro Visual Basic projekty.

3. Chcete-li sestavit projekt, v **Průzkumník řešení**zvolte možnost **sestavit** z místní nabídky projektu (nebo stiskněte klávesovou zkratku **CTRL** + **SHIFT** + **B**).

## <a name="install-the-service"></a>Instalace služby

Teď, když jste sestavili službu systému Windows, ji můžete nainstalovat. Chcete-li nainstalovat službu systému Windows, je nutné mít v počítači, kde je nainstalován, pověření správce.

1. Otevřete [Developer Command Prompt pro Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs) s přihlašovacími údaji správce. V nabídce **Start** systému Windows vyberte ve složce Visual Studio možnost **Developer Command Prompt pro vs 2017** a potom v místní nabídce vyberte **Další**  >  **Spustit jako správce** .

2. V okně **Developer Command Prompt pro Visual Studio** přejděte do složky, která obsahuje výstup vašeho projektu (ve výchozím nastavení je to podadresář *\bin\debug* projektu).

3. Zadejte následující příkaz:

    ```shell
    installutil MyNewService.exe
    ```

    Pokud se služba nainstaluje úspěšně, příkaz ohlásí úspěch.

    Pokud systém nemůže najít *installutil.exe*, ujistěte se, že v počítači existuje. Tento nástroj se instaluje s .NET Framework do složky * \\ &lt; verze &gt; architektury%windir%\Microsoft.NET\Framework [64]*. Například výchozí cesta pro 64 verze je *% windir% \Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.

    Pokud se **installutil.exe** proces nezdařil, zjistěte v protokolu o instalaci, proč. Ve výchozím nastavení je protokol ve stejné složce jako spustitelný soubor služby. Instalace může selhat, pokud:
    - <xref:System.ComponentModel.RunInstallerAttribute>Třída není ve třídě k dispozici `ProjectInstaller` .
    - Atribut není nastaven na hodnotu `true` .
    - `ProjectInstaller`Třída není definovaná jako `public` .

Další informace najdete v tématu [Postupy: instalace a odinstalace služeb](how-to-install-and-uninstall-services.md).

## <a name="start-and-run-the-service"></a>Spuštění a spuštění služby

1. V systému Windows otevřete desktopovou aplikaci **služby** . Stisknutím **Windows** + **R** otevřete pole **Spustit** , zadejte *Services. msc*a potom stiskněte klávesu **ENTER** nebo klikněte na **tlačítko OK**.

     Vaše služba by se měla zobrazit v seznamu **služby**zobrazená abecedně podle zobrazovaného názvu, který jste pro něj nastavili.

     ![MyNewService v okně služby.](./media/windowsservices-serviceswindow.PNG)

2. Službu spustíte tak, že v místní nabídce služby zvolíte možnost **Spustit** .

3. Pokud chcete službu zastavit, v místní nabídce služby klikněte na **zastavit** .

4. Volitelné Na příkazovém řádku spusťte a zastavte službu pomocí příkazu **net start &lt; Service název &gt; ** a ** &lt; název &gt; služby net stop** .

### <a name="verify-the-event-log-output-of-your-service"></a>Ověření výstupu protokolu událostí vaší služby

1. Ve Windows otevřete **Prohlížeč událostí** desktopovou aplikaci. Do panelu hledání ve Windows zadejte *Prohlížeč událostí* a pak ve výsledcích hledání vyberte **Prohlížeč událostí** .

   > [!TIP]
   > V aplikaci Visual Studio můžete získat přístup k protokolům událostí otevřením **Průzkumník serveru** v nabídce **zobrazení** (nebo stisknutím kláves **CTRL** + **+ ALT** + **S**) a rozbalením uzlu **protokoly událostí** pro místní počítač.

2. V **Prohlížeč událostí**rozbalte **protokoly aplikací a služeb**.

3. Vyhledejte výpis pro **myNewLog** (nebo **MyLogFile1** , pokud jste postupovali podle postupu pro přidání argumentů příkazového řádku) a rozbalte ho. Měli byste vidět položky dvou akcí (spustit a zastavit), které služba provedla.

     ![Použití Prohlížeč událostí k zobrazení položek protokolu událostí](./media/windows-service-event-viewer.png)

## <a name="clean-up-resources"></a>Vyčištění prostředků

Pokud už aplikaci služby systému Windows nepotřebujete, můžete ji odebrat.

1. Otevřete **Developer Command Prompt pro Visual Studio** s přihlašovacími údaji správce.

2. V okně **Developer Command Prompt pro Visual Studio** přejděte do složky, která obsahuje výstup vašeho projektu.

3. Zadejte následující příkaz:

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   Pokud se služba úspěšně odinstaluje, příkaz oznámí, že vaše služba byla úspěšně odebrána. Další informace najdete v tématu [Postupy: instalace a odinstalace služeb](how-to-install-and-uninstall-services.md).

## <a name="next-steps"></a>Další kroky

Teď, když jste vytvořili službu, můžete:

- Vytvoření samostatného instalačního programu, který bude používat k instalaci služby systému Windows. Pomocí sady [nástrojů WIX](https://wixtoolset.org/) můžete vytvořit instalační program pro službu systému Windows. Další nápady najdete v tématu [Vytvoření balíčku instalačního programu](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).

- Prozkoumejte <xref:System.ServiceProcess.ServiceController> komponentu, která vám umožní odesílat příkazy do služby, kterou jste nainstalovali.

- Místo vytvoření protokolu událostí při spuštění aplikace použijte instalační program k vytvoření protokolu událostí při instalaci aplikace. Protokol událostí je odstraněn instalačním programem při odinstalaci aplikace. Další informace naleznete v tématu <xref:System.Diagnostics.EventLogInstaller>.

## <a name="see-also"></a>Viz také

- [Aplikace služby systému Windows](index.md)
- [Úvod do aplikací služby systému Windows](introduction-to-windows-service-applications.md)
- [Postupy: ladění aplikací služby systému Windows](how-to-debug-windows-service-applications.md)
- [Služby (Windows)](/windows/desktop/Services/services)
