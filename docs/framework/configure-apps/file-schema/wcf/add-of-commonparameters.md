---
title: <add> z <commonParameters>
ms.date: 03/30/2017
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
ms.openlocfilehash: 6aaba3f82966ad4496e6edaae06b5d7a8aef3863
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673651"
---
# <a name="add-of-commonparameters"></a><span data-ttu-id="bf8ab-102">\<Přidat > z \<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="bf8ab-102">\<add> of \<commonParameters></span></span>
<span data-ttu-id="bf8ab-103">Určuje dvojice název hodnota parametrů, které jsou používány globálně u více služeb.</span><span class="sxs-lookup"><span data-stu-id="bf8ab-103">Specifies a name-value pair of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="bf8ab-104">Obvykle tento parametr obsahuje připojovací řetězec databáze, kterou může sdílet trvalé služby.</span><span class="sxs-lookup"><span data-stu-id="bf8ab-104">Typically this parameter includes the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="bf8ab-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bf8ab-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="bf8ab-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="bf8ab-106">\<behaviors></span></span>  
<span data-ttu-id="bf8ab-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="bf8ab-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="bf8ab-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="bf8ab-108">\<behavior></span></span>  
<span data-ttu-id="bf8ab-109">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="bf8ab-109">\<workflowRuntime></span></span>  
<span data-ttu-id="bf8ab-110">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="bf8ab-110">\<commonParameters></span></span>  
<span data-ttu-id="bf8ab-111">\<add></span><span class="sxs-lookup"><span data-stu-id="bf8ab-111">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf8ab-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf8ab-112">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String" value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf8ab-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bf8ab-113">Attributes and Elements</span></span>  
 <span data-ttu-id="bf8ab-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bf8ab-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf8ab-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="bf8ab-115">Attributes</span></span>  
  
|<span data-ttu-id="bf8ab-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="bf8ab-116">Attribute</span></span>|<span data-ttu-id="bf8ab-117">Popis</span><span class="sxs-lookup"><span data-stu-id="bf8ab-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bf8ab-118">name</span><span class="sxs-lookup"><span data-stu-id="bf8ab-118">name</span></span>|<span data-ttu-id="bf8ab-119">Název parametru určeného pro službu.</span><span class="sxs-lookup"><span data-stu-id="bf8ab-119">The name of the parameter specified for a service.</span></span>|  
|<span data-ttu-id="bf8ab-120">value</span><span class="sxs-lookup"><span data-stu-id="bf8ab-120">value</span></span>|<span data-ttu-id="bf8ab-121">Hodnota parametru určeného pro službu.</span><span class="sxs-lookup"><span data-stu-id="bf8ab-121">The value of the parameter specified for a service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bf8ab-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bf8ab-122">Child Elements</span></span>  
 <span data-ttu-id="bf8ab-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="bf8ab-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bf8ab-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bf8ab-124">Parent Elements</span></span>  
  
|<span data-ttu-id="bf8ab-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="bf8ab-125">Element</span></span>|<span data-ttu-id="bf8ab-126">Popis</span><span class="sxs-lookup"><span data-stu-id="bf8ab-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf8ab-127">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="bf8ab-127">\<commonParameters></span></span>](commonparameters.md)|<span data-ttu-id="bf8ab-128">Kolekce společných parametrů, které jsou používané službami.</span><span class="sxs-lookup"><span data-stu-id="bf8ab-128">A collection of common parameters used by services.</span></span> <span data-ttu-id="bf8ab-129">Tato kolekce bude obvykle obsahují řetězec připojení k databázi, kterou může sdílet trvalé služby.</span><span class="sxs-lookup"><span data-stu-id="bf8ab-129">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf8ab-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bf8ab-130">Remarks</span></span>  
 <span data-ttu-id="bf8ab-131">`<commonParameters>` Všechny parametry, které jsou používány globálně u více služeb, například definuje element `ConnectionString` při použití <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span><span class="sxs-lookup"><span data-stu-id="bf8ab-131">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
 <span data-ttu-id="bf8ab-132">Pro služby, které potvrdí práci dávek trvalého úložiště, jako například <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> a <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, umožníte jim to chcete zkusit znovu jejich transakce pomocí `EnableRetries` parametru, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="bf8ab-132">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="bf8ab-133">Všimněte si, že `EnableRetries` parametr lze nastavit buď na globální úrovni (jak je znázorněno *CommonParameters* části) nebo pro jednotlivé služby, které podporují `EnableRetries` (jak je znázorněno v *služby*části).</span><span class="sxs-lookup"><span data-stu-id="bf8ab-133">Notice that the `EnableRetries` parameter can be set at either a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="bf8ab-134">Další informace o použití konfiguračního souboru pro řízení chování <xref:System.Workflow.Runtime.WorkflowRuntime> objekt hostitele aplikace Windows Workflow Foundation, najdete v článku [konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="bf8ab-134">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf8ab-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="bf8ab-135">Example</span></span>  
  
```xml  
<commonParameters>
  <add name="ConnectionString"
       value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
  <add name="EnableRetries"
       value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="bf8ab-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf8ab-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="bf8ab-137">[Konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="bf8ab-137">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [<span data-ttu-id="bf8ab-138">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="bf8ab-138">\<commonParameters></span></span>](commonparameters.md)
