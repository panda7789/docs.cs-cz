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
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509850"
---
# <a name="walkthrough-creating-a-windows-service-application-in-the-component-designer"></a>Návod: Vytvoření aplikace spouštěné jako služba systému Windows v návrháři součástí
Tento článek ukazuje, jak vytvořit jednoduchou aplikaci Windows služby v sadě Visual Studio, která zapisuje zprávy do protokolu událostí. Tady jsou základní kroky, které provádějí vytváření a používání služby:  
  
1.  [Vytvoření služby](#BK_CreateProject) pomocí **Windows Service** šablony projektu a nakonfigurujte ho. Tato šablona vytvoří třídu dědící z <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> a velkou část základního kódu služby, jako je například kód ke spuštění služby.  
  
2.  [Přidání funkcí do služby](#BK_WriteCode) pro <xref:System.ServiceProcess.ServiceBase.OnStart%2A> a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> postupy a přepište všechny jiné metody, které chcete předefinovat.  
  
3.  [Nastavení služby stavu](#BK_SetStatus). Ve výchozím nastavení, služby vytvořené pomocí <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> implementovat pouze podmnožinu příznaků stavu k dispozici. Pokud vaše služba trvá dlouhou dobu spuštění, pozastavení nebo ukončení, můžete implementovat hodnoty stavu, jako je například čeká na spuštění nebo zastavení čeká na vyřízení k označení, že funguje u určité operace.  
  
4.  [Přidávání instalačních programů do služby](#BK_AddInstallers) pro aplikaci služby.  
  
5.  (Volitelné) [Nastavit parametry pro spuštění](#BK_StartupParameters), zadat výchozí argumenty pro spuštění a umožňují uživatelům přepsat výchozí nastavení při spuštění služby ručně.  
  
6.  [Vytváření služby](#BK_Build).  
  
7.  [Instalace služby](#BK_Install) v místním počítači.  
  
8.  Přístup ke správci řízení služeb Windows a [spuštění a spuštěná služba](#BK_StartService).  
  
9. [Odinstalace služby Windows](#BK_Uninstall).  
  
> [!WARNING]
>  Šablona projektu Služby systému Windows, která je zapotřebí pro tento návod, není k dispozici v edici Express sady Visual Studio.  
  
 [!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]  
  
<a name="BK_CreateProject"></a>   
## <a name="creating-a-service"></a>Vytvoření služby  
 Začněte tím, že vytvoříte projekt a nastavíte hodnoty, které jsou požadovány pro správné fungování služby.  
  
#### <a name="to-create-and-configure-your-service"></a>Vytvoření a konfigurace služby  
  
1.  V sadě Visual Studio v panelu nabídek zvolte **souboru**, **nový**, **projektu**.  
  
     **Nový projekt** zobrazí se dialogové okno.  
  
2.  V seznamu šablon projektů jazyka Visual Basic nebo Visual C#, zvolte **Windows Service**a název projektu **MyNewService**. Zvolte **OK**.  
  
     Šablona projektu automaticky přidá komponentní třídu s názvem `Service1` , která dědí z <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.  
  
3.  Na **upravit** nabídce zvolte **najít a nahradit**, **najít v souborech** (klávesnice: Ctrl + Shift + F). Změňte všechny výskyty `Service1` k `MyNewService`. Instance najdete v Service1.cs, Program.cs a Service1.Designer.cs (nebo jejich ekvivalenty .vb).  
  
4.  V **vlastnosti** okně **Service1.cs [Design]** nebo **Service1.vb [Design]**, nastavte <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> a **(název)** Vlastnost `Service1` k **MyNewService**, pokud ještě není nastavený.  
  
5.  V Průzkumníku řešení, přejmenujte **Service1.cs** k **MyNewService.cs**, nebo **Service1.vb** k **MyNewService.vb**.  
  
<a name="BK_WriteCode"></a>   
## <a name="adding-features-to-the-service"></a>Přidání funkcí do služby  
 V této části přidáte do služby Windows vlastního protokolu událostí. Protokoly událostí nejsou nijak spojené se službami systému Windows. Tady <xref:System.Diagnostics.EventLog> komponenty slouží jako příklad typ součásti, můžete přidat do služby Windows.  
  
#### <a name="to-add-custom-event-log-functionality-to-your-service"></a>Přidání funkce vlastního protokolu událostí do služby  
  
1.  V **Průzkumníka řešení**, otevřete kontextovou nabídku pro **MyNewService.cs** nebo **MyNewService.vb**a klikněte na tlačítko **Návrhář zobrazení**.  
  
2.  Z **součásti** část **nástrojů**, přetáhněte <xref:System.Diagnostics.EventLog> komponentu do návrháře.  
  
3.  V **Průzkumníka řešení**, otevřete kontextovou nabídku pro **MyNewService.cs** nebo **MyNewService.vb**a klikněte na tlačítko **zobrazit kód**.  
  
4.  Přidat deklaraci **protokolu událostí** objekt `MyNewService` třídy hned po řádek, který deklaruje `components` proměnné:  
  
     [!code-csharp[VbRadconService#16](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#16)]
     [!code-vb[VbRadconService#16](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#16)]  
  
5.  Přidejte nebo upravte konstruktor pro definování vlastního protokolu událostí:  
  
     [!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#2)]
     [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]  
  
#### <a name="to-define-what-occurs-when-the-service-starts"></a>Definování toho, co se stane při spuštění služby  
  
-   V editoru kódu vyhledejte <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodu, která byla automaticky přepsána při vytvoření projektu a nahraďte kód následujícím kódem. To přidá položku do protokolu událostí při spuštění služby:  
  
     [!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
     [!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]  
  
     Aplikace služby byla navržena jako dlouhotrvající, takže obvykle dotazuje nebo něco monitoruje v systému. Monitorování je nastavení <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody. Ale <xref:System.ServiceProcess.ServiceBase.OnStart%2A> neumí skutečně monitorování. <xref:System.ServiceProcess.ServiceBase.OnStart%2A> Metoda musí vracet v operačním systému po operaci služby. Nesmí spustit nekonečnou smyčku ani blokovat. Pokud chcete nastavit jednoduchý mechanismus dotazování, můžete použít <xref:System.Timers.Timer?displayProperty=nameWithType> komponenty následujícím způsobem: V <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodu, nastavení parametrů na komponentu a potom nastavte <xref:System.Timers.Timer.Enabled%2A> vlastnost `true`. Časovač vyvolává události ve vašem kódu pravidelně, po kterém může služba provádět monitorování. K tomu můžete použít následující kód:  
  
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
     Přidání členské proměnné třídy. Bude obsahovat identifikátor další události pro zápis do protokolu událostí.

    ```csharp
    private int eventId = 1;
    ```

    ```vb
    Private eventId As Integer = 1
    ```

     Přidejte kód pro zpracování události časovače:  
  
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
  
     Můžete chtít provádět úlohy pomocí pracovních vláken na pozadí místo spouštění veškerou práci na hlavním vlákně. Příkladem, najdete v článku <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> referenční stránce.  
  
#### <a name="to-define-what-occurs-when-the-service-is-stopped"></a>Definování toho, co se stane při zastavení služby  
  
-   Nahraďte kód <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metoda následujícím kódem. To přidá položku do protokolu událostí po zastavení služby:  
  
     [!code-csharp[VbRadconService#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#4)]
     [!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]  
  
 V další části, můžete přepsat <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, a <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> metody definovat další zpracování pro komponentu.  
  
#### <a name="to-define-other-actions-for-the-service"></a>Definování dalších akcí služby  
  
-   Vyhledejte metodu, kterou chcete zpracovat a přepsat definovat, co má vykonávat.  
  
     Následující kód ukazuje, jak je možné přepsat <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> metody:  
  
     [!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
     [!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]  
  
 Některé vlastní akce musejí nastat při instalaci služby Windows podle <xref:System.Configuration.Install.Installer> třídy. Sada Visual Studio může vytvořit tyto instalační programy speciálně pro službu systému Windows a přidat je do projektu.  
  
<a name="BK_SetStatus"></a>   
## <a name="setting-service-status"></a>Nastavení služby stavu  
 Služby oznamují svůj stav tak, aby uživatelé můžete říct, jestli služba správně funguje ke správci řízení služeb. Ve výchozím nastavení, služby, které dědí <xref:System.ServiceProcess.ServiceBase> omezenou sadu nastavení, stav, včetně zastaven, pozastaven a spouštění sestav. Pokud služba trvá o něco se spustí ho může být užitečné oznámit spuštění čeká na stav. Nastavení stavu čeká na spuštění a zastavení probíhající můžete také implementovat přidáním kódu, která volá Windows [SetServiceStatus funkce](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus).  
  
#### <a name="to-implement-service-pending-status"></a>K implementaci služby čekajícím stavu  
  
1.  Přidat `using` příkazu nebo `Imports` prohlášení <xref:System.Runtime.InteropServices?displayProperty=nameWithType> obor názvů v souboru MyNewService.cs nebo MyNewService.vb:  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    ```  
  
    ```vb  
    Imports System.Runtime.InteropServices  
    ```  
  
2.  Přidejte následující kód k MyNewService.cs pro deklaraci `ServiceState` hodnoty a přidat strukturu pro stav, který budete používat ve volání funkce invoke:  
  
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
  
3.  Teď v `MyNewService` třídy, deklarujte [SetServiceStatus funkce](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) pomocí platformy vyvolání:  
  
    ```csharp  
    [DllImport("advapi32.dll", SetLastError=true)]  
            private static extern bool SetServiceStatus(IntPtr handle, ref ServiceStatus serviceStatus);  
    ```  
  
    ```vb  
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean  
    ```  
  
4.  K implementaci spuštění čeká na stav, přidejte následující kód do začátku <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody:  
  
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
  
5.  Přidejte kód pro spuštění na konci nastavit stav <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody.  
  
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
  
6.  (Volitelné) Tento postup zopakujte pro <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody.  
  
> [!CAUTION]
>  [Správce řízení služeb](/windows/desktop/Services/service-control-manager) používá `dwWaitHint` a `dwCheckpoint` členy [SERVICE_STATUS struktura](/windows/desktop/api/winsvc/ns-winsvc-_service_status) k určení doby čekání na službu Windows ke spuštění nebo vypnutí. Pokud vaše <xref:System.ServiceProcess.ServiceBase.OnStart%2A> a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody se spustí, long, vaše služba může požádat o víc času voláním [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) znovu se zvýšena `dwCheckPoint` hodnotu.  
  
<a name="BK_AddInstallers"></a>   
## <a name="adding-installers-to-the-service"></a>Přidávání instalačních programů do služby  
 Před spuštěním služby Windows, musíte nainstalovat, které je zaregistruje ho s správce řízení služeb. Přidání instalačních programů do projektu, který zpracovat podrobnosti registrace.  
  
#### <a name="to-create-the-installers-for-your-service"></a>Vytvoření instalačních programů pro vaši službu  
  
1.  V **Průzkumníka řešení**, otevřete kontextovou nabídku pro **MyNewService.cs** nebo **MyNewService.vb**a klikněte na tlačítko **Návrhář zobrazení**.  
  
2.  Kliknutím na pozadí návrháře vyberte samotnou službu namísto některé z jejích komponent.  
  
3.  Otevřete místní nabídku pro okna návrháře (Pokud používáte polohovací zařízení, klikněte pravým tlačítkem uvnitř okna) a klikněte na tlačítko **přidat instalační program**.  
  
     Ve výchozím nastavení bude do projektu přidána komponentní třída, která obsahuje dva instalační programy. Komponenta má název **ProjectInstaller**a obsahuje instalační program pro vaši službu a instalační program služby přidruženého k tomuto procesu.  
  
4.  V **návrhu** zobrazit **ProjectInstaller**, zvolte **serviceInstaller1** pro projekt jazyka Visual C#, nebo **ServiceInstaller1** vizuálu Základní projekt.  
  
5.  V **vlastnosti** okno, ujistěte se, že <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> je nastavena na **MyNewService**.  
  
6.  Nastavte **popis** vlastnost nějaký text, například "Ukázková služba". Tento text se zobrazí v okně služby a pomáhá uživatelům identifikaci služby a pochopit, co se používá.  
  
7.  Nastavte <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> vlastnost text, který se má zobrazit v okně služby **název** sloupec. Můžete například zadat "MyNewService zobrazované jméno". Tento název se může lišit od <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> vlastnost, která je název použitý v systému (třeba když použijete `net start` příkaz pro spuštění služby).  
  
8.  Nastavte <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnost <xref:System.ServiceProcess.ServiceStartMode.Automatic>.  
  
     ![Vlastnosti Instalační služby systému Windows služby](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")  
  
9. V návrháři, zvolte **serviceProcessInstaller1** pro projekt jazyka Visual C#, nebo **ServiceProcessInstaller1** pro projekt jazyka Visual Basic. Nastavte <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> vlastnost <xref:System.ServiceProcess.ServiceAccount.LocalSystem>. To způsobí, že bude služba nainstalována a spuštěna s použitím účtu místní služby.  
  
    > [!IMPORTANT]
    >  <xref:System.ServiceProcess.ServiceAccount.LocalSystem> Účet má širší oprávnění, včetně možnosti zapisovat do protokolu událostí. Používejte tento účet opatrně, protože může zvýšit riziko napadení škodlivým softwarem. Pro jiné úlohy zvažte použití <xref:System.ServiceProcess.ServiceAccount.LocalService> účet, který funguje jako neprivilegované uživatele v místním počítači a nabízí pověření anonymního a jakémukoli vzdálenému serveru. V tomto příkladu se nezdaří, pokud se pokusíte použít <xref:System.ServiceProcess.ServiceAccount.LocalService> účtu, proto, že potřebuje oprávnění k zápisu do protokolu událostí.  
  
     Další informace o instalačních programů najdete v tématu [postupy: Přidání instalačních programů do aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
<a name="BK_StartupParameters"></a>   
## <a name="set-startup-parameters"></a>Nastavit parametry pro spuštění  
 Služba Windows, stejně jako jakéhokoliv jiného spustitelného souboru, může přijmout argumenty příkazového řádku, nebo parametry spuštění. Když přidáte kód do parametrů spuštění procesu, uživatelé mohou spustit služby s vlastní vlastní spouštěcí parametry pomocí okna služby v Ovládacích panelech Windows. Tyto spouštěcí parametry nejsou však zachované při příštím spuštění služby. Pokud chcete nastavit spouštěcí parametry trvale, můžete nastavit je v registru, jak je znázorněno v tomto postupu.  
  
> [!NOTE]
>  Předtím, než se rozhodnete přidat parametry spuštění, zvažte, jestli, která je nejlepší způsob, jak předávání informací do vaší služby. I když parametry spuštění jsou snadno použitelné a pro analýzy a uživatelé snadno je můžete přepsat, mohou být obtížnější uživatelům objevit a používat bez dokumentaci. Obecně platí Pokud vaše služba vyžaduje více než několik parametrů spuštění, měli byste zvážit použití registru nebo konfiguračního souboru místo toho. Každá služba Windows má záznam v registru pod HKLM\System\CurrentControlSet\services. V klíči služby, můžete použít **parametry** podklíč pro ukládání informací, které můžou přistupovat k vaší služby. Konfigurační soubory aplikace můžete použít pro službu Windows stejným způsobem jako u jiných typů aplikací. Příklad kódu naleznete v tématu <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.  
  
#### <a name="adding-startup-parameters"></a>Přidání parametrů spuštění  
  
1.  V `Main` metodu v souboru Program.cs nebo MyNewService.Designer.vb, přidejte argument příkazového řádku:  
  
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
  
2.  Změnit `MyNewService` konstruktor následujícím způsobem:  
  
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
  
<a name="BK_Build"></a>   
## <a name="building-the-service"></a>Vytvoření služby  
  
#### <a name="to-build-your-service-project"></a>Sestavení projektu služby  
  
1.  V **Průzkumníka řešení**, otevřete kontextovou nabídku pro váš projekt a klikněte na tlačítko **vlastnosti**. Stránky vlastností pro váš projekt se zobrazí.  
  
2.  Na kartě aplikace v **spouštěcí objekt** klikněte na položku **MyNewService.Program**.  
  
3.  V **Průzkumníka řešení**, otevřete kontextovou nabídku pro váš projekt a klikněte na tlačítko **sestavení** a sestavte projekt (klávesnice: Ctrl + Shift + B).  
  
<a name="BK_Install"></a>   
## <a name="installing-the-service"></a>Instalace služby  
 Teď, když jste vytvořili službu Windows, můžete ho nainstalovat. Instalace služby Windows, musí mít pověření správce na počítači, na kterém instalujete ho.  
  
#### <a name="to-install-a-windows-service"></a>Chcete-li nainstalovat službu Windows  
  
1.  Ve Windows 7 a Windows serveru, otevřete **Developer Command Prompt** pod **Visual Studio Tools** v **Start** nabídky. V systému Windows 8 nebo Windows 8.1, zvolte **Visual Studio Tools** na dlaždici **Start** obrazovky a pak spusťte příkazový řádek pro vývojáře s přihlašovacími údaji správce. (Pokud používáte myš, klikněte pravým tlačítkem na **Developer Command Prompt**a klikněte na tlačítko **spustit jako správce**.)  
  
2.  V okně příkazového řádku přejděte do složky, který obsahuje výstup projektu. Například v rámci složky Dokumenty přejděte do složky Visual Studio 2013\Projects\MyNewService\bin\Debug.  
  
3.  Zadejte následující příkaz:  
  
    ```  
    installutil.exe MyNewService.exe  
    ```  
  
     Pokud je služba nainstalována úspěšně, oznámí program installutil.exe úspěch. Pokud systém nemůže najít InstallUtil.exe, ujistěte se, zda existuje ve vašem počítači. Tento nástroj je nainstalován pomocí rozhraní .NET Framework do složky `%WINDIR%\Microsoft.NET\Framework[64]\` *framework_version*. Například výchozí cesta pro 32bitové verze rozhraní .NET Framework 4, 4.5, 4.5.1 a 4.5.2 je `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`.  
  
     Pokud proces installutil.exe oznámí selhání, naleznete v protokolu instalace a zjistěte, proč. Ve výchozím nastavení protokolu je ve stejné složce jako spustitelný soubor služby. Instalace může selhat, pokud <xref:System.ComponentModel.RunInstallerAttribute> třída není k dispozici na `ProjectInstaller` třídy, jinak atribut není nastaven na `true`, jinak `ProjectInstaller` třída není `public`.  
  
     Další informace najdete v tématu [postupy: instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
<a name="BK_StartService"></a>   
## <a name="starting-and-running-the-service"></a>Spuštění a spuštěná služba  
  
#### <a name="to-start-and-stop-your-service"></a>Spuštění a zastavení služby  
  
1.  Ve Windows, otevřete **Start** obrazovky nebo **Start** nabídce a zadejte `services.msc`.  
  
     Teď byste měli vidět **MyNewService** uvedené v **služby** okna.  
  
     ![MyNewService v okně služby. ](../../../docs/framework/windows-services/media/windowsservices-serviceswindow.PNG "WindowsServices_ServicesWindow")  
  
2.  V **služby** okno, otevřete místní nabídku pro vaši službu a pak zvolte **Start**.  
  
3.  Otevřete místní nabídku pro službu a klikněte na tlačítko **Zastavit**.  
  
4.  (Volitelné) Z příkazového řádku, můžete použít příkazy `net start``ServiceName` a `net stop``ServiceName` spuštění a zastavení služby.  
  
#### <a name="to-verify-the-event-log-output-of-your-service"></a>Ověření výstupu služby v protokolu událostí  
  
1.  V sadě Visual Studio, otevřete **Průzkumníka serveru** (klávesnice: Ctrl + Alt + S) a získat přístup **protokoly událostí** uzel v místním počítači.  
  
2.  Vyhledejte výpis pro **MyNewLog** (nebo **MyLogFile1**, pokud jste použili volitelný postup k přidání argumentů příkazového řádku) a rozbalte ho. Měli byste vidět položky pro dvě akce (spouštění a zastavování) vaše služba provedla.  
  
     ![Pomocí prohlížeče událostí zobrazíte položky protokolu událostí. ](../../../docs/framework/windows-services/media/windowsservices-eventviewer.PNG "WindowsServices_EventViewer")  
  
<a name="BK_Uninstall"></a>   
## <a name="uninstalling-a-windows-service"></a>Odinstalace služby Windows  
  
#### <a name="to-uninstall-your-service"></a>Odinstalace služby  
  
1.  Otevřete příkazový řádek pro vývojáře s přihlašovacími údaji správce.  
  
2.  V okně příkazového řádku přejděte do složky, který obsahuje výstup projektu. Například v rámci složky Dokumenty přejděte do složky Visual Studio 2013\Projects\MyNewService\bin\Debug.  
  
3.  Zadejte následující příkaz:  
  
    ```  
    installutil.exe /u MyNewService.exe  
    ```  
  
     Pokud je služba úspěšně odinstalována, program installutil.exe oznámí, že byla služba úspěšně odebrána. Další informace najdete v tématu [postupy: instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
## <a name="next-steps"></a>Další kroky  
 Můžete vytvořit samostatný instalační program, který ostatní mohli používat k instalaci služby Windows, ale vyžaduje další kroky. Technologie ClickOnce nepodporuje služby systému Windows, a proto nelze použít Průvodce publikováním. Můžete použít plnou edici nástroje InstallShield, kterou ale společnost Microsoft neposkytuje. Další informace o nástroji InstallShield naleznete v tématu [InstallShield Limited Edition](/visualstudio/deployment/installshield-limited-edition). Můžete také použít [sady nástrojů XML Instalační služby systému Windows](https://go.microsoft.com/fwlink/?LinkId=249067) vytvořit instalační službu pro službu Windows.  
  
 Použití může zkoumat <xref:System.ServiceProcess.ServiceController> součásti, která vám umožní odesílat příkazy do služby, které jste nainstalovali.  
  
 Pomocí instalačního programu můžete vytvořit protokol událostí při instalaci aplikace namísto vytvoření protokolu událostí po spuštění aplikace. Při odinstalaci aplikace navíc instalační program protokol událostí odstraní. Další informace najdete v tématu <xref:System.Diagnostics.EventLogInstaller> referenční stránce.  
  
## <a name="see-also"></a>Viz také  
 [Aplikace služby systému Windows](../../../docs/framework/windows-services/index.md)  
 [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Postupy: Ladění aplikací služby systému Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [Služby (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms685141.aspx)
