---
title: Element &lt;synchronousReceive&gt;
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: bc89470900e50e4d3e522682b39b20e21a66b284
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147379"
---
# <a name="ltsynchronousreceivegt-element"></a><span data-ttu-id="de4dd-102">Element &lt;synchronousReceive&gt;</span><span class="sxs-lookup"><span data-stu-id="de4dd-102">&lt;synchronousReceive&gt; element</span></span>
<span data-ttu-id="de4dd-103">Tento prvek konfigurace slouží k určení chování za běhu pro příjem zpráv v aplikaci klienta nebo službě.</span><span class="sxs-lookup"><span data-stu-id="de4dd-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="de4dd-104">Nemá žádné atributy nebo podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="de4dd-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="de4dd-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="de4dd-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="de4dd-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="de4dd-106">\<behaviors></span></span>  
<span data-ttu-id="de4dd-107">\<názvy endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="de4dd-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="de4dd-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="de4dd-108">\<behavior></span></span>  
<span data-ttu-id="de4dd-109">\<synchronousReceive ></span><span class="sxs-lookup"><span data-stu-id="de4dd-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de4dd-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de4dd-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de4dd-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="de4dd-111">Attributes and Elements</span></span>  
 <span data-ttu-id="de4dd-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="de4dd-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de4dd-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="de4dd-113">Attributes</span></span>  
 <span data-ttu-id="de4dd-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="de4dd-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="de4dd-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="de4dd-115">Child Elements</span></span>  
 <span data-ttu-id="de4dd-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="de4dd-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de4dd-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="de4dd-117">Parent Elements</span></span>  
  
|<span data-ttu-id="de4dd-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="de4dd-118">Element</span></span>|<span data-ttu-id="de4dd-119">Popis</span><span class="sxs-lookup"><span data-stu-id="de4dd-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de4dd-120">\<chování ></span><span class="sxs-lookup"><span data-stu-id="de4dd-120">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="de4dd-121">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="de4dd-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de4dd-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="de4dd-122">Remarks</span></span>  
 <span data-ttu-id="de4dd-123">Toto chování použijte dáte pokyn, aby modul pro naslouchání kanálu pro použití synchronního přijímat spíše než výchozí, asynchronní.</span><span class="sxs-lookup"><span data-stu-id="de4dd-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="de4dd-124">Windows Communication Foundation (WCF) vydá nové vlákno odeslané pro každé přijaté kanálu.</span><span class="sxs-lookup"><span data-stu-id="de4dd-124">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="de4dd-125">Pokud existuje mnoho kanálů, je možné došly vlákna.</span><span class="sxs-lookup"><span data-stu-id="de4dd-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de4dd-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="de4dd-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>  
 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
