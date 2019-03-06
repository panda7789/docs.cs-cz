---
title: Použití WorkflowIdentity a správy verzí
ms.date: 03/30/2017
ms.assetid: b8451735-8046-478f-912b-40870a6c0c3a
ms.openlocfilehash: ad1d3385801b451795c6be321094851339a55f81
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373423"
---
# <a name="using-workflowidentity-and-versioning"></a>Použití WorkflowIdentity a správy verzí
<xref:System.Activities.WorkflowIdentity> nabízí způsob, jak pro pracovní postup přidružit název a <xref:System.Version> s definicí pracovního postupu a tyto informace k trvalé instance práce. Tyto informace identita umožňuje vývojáři aplikace pracovního postupu povolení scénářů, jako je vedle sebe spuštění více verzí modulu definice pracovního postupu a poskytuje základní kámen pro další funkce, jako je například dynamická aktualizace. Toto téma obsahuje přehled používání <xref:System.Activities.WorkflowIdentity> s <xref:System.Activities.WorkflowApplication> hostování. Informace o spuštění vedle sebe definice pracovního postupu ve službě pracovního postupu v tématu [správy verzí vedle sebe ve třídě WorkflowServiceHost](../../../docs/framework/wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md). Informace o dynamické aktualizace, naleznete v tématu [dynamická aktualizace](../../../docs/framework/windows-workflow-foundation/dynamic-update.md).  
  
## <a name="in-this-topic"></a>V tomto tématu  
  
-   [Pomocí identita WorkflowIdentity](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UsingWorkflowIdentity)  
  
    -   [Pomocí identita WorkflowIdentity spuštění vedle sebe](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#SxS)  
  
-   [Upgrade rozhraní .NET Framework 4 trvalost databází pro podporu správy verzí pracovního postupu](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)  
  
    -   [Aktualizace schématu databáze](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#ToUpgrade)  
  
## <a name="UsingWorkflowIdentity"></a> Pomocí identita WorkflowIdentity  
 Použití <xref:System.Activities.WorkflowIdentity>vytvořit instanci, nakonfigurujte ji a přidružte jej k <xref:System.Activities.WorkflowApplication> instance. A <xref:System.Activities.WorkflowIdentity> instance obsahuje tři identifikační údaje. <xref:System.Activities.WorkflowIdentity.Name%2A> a <xref:System.Activities.WorkflowIdentity.Version%2A> obsahovat název a <xref:System.Version> a jsou povinné, a <xref:System.Activities.WorkflowIdentity.Package%2A> je volitelný a slouží k určení další řetězec obsahující informace, jako je název sestavení nebo jiné požadované informace. A <xref:System.Activities.WorkflowIdentity> je jedinečné, pokud některý z jeho tři vlastnosti se liší od jiného <xref:System.Activities.WorkflowIdentity>.  
  
> [!IMPORTANT]
>  A <xref:System.Activities.WorkflowIdentity> nesmí obsahovat žádné identifikovatelné osobní údaje (PII). Informace o <xref:System.Activities.WorkflowIdentity> použitý k vytvoření instance je vygenerován pro všechny nakonfigurované sledování životního cyklu služeb v několika různých fázích aktivity modulem runtime. Sledování WF nemá žádný mechanismus skrýt identifikovatelné osobní údaje (citlivými daty). Proto <xref:System.Activities.WorkflowIdentity> instance by neměla obsahovat žádná data identifikovatelné osobní údaje, jak bude vygenerován modulem runtime ve sledování záznamů a mohou být viditelná pro každý, kdo má přístup k zobrazení záznamů sledování.  
  
 V následujícím příkladu <xref:System.Activities.WorkflowIdentity> se vytvoří a přidružené k instanci pracovního postupu vytvořené využitím `MortgageWorkflow` definice pracovního postupu.  
  
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
  
 Při opětovném načtení a obnovení pracovního postupu, <xref:System.Activities.WorkflowIdentity> , který je nakonfigurovaný tak, aby odpovídaly <xref:System.Activities.WorkflowIdentity> trvalá pracovního postupu instance musí být použita.  
  
```csharp  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Load the workflow.  
wfApp.Load(instanceId);  
  
// Resume the workflow...  
```  
  
 Pokud <xref:System.Activities.WorkflowIdentity> při opětovném načtení instance pracovního postupu se neshoduje trvalý <xref:System.Activities.WorkflowIdentity>, <xref:System.Activities.VersionMismatchException> je vyvolána výjimka. V následujícím příkladu pokusu o načtení se provádí na `MortgageWorkflow` instanci, která byla zachována v předchozím příkladu. Tato zatížení pokus se uskuteční pomocí <xref:System.Activities.WorkflowIdentity> nakonfigurovaný pro novější verze na dům pracovního postupu, který se neshoduje s trvalé instanci.  
  
```csharp  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow_v2(), identityV2);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Attempt to load the workflow instance.  
wfApp.Load(instanceId);  
  
// Resume the workflow...  
```  
  
 Když je spuštěn předchozí kód, následující <xref:System.Activities.VersionMismatchException> je vyvolána výjimka.  
  
 **Identita WorkflowIdentity ("MortgageWorkflow v1; Verze = 1.0.0.0') načtené instance neodpovídá identitě WorkflowIdentity ("MortgageWorkflow v2; Verze = 2.0.0.0') definice pracovního postupu. Tuto instanci lze načíst s použitím jiné definice nebo ji aktualizovat pomocí dynamické aktualizace.**  
### <a name="SxS"></a> Pomocí identita WorkflowIdentity spuštění vedle sebe  
 <xref:System.Activities.WorkflowIdentity> slouží k usnadnění spuštění více verzí pracovní postup-souběžně. Jeden běžný scénář se mění obchodní požadavky v rámci dlouhotrvající pracovního postupu. Velký počet instancí pracovního postupu může být spuštěn při nasazení aktualizované verze. Hostitelská aplikace je nakonfigurovat pro použití definice aktualizovaný pracovní postup při spuštění nové instance a zodpovídá hostitelskou aplikaci poskytnout definici správné pracovního postupu při opětovném spuštění instance. <xref:System.Activities.WorkflowIdentity> je možné identifikovat a zadat odpovídající definice pracovního postupu při opětovném spuštění instance pracovního postupu.  
  
 Načíst <xref:System.Activities.WorkflowIdentity> z trvalé instance práce, <xref:System.Activities.WorkflowApplication.GetInstance%2A> metoda se používá. <xref:System.Activities.WorkflowApplication.GetInstance%2A> Přijímá metodu <xref:System.Activities.WorkflowApplication.Id%2A> instance trvalá pracovního postupu a <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> , který obsahuje trvalé instanci a vrátí <xref:System.Activities.WorkflowApplicationInstance>. A <xref:System.Activities.WorkflowApplicationInstance> obsahuje informace o trvalé instance práce, včetně jeho přidruženého <xref:System.Activities.WorkflowIdentity>. Tato související <xref:System.Activities.WorkflowIdentity> je možné zadat definici správné pracovního postupu při načítání a obnovení instance pracovního postupu hostitele.  
  
> [!NOTE]
>  S hodnotou null <xref:System.Activities.WorkflowIdentity> je platný a je možné mapovat instancí, které byly trvale uložena s žádné přidružené hostitelem <xref:System.Activities.WorkflowIdentity> k definici pracovního postupu správné. Tato situace může nastat, když aplikace pracovního postupu nebyl původně zapsán s verzí pracovního postupu, nebo když aplikace se upgraduje z [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]. Další informace najdete v tématu [upgrade rozhraní .NET Framework 4 trvalost databází na podporu pracovních postupů správy verzí](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).  
  
 V následujícím příkladu `Dictionary<WorkflowIdentity, Activity>` slouží k přidružení <xref:System.Activities.WorkflowIdentity> instance s jejich odpovídající definice pracovního postupu a pracovní postup je začít používat `MortgageWorkflow` definice pracovního postupu, který je přidružený `identityV1` <xref:System.Activities.WorkflowIdentity>.  
  
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
  
 V následujícím příkladu je načíst informace o instanci trvalá pracovního postupu z předchozího příkladu voláním <xref:System.Activities.WorkflowApplication.GetInstance%2A>a trvalý <xref:System.Activities.WorkflowIdentity> informace slouží k načtení odpovídajícího definice pracovního postupu. Tyto informace slouží ke konfiguraci <xref:System.Activities.WorkflowApplication>, a pak je načíst pracovní postup. Upozorňujeme, že <xref:System.Activities.WorkflowApplication.Load%2A> přetížení přebírající <xref:System.Activities.WorkflowApplicationInstance> se používá, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> , který byl nakonfigurován na <xref:System.Activities.WorkflowApplicationInstance> používá <xref:System.Activities.WorkflowApplication> a proto jeho <xref:System.Activities.WorkflowApplication.InstanceStore%2A> vlastnost není nutné konfigurovat.  
  
> [!NOTE]
>  Pokud <xref:System.Activities.WorkflowApplication.InstanceStore%2A> je hodnota nastavena, je nutné ji nastavit pomocí stejné <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> instanci použitou <xref:System.Activities.WorkflowApplicationInstance> jinak <xref:System.ArgumentException> bude vyvolána výjimka s následující zprávou: `The instance is configured with a different InstanceStore than this WorkflowApplication.`.  
  
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
  
## <a name="UpdatingWF4PersistenceDatabases"></a> Upgrade rozhraní .NET Framework 4 trvalost databází pro podporu správy verzí pracovního postupu  
 Upgrade databáze trvalosti vytvořené ve službě je poskytován skript databáze SqlWorkflowInstanceStoreSchemaUpgrade.sql [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] databázové skripty. Tento skript aktualizace databází, aby podporovaly nové funkce správy verzí zavedený [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Všechny instance trvalá pracovního postupu v databázích jsou uvedeny výchozí hodnoty správy verzí a potom účastnit spuštění vedle sebe a dynamické aktualizace.  
  
 Pokud [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] pracovního postupu aplikace pokusí všechny operace trvalého uložení, které používají nové funkce správy verzí na stálost databázi, která nebyla upgradována pomocí dodávaného skriptu <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> dojde a zobrazí se zpráva podobná následující zpráva.  
  
 **Úložiště SqlWorkflowInstanceStore je verze databáze "4.0.0.0". Příkaz InstancePersistenceCommand "System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand" nelze spustit proti této verzi databáze.  Upgradujte databázi na "4.5.0.0".**  
### <a name="ToUpgrade"></a> Aktualizace schématu databáze  
  
1.  Otevřete SQL Server Management Studio a připojte se k serveru databáze trvalosti, například **. \SQLEXPRESS**.  
  
2.  Zvolte **otevřít**, **souboru** z **souboru** nabídky. Přejděte do následující složky: `C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`  
  
3.  Vyberte **SqlWorkflowInstanceStoreSchemaUpgrade.sql** a klikněte na tlačítko **otevřít**.  
  
4.  Vyberte název databáze trvalosti v **dostupných databází** rozevíracího seznamu.  
  
5.  Zvolte **Execute** z **dotazu** nabídky.  
  
 Po dokončení dotazu schéma databáze se upgraduje a v případě potřeby můžete zobrazit výchozí identity pracovního postupu, která byla přiřazena instance trvalá pracovního postupu. Rozbalte databázi přetrvávání v **databází** uzlu **Průzkumník objektů**a potom rozbalte **zobrazení** uzlu. Klikněte pravým tlačítkem na **System.Activities.DurableInstancing.Instances** a zvolte **vybrat prvních 1000 řádků**. Přejděte na konec sloupců a Všimněte si, že jsou šest další sloupce, které jsou přidány do zobrazení: **IdentityName**, **IdentityPackage**, **sestavení**, **hlavní**, **menší**, a **revize**. Žádný trvalý pracovní postup bude mít hodnotu **NULL** tato pole představující identity pracovního postupu hodnotu null.
