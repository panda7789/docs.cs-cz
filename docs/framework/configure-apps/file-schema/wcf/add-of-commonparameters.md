---
title: <add> z <commonParameters>
ms.date: 03/30/2017
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
ms.openlocfilehash: d682acd7fff6bab2c66660a028f8a75b780e21d2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400670"
---
# <a name="add-of-commonparameters"></a><span data-ttu-id="159bf-102">\<Přidat > \<> commonParameters</span><span class="sxs-lookup"><span data-stu-id="159bf-102">\<add> of \<commonParameters></span></span>
<span data-ttu-id="159bf-103">Určuje dvojici název-hodnota parametrů, které jsou používány globálně v rámci více služeb.</span><span class="sxs-lookup"><span data-stu-id="159bf-103">Specifies a name-value pair of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="159bf-104">Tento parametr obvykle zahrnuje připojovací řetězec databáze, který může být sdílen trvalými službami.</span><span class="sxs-lookup"><span data-stu-id="159bf-104">Typically this parameter includes the database connection string that might be shared by durable services.</span></span>  
  
<span data-ttu-id="159bf-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="159bf-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="159bf-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="159bf-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="159bf-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="159bf-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="159bf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="159bf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="159bf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="159bf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="159bf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> aktivity typu workflowRuntime**](workflowruntime.md)</span><span class="sxs-lookup"><span data-stu-id="159bf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)</span></span>\
<span data-ttu-id="159bf-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<commonParameters >** ](commonparameters.md)</span><span class="sxs-lookup"><span data-stu-id="159bf-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<commonParameters>**](commonparameters.md)</span></span>\
<span data-ttu-id="159bf-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="159bf-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="159bf-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="159bf-113">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String" value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="159bf-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="159bf-114">Attributes and Elements</span></span>  
 <span data-ttu-id="159bf-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="159bf-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="159bf-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="159bf-116">Attributes</span></span>  
  
|<span data-ttu-id="159bf-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="159bf-117">Attribute</span></span>|<span data-ttu-id="159bf-118">Popis</span><span class="sxs-lookup"><span data-stu-id="159bf-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="159bf-119">name</span><span class="sxs-lookup"><span data-stu-id="159bf-119">name</span></span>|<span data-ttu-id="159bf-120">Název parametru určeného pro službu.</span><span class="sxs-lookup"><span data-stu-id="159bf-120">The name of the parameter specified for a service.</span></span>|  
|<span data-ttu-id="159bf-121">value</span><span class="sxs-lookup"><span data-stu-id="159bf-121">value</span></span>|<span data-ttu-id="159bf-122">Hodnota parametru určeného pro službu.</span><span class="sxs-lookup"><span data-stu-id="159bf-122">The value of the parameter specified for a service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="159bf-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="159bf-123">Child Elements</span></span>  
 <span data-ttu-id="159bf-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="159bf-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="159bf-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="159bf-125">Parent Elements</span></span>  
  
|<span data-ttu-id="159bf-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="159bf-126">Element</span></span>|<span data-ttu-id="159bf-127">Popis</span><span class="sxs-lookup"><span data-stu-id="159bf-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="159bf-128">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="159bf-128">\<commonParameters></span></span>](commonparameters.md)|<span data-ttu-id="159bf-129">Kolekce běžných parametrů používaných službami.</span><span class="sxs-lookup"><span data-stu-id="159bf-129">A collection of common parameters used by services.</span></span> <span data-ttu-id="159bf-130">Tato kolekce obvykle zahrnuje připojovací řetězec databáze, který může sdílet trvalé služby.</span><span class="sxs-lookup"><span data-stu-id="159bf-130">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="159bf-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="159bf-131">Remarks</span></span>  
 <span data-ttu-id="159bf-132">Element definuje všechny parametry, které jsou používány globálně v rámci více služeb, například `ConnectionString` při použití <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>. `<commonParameters>`</span><span class="sxs-lookup"><span data-stu-id="159bf-132">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
 <span data-ttu-id="159bf-133">Pro služby, které potvrzují pracovní dávky do úložišť pro uchovávání <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>dat, například <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> a, je můžete povolit, aby znovu opakovaly `EnableRetries` svou transakci pomocí parametru, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="159bf-133">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="159bf-134">Všimněte si, `EnableRetries` že parametr lze nastavit buď na globální úrovni (jak je uvedeno v části *CommonParameters* ), nebo pro jednotlivé služby, které `EnableRetries` podporují (jak je uvedeno v části *služby* ).</span><span class="sxs-lookup"><span data-stu-id="159bf-134">Notice that the `EnableRetries` parameter can be set at either a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="159bf-135">Další informace o tom, jak pomocí konfiguračního souboru řídit chování <xref:System.Workflow.Runtime.WorkflowRuntime> objektu programovací model Windows Workflow Foundation hostitelské aplikace, najdete v tématu [konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="159bf-135">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="159bf-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="159bf-136">Example</span></span>  
  
```xml  
<commonParameters>
  <add name="ConnectionString"
       value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
  <add name="EnableRetries"
       value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="159bf-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="159bf-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="159bf-138">[Konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="159bf-138">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [<span data-ttu-id="159bf-139">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="159bf-139">\<commonParameters></span></span>](commonparameters.md)
