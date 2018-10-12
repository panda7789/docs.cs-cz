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
ms.openlocfilehash: 79447ede354de104607117f657182023a2e57127
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123667"
---
# <a name="walkthrough-create-a-windows-service-app"></a>Návod: Vytvoření aplikace služby Windows

Tento článek ukazuje, jak vytvořit jednoduchou aplikaci služby Windows v sadě Visual Studio, která zapisuje zprávy do protokolu událostí.

## <a name="create-a-service"></a>Vytvoření služby

Pokud chcete začít, vytvořte projekt a nastavte hodnoty, které jsou požadovány pro správné fungování služby.

1. V sadě Visual Studio v panelu nabídek zvolte **souboru** > **nový** > **projektu** (nebo stiskněte klávesu **Ctrl** + **Shift**+**N**) Chcete-li otevřít **nový projekt** dialogového okna.

2. Vyhledejte a vyberte **Windows Service** šablony projektu. Rozbalte **nainstalováno** > [**Visual C#** nebo **jazyka Visual Basic**] > **Windows Desktop**, nebo typ **Windows Service** do vyhledávacího pole v pravém horním rohu.

   ![Šablona služby Windows v dialogu Nový projekt v sadě Visual Studio](media/new-project-dialog.png)

   > [!NOTE]
   > Pokud se nezobrazí **Windows Service** šablony, je nutné nainstalovat **vývoj desktopových aplikací .NET** pracovního vytížení. V **nový projekt** dialogového okna, klikněte na odkaz, který říká **otevřít instalační program Visual Studio** v levé dolní části. V **instalační program sady Visual Studio**, vyberte **vývoj desktopových aplikací .NET** úloh a klikněte na tlačítko **změnit**.

3. Pojmenujte projekt **MyNewService**a klikněte na tlačítko **OK**.

   Šablona projektu zahrnuje komponentní třídu s názvem `Service1` , která dědí z <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>. Obsahuje velkou část základního kódu služby, jako je například kód ke spuštění služby.

## <a name="rename-the-service"></a>Přejmenování služby

Přejmenování služby z **Service1** k **MyNewService**.

1. V **návrhu** zobrazení Service1.cs (nebo Service1.vb), klikněte na odkaz pro **přepněte do zobrazení kódu**. Klikněte pravým tlačítkem na **Service1** a vyberte **přejmenovat** v místní nabídce. Zadejte **MyNewService** a potom stiskněte klávesu **Enter** nebo klikněte na tlačítko **použít**.

2. V **vlastnosti** okně **Service1.cs [Design]** nebo **Service1.vb [Design]**, změnit **ServiceName** hodnota, která má **MyNewService**.

3. V **Průzkumníka řešení**, přejmenujte **Service1.cs** k **MyNewService.cs**, nebo přejmenujte **Service1.vb** k  **MyNewService.vb**.

## <a name="add-features-to-the-service"></a>Přidání funkcí do služby

V této části přidáte do služby Windows vlastního protokolu událostí. Protokoly událostí nejsou nijak spojené se službami systému Windows. <xref:System.Diagnostics.EventLog> Součást slouží jako příklad typ součásti, můžete přidat do služby Windows.

### <a name="add-custom-event-log-functionality"></a>Přidání funkce vlastního protokolu událostí

1. V **Průzkumníka řešení**, otevřete kontextovou nabídku pro **MyNewService.cs** nebo **MyNewService.vb**a klikněte na tlačítko **Návrhář zobrazení**.

2. Z **součásti** část **nástrojů**, přetáhněte <xref:System.Diagnostics.EventLog> komponentu do návrháře.

3. V **Průzkumníka řešení**, otevřete kontextovou nabídku pro **MyNewService.cs** nebo **MyNewService.vb**a klikněte na tlačítko **zobrazit kód**.

4. Upravte konstruktor pro definování vlastního protokolu událostí:

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

### <a name="define-what-occurs-when-the-service-starts"></a>Definujte, co se stane při spuštění služby

V editoru kódu vyhledejte <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodu, která byla automaticky přepsána při vytvoření projektu. Přidáte řádek kódu, který zapíše položku do protokolu událostí při spuštění služby:

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

Aplikace služby byla navržena jako dlouhotrvající, takže obvykle dotazuje nebo něco monitoruje v systému. Monitorování je nastavení <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody. Ale <xref:System.ServiceProcess.ServiceBase.OnStart%2A> neumí skutečně monitorování. <xref:System.ServiceProcess.ServiceBase.OnStart%2A> Metoda musí vracet v operačním systému po operaci služby. Nesmí spustit nekonečnou smyčku ani blokovat. Pokud chcete nastavit jednoduchý mechanismus dotazování, můžete použít <xref:System.Timers.Timer?displayProperty=nameWithType> komponenty následujícím způsobem: V <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodu, nastavení parametrů na komponentu a potom nastavte <xref:System.Timers.Timer.Enabled%2A> vlastnost `true`. Časovač vyvolává události ve vašem kódu pravidelně, po kterém může služba provádět monitorování. K tomu můžete použít následující kód:

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

Přidání členské proměnné třídy. Obsahuje identifikátor další události pro zápis do protokolu událostí.

```csharp
private int eventId = 1;
```

```vb
Private eventId As Integer = 1
```

Přidáte nové metody pro zpracování události časovače:

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

Můžete chtít provádět úlohy pomocí pracovních vláken na pozadí místo spouštění veškerou práci na hlavním vlákně. Další informace naleznete v tématu <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.

### <a name="define-what-occurs-when-the-service-is-stopped"></a>Definujte, co se stane při zastavení služby

Přidat řádek kódu, který <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metodu, která přidá položku do protokolu událostí po zastavení služby:

```csharp
eventLog1.WriteEntry("In OnStop.");
```

[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a>Definování dalších akcí služby

Je možné přepsat <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, a <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> metody definovat další zpracování pro komponentu. Následující kód ukazuje, jak je možné přepsat <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> metody:

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]

Některé vlastní akce musejí nastat při instalaci služby Windows podle <xref:System.Configuration.Install.Installer> třídy. Sada Visual Studio může vytvořit tyto instalační programy speciálně pro službu systému Windows a přidat je do projektu.

## <a name="set-service-status"></a>Nastavit stav služby

Služby oznamují svůj stav tak, aby uživatelé můžete říct, jestli služba správně funguje ke správci řízení služeb. Ve výchozím nastavení, služby, které dědí <xref:System.ServiceProcess.ServiceBase> omezenou sadu nastavení, stav, včetně zastaven, pozastaven a spouštění sestav. Pokud služba trvá o něco se spustí ho může být užitečné oznámit spuštění čeká na stav. Nastavení stavu čeká na spuštění a zastavení probíhající můžete také implementovat přidáním kódu, která volá Windows [SetServiceStatus funkce](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus).

K implementaci služby čekajícím stavu:

1. Přidat `using` příkaz nebo `Imports` deklarace <xref:System.Runtime.InteropServices?displayProperty=nameWithType> obor názvů v souboru MyNewService.cs nebo MyNewService.vb:

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. Přidejte následující kód k MyNewService.cs pro deklaraci `ServiceState` hodnoty a přidat strukturu pro stav, který budete používat ve volání funkce invoke:

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

3. Teď v `MyNewService` třídy, deklarujte [SetServiceStatus funkce](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) pomocí [vyvolání platformy](../interop/consuming-unmanaged-dll-functions.md):

    ```csharp
    [DllImport("advapi32.dll", SetLastError = true)]
    private static extern bool SetServiceStatus(System.IntPtr handle, ref ServiceStatus serviceStatus);
    ```

    ```vb
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean
    ```

4. K implementaci spuštění čeká na stav, přidejte následující kód do začátku <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody:

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

5. Přidejte kód pro spuštění na konci nastavit stav <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody.

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

6. (Volitelné) Tento postup zopakujte pro <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody.

> [!NOTE]
> [Správce řízení služeb](/windows/desktop/Services/service-control-manager) používá `dwWaitHint` a `dwCheckpoint` členy [SERVICE_STATUS struktura](/windows/desktop/api/winsvc/ns-winsvc-_service_status) k určení doby čekání na službu Windows ke spuštění nebo vypnutí. Pokud vaše <xref:System.ServiceProcess.ServiceBase.OnStart%2A> a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody se spustí, long, vaše služba může požádat o víc času voláním [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) znovu se zvýšena `dwCheckPoint` hodnotu.

## <a name="add-installers-to-the-service"></a>Přidání instalačních programů do služby

Před spuštěním služby Windows, musíte nainstalovat, které je zaregistruje ho s správce řízení služeb. Přidání instalačních programů do projektu, který zpracovat podrobnosti registrace.

1. V **Průzkumníka řešení**, otevřete kontextovou nabídku pro **MyNewService.cs** nebo **MyNewService.vb**a klikněte na tlačítko **Návrhář zobrazení**.

2. Kliknutím na pozadí návrháře vyberte samotnou službu namísto některé z jejích komponent.

3. Otevřete místní nabídku pro okna návrháře (Pokud používáte polohovací zařízení, klikněte pravým tlačítkem uvnitř okna) a klikněte na tlačítko **přidat instalační program**.

   Ve výchozím nastavení bude do projektu přidána komponentní třída, která obsahuje dva instalační programy. Komponenta má název **ProjectInstaller**a obsahuje instalační program pro vaši službu a instalační program služby přidruženého k tomuto procesu.

4. V **návrhu** zobrazit **ProjectInstaller**, zvolte **serviceInstaller1** pro projekt jazyka Visual C#, nebo **ServiceInstaller1** vizuálu Základní projekt.

5. V **vlastnosti** okno, ujistěte se, že <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> je nastavena na **MyNewService**.

6. Nastavte **popis** vlastnost nějaký text, například "Ukázková služba". Tento text se zobrazí v okně služby a pomáhá uživatelům identifikaci služby a pochopit, co se používá.

7. Nastavte <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> vlastnost text, který se má zobrazit v okně služby **název** sloupec. Můžete například zadat "MyNewService zobrazované jméno". Tento název se může lišit od <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> vlastnost, která je název použitý v systému (třeba když použijete `net start` příkaz pro spuštění služby).

8. Nastavte <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnost <xref:System.ServiceProcess.ServiceStartMode.Automatic>.

     ![Vlastnosti Instalační služby systému Windows služby](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")

9. V návrháři, zvolte **serviceProcessInstaller1** pro projekt jazyka Visual C#, nebo **ServiceProcessInstaller1** pro projekt jazyka Visual Basic. Nastavte <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> vlastnost <xref:System.ServiceProcess.ServiceAccount.LocalSystem>. To způsobí, že služba nainstalována a spuštěna s použitím místního systémového účtu.

    > [!IMPORTANT]
    > <xref:System.ServiceProcess.ServiceAccount.LocalSystem> Účet má širší oprávnění, včetně možnosti zapisovat do protokolu událostí. Používejte tento účet opatrně, protože může zvýšit riziko napadení škodlivým softwarem. Pro jiné úlohy zvažte použití <xref:System.ServiceProcess.ServiceAccount.LocalService> účet, který funguje jako neprivilegované uživatele v místním počítači a nabízí pověření anonymního a jakémukoli vzdálenému serveru. V tomto příkladu se nezdaří, pokud se pokusíte použít <xref:System.ServiceProcess.ServiceAccount.LocalService> účtu, proto, že potřebuje oprávnění k zápisu do protokolu událostí.

Další informace o instalačních programů najdete v tématu [postupy: Přidání instalačních programů do aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).

## <a name="optional-set-startup-parameters"></a>(Volitelné) Nastavit parametry spuštění

Služba Windows, stejně jako jakéhokoliv jiného spustitelného souboru, může přijmout argumenty příkazového řádku, nebo parametry spuštění. Když přidáte kód do parametrů spuštění procesu, uživatelé mohou spustit služby s vlastní vlastní spouštěcí parametry pomocí okna služby v Ovládacích panelech Windows. Tyto spouštěcí parametry nejsou však zachované při příštím spuštění služby. Pokud chcete nastavit spouštěcí parametry trvale, můžete nastavit je v registru, jak je znázorněno v tomto postupu.

> [!NOTE]
> Předtím, než se rozhodnete přidat parametry spuštění, zvažte, jestli, která je nejlepší způsob, jak předávání informací do vaší služby. I když parametry spuštění jsou snadno použitelné a pro analýzy a uživatelé snadno je můžete přepsat, mohou být obtížnější uživatelům objevit a používat bez dokumentaci. Obecně platí Pokud vaše služba vyžaduje více než několik parametrů spuštění, měli byste zvážit použití registru nebo konfiguračního souboru místo toho. Každá služba Windows má záznam v registru pod **HKLM\System\CurrentControlSet\services**. V klíči služby, můžete použít **parametry** podklíč pro ukládání informací, které můžou přistupovat k vaší služby. Konfigurační soubory aplikace můžete použít pro službu Windows stejným způsobem jako u jiných typů aplikací. Příklad kódu naleznete v tématu <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.

Chcete-li přidat parametry spuštění:

1. V `Main` metodu v souboru Program.cs nebo MyNewService.Designer.vb, přidejte vstupní parametr předat konstruktoru služby:

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

2. Změnit `MyNewService` konstruktor následujícím způsobem:

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

   Tento kód nastaví název zdroje a protokol událostí podle Zadaný spouštěcí parametry, nebo použije výchozí hodnoty, pokud nejsou dodány žádné argumenty.

3. Chcete-li zadat argumenty příkazového řádku, přidejte následující kód, který `ProjectInstaller` třídy v ProjectInstaller.cs nebo ProjectInstaller.vb:

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

   Tento kód změní **ImagePath** klíč registru, který obvykle obsahuje úplnou cestu ke spustitelnému souboru pro službu Windows tak, že přidáte výchozí hodnoty parametrů. Uvozovky kolem cestu (a po každé jednotlivé parametr) jsou požadovány pro službu spustit správně. Chcete-li změnit spouštěcí parametry pro tuto službu Windows, uživatelé mohou změnit parametrech daných **ImagePath** klíč registru, i když lepší je vytvoření a změna programu zpřístupnění funkcí pro uživatele v popisný způsobem (třeba správu nebo konfigurace nástroje).

## <a name="build-the-service"></a>Vytvoření služby

1. V **Průzkumníka řešení**, otevřete kontextovou nabídku pro váš projekt a klikněte na tlačítko **vlastnosti**.

   Stránky vlastností pro váš projekt se zobrazí.

2. Na **aplikace** kartě **spouštěcí objekt** klikněte na položku **MyNewService.Program**.

3. V **Průzkumníka řešení**, otevřete kontextovou nabídku pro váš projekt a klikněte na tlačítko **sestavení** k sestavení projektu (nebo stiskněte klávesu **Ctrl**+**Shift**  + **B**).

## <a name="install-the-service"></a>Instalace služby

Teď, když jste vytvořili službu Windows, můžete ho nainstalovat. Pro instalaci služby Windows, musíte mít pověření správce na počítači, na kterém instalujete ho.

1. Otevřít **Developer Command Prompt pro sadu Visual Studio** s přihlašovacími údaji správce. Pokud používáte myš, klikněte pravým tlačítkem na **Developer Command Prompt for VS 2017** nabídky Start v Windows a klikněte na tlačítko **Další** > **spustit jako správce** .

2. V **Developer Command Prompt** okno, přejděte do složky, který obsahuje výstup projektu (ve výchozím nastavení, je *\bin\Debug* podadresáře projektu).

3. Zadejte následující příkaz:

    ```shell
    installutil.exe MyNewService.exe
    ```

    Pokud je služba nainstalována úspěšně, **installutil.exe** oznámí úspěšné dokončení. Pokud systém nemůže najít **InstallUtil.exe**, ujistěte se, že existuje ve vašem počítači. Tento nástroj je nainstalován pomocí rozhraní .NET Framework do složky *% windir%\Microsoft.NET\Framework[64]\\[framework verze]*. Například výchozí cesta pro 32bitovou verzi je *%windir%\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.

    Pokud **installutil.exe** zpracovat selhání zpráv, najdete v protokolu instalace a zjistěte, proč. Ve výchozím nastavení protokolu je ve stejné složce jako spustitelný soubor služby. Instalace může selhat, pokud <xref:System.ComponentModel.RunInstallerAttribute> třída není k dispozici na `ProjectInstaller` třídy, pokud atribut není nastavená na **true**, nebo pokud `ProjectInstaller` třída není označena **veřejné**.

Další informace najdete v tématu [postupy: instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).

## <a name="start-and-run-the-service"></a>Spuštění a spuštění služby

1. Ve Windows, otevřete **služby** aplikace klasické pracovní plochy. Stisknutím klávesy **Windows**+**R** otevřít **spustit** a pak zadejte **services.msc** a stiskněte klávesu **Enter**  nebo klikněte na tlačítko **OK**.

     Měli byste vidět vaše služba uvedená v **služby**, zobrazené abecedně podle zobrazovaného názvu, kterou jste nastavili pro něj.

     ![MyNewService v okně služby.](../../../docs/framework/windows-services/media/windowsservices-serviceswindow.PNG)

2. V **služby**, otevřete místní nabídku pro vaši službu a pak zvolte **Start**.

3. K zastavení služby, otevřete místní nabídku pro službu a pak zvolte **Zastavit**.

4. (Volitelné) Z příkazového řádku, můžete použít příkazy `net start ServiceName` a `net stop ServiceName` spuštění a zastavení služby.

### <a name="verify-the-event-log-output-of-your-service"></a>Ověření výstupu služby v protokolu událostí

1. Otevřít **Prohlížeč událostí** spuštěním na typ **Prohlížeč událostí** do vyhledávacího pole na hlavním panelu Windows a pak vyberete **Prohlížeč událostí** ve výsledcích hledání.

   > [!TIP]
   > V sadě Visual Studio, dostanete protokoly událostí tak, že otevřete **Průzkumníka serveru** (klávesnice: **Ctrl**+**Alt**+**S**) rozšiřuje i **protokoly událostí** uzel v místním počítači.

2. V **Prohlížeč událostí**, rozbalte **protokoly aplikací a služeb**.

3. Vyhledejte výpis pro **MyNewLog** (nebo **MyLogFile1**, pokud jste postupovali podle volitelný postup pro přidání argumentů příkazového řádku) a rozbalte ho. Měli byste vidět položky pro dvě akce (spouštění a zastavování), které provádí vaší služby.

     ![Pomocí prohlížeče událostí zobrazíte položky protokolu událostí](../../../docs/framework/windows-services/media/windows-service-event-viewer.png)

## <a name="uninstall-the-service"></a>Odinstalujte službu

1. Otevřít **Developer Command Prompt pro sadu Visual Studio** s přihlašovacími údaji správce.

2. V okně příkazového řádku přejděte do složky, který obsahuje výstup projektu.

3. Zadejte následující příkaz:

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   Pokud služba úspěšně, odinstalována **installutil.exe** hlásí, že vaše služba byla úspěšně odebrána. Další informace najdete v tématu [postupy: instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).

## <a name="next-steps"></a>Další kroky

Teď, když jste vytvořili službu, můžete chtít vytvořit samostatný instalační program, který ostatní mohli používat k instalaci služby Windows. Technologie ClickOnce nepodporuje služby Windows, ale můžete použít [sadu nástrojů WiX Toolset](http://wixtoolset.org/) vytvořit instalační službu pro službu Windows. Další příklady naleznete v tématu [vytvoření instalačního balíčku](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).

Použití může zkoumat <xref:System.ServiceProcess.ServiceController> komponenta, která vám umožní odesílat příkazy do služby, které jste nainstalovali.

Pomocí instalačního programu můžete vytvořit protokol událostí při instalaci aplikace namísto vytvoření protokolu událostí po spuštění aplikace. Při odinstalaci aplikace navíc instalační program protokol událostí odstraní. Další informace najdete v tématu <xref:System.Diagnostics.EventLogInstaller> referenční stránce.

## <a name="see-also"></a>Viz také:

- [Aplikace služby Windows](../../../docs/framework/windows-services/index.md)
- [Úvod do aplikace služby Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [Postupy: ladění aplikace služby Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)
- [Služby (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms685141.aspx)
