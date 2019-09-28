---
title: Konfigurace sledování pracovního postupu
ms.date: 03/30/2017
ms.assetid: 905adcc9-30a0-4918-acd6-563f86db988a
ms.openlocfilehash: 889efc804bb45b384dfde5b4deb520a81d1e5486
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353051"
---
# <a name="configuring-tracking-for-a-workflow"></a>Konfigurace sledování pracovního postupu

Pracovní postup může být proveden třemi způsoby:

- Hostovaná v <xref:System.ServiceModel.Activities.WorkflowServiceHost>

- Provedeno jako <xref:System.Activities.WorkflowApplication>

- Provedeno přímo pomocí <xref:System.Activities.WorkflowInvoker>

V závislosti na možnosti hostování pracovního postupu lze sledování účastníka přidat prostřednictvím kódu nebo prostřednictvím konfiguračního souboru. Toto téma popisuje, jak je sledování nakonfigurováno přidáním účastníka sledování do <xref:System.Activities.WorkflowApplication> a do <xref:System.ServiceModel.Activities.WorkflowServiceHost> a jak povolit sledování při použití <xref:System.Activities.WorkflowInvoker>.

## <a name="configuring-workflow-application-tracking"></a>Konfigurace sledování aplikace pracovního postupu

Pracovní postup lze spustit pomocí třídy <xref:System.Activities.WorkflowApplication>. Toto téma ukazuje, jak je nakonfigurováno sledování pro aplikaci pracovního postupu [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] přidáním účastníka sledování do hostitele pracovního postupu <xref:System.Activities.WorkflowApplication>. V takovém případě pracovní postup běží jako aplikace pracovního postupu. Můžete nakonfigurovat aplikaci pracovního postupu prostřednictvím kódu (nikoli pomocí konfiguračního souboru), což je samostatný soubor. exe s použitím třídy <xref:System.Activities.WorkflowApplication>. Účastník sledování se přidá jako rozšíření instance <xref:System.Activities.WorkflowApplication>. To se provádí přidáním <xref:System.Activities.Tracking.TrackingParticipant> do kolekce rozšíření pro instanci WorkflowApplication.

U aplikace pracovního postupu můžete přidat rozšíření chování <xref:System.Activities.Tracking.EtwTrackingParticipant>, jak je znázorněno v následujícím kódu.

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

Pracovní postup může být vystavený jako služba WCF při hostování v hostiteli služby <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowServiceHost> je specializovaná implementace rozhraní .NET ServiceHost pro službu založenou na pracovních postupech. V této části se dozvíte, jak nakonfigurovat sledování pro službu pracovního postupu [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] běžící v <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Je nakonfigurována pomocí souboru Web. config (pro službu hostovanou na webu) nebo souboru App. config (pro službu hostovanou v samostatné aplikaci, jako je například Konzolová aplikace), zadáním chování služby nebo prostřednictvím kódu přidáním konkrétního chování pro sledování do kolekce <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> pro hostitele služby.

U služby pracovního postupu hostovaného v <xref:System.ServiceModel.WorkflowServiceHost> můžete přidat <xref:System.Activities.Tracking.EtwTrackingParticipant> pomocí > elementu < `behavior` v konfiguračním souboru, jak je znázorněno v následujícím příkladu.

```xml
<behaviors>
   <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
   </serviceBehaviors>
<behaviors>
```

Alternativně můžete pro službu pracovního postupu, která je hostovaná v <xref:System.ServiceModel.WorkflowServiceHost>, přidat rozšíření chování <xref:System.Activities.Tracking.EtwTrackingParticipant> prostřednictvím kódu. Chcete-li přidat vlastního účastníka sledování, vytvořte nové rozšíření chování a přidejte ho do <xref:System.ServiceModel.ServiceHost>, jak je znázorněno v následujícím příkladu kódu.

> [!NOTE]
> Chcete-li zobrazit vzorový kód, který ukazuje, jak vytvořit vlastní prvek chování, který přidá vlastního účastníka sledování, přečtěte si ukázky [sledování](./samples/tracking.md) .

```csharp
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

Účastník sledování se přidá do hostitele služby pracovního postupu jako rozšíření chování.

Následující vzorový kód ukazuje, jak číst profil sledování z konfiguračního souboru.

```csharp
TrackingProfile GetProfile(string profileName, string displayName)
        {
            TrackingProfile trackingProfile = null;
            TrackingSection trackingSection = (TrackingSection)WebConfigurationManager.GetSection("system.serviceModel/tracking");
            if (trackingSection == null)
            {
                return null;
            }

            profileName ??= "";

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

Tento vzorový kód ukazuje, jak přidat profil sledování do hostitele pracovního postupu.

```csharp
WorkflowServiceHost workflowServiceHost = serviceHostBase as WorkflowServiceHost;
if (null != workflowServiceHost)
{
    string workflowDisplayName = workflowServiceHost.Activity.DisplayName;
    TrackingProfile trackingProfile = GetProfile(this.profileName, workflowDisplayName);
    workflowServiceHost.WorkflowExtensions.Add(()  => new EtwTrackingParticipant {
        TrackingProfile = trackingProfile
    });
 }
```

> [!NOTE]
> Další informace o sledování profilů najdete v tématu [sledování profilů](https://go.microsoft.com/fwlink/?LinkId=201310).

### <a name="configuring-tracking-using-workflowinvoker"></a>Konfigurace sledování pomocí WorkflowInvoker

Ke konfiguraci sledování pracovního postupu spuštěného pomocí <xref:System.Activities.WorkflowInvoker> přidejte zprostředkovatele sledování jako rozšíření do instance <xref:System.Activities.WorkflowInvoker>. Následující příklad kódu je z vlastní ukázky [sledování](./samples/custom-tracking.md) .

```csharp
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());
invoker.Extensions.Add(customTrackingParticipant);
invoker.Invoke();
```

### <a name="viewing-tracking-records-in-event-viewer"></a>Zobrazení záznamů sledování v Prohlížeč událostí

Existují dva Prohlížeč událostí protokoly, které se týkají zvláštního zájmu k zobrazení při sledování provádění technologie WF – analytického protokolu a protokolu ladění. Oba se nacházejí v uzlu aplikace&#124;serveru&#124;Microsoft Windows – aplikace. Protokoly v této části obsahují události z jedné aplikace a nikoli události, které mají vliv na celý systém.

Události trasování ladění se zapisují do protokolu ladění. Chcete-li shromáždit události trasování ladění WF v Prohlížeč událostí, povolte protokol ladění.

1. Chcete-li otevřít Prohlížeč událostí, klikněte na tlačítko **Start**a poté klikněte na příkaz **Spustit.** V dialogovém okně Spustit zadejte `eventvwr`.

2. V dialogovém okně Prohlížeč událostí rozbalte uzel **protokoly aplikací a služeb** .

3. Rozbalte uzly **Microsoft**, **Windows**a **aplikační server – aplikace** .

4. Klikněte pravým tlačítkem myši na uzel **ladění** v uzlu **aplikační server – aplikace** a vyberte **Povolit protokol**.

5. Spusťte aplikaci s povoleným trasováním a vygenerujte události trasování.

6. Klikněte pravým tlačítkem na uzel **ladění** a vyberte **aktualizovat.** Události trasování by měly být viditelné v prostředním podokně.

WF 4 poskytuje účastníkovi sledování, který zapisuje záznamy sledování do relace ETW (trasování událostí pro Windows). Účastník sledování ETW je nakonfigurovaný s profilem sledování, aby se mohl přihlásit k odběru sledování záznamů. Pokud je povoleno sledování, jsou záznamy sledování chyb generovány do ETW. Události sledování ETW (mezi rozsahem 100-113) odpovídající sledovacím událostem vygenerovaným účastníkem sledování ETW jsou zapisovány do analytického protokolu.

Chcete-li zobrazit záznamy sledování, postupujte podle těchto kroků.

1. Chcete-li otevřít Prohlížeč událostí, klikněte na tlačítko **Start**a poté klikněte na příkaz **Spustit.** V dialogovém okně Spustit zadejte `eventvwr`.

2. V dialogovém okně Prohlížeč událostí rozbalte uzel **protokoly aplikací a služeb** .

3. Rozbalte uzly **Microsoft**, **Windows**a **aplikační server – aplikace** .

4. Klikněte pravým tlačítkem myši **na uzel Analytics v uzlu** **aplikační server – aplikace** a vyberte možnost **Povolit protokol**.

5. Spusťte aplikaci s povoleným sledováním pro generování záznamů sledování.

6. Klikněte pravým tlačítkem **na uzel analýzy** a vyberte **aktualizovat.** Záznamy sledování by se měly zobrazit v prostředním podokně.

Následující obrázek ukazuje sledování událostí v prohlížeči událostí:

![Snímek obrazovky Prohlížeč událostí zobrazující záznamy o sledování](./media/configuring-tracking-for-a-workflow/tracking-event-viewer.png)

### <a name="registering-an-application-specific-provider-id"></a>Registrace ID zprostředkovatele specifického pro aplikaci

Pokud je třeba události zapsat do konkrétního protokolu aplikace, použijte následující postup k registraci nového manifestu poskytovatele.

1. Deklarujete ID zprostředkovatele v konfiguračním souboru aplikace.

    ```xml
    <system.serviceModel>
        <diagnostics etwProviderId="2720e974-9fe9-477a-bb60-81fe3bf91eec"/>
    </system.serviceModel>
    ```

2. Zkopírujte soubor manifestu z%windir%\Microsoft.NET\Framework @ no__t-0 @ no__t-1latest verze [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] > \Microsoft.Windows.ApplicationServer.Applications.man do dočasného umístění a přejmenujte ho na Microsoft. Windows. ApplicationServer. Applications_Provider1. Man

3. Změňte identifikátor GUID v souboru manifestu na nový identifikátor GUID.

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"
    ```

4. Pokud nechcete odinstalovat výchozího zprostředkovatele, změňte název zprostředkovatele.

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"
    ```

5. Pokud jste v předchozím kroku změnili název poskytovatele, změňte názvy kanálů v souboru manifestu na název nového poskytovatele.

    ```xml
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Admin" chid="ADMIN_CHANNEL" symbol="ADMIN_CHANNEL" type="Admin" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ADMIN_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Operational" chid="OPERATIONAL_CHANNEL" symbol="OPERATIONAL_CHANNEL" type="Operational" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.OPERATIONAL_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Debug" chid="DEBUG_CHANNEL" symbol="DEBUG_CHANNEL" type="Debug" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.DEBUG_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Perf" chid="PERF_CHANNEL" symbol="PERF_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.PERF_CHANNEL.message)" />
    ```

6. Vygenerujte DLL prostředku pomocí následujících kroků.

    1. Nainstalujte Windows SDK. Windows SDK obsahuje kompilátor zpráv ([MC. exe](https://go.microsoft.com/fwlink/?LinkId=184606)) a kompilátor prostředků ([RC. exe](https://go.microsoft.com/fwlink/?LinkId=184605)).

    2. Na příkazovém řádku Windows SDK spusťte příkaz MC. exe na novém souboru manifestu.

        ```console
        mc.exe Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

    3. Spusťte RC. exe v souboru prostředků vygenerovaném v předchozím kroku.

        ```console
        rc.exe  Microsoft.Windows.ApplicationServer.Applications_Provider1.rc
        ```

    4. Vytvořte prázdný soubor cs s názvem NewProviderReg.cs.

    5. Vytvořte DLL prostředku pomocí C# kompilátoru.

        ```console
        csc /target:library /win32res:Microsoft.Windows.ApplicationServer.Applications_Provider1.res NewProviderReg.cs /out:Microsoft.Windows.ApplicationServer.Applications_Provider1.dll
        ```

    6. Změňte název knihovny DLL prostředku a zprávy v souboru manifestu z `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` na nový název knihovny DLL.

        ```xml
        <provider name="Microsoft-Windows-Application Server-Applications_Provider1" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" symbol="Microsoft_Windows_ApplicationServer_ApplicationEvents" resourceFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" messageFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll">
        ```

    7. K registraci manifestu použijte [wevtutil](https://go.microsoft.com/fwlink/?LinkId=184608) .

        ```console
        wevtutil im Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

## <a name="see-also"></a>Viz také:

- [Monitorování Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201273)
- [Monitorování aplikací pomocí prostředků infrastruktury aplikace](https://go.microsoft.com/fwlink/?LinkId=201275)
