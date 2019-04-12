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
ms.openlocfilehash: 35ef113acffbebdcd4cb585970e575f17959f75b
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/12/2019
ms.locfileid: "59518029"
---
# <a name="tutorial-create-a-windows-service-app"></a>Kurz: Vytvoření aplikace služby Windows

Tento článek ukazuje, jak vytvořit aplikaci služby Windows v sadě Visual Studio, která zapisuje zprávy do protokolu událostí.

## <a name="create-a-service"></a>Vytvoření služby

Pokud chcete začít, vytvořte projekt a nastavte hodnoty, které jsou požadovány pro správné fungování služby.

1. Ze sady Visual Studio **souboru** nabídce vyberte možnost **nový** > **projektu** (nebo stiskněte klávesu **Ctrl** + **Shift**+**N**) Chcete-li otevřít **nový projekt** okna.

2. Vyhledejte a vyberte **služba Windows (.NET Framework)** šablony projektu. Pokud chcete ji najít, rozbalte **nainstalováno** a **Visual C#**  nebo **jazyka Visual Basic**a pak vyberte **Windows Desktop**. Nebo zadejte *Windows Service* do vyhledávacího pole na vpravo nahoře a stiskněte klávesu **Enter**.

   ![Šablona služby Windows v dialogu Nový projekt v sadě Visual Studio](media/new-project-dialog.png)

   > [!NOTE]
   > Pokud se nezobrazí **Windows Service** šablony, je nutné nainstalovat **vývoj desktopových aplikací .NET** úlohy:
   >  
   > V **nový projekt** dialogového okna, vyberte **otevřít instalační program Visual Studio** v levé dolní části. Vyberte **vývoj desktopových aplikací .NET** úlohy a pak vyberte **změnit**.

3. Pro **název**, zadejte *MyNewService*a pak vyberte **OK**.

   **Návrhu** se zobrazí karta (**Service1.cs [Design]** nebo **Service1.vb [Design]**).
   
   Šablona projektu zahrnuje komponentní třídu s názvem `Service1` , která dědí z <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>. Obsahuje velkou část základního kódu služby, jako je například kód ke spuštění služby.

## <a name="rename-the-service"></a>Přejmenování služby

Přejmenování služby z **Service1** k **MyNewService**.

1. V **Průzkumníka řešení**vyberte **Service1.cs**, nebo **Service1.vb**a zvolte **přejmenovat** z místní nabídky. Přejmenujte soubor na **MyNewService.cs**, nebo **MyNewService.vb**a potom stiskněte klávesu **Enter**

    Zobrazí se automaticky otevírané okno s dotazem, zda chcete přejmenovat všechny odkazy na prvek kódu *Service1*.

2. V místním okně vyberte **Ano**.

    ![Přejmenovat řádku](media/windows-service-rename.png "Windows service přejmenovat řádku")

2. V **návrhu** kartu, vyberte možnost **vlastnosti** z místní nabídky. Z **vlastnosti** okno Změnit **ServiceName** hodnota, která se *MyNewService*.

    ![Vlastnosti služby](media/windows-service-properties.png "vlastností služby Windows")

3. Vyberte **Uložit vše** z **souboru** nabídky.

## <a name="add-features-to-the-service"></a>Přidání funkcí do služby

V této části přidáte do služby Windows vlastního protokolu událostí. <xref:System.Diagnostics.EventLog> Komponenta je příkladem typ součásti, můžete přidat do služby Windows.

### <a name="add-custom-event-log-functionality"></a>Přidání funkce vlastního protokolu událostí

1. V **Průzkumníka řešení**, v místní nabídce pro **MyNewService.cs**, nebo **MyNewService.vb**, zvolte **Návrhář zobrazení**.

2. V **nástrojů**, rozbalte **součásti**a pak přetáhněte **EventLog** komponentu do **Service1.cs [Design]**, nebo  **Service1.VB [Design]** kartu.

3. V **Průzkumníka řešení**, v místní nabídce pro **MyNewService.cs**, nebo **MyNewService.vb**, zvolte **zobrazit kód**.

4. Definování vlastního protokolu událostí. Pro C#, upravte existující `MyNewService()` konstruktor; v jazyce Visual Basic přidejte `New()` konstruktor:

   [!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#2)]
   [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]

5. Přidat `using` příkazu **MyNewService.cs** (pokud ještě neexistuje), nebo `Imports` příkaz **MyNewService.vb**, pro <xref:System.Diagnostics?displayProperty=nameWithType> obor názvů:

    ```csharp
    using System.Diagnostics;
    ```

    ```vb
    Imports System.Diagnostics
    ```

6. Vyberte **Uložit vše** z **souboru** nabídky.

### <a name="define-what-occurs-when-the-service-starts"></a>Definujte, co se stane při spuštění služby

V editoru kódu pro **MyNewService.cs** nebo **MyNewService.vb**, vyhledejte <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody. Visual Studio automaticky vytvoří definici prázdnou metodu při vytváření projektu. Přidejte kód, který zapíše položku do protokolu událostí při spuštění služby:

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

#### <a name="polling"></a>Dotazování

Protože aplikace služby byla navržena jako dlouhotrvající, obvykle dotazuje nebo sleduje systém, který jste vytvořili v <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody. `OnStart` Metoda musí vracet v operačním systému po operaci služby tak, aby systém není blokován. 

Pokud chcete nastavit jednoduchý mechanismus dotazování, použijte <xref:System.Timers.Timer?displayProperty=nameWithType> komponenty. Časovač vyvolá <xref:System.Timers.Timer.Elapsed> události v pravidelných intervalech, po kterém můžete provádět monitorování vaší služby. Můžete použít <xref:System.Timers.Timer> komponenty následujícím způsobem:

- Nastavte vlastnosti <xref:System.Timers.Timer> v komponentu `MyNewService.OnStart` metody.
- Spuštění časovače voláním <xref:System.Timers.Timer.Start%2A> metody.

##### <a name="set-up-the-polling-mechanism"></a>Nastavte dotazovací mechanismus.

1. Přidejte následující kód `MyNewService.OnStart` událost nastavit dotazovací mechanismus:

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

2. Přidat `using` příkazu **MyNewService.cs**, nebo `Imports` příkazu **MyNewService.vb**, pro <xref:System.Timers?displayProperty=nameWithType> obor názvů:

   ```csharp
   using System.Timers;
   ```

   ```vb
   Imports System.Timers
   ```

3. V `MyNewService` třídy, přidejte `OnTimer` metodu ke zpracování <xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType> události:

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

4. V `MyNewService` třídy, přidat členskou proměnnou. Obsahuje identifikátor další události pro zápis do protokolu událostí:

   ```csharp
   private int eventId = 1;
   ```

   ```vb
   Private eventId As Integer = 1
   ```

Místo spouštění veškerou práci na hlavním vlákně, můžete spouštět úlohy s použitím pracovních vláken na pozadí. Další informace naleznete v tématu <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.

### <a name="define-what-occurs-when-the-service-is-stopped"></a>Definujte, co se stane při zastavení služby

Vložit řádek kódu <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metodu, která přidá položku do protokolu událostí po zastavení služby:

[!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#4)]
[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a>Definování dalších akcí služby

Je možné přepsat <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, a <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> metody definovat další zpracování pro komponentu. 

Následující kód ukazuje, jak přepsat <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> metodu `MyNewService` třídy:

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]

## <a name="set-service-status"></a>Nastavit stav služby

Služby oznamují svůj stav na [správce řízení služeb](/windows/desktop/Services/service-control-manager) tak, aby uživatel můžete zjistit, jestli služba správně funguje. Ve výchozím nastavení, služby, která dědí z <xref:System.ServiceProcess.ServiceBase> omezenou sadu nastavení stavu, které zahrnují SERVICE_STOPPED SERVICE_PAUSED a SERVICE_RUNNING sestavy. Pokud služba chvíli trvat, než se spustí, je vhodné informuje o stavu SERVICE_START_PENDING. 

Nastavení stavu SERVICE_START_PENDING a SERVICE_STOP_PENDING můžete implementovat přidáním kódu, který volá Windows [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) funkce.

### <a name="implement-service-pending-status"></a>Implementace služby čekajícím stavu

1. Přidat `using` příkazu **MyNewService.cs**, nebo `Imports` příkazu **MyNewService.vb**, pro <xref:System.Runtime.InteropServices?displayProperty=nameWithType> obor názvů:

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. Přidejte následující kód, který **MyNewService.cs**, nebo **MyNewService.vb**, chcete-li deklarovat `ServiceState` hodnoty a přidat strukturu pro stav, který budete používat ve volání funkce invoke:

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
    > Správce řízení služeb používá `dwWaitHint` a `dwCheckpoint` členy [SERVICE_STATUS struktura](/windows/desktop/api/winsvc/ns-winsvc-_service_status) k určení doby čekání na službu Windows ke spuštění nebo vypnutí. Pokud vaše `OnStart` a `OnStop` metody se spustí, long, vaše služba může požádat o víc času voláním `SetServiceStatus` znovu se zvýšena `dwCheckPoint` hodnotu.

3. V `MyNewService` třídy, deklarujte [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) funkce s použitím [vyvolání platformy](../interop/consuming-unmanaged-dll-functions.md):

    ```csharp
    [DllImport("advapi32.dll", SetLastError = true)]
    private static extern bool SetServiceStatus(System.IntPtr handle, ref ServiceStatus serviceStatus);
    ```

    ```vb
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean
    ```

4. K implementaci SERVICE_START_PENDING stavu, přidejte následující kód do začátku <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody:

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

5. Přidejte kód do konce `OnStart` metody nastavte stav SERVICE_RUNNING:

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

6. (Volitelné) Pokud <xref:System.ServiceProcess.ServiceBase.OnStop%2A> je metoda dlouhotrvající, opakujte tento postup `OnStop` metoda. Implementace SERVICE_STOP_PENDING stav a stav SERVICE_STOPPED před vrácení `OnStop` metoda ukončení.

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

## <a name="add-installers-to-the-service"></a>Přidání instalačních programů do služby

Před spuštěním služby Windows musíte nainstalovat, které je zaregistruje ho s správce řízení služeb. Přidání instalačních programů do projektu pro zpracování podrobnosti registrace.

1. V **Průzkumníka řešení**, v místní nabídce pro **MyNewService.cs**, nebo **MyNewService.vb**, zvolte **Návrhář zobrazení**.

2. V **návrhu** zobrazení, vyberte oblast, pozadí a pak zvolte **přidat instalační program** z místní nabídky.

     Ve výchozím nastavení, sada Visual Studio přidá komponentní třídu s názvem `ProjectInstaller`, který obsahuje dva instalační programy, do projektu. Tyto instalační programy jsou pro vaši službu a pro služby přidruženého procesu.

4. V **návrhu** zobrazit **ProjectInstaller**vyberte **serviceInstaller1** vizuálu C# projektu, nebo **ServiceInstaller1**projektu jazyka Visual Basic, zvolte **vlastnosti** z místní nabídky.

5. V **vlastnosti** okna, ověřte <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> je nastavena na **MyNewService**.

6. Přidejte text, který se <xref:System.ServiceProcess.ServiceInstaller.Description%2A> vlastnost, jako například *Ukázka služby*. 

     Tento text se zobrazí **popis** sloupec **služby** okno a popisuje službu pro uživatele.

    ![Popis služby v okně služby. ](media/windows-service-description.png "Popis služby")

7. Přidejte text, který má <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> vlastnost. Například *MyNewService zobrazovaný název*. 

     Tento text se zobrazí **zobrazovaný název** sloupec **služby** okna. Tento název se může lišit od <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> vlastnost, která je název, použije systém (třeba název, který slouží pro `net start` příkaz pro spuštění služby).

8. Nastavte <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnost <xref:System.ServiceProcess.ServiceStartMode.Automatic> z rozevíracího seznamu.

9. Jakmile budete hotovi, **vlastnosti** windows by měl vypadat jako na následujícím obrázku:

     ![Vlastnosti Instalační služby systému Windows služby](media/windows-service-installer-properties.png "služby vlastnosti Instalační služby systému Windows")

9. V **návrhu** zobrazit **ProjectInstaller**, zvolte **serviceProcessInstaller1** vizuálu C# projektu, nebo **ServiceProcessInstaller1**  projektu jazyka Visual Basic, zvolte **vlastnosti** z místní nabídky. Nastavte <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> vlastnost <xref:System.ServiceProcess.ServiceAccount.LocalSystem> z rozevíracího seznamu. 

     Toto nastavení se nainstaluje službu a běží za použití místního systémového účtu.

    > [!IMPORTANT]
    > <xref:System.ServiceProcess.ServiceAccount.LocalSystem> Účet má širší oprávnění, včetně možnosti zapisovat do protokolu událostí. Používejte tento účet opatrně, protože může zvýšit riziko napadení škodlivým softwarem. Pro jiné úlohy zvažte použití <xref:System.ServiceProcess.ServiceAccount.LocalService> účet, který funguje jako neprivilegované uživatele v místním počítači a nabízí pověření anonymního a jakémukoli vzdálenému serveru. V tomto příkladu se nezdaří, pokud se pokusíte použít <xref:System.ServiceProcess.ServiceAccount.LocalService> účtu, proto, že potřebuje oprávnění k zápisu do protokolu událostí.

Další informace o instalačních programů najdete v tématu [jak: Přidání instalačních programů do aplikace služby](how-to-add-installers-to-your-service-application.md).

## <a name="optional-set-startup-parameters"></a>(Volitelné) Nastavit parametry spuštění

> [!NOTE]
> Předtím, než se rozhodnete přidat parametry spuštění, zvažte, zda je nejlepší způsob, jak předávání informací do vaší služby. I když jsou snadno použitelné a analýzy a uživatel snadno je můžete přepsat, mohou být obtížnější uživatelům objevit a používat bez dokumentaci. Obecně platí Pokud vaše služba vyžaduje více než několik parametrů spuštění, měli byste použít registru nebo konfiguračního souboru místo toho. 

Služba Windows může přijmout argumenty příkazového řádku, nebo parametry spuštění. Když přidáte kód do parametrů spuštění procesu, uživatele můžete začít vaši službu s vlastní vlastní spouštěcí parametry v okně Vlastnosti služby. Tyto spouštěcí parametry nejsou však zachované při příštím spuštění služby. Pokud chcete nastavit spouštěcí parametry trvale, jejich nastavení v registru.

Každá služba Windows má záznam v registru pod **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services** podklíči. V podklíči každou službu, použijte **parametry** podklíč pro ukládání informací, které můžou přistupovat k vaší služby. Konfigurační soubory aplikace můžete použít pro službu Windows stejným způsobem jako u jiných typů aplikací. Ukázkový kód, naleznete v tématu <xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType>.

### <a name="to-add-startup-parameters"></a>Chcete-li přidat parametry spuštění

1. Vyberte **Program.cs**, nebo **MyNewService.Designer.vb**, klikněte na tlačítko **zobrazit kód** z místní nabídky. V `Main` metodu, změňte kód pro přidání vstupního parametru a předejte jej do konstruktoru služby:

   [!code-csharp[VbRadconService](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/Program-add-parameter.cs?highlight=1,6)]
   [!code-vb[VbRadconService](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.Designer-add-parameter.vb?highlight=1-2)]

2. V **MyNewService.cs**, nebo **MyNewService.vb**, změnit `MyNewService` konstruktor zpracovat vstupní parametr následujícím způsobem:

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

   Tento kód nastaví název zdroje a protokol událostí podle spouštěcí parametry, které uživatel zadává. Pokud nejsou dodány žádné argumenty, použije výchozí hodnoty.

3. Chcete-li zadat argumenty příkazového řádku, přidejte následující kód, který `ProjectInstaller` třídy v **ProjectInstaller.cs**, nebo **ProjectInstaller.vb**:

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

   Tato hodnota se obvykle obsahuje úplnou cestu ke spustitelnému souboru pro službu Windows. Služba správně je nutné zadat znaky uvozovek pro cestu a jednotlivé jednotlivé parametry. Uživatel může změnit na parametry **ImagePath** záznam v registru můžete změnit parametry spuštění pro službu Windows. Je však lepší způsob, a změňte hodnotu prostřednictvím kódu programu zpřístupnění funkce a uživatelsky přívětivé, například pomocí nástroje pro správu nebo konfigurace.

## <a name="build-the-service"></a>Vytvoření služby

1. V **Průzkumníka řešení**, zvolte **vlastnosti** z místní nabídky pro **MyNewService** projektu.

   Stránky vlastností pro váš projekt se zobrazí.

2. Na **aplikace** kartě **spouštěcí objekt** klikněte na položku **MyNewService.Program**, nebo **Sub Main** pro projekty jazyka Visual Basic.

3. Sestavte projekt, v **Průzkumníka řešení**, zvolte **sestavení** z místní nabídky projektu (nebo stiskněte klávesu **Ctrl**+**Shift** + **B**).

## <a name="install-the-service"></a>Instalace služby

Teď, když jste vytvořili službu Windows, můžete ho nainstalovat. Pro instalaci služby Windows, musíte mít pověření správce na počítači, kde je nainstalován.

1. Otevřít [Developer Command Prompt pro sadu Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs) s přihlašovacími údaji správce. Z Windows **Start** nabídce vyberte možnost **Developer Command Prompt for VS 2017** ve složce aplikace Visual Studio vyberte **Další** > **spustit jako Správce** z místní nabídky.

2. V **Developer Command Prompt pro sadu Visual Studio** okno, přejděte do složky, který obsahuje výstup projektu (ve výchozím nastavení, *\bin\Debug* podadresáře projektu).

3. Zadejte následující příkaz:

    ```shell
    installutil MyNewService.exe
    ```

    Pokud je služba nainstalována úspěšně, příkaz oznámí úspěšné dokončení. 

    Pokud systém nemůže najít *installutil.exe*, ujistěte se, že existuje ve vašem počítači. Tento nástroj je nainstalován pomocí rozhraní .NET Framework do složky *% windir%\Microsoft.NET\Framework[64]\\&lt;verzi rozhraní framework&gt;*. Například výchozí cesta pro 64bitovou verzi je *%windir%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.

    Pokud **installutil.exe** proces selže, najdete v protokolu instalace a zjistěte, proč. Ve výchozím nastavení v protokolu je ve stejné složce jako spustitelný soubor služby. Instalace může selhat, pokud: 
    - <xref:System.ComponentModel.RunInstallerAttribute> Třída není k dispozici na `ProjectInstaller` třídy.
    -  Atribut není nastavená na `true`. 
    - `ProjectInstaller` Třída není definován jako `public`.

Další informace najdete v tématu [jak: Instalace a odinstalace služeb](how-to-install-and-uninstall-services.md).

## <a name="start-and-run-the-service"></a>Spuštění a spuštění služby

1. Ve Windows, otevřete **služby** aplikace klasické pracovní plochy. Stisknutím klávesy **Windows**+**R** otevřít **spustit** zadejte *services.msc*a potom stiskněte klávesu **Enter** nebo vyberte **OK**.

     Měli byste vidět vaše služba uvedená v **služby**, zobrazené abecedně podle zobrazovaného názvu, kterou jste nastavili pro něj.

     ![MyNewService v okně služby.](media/windowsservices-serviceswindow.PNG)

2. Chcete-li spustit službu, zvolte **Start** z místní nabídky služby.

3. Chcete-li zastavit službu, zvolte **Zastavit** z místní nabídky služby.

4. (Volitelné) Z příkazového řádku, použijte příkazy **net start &lt;název služby&gt;**  a **net stop &lt;název služby&gt;**  spuštění a zastavení služby.

### <a name="verify-the-event-log-output-of-your-service"></a>Ověření výstupu služby v protokolu událostí

1. Ve Windows, otevřete **Prohlížeč událostí** aplikace klasické pracovní plochy. Zadejte *Prohlížeč událostí* ve službě Windows search panelu a pak vyberte **Prohlížeč událostí** ve výsledcích hledání.

   > [!TIP]
   > V sadě Visual Studio, dostanete protokoly událostí tak, že otevřete **Průzkumníka serveru** z **zobrazení** nabídce (nebo stiskněte klávesu **Ctrl**+**Alt** + **S**) rozšiřuje i **protokoly událostí** uzel v místním počítači.

2. V **Prohlížeč událostí**, rozbalte **protokoly aplikací a služeb**.

3. Vyhledejte výpis pro **MyNewLog** (nebo **MyLogFile1** Pokud jste postupovali podle postupu pro přidání argumentů příkazového řádku) a rozbalte ho. Měli byste vidět položky pro dvě akce (spouštění a zastavování), které provádí vaší služby.

     ![Pomocí prohlížeče událostí zobrazíte položky protokolu událostí](media/windows-service-event-viewer.png)

## <a name="clean-up-resources"></a>Vyčištění prostředků

Pokud už nepotřebujete Windows service app, můžete ho odebrat. 

1. Otevřít **Developer Command Prompt pro sadu Visual Studio** s přihlašovacími údaji správce.

2. V **Developer Command Prompt pro sadu Visual Studio** okno, přejděte do složky, který obsahuje výstup projektu.

3. Zadejte následující příkaz:

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   Pokud služba úspěšně odinstalována, příkaz hlásí, že vaše služba byla úspěšně odebrána. Další informace najdete v tématu [jak: Instalace a odinstalace služeb](how-to-install-and-uninstall-services.md).

## <a name="next-steps"></a>Další kroky

Teď, když jste vytvořili službu, můžete:

- Vytvořte samostatný instalační program ostatním uživatelům pro instalaci služby Windows. Použití [sadu nástrojů WiX Toolset](http://wixtoolset.org/) vytvořit instalační službu pro službu Windows. Další příklady naleznete v tématu [vytvoření instalačního balíčku](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).

- Prozkoumejte <xref:System.ServiceProcess.ServiceController> komponenta, která vám umožní odesílat příkazy do služby, které jste nainstalovali.

- Namísto vytvoření protokolu událostí při spuštění aplikace, použijte instalační program k vytvoření protokolu událostí při instalaci aplikace. Když odinstalujete aplikaci je protokol událostí odstraní instalační služby. Další informace naleznete v tématu <xref:System.Diagnostics.EventLogInstaller>.

## <a name="see-also"></a>Viz také:

- [Aplikace služby Windows](index.md)
- [Úvod do aplikace služby Windows](introduction-to-windows-service-applications.md)
- [Postupy: Ladění aplikace služby Windows](how-to-debug-windows-service-applications.md)
- [Služby (Windows)](/windows/desktop/Services/services)
