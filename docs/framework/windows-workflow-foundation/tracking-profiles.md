---
title: Sledování profily
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: 6651b79a474125f57c1cad773ae858dc7654d58a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43396987"
---
# <a name="tracking-profiles"></a>Sledování profily
Sledování profily obsahuje sledování dotazy, které umožňují sledování účastník přihlásit k odběru události pracovních postupů, které jsou emitovány při změně stavu instance pracovního postupu za běhu.  
  
## <a name="tracking-profiles"></a>Sledování profily  
 Sledování profily se používají k určení, jaké informace o sledování je vygenerován pro instanci pracovního postupu. Pokud není zadán žádný profil, jsou emitovány všechny události sledování. Pokud je zadaný profil, bude vygenerován sledování událostí specifikovaný v profilu. V závislosti na vašich požadavků na monitorování napíšete profilu, který je velmi obecná, který se přihlásí k odběru malou sadu změn stavu vysoké úrovně v pracovním postupu. Naopak můžete vytvořit profil velmi podrobné, jehož výsledné události jsou bohaté dostatečně k rekonstrukci podrobné provádění toku později.  
  
 Sledování profily projevují jako XML elementů v rámci standardní [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] konfigurační soubor nebo zadaný v kódu. V následujícím příkladu je [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] profil sledování tracking profile v konfiguračním souboru, který umožňuje sledování účastník přihlásit k odběru `Started` a `Completed` události pracovního postupu.  
  
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
  
 Následující příklad ukazuje ekvivalent sledování profil se vytvořil pomocí kódu.  
  
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
  
 Sledování záznamy jsou filtrovány pomocí režim viditelnosti v rámci profilu sledování používání <xref:System.Activities.Tracking.ImplementationVisibility> atribut. Složená aktivita je nejvyšší úrovně aktivity, který obsahuje další aktivity, které tvoří jeho implementace. Určuje režim viditelnosti záznamů sledování vyzařováno složených aktivit v rámci aktivity pracovního postupu, chcete-li určit, pokud jsou sledovány aktivity, které tvoří implementaci.  Režim viditelnosti se vztahuje na sledování profil úroveň. Filtrování sledování záznamů pro jednotlivé aktivity v pracovním postupu je řízen pomocí dotazů v rámci profilu sledování. Další informace najdete v tématu **sledování typů profilů dotazu** části v tomto dokumentu.  
  
 Viditelnost dva režimy určené `implementationVisibility` atributu v profilu sledování `RootScope` a `All`. Použití `RootScope` režimu potlačí na sledování záznamy aktivity, které tvoří implementaci aktivity v případě, kdy složené aktivity není kořenem pracovního postupu.  Z toho vyplývá, že když aktivita, která je implementována pomocí další aktivity se přidá do pracovního postupu a `implementationVisibility` nastavíte RootScope, jsou sledovány pouze nejvyšší úrovně aktivity v rámci složené aktivity. Pokud aktivita je kořenového pracovního postupu, je provádění aktivity pracovního postupu pro aktivity, které tvoří implementaci jsou emitovány samostatně a sledování záznamů. Všechny režimu povoluje všechny záznamy sledování, aby byly vypuštěny kořenové aktivity a všechny složené aktivity.  
  
 Předpokládejme například, že *MyActivity* je složená aktivita, jejíž implementace obsahuje dvě aktivity *aktivity "activity1"* a *"activity2"*.  Když je tato aktivita přidána do pracovního postupu a je povoleno sledování pomocí profilu sledování s `implementationVisibility` nastavena na `RootScope`, jsou vydávány sledování záznamů pouze pro *MyActivity*.  Nicméně jsou emitovány žádné záznamy pro aktivity *aktivity "activity1"* a *"activity2"*.  
  
 Ale pokud `implementationVisisbility` atribut profilu sledování je nastavený na `All`, pak jsou vydávány sledování záznamů nejen *MyActivity*, ale také pro aktivity *aktivity "activity1"* a  *"Activity2"*.  
  
 `implementationVisibility` Příznak platí pro následující typy záznamů sledování:  
  
-   ActivityStateRecord  
  
-   FaultPropagationRecord  
  
-   CancelRequestedRecord  
  
-   ActivityScheduledRecord  
  
> [!NOTE]
>  Nastavením implementationVisibility nejsou odfiltrovat CustomTrackingRecords vyzařováno implementaci aktivity.  
  
 `implementationVisibility` Funkce je zadán jako <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> na sledování profil v kódu následujícím způsobem:  
  
```  
TrackingProfile sampleTrackingProfile = new TrackingProfile()  
{  
    Name = "Sample Tracking Profile",  
    ImplementationVisibility = ImplementationVisibility.RootScope  
};  
```  
  
 `implementationVisibility` Funkce je zadán jako <xref:System.Activities.Tracking.ImplementationVisibility.All> profilu sledování v konfiguraci souboru následujícím způsobem:  
  
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
  
 `ImplementationVisibility` Je volitelné nastavení v profilu sledování. Ve výchozím nastavení, jeho hodnota nastavená na `RootScope`. Hodnoty pro tento atribut se také malá a velká písmena.  
  
### <a name="tracking-profile-query-types"></a>Typy dotazů profilu sledování  
 Sledování profily mají strukturu deklarativní odběrů pro sledování záznamů, které umožňují dotazů modulu runtime pracovního postupu pro záznamy sledování. Existuje několik typů dotazu, které umožňují předplatit různé třídy <xref:System.Activities.Tracking.TrackingRecord> objekty. Sledování profily se dá nastavit v konfiguraci nebo prostřednictvím kódu. Tady jsou nejčastější typy dotazů:  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceQuery> – Můžete tak sledovat změny životního cyklu instance pracovního postupu jako dříve-jsme vám ukázali `Started` a `Completed`. <xref:System.Activities.Tracking.WorkflowInstanceQuery> Se používá k přihlášení k odběru následující <xref:System.Activities.Tracking.TrackingRecord> objekty:  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
     Stavy, které se můžete přihlásit k odběru jsou uvedeny v <xref:System.Activities.Tracking.WorkflowInstanceStates> třídy.  
  
     Konfigurace nebo kódu používá k odběru na úrovni instance sledování záznamů pro pracovní postup `Started` pomocí stav instance <xref:System.Activities.Tracking.WorkflowInstanceQuery> je znázorněno v následujícím příkladu.  
  
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
  
-   <xref:System.Activities.Tracking.ActivityStateQuery> – Tuto možnost použijte sledování změn životního cyklu aktivit, které tvoří instance pracovního postupu. Můžete například sledovat, pokaždé, když dokončí "Odeslat E-Mail" aktivity v rámci instance pracovního postupu. Tento dotaz je nezbytné pro <xref:System.Activities.Tracking.TrackingParticipant> přihlásit k odběru <xref:System.Activities.Tracking.ActivityStateRecord> objekty. Dostupné stavy přihlásit k odběru jsou uvedeny v <xref:System.Activities.Tracking.ActivityStates>.  
  
     Konfigurace a kód používá k registraci záznamů o sledování stavu aktivity, které používají <xref:System.Activities.Tracking.ActivityStateQuery> pro `SendEmailActivity` aktivity je znázorněno v následujícím příkladu.  
  
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
    >  Pokud více activityStateQuery elementy mají stejný název, stavy v posledním elementu se používají v profilu sledování.  
  
-   <xref:System.Activities.Tracking.ActivityScheduledQuery> – Tento dotaz můžete ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený. Dotaz, je nezbytné pro <xref:System.Activities.Tracking.TrackingParticipant> přihlásit k odběru <xref:System.Activities.Tracking.ActivityScheduledRecord> objekty.  
  
     Konfigurace a kód používaný k přihlásit k odběru záznamů související s `SendEmailActivity` podřízená aktivita naplánované pomocí <xref:System.Activities.Tracking.ActivityScheduledQuery> je znázorněno v následujícím příkladu.  
  
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
  
-   <xref:System.Activities.Tracking.FaultPropagationQuery> – Použijte to ke sledování zpracování chyb, ke kterým dochází v rámci aktivity. Dotaz, je nezbytné pro <xref:System.Activities.Tracking.TrackingParticipant> přihlásit k odběru <xref:System.Activities.Tracking.FaultPropagationRecord> objekty.  
  
     Konfigurace a kód používaný k přihlásit k odběru záznamů související s pomocí šíření chyb <xref:System.Activities.Tracking.FaultPropagationQuery> je znázorněno v následujícím příkladu.  
  
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
  
-   <xref:System.Activities.Tracking.CancelRequestedQuery> – Použijte to ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita. Dotaz, je nezbytné pro <xref:System.Activities.Tracking.TrackingParticipant> přihlásit k odběru <xref:System.Activities.Tracking.CancelRequestedRecord> objekty.  
  
     Konfigurace a kód používaný k přihlásit k odběru záznamů týkající se použití aktivity zrušení <xref:System.Activities.Tracking.CancelRequestedQuery> je znázorněno v následujícím příkladu.  
  
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
  
-   <xref:System.Activities.Tracking.CustomTrackingQuery> – Tuto možnost použijte sledování událostí, které definujete své kód aktivity. Dotaz, je nezbytné pro <xref:System.Activities.Tracking.TrackingParticipant> přihlásit k odběru <xref:System.Activities.Tracking.CustomTrackingRecord> objekty.  
  
     Konfigurace a kód používaný k přihlásit k odběru záznamů související s vlastní sledování záznamů pomocí <xref:System.Activities.Tracking.CustomTrackingQuery> je znázorněno v následujícím příkladu.  
  
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
  
-   <xref:System.Activities.Tracking.BookmarkResumptionQuery> – Použijte to ke sledování obnovení záložku v instanci pracovního postupu. Tento dotaz je nezbytné pro <xref:System.Activities.Tracking.TrackingParticipant> přihlásit k odběru <xref:System.Activities.Tracking.BookmarkResumptionRecord> objekty.  
  
     Konfigurace a kód používaný k přihlásit k odběru záznamů týkající se použití obnovení záložku <xref:System.Activities.Tracking.BookmarkResumptionQuery> je znázorněno v následujícím příkladu.  
  
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
 Anotace umožňují libovolně značku sledování záznamů s hodnotou, kterou lze nakonfigurovat po čas sestavení. Například chtít několik sledování záznamů napříč několika pracovních úloh a být s klíčovým slovem "Poštovního serveru" == "Pošty Server1". To umožňuje snadno vyhledat všechny záznamy s touto značkou při dotazování sledování záznamy později.  
  
 K tomu, poznámka přidána do dotazu sledování, jak je znázorněno v následujícím příkladu.  
  
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
 Sledování elementy dotazu se používají k vytvoření profilu sledování pomocí konfiguračního souboru XML nebo [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]kódu.  Tady je příklad profilu sledování vytvořené pomocí konfiguračního souboru.  
  
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
>  WF pomocí hostitele služby pracovního postupu se profilu sledování obvykle vytvoří pomocí konfiguračního souboru. Je také možné vytvořit profil sledování s kódem pomocí profilu sledování a sledování rozhraní API pro dotazy.  
  
 Profil nakonfigurovaný jako soubor XML konfigurace platí pro sledování účastníka pomocí chování rozšíření. Ten se přidává k hostiteli WorkflowServiceHost, jak je popsáno v další části [konfigurace sledování pracovního postupu](../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
 Úroveň podrobností na sledování záznamy, protože ho vygeneroval hostitele se určuje podle nastavení konfigurace v rámci profilu sledování. Účastník sledování přihlásí k sledování záznamů tak, že přidáte dotazy sledovacího profilu. Přihlásit k odběru všech sledování záznamů, musí určovat všechny dotazy sledování pomocí profilu sledování "*" název pole v jednotlivých dotazů.  
  
 Tady jsou některé běžné příklady sledování profilů.  
  
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
  
1.  Profil sledování získat všechny vlastní sledování záznamů.  
  
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
 [Windows Server App Fabric monitorování](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitorování aplikací pomocí App Fabric](https://go.microsoft.com/fwlink/?LinkId=201275)
