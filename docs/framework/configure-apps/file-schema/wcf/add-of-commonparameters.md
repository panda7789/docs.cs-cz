---
title: <add> z <commonParameters>
ms.date: 03/30/2017
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
ms.openlocfilehash: d682acd7fff6bab2c66660a028f8a75b780e21d2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400670"
---
# <a name="add-of-commonparameters"></a><span data-ttu-id="22766-102">\<add> z \<commonParameters></span><span class="sxs-lookup"><span data-stu-id="22766-102">\<add> of \<commonParameters></span></span>
<span data-ttu-id="22766-103">Určuje dvojici název-hodnota parametrů, které jsou používány globálně v rámci více služeb.</span><span class="sxs-lookup"><span data-stu-id="22766-103">Specifies a name-value pair of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="22766-104">Tento parametr obvykle zahrnuje připojovací řetězec databáze, který může být sdílen trvalými službami.</span><span class="sxs-lookup"><span data-stu-id="22766-104">Typically this parameter includes the database connection string that might be shared by durable services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<commonParameters>**](commonparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="22766-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22766-105">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String" value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22766-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="22766-106">Attributes and Elements</span></span>  
 <span data-ttu-id="22766-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="22766-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22766-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="22766-108">Attributes</span></span>  
  
|<span data-ttu-id="22766-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="22766-109">Attribute</span></span>|<span data-ttu-id="22766-110">Popis</span><span class="sxs-lookup"><span data-stu-id="22766-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="22766-111">name</span><span class="sxs-lookup"><span data-stu-id="22766-111">name</span></span>|<span data-ttu-id="22766-112">Název parametru určeného pro službu.</span><span class="sxs-lookup"><span data-stu-id="22766-112">The name of the parameter specified for a service.</span></span>|  
|<span data-ttu-id="22766-113">hodnota</span><span class="sxs-lookup"><span data-stu-id="22766-113">value</span></span>|<span data-ttu-id="22766-114">Hodnota parametru určeného pro službu.</span><span class="sxs-lookup"><span data-stu-id="22766-114">The value of the parameter specified for a service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="22766-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="22766-115">Child Elements</span></span>  
 <span data-ttu-id="22766-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="22766-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="22766-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="22766-117">Parent Elements</span></span>  
  
|<span data-ttu-id="22766-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="22766-118">Element</span></span>|<span data-ttu-id="22766-119">Description</span><span class="sxs-lookup"><span data-stu-id="22766-119">Description</span></span>|  
|-------------|-----------------|  
|[\<commonParameters>](commonparameters.md)|<span data-ttu-id="22766-120">Kolekce běžných parametrů používaných službami.</span><span class="sxs-lookup"><span data-stu-id="22766-120">A collection of common parameters used by services.</span></span> <span data-ttu-id="22766-121">Tato kolekce obvykle zahrnuje připojovací řetězec databáze, který může sdílet trvalé služby.</span><span class="sxs-lookup"><span data-stu-id="22766-121">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22766-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="22766-122">Remarks</span></span>  
 <span data-ttu-id="22766-123">`<commonParameters>`Element definuje všechny parametry, které jsou používány globálně v rámci více služeb, například `ConnectionString` při použití <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService> .</span><span class="sxs-lookup"><span data-stu-id="22766-123">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
 <span data-ttu-id="22766-124">Pro služby, které potvrzují pracovní dávky do úložišť pro uchovávání dat, například <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> a <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService> , je můžete povolit, aby znovu opakovaly svou transakci pomocí `EnableRetries` parametru, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="22766-124">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="22766-125">Všimněte si, že `EnableRetries` parametr lze nastavit buď na globální úrovni (jak je uvedeno v části *CommonParameters* ), nebo pro jednotlivé služby, které podporují `EnableRetries` (jak je uvedeno v části *služby* ).</span><span class="sxs-lookup"><span data-stu-id="22766-125">Notice that the `EnableRetries` parameter can be set at either a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="22766-126">Další informace o tom, jak pomocí konfiguračního souboru řídit chování <xref:System.Workflow.Runtime.WorkflowRuntime> objektu programovací model Windows Workflow Foundation hostitelské aplikace, najdete v tématu [konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="22766-126">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="22766-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="22766-127">Example</span></span>  
  
```xml  
<commonParameters>
  <add name="ConnectionString"
       value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
  <add name="EnableRetries"
       value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="22766-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="22766-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="22766-129">[Konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="22766-129">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [\<commonParameters>](commonparameters.md)
