---
title: "Návod: Vytvoření aplikace spouštěné jako služba systému Windows v návrháři součástí"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Service applications, walkthroughs
- Windows Service applications, creating
ms.assetid: e24d8a3d-edc6-485c-b6e0-5672d91fb607
caps.latest.revision: "57"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 42fc5f27f1c78e243ff1d3a705c61a20ff459937
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-windows-service-application-in-the-component-designer"></a>Návod: Vytvoření aplikace spouštěné jako služba systému Windows v návrháři součástí
Tento článek ukazuje, jak vytvořit jednoduchou aplikaci služby systému Windows v sadě Visual Studio, která zapisuje zprávy do protokolu událostí. Zde jsou základní kroky, které jste při vytváření a používání služby:  
  
1.  [Vytvoření služby](#BK_CreateProject) pomocí **služba systému Windows** projektu šablony a nakonfigurovat ho. Tato šablona vytvoří za vás, která dědí z třídy <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> a zapisuje většinu kódu základní služby, jako je například kód pro spuštění služby.  
  
2.  [Přidávání funkcí do služby](#BK_WriteCode) pro <xref:System.ServiceProcess.ServiceBase.OnStart%2A> a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> postupy a přepsat jiné metody, které chcete znovu definovat.  
  
3.  [Nastavení služby stavu](#BK_SetStatus). Ve výchozím nastavení vytvoří služby s <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> implementovat jenom podmnožinu příznaků stavu k dispozici. Pokud služby trvá dlouhou dobu spuštění, pozastavení nebo zastavit, můžete implementovat hodnoty stavu, jako je například čekající spustit nebo Zastavit čekající indikující, že funguje na operace.  
  
4.  [Přidávání instalačních programů do služby](#BK_AddInstallers) pro aplikaci služby.  
  
5.  (Volitelné) [Nastavit parametry spuštění](#BK_StartupParameters), zadejte výchozí argumenty spuštění a povolte uživatelům přepíší výchozí nastavení, když budou službu spustit ručně.  
  
6.  [Vytváření služby](#BK_Build).  
  
7.  [Nainstalovat službu](#BK_Install) v místním počítači.  
  
8.  Přístup správce řízení služeb systému Windows a [spuštění a spuštěna služba](#BK_StartService).  
  
9. [Odinstalace služby systému Windows](#BK_Uninstall).  
  
> [!WARNING]
>  Šablona projektu Služby systému Windows, která je zapotřebí pro tento návod, není k dispozici v edici Express sady Visual Studio.  
  
 [!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]  
  
<a name="BK_CreateProject"></a>   
## <a name="creating-a-service"></a>Vytvoření služby  
 Začněte tím, že vytvoříte projekt a nastavíte hodnoty, které jsou požadovány pro správné fungování služby.  
  
#### <a name="to-create-and-configure-your-service"></a>Vytvoření a konfigurace služby  
  
1.  V sadě Visual Studio na řádku nabídek zvolte **soubor**, **nový**, **projektu**.  
  
     **Nový projekt** otevře se dialogové okno.  
  
2.  V seznamu šablon projektu jazyka Visual Basic a Visual C#, zvolte **služba systému Windows**a název projektu **MyNewService**. Zvolte **OK**.  
  
     Šablona projektu automaticky přidá třídu součást s názvem `Service1` který dědí z <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.  
  
3.  Na **upravit** nabídce zvolte **najít a nahradit**, **hledání v souborech** (klávesové: Ctrl + Shift + F). Změňte všechny výskyty `Service1` k `MyNewService`. Instance najdete v Service1.cs, souboru Program.cs a Service1.Designer.cs (nebo jejich ekvivalenty VB).  
  
4.  V **vlastnosti** okna pro **Service1.cs [návrhu]** nebo **Service1.vb [návrhu]**, nastavte <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> a **(název)** Vlastnost pro `Service1` k **MyNewService**, pokud ještě není nastavena.  
  
5.  V Průzkumníku řešení, přejmenujte **Service1.cs** k **MyNewService.cs**, nebo **Service1.vb** k **MyNewService.vb**.  
  
<a name="BK_WriteCode"></a>   
## <a name="adding-features-to-the-service"></a>Přidání funkcí do služby  
 V této části přidáte vlastní protokol událostí pro službu systému Windows. Protokoly událostí nejsou nijak spojené se službami systému Windows. Zde <xref:System.Diagnostics.EventLog> součást slouží jako příklad typ součásti, které můžete přidat k službě systému Windows.  
  
#### <a name="to-add-custom-event-log-functionality-to-your-service"></a>Přidání funkce vlastního protokolu událostí do služby  
  
1.  V **Průzkumníku řešení**, otevřete kontextovou nabídku **MyNewService.cs** nebo **MyNewService.vb**a potom zvolte **Návrhář zobrazení**.  
  
2.  Z **součásti** části **sada nástrojů**, přetáhněte <xref:System.Diagnostics.EventLog> součásti do návrháře.  
  
3.  V **Průzkumníku řešení**, otevřete kontextovou nabídku **MyNewService.cs** nebo **MyNewService.vb**a potom zvolte **kód zobrazení**.  
  
4.  Přidejte deklaraci pro **protokolu událostí** objekt v `MyNewService` třída hned po řádek, který deklaruje `components` proměnné:  
  
     [!code-csharp[VbRadconService#16](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#16)]
     [!code-vb[VbRadconService#16](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#16)]  
  
5.  Přidat nebo upravit konstruktor k definovat vlastní protokol událostí:  
  
     [!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#2)]
     [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]  
  
#### <a name="to-define-what-occurs-when-the-service-starts"></a>Definování toho, co se stane při spuštění služby  
  
-   Vyhledejte v editoru kódu <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodu, která byla automaticky přepsat při vytváření projektu a nahraďte kód následujícím kódem. Tento postup přidá položku do protokolu událostí při spuštění služby:  
  
     [!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
     [!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]  
  
     Aplikace služby je navržený jako dlouhodobé, takže obvykle dotazuje nebo monitoruje něco v systému. Monitorování je nastavený <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda. Ale <xref:System.ServiceProcess.ServiceBase.OnStart%2A> neprovádí ve skutečnosti monitorování. <xref:System.ServiceProcess.ServiceBase.OnStart%2A> Metoda musí vrátit do operačního systému po zahájení operace služby. Nesmí spustit nekonečnou smyčku ani blokovat. Pokud chcete nastavit jednoduché dotazování mechanismus, můžete použít <xref:System.Timers.Timer?displayProperty=nameWithType> součást následujícím způsobem: V <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda nastavit parametry na komponentu a potom nastavte <xref:System.Timers.Timer.Enabled%2A> vlastnost `true`. Časovač vyvolává události ve vašem kódu pravidelně, po kterém služby udělat jeho monitorování. K tomu můžete použít následující kód:  
  
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
     Přidání členské proměnné na třídu. Bude obsahovat identifikátor další události, k zápisu do protokolu událostí.

    ```csharp
    private int eventId = 1;
    ```

    ```vb
    Private eventId As Integer = 1
    ```

     Přidáte kód pro zpracování událost časovače:  
  
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
  
     Můžete chtít provádět úlohy pomocí pracovní vlákna na pozadí namísto spuštění všechnu práci na hlavní vlákno. Příklady, najdete v článku <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> stránka s referencemi k.  
  
#### <a name="to-define-what-occurs-when-the-service-is-stopped"></a>Definování toho, co se stane při zastavení služby  
  
-   Nahraďte kód <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metoda následujícím kódem. Tento postup přidá položku do protokolu událostí po zastavení služby:  
  
     [!code-csharp[VbRadconService#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#4)]
     [!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]  
  
 V další části, můžete přepsat <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, a <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> metody můžete definovat další zpracování pro příslušné součásti.  
  
#### <a name="to-define-other-actions-for-the-service"></a>Definování dalších akcí služby  
  
-   Vyhledejte metodu, kterou chcete zpracovat a přepsat definovat, co chcete dojít.  
  
     Následující kód ukazuje, jak je možné přepsat <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> metoda:  
  
     [!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
     [!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]  
  
 Některé vlastní akce muset dojít, když je nainstalovaná služba systému Windows pomocí <xref:System.Configuration.Install.Installer> třídy. Sada Visual Studio může vytvořit tyto instalační programy speciálně pro službu systému Windows a přidat je do projektu.  
  
<a name="BK_SetStatus"></a>   
## <a name="setting-service-status"></a>Nastavení služby stavu  
 Sestavy služby Services jejich stav ke správci řízení služeb tak, aby uživatelé zjistíte, jestli služba funguje správně. Ve výchozím nastavení služby, které dědí od <xref:System.ServiceProcess.ServiceBase> omezenou sadu nastavení stavu, včetně zastavit, pozastavit a spouštění sestav. Pokud služba přijímá trochu při pro spuštění, se může být užitečné nahlásit stav spuštění čekání. Můžete taky implementovat nastavení stavu čekající spustit a zastavit čekající tak, že přidáte kód, který volá do systému Windows [SetServiceStatus funkce](http://msdn.microsoft.com/library/windows/desktop/ms686241.aspx).  
  
#### <a name="to-implement-service-pending-status"></a>K implementaci služby čekající na vyřízení stavu  
  
1.  Přidat `using` příkaz nebo `Imports` deklarace k <xref:System.Runtime.InteropServices?displayProperty=nameWithType> oboru názvů v souboru MyNewService.cs nebo MyNewService.vb:  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    ```  
  
    ```vb  
    Imports System.Runtime.InteropServices  
    ```  
  
2.  Přidejte následující kód do MyNewService.cs deklarovat `ServiceState` hodnoty a přidat do struktury na stav, který budete používat na platformě vyvolat volání:  
  
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
  
3.  Nyní v `MyNewService` třídy, deklarovat [SetServiceStatus funkce](http://msdn.microsoft.com/library/windows/desktop/ms686241.aspx) pomocí platformy vyvolání:  
  
    ```csharp  
    [DllImport("advapi32.dll", SetLastError=true)]  
            private static extern bool SetServiceStatus(IntPtr handle, ref ServiceStatus serviceStatus);  
    ```  
  
    ```vb  
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean  
    ```  
  
4.  K implementaci spuštění čeká na stav, přidejte následující kód do začátku <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda:  
  
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
  
5.  Přidejte kód pro nastavení stavu spuštěná na konci <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda.  
  
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
  
6.  (Volitelné) Tento postup zopakujte pro <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metoda.  
  
> [!CAUTION]
>  [Správce řízení služeb](http://msdn.microsoft.com/library/windows/desktop/ms685150.aspx) používá `dwWaitHint` a `dwCheckpoint` členy [SERVICE_STATUS struktura](http://msdn.microsoft.com/library/windows/desktop/ms685996.aspx) k určení jak dlouho čekat na spuštění nebo vypnutí služby systému Windows. Pokud vaše <xref:System.ServiceProcess.ServiceBase.OnStart%2A> a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody spustit dlouhé, služby můžete požádat o víc času voláním [SetServiceStatus](http://msdn.microsoft.com/library/windows/desktop/ms686241.aspx) znovu s zvýšena `dwCheckPoint` hodnotu.  
  
<a name="BK_AddInstallers"></a>   
## <a name="adding-installers-to-the-service"></a>Přidávání instalačních programů do služby  
 Před spuštěním služby systému Windows, musíte nainstalovat ji, který registruje ho s správce řízení služeb. Instalační programy můžete přidat do projektu, který zpracovává podrobnosti registrace.  
  
#### <a name="to-create-the-installers-for-your-service"></a>Vytvoření instalačních programů pro vaši službu  
  
1.  V **Průzkumníku řešení**, otevřete kontextovou nabídku **MyNewService.cs** nebo **MyNewService.vb**a potom zvolte **Návrhář zobrazení**.  
  
2.  Kliknutím na pozadí návrháře vyberte samotnou službu namísto některé z jejích komponent.  
  
3.  Otevřete kontextu nabídku pro návrháře okno (Pokud používáte polohovací zařízení, klikněte pravým tlačítkem uvnitř okna) a potom zvolte **přidat instalační program**.  
  
     Ve výchozím nastavení bude do projektu přidána komponentní třída, která obsahuje dva instalační programy. Součást jmenuje **ProjectInstaller**a instalační programy obsahuje instalační program služby a instalační program služby přidruženému procesu.  
  
4.  V **návrhu** zobrazit **ProjectInstaller**, zvolte **serviceInstaller1** pro projektu jazyka Visual C#, nebo **ServiceInstaller1** pro zobrazení Základní projektu.  
  
5.  V **vlastnosti** okno, zajistěte, aby <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> je nastavena na **MyNewService**.  
  
6.  Nastavte **popis** vlastnost, která má některé text, například "Ukázka služba". Tento text se zobrazí v okně služby a pomáhá uživatele k identifikaci služby a pochopit, co se používá.  
  
7.  Nastavte <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> vlastnost text, který se má zobrazit v okně služby v **název** sloupce. Můžete například zadat "MyNewService zobrazovaný název". Tento název se může lišit od <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> vlastnost, která je název používaný systému (například při použití `net start` příkaz ke spuštění služby).  
  
8.  Nastavte <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnost <xref:System.ServiceProcess.ServiceStartMode.Automatic>.  
  
     ![Vlastnosti Instalační služby systému Windows](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")  
  
9. V návrháři, zvolte **serviceProcessInstaller1** pro projektu jazyka Visual C#, nebo **ServiceProcessInstaller1** pro projektu jazyka Visual Basic. Nastavte <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> vlastnost <xref:System.ServiceProcess.ServiceAccount.LocalSystem>. To způsobí, že bude služba nainstalována a spuštěna s použitím účtu místní služby.  
  
    > [!IMPORTANT]
    >  <xref:System.ServiceProcess.ServiceAccount.LocalSystem> Účet má oprávnění široký, včetně možnost zapisovat do protokolu událostí. Používejte tento účet opatrně, protože může zvýšit riziko napadení škodlivým softwarem. Pro ostatní úlohy, zvažte použití pomocí <xref:System.ServiceProcess.ServiceAccount.LocalService> účet, který funguje jako uživatel bez oprávnění místního počítače a uvede anonymní přihlašovací údaje k žádnému vzdáleného serveru. V tomto příkladu se nezdaří, pokud se pokusíte použít <xref:System.ServiceProcess.ServiceAccount.LocalService> účet, protože je nutné oprávnění k zápisu do protokolu událostí.  
  
     Další informace o instalačních programů najdete v tématu [postupy: Přidání instalačních programů pro vaše aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
<a name="BK_StartupParameters"></a>   
## <a name="set-startup-parameters"></a>Nastavit parametry spuštění  
 Služby systému Windows, jako je jakéhokoliv jiného spustitelného souboru, může přijmout argumenty příkazového řádku, nebo parametry spuštění. Když přidáte kód k parametrům spuštění procesu, uživatelé mohou spustit služby s vlastní parametry vlastní spuštění pomocí okna služby v Ovládacích panelech Windows. Tyto parametry spuštění však nejsou trvalé při příštím spuštění služby. Pokud chcete nastavit parametry spuštění trvale, můžete nastavit je v registru, jak je znázorněno v tomto postupu.  
  
> [!NOTE]
>  Předtím, než se rozhodnete přidat parametry spuštění, zvažte, zda je to nejlepší způsob, jak předat informace k službě. I když jsou parametry spuštění snadno použitelný a analýzy a uživatelé mohou snadno nepřepíšete, mohou být těžší uživatelům zjišťovat a používat bez dokumentaci. Obecně platí Pokud služba vyžaduje více než jen pár parametry spuštění, měli byste zvážit použití registru nebo konfiguračního souboru místo toho. Všechny služby systému Windows má záznam v registru pod HKLM\System\CurrentControlSet\services. V klíči služby, můžete použít **parametry** podklíč k uložení informace, které můžete přístup k službě. Konfigurační soubory aplikace můžete použít pro službu systému Windows stejným způsobem jako u jiných typů programy. Příklad kódu, najdete v části <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.  
  
#### <a name="adding-startup-parameters"></a>Přidání parametrů spuštění  
  
1.  V `Main` metoda v souboru Program.cs nebo v MyNewService.Designer.vb, přidejte argument příkazového řádku:  
  
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
  
2.  Změna `MyNewService` konstruktor následujícím způsobem:  
  
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
  
Tento kód nastaví název zdroje a protokol událostí podle parametry zadané spuštění nebo používá výchozí hodnoty, pokud jsou zadány žádné argumenty.  
  
3. Pokud chcete zadat argumenty příkazového řádku, přidejte následující kód, který `ProjectInstaller` třídy v ProjectInstaller.cs nebo ProjectInstaller.vb:  
  
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
  
Tento kód upraví **ImagePath** klíč registru, který obvykle obsahuje úplnou cestu ke spustitelnému souboru pro službu systému Windows tak, že přidáte výchozí hodnoty parametrů. Uvozovky kolem cestu (a kolem každé jednotlivé parametr) se vyžadují pro službu, kterou chcete spustit správně. Chcete-li změnit parametry pro spuštění této služby systému Windows, uživatelé mohou změnit zadanými parametry **ImagePath** klíče registru, i když tím lépe způsobem je ho změnit prostřednictvím kódu programu a zpřístupnění funkcí pro uživatele v popisný způsobem (například nástroj pro správu nebo konfigurace).  
  
<a name="BK_Build"></a>   
## <a name="building-the-service"></a>Vytvoření služby  
  
#### <a name="to-build-your-service-project"></a>Sestavení projektu služby  
  
1.  V **Průzkumníku řešení**, otevřete v místní nabídce pro svůj projekt a zvolte **vlastnosti**. Zobrazí se na stránkách vlastností projektu.  
  
2.  Na kartě aplikace v **spouštěcí objekt** vyberte **MyNewService.Program**.  
  
3.  V **Průzkumníku řešení**, otevřete v místní nabídce pro svůj projekt a zvolte **sestavení** pro sestavení projektu (klávesové: Ctrl + Shift + B).  
  
<a name="BK_Install"></a>   
## <a name="installing-the-service"></a>Nainstalovat službu  
 Teď, když jste sestavili službu systému Windows, můžete ho nainstalovat. K instalaci služby systému Windows, musíte mít pověření správce na počítači, na kterém instalujete ho.  
  
#### <a name="to-install-a-windows-service"></a>Chcete-li nainstalovat služby systému Windows  
  
1.  Ve Windows 7 a Windows Server, otevřete **příkazový řádek vývojáře** pod **nástroje sady Visual Studio** v **spustit** nabídky. V systému Windows 8 nebo Windows 8.1, vyberte **nástroje sady Visual Studio** na dlaždici **spustit** obrazovky a pak spusťte příkazový řádek vývojáře s přihlašovacími údaji správce. (Pokud používáte myši, klikněte pravým tlačítkem na **příkazový řádek vývojáře**a potom zvolte **spustit jako správce**.)  
  
2.  V okně příkazového řádku přejděte do složky, která obsahuje výstupní vašeho projektu. Například v rámci složky Dokumenty přejděte do složky Visual Studio 2013\Projects\MyNewService\bin\Debug.  
  
3.  Zadejte následující příkaz:  
  
    ```  
    installutil.exe MyNewService.exe  
    ```  
  
     Pokud je služba nainstalována úspěšně, oznámí program installutil.exe úspěch. Pokud nelze najít InstallUtil.exe, ujistěte se, zda existuje ve vašem počítači. Tento nástroj je instalován s rozhraním .NET Framework ke složce `%WINDIR%\Microsoft.NET\Framework[64]\` *framework_version*. Například výchozí cesta pro 32bitovou verzi rozhraní .NET Framework 4, 4.5, 4.5.1 a 4.5.2 je `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`.  
  
     Pokud proces installutil.exe ohlásí selhání, zkontrolujte v protokolu instalace a zjistěte, proč. Ve výchozím nastavení v protokolu je ve stejné složce jako spustitelný soubor služby. Instalace může selhat, pokud <xref:System.ComponentModel.RunInstallerAttribute> třída není obsažena v `ProjectInstaller` třídy, jinak atribut není nastavený na `true`, jinak `ProjectInstaller` třída není `public`.  
  
     Další informace najdete v tématu [postupy: instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
<a name="BK_StartService"></a>   
## <a name="starting-and-running-the-service"></a>Spuštění a spuštěna služba  
  
#### <a name="to-start-and-stop-your-service"></a>Spuštění a zastavení služby  
  
1.  V systému Windows, otevřete **spustit** obrazovky nebo **spustit** nabídce a typ `services.msc`.  
  
     Teď byste měli vidět **MyNewService** uvedené v **služby** okno.  
  
     ![MyNewService v okně služby. ] (../../../docs/framework/windows-services/media/windowsservices-serviceswindow.PNG "WindowsServices_ServicesWindow")  
  
2.  V **služby** oken, otevřete místní nabídku pro vaši službu a pak zvolte **spustit**.  
  
3.  Otevřete místní nabídku pro službu a potom zvolte **Zastavit**.  
  
4.  (Volitelné) Z příkazového řádku, můžete použít příkazy `net start``ServiceName` a `net stop``ServiceName` spuštění a zastavení služby.  
  
#### <a name="to-verify-the-event-log-output-of-your-service"></a>Ověření výstupu služby v protokolu událostí  
  
1.  V sadě Visual Studio, otevřete **Průzkumníka serveru** (klávesové: Ctrl + Alt + S) a přístup **protokoly událostí** uzel pro místní počítač.  
  
2.  Vyhledejte položku **MyNewLog** (nebo **MyLogFile1**, pokud jste použili volitelný postup pro přidání argumenty příkazového řádku) a rozbalte ho. Měli byste vidět položky pro dvě akce (spouštění a zastavování) byla provedena služby.  
  
     ![Pomocí prohlížeče událostí zobrazíte položky protokolu událostí. ] (../../../docs/framework/windows-services/media/windowsservices-eventviewer.PNG "WindowsServices_EventViewer")  
  
<a name="BK_Uninstall"></a>   
## <a name="uninstalling-a-windows-service"></a>Odinstalace služby systému Windows  
  
#### <a name="to-uninstall-your-service"></a>Odinstalace služby  
  
1.  Otevřete příkazový řádek vývojáře s přihlašovacími údaji správce.  
  
2.  V okně příkazového řádku přejděte do složky, která obsahuje výstupní vašeho projektu. Například v rámci složky Dokumenty přejděte do složky Visual Studio 2013\Projects\MyNewService\bin\Debug.  
  
3.  Zadejte následující příkaz:  
  
    ```  
    installutil.exe /u MyNewService.exe  
    ```  
  
     Pokud je služba úspěšně odinstalována, program installutil.exe oznámí, že byla služba úspěšně odebrána. Další informace najdete v tématu [postupy: instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
## <a name="next-steps"></a>Další kroky  
 Můžete vytvořit samostatný instalační program, který ostatní můžete použít k instalaci služby Windows, ale vyžaduje další kroky. Technologie ClickOnce nepodporuje služby systému Windows, a proto nelze použít Průvodce publikováním. Můžete použít plnou edici nástroje InstallShield, kterou ale společnost Microsoft neposkytuje. Další informace o programu InstallShield najdete v tématu [InstallShield Limited Edition](/visualstudio/deployment/installshield-limited-edition). Můžete také [sada nástrojů XML pro instalační program systému Windows](http://go.microsoft.com/fwlink/?LinkId=249067) vytvořit instalační program pro službu systému Windows.  
  
 Použití může zkoumat <xref:System.ServiceProcess.ServiceController> komponenta, která umožňuje odesílání příkazů do mají nainstalovánu službu.  
  
 Pomocí instalačního programu můžete vytvořit protokol událostí při instalaci aplikace namísto vytvoření protokolu událostí po spuštění aplikace. Při odinstalaci aplikace navíc instalační program protokol událostí odstraní. Další informace najdete v tématu <xref:System.Diagnostics.EventLogInstaller> stránka s referencemi k.  
  
## <a name="see-also"></a>Viz také  
 [Aplikace služby systému Windows](../../../docs/framework/windows-services/index.md)  
 [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Postupy: Ladění aplikací služby systému Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [Služby (Windows)](http://msdn.microsoft.com/library/windows/desktop/ms685141.aspx)
