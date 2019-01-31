---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 842f989ab1f2f0b9e8fe08e8fd729f983e846ffc
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261565"
---
# <a name="userequestheadersformetadataaddress"></a><span data-ttu-id="f11a3-101">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="f11a3-101">\<useRequestHeadersForMetadataAddress></span></span>
<span data-ttu-id="f11a3-102">Umožňuje načítání informací o adrese metadat ze záhlaví zpráv požadavku.</span><span class="sxs-lookup"><span data-stu-id="f11a3-102">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="f11a3-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f11a3-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="f11a3-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f11a3-104">\<behaviors></span></span>  
<span data-ttu-id="f11a3-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="f11a3-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="f11a3-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f11a3-106">\<behavior></span></span>  
<span data-ttu-id="f11a3-107">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="f11a3-107">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f11a3-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f11a3-108">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f11a3-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f11a3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f11a3-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f11a3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f11a3-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="f11a3-111">Attributes</span></span>  
 <span data-ttu-id="f11a3-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="f11a3-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f11a3-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f11a3-113">Child Elements</span></span>  
  
|<span data-ttu-id="f11a3-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="f11a3-114">Element</span></span>|<span data-ttu-id="f11a3-115">Popis</span><span class="sxs-lookup"><span data-stu-id="f11a3-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f11a3-116">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="f11a3-116">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="f11a3-117">Kolekce výchozích portů obsahující seznam výchozích komunikačních koncových bodů, které naslouchá klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="f11a3-117">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f11a3-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f11a3-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f11a3-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="f11a3-119">Element</span></span>|<span data-ttu-id="f11a3-120">Popis</span><span class="sxs-lookup"><span data-stu-id="f11a3-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f11a3-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="f11a3-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="f11a3-122">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="f11a3-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f11a3-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f11a3-123">See also</span></span>
- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
