---
title: <synchronousReceive> – element
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: b3f4860be6b7edac776a1c30611271b2eb36968e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399500"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="27b0c-102">\<synchronousReceive – element ></span><span class="sxs-lookup"><span data-stu-id="27b0c-102">\<synchronousReceive> element</span></span>
<span data-ttu-id="27b0c-103">Tento prvek konfigurace slouží k určení chování za běhu pro příjem zpráv v klientské aplikaci nebo službě.</span><span class="sxs-lookup"><span data-stu-id="27b0c-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="27b0c-104">Neobsahuje žádné atributy ani podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="27b0c-104">It does not have any attributes or child elements.</span></span>  
  
<span data-ttu-id="27b0c-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="27b0c-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="27b0c-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="27b0c-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="27b0c-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="27b0c-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="27b0c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="27b0c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="27b0c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="27b0c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="27b0c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<synchronousReceive >**</span><span class="sxs-lookup"><span data-stu-id="27b0c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<synchronousReceive>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27b0c-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27b0c-111">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27b0c-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="27b0c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="27b0c-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="27b0c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27b0c-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="27b0c-114">Attributes</span></span>  
 <span data-ttu-id="27b0c-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="27b0c-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="27b0c-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="27b0c-116">Child Elements</span></span>  
 <span data-ttu-id="27b0c-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="27b0c-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="27b0c-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="27b0c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="27b0c-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="27b0c-119">Element</span></span>|<span data-ttu-id="27b0c-120">Popis</span><span class="sxs-lookup"><span data-stu-id="27b0c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27b0c-121">\<> chování</span><span class="sxs-lookup"><span data-stu-id="27b0c-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="27b0c-122">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="27b0c-122">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27b0c-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="27b0c-123">Remarks</span></span>  
 <span data-ttu-id="27b0c-124">Toto chování použijte, pokud chcete, aby naslouchací proces kanálu použil synchronní příjem, nikoli jako výchozí, asynchronní.</span><span class="sxs-lookup"><span data-stu-id="27b0c-124">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="27b0c-125">Windows Communication Foundation (WCF) vydá nové vlákno pro každý přijatý kanál.</span><span class="sxs-lookup"><span data-stu-id="27b0c-125">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="27b0c-126">Pokud existuje spousta kanálů, existuje možnost, že je možné vymezit vlákna z provozu.</span><span class="sxs-lookup"><span data-stu-id="27b0c-126">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27b0c-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="27b0c-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
