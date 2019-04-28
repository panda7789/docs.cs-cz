---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 6be9752e8102a5d4db4fed31aae8ff6d56fdd24e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673404"
---
# <a name="dispatchersynchronization"></a><span data-ttu-id="cf7d2-101">\<dispatcherSynchronization></span><span class="sxs-lookup"><span data-stu-id="cf7d2-101">\<dispatcherSynchronization></span></span>
  
<span data-ttu-id="cf7d2-102">Určuje chování koncového bodu umožňující službě odeslání asynchronních odpovědí.</span><span class="sxs-lookup"><span data-stu-id="cf7d2-102">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
<span data-ttu-id="cf7d2-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="cf7d2-103">\<system.serviceModel></span></span>  
<span data-ttu-id="cf7d2-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="cf7d2-104">\<behaviors></span></span>  
<span data-ttu-id="cf7d2-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="cf7d2-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="cf7d2-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="cf7d2-106">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf7d2-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf7d2-107">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="cf7d2-108">Type</span><span class="sxs-lookup"><span data-stu-id="cf7d2-108">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf7d2-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cf7d2-109">Attributes and elements</span></span>  
  
<span data-ttu-id="cf7d2-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cf7d2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf7d2-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="cf7d2-111">Attributes</span></span>

| <span data-ttu-id="cf7d2-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="cf7d2-112">Attribute</span></span>               | <span data-ttu-id="cf7d2-113">Popis</span><span class="sxs-lookup"><span data-stu-id="cf7d2-113">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="cf7d2-114">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="cf7d2-114">asynchronousSendEnabled</span></span> | <span data-ttu-id="cf7d2-115">Logická hodnota, která určuje, zda je povoleno chování asynchronního odeslání.</span><span class="sxs-lookup"><span data-stu-id="cf7d2-115">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="cf7d2-116">Celé číslo, které určuje, že počet souběžných přijímání, která může na kanálu uskutečněna.</span><span class="sxs-lookup"><span data-stu-id="cf7d2-116">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="cf7d2-117">Tato hodnota musí být nakonfigurovaný jenom po jste správně nakonfigurovali chování při omezování služby.</span><span class="sxs-lookup"><span data-stu-id="cf7d2-117">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="cf7d2-118">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="cf7d2-118">Child elements</span></span>

<span data-ttu-id="cf7d2-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="cf7d2-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cf7d2-120">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="cf7d2-120">Parent elements</span></span>

| <span data-ttu-id="cf7d2-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="cf7d2-121">Element</span></span> | <span data-ttu-id="cf7d2-122">Popis</span><span class="sxs-lookup"><span data-stu-id="cf7d2-122">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="cf7d2-123">\<behavior></span><span class="sxs-lookup"><span data-stu-id="cf7d2-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="cf7d2-124">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="cf7d2-124">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="cf7d2-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cf7d2-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
