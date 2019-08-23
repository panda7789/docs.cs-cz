---
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 2c9774217b835acdb9ebf7374b964d838497fc9f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915325"
---
# <a name="workflowcontrolendpoint"></a><span data-ttu-id="024e7-101">\<workflowControlEndpoint></span><span class="sxs-lookup"><span data-stu-id="024e7-101">\<workflowControlEndpoint></span></span>
<span data-ttu-id="024e7-102">Tento prvek konfigurace definuje standardní koncový bod pro řízení spouštění instancí pracovního postupu (vytvořit, spustit, pozastavit, ukončit atd.).</span><span class="sxs-lookup"><span data-stu-id="024e7-102">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="024e7-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="024e7-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="024e7-104">\<Oddílu StandardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="024e7-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="024e7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="024e7-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="024e7-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="024e7-106">Attributes and Elements</span></span>  
 <span data-ttu-id="024e7-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="024e7-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="024e7-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="024e7-108">Attributes</span></span>  
  
|<span data-ttu-id="024e7-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="024e7-109">Attribute</span></span>|<span data-ttu-id="024e7-110">Popis</span><span class="sxs-lookup"><span data-stu-id="024e7-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="024e7-111">name</span><span class="sxs-lookup"><span data-stu-id="024e7-111">name</span></span>|<span data-ttu-id="024e7-112">Řetězec, který určuje název konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="024e7-112">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="024e7-113">Název se používá v `endpointConfiguration` atributu koncového bodu služby k propojení standardního koncového bodu s jeho konfigurací.</span><span class="sxs-lookup"><span data-stu-id="024e7-113">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="024e7-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="024e7-114">Child Elements</span></span>  
 <span data-ttu-id="024e7-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="024e7-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="024e7-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="024e7-116">Parent Elements</span></span>  
  
|<span data-ttu-id="024e7-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="024e7-117">Element</span></span>|<span data-ttu-id="024e7-118">Popis</span><span class="sxs-lookup"><span data-stu-id="024e7-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="024e7-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="024e7-119">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="024e7-120">Kolekce standardních koncových bodů, které jsou předem definovanými koncovými body s jednou nebo více vlastnostmi (adresa, vazba, smlouva) opraveny.</span><span class="sxs-lookup"><span data-stu-id="024e7-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="024e7-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="024e7-121">See also</span></span>

- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
