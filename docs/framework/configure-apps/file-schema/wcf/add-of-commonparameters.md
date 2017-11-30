---
title: "&lt;add&gt; – &lt;commonParameters&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dbdc3b87b0b501ffdbe2d6b16d59e86659b27585
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltcommonparametersgt"></a><span data-ttu-id="b58db-102">&lt;add&gt; – &lt;commonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="b58db-102">&lt;add&gt; of &lt;commonParameters&gt;</span></span>
<span data-ttu-id="b58db-103">Určuje dvojice název hodnota parametry, které jsou použity globálně ve více službách.</span><span class="sxs-lookup"><span data-stu-id="b58db-103">Specifies a name-value pair of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="b58db-104">Tento parametr obvykle obsahuje připojovací řetězec databáze, který může být sdílen trvalé služby.</span><span class="sxs-lookup"><span data-stu-id="b58db-104">Typically this parameter includes the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="b58db-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b58db-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="b58db-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="b58db-106">\<behaviors></span></span>  
<span data-ttu-id="b58db-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b58db-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="b58db-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="b58db-108">\<behavior></span></span>  
<span data-ttu-id="b58db-109">\<modul runtime pracovního postupu ></span><span class="sxs-lookup"><span data-stu-id="b58db-109">\<workflowRuntime></span></span>  
<span data-ttu-id="b58db-110">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="b58db-110">\<commonParameters></span></span>  
<span data-ttu-id="b58db-111">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="b58db-111">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b58db-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b58db-112">Syntax</span></span>  
  
```xml  
<workflowRuntime>  
   <commonParameters>  
      <add name="String" value="String" />  
   </commonParameters>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b58db-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b58db-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b58db-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b58db-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b58db-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="b58db-115">Attributes</span></span>  
  
|<span data-ttu-id="b58db-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="b58db-116">Attribute</span></span>|<span data-ttu-id="b58db-117">Popis</span><span class="sxs-lookup"><span data-stu-id="b58db-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b58db-118">name</span><span class="sxs-lookup"><span data-stu-id="b58db-118">name</span></span>|<span data-ttu-id="b58db-119">Název parametr zadaný pro službu.</span><span class="sxs-lookup"><span data-stu-id="b58db-119">The name of the parameter specified for a service.</span></span>|  
|<span data-ttu-id="b58db-120">value</span><span class="sxs-lookup"><span data-stu-id="b58db-120">value</span></span>|<span data-ttu-id="b58db-121">Hodnota parametru zadaná pro službu.</span><span class="sxs-lookup"><span data-stu-id="b58db-121">The value of the parameter specified for a service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b58db-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b58db-122">Child Elements</span></span>  
 <span data-ttu-id="b58db-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="b58db-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b58db-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b58db-124">Parent Elements</span></span>  
  
|<span data-ttu-id="b58db-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="b58db-125">Element</span></span>|<span data-ttu-id="b58db-126">Popis</span><span class="sxs-lookup"><span data-stu-id="b58db-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b58db-127">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="b58db-127">\<commonParameters></span></span>](http://msdn.microsoft.com/en-us/d0e1e6fc-985a-4713-b7da-194e30dfab4c)|<span data-ttu-id="b58db-128">Kolekce společných parametrů, které jsou používané službami.</span><span class="sxs-lookup"><span data-stu-id="b58db-128">A collection of common parameters used by services.</span></span> <span data-ttu-id="b58db-129">Tato kolekce bude obvykle obsahovat připojovací řetězec databáze, který může být sdílen trvalé služby.</span><span class="sxs-lookup"><span data-stu-id="b58db-129">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b58db-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b58db-130">Remarks</span></span>  
 <span data-ttu-id="b58db-131">`<commonParameters>` Element definuje žádné parametry, které se používají globálně ve více službách, například `ConnectionString` při použití <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span><span class="sxs-lookup"><span data-stu-id="b58db-131">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
 <span data-ttu-id="b58db-132">Pro služby, které potvrdit pracovní dávek trvalost úložiště, jako například <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> a <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, můžete povolit, aby opakujte pokus o jejich transakce pomocí `EnableRetries` parametr, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="b58db-132">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="b58db-133">Všimněte si, že `EnableRetries` parametr je možné nastavit buď na globální úrovni (jak je znázorněno v *CommonParameters* části) nebo pro jednotlivé služby podporující `EnableRetries` (jak je znázorněno v *služby*části).</span><span class="sxs-lookup"><span data-stu-id="b58db-133">Notice that the `EnableRetries` parameter can be set at either a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="b58db-134">Další informace o použití konfiguračního souboru pro řízení chování <xref:System.Workflow.Runtime.WorkflowRuntime> objekt hostitele aplikace Windows Workflow Foundation, najdete v části [konfigurační soubory pracovního postupu](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).</span><span class="sxs-lookup"><span data-stu-id="b58db-134">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b58db-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="b58db-135">Example</span></span>  
  
```xml  
<commonParameters>  
   <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;"/>  
   <add name="EnableRetries" value="true"/>  
</commonParameters>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b58db-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="b58db-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>  
 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>  
 [<span data-ttu-id="b58db-137">Konfigurační soubory pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="b58db-137">Workflow Configuration Files</span></span>](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)  
 [<span data-ttu-id="b58db-138">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="b58db-138">\<commonParameters></span></span>](http://msdn.microsoft.com/en-us/d0e1e6fc-985a-4713-b7da-194e30dfab4c)
