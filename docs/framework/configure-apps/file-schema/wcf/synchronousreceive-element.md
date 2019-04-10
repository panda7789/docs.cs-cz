---
title: <synchronousReceive>  – element
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: 20390f747c8beaccba1cfea7a9ea0ed366037ecb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166540"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="39051-102">\<synchronousReceive > – element</span><span class="sxs-lookup"><span data-stu-id="39051-102">\<synchronousReceive> element</span></span>
<span data-ttu-id="39051-103">Tento prvek konfigurace slouží k určení chování za běhu pro příjem zpráv v aplikaci klienta nebo službě.</span><span class="sxs-lookup"><span data-stu-id="39051-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="39051-104">Nemá žádné atributy nebo podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="39051-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="39051-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="39051-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="39051-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="39051-106">\<behaviors></span></span>  
<span data-ttu-id="39051-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="39051-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="39051-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="39051-108">\<behavior></span></span>  
<span data-ttu-id="39051-109">\<synchronousReceive ></span><span class="sxs-lookup"><span data-stu-id="39051-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39051-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39051-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39051-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="39051-111">Attributes and Elements</span></span>  
 <span data-ttu-id="39051-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="39051-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39051-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="39051-113">Attributes</span></span>  
 <span data-ttu-id="39051-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="39051-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="39051-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="39051-115">Child Elements</span></span>  
 <span data-ttu-id="39051-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="39051-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="39051-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="39051-117">Parent Elements</span></span>  
  
|<span data-ttu-id="39051-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="39051-118">Element</span></span>|<span data-ttu-id="39051-119">Popis</span><span class="sxs-lookup"><span data-stu-id="39051-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39051-120">\<chování ></span><span class="sxs-lookup"><span data-stu-id="39051-120">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="39051-121">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="39051-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39051-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="39051-122">Remarks</span></span>  
 <span data-ttu-id="39051-123">Toto chování použijte dáte pokyn, aby modul pro naslouchání kanálu pro použití synchronního přijímat spíše než výchozí, asynchronní.</span><span class="sxs-lookup"><span data-stu-id="39051-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="39051-124">Windows Communication Foundation (WCF) vydá nové vlákno odeslané pro každé přijaté kanálu.</span><span class="sxs-lookup"><span data-stu-id="39051-124">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="39051-125">Pokud existuje mnoho kanálů, je možné došly vlákna.</span><span class="sxs-lookup"><span data-stu-id="39051-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39051-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="39051-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
