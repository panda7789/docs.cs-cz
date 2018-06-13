---
title: '&lt;mexEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: aceff3e373d9a5f7e57c28d85870af19ae8ef3e1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747782"
---
# <a name="ltmexendpointgt"></a><span data-ttu-id="b9ade-102">&lt;mexEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="b9ade-102">&lt;mexEndpoint&gt;</span></span>
<span data-ttu-id="b9ade-103">Tento element konfigurace definuje standardní koncový bod s pevnou IMetadataExchange kontrakt.</span><span class="sxs-lookup"><span data-stu-id="b9ade-103">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="b9ade-104">Vzhledem k tomu, že všechny koncové body metadat serveru exchange zadejte IMetadataExchange jako jejich kontrakt, můžete použít tento standardní bod místo definování jeden pro sami.</span><span class="sxs-lookup"><span data-stu-id="b9ade-104">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
 <span data-ttu-id="b9ade-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b9ade-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="b9ade-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="b9ade-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9ade-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9ade-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9ade-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b9ade-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b9ade-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b9ade-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9ade-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="b9ade-110">Attributes</span></span>  
  
|<span data-ttu-id="b9ade-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="b9ade-111">Attribute</span></span>|<span data-ttu-id="b9ade-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b9ade-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b9ade-113">name</span><span class="sxs-lookup"><span data-stu-id="b9ade-113">name</span></span>|<span data-ttu-id="b9ade-114">Řetězec, který určuje název konfigurace standardní koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="b9ade-114">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="b9ade-115">Název je používán `endpointConfiguration` atribut propojení koncový bod standardní konfiguraci koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="b9ade-115">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b9ade-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b9ade-116">Child Elements</span></span>  
 <span data-ttu-id="b9ade-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="b9ade-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b9ade-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b9ade-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b9ade-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="b9ade-119">Element</span></span>|<span data-ttu-id="b9ade-120">Popis</span><span class="sxs-lookup"><span data-stu-id="b9ade-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9ade-121">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="b9ade-121">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="b9ade-122">Kolekce standardních koncových bodů, které jsou předem definované koncových bodů s jedním nebo více jejich vlastnosti (adresy, vazby, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="b9ade-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
