---
title: Dynamická aktualizace
ms.date: 03/30/2017
ms.assetid: 8b6ef19b-9691-4b4b-824c-3c651a9db96e
ms.openlocfilehash: cfd10e4b93351c607ef270487a12bec19ded4ca8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="dynamic-update"></a>Dynamická aktualizace
Dynamická aktualizace poskytuje mechanismus pro pracovní postup vývojáři aplikace k aktualizaci definice pracovního postupu instance trvalou pracovního postupu. To může být implementace oprava chyb, nové požadavky, nebo aby bylo možné ošetřit neočekávané změny. Toto téma obsahuje přehled funkcí Dynamická aktualizace byla zavedená v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].  
  
## <a name="dynamic-update"></a>Dynamická aktualizace  
 Na instanci pracovního postupu trvalý, dynamická aktualizace <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> je vytvořen, který obsahuje pokyny pro modul runtime, které popisují, jak upravit k instanci pracovního postupu trvalou tak, aby odrážela požadované změny. Po vytvoření mapy aktualizace, je tato instance požadované trvalou pracovního postupu. Po dynamické aktualizace, dá se k instanci pracovního postupu obnovit pomocí nové definice aktualizované pracovního postupu. Existují čtyři kroky potřebné k vytvoření a použití mapování aktualizace.  
  
1.  [Příprava definice pracovního postupu pro dynamické aktualizace](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Prepare)  
  
2.  [Aktualizace definice pracovního postupu tak, aby odrážela požadované změny](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Update)  
  
3.  [Vytvoření mapy aktualizace](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Create)  
  
4.  [Použít aktualizace mapy pro instance požadované trvalou pracovních postupů](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Apply)  
  
> [!NOTE]
>  Všimněte si, že se dají provést kroky 1 až 3, které zahrnují vytváření mapy aktualizace, nezávisle na instalaci aktualizace. Běžný scénář, že vývojář pracovního postupu vytvoříte aktualizace mapovat do offline režimu a pak správce budou platit aktualizace později.  
  
 Toto téma obsahuje přehled procesu dynamické aktualizace pro přidání nové aktivity na trvalou instanci kompilované Xaml pracovního postupu.  
  
###  <a name="Prepare"></a> Příprava definice pracovního postupu pro dynamické aktualizace  
 Prvním krokem v procesu dynamické aktualizace je příprava definice pracovního postupu požadované pro aktualizaci. To se provádí volání <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> metoda a předávání definice pracovního postupu, který chcete upravit. Tato metoda ověří a potom provede stromu pracovního postupu k identifikaci všechny objekty, například veřejné a proměnné, které je třeba označit tak, že se má porovnat později s definice upravené pracovního postupu. Po jejím dokončení, je stromu pracovního postupu klonovat a připojené k původní definice pracovního postupu. Při aktualizaci mapy je aktualizovaná verze definice pracovního postupu se porovná se původní definice pracovního postupu a mapy aktualizace bude vytvořena podle rozdíly.  
  
 Příprava pracovního postupu Xaml pro dynamické aktualizace může být načten do <xref:System.Activities.ActivityBuilder>a potom <xref:System.Activities.ActivityBuilder> je předána do <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>.  
  
> [!NOTE]
>  Další informace o práci s serializovat pracovní postupy a <xref:System.Activities.ActivityBuilder>, najdete v části [serializaci pracovních postupů a aktivit do a z XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).  
  
 V následujícím příkladu `MortgageWorkflow` definice (který se skládá z <xref:System.Activities.Statements.Sequence> s několika aktivitami podřízené) je načten do <xref:System.Activities.ActivityBuilder>a pak připravené pro dynamické aktualizace. Po metoda vrátí, <xref:System.Activities.ActivityBuilder> obsahuje původní definice pracovního postupu, jakož i kopii.  
  
```csharp  
// Load the MortgageWorkflow definition from Xaml into  
// an ActivityBuilder.  
XamlXmlReaderSettings readerSettings = new XamlXmlReaderSettings()  
{  
    LocalAssembly = Assembly.GetExecutingAssembly()  
};  
  
XamlXmlReader xamlReader = new XamlXmlReader(@"C:\WorkflowDefitinions\MortgageWorkflow.xaml",   
    readerSettings);  
  
ActivityBuilder ab = XamlServices.Load(  
    ActivityXamlServices.CreateBuilderReader(xamlReader)) as ActivityBuilder;  
  
// Prepare the workflow definition for dynamic update.  
DynamicUpdateServices.PrepareForUpdate(ab);  
```  
  
> [!NOTE]
>  Chcete-li stáhnout ukázkový kód, který doprovází toto téma, přečtěte si téma [dynamická aktualizace ukázkový kód](http://go.microsoft.com/fwlink/?LinkId=227905).  
  
###  <a name="Update"></a> Aktualizace definice pracovního postupu tak, aby odrážela požadované změny  
 Jakmile definice pracovního postupu je připravena pro aktualizace, můžete provést požadované změny. Můžete přidat nebo odebrat aktivity, přidat, přesunout nebo odstranit veřejné proměnné, přidat nebo odebrat argumenty a provést změny podpis delegáti aktivity. Nelze odebrat aktivitu spuštěné ani změnit podpis spuštěné delegáta. Tyto změny pomocí kódu, nebo v Návrháři znovu hostovaných pracovních postupů. V následujícím příkladu, vlastní `VerifyAppraisal` aktivity se přidá do pořadí, které tvoří text `MortgageWorkflow` z předchozího příkladu.  
  
```csharp  
// Make desired changes to the definition. In this example, we are  
// inserting a new VerifyAppraisal activity as the 3rd child of the root Sequence.  
VerifyAppraisal va = new VerifyAppraisal  
{  
    Result = new VisualBasicReference<bool>("LoanCriteria")  
};  
  
// Get the Sequence that makes up the body of the workflow.  
Sequence s = ab.Implementation as Sequence;  
  
// Insert the new activity into the Sequence.  
s.Activities.Insert(2, va);  
```  
  
###  <a name="Create"></a> Vytvoření mapy aktualizace  
 Jakmile připravené pro aktualizaci definice pracovního postupu byla změněna, lze vytvořit mapy aktualizace. K vytvoření mapy dynamické aktualizace, <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> metoda je volána. Tento příkaz vrátí <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> obsahující informace o modulu runtime je potřeba upravit instanci trvalou pracovního postupu tak, aby může být načtena a pokračuje s novou definici pracovního postupu. V následujícím příkladu se vytvoří dynamické mapy pro upravenou `MortgageWorkflow` definice z předchozího příkladu.  
  
```csharp  
// Create the update map.  
DynamicUpdateMap map = DynamicUpdateServices.CreateUpdateMap(ab);  
```  
  
 Tato mapa aktualizace okamžitě lze upravit instancí trvalou pracovních postupů, nebo více obvykle lze uložit a aktualizace později. Jeden způsob, jak uložit mapy aktualizace je určená k serializaci do souboru, jak je znázorněno v následujícím příkladu.  
  
```csharp  
// Serialize the update map to a file.  
DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));  
using (FileStream fs = System.IO.File.Open(@"C:\WorkflowDefitinions\MortgageWorkflow.map", FileMode.Create))  
{  
    serializer.WriteObject(fs, map);  
}  
```  
  
 Když <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> vrátí definice klonovaný pracovního postupu a další informace dynamické aktualizace, která byla přidána ve volání <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> je odebrán, a je připravený uložit tak, aby ho lze později při obnovení aktualizaci definice pracovního postupu změny instance pracovního postupu. V následujícím příkladu je uložena definice pracovního postupu změny `MortgageWorkflow_v2.xaml`.  
  
```csharp  
// Save the modified workflow definition.  
StreamWriter sw = File.CreateText(@"C:\WorkflowDefitinions\MortgageWorkflow_v1.1.xaml");  
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));  
XamlServices.Save(xw, ab);  
sw.Close();  
```  
  
###  <a name="Apply"></a> Použít aktualizace mapy pro instance požadované trvalou pracovních postupů  
 Použití map aktualizace lze provést kdykoli po jeho vytvoření. Je možné ji provést, hned pomocí <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> instanci, která vrátila <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>, nebo je možné ji provést, později pomocí uložené kopie mapy aktualizace. Aktualizace instance pracovního postupu, načíst do <xref:System.Activities.WorkflowApplicationInstance> pomocí <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>. Dále vytvořte <xref:System.Activities.WorkflowApplication> pomocí definice aktualizované pracovního postupu a požadovanou <xref:System.Activities.WorkflowIdentity>. To <xref:System.Activities.WorkflowIdentity> může být jiný než ten, který byl použitý k zachování původní pracovního postupu a většinou je, aby bylo zřejmé, že trvalou instanci se změnila. Jednou <xref:System.Activities.WorkflowApplication> je vytvořen, je načten pomocí přetížení <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> , která má <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>a potom pomocí volání uvolněna z <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType>. To platí dynamická aktualizace a přetrvává k instanci pracovního postupu aktualizované.  
  
```csharp  
// Load the serialized update map.  
DynamicUpdateMap map;  
using (FileStream fs = File.Open(@"C:\WorkflowDefitinions\MortgageWorkflow.map", FileMode.Open))  
{  
    DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));  
    object updateMap = serializer.ReadObject(fs);  
    if (updateMap == null)  
    {  
        throw new ApplicationException("DynamicUpdateMap is null.");  
    }  
  
    map = (DynamicUpdateMap)updateMap;  
}  
  
// Retrieve a list of workflow instance ids that corresponds to the  
// workflow instances to update. This step is the responsibility of  
// the application developer.  
List<Guid> ids = GetPersistedWorkflowIds();  
foreach (Guid id in ids)  
{  
    // Get a proxy to the persisted workflow instance.  
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);  
    WorkflowApplicationInstance instance = WorkflowApplication.GetInstance(id, store);  
  
    // If desired, you can inspect the WorkflowIdentity of the instance  
    // using the DefinitionIdentity property to determine whether to apply  
    // the update.  
    Console.WriteLine(instance.DefinitionIdentity);  
  
    // Create a workflow application. You must specify the updated workflow definition, and  
    // you may provide an updated WorkflowIdentity if desired to reflect the update.  
    WorkflowIdentity identity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow v1.1",  
        Version = new Version(1, 1, 0, 0)  
    };  
  
    // Load the persisted workflow instance using the updated workflow definition  
    // and with an updated WorkflowIdentity. In this example the MortgageWorkflow class  
    // contains the updated definition.  
    WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);  
  
    // Apply the dynamic update on the loaded instance.                
    wfApp.Load(instance, map);  
  
    // Unload the updated instance.  
    wfApp.Unload();  
}  
```  
  
### <a name="resuming-an-updated-workflow-instance"></a>Obnovování Instance aktualizované pracovního postupu  
 Po dynamické aktualizace, může být obnoven k instanci pracovního postupu. Všimněte si, že nové aktualizované definice a <xref:System.Activities.WorkflowIdentity> se musí použít.  
  
> [!NOTE]
>  Další informace o práci s <xref:System.Activities.WorkflowApplication> a <xref:System.Activities.WorkflowIdentity>, najdete v části[pomocí WorkflowIdentity a správa verzí](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md).  
  
 V následujícím příkladu `MortgageWorkflow_v1.1.xaml` pracovní postup z předchozího příkladu je kompilovaná a je načtena a obnovit pomocí definice aktualizované pracovního postupu.  
  
```csharp  
// Load the persisted workflow instance using the updated workflow definition  
// and updated WorkflowIdentity.  
WorkflowIdentity identity = new WorkflowIdentity  
{  
    Name = "MortgageWorkflow v1.1",  
    Version = new Version(1, 1, 0, 0)  
};  
  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);  
  
// Configure persistence and desired workflow event handlers.  
// (Omitted for brevity.)  
ConfigureWorkflowApplication(wfApp);  
  
// Load the persisted workflow instance.  
wfApp.Load(InstanceId);  
  
// Resume the workflow.  
// wfApp.ResumeBookmark(...);  
```  
  
> [!NOTE]
>  Chcete-li stáhnout ukázkový kód, který doprovází toto téma, přečtěte si téma [dynamická aktualizace ukázkový kód](http://go.microsoft.com/fwlink/?LinkId=227905).
