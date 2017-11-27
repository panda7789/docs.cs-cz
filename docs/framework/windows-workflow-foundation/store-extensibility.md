---
title: "Rozšíření úložiště"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c3f4a46-4bac-4138-ae6a-a7c7ee0d28f5
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f6700fe67d151e78c8b216d93a4cd7098ed6401d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="store-extensibility"></a><span data-ttu-id="30ecf-102">Rozšíření úložiště</span><span class="sxs-lookup"><span data-stu-id="30ecf-102">Store Extensibility</span></span>
<span data-ttu-id="30ecf-103"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>umožňuje uživatelům povýšit specifické pro aplikace, vlastní vlastnosti, které lze použít k dotazu pro instance v databázi trvalost.</span><span class="sxs-lookup"><span data-stu-id="30ecf-103"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> allows users to promote custom, application-specific properties that can be used to query for instances in the persistence database.</span></span> <span data-ttu-id="30ecf-104">Operace povýšení vlastnost způsobí, že hodnota, která má být k dispozici v rámci speciální zobrazení v databázi.</span><span class="sxs-lookup"><span data-stu-id="30ecf-104">The act of promoting a property causes the value to be available within a special view in the database.</span></span> <span data-ttu-id="30ecf-105">Tyto vlastnosti propagovaných (vlastnosti, které lze použít v dotazech uživatele) může být jednoduché typy, jako je například Int64, Guid, String a data a času nebo serializovaných binárního typu (byte[]).</span><span class="sxs-lookup"><span data-stu-id="30ecf-105">These promoted properties (properties that can be used in user queries) can be of simple types such as Int64, Guid, String, and DateTime or of a serialized binary type (byte[]).</span></span>  
  
 <span data-ttu-id="30ecf-106"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Třída má <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> metodu, kterou můžete použít ke zvýšení úrovně vlastnost jako vlastnost, která lze použít v dotazech.</span><span class="sxs-lookup"><span data-stu-id="30ecf-106">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> class has the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> method that you can use to promote a property as a property that can be used in queries.</span></span> <span data-ttu-id="30ecf-107">V následujícím příkladu je příkladem začátku do konce rozšíření úložiště.</span><span class="sxs-lookup"><span data-stu-id="30ecf-107">The following example is an end-to-end example of store extensibility.</span></span>  
  
1.  <span data-ttu-id="30ecf-108">V tomto ukázkovém scénáři dokumentu zpracování (DP) aplikace má pracovní postupy, z nichž každá používá vlastní aktivity pro zpracování dokumentu.</span><span class="sxs-lookup"><span data-stu-id="30ecf-108">In this example scenario, a document processing (DP) application has workflows, each of which uses custom activities for document processing.</span></span> <span data-ttu-id="30ecf-109">Tyto pracovní postupy mají sadu proměnné stavu, které musí být viditelné pro koncového uživatele.</span><span class="sxs-lookup"><span data-stu-id="30ecf-109">These workflows have a set of state variables that need to be made visible to the end user.</span></span> <span data-ttu-id="30ecf-110">K dosažení tohoto distribučního bodu aplikace poskytuje rozšíření instance typu <xref:System.Activities.Persistence.PersistenceParticipant>, který je využíván jiným aktivity k poskytování proměnné stavu.</span><span class="sxs-lookup"><span data-stu-id="30ecf-110">To achieve this, the DP application provides an instance extension of type <xref:System.Activities.Persistence.PersistenceParticipant>, which is used by activities to supply the state variables.</span></span>  
  
    ```  
    class DocumentStatusExtension : PersistenceParticipant  
    {  
        public string DocumentId;  
        public string ApprovalStatus;  
        public string UserName;  
        public DateTime LastUpdateTime;  
    }  
    ```  
  
2.  <span data-ttu-id="30ecf-111">Nové rozšíření se pak přidá k hostiteli.</span><span class="sxs-lookup"><span data-stu-id="30ecf-111">The new extension is then added to the host.</span></span>  
  
    ```  
    static Activity workflow = CreateWorkflow();  
    WorkflowApplication application = new WorkflowApplication(workflow);  
    DocumentStatusExtension documentStatusExtension = new DocumentStatusExtension ();  
    application.Extensions.Add(documentStatusExtension);  
    ```  
  
     <span data-ttu-id="30ecf-112">Další informace o přidání vlastního účastník najdete v tématu [trvalost účastníky](../../../docs/framework/windows-workflow-foundation/persistence-participants.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="30ecf-112">For more details about adding a custom persistence participant, see the [Persistence Participants](../../../docs/framework/windows-workflow-foundation/persistence-participants.md) sample.</span></span>  
  
3.  <span data-ttu-id="30ecf-113">Vlastní aktivity v aplikaci distribučního bodu naplnění různých polí stav v **Execute** metoda.</span><span class="sxs-lookup"><span data-stu-id="30ecf-113">The custom activities in the DP application populate various status fields in the **Execute** method.</span></span>  
  
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
  
4.  <span data-ttu-id="30ecf-114">Když bod trvalost dosáhne instanci pracovního postupu **CollectValues** metodu **DocumentStatusExtension** trvalost účastník uloží tyto vlastnosti do trvalosti dat kolekce.</span><span class="sxs-lookup"><span data-stu-id="30ecf-114">When a workflow instance reaches a persistence point, the **CollectValues** method of the **DocumentStatusExtension** persistence participant saves these properties into the persistence data collection.</span></span>  
  
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
    >  <span data-ttu-id="30ecf-115">Všechny tyto vlastnosti jsou předány **SqlWorkflowInstanceStore** rámcem trvalost prostřednictvím **SaveWorkflowCommand.InstanceData** kolekce.</span><span class="sxs-lookup"><span data-stu-id="30ecf-115">All these properties are passed to **SqlWorkflowInstanceStore** by the persistence framework through the **SaveWorkflowCommand.InstanceData** collection.</span></span>  
  
5.  <span data-ttu-id="30ecf-116">Distribuční bod aplikace inicializuje ukládání Instance pracovního postupu SQL a vyvolá **povýšit** metoda zvýšení úrovně tato data.</span><span class="sxs-lookup"><span data-stu-id="30ecf-116">The DP application initializes the SQL Workflow Instance Store and invokes the **Promote** method to promote this data.</span></span>  
  
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
  
     <span data-ttu-id="30ecf-117">Na základě této informace povýšení **SqlWorkflowInstanceStore** umístí vlastnosti dat ve sloupcích [InstancePromotedProperties](#InstancePromotedProperties) zobrazení.</span><span class="sxs-lookup"><span data-stu-id="30ecf-117">Based on this promotion information, **SqlWorkflowInstanceStore** places the data properties in the columns of the [InstancePromotedProperties](#InstancePromotedProperties) view.</span></span>
  
6.  <span data-ttu-id="30ecf-118">Pro dotaz na podmnožinu dat z tabulky povýšení, přidá aplikace distribučního bodu přizpůsobené zobrazení nad zobrazení povýšení.</span><span class="sxs-lookup"><span data-stu-id="30ecf-118">To query a subset of the data from the promotion table, the DP application adds a customized view on top of the promotion view.</span></span>  
  
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
  
##  <span data-ttu-id="30ecf-119"><a name="InstancePromotedProperties"></a>Zobrazení [System.Activities.DurableInstancing.InstancePromotedProperties]</span><span class="sxs-lookup"><span data-stu-id="30ecf-119"><a name="InstancePromotedProperties"></a> [System.Activities.DurableInstancing.InstancePromotedProperties] view</span></span>  
  
|<span data-ttu-id="30ecf-120">Název sloupce</span><span class="sxs-lookup"><span data-stu-id="30ecf-120">Column Name</span></span>|<span data-ttu-id="30ecf-121">Typ sloupce</span><span class="sxs-lookup"><span data-stu-id="30ecf-121">Column Type</span></span>|<span data-ttu-id="30ecf-122">Popis</span><span class="sxs-lookup"><span data-stu-id="30ecf-122">Description</span></span>|  
|-----------------|-----------------|-----------------|  
|<span data-ttu-id="30ecf-123">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="30ecf-123">InstanceId</span></span>|<span data-ttu-id="30ecf-124">GUID</span><span class="sxs-lookup"><span data-stu-id="30ecf-124">GUID</span></span>|<span data-ttu-id="30ecf-125">K instanci pracovního postupu, které patří tato povýšení.</span><span class="sxs-lookup"><span data-stu-id="30ecf-125">The workflow instance that this promotion belongs to.</span></span>|  
|<span data-ttu-id="30ecf-126">PromotionName</span><span class="sxs-lookup"><span data-stu-id="30ecf-126">PromotionName</span></span>|<span data-ttu-id="30ecf-127">Nvarchar(400)</span><span class="sxs-lookup"><span data-stu-id="30ecf-127">nvarchar(400)</span></span>|<span data-ttu-id="30ecf-128">Název povýšení sám sebe.</span><span class="sxs-lookup"><span data-stu-id="30ecf-128">The name of the promotion itself.</span></span>|  
|<span data-ttu-id="30ecf-129">Hodnota1, hodnota2, hodnota3,.., Value32</span><span class="sxs-lookup"><span data-stu-id="30ecf-129">Value1, Value2, Value3,..,Value32</span></span>|<span data-ttu-id="30ecf-130">SQL_VARIANT</span><span class="sxs-lookup"><span data-stu-id="30ecf-130">sql_variant</span></span>|<span data-ttu-id="30ecf-131">Hodnota propagovaných samotné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="30ecf-131">The value of the promoted property itself.</span></span> <span data-ttu-id="30ecf-132">V sql_variant vejde na většině primitivní datové typy SQL s výjimkou binární objekty BLOB a více než 8 000 bajtů délku řetězce.</span><span class="sxs-lookup"><span data-stu-id="30ecf-132">Most SQL primitive data types except binary blobs and strings over 8000 bytes in length can fit in sql_variant.</span></span>|  
|<span data-ttu-id="30ecf-133">Value33, Value34, Value35,..., Value64</span><span class="sxs-lookup"><span data-stu-id="30ecf-133">Value33, Value34, Value35, …, Value64</span></span>|<span data-ttu-id="30ecf-134">Varbinary(max)</span><span class="sxs-lookup"><span data-stu-id="30ecf-134">varbinary(max)</span></span>|<span data-ttu-id="30ecf-135">Hodnota propagovaných vlastnosti, které jsou explicitně deklarované jako varbinary(max).</span><span class="sxs-lookup"><span data-stu-id="30ecf-135">The value of promoted properties that are explicitly declared as varbinary(max).</span></span>|
