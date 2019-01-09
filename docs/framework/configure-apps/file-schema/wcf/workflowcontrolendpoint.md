---
title: '&lt;koncového bodu workflowControlEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 178ccc8ac35b0ac76d74c818dce43dcffc5c0835
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54144948"
---
# <a name="ltworkflowcontrolendpointgt"></a><span data-ttu-id="e4ea9-102">&lt;koncového bodu workflowControlEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="e4ea9-102">&lt;workflowControlEndpoint&gt;</span></span>
<span data-ttu-id="e4ea9-103">Tento prvek konfigurace definuje standardní koncový bod pro řízení spouštění instance pracovního postupu (vytvoření, spuštění, pozastavení, ukončit atd).</span><span class="sxs-lookup"><span data-stu-id="e4ea9-103">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="e4ea9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e4ea9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e4ea9-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="e4ea9-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4ea9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4ea9-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4ea9-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e4ea9-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e4ea9-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e4ea9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4ea9-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="e4ea9-109">Attributes</span></span>  
  
|<span data-ttu-id="e4ea9-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="e4ea9-110">Attribute</span></span>|<span data-ttu-id="e4ea9-111">Popis</span><span class="sxs-lookup"><span data-stu-id="e4ea9-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e4ea9-112">name</span><span class="sxs-lookup"><span data-stu-id="e4ea9-112">name</span></span>|<span data-ttu-id="e4ea9-113">Řetězec, který určuje název konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="e4ea9-113">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="e4ea9-114">Název se používá v `endpointConfiguration` atribut koncového bodu služby propojit s jeho konfigurace je standardní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="e4ea9-114">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4ea9-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e4ea9-115">Child Elements</span></span>  
 <span data-ttu-id="e4ea9-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="e4ea9-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4ea9-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e4ea9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e4ea9-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="e4ea9-118">Element</span></span>|<span data-ttu-id="e4ea9-119">Popis</span><span class="sxs-lookup"><span data-stu-id="e4ea9-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4ea9-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="e4ea9-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="e4ea9-121">Kolekce standardních koncových bodů, které jsou předem definované koncové body s jedním nebo více z jejich vlastností (adresu, vazbu, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="e4ea9-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e4ea9-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="e4ea9-122">See Also</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
