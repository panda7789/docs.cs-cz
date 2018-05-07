---
title: Pomocí WorkflowIdentity a správa verzí
ms.date: 03/30/2017
ms.assetid: b8451735-8046-478f-912b-40870a6c0c3a
ms.openlocfilehash: 0d8c02dca67d24399972417f9d6485d668215742
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-workflowidentity-and-versioning"></a>Pomocí WorkflowIdentity a správa verzí
<xref:System.Activities.WorkflowIdentity> poskytuje způsob pro pracovní postup vývojáři aplikace k přidružit název a <xref:System.Version> s definicí pracovního postupu a pro tyto informace k být přidružen k instanci pracovního postupu trvalý. Tyto informace identity lze použít vývojáři aplikace pracovního postupu povolit scénáře, jako je vedle sebe spouštění více verzí definice pracovního postupu a poskytuje základním kamenem pro další funkce, jako je například dynamická aktualizace. Toto téma poskytuje přehled používání <xref:System.Activities.WorkflowIdentity> s <xref:System.Activities.WorkflowApplication> hostování. Informace o provádění vedle sebe definice pracovního postupu v služby pracovního postupu v tématu [správu verzí vedle sebe v hostitele služby pracovního postupu](../../../docs/framework/wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md). Informace o dynamické aktualizace, najdete v části [dynamické aktualizace](../../../docs/framework/windows-workflow-foundation/dynamic-update.md).  
  
## <a name="in-this-topic"></a>V tomto tématu  
  
-   [Pomocí WorkflowIdentity](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UsingWorkflowIdentity)  
  
    -   [Pomocí WorkflowIdentity spuštění vedle sebe](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#SxS)  
  
-   [Upgrade rozhraní .NET Framework 4 trvalost databáze podporující pracovní postup správy verzí](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)  
  
    -   [Aktualizace schématu databáze](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#ToUpgrade)  
  
##  <a name="UsingWorkflowIdentity"></a> Pomocí WorkflowIdentity  
 Chcete-li použít <xref:System.Activities.WorkflowIdentity>, vytvoření instance, konfiguraci a přidružte ji s <xref:System.Activities.WorkflowApplication> instance. A <xref:System.Activities.WorkflowIdentity> instance obsahuje tři identifikační údaje. <xref:System.Activities.WorkflowIdentity.Name%2A> a <xref:System.Activities.WorkflowIdentity.Version%2A> obsahovat název a <xref:System.Version> a jsou povinné, a <xref:System.Activities.WorkflowIdentity.Package%2A> je volitelný a může sloužit k určení požadovaných další řetězec obsahující informace, jako je název sestavení nebo jiné informace. A <xref:System.Activities.WorkflowIdentity> je jedinečný, pokud jsou některé jeho vlastnosti tři liší od jiného <xref:System.Activities.WorkflowIdentity>.  
  
> [!IMPORTANT]
>  A <xref:System.Activities.WorkflowIdentity> nesmí obsahovat žádné identifikovatelné osobní údaje (PII). Informace o <xref:System.Activities.WorkflowIdentity> použít k vytvoření instance je pro všechny nakonfigurované sledování životního cyklu služeb v několika různých místech aktivity vygenerované modulem runtime. WF sledování nemá žádný mechanismus skrýt PII (citlivé uživatelských dat). Proto <xref:System.Activities.WorkflowIdentity> instance nesmí obsahovat žádná data PII tak, jak bude vygenerované modulem runtime v sledování záznamů a mohou být viditelná pro každý, kdo má přístup k zobrazení záznamů sledování.  
  
 V následujícím příkladu <xref:System.Activities.WorkflowIdentity> se vytvoří a přidružené k instanci pracovního postupu vytvořený `MortgageWorkflow` definice pracovního postupu.  
  
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
  
 Při opětovném načtení a obnovení pracovního postupu, <xref:System.Activities.WorkflowIdentity> nakonfigurovaný tak, aby odpovídala <xref:System.Activities.WorkflowIdentity> trvalou pracovního postupu instance musí být použita.  
  
```csharp  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Load the workflow.  
wfApp.Load(instanceId);  
  
// Resume the workflow...  
```  
  
 Pokud <xref:System.Activities.WorkflowIdentity> používá při opětovném načtení instance pracovního postupu neodpovídá trvalou <xref:System.Activities.WorkflowIdentity>, <xref:System.Activities.VersionMismatchException> je vyvolána výjimka. V následujícím příkladu je pokusu o načtení probíhají `MortgageWorkflow` instanci, která byla v předchozím příkladu jako trvalý. Tato zatížení pokus se uskuteční pomocí <xref:System.Activities.WorkflowIdentity> nakonfigurovaný pro novější verzi hypotéční pracovního postupu, který neodpovídá trvalou instanci.  
  
```csharp  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow_v2(), identityV2);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Attempt to load the workflow instance.  
wfApp.Load(instanceId);  
  
// Resume the workflow...  
```  
  
 Při spuštění předchozího kódu, následující <xref:System.Activities.VersionMismatchException> je vyvolána výjimka.  
  
 **WorkflowIdentity ('MortgageWorkflow v1; Verze = 1.0.0.0') načíst instance neodpovídá WorkflowIdentity ('MortgageWorkflow v2; Verze = 2.0.0.0') z definice pracovního postupu zadané. Instanci lze načíst pomocí jiné definice nebo aktualizovat pomocí dynamické aktualizace.**  
###  <a name="SxS"></a> Pomocí WorkflowIdentity spuštění vedle sebe  
 <xref:System.Activities.WorkflowIdentity> můžete ji použít pro usnadnění provádění více verzí pracovní postup-souběžného. Jeden běžný scénář mění obchodní požadavky na dlouhodobé pracovního postupu. Velký počet instancí pracovního postupu může být spuštěn při nasazení aktualizované verze. Hostitelskou aplikaci může být konfigurovaná pro použití definice aktualizované pracovního postupu při spouštění nové instance a je zodpovědností hostitelskou aplikaci můžete při obnovení instance definice pracovního postupu správné. <xref:System.Activities.WorkflowIdentity> slouží k identifikaci a zadejte odpovídající definice pracovního postupu při obnovení instancí pracovních postupů.  
  
 Načíst <xref:System.Activities.WorkflowIdentity> instance trvalou pracovního postupu, <xref:System.Activities.WorkflowApplication.GetInstance%2A> metoda se používá. <xref:System.Activities.WorkflowApplication.GetInstance%2A> Metoda trvá <xref:System.Activities.WorkflowApplication.Id%2A> instance trvalou pracovního postupu a <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> který obsahuje trvalý instanci a vrátí <xref:System.Activities.WorkflowApplicationInstance>. A <xref:System.Activities.WorkflowApplicationInstance> obsahuje informace o instanci trvalou pracovního postupu, včetně přidružené <xref:System.Activities.WorkflowIdentity>. To přidružené <xref:System.Activities.WorkflowIdentity> lze použít pro hostitele k poskytování definice pracovního postupu správné načítání a obnovení k instanci pracovního postupu.  
  
> [!NOTE]
>  Null <xref:System.Activities.WorkflowIdentity> je platný a můžete použít pro hostitele k mapování instancí, které byly nastavené jako trvalé bez přidružené <xref:System.Activities.WorkflowIdentity> k definici správné pracovního postupu. Tato situace může nastat, když aplikace pracovního postupu nebyla původně zapsána s pracovní postup správy verzí, nebo když je aplikace upgradovali z [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]. Další informace najdete v tématu [upgrade rozhraní .NET Framework 4 trvalost databáze na podporu pracovních postupů správy verzí](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).  
  
 V následujícím příkladu `Dictionary<WorkflowIdentity, Activity>` je použito k přidružení <xref:System.Activities.WorkflowIdentity> pomocí je spuštěna instance s jejich odpovídající definice pracovního postupu a pracovní postup `MortgageWorkflow` definice pracovního postupu, který je přidružen `identityV1` <xref:System.Activities.WorkflowIdentity>.  
  
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
  
 V následujícím příkladu je načíst informace o instanci trvalou pracovního postupu z předchozího příkladu voláním <xref:System.Activities.WorkflowApplication.GetInstance%2A>a trvalou <xref:System.Activities.WorkflowIdentity> informace slouží k načtení odpovídající definice pracovního postupu. Tyto informace slouží ke konfiguraci <xref:System.Activities.WorkflowApplication>, a pak je načtena pracovního postupu. Všimněte si, že vzhledem k tomu, <xref:System.Activities.WorkflowApplication.Load%2A> přetížení, které přijímá <xref:System.Activities.WorkflowApplicationInstance> se používá, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> který byl nakonfigurován na <xref:System.Activities.WorkflowApplicationInstance> je používán <xref:System.Activities.WorkflowApplication> a proto jeho <xref:System.Activities.WorkflowApplication.InstanceStore%2A> vlastnost není nutné nakonfigurovat.  
  
> [!NOTE]
>  Pokud <xref:System.Activities.WorkflowApplication.InstanceStore%2A> vlastnost nastavena, je nutné ji nastavit pomocí stejné <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> instanci použitou <xref:System.Activities.WorkflowApplicationInstance> jinak <xref:System.ArgumentException> bude vyvolána s následující zprávou: `The instance is configured with a different InstanceStore than this WorkflowApplication.`.  
  
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
  
##  <a name="UpdatingWF4PersistenceDatabases"></a> Upgrade rozhraní .NET Framework 4 trvalost databáze podporující pracovní postup správy verzí  
 SqlWorkflowInstanceStoreSchemaUpgrade.sql databázového skriptu je zadán pro upgrade trvalost databází vytvořených přes [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] databáze skripty. Tento skript aktualizace databáze podporují nové možnosti správy verzí, počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Všechny instance pracovního postupu trvalý v databázích mají výchozí hodnoty verze a můžete pak podílet na spuštění vedle sebe a dynamické aktualizace.  
  
 Pokud [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] pracovní postup aplikace pokusí žádné trvalost operace, které používají nové funkce správy verzí v trvalost databázi, která nebyla upgradována, pomocí poskytnutého skriptu <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> je vyvolána s zpráva podobná následující zpráva.  
  
 **SqlWorkflowInstanceStore má verzi databáze, 4.0.0.0'. InstancePersistenceCommand 'System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand' nelze spustit pro tuto verzi databáze.  Upgradujte databázi na '4.5.0.0'.**  
###  <a name="ToUpgrade"></a> Aktualizace schématu databáze  
  
1.  Otevřete aplikaci SQL Server Management Studio a připojte se k serveru databáze trvalost například **. \SQLEXPRESS**.  
  
2.  Zvolte **otevřete**, **soubor** z **souboru** nabídky. Přejděte do následující složky: `C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`  
  
3.  Vyberte **SqlWorkflowInstanceStoreSchemaUpgrade.sql** a klikněte na tlačítko **otevřete**.  
  
4.  Vyberte název databáze trvalost v **dostupné databáze** rozevíracího seznamu.  
  
5.  Zvolte **Execute** z **dotazu** nabídky.  
  
 Po dokončení dotazu je upgradována schématu databáze, a v případě potřeby můžete zobrazit výchozí identitu pracovního postupu, který byl přiřazen k instancím trvalou pracovního postupu. Trvalost databázi v rozšířit **databáze** uzlu **Průzkumník objektů**a potom rozbalte **zobrazení** uzlu. Klikněte pravým tlačítkem na **System.Activities.DurableInstancing.Instances** a zvolte **vyberte Top 1000 řádky**. Přejděte na konec sloupců a Všimněte si, že jsou šesti další sloupce, které jsou přidané do zobrazení: **IdentityName**, **IdentityPackage**, **sestavení**, **hlavní** , **Menší**, a **revize**. Žádný trvalou pracovní postup bude mít hodnotu **NULL** pro tato pole představující identity hodnotu null. pracovní postup.
