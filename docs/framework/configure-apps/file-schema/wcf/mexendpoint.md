---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 78788f9dfbf6cdf3439fd6e33eddfe721e49840d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931259"
---
# <a name="mexendpoint"></a><span data-ttu-id="03046-101">\<mexEndpoint></span><span class="sxs-lookup"><span data-stu-id="03046-101">\<mexEndpoint></span></span>
<span data-ttu-id="03046-102">Tento prvek konfigurace definuje standardní koncový bod s pevnou smlouvou IMetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="03046-102">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="03046-103">Vzhledem k tomu, že všechny koncové body výměny metadat určují jako kontrakt IMetadataExchange, můžete použít tento standardní bod, místo abyste ho nadefinovali sami.</span><span class="sxs-lookup"><span data-stu-id="03046-103">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
 <span data-ttu-id="03046-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="03046-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="03046-105">\<Oddílu StandardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="03046-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03046-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03046-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03046-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="03046-107">Attributes and Elements</span></span>  
 <span data-ttu-id="03046-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="03046-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03046-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="03046-109">Attributes</span></span>  
  
|<span data-ttu-id="03046-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="03046-110">Attribute</span></span>|<span data-ttu-id="03046-111">Popis</span><span class="sxs-lookup"><span data-stu-id="03046-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="03046-112">name</span><span class="sxs-lookup"><span data-stu-id="03046-112">name</span></span>|<span data-ttu-id="03046-113">Řetězec, který určuje název konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="03046-113">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="03046-114">Název se používá v `endpointConfiguration` atributu koncového bodu služby k propojení standardního koncového bodu s jeho konfigurací.</span><span class="sxs-lookup"><span data-stu-id="03046-114">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="03046-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="03046-115">Child Elements</span></span>  
 <span data-ttu-id="03046-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="03046-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="03046-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="03046-117">Parent Elements</span></span>  
  
|<span data-ttu-id="03046-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="03046-118">Element</span></span>|<span data-ttu-id="03046-119">Popis</span><span class="sxs-lookup"><span data-stu-id="03046-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03046-120">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="03046-120">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="03046-121">Kolekce standardních koncových bodů, které jsou předem definovanými koncovými body s jednou nebo více vlastnostmi (adresa, vazba, smlouva) opraveny.</span><span class="sxs-lookup"><span data-stu-id="03046-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
