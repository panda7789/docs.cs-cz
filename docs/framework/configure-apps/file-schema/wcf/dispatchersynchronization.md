---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: b95f25217c2a3558846cc7a0ef43e21aacd2ee2a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398006"
---
# <a name="dispatchersynchronization"></a><span data-ttu-id="c0f0a-101">\<dispatcherSynchronization ></span><span class="sxs-lookup"><span data-stu-id="c0f0a-101">\<dispatcherSynchronization></span></span>
  
<span data-ttu-id="c0f0a-102">Určuje chování koncového bodu, které umožňuje službě odesílat odpovědi asynchronně.</span><span class="sxs-lookup"><span data-stu-id="c0f0a-102">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
<span data-ttu-id="c0f0a-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c0f0a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c0f0a-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c0f0a-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c0f0a-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c0f0a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="c0f0a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c0f0a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="c0f0a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c0f0a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="c0f0a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dispatcherSynchronization >**</span><span class="sxs-lookup"><span data-stu-id="c0f0a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dispatcherSynchronization>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0f0a-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0f0a-109">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="c0f0a-110">type</span><span class="sxs-lookup"><span data-stu-id="c0f0a-110">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0f0a-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c0f0a-111">Attributes and elements</span></span>  
  
<span data-ttu-id="c0f0a-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c0f0a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0f0a-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="c0f0a-113">Attributes</span></span>

| <span data-ttu-id="c0f0a-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="c0f0a-114">Attribute</span></span>               | <span data-ttu-id="c0f0a-115">Popis</span><span class="sxs-lookup"><span data-stu-id="c0f0a-115">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="c0f0a-116">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="c0f0a-116">asynchronousSendEnabled</span></span> | <span data-ttu-id="c0f0a-117">Logická hodnota, která určuje, zda je povoleno chování asynchronního odeslání.</span><span class="sxs-lookup"><span data-stu-id="c0f0a-117">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="c0f0a-118">Celé číslo, které určuje počet souběžných přijímání, které mohou být na kanálu vydány.</span><span class="sxs-lookup"><span data-stu-id="c0f0a-118">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="c0f0a-119">Tato hodnota by se měla konfigurovat až po správném nakonfigurování chování omezení služby.</span><span class="sxs-lookup"><span data-stu-id="c0f0a-119">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="c0f0a-120">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="c0f0a-120">Child elements</span></span>

<span data-ttu-id="c0f0a-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="c0f0a-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c0f0a-122">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="c0f0a-122">Parent elements</span></span>

| <span data-ttu-id="c0f0a-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="c0f0a-123">Element</span></span> | <span data-ttu-id="c0f0a-124">Popis</span><span class="sxs-lookup"><span data-stu-id="c0f0a-124">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="c0f0a-125">\<> chování</span><span class="sxs-lookup"><span data-stu-id="c0f0a-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c0f0a-126">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="c0f0a-126">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="c0f0a-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c0f0a-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
