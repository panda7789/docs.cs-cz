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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c0a6349f50c8810d834d7887daecb6ac9cffb2e9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltdispatchersynchronizationgt"></a><span data-ttu-id="e8f1b-102">&lt;dispatcherSynchronization&gt;</span><span class="sxs-lookup"><span data-stu-id="e8f1b-102">&lt;dispatcherSynchronization&gt;</span></span>

<span data-ttu-id="e8f1b-103">Určuje chování koncového bodu, umožňující službu pro odeslání odpovědi asynchronně.</span><span class="sxs-lookup"><span data-stu-id="e8f1b-103">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>

<span data-ttu-id="e8f1b-104">\<system.serviceModel > \<chování > \<endpointBehaviors > \<chování ></span><span class="sxs-lookup"><span data-stu-id="e8f1b-104">\<system.serviceModel> \<behaviors> \<endpointBehaviors> \<behavior></span></span>

## <a name="syntax"></a><span data-ttu-id="e8f1b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8f1b-105">Syntax</span></span>

```xml
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean" 
                                   maxPendingReceives="Integer" />
```

## <a name="type"></a><span data-ttu-id="e8f1b-106">Typ</span><span class="sxs-lookup"><span data-stu-id="e8f1b-106">Type</span></span>

`Type`

## <a name="attributes-and-elements"></a><span data-ttu-id="e8f1b-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e8f1b-107">Attributes and elements</span></span>

<span data-ttu-id="e8f1b-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e8f1b-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e8f1b-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="e8f1b-109">Attributes</span></span>

| <span data-ttu-id="e8f1b-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="e8f1b-110">Attribute</span></span>               | <span data-ttu-id="e8f1b-111">Popis</span><span class="sxs-lookup"><span data-stu-id="e8f1b-111">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="e8f1b-112">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="e8f1b-112">asynchronousSendEnabled</span></span> | <span data-ttu-id="e8f1b-113">Logická hodnota, která určuje, zda je povoleno chování asynchronní odesílání.</span><span class="sxs-lookup"><span data-stu-id="e8f1b-113">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="e8f1b-114">Celé číslo, které určuje, že počet souběžných obdrží, které mohou být vystaveny na kanálu.</span><span class="sxs-lookup"><span data-stu-id="e8f1b-114">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="e8f1b-115">Tato hodnota musí být nakonfigurovaný jenom po je aplikace správně nakonfigurována omezení chování služby.</span><span class="sxs-lookup"><span data-stu-id="e8f1b-115">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="e8f1b-116">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="e8f1b-116">Child elements</span></span>

<span data-ttu-id="e8f1b-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="e8f1b-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e8f1b-118">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="e8f1b-118">Parent elements</span></span>

| <span data-ttu-id="e8f1b-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="e8f1b-119">Element</span></span> | <span data-ttu-id="e8f1b-120">Popis</span><span class="sxs-lookup"><span data-stu-id="e8f1b-120">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="e8f1b-121">\<chování ></span><span class="sxs-lookup"><span data-stu-id="e8f1b-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="e8f1b-122">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="e8f1b-122">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="e8f1b-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8f1b-123">See also</span></span>

 <span data-ttu-id="e8f1b-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement><xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span><span class="sxs-lookup"><span data-stu-id="e8f1b-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span></span>
