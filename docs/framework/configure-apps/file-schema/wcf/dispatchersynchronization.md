---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 7336c9f7d8a117f9a9bfd338e47941eeb648fa51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925847"
---
# <a name="dispatchersynchronization"></a><span data-ttu-id="59f3a-101">\<dispatcherSynchronization ></span><span class="sxs-lookup"><span data-stu-id="59f3a-101">\<dispatcherSynchronization></span></span>
  
<span data-ttu-id="59f3a-102">Určuje chování koncového bodu, které umožňuje službě odesílat odpovědi asynchronně.</span><span class="sxs-lookup"><span data-stu-id="59f3a-102">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
<span data-ttu-id="59f3a-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="59f3a-103">\<system.serviceModel></span></span>  
<span data-ttu-id="59f3a-104">\<> chování</span><span class="sxs-lookup"><span data-stu-id="59f3a-104">\<behaviors></span></span>  
<span data-ttu-id="59f3a-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="59f3a-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="59f3a-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="59f3a-106">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59f3a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59f3a-107">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="59f3a-108">type</span><span class="sxs-lookup"><span data-stu-id="59f3a-108">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59f3a-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="59f3a-109">Attributes and elements</span></span>  
  
<span data-ttu-id="59f3a-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="59f3a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59f3a-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="59f3a-111">Attributes</span></span>

| <span data-ttu-id="59f3a-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="59f3a-112">Attribute</span></span>               | <span data-ttu-id="59f3a-113">Popis</span><span class="sxs-lookup"><span data-stu-id="59f3a-113">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="59f3a-114">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="59f3a-114">asynchronousSendEnabled</span></span> | <span data-ttu-id="59f3a-115">Logická hodnota, která určuje, zda je povoleno chování asynchronního odeslání.</span><span class="sxs-lookup"><span data-stu-id="59f3a-115">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="59f3a-116">Celé číslo, které určuje počet souběžných přijímání, které mohou být na kanálu vydány.</span><span class="sxs-lookup"><span data-stu-id="59f3a-116">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="59f3a-117">Tato hodnota by se měla konfigurovat až po správném nakonfigurování chování omezení služby.</span><span class="sxs-lookup"><span data-stu-id="59f3a-117">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="59f3a-118">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="59f3a-118">Child elements</span></span>

<span data-ttu-id="59f3a-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="59f3a-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="59f3a-120">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="59f3a-120">Parent elements</span></span>

| <span data-ttu-id="59f3a-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="59f3a-121">Element</span></span> | <span data-ttu-id="59f3a-122">Popis</span><span class="sxs-lookup"><span data-stu-id="59f3a-122">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="59f3a-123">\<> chování</span><span class="sxs-lookup"><span data-stu-id="59f3a-123">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="59f3a-124">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="59f3a-124">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="59f3a-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59f3a-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
