---
title: <synchronousReceive> – element
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: fa14d4606303b2d67cf5ef845d428bb086680204
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938969"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="c4030-102">\<synchronousReceive – element ></span><span class="sxs-lookup"><span data-stu-id="c4030-102">\<synchronousReceive> element</span></span>
<span data-ttu-id="c4030-103">Tento prvek konfigurace slouží k určení chování za běhu pro příjem zpráv v klientské aplikaci nebo službě.</span><span class="sxs-lookup"><span data-stu-id="c4030-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="c4030-104">Neobsahuje žádné atributy ani podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="c4030-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="c4030-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c4030-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="c4030-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="c4030-106">\<behaviors></span></span>  
<span data-ttu-id="c4030-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="c4030-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="c4030-108">\<> chování</span><span class="sxs-lookup"><span data-stu-id="c4030-108">\<behavior></span></span>  
<span data-ttu-id="c4030-109">\<synchronousReceive ></span><span class="sxs-lookup"><span data-stu-id="c4030-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4030-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4030-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4030-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c4030-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c4030-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c4030-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4030-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="c4030-113">Attributes</span></span>  
 <span data-ttu-id="c4030-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="c4030-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c4030-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c4030-115">Child Elements</span></span>  
 <span data-ttu-id="c4030-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="c4030-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c4030-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c4030-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c4030-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="c4030-118">Element</span></span>|<span data-ttu-id="c4030-119">Popis</span><span class="sxs-lookup"><span data-stu-id="c4030-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c4030-120">\<> chování</span><span class="sxs-lookup"><span data-stu-id="c4030-120">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c4030-121">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="c4030-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4030-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4030-122">Remarks</span></span>  
 <span data-ttu-id="c4030-123">Toto chování použijte, pokud chcete, aby naslouchací proces kanálu použil synchronní příjem, nikoli jako výchozí, asynchronní.</span><span class="sxs-lookup"><span data-stu-id="c4030-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="c4030-124">Windows Communication Foundation (WCF) vydá nové vlákno pro každý přijatý kanál.</span><span class="sxs-lookup"><span data-stu-id="c4030-124">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="c4030-125">Pokud existuje spousta kanálů, existuje možnost, že je možné vymezit vlákna z provozu.</span><span class="sxs-lookup"><span data-stu-id="c4030-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4030-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4030-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
