---
title: Element &lt;synchronousReceive&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b630f5ad2fbf5e3f20667e0bd1b7ae711992dc18
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltsynchronousreceivegt-element"></a><span data-ttu-id="29a69-102">Element &lt;synchronousReceive&gt;</span><span class="sxs-lookup"><span data-stu-id="29a69-102">&lt;synchronousReceive&gt; element</span></span>
<span data-ttu-id="29a69-103">Tento element konfigurace slouží k určení chování pro příjem zpráv v aplikaci služby nebo klienta.</span><span class="sxs-lookup"><span data-stu-id="29a69-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="29a69-104">Nástroj nemá žádné atributy nebo podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="29a69-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="29a69-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="29a69-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="29a69-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="29a69-106">\<behaviors></span></span>  
<span data-ttu-id="29a69-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="29a69-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="29a69-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="29a69-108">\<behavior></span></span>  
<span data-ttu-id="29a69-109">\<synchronousReceive ></span><span class="sxs-lookup"><span data-stu-id="29a69-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29a69-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29a69-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29a69-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="29a69-111">Attributes and Elements</span></span>  
 <span data-ttu-id="29a69-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="29a69-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29a69-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="29a69-113">Attributes</span></span>  
 <span data-ttu-id="29a69-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="29a69-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="29a69-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="29a69-115">Child Elements</span></span>  
 <span data-ttu-id="29a69-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="29a69-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="29a69-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="29a69-117">Parent Elements</span></span>  
  
|<span data-ttu-id="29a69-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="29a69-118">Element</span></span>|<span data-ttu-id="29a69-119">Popis</span><span class="sxs-lookup"><span data-stu-id="29a69-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29a69-120">\<chování ></span><span class="sxs-lookup"><span data-stu-id="29a69-120">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="29a69-121">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="29a69-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29a69-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="29a69-122">Remarks</span></span>  
 <span data-ttu-id="29a69-123">Naslouchací proces kanálu nástroje použijte synchronního přijímat spíše než výchozí, asynchronní použitím toto chování.</span><span class="sxs-lookup"><span data-stu-id="29a69-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="29a69-124">vydá nové vlákno čerpadlo pro každý přijatý kanál.</span><span class="sxs-lookup"><span data-stu-id="29a69-124"> issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="29a69-125">Pokud je celá řada kanály, existuje možnost spuštění z vláken.</span><span class="sxs-lookup"><span data-stu-id="29a69-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29a69-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="29a69-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>  
 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
