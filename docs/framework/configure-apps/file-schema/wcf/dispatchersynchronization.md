---
title: '&lt;dispatcherSynchronization&gt;'
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 537dee408f1af29a06042de439a2c1e7d7874222
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555385"
---
# <a name="ltdispatchersynchronizationgt"></a><span data-ttu-id="155da-102">&lt;dispatcherSynchronization&gt;</span><span class="sxs-lookup"><span data-stu-id="155da-102">&lt;dispatcherSynchronization&gt;</span></span>
  
<span data-ttu-id="155da-103">Určuje chování koncového bodu umožňující službě odeslání asynchronních odpovědí.</span><span class="sxs-lookup"><span data-stu-id="155da-103">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
<span data-ttu-id="155da-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="155da-104">\<system.serviceModel></span></span>  
<span data-ttu-id="155da-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="155da-105">\<behaviors></span></span>  
<span data-ttu-id="155da-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="155da-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="155da-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="155da-107">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="155da-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="155da-108">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="155da-109">Typ</span><span class="sxs-lookup"><span data-stu-id="155da-109">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="155da-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="155da-110">Attributes and elements</span></span>  
  
<span data-ttu-id="155da-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="155da-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="155da-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="155da-112">Attributes</span></span>

| <span data-ttu-id="155da-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="155da-113">Attribute</span></span>               | <span data-ttu-id="155da-114">Popis</span><span class="sxs-lookup"><span data-stu-id="155da-114">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="155da-115">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="155da-115">asynchronousSendEnabled</span></span> | <span data-ttu-id="155da-116">Logická hodnota, která určuje, zda je povoleno chování asynchronního odeslání.</span><span class="sxs-lookup"><span data-stu-id="155da-116">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="155da-117">Celé číslo, které určuje, že počet souběžných přijímání, která může na kanálu uskutečněna.</span><span class="sxs-lookup"><span data-stu-id="155da-117">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="155da-118">Tato hodnota musí být nakonfigurovaný jenom po jste správně nakonfigurovali chování při omezování služby.</span><span class="sxs-lookup"><span data-stu-id="155da-118">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="155da-119">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="155da-119">Child elements</span></span>

<span data-ttu-id="155da-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="155da-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="155da-121">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="155da-121">Parent elements</span></span>

| <span data-ttu-id="155da-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="155da-122">Element</span></span> | <span data-ttu-id="155da-123">Popis</span><span class="sxs-lookup"><span data-stu-id="155da-123">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="155da-124">\<behavior></span><span class="sxs-lookup"><span data-stu-id="155da-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="155da-125">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="155da-125">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="155da-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="155da-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
