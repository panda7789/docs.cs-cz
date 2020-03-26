---
title: Konfigurace sledování pracovního postupu
ms.date: 03/30/2017
ms.assetid: 905adcc9-30a0-4918-acd6-563f86db988a
ms.openlocfilehash: 5ec94d6b8e58012d0c5c8ca8593c3cef81cd9ec3
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248209"
---
# <a name="configuring-tracking-for-a-workflow"></a>Konfigurace sledování pracovního postupu

Pracovní postup lze spustit třemi způsoby:

- Hostované v<xref:System.ServiceModel.Activities.WorkflowServiceHost>

- Popraven jako<xref:System.Activities.WorkflowApplication>

- Spuštěno přímo pomocí<xref:System.Activities.WorkflowInvoker>

V závislosti na možnosti hostování pracovního postupu lze účastníka sledování přidat buď prostřednictvím kódu, nebo prostřednictvím konfiguračního souboru. Toto téma popisuje, jak je sledování konfigurováno přidáním účastníka <xref:System.Activities.WorkflowApplication> sledování do a <xref:System.ServiceModel.Activities.WorkflowServiceHost>a , a jak povolit sledování při použití <xref:System.Activities.WorkflowInvoker>.

## <a name="configuring-workflow-application-tracking"></a>Konfigurace sledování aplikací pracovního postupu

Pracovní postup lze <xref:System.Activities.WorkflowApplication> spustit pomocí třídy. Toto téma ukazuje, jak [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] je sledování konfigurováno pro <xref:System.Activities.WorkflowApplication> aplikaci pracovního postupu přidáním účastníka sledování do hostitele pracovního postupu. V tomto případě je pracovní postup spuštěn jako aplikace pracovního postupu. Aplikaci pracovního postupu nakonfigurujete prostřednictvím kódu (nikoli pomocí konfiguračního souboru), což je samoobslužný soubor .exe používající třídu. <xref:System.Activities.WorkflowApplication> Účastník sledování je přidán jako <xref:System.Activities.WorkflowApplication> rozšíření instance. To se provádí <xref:System.Activities.Tracking.TrackingParticipant> přidáním kolekce rozšíření pro instanci WorkflowApplication.

Pro aplikaci pracovního postupu <xref:System.Activities.Tracking.EtwTrackingParticipant> můžete přidat rozšíření chování, jak je znázorněno v následujícím kódu.

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

Pracovní postup může být vystaven jako služba WCF při hostování v hostiteli služby. <xref:System.ServiceModel.Activities.WorkflowServiceHost> <xref:System.ServiceModel.Activities.WorkflowServiceHost>je specializovaná implementace služby .NET ServiceHost pro službu založenou na pracovním postupu. Tato část vysvětluje, jak nakonfigurovat sledování pro službu pracovního postupu spuštěnou [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] v aplikaci <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Je konfigurován prostřednictvím souboru Web.config (pro webovou hostovanou službu) nebo souboru App.config (pro službu hostovanou v samostatné aplikaci, například v aplikaci konzoly) zadáním chování služby nebo prostřednictvím kódu přidáním chování specifického pro sledování do <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekce pro hostitele služby.

Pro službu pracovního <xref:System.ServiceModel.WorkflowServiceHost>postupu hostovoje v aplikaci můžete přidat <xref:System.Activities.Tracking.EtwTrackingParticipant> pomocí <`behavior`> prvek v konfiguračním souboru, jak je znázorněno v následujícím příkladu.

```xml
<behaviors>
   <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
   </serviceBehaviors>
</behaviors>
```

Případně pro službu pracovního <xref:System.ServiceModel.WorkflowServiceHost>postupu hostované <xref:System.Activities.Tracking.EtwTrackingParticipant> v aplikaci můžete přidat rozšíření chování prostřednictvím kódu. Chcete-li přidat vlastní účastníksledování, vytvořte nové <xref:System.ServiceModel.ServiceHost> rozšíření chování a přidejte jej tak, jak je znázorněno v následujícím ukázkovém kódu.

> [!NOTE]
> Pokud chcete zobrazit ukázkový kód, který ukazuje, jak vytvořit vlastní prvek chování, který přidá vlastní účastníka sledování, podívejte se na [sledování](./samples/tracking.md) vzorků.

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

Účastník sledování je přidán do hostitele služby pracovního postupu jako rozšíření chování.

Tento ukázkový kód níže ukazuje, jak číst profil sledování z konfiguračního souboru.

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

Tento ukázkový kód ukazuje, jak přidat profil sledování do hostitele pracovního postupu.

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
> Další informace o profilech sledování naleznete [v informacích o profilech sledování](tracking-profiles.md).

### <a name="configuring-tracking-using-workflowinvoker"></a>Konfigurace sledování pomocí workflowinvokeru

Chcete-li nakonfigurovat sledování <xref:System.Activities.WorkflowInvoker>pracovního postupu prováděného pomocí <xref:System.Activities.WorkflowInvoker> , přidejte zprostředkovatele sledování jako rozšíření instance. Následující příklad kódu je z [ukázky vlastní sledování.](./samples/custom-tracking.md)

```csharp
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());
invoker.Extensions.Add(customTrackingParticipant);
invoker.Invoke();
```

### <a name="viewing-tracking-records-in-event-viewer"></a>Zobrazení záznamů sledování v Prohlížeči událostí

Existují dva protokoly prohlížeče událostí, které jsou zvláště zajímavé při sledování provádění služby WF - protokol Analytic a protokol ladění. Obě jsou umístěny pod uzu Microsoft&#124;Windows&#124;Application Server-Applications. Protokoly v této části obsahují události z jedné aplikace, nikoli události, které mají vliv na celý systém.

Ladění trasování události jsou zapsány do protokolu ladění. Chcete-li shromažďovat události trasování ladění wf v Prohlížeči událostí, povolte protokol ladění.

1. Pokud chcete spustit Prohlížeč událostí, klikněte na **Tlačítko Start**a potom klikněte na **Spustit.** V dialogovém okně `eventvwr`Spustit zadejte .

2. V dialogovém okně Prohlížeč událostí rozbalte uzel **Protokoly aplikací a služeb.**

3. Rozbalte uzly **Microsoft**, **Windows**a **Application Server-Applications.**

4. Klepněte pravým tlačítkem myši na uzel **Ladění** pod uzlemi **Aplikační server-aplikace** a vyberte **příkaz Povolit protokol**.

5. Spusťte aplikaci s povoleným trasování a vygenerujte události trasování.

6. Klikněte pravým tlačítkem myši na uzel **ladění** a vyberte **Aktualizovat.** Události trasování by měly být viditelné v prostředním podokně.

WF 4 poskytuje sledování účastníka, který zapisuje záznamy sledování do relace ETW (Event Tracing for Windows). Účastník sledování ETW je nakonfigurován s profilem sledování k odběru záznamů sledování. Je-li povoleno sledování, jsou e-tW emitovány záznamy sledování chyb. Události sledování ETW (mezi rozsahem 100-113) odpovídající událostem sledování vyzařovaným účastníkem sledování ETW jsou zapsány do analytického protokolu.

Chcete-li zobrazit záznamy sledování, postupujte takto.

1. Pokud chcete spustit Prohlížeč událostí, klikněte na **Tlačítko Start**a potom klikněte na **Spustit.** V dialogovém okně `eventvwr`Spustit zadejte .

2. V dialogovém okně Prohlížeč událostí rozbalte uzel **Protokoly aplikací a služeb.**

3. Rozbalte uzly **Microsoft**, **Windows**a **Application Server-Applications.**

4. Klepněte pravým tlačítkem myši na uzel **Analytická** analýza pod uzlemi **Aplikační server-aplikace** a vyberte **povolit protokol**.

5. Spusťte aplikaci s povolenou sledováním a vygenerujte záznamy sledování.

6. Klikněte pravým tlačítkem myši na uzel **Analytická** a vyberte **Aktualizovat.** Záznamy sledování by měly být viditelné v prostředním podokně.

Následující obrázek znázorňuje sledování událostí v prohlížeči událostí:

![Snímek obrazovky prohlížeče událostí zobrazující záznamy sledování](./media/configuring-tracking-for-a-workflow/tracking-event-viewer.png)

### <a name="registering-an-application-specific-provider-id"></a>Registrace ID poskytovatele specifického pro aplikaci

Pokud události je třeba zapsat do protokolu konkrétní aplikace, postupujte takto zaregistrovat manifest nového zprostředkovatele.

1. Deklarujte ID zprostředkovatele v konfiguračním souboru aplikace.

    ```xml
    <system.serviceModel>
        <diagnostics etwProviderId="2720e974-9fe9-477a-bb60-81fe3bf91eec"/>
    </system.serviceModel>
    ```

2. Zkopírujte soubor manifestu z %windir%\Microsoft.NET\Framework\\\<nejnovější verze [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]>\Microsoft.Windows.ApplicationServer.Applications.man do dočasného umístění a přejmenujte jej na Microsoft.Windows.ApplicationServer.Applications_Provider1.man

3. Změňte identifikátor GUID v souboru manifestu na nový identifikátor GUID.

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" />
    ```

4. Pokud nechcete odinstalovat výchozího zprostředkovatele, změňte název zprostředkovatele.

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" />
    ```

5. Pokud jste v předchozím kroku změnili název zprostředkovatele, změňte názvy kanálů v souboru manifestu na nový název zprostředkovatele.

    ```xml
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Admin" chid="ADMIN_CHANNEL" symbol="ADMIN_CHANNEL" type="Admin" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ADMIN_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Operational" chid="OPERATIONAL_CHANNEL" symbol="OPERATIONAL_CHANNEL" type="Operational" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.OPERATIONAL_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Debug" chid="DEBUG_CHANNEL" symbol="DEBUG_CHANNEL" type="Debug" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.DEBUG_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Perf" chid="PERF_CHANNEL" symbol="PERF_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.PERF_CHANNEL.message)" />
    ```

6. Vygenerujte dll prostředku podle následujících kroků.

    1. Nainstalujte sadu Windows SDK. Sada Windows SDK obsahuje kompilátor zpráv ([mc.exe](/windows/win32/wes/message-compiler--mc-exe-)) a kompilátor prostředků ([rc.exe](/windows/win32/menurc/using-rc-the-rc-command-line-)).

    2. V příkazovém řádku sady Windows SDK spusťte program mc.exe v novém souboru manifestu.

        ```console
        mc.exe Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

    3. Spusťte soubor rc.exe v souboru prostředků generovaném v předchozím kroku.

        ```console
        rc.exe  Microsoft.Windows.ApplicationServer.Applications_Provider1.rc
        ```

    4. Vytvořte prázdný cs soubor s názvem NewProviderReg.cs.

    5. Vytvořte dll prostředku pomocí kompilátoru Jazyka C#.

        ```console
        csc /target:library /win32res:Microsoft.Windows.ApplicationServer.Applications_Provider1.res NewProviderReg.cs /out:Microsoft.Windows.ApplicationServer.Applications_Provider1.dll
        ```

    6. Změňte název dll prostředku a zprávy `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` v souboru manifestu z nového názvu dll.

        ```xml
        <provider name="Microsoft-Windows-Application Server-Applications_Provider1" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" symbol="Microsoft_Windows_ApplicationServer_ApplicationEvents" resourceFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" messageFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" />
        ```

    7. Použijte [wevtutil](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732848(v=ws.10)) k registraci manifestu.

        ```console
        wevtutil im Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

## <a name="see-also"></a>Viz také

- [Monitorování prostředků infrastruktury aplikací pro Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))
- [Monitorování aplikací pomocí prostředků infrastruktury aplikací](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))
