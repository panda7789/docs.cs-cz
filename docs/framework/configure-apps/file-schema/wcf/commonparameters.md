---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: b9ab4e8ca5a71d54a80d17322b61c83d41af2b40
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673586"
---
# <a name="commonparameters"></a><span data-ttu-id="79d15-101">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="79d15-101">\<commonParameters></span></span>
<span data-ttu-id="79d15-102">Představuje kolekci parametrů, které jsou používány globálně u více služeb.</span><span class="sxs-lookup"><span data-stu-id="79d15-102">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="79d15-103">Tato kolekce bude obvykle obsahují řetězec připojení k databázi, kterou může sdílet trvalé služby.</span><span class="sxs-lookup"><span data-stu-id="79d15-103">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="79d15-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="79d15-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="79d15-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="79d15-105">\<behaviors></span></span>  
<span data-ttu-id="79d15-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="79d15-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="79d15-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="79d15-107">\<behavior></span></span>  
<span data-ttu-id="79d15-108">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="79d15-108">\<workflowRuntime></span></span>  
<span data-ttu-id="79d15-109">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="79d15-109">\<commonParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79d15-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79d15-110">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79d15-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="79d15-111">Attributes and Elements</span></span>  
 <span data-ttu-id="79d15-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="79d15-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79d15-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="79d15-113">Attributes</span></span>  
 <span data-ttu-id="79d15-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="79d15-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="79d15-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="79d15-115">Child Elements</span></span>  
  
|<span data-ttu-id="79d15-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="79d15-116">Element</span></span>|<span data-ttu-id="79d15-117">Popis</span><span class="sxs-lookup"><span data-stu-id="79d15-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="79d15-118">\<add></span><span class="sxs-lookup"><span data-stu-id="79d15-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)|<span data-ttu-id="79d15-119">Přidá dvojici název hodnota společné parametry, které používají služby do kolekce.</span><span class="sxs-lookup"><span data-stu-id="79d15-119">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="79d15-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="79d15-120">Parent Elements</span></span>  
  
|<span data-ttu-id="79d15-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="79d15-121">Element</span></span>|<span data-ttu-id="79d15-122">Popis</span><span class="sxs-lookup"><span data-stu-id="79d15-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="79d15-123">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="79d15-123">\<workflowRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowruntime.md)|<span data-ttu-id="79d15-124">Určuje nastavení pro instanci <xref:System.Workflow.Runtime.WorkflowRuntime> pro hostování služby Windows Communication Foundation (WCF) založené na pracovních postupech.</span><span class="sxs-lookup"><span data-stu-id="79d15-124">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79d15-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="79d15-125">Remarks</span></span>  
 <span data-ttu-id="79d15-126">`<commonParameters>` Všechny parametry, které jsou používány globálně u více služeb, například definuje element `ConnectionString` při použití <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span><span class="sxs-lookup"><span data-stu-id="79d15-126">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="79d15-127">Služba sledování SQL Server nepoužívá konzistentně `ConnectionString` hodnotu, pokud je zadán v `<commonParameters>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="79d15-127">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="79d15-128">Některé z jeho operace, třeba načítání `StateMachineWorkflowInstance.StateHistory` vlastnost může selhat.</span><span class="sxs-lookup"><span data-stu-id="79d15-128">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="79d15-129">Chcete-li vyřešit, zadejte `ConnectionString` atribut v konfiguračním oddílu pro zprostředkovatele sledování, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="79d15-129">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  
  
 `<add`  
  
 `type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"`  
  
 `ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />`  
  
 <span data-ttu-id="79d15-130">Pro služby, které potvrdí práci dávek trvalého úložiště, jako například <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> a <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, umožníte jim to chcete zkusit znovu jejich transakce pomocí `EnableRetries` parametru, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="79d15-130">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="79d15-131">Všimněte si, že `EnableRetries` parametr může být nastaven buď na globální úrovni (jak je znázorněno *CommonParameters* části) nebo pro jednotlivé služby, které podporují `EnableRetries` (jak je znázorněno v *služby*části).</span><span class="sxs-lookup"><span data-stu-id="79d15-131">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="79d15-132">Následující ukázkový kód ukazuje, jak programově změnit společných parametrů.</span><span class="sxs-lookup"><span data-stu-id="79d15-132">The following sample code shows how to change the common parameters programmatically.</span></span>  
  
```  
Configuration config=WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");  
WorkflowRuntimeSection wfruntime=config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters=wfruntime.CommonParameters;  
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="79d15-133">Další informace o použití konfiguračního souboru pro řízení chování <xref:System.Workflow.Runtime.WorkflowRuntime> objekt hostitele aplikace Windows Workflow Foundation, najdete v článku [konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="79d15-133">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="79d15-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="79d15-134">Example</span></span>  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="79d15-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79d15-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="79d15-136">[Konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="79d15-136">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [<span data-ttu-id="79d15-137">\<add></span><span class="sxs-lookup"><span data-stu-id="79d15-137">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)
