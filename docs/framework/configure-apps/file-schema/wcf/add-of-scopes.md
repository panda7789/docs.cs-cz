---
title: <add> z <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: b190cb72e21d47bdc62aab2daba0f6eea1ee04ac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926633"
---
# <a name="add-of-scopes"></a><span data-ttu-id="068a6-102">\<Přidat > \<oborů ></span><span class="sxs-lookup"><span data-stu-id="068a6-102">\<add> of \<scopes></span></span>
<span data-ttu-id="068a6-103">Přidá identifikátor URI vlastního rozsahu, který lze použít k filtrování koncových bodů služby během dotazu.</span><span class="sxs-lookup"><span data-stu-id="068a6-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="068a6-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="068a6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="068a6-105">\<> chování</span><span class="sxs-lookup"><span data-stu-id="068a6-105">\<behaviors></span></span>  
<span data-ttu-id="068a6-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="068a6-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="068a6-107">\<> chování</span><span class="sxs-lookup"><span data-stu-id="068a6-107">\<behavior></span></span>  
<span data-ttu-id="068a6-108">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="068a6-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="068a6-109">\<> oborů</span><span class="sxs-lookup"><span data-stu-id="068a6-109">\<scopes></span></span>  
<span data-ttu-id="068a6-110">\<add></span><span class="sxs-lookup"><span data-stu-id="068a6-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="068a6-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="068a6-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="068a6-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="068a6-112">Attributes and Elements</span></span>  
 <span data-ttu-id="068a6-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="068a6-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="068a6-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="068a6-114">Attributes</span></span>  
  
|<span data-ttu-id="068a6-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="068a6-115">Attribute</span></span>|<span data-ttu-id="068a6-116">Popis</span><span class="sxs-lookup"><span data-stu-id="068a6-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="068a6-117">rozsah</span><span class="sxs-lookup"><span data-stu-id="068a6-117">scope</span></span>|<span data-ttu-id="068a6-118">Identifikátor URI, který obsahuje informace o oboru pro koncový bod, který lze použít v porovnání kritérií pro hledání služeb.</span><span class="sxs-lookup"><span data-stu-id="068a6-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="068a6-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="068a6-119">Child Elements</span></span>  
 <span data-ttu-id="068a6-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="068a6-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="068a6-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="068a6-121">Parent Elements</span></span>  
  
|<span data-ttu-id="068a6-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="068a6-122">Element</span></span>|<span data-ttu-id="068a6-123">Popis</span><span class="sxs-lookup"><span data-stu-id="068a6-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="068a6-124">\<> oborů</span><span class="sxs-lookup"><span data-stu-id="068a6-124">\<scopes></span></span>](scopes.md)|<span data-ttu-id="068a6-125">Obsahuje kolekci prvků konfigurace, které určují identifikátory URI vlastního oboru, které lze použít k filtrování koncových bodů služby během dotazu.</span><span class="sxs-lookup"><span data-stu-id="068a6-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="068a6-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="068a6-126">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
