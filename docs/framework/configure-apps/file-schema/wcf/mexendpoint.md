---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 7760ee4d3b118e339944317e8ec8d8217b5d909d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855107"
---
# \<mexEndpoint>
<span data-ttu-id="83f7f-101">Tento prvek konfigurace definuje standardní koncový bod s pevnou smlouvou IMetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="83f7f-101">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="83f7f-102">Vzhledem k tomu, že všechny koncové body výměny metadat určují jako kontrakt IMetadataExchange, můžete použít tento standardní bod, místo abyste ho nadefinovali sami.</span><span class="sxs-lookup"><span data-stu-id="83f7f-102">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="83f7f-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83f7f-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83f7f-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="83f7f-104">Attributes and Elements</span></span>  
 <span data-ttu-id="83f7f-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="83f7f-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83f7f-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="83f7f-106">Attributes</span></span>  
  
|<span data-ttu-id="83f7f-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="83f7f-107">Attribute</span></span>|<span data-ttu-id="83f7f-108">Popis</span><span class="sxs-lookup"><span data-stu-id="83f7f-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="83f7f-109">name</span><span class="sxs-lookup"><span data-stu-id="83f7f-109">name</span></span>|<span data-ttu-id="83f7f-110">Řetězec, který určuje název konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="83f7f-110">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="83f7f-111">Název se používá v `endpointConfiguration` atributu koncového bodu služby k propojení standardního koncového bodu s jeho konfigurací.</span><span class="sxs-lookup"><span data-stu-id="83f7f-111">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="83f7f-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="83f7f-112">Child Elements</span></span>  
 <span data-ttu-id="83f7f-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="83f7f-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="83f7f-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="83f7f-114">Parent Elements</span></span>  
  
|<span data-ttu-id="83f7f-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="83f7f-115">Element</span></span>|<span data-ttu-id="83f7f-116">Description</span><span class="sxs-lookup"><span data-stu-id="83f7f-116">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="83f7f-117">Kolekce standardních koncových bodů, které jsou předem definovanými koncovými body s jednou nebo více vlastnostmi (adresa, vazba, smlouva) opraveny.</span><span class="sxs-lookup"><span data-stu-id="83f7f-117">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
