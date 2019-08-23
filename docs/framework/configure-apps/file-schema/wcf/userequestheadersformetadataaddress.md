---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 84310d4ae5e04e76e4484f4fc606c9896239c776
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940554"
---
# <a name="userequestheadersformetadataaddress"></a><span data-ttu-id="2e1d2-101">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="2e1d2-101">\<useRequestHeadersForMetadataAddress></span></span>
<span data-ttu-id="2e1d2-102">Umožňuje načtení informací o adrese metadat ze záhlaví zpráv požadavku.</span><span class="sxs-lookup"><span data-stu-id="2e1d2-102">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="2e1d2-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2e1d2-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="2e1d2-104">\<> chování</span><span class="sxs-lookup"><span data-stu-id="2e1d2-104">\<behaviors></span></span>  
<span data-ttu-id="2e1d2-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="2e1d2-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="2e1d2-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="2e1d2-106">\<behavior></span></span>  
<span data-ttu-id="2e1d2-107">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="2e1d2-107">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e1d2-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e1d2-108">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2e1d2-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2e1d2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2e1d2-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2e1d2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2e1d2-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="2e1d2-111">Attributes</span></span>  
 <span data-ttu-id="2e1d2-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="2e1d2-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2e1d2-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2e1d2-113">Child Elements</span></span>  
  
|<span data-ttu-id="2e1d2-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="2e1d2-114">Element</span></span>|<span data-ttu-id="2e1d2-115">Popis</span><span class="sxs-lookup"><span data-stu-id="2e1d2-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2e1d2-116">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="2e1d2-116">\<defaultPorts></span></span>](defaultports.md)|<span data-ttu-id="2e1d2-117">Kolekce výchozích portů, které jsou uvedeny v seznamu výchozích koncových bodů komunikace, na které klientská aplikace naslouchá.</span><span class="sxs-lookup"><span data-stu-id="2e1d2-117">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2e1d2-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2e1d2-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2e1d2-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="2e1d2-119">Element</span></span>|<span data-ttu-id="2e1d2-120">Popis</span><span class="sxs-lookup"><span data-stu-id="2e1d2-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2e1d2-121">\<> chování</span><span class="sxs-lookup"><span data-stu-id="2e1d2-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="2e1d2-122">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="2e1d2-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2e1d2-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e1d2-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
