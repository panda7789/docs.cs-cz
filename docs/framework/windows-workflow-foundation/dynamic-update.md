---
title: Dynamická aktualizace
ms.date: 03/30/2017
ms.assetid: 8b6ef19b-9691-4b4b-824c-3c651a9db96e
ms.openlocfilehash: dea930de2103a24aa48b1d0a31a3cbf5fc0ae26c
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44076716"
---
# <a name="dynamic-update"></a>Dynamická aktualizace
Dynamická aktualizace poskytuje mechanismus pro pracovní postup vývojářům aplikací k aktualizaci pracovního postupu definici trvalé instance práce. To může být implementace opravy chyb, nové požadavky, nebo tak, aby vyhovovaly neočekávaným změnám. Toto téma obsahuje základní informace o dynamické aktualizace funkcích uvedených ve [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].  
  
## <a name="dynamic-update"></a>Dynamická aktualizace  
 Použití dynamických aktualizací trvalé instance práce, <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> je vytvořen, který obsahuje pokyny pro modul runtime, které popisují, jak změnit trvalými instancemi pracovního postupu tak, aby odrážely požadované změny. Po vytvoření mapa aktualizace se použije k instancím požadované trvalá pracovního postupu. Po použití dynamické aktualizace, může být obnoveno instance pracovního postupu, pomocí nové definice aktualizovaný pracovní postup. Existují čtyři kroky potřebné k vytvoření a použijte mapu aktualizace.  
  
1.  [Příprava pro dynamickou aktualizaci definice pracovního postupu](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Prepare)  
  
2.  [Aktualizace definice pracovního postupu tak, aby odrážely požadované změny](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Update)  
  
3.  [Vytvoření mapy aktualizace](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Create)  
  
4.  [Použijte mapu aktualizace instance požadované trvalá pracovního postupu](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Apply)  
  
> [!NOTE]
>  Všimněte si, že kroky 1 až 3, které zahrnují vytváření mapa aktualizace, se dají provést nezávisle na instalaci aktualizace nezměnilo. Běžný scénář tím, že pracovní postup pro vývojáře se vytvoří aktualizace mapování v režimu offline a správce použije aktualizace později.  
  
 Toto téma obsahuje přehled procesu dynamické aktualizace do trvalé instanci pracovního postupu Xaml kompilované přidat novou aktivitu.  
  
###  <a name="Prepare"></a> Příprava pro dynamickou aktualizaci definice pracovního postupu  
 Prvním krokem v procesu dynamické aktualizace je k přípravě definice pracovního postupu požadované aktualizace. To se provádí pomocí volání <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> metoda a předání v definici pracovního postupu, který chcete upravit. Tato metoda ověří a pak vás stromu pracovního postupu k identifikaci všech objektů, například veřejné a proměnné, které musí být označené, můžete později porovnat s definicí změny pracovního postupu. Po jejím dokončení, stromu pracovního postupu klonovat a připojené k původní definici pracovního postupu. Při aktualizaci mapy, aktualizovaná verze definice pracovního postupu je ve srovnání s původní definici pracovního postupu a mapa aktualizace je generován a základě rozdíly.  
  
 Příprava pracovní postup Xaml pro dynamické aktualizace, které mohou být načteny do <xref:System.Activities.ActivityBuilder>a pak <xref:System.Activities.ActivityBuilder> je předána do <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>.  
  
> [!NOTE]
>  Další informace o práci s serializovat pracovních postupů a <xref:System.Activities.ActivityBuilder>, naleznete v tématu [serializace pracovních postupů a aktivit do a z XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).  
  
 V následujícím příkladu `MortgageWorkflow` definice (, který se skládá z <xref:System.Activities.Statements.Sequence> s několika podřízených aktivit) je načteno do <xref:System.Activities.ActivityBuilder>a pak připraví se dynamická aktualizace. Po vrácení metody, <xref:System.Activities.ActivityBuilder> obsahuje původní definici pracovního postupu, stejně jako kopii.  
  
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
>  Pokud chcete stáhnout ukázkový kód, který doprovází v tomto tématu, navštivte [dynamická aktualizace vzorového kódu](https://go.microsoft.com/fwlink/?LinkId=227905).  
  
###  <a name="Update"></a> Aktualizace definice pracovního postupu tak, aby odrážely požadované změny  
 Jakmile definice pracovního postupu je připraven na aktualizace, můžete provést požadované změny. Můžete přidat nebo odebrat aktivity, přidat, přesunout nebo odstranit veřejné proměnné, přidat nebo odebrat argumenty a provést změny podpis delegátů aktivit. Nelze odebrat aktivitu spuštěné nebo změnit signaturu spuštěné delegáta. Mohou být provedeny tyto změny pomocí kódu, nebo v okně návrháře znovu hostovaných pracovních postupů. V následujícím příkladu, vlastní `VerifyAppraisal` je aktivita přidána do sekvenci, která tvoří text `MortgageWorkflow` z předchozího příkladu.  
  
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
 Jakmile se změnila definice pracovního postupu, která byla připravena pro aktualizace, je možné vytvořit mapa aktualizace. Chcete-li vytvořit mapu dynamickou aktualizaci <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> vyvolání metody. Tím se vrátí <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> , který obsahuje informace o modulu runtime je potřeba upravit trvalé instance práce tak, že může být načten a pokračuje s novou definici pracovního postupu. V následujícím příkladu se vytvoří dynamickou mapu pro upravené `MortgageWorkflow` definice z předchozího příkladu.  
  
```csharp  
// Create the update map.  
DynamicUpdateMap map = DynamicUpdateServices.CreateUpdateMap(ab);  
```  
  
 Toto mapování aktualizace okamžitě lze upravit instancí pracovních postupů trvalý, nebo více obvykle můžete uložit a aktualizace použity později. Jeden způsob, jak uložit mapa aktualizace je určená k serializaci do souboru, jak je znázorněno v následujícím příkladu.  
  
```csharp  
// Serialize the update map to a file.  
DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));  
using (FileStream fs = System.IO.File.Open(@"C:\WorkflowDefitinions\MortgageWorkflow.map", FileMode.Create))  
{  
    serializer.WriteObject(fs, map);  
}  
```  
  
 Když <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> definice naklonovaného pracovního postupu a další informace o dynamické aktualizace, která byla přidána při volání funkce vrátí <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> Odebereme, a připraven k uložit tak, aby ji lze později při obnovování aktualizaci definice změny pracovního postupu instance pracovního postupu. V následujícím příkladu je uložena definice pracovního postupu upravené `MortgageWorkflow_v2.xaml`.  
  
```csharp  
// Save the modified workflow definition.  
StreamWriter sw = File.CreateText(@"C:\WorkflowDefitinions\MortgageWorkflow_v1.1.xaml");  
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));  
XamlServices.Save(xw, ab);  
sw.Close();  
```  
  
###  <a name="Apply"></a> Použijte mapu aktualizace instance požadované trvalá pracovního postupu  
 Použití mapy aktualizace lze provést kdykoli po jeho vytvoření. Je možné ji provést, okamžitě <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> instance, který byl vrácen <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>, nebo lze provést, pokud později pomocí uložené kopie mapa aktualizace. Aktualizace instance pracovního postupu, načíst je do <xref:System.Activities.WorkflowApplicationInstance> pomocí <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>. Dále vytvořte <xref:System.Activities.WorkflowApplication> pomocí definice aktualizovaný pracovní postup a požadovaný <xref:System.Activities.WorkflowIdentity>. To <xref:System.Activities.WorkflowIdentity> může být jiný než ten, který byl použit k uchování původní pracovního postupu a aby bylo zřejmé, že byla změněna trvalé instanci je obvykle. Jednou <xref:System.Activities.WorkflowApplication> je vytvořen, je načteno pomocí přetížení <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> , která přijímá <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>a potom byla uvolněna voláním <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType>. Použije dynamické aktualizace a opakuje instance aktualizovaný pracovní postup.  
  
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
  
### <a name="resuming-an-updated-workflow-instance"></a>Obnovení Instance aktualizovaný pracovní postup  
 Po použití dynamické aktualizace, může být obnoveno instance pracovního postupu. Všimněte si, že nový aktualizované definice a <xref:System.Activities.WorkflowIdentity> musí být použita.  
  
> [!NOTE]
>  Další informace o práci s <xref:System.Activities.WorkflowApplication> a <xref:System.Activities.WorkflowIdentity>, naleznete v tématu [použití WorkflowIdentity a správy verzí](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md).  
  
 V následujícím příkladu `MortgageWorkflow_v1.1.xaml` pracovní postup z předchozího příkladu byl zkompilován a je načten a obnovit pomocí definice aktualizovaný pracovní postup.  
  
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
>  Pokud chcete stáhnout ukázkový kód, který doprovází v tomto tématu, navštivte [dynamická aktualizace vzorového kódu](https://go.microsoft.com/fwlink/?LinkId=227905).
