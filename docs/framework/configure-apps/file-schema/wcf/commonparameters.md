---
title: '&lt;commonParameters&gt;'
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: 5e4c19c48709ffd81cb00e9820e6c3cdb297ec7e
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45529027"
---
# <a name="ltcommonparametersgt"></a><span data-ttu-id="677f1-102">&lt;commonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="677f1-102">&lt;commonParameters&gt;</span></span>
<span data-ttu-id="677f1-103">Představuje kolekci parametrů, které jsou používány globálně u více služeb.</span><span class="sxs-lookup"><span data-stu-id="677f1-103">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="677f1-104">Tato kolekce bude obvykle obsahují řetězec připojení k databázi, kterou může sdílet trvalé služby.</span><span class="sxs-lookup"><span data-stu-id="677f1-104">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="677f1-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="677f1-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="677f1-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="677f1-106">\<behaviors></span></span>  
<span data-ttu-id="677f1-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="677f1-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="677f1-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="677f1-108">\<behavior></span></span>  
<span data-ttu-id="677f1-109">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="677f1-109">\<workflowRuntime></span></span>  
<span data-ttu-id="677f1-110">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="677f1-110">\<commonParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="677f1-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="677f1-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>  
   <commonParameters>  
      <add name="String" value="String" />  
   </commonParameters>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="677f1-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="677f1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="677f1-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="677f1-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="677f1-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="677f1-114">Attributes</span></span>  
 <span data-ttu-id="677f1-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="677f1-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="677f1-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="677f1-116">Child Elements</span></span>  
  
|<span data-ttu-id="677f1-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="677f1-117">Element</span></span>|<span data-ttu-id="677f1-118">Popis</span><span class="sxs-lookup"><span data-stu-id="677f1-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="677f1-119">\<add></span><span class="sxs-lookup"><span data-stu-id="677f1-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)|<span data-ttu-id="677f1-120">Přidá dvojici název hodnota společné parametry, které používají služby do kolekce.</span><span class="sxs-lookup"><span data-stu-id="677f1-120">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="677f1-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="677f1-121">Parent Elements</span></span>  
  
|<span data-ttu-id="677f1-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="677f1-122">Element</span></span>|<span data-ttu-id="677f1-123">Popis</span><span class="sxs-lookup"><span data-stu-id="677f1-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="677f1-124">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="677f1-124">\<workflowRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowruntime.md)|<span data-ttu-id="677f1-125">Určuje nastavení pro instanci <xref:System.Workflow.Runtime.WorkflowRuntime> pro hostování služby Windows Communication Foundation (WCF) založené na pracovních postupech.</span><span class="sxs-lookup"><span data-stu-id="677f1-125">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="677f1-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="677f1-126">Remarks</span></span>  
 <span data-ttu-id="677f1-127">`<commonParameters>` Všechny parametry, které jsou používány globálně u více služeb, například definuje element `ConnectionString` při použití <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span><span class="sxs-lookup"><span data-stu-id="677f1-127">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="677f1-128">Služba sledování SQL Server nepoužívá konzistentně `ConnectionString` hodnotu, pokud je zadán v `<commonParameters>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="677f1-128">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="677f1-129">Některé z jeho operace, třeba načítání `StateMachineWorkflowInstance.StateHistory` vlastnost může selhat.</span><span class="sxs-lookup"><span data-stu-id="677f1-129">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="677f1-130">Chcete-li vyřešit, zadejte `ConnectionString` atribut v konfiguračním oddílu pro zprostředkovatele sledování, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="677f1-130">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  
  
 `<add`  
  
 `type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"`  
  
 `ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />`  
  
 <span data-ttu-id="677f1-131">Pro služby, které potvrdí práci dávek trvalého úložiště, jako například <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> a <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, umožníte jim to chcete zkusit znovu jejich transakce pomocí `EnableRetries` parametru, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="677f1-131">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
```xml  
<WorkflowRuntime Name="SampleApplication" UnloadOnIdle="false">  
    <commonParameters>  
        <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />  
        <add name="EnableRetries" value="True" />  
    </commonParameters>  
    <Services>  
        <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" EnableRetries="False" />   
     </Services>  
</WorkflowRuntime>  
```  
  
 <span data-ttu-id="677f1-132">Všimněte si, že `EnableRetries` parametr může být nastaven buď na globální úrovni (jak je znázorněno *CommonParameters* části) nebo pro jednotlivé služby, které podporují `EnableRetries` (jak je znázorněno v *služby*části).</span><span class="sxs-lookup"><span data-stu-id="677f1-132">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="677f1-133">Následující ukázkový kód ukazuje, jak programově změnit společných parametrů.</span><span class="sxs-lookup"><span data-stu-id="677f1-133">The following sample code shows how to change the common parameters programmatically.</span></span>  
  
```  
Configuration config=WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");  
WorkflowRuntimeSection wfruntime=config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters=wfruntime.CommonParameters;  
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="677f1-134">Další informace o použití konfiguračního souboru pro řízení chování <xref:System.Workflow.Runtime.WorkflowRuntime> objekt hostitele aplikace Windows Workflow Foundation, najdete v článku [konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="677f1-134">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="677f1-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="677f1-135">Example</span></span>  
  
```xml  
<commonParameters>  
   <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;"/>  
   <add name="EnableRetries" value="true"/>  
</commonParameters>  
```  
  
## <a name="see-also"></a><span data-ttu-id="677f1-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="677f1-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>  
 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>  
 <span data-ttu-id="677f1-137">[Konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="677f1-137">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>  
 [<span data-ttu-id="677f1-138">\<add></span><span class="sxs-lookup"><span data-stu-id="677f1-138">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)
