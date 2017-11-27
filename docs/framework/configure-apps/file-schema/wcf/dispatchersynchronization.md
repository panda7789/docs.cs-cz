---
title: '&lt;dispatcherSynchronization&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 24ae6dbf0fb67b5755aca848ea7fce6abda14b0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltdispatchersynchronizationgt"></a><span data-ttu-id="1f3b4-102">&lt;dispatcherSynchronization&gt;</span><span class="sxs-lookup"><span data-stu-id="1f3b4-102">&lt;dispatcherSynchronization&gt;</span></span>

<span data-ttu-id="1f3b4-103">Určuje chování koncového bodu, umožňující službu pro odeslání odpovědi asynchronně.</span><span class="sxs-lookup"><span data-stu-id="1f3b4-103">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>

<span data-ttu-id="1f3b4-104">\<system.serviceModel > \<chování > \<endpointBehaviors > \<chování ></span><span class="sxs-lookup"><span data-stu-id="1f3b4-104">\<system.serviceModel> \<behaviors> \<endpointBehaviors> \<behavior></span></span>

## <a name="syntax"></a><span data-ttu-id="1f3b4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f3b4-105">Syntax</span></span>

```xml
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean" 
                                   maxPendingReceives="Integer" />
```

## <a name="type"></a><span data-ttu-id="1f3b4-106">Typ</span><span class="sxs-lookup"><span data-stu-id="1f3b4-106">Type</span></span>

`Type`

## <a name="attributes-and-elements"></a><span data-ttu-id="1f3b4-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1f3b4-107">Attributes and elements</span></span>

<span data-ttu-id="1f3b4-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1f3b4-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="1f3b4-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="1f3b4-109">Attributes</span></span>

| <span data-ttu-id="1f3b4-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="1f3b4-110">Attribute</span></span>               | <span data-ttu-id="1f3b4-111">Popis</span><span class="sxs-lookup"><span data-stu-id="1f3b4-111">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="1f3b4-112">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="1f3b4-112">asynchronousSendEnabled</span></span> | <span data-ttu-id="1f3b4-113">Logická hodnota, která určuje, zda je povoleno chování asynchronní odesílání.</span><span class="sxs-lookup"><span data-stu-id="1f3b4-113">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="1f3b4-114">Celé číslo, které určuje, že počet souběžných obdrží, které mohou být vystaveny na kanálu.</span><span class="sxs-lookup"><span data-stu-id="1f3b4-114">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="1f3b4-115">Tato hodnota musí být nakonfigurovaný jenom po je aplikace správně nakonfigurována omezení chování služby.</span><span class="sxs-lookup"><span data-stu-id="1f3b4-115">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="1f3b4-116">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="1f3b4-116">Child elements</span></span>

<span data-ttu-id="1f3b4-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="1f3b4-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1f3b4-118">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="1f3b4-118">Parent elements</span></span>

| <span data-ttu-id="1f3b4-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="1f3b4-119">Element</span></span> | <span data-ttu-id="1f3b4-120">Popis</span><span class="sxs-lookup"><span data-stu-id="1f3b4-120">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="1f3b4-121">\<chování ></span><span class="sxs-lookup"><span data-stu-id="1f3b4-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="1f3b4-122">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="1f3b4-122">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="1f3b4-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f3b4-123">See also</span></span>

 <span data-ttu-id="1f3b4-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement><xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span><span class="sxs-lookup"><span data-stu-id="1f3b4-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span></span>
