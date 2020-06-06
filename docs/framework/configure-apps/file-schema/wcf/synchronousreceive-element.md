---
title: <synchronousReceive> – element
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: b3f4860be6b7edac776a1c30611271b2eb36968e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399500"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="c81e6-102">\<synchronousReceive> – element</span><span class="sxs-lookup"><span data-stu-id="c81e6-102">\<synchronousReceive> element</span></span>
<span data-ttu-id="c81e6-103">Tento prvek konfigurace slouží k určení chování za běhu pro příjem zpráv v klientské aplikaci nebo službě.</span><span class="sxs-lookup"><span data-stu-id="c81e6-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="c81e6-104">Neobsahuje žádné atributy ani podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="c81e6-104">It does not have any attributes or child elements.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<synchronousReceive>**  
  
## <a name="syntax"></a><span data-ttu-id="c81e6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c81e6-105">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c81e6-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c81e6-106">Attributes and Elements</span></span>  
 <span data-ttu-id="c81e6-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c81e6-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c81e6-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="c81e6-108">Attributes</span></span>  
 <span data-ttu-id="c81e6-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="c81e6-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c81e6-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c81e6-110">Child Elements</span></span>  
 <span data-ttu-id="c81e6-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="c81e6-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c81e6-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c81e6-112">Parent Elements</span></span>  
  
|<span data-ttu-id="c81e6-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="c81e6-113">Element</span></span>|<span data-ttu-id="c81e6-114">Description</span><span class="sxs-lookup"><span data-stu-id="c81e6-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c81e6-115">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="c81e6-115">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c81e6-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c81e6-116">Remarks</span></span>  
 <span data-ttu-id="c81e6-117">Toto chování použijte, pokud chcete, aby naslouchací proces kanálu použil synchronní příjem, nikoli jako výchozí, asynchronní.</span><span class="sxs-lookup"><span data-stu-id="c81e6-117">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="c81e6-118">Windows Communication Foundation (WCF) vydá nové vlákno pro každý přijatý kanál.</span><span class="sxs-lookup"><span data-stu-id="c81e6-118">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="c81e6-119">Pokud existuje spousta kanálů, existuje možnost, že je možné vymezit vlákna z provozu.</span><span class="sxs-lookup"><span data-stu-id="c81e6-119">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c81e6-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="c81e6-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
