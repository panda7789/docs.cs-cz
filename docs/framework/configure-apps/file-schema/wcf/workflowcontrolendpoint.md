---
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: a9c16d1036a8177120cd152d4ac211ad084d588e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150381"
---
# <a name="workflowcontrolendpoint"></a><span data-ttu-id="b001b-101">\<workflowControlEndpoint></span><span class="sxs-lookup"><span data-stu-id="b001b-101">\<workflowControlEndpoint></span></span>
<span data-ttu-id="b001b-102">Tento prvek konfigurace definuje standardní koncový bod pro řízení spouštění instance pracovního postupu (vytvoření, spuštění, pozastavení, ukončit atd).</span><span class="sxs-lookup"><span data-stu-id="b001b-102">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="b001b-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b001b-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="b001b-104">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="b001b-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b001b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b001b-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b001b-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b001b-106">Attributes and Elements</span></span>  
 <span data-ttu-id="b001b-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b001b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b001b-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="b001b-108">Attributes</span></span>  
  
|<span data-ttu-id="b001b-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="b001b-109">Attribute</span></span>|<span data-ttu-id="b001b-110">Popis</span><span class="sxs-lookup"><span data-stu-id="b001b-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b001b-111">name</span><span class="sxs-lookup"><span data-stu-id="b001b-111">name</span></span>|<span data-ttu-id="b001b-112">Řetězec, který určuje název konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="b001b-112">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="b001b-113">Název se používá v `endpointConfiguration` atribut koncového bodu služby propojit s jeho konfigurace je standardní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="b001b-113">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b001b-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b001b-114">Child Elements</span></span>  
 <span data-ttu-id="b001b-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="b001b-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b001b-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b001b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="b001b-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="b001b-117">Element</span></span>|<span data-ttu-id="b001b-118">Popis</span><span class="sxs-lookup"><span data-stu-id="b001b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b001b-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="b001b-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="b001b-120">Kolekce standardních koncových bodů, které jsou předem definované koncové body s jedním nebo více z jejich vlastností (adresu, vazbu, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="b001b-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b001b-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b001b-121">See also</span></span>

- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
