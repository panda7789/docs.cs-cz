---
title: '&lt;dispatcherSynchronization&gt;'
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 86660620113b162a9a5260b7026a64455284d184
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151459"
---
# <a name="ltdispatchersynchronizationgt"></a><span data-ttu-id="33ef1-102">&lt;dispatcherSynchronization&gt;</span><span class="sxs-lookup"><span data-stu-id="33ef1-102">&lt;dispatcherSynchronization&gt;</span></span>
  
<span data-ttu-id="33ef1-103">Určuje chování koncového bodu umožňující službě odeslání asynchronních odpovědí.</span><span class="sxs-lookup"><span data-stu-id="33ef1-103">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
<span data-ttu-id="33ef1-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="33ef1-104">\<system.serviceModel></span></span>  
<span data-ttu-id="33ef1-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="33ef1-105">\<behaviors></span></span>  
<span data-ttu-id="33ef1-106">\<názvy endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="33ef1-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="33ef1-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="33ef1-107">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33ef1-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33ef1-108">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="33ef1-109">Typ</span><span class="sxs-lookup"><span data-stu-id="33ef1-109">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="33ef1-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="33ef1-110">Attributes and elements</span></span>  
  
<span data-ttu-id="33ef1-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="33ef1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="33ef1-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="33ef1-112">Attributes</span></span>

| <span data-ttu-id="33ef1-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="33ef1-113">Attribute</span></span>               | <span data-ttu-id="33ef1-114">Popis</span><span class="sxs-lookup"><span data-stu-id="33ef1-114">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="33ef1-115">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="33ef1-115">asynchronousSendEnabled</span></span> | <span data-ttu-id="33ef1-116">Logická hodnota, která určuje, zda je povoleno chování asynchronního odeslání.</span><span class="sxs-lookup"><span data-stu-id="33ef1-116">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="33ef1-117">Celé číslo, které určuje, že počet souběžných přijímání, která může na kanálu uskutečněna.</span><span class="sxs-lookup"><span data-stu-id="33ef1-117">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="33ef1-118">Tato hodnota musí být nakonfigurovaný jenom po jste správně nakonfigurovali chování při omezování služby.</span><span class="sxs-lookup"><span data-stu-id="33ef1-118">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="33ef1-119">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="33ef1-119">Child elements</span></span>

<span data-ttu-id="33ef1-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="33ef1-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="33ef1-121">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="33ef1-121">Parent elements</span></span>

| <span data-ttu-id="33ef1-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="33ef1-122">Element</span></span> | <span data-ttu-id="33ef1-123">Popis</span><span class="sxs-lookup"><span data-stu-id="33ef1-123">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="33ef1-124">\<chování ></span><span class="sxs-lookup"><span data-stu-id="33ef1-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="33ef1-125">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="33ef1-125">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="33ef1-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="33ef1-126">See also</span></span>

 <span data-ttu-id="33ef1-127"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement><xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span><span class="sxs-lookup"><span data-stu-id="33ef1-127"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span></span>
