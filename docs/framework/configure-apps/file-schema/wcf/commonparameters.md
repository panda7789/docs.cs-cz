---
title: '&lt;commonParameters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bbb67714a58df0c5ccec86c7eac85a5194d780a5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltcommonparametersgt"></a><span data-ttu-id="9705c-102">&lt;commonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="9705c-102">&lt;commonParameters&gt;</span></span>
<span data-ttu-id="9705c-103">Představuje kolekci parametrů, které se používají globálně ve více službách.</span><span class="sxs-lookup"><span data-stu-id="9705c-103">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="9705c-104">Tato kolekce bude obvykle obsahovat připojovací řetězec databáze, který může být sdílen trvalé služby.</span><span class="sxs-lookup"><span data-stu-id="9705c-104">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="9705c-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="9705c-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="9705c-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="9705c-106">\<behaviors></span></span>  
<span data-ttu-id="9705c-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="9705c-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="9705c-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="9705c-108">\<behavior></span></span>  
<span data-ttu-id="9705c-109">\<modul runtime pracovního postupu ></span><span class="sxs-lookup"><span data-stu-id="9705c-109">\<workflowRuntime></span></span>  
<span data-ttu-id="9705c-110">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="9705c-110">\<commonParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9705c-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9705c-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>  
   <commonParameters>  
      <add name="String" value="String" />  
   </commonParameters>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9705c-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9705c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="9705c-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9705c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9705c-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="9705c-114">Attributes</span></span>  
 <span data-ttu-id="9705c-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="9705c-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9705c-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9705c-116">Child Elements</span></span>  
  
|<span data-ttu-id="9705c-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="9705c-117">Element</span></span>|<span data-ttu-id="9705c-118">Popis</span><span class="sxs-lookup"><span data-stu-id="9705c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9705c-119">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="9705c-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)|<span data-ttu-id="9705c-120">Přidá dvojici název hodnota společné parametry, které používají služby do kolekce.</span><span class="sxs-lookup"><span data-stu-id="9705c-120">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9705c-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9705c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="9705c-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="9705c-122">Element</span></span>|<span data-ttu-id="9705c-123">Popis</span><span class="sxs-lookup"><span data-stu-id="9705c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9705c-124">\<modul runtime pracovního postupu ></span><span class="sxs-lookup"><span data-stu-id="9705c-124">\<workflowRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowruntime.md)|<span data-ttu-id="9705c-125">Určuje nastavení pro instanci <xref:System.Workflow.Runtime.WorkflowRuntime> pro hostování založené na pracovním postupu [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="9705c-125">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9705c-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9705c-126">Remarks</span></span>  
 <span data-ttu-id="9705c-127">`<commonParameters>` Element definuje žádné parametry, které se používají globálně ve více službách, například `ConnectionString` při použití <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span><span class="sxs-lookup"><span data-stu-id="9705c-127">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9705c-128">Služba SQL sledování nepoužívá konzistentně `ConnectionString` hodnotu, pokud je zadána v `<commonParameters>` části.</span><span class="sxs-lookup"><span data-stu-id="9705c-128">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="9705c-129">Některé jeho operací, jako je například načítání `StateMachineWorkflowInstance.StateHistory` vlastnost může selhat.</span><span class="sxs-lookup"><span data-stu-id="9705c-129">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="9705c-130">Chcete-li vyřešit, zadejte `ConnectionString` atribut konfigurační oddíl pro sledování poskytovatele, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9705c-130">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  
  
 `<add`  
  
 `type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"`  
  
 `ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />`  
  
 <span data-ttu-id="9705c-131">Pro služby, které potvrdit pracovní dávek trvalost úložiště, jako například <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> a <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, můžete povolit, aby opakujte pokus o jejich transakce pomocí `EnableRetries` parametr, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9705c-131">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="9705c-132">Všimněte si, že `EnableRetries` parametr může být nastaven buď na globální úrovni (jak je znázorněno v *CommonParameters* části) nebo pro jednotlivé služby podporující `EnableRetries` (jak je znázorněno v *služby*části).</span><span class="sxs-lookup"><span data-stu-id="9705c-132">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="9705c-133">Následující vzorový kód ukazuje, jak změnit společné parametry prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="9705c-133">The following sample code shows how to change the common parameters programmatically.</span></span>  
  
```  
Configuration config=WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");  
WorkflowRuntimeSection wfruntime=config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters=wfruntime.CommonParameters;  
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="9705c-134">Další informace o použití konfiguračního souboru pro řízení chování <xref:System.Workflow.Runtime.WorkflowRuntime> objekt hostitele aplikace Windows Workflow Foundation, najdete v části [konfigurační soubory pracovního postupu](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).</span><span class="sxs-lookup"><span data-stu-id="9705c-134">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9705c-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="9705c-135">Example</span></span>  
  
```xml  
<commonParameters>  
   <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;"/>  
   <add name="EnableRetries" value="true"/>  
</commonParameters>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9705c-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="9705c-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>  
 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>  
 [<span data-ttu-id="9705c-137">Konfigurační soubory pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="9705c-137">Workflow Configuration Files</span></span>](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)  
 [<span data-ttu-id="9705c-138">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="9705c-138">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)
