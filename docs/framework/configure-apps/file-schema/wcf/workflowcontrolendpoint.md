---
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 670c1573fe4378a18c19d0a58fe58241745725bd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854781"
---
# \<workflowControlEndpoint>
<span data-ttu-id="61a50-101">Tento prvek konfigurace definuje standardní koncový bod pro řízení spouštění instancí pracovního postupu (vytvořit, spustit, pozastavit, ukončit atd.).</span><span class="sxs-lookup"><span data-stu-id="61a50-101">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowControlEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="61a50-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61a50-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61a50-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="61a50-103">Attributes and Elements</span></span>  
 <span data-ttu-id="61a50-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="61a50-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61a50-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="61a50-105">Attributes</span></span>  
  
|<span data-ttu-id="61a50-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="61a50-106">Attribute</span></span>|<span data-ttu-id="61a50-107">Popis</span><span class="sxs-lookup"><span data-stu-id="61a50-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="61a50-108">name</span><span class="sxs-lookup"><span data-stu-id="61a50-108">name</span></span>|<span data-ttu-id="61a50-109">Řetězec, který určuje název konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="61a50-109">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="61a50-110">Název se používá v `endpointConfiguration` atributu koncového bodu služby k propojení standardního koncového bodu s jeho konfigurací.</span><span class="sxs-lookup"><span data-stu-id="61a50-110">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61a50-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="61a50-111">Child Elements</span></span>  
 <span data-ttu-id="61a50-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="61a50-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="61a50-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="61a50-113">Parent Elements</span></span>  
  
|<span data-ttu-id="61a50-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="61a50-114">Element</span></span>|<span data-ttu-id="61a50-115">Description</span><span class="sxs-lookup"><span data-stu-id="61a50-115">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="61a50-116">Kolekce standardních koncových bodů, které jsou předem definovanými koncovými body s jednou nebo více vlastnostmi (adresa, vazba, smlouva) opraveny.</span><span class="sxs-lookup"><span data-stu-id="61a50-116">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="61a50-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="61a50-117">See also</span></span>

- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
