---
title: '&lt;add&gt; – &lt;commonParameters&gt;'
ms.date: 03/30/2017
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
ms.openlocfilehash: 431a4b6a58a0c2d2ecd6c448e05e7f2104dd10ed
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145195"
---
# <a name="ltaddgt-of-ltcommonparametersgt"></a><span data-ttu-id="b0d47-102">&lt;add&gt; – &lt;commonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="b0d47-102">&lt;add&gt; of &lt;commonParameters&gt;</span></span>
<span data-ttu-id="b0d47-103">Určuje dvojice název hodnota parametrů, které jsou používány globálně u více služeb.</span><span class="sxs-lookup"><span data-stu-id="b0d47-103">Specifies a name-value pair of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="b0d47-104">Obvykle tento parametr obsahuje připojovací řetězec databáze, kterou může sdílet trvalé služby.</span><span class="sxs-lookup"><span data-stu-id="b0d47-104">Typically this parameter includes the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="b0d47-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b0d47-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="b0d47-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="b0d47-106">\<behaviors></span></span>  
<span data-ttu-id="b0d47-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b0d47-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="b0d47-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="b0d47-108">\<behavior></span></span>  
<span data-ttu-id="b0d47-109">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="b0d47-109">\<workflowRuntime></span></span>  
<span data-ttu-id="b0d47-110">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="b0d47-110">\<commonParameters></span></span>  
<span data-ttu-id="b0d47-111">\<add></span><span class="sxs-lookup"><span data-stu-id="b0d47-111">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0d47-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0d47-112">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String" value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0d47-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b0d47-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b0d47-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b0d47-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0d47-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="b0d47-115">Attributes</span></span>  
  
|<span data-ttu-id="b0d47-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="b0d47-116">Attribute</span></span>|<span data-ttu-id="b0d47-117">Popis</span><span class="sxs-lookup"><span data-stu-id="b0d47-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b0d47-118">name</span><span class="sxs-lookup"><span data-stu-id="b0d47-118">name</span></span>|<span data-ttu-id="b0d47-119">Název parametru určeného pro službu.</span><span class="sxs-lookup"><span data-stu-id="b0d47-119">The name of the parameter specified for a service.</span></span>|  
|<span data-ttu-id="b0d47-120">value</span><span class="sxs-lookup"><span data-stu-id="b0d47-120">value</span></span>|<span data-ttu-id="b0d47-121">Hodnota parametru určeného pro službu.</span><span class="sxs-lookup"><span data-stu-id="b0d47-121">The value of the parameter specified for a service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b0d47-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b0d47-122">Child Elements</span></span>  
 <span data-ttu-id="b0d47-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="b0d47-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b0d47-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b0d47-124">Parent Elements</span></span>  
  
|<span data-ttu-id="b0d47-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="b0d47-125">Element</span></span>|<span data-ttu-id="b0d47-126">Popis</span><span class="sxs-lookup"><span data-stu-id="b0d47-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b0d47-127">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="b0d47-127">\<commonParameters></span></span>](https://msdn.microsoft.com/library/d0e1e6fc-985a-4713-b7da-194e30dfab4c)|<span data-ttu-id="b0d47-128">Kolekce společných parametrů, které jsou používané službami.</span><span class="sxs-lookup"><span data-stu-id="b0d47-128">A collection of common parameters used by services.</span></span> <span data-ttu-id="b0d47-129">Tato kolekce bude obvykle obsahují řetězec připojení k databázi, kterou může sdílet trvalé služby.</span><span class="sxs-lookup"><span data-stu-id="b0d47-129">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0d47-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b0d47-130">Remarks</span></span>  
 <span data-ttu-id="b0d47-131">`<commonParameters>` Všechny parametry, které jsou používány globálně u více služeb, například definuje element `ConnectionString` při použití <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span><span class="sxs-lookup"><span data-stu-id="b0d47-131">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
 <span data-ttu-id="b0d47-132">Pro služby, které potvrdí práci dávek trvalého úložiště, jako například <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> a <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, umožníte jim to chcete zkusit znovu jejich transakce pomocí `EnableRetries` parametru, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="b0d47-132">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
    <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
         enableRetries="False" />
  </services>
</workflowRuntime>
```  
  
 <span data-ttu-id="b0d47-133">Všimněte si, že `EnableRetries` parametr lze nastavit buď na globální úrovni (jak je znázorněno *CommonParameters* části) nebo pro jednotlivé služby, které podporují `EnableRetries` (jak je znázorněno v *služby*části).</span><span class="sxs-lookup"><span data-stu-id="b0d47-133">Notice that the `EnableRetries` parameter can be set at either a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="b0d47-134">Další informace o použití konfiguračního souboru pro řízení chování <xref:System.Workflow.Runtime.WorkflowRuntime> objekt hostitele aplikace Windows Workflow Foundation, najdete v článku [konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="b0d47-134">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0d47-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0d47-135">Example</span></span>  
  
```xml  
<commonParameters>
  <add name="ConnectionString"
       value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
  <add name="EnableRetries"
       value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="b0d47-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0d47-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>  
 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>  
 <span data-ttu-id="b0d47-137">[Konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="b0d47-137">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>  
 [<span data-ttu-id="b0d47-138">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="b0d47-138">\<commonParameters></span></span>](https://msdn.microsoft.com/library/d0e1e6fc-985a-4713-b7da-194e30dfab4c)
