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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 79d78517b62e4476106ff1ed7978c770a17caf2a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltsynchronousreceivegt-element"></a><span data-ttu-id="60358-102">Element &lt;synchronousReceive&gt;</span><span class="sxs-lookup"><span data-stu-id="60358-102">&lt;synchronousReceive&gt; element</span></span>
<span data-ttu-id="60358-103">Tento element konfigurace slouží k určení chování pro příjem zpráv v aplikaci služby nebo klienta.</span><span class="sxs-lookup"><span data-stu-id="60358-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="60358-104">Nástroj nemá žádné atributy nebo podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="60358-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="60358-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="60358-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="60358-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="60358-106">\<behaviors></span></span>  
<span data-ttu-id="60358-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="60358-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="60358-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="60358-108">\<behavior></span></span>  
<span data-ttu-id="60358-109">\<synchronousReceive ></span><span class="sxs-lookup"><span data-stu-id="60358-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60358-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60358-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60358-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="60358-111">Attributes and Elements</span></span>  
 <span data-ttu-id="60358-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="60358-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60358-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="60358-113">Attributes</span></span>  
 <span data-ttu-id="60358-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="60358-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="60358-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="60358-115">Child Elements</span></span>  
 <span data-ttu-id="60358-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="60358-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="60358-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="60358-117">Parent Elements</span></span>  
  
|<span data-ttu-id="60358-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="60358-118">Element</span></span>|<span data-ttu-id="60358-119">Popis</span><span class="sxs-lookup"><span data-stu-id="60358-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60358-120">\<chování ></span><span class="sxs-lookup"><span data-stu-id="60358-120">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="60358-121">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="60358-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60358-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="60358-122">Remarks</span></span>  
 <span data-ttu-id="60358-123">Naslouchací proces kanálu nástroje použijte synchronního přijímat spíše než výchozí, asynchronní použitím toto chování.</span><span class="sxs-lookup"><span data-stu-id="60358-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="60358-124">vydá nové vlákno čerpadlo pro každý přijatý kanál.</span><span class="sxs-lookup"><span data-stu-id="60358-124"> issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="60358-125">Pokud je celá řada kanály, existuje možnost spuštění z vláken.</span><span class="sxs-lookup"><span data-stu-id="60358-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60358-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="60358-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>  
 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
