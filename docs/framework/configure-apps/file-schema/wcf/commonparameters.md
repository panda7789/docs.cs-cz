---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: 6f187e9cdcabc358ee69d65e392bc59aa38e52ca
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398168"
---
# <a name="commonparameters"></a><span data-ttu-id="1fb05-101">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="1fb05-101">\<commonParameters></span></span>
<span data-ttu-id="1fb05-102">Představuje kolekci parametrů, které jsou používány globálně v rámci více služeb.</span><span class="sxs-lookup"><span data-stu-id="1fb05-102">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="1fb05-103">Tato kolekce obvykle zahrnuje připojovací řetězec databáze, který může sdílet trvalé služby.</span><span class="sxs-lookup"><span data-stu-id="1fb05-103">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
<span data-ttu-id="1fb05-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1fb05-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1fb05-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="1fb05-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1fb05-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="1fb05-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="1fb05-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="1fb05-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="1fb05-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="1fb05-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="1fb05-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> aktivity typu workflowRuntime**](workflowruntime.md)</span><span class="sxs-lookup"><span data-stu-id="1fb05-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)</span></span>\
<span data-ttu-id="1fb05-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<commonParameters >**</span><span class="sxs-lookup"><span data-stu-id="1fb05-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<commonParameters>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fb05-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1fb05-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1fb05-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1fb05-112">Attributes and Elements</span></span>  
 <span data-ttu-id="1fb05-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1fb05-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1fb05-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="1fb05-114">Attributes</span></span>  
 <span data-ttu-id="1fb05-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="1fb05-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1fb05-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1fb05-116">Child Elements</span></span>  
  
|<span data-ttu-id="1fb05-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="1fb05-117">Element</span></span>|<span data-ttu-id="1fb05-118">Popis</span><span class="sxs-lookup"><span data-stu-id="1fb05-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1fb05-119">\<add></span><span class="sxs-lookup"><span data-stu-id="1fb05-119">\<add></span></span>](add-of-commonparameters.md)|<span data-ttu-id="1fb05-120">Přidá dvojici název-hodnota společných parametrů používaných službami do kolekce.</span><span class="sxs-lookup"><span data-stu-id="1fb05-120">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1fb05-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1fb05-121">Parent Elements</span></span>  
  
|<span data-ttu-id="1fb05-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="1fb05-122">Element</span></span>|<span data-ttu-id="1fb05-123">Popis</span><span class="sxs-lookup"><span data-stu-id="1fb05-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1fb05-124">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="1fb05-124">\<workflowRuntime></span></span>](workflowruntime.md)|<span data-ttu-id="1fb05-125">Určuje nastavení pro instanci <xref:System.Workflow.Runtime.WorkflowRuntime> pro hostování služeb Windows Communication Foundation založených na pracovních postupech (WCF).</span><span class="sxs-lookup"><span data-stu-id="1fb05-125">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1fb05-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1fb05-126">Remarks</span></span>  
 <span data-ttu-id="1fb05-127">Element definuje všechny parametry, které jsou používány globálně v rámci více služeb, například `ConnectionString` při použití <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>. `<commonParameters>`</span><span class="sxs-lookup"><span data-stu-id="1fb05-127">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1fb05-128">Služba sledování SQL tuto `ConnectionString` hodnotu konzistentně nepoužívá, pokud je uvedena `<commonParameters>` v části.</span><span class="sxs-lookup"><span data-stu-id="1fb05-128">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="1fb05-129">Některé jeho operace, jako je například načtení `StateMachineWorkflowInstance.StateHistory` vlastnosti, mohou selhat.</span><span class="sxs-lookup"><span data-stu-id="1fb05-129">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="1fb05-130">Chcete-li tento problém vyřešit `ConnectionString` , zadejte atribut v oddílu konfigurace pro zprostředkovatele sledování, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1fb05-130">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  
  
 `<add`  
  
 `type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"`  
  
 `ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />`  
  
 <span data-ttu-id="1fb05-131">Pro služby, které potvrzují pracovní dávky do úložišť pro uchovávání <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>dat, například <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> a, je můžete povolit, aby znovu opakovaly `EnableRetries` svou transakci pomocí parametru, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="1fb05-131">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="1fb05-132">Všimněte si, `EnableRetries` že parametr lze nastavit buď na globální úrovni (jak je uvedeno v části *CommonParameters* ), nebo pro jednotlivé služby, které `EnableRetries` podporují (jak je uvedeno v části *služby* ).</span><span class="sxs-lookup"><span data-stu-id="1fb05-132">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="1fb05-133">Následující vzorový kód ukazuje, jak změnit společné parametry programově.</span><span class="sxs-lookup"><span data-stu-id="1fb05-133">The following sample code shows how to change the common parameters programmatically.</span></span>  
  
```  
Configuration config=WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");  
WorkflowRuntimeSection wfruntime=config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters=wfruntime.CommonParameters;  
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="1fb05-134">Další informace o tom, jak pomocí konfiguračního souboru řídit chování <xref:System.Workflow.Runtime.WorkflowRuntime> objektu programovací model Windows Workflow Foundation hostitelské aplikace, najdete v tématu [konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="1fb05-134">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fb05-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="1fb05-135">Example</span></span>  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="1fb05-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1fb05-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="1fb05-137">[Konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="1fb05-137">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [<span data-ttu-id="1fb05-138">\<add></span><span class="sxs-lookup"><span data-stu-id="1fb05-138">\<add></span></span>](add-of-commonparameters.md)
