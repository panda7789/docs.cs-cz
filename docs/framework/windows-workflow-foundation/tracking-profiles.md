---
title: Sledování profilů
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: 9723b8fbb0bb8f24e8c9544d8bac8252b2fc763a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182731"
---
# <a name="tracking-profiles"></a>Sledování profilů

Profily sledování obsahují sledovací dotazy, které umožňují účastníkovi sledování přihlásit se k odběru událostí pracovního postupu, které jsou emitovány při změně stavu instance pracovního postupu za běhu.

## <a name="tracking-profiles"></a>Sledování profilů

Profily sledování se používají k určení informací o sledování, které jsou vydávány pro instanci pracovního postupu. Pokud není zadán žádný profil, jsou emitovány všechny události sledování. Pokud je zadán profil, budou emitovány události sledování zadané v profilu. V závislosti na požadavcích na monitorování můžete napsat profil, který je velmi obecný, který se přihlásí k malé sadě změn stavu vysoké úrovně v pracovním postupu. Naopak můžete vytvořit velmi podrobný profil, jehož výsledné události jsou dostatečně bohaté na to, aby později rekonstruovaly podrobný tok spuštění.

Sledovací profily se projevují jako elementy XML v rámci standardního konfiguračního souboru rozhraní .NET Framework nebo zadaném v kódu. Následující příklad je [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] profil sledování v konfiguračním souboru, `Started` `Completed` který umožňuje účastníkovi sledování přihlásit k odběru událostí a pracovního postupu.

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

Následující příklad ukazuje ekvivalentní profil sledování vytvořený pomocí kódu.

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

Záznamy sledování jsou filtrovány prostřednictvím režimu viditelnosti <xref:System.Activities.Tracking.ImplementationVisibility> v rámci profilu sledování pomocí atributu. Složená aktivita je aktivita nejvyšší úrovně, která obsahuje další aktivity, které tvoří jeho implementaci. Režim viditelnosti určuje sledování záznamů vyzařovaných z složených aktivit v rámci aktivity pracovního postupu, chcete-li určit, zda jsou sledovány aktivity, které tvoří implementaci. Režim viditelnosti platí na úrovni profilu sledování. Filtrování sledování záznamů pro jednotlivé aktivity v rámci pracovního postupu je řízeno dotazy v rámci profilu sledování. Další informace naleznete v části **Typy dotazů profilu sledování** v tomto dokumentu.

Dva režimy viditelnosti `implementationVisibility` určené atributem v `RootScope` `All`profilu sledování jsou a . Použití `RootScope` režimu potlačí záznamy sledování pro aktivity, které tvoří implementaci aktivity v případě, že složená aktivita není kořenem pracovního postupu. To znamená, že při aktivitě, která je implementována `implementationVisibility` pomocí jiných aktivit, je přidána do pracovního postupu a nastavena na RootScope, je sledována pouze aktivita nejvyšší úrovně v rámci této složené aktivity. Pokud je aktivita kořenem pracovního postupu, pak implementace aktivity je samotný pracovní postup a sledování záznamů jsou vydávány pro aktivity, které tvoří implementaci. Použití režimu Vše umožňuje, aby byly emitovány všechny záznamy sledování pro kořenovou aktivitu a všechny její složené aktivity.

Předpokládejme například, že *MyActivity* je složená aktivita, jejíž implementace obsahuje dvě aktivity, *Activity1* a *Activity2*. Pokud je tato aktivita přidána do pracovního `implementationVisibility` postupu `RootScope`a sledování je povoleno s profilem sledování s nastavenou na , jsou záznamy sledování emitovány pouze pro *MyActivity*. Nejsou však vyzařovány žádné záznamy pro aktivity *Activity1* a *Activity2*.

Pokud je `implementationVisibility` však atribut pro profil `All`sledování nastaven na , jsou záznamy sledování emitovány nejen pro *MyActivity*, ale také pro aktivity *Activity1* a *Activity2*.

Příznak `implementationVisibility` se vztahuje na následující typy záznamů sledování:

- ActivityStateRecord

- Záznam propagace faultpro

- CancelRequestedRecord

- ActivityScheduledRecord

> [!NOTE]
> CustomTrackingRecords vyzařované z implementace aktivity nejsou odfiltrovány implementacíVisibility nastavení.

Funkce `implementationVisibility` je určena <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> jako na sledování profilu v kódu takto:

```csharp
TrackingProfile sampleTrackingProfile = new TrackingProfile()
{
    Name = "Sample Tracking Profile",
    ImplementationVisibility = ImplementationVisibility.RootScope
};
```

Funkce `implementationVisibility` je určena <xref:System.Activities.Tracking.ImplementationVisibility.All> jako na sledování profilu v konfiguračním souboru takto:

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

Nastavení `ImplementationVisibility` na profilu sledování je volitelné. Ve výchozím nastavení je `RootScope`jeho hodnota nastavena na hodnotu . Hodnoty pro tento atribut jsou také malá a velká písmena.

### <a name="tracking-profile-query-types"></a>Sledování typů dotazů profilu

Sledování profily mají strukturu deklarativní odběrů pro sledování záznamů, které umožňují dotazů modulu runtime pracovního postupu pro záznamy sledování. Existuje několik typů dotazů, které umožňují <xref:System.Activities.Tracking.TrackingRecord> přihlásit se k odběru různých tříd objektů. Profily sledování lze zadat v konfiguraci nebo prostřednictvím kódu. Zde jsou nejběžnější typy dotazů:

- <xref:System.Activities.Tracking.WorkflowInstanceQuery>- Slouží ke sledování změn životního cyklu instance `Started` pracovního postupu, jako jsou dříve demonstrované a `Completed`. <xref:System.Activities.Tracking.WorkflowInstanceQuery> Se používá k přihlášení k odběru následující <xref:System.Activities.Tracking.TrackingRecord> objekty:

  - <xref:System.Activities.Tracking.WorkflowInstanceRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>

  Stavy, které lze přihlásit k <xref:System.Activities.Tracking.WorkflowInstanceStates> odběru jsou určeny ve třídě.

  Konfigurace nebo kód použitý k odběru záznamů sledování `Started` na úrovni <xref:System.Activities.Tracking.WorkflowInstanceQuery> instance pracovního postupu pro stav instance pomocí uvedeného v následujícím příkladu.

  ```xml
  <workflowInstanceQueries>
      <workflowInstanceQuery>
        <states>
          <state name="Started"/>
        </states>
      </workflowInstanceQuery>
  </workflowInstanceQueries>
  ```

  ```csharp
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

- <xref:System.Activities.Tracking.ActivityStateQuery>- Slouží ke sledování změn životního cyklu aktivit, které tvoří instanci pracovního postupu. Můžete například sledovat pokaždé, když se aktivita "Odeslat e-mail" dokončí v rámci instance pracovního postupu. Tento dotaz je <xref:System.Activities.Tracking.TrackingParticipant> nezbytné pro <xref:System.Activities.Tracking.ActivityStateRecord> odběr k odběru objektů. Dostupné stavy, k jejichž <xref:System.Activities.Tracking.ActivityStates>odběru se chcete přihlásit, jsou uvedeny v .

  Konfigurace a kód použitý k odběru záznamů <xref:System.Activities.Tracking.ActivityStateQuery> sledování `SendEmailActivity` stavu aktivity, které používají pro aktivitu, jsou uvedeny v následujícím příkladu.

  ```xml
  <activityStateQueries>
    <activityStateQuery activityName="SendEmailActivity">
      <states>
        <state name="Closed"/>
      </states>
    </activityStateQuery>
  </activityStateQueries>
  ```

  ```csharp
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
  > Pokud více activityStateQuery prvky mají stejný název, pouze stavy v poslední prvek se používají v profilu sledování.

- <xref:System.Activities.Tracking.ActivityScheduledQuery>- Tento dotaz umožňuje sledovat aktivitu naplánovanou k provedení nadřazenou aktivitou. Dotaz je nezbytné <xref:System.Activities.Tracking.TrackingParticipant> pro odběr <xref:System.Activities.Tracking.ActivityScheduledRecord> k odběru objektů.

  Konfigurace a kód použitý k odběru `SendEmailActivity` záznamů souvisejících s <xref:System.Activities.Tracking.ActivityScheduledQuery> podřízenou aktivitou naplánovanou pomocí následujícího příkladu.

  ```xml
  <activityScheduledQueries>
    <activityScheduledQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />
  </activityScheduledQueries>
  ```

  ```csharp
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

- <xref:System.Activities.Tracking.FaultPropagationQuery>- Použijte ke sledování zpracování chyb, ke kterým dochází v rámci aktivity. Dotaz je nezbytné <xref:System.Activities.Tracking.TrackingParticipant> pro odběr <xref:System.Activities.Tracking.FaultPropagationRecord> k odběru objektů.

  Konfigurace a kód použitý k odběru záznamů souvisejících <xref:System.Activities.Tracking.FaultPropagationQuery> s šířením chyb pomocí je uveden v následujícím příkladu.

  ```xml
  <faultPropagationQueries>
    <faultPropagationQuery faultSourceActivityName="SendEmailActivity" faultHandlerActivityName="NotificationsFaultHandler" />
  </faultPropagationQueries>
  ```

  ```csharp
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

- <xref:System.Activities.Tracking.CancelRequestedQuery>- Slouží ke sledování požadavků na zrušení podřízené aktivity nadřazenou aktivitou. Dotaz je nezbytné <xref:System.Activities.Tracking.TrackingParticipant> pro odběr <xref:System.Activities.Tracking.CancelRequestedRecord> k odběru objektů.

  Konfigurace a kód použitý k odběru záznamů <xref:System.Activities.Tracking.CancelRequestedQuery> souvisejících se zrušením aktivity pomocí je uveden v následujícím příkladu.

  ```xml
  <cancelRequestedQueries>
    <cancelRequestedQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />
  </cancelRequestedQueries>
  ```

  ```csharp
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

- <xref:System.Activities.Tracking.CustomTrackingQuery>- Pomocí tohoto můžete sledovat události, které definujete v kódu aktivity. Dotaz je nezbytné <xref:System.Activities.Tracking.TrackingParticipant> pro odběr <xref:System.Activities.Tracking.CustomTrackingRecord> k odběru objektů.

  Konfigurace a kód použitý k přihlášení k odběru <xref:System.Activities.Tracking.CustomTrackingQuery> záznamů souvisejících s vlastními záznamy sledování pomocí je uveden v následujícím příkladu.

  ```xml
  <customTrackingQueries>
    <customTrackingQuery name="EmailAddress" activityName="SendEmailActivity" />
  </customTrackingQueries>
  ```

  ```csharp
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

- <xref:System.Activities.Tracking.BookmarkResumptionQuery>- Pomocí tohoto můžete sledovat obnovení záložky v rámci instance pracovního postupu. Tento dotaz je <xref:System.Activities.Tracking.TrackingParticipant> nezbytné pro <xref:System.Activities.Tracking.BookmarkResumptionRecord> odběr k odběru objektů.

  Konfigurace a kód použitý k odběru záznamů souvisejících s obnovením záložky pomocí <xref:System.Activities.Tracking.BookmarkResumptionQuery> je uveden v následujícím příkladu.

  ```xml
  <bookmarkResumptionQueries>
    <bookmarkResumptionQuery name="SentEmailBookmark" />
  </bookmarkResumptionQueries>
  ```

  ```csharp
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

Anotace umožňují libovolně značku sledování záznamů s hodnotou, kterou lze nakonfigurovat po čas sestavení. Můžete například chtít, aby bylo několik záznamů sledování v několika pracovních postupech označeno "Poštovním serverem" == "Poštovní server1". To umožňuje snadno vyhledat všechny záznamy s touto značkou při dotazování sledování záznamy později.

Chcete-li to provést, je do sledovacího dotazu přidána anotace, jak je znázorněno v následujícím příkladu.

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

### <a name="how-to-create-a-tracking-profile"></a>Jak vytvořit profil sledování

Prvky sledovacího dotazu se používají k vytvoření [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] profilu sledování pomocí konfiguračního souboru XML nebo kódu. Zde je příklad profilu sledování vytvořeného pomocí konfiguračního souboru.

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
> Pro wf pomocí hostitele služby Workflow je profil sledování obvykle vytvořen pomocí konfiguračního souboru. Je také možné vytvořit profil sledování s kódem pomocí sledování profilu a sledování dotazu ROZHRANÍ API.

Profil nakonfigurovaný jako konfigurační soubor XML se použije na účastníka sledování pomocí přípony chování. To je přidáno do WorkflowServiceHost, jak je popsáno v další části [Konfigurace sledování pro pracovní postup](configuring-tracking-for-a-workflow.md).

Podrobnost záznamů sledování vyzařovaných hostitelem je určena nastavením konfigurace v rámci profilu sledování. Účastník sledování se přihlásí ke sledování záznamů přidáním dotazů do profilu sledování. Chcete-li se přihlásit k odběru všech záznamů sledování,\*musí profil sledování zadat všechny sledovací dotazy pomocí " " v polích názvů v každém z dotazů.

Zde jsou některé z běžných příkladů sledování profilů.

- Profil sledování pro získání záznamů instancí pracovního postupu a chyb.

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

- Profil sledování pro získání všech vlastních záznamů sledování.

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

- [Sledování SQL](./samples/sql-tracking.md)
- [Monitorování prostředků infrastruktury aplikací pro Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))
- [Monitorování aplikací pomocí prostředků infrastruktury aplikací](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))
