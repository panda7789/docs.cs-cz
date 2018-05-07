---
title: Konfigurace sledování pro pracovní postup
ms.date: 03/30/2017
ms.assetid: 905adcc9-30a0-4918-acd6-563f86db988a
ms.openlocfilehash: 70697d82242ab0704dd67129940a6660d300bef9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="configuring-tracking-for-a-workflow"></a>Konfigurace sledování pro pracovní postup
Pracovní postup můžete provést třemi způsoby:  
  
-   Hostované v <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
-   Provést, protože <xref:System.Activities.WorkflowApplication>  
  
-   Provést přímo pomocí <xref:System.Activities.WorkflowInvoker>  
  
 V závislosti na pracovním postupu možností hostování účastník sledování přidat kód nebo pomocí konfiguračního souboru. Toto téma popisuje konfiguraci sledování přidáním sledování navrhnout <xref:System.Activities.WorkflowApplication> a <xref:System.ServiceModel.Activities.WorkflowServiceHost>a jak povolit sledování, pokud používáte <xref:System.Activities.WorkflowInvoker>.  
  
## <a name="configuring-workflow-application-tracking"></a>Konfigurace aplikace pracovního postupu pro sledování  
 Pracovní postup můžete spustit pomocí <xref:System.Activities.WorkflowApplication> třídy. Toto téma popisuje, jak je sledování nakonfigurovaná pro [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] aplikace pracovního postupu přidáním sledování navrhnout <xref:System.Activities.WorkflowApplication> hostitele pracovního postupu. V takovém případě pracovní postup spouští jako aplikace pracovního postupu. Konfigurace aplikace pracovního postupu prostřednictvím kódu (nikoli pomocí konfiguračního souboru), což je vlastním hostováním .exe souboru pomocí <xref:System.Activities.WorkflowApplication> třídy. Sledování účastník se přidal jako extension <xref:System.Activities.WorkflowApplication> instance. To se provádí přidáním <xref:System.Activities.Tracking.TrackingParticipant> ke kolekci rozšíření pro instanci WorkflowApplication.  
  
 Aplikace pomocí pracovního postupu můžete přidat <xref:System.Activities.Tracking.EtwTrackingParticipant> chování rozšíření, jak je znázorněno v následujícím kódu.  
  
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
 Pracovní postup, mohou být zpřístupněny jako [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby, když jsou hostované v <xref:System.ServiceModel.Activities.WorkflowServiceHost> hostitele služby. <xref:System.ServiceModel.Activities.WorkflowServiceHost> je specializovaná implementace rozhraní .NET ServiceHost služby založené na pracovním postupu. Tato část vysvětluje postup konfigurace sledování pro [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] pracovního postupu služby spuštěné <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Je nakonfigurovaný pomocí souboru Web.config (pro hostované webové služby) nebo soubor App.config (pro služby hostované v samostatná aplikace, jako je například aplikace konzoly) zadáním chování služby nebo prostřednictvím kódu přidáním specifické pro sledování chování <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekce hostitele služby.  
  
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
  
 Můžete taky pro pracovní postup služby hostované v <xref:System.ServiceModel.WorkflowServiceHost>, můžete přidat <xref:System.Activities.Tracking.EtwTrackingParticipant> chování rozšíření prostřednictvím kódu. Pokud chcete přidat vlastní sledování účastník, vytvořte nové rozšíření chování a přidejte ho do <xref:System.ServiceModel.ServiceHost> jak je znázorněno v následujícím příkladu kódu.  
  
> [!NOTE]
>  Pokud chcete zobrazit ukázkový kód, který ukazuje, jak vytvořit vlastní chování element, který přidá vlastní sledování účastník, podívejte se na [sledování](../../../docs/framework/windows-workflow-foundation/samples/tracking.md) ukázky.  
  
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
  
 Sledování účastník je na hostiteli služby pracovního postupu přidal jako extension v chování.  
  
 Následující ukázkový kód ukazuje, jak načíst profil sledování z konfiguračního souboru.  
  
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
>  Další informace o sledování profily, najdete v části [sledování profily](http://go.microsoft.com/fwlink/?LinkId=201310).  
  
### <a name="configuring-tracking-using-workflowinvoker"></a>Konfigurace sledování pomocí WorkflowInvoker  
 Konfigurace sledování pro pracovní postup provést pomocí <xref:System.Activities.WorkflowInvoker>, přidejte zprostředkovatele sledování jako rozšíření <xref:System.Activities.WorkflowInvoker> instance. Následující příklad kódu je z [vlastní sledování](../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) ukázka.  
  
```  
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());  
invoker.Extensions.Add(customTrackingParticipant);  
invoker.Invoke();  
```  
  
### <a name="viewing-tracking-records-in-event-viewer"></a>Zobrazení sledování záznamů v prohlížeči událostí  
 Existují dva protokoly Prohlížeče událostí zajímají hlavně o zobrazíte při sledování provádění WF - analytické protokolu a protokolu ladění. Obě jsou umístěny v části Microsoft&#124;Windows&#124;uzlu serveru aplikace – aplikace.  Protokoly v této části obsahují události z jedné aplikace a nikoli události, které mají vliv na celý systém.  
  
 Ladění trasování, které události se zapisují do protokolů ladění. Chcete-li shromažďovat události trasování ladění WF v prohlížeči událostí, povolte protokol ladění.  
  
1.  Chcete-li spustit nástroj Prohlížeč událostí, klikněte na tlačítko **spustit**a pak klikněte na tlačítko **spustit.** V dialogovém okně Spustit zadejte `eventvwr`.  
  
2.  V dialogovém okně prohlížeče událostí, rozbalte **protokoly aplikací a služeb** uzlu.  
  
3.  Rozbalte **Microsoft**, **Windows**, a **serveru aplikace – aplikace** uzlů.  
  
4.  Klikněte pravým tlačítkem myši **ladění** pod uzlem **serveru aplikace – aplikace** uzel a vyberte možnost **povolit protokol**.  
  
5.  Spusťte aplikaci povoleno trasování generovat události trasování.  
  
6.  Klikněte pravým tlačítkem myši **ladění** uzel a vyberte možnost **aktualizovat.** Trasování událostí má být zobrazen ve středovém podokně.  
  
 WF 4 poskytuje sledování člena, který zapíše sledování záznamů relaci trasování událostí pro Windows (trasování událostí pro Windows). Trasování událostí pro Windows Sledování účastník je nakonfigurovaný s profil sledování k odběru sledování záznamů.  Pokud je povoleno sledování, jsou chyby sledování záznamy vygenerované do trasování událostí pro Windows. Trasování událostí pro Windows Sledování událostí (mezi rozsahu 100 113) odpovídající sledování události vygenerované účastníkem sledování, trasování událostí pro Windows se zapíšou do analytické protokolu.  
  
 Chcete-li zobrazit záznamy o sledování, postupujte podle těchto kroků.  
  
1.  Chcete-li spustit nástroj Prohlížeč událostí, klikněte na tlačítko **spustit**a pak klikněte na tlačítko **spustit.** V dialogovém okně Spustit zadejte `eventvwr`.  
  
2.  V dialogovém okně prohlížeče událostí, rozbalte **protokoly aplikací a služeb** uzlu.  
  
3.  Rozbalte **Microsoft**, **Windows**, a **serveru aplikace – aplikace** uzlů.  
  
4.  Klikněte pravým tlačítkem myši **analytické** pod uzlem **serveru aplikace – aplikace** uzel a vyberte možnost **povolit protokol**.  
  
5.  Spuštění vaší aplikace s povolenými sledování ke generování sledování záznamů.  
  
6.  Klikněte pravým tlačítkem myši **analytické** uzel a vyberte možnost **aktualizovat.** Sledování záznamy by měly jít vidět ve středovém podokně.  
  
 Následující obrázek znázorňuje sledování událostí v prohlížeči událostí.  
  
 ![Zobrazuje Prohlížeč událostí sledování záznamů](../../../docs/framework/windows-workflow-foundation/media/trackingeventviewer.PNG "TrackingEventViewer")  
  
### <a name="registering-an-application-specific-provider-id"></a>Registrace ID zprostředkovatele specifické pro aplikaci  
 Pokud události jsou určeny k zápisu do protokolu konkrétní aplikaci, postupujte podle těchto kroků k registraci nového manifestu zprostředkovatele.  
  
1.  Deklarujte ID zprostředkovatele v konfiguračním souboru aplikace.  
  
    ```xml  
    <system.serviceModel>  
        <diagnostics etwProviderId="2720e974-9fe9-477a-bb60-81fe3bf91eec"/>  
    </system.serviceModel>  
    ```  
  
2.  Zkopírujte soubor manifestu z %windir%\Microsoft.NET\Framework\\< nejnovější verzi [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]> \Microsoft.Windows.ApplicationServer.Applications.man do dočasného umístění a přejmenujte ji na Microsoft.Windows.ApplicationServer.Applications_Provider1.man  
  
3.  Identifikátor GUID v souboru manifestu změňte na nový identifikátor GUID.  
  
    ```xml  
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"  
    ```  
  
4.  Změňte název zprostředkovatele, pokud nechcete odinstalovat výchozího zprostředkovatele.  
  
    ```xml  
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"  
    ```  
  
5.  Pokud jste změnili název zprostředkovatele v předchozím kroku, změňte názvy kanál v souboru manifestu na nový název zprostředkovatele.  
  
    ```xml  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Admin" chid="ADMIN_CHANNEL" symbol="ADMIN_CHANNEL" type="Admin" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ADMIN_CHANNEL.message)" />  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Operational" chid="OPERATIONAL_CHANNEL" symbol="OPERATIONAL_CHANNEL" type="Operational" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.OPERATIONAL_CHANNEL.message)" />  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" />  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Debug" chid="DEBUG_CHANNEL" symbol="DEBUG_CHANNEL" type="Debug" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.DEBUG_CHANNEL.message)" />  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Perf" chid="PERF_CHANNEL" symbol="PERF_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.PERF_CHANNEL.message)" />  
    ```  
  
6.  Generovat DLL prostředků pomocí následujících kroků.  
  
    1.  Instalace sady Windows SDK. Sada Windows SDK zahrnuje kompilátoru zprávy ([mc.exe](http://go.microsoft.com/fwlink/?LinkId=184606)) a kompilátor prostředků ([rc.exe](http://go.microsoft.com/fwlink/?LinkId=184605)).  
  
    2.  V příkazovém řádku Windows SDK spusťte mc.exe na nový soubor manifestu.  
  
        ```  
        mc.exe Microsoft.Windows.ApplicationServer.Applications_Provider1.man  
        ```  
  
    3.  Spusťte rc.exe v souboru prostředků vygenerované v předchozím kroku.  
  
        ```  
        rc.exe  Microsoft.Windows.ApplicationServer.Applications_Provider1.rc  
        ```  
  
    4.  Vytvořte soubor prázdný cs názvem NewProviderReg.cs.  
  
    5.  Vytvořte prostředek knihovny DLL pomocí kompilátor jazyka C#.  
  
        ```  
        csc /target:library /win32res:Microsoft.Windows.ApplicationServer.Applications_Provider1.res NewProviderReg.cs /out:Microsoft.Windows.ApplicationServer.Applications_Provider1.dll  
        ```  
  
    6.  Změnit dl namel prostředků a zpráv v souboru manifestu z `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` na nový název knihovny dll.  
  
        ```xml  
        <provider name="Microsoft-Windows-Application Server-Applications_Provider1" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" symbol="Microsoft_Windows_ApplicationServer_ApplicationEvents" resourceFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" messageFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll">  
        ```  
  
    7.  Použití [wevtutil](http://go.microsoft.com/fwlink/?LinkId=184608) k registraci v manifestu.  
  
        ```  
        wevtutil im Microsoft.Windows.ApplicationServer.Applications_Provider1.man  
        ```  
  
## <a name="see-also"></a>Viz také  
 [Windows Server App Fabric monitorování](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitorování aplikací pomocí App Fabric](http://go.microsoft.com/fwlink/?LinkId=201275)
