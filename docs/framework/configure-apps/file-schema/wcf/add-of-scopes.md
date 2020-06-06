---
title: <add> z <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: bcde6b18c34dccf1716c809dddeb45b1b4da90f0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398310"
---
# <a name="add-of-scopes"></a><span data-ttu-id="2770e-102">\<add> z \<scopes></span><span class="sxs-lookup"><span data-stu-id="2770e-102">\<add> of \<scopes></span></span>
<span data-ttu-id="2770e-103">Přidá identifikátor URI vlastního rozsahu, který lze použít k filtrování koncových bodů služby během dotazu.</span><span class="sxs-lookup"><span data-stu-id="2770e-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopes>**](scopes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="2770e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2770e-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2770e-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2770e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="2770e-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2770e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2770e-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="2770e-107">Attributes</span></span>  
  
|<span data-ttu-id="2770e-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="2770e-108">Attribute</span></span>|<span data-ttu-id="2770e-109">Popis</span><span class="sxs-lookup"><span data-stu-id="2770e-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2770e-110">scope</span><span class="sxs-lookup"><span data-stu-id="2770e-110">scope</span></span>|<span data-ttu-id="2770e-111">Identifikátor URI, který obsahuje informace o oboru pro koncový bod, který lze použít v porovnání kritérií pro hledání služeb.</span><span class="sxs-lookup"><span data-stu-id="2770e-111">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2770e-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2770e-112">Child Elements</span></span>  
 <span data-ttu-id="2770e-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="2770e-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2770e-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2770e-114">Parent Elements</span></span>  
  
|<span data-ttu-id="2770e-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="2770e-115">Element</span></span>|<span data-ttu-id="2770e-116">Description</span><span class="sxs-lookup"><span data-stu-id="2770e-116">Description</span></span>|  
|-------------|-----------------|  
|[\<scopes>](scopes.md)|<span data-ttu-id="2770e-117">Obsahuje kolekci prvků konfigurace, které určují identifikátory URI vlastního oboru, které lze použít k filtrování koncových bodů služby během dotazu.</span><span class="sxs-lookup"><span data-stu-id="2770e-117">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2770e-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="2770e-118">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
