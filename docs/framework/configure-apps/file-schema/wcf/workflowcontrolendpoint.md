---
title: '&lt;workflowControlEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 9c641d4081d88b059e1d778f6383f85c064af7f0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558667"
---
# <a name="ltworkflowcontrolendpointgt"></a><span data-ttu-id="5eafe-102">&lt;workflowControlEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="5eafe-102">&lt;workflowControlEndpoint&gt;</span></span>
<span data-ttu-id="5eafe-103">Tento prvek konfigurace definuje standardní koncový bod pro řízení spouštění instance pracovního postupu (vytvoření, spuštění, pozastavení, ukončit atd).</span><span class="sxs-lookup"><span data-stu-id="5eafe-103">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="5eafe-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5eafe-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5eafe-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="5eafe-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5eafe-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5eafe-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5eafe-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5eafe-107">Attributes and Elements</span></span>  
 <span data-ttu-id="5eafe-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5eafe-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5eafe-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="5eafe-109">Attributes</span></span>  
  
|<span data-ttu-id="5eafe-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="5eafe-110">Attribute</span></span>|<span data-ttu-id="5eafe-111">Popis</span><span class="sxs-lookup"><span data-stu-id="5eafe-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5eafe-112">name</span><span class="sxs-lookup"><span data-stu-id="5eafe-112">name</span></span>|<span data-ttu-id="5eafe-113">Řetězec, který určuje název konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="5eafe-113">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="5eafe-114">Název se používá v `endpointConfiguration` atribut koncového bodu služby propojit s jeho konfigurace je standardní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="5eafe-114">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5eafe-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5eafe-115">Child Elements</span></span>  
 <span data-ttu-id="5eafe-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="5eafe-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5eafe-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5eafe-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5eafe-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="5eafe-118">Element</span></span>|<span data-ttu-id="5eafe-119">Popis</span><span class="sxs-lookup"><span data-stu-id="5eafe-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5eafe-120">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="5eafe-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="5eafe-121">Kolekce standardních koncových bodů, které jsou předem definované koncové body s jedním nebo více z jejich vlastností (adresu, vazbu, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="5eafe-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5eafe-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5eafe-122">See also</span></span>
- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
