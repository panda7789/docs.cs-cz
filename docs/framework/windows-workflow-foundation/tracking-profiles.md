---
title: "Sledování profily"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a3b1e96451eb89544d0902a1f3498263dec981a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="tracking-profiles"></a>Sledování profily
Sledování profily obsahují dotazy pro sledování, které umožňují sledování účastník přihlásit k odběru událostí pracovního postupu, které jsou vygenerované při změně stavu instance pracovního postupu za běhu.  
  
## <a name="tracking-profiles"></a>Sledování profily  
 Sledování profily se používají k určení, které informace sledování jsou vydávány pro instanci pracovního postupu. Pokud není zadán žádný profil, jsou vydávány všechny události sledování. Pokud je zadaný profil, bude vygenerované sledování událostí specifikovaný v profilu. V závislosti na vašich požadavků na monitorování, může zapisovat profil, který je velmi obecná, který jako odběratel u malého podrobný stav změn v pracovním postupu. Naopak můžete vytvořit profil velmi podrobné, jejichž výsledné události jsou dostatečně bohaté k rekonstrukci toku podrobné spuštění později.  
  
 Sledování profily projevují jako XML elementů v rámci standardní [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] konfigurační soubor nebo zadaný v kódu. V následujícím příkladu je [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] sledovacího profilu v konfiguračním souboru, který umožňuje účastníkem sledování pro přihlášení k odběru `Started` a `Completed` události pracovního postupu.  
  
```xml  
<system.serviceModel>  
    ...  
    <tracking>    
      <trackingProfile name="Sample Tracking Profile">  
        <workflow activityDefinitionId="*">  
          <workflowInstanceQueries>  
            <workflowInstanceQuery>  
              <states>  
                <state name="Started"/>  
                <state name="Completed"/>  
              </states>  
            </workflowInstanceQuery>  
          </workflowInstanceQueries>  
        </workflow>  
      </trackingProfile>          
    </profiles>  
  </tracking>  
    ...  
</system.serviceModel>  
```  
  
 Následující příklad ukazuje ekvivalentní sledování profil vytvořený pomocí kódu.  
  
```csharp  
TrackingProfile profile = new TrackingProfile()  
{  
    Name = "CustomTrackingProfile",  
    Queries =   
    {  
        new WorkflowInstanceQuery()  
        {  
            // Limit workflow instance tracking records for started and  
            // completed workflow states.  
            States = { WorkflowInstanceStates.Started, WorkflowInstanceStates.Completed },  
        }  
    }  
};  
```  
  
 Sledování záznamy jsou filtrovány pomocí režim viditelnosti v rámci profilu sledování pomocí <xref:System.Activities.Tracking.ImplementationVisibility> atribut. Složené aktivita je nejvyšší úrovně aktivity, který obsahuje další aktivity, které tvoří jeho implementace. Určuje režim viditelnosti sledování záznamy vygenerované ze složeného aktivity v rámci aktivity pracovního postupu, chcete-li určit, pokud jsou sledovány aktivity, které tvoří implementace.  Režim viditelnosti se vztahuje na sledování profilu úroveň. Filtrování sledování záznamy pro jednotlivé aktivity v rámci pracovního postupu je řízena v dotazech v rámci profilu sledování. Další informace najdete v tématu **sledování typy dotazů profil** v tomto dokumentu.  
  
 Viditelnost dva režimy určeného `implementationVisibility` atribut v profilu sledování jsou `RootScope` a `All`. Pomocí `RootScope` režimu potlačí sledování záznamy pro aktivity, které tvoří implementace aktivitu v případě, kdy složených aktivit není kořenu pracovního postupu.  To vyplývá, že při přidání aktivitu, která je implementovaná pomocí jiné aktivity do pracovního postupu a `implementationVisibility` nastavení RootScope, je sledovat pouze nejvyšší úrovně aktivity v rámci složené aktivity. Pokud aktivita je kořenu pracovního postupu, je implementace aktivity pracovního postupu pro aktivity, které tvoří implementace jsou vygenerované samostatně a sledování záznamů. Pomocí všechny režimu umožňuje všechny záznamy sledování pro vypuštění kořenové aktivity a všechny její složené aktivity.  
  
 Předpokládejme například, *MyActivity* složené aktivita, jejíž implementace obsahuje dvě aktivity *aktivity "activity1"* a *"activity2"*.  Pokud tato aktivita se přidá do pracovního postupu a sledování je povolená s profil sledování s `implementationVisibility` nastavena na `RootScope`, záznamy o sledování jsou vygenerované pouze pro *MyActivity*.  Však nejsou žádné záznamy vygenerované pro aktivity *aktivity "activity1"* a *"activity2"*.  
  
 Ale pokud `implementationVisisbility` atribut profil sledování je nastavený na `All`, pak sledování záznamy jsou vygenerované nejen pro *MyActivity*, ale také pro aktivity *aktivity "activity1"* a  *"Activity2"*.  
  
 `implementationVisibility` Příznak platí pro následující typy záznamů sledování:  
  
-   ActivityStateRecord  
  
-   FaultPropagationRecord  
  
-   CancelRequestedRecord  
  
-   ActivityScheduledRecord  
  
> [!NOTE]
>  CustomTrackingRecords vygenerované z aktivity implementace nejsou vyfiltrovány implementationVisibility nastavení.  
  
 `implementationVisibility` Funkce je zadán jako <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> na sledování profilu v kódu následujícím způsobem:  
  
```  
TrackingProfile sampleTrackingProfile = new TrackingProfile()  
{  
    Name = "Sample Tracking Profile",  
    ImplementationVisibility = ImplementationVisibility.RootScope  
};  
```  
  
 `implementationVisibility` Funkce je zadán jako <xref:System.Activities.Tracking.ImplementationVisibility.All> profil sledování v konfiguraci souboru následujícím způsobem:  
  
```xml  
<tracking>  
      <profiles>  
        <trackingProfile name="Shipping Monitoring" implementationVisibility="All">  
          <workflow activityDefinitionId="*">  
...  
         </workflow>  
        </trackingProfile>  
      </profiles>  
</tracking>  
```  
  
 `ImplementationVisibility` Nastavení v profilu sledování je volitelné. Ve výchozím nastavení, jeho hodnota nastavena na `RootScope`. Hodnoty pro tento atribut jsou také malá a velká písmena.  
  
### <a name="tracking-profile-query-types"></a>Typy dotazů profil sledování  
 Sledování profily mají strukturu deklarativní odběrů pro sledování záznamů, které umožňují dotazů modulu runtime pracovního postupu pro záznamy sledování. Existuje několik typů dotazu, které umožňují přihlášení k odběru pro různé třídy <xref:System.Activities.Tracking.TrackingRecord> objekty. Sledování profilů může být určený v konfiguraci nebo prostřednictvím kódu. Zde jsou nejčastější typy dotazů:  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceQuery>-Použít toto sledování změn životní cyklus instance pracovního postupu jako dříve ukázán `Started` a `Completed`. <xref:System.Activities.Tracking.WorkflowInstanceQuery> Se používá k přihlášení k odběru následující <xref:System.Activities.Tracking.TrackingRecord> objekty:  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
     Stavy, které se můžete přihlásit k odběru jsou určené v <xref:System.Activities.Tracking.WorkflowInstanceStates> třídy.  
  
     Konfigurace nebo kód používaný k přihlášení k odběru na úrovni instance sledování záznamů pro pracovní postup `Started` instance stavu pomocí <xref:System.Activities.Tracking.WorkflowInstanceQuery> je znázorněno v následujícím příkladu.  
  
    ```xml  
    <workflowInstanceQueries>  
        <workflowInstanceQuery>  
          <states>  
            <state name="Started"/>  
          </states>  
        </workflowInstanceQuery>  
    </workflowInstanceQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =   
        {  
            new WorkflowInstanceQuery()  
            {  
                States = { WorkflowInstanceStates.Started}                                                                     
            }  
        }  
    };  
    ```  
  
-   <xref:System.Activities.Tracking.ActivityStateQuery>-Použijte ke sledování změn životní cyklus aktivity, které tvoří instanci pracovního postupu. Například můžete udržovat přehled o každém dokončení aktivity "Odeslat E-Mail" v rámci instance pracovního postupu. Je nezbytné pro tento dotaz <xref:System.Activities.Tracking.TrackingParticipant> přihlásit k odběru <xref:System.Activities.Tracking.ActivityStateRecord> objekty. Dostupné stavy pro přihlášení k odběru jsou určené v <xref:System.Activities.Tracking.ActivityStates>.  
  
     Konfigurace a kód používaný k přihlášení k odběru záznamy sledování stavu aktivity, které používají <xref:System.Activities.Tracking.ActivityStateQuery> pro `SendEmailActivity` aktivity je znázorněno v následujícím příkladu.  
  
    ```xml  
    <activityStateQueries>  
      <activityStateQuery activityName="SendEmailActivity">  
        <states>  
          <state name="Closed"/>  
        </states>  
      </activityStateQuery>  
    </activityStateQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =  
        {  
            new ActivityStateQuery()  
            {                              
                ActivityName = "SendEmailActivity",  
                States = { ActivityStates.Closed }  
            }  
        }  
    };  
    ```  
  
    > [!NOTE]
    >  Pokud více elementů activityStateQuery mají stejný název, se používají pouze stavů v posledním elementem v profilu sledování.  
  
-   <xref:System.Activities.Tracking.ActivityScheduledQuery>-Tento dotaz umožňuje sledovat aktivity naplánovaných pro spuštění pomocí nadřazené aktivity. Je nezbytné pro dotaz <xref:System.Activities.Tracking.TrackingParticipant> přihlásit k odběru <xref:System.Activities.Tracking.ActivityScheduledRecord> objekty.  
  
     Konfigurace a kód používaný k přihlášení k odběru záznamy související s `SendEmailActivity` podřízené aktivity naplánován pomocí <xref:System.Activities.Tracking.ActivityScheduledQuery> je znázorněno v následujícím příkladu.  
  
    ```xml  
    <activityScheduledQueries>  
      <activityScheduledQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />  
     </activityScheduledQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =   
        {  
            new ActivityScheduledQuery()  
            {  
                ActivityName = "ProcessNotificationsActivity",  
                ChildActivityName = "SendEmailActivity"  
            }  
        }  
    };  
    ```  
  
-   <xref:System.Activities.Tracking.FaultPropagationQuery>-Použijte ke sledování ošetření chyb, které se vyskytují v aktivitě. Je nezbytné pro dotaz <xref:System.Activities.Tracking.TrackingParticipant> přihlásit k odběru <xref:System.Activities.Tracking.FaultPropagationRecord> objekty.  
  
     Konfigurace a kód používaný k přihlášení k odběru záznamy související s použitím šíření k selhání <xref:System.Activities.Tracking.FaultPropagationQuery> je znázorněno v následujícím příkladu.  
  
    ```xml  
    <faultPropagationQueries>  
      <faultPropagationQuery faultSourceActivityName="SendEmailActivity" faultHandlerActivityName="NotificationsFaultHandler" />  
    </faultPropagationQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =  
        {  
            new FaultPropagationQuery()  
            {  
                FaultSourceActivityName = "SendEmailActivity",  
                FaultHandlerActivityName = "NotificationsFaultHandler"  
            }  
        }  
    };  
    ```  
  
-   <xref:System.Activities.Tracking.CancelRequestedQuery>-Použijte ke sledování žádosti o zrušení podřízené aktivity podle nadřazené aktivity. Je nezbytné pro dotaz <xref:System.Activities.Tracking.TrackingParticipant> přihlásit k odběru <xref:System.Activities.Tracking.CancelRequestedRecord> objekty.  
  
     Konfigurace a kód používaný k přihlášení k odběru záznamy související s aktivity zrušení pomocí <xref:System.Activities.Tracking.CancelRequestedQuery> je znázorněno v následujícím příkladu.  
  
    ```xml  
    <cancelRequestedQueries>  
      <cancelRequestedQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />  
    </cancelRequestedQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =   
        {  
            new CancelRequestedQuery()  
            {  
                ActivityName = "ProcessNotificationsActivity",  
                ChildActivityName = "SendEmailActivity"  
            }  
        }  
    };  
    ```  
  
-   <xref:System.Activities.Tracking.CustomTrackingQuery>-Použijte ke sledování událostí, které definujete ve vašich aktivit kódu. Je nezbytné pro dotaz <xref:System.Activities.Tracking.TrackingParticipant> přihlásit k odběru <xref:System.Activities.Tracking.CustomTrackingRecord> objekty.  
  
     Konfigurace a kód používaný k přihlášení k odběru záznamy související s vlastní sledování záznamů pomocí <xref:System.Activities.Tracking.CustomTrackingQuery> je znázorněno v následujícím příkladu.  
  
    ```xml  
    <customTrackingQueries>  
      <customTrackingQuery name="EmailAddress" activityName="SendEmailActivity" />  
    </customTrackingQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =   
        {  
            new CustomTrackingQuery()   
            {  
                Name = "EmailAddress",  
                ActivityName = "SendEmailActivity"  
            }  
        }  
    };  
    ```  
  
-   <xref:System.Activities.Tracking.BookmarkResumptionQuery>-Použijte ke sledování obnovení záložky v rámci instance pracovního postupu. Je nezbytné pro tento dotaz <xref:System.Activities.Tracking.TrackingParticipant> přihlásit k odběru <xref:System.Activities.Tracking.BookmarkResumptionRecord> objekty.  
  
     Konfigurace a kód používaný k přihlášení k odběru záznamy týkající se použití záložek obnovení <xref:System.Activities.Tracking.BookmarkResumptionQuery> je znázorněno v následujícím příkladu.  
  
    ```xml  
    <bookmarkResumptionQueries>  
      <bookmarkResumptionQuery name="SentEmailBookmark" />  
    </bookmarkResumptionQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =   
        {  
            new BookmarkResumptionQuery()  
            {  
                Name = "sentEmailBookmark"  
            }  
        }  
    };  
    ```  
  
### <a name="annotations"></a>Poznámky  
 Anotace umožňují libovolně značku sledování záznamů s hodnotou, kterou lze nakonfigurovat po čas sestavení. Například můžete několik záznamů sledování napříč několika pracovní postupy pro označené "Poštovní Server" == "E-mailu Server1". To umožňuje snadno vyhledat všechny záznamy s touto značkou při dotazování sledování záznamy později.  
  
 K tomu poznámky přidat do dotazu sledování, jak je znázorněno v následujícím příkladu.  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <annotations>  
    <annotation name="MailServer" value="Mail Server1"/>  
  </annotations>  
</activityStateQuery>  
```  
  
### <a name="how-to-create-a-tracking-profile"></a>Postup vytvoření profilu sledování  
 Sledování dotazu elementy slouží k vytvoření profilu sledování buď pomocí konfiguračního souboru XML nebo [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]kódu.  Tady je příklad profilu sledování vytvořené pomocí konfiguračního souboru.  
  
```xml  
<system.serviceModel>  
  <tracking>  
    <profiles>  
      <trackingProfile name="Sample Tracking Profile ">  
        <workflow activityDefinitionId="*">  
          <!--Specify the tracking profile query elements to subscribe for tracking records-->  
        </workflow>  
      </trackingProfile>  
    </profiles>  
  </tracking>  
</system.serviceModel>  
```  
  
> [!WARNING]
>  Pracovního postupu pomocí hostitele služby pracovního postupu se profil sledování obvykle vytvoří pomocí konfiguračního souboru. Je také možné vytvořit profil sledování kódem pomocí profilu sledování a sledování rozhraní API dotazu.  
  
 Profil nakonfigurovaný jako konfigurační soubor XML se použije ke členovi sledování pomocí rozšíření chování. To se přidá hostitele služby pracovního postupu, jak je popsáno v části novější [konfigurace sledování pro pracovní postup](../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
 Podrobností Sledování záznamy vygenerované hostitelem je určen podle nastavení konfigurace v rámci profilu sledování. Sledování účastník jako odběratel u sledování záznamů přidáním dotazy do profilu sledování. K odběru všech záznamů o sledování, musí určovat všechny dotazy sledování pomocí profilu sledování "*" v polích pro název v jednotlivých dotazů.  
  
 Zde jsou některé z běžných příkladů sledování profily.  
  
-   Profil sledování získat záznamy instance pracovního postupu a chyb.  
  
```xml  
<trackingProfile name="Instance and Fault Records">  
  <workflow activityDefinitionId="*">  
    <workflowInstanceQueries>  
      <workflowInstanceQuery>  
        <states>  
          <state name="*" />  
        </states>  
      </workflowInstanceQuery>  
    </workflowInstanceQueries>  
    <activityStateQueries>  
      <activityStateQuery activityName="*">  
        <states>  
          <state name="Faulted"/>  
        </states>  
      </activityStateQuery>  
    </activityStateQueries>  
  </workflow>  
</trackingProfile>  
```  
  
1.  Profil sledování získat všechny záznamy vlastní sledování.  
  
```xml  
<trackingProfile name="Instance_And_Custom_Records">  
  <workflow activityDefinitionId="*">  
    <customTrackingQueries>  
      <customTrackingQuery name="*" activityName="*" />  
    </customTrackingQueries>  
  </workflow>  
</trackingProfile>  
```  
  
## <a name="see-also"></a>Viz také  
 [Sledování SQL](../../../docs/framework/windows-workflow-foundation/samples/sql-tracking.md)  
 [Windows Server App Fabric monitorování](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitorování aplikací pomocí App Fabric](http://go.microsoft.com/fwlink/?LinkId=201275)
