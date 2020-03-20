---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: 73d8549f68e8ca77115619431c857c4a2aac3fdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153019"
---
# <a name="commonparameters"></a><span data-ttu-id="97792-101">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="97792-101">\<commonParameters></span></span>
<span data-ttu-id="97792-102">Představuje kolekci parametrů, které se používají globálně napříč více službami.</span><span class="sxs-lookup"><span data-stu-id="97792-102">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="97792-103">Tato kolekce bude obvykle obsahovat připojovací řetězec databáze, které mohou být sdíleny trvalé služby.</span><span class="sxs-lookup"><span data-stu-id="97792-103">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
<span data-ttu-id="97792-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="97792-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="97792-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="97792-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="97792-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<chování>**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="97792-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="97792-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="97792-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="97792-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<chování>**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="97792-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="97792-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)</span><span class="sxs-lookup"><span data-stu-id="97792-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)</span></span>\
<span data-ttu-id="97792-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<commonParameters>**</span><span class="sxs-lookup"><span data-stu-id="97792-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<commonParameters>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97792-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97792-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97792-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="97792-112">Attributes and Elements</span></span>  
 <span data-ttu-id="97792-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="97792-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97792-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="97792-114">Attributes</span></span>  
 <span data-ttu-id="97792-115">Žádné.</span><span class="sxs-lookup"><span data-stu-id="97792-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="97792-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="97792-116">Child Elements</span></span>  
  
|<span data-ttu-id="97792-117">Element</span><span class="sxs-lookup"><span data-stu-id="97792-117">Element</span></span>|<span data-ttu-id="97792-118">Popis</span><span class="sxs-lookup"><span data-stu-id="97792-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97792-119">\<přidat></span><span class="sxs-lookup"><span data-stu-id="97792-119">\<add></span></span>](add-of-commonparameters.md)|<span data-ttu-id="97792-120">Přidá dvojici název-hodnota společné parametry používané služby do kolekce.</span><span class="sxs-lookup"><span data-stu-id="97792-120">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="97792-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="97792-121">Parent Elements</span></span>  
  
|<span data-ttu-id="97792-122">Element</span><span class="sxs-lookup"><span data-stu-id="97792-122">Element</span></span>|<span data-ttu-id="97792-123">Popis</span><span class="sxs-lookup"><span data-stu-id="97792-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97792-124">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="97792-124">\<workflowRuntime></span></span>](workflowruntime.md)|<span data-ttu-id="97792-125">Určuje nastavení instance <xref:System.Workflow.Runtime.WorkflowRuntime> pro hostování služeb WCF (Windows Communication Foundation) založených na pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="97792-125">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97792-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="97792-126">Remarks</span></span>  
 <span data-ttu-id="97792-127">Prvek `<commonParameters>` definuje všechny parametry, které se používají globálně `ConnectionString` napříč <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>více službami, například při použití rozhraní .</span><span class="sxs-lookup"><span data-stu-id="97792-127">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="97792-128">Služba sledování SQL nepoužívá `ConnectionString` konzistentně `<commonParameters>` hodnotu, pokud je zadána v části.</span><span class="sxs-lookup"><span data-stu-id="97792-128">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="97792-129">Některé z jeho operací, `StateMachineWorkflowInstance.StateHistory` jako je například načítání vlastnosti může selhat.</span><span class="sxs-lookup"><span data-stu-id="97792-129">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="97792-130">Chcete-li to toto řešení vyřešit, zadejte `ConnectionString` atribut v části konfigurace pro sledování zprostředkovatele, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="97792-130">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  

```xml  
<add
type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />
```  
  
 <span data-ttu-id="97792-131">Pro služby, které potvrdí pracovní dávky do úložišť trvalosti, například <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> a <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, můžete jim povolit opakování jejich transakce pomocí parametru, `EnableRetries` jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="97792-131">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="97792-132">Všimněte `EnableRetries` si, že parametr lze nastavit buď na globální úrovni (jak je znázorněno v *commonparameters* části) nebo pro jednotlivé služby, které podporují `EnableRetries` (jak je znázorněno v části *Služby).*</span><span class="sxs-lookup"><span data-stu-id="97792-132">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="97792-133">Následující ukázkový kód ukazuje, jak programově změnit běžné parametry:</span><span class="sxs-lookup"><span data-stu-id="97792-133">The following sample code shows how to change the common parameters programmatically:</span></span>
  
```csharp  
Configuration config = WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");
var wfruntime = config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters = wfruntime.CommonParameters;
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="97792-134">Další informace o použití konfiguračního <xref:System.Workflow.Runtime.WorkflowRuntime> souboru k řízení chování objektu hostitelské aplikace služby Windows Workflow Foundation naleznete v [tématu Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="97792-134">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="97792-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="97792-135">Example</span></span>  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="97792-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="97792-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="97792-137">[Konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="97792-137">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [<span data-ttu-id="97792-138">\<přidat></span><span class="sxs-lookup"><span data-stu-id="97792-138">\<add></span></span>](add-of-commonparameters.md)
