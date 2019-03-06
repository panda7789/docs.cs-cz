---
title: Rozšiřitelnost Store
ms.date: 03/30/2017
ms.assetid: 7c3f4a46-4bac-4138-ae6a-a7c7ee0d28f5
ms.openlocfilehash: 8f317e8e0864dd6c4595ac669611594c843b277c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375425"
---
# <a name="store-extensibility"></a><span data-ttu-id="b59ee-102">Rozšiřitelnost Store</span><span class="sxs-lookup"><span data-stu-id="b59ee-102">Store Extensibility</span></span>
<span data-ttu-id="b59ee-103"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> umožňuje zvýšit úroveň specifické pro aplikace, vlastní vlastnosti, které lze použít k dotazování pro instance databáze trvalosti.</span><span class="sxs-lookup"><span data-stu-id="b59ee-103"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> allows users to promote custom, application-specific properties that can be used to query for instances in the persistence database.</span></span> <span data-ttu-id="b59ee-104">V rámci podpory vlastnosti způsobí, že hodnota, která má být k dispozici v rámci speciální zobrazení v databázi.</span><span class="sxs-lookup"><span data-stu-id="b59ee-104">The act of promoting a property causes the value to be available within a special view in the database.</span></span> <span data-ttu-id="b59ee-105">Tyto propagované vlastnosti (vlastnosti, které lze použít v uživatelských dotazů) může být jednoduché typy, jako je například Int64, Guid, String a datum a čas nebo typ serializovaného binární (byte[]).</span><span class="sxs-lookup"><span data-stu-id="b59ee-105">These promoted properties (properties that can be used in user queries) can be of simple types such as Int64, Guid, String, and DateTime or of a serialized binary type (byte[]).</span></span>  
  
 <span data-ttu-id="b59ee-106"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Třída nemá <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> metodu, která vám umožní podporovat vlastnost jako vlastnost, která můžete v dotazech použít nedají.</span><span class="sxs-lookup"><span data-stu-id="b59ee-106">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> class has the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> method that you can use to promote a property as a property that can be used in queries.</span></span> <span data-ttu-id="b59ee-107">V následujícím příkladu je příkladem začátku do konce rozšíření úložiště.</span><span class="sxs-lookup"><span data-stu-id="b59ee-107">The following example is an end-to-end example of store extensibility.</span></span>  
  
1.  <span data-ttu-id="b59ee-108">V tomto ukázkovém scénáři má dokument zpracování (DP) aplikací pracovních postupů, z nichž každý používá vlastní aktivity pro zpracování dokumentu.</span><span class="sxs-lookup"><span data-stu-id="b59ee-108">In this example scenario, a document processing (DP) application has workflows, each of which uses custom activities for document processing.</span></span> <span data-ttu-id="b59ee-109">Tyto pracovní postupy mají sadu proměnných stavu, které je potřeba nastavena jako viditelná pro koncového uživatele.</span><span class="sxs-lookup"><span data-stu-id="b59ee-109">These workflows have a set of state variables that need to be made visible to the end user.</span></span> <span data-ttu-id="b59ee-110">K dosažení tohoto distribučního bodu aplikace poskytuje rozšíření instance typu <xref:System.Activities.Persistence.PersistenceParticipant>, které používají aktivity slouží k poskytování proměnné stavu.</span><span class="sxs-lookup"><span data-stu-id="b59ee-110">To achieve this, the DP application provides an instance extension of type <xref:System.Activities.Persistence.PersistenceParticipant>, which is used by activities to supply the state variables.</span></span>  
  
    ```  
    class DocumentStatusExtension : PersistenceParticipant  
    {  
        public string DocumentId;  
        public string ApprovalStatus;  
        public string UserName;  
        public DateTime LastUpdateTime;  
    }  
    ```  
  
2.  <span data-ttu-id="b59ee-111">Nové rozšíření se pak přidá do hostitele.</span><span class="sxs-lookup"><span data-stu-id="b59ee-111">The new extension is then added to the host.</span></span>  
  
    ```  
    static Activity workflow = CreateWorkflow();  
    WorkflowApplication application = new WorkflowApplication(workflow);  
    DocumentStatusExtension documentStatusExtension = new DocumentStatusExtension ();  
    application.Extensions.Add(documentStatusExtension);  
    ```  
  
     <span data-ttu-id="b59ee-112">Další podrobnosti o přidání vlastního účastníka trvalosti najdete v článku [účastníci trvalosti](../../../docs/framework/windows-workflow-foundation/persistence-participants.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="b59ee-112">For more details about adding a custom persistence participant, see the [Persistence Participants](../../../docs/framework/windows-workflow-foundation/persistence-participants.md) sample.</span></span>  
  
3.  <span data-ttu-id="b59ee-113">Vlastní aktivity v aplikaci distribučního bodu naplnění různých polí stav v **Execute** metody.</span><span class="sxs-lookup"><span data-stu-id="b59ee-113">The custom activities in the DP application populate various status fields in the **Execute** method.</span></span>  
  
    ```  
    public override void Execute(CodeActivityContext context)  
    {  
        // ...  
        context.GetExtension<DocumentStatusExtension>().DocumentId = Guid.NewGuid();  
        context.GetExtension<DocumentStatusExtension>().UserName = "John Smith";  
        context.GetExtension<DocumentStatusExtension>().ApprovalStatus = "Approved";  
        context.GetExtension<DocumentStatusExtension>().LastUpdateTime = DateTime.Now();  
        // ...  
    }  
    ```  
  
4.  <span data-ttu-id="b59ee-114">Instance pracovního postupu dosáhne bod trvalost **CollectValues** metodu **DocumentStatusExtension** trvalého účastníka trvalosti dat uloží tyto vlastnosti kolekce.</span><span class="sxs-lookup"><span data-stu-id="b59ee-114">When a workflow instance reaches a persistence point, the **CollectValues** method of the **DocumentStatusExtension** persistence participant saves these properties into the persistence data collection.</span></span>  
  
    ```  
    class DocumentStatusExtension : PersistenceParticipant  
    {  
        const XNamespace xNS = XNamespace.Get("http://contoso.com/DocumentStatus");  
  
        protected override void CollectValues(out IDictionary<XName, object> readWriteValues, out IDictionary<XName, object> writeOnlyValues)  
        {  
            readWriteValues = new Dictionary<XName, object>();  
            readWriteValues.Add(xNS.GetName("UserName"), this.UserName);  
            readWriteValues.Add(xNS.GetName("ApprovalStatus"), this.ApprovalStatus);  
            readWriteValues.Add(xNS.GetName("DocumentId"), this.DocumentId);  
            readWriteValues.Add(xNS.GetName("LastModifiedTime"), this.LastUpdateTime);  
  
            writeOnlyValues = null;  
        }  
        // ...  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="b59ee-115">Všechny tyto vlastnosti jsou předány **SqlWorkflowInstanceStore** rozhraním trvalost prostřednictvím **SaveWorkflowCommand.InstanceData** kolekce.</span><span class="sxs-lookup"><span data-stu-id="b59ee-115">All these properties are passed to **SqlWorkflowInstanceStore** by the persistence framework through the **SaveWorkflowCommand.InstanceData** collection.</span></span>  
  
5.  <span data-ttu-id="b59ee-116">Distribučního bodu aplikace inicializuje Store Instance pracovního postupu SQL a vyvolá **povýšit** metoda podporovat tato data.</span><span class="sxs-lookup"><span data-stu-id="b59ee-116">The DP application initializes the SQL Workflow Instance Store and invokes the **Promote** method to promote this data.</span></span>  
  
    ```  
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);  
  
    List<XName> variantProperties = new List<XName>()   
    {   
        xNS.GetName("UserName"),   
        xNS.GetName("ApprovalStatus"),   
        xNS.GetName("DocumentId"),   
        xNS.GetName("LastModifiedTime")   
    };  
  
    store.Promote("DocumentStatus", variantProperties, null);  
    ```  
  
     <span data-ttu-id="b59ee-117">Na základě těchto informací povýšení **SqlWorkflowInstanceStore** umístí vlastnosti dat sloupců [InstancePromotedProperties](#InstancePromotedProperties) zobrazení.</span><span class="sxs-lookup"><span data-stu-id="b59ee-117">Based on this promotion information, **SqlWorkflowInstanceStore** places the data properties in the columns of the [InstancePromotedProperties](#InstancePromotedProperties) view.</span></span>
  
6.  <span data-ttu-id="b59ee-118">Pro dotaz na podmnožinu dat z tabulky povýšení, distribučního bodu aplikace přidá vlastní zobrazení nad zobrazení povýšení.</span><span class="sxs-lookup"><span data-stu-id="b59ee-118">To query a subset of the data from the promotion table, the DP application adds a customized view on top of the promotion view.</span></span>  
  
    ```  
    create view [dbo].[DocumentStatus] with schemabinding  
    as  
        select  P.[InstanceId] as [InstanceId],  
            P.Value1 as [UserName],  
            P.Value2 as [ApprovalStatus],  
            P.Value3 as [DocumentId],  
            P.Value4 as [LastUpdatedTime]  
    from [System.Activities.DurableInstancing].[InstancePromotedProperties] as P  
    where P.PromotionName = N'DocumentStatus'  
    go  
    ```  
  
## <a name="InstancePromotedProperties"></a> <span data-ttu-id="b59ee-119">Zobrazení [System.Activities.DurableInstancing.InstancePromotedProperties]</span><span class="sxs-lookup"><span data-stu-id="b59ee-119">[System.Activities.DurableInstancing.InstancePromotedProperties] view</span></span>  
  
|<span data-ttu-id="b59ee-120">Název sloupce</span><span class="sxs-lookup"><span data-stu-id="b59ee-120">Column Name</span></span>|<span data-ttu-id="b59ee-121">Typ sloupce</span><span class="sxs-lookup"><span data-stu-id="b59ee-121">Column Type</span></span>|<span data-ttu-id="b59ee-122">Popis</span><span class="sxs-lookup"><span data-stu-id="b59ee-122">Description</span></span>|  
|-----------------|-----------------|-----------------|  
|<span data-ttu-id="b59ee-123">InstanceId</span><span class="sxs-lookup"><span data-stu-id="b59ee-123">InstanceId</span></span>|<span data-ttu-id="b59ee-124">GUID</span><span class="sxs-lookup"><span data-stu-id="b59ee-124">GUID</span></span>|<span data-ttu-id="b59ee-125">Instance pracovního postupu patřící do této propagační akce.</span><span class="sxs-lookup"><span data-stu-id="b59ee-125">The workflow instance that this promotion belongs to.</span></span>|  
|<span data-ttu-id="b59ee-126">PromotionName</span><span class="sxs-lookup"><span data-stu-id="b59ee-126">PromotionName</span></span>|<span data-ttu-id="b59ee-127">nvarchar(400)</span><span class="sxs-lookup"><span data-stu-id="b59ee-127">nvarchar(400)</span></span>|<span data-ttu-id="b59ee-128">Název povýšení, samotného.</span><span class="sxs-lookup"><span data-stu-id="b59ee-128">The name of the promotion itself.</span></span>|  
|<span data-ttu-id="b59ee-129">Hodnota1, hodnota2, hodnota3,..., Value32</span><span class="sxs-lookup"><span data-stu-id="b59ee-129">Value1, Value2, Value3,..,Value32</span></span>|<span data-ttu-id="b59ee-130">SQL_VARIANT</span><span class="sxs-lookup"><span data-stu-id="b59ee-130">sql_variant</span></span>|<span data-ttu-id="b59ee-131">Hodnota samotné propagované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b59ee-131">The value of the promoted property itself.</span></span> <span data-ttu-id="b59ee-132">Většina primitivní datové typy SQL s výjimkou binární objekty BLOB a víc než 8 000 bajtů délku řetězce lze zobrazit v sql_variant.</span><span class="sxs-lookup"><span data-stu-id="b59ee-132">Most SQL primitive data types except binary blobs and strings over 8000 bytes in length can fit in sql_variant.</span></span>|  
|<span data-ttu-id="b59ee-133">Value33 Value34, Value35,..., Value64</span><span class="sxs-lookup"><span data-stu-id="b59ee-133">Value33, Value34, Value35, …, Value64</span></span>|<span data-ttu-id="b59ee-134">Varbinary(max)</span><span class="sxs-lookup"><span data-stu-id="b59ee-134">varbinary(max)</span></span>|<span data-ttu-id="b59ee-135">Hodnoty propagované vlastnosti, které jsou explicitně deklarovány jako varbinary(max).</span><span class="sxs-lookup"><span data-stu-id="b59ee-135">The value of promoted properties that are explicitly declared as varbinary(max).</span></span>|
