---
title: Sledování profilů
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: 9217f25ba4499e7ff75020642be387aa79ba27bf
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837620"
---
# <a name="tracking-profiles"></a>Sledování profilů

Sledování profilů obsahuje sledovací dotazy, které umožňují sledování účastníka přihlásit k odběru událostí pracovního postupu, které jsou emitovány při změně stavu instance pracovního postupu za běhu.

## <a name="tracking-profiles"></a>Sledování profilů

Sledování profilů se používá k určení, které informace o sledování budou vygenerovány pro instanci pracovního postupu. Pokud není zadán žádný profil, budou vygenerovány všechny události sledování. Pokud je zadán profil, budou vygenerovány události sledování zadané v profilu. V závislosti na požadavcích na monitorování můžete napsat profil, který je velmi obecný, který se přihlásí k odběru malé sady změn stavu vysoké úrovně v pracovním postupu. Naopak můžete vytvořit velmi podrobný profil, jehož výsledné události jsou dostatečně bohatě pro pozdější vytvoření podrobného toku spuštění.

Sledovací profily se manifestují jako prvky XML v rámci standardního konfiguračního souboru .NET Framework nebo jsou zadané v kódu. V následujícím příkladu je profil sledování [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] v konfiguračním souboru, který umožňuje sledování účastníka přihlásit k odběru `Started` a `Completed` události pracovního postupu.

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

Sledování záznamů se filtruje přes režim viditelnosti v rámci profilu sledování pomocí atributu <xref:System.Activities.Tracking.ImplementationVisibility>. Složená aktivita je aktivita nejvyšší úrovně, která obsahuje další aktivity, které tvoří svou implementaci. Režim viditelnosti určuje sledování záznamů emitovaných ze složených aktivit v rámci aktivity pracovního postupu, které určují, jestli se mají sledovat aktivity, které tvoří implementaci. Režim viditelnosti se vztahuje na úroveň profilu sledování. Filtrování záznamů sledování pro jednotlivé aktivity v rámci pracovního postupu je řízeno dotazy v rámci profilu sledování. Další informace najdete v části **typy dotazů profilu sledování** v tomto dokumentu.

Dva režimy viditelnosti zadané atributem `implementationVisibility` v profilu sledování jsou `RootScope` a `All`. Použití režimu `RootScope` potlačí záznamy sledování pro aktivity, které tvoří implementaci aktivity v případě, že složená aktivita není kořenem pracovního postupu. To znamená, že když se do pracovního postupu přidá aktivita, která je implementovaná pomocí jiných aktivit, a `implementationVisibility` nastavená na RootScope, bude sledována pouze aktivita nejvyšší úrovně v rámci této složené aktivity. Pokud je aktivita kořenem pracovního postupu, pak implementace aktivity je samotný pracovní postup a záznamy sledování jsou vygenerovány pro aktivity, které tvoří implementaci. Použití režimu All povoluje generování všech záznamů sledování pro kořenovou aktivitu a všechny její složené aktivity.

Předpokládejme například, že *MyActivity* je složená aktivita, jejíž implementace obsahuje dvě aktivity, *Activity1* a *"Activity2"* . Když se tato aktivita přidá do pracovního postupu a sledování je povolené s profilem sledování s `implementationVisibility` nastavenou na `RootScope`, sledování záznamů se generuje jenom pro *MyActivity*. Pro aktivity *Activity1* a *"Activity2"* se ale negenerují žádné záznamy.

Pokud je však atribut `implementationVisibility` pro profil sledování nastaven na hodnotu `All`, pak sledování záznamů je generováno nejen pro *MyActivity*, ale také pro aktivity *Activity1* a *"Activity2"* .

Příznak `implementationVisibility` se vztahuje na následující typy záznamů sledování:

- ActivityStateRecord

- FaultPropagationRecord

- CancelRequestedRecord

- ActivityScheduledRecord

> [!NOTE]
> CustomTrackingRecords vysílaná z implementace aktivity není odfiltrována nastavením implementationVisibility.

Funkce `implementationVisibility` je určena jako <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> v profilu sledování v kódu následujícím způsobem:

```csharp
TrackingProfile sampleTrackingProfile = new TrackingProfile()
{
    Name = "Sample Tracking Profile",
    ImplementationVisibility = ImplementationVisibility.RootScope
};
```

Funkce `implementationVisibility` je určena jako <xref:System.Activities.Tracking.ImplementationVisibility.All> v profilu sledování v konfiguračním souboru následujícím způsobem:

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

Nastavení `ImplementationVisibility` v profilu sledování je volitelné. Ve výchozím nastavení je jeho hodnota nastavená na `RootScope`. Hodnoty pro tento atribut také rozlišují velká a malá písmena.

### <a name="tracking-profile-query-types"></a>Typy dotazů na profil sledování

Sledování profily mají strukturu deklarativní odběrů pro sledování záznamů, které umožňují dotazů modulu runtime pracovního postupu pro záznamy sledování. Existuje několik typů dotazů, které umožňují přihlášení k odběru různých tříd <xref:System.Activities.Tracking.TrackingRecord> objektů. Profily sledování lze zadat v konfiguraci nebo prostřednictvím kódu. Tady jsou nejběžnější typy dotazů:

- <xref:System.Activities.Tracking.WorkflowInstanceQuery> – Toto použijte ke sledování změn životního cyklu instance pracovního postupu, jako jsou dřív vykázáno `Started` a `Completed`. <xref:System.Activities.Tracking.WorkflowInstanceQuery> Se používá k přihlášení k odběru následující <xref:System.Activities.Tracking.TrackingRecord> objekty:

  - <xref:System.Activities.Tracking.WorkflowInstanceRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>

  Stavy, které lze předplatit, jsou určeny ve třídě <xref:System.Activities.Tracking.WorkflowInstanceStates>.

  V následujícím příkladu je uvedena konfigurace nebo kód, který se používá k přihlášení k odběru záznamů sledování na úrovni instance pracovního postupu pro stav `Started` instance pomocí <xref:System.Activities.Tracking.WorkflowInstanceQuery>.

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

- <xref:System.Activities.Tracking.ActivityStateQuery> – slouží ke sledování změn životního cyklu aktivit, které tvoří instanci pracovního postupu. Například můžete chtít sledovat pokaždé, když se aktivita odeslat E-Mail dokončí v instanci pracovního postupu. Tento dotaz je nutný, aby se <xref:System.Activities.Tracking.TrackingParticipant> přihlásil k odběru <xref:System.Activities.Tracking.ActivityStateRecord> objektů. Dostupné stavy pro přihlášení k odběru jsou určené v <xref:System.Activities.Tracking.ActivityStates>.

  V následujícím příkladu je uvedena konfigurace a kód, který se používá k odběru záznamů sledování stavu aktivity, které používají <xref:System.Activities.Tracking.ActivityStateQuery> pro aktivitu `SendEmailActivity`.

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
  > Pokud má více elementů activityStateQuery stejný název, budou použity pouze stavy v posledním prvku v profilu sledování.

- <xref:System.Activities.Tracking.ActivityScheduledQuery> – tento dotaz umožňuje sledovat aktivitu naplánovanou pro provádění nadřazenou aktivitou. Dotaz je nutný, aby se <xref:System.Activities.Tracking.TrackingParticipant> přihlásil k odběru <xref:System.Activities.Tracking.ActivityScheduledRecord> objektů.

  V následujícím příkladu je uvedena konfigurace a kód, který se používá k přihlášení k odběru záznamů souvisejících s `SendEmailActivity` podřízená aktivita pomocí <xref:System.Activities.Tracking.ActivityScheduledQuery>.

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

- <xref:System.Activities.Tracking.FaultPropagationQuery> – slouží ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity. Dotaz je nutný, aby se <xref:System.Activities.Tracking.TrackingParticipant> přihlásil k odběru <xref:System.Activities.Tracking.FaultPropagationRecord> objektů.

  V následujícím příkladu je uvedena konfigurace a kód, který se používá k přihlášení k odběru záznamů souvisejících s šířením chyb pomocí <xref:System.Activities.Tracking.FaultPropagationQuery>.

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

- <xref:System.Activities.Tracking.CancelRequestedQuery> – slouží ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita. Dotaz je nutný, aby se <xref:System.Activities.Tracking.TrackingParticipant> přihlásil k odběru <xref:System.Activities.Tracking.CancelRequestedRecord> objektů.

  V následujícím příkladu je uvedena konfigurace a kód, který se používá k přihlášení k odběru záznamů souvisejících s zrušením aktivity pomocí <xref:System.Activities.Tracking.CancelRequestedQuery>.

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

- <xref:System.Activities.Tracking.CustomTrackingQuery> – slouží ke sledování událostí, které definujete v aktivitách kódu. Dotaz je nutný, aby se <xref:System.Activities.Tracking.TrackingParticipant> přihlásil k odběru <xref:System.Activities.Tracking.CustomTrackingRecord> objektů.

  Konfigurace a kód, který se používá k přihlášení k odběru záznamů souvisejících s vlastními záznamy sledování pomocí <xref:System.Activities.Tracking.CustomTrackingQuery>, je znázorněno v následujícím příkladu.

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

- <xref:System.Activities.Tracking.BookmarkResumptionQuery> – slouží ke sledování obnovování záložky v rámci instance pracovního postupu. Tento dotaz je nutný, aby se <xref:System.Activities.Tracking.TrackingParticipant> přihlásil k odběru <xref:System.Activities.Tracking.BookmarkResumptionRecord> objektů.

  Konfigurace a kód, který se používá k přihlášení k odběru záznamů souvisejících s obnovením záložek pomocí <xref:System.Activities.Tracking.BookmarkResumptionQuery>, je znázorněno v následujícím příkladu.

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

Anotace umožňují libovolně značku sledování záznamů s hodnotou, kterou lze nakonfigurovat po čas sestavení. Můžete například chtít, aby několik sledovacích záznamů v několika pracovních postupech bylo označeno jako "poštovní server" = = "pošta Server1". To umožňuje snadno vyhledat všechny záznamy s touto značkou při dotazování sledování záznamy později.

K tomu je přidána poznámka do sledovacího dotazu, jak je znázorněno v následujícím příkladu.

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

Sledování prvků dotazu slouží k vytvoření profilu sledování pomocí konfiguračního souboru XML nebo kódu [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]. Tady je příklad profilu sledování vytvořeného pomocí konfiguračního souboru.

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
> V případě WF pomocí hostitele služby pracovního postupu se profil sledování obvykle vytváří pomocí konfiguračního souboru. Je také možné vytvořit profil sledování s kódem pomocí sledovacího profilu a rozhraní API pro sledování dotazů.

Profil nakonfigurovaný jako konfigurační soubor XML je použit pro sledování účastníka pomocí rozšíření chování. Tento postup je přidán k hostiteli WorkflowServiceHost, jak je popsáno v části Další [Konfigurace sledování pracovního postupu](configuring-tracking-for-a-workflow.md).

Podrobnost sledování záznamů generovaných hostitelem je určena nastavením konfigurace v rámci profilu sledování. Účastník sledování se přihlašuje k odběru sledování záznamů přidáním dotazů do profilu sledování. Chcete-li se přihlásit k odběru všech záznamů sledování, je potřeba, abyste profil sledování určili všechny sledovací dotazy pomocí "\*" v polích Název v jednotlivých dotazech.

Tady jsou některé z běžných příkladů sledování profilů.

- Sledovací profil pro získání záznamů a chyb instance pracovního postupu.

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

## <a name="see-also"></a>Viz také:

- [Sledování SQL](./samples/sql-tracking.md)
- [Monitorování Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))
- [Monitorování aplikací pomocí prostředků infrastruktury aplikace](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))
