---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: dd6513930798e9e1ab263f75c9350511c2dcdcd5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935185"
---
# <a name="scopes"></a><span data-ttu-id="14802-101">\<> oborů</span><span class="sxs-lookup"><span data-stu-id="14802-101">\<scopes></span></span>
<span data-ttu-id="14802-102">Obsahuje kolekci prvků konfigurace, které určují identifikátory URI vlastního oboru, které lze použít k filtrování koncových bodů služby během dotazu.</span><span class="sxs-lookup"><span data-stu-id="14802-102">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="14802-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="14802-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="14802-104">\<> chování</span><span class="sxs-lookup"><span data-stu-id="14802-104">\<behaviors></span></span>  
<span data-ttu-id="14802-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="14802-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="14802-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="14802-106">\<behavior></span></span>  
<span data-ttu-id="14802-107">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="14802-107">\<endpointDiscovery></span></span>  
<span data-ttu-id="14802-108">\<> oborů</span><span class="sxs-lookup"><span data-stu-id="14802-108">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14802-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14802-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI" />
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14802-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="14802-110">Attributes and Elements</span></span>  
 <span data-ttu-id="14802-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="14802-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14802-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="14802-112">Attributes</span></span>  
 <span data-ttu-id="14802-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="14802-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="14802-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="14802-114">Child Elements</span></span>  
  
|<span data-ttu-id="14802-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="14802-115">Attribute</span></span>|<span data-ttu-id="14802-116">Popis</span><span class="sxs-lookup"><span data-stu-id="14802-116">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="14802-117">\<add></span><span class="sxs-lookup"><span data-stu-id="14802-117">\<add></span></span>](add-of-scopes.md)|<span data-ttu-id="14802-118">Přidá informace o oboru pro koncový bod, který lze použít v porovnání kritérií pro hledání služeb.</span><span class="sxs-lookup"><span data-stu-id="14802-118">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="14802-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="14802-119">Parent Elements</span></span>  
  
|<span data-ttu-id="14802-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="14802-120">Element</span></span>|<span data-ttu-id="14802-121">Popis</span><span class="sxs-lookup"><span data-stu-id="14802-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14802-122">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="14802-122">\<endpointDiscovery></span></span>](endpointdiscovery.md)|<span data-ttu-id="14802-123">Určuje různá nastavení zjišťování pro koncový bod, například jeho zjistitelnost, obory a jakákoli vlastní rozšíření pro jeho metadata.</span><span class="sxs-lookup"><span data-stu-id="14802-123">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="14802-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14802-124">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
