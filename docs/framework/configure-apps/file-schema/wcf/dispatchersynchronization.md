---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 6be9752e8102a5d4db4fed31aae8ff6d56fdd24e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55273329"
---
# <a name="dispatchersynchronization"></a><span data-ttu-id="e3019-101">\<dispatcherSynchronization></span><span class="sxs-lookup"><span data-stu-id="e3019-101">\<dispatcherSynchronization></span></span>
  
<span data-ttu-id="e3019-102">Určuje chování koncového bodu umožňující službě odeslání asynchronních odpovědí.</span><span class="sxs-lookup"><span data-stu-id="e3019-102">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
<span data-ttu-id="e3019-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e3019-103">\<system.serviceModel></span></span>  
<span data-ttu-id="e3019-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="e3019-104">\<behaviors></span></span>  
<span data-ttu-id="e3019-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="e3019-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="e3019-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="e3019-106">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3019-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3019-107">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="e3019-108">Typ</span><span class="sxs-lookup"><span data-stu-id="e3019-108">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3019-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e3019-109">Attributes and elements</span></span>  
  
<span data-ttu-id="e3019-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e3019-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3019-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="e3019-111">Attributes</span></span>

| <span data-ttu-id="e3019-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="e3019-112">Attribute</span></span>               | <span data-ttu-id="e3019-113">Popis</span><span class="sxs-lookup"><span data-stu-id="e3019-113">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="e3019-114">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="e3019-114">asynchronousSendEnabled</span></span> | <span data-ttu-id="e3019-115">Logická hodnota, která určuje, zda je povoleno chování asynchronního odeslání.</span><span class="sxs-lookup"><span data-stu-id="e3019-115">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="e3019-116">Celé číslo, které určuje, že počet souběžných přijímání, která může na kanálu uskutečněna.</span><span class="sxs-lookup"><span data-stu-id="e3019-116">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="e3019-117">Tato hodnota musí být nakonfigurovaný jenom po jste správně nakonfigurovali chování při omezování služby.</span><span class="sxs-lookup"><span data-stu-id="e3019-117">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="e3019-118">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="e3019-118">Child elements</span></span>

<span data-ttu-id="e3019-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="e3019-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e3019-120">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="e3019-120">Parent elements</span></span>

| <span data-ttu-id="e3019-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="e3019-121">Element</span></span> | <span data-ttu-id="e3019-122">Popis</span><span class="sxs-lookup"><span data-stu-id="e3019-122">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="e3019-123">\<behavior></span><span class="sxs-lookup"><span data-stu-id="e3019-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="e3019-124">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="e3019-124">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="e3019-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3019-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
