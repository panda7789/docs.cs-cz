---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: a92a81062e92f832be78af2bfd75270390eaac3e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919497"
---
# <a name="commonparameters"></a><span data-ttu-id="e2094-101">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="e2094-101">\<commonParameters></span></span>
<span data-ttu-id="e2094-102">Představuje kolekci parametrů, které jsou používány globálně v rámci více služeb.</span><span class="sxs-lookup"><span data-stu-id="e2094-102">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="e2094-103">Tato kolekce obvykle zahrnuje připojovací řetězec databáze, který může sdílet trvalé služby.</span><span class="sxs-lookup"><span data-stu-id="e2094-103">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="e2094-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e2094-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e2094-105">\<> chování</span><span class="sxs-lookup"><span data-stu-id="e2094-105">\<behaviors></span></span>  
<span data-ttu-id="e2094-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="e2094-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="e2094-107">\<> chování</span><span class="sxs-lookup"><span data-stu-id="e2094-107">\<behavior></span></span>  
<span data-ttu-id="e2094-108">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="e2094-108">\<workflowRuntime></span></span>  
<span data-ttu-id="e2094-109">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="e2094-109">\<commonParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2094-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2094-110">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2094-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e2094-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e2094-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e2094-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2094-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="e2094-113">Attributes</span></span>  
 <span data-ttu-id="e2094-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="e2094-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e2094-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e2094-115">Child Elements</span></span>  
  
|<span data-ttu-id="e2094-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="e2094-116">Element</span></span>|<span data-ttu-id="e2094-117">Popis</span><span class="sxs-lookup"><span data-stu-id="e2094-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2094-118">\<add></span><span class="sxs-lookup"><span data-stu-id="e2094-118">\<add></span></span>](add-of-commonparameters.md)|<span data-ttu-id="e2094-119">Přidá dvojici název-hodnota společných parametrů používaných službami do kolekce.</span><span class="sxs-lookup"><span data-stu-id="e2094-119">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e2094-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e2094-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e2094-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="e2094-121">Element</span></span>|<span data-ttu-id="e2094-122">Popis</span><span class="sxs-lookup"><span data-stu-id="e2094-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2094-123">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="e2094-123">\<workflowRuntime></span></span>](workflowruntime.md)|<span data-ttu-id="e2094-124">Určuje nastavení pro instanci <xref:System.Workflow.Runtime.WorkflowRuntime> pro hostování služeb Windows Communication Foundation založených na pracovních postupech (WCF).</span><span class="sxs-lookup"><span data-stu-id="e2094-124">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2094-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2094-125">Remarks</span></span>  
 <span data-ttu-id="e2094-126">Element definuje všechny parametry, které jsou používány globálně v rámci více služeb, například `ConnectionString` při použití <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>. `<commonParameters>`</span><span class="sxs-lookup"><span data-stu-id="e2094-126">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e2094-127">Služba sledování SQL tuto `ConnectionString` hodnotu konzistentně nepoužívá, pokud je uvedena `<commonParameters>` v části.</span><span class="sxs-lookup"><span data-stu-id="e2094-127">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="e2094-128">Některé jeho operace, jako je například načtení `StateMachineWorkflowInstance.StateHistory` vlastnosti, mohou selhat.</span><span class="sxs-lookup"><span data-stu-id="e2094-128">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="e2094-129">Chcete-li tento problém vyřešit `ConnectionString` , zadejte atribut v oddílu konfigurace pro zprostředkovatele sledování, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e2094-129">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  
  
 `<add`  
  
 `type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"`  
  
 `ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />`  
  
 <span data-ttu-id="e2094-130">Pro služby, které potvrzují pracovní dávky do úložišť pro uchovávání <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>dat, například <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> a, je můžete povolit, aby znovu opakovaly `EnableRetries` svou transakci pomocí parametru, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e2094-130">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
```xml  
<workflowRuntime name="SampleApplication"
                 unloadOnIdle="false">
  <commonParameters>
    <add name="ConnectionString"
         value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
    <add name="EnableRetries"
         value="True" />
  </commonParameters>
  <services>
    <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime,
               Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
         enableRetries="False" />
  </services>
</workflowRuntime>
```  
  
 <span data-ttu-id="e2094-131">Všimněte si, `EnableRetries` že parametr lze nastavit buď na globální úrovni (jak je uvedeno v části *CommonParameters* ), nebo pro jednotlivé služby, které `EnableRetries` podporují (jak je uvedeno v části *služby* ).</span><span class="sxs-lookup"><span data-stu-id="e2094-131">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="e2094-132">Následující vzorový kód ukazuje, jak změnit společné parametry programově.</span><span class="sxs-lookup"><span data-stu-id="e2094-132">The following sample code shows how to change the common parameters programmatically.</span></span>  
  
```  
Configuration config=WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");  
WorkflowRuntimeSection wfruntime=config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters=wfruntime.CommonParameters;  
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="e2094-133">Další informace o tom, jak pomocí konfiguračního souboru řídit chování <xref:System.Workflow.Runtime.WorkflowRuntime> objektu programovací model Windows Workflow Foundation hostitelské aplikace, najdete v tématu [konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="e2094-133">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2094-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="e2094-134">Example</span></span>  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="e2094-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2094-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="e2094-136">[Konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="e2094-136">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [<span data-ttu-id="e2094-137">\<add></span><span class="sxs-lookup"><span data-stu-id="e2094-137">\<add></span></span>](add-of-commonparameters.md)
