---
title: Dynamická aktualizace
ms.date: 03/30/2017
ms.assetid: 8b6ef19b-9691-4b4b-824c-3c651a9db96e
ms.openlocfilehash: e28a34e500034eec6cf250d94cf7631ca85a7d40
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/29/2019
ms.locfileid: "58653883"
---
# <a name="dynamic-update"></a><span data-ttu-id="75202-102">Dynamická aktualizace</span><span class="sxs-lookup"><span data-stu-id="75202-102">Dynamic Update</span></span>

<span data-ttu-id="75202-103">Dynamická aktualizace poskytuje mechanismus pro pracovní postup vývojářům aplikací k aktualizaci pracovního postupu definici trvalé instance práce.</span><span class="sxs-lookup"><span data-stu-id="75202-103">Dynamic update provides a mechanism for workflow application developers to update the workflow definition of a persisted workflow instance.</span></span> <span data-ttu-id="75202-104">To může být implementace opravy chyb, nové požadavky, nebo tak, aby vyhovovaly neočekávaným změnám.</span><span class="sxs-lookup"><span data-stu-id="75202-104">This can be to implement a bug fix, new requirements, or to accommodate unexpected changes.</span></span> <span data-ttu-id="75202-105">Toto téma obsahuje základní informace o dynamické aktualizace funkcích uvedených ve [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="75202-105">This topic provides an overview of the dynamic update functionality introduced in [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>

## <a name="dynamic-update"></a><span data-ttu-id="75202-106">Dynamická aktualizace</span><span class="sxs-lookup"><span data-stu-id="75202-106">Dynamic Update</span></span>

<span data-ttu-id="75202-107">Použití dynamických aktualizací trvalé instance práce, <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> je vytvořen, který obsahuje pokyny pro modul runtime, které popisují, jak změnit trvalými instancemi pracovního postupu tak, aby odrážely požadované změny.</span><span class="sxs-lookup"><span data-stu-id="75202-107">To apply dynamic updates to a persisted workflow instance, a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> is created that contains instructions for the runtime that describe how to modify the persisted workflow instance to reflect the desired changes.</span></span> <span data-ttu-id="75202-108">Po vytvoření mapa aktualizace se použije k instancím požadované trvalá pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="75202-108">Once the update map is created, it is applied to the desired persisted workflow instances.</span></span> <span data-ttu-id="75202-109">Po použití dynamické aktualizace, může být obnoveno instance pracovního postupu, pomocí nové definice aktualizovaný pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="75202-109">Once the dynamic update is applied, the workflow instance may be resumed using the new updated workflow definition.</span></span> <span data-ttu-id="75202-110">Existují čtyři kroky potřebné k vytvoření a použijte mapu aktualizace.</span><span class="sxs-lookup"><span data-stu-id="75202-110">There are four steps required to create and apply an update map.</span></span>

1. [<span data-ttu-id="75202-111">Příprava pro dynamickou aktualizaci definice pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="75202-111">Prepare the workflow definition for dynamic update</span></span>](dynamic-update.md#Prepare)

2. [<span data-ttu-id="75202-112">Aktualizace definice pracovního postupu tak, aby odrážely požadované změny</span><span class="sxs-lookup"><span data-stu-id="75202-112">Update the workflow definition to reflect the desired changes</span></span>](dynamic-update.md#Update)

3. [<span data-ttu-id="75202-113">Vytvoření mapy aktualizace</span><span class="sxs-lookup"><span data-stu-id="75202-113">Create the update map</span></span>](dynamic-update.md#Create)

4. [<span data-ttu-id="75202-114">Použijte mapu aktualizace instance požadované trvalá pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="75202-114">Apply the update map to the desired persisted workflow instances</span></span>](dynamic-update.md#Apply)

> [!NOTE]
> <span data-ttu-id="75202-115">Všimněte si, že kroky 1 až 3, které zahrnují vytváření mapa aktualizace, se dají provést nezávisle na instalaci aktualizace nezměnilo.</span><span class="sxs-lookup"><span data-stu-id="75202-115">Note that steps 1 through 3, which cover the creation of the update map, may be performed independently of applying the update.</span></span> <span data-ttu-id="75202-116">Běžný scénář, že pracovní postup pro vývojáře se vytvořit mapa aktualizace do režimu offline a pak správce použije aktualizace později.</span><span class="sxs-lookup"><span data-stu-id="75202-116">A common scenario that the workflow developer will create the update map offline, and then an administrator will apply the update at a later time.</span></span>

<span data-ttu-id="75202-117">Toto téma obsahuje přehled procesu dynamické aktualizace do trvalé instanci pracovního postupu Xaml kompilované přidat novou aktivitu.</span><span class="sxs-lookup"><span data-stu-id="75202-117">This topic provides an overview of the dynamic update process of adding a new activity to a persisted instance of a compiled Xaml workflow.</span></span>

### <a name="Prepare"></a> <span data-ttu-id="75202-118">Příprava pro dynamickou aktualizaci definice pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="75202-118">Prepare the workflow definition for dynamic update</span></span>

<span data-ttu-id="75202-119">Prvním krokem v procesu dynamické aktualizace je k přípravě definice pracovního postupu požadované aktualizace.</span><span class="sxs-lookup"><span data-stu-id="75202-119">The first step in the dynamic update process is to prepare the desired workflow definition for update.</span></span> <span data-ttu-id="75202-120">To se provádí pomocí volání <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> metoda a předání v definici pracovního postupu, který chcete upravit.</span><span class="sxs-lookup"><span data-stu-id="75202-120">This is done by calling the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> method and passing in the workflow definition to modify.</span></span> <span data-ttu-id="75202-121">Tato metoda ověří a pak vás stromu pracovního postupu k identifikaci všech objektů, například veřejné a proměnné, které musí být označené, můžete později porovnat s definicí změny pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="75202-121">This method validates and then walks the workflow tree to identify all of the objects such as public activities and variables that need to be tagged so they can be compared later with the modified workflow definition.</span></span> <span data-ttu-id="75202-122">Po jejím dokončení, stromu pracovního postupu klonovat a připojené k původní definici pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="75202-122">When this is complete, the workflow tree is cloned and attached to the original workflow definition.</span></span> <span data-ttu-id="75202-123">Při aktualizaci mapy, aktualizovaná verze definice pracovního postupu je ve srovnání s původní definici pracovního postupu a mapa aktualizace je generován a základě rozdíly.</span><span class="sxs-lookup"><span data-stu-id="75202-123">When the update map is created, the updated version of the workflow definition is compared with the original workflow definition and the update map is generated based on the differences.</span></span>

<span data-ttu-id="75202-124">Příprava pracovní postup Xaml pro dynamické aktualizace, které mohou být načteny do <xref:System.Activities.ActivityBuilder>a pak <xref:System.Activities.ActivityBuilder> je předána do <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="75202-124">To prepare a Xaml workflow for dynamic update it may be loaded into an <xref:System.Activities.ActivityBuilder>, and then the <xref:System.Activities.ActivityBuilder> is passed into <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>.</span></span>

> [!NOTE]
> <span data-ttu-id="75202-125">Další informace o práci s serializovat pracovních postupů a <xref:System.Activities.ActivityBuilder>, naleznete v tématu [serializace pracovních postupů a aktivit do a z XAML](serializing-workflows-and-activities-to-and-from-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="75202-125">For more information about working with serialized workflows and <xref:System.Activities.ActivityBuilder>, see [Serializing Workflows and Activities to and from XAML](serializing-workflows-and-activities-to-and-from-xaml.md).</span></span>

<span data-ttu-id="75202-126">V následujícím příkladu `MortgageWorkflow` definice (, který se skládá z <xref:System.Activities.Statements.Sequence> s několika podřízených aktivit) je načteno do <xref:System.Activities.ActivityBuilder>a pak připraví se dynamická aktualizace.</span><span class="sxs-lookup"><span data-stu-id="75202-126">In the following example, a `MortgageWorkflow` definition (that consists of a <xref:System.Activities.Statements.Sequence> with several child activities) is loaded into an <xref:System.Activities.ActivityBuilder>, and then prepared for dynamic update.</span></span> <span data-ttu-id="75202-127">Po vrácení metody, <xref:System.Activities.ActivityBuilder> obsahuje původní definici pracovního postupu, stejně jako kopii.</span><span class="sxs-lookup"><span data-stu-id="75202-127">After the method returns, the <xref:System.Activities.ActivityBuilder> contains the original workflow definition as well as a copy.</span></span>

```csharp
// Load the MortgageWorkflow definition from Xaml into
// an ActivityBuilder.
XamlXmlReaderSettings readerSettings = new XamlXmlReaderSettings()
{
    LocalAssembly = Assembly.GetExecutingAssembly()
};

XamlXmlReader xamlReader = new XamlXmlReader(@"C:\WorkflowDefinitions\MortgageWorkflow.xaml",
    readerSettings);

ActivityBuilder ab = XamlServices.Load(
    ActivityXamlServices.CreateBuilderReader(xamlReader)) as ActivityBuilder;

// Prepare the workflow definition for dynamic update.
DynamicUpdateServices.PrepareForUpdate(ab);
```

> [!NOTE]
> <span data-ttu-id="75202-128">Pokud chcete stáhnout ukázkový kód, který doprovází v tomto tématu, navštivte [dynamická aktualizace vzorového kódu](https://go.microsoft.com/fwlink/?LinkId=227905).</span><span class="sxs-lookup"><span data-stu-id="75202-128">To download the sample code that accompanies this topic, see [Dynamic Update sample code](https://go.microsoft.com/fwlink/?LinkId=227905).</span></span>

### <a name="Update"></a> <span data-ttu-id="75202-129">Aktualizace definice pracovního postupu tak, aby odrážely požadované změny</span><span class="sxs-lookup"><span data-stu-id="75202-129">Update the workflow definition to reflect the desired changes</span></span>

<span data-ttu-id="75202-130">Jakmile definice pracovního postupu je připraven na aktualizace, můžete provést požadované změny.</span><span class="sxs-lookup"><span data-stu-id="75202-130">Once the workflow definition has been prepared for updating, the desired changes can be made.</span></span> <span data-ttu-id="75202-131">Můžete přidat nebo odebrat aktivity, přidat, přesunout nebo odstranit veřejné proměnné, přidat nebo odebrat argumenty a provést změny podpis delegátů aktivit.</span><span class="sxs-lookup"><span data-stu-id="75202-131">You can add or remove activities, add, move or delete public variables, add or remove arguments, and make changes to the signature of activity delegates.</span></span> <span data-ttu-id="75202-132">Nelze odebrat aktivitu spuštěné nebo změnit signaturu spuštěné delegáta.</span><span class="sxs-lookup"><span data-stu-id="75202-132">You cannot remove a running activity or change the signature of a running delegate.</span></span> <span data-ttu-id="75202-133">Mohou být provedeny tyto změny pomocí kódu, nebo v okně návrháře znovu hostovaných pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="75202-133">These changes may be made using code, or in a re-hosted workflow designer.</span></span> <span data-ttu-id="75202-134">V následujícím příkladu, vlastní `VerifyAppraisal` je aktivita přidána do sekvenci, která tvoří text `MortgageWorkflow` z předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="75202-134">In the following example, a custom `VerifyAppraisal` activity is added to the Sequence that makes up the body of the `MortgageWorkflow` from the previous example.</span></span>

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

### <a name="Create"></a> <span data-ttu-id="75202-135">Vytvoření mapy aktualizace</span><span class="sxs-lookup"><span data-stu-id="75202-135">Create the update map</span></span>

<span data-ttu-id="75202-136">Jakmile se změnila definice pracovního postupu, která byla připravena pro aktualizace, je možné vytvořit mapa aktualizace.</span><span class="sxs-lookup"><span data-stu-id="75202-136">Once the workflow definition that was prepared for update has been modified, the update map can be created.</span></span> <span data-ttu-id="75202-137">Chcete-li vytvořit mapu dynamickou aktualizaci <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> vyvolání metody.</span><span class="sxs-lookup"><span data-stu-id="75202-137">To create a dynamic update map, the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> method is invoked.</span></span> <span data-ttu-id="75202-138">Tím se vrátí <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> , který obsahuje informace o modulu runtime je potřeba upravit trvalé instance práce tak, že může být načten a pokračuje s novou definici pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="75202-138">This returns a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> that contains the information the runtime needs to modify a persisted workflow instance so that it may be loaded and resumed with the new workflow definition.</span></span> <span data-ttu-id="75202-139">V následujícím příkladu se vytvoří dynamickou mapu pro upravené `MortgageWorkflow` definice z předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="75202-139">In the following example, a dynamic map is created for the modified `MortgageWorkflow` definition from the previous example.</span></span>

```csharp
// Create the update map.
DynamicUpdateMap map = DynamicUpdateServices.CreateUpdateMap(ab);
```

<span data-ttu-id="75202-140">Toto mapování aktualizace okamžitě lze upravit instancí pracovních postupů trvalý, nebo více obvykle můžete uložit a aktualizace použity později.</span><span class="sxs-lookup"><span data-stu-id="75202-140">This update map can immediately be used to modify persisted workflow instances, or more typically it can be saved and the updates applied later.</span></span> <span data-ttu-id="75202-141">Jeden způsob, jak uložit mapa aktualizace je určená k serializaci do souboru, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="75202-141">One way to save the update map is to serialize it to a file, as shown in the following example.</span></span>

```csharp
// Serialize the update map to a file.
DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));
using (FileStream fs = System.IO.File.Open(@"C:\WorkflowDefinitions\MortgageWorkflow.map", FileMode.Create))
{
    serializer.WriteObject(fs, map);
}
```

<span data-ttu-id="75202-142">Když <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> definice naklonovaného pracovního postupu a další informace o dynamické aktualizace, která byla přidána při volání funkce vrátí <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> Odebereme, a připraven k uložit tak, aby ji lze později při obnovování aktualizaci definice změny pracovního postupu instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="75202-142">When <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> returns, the cloned workflow definition and other dynamic update information that was added in the call to <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> is removed, and the modified workflow definition is ready to be saved so that it can be used later when resuming updated workflow instances.</span></span> <span data-ttu-id="75202-143">V následujícím příkladu je uložena definice pracovního postupu upravené `MortgageWorkflow_v1.1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="75202-143">In the following example, the modified workflow definition is saved to `MortgageWorkflow_v1.1.xaml`.</span></span>

```csharp
// Save the modified workflow definition.
StreamWriter sw = File.CreateText(@"C:\WorkflowDefinitions\MortgageWorkflow_v1.1.xaml");
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));
XamlServices.Save(xw, ab);
sw.Close();
```

### <a name="Apply"></a> <span data-ttu-id="75202-144">Použijte mapu aktualizace instance požadované trvalá pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="75202-144">Apply the update map to the desired persisted workflow instances</span></span>

<span data-ttu-id="75202-145">Použití mapy aktualizace lze provést kdykoli po jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="75202-145">Applying the update map can be done at any time after creating it.</span></span> <span data-ttu-id="75202-146">Je možné ji provést, okamžitě <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> instance, který byl vrácen <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>, nebo lze provést, pokud později pomocí uložené kopie mapa aktualizace.</span><span class="sxs-lookup"><span data-stu-id="75202-146">It can be done right away using the <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> instance that was returned by <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>, or it can be done later using a saved copy of the update map.</span></span> <span data-ttu-id="75202-147">Aktualizace instance pracovního postupu, načíst je do <xref:System.Activities.WorkflowApplicationInstance> pomocí <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="75202-147">To update a workflow instance, load it into a <xref:System.Activities.WorkflowApplicationInstance> using <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="75202-148">Dále vytvořte <xref:System.Activities.WorkflowApplication> pomocí definice aktualizovaný pracovní postup a požadovaný <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="75202-148">Next, create a <xref:System.Activities.WorkflowApplication> using the updated workflow definition, and the desired <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="75202-149">To <xref:System.Activities.WorkflowIdentity> může být jiný než ten, který byl použit k uchování původní pracovního postupu a aby bylo zřejmé, že byla změněna trvalé instanci je obvykle.</span><span class="sxs-lookup"><span data-stu-id="75202-149">This <xref:System.Activities.WorkflowIdentity> may be different than the one that was used to persist the original workflow, and typically is in order to reflect that the persisted instance has been modified.</span></span> <span data-ttu-id="75202-150">Jednou <xref:System.Activities.WorkflowApplication> je vytvořen, je načteno pomocí přetížení <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> , která přijímá <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>a potom byla uvolněna voláním <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="75202-150">Once the <xref:System.Activities.WorkflowApplication> is created, it is loaded using the overload of <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> that takes a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>, and then unloaded with a call to <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="75202-151">Použije dynamické aktualizace a opakuje instance aktualizovaný pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="75202-151">This applies the dynamic update and persists the updated workflow instance.</span></span>

```csharp
// Load the serialized update map.
DynamicUpdateMap map;
using (FileStream fs = File.Open(@"C:\WorkflowDefinitions\MortgageWorkflow.map", FileMode.Open))
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

### <a name="resuming-an-updated-workflow-instance"></a><span data-ttu-id="75202-152">Obnovení Instance aktualizovaný pracovní postup</span><span class="sxs-lookup"><span data-stu-id="75202-152">Resuming an Updated Workflow Instance</span></span>

<span data-ttu-id="75202-153">Po použití dynamické aktualizace, může být obnoveno instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="75202-153">Once dynamic update has been applied, the workflow instance may be resumed.</span></span> <span data-ttu-id="75202-154">Všimněte si, že nový aktualizované definice a <xref:System.Activities.WorkflowIdentity> musí být použita.</span><span class="sxs-lookup"><span data-stu-id="75202-154">Note that the new updated definition and <xref:System.Activities.WorkflowIdentity> must be used.</span></span>

> [!NOTE]
> <span data-ttu-id="75202-155">Další informace o práci s <xref:System.Activities.WorkflowApplication> a <xref:System.Activities.WorkflowIdentity>, naleznete v tématu [použití WorkflowIdentity a správy verzí](using-workflowidentity-and-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="75202-155">For more information about working with <xref:System.Activities.WorkflowApplication> and <xref:System.Activities.WorkflowIdentity>, see [Using WorkflowIdentity and Versioning](using-workflowidentity-and-versioning.md).</span></span>

<span data-ttu-id="75202-156">V následujícím příkladu `MortgageWorkflow_v1.1.xaml` pracovní postup z předchozího příkladu byl zkompilován a je načten a obnovit pomocí definice aktualizovaný pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="75202-156">In the following example, the `MortgageWorkflow_v1.1.xaml` workflow from the previous example has been compiled, and is loaded and resumed using the updated workflow definition.</span></span>

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
> <span data-ttu-id="75202-157">Pokud chcete stáhnout ukázkový kód, který doprovází v tomto tématu, navštivte [dynamická aktualizace vzorového kódu](https://go.microsoft.com/fwlink/?LinkId=227905).</span><span class="sxs-lookup"><span data-stu-id="75202-157">To download the sample code that accompanies this topic, see [Dynamic Update sample code](https://go.microsoft.com/fwlink/?LinkId=227905).</span></span>
