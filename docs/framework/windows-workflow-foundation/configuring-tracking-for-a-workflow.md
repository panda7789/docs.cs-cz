---
title: Konfigurace sledování pracovního postupu
ms.date: 03/30/2017
ms.assetid: 905adcc9-30a0-4918-acd6-563f86db988a
ms.openlocfilehash: ae6b61bf572da1757920b737b03861c891637f51
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519698"
---
# <a name="configuring-tracking-for-a-workflow"></a>Konfigurace sledování pracovního postupu
Pracovní postup můžete provést třemi způsoby:  
  
-   Hostované v <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
-   Provést, protože <xref:System.Activities.WorkflowApplication>  
  
-   Proveden přímo pomocí <xref:System.Activities.WorkflowInvoker>  
  
 V závislosti na pracovním postupu možnost hostování sledování účastník přidat buď prostřednictvím kódu nebo konfiguračního souboru. Toto téma popisuje, jak je sledování nakonfigurované tak, že přidáte sledování účastník <xref:System.Activities.WorkflowApplication> a získat <xref:System.ServiceModel.Activities.WorkflowServiceHost>a jak povolit sledování při použití <xref:System.Activities.WorkflowInvoker>.  
  
## <a name="configuring-workflow-application-tracking"></a>Konfigurace sledování aplikace pracovního postupu  
 Pracovní postup můžete spustit pomocí <xref:System.Activities.WorkflowApplication> třídy. Toto téma popisuje konfiguraci sledování pro [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] aplikace pracovního postupu tak, že přidáte sledování účastník <xref:System.Activities.WorkflowApplication> hostitele pracovního postupu. V takovém případě pracovní postup spouští jako aplikace pracovního postupu. Nakonfigurovat aplikace pracovního postupu pomocí kódu (spíše než pomocí konfiguračního souboru), který je v místním prostředí .exe souboru pomocí <xref:System.Activities.WorkflowApplication> třídy. Sledování účastník bude přidán jako rozšíření <xref:System.Activities.WorkflowApplication> instance. To se provádí tak, že přidáte <xref:System.Activities.Tracking.TrackingParticipant> do kolekce rozšíření pro instanci aplikace WorkflowApplication.  
  
 Pro aplikace pracovního postupu můžete přidat <xref:System.Activities.Tracking.EtwTrackingParticipant> rozšíření chování, jak je znázorněno v následujícím kódu.  
  
```csharp  
LogActivity activity = new LogActivity();  
  
WorkflowApplication instance = new WorkflowApplication(activity);  
EtwTrackingParticipant trackingParticipant =  
    new EtwTrackingParticipant  
{  
  
        TrackingProfile = new TrackingProfile  
           {  
               Name = "SampleTrackingProfile",  
               ActivityDefinitionId = "ProcessOrder",  
               Queries = new WorkflowInstanceQuery  
               {  
                  States = { "*" }  
              }  
          }  
       };  
instance.Extensions.Add(trackingParticipant);  
```  
  
### <a name="configuring-workflow-service-tracking"></a>Konfigurace sledování služby pracovního postupu  
 Pracovní postup může být vystavena jako služba WCF při hostování v <xref:System.ServiceModel.Activities.WorkflowServiceHost> hostitele služby. <xref:System.ServiceModel.Activities.WorkflowServiceHost> je specializovaná implementace .NET ServiceHost pro nějakou službu založenou na pracovního postupu. Tato část vysvětluje postup konfigurace sledování [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] používané služby pracovního postupu <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Je nakonfigurovaný pomocí souboru Web.config (pro Web hostované služby) nebo soubor App.config (pro služby hostované v samostatné aplikaci, jako je například aplikace konzoly) zadáním chování služby nebo pomocí kódu přidáním specifické pro sledování chování <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekce pro tohoto hostitele služby.  
  
 Pro pracovní postup služby hostované v <xref:System.ServiceModel.WorkflowServiceHost>, můžete přidat <xref:System.Activities.Tracking.EtwTrackingParticipant> pomocí <`behavior`> element v konfiguračním souboru, jak je znázorněno v následujícím příkladu.  
  
```xml  
<behaviors>  
   <serviceBehaviors>  
        <behavior>  
          <etwTracking profileName="Sample Tracking Profile" />  
        </behavior>              
   </serviceBehaviors>  
<behaviors>  
```  
  
 Můžete také služby pracovního postupu hostované v <xref:System.ServiceModel.WorkflowServiceHost>, můžete přidat <xref:System.Activities.Tracking.EtwTrackingParticipant> rozšíření chování prostřednictvím kódu. Chcete-li přidat vlastní sledování účastník, vytvořit nové rozšíření chování a přidejte ho do <xref:System.ServiceModel.ServiceHost> jak je znázorněno v následujícím příkladu kódu.  
  
> [!NOTE]
>  Pokud chcete zobrazit ukázkový kód, který ukazuje, jak vytvořit vlastní chování element, který přidá vlastní sledování účastník, přečtěte si [sledování](../../../docs/framework/windows-workflow-foundation/samples/tracking.md) ukázky.  
  
```  
ServiceHost svcHost = new ServiceHost(typeof(WorkflowService), new   
                                 Uri("http://localhost:8001/Sample"));  
EtwTrackingBehavior trackingBehavior =   
    new EtwTrackingBehavior  
    {  
        ProfileName = "Sample Tracking Profile"  
    };  
svcHost.Description.Behaviors.Add(trackingBehavior);  
svcHost.Open();  
```  
  
 Účastník sledování se přidá k hostiteli služby pracovního postupu jako rozšíření chování.  
  
 Následující ukázkový kód ukazuje, jak číst z konfiguračního souboru profilu sledování.  
  
```  
TrackingProfile GetProfile(string profileName, string displayName)  
        {  
            TrackingProfile trackingProfile = null;  
            TrackingSection trackingSection = (TrackingSection)WebConfigurationManager.GetSection("system.serviceModel/tracking");  
            if (trackingSection == null)   
            {  
                return null;  
            }  
  
            if (profileName == null)   
            {  
                profileName = "";  
            }  
  
            //Find the profile with the specified profile name in the list of profile found in config  
            var match = from p in new List<TrackingProfile>(trackingSection.TrackingProfiles)  
                        where (p.Name == profileName) && ((p.ActivityDefinitionId == displayName) || (p.ActivityDefinitionId == "*"))  
                        select p;  
  
            if (match.Count() == 0)  
            {  
                //return an empty profile  
                trackingProfile = new TrackingProfile()  
                {  
                    ActivityDefinitionId = displayName  
                };  
  
            }  
            else  
            {  
                trackingProfile = match.First();  
            }  
  
            return trackingProfile;  
```  
  
 Tento ukázkový kód ukazuje, jak přidat profil sledování do hostitele pracovního postupu.  
  
```  
WorkflowServiceHost workflowServiceHost = serviceHostBase as WorkflowServiceHost;  
if (null != workflowServiceHost)  
{  
              string workflowDisplayName = workflowServiceHost.Activity.DisplayName;  
               TrackingProfile trackingProfile = GetProfile(this.profileName, workflowDisplayName);  
                workflowServiceHost.WorkflowExtensions.Add(()  => new EtwTrackingParticipant  {  
               TrackingProfile = trackingProfile  
                        });  
 }  
```  
  
> [!NOTE]
>  Další informace o sledování profilů najdete [sledování profilů](https://go.microsoft.com/fwlink/?LinkId=201310).  
  
### <a name="configuring-tracking-using-workflowinvoker"></a>Konfigurace sledování pomocí WorkflowInvoker  
 Konfigurace sledování pracovního postupu spuštěn pomocí <xref:System.Activities.WorkflowInvoker>, přidejte zprostředkovatele sledování jako rozšíření <xref:System.Activities.WorkflowInvoker> instance. Následující příklad kódu je z [vlastní sledování](../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) vzorku.  
  
```  
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());  
invoker.Extensions.Add(customTrackingParticipant);  
invoker.Invoke();  
```  
  
### <a name="viewing-tracking-records-in-event-viewer"></a>Zobrazení sledování záznamů v prohlížeči událostí  
 Existují dva protokoly Prohlížeče událostí zajímají hlavně o zobrazení při sledování provádění pracovního postupu - analýzy protokolů a protokolů ladění. Obě nacházet v rámci Microsoft&#124;Windows&#124;uzlu serveru aplikace.  Protokoly v této části obsahují události z jedné aplikace, nikoli události, které mají vliv na celý systém.  
  
 Ladění trasování, které události se zapisují do protokolů ladění. Shromažďování událostí trasování ladění pracovního postupu v prohlížeči událostí, povolte protokol ladění.  
  
1.  Chcete-li spustit nástroj Prohlížeč událostí, klikněte na tlačítko **Start**a potom klikněte na tlačítko **spustit.** V dialogu Spustit zadejte `eventvwr`.  
  
2.  V dialogovém okně prohlížeče událostí, rozbalte **protokoly aplikací a služeb** uzlu.  
  
3.  Rozbalte **Microsoft**, **Windows**, a **aplikace Server-** uzly.  
  
4.  Klikněte pravým tlačítkem myši **ladění** pod uzlem **Server aplikace** uzel a vyberte možnost **povolit protokol**.  
  
5.  Spusťte vaši aplikaci povoleno trasování generovat události trasování.  
  
6.  Klikněte pravým tlačítkem myši **ladění** uzel a vyberte možnost **aktualizovat.** Trasování událostí by se zobrazovat v prostředním podokně.  
  
 WF 4 poskytuje sledování účastník, který zapíše záznamy sledování k relaci ETW (událost trasování pro Windows). Účastník sledování ETW konfigurován pomocí sledování profil přihlásit k odběru sledování záznamů.  Pokud je povoleno sledování, chyby sledování záznamů je vygenerován pro trasování událostí pro Windows. Trasování událostí pro Windows Sledování událostí (v rozsahu 100 113) od odpovídající, protože ho vygeneroval účastník sledování ETW sledování události se zapisují do v analytickém protokolu.  
  
 Chcete-li zobrazit záznamy sledování, postupujte podle těchto kroků.  
  
1.  Chcete-li spustit nástroj Prohlížeč událostí, klikněte na tlačítko **Start**a potom klikněte na tlačítko **spustit.** V dialogu Spustit zadejte `eventvwr`.  
  
2.  V dialogovém okně prohlížeče událostí, rozbalte **protokoly aplikací a služeb** uzlu.  
  
3.  Rozbalte **Microsoft**, **Windows**, a **aplikace Server-** uzly.  
  
4.  Klikněte pravým tlačítkem myši **analytické** pod uzlem **Server aplikace** uzel a vyberte možnost **povolit protokol**.  
  
5.  Spuštění vaší aplikace s povolenými sledování k vygenerování záznamů sledování.  
  
6.  Klikněte pravým tlačítkem myši **analytické** uzel a vyberte možnost **aktualizovat.** Sledování záznamů by se zobrazovat v prostředním podokně.  
  
 Sledování událostí v prohlížeči událostí na následujícím obrázku.  
  
 ![Zobrazení prohlížeče událostí sledování záznamů](../../../docs/framework/windows-workflow-foundation/media/trackingeventviewer.PNG "TrackingEventViewer")  
  
### <a name="registering-an-application-specific-provider-id"></a>Registrace poskytovatele specifické pro aplikaci ID  
 Pokud události se zapisují do protokolu konkrétní aplikaci, použijte následující postup zaregistrovat nový manifest zprostředkovatele.  
  
1.  Deklarujte ID zprostředkovatele v konfiguračním souboru aplikace.  
  
    ```xml  
    <system.serviceModel>  
        <diagnostics etwProviderId="2720e974-9fe9-477a-bb60-81fe3bf91eec"/>  
    </system.serviceModel>  
    ```  
  
2.  Zkopírujte soubor manifestu z %windir%\Microsoft.NET\Framework\\< nejnovější verzi [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]> \Microsoft.Windows.ApplicationServer.Applications.man do dočasného umístění a přejmenujte ho na Microsoft.Windows.ApplicationServer.Applications_Provider1.man  
  
3.  Změňte na nové GUID identifikátoru GUID v souboru manifestu.  
  
    ```xml  
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"  
    ```  
  
4.  Pokud nechcete odinstalovat výchozího zprostředkovatele, změňte název zprostředkovatele.  
  
    ```xml  
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"  
    ```  
  
5.  Pokud jste změnili název zprostředkovatele v předchozím kroku, změňte názvy kanálů v souboru manifestu na nový název poskytovatele.  
  
    ```xml  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Admin" chid="ADMIN_CHANNEL" symbol="ADMIN_CHANNEL" type="Admin" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ADMIN_CHANNEL.message)" />  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Operational" chid="OPERATIONAL_CHANNEL" symbol="OPERATIONAL_CHANNEL" type="Operational" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.OPERATIONAL_CHANNEL.message)" />  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" />  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Debug" chid="DEBUG_CHANNEL" symbol="DEBUG_CHANNEL" type="Debug" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.DEBUG_CHANNEL.message)" />  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Perf" chid="PERF_CHANNEL" symbol="PERF_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.PERF_CHANNEL.message)" />  
    ```  
  
6.  Vygenerujte prostředek knihovny DLL pomocí následujících kroků.  
  
    1.  Nainstalujte Windows SDK. Sada Windows SDK obsahuje kompilátor zprávy ([mc.exe](https://go.microsoft.com/fwlink/?LinkId=184606)) a kompilátor prostředků ([rc.exe](https://go.microsoft.com/fwlink/?LinkId=184605)).  
  
    2.  V příkazovém řádku Windows SDK spusťte mc.exe na nový soubor manifestu.  
  
        ```  
        mc.exe Microsoft.Windows.ApplicationServer.Applications_Provider1.man  
        ```  
  
    3.  Spusťte rc.exe na soubor prostředků vygenerované v předchozím kroku.  
  
        ```  
        rc.exe  Microsoft.Windows.ApplicationServer.Applications_Provider1.rc  
        ```  
  
    4.  Vytvořte soubor prázdný cs názvem NewProviderReg.cs.  
  
    5.  Vytvořte prostředek knihovny DLL pomocí kompilátoru jazyka C#.  
  
        ```  
        csc /target:library /win32res:Microsoft.Windows.ApplicationServer.Applications_Provider1.res NewProviderReg.cs /out:Microsoft.Windows.ApplicationServer.Applications_Provider1.dll  
        ```  
  
    6.  Změnit dl namel prostředků a zprávy v souboru manifestu z `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` na nový název knihovny dll.  
  
        ```xml  
        <provider name="Microsoft-Windows-Application Server-Applications_Provider1" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" symbol="Microsoft_Windows_ApplicationServer_ApplicationEvents" resourceFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" messageFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll">  
        ```  
  
    7.  Použití [wevtutil](https://go.microsoft.com/fwlink/?LinkId=184608) k registraci manifestu.  
  
        ```  
        wevtutil im Microsoft.Windows.ApplicationServer.Applications_Provider1.man  
        ```  
  
## <a name="see-also"></a>Viz také  
 [Windows Server App Fabric monitorování](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitorování aplikací pomocí App Fabric](https://go.microsoft.com/fwlink/?LinkId=201275)
