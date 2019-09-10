---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 7760ee4d3b118e339944317e8ec8d8217b5d909d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855107"
---
# <a name="mexendpoint"></a><span data-ttu-id="1a725-101">\<mexEndpoint></span><span class="sxs-lookup"><span data-stu-id="1a725-101">\<mexEndpoint></span></span>
<span data-ttu-id="1a725-102">Tento prvek konfigurace definuje standardní koncový bod s pevnou smlouvou IMetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="1a725-102">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="1a725-103">Vzhledem k tomu, že všechny koncové body výměny metadat určují jako kontrakt IMetadataExchange, můžete použít tento standardní bod, místo abyste ho nadefinovali sami.</span><span class="sxs-lookup"><span data-stu-id="1a725-103">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
<span data-ttu-id="1a725-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1a725-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1a725-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="1a725-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1a725-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Oddílu StandardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="1a725-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="1a725-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="1a725-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a725-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a725-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a725-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1a725-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1a725-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1a725-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a725-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="1a725-111">Attributes</span></span>  
  
|<span data-ttu-id="1a725-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="1a725-112">Attribute</span></span>|<span data-ttu-id="1a725-113">Popis</span><span class="sxs-lookup"><span data-stu-id="1a725-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1a725-114">name</span><span class="sxs-lookup"><span data-stu-id="1a725-114">name</span></span>|<span data-ttu-id="1a725-115">Řetězec, který určuje název konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="1a725-115">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="1a725-116">Název se používá v `endpointConfiguration` atributu koncového bodu služby k propojení standardního koncového bodu s jeho konfigurací.</span><span class="sxs-lookup"><span data-stu-id="1a725-116">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1a725-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1a725-117">Child Elements</span></span>  
 <span data-ttu-id="1a725-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="1a725-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1a725-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1a725-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1a725-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="1a725-120">Element</span></span>|<span data-ttu-id="1a725-121">Popis</span><span class="sxs-lookup"><span data-stu-id="1a725-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a725-122">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="1a725-122">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="1a725-123">Kolekce standardních koncových bodů, které jsou předem definovanými koncovými body s jednou nebo více vlastnostmi (adresa, vazba, smlouva) opraveny.</span><span class="sxs-lookup"><span data-stu-id="1a725-123">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
