---
title: '&lt;mexEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 4e2fb4946ee68b3cbd5bd6bfbafe6bb5e9c9106f
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149147"
---
# <a name="ltmexendpointgt"></a><span data-ttu-id="87480-102">&lt;mexEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="87480-102">&lt;mexEndpoint&gt;</span></span>
<span data-ttu-id="87480-103">Tento prvek konfigurace definuje standardní koncový bod s pevným kontraktem IMetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="87480-103">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="87480-104">Protože všechny koncové body metadat exchange určit jako jejich kontraktu IMetadataExchange, můžete použít tento standardní bod místo definování sami.</span><span class="sxs-lookup"><span data-stu-id="87480-104">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
 <span data-ttu-id="87480-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="87480-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="87480-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="87480-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87480-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87480-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87480-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="87480-108">Attributes and Elements</span></span>  
 <span data-ttu-id="87480-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="87480-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87480-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="87480-110">Attributes</span></span>  
  
|<span data-ttu-id="87480-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="87480-111">Attribute</span></span>|<span data-ttu-id="87480-112">Popis</span><span class="sxs-lookup"><span data-stu-id="87480-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="87480-113">name</span><span class="sxs-lookup"><span data-stu-id="87480-113">name</span></span>|<span data-ttu-id="87480-114">Řetězec, který určuje název konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="87480-114">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="87480-115">Název se používá v `endpointConfiguration` atribut koncového bodu služby propojit s jeho konfigurace je standardní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="87480-115">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87480-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="87480-116">Child Elements</span></span>  
 <span data-ttu-id="87480-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="87480-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87480-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="87480-118">Parent Elements</span></span>  
  
|<span data-ttu-id="87480-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="87480-119">Element</span></span>|<span data-ttu-id="87480-120">Popis</span><span class="sxs-lookup"><span data-stu-id="87480-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87480-121">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="87480-121">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="87480-122">Kolekce standardních koncových bodů, které jsou předem definované koncové body s jedním nebo více z jejich vlastností (adresu, vazbu, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="87480-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
