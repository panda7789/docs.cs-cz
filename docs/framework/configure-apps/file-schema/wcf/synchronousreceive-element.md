---
title: Element &lt;synchronousReceive&gt;
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: af1ca2ee1fe3c03c33f05e0c30c7b843b3720a36
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltsynchronousreceivegt-element"></a><span data-ttu-id="5df2b-102">Element &lt;synchronousReceive&gt;</span><span class="sxs-lookup"><span data-stu-id="5df2b-102">&lt;synchronousReceive&gt; element</span></span>
<span data-ttu-id="5df2b-103">Tento element konfigurace slouží k určení chování pro příjem zpráv v aplikaci služby nebo klienta.</span><span class="sxs-lookup"><span data-stu-id="5df2b-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="5df2b-104">Nástroj nemá žádné atributy nebo podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="5df2b-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="5df2b-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5df2b-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="5df2b-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="5df2b-106">\<behaviors></span></span>  
<span data-ttu-id="5df2b-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5df2b-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="5df2b-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="5df2b-108">\<behavior></span></span>  
<span data-ttu-id="5df2b-109">\<synchronousReceive ></span><span class="sxs-lookup"><span data-stu-id="5df2b-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5df2b-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5df2b-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5df2b-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5df2b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5df2b-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5df2b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5df2b-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="5df2b-113">Attributes</span></span>  
 <span data-ttu-id="5df2b-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="5df2b-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5df2b-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5df2b-115">Child Elements</span></span>  
 <span data-ttu-id="5df2b-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="5df2b-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5df2b-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5df2b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5df2b-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="5df2b-118">Element</span></span>|<span data-ttu-id="5df2b-119">Popis</span><span class="sxs-lookup"><span data-stu-id="5df2b-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5df2b-120">\<chování ></span><span class="sxs-lookup"><span data-stu-id="5df2b-120">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="5df2b-121">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="5df2b-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5df2b-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5df2b-122">Remarks</span></span>  
 <span data-ttu-id="5df2b-123">Naslouchací proces kanálu nástroje použijte synchronního přijímat spíše než výchozí, asynchronní použitím toto chování.</span><span class="sxs-lookup"><span data-stu-id="5df2b-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="5df2b-124">Windows Communication Foundation (WCF) vydá nové vlákno čerpadlo pro každý přijatý kanál.</span><span class="sxs-lookup"><span data-stu-id="5df2b-124">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="5df2b-125">Pokud je celá řada kanály, existuje možnost spuštění z vláken.</span><span class="sxs-lookup"><span data-stu-id="5df2b-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5df2b-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="5df2b-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>  
 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
