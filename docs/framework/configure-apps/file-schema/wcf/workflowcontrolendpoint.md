---
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: a9c16d1036a8177120cd152d4ac211ad084d588e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150381"
---
# <a name="workflowcontrolendpoint"></a><span data-ttu-id="81603-101">\<workflowControlEndpoint></span><span class="sxs-lookup"><span data-stu-id="81603-101">\<workflowControlEndpoint></span></span>
<span data-ttu-id="81603-102">Tento prvek konfigurace definuje standardní koncový bod pro řízení spouštění instance pracovního postupu (vytvoření, spuštění, pozastavení, ukončit atd).</span><span class="sxs-lookup"><span data-stu-id="81603-102">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="81603-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="81603-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="81603-104">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="81603-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81603-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81603-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81603-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="81603-106">Attributes and Elements</span></span>  
 <span data-ttu-id="81603-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="81603-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81603-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="81603-108">Attributes</span></span>  
  
|<span data-ttu-id="81603-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="81603-109">Attribute</span></span>|<span data-ttu-id="81603-110">Popis</span><span class="sxs-lookup"><span data-stu-id="81603-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="81603-111">name</span><span class="sxs-lookup"><span data-stu-id="81603-111">name</span></span>|<span data-ttu-id="81603-112">Řetězec, který určuje název konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="81603-112">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="81603-113">Název se používá v `endpointConfiguration` atribut koncového bodu služby propojit s jeho konfigurace je standardní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="81603-113">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81603-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="81603-114">Child Elements</span></span>  
 <span data-ttu-id="81603-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="81603-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="81603-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="81603-116">Parent Elements</span></span>  
  
|<span data-ttu-id="81603-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="81603-117">Element</span></span>|<span data-ttu-id="81603-118">Popis</span><span class="sxs-lookup"><span data-stu-id="81603-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="81603-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="81603-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="81603-120">Kolekce standardních koncových bodů, které jsou předem definované koncové body s jedním nebo více z jejich vlastností (adresu, vazbu, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="81603-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81603-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="81603-121">See also</span></span>

- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
