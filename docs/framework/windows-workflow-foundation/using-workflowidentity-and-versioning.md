---
title: Použití WorkflowIdentity a správy verzí
ms.date: 03/30/2017
ms.assetid: b8451735-8046-478f-912b-40870a6c0c3a
ms.openlocfilehash: 1d31739c135dbb518f05c40ba802c782b6817bff
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855631"
---
# <a name="using-workflowidentity-and-versioning"></a>Použití WorkflowIdentity a správy verzí

<xref:System.Activities.WorkflowIdentity>poskytuje způsob, jak můžou vývojáři aplikací pracovních postupů přidružit název a <xref:System.Version> definici pracovního postupu a pro tyto informace musí být přidružené k trvalé instanci pracovního postupu. Tyto informace o identitě mohou vývojáři aplikací pracovních postupů použít k povolení scénářů, jako je souběžné spouštění více verzí definice pracovního postupu, a poskytuje základní kámen pro jiné funkce, jako je například dynamická aktualizace. Toto téma poskytuje přehled o použití <xref:System.Activities.WorkflowIdentity> s <xref:System.Activities.WorkflowApplication> hostováním. Informace o souběžném spouštění definic pracovních postupů ve službě pracovního postupu najdete v tématu [Správa verzí vedle sebe v hostiteli WorkflowServiceHost](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md). Informace o dynamické aktualizaci najdete v tématu [Dynamická aktualizace](dynamic-update.md).

## <a name="in-this-topic"></a>V tomto tématu

- [Použití identita WorkflowIdentity](using-workflowidentity-and-versioning.md#UsingWorkflowIdentity)

  - [Souběžné spouštění pomocí identita WorkflowIdentity](using-workflowidentity-and-versioning.md#SxS)

- [Upgrade databází trvalosti .NET Framework 4 pro podporu správy verzí pracovních postupů](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)

  - [Postup upgradu schématu databáze](using-workflowidentity-and-versioning.md#ToUpgrade)

## <a name="using-workflowidentity"></a><a name="UsingWorkflowIdentity"></a>Použití identita WorkflowIdentity

Chcete-li použít <xref:System.Activities.WorkflowIdentity> , vytvořte instanci, nakonfigurujte ji a přidružte ji k <xref:System.Activities.WorkflowApplication> instanci. <xref:System.Activities.WorkflowIdentity>Instance obsahuje tři identifikační části informací. <xref:System.Activities.WorkflowIdentity.Name%2A>a <xref:System.Activities.WorkflowIdentity.Version%2A> musí obsahovat název a <xref:System.Version> a a a <xref:System.Activities.WorkflowIdentity.Package%2A> je nepovinné a lze jej použít k určení dalšího řetězce obsahujícího informace, jako je například název sestavení nebo jiné požadované informace. Objekt <xref:System.Activities.WorkflowIdentity> je jedinečný, pokud se některá z jeho tří vlastností liší od jiného <xref:System.Activities.WorkflowIdentity> .

> [!IMPORTANT]
> <xref:System.Activities.WorkflowIdentity>By neměl obsahovat žádné identifikovatelné osobní údaje (PII). Informace o <xref:System.Activities.WorkflowIdentity> použití pro vytvoření instance jsou generovány do všech nakonfigurovaných služeb sledování v několika různých místech životního cyklu aktivity modulem runtime. Sledování WF nemá žádný mechanismus pro skrytí PII (citlivých uživatelských dat). <xref:System.Activities.WorkflowIdentity>Instance by proto neměla obsahovat žádná data PII, protože bude vygenerována modulem runtime ve sledování záznamů a může být viditelná pro kohokoli s přístupem k zobrazení záznamů sledování.

V následujícím příkladu <xref:System.Activities.WorkflowIdentity> je vytvořen a přidružen k instanci pracovního postupu vytvořeného pomocí `MortgageWorkflow` definice pracovního postupu.

```csharp
WorkflowIdentity identityV1 = new WorkflowIdentity
{
    Name = "MortgageWorkflow v1",
    Version = new Version(1, 0, 0, 0)
};

WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Run the workflow.
wfApp.Run();
```

Po opětovném načtení a obnovení pracovního postupu, <xref:System.Activities.WorkflowIdentity> který je nakonfigurován tak, aby odpovídal <xref:System.Activities.WorkflowIdentity> instanci trvalého pracovního postupu, je nutné použít.

```csharp
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Load the workflow.
wfApp.Load(instanceId);

// Resume the workflow...
```

Pokud se <xref:System.Activities.WorkflowIdentity> použití při opětovném načtení instance pracovního postupu neshoduje s trvalým <xref:System.Activities.WorkflowIdentity> , <xref:System.Activities.VersionMismatchException> je vyvolána výjimka. V následujícím příkladu je proveden pokus o načtení u `MortgageWorkflow` instance, která byla trvala v předchozím příkladu. Tento pokus o načtení se provádí pomocí <xref:System.Activities.WorkflowIdentity> nakonfigurovaného pro novější verzi pracovního postupu hypotéky, která neodpovídá trvalé instanci.

```csharp
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow_v2(), identityV2);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Attempt to load the workflow instance.
wfApp.Load(instanceId);

// Resume the workflow...
```

Po spuštění předchozího kódu <xref:System.Activities.VersionMismatchException> je vyvolána následující výjimka.

```output
The WorkflowIdentity ('MortgageWorkflow v1; Version=1.0.0.0') of the loaded instance does not match the WorkflowIdentity ('MortgageWorkflow v2; Version=2.0.0.0') of the provided workflow definition. The instance can be loaded using a different definition, or updated using Dynamic Update.
```

### <a name="side-by-side-execution-using-workflowidentity"></a><a name="SxS"></a>Souběžné spouštění pomocí identita WorkflowIdentity

<xref:System.Activities.WorkflowIdentity>dá se použít k usnadnění provádění několika verzí pracovního postupu vedle sebe. Jedním z běžných scénářů je změna obchodních požadavků na dlouhodobě běžící pracovní postup. V případě, že je nasazena aktualizovaná verze, může být spuštěno mnoho instancí pracovního postupu. Hostitelská aplikace se dá nakonfigurovat tak, aby při spuštění nových instancí používala aktualizovanou definici pracovního postupu, a je zodpovědností, že hostitelská aplikace poskytne správnou definici pracovního postupu při obnovení instancí. <xref:System.Activities.WorkflowIdentity>dá se použít k identifikaci a dodávání odpovídajícího definice pracovního postupu při obnovování instancí pracovního postupu.

Pro načtení <xref:System.Activities.WorkflowIdentity> trvalé instance pracovního postupu <xref:System.Activities.WorkflowApplication.GetInstance%2A> je použita metoda. <xref:System.Activities.WorkflowApplication.GetInstance%2A>Metoda převezme <xref:System.Activities.WorkflowApplication.Id%2A> instanci trvalého pracovního postupu a <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> , která obsahuje trvalou instanci a vrátí <xref:System.Activities.WorkflowApplicationInstance> . <xref:System.Activities.WorkflowApplicationInstance>Obsahuje informace o trvalé instanci pracovního postupu, včetně jejího přidruženého <xref:System.Activities.WorkflowIdentity> . Tuto přidruženou adresu <xref:System.Activities.WorkflowIdentity> může hostitel použít k poskytnutí správné definice pracovního postupu při načítání a obnovování instance pracovního postupu.

> [!NOTE]
> Hodnota null <xref:System.Activities.WorkflowIdentity> je platná a může být použita hostitelem k mapování instancí, které byly trvale nastaveny bez přidružení <xref:System.Activities.WorkflowIdentity> ke správné definici pracovního postupu. K tomuto scénáři může dojít, když aplikace pracovního postupu nebyla původně zapsána pomocí správy verzí pracovních postupů nebo při upgradu aplikace z .NET Framework 4. Další informace najdete v tématu [upgrade databáze .NET Framework 4 Persistence pro podporu správy verzí pracovních postupů](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).

V následujícím příkladu `Dictionary<WorkflowIdentity, Activity>` se používá k přidružení instancí k <xref:System.Activities.WorkflowIdentity> odpovídajícím definicím pracovního postupu a pracovní postup se spustí pomocí `MortgageWorkflow` definice pracovního postupu, která je přidružena k `identityV1` <xref:System.Activities.WorkflowIdentity> .

```csharp
WorkflowIdentity identityV1 = new WorkflowIdentity
{
    Name = "MortgageWorkflow v1",
    Version = new Version(1, 0, 0, 0)
};

WorkflowIdentity identityV2 = new WorkflowIdentity
{
    Name = "MortgageWorkflow v2",
    Version = new Version(2, 0, 0, 0)
};

Dictionary<WorkflowIdentity, Activity> WorkflowVersionMap = new Dictionary<WorkflowIdentity, Activity>();
WorkflowVersionMap.Add(identityV1, new MortgageWorkflow());
WorkflowVersionMap.Add(identityV2, new MortgageWorkflow_v2());

WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Run the workflow.
wfApp.Run();
```

V následujícím příkladu jsou informace o trvalé instanci pracovního postupu z předchozího příkladu načteny voláním <xref:System.Activities.WorkflowApplication.GetInstance%2A> a trvalé <xref:System.Activities.WorkflowIdentity> informace jsou použity k načtení odpovídajícího definice pracovního postupu. Tyto informace slouží ke konfiguraci <xref:System.Activities.WorkflowApplication> a následnému načtení pracovního postupu. Všimněte si, že vzhledem k tomu, že <xref:System.Activities.WorkflowApplication.Load%2A> přetížení, které přijímá, je použito <xref:System.Activities.WorkflowApplicationInstance> , <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> které bylo konfigurováno v rozhraní, <xref:System.Activities.WorkflowApplicationInstance> <xref:System.Activities.WorkflowApplication> a proto jeho <xref:System.Activities.WorkflowApplication.InstanceStore%2A> vlastnost není nutné konfigurovat.

> [!NOTE]
> Pokud <xref:System.Activities.WorkflowApplication.InstanceStore%2A> je vlastnost nastavena, musí být nastavena se stejnou instancí, jakou <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> používá <xref:System.Activities.WorkflowApplicationInstance> nebo else, <xref:System.ArgumentException> bude vyvolána s následující zprávou: `The instance is configured with a different InstanceStore than this WorkflowApplication.` .

```csharp
// Get the WorkflowApplicationInstance of the desired workflow from the specified
// SqlWorkflowInstanceStore.
WorkflowApplicationInstance instance = WorkflowApplication.GetInstance(instanceId, store);

// Use the persisted WorkflowIdentity to retrieve the correct workflow
// definition from the dictionary.
Activity definition = WorkflowVersionMap[instance.DefinitionIdentity];

WorkflowApplication wfApp = new WorkflowApplication(definition, instance.DefinitionIdentity);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Load the persisted workflow instance.
wfApp.Load(instance);

// Resume the workflow...
```

## <a name="upgrading-net-framework-4-persistence-databases-to-support-workflow-versioning"></a><a name="UpdatingWF4PersistenceDatabases"></a>Upgrade databází trvalosti .NET Framework 4 pro podporu správy verzí pracovních postupů

K upgradu databáze trvalosti vytvořené pomocí databázových skriptů .NET Framework 4 se poskytuje skript databáze SqlWorkflowInstanceStoreSchemaUpgrade. SQL. Tento skript aktualizuje databáze nástroje tak, aby podporovaly nové možnosti správy verzí, zavedené v .NET Framework 4,5. Všechny trvalé instance pracovního postupu v databázích mají výchozí hodnoty pro správu verzí a můžou se pak zúčastnit souběžného spouštění a dynamické aktualizace.

Pokusí-li se aplikace pracovního postupu .NET Framework 4,5 nějaké operace trvalého uložení, které používají nové funkce správy verzí na trvalé databázi, která nebyla upgradována pomocí zadaného skriptu, <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> je vyvolána zpráva podobná následující zprávě.

```output
The SqlWorkflowInstanceStore has a database version of '4.0.0.0'. InstancePersistenceCommand 'System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand' cannot be run against this database version.  Please upgrade the database to '4.5.0.0'.
```

### <a name="to-upgrade-the-database-schema"></a><a name="ToUpgrade"></a>Postup upgradu schématu databáze

1. Otevřete SQL Server Management Studio a připojte se k serveru databáze trvalosti, například **.\SQLEXPRESS**.

2. V nabídce **soubor** vyberte **otevřít**, **soubor** . Přejděte do následující složky:`C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`

3. Vyberte **SqlWorkflowInstanceStoreSchemaUpgrade. SQL** a klikněte na **otevřít**.

4. V rozevíracím seznamu **dostupné databáze** vyberte název databáze trvalosti.

5. V nabídce **dotaz** klikněte na příkaz **Spustit** .

Po dokončení dotazu se aktualizuje schéma databáze a v případě potřeby můžete zobrazit výchozí identitu pracovního postupu, která byla přiřazena k trvale vytvořeným instancím pracovních postupů. Rozbalte databázi Persistence v uzlu **databáze** **Průzkumník objektů**a poté rozbalte uzel **zobrazení** . Klikněte pravým tlačítkem na **System. Activities. DurableInstancing. Instances** a zvolte **Vybrat prvních 1000 řádků**. Posuňte se na konec sloupců a Všimněte si, že do zobrazení bylo přidáno šest dalších sloupců: **identity**, **IdentityPackage**, **Build**, **hlavní_verze**, **podverze**a **Revize**. Všechny trvalé pracovní postupy budou mít pro tato pole hodnotu **null** , která představuje identitu pracovního postupu s hodnotou null.
