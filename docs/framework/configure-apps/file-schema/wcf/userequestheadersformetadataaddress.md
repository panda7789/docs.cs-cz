---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 969461d0e5bdc9f8c49b7a019a6000af5af77eec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788723"
---
# <a name="userequestheadersformetadataaddress"></a><span data-ttu-id="1f926-101">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="1f926-101">\<useRequestHeadersForMetadataAddress></span></span>
<span data-ttu-id="1f926-102">Umožňuje načítání informací o adrese metadat ze záhlaví zpráv požadavku.</span><span class="sxs-lookup"><span data-stu-id="1f926-102">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="1f926-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1f926-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="1f926-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="1f926-104">\<behaviors></span></span>  
<span data-ttu-id="1f926-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="1f926-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="1f926-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="1f926-106">\<behavior></span></span>  
<span data-ttu-id="1f926-107">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="1f926-107">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f926-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f926-108">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f926-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1f926-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1f926-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1f926-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f926-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="1f926-111">Attributes</span></span>  
 <span data-ttu-id="1f926-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="1f926-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1f926-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1f926-113">Child Elements</span></span>  
  
|<span data-ttu-id="1f926-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="1f926-114">Element</span></span>|<span data-ttu-id="1f926-115">Popis</span><span class="sxs-lookup"><span data-stu-id="1f926-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1f926-116">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="1f926-116">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="1f926-117">Kolekce výchozích portů obsahující seznam výchozích komunikačních koncových bodů, které naslouchá klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="1f926-117">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1f926-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1f926-118">Parent Elements</span></span>  
  
|<span data-ttu-id="1f926-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="1f926-119">Element</span></span>|<span data-ttu-id="1f926-120">Popis</span><span class="sxs-lookup"><span data-stu-id="1f926-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1f926-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="1f926-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="1f926-122">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="1f926-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1f926-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1f926-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
