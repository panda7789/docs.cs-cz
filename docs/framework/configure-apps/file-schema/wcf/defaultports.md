---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 595970a56e05c4fc1c9b2c0eb669ec3b3a120fe1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262375"
---
# <a name="defaultports"></a><span data-ttu-id="fe151-101">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="fe151-101">\<defaultPorts></span></span>
<span data-ttu-id="fe151-102">Kolekce výchozích portů obsahující seznam výchozích komunikačních koncových bodů, které naslouchá klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="fe151-102">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="fe151-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fe151-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="fe151-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="fe151-104">\<behaviors></span></span>  
<span data-ttu-id="fe151-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="fe151-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="fe151-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="fe151-106">\<behavior></span></span>  
<span data-ttu-id="fe151-107">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="fe151-107">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="fe151-108">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="fe151-108">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe151-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe151-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe151-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fe151-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fe151-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fe151-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe151-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="fe151-112">Attributes</span></span>  
 <span data-ttu-id="fe151-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="fe151-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fe151-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fe151-114">Child Elements</span></span>  
  
|<span data-ttu-id="fe151-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="fe151-115">Element</span></span>|<span data-ttu-id="fe151-116">Popis</span><span class="sxs-lookup"><span data-stu-id="fe151-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe151-117">\<Přidat > z \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="fe151-117">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="fe151-118">Výchozí koncový bod komunikace, na kterém naslouchá klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="fe151-118">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fe151-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fe151-119">Parent Elements</span></span>  
  
|<span data-ttu-id="fe151-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="fe151-120">Element</span></span>|<span data-ttu-id="fe151-121">Popis</span><span class="sxs-lookup"><span data-stu-id="fe151-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe151-122">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="fe151-122">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="fe151-123">Seznam výchozích portů.</span><span class="sxs-lookup"><span data-stu-id="fe151-123">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fe151-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fe151-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
