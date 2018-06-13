---
title: '&lt;WorkflowControlEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 87c745cfb8f7cd98c25cd34fc1aa94a26a5ba507
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754782"
---
# <a name="ltworkflowcontrolendpointgt"></a><span data-ttu-id="27984-102">&lt;WorkflowControlEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="27984-102">&lt;workflowControlEndpoint&gt;</span></span>
<span data-ttu-id="27984-103">Koncový bod standardní řízení provádění instancí pracovního postupu definuje tento element konfigurace (vytvoření, spuštění, pozastavení, ukončit, atd).</span><span class="sxs-lookup"><span data-stu-id="27984-103">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="27984-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="27984-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="27984-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="27984-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27984-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27984-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27984-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="27984-107">Attributes and Elements</span></span>  
 <span data-ttu-id="27984-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="27984-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27984-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="27984-109">Attributes</span></span>  
  
|<span data-ttu-id="27984-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="27984-110">Attribute</span></span>|<span data-ttu-id="27984-111">Popis</span><span class="sxs-lookup"><span data-stu-id="27984-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="27984-112">name</span><span class="sxs-lookup"><span data-stu-id="27984-112">name</span></span>|<span data-ttu-id="27984-113">Řetězec, který určuje název konfigurace standardní koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="27984-113">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="27984-114">Název je používán `endpointConfiguration` atribut propojení koncový bod standardní konfiguraci koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="27984-114">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="27984-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="27984-115">Child Elements</span></span>  
 <span data-ttu-id="27984-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="27984-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="27984-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="27984-117">Parent Elements</span></span>  
  
|<span data-ttu-id="27984-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="27984-118">Element</span></span>|<span data-ttu-id="27984-119">Popis</span><span class="sxs-lookup"><span data-stu-id="27984-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27984-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="27984-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="27984-121">Kolekce standardních koncových bodů, které jsou předem definované koncových bodů s jedním nebo více jejich vlastnosti (adresy, vazby, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="27984-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="27984-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="27984-122">See Also</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
