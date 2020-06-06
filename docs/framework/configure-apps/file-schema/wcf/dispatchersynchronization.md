---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: b95f25217c2a3558846cc7a0ef43e21aacd2ee2a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398006"
---
# \<dispatcherSynchronization>
  
<span data-ttu-id="95715-101">Určuje chování koncového bodu, které umožňuje službě odesílat odpovědi asynchronně.</span><span class="sxs-lookup"><span data-stu-id="95715-101">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dispatcherSynchronization>**  
  
## <a name="syntax"></a><span data-ttu-id="95715-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95715-102">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="95715-103">Typ</span><span class="sxs-lookup"><span data-stu-id="95715-103">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95715-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="95715-104">Attributes and elements</span></span>  
  
<span data-ttu-id="95715-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="95715-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95715-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="95715-106">Attributes</span></span>

| <span data-ttu-id="95715-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="95715-107">Attribute</span></span>               | <span data-ttu-id="95715-108">Popis</span><span class="sxs-lookup"><span data-stu-id="95715-108">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="95715-109">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="95715-109">asynchronousSendEnabled</span></span> | <span data-ttu-id="95715-110">Logická hodnota, která určuje, zda je povoleno chování asynchronního odeslání.</span><span class="sxs-lookup"><span data-stu-id="95715-110">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="95715-111">Celé číslo, které určuje počet souběžných přijímání, které mohou být na kanálu vydány.</span><span class="sxs-lookup"><span data-stu-id="95715-111">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="95715-112">Tato hodnota by se měla konfigurovat až po správném nakonfigurování chování omezení služby.</span><span class="sxs-lookup"><span data-stu-id="95715-112">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="95715-113">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="95715-113">Child elements</span></span>

<span data-ttu-id="95715-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="95715-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="95715-115">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="95715-115">Parent elements</span></span>

| <span data-ttu-id="95715-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="95715-116">Element</span></span> | <span data-ttu-id="95715-117">Description</span><span class="sxs-lookup"><span data-stu-id="95715-117">Description</span></span> |  
| ------- | ----------- |  
| [\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="95715-118">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="95715-118">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="95715-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="95715-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
