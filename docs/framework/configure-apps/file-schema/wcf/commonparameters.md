---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: 73d8549f68e8ca77115619431c857c4a2aac3fdf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153019"
---
# \<commonParameters>
<span data-ttu-id="a4353-101">Představuje kolekci parametrů, které jsou používány globálně v rámci více služeb.</span><span class="sxs-lookup"><span data-stu-id="a4353-101">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="a4353-102">Tato kolekce obvykle zahrnuje připojovací řetězec databáze, který může sdílet trvalé služby.</span><span class="sxs-lookup"><span data-stu-id="a4353-102">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<commonParameters>**  
  
## <a name="syntax"></a><span data-ttu-id="a4353-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4353-103">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4353-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a4353-104">Attributes and Elements</span></span>  
 <span data-ttu-id="a4353-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a4353-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4353-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="a4353-106">Attributes</span></span>  
 <span data-ttu-id="a4353-107">Žádné</span><span class="sxs-lookup"><span data-stu-id="a4353-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a4353-108">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a4353-108">Child Elements</span></span>  
  
|<span data-ttu-id="a4353-109">Prvek</span><span class="sxs-lookup"><span data-stu-id="a4353-109">Element</span></span>|<span data-ttu-id="a4353-110">Description</span><span class="sxs-lookup"><span data-stu-id="a4353-110">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-commonparameters.md)|<span data-ttu-id="a4353-111">Přidá dvojici název-hodnota společných parametrů používaných službami do kolekce.</span><span class="sxs-lookup"><span data-stu-id="a4353-111">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a4353-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a4353-112">Parent Elements</span></span>  
  
|<span data-ttu-id="a4353-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="a4353-113">Element</span></span>|<span data-ttu-id="a4353-114">Description</span><span class="sxs-lookup"><span data-stu-id="a4353-114">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowRuntime>](workflowruntime.md)|<span data-ttu-id="a4353-115">Určuje nastavení pro instanci <xref:System.Workflow.Runtime.WorkflowRuntime> pro hostování služeb Windows Communication Foundation založených na pracovních postupech (WCF).</span><span class="sxs-lookup"><span data-stu-id="a4353-115">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4353-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a4353-116">Remarks</span></span>  
 <span data-ttu-id="a4353-117">`<commonParameters>`Element definuje všechny parametry, které jsou používány globálně v rámci více služeb, například `ConnectionString` při použití <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService> .</span><span class="sxs-lookup"><span data-stu-id="a4353-117">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a4353-118">Služba sledování SQL tuto hodnotu konzistentně nepoužívá, `ConnectionString` Pokud je uvedena v `<commonParameters>` části.</span><span class="sxs-lookup"><span data-stu-id="a4353-118">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="a4353-119">Některé jeho operace, jako je například načtení `StateMachineWorkflowInstance.StateHistory` vlastnosti, mohou selhat.</span><span class="sxs-lookup"><span data-stu-id="a4353-119">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="a4353-120">Chcete-li tento problém vyřešit, zadejte `ConnectionString` atribut v oddílu konfigurace pro zprostředkovatele sledování, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a4353-120">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  

```xml  
<add
type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />
```  
  
 <span data-ttu-id="a4353-121">Pro služby, které potvrzují pracovní dávky do úložišť pro uchovávání dat, například <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> a <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService> , je můžete povolit, aby znovu opakovaly svou transakci pomocí `EnableRetries` parametru, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a4353-121">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="a4353-122">Všimněte si, že `EnableRetries` parametr lze nastavit buď na globální úrovni (jak je uvedeno v části *CommonParameters* ), nebo pro jednotlivé služby, které podporují `EnableRetries` (jak je uvedeno v části *služby* ).</span><span class="sxs-lookup"><span data-stu-id="a4353-122">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="a4353-123">Následující vzorový kód ukazuje, jak změnit společné parametry programově:</span><span class="sxs-lookup"><span data-stu-id="a4353-123">The following sample code shows how to change the common parameters programmatically:</span></span>
  
```csharp  
Configuration config = WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");
var wfruntime = config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters = wfruntime.CommonParameters;
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="a4353-124">Další informace o tom, jak pomocí konfiguračního souboru řídit chování <xref:System.Workflow.Runtime.WorkflowRuntime> objektu programovací model Windows Workflow Foundation hostitelské aplikace, najdete v tématu [konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="a4353-124">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4353-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="a4353-125">Example</span></span>  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="a4353-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4353-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="a4353-127">[Konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="a4353-127">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [\<add>](add-of-commonparameters.md)
